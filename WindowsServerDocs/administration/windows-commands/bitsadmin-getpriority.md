---
title: bitsadmin GetPriority (
description: En el tema comandos de Windows para **bitsadmin GetPriority (** se recupera la prioridad del trabajo especificado.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 0b8914f27c690aa9bb9cbf30430b3edf55f2eb92
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381429"
---
# <a name="bitsadmin-getpriority"></a>bitsadmin GetPriority (

Recupera la prioridad del trabajo especificado.

## <a name="syntax"></a>Sintaxis

```
bitsadmin /GetPriority <Job>
```

## <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|Trabajo|El nombre para mostrar del trabajo o el GUID|

## <a name="remarks"></a>Comentarios

La prioridad es **Foreground**, **High**, **normal**, **Low**o **Unknown**.

## <a name="BKMK_examples"></a>Example

En el ejemplo siguiente se recupera la prioridad del trabajo denominado *myDownloadJob*.
```
C:\>bitsadmin /GetPriority myDownloadJob
```

#### <a name="additional-references"></a>Referencias adicionales

[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)
