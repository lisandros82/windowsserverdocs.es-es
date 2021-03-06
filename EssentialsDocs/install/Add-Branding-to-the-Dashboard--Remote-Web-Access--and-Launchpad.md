---
title: Agregar personalizaciones de marca al Panel, el acceso web remoto y Launchpad
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 04/10/2014
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 166262f8-b2a5-4b1c-a4a7-a141e1c54f10
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 02088b169e44cdcf87385425e1949232ffa408a6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59823506"
---
# <a name="add-branding-to-the-dashboard-remote-web-access-and-launchpad"></a>Agregar personalizaciones de marca al Panel, el acceso web remoto y Launchpad

>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_Branding"></a> Agregar personalización de marca al panel, acceso Web remoto y Launchpad  
 Para agregar marcas, añada más entradas al registro. Todas las entradas de personalización de marca del Registro del sistema operativo se encuentran en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OEM.  
  
 Toda la personalización de marca conjunta debe cumplir los siguientes requisitos de logotipo:  
  
-   El logotipo de Windows Server Essentials debe tener una anchura mínima de **170 píxeles**, mantener la relación de aspecto correcta, con **96 PPP**.  
  
#### <a name="to-add-branding-by-changing-the-registry"></a>Para cambiar la personalización de marca en el registro  
  
1.  En el servidor, mueva el ratón a la esquina superior derecha de la pantalla y haga clic en **Buscar**.  
  
2.  En el cuadro de búsqueda, escriba **regedit**y después haga clic en la aplicación **Regedit** .  
  
3.  En el panel de navegación, expanda **HKEY_LOCAL_MACHINE**, **SOFTWARE**, **Microsoft** y finalmente **Windows Server**. Si la clave **OEM** no existe, siga los pasos que se indican a continuación para crearla:  
  
    1.  Haga clic con el botón secundario en **Windows Server**, en **Nuevo**y, a continuación, en **Clave**.  
  
    2.  Escriba **OEM** como nombre de la clave.  
  
4.  (Opcional) Si va a crear una entrada para un logotipo, puede crear diferentes claves para diferenciar las versiones de idioma. Por ejemplo, si tiene versiones en inglés y en alemán de su logotipo, puede crear una clave en-us y otra de-de. Ya que todos los archivos de logotipo se almacenan en la misma carpeta, deberá proporcionar instancias de archivo de imagen de logotipo con nombres únicos para cada idioma. Por ejemplo, puede crear un archivo llamado DashboardLogo_en.png y otro DashboardLogo_de.png.  
  
5.  Haga clic con el botón secundario en **OEM** o en la clave de idioma correspondiente, haga clic en **Nuevo** y, a continuación, en **Valor de cadena**.  
  

