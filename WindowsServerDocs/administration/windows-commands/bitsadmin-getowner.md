---
title: bitsadmin getowner
description: 'Temas de comandos de Windows para **bitsadmin GetOwner** : recupera el propietario del trabajo especificado.'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5203f84c-a879-4f31-ae3e-7ea74bd63ca5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ab8151ba8b1379c101aa037504ae2021ff0df62f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381451"
---
# <a name="bitsadmin-getowner"></a>bitsadmin getowner

Muestra el nombre para mostrar o el GUID del propietario del trabajo especificado.

## <a name="syntax"></a>Sintaxis

```
bitsadmin /GetOwner <Job>
```

## <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|Trabajo|El nombre para mostrar del trabajo o el GUID|

## <a name="BKMK_examples"></a>Example

En el ejemplo siguiente se muestra el propietario del trabajo denominado *myDownloadJob*.
```
C:\>bitsadmin /GetOwner myDownloadJob
```

#### <a name="additional-references"></a>Referencias adicionales

[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)