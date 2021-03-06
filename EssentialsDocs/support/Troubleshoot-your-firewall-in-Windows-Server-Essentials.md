---
title: Solucionar problemas del firewall en Windows Server Essentials
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 51d94b67-8b9b-4159-80dd-f652d73a43cb
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 11372589528fcc78e0053bc7002449b53cb3181d
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436044"
---
# <a name="troubleshoot-your-firewall-in-windows-server-essentials"></a>Solucionar problemas del firewall en Windows Server Essentials
 
>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
  
 Si experimenta problemas en el acceso remoto, ejecute el Asistente para reparación del Acceso desde cualquier lugar.  
  
### <a name="to-run-the-repair-anywhere-access-wizard"></a>Para ejecutar el Asistente para reparación del Acceso desde cualquier lugar  
  
1. Abra el Panel.  
  
2. Haga clic en **Configuración**, en la pestaña **Acceso desde cualquier lugar** y en **Reparar**.  
  
3. Siga las instrucciones del Asistente para reparación del Acceso desde cualquier lugar.  
  
   Si está usando una configuración de red avanzada o un firewall que no es de Microsoft, puede que necesite abrir puertos adicionales en el firewall. Los puertos de la tabla siguiente están registrados en la Autoridad de asignación de números de Internet (IANA).  
  
|Número de puerto|Descripción|  
|-----------------|-----------------|  
|65500|Servicio web de certificados|  
|65510 y 65515|Sitio web de implementación de equipos cliente|  
|65520|Servicio web para equipos cliente Mac|  
|65532|Marco de proveedores para las comunicaciones de bucle invertido de servidor|  
|6602|Marco de proveedores para la comunicación entre los equipos cliente y servidor|  
  
## <a name="see-also"></a>Vea también  
  
-   [Usar acceso Web remoto](../use/Use-Remote-Web-Access-in-Windows-Server-Essentials.md)  
  
-   [Administrar acceso Web remoto](../manage/Manage-Remote-Web-Access-in-Windows-Server-Essentials.md)  
  
-   [Administrar acceso ilimitado](../manage/Manage-Anywhere-Access-in-Windows-Server-Essentials.md)  
  
-   [Administrar Windows Server Essentials](../manage/Manage-Windows-Server-Essentials.md)  
  

-   [Soporte técnico de Windows Server Essentials](Support-Windows-Server-Essentials.md)

-   [Soporte técnico de Windows Server Essentials](../support/Support-Windows-Server-Essentials.md)

