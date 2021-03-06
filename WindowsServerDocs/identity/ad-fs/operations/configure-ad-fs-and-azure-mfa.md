---
ms.assetid: 24c4b9bb-928a-4118-acf1-5eb06c6b08e5
title: Configuración de AD FS 2016 y Azure MFA
description: ''
ms.author: billmath
author: billmath
manager: mtillman
ms.date: 01/28/2019
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b658644d1ba7cec1b02a2a51331cd7b7152efc77
ms.sourcegitcommit: 75e611fd5de8b8aa03fc26c2a3d5dbf8211b8ce3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77145488"
---
# <a name="configure-azure-mfa-as-authentication-provider-with-ad-fs"></a>Configuración de Azure MFA como proveedor de autenticación con AD FS

Si su organización está federada con Azure AD, puede usar Azure Multi-Factor Authentication para proteger AD FS recursos, tanto en el entorno local como en la nube. Azure MFA permite eliminar contraseñas y proporcionar una manera más segura de autenticarse.  A partir de Windows Server 2016, ahora puede configurar Azure MFA para la autenticación principal o usarlo como un proveedor de autenticación adicional. 
  
A diferencia de lo que sucede con AD FS en Windows Server 2012 R2, el adaptador de Azure MFA de AD FS 2016 se integra directamente con Azure AD y no requiere un servidor de Azure MFA local.   El adaptador de Azure MFA está integrado en Windows Server 2016 y no hay necesidad de instalación adicional.


## <a name="registering-users-for-azure-mfa-with-ad-fs"></a>Registro de usuarios para Azure MFA con AD FS

AD FS no admite la prueba &#34;&#34;en línea o el registro de la información de comprobación de seguridad de Azure MFA, como el número de teléfono o la aplicación móvil. Esto significa que los usuarios deben revisarse visitando [https://account.activedirectory.windowsazure.com/Proofup.aspx](https://account.activedirectory.windowsazure.com/Proofup.aspx) antes de usar Azure MFA para autenticarse en AD FS aplicaciones. Cuando un usuario que todavía no se ha actualizado en Azure AD intenta autenticarse con Azure MFA en AD FS, recibirá un error AD FS.  Como administrador de AD FS, puede personalizar esta experiencia de error para guiar al usuario a la página proofup en su lugar.  Puede hacerlo mediante la personalización de onload. js para detectar la cadena de mensaje de error en la página de AD FS y mostrar un mensaje nuevo para guiar a los usuarios para que visiten [https://aka.ms/mfasetup](https://aka.ms/mfasetup)y vuelva a intentar la autenticación. Para obtener instrucciones detalladas, vea la página web sobre cómo personalizar el AD FS para guiar a los usuarios para que registren métodos de comprobación de MFA en este artículo.

