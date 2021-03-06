---
ms.assetid: ''
title: Versión preliminar de Insider para características del servicio de hora de Windows en Windows Server 2019
description: Nuevas características del servicio de hora de Windows en Windows Server 2019
author: shortpatti
ms.author: pashort
ms.date: 09/05/2018
ms.topic: article
ms.prod: windows-server
ms.technology: networking
ms.openlocfilehash: 38682afa37a4c6882ee2e63a4abf4cd9fdbd2b27
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405214"
---
# <a name="insider-preview"></a>Versión preliminar de Insider 


## <a name="leap-second-support"></a>Compatibilidad con segundo intercalar


>Se aplica a: Windows Server 2019 y Windows 10, versión 1809

Un segundo intercalar es un ajuste ocasional de 1 segundo a la hora UTC. A medida que la rotación de la tierra se ralentiza, la hora [UTC](https://en.wikipedia.org/wiki/Coordinated_Universal_Time) (una escala de tiempo atómica) difiere de la [hora solar media](https://en.wikipedia.org/wiki/Solar_time#Mean_solar_time) o astronómica.  Una vez que la hora UTC ha divergido un máximo de 0,9 segundos, se inserta un [segundo intercalar](https://en.wikipedia.org/wiki/Leap_second) para mantener la hora UTC sincronizada con la hora solar media.

Los segundos intercalares se han vuelto importantes para cumplir con los requisitos normativos de precisión y rastreabilidad tanto en el Estados Unidos como en la Unión Europea.

Para obtener más información, consulte:

-  Nuestro [blog de anuncios](https://blogs.technet.microsoft.com/networking/2018/07/18/top10-ws2019-hatime/)

-  La guía de validación para [desarrolladores](https://aka.ms/Dev-LeapSecond)

-  La guía de validación para [profesionales de TI](https://aka.ms/ITPro-LeapSecond)


## <a name="precision-time-protocol"></a>Protocolo de tiempo de precisión

>Se aplica a: Windows Server 2019 y Windows 10, versión 1809

Un nuevo proveedor de hora incluido en Windows Server 2019 y Windows 10 (versión 1809) te permite sincronizar la hora mediante el Protocolo de tiempo de precisión (PTP). A medida que la hora se distribuye a través de una red, encuentra un retraso (latencia) que, si no se tiene en cuenta, o si no es simétrico, hace que cada vez sea más difícil comprender la marca de tiempo enviada desde el servidor de hora. PTP permite que los dispositivos de red sumen la latencia introducida por cada dispositivo de red a las mediciones de tiempo, con lo que se proporciona una muestra de hora mucho más precisa para el cliente Windows.

Para obtener más información, consulte:

-  Nuestro [blog de anuncios](https://blogs.technet.microsoft.com/networking/2018/07/18/top10-ws2019-hatime/)

-  La guía de validación para [profesionales de TI](https://aka.ms/PTPValidation)


## <a name="software-timestamping"></a>Marca de tiempo de software

>Se aplica a: Windows Server 2019 y Windows 10, versión 1809

Al recibir un paquete de control de hora a través de la red desde un servidor de hora, la pila de red del sistema operativo tiene que procesarlo antes de que se use en el servicio de hora. Cada componente de la pila de red introduce una cantidad variable de latencia que afecta a la precisión de la medición de la hora.

![marca de tiempo de software](../media/Windows-Time-Service/software-timestamping.png)

Para solucionar este problema, la marca de tiempo de software nos permite insertar la marca de tiempo en paquetes antes y después de los "componentes de red de Windows" que se muestran anteriormente para tener en cuenta el retraso en el sistema operativo.

Para obtener más información, consulte:

-  Nuestro [blog de anuncios](https://blogs.technet.microsoft.com/networking/2018/07/18/top10-ws2019-hatime/)

-  La guía de validación para [profesionales de TI](https://github.com/Microsoft/SDN/blob/master/FeatureGuide/Validation%20Guide%20-%20RS5%20-%20Software%20Timestamping.docx)



---