---
title: tzutil
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcf6e007-c9b6-4df5-83c5-ed7b4b1b5913
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 347254bd5a00a8bfb4a80f20d518f1e0e8b593bf
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392304"
---
# <a name="tzutil"></a>tzutil

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Muestra la utilidad de zona horaria de Windows. 
## <a name="syntax"></a>Sintaxis
```
tzutil [/?] [/g] [/s <timeZoneID>[_dstoff]] [/l]
```
### <a name="parameters"></a>Parámetros
|Parámetro|Descripción|
|-------|--------|
|/?|Muestra la ayuda en el símbolo del sistema.|
|/g|Muestra el ID. de zona horaria actual.|
|/s \<timeZoneID > [_dstoff]|Establece la zona horaria actual mediante el identificador de zona horaria especificado. El sufijo **_dstoff** deshabilita los ajustes del horario de verano de la zona horaria (si procede).|
|/l|enumera todos los ID. de zona horaria y nombres para mostrar válidos. La salida será:<br /><br />-   \<nombre para Mostrar ><br />-   \<ID. de zona horaria >|

## <a name="remarks"></a>Observaciones
Un código de salida de **0** indica que el comando se completó correctamente.

## <a name="BKMK_Examples"></a>Example
Para mostrar el ID. de zona horaria actual, escriba:
```
tzutil /g
```
Para establecer la zona horaria actual en hora estándar del Pacífico, escriba:
```
tzutil /s Pacific Standard time
```
Para establecer la zona horaria actual en hora estándar del Pacífico y deshabilitar los ajustes del horario de verano, escriba:
```
tzutil /s Pacific Standard time_dstoff
```
## <a name="additional-references"></a>referencias adicionales
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)