>[!NOTE]
> Anteriormente, los usuarios debían autenticarse con MFA para registrarse (visitando [https://account.activedirectory.windowsazure.com/Proofup.aspx](https://account.activedirectory.windowsazure.com/Proofup.aspx), por ejemplo, a través del [https://aka.ms/mfasetup](https://aka.ms/mfasetup)de acceso directo).  Ahora, un usuario de AD FS que todavía no haya registrado información de comprobación de MFA&#34;puede tener acceso a la página de proofup de Azure ad s a través del acceso directo [https://aka.ms/mfasetup](https://aka.ms/mfasetup) solo con la autenticación principal (como la autenticación integrada de Windows o el nombre de usuario y la contraseña a través de las páginas web de AD FS).  Si el usuario no tiene ningún método de comprobación configurado, Azure AD realizará el registro en línea en el que el &#34;usuario ve el mensaje el administrador requiere que configure esta cuenta para realizar&#34;una comprobación de seguridad adicional y, a &#34;continuación, el usuario&#34;puede seleccionar para configurarla ahora.
> Se seguirá solicitando a los usuarios que ya tienen al menos un método de comprobación MFA configurado que proporcionen MFA al visitar la página proofup.

## <a name="recommended-deployment-topologies"></a>Topologías de implementación recomendadas

### <a name="azure-mfa-as-primary-authentication"></a>Azure MFA como autenticación principal

Hay un par de razones excelentes para usar Azure MFA como autenticación principal con AD FS:

 - Para evitar contraseñas para el inicio de sesión en Azure AD, Office 365 y otras aplicaciones de AD FS
 - Para proteger el inicio de sesión basado en contraseña requiriendo un factor adicional, como el código de verificación antes de la contraseña

Si desea usar Azure MFA como método de autenticación principal en AD FS para lograr estas ventajas, es probable que también quiera mantener la capacidad de usar Azure AD acceso condicional, incluido &#34;MFA&#34; real, solicitando factores adicionales en AD FS.

Ahora puede hacerlo configurando la opción de dominio Azure AD para realizar MFA de forma local ( &#34;estableciendo&#34; SupportsMfa en $true).  En esta configuración, se puede solicitar AD FS Azure AD para realizar la autenticación adicional o &#34;MFA&#34; real para escenarios de acceso condicional que lo requieran.  

Tal y como se describió anteriormente, los usuarios AD FS que todavía no se hayan registrado (información de comprobación de MFA configurada) deben solicitarse a través de una página de error de AD FS personalizada para visitar [https://aka.ms/mfasetup](https://aka.ms/mfasetup) para configurar la información de comprobación y, a continuación, volver a intentar AD FS inicio de sesión.  
Dado que Azure MFA como principal se considera un único factor, después de que los usuarios de la configuración inicial deban proporcionar un factor adicional para administrar o actualizar la información de comprobación en Azure AD, o para tener acceso a otros recursos que requieran MFA.

>[!NOTE]
> Con ADFS 2019, es necesario realizar una modificación en el tipo de notificación de delimitador para la Active Directory confianza del proveedor de notificaciones y modificarlo de atributos windowsaccountname a UPN. Ejecute el cmdlet de PowerShell que se proporciona a continuación. Esto no afecta al funcionamiento interno de la granja de AD FS. Es posible que observe que algunos usuarios pueden volver a solicitar las credenciales una vez que se realiza este cambio. Después de volver a iniciar sesión, los usuarios finales no verán ninguna diferencia. 

```powershell
Set-AdfsClaimsProviderTrust -AnchorClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -TargetName "Active Directory"
```

### <a name="azure-mfa-as-additional-authentication-to-office-365"></a>Azure MFA como autenticación adicional para Office 365

Anteriormente, si deseaba tener Azure MFA como método de autenticación adicional en AD FS para Office 365 u otros usuarios de confianza, la mejor opción era configurar Azure AD para la MFA compuesta, en la que se realiza la autenticación principal en el entorno local de AD FS y MFA es TR. iggered por Azure AD. Ahora, puede usar Azure MFA como autenticación adicional en AD FS cuando el valor de dominio SupportsMfa se establece en $True.  

Tal y como se describió anteriormente, los usuarios AD FS que todavía no se hayan registrado (información de comprobación de MFA configurada) deben solicitarse a través de una página de error de AD FS personalizada para visitar [https://aka.ms/mfasetup](https://aka.ms/mfasetup) para configurar la información de comprobación y, a continuación, volver a intentar AD FS inicio de sesión.  

## <a name="pre-requisites"></a>Requisitos previos

Los siguientes requisitos previos son necesarios cuando se usa Azure MFA para la autenticación con AD FS:  
  
- Una [suscripción de Azure con Azure Active Directory](https://azure.microsoft.com/pricing/free-trial/).  
- [Multi-Factor Authentication de Azure](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/) 


> [!NOTE]
> Azure AD y Azure MFA se incluyen en Azure AD Premium y en Enterprise Mobility Suite (EMS).  Si tiene alguno de estos, no necesita suscripciones individuales.

- Un entorno de Windows Server 2016 AD FS local.  
   - El servidor debe ser capaz de comunicarse con las siguientes direcciones URL a través del puerto 443.
      - https://adnotifications.windowsazure.com
      - https://login.microsoftonline.com
- El entorno local está [federado con Azure ad.](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-custom/#configuring-federation-with-ad-fs)  
- [Módulo de Azure Active Directory de Windows para Windows PowerShell](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).  
- Permisos de administrador global en la instancia de Azure AD para configurarlo mediante Azure AD PowerShell.  
- Credenciales de administrador de organización para configurar la granja de AD FS para Azure MFA.

## <a name="configure-the-ad-fs-servers"></a>Configurar los servidores de AD FS

Para completar la configuración de Azure MFA para AD FS, debe configurar cada servidor de AD FS mediante los pasos descritos. 

>[!NOTE]
>Asegúrese de que estos pasos se realizan en **todos** los servidores de AD FS de la granja. Si tiene varios servidores de AD FS en la granja, puede realizar la configuración necesaria de forma remota con Azure AD PowerShell.  

### <a name="step-1-generate-a-certificate-for-azure-mfa-on-each-ad-fs-server-using-the-new-adfsazuremfatenantcertificate-cmdlet"></a>Paso 1: generación de un certificado para Azure MFA en cada servidor de AD FS mediante el cmdlet `New-AdfsAzureMfaTenantCertificate`

Lo primero que debe hacer es generar un certificado para que lo use Azure MFA.  Esto se puede hacer mediante PowerShell.  El certificado generado se puede encontrar en el almacén de certificados de las máquinas locales y se marca con un nombre de sujeto que contiene el TenantID del directorio de Azure AD.

![AD FS y MFA](media/Configure-AD-FS-2016-and-Azure-MFA/ADFS_AzureMFA3.png)  

Tenga en cuenta que TenantID es el nombre del directorio en Azure AD.  Use el siguiente cmdlet de PowerShell para generar el nuevo certificado.  
    `$certbase64 = New-AdfsAzureMfaTenantCertificate -TenantID <tenantID>`  

![AD FS y MFA](media/Configure-AD-FS-2016-and-Azure-MFA/ADFS_AzureMFA1.PNG)  
  
### <a name="step-2-add-the-new-credentials-to-the-azure-multi-factor-auth-client-service-principal"></a>Paso 2: agregar las nuevas credenciales a la entidad de servicio de cliente de Azure multi-factor auth

Para permitir que los servidores de AD FS se comuniquen con el cliente de Azure multi-factor auth, debe agregar las credenciales a la entidad de servicio para el cliente de Azure multi-factor auth. Los certificados generados con el cmdlet `New-AdfsAzureMFaTenantCertificate` actuarán como estas credenciales. Realice lo siguiente con PowerShell para agregar las nuevas credenciales a la entidad de servicio de cliente de Azure multi-factor auth.  

> [!NOTE]
> Para completar este paso, debe conectarse a la instancia de Azure AD con PowerShell mediante `Connect-MsolService`.  En estos pasos se supone que ya se ha conectado a través de PowerShell.  Para obtener información, consulte [`Connect-MsolService`.](https://msdn.microsoft.com/library/dn194123.aspx)  

**Establecimiento del certificado como la nueva credencial en el cliente de Azure multi-factor auth**  

`New-MsolServicePrincipalCredential -AppPrincipalId 981f26a1-7f43-403b-a875-f8b09b8cd720 -Type asymmetric -Usage verify -Value $certBase64`

> [!IMPORTANT]
> Este comando debe ejecutarse en todos los servidores de AD FS de la granja.  Azure AD MFA producirá un error en los servidores que no tienen el certificado establecido como la nueva credencial en el cliente de Azure multi-factor auth.

> [!NOTE]  
> 981f26a1-7f43-403b-a875-f8b09b8cd720 es el GUID para el cliente de Azure multi-factor auth.  
  
## <a name="configure-the-ad-fs-farm"></a>Configuración de la granja de AD FS  
  
Una vez que haya completado la sección anterior en cada servidor de AD FS, establezca la información del inquilino de Azure mediante el cmdlet [set-AdfsAzureMfaTenant](https://docs.microsoft.com/powershell/module/adfs/export-adfsauthenticationproviderconfigurationdata) . Este cmdlet debe ejecutarse una sola vez para una granja de AD FS.

Abra un símbolo del sistema de PowerShell y escriba su propio *tenantId* con el cmdlet [set-AdfsAzureMfaTenant](https://docs.microsoft.com/powershell/module/adfs/export-adfsauthenticationproviderconfigurationdata) . Para los clientes que usan Microsoft Azure Government Cloud, agregue el parámetro `-Environment USGov`:

> [!NOTE]
> Debe reiniciar el servicio de AD FS en cada servidor de la granja de servidores antes de que estos cambios surtan efecto. Para un impacto mínimo, tome cada AD FS servidor fuera de la rotación de NLB de uno en uno y espere a que se vacíen todas las conexiones.

```powershell
Set-AdfsAzureMfaTenant -TenantId <tenant ID> -ClientId 981f26a1-7f43-403b-a875-f8b09b8cd720
```

![AD FS y MFA](media/Configure-AD-FS-2016-and-Azure-MFA/ADFS_AzureMFA5.png)

Windows Server sin el Service Pack más reciente no admite el parámetro `-Environment` para el cmdlet [set-AdfsAzureMfaTenant](https://docs.microsoft.com/powershell/module/adfs/export-adfsauthenticationproviderconfigurationdata) . Si usa Azure Government nube y en los pasos anteriores no se pudo configurar el inquilino de Azure debido a la falta de `-Environment` parámetro, realice los pasos siguientes para crear manualmente las entradas del registro. Omita estos pasos si el cmdlet anterior registró correctamente la información del inquilino o no está en la nube de Azure Government:

1. Abra el **Editor del registro** en el servidor de AD FS.
1. Vaya a `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ADFS`. Cree los siguientes valores de clave del registro:

    | Clave del Registro       | Valor |
    |--------------------|-----------------------------------|
    | SasUrl             | https://adnotifications.windowsazure.us/StrongAuthenticationService.svc/Connector |
    | StsUrl             | https://login.microsoftonline.us |
    | ResourceUri        | https://adnotifications.windowsazure.us/StrongAuthenticationService.svc/Connector |

1. Reinicie el servicio AD FS en cada servidor de la granja antes de que estos cambios surtan efecto. Para un impacto mínimo, tome cada AD FS servidor fuera de la rotación de NLB de uno en uno y espere a que se vacíen todas las conexiones.

Después, verá que Azure MFA está disponible como método de autenticación principal para el uso de la intranet y la extranet.

![AD FS y MFA](media/Configure-AD-FS-2016-and-Azure-MFA/ADFS_AzureMFA6.png)  

## <a name="renew-and-manage-ad-fs-azure-mfa-certificates"></a>Renovar y administrar AD FS certificados de Azure MFA

La siguiente orientación le guiará a través de la administración de los certificados de Azure MFA en los servidores de AD FS.
De forma predeterminada, al configurar AD FS con Azure MFA, los certificados generados a través del cmdlet de PowerShell de `New-AdfsAzureMfaTenantCertificate` son válidos durante 2 años.  Para determinar la proximidad de la expiración de los certificados y, a continuación, para renovar e instalar nuevos certificados, use el procedimiento siguiente.

### <a name="assess-ad-fs-azure-mfa-certificate-expiration-date"></a>Evaluación de AD FS fecha de expiración del certificado de Azure MFA

En cada servidor de AD FS, en el equipo local mi tienda, habrá un certificado autofirmado con &#34;uo = Microsoft AD FS Azure MFA&#34; en el emisor y el asunto.  Este es el certificado de Azure MFA.  Compruebe el período de validez de este certificado en cada servidor de AD FS para determinar la fecha de expiración.  

### <a name="create-new-ad-fs-azure-mfa-certificate-on-each-ad-fs-server"></a>Creación de un nuevo AD FS certificado de Azure MFA en cada servidor de AD FS

Si el período de validez de los certificados está llegando al final, inicie el proceso de renovación mediante la generación de un nuevo certificado de Azure MFA en cada servidor de AD FS. En una ventana de comandos de PowerShell, genere un nuevo certificado en cada servidor de AD FS con el siguiente cmdlet:

> [!CAUTION]
> Si el certificado ya ha expirado, no agregue el parámetro `-Renew $true` al siguiente comando. En este escenario, el certificado expirado existente se sustituye por uno nuevo en lugar de dejarse en vigor y se crea un certificado adicional.

```
PS C:\> $newcert = New-AdfsAzureMfaTenantCertificate -TenantId <tenant id such as contoso.onmicrosoft.com> -Renew $true
```

Si el certificado no ha expirado, se genera un nuevo certificado válido de 2 días en el futuro a 2 días + 2 años. Las operaciones de AD FS y Azure MFA no se ven afectadas por este cmdlet ni por el nuevo certificado. (Nota: el retraso de 2 días es intencionado y proporciona el tiempo de ejecución de los pasos siguientes para configurar el nuevo certificado en el inquilino antes de que AD FS empiece a usarlo para Azure MFA).

### <a name="configure-each-new-ad-fs-azure-mfa-certificate-in-the-azure-ad-tenant"></a>Configuración de cada nuevo AD FS certificado de Azure MFA en el inquilino de Azure AD

Con el módulo de Azure AD PowerShell, para cada nuevo certificado (en cada servidor de AD FS), actualice la configuración del inquilino de Azure AD como se indica a continuación (Nota: primero debe conectarse al inquilino mediante `Connect-MsolService` para ejecutar los siguientes comandos).

```
PS C:/> New-MsolServicePrincipalCredential -AppPrincipalId 981f26a1-7f43-403b-a875-f8b09b8cd720 -Type Asymmetric -Usage Verify -Value $newcert
```

Si el certificado anterior ya expiró, reinicie el servicio AD FS para recoger el nuevo certificado. No es necesario reiniciar el servicio AD FS si renovó un certificado antes de que expirara.

### <a name="verify-that-the-new-certificates-will-be-used-for-azure-mfa"></a>Compruebe que los nuevos certificados se usarán para Azure MFA.

Una vez que los nuevos certificados sean válidos, AD FS los recopilará y comenzará a usar cada uno de ellos para Azure MFA en cuestión de horas al día.  Una vez hecho esto, en cada servidor verá un evento registrado en el registro de eventos de AD FS admin con la siguiente información:

```
Log Name:      AD FS/Admin
Source:        AD FS
Date:          2/27/2018 7:33:31 PM
Event ID:      547
Task Category: None
Level:         Information
Keywords:      AD FS
User:          DOMAIN\adfssvc
Computer:      ADFS.domain.contoso.com
Description:
The tenant certificate for Azure MFA has been renewed.  

TenantId: contoso.onmicrosoft.com.
Old thumbprint: 7CC103D60967318A11D8C51C289EF85214D9FC63.
Old expiration date: 9/15/2019 9:43:17 PM.
New thumbprint: 8110D7415744C9D4D5A4A6309499F7B48B5F3CCF.
New expiration date: 2/27/2020 2:16:07 AM.
```

## <a name="customize-the-ad-fs-web-page-to-guide-users-to-register-mfa-verification-methods"></a>Personalizar la Página Web de AD FS para guiar a los usuarios para que registren métodos de comprobación de MFA

Use los ejemplos siguientes para personalizar las páginas web de AD FS para los usuarios que todavía no se han actualizado (información de comprobación de MFA configurada).

### <a name="find-the-error"></a>Buscar el error

En primer lugar, hay un par de mensajes de error diferentes AD FS devolverán en caso de que el usuario no tenga información de comprobación.
Si usa Azure MFA como autenticación principal, el usuario no justificado verá una página de error AD FS que contiene los siguientes mensajes:
```
    <div id="errorArea">
        <div id="openingMessage" class="groupMargin bigText">
            An error occurred
        </div>
        <div id="errorMessage" class="groupMargin">
            Authentication attempt failed. Select a different sign in option or close the web browser and sign in again. Contact your administrator for more information.
        </div>
```
Cuando se Azure AD a medida que se intenta la autenticación adicional, el usuario no probado verá una página de error de AD FS que contiene los siguientes mensajes:
```
<div id='mfaGreetingDescription' class='groupMargin'>For security reasons, we require additional information to verify your account (mahesh@jenfield.net)</div>
    <div id="errorArea">
        <div id="openingMessage" class="groupMargin bigText">
            An error occurred
        </div>
        <div id="errorMessage" class="groupMargin">
            The selected authentication method is not available for &#39;username@contoso.com&#39;. Choose another authentication method or contact your system administrator for details.
        </div>
```

### <a name="catch-the-error-and-update-the-page-text"></a>Detectar el error y actualizar el texto de la página

Para detectar el error y mostrar la guía personalizada del usuario, simplemente Anexe el código JavaScript al final del archivo onload. js que forma parte del AD FS tema Web.  Esto le permite hacer lo siguiente:
 - buscar las cadenas de error de identificación
 - proporcionar contenido web personalizado.  

> [!NOTE]
> Para obtener instrucciones generales sobre cómo personalizar el archivo onload. js, consulte el artículo [Personalización avanzada de las páginas de inicio de sesión de AD FS](advanced-customization-of-ad-fs-sign-in-pages.md).

Este es un ejemplo sencillo, tal vez desee extender:

1. Abra Windows PowerShell en el servidor de AD FS principal y cree un nuevo tema Web de AD FS mediante la ejecución del siguiente comando:
    
    ``` PowerShell
        New-AdfsWebTheme –Name ProofUp –SourceName default
    ``` 
2. A continuación, cree la carpeta y exporte el AD FS tema Web predeterminado:

    ``` PowerShell
       New-Item -Path 'c:\Theme' -ItemType Directory;Export-AdfsWebTheme –Name default –DirectoryPath c:\Theme
    ```
3. Abra el archivo C:\Theme\script\onload.js en un editor de texto.
4. Anexe el código siguiente al final del archivo onload. js
    
    ``` JavaScript
    //Custom Code
    //Customize MFA exception
    //Begin

    var domain_hint = "<YOUR_DOMAIN_NAME_HERE>";
    var mfaSecondFactorErr = "The selected authentication method is not available for";
    var mfaProofupMessage = "You will be automatically redirected in 5 seconds to set up your account for additional security verification. Once you have completed the setup, please return to the application you are attempting to access.<br><br>If you are not redirected automatically, please click <a href='{0}'>here</a>."
    var authArea = document.getElementById("authArea");
    if (authArea) {
        var errorMessage = document.getElementById("errorMessage");
        if (errorMessage) {
            if (errorMessage.innerHTML.indexOf(mfaSecondFactorErr) >= 0) {

                //Hide the error message
                var openingMessage = document.getElementById("openingMessage");
                if (openingMessage) {
                    openingMessage.style.display = 'none'
                }
                var errorDetailsLink = document.getElementById("errorDetailsLink");
                if (errorDetailsLink) {
                    errorDetailsLink.style.display = 'none'
                }

                //Provide a message and redirect to Azure AD MFA Registration Url
                var mfaRegisterUrl = "https://account.activedirectory.windowsazure.com/proofup.aspx?proofup=1&whr=" + domain_hint;
                errorMessage.innerHTML = "<br>" + mfaProofupMessage.replace("{0}", mfaRegisterUrl);
                window.setTimeout(function () { window.location.href = mfaRegisterUrl; }, 5000);
            }
        }
    }

    //End Customize MFA Exception
    //End Custom Code
    ```
    > [!IMPORTANT]
    > Debe cambiar "< YOUR_DOMAIN_NAME_HERE >"; para usar el nombre de dominio. Por ejemplo: `var domain_hint = "contoso.com";`
    
5. Guardar el archivo onload. js
6. Importe el archivo onload. js en el tema personalizado escribiendo el siguiente comando de Windows PowerShell:
    
    ``` PowerShell
    Set-AdfsWebTheme -TargetName ProofUp -AdditionalFileResource @{Uri='/adfs/portal/script/onload.js';path="c:\theme\script\onload.js"}
    ```
7. Por último, aplique el tema Web de AD FS personalizado escribiendo el siguiente comando de Windows PowerShell:
    
    ``` PowerShell
    Set-AdfsWebConfig -ActiveThemeName "ProofUp"
    ```

## <a name="next-steps"></a>Pasos siguientes

[Administración de los protocolos TLS/SSL y los conjuntos de cifrado usados por AD FS y Azure MFA](manage-ssl-protocols-in-ad-fs.md)
