---
title: Solución de problemas del servicio de protección de host
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 424b8090-0692-49a6-9dc4-3c0e77d74b80
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 09/25/2019
ms.openlocfilehash: d34bbeee1a980aba76b5bed994be8db7fc8c8acf
ms.sourcegitcommit: de71970be7d81b95610a0977c12d456c3917c331
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940819"
---
# <a name="troubleshooting-the-host-guardian-service"></a>Solución de problemas del servicio de protección de host

> Se aplica a: Windows Server 2019, Windows Server (canal semianual), Windows Server 2016

En este tema se describen las soluciones a problemas comunes que se producen al implementar o operar un servidor de servicio de protección de host (HGS) en un tejido protegido.
Si no está seguro de la naturaleza del problema, primero intente ejecutar los [diagnósticos de tejido protegido](guarded-fabric-troubleshoot-diagnostics.md) en los servidores de HGS y en los hosts de Hyper-V para reducir las posibles causas.

## <a name="certificates"></a>Certificados

HGS requiere varios certificados para poder funcionar, incluidos el certificado de firma y cifrado configurado por el administrador, así como un certificado de atestación administrado por el propio HGS.
Si estos certificados no están configurados correctamente, HGS no podrá atender las solicitudes de los hosts de Hyper-V que desean atestiguar o desbloquear los protectores de clave para las máquinas virtuales blindadas.
En las secciones siguientes se tratan los problemas comunes relacionados con los certificados configurados en HGS.

### <a name="certificate-permissions"></a>Permisos de certificado

HGS debe poder acceder a las claves públicas y privadas de los certificados de cifrado y firma agregados a HGS mediante la huella digital del certificado.
En concreto, la cuenta de servicio administrada de grupo (gMSA) que ejecuta el servicio HGS necesita tener acceso a las claves.
Para buscar el gMSA que usa HGS, ejecute el siguiente comando en un símbolo del sistema de PowerShell con privilegios elevados en el servidor HGS:

```powershell
(Get-IISAppPool -Name KeyProtection).ProcessModel.UserName
```

La forma de conceder acceso a la cuenta de gMSA para usar la clave privada depende de dónde se almacene la clave: en el equipo como un archivo de certificado local, en un módulo de seguridad de hardware (HSM) o mediante un proveedor personalizado de almacenamiento de claves de terceros.

#### <a name="grant-access-to-software-backed-private-keys"></a>Conceder acceso a las claves privadas respaldadas por software

Si está utilizando un certificado autofirmado o un certificado emitido por una entidad de certificación que **no** está almacenada en un módulo de seguridad de hardware o un proveedor de almacenamiento de claves personalizado, puede cambiar los permisos de la clave privada realizando los pasos siguientes:

1. Abra el administrador de certificados local (certlm. msc).
2. Expanda **certificados de > personales** y busque el certificado de firma o cifrado que desea actualizar.
3. Haga clic con el botón derecho en el certificado y seleccione **todas las tareas > administrar claves privadas**.
4. Haga clic en **Agregar** para conceder a un usuario nuevo acceso a la clave privada de Certiciate.
5. En el selector de objetos, escriba el nombre de cuenta de gMSA para HGS encontrado anteriormente y haga clic en **Aceptar**.
6. Asegúrese de que gMSA tenga acceso de **lectura** al certificado.
7. Haga clic en **Aceptar** para cerrar la ventana de permisos.

