---
ms.assetid: f6e76ef0-2217-4cdb-980f-22a780a85ebb
title: Requisitos de diseño de AD DS
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: cb9d4c04bc3fc7bb534e75b80f0947bd225b7b85
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71368962"
---
# <a name="ad-ds-design-requirements"></a>Requisitos de diseño de AD DS

>Se aplica a: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

  
## <a name="designing-the-active-directory-logical-structure"></a>Diseñar la estructura lógica de Active Directory  
Antes de implementar Windows Server 2008 Active Directory Domain Services (AD DS), debe planear y diseñar la estructura lógica de AD DS para su entorno. La estructura lógica AD DS determina el modo en que se organizan los objetos de directorio, y proporciona un método eficaz para administrar las cuentas de red y los recursos compartidos. Al diseñar la estructura lógica de AD DS, se define una parte importante de la infraestructura de red de la organización.  
  
Para diseñar la estructura lógica de AD DS, determine el número de bosques que requiere su organización y, a continuación, cree diseños para los dominios, la infraestructura del sistema de nombres de dominio (DNS) y las unidades organizativas (OU). En la ilustración siguiente se muestra el proceso para diseñar la estructura lógica.  
  
![Requisitos de diseño de AD DS](media/AD-DS-Design-Requirements/d5cebae6-a752-4063-a98f-473799c251bd.gif)  
  
Para obtener más información, vea [diseñar la estructura lógica para Windows Server 2008 AD DS](Designing-the-Logical-Structure.md).  
  
## <a name="designing-the-site-topology"></a>Diseño de la topología de sitio  
Después de diseñar la estructura lógica de la infraestructura de AD DS, debe diseñar la topología del sitio para la red. La topología del sitio es una representación lógica de la red física. Contiene información acerca de la ubicación de los sitios de AD DS, el AD DS los controladores de dominio de cada sitio y los vínculos a sitios y puentes de vínculos a sitios que admiten la replicación de AD DS entre sitios. En la ilustración siguiente se muestra el proceso de diseño de la topología de sitio.  
  
![Requisitos de diseño de AD DS](media/AD-DS-Design-Requirements/d34d43c0-437f-47cb-9b64-09c0f9ce6479.gif)  
  
Para obtener más información, vea [diseñar la topología de sitio para Windows Server 2008 AD DS](Designing-the-Site-Topology.md).  
  
## <a name="planning-domain-controller-capacity"></a>Planear la capacidad del controlador de dominio  
Para garantizar un rendimiento eficaz AD DS, debe determinar el número adecuado de controladores de dominio para cada sitio y comprobar que cumplen los requisitos de hardware para Windows Server 2008. Un cuidadoso planeamiento de la capacidad de los controladores de dominio garantiza que no se subestiman los requisitos de hardware, lo que puede provocar un rendimiento deficiente del controlador de dominio y el tiempo de respuesta de la aplicación. En la ilustración siguiente se muestra el proceso de planeamiento de la capacidad del controlador de dominio.  
  
![Requisitos de diseño de AD DS](media/AD-DS-Design-Requirements/fff6ef22-5c7b-4478-ad76-42b296dcf769.gif)  
  
## <a name="enabling-windows-server-2008-advanced-ad-ds-features"></a>Habilitación de características avanzadas de AD DS de Windows Server 2008  
Puede usar Windows Server 2008 AD DS para introducir características avanzadas en su entorno elevando el nivel funcional del bosque o del dominio. Puede elevar el nivel funcional a Windows Server 2008 cuando todos los controladores de dominio del dominio o bosque ejecutan Windows Server 2008.  
  
Para obtener más información, vea [habilitar características avanzadas para AD DS](../../ad-ds/plan/Enabling-Advanced-Features-for-AD-DS.md).  
  


