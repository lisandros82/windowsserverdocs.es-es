---
title: autochk
description: 'Temas de comandos de Windows para **Autochk** : se ejecuta cuando se inicia el equipo y antes de Windows Server a partir de la comprobación de la integridad lógica de un sistema de archivos.'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8787e6a3-f023-4ea5-b2d1-61c6876d8aff
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 76e54d14879cefd4661a1ca7f1c3b8ee7ec58de2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382355"
---
# <a name="autochk"></a>autochk



Se ejecuta cuando se inicia el equipo y antes de Windows Server® 2008 R2 a partir de la comprobación de la integridad lógica de un sistema de archivos.

**Autochk. exe** es una versión de **CHKDSK** que solo se ejecuta en discos NTFS y solo antes de que se inicie Windows Server 2008 R2. **Autochk** no se puede ejecutar directamente desde la línea de comandos. En su lugar, **Autochk** se ejecuta en las siguientes situaciones:
-   Si intenta ejecutar **CHKDSK** en el volumen de arranque
-   Si **CHKDSK** no puede obtener el uso exclusivo del volumen
-   Si el volumen está marcado como sucio

## <a name="remarks"></a>Comentarios

> -   [!WARNING]
>     La herramienta de línea de comandos **Autochk** no se puede ejecutar directamente desde la línea de comandos. En su lugar, use la herramienta de línea de comandos **chkntfs** para configurar la forma en que se desea que **Autochk** se ejecute en el inicio.
> -   Puede usar **chkntfs** con el parámetro **/x** para impedir que **Autochk** se ejecute en un volumen específico o en varios volúmenes.
> -   Use la herramienta de línea de comandos **chkntfs. exe** con el parámetro **/t** para cambiar el retraso de AUTOCHK desde 0 segundos hasta 3 días (259.200 segundos). Sin embargo, un retraso largo significa que el equipo no se inicia hasta que transcurre el tiempo o hasta que se presiona una tecla para cancelar el **Autochk**.

#### <a name="additional-references"></a>Referencias adicionales

[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)

[Emprende](chkdsk.md)

[Chkntfs](chkntfs.md)

[Solución de problemas de discos y sistemas de archivos](https://go.microsoft.com/fwlink/?LinkId=4527)