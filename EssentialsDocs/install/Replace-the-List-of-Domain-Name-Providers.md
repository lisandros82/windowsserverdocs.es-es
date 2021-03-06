---
title: Sustituir la lista de proveedores de nombre de dominio
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 104d0412-2d77-4cd4-99f7-65a885522850
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: c087cdad4d2c047db40b370673fb04b232036b61
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433495"
---
# <a name="replace-the-list-of-domain-name-providers"></a>Sustituir la lista de proveedores de nombre de dominio

>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Para sustituir la lista de proveedores de nombres de dominio que aparece en el Asistente de configuración de nombre de dominio, siga estos pasos:  


-   [Cree los archivos de servicio referencia](Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)  

-   [Agregar una entrada al registro en el equipo de referencia](Replace-the-List-of-Domain-Name-Providers.md#BKMK_AddRegistry)  

-   [Cree los archivos de servicio referencia](../install/Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)  

-   [Agregar una entrada al registro en el equipo de referencia](../install/Replace-the-List-of-Domain-Name-Providers.md#BKMK_AddRegistry)  


###  <a name="BKMK_ReferralFiles"></a> Cree los archivos de servicio referencia  
 La Herramienta de administración de servicios de referencia crea una conjunto de archivos que se utilizan para definir la lista de proveedores de nombres de dominio que aparece en el Asistente de configuración de nombre de dominio. Se crea un archivo con formato XML por cada región del mundo con información de los proveedores de nombres de dominio que haya especificado en la herramienta. Deberá copiar los archivos creados por la herramienta en una carpeta accesible mediante una conexión segura (HTTPS) que administre en Internet.  

##### <a name="to-create-the-referral-files"></a>Para crear los archivos de referencia  

1.  Abra la Herramienta de administración de servicios de referencia.  

2.  Haz clic en **Agregar**.  

3.  En el nombre de dominio, Agregar un proveedor de nombres de dominio, introduciendo el nombre del mismo.  

4.  Agregue los dominios de nivel superior que sean compatibles con el proveedor de nombres de dominio. Para ello, haga clic en **Agregar**, introduzca el identificador de dominio de nivel superior y a continuación seleccione las regiones compatibles. Puede seleccionar**Todas las regiones**.  

5.  Introduzca la descripción del proveedor de nombres de dominio.  

6.  Agregue las direcciones URL de todos los sitios web asociados con el proveedor de nombres de dominio.  

7.  Para agregar un logotipo al proveedor de nombres de dominio, haga clic en **Cambiar logotipo**.  

8.  Haga clic en **Guardar**.  

9. Repita los pasos 2 al 8 con todos los proveedor de nombres de dominio que desee agregar a la lista del asistente.  

10. Después de agregar todos los proveedores de nombres de dominio, seleccione la carpeta donde se encuentren los archivos de referencia. Tenga en cuenta que la carpeta que seleccione debe ser accesible a través de un enlace HTTPS.  

11. Haga clic en **Generar archivos en el sistema de archivos**.  

###  <a name="BKMK_AddRegistry"></a> Agregar una entrada al registro en el equipo de referencia  
 Deberá agregar una entrada de registro para especificar la ubicación donde el sistema operativo pueda encontrar los archivos de servicio.  

##### <a name="to-add-a-key-to-the-registry"></a>Para agregar una clave al registro  

1.  En el equipo de referencia. haga clic en **Inicio**, escriba **regedit**y después presione **Entrar**.  

2.  En el panel izquierdo, expanda **HKEY_LOCAL_MACHINE**, **SOFTWARE**, **Microsoft**, **Windows Server**, **Domain Managers** y finalmente **Providers**.  

3.  Haga clic con el botón derecho en la clave **E423C85D-6B1F-4583-95E0-449D8263BAC4** y a continuación haga clic en **Valor de cadena**.  

4.  Escriba **ReferralServerHttpsUri** como nombre de la cadena y después presione **Entrar**.  

5.  Haga clic con el botón secundario sobre la nueva cadena **ReferralServerHttpsUri** en el panel derecho y a continuación haga clic en **Modificar**.  


6.  Escriba la dirección URL HTTPS que utilice para acceder a los archivos de referencia creados en [Create the referral service files](Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)y, a continuación, haga clic en **Aceptar**.  

6.  Escriba la dirección URL HTTPS que utilice para acceder a los archivos de referencia creados en [Create the referral service files](../install/Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)y, a continuación, haga clic en **Aceptar**.  


~~~
> [!IMPORTANT]
>  A slash (/) is required at the end of the URL.  
~~~

###  <a name="BKMK_ReplaceDomainNameProviders"></a> Problemas de estado del nombre de dominio  
 Si un asociado agrega proveedores de nombre de dominio y usa una interfaz de programación de aplicaciones (API) en el SDK de Windows Server Essentials para establecer los Estados Unknown, Failed y CertificateRequestNotSubmitted al certificado, el cliente recibe una incorrecta resultado de mensaje y la configuración. Esto se debe a que los casos los tratan las excepciones, en lugar de devolver un estado.  

 Los siguientes estados de dominio son errores y deben notificarse como tales:  

- Failed  

- PendingCustomerInterventionRequired  

- PurchaseFailed  

- DomainNotFound  

- InRenewalCustomerInterventionRequired  

- RenewalFailed  

  Los siguientes estados de dominio son correctos y deben notificarse como tales:  

- Ready  

- Pending  

- InRenewal  

## <a name="see-also"></a>Vea también  

 [Crear y personalizar la imagen](Creating-and-Customizing-the-Image.md)   
 [Personalizaciones adicionales](Additional-Customizations.md)   
 [Preparar la imagen para la implementación](Preparing-the-Image-for-Deployment.md)   
 [Probar la experiencia del cliente](Testing-the-Customer-Experience.md)

 [Crear y personalizar la imagen](../install/Creating-and-Customizing-the-Image.md)   
 [Personalizaciones adicionales](../install/Additional-Customizations.md)   
 [Preparar la imagen para la implementación](../install/Preparing-the-Image-for-Deployment.md)   
 [Probar la experiencia del cliente](../install/Testing-the-Customer-Experience.md)

