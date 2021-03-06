---
title: Usar el comando New-MulticastTransmission
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1f1dc46-dd50-4eb9-9f72-cf0e5d71bd3d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8a6893d34e8f1242966d644159823277cf71a0c0
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401990"
---
# <a name="using-the-new-multicasttransmission-command"></a>Usar el comando New-MulticastTransmission

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

crea una nueva transmisión de multidifusión para una imagen. Este comando es equivalente a crear una transmisión mediante el complemento MMC de servicios de implementación de Windows (haga clic con el botón secundario en el nodo **transmisiones** de multidifusión y, a continuación, haga clic en **crear transmisión por multidifusión**). Debe utilizar este comando cuando tenga instalado el servicio de rol servidor de implementación y el servicio de función servidor de transporte (que es la instalación predeterminada). Si solo tiene instalado el servicio de función servidor de transporte, use [el comando New-namespace](using-the-new-namespace-command.md).
## <a name="syntax"></a>Sintaxis
para las transmisiones de imágenes de instalación:
```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      mediatype:Install
       mediaGroup:<Image Group>]
        [/Filename:<File name>]
```
para las transmisiones de imagen de arranque (solo se admiten en Windows Server 2008 R2):
```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      mediatype:Boot
        /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
## <a name="parameters"></a>Parámetros
|Parámetro|Descripción|
|-------|--------|
medios: <Image name>|Especifica el nombre de la imagen que se va a transmitir mediante multidifusión.|
|[/Server:<Server name>]|Especifica el nombre del servidor. Puede ser el nombre NetBIOS o el nombre de dominio completo (FQDN). Si no se especifica ningún nombre de servidor, se utilizará el servidor local.|
|/FriendlyName: <Friendly name>|Especifica el nombre descriptivo de la transmisión.|
|/Description<Description>]|Especifica la descripción de la transmisión.|
mediatype: {boot&#124;install}|Especifica el tipo de imagen que se va a transmitir mediante multidifusión. Nota: el **arranque** solo se admite para Windows Server 2008 R2.|
|\mediaGroup: <Image group name>]|Especifica el grupo de imágenes que contiene la imagen. Si no se especifica ningún nombre de grupo de imágenes y solo existe un grupo de imágenes en el servidor, se utiliza ese grupo de imágenes. Si existe más de un grupo de imágenes en el servidor, debe usar esta opción para especificar el nombre del grupo de imágenes.|
|[/Filename:<File name>]|Especifica el nombre de archivo. Si la imagen de origen no se puede identificar de forma única mediante el nombre, debe usar esta opción para especificar el nombre de archivo.|
|/Transmissiontype: {autocast &#124; ScheduledCast}|Especifica si la transmisión se inicia automáticamente (autocast) o se basa en los criterios de inicio especificados (ScheduledCast).<br /><br /><ul><li>**Conversión automática**. Este tipo de transmisión indica que tan pronto como un cliente aplicable solicita una imagen de instalación, comienza una transmisión por multidifusión de la imagen seleccionada. A medida que otros clientes solicitan la misma imagen, se unen a la transmisión que ya se ha iniciado.</li><li>**Difusión programada**. Este tipo de transmisión establece los criterios de inicio de la transmisión según el número de clientes que solicitan una imagen o un día y hora específicos. Puede especificar las siguientes opciones:<br /><br /><ul><li>[/Time: <time>]: establece el tiempo que la transmisión debe comenzar con el siguiente formato: AAAA/MM/DD: HH: mm.</li><li>[/Clients: <Number of clients>]: establece el número mínimo de clientes que hay que esperar antes de que se inicie la transmisión.</li></ul></li></ul>|
|/Architecture: {x86 &#124; ia64 &#124; x64}|Especifica la arquitectura de la imagen de arranque que se va a transmitir mediante multidifusión. Dado que es posible tener el mismo nombre para las imágenes de arranque de distintas arquitecturas, debe especificar la arquitectura para asegurarse de que se usa la imagen correcta.|
|[/Filename:<File name>]|Especifica el nombre de archivo. Si la imagen de origen no se puede identificar de forma única por nombre, debe especificar el nombre de archivo.|
## <a name="BKMK_examples"></a>Example
Para crear una transmisión de difusión automática de una imagen de arranque en Windows Server 2008 R2, escriba:
```
wdsutil /New-MulticastTransmission /FriendlyName:"WDS Boot Transmission"
/Image:"X64 Boot Imagemediatype:Boot /Architecture:x64 /Transmissiontype:AutoCast
```
Para crear una transmisión de difusión automática de una imagen de instalación, escriba:
```
wdsutil /New-MulticastTransmission /FriendlyName:"WDS AutoCast Transmission"
/Image:"Vista with Officemediatype:Install /Transmissiontype:AutoCast
```
Para crear una transmisión de difusión programada de una imagen de instalación, escriba:
```
wdsutil /New-MulticastTransmission /FriendlyName:"WDS SchedCast Transmission" /Server:MyWDSServemedia:"Vista with Officemediatype:Install 
/Transmissiontype:ScheduledCast /time:"2006/11/20:17:00" /Clients:100
```
#### <a name="additional-references"></a>Referencias adicionales
[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)
[con el comando get-AllMulticastTransmissions](using-the-get-allmulticasttransmissions-command.md)
[mediante el comando Get-MulticastTransmission](using-the-get-multicasttransmission-command.md)
[mediante el comando Remove-MulticastTransmission](using-the-remove-multicasttransmission-command.md)
[ Subcomando: Start-MulticastTransmission](subcommand-start-multicasttransmission.md)
