---
title: 'ksetup: delkdc'
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d6ec389-094c-4a7b-a78b-605497ddc289
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b918f8c2fa0ec09c2aae77517a0ee2c9e77ce2dc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375141"
---
# <a name="ksetupdelkdc"></a>ksetup: delkdc



Elimina instancias de nombres de Centro de distribución de claves (KDC) para el dominio Kerberos. Para obtener ejemplos de cómo se puede usar este comando, vea [ejemplos](#BKMK_Examples).

## <a name="syntax"></a>Sintaxis

```
ksetup /delkdc <RealmName> <KDCName>
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|\<RealmName >|El nombre de dominio Kerberos se indica como un nombre DNS en mayúsculas, como CORP. CONTOSO.COM, y aparece como el dominio Kerberos predeterminado cuando se ejecuta **ksetup** . Es el dominio Kerberos desde el que está intentando eliminar el otro KDC.|
|\<KDCName >|El nombre del KDC se indica como un nombre de dominio completo que no distingue entre mayúsculas y minúsculas, como mitkdc.contoso.com.|

## <a name="remarks"></a>Observaciones

Estas asignaciones se almacenan en el registro en **HKEY_LOCAL_MACHINE \system\currentcontrolset\control\lsa\kerberos\domains**. Para quitar los datos de configuración de dominio Kerberos de varios equipos, use el complemento de plantilla de configuración de seguridad y la distribución de directivas en lugar de usar **ksetup** explícitamente en equipos individuales.

En los equipos que ejecutan Windows 2000 Server con Service Pack 1 (SP1) y versiones anteriores, el equipo debe reiniciarse antes de que se use la configuración de configuración de dominio Kerberos modificada.

Para comprobar el nombre de dominio Kerberos predeterminado del equipo, o para comprobar que este comando funcionó como se esperaba, ejecute **ksetup** en el símbolo del sistema y compruebe que el KDC que se quitó no existe en la lista.

## <a name="BKMK_Examples"></a>Example

Los requisitos de seguridad de este equipo han cambiado, por lo que debe quitarse el vínculo entre el dominio Kerberos de Windows y el dominio que no es de Windows. En primer lugar, determine qué asociación desea quitar y generar la salida de las asociaciones existentes:
```
ksetup
```
Quite la asociación mediante el comando siguiente:
```
Ksetup /delkdc CORP.CONTOSO.COM mitkdc.contoso.com
```

#### <a name="additional-references"></a>Referencias adicionales

-   [Ksetup](ksetup.md)
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)