---
title: Novedades de Puerta de enlace de RAS
description: Puede usar este tema para obtener información acerca de las nuevas características de puerta de enlace RAS, que es un enrutador compatible con Protocolo de puerta de enlace de borde (BGP) basado en software y multiinquilino en Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 709cb192-313a-47b5-954e-eb5f6fee51a7
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 85595c47c599a72039e93e67ea2f33f92af7200c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405893"
---
# <a name="whats-new-in-ras-gateway"></a>Novedades de Puerta de enlace de RAS

>Se aplica a: Windows Server (canal semianual), Windows Server 2016

Puede usar este tema para obtener información acerca de las nuevas características de puerta de enlace RAS, que es un enrutador compatible con Protocolo de puerta de enlace de borde (BGP) basado en software y multiinquilino en Windows Server 2016. El enrutador BGP de puerta de enlace RAS multiempresa está diseñado para los proveedores de servicios en la nube (CSP) y las empresas que hospedan varias redes virtuales de inquilinos mediante la virtualización de red de Hyper-V.  
  
> [!NOTE]  
> En Windows Server 2012 R2, la puerta de enlace RAS se denomina puerta de enlace RRAS. y, en System Center Virtual Machine Manager, la puerta de enlace de RAS se denomina puerta de enlace de Windows Server.  
  
En este tema se incluyen las siguientes secciones.  
  
