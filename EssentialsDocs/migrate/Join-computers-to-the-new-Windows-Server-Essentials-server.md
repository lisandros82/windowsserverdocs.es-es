---
title: Unir equipos a la nueva server1 Windows Server Essentials
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdfa9504-9881-4265-b308-c7ee8721bfaa
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 0240abfff58baedd79ab038af93b107dbb898eb2
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432943"
---
# <a name="join-computers-to-the-new-windows-server-essentials-server1"></a>Unir equipos a la nueva server1 Windows Server Essentials

>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_JoinComputers"></a>   
 El siguiente paso del proceso de migración es unir equipos cliente a la nueva red de Windows Server Essentials y actualizar la configuración de directiva de grupo.  
  
> [!NOTE]
>  Si un equipo cliente ya está unido al servidor de origen, debe desinstalar el software del conector en el equipo cliente para que el equipo pueda conectarse al servidor de destino.  
  
 El proceso de conectar un equipo cliente al servidor es el mismo tanto si los equipos están unidos a un dominio como si no.  
  
- Vaya a **http://** <em>nombre-de-servidor-de-destino</em> **/connect** e instale el software del Conector de Windows Server como si fuera un nuevo equipo.  
  
> [!NOTE]
>  El software del Conector de Windows Server no admite equipos que ejecuten Windows XP o Windows Vista. Si ya se han unido al dominio equipos con estos sistemas operativos, puede omitir este paso.  
  
### <a name="ensure-that-group-policy-has-updated"></a>Comprobación de actualización de la directiva de grupo  
  
> [!NOTE]
>  Este paso es opcional y solo es necesario si se estableció una directiva de grupo personalizada en el servidor de origen, como la de redirección de carpetas.  
  
 Mientras el servidor de origen y de destino aún estén en línea, debe asegurarse de que se haya aplicado la configuración de la directiva de grupo del servidor de destino a los equipos cliente. Haga lo siguiente en cada equipo cliente:  
  
1.  Abra una ventana del símbolo del sistema.  
  
2.  En el símbolo del sistema, escriba **GPRESULT /R** y presione INTRO.  
  
3.  Revise el resultado de la sección Directiva de grupo aplicada desde: y asegúrese de que el servidor de destino, como **DestinationSrv.Domain.local**. Por ejemplo:  
  
    ```  
    USER SETTINGS  
    --------------  
        CN=User,OU=Users,DC=DOMAIN,DC=Local  
        Last time Group Policy was applied: 1/24/2011 at 1:26:27 PM  
        Group Policy was applied from:      DestinationSrv.Domain.local  
        Group Policy slow link threshold:   500 kbps  
        Domain Name:                        Domain  
        Domain Type:                        Windows 2011  
  
    ```  
  
4.  Si no aparece el servidor de destino, escriba **gpupdate /force**en el símbolo del sistema, y, a continuación, presione INTRO para actualizar la configuración de directiva de grupo. Vuelva a realizar el procedimiento anterior.  
  
5.  Si aún no aparece el servidor de destino, puede haber un error en la configuración de directiva de grupo o que esta no se haya aplicado correctamente en el equipo cliente en cuestión. Si no aparece el servidor de destino, siga los pasos siguientes:  
  
    1.  Haga clic en **Inicio** y luego en **Ejecutar**. Escriba **rsop.msc** (conjunto resultante de directivas) y, a continuación, presione INTRO.  
  
    2.  Expanda el árbol con la X hasta llegar a un nodo.  
  
    3.  Haga clic en el nodo y, luego, en **Ver error** para saber por qué se producen errores en la configuración de directiva de grupo en el equipo que se muestra.
