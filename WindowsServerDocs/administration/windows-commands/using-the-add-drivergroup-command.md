---
title: Con el comando add-DriverGroup
description: 'Tema de los comandos de Windows para ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a92fe8f-03f9-462a-b99e-f23275259807
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 322a9a671f90bf56f6357289f7727c142a0145cc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825096"
---
# <a name="using-the-add-drivergroup-command"></a>Con el comando add-DriverGroup

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Agrega un grupo de controladores al servidor.
Para obtener ejemplos de cómo se puede utilizar este comando, consulte [ejemplos](#BKMK_examples).
## <a name="syntax"></a>Sintaxis
```
wdsutil /add-DriverGroup /DriverGroup:<Group Name>\n\
[/Server:<Server name>] [/Enabled:{Yes | No}] [/Applicability:{Matched | All}] [/Filtertype:<Filter type> /Policy:{Include | Exclude} /Value:<Value> [/Value:<Value> ...]]
```
## <a name="parameters"></a>Parámetros
|Parámetro|Descripción|
|-------|--------|
|/DriverGroup:<Group Name>|Especifica el nombre del nuevo grupo de controladores.|
|/ Server:<Server name>|Especifica el nombre del servidor. Esto puede ser el nombre NetBIOS o el FQDN. Si no se especifica ningún nombre de servidor, se usa el servidor local.|
|/ Habilitado: {Sí &#124; n}|Habilita o deshabilita el paquete.|
|/ Aplicabilidad: {Matched &#124; todas}|Especifica qué paquetes se instalan si se cumplen los criterios de filtro. **Coincidir** significa instala sólo los paquetes de controladores que coincidan con un hardware de cliente s. **Todos los** significa instala todos los paquetes a los clientes independientemente de su hardware.|
|/Filtertype:<Filtertype>|Especifica el tipo de filtro que se agregará al grupo. Puede especificar varios tipos de filtro en un solo comando. Cada tipo de filtro debe ir seguido por **/Policy** y al menos un **/valor**. <Filtertype> Puede ser uno de los siguientes:<br /><br />**BiosVendor**<br /><br />**BIOSVersion**<br /><br />**Chassistype**<br /><br />**Fabricante**<br /><br />**Uuid**<br /><br />**Versión del SO**<br /><br />**Osedition**<br /><br />**OsLanguage**<br /><br />Para obtener información acerca de cómo obtener los valores para todos los demás tipos de filtro, vea [los filtros de grupo de controladores](https://go.microsoft.com/fwlink/?LinkID=155158) (https://go.microsoft.com/fwlink/?LinkID=155158).|
|[/ Directiva: {incluyen &#124; excluir}]|Especifica la directiva debe establecerse en el filtro. Si **/Policy** está establecido en **Include**, pueden instalar los controladores de este grupo de equipos cliente que coinciden con el filtro. Si **/Policy** está establecido en **excluir**, a continuación, los equipos cliente que coinciden con el filtro no se permiten para instalar los controladores de este grupo.|
|[/ Valor:<Value>]|Especifica el valor de cliente que se corresponde con **/Filtertype**. Puede especificar varios valores para un tipo único. Consulte la siguiente lista de valores válidos para ciertos tipos de filtro. Los atributos siguientes son para **Chassistype**. Para obtener información acerca de cómo obtener los valores para todos los demás tipos de filtro, vea [los filtros de grupo de controladores](https://go.microsoft.com/fwlink/?LinkID=155158) (https://go.microsoft.com/fwlink/?LinkID=155158).<br /><br />**Otros**<br /><br />**UnknownChassis**<br /><br />**Equipo de escritorio**<br /><br />**LowProfileDesktop**<br /><br />**PizzaBox**<br /><br />**MiniTower**<br /><br />**Tower**<br /><br />**Portable**<br /><br />**Laptop**<br /><br />**Notebook**<br /><br />**Handheld**<br /><br />**DockingStation**<br /><br />**AllInOne**<br /><br />**SubNotebook**<br /><br />**SpaceSaving**<br /><br />**LunchBox**<br /><br />**MainSystemChassis**<br /><br />**ExpansionChassis**<br /><br />**SubChassis**<br /><br />**BusExpansionChassis**<br /><br />**PeripheralChassis**<br /><br />**StoraeChassis**<br /><br />**RackmountChassis**<br /><br />**SealedCasecomputer**<br /><br />**MultiSystemChassis**<br /><br />**compactPci**<br /><br />**AdvancedTca**|
## <a name="BKMK_examples"></a>Ejemplos
Para agregar un grupo de controladores, escriba uno de los siguientes:
```
wdsutil /add-DriverGroup /DriverGroup:printerdrivers /Enabled:Yes
```
```
wdsutil /add-DriverGroup /DriverGroup:printerdrivers /Applicability:All /Filtertype:Manufacturer /Policy:Include /Value:Name1 /Filtertype:Chassistype /Policy:Exclude /Value:Tower /Value:MiniTower
```
#### <a name="additional-references"></a>Referencias adicionales
[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)
[con el comando add-DriverGroupPackage](using-the-add-drivergrouppackage-command.md)
[con el comando add-DriverGroupPackages](using-the-add-drivergrouppackages-command.md) 
 [ Con el comando add-DriverGroupFilter](using-the-add-drivergroupfilter-command.md)