---
title: Actualizar controladores de dominio a Windows Server 2016
description: En este documento se describe cómo actualizar de Windows Server 2012 R2 a Windows Server 2016
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: cbb947c17219d4fe2f6694f0e44e379fc8671e76
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401932"
---
# <a name="upgrade-domain-controllers-to-windows-server-2016"></a>Actualizar controladores de dominio a Windows Server 2016

Se aplica a: Windows Server

En este tema se proporciona información general sobre Active Directory Domain Services en Windows Server 2016 y se explica el proceso para actualizar controladores de dominio de Windows Server 2012 o Windows Server 2012 R2.

## <a name="pre-requisites"></a>Requisitos previos

La manera recomendada de actualizar un dominio es promover controladores de dominio que ejecuten versiones más recientes de Windows Server y disminuir de nivel los controladores de dominio más antiguos según sea necesario. Ese método es preferible a actualizar el sistema operativo de un controlador de dominios existente. En esta lista se describen los pasos generales a seguir antes de promover un controlador de dominio que ejecute una versión más reciente de Windows Server:

1. Confirme que el servidor de destino reúne los requisitos del sistema.
1. Compruebe la compatibilidad de aplicaciones.
1. Revisar recomendaciones para cambiar a Windows Server 2016
1. Compruebe la configuración de seguridad. Para obtener más información, vea [características desusadas y cambios de comportamiento relacionados con la AD DS en Windows Server 2016](../../../get-started/deprecated-features.md).
1. Compruebe la conectividad del servidor de destino desde el equipo donde tenga intención de realizar la instalación.
1. Compruebe la disponibilidad de los roles de maestro de operaciones necesarios:
   - Para instalar el primer controlador de dominio que ejecuta Windows Server 2016 en un dominio y bosque existente, el equipo en el que se ejecuta la instalación necesita conectividad con el **maestro de esquema** para poder ejecutar Adprep/ForestPrep y el maestro de infraestructura para ejecutar adprep/ preparar.
   - Para instalar el primer controlador de dominio en un dominio en el que el esquema del bosque ya está extendido, solo necesita conectividad con el **maestro de infraestructura**.
   - Para instalar o quitar un dominio en un bosque existente, necesita conectividad con el **maestro de nomenclatura de dominios**.
   - Cualquier instalación de controlador de dominio también requiere conectividad con el **maestro RID.**
   - Si va a instalar el primer controlador de dominio de solo lectura en un bosque existente, necesita conectividad con el **maestro de infraestructura** para cada partición del directorio de aplicaciones, también conocido como contexto de nomenclatura que no es de dominio o NDNC).

### <a name="installation-steps-and-required-administrative-levels"></a>Pasos de instalación y niveles administrativos necesarios

En la tabla siguiente se proporciona un resumen de los pasos de actualización y los requisitos de permisos para realizar estos pasos.

|Acción de instalación|Requisitos de credenciales|
| ----- | ----- |
|Instalar un bosque nuevo|Administrador local en el servidor de destino|
|Instalar un dominio nuevo en un bosque existente|Administradores de empresas|
|Instalar más controladores de dominio en un dominio existente|Admins. del dominio|
|Ejecutar adprep /forestprep|Administradores de esquema, Administradores de empresas y Admins. del dominio|
|Ejecutar adprep /domainprep|Admins. del dominio|
|Ejecutar adprep /domainprep /gpprep|Admins. del dominio|
|Ejecutar adprep /rodcprep|Administradores de empresas|

Para obtener información adicional sobre las nuevas características de Windows Server 2016, vea [novedades de Windows server 2016](../../../get-started/what-s-new-in-windows-server-2016.md).

## <a name="supported-in-place-upgrade-paths"></a>Rutas de acceso de actualización en contexto admitidas

Los controladores de dominio que ejecutan versiones de 64 bits de Windows Server 2012 o Windows Server 2012 R2 se pueden actualizar a Windows Server 2016. Solo se admiten las actualizaciones de versión de 64, ya que Windows Server 2016 solo se incluye en una versión de 64 bits.