6.  Escriba el nombre de la cadena y, a continuación, presione ENTRAR. Para ver los nombres de las cadenas y los valores de los datos, consulte la tabla [Cadenas y valores del Registro](Add-Branding-to-the-Dashboard--Remote-Web-Access--and-Launchpad.md#BKMK_RegStrings).  

6.  Escriba el nombre de la cadena y, a continuación, presione ENTRAR. Para ver los nombres de las cadenas y los valores de los datos, consulte la tabla [Cadenas y valores del Registro](../install/Add-Branding-to-the-Dashboard--Remote-Web-Access--and-Launchpad.md#BKMK_RegStrings).  

  
7.  Haga clic con el botón secundario en la cadena nueva y, a continuación, haga clic en **Modificar**.  
  
8.  Introduzca el valor de la tabla asociada con el nombre de la cadena y haga clic en **Aceptar**.  
  
9. Si va a crear una entrada para una imagen de logotipo o enlaces adicionales, copie el archivo a %programFiles%\Windows Server\Bin\OEM. Si la clave RemoteUserPortal no existe, créela.  
  
10. Si se realizan cambios que afectan al Acceso web remoto, informe al cliente de que deberá activarlo una vez tenga acceso al servidor. Aconseje al cliente que realice las siguientes operaciones:  
  
    1.  En el Panel, haga clic en **Settings** y, a continuación, haga clic en la ficha **Acceso desde cualquier lugar**.  
  
    2.  Si el Acceso desde cualquier lugar está activado, haga clic en **Configurar** y, a continuación, desactive la casilla de Acceso web remoto en la página **Elegir las características de Acceso desde cualquier lugar que desea habilitar** del Asistente para Configurar el acceso desde cualquier lugar.  
  
    3.  Haga clic en **configurar**.  
  
###  <a name="BKMK_RegStrings"></a> En la tabla siguiente se muestra la ubicación que afectan a la personalización de marca de cambios en el registro, el nombre de cadena y el valor de datos.  
  
### <a name="registry-strings-and-values"></a>Cadenas y valores del registro  
  
|Ubicación de la personalización de marca|Descripción|Nombre de la cadena|Valor de los datos|  
|--------------------------|-----------------|-----------------|----------------|  
|Logotipo del Panel|Agrega la imagen de logotipo al Panel. El logotipo del Panel debe estar en formato .png y el tamaño no debe superar los 350 píxeles de ancho por 38 de alto.<br /><br /> **Importante:** Para complementar la personalización de marca del Panel con su logotipo, debe editar la ilustración del mosaico que se proporciona en el DVD del OPK e incorporar el logotipo de su empresa a la imagen siguiendo los requisitos de espacio en blanco correspondientes. Para obtener más información consulte el mosaico de ejemplo que se proporciona.|DashboardLogo|Nombre del archivo de imagen del logotipo|  
|DashboardClientLogo|Agrega la imagen del logotipo a la pantalla de inicio de sesión de cliente del panel.|DashboardClientLogo|Nombre del archivo de imagen del logotipo|  
|Imagen de fondo del sitio web|Cambia la imagen de fondo que aparece en la página de inicio de sesión de acceso web remoto. Las resoluciones típicas son las siguientes:<br /><br /> -la resolución de 1024 x 768 píxeles rellenará de forma precisa la página de inicio de sesión<br /><br /> -800 x resolución 600 píxeles estará centrada en la página y aparecen con un borde negro<br /><br /> -la resolución de 1280 x 720 píxeles estará centrada y los píxeles que superen los 1024 x 768 no aparecerán.|LogonBackground|Nombre del archivo de imagen de fondo|  
|Título del sitio web|Reemplaza el título del sitio acceso Web remoto de Windows Server Essentials a un título que elija.|WebsiteName|Nuevo título del sitio de Acceso web remoto|  
|Logotipo del sitio web|Cambia el logotipo predeterminado del sitio de Acceso web remoto. El tamaño esperado del logotipo es de 32 píxeles por 32 píxeles. Si el logotipo es más pequeño o más grande, se ampliará o reducirá para que coincida con estas dimensiones|WebsiteLogo|Nombre del archivo de imagen del logotipo|  
|Logotipo del sitio web anexo|El logotipo de su asociado aparecerá inmediatamente debajo del logotipo de Microsoft que aparece en el sitio de Acceso web remoto. El tamaño esperado del logotipo es de 200 píxeles de alto por 50 píxeles de ancho. Si el tamaño de su logotipo es mayor, se reducirá para ajustarlo pero se mantendrá la relación de aspecto original. Si el logotipo es más pequeño, se centrará en el espacio de 200 por 50 píxeles y no se cambiarán ni el relación de aspecto ni la relación de aspecto.|OEMLogo|Nombre del archivo de imagen del logotipo|  

| Vínculos en la página de inicio de sesión y la página principal del sitio Web | Añade enlaces a la página de inicio de sesión y la página principal del sitio acceso Web remoto. Debe copiar el .xml que contiene la información del enlace en %programFiles%\Windows Server\Bin\OEM. En el ejemplo siguiente se muestra el formato del archivo .xml:<br /><br /> < OemLinks\><br /> < LogonLinks\><br /> < nombre de vínculo\=LogonLinkName ><br /> <Text\>LogonLinkDescription</Text\><br /> <Url\>LogonLinkURL</Url\><br /> <Icon\>LinkIcon</Icon\><br /> < / link\><br /> < / LogonLinks\><br /> <HomepageLinks\><br /> < nombre de vínculo\=HomepageLinkName ><br /> <Text\>HomepageLinkDescription</Text\><br /> <Url\>HomepageLinkURL</Url\><br /> < / link\><br /> </HomepageLinks\><br /> < / OemLinks\>| LinksXML | Hacer referencia a la [elementos de LinksXML](Add-Branding-to-the-Dashboard--Remote-Web-Access--and-Launchpad.md#BKMK_Links) tabla para obtener una lista de los elementos y descripciones. |  

| Vínculos en la página de inicio de sesión y la página principal del sitio Web | Añade enlaces a la página de inicio de sesión y la página principal del sitio acceso Web remoto. Debe copiar el .xml que contiene la información del enlace en %programFiles%\Windows Server\Bin\OEM. En el ejemplo siguiente se muestra el formato del archivo .xml:<br /><br /> < OemLinks\><br /> < LogonLinks\><br /> < nombre de vínculo\=LogonLinkName ><br /> <Text\>LogonLinkDescription</Text\><br /> <Url\>LogonLinkURL</Url\><br /> <Icon\>LinkIcon</Icon\><br /> < / link\><br /> < / LogonLinks\><br /> <HomepageLinks\><br /> < nombre de vínculo\=HomepageLinkName ><br /> <Text\>HomepageLinkDescription</Text\><br /> <Url\>HomepageLinkURL</Url\><br /> < / link\><br /> </HomepageLinks\><br /> < / OemLinks\>| LinksXML | Hacer referencia a la [elementos de LinksXML](../install/Add-Branding-to-the-Dashboard--Remote-Web-Access--and-Launchpad.md#BKMK_Links) tabla para obtener una lista de los elementos y descripciones. |  

| Logotipo de LaunchPad | Agrega la imagen de logotipo al Launchpad. El logotipo de Launchpad debe estar en formato .png y debe no más alto que 64 píxeles. | LaunchpadLogo | Nombre del archivo de imagen de logotipo |  
  
###  <a name="BKMK_Links"></a> En la tabla siguiente enumera y describe los elementos de nombre de la cadena de LinksXML.  
  
### <a name="linksxml-elements"></a>Elementos de LinksXML  
  
|Elemento de LinksXML|Descripción|  
|----------------------|-----------------|  
|**LogonLinks**|  
|LogonLinkName|El nombre del enlace de inicio de sesión.|  
|LogonLinkDescription|El texto del enlace de la página de inicio de sesión.|  
|LogonLinkURL|La dirección URL que enlaza con la página de inicio de sesión.|  
|LinkIcon|El nombre del archivo de icono del enlace de inicio de sesión. El archivo debe encontrarse en la misma carpeta que el archivo .xml. Las imágenes de icono deben ser de 16x16 píxeles y estar en formato .png. Si no proporciona un LinkIcon, se utilizará el icono de vínculo predeterminado.|  
|**HomepageLinks**|  
|HomepageLinkName|El nombre del enlace de la página de inicio.|  
|HomepageLinkDescription|El texto que aparece como el enlace de la página de inicio.|  
|HomepageLinkURL|La dirección URL que enlaza a la página de inicio.|  
|HomepageLinkIcon|El nombre del archivo de icono del enlace de la página de inicio. El archivo debe encontrarse en la misma carpeta que el archivo .xml. Las imágenes de HomepageLinkIcon deben ser de 16x16 píxeles y estar en formato .png. Si no proporciona un HomepageLinkIcon, se utilizará el icono de vínculo de página de inicio predeterminado.|  
  
## <a name="see-also"></a>Vea también  

 [Crear y personalizar la imagen](Creating-and-Customizing-the-Image.md)   
 [Personalizaciones adicionales](Additional-Customizations.md)   
 [Preparar la imagen para la implementación](Preparing-the-Image-for-Deployment.md)   
 [Probar la experiencia del cliente](Testing-the-Customer-Experience.md)

 [Crear y personalizar la imagen](../install/Creating-and-Customizing-the-Image.md)   
 [Personalizaciones adicionales](../install/Additional-Customizations.md)   
 [Preparar la imagen para la implementación](../install/Preparing-the-Image-for-Deployment.md)   
 [Probar la experiencia del cliente](../install/Testing-the-Customer-Experience.md)

