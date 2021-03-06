---
title: Memoria dinámica está habilitado pero no responde en algunas máquinas virtuales
description: Versión en línea del texto de esta regla de Analizador de procedimientos recomendados.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 91b7f50f-a071-4ab6-beb1-1b29f92f52b6
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 9aa482d91c94a7a619bb65046cf152d6a5f8827a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393678"
---
# <a name="dynamic-memory-is-enabled-but-not-responding-on-some-virtual-machines"></a>Memoria dinámica está habilitado pero no responde en algunas máquinas virtuales

>Se aplica a: Windows Server 2016

Para obtener más información sobre los análisis y los procedimientos recomendados, vea [ejecución de exámenes de analizador de procedimientos recomendados y administración de los resultados de los exámenes](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Propiedad|Detalles|  
|-|-|  
|**Sistema operativo**|Windows Server 2016|  
|**Producto o característica**|Hyper-V|  
|**Gravedad**|Advertencia|  
|**Categoría**|Configuración|  
  
En las secciones siguientes, cursiva indica el texto de la interfaz de usuario que aparece en la herramienta de Analizador de procedimientos recomendados para este problema.  
  
## <a name="issue"></a>Problema  
*Una o varias máquinas virtuales están experimentando problemas con el controlador necesario para Memoria dinámica en el sistema operativo invitado.*  
  
## <a name="impact"></a>Impacto  
*Es posible que el sistema operativo invitado de las siguientes máquinas virtuales no se ejecute o se ejecute de manera no confiable porque Hyper-V no puede ajustar la memoria de forma dinámica para responder a los cambios en la demanda de memoria. Esto afecta a las siguientes máquinas virtuales:*  
  
\<lista de máquinas virtuales >  
  
## <a name="resolution"></a>Resolución  
*Este es el comportamiento esperado si se está iniciando la máquina virtual. Si la máquina virtual no arranca, asegúrese de que Integration Services se actualiza a la versión más reciente y que el sistema operativo invitado admite Memoria dinámica.*  
  
A partir de Windows Server 2016, los servicios de integración se entregan a través de Windows Update. Asegúrese de que las máquinas virtuales están configuradas para recibir actualizaciones para obtener la versión más reciente de Integration Services.  
  
Memoria dinámica funciona con versiones específicas de invitados admitidos. Vea [información general de memoria dinámica de Hyper-V](https://technet.microsoft.com/library/hh831766.aspx) para versiones anteriores a windows Server 2016 y Windows 10.  
  


