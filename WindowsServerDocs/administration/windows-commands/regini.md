---
title: regini
description: Obtenga información acerca de cómo modificar el registro desde el símbolo del sistema o mediante un script.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ff18dc3-5bd8-400a-b311-fd73a3267e8c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 482a0a256c537965a9960a896fa323aa8b8fac42
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371636"
---
# <a name="regini"></a>regini

Modifica el registro desde la línea de comandos o un script, y aplica los cambios predefinidos en uno o varios archivos de texto. Puede crear, modificar o eliminar claves del registro, además de modificar los permisos en las claves del registro.

Para obtener información detallada sobre el formato y el contenido del archivo de script de texto que Regini. exe utiliza para realizar cambios en el registro, vea [Cómo cambiar los valores o los permisos del registro desde una línea de comandos o un script](https://support.microsoft.com/help/264584/how-to-change-registry-values-or-permissions-from-a-command-line-or-a).

## <a name="syntax"></a>Sintaxis

```
regini [-m \\machinename | -h hivefile hiveroot][-i n] [-o outputWidth][-b] textFiles...
```

### <a name="parameters"></a>Parámetros

| Parámetro | Descripción |

|-m \< \\ ComputerName\\>|Especifica el nombre del equipo remoto con un registro que se va a modificar. Use el  **\\ formato\\COMPUTERNAME**.|
|---------------------|-|
|-h \<hivefile hiveroot >|Especifica el subárbol del registro local que se va a modificar. Debe especificar el nombre del archivo de Hive y la raíz del subárbol en el formato **hivefile hiveroot**.|
|\<-n >|Especifica el nivel de sangría que se va a utilizar para indicar la estructura de árbol de las claves del registro en el resultado del comando. La herramienta **Regdmp. exe** (que obtiene los permisos actuales de una clave del registro en formato binario) utiliza la sangría en múltiplos de cuatro, por lo que el valor predeterminado es **4**.|
|-o \<outputwidth >|Especifica el ancho del resultado del comando, en caracteres. Si el resultado aparecerá en la ventana de comandos, el valor predeterminado es el ancho de la ventana. Si el resultado se dirige a un archivo, el valor predeterminado es **240** caracteres.|
|-b|Especifica que la salida de **Regini. exe** es compatible con versiones anteriores de **Regini. exe**. Vea la sección Comentarios para obtener más información.|
|textfiles|Especifica el nombre de uno o más archivos de texto que contienen datos del registro. Se puede enumerar cualquier número de archivos de texto ANSI o Unicode.|

## <a name="remarks"></a>Comentarios

Las siguientes directrices se aplican principalmente al contenido de los archivos de texto que contienen los datos del registro que se aplican mediante **Regini. exe**.
-   Use el punto y coma como un carácter de comentario de final de línea. Debe ser el primer carácter que no esté en blanco en una línea.
-   Use la barra diagonal inversa para indicar la continuación de una línea. El comando omitirá todos los caracteres de la barra diagonal inversa hasta el primer carácter que no esté en blanco de la línea siguiente, pero no lo incluya. Si incluye más de un espacio antes de la barra diagonal inversa, se reemplaza por un solo espacio.
-   Use caracteres de tabulación para controlar la sangría. Esta sangría indica la estructura de árbol de las claves del registro; sin embargo, estos caracteres se convierten en un solo espacio, independientemente de su posición.

#### <a name="additional-references"></a>Referencias adicionales

-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)