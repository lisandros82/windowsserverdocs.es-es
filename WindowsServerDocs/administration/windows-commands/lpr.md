---
title: lpr
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afc8790b-8b52-45c4-acdf-be0ffa9da534 jpjofre
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e853933e368f181866963fdcbc1eca5b84bb8c09
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374157"
---
# <a name="lpr"></a>lpr

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Envía un archivo a un equipo o a un dispositivo de uso compartido de impresoras que ejecuta el servicio line Printer daemon (LPD) como preparación para la impresión.  

## <a name="syntax"></a>Sintaxis  
```  
lpr [-S <ServerName>] -P <printerName> [-C <BannerContent>] [-J <JobName>] [-o | "-o l"] [-x] [-d] <filename>  
```  
## <a name="parameters"></a>Parámetros  

|     Parámetro      |                                                                                                           Descripción                                                                                                           |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  -S <ServerName>   |                                    Especifica (por nombre o dirección IP) el equipo o el dispositivo de uso compartido de impresoras que hospeda la cola de impresión de LPD con el estado que desea mostrar. Obligatorio.                                    |
|  -P <printerName>  |                                                              Especifica (por nombre) la impresora para la cola de impresión con el estado que desea mostrar. Obligatorio.                                                              |
| -C <BannerContent> |                Especifica el contenido que se va a imprimir en la página de encabezado del trabajo de impresión. Si no incluye este parámetro, aparece el nombre del equipo desde el que se envió el trabajo de impresión en la página de encabezado.                 |
|    -J <JobName>    |                           Especifica el nombre del trabajo de impresión que se imprimirá en la página de encabezado. Si no incluye este parámetro, el nombre del archivo que se va a imprimir aparece en la página de encabezado.                            |
| [-o&#124; "-o l"]  | Especifica el tipo de archivo que desea imprimir. El parámetro **-o** especifica que desea imprimir un archivo de texto. El parámetro **"-o l"** especifica que desea imprimir un archivo binario (por ejemplo, un archivo PostScript). |
|         -d         |              Especifica que el archivo de datos debe enviarse antes que el archivo de control. Use este parámetro si la impresora requiere que se envíe primero el archivo de datos. Para obtener más información, consulte la documentación de la impresora.               |
|         -x         |                               Especifica que el comando **LPR** debe ser compatible con el sistema operativo Sun Microsystems (conocido como SunOS) para las versiones hasta un 4.1.4 _u1.                                |
|     <FileName>     |                                                                                      Especifica (por nombre) el archivo que se va a imprimir. Obligatorio.                                                                                      |
|         /?         |                                                                                              Muestra la ayuda en el símbolo del sistema.                                                                                               |

## <a name="remarks"></a>Comentarios  
- Para buscar el nombre de la impresora, abra la carpeta Impresoras.  
- Los parámetros **-S**, **-P**, **-C**y **-J** distinguen mayúsculas de minúsculas y deben escribirse en letras mayúsculas.  
  ## <a name="BKMK_examples"></a>Example  
  En este ejemplo se muestra cómo imprimir el archivo de texto "Document. txt" en la cola de impresión de Laserprinter1 en un host de LPD en 10.0.0.45:  
  ```  
  lpr -S 10.0.0.45 -P Laserprinter1 -o Document.txt  
  ```  
  En este ejemplo se muestra cómo imprimir el archivo de Adobe PostScript "PostScript_file. PS" en la cola de impresión de Laserprinter1 en un host de LPD en 10.0.0.45:  
  ```  
  lpr -S 10.0.0.45 -P Laserprinter1 "-o l" PostScript_file.ps  
  ```  

#### <a name="additional-references"></a>Referencias adicionales  
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)  
-   [Referencia de comandos de impresión](print-command-reference.md)  
