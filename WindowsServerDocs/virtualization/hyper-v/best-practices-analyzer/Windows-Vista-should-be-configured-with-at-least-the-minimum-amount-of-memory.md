---
title: Windows Vista debe configurarse con al menos la cantidad mínima de memoria
description: Proporciona instrucciones para resolver el problema que informa esta regla de Analizador de procedimientos recomendados.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 49f6f9b6-c290-4b1b-b6f3-cc9a0acd8fb2
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 6a5197af0577c411337194104a4fe97d06d41a01
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393042"
---
# <a name="windows-vista-should-be-configured-with-at-least-the-minimum-amount-of-memory"></a>Windows Vista debe configurarse con al menos la cantidad mínima de memoria

>Se aplica a: Windows Server 2016

Para más información acerca de los análisis y los procedimientos recomendados, vea [Analizador de procedimientos recomendados](https://go.microsoft.com/fwlink/?LinkId=122786).  
  
|Propiedad|Detalles|  
|-|-|  
|**Sistema operativo**|Windows Server 2016|  
|**Producto o característica**|Hyper-V|  
|**Gravedad**|Error|  
|**Categoría**|Configuración|  
  
En las secciones siguientes, cursiva indica el texto de la interfaz de usuario que aparece en la herramienta de Analizador de procedimientos recomendados para este problema.  
  
## <a name="issue"></a>Problema  
  
*Una máquina virtual que ejecuta Windows Vista está configurada con menos de la cantidad mínima de RAM, que es 512 MB.*  
  
## <a name="impact"></a>Impacto  
  
*Es posible que el sistema operativo invitado de las siguientes máquinas virtuales no se ejecute o se ejecute de forma no confiable:*  
  
\<lista de nombres de máquina virtual >  
  
## <a name="resolution"></a>Resolución  
  
*Use el administrador de Hyper-V para aumentar la memoria asignada a esta máquina virtual al menos 512 MB.*  
  
### <a name="to-increase-the-memory-using-hyper-v-manager"></a>Para aumentar la memoria mediante el administrador de Hyper-V  
  
1.  Abre el Administrador Hyper-V. Haga clic en **Inicio**, seleccione **Herramientas administrativas** y, a continuación, haga clic en **Administrador de Hyper-V**.  
  
2.  En el panel de resultados, en **virtual machines**, seleccione la máquina virtual que desea configurar. El estado de la máquina virtual debe aparecer como **desactivado**. Si no es así, haga clic con el botón secundario en la máquina virtual y, a continuación, haga clic en **apagar**.  
  
3.  En el panel **Acción**, en el nombre de la máquina virtual, haga clic en **Configuración**.  
  
4.  En el panel de navegación, haga clic en **memoria**.  
  
5.  En la página **memoria** , establezca la **RAM de inicio** en al menos 512 MB y, a continuación, haga clic en **Aceptar**.  
  
### <a name="increase-the-memory-using-windows-powershell"></a>Aumentar la memoria mediante Windows PowerShell  
  
1.  Abra Windows PowerShell. (En el escritorio, haga clic en **Inicio** y comience a escribir **Windows PowerShell**).  
  
2.  Haga clic con el botón derecho en **Windows PowerShell** y haga clic en **Ejecutar como administrador**.  
  
3.  Ejecute este comando después de reemplazar \<MyVM > por el nombre de la máquina virtual:  
  
```  
Set-VMMemory <MyVM> -StartupBytes 512MB  
```  
  
## <a name="see-also"></a>Consulta también  
[Set-VMMemory](https://technet.microsoft.com/library/hh848572.aspx)  
  


