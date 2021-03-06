---
title: PowerShell_ise
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32c41b5b-a210-47d9-bd8c-91eb9830b4f0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65d8b9e7b7952ec64cd24e8106802cf66de693c6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372190"
---
# <a name="powershell_ise"></a>PowerShell_ise



El entorno de scripting integrado (ISE) de Windows PowerShell es una aplicación de host gráfico que permite leer, escribir, ejecutar, depurar y probar scripts y módulos en un entorno asistido por gráficos. Características clave como IntelliSense, show-Command, Snippets, finalización con tabulación, color de sintaxis, depuración visual y ayuda contextual proporcionan una experiencia de scripting enriquecida.

La herramienta **PowerShell_ISE. exe** inicia una sesión Windows PowerShell ISE. Al usar **PowerShell_ISE. exe**, puede usar sus parámetros opcionales para abrir archivos en Windows PowerShell ISE o para iniciar una sesión de Windows PowerShell ISE sin ningún perfil o con un apartamento multiproceso.

**PowerShell_ISE. exe** se incorporó en windows PowerShell 2,0 y se amplió significativamente en windows PowerShell 3,0.

## <a name="using-powershell_iseexe"></a>Usar PowerShell_ISE. exe

Puede usar **PowerShell_ISE. exe** para iniciar y finalizar una sesión de Windows PowerShell de la siguiente manera:
- Para iniciar una sesión de Windows PowerShell ISE, en una ventana del símbolo del sistema, en Windows PowerShell, o en el menú Inicio, escriba:  
  ```
  PowerShell_Ise
  ```  
- Para abrir un script (. PS1), un módulo de script (. psm1), un manifiesto de módulo (. psd1), un archivo XML o cualquier otro archivo compatible en Windows PowerShell ISE, use el siguiente formato de comando:  
  ```
  PowerShell_Ise <FilePath>
  ```  
  En Windows PowerShell 3,0, puede usar el parámetro **archivo** opcional de la siguiente manera:  
  ```
  PowerShell_Ise -File <FilePath>
  ```  
- Para iniciar una sesión de Windows PowerShell ISE sin sus perfiles de Windows PowerShell, use el parámetro **NOPROFILE** . (El parámetro **NOPROFILE** se incluye en Windows PowerShell 3,0).  
  ```
  PowerShell_Ise -NoProfile
  ```  
- Para ver el archivo de ayuda de **PowerShell_ISE. exe** en una ventana del símbolo del sistema, use el siguiente formato de comando:  
  ```
  PowerShell_Ise -help, -?, /?
  ```  
  Para obtener una lista completa de los parámetros de línea de comandos de **PowerShell_ISE. exe** , vea [about_PowerShell_Ise. exe](https://go.microsoft.com/fwlink/?LinkId=256512).

## <a name="start-windows-powershell-ise-in-other-ways"></a>Iniciar Windows PowerShell ISE de otras maneras

Para obtener información sobre otras maneras de iniciar Windows PowerShell ISE, consulte [iniciar Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=135259).

## <a name="remarks"></a>Comentarios

Windows PowerShell se ejecuta en la opción de instalación Server Core de los sistemas operativos Windows Server. Sin embargo, dado que Windows PowerShell ISE requiere una interfaz gráfica de usuario, no se ejecuta en instalaciones Server Core.

## <a name="additional-references"></a>Referencias adicionales

[about_PowerShell_Ise. exe](https://go.microsoft.com/fwlink/?LinkId=256512)
[about_PowerShell. exe](https://go.microsoft.com/fwlink/?LinkID=113439)
[Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
[scripting con Windows PowerShell](https://technet.microsoft.com/scriptcenter/dd742419) vea también