|Si ejecuta esta edición:|Puede realizar una actualización a estas ediciones:|
| ----- | ----- |
|Windows Server 2012 Standard|Windows Server 2016 Standard o Datacenter|
|Windows Server 2012 Datacenter|Windows Server 2016 Datacenter|
|Windows Server 2012 R2 Standard|Windows Server 2016 Standard o Datacenter|
|Windows Server 2012 R2 Datacenter|Windows Server 2016 Datacenter|
|Windows Server 2012 R2 Essentials|Windows Server 2016 Essentials|
|Windows Storage Server 2012 Standard|Windows Storage Server 2016 Standard|
|Windows Storage Server 2012 Workgroup|Windows Storage Server 2016 Workgroup|
|Windows Storage Server 2012 R2 Standard|Windows Storage Server 2016 Standard|
|Windows Storage Server 2012 R2 Workgroup|Windows Storage Server 2016 Workgroup|

Para obtener más información sobre las rutas de actualización admitidas, vea [rutas de actualización admitidas](../../../get-started/supported-upgrade-paths.md) .

## <a name="adprep-and-domainprep"></a>Adprep y DomainPrep

Si va a realizar una actualización en contexto de un controlador de dominio existente al sistema operativo Windows Server 2016, tendrá que ejecutar Adprep/ForestPrep y Adprep/DomainPrep manualmente.  Adprep/ForestPrep solo debe ejecutarse una vez en el bosque.  Adprep/DomainPrep debe ejecutarse una vez en cada dominio en el que tenga controladores de dominio que esté actualizando a Windows Server 2016.

Si va a promocionar un nuevo servidor de Windows Server 2016, no es necesario que los ejecute manualmente.  Se integran en las experiencias de PowerShell y Administrador del servidor.

