---
ms.assetid: 134840f3-c416-4a10-ad73-ef7855b206f7
title: Información general de arranque de destino iSCSI
ms.prod: windows-server
ms.technology: storage-iscsi
ms.topic: article
author: JasonGerend
manager: dougkim
ms.author: jgerend
ms.date: 09/11/2018
ms.openlocfilehash: 9c359c7929ff90968d16e92b1128f4fc8ebde37c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402982"
---
# <a name="iscsi-target-boot-overview"></a>Información general de arranque de destino iSCSI

> Se aplica a: Windows Server 2016

El Servidor de destino iSCSI en Windows Server puede arrancar cientos de equipos desde una sola imagen de sistema operativo que se almacena en una ubicación centralizada. Esto mejora la eficacia, la facilidad de uso, la disponibilidad y la seguridad.  
  
## <a name="BKMK_OVER"></a>Descripción de la característica  
Mediante el uso de discos duros virtuales de diferenciación \(los VHD\), puede usar una sola imagen de sistema operativo \(la\) "imagen maestra" para arrancar hasta 256 equipos. Por ejemplo, supongamos que ha implementado Windows Server con una imagen de sistema operativo de aproximadamente 20 GB y usó dos unidades de disco reflejadas para que actúen como el volumen de arranque. Hubiera necesitado aproximadamente 10 TB de almacenamiento solo para la imagen del sistema operativo para arrancar 256 equipos. Con el servidor de destino iSCSI, usará 40 GB para la imagen base de sistema operativo y 2 GB para los discos duros virtuales de diferenciación por cada instancia de servidor, lo que hace un total de 552 GB para las imágenes de sistema operativo. Esto permite ahorrar más del 90 % del almacenamiento solamente para las imágenes de sistema operativo.  
  
## <a name="BKMK_APP"></a>Aplicaciones prácticas  
El uso de una imagen de sistema operativo controlada ofrece las siguientes ventajas:  
  
**Es más segura y fácil de administrar.** Algunas empresas necesitan proteger sus datos bloqueando físicamente el almacenamiento en una ubicación centralizada. En este escenario, los servidores obtienen acceso a los datos de forma remota, incluida la imagen de sistema operativo. Con el servidor de destino iSCSI, los administradores pueden administrar las imágenes de inicio del sistema operativo de forma centralizada y controlar las aplicaciones que se utilizarán para la imagen maestra.  
  
**Implementación rápida.** Dado que la imagen maestra se prepara con Sysprep, cuando los equipos arrancan desde la imagen maestra, omiten la fase de copia e instalación del archivo que tiene lugar durante la instalación de Windows y pasan directamente a la fase de personalización. En pruebas internas de Microsoft, se implementaron 256 equipos en 34 minutos.  
  
**Recuperación rápida.** Como las imágenes de sistema operativo se hospedan en el equipo que ejecuta el servidor de destino iSCSI, si debe reemplazarse un cliente sin disco, el nuevo equipo puede seleccionar la imagen de sistema operativo y arrancar de inmediato.  
  
> [!NOTE]  
> Varios proveedores ofrecen una solución de arranque de red de área de almacenamiento \(SAN\), que el Servidor de destino iSCSI puede usar en Windows Server con hardware económico.  
  
## <a name="BKMK_HARD"></a>Requisitos de hardware  
El servidor de destino iSCSI no requiere hardware especial para la verificación funcional. En los centros de datos con grandes implementaciones de escalado de\-, el diseño debe validarse en relación con el hardware específico. Como referencia, las pruebas internas de Microsoft indicaron que una implementación de equipo 256 requería necesitaba 15.000\-RPM en una configuración de RAID 10 para almacenamiento. El ancho de banda óptimo es de 10 GB. El cálculo general es de servidores de arranque de 60 iSCSI por adaptador de red de 1 GB.  
  
No se necesita un adaptador de red para este escenario y puede usarse un cargador de arranque de software \(como el firmware de arranque de código abierto de iPXE\).  
  
## <a name="BKMK_SOFT"></a>Requisitos de software  
El servidor de destino iSCSI se puede instalar como parte del servicio del rol Servicios de iSCSI y archivo en el administrador del servidor.

> [!NOTE]
> No se admite el arranque de Nano Server desde iSCSI (ya sea desde el Servidor de destino iSCSI de Windows o una implementación de destino de terceros).

## <a name="see-also"></a>Consulte también
* [Servidor de destino iSCSI](https://technet.microsoft.com/library/hh848272(v=ws.11).aspx)
* [cmdlets del iniciador iSCSI](https://technet.microsoft.com/library/hh826099(v=wps.640).aspx)
* [cmdlets del servidor de destino iSCSI](https://technet.microsoft.com/library/jj612803(v=wps.630).aspx)