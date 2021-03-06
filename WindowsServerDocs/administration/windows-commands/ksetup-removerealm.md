---
title: 'ksetup: removerealm'
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 11858d8a24d4f125c83b3e4092ac48f336a9ef0b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374948"
---
# <a name="ksetupremoverealm"></a>ksetup: removerealm



Elimina toda la información del dominio Kerberos especificado del registro. Para obtener ejemplos de cómo se puede usar este comando, vea [ejemplos](#BKMK_Examples).

## <a name="syntax"></a>Sintaxis

```
ksetup /removerealm <RealmName>
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|\<RealmName >|El nombre de dominio Kerberos se indica como un nombre DNS en mayúsculas, como CORP. CONTOSO.COM, y aparece como el dominio Kerberos predeterminado cuando se ejecuta **ksetup** .|

## <a name="remarks"></a>Observaciones

El nombre de dominio Kerberos se almacena en dos lugares del registro: **HKEY_LOCAL_MACHINE \system\controlset001** y **\CurrentControlSet\Control\Lsa\Kerberos**.

No se puede quitar el nombre de dominio Kerberos predeterminado del controlador de dominio, ya que se restablecerá la información de DNS y se podrá quitar el controlador de dominio.

## <a name="BKMK_Examples"></a>Example

Se estableció erróneamente el nombre de dominio Kerberos al escribir ". COM" en el equipo local en CORP. Senda. TIMADO
```
ksetup /setrealm CORP.CONTOSO.CON
```
Quite el nombre de dominio Kerberos erróneo del equipo local:
```
ksetup /removerealm CORP.CONTOSO.CON
```
Compruebe la eliminación ejecutando **ksetup** y revise la salida.

#### <a name="additional-references"></a>Referencias adicionales

-   [Ksetup](ksetup.md)
-   [Ksetup:setrealm](ksetup-setrealm.md)
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)