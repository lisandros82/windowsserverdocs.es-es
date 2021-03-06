---
title: Los controladores de almacenamiento deben estar habilitados en las máquinas virtuales para proporcionar acceso al almacenamiento conectado
description: Proporciona instrucciones para resolver el problema que informa esta regla de Analizador de procedimientos recomendados.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 532548a1-8ffe-4b5b-902e-ed2f0819012b
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: f0d10ab4c419a6014a9edb4b7f721714dc92798d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393491"
---
# <a name="storage-controllers-should-be-enabled-in-virtual-machines-to-provide-access-to-attached-storage"></a>Los controladores de almacenamiento deben estar habilitados en las máquinas virtuales para proporcionar acceso al almacenamiento conectado

>Se aplica a: Windows Server 2016

Para más información acerca de los análisis y los procedimientos recomendados, vea [Analizador de procedimientos recomendados](https://go.microsoft.com/fwlink/?LinkId=122786).  
  
|Propiedad|Detalles|  
|-|-|  
|**Sistema operativo**|Windows Server 2016|  
|**Producto o característica**|Hyper-V|  
|**Gravedad**|Advertencia|  
|**Categoría**|Configuración|  

En las secciones siguientes, cursiva indica el texto de la interfaz de usuario que aparece en la herramienta de Analizador de procedimientos recomendados para este problema.

## <a name="issue"></a>Problema  
  
*Es posible que uno o varios controladores de almacenamiento estén deshabilitados en una máquina virtual.*  
  
## <a name="impact"></a>Impacto  
  
*Las máquinas virtuales no pueden usar el almacenamiento conectado a un controlador de almacenamiento deshabilitado. Esto afecta a las siguientes máquinas virtuales:*  
  
\<lista de nombres de máquina virtual >  
  
## <a name="resolution"></a>Resolución  
  
*Use Device Manager del sistema operativo invitado para habilitar todos los controladores de almacenamiento. Si el controlador de almacenamiento no es necesario, use el administrador de Hyper-V para quitarlo de la máquina virtual.*  
  
Para obtener instrucciones sobre cómo usar Device Manager, consulte la ayuda del sistema operativo invitado. Para obtener instrucciones sobre cómo quitar el controlador de almacenamiento, consulte el procedimiento siguiente.  
  
#### <a name="to-remove-a-scsi-storage-controller-from-the-virtual-machine"></a>Para quitar un controlador de almacenamiento SCSI de la máquina virtual  
  
1.  Abre el Administrador Hyper-V. Haga clic en **Inicio**, seleccione **Herramientas administrativas** y, a continuación, haga clic en **Administrador de Hyper-V**.  
  
2.  En el panel de resultados, en **virtual machines**, seleccione la máquina virtual que desea configurar.  
  
3.  Si la máquina virtual se está ejecutando, apague la máquina virtual. Haga clic con el botón secundario en la máquina virtual y haga clic en **apagar**.  
  
4.  En el panel **Acción**, en el nombre de la máquina virtual, haga clic en **Configuración**.  
  
5.  En el panel izquierdo del cuadro de diálogo **configuración** , en **hardware**, haga clic en **controladora SCSI**.  
  
6.  En el panel derecho, haga clic en **quitar**.  
  


