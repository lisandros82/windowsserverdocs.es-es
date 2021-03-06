---
title: diskshadow
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e962537d-b759-4368-b6f1-e8391cf7b221
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8d9f34377473608d71ce7753972e5312d9eea0f6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377772"
---
# <a name="diskshadow"></a>diskshadow

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

DiskShadow. exe es una herramienta que expone la funcionalidad que ofrece el servicio de instantáneas de volumen \(VSS\). De forma predeterminada, DiskShadow usa un intérprete de comandos interactivo similar al de Diskraid o Diskpart. DiskShadow también incluye un modo que admite scripts.  
  
> [!NOTE]  
> La pertenencia al grupo local Administradores, o equivalente, es lo mínimo necesario para ejecutar DiskShadow.  
  
para obtener ejemplos de cómo usar los comandos de DiskShadow, vea [ejemplos](#BKMK_examples).  
  
## <a name="syntax"></a>Sintaxis  
en el modo interactivo, escriba lo siguiente en el símbolo del sistema para iniciar el intérprete de comandos de DiskShadow:  
  
```  
diskshadow  
```  
  
en modo de script, escriba lo siguiente, donde *script. txt* es un archivo de script que contiene comandos de DiskShadow:  
  
```  
diskshadow -s script.txt  
```  
  
## <a name="diskshadow-commands"></a>comandos de DiskShadow  
Puede ejecutar los siguientes comandos en el intérprete de comandos de DiskShadow o a través de un archivo de script:  
  
|Parámetro|Descripción|  
|-------|--------|  
|[set_2](set_2.md)|Establece el contexto, las opciones, el modo detallado y el archivo de metadatos para crear instantáneas.|  
|[Simular restauración](simulate-restore.md)|La implicación del escritor de pruebas en las sesiones de restauración del equipo sin emitir eventos de **restauración** o **postrestauración** a escritores.|  
|[Cargar metadatos](load-metadata.md)|Carga un archivo Metadata. cab antes de importar una instantánea transportable o carga los metadatos del escritor en el caso de una restauración.|  
|[escritor](writer.md)|comprueba que un escritor o componente está incluido o excluye un escritor o componente del procedimiento de copia de seguridad o restauración.|  
|[add_1](add_1.md)|agrega volúmenes al conjunto de volúmenes de los que se van a realizar instantáneas o agrega alias al entorno de alias.|  
|[create_1](create_1.md)|inicia el proceso de creación de instantáneas con la configuración de contexto y opciones actual.|  
|[ejec](exec.md)|ejecuta un archivo en el equipo local.|  
|[Iniciar copia de seguridad](begin-backup.md)|inicia una sesión de copia de seguridad completa.|  
|[Finalizar copia de seguridad](end-backup.md)|Finaliza una sesión de copia de seguridad completa y emite un evento **Backupcomplete** con el estado de escritor adecuado, si es necesario.|  
|[Iniciar restauración](begin-restore.md)|inicia una sesión de restauración y emite un evento de **prerestauración** a escritores implicados.|  
|[Finalizar restauración](end-restore.md)|Finaliza una sesión de restauración y emite un evento **Postrestore** a escritores implicados.|  
|[determinado](reset.md)|restablece DiskShadow al estado predeterminado.|  
|[lista](list.md)|enumera escritores, instantáneas o proveedores de instantáneas registrados actualmente en el sistema.|  
|[eliminar sombras](delete-shadows.md)|elimina las instantáneas.|  
|[import](import.md)|importa una instantánea transportable de un archivo de metadatos cargado en el sistema.|  
|[mask](mask.md)|quita las instantáneas de hardware que se importaron mediante el comando de **importación** .|  
|[aprovecha](expose.md)|Expone una instantánea persistente como letra de unidad, recurso compartido o punto de montaje.|  
|[x:.](unexpose.md)|Anula la exposición de una instantánea que se expuso mediante el comando de **exposición** .|  
|[break_2](break_2.md)|Desasocia un volumen de instantáneas de VSS.|  
|[revertir](revert.md)|Revierte un volumen a una instantánea especificada.|  
|[exit_1](exit_1.md)|sale de DiskShadow.|  
  
## <a name="remarks"></a>Observaciones  
  
-   como mínimo, solo se necesitan **Agregar** y **crear** para crear una instantánea. Sin embargo, esto perderá la configuración de contexto y de opciones, será una copia de seguridad de copia y solo creará una instantánea sin ningún script de ejecución de copia de seguridad.  
  
## <a name="BKMK_examples"></a>Example  
Se trata de una secuencia de comandos de ejemplo que creará una instantánea para la copia de seguridad. Se puede guardar en el archivo como script. DSH y ejecutarse con el script de DiskShadow \/s. DSH  
  
Supongamos lo siguiente:  
  
-   Tiene un directorio existente denominado c:\\diskshadowdata.  
  
-   El volumen del sistema es C: y el volumen de datos es D:.  
  
-   Tiene un archivo backupscript. cmd en c:\\diskshadowdata.  
  
-   El archivo backupscript. cmd realizará la copia de los datos de instantáneas p: y q: en la unidad de copia de seguridad.  
  
Puede escribir estos comandos manualmente o incluirlos en el script:  
  
```  
#diskshadow script file  
set context persistent nowriters  
set metadata c:\diskshadowdata\example.cab  
set verbose on  
begin backup  
add volume c: alias Systemvolumeshadow  
add volume d: alias Datavolumeshadow  
  
create  
  
expose %Systemvolumeshadow% p:  
expose %Datavolumeshadow% q:  
exec c:\diskshadowdata\backupscript.cmd  
end backup  
#End of script  
```  
  
#### <a name="additional-references"></a>referencias adicionales  
[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)  
  

