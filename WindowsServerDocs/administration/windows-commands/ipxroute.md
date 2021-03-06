---
title: ipxroute
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a30304f-655e-43d2-a4ac-7568abf8975c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bd5f33766ff9b33c9d6020b7284f2fbf9552d44d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375332"
---
# <a name="ipxroute"></a>ipxroute

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Muestra y modifica información acerca de las tablas de enrutamiento utilizadas por el protocolo IPX. Si se usa sin parámetros, **ipxroute** muestra la configuración predeterminada de los paquetes que se envían a direcciones desconocidas, de difusión y de multidifusión.   
## <a name="syntax"></a>Sintaxis  
```  
ipxroute servers [/type=X]  
ipxroute ripout <Network>  
ipxroute resolve {guid | name} {GUID | <AdapterName>}  
ipxroute board= N [def] [gbr] [mbr] [remove=xxxxxxxxxxxx]  
ipxroute config  
```  
### <a name="parameters"></a>Parámetros  
|Parámetro|Descripción|  
|-------|--------|  
|servidores [/Type = X]|Muestra la tabla de punto de acceso de servicio (SAP) para el tipo de servidor especificado.  **X** debe ser un entero. Por ejemplo, **/Type = 4** muestra todos los servidores de archivos. Si no especifica **/Type**, **los servidores ipxroute** muestran todos los tipos de servidores y los enumeran por nombre de servidor.|  
|Red ripout|Detecta si la *red* es accesible mediante la consulta de la tabla de rutas de la pila IPX y el envío de una solicitud RIP si es necesario.  *Network* es el número de segmento de red IPX.|  
|resolver {GUID&#124; Name} {GUID&#124; AdapterName}|Resuelve el nombre del GUID como su nombre descriptivo o el nombre descriptivo de su GUID.|  
|panel = *N*|Especifica el adaptador de red para el que se van a consultar o establecer parámetros.|  
|Def|Envía paquetes a la difusión ALL ROUTEs. Si un paquete se transmite a una dirección de tarjeta de acceso a medios (MAC) única que no se encuentra en la tabla de enrutamiento de origen, **ipxroute** envía el paquete a la difusión de rutas únicas de forma predeterminada.|  
|GbR|Envía paquetes a la difusión ALL ROUTEs. Si un paquete se transmite a la dirección de difusión (FFFFFFFFFFFF), **ipxroute** envía el paquete a la difusión de rutas únicas de forma predeterminada.|  
|Maestro|Envía paquetes a la difusión ALL ROUTEs. Si un paquete se transmite a una dirección de multidifusión (C000xxxxxxxx), **ipxroute** envía el paquete a la difusión de rutas únicas de forma predeterminada.|  
|Remove = *XXXXXXXXXXXX*|quita la dirección de nodo especificada de la tabla de enrutamiento de origen.|  
|configurar|Muestra información acerca de todos los enlaces para los que se ha configurado IPX.|  
|/?|Muestra la ayuda en el símbolo del sistema.|  
## <a name="BKMK_Examples"></a>Example  
Para mostrar los segmentos de red a los que está conectada la estación de trabajo, la dirección del nodo de estación de trabajo y el tipo de marco que se está usando, escriba:  
```  
ipxroute config  
```  
## <a name="additional-references"></a>Referencias adicionales  
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)  
