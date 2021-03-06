---
title: Administrar recursos de almacenamiento remoto
description: En este artículo se describe cómo administrar recursos de almacenamiento en un equipo remoto
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 5c6dc9c931e130e36e01655de05fbd209f50f3dc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71394077"
---
# <a name="managing-remote-storage-resources"></a>Administrar recursos de almacenamiento remoto

> Se aplica a: Windows Server 2019, Windows Server 2016, Windows Server (canal semianual), Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Para administrar recursos de almacenamiento en un equipo remoto, tienes dos opciones:

-   Conectarte al equipo remoto desde el Complemento de la consola de administración de Microsoft<sup>®</sup> (MMC) del Administrador de recursos del servidor de archivos (que puedes usar para administrar los recursos remotos).
-   Usar las herramientas de línea de comandos que se instalan con el Administrador de recursos del servidor de archivos.

Cualquier opción te permite trabajar cuotas, filtrar archivos, administrar clasificaciones, programar tareas de administración de archivos y generar informes con esos recursos remotos.

> [!Note]
> El Administrador de recursos del servidor de archivos puede administrar recursos tanto en el equipo local como en un equipo remoto, pero no en ambos al mismo tiempo.

Por ejemplo, puedes:

-   Conectarte a otro equipo del dominio mediante el Complemento MMC del Administrador de recursos del servidor de archivos y revisar el uso del almacenamiento en un volumen o carpeta que se encuentran en el equipo remoto.
-   Crear plantillas de filtros de archivos y cuotas en un servidor local y luego usar las herramientas de línea de comandos para importar estas plantillas en un servidor de archivos que se encuentra en una sucursal.

Esta sección incluye los temas siguientes:

-   [Conectarse a un equipo remoto](connect-to-remote-computer.md)
-   [Herramientas de línea de comandos](command-line-tools.md)
