---
title: mqbkup
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7bdd41c4-75ef-455f-b241-1d64a4c7acf5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 66783e0bbfe5c82971e14fd05e913d485485dc6f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373509"
---
# <a name="mqbkup"></a>mqbkup

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Realiza una copia de seguridad de los archivos de mensajes y la configuración del registro de MSMQ en un dispositivo de almacenamiento y restaura los mensajes y configuraciones almacenados previamente.   
La operación de copia de seguridad y restauración detendrá el servicio MSMQ local. Si el servicio MSMQ se inició de antemano, la utilidad intentará reiniciar el servicio MSMQ al final de la copia de seguridad o de la operación de restauración. Si el servicio ya se detuvo antes de ejecutar la utilidad, no se intentará reiniciar el servicio.  
Antes de utilizar la utilidad de copia de seguridad/restauración de mensajes de MSMQ, debe cerrar todas las aplicaciones locales que utilizan MSMQ.  
## <a name="syntax"></a>Sintaxis  
```  
mqbkup {/b | /r} <folder path_to_storage_device>  
```  
### <a name="parameters"></a>Parámetros  
|Parámetro|Descripción|  
|-------|--------|  
|b|Especifica la operación de copia de seguridad|  
|/r|Especifica la operación de restauración|  
|< carpeta path_to_storage\_dispositivo >|Especifica la ruta de acceso donde se almacenan los archivos de mensajes y la configuración del registro de MSMQ|  
|/?|Muestra la ayuda en el símbolo del sistema.|  
## <a name="BKMK_Examples"></a>Example  
Para realizar una copia de seguridad de todos los archivos de mensajes de MSMQ y la configuración del registro y almacenarlos en la carpeta *Msmqbkup* de la unidad c:.  
```  
mqbkup /b c:\msmqbkup  
```  
Si la carpeta especificada no existe, la utilidad creará una automáticamente. Si decide especificar una carpeta existente, esta carpeta debe estar vacía. Si especifica una carpeta que no está vacía, la utilidad eliminará todos los archivos y subcarpetas que contiene. En este caso, se le pedirá que conceda permiso para eliminar archivos y subcarpetas existentes. Puede usar el parámetro **/y** para indicar que acepta de antemano la eliminación de todos los archivos y subcarpetas existentes en la carpeta especificada.  
Para eliminar todos los archivos y subcarpetas de la carpeta *Oldbkup* de la unidad C: y almacenar los archivos de mensajes de MSMQ y la configuración del registro en esta carpeta.  
```  
mqbkup /b /y c:\oldbkup  
```  
Para restaurar la configuración del registro y los mensajes de MSMQ:  
```  
mqbkup /r c:\msmqbkup  
```  
Las ubicaciones de las carpetas utilizadas para almacenar los archivos de mensajes de MSMQ se almacenan en el registro. Por lo tanto, la utilidad restaurará los archivos de mensajes de MSMQ en las carpetas especificadas en el registro y no en las carpetas de almacenamiento usadas antes de la operación de restauración. Si las carpetas especificadas en el registro no existen, la operación de restauración las creará automáticamente. Si existen directorios de carpetas y no están vacíos, la utilidad le pedirá permiso para eliminar el contenido actual de estas carpetas.  
## <a name="additional-references"></a>referencias adicionales  
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)  
