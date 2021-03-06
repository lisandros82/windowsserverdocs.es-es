---
title: color
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5b67131-d196-45ec-a3f9-b5d9f091fd86
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed792e4626897945e688f1c54767d7680ade6d99
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379240"
---
# <a name="color"></a>color



Cambia los colores de primer plano y de fondo de la ventana del símbolo del sistema para la sesión actual. Si se usa sin parámetros, el **color** restaura los colores de primer plano y de fondo de la ventana del símbolo del sistema predeterminado.

Para obtener ejemplos de cómo utilizar este comando, consulte [Ejemplos](#BKMK_examples).

## <a name="syntax"></a>Sintaxis

```
color [[<B>]<F>]
```

## <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|\<B >|Especifica el color de fondo.|
|\<F >|Especifica el color de primer plano.|
|/?|Muestra la ayuda en el símbolo del sistema.|

## <a name="remarks"></a>Comentarios

-   En la tabla siguiente se enumera los dígitos hexadecimales válidos que puede usar como valores para *B* y *F*.

|Valor|Color|
|-----|-----|
|0|Negro|
|1|Azul|
|2|Verde|
|3|Aguamarina|
|4|Roja|
|5|Ponen|
|6|Amarillo|
|7|Blanco|
|8|Gris|
|9|Azul claro|
|A|Verde claro|
|B|Aguamarina claro|
|C|Rojo claro|
|D|Púrpura claro|
|E|Amarillo claro|
|F|Blanco brillante|
    
-   No use caracteres de espacio entre *B* y *F*.
-   Si especifica un solo dígito hexadecimal, el color correspondiente se utiliza como color de primer plano y el color de fondo se establece en el color predeterminado.
-   Para establecer el color predeterminado de la ventana del símbolo del sistema, haga clic en la esquina superior izquierda de la ventana del símbolo del sistema, haga clic en **valores predeterminados**, haga clic en la pestaña **colores** y, a continuación, haga clic en los colores que desee utilizar para el **texto de pantalla** y el fondo de la **pantalla.** .
-   Si *B* y *F* son iguales, el comando **color** establece ERRORLEVEL en 1 y no se realiza ningún cambio en el color de primer plano o de fondo.

## <a name="BKMK_examples"></a>Example

Para cambiar el color de fondo de la ventana del símbolo del sistema a gris y el color de primer plano a rojo, escriba:
```
color 84
```
Para cambiar el color de primer plano de la ventana del símbolo del sistema a amarillo claro, escriba:
```
color e
```

> [!NOTE]
> En este ejemplo, el fondo se establece en el color predeterminado porque solo se especifica un dígito hexadecimal.

#### <a name="additional-references"></a>Referencias adicionales

[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)
