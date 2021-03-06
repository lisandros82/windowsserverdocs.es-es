---
title: Configuración de la redirección de carpetas en el servidor de destino de Windows Server Essentials
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe77ba67-128c-4fc3-9361-30fa6af42516
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 6709aa2a342efd5837cf340b645961499baff6a5
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433013"
---
# <a name="configure-folder-redirection-on-the-windows-server-essentials-destination-server"></a>Configuración de la redirección de carpetas en el servidor de destino de Windows Server Essentials

>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Haga esta tarea si está habilitada la redirección de carpetas en el servidor de origen.  
  
 En primer lugar, elimine la antigua configuración de directiva de grupo de redirección de carpetas. A continuación, utilice el panel de Windows Server Essentials para habilitar la redirección de carpetas en el servidor de destino.  
  
### <a name="to-delete-the-old-folder-redirection-group-policy-setting"></a>Para eliminar la antigua configuración de directiva de grupo de redirección de carpetas  
  
1. En el servidor de destino, abra la herramienta administrativa **Administración de directivas de grupo**.  
  
2. En **Administración de directivas de grupo**, expandaaa **Bosque:** <em>NombreDominioRed</em>, expandaaa **Dominios**, expandaaa *NombreDominioRed*y **Objetos de directiva de grupo**.  
  
3. Haga clic con el botón secundario en **Redirección de carpetas de directiva de grupo de SBS**y después haga clic en **Eliminar**.  
  
4. Haga clic con el botón secundario en **Plantillas de seguridad de directiva de grupo de SBS** y después haga clic en **Eliminar**.  
  
5. Lea la advertencia y haga clic en **Sí**.  
  
6. Cierre **Administración de directivas de grupo**.  
  
### <a name="to-enable-folder-redirection-on-the-destination-server"></a>Para habilitar la redirección de carpetas en el servidor de destino  
  
1. En el servidor de destino, abra el panel de Windows Server Essentials.  
  
2. En la barra de navegación, haga clic en **Dispositivos**.  
  
3. En el panel **Tareas de dispositivos**, haga clic en **Implementar directiva de grupo**.  
  
4. En la página **Habilitar la directiva de grupo de redirección de carpetas**, seleccione las carpetas que desea redirigir y haga clic en **Siguiente**.  
  
5. En la página **Habilitar la configuración de directivas de seguridad** , haga clic en **Finalizar**.  
  
   Para aplicar el cambio a la redirección de carpetas, los usuarios de la red deben cerrar sesión en su equipo y después reiniciarla. Así se garantiza la transferencia de todas las carpetas redirigidas al servidor de destino.
