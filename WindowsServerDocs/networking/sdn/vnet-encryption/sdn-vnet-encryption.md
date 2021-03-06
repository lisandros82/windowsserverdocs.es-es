---
title: Cifrado de Virtual Network
description: El cifrado de red virtual permite el cifrado del tráfico de red virtual entre máquinas virtuales que se comunican entre sí dentro de subredes marcadas como "cifrado habilitado".
manager: dougkim
ms.prod: windows-server
ms.technology: networking-hv-switch
ms.topic: get-started-article
ms.assetid: 7da0f509-7b02-4a0f-90fb-d97c83a2bc4e
ms.author: pashort
author: shortpatti
ms.date: 08/08/2018
ms.openlocfilehash: 7ecb2a1373efcf15aada451313e334e210c76d1e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71355529"
---
# <a name="virtual-network-encryption"></a>Cifrado de Virtual Network

>Se aplica a: Windows Server

El cifrado de red virtual permite el cifrado del tráfico de red virtual entre máquinas virtuales que se comunican entre sí dentro de subredes marcadas como "cifrado habilitado". También utiliza la Seguridad de la capa de transporte de datagrama (DTLS) en la subred virtual para cifrar los paquetes. DTLS protege frente a las interceptaciones, alteraciones y falsificaciones realizadas por cualquier persona con acceso a la red física.

El cifrado de red virtual requiere:
- Certificados de cifrado instalados en cada uno de los hosts de Hyper-V habilitados para SDN.
- Un objeto de credencial de la controladora de red que hace referencia a la huella digital de ese certificado.
- La configuración de cada una de las redes virtuales contiene subredes que requieren cifrado.

Una vez habilitado el cifrado en una subred, todo el tráfico de red dentro de esa subred se cifra automáticamente, además de cualquier cifrado de nivel de aplicación que también pueda tener lugar.  El tráfico que cruza entre subredes, incluso si está marcado como cifrado, se envía automáticamente sin cifrar. El tráfico que cruza el límite de la red virtual también se envía sin cifrar.

>[!TIP]
>Si debe restringir las aplicaciones para que solo se comuniquen en la subred cifrada, puede usar listas de Access Control (ACL) solo para permitir la comunicación dentro de la subred actual. Para obtener más información, consulte [uso de listas de Access Control (ACL) para administrar el flujo de tráfico de red del centro](https://docs.microsoft.com/windows-server/networking/sdn/manage/use-acls-for-traffic-flow)de datos.

### <a name="next-steps"></a>Pasos siguientes

[Configuración del cifrado para una red virtual](https://docs.microsoft.com/windows-server/networking/sdn/vnet-encryption/sdn-config-vnet-encryption)