Para obtener más información acerca de la ejecución de Adprep, vea [Ejecutar Adprep](https://technet.microsoft.com/library/dd464018.aspx)

## <a name="functional-level-features-and-requirements"></a>Requisitos y características de niveles funcionales

Windows Server 2016 requiere un nivel funcional de bosque de Windows Server 2003. Es decir, para poder agregar un controlador de dominio que ejecute Windows Server 2016 a un bosque de Active Directory existente, el nivel funcional del bosque debe ser Windows Server 2003 o posterior. Si el bosque contiene controladores de dominio que ejecutan Windows Server 2003 o posterior, pero el nivel funcional de dicho bosque sigue siendo Windows 2000, la instalación se bloqueará igualmente.

Los controladores de dominio de Windows 2000 deben quitarse antes de agregar controladores de dominio de Windows Server 2016 al bosque. En este caso, considere el siguiente flujo de trabajo:

1. Instale controladores de dominio que ejecuten Windows Server 2003 o posterior. Estos controladores de dominio se pueden implementar en una versión de evaluación de Windows Server. Este paso también requiere la ejecución de adprep. exe para la versión del sistema operativo como requisito previo.
1. Quite los controladores de dominio de Windows 2000. En concreto, quite a la fuerza o disminuya de nivel correctamente los controladores de dominio de Windows Server 2000 del dominio y utilice Usuarios y equipos de Active Directory para quitar las cuentas de controlador de dominio correspondientes a todos los controladores de dominio eliminados.
1. Eleve el nivel funcional del bosque a Windows Server 2003 o posterior.
1. Instale los controladores de dominio que ejecutan Windows Server 2016.
1. Quite los controladores de dominio que ejecuten versiones anteriores de Windows Server.

### <a name="rolling-back-functional-levels"></a>Revertir niveles funcionales

Después de establecer el nivel funcional del bosque (FFL) en un determinado valor, no se puede revertir o bajar el nivel funcional del bosque, con las siguientes excepciones:

- Si va a actualizar desde Windows Server 2012 R2 FFL, puede volver a bajar a Windows Server 2012 R2.
- Si va a actualizar desde Windows Server 2008 R2 FFL, puede volver a bajar a Windows Server 2008 R2.

Después de establecer el nivel funcional del dominio en un determinado valor, no se puede revertir o bajar el nivel funcional del dominio, con las siguientes excepciones:

- Cuando eleva el nivel funcional del dominio a Windows Server 2016 y el nivel funcional del bosque es Windows Server 2012 o inferior, tiene la opción de revertir el nivel funcional del dominio a Windows Server 2012 o Windows Server 2012 R2.

Para obtener más información sobre las características disponibles a niveles funcionales inferiores, consulte [Descripción de los niveles funcionales de Servicios de dominio de Active Directory (AD DS)](../active-directory-functional-levels.md).

## <a name="ad-ds-interoperability-with-other-server-roles-and-windows-operating-systems"></a>Interoperabilidad de AD DS con otros roles del servidor y sistemas operativos Windows

AD DS no es compatible con los siguientes sistemas operativos:

- Windows MultiPoint Server
- Windows Server 2016 Essentials

AD DS no se puede instalar en un servidor donde también se ejecuten los siguientes roles o servicios del servidor:

- Microsoft Hyper-V Server 2016
- Agente de conexión a Escritorio remoto

## <a name="administration-of-windows-server-2016-servers"></a>Administración de servidores de Windows Server 2016

Use el Herramientas de administración remota del servidor para Windows 10 para administrar controladores de dominio y otros servidores que ejecutan Windows Server 2016. Puede ejecutar el Herramientas de administración remota del servidor de Windows Server 2016 en un equipo que ejecute Windows 10.

## <a name="step-by-step-for-upgrading-to-windows-server-2016"></a>Paso a paso para la actualización a Windows Server 2016

A continuación se facilita un ejemplo sencillo de la actualización del bosque de Contoso de Windows Server 2012 R2 a Windows Server 2016.

![Actualizar versión](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade1.png)

1. Únase al nuevo Windows Server 2016 en el bosque. Reinicie cuando se le solicite.

   ![Actualizar versión](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade2.png)

1. Inicie sesión en el nuevo Windows Server 2016 con una cuenta de administrador de dominio.
1. En **Administrador del servidor**, en **Agregar roles y características**, instale **Active Directory Domain Services** en el nuevo Windows Server 2016. Se ejecutará automáticamente Adprep en el bosque y el dominio 2012 R2.

   ![Actualizar versión](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade3.png)

1. En **Administrador del servidor**, haga clic en el triángulo amarillo y, en la lista desplegable, haga clic en **promover el servidor a controlador de dominio**.

   ![Actualizar versión](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade4.png)

1. En la pantalla **configuración de implementación** , seleccione **Agregar un controlador de dominio a un bosque existente** y haga clic en siguiente.

   ![Actualizar versión](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade5.png)

1. En la pantalla **Opciones del controlador de dominio** , escriba la contraseña de **modo de restauración de servicios de directorio (DSRM)** y haga clic en siguiente.
1. En el resto de las pantallas, haga clic en **siguiente**.
1. En la pantalla de **comprobación de requisitos previos** , haga clic en **instalar**. Una vez completado el reinicio, puede volver a iniciar sesión.
1. En el servidor de Windows Server 2012 R2, en **Administrador del servidor**, en herramientas, seleccione **módulo de Active Directory para Windows PowerShell**.

   ![Actualizar versión](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade6.png)

1. En las ventanas de PowerShell, use Move-ADDirectoryServerOperationMasterRole para trasladar los roles FSMO. Puede escribir el nombre de cada-OperationMasterRole o utilizar números para especificar los roles. Para obtener más información [, consulte Move-ADDirectoryServerOperationMasterRole](https://technet.microsoft.com/library/hh852302.aspx)

    ``` powershell
    Move-ADDirectoryServerOperationMasterRole -Identity "DC-W2K16" -OperationMasterRole 0,1,2,3,4
    ```

    ![Actualizar versión](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade7.png)

1. Para comprobar que los roles se han migrado, vaya al servidor de Windows Server 2016, en **Administrador del servidor**, en **herramientas**, seleccione **módulo de Active Directory para Windows PowerShell**. Use los `Get-ADDomain` cmdlets y `Get-ADForest` para ver los titulares de la función FSMO.

    ![Actualizar versión](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade8.png)

    ![Actualizar versión](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade9.png)

1. Disminuir de nivel y quitar el controlador de dominio de Windows Server 2012 R2. Para obtener información acerca de cómo disminuir de nivel un controlador de dominio, consulte [degradar controladores de dominio y dominios](../../ad-ds/deploy/Demoting-Domain-Controllers-and-Domains--Level-200-.md)
1. Una vez que el servidor se degrada y se quita, puede elevar el nivel funcional del bosque y los niveles funcionales de dominio a Windows Server 2016.

## <a name="next-steps"></a>Pasos siguientes

- [Novedades sobre la instalación y eliminación de Active Directory Domain Services (AD DS)](../../ad-ds/deploy/What-s-New-in-Active-Directory-Domain-Services-Installation-and-Removal.md)
- [Active Directory Domain Services &#40;nivel de instalación 100&#41;](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md)
- [Niveles funcionales de Windows Server 2016](../../ad-ds/Windows-Server-2016-Functional-Levels.md)  
