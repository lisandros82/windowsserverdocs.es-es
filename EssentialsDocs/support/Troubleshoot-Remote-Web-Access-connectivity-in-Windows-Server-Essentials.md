---
title: Solucionar los problemas de conectividad del acceso Web remoto en Windows Server Essentials
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d3642575-b3ee-4488-b654-5bf9d3b8c935
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: fda0b5a227fe25b4e8780915089e97ee48620383
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432432"
---
# <a name="troubleshoot-remote-web-access-connectivity-in-windows-server-essentials"></a>Solucionar los problemas de conectividad del acceso Web remoto en Windows Server Essentials
 
>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
  
 Normalmente, Windows Server Essentials puede configurar automáticamente un enrutador de banda ancha si el enrutador es un dispositivo certificado UPnP y si la configuración de UPnP está habilitada en el enrutador.  
  
## <a name="possible-issues"></a>Posibles problemas  
 Puede encontrarse con los siguientes problemas de conectividad del acceso Web remoto:  
  
-   El enrutador no está activado o no está conectado a la red.  
  
-   La configuración de UPnP del enrutador está desactivada.  
  
-   El enrutador podría no admitir totalmente el estándar UPnP. Microsoft mantiene una lista de los enrutadores que funcionan con los sistemas operativos Windows. Para ver la lista de enrutadores (incluidos los enrutadores inalámbricos) que son compatibles con Windows Server Essentials, visite el [Centro de compatibilidad de Windows](https://www.microsoft.com/windows/compatibility/CompatCenter/Home).  
  
## <a name="possible-fixes"></a>Posibles soluciones  
 Las siguientes acciones pueden solucionar estos problemas:  
  
- Compruebe que el enrutador está activado y funciona correctamente.  
  
- Asegúrese de que el servidor está conectado directamente al enrutador o que está conectado a un conmutador que esté conectado al enrutador.  
  
- Compruebe que el dispositivo de banda ancha que se conecta al proveedor de servicios de Internet (ISP) está activado y funciona correctamente, y que el enrutador está conectado al dispositivo de banda ancha.  
  
- Active la configuración de DHCP del enrutador. Conéctese a la página web de configuración del enrutador activar la configuración de UPnP. Para obtener información acerca de cómo iniciar sesión en el enrutador y cómo activar la configuración de UPnP, consulte la documentación del enrutador. Después de activar la configuración de UPnP, ejecute la active en Web Asistente para acceso remoto para configurar el enrutador.  
  
- Si el enrutador no es totalmente compatible con el estándar UPnP, no se puede configurar automáticamente. Debe configurar manualmente el enrutador o comprar un enrutador que admita el estándar UPnP.  
  
   Para configurar manualmente el enrutador, complete las tareas siguientes:  
  
  - Cree la reserva de direcciones IP para el servidor de Windows Server Essentials.  
  
     Antes de configurar manualmente el enrutador para reenviar los puertos necesarios para Windows Server Essentials, debe configurar una reserva de Protocolo de configuración dinámica de host (DHCP) para el servidor que ejecuta Windows Server Essentials en el enrutador. Este paso garantiza que la dirección IP a la que se van a reenviar los puertos no cambie.  
  
     Para obtener información acerca de cómo configurar manualmente una reserva DHCP para el servidor en el enrutador, consulte la documentación del fabricante del enrutador.  
  
  - Configure el enrutamiento de puerto en el enrutador para los puertos siguientes:  
  
    |Servicio o protocolo|Puerto|  
    |-------------------------|----------|  
    |HTTP|TCP 80|  
    |HTTPS|TCP 443|  
  
    Para obtener información acerca de cómo configurar manualmente el reenvío de puerto en el enrutador, consulte la documentación del fabricante.  
  
    Una página de configuración de enrutador típica incluye una tabla similar a la siguiente.  
  
  > [!NOTE]
  >  En esta tabla, la dirección IP del equipo que ejecuta Windows Server Essentials es 192.168.0.100. Debe determinar la dirección IP del equipo y sustituirla por la dirección IP que se muestra en la tabla.  
  
  |Dirección IP|Protocolo (TCP/UDP)|Programa|Filtro de entrada|  
  |----------------|---------------------------|--------------|--------------------|  
  |192.168.0.100|TCP 80|Siempre|Permitir todo|  
  |192.168.0.100|TCP 443|Siempre|Permitir todo|  
  
   Después de configurar manualmente el enrutador, ejecute la active en Web Asistente para acceso remoto, asegurándose de seleccionar la **omitir la configuración del enrutador** opción el **Introducción** página.  
  
- Compre un enrutador nuevo si su enrutador no es totalmente compatible con el estándar UPnP.  
  
> [!TIP]
>  Asegúrese de que el enrutador tenga instalado el firmware BIOS más reciente. Puede actualizar a menudo el firmware BIOS del enrutador desde la página web de configuración del enrutador. Para obtener más información, consulte la documentación del enrutador Una vez actualizado el enrutador, ejecute el Asistente para configurar el Acceso desde cualquier lugar.  
  
## <a name="see-also"></a>Vea también  
  
-   [Usar acceso Web remoto](../use/Use-Remote-Web-Access-in-Windows-Server-Essentials.md)  
  
-   [Administrar acceso Web remoto](../manage/Manage-Remote-Web-Access-in-Windows-Server-Essentials.md)  
  
-   [Administrar acceso ilimitado](../manage/Manage-Anywhere-Access-in-Windows-Server-Essentials.md)  
  
-   [Administrar Windows Server Essentials](../manage/Manage-Windows-Server-Essentials.md)  
  

-   [Soporte técnico de Windows Server Essentials](Support-Windows-Server-Essentials.md)

-   [Soporte técnico de Windows Server Essentials](../support/Support-Windows-Server-Essentials.md)