Si está ejecutando HGS en Server Core o administra el servidor de forma remota, no podrá administrar las claves privadas mediante el administrador de certificados local.
En su lugar, debe descargar el módulo de [PowerShell herramientas de tejido protegido](https://www.powershellgallery.com/packages/GuardedFabricTools) , que le permitirá administrar los permisos en PowerShell.

1. Abra una consola de PowerShell con privilegios elevados en el equipo de Server Core o use la comunicación remota de PowerShell con una cuenta que tenga permisos de administrador local en HGS.
2. Ejecute los siguientes comandos para instalar el módulo de PowerShell herramientas de tejido protegido y conceda a la cuenta gMSA acceso a la clave privada.

```powershell
$certificateThumbprint = '<ENTER CERTIFICATE THUMBPRINT HERE>'

# Install the Guarded Fabric Tools module, if necessary
Install-Module -Name GuardedFabricTools -Repository PSGallery

# Import the module into the current session
Import-Module -Name GuardedFabricTools

# Get the certificate object
$cert = Get-Item "Cert:\LocalMachine\My\$certificateThumbprint"

# Get the gMSA account name
$gMSA = (Get-IISAppPool -Name KeyProtection).ProcessModel.UserName

# Grant the gMSA read access to the certificate
$cert.Acl = $cert.Acl | Add-AccessRule $gMSA Read Allow
```

#### <a name="grant-access-to-hsm-or-custom-provider-backed-private-keys"></a>Conceder acceso a HSM o a claves privadas respaldadas por un proveedor personalizado

Si las claves privadas del certificado están respaldadas por un módulo de seguridad de hardware (HSM) o un proveedor de almacenamiento de claves (KSP) personalizado, el modelo de permisos dependerá de su proveedor de software específico.
Para obtener los mejores resultados, consulte la documentación del proveedor o el sitio de soporte técnico para obtener información sobre cómo se administran los permisos de clave privada para un dispositivo o software específico.
En todos los casos, el gMSA que usa HGS requiere permisos de *lectura* en las claves privadas del certificado de cifrado, firma y comunicaciones para que pueda realizar operaciones de firma y cifrado.

Algunos módulos de seguridad de hardware no admiten la concesión de cuentas de usuario específicas al acceso a una clave privada. en su lugar, permiten que la cuenta de equipo tenga acceso a todas las claves de un conjunto de claves específico.
Para estos dispositivos, normalmente es suficiente proporcionar al equipo acceso a las claves y HGS podrá aprovechar esa conexión.

**Sugerencias para HSM**

A continuación se muestran las opciones de configuración recomendadas para ayudarle a usar correctamente las claves respaldadas por HSM con el HGS basado en las experiencias de Microsoft y sus asociados.
Estas sugerencias se proporcionan para su comodidad y no se garantiza que sean correctas en el momento de la lectura, ni son aprobadas por los fabricantes de HSM.
Si tiene más preguntas, póngase en contacto con el fabricante de HSM para obtener información precisa sobre el dispositivo específico.

Marca/serie HSM      | Sugerencia
----------------------|-------------
Gemalto SafeNet       | Asegúrese de que la propiedad uso de la clave del archivo de solicitud de certificado está establecida en 0XA0, lo que permite usar el certificado para la firma y el cifrado. Además, debe conceder a la cuenta gMSA acceso de *lectura* a la clave privada mediante la herramienta Administrador de certificados local (consulte los pasos anteriores).
nCipher nShield        | Asegúrese de que cada nodo de HGS tiene acceso al mundo de seguridad que contiene las claves de firma y cifrado. Además, es posible que tenga que conceder a gMSA acceso de *lectura* a la clave privada mediante el administrador de certificados local (consulte los pasos anteriores).
Utimaco CryptoServers | Asegúrese de que la propiedad uso de la clave del archivo de solicitud de certificado está establecida en 0x13, lo que permite usar el certificado para el cifrado, el descifrado y la firma.

### <a name="certificate-requests"></a>Solicitudes de certificado

Si usa una entidad de certificación para emitir los certificados en un entorno de infraestructura de clave pública (PKI), deberá asegurarse de que la solicitud de certificado incluye los requisitos mínimos para el uso de las claves de HGS.

**Certificados de firma**

Propiedad CSR | Valor obligatorio
-------------|---------------
Algoritmo    | RSA
Tamaño de clave     | Al menos 2048 bits
Uso de la clave    | Signature/Sign/DigitalSignature

**Certificados de cifrado**

Propiedad CSR | Valor obligatorio
-------------|---------------
Algoritmo    | RSA
Tamaño de clave     | Al menos 2048 bits
Uso de la clave    | Cifrado/cifrado/DataEncipherment

**Active Directory plantillas de servicios de certificados**

Si está utilizando Active Directory plantillas de certificado de servicios de Certificate Server (ADCS) para crear los certificados, se recomienda usar una plantilla con la siguiente configuración:

Propiedad de plantilla ADCS | Valor obligatorio
-----------------------|---------------
Categoría de proveedor      | Proveedor de almacenamiento de claves
Nombre del algoritmo         | RSA
Tamaño mínimo de clave       | 2048
Propósito                | Firma y cifrado
Extensión uso de claves    | Firma digital, cifrado de clave, cifrado de datos ("permitir cifrado de datos de usuario")


### <a name="time-drift"></a>Desplazamiento de tiempo

Si el tiempo de su servidor se ha desplazado significativamente del de otros nodos de HGS o de hosts de Hyper-V en el tejido protegido, es posible que se produzcan problemas con la validez del certificado de firma de atestación.
El certificado de firma de atestación se crea y se renueva en segundo plano en el HGS y se usa para firmar los certificados de mantenimiento emitidos para los hosts protegidos por el servicio de atestación.

Para actualizar el certificado de firma de atestación, ejecute el siguiente comando en un símbolo del sistema de PowerShell con privilegios elevados.

```powershell
Start-ScheduledTask -TaskPath \Microsoft\Windows\HGSServer -TaskName 
AttestationSignerCertRenewalTask
```

Como alternativa, puede ejecutar manualmente la tarea programada abriendo **programador de tareas** (taskschd. msc), navegando a **programador de tareas Library > Microsoft > Windows > HGSServer** y ejecutando la tarea denominada **AttestationSignerCertRenewalTask**.

## <a name="switching-attestation-modes"></a>Cambiar los modos de atestación

Si cambia HGS del modo TPM al modo Active Directory, o viceversa con el cmdlet [set-HgsServer](https://technet.microsoft.com/library/mt652180.aspx) , los nodos del clúster de HGS pueden tardar hasta 10 minutos en comenzar a aplicar el nuevo modo de atestación.
Este es el comportamiento normal.
Se recomienda no quitar las directivas que permitan a los hosts del modo de atestación anterior hasta que haya verificado que todos los hosts se atestiguan correctamente mediante el nuevo modo de atestación.

**Problema conocido al cambiar de TPM a modo de AD**

Si ha inicializado el clúster de HGS en modo TPM y después cambia al modo Active Directory, hay un problema conocido que impedirá que otros nodos del clúster de HGS cambien al nuevo modo de atestación.
Para asegurarse de que todos los servidores de HGS están aplicando el modo de atestación correcto, ejecute `Set-HgsServer -TrustActiveDirectory` **en cada nodo** del clúster de HGS.
Este problema no se aplica si va a cambiar del modo TPM al modo AD *y* el clúster se configuró originalmente en el modo ad.

Puede comprobar el modo de atestación del servidor HGS mediante la ejecución de [Get-HgsServer](https://technet.microsoft.com/library/mt652162.aspx).

## <a name="memory-dump-encryption-policies"></a>Directivas de cifrado de volcado de memoria

Si está intentando configurar las directivas de cifrado de volcado de memoria y no ve las directivas de volcado de HGS predeterminadas (HGS\_nodumps, HGS\_DumpEncryption y HGS\_DumpEncryptionKey) o el cmdlet dump Policy (Add-HgsAttestationDumpPolicy), es probable que no tenga instalada la actualización acumulativa más reciente.
Para corregir esto, [actualice el servidor HGS](guarded-fabric-manage-hgs.md#patching-hgs) a la actualización acumulativa más reciente de Windows y [Active las nuevas directivas de atestación](guarded-fabric-manage-hgs.md#updates-requiring-policy-activation).
Asegúrese de actualizar los hosts de Hyper-V a la misma actualización acumulativa antes de activar las nuevas directivas de atestación, ya que es probable que los hosts que no tengan instaladas las nuevas funcionalidades de cifrado de volcado de memoria no se realicen correctamente cuando se active la Directiva HGS.

## <a name="endorsement-key-certificate-error-messages"></a>Mensajes de error de certificado de clave de aprobación

Al registrar un host con el cmdlet [Add-HgsAttestationTpmHost](https://docs.microsoft.com/powershell/module/hgsattestation/add-hgsattestationtpmhost) , se extraen dos identificadores de TPM del archivo de identificador de plataforma proporcionado: el certificado de clave de aprobación (EKcert) y la clave de aprobación pública (EKpub).
EKcert identifica el fabricante del TPM, lo que proporciona garantías de que el TPM es auténtico y fabricado a través de la cadena de suministro normal.
EKpub identifica de forma única ese TPM específico y es una de las medidas que HGS usa para conceder a un host acceso para ejecutar máquinas virtuales blindadas.

Recibirá un error al registrar un host de TPM si se cumple alguna de las dos condiciones:
1. El archivo de identificador de plataforma **no** contiene un certificado de clave de aprobación
2. El archivo de identificador de plataforma contiene un certificado de clave de aprobación, pero ese certificado no es de **confianza** en el sistema

Algunos fabricantes de TPM no incluyen EKcerts en sus TPM.
Si sospecha que este es el caso del TPM, confirme con el OEM que los TPM no deben tener un EKcert y use la marca de `-Force` para registrar manualmente el host con HGS.
Si el TPM debe tener un EKcert pero no se encontró ninguno en el archivo de identificador de plataforma, asegúrese de que está usando una consola de PowerShell de administrador (elevado) al ejecutar [Get-PlatformIdentifier](https://docs.microsoft.com/powershell/module/platformidentifier/get-platformidentifier) en el host.

Si ha recibido el error de que el EKcert no es de confianza, asegúrese de que ha [instalado el paquete de certificados raíz de TPM de confianza](guarded-fabric-install-trusted-tpm-root-certificates.md) en cada servidor de HGS y que el certificado raíz para el proveedor de TPM se encuentra en el almacén de **TrustedTPM\_RootCA** de la máquina local. Cualquier certificado intermedio aplicable también debe instalarse en el almacén de **TrustedTPM\_IntermediateCA** en el equipo local.
Después de instalar los certificados raíz e intermedios, debería poder ejecutar `Add-HgsAttestationTpmHost` correctamente.
