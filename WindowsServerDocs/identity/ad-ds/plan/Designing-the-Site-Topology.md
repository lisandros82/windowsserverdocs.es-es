---
ms.assetid: eeb919de-e21e-48d8-8186-e42adec6933f
title: Diseño de la topología de sitio
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: d3ebc3bd764a8ed44e201d0fca5f85b06df8be9d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408897"
---
# <a name="designing-the-site-topology"></a>Diseño de la topología de sitio

>Se aplica a: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Una topología de sitio de servicio de directorio es una representación lógica de la red física. El diseño de una topología de sitio para Active Directory Domain Services (AD DS) implica la planeación de la ubicación del controlador de dominio y el diseño de sitios, subredes, vínculos a sitios y puentes de vínculos a sitios para garantizar un enrutamiento eficaz del tráfico de consultas y replicación.  
  
El diseño de una topología de sitio le ayuda a enrutar de forma eficaz las consultas de cliente y Active Directory el tráfico de replicación. Una topología de sitio bien diseñada ayuda a su organización a lograr las siguientes ventajas:  
  
-   Minimice el costo de la replicación de datos de Active Directory.  
  
-   Minimice los esfuerzos administrativos necesarios para mantener la topología del sitio.  
  
-   Programe la replicación para que las ubicaciones con vínculos de red lentos o de acceso telefónico se repliquen Active Directory datos durante las horas de poca actividad.  
  
-   Optimice la capacidad de los equipos cliente para buscar los recursos más cercanos, como los controladores de dominio y los servidores de Sistema de archivos distribuido (DFS). Esto ayuda a reducir el tráfico de red a través de vínculos de red de área extensa (WAN) lenta, mejorar los procesos de inicio de sesión y cierre de sesión y acelerar las operaciones de descarga de archivos.  
  
Antes de empezar a diseñar la topología del sitio, debe comprender la estructura de la red física. Además, debe diseñar primero el Active Directory estructura lógica, incluida la jerarquía administrativa, el plan de bosque y el plan de dominio para cada bosque. También debe completar el diseño de la infraestructura del sistema de nombres de dominio (DNS) para AD DS. Para obtener más información sobre cómo diseñar la estructura lógica de Active Directory y la infraestructura de DNS, vea [diseñar la estructura lógica para Windows Server 2008 AD DS](https://technet.microsoft.com/library/cc770806.aspx).  
  
Después de completar el diseño de la topología de sitio, debe comprobar que los controladores de dominio cumplan los requisitos de hardware para Windows Server 2008 Standard, Windows Server 2008 Enterprise y Windows Server 2008 Datacenter.  
  
## <a name="in-this-guide"></a>En esta guía  
  
-   [Descripción de la topología de sitio de Active Directory](../../ad-ds/plan/Understanding-Active-Directory-Site-Topology.md)  
  
-   [Recopilar información de red](../../ad-ds/plan/Collecting-Network-Information.md)  
  
-   [Planear la ubicación del controlador de dominio](../../ad-ds/plan/Planning-Domain-Controller-Placement.md)  
  
-   [Crear un diseño de sitio](../../ad-ds/plan/Creating-a-Site-Design.md)  
  
-   [Crear un diseño de vínculo de sitio](../../ad-ds/plan/Creating-a-Site-Link-Design.md)  
  
-   [Crear un diseño de puente de vínculos a sitios](../../ad-ds/plan/Creating-a-Site-Link-Bridge-Design.md)  
  
-   [Búsqueda de recursos adicionales para Windows Server 2008 Active Directory el diseño de la topología de sitio](../../ad-ds/plan/Finding-Additional-Resources-for-Windows-Server-2008-Active-Directory-Site-Topology-Design.md)  
  


