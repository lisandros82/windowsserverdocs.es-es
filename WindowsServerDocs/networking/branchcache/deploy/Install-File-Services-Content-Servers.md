---
title: Instalar servidores de contenido de Servicios de archivo
description: Este tema forma parte de la guía de implementación de BranchCache para Windows Server 2016, que muestra cómo implementar BranchCache en los modos de caché distribuida y hospedada para optimizar el uso del ancho de banda WAN en las sucursales.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 74b0a5ed-dc20-4974-9d4b-2426987a01a1
ms.author: pashort
author: shortpatti
ms.openlocfilehash: c55f8df57ed98d13d6d0d6d2a281edfb55883bea
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71356556"
---
# <a name="install-file-services-content-servers"></a>Instalar servidores de contenido de Servicios de archivo

>Se aplica a: Windows Server (canal semianual), Windows Server 2016

Para implementar servidores de contenido que ejecutan el rol de servidor Servicios de archivo, debe instalar el servicio de rol BranchCache para archivos de red del rol de servidor Servicios de archivo. Además, debe habilitar BranchCache en recursos compartidos de archivos de acuerdo con sus requisitos.  
  
Durante la configuración del servidor de contenido, puede permitir la publicación de contenido de BranchCache para todos los recursos compartidos de archivos, o puede seleccionar un subconjunto de los recursos compartidos de archivos para su publicación.  
  
> [!NOTE]  
> Cuando se implementa un servidor web o un servidor de archivos habilitado para BranchCache como servidor de contenido, la información de contenido se calcula ahora sin conexión, bien antes de que un cliente de BranchCache solicite un archivo. Debido a esta mejora, no es necesario configurar la publicación de hash para los servidores de contenido, como hizo en la versión anterior de BranchCache.  
>   
> Esta generación automática de hash proporciona un rendimiento más rápido y mayor ahorro de ancho de banda, ya que la información de contenido está lista para el primer cliente que solicita el contenido y los cálculos ya se han realizado.  
  
Vea los temas siguientes para implementar servidores de contenido.  
  
-   [Configurar el rol de servidor de Servicios de archivo](../../branchcache/deploy/Configure-the-File-Services-server-role.md)  
  
-   [Habilitar la publicación de hash para servidores de archivos](../../branchcache/deploy/Enable-Hash-Publication-for-File-Servers.md)  
  
-   [Habilitar BranchCache en un recurso compartido &#40;de archivos opcional&#41;](../../branchcache/deploy/enable-bc-on-file-share.md)  
  


