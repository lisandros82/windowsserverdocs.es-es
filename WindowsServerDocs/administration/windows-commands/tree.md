---
title: tree
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 345d3192-401e-4a3b-a8ac-36a85c7be79d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 22875e63526dc3465021c9aa990f6cea388b81e4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385620"
---
# <a name="tree"></a>tree



Muestra gráficamente la estructura de directorios de una ruta de acceso o del disco de una unidad.

Para obtener ejemplos de cómo utilizar este comando, consulte [Ejemplos](#BKMK_examples).

## <a name="syntax"></a>Sintaxis

```
tree [<Drive>:][<Path>] [/f] [/a]
```

## <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|> de \<unidad:|Especifica la unidad que contiene el disco para el que desea mostrar la estructura de directorios.|
|\<ruta de acceso >|Especifica el directorio para el que desea mostrar la estructura de directorios.|
|/f|Muestra los nombres de los archivos de cada directorio.|
|/a|Especifica que el **árbol** va a utilizar caracteres de texto en lugar de caracteres gráficos para mostrar las líneas que vinculan a los subdirectorios.|
|/?|Muestra la ayuda en el símbolo del sistema.|

## <a name="remarks"></a>Observaciones

La estructura que muestra el **árbol** depende de los parámetros que se especifiquen en el símbolo del sistema. Si no especifica una unidad o una ruta de acceso, **árbol** muestra la estructura de árbol que empieza con el directorio actual de la unidad actual.

## <a name="BKMK_examples"></a>Example

Para mostrar los nombres de todos los subdirectorios del disco en la unidad actual, escriba:
```
tree \
```
Para mostrar una pantalla a la vez, los archivos de todos los directorios de la unidad C, escriba:
```
tree c:\ /f | more 
```
Para imprimir una lista de todos los directorios de la unidad C, escriba:
```
tree c:\ /f  prn 
```

#### <a name="additional-references"></a>Referencias adicionales

[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)