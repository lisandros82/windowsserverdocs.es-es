---
title: 'ksetup: addrealmflags'
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80ca1e16-8871-494b-b9be-6bc9d63de860
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 543fcb8105d21020cc9a4ab5e5e8c1eca14a358b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375168"
---
# <a name="ksetupaddrealmflags"></a>ksetup: addrealmflags



Agrega marcas de dominio Kerberos adicionales al dominio Kerberos especificado. Para obtener ejemplos de cómo se puede usar este comando, vea [ejemplos](#BKMK_Examples).

## <a name="syntax"></a>Sintaxis

```
ksetup /addrealmflags <RealmName> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|Nombre de dominio Kerberos|El nombre de dominio Kerberos se indica como un nombre DNS en mayúsculas, como CORP. CONTOSO.COM.|

## <a name="remarks"></a>Observaciones

Las marcas de dominio Kerberos especifican características adicionales de un dominio Kerberos que no se basa en el sistema operativo Windows Server. Los equipos que ejecutan Windows Server 2003, Windows Server 2008 o Windows Server 2008 R2 pueden usar un servidor Kerberos para administrar la autenticación en lugar de usar un dominio que ejecute un sistema operativo Windows Server, y estos sistemas participarán en un Dominio Kerberos. Esta entrada establece las características del dominio Kerberos. En la tabla siguiente se describe cada uno de ellos.

|Valor|Marca de dominio Kerberos|Descripción|
|-----|----------|-----------|
|0xF|Todos|Se establecen todas las marcas de dominio Kerberos.|
|0x00|Ninguno|No se establecen marcas de dominio Kerberos y no se habilitan características adicionales.|
|0x01|SendAddress|La dirección IP se incluirá en los vales de concesión de vales.|
|0x02|TcpSupported|El protocolo de control de transmisión (TCP) y el protocolo de datagramas de usuario (UDP) se admiten en este dominio Kerberos.|
|0x04|Delegado|Todos los usuarios de este dominio Kerberos son de confianza para la delegación.|
|0x08|NcSupported|Este dominio Kerberos admite la canonización de nombres, que permite los estándares de nomenclatura DNS y dominio Kerberos.|
|0x80|RC4|Este dominio Kerberos es compatible con el cifrado RC4 para habilitar la confianza entre dominios, lo que permite el uso de TLS.|

Las marcas de dominio Kerberos se almacenan en el registro en **HKEY_LOCAL_MACHINE \system\currentcontrolset\control\lsa\kerberos\domains\\** <em>realm-name</em>. Esta entrada no existe en el registro de forma predeterminada. Puede usar el comando [Ksetup: addrealmflags](ksetup-addrealmflags.md) para rellenar el registro.

Puede ver qué marcas de dominio están disponibles y establecerse mediante la visualización de la salida de ksetup o ksetup/dumpstate.

## <a name="BKMK_Examples"></a>Example

Enumere las marcas de dominio Kerberos disponibles para el dominio Kerberos CONTOSO:
```
Ksetup /listrealmflags
```
Establezca dos marcas en el dominio Kerberos de CONTOSO:
```
ksetup /setrealmflags CONTOSO ncsupported delegate
```
Agregue una marca más que no esté actualmente en el conjunto:
```
ksetup /addrealmflags CONTOSO SendAddress
```
Ejecute el comando **ksetup** para comprobar que la marca de dominio Kerberos está establecida visualizando la salida y buscando **marcas de dominio Kerberos =** .

#### <a name="additional-references"></a>Referencias adicionales

-   [Ksetup:listrealmflags](ksetup-listrealmflags.md)
-   [Ksetup:setrealmflags](ksetup-setrealmflags.md)
-   [Ksetup:delrealmflags](ksetup-delrealmflags.md)
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)