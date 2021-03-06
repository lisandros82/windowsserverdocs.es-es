---
title: Todas las redes para el tráfico de migración en vivo deben tener una velocidad de vínculo de al menos 1 Gbps
description: Versión en línea del texto de esta regla de Analizador de procedimientos recomendados.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 89411b63-bec8-463d-b486-107548ed440e
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 92ba74ec75d8e90979e1cc329415a52af0218f54
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71365301"
---
# <a name="all-networks-for-live-migration-traffic-should-have-a-link-speed-of-at-least-1-gbps"></a>Todas las redes para el tráfico de migración en vivo deben tener una velocidad de vínculo de al menos 1 Gbps

>Se aplica a: Windows Server 2016


  
|Property|Detalles|  
|-|-|  
|**Sistema operativo**|Windows Server 2016|  
|**Producto o característica**|Hyper-V|  
|**Gravedad**|Advertencia|  
|**Categoría**|Configuración|  
  
En las secciones siguientes, cursiva indica el texto de la interfaz de usuario que aparece en la herramienta de Analizador de procedimientos recomendados para este problema.  
  
## <a name="issue"></a>Problema  
*Ninguna de las redes para el tráfico de migración en vivo tiene una velocidad de vínculo de al menos 1 Gbps.*  
  
## <a name="impact"></a>Impacto  
*Las migraciones en vivo pueden producirse lentamente, lo que podría interrumpir la conexión de red debido a un tiempo de espera de conexión TCP.*  
  
## <a name="resolution"></a>Resolución  
*Configure al menos una red de migración en vivo con una velocidad de 1 Gbps o más.*  
  
Consulte la documentación del proveedor de hardware de red para averiguar si alguno de los adaptadores de red existentes puede admitir una velocidad de vínculo de al menos 1 Gbps.  
  


