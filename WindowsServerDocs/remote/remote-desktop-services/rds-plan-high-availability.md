---
title: 'Servicios de Escritorio remoto: Alta disponibilidad'
description: Planea la información sobre cómo configurar una implementación de RDS de alta disponibilidad.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec630ea0-ab80-4dfe-a25f-f4f601651f72
author: lizap
ms.author: elizapo
ms.date: 09/07/2016
manager: dongill
ms.openlocfilehash: 3d3d216c528b0b83d9dfd5265fe153a388c7382a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71387277"
---
# <a name="remote-desktop-services---high-availability"></a>Servicios de Escritorio remoto: Alta disponibilidad

>Se aplica a: Windows Server (canal semianual), Windows Server 2019, Windows Server 2016

Los errores y la limitación son inevitables en sistemas a gran escala. Resulta fácil configurar roles de infraestructura de Escritorio remoto que admitan la alta disponibilidad y permitan que los usuarios finales se conecten siempre fácilmente.

En Servicios de Escritorio remoto, los siguientes elementos representan los roles de infraestructura de Escritorio remoto, con sus correspondientes instrucciones para establecer la alta disponibilidad:
- [Agente de conexión a Escritorio remoto](Deploy-a-Remote-Desktop-Connection-Broker-cluster.md)
- [Puerta de enlace de Escritorio remoto](Deploy-a-RD-Web-Access-and-Gateway-farm.md)
- Administración de licencias de Escritorio remoto
- [Acceso web de Escritorio remoto](Deploy-a-RD-Web-Access-and-Gateway-farm.md)

La alta disponibilidad se establece mediante la duplicación de cada uno de los servicios de roles en segundas máquinas. En Azure, puedes recibir un tiempo de actividad garantizado al colocar el conjunto de las dos máquinas virtuales (que hospedan el mismo rol) en un conjunto de disponibilidad.

Junto con los conjuntos de disponibilidad, ahora puedes aprovechar la eficacia de Azure SQL Database y su SLA con respaldo de Azure para asegurarte de tener siempre la información de conexión y poder redirigir a los usuarios a sus escritorios y aplicaciones.

Para los procedimientos recomendados sobre la creación de un entorno de RDS, consulta la [arquitectura de hospedaje de escritorio](desktop-hosting-reference-architecture.md).