-   [Opciones de conectividad de sitio a sitio](#bkmk_s2s)  
  
-   [Grupos de puerta de enlace](#bkmk_pools)  
  
-   [Escalabilidad del grupo de puerta de enlace](#bkmk_gps)  
  
-   [Redundancia de grupo de puerta de enlace M + N](#bkmk_m)  
  
-   [Reflector de rutas](#bkmk_rr)  
  
## <a name="bkmk_s2s"></a>Opciones de conectividad de sitio a sitio  
La puerta de enlace RAS admite ahora tres tipos de conexiones VPN de sitio a sitio:  Redes privadas virtuales (VPN) de sitio a sitio de Intercambio de claves por red versión 2 (IKEv2) y túneles de encapsulación de enrutamiento genérico (GRE).  
  
Para obtener más información acerca de GRE, consulte [tunelización de GRE en Windows Server 2016](../../../../remote/remote-access/ras-gateway/gre-tunneling-windows-server.md).  
  
## <a name="bkmk_pools"></a>Grupos de puerta de enlace  
En Windows Server 2016, puede crear grupos de puertas de enlace de distintos tipos. Los grupos de puertas de enlace contienen muchas instancias de puerta de enlace RAS y enrutan el tráfico de red entre las redes físicas y virtuales. Los grupos de puerta de enlace pueden realizar cualquiera de las funciones de puerta de enlace individuales: Intercambio de claves por red la versión 2 (IKEv2) de red privada virtual (VPN), VPN de nivel 3 (L3) y túneles de encapsulación de enrutamiento genérico (GRE), o el grupo puede realizar todas estas acciones Functions y actúan como un grupo mixto.  
  
Puede crear grupos de puerta de enlace con cualquier lógica que prefiera en función de los requisitos de infraestructura. Por ejemplo, puede crear grupos de puerta de enlace basados en cualquiera de las siguientes características.  
  
-   Tipos de túnel (VPN IKEv2, VPN L3, VPN GRE)  
  
-   Capacidad  
  
-   Nivel de redundancia (confiabilidad según el plan de facturación para los inquilinos)  
  
-   Separación personalizada para clientes  
  
Para obtener más información, consulte [alta disponibilidad de puerta de enlace de Ras](RAS-Gateway-High-Availability.md).  
  
## <a name="bkmk_gps"></a>Escalabilidad del grupo de puerta de enlace  
Puede escalar o reducir verticalmente un grupo de puerta de enlace fácilmente agregando o quitando máquinas virtuales de puerta de enlace en el grupo. La eliminación o adición de puertas de enlace no interrumpe los servicios proporcionados por un grupo. También puede Agregar y quitar grupos de puertas de enlace completos.  
  
Para obtener más información, consulte [alta disponibilidad de puerta de enlace de Ras](RAS-Gateway-High-Availability.md).  
  
## <a name="bkmk_m"></a>Redundancia de grupo de puerta de enlace M + N  
Cada grupo de puerta de enlace es M + N redundante. Esto significa que se realiza una copia de seguridad de un número de máquinas virtuales (VM) de puerta de enlace activa mediante un número "N" de máquinas virtuales de puerta de enlace en espera. La redundancia M + N proporciona más flexibilidad a la hora de determinar el nivel de confiabilidad que necesita al implementar la puerta de enlace de RAS. En lugar de usar una sola puerta de enlace RAS en espera por VM de puerta de enlace RAS activa, que es la única opción de configuración con Windows Server 2012 R2, ahora puede configurar tantas máquinas virtuales en espera como necesite. La característica Service Manager de puerta de enlace de controladora de red usa eficazmente la capacidad de la máquina virtual de puerta de enlace RAS de reserva para proporcionar una conmutación por error confiable si se produce un error en una máquina virtual de puerta  
  
Para obtener más información, consulte [alta disponibilidad de puerta de enlace de Ras](RAS-Gateway-High-Availability.md).  
  
## <a name="bkmk_rr"></a>Reflector de rutas  
El reflector de rutas de Protocolo de puerta de enlace de borde (BGP) ahora se incluye con la puerta de enlace de RAS y proporciona una alternativa a la topología de malla completa de BGP necesaria para la sincronización de rutas entre los enrutadores. Con la sincronización de malla completa, todos los enrutadores BGP deben conectarse con todos los demás enrutadores en la topología de enrutamiento. Sin embargo, cuando se usa el reflector de rutas, el reflector de rutas es el único enrutador que se conecta con todos los otros enrutadores, denominados clientes de BGP, lo que simplifica la sincronización de rutas y reduce el tráfico de red. El reflector de rutas aprende todas las rutas, calcula las mejores rutas y redistribuye las mejores rutas a sus clientes BGP.  
  
Con Windows Server 2016, puede configurar los túneles de acceso remoto de un inquilino individual para que finalicen en más de una máquina virtual de puerta de enlace de RAS. Esto proporciona mayor flexibilidad a los proveedores de servicios en la nube cuando se enfrenta a circunstancias en las que una máquina virtual de puerta de enlace RAS no puede cumplir todos los requisitos de ancho de banda de las conexiones de inquilino.  
  
Sin embargo, esta funcionalidad presenta la complejidad adicional de la administración de rutas y la sincronización efectiva de rutas entre los sitios remotos de inquilinos y sus recursos virtuales en el centro de servicios en la nube. El suministro de inquilinos con conexiones a varias puertas de enlace de RAS también introduce una complejidad adicional en la configuración en el extremo de la empresa, donde cada sitio de inquilino tendrá vecinos de enrutamiento independientes.  
  
Un reflector de rutas BGP en el plano de control aborda estos problemas y hace que la implementación de tejido interno de CSP sea transparente para los inquilinos empresariales. A continuación se muestran algunos puntos clave sobre el reflector de rutas BGP que se incluye con la puerta de enlace de RAS y se integra con la controladora de red.  
  
-   Un reflector de rutas en una implementación de redes definidas por software es una entidad lógica que se encuentra en el plano de control entre las puertas de enlace de RAS y la controladora de red. No obstante, no participa en el enrutamiento del plano de datos.  
  
-   Cuando se agrega un nuevo inquilino al centro de recursos, la controladora de red configura automáticamente la primera puerta de enlace RAS de inquilino como reflector de rutas.  
  
-   Cada inquilino tiene un reflector de rutas correspondiente y reside en una de las máquinas virtuales de puerta de enlace de RAS que están asociadas a ese inquilino.  
  
-   Un reflector de rutas de inquilino actúa como el reflector de rutas de todas las máquinas virtuales de puerta de enlace de RAS asociadas al inquilino. Las puertas de enlace de inquilinos que no sean el reflector de rutas de puerta de enlace de RAS son los clientes de reflector de rutas. El reflector de rutas realiza la sincronización de rutas entre todos los clientes de reflector de rutas para que pueda producirse el enrutamiento de la ruta de acceso de datos real.  
  
-   Un reflector de rutas no proporciona servicios de reflector de enrutamiento para la puerta de enlace de RAS en la que está configurada.  
  
-   Un reflector de rutas actualiza el controlador de red con las rutas de empresa que se corresponden con los sitios empresariales del inquilino. Esto permite que la controladora de red configure las directivas de virtualización de red de Hyper-V necesarias en la red virtual de inquilino para acceder a la ruta de acceso a los datos de un extremo a otro.  
  
-   Si los clientes empresariales usan el enrutamiento BGP en el espacio de direcciones de cliente, el reflector de rutas de puerta de enlace RAS es el único vecino BGP externo (eBGP) para todos los sitios del inquilino correspondiente. Esto es así independientemente de los puntos de terminación de túnel del inquilino empresarial. En otras palabras, independientemente de que la máquina virtual de puerta de enlace de RAS en el centro de recursos de CSP termine el túnel VPN de sitio a sitio para un sitio de inquilino, el eBGP del mismo nivel para todos los sitios de inquilino es el reflector de rutas.  
  
Para obtener más información, consulte la [arquitectura de implementación de puerta de enlace de Ras](RAS-Gateway-Deployment-Architecture.md) y el tema de solicitud de comentarios de Internet Engineering Task Force (IETF) [RFC 4456, reflexión de rutas BGP: Una alternativa al BGP interno de la malla completa (IBGP) ](https://tools.ietf.org/html/rfc4456).  
  

