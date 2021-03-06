---
ms.assetid: e5f55f3e-8d2a-4526-8d67-36a539126c22
title: Niveles de fsutil
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 6863940d69e30f4984897a7e03369a834da21d1d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376784"
---
# <a name="fsutil-tiering"></a>Niveles de fsutil
>Se aplica a: Windows Server (canal semianual), Windows Server 2016 y Windows 10

Habilita la administración de funciones de nivel de almacenamiento, como la configuración y deshabilitación de marcas y la lista de niveles.

## <a name="syntax"></a>Sintaxis

```
fsutil tiering [clearflags] <volume> <flags>
fsutil tiering [queryflags] <volume>
fsutil tiering [regionlist] <volume>
fsutil tiering [setflags] <volume> <flags>
fsutil tiering [tierlist] <volume>
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-------------|---------------|
|clearflags|Deshabilita las marcas de comportamiento de niveles de un volumen.|
|\<> de volumen|Especifica el volumen.|
|/TrNH|En el caso de los volúmenes con almacenamiento en capas, hace que la recopilación térmica se deshabilite.<br /><br>Solo se aplica a NTFS y ReFS.|
|queryflags|Consulta las marcas de comportamiento de niveles de un volumen.|
|regionlist|Enumera las regiones en capas de un volumen y sus respectivos niveles de almacenamiento.|
|SetFlags|Habilita las marcas de comportamiento de niveles de un volumen.|
|tierlist|Enumera los niveles de almacenamiento asociados a un volumen.|


### <a name="examples"></a>Ejemplos

Para consultar las marcas en el volumen C, escriba:

```
fsutil tiering clearflags C:
```

Para establecer las marcas en el volumen C, escriba:

```
fsutil tiering setflags C: /TrNH
```

Para borrar las marcas del volumen C, escriba:

```
fsutil tiering clearflags C: /TrNH
```

Para enumerar las regiones del volumen C y sus respectivas capas de almacenamiento, escriba:

```
fsutil tiering regionlist C:
```

Para enumerar los niveles del volumen C, escriba:

```
fsutil tiering tierlist C:
```



### <a name="additional-references"></a>Referencias adicionales
[Clave de sintaxis de línea de comandos](Command-Line-Syntax-Key.md)

[Fsutil](Fsutil.md)

