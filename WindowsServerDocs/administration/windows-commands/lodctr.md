---
title: lodctr
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a849abd-6b31-4833-bc8a-306c05eca29a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 96a2818110b766071eb83822abd34d8c0d00132d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374574"
---
# <a name="lodctr"></a>lodctr

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Permite registrar o guardar la configuración del registro y el nombre del contador de rendimiento en un archivo y designar los servicios de confianza.
## <a name="syntax"></a>Sintaxis
```
lodctr <filename> [/s:<filename>] [/r:<filename>] [/t:<servicename>]
```
### <a name="parameters"></a>Parámetros

|    Parámetro     |                                                                                                                                         Descripción                                                                                                                                          |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    <filename>    |                                                                                          Registra la configuración del nombre del contador de rendimiento y el texto explicativo que se proporciona en el archivo de inicialización FileName.                                                                                          |
|  /s: <filename>   |                                                                                                       Guarda la configuración del registro del contador de rendimiento y el texto explicativo en el archivo <filename>.                                                                                                       |
|        /r        |                                Restaura la configuración del registro de contadores y el texto explicativo de la configuración actual del registro y los archivos de rendimiento almacenados en caché relacionados con el registro.<br /><br />Esta opción solo está disponible en el sistema operativo Windows Server 2003.                                |
|  /r: <filename>   | Restaura la configuración del registro del contador de rendimiento y el texto explicativo del archivo <filename>. **ADVERTENCIA:** si usa el comando **LODCTR/r** , sobrescribirá todos los valores del registro de contadores de rendimiento y el texto explicativo y los reemplazará por la configuración definida en el archivo especificado. |
| /t: <servicename> |                                                                                                                       Indica que el servicio <servicename> es de confianza.                                                                                                                       |
|        /?        |                                                                                                                             Muestra la ayuda en el símbolo del sistema.                                                                                                                             |

## <a name="remarks"></a>Comentarios
Si la información proporcionada contiene espacios, utilice comillas alrededor del texto (por ejemplo, "<filename>").
## <a name="BKMK_Examples"></a>Example
Para guardar la configuración actual del registro de rendimiento y el texto de explicación del contador en el archivo **Perf 1. txt**:
```
lodctr /s:"perf backup1.txt"
```
## <a name="additional-references"></a>Referencias adicionales
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)

