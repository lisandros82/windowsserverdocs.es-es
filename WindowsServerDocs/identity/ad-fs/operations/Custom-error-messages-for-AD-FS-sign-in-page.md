---
ms.assetid: 1df78c2a-5054-4b54-8310-c48ea62e6e0b
title: Mensajes de error personalizados para la página de inicio de sesión de AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 98cd1dd6763886a9b9f63ab6eca1c52094424284
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407554"
---
# <a name="custom-error-messages-for-ad-fs-sign-in-page"></a>Mensajes de error personalizados para la página de inicio de sesión de AD FS  


Puedes configurar mensajes de error personalizados que se adapten a la organización. En la siguiente ilustración, se muestra la descripción de una página de error personalizada y un mensaje de error genérico. Use los siguientes cmdlets de Windows PowerShell para personalizar los mensajes de error.  
  
![error personalizado](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom3.png)  
  
## <a name="customize-the-error-page-description"></a>Personalización de la descripción de la página de error  
Para personalizar la descripción de la página de error, use el siguiente cmdlet de Windows PowerShell y la siguiente sintaxis.  
  

`Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description" ` 

  
## <a name="customize-a-generic-error-message"></a>Personalización de un mensaje de error genérico  
Para personalizar el mensaje de error genérico, utilice el siguiente cmdlet de Windows PowerShell y la siguiente sintaxis.  
  
 
`Set-AdfsGlobalWebContent -ErrorPageGenericErrorMessage "This is a generic error message.  Contact Contoso IT for assistance." ` 

  
## <a name="customize-an-authorization-error-message"></a>Personalización de un mensaje de error de autorización  
Para personalizar el mensaje de error de autorización, use el siguiente cmdlet de Windows PowerShell y la siguiente sintaxis.  
  

    Set-AdfsGlobalWebContent -ErrorPageAuthorizationErrorMessage "You have received an Authorization error.  Contact Contoso IT for assistance."  

  
## <a name="customize-a-device-authentication-error-message"></a>Personalización de un mensaje de error de autenticación de dispositivo  
Para personalizar el mensaje de error de autenticación del dispositivo, use el siguiente cmdlet de Windows PowerShell y la siguiente sintaxis.  
  
 
`Set-AdfsGlobalWebContent -ErrorPageDeviceAuthenticationErrorMessage "Your device is not authorized.  Contact Contoso IT for assistance."`  
 
  
## <a name="customize-a-support-email-error-message"></a>Personalización de un mensaje de error con envío de correo electrónico de soporte  
Puede configurar una dirección de correo electrónico de soporte en AD FS. Si está configurado, AD FS muestra automáticamente un vínculo para que los usuarios finales envíen por correo electrónico los detalles del error.  
  
Para personalizar el mensaje de error del correo electrónico de soporte técnico, use el siguiente cmdlet de Windows PowerShell y la siguiente sintaxis.  
  

    Set-AdfsGlobalWebContent -ErrorPageSupportEmail  "admin@contoso.com"  

  
## <a name="customize-a-relying-party-authorization-message"></a>Personalización de un mensaje de autorización de usuario de confianza  
Puede configurar un mensaje de error de autorización de usuario de confianza en AD FS.  
  
Para personalizar el mensaje de error del usuario de confianza, use el siguiente cmdlet de Windows PowerShell y la siguiente sintaxis.  

    Set-AdfsRelyingPartyWebContent -Name fedpassive -ErrorPageAuthorizationErrorMessage "<p> You need to be a member of Security Auditors to access this site. Click <A href='http://accessrequest/'>here</A> for more information.</p>“  


## <a name="additional-references"></a>Referencias adicionales 
[Personalización de inicio de sesión de AD FS usuario](AD-FS-user-sign-in-customization.md)    
