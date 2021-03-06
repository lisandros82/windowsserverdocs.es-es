---
title: iSCSI Target Server Overview
TOCTitle: iSCSI Target Server
ms.prod: windows-server
ms.technology: storage-iscsi
ms.topic: article
author: JasonGerend
manager: dougkim
ms.author: jgerend
ms.date: 09/11/2018
ms.openlocfilehash: 638343abf782983020a3301898920470ffcd5952
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403058"
---
# <a name="iscsi-target-server-overview"></a>Introducción al servidor de destino iSCSI

Se aplica a: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

En este tema se proporciona una breve introducción al servidor de destino iSCSI, un servicio de rol de Windows Server que le permite hacer que el almacenamiento esté disponible a través del protocolo iSCSI. Esto resulta útil para proporcionar acceso al almacenamiento en el servidor de Windows para los clientes que no pueden comunicarse a través del protocolo nativo de uso compartido de archivos de Windows, SMB.

El servidor de destino iSCSI es ideal para lo siguiente:

*    de **arranque sin disco y de red** mediante el uso de adaptadores de red con capacidad de arranque o un cargador de software, puede implementar cientos de servidores sin disco. Con el servidor de destino iSCSI, la implementación es rápida. En las pruebas internas de Microsoft, se implementaron 256 equipos en 34 minutos. Al usar discos duros virtuales de diferenciación, puede ahorrar hasta el 90% del espacio de almacenamiento usado para las imágenes del sistema operativo. Esto resulta perfecto en implementaciones a gran escala de imágenes de sistemas operativos idénticas, como en máquinas virtuales con Hyper-V o clústeres de informática de alto rendimiento (HPC).

* **Almacenamiento de aplicaciones de servidor**   algunas aplicaciones requieren almacenamiento en bloque. El servidor de destino iSCSI puede proveer a esas aplicaciones de almacenamiento en bloque de continuamente disponible. Dado que es posible obtener acceso al almacenamiento de forma remota, también puede consolidar el almacenamiento de bloque para ubicaciones de oficinas centrales o sucursales.

* **Almacenamiento heterogéneo**   servidor de destino iSCSI admite iniciadores iSCSI que no sean de Microsoft, lo que facilita compartir el almacenamiento en servidores en un entorno de software mixto.

* **Entornos de desarrollo, prueba, demostración y laboratorio**   cuando el servidor de destino iSCSI está habilitado, un equipo que ejecuta el sistema operativo Windows Server se convierte en un dispositivo de almacenamiento en bloque accesible a través de la red. Esto es útil para probar aplicaciones antes de implementarlas en una red de área de almacenamiento (SAN).

## <a name="block-storage-requirements"></a>Requisitos de almacenamiento en bloque

La habilitación del servidor del destino iSCSI para proporcionar almacenamiento en bloque aprovecha la red Ethernet existente. No se necesita ningún hardware adicional. Si contar con una alta disponibilidad es un criterio relevante, considere la posibilidad de instalar un clúster de alta disponibilidad. Necesita almacenamiento compartido para un clúster de alta disponibilidad (ya sea almacenamiento en hardware de canal de fibra o una matriz de almacenamiento SCSI conectada en serie (SAS)).

Si habilita la agrupación en clústeres de invitado, debe proporcionar almacenamiento de bloque. Todos los servidores que ejecutan software de Windows Server con Servidor de destino iSCSI pueden proporcionar almacenamiento de bloque.

## <a name="see-also"></a>Consulta también

[Almacenamiento de bloque de destino iSCSI, procedimientos](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh848268(v%3dws.11))  
[Novedades del servidor de destino iSCSI en Windows Server](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn305893(v%3dws.11))

