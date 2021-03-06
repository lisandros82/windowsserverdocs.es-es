---
title: Compilar medios de restauración de cliente multilingüe
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fdbc016-d464-43cb-bd75-8a63e61588a2
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 1ad934d297c3092050bd6adbb6bb0f50d1ec6f36
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879876"
---
# <a name="build-multi-language-client-restore-media"></a>Compilar medios de restauración de cliente multilingüe

>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

> [!NOTE]
>  En primer lugar debe crear una imagen de Windows multilingüe tal y como se describe en el [Tutorial: Creación de imágenes de Windows multilingües](https://technet.microsoft.com/library/jj126995) antes de agregar el paquete de idioma de Windows Server Essentials a install.wim.  
  
 Al generar el DVD de instalación de servidor multilingüe, se instalarán los paquetes de idioma para install.wim de Windows Server. Los recursos localizados para el asistente de restauración se instalarán como parte del paquete de idioma.  
  
### <a name="to-build-a-multi-language-client-restore-media"></a>Para generar un medio de restauración de cliente multilingüe  
  
1.  Monte install.wim en c:\mount; llamamos la carpeta c:\mount\Archivos de programa\Windows Server\bin\ClientRestore como raíz del medio de restauración de cliente: [RestoreMediaRoot] abajo:  
  
    ```  
    dism /mount-wim /wimfile:install.wim /index:1 /mountdir:c:\mount  
    ```  
  
2.  Monte el archivo WIM de restauración de cliente en [RestoreMediaRoot]\Sources\Boot.wim (Los mismos pasos deben realizarse también para boot_x86.wim). Esta línea de comandos es:  
  
    ```  
    dism /mount-wim /wimfile:boot.wim /index:1 /mountdir:c:\mountRestore  
    ```  
  
3.  Agregue el paquete WinPE-Setup.cab al medio de restauración ejecutando:  
  
    ```  
    dism /image:c:\mountRestore /add-package /packagepath:WinPE-Setup.cab  
    ```  
  
4.  Utilice el Bloc de notas para editar c:\mountRestore\windows\system32\winpeshl.ini y complete el archivo con el contenido siguiente:  
  
    ```  
    [LaunchApp]  
    AppPath = %SYSTEMDRIVE%\sources\SelectLanguage.exe  
    ```  
  
5.  Agregue paquetes de idioma al medio de restauración. La agregación de paquetes de idioma se puede realizar ejecutando el comando siguiente:  
  
    ```  
    dism /image:c:\mountRestore /add-package /packagepath:[language pack path]  
    ```  
  
     Se deben agregar los siguientes paquetes de idioma:  
  
    1.  Paquete de idioma WinPE (lp.cab)  
  
    2.  Paquete de idioma WinPE-Setup (WinPE-Setup_[lang].cab; por ejemplo, WinPE-Setup_en-us.cab)  
  
    3.  Para las fuentes de idiomas asiáticos como zh-cn, zh-tw, zh-hk, ko-kr y ja-jp, es necesario instalar paquetes de fuentes adicionales (winpe-fontsupport-[lang].cab, por ejemplo: winpe-fontsupport-zh-cn.cab)  
  
6.  Genere un nuevo archivo Lang.ini ejecutando:  
  
    ```  
    dism /image:c:\mountRestore /Gen-LangINI /distribution:mount  
    ```  
  
7.  Confirme y desmonte la imagen ejecutando:  
  
    ```  
    dism /unmount-wim /mountdir:c:\mountRestore /commit  
    ```  
  
8.  Repita del paso 2 al paso 7 para [RestoreMediaroot]\Sources\Boot_x86.wim.  
  
9. Confirme y desmonte la imagen ejecutando:  
  
    ```  
    dism /unmount-wim /mountdir:c:\mount /commit  
    ```  
  
## <a name="see-also"></a>Vea también  

 [Crear y personalizar la imagen](Creating-and-Customizing-the-Image.md)   
 [Personalizaciones adicionales](Additional-Customizations.md)   
 [Preparar la imagen para la implementación](Preparing-the-Image-for-Deployment.md)   
 [Probar la experiencia del cliente](Testing-the-Customer-Experience.md)

 [Crear y personalizar la imagen](../install/Creating-and-Customizing-the-Image.md)   
 [Personalizaciones adicionales](../install/Additional-Customizations.md)   
 [Preparar la imagen para la implementación](../install/Preparing-the-Image-for-Deployment.md)   
 [Probar la experiencia del cliente](../install/Testing-the-Customer-Experience.md)

