---
title: Subcomando set-DriverPackage
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11804bb6-ca29-4461-8c63-5131748cd742
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65751cf6e03baa87c7734b318a26111652bee0a1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370823"
---
# <a name="subcommand-set-driverpackage"></a>Subcomando: set-DriverPackage



Cambia el nombre o habilita o deshabilita un paquete de controladores en un servidor.

## <a name="syntax"></a>Sintaxis

```
WDSUTIL /Set-DriverPackage [/Server:<Server name>] {/DriverPackage:<Name> | /PackageId:<ID>} [/Name:<New Name>] [/Enabled:{Yes | No}
```

## <a name="parameters"></a>Parámetros

|        Parámetro         |                                                                                                                                                                                                               Descripción                                                                                                                                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server:\<nombre de servidor >] |                                                                                                                                                 Especifica el nombre del servidor. Puede ser el nombre NetBIOS o el FQDN. Si no se especifica un nombre de servidor, se utiliza el servidor local.                                                                                                                                                 |
| [/DriverPackage: nombre de\<>] |                                                                                                                                                                                       Especifica el nombre actual del paquete de controladores que se va a modificar.                                                                                                                                                                                        |
|    [/PackageId: ID. de\<>]    | Especifica el ID. de servicios de implementación de Windows del paquete de controladores. Debe especificar esta opción si el paquete de controladores no se puede identificar de forma única por nombre. Para encontrar este ID. para un paquete, haga clic en el grupo de controladores en el que se encuentra el paquete (o en el nodo **todos los paquetes** ), haga clic con el botón secundario en el paquete y, a continuación, haga clic en **propiedades**. El identificador del paquete se muestra en la pestaña **General** . Por ejemplo: {DD098D20-1850-4FC8-8E35-EA24A1BEFF5E}. |
|   [/Name:\<nuevo nombre >]    |                                                                                                                                                                                              Especifica el nuevo nombre del paquete de controladores.                                                                                                                                                                                              |
|      [/Enabled: {Yes      |                                                                                                                                                                                                                   Ninguno                                                                                                                                                                                                                    |

## <a name="BKMK_examples"></a>Example

Para cambiar la configuración de un paquete, escriba uno de los siguientes:
```
WDSUTIL /Set-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318} /Name:MyDriverPackage
```
```
WDSUTIL /Set-DriverPackage /DriverPackage:MyDriverPackage /Name:NewName /Enabled:Yes
```

#### <a name="additional-references"></a>Referencias adicionales

[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)