---
title: Servicios de escritorio remoto - autenticación multifactor
description: Información de planeación para usar MFA con RDS.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09ea784e-5644-417a-a3d9-bdbcebc313f9
author: lizap
ms.author: elizapo
ms.date: 09/07/2016
manager: dongill
ms.openlocfilehash: 50cbabf377e5b01c44360d776b9ff999826303c6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814876"
---
# <a name="remote-desktop-services---multi-factor-authentication"></a>Servicios de escritorio remoto - autenticación multifactor

>Se aplica a: Windows Server (canal semianual), Windows Server 2016

Aproveche la eficacia de Active Directory con autenticación multifactor para aplicar la protección de alta seguridad de los recursos empresariales.

Para los usuarios finales conectarse a sus equipos de escritorio y aplicaciones, la experiencia es similar a lo ya se enfrentan mientras llevan a cabo una segunda medida de autenticación para conectarse al recurso deseado:
- Iniciar un escritorio o desde un archivo RDP o a través de una aplicación de cliente de escritorio remoto de RemoteApp
- Al conectarse a la puerta de enlace de escritorio remoto para el acceso remoto seguro, recibir un SMS o aplicación móvil de desafío de MFA
- Correctamente autenticarse y conectarse a sus recursos.

Para obtener más detalles sobre el proceso de configuración, consulte [integración de la infraestructura de la puerta de enlace de escritorio remoto con la extensión de servidor de directivas de redes (NPS) y Azure AD ](https://docs.microsoft.com/azure/multi-factor-authentication/nps-extension-remote-desktop-gateway).