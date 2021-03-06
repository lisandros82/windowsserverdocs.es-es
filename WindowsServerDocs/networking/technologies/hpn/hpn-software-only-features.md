---
title: Funciones y tecnologías de solo software
description: Estas características se implementan como parte del sistema operativo y son independientes de las NIC subyacentes. A veces, estas características requieren cierta optimización de la NIC para una operación óptima. Algunos ejemplos son las características de Hyper-v, como la calidad de servicio de las máquinas virtuales (vmQoS), las listas de Access Control (ACL) y las características que no son de Hyper-V, como la formación de equipos NIC.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 0cafb1cc-5798-42f5-89b6-3ffe7ac024ba
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/20/2018
ms.openlocfilehash: 8c354d53db983d0437749de918b2d5f12ede0f5b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405700"
---
# <a name="software-only-so-features-and-technologies"></a>Funciones y tecnologías de solo software
Las características de solo software se implementan como parte del sistema operativo y son independientes de las NIC subyacentes. A veces, estas características requieren cierta optimización de la NIC para una operación óptima. Algunos ejemplos son las características de Hyper-v, como la calidad de servicio de las máquinas virtuales (vmQoS), las listas de Access Control (ACL) y las características que no son de Hyper-V, como la formación de equipos NIC.

## <a name="access-control-lists-acls"></a>Listas de Access Control (ACL)

Una característica de Hyper-V y SDNv1 para administrar la seguridad de una máquina virtual. Esta característica se aplica a la pila de Hyper-V no virtualizada y a la pila HVNv1. Puede administrar las ACL del conmutador de Hyper-V a través de los cmdlets de PowerShell [Add-VMNetworkAdapterAcl](https://docs.microsoft.com/powershell/module/hyper-v/add-vmnetworkadapteracl?view=win10-ps) y [Remove-VMNetworkAdapterAcl](https://docs.microsoft.com/powershell/module/hyper-v/remove-vmnetworkadapteracl?view=win10-ps) .

## <a name="extended-acls"></a>ACL extendidas

Las ACL extendidas del conmutador virtual de Hyper-V permiten configurar las ACL de Puerto extendido del conmutador virtual de Hyper-V para proporcionar protección de firewall y aplicar directivas de seguridad para las máquinas virtuales de inquilino en los centros de recursos. Dado que las ACL de puerto se configuran en el conmutador virtual de Hyper-V en lugar de en las máquinas virtuales, el administrador puede administrar las directivas de seguridad para todos los inquilinos en un entorno de varios inquilinos.

Puede administrar las ACL extendidas del conmutador de Hyper-V a través de los cmdlets de PowerShell [Add-VMNetworkAdapterExtendedAcl](https://docs.microsoft.com/powershell/module/hyper-v/add-vmnetworkadapterextendedacl?view=win10-ps) y [Remove-VMNetworkAdapterExtendedAcl](https://docs.microsoft.com/powershell/module/hyper-v/remove-vmnetworkadapteracl?view=win10-ps) .

>[!TIP] 
>Esta característica se aplica a la pila HNVv1. En el caso de las ACL de la pila de SDN, consulte las ACL de redes definidas por software (SDN) a continuación.

Para obtener más información acerca de las listas de Access Control de puertos extendidos en esta biblioteca, vea [crear directivas de seguridad con listas de Access Control de puertos extendidos](https://docs.microsoft.com/windows-server/virtualization/hyper-v-virtual-switch/Create-Security-Policies-with-Extended-Port-Access-Control-Lists).

## <a name="nic-teaming"></a>Formación de equipos NIC

La formación de equipos NIC, también denominada "enlace NIC", es la agregación de varios puertos NIC a una entidad que el host percibe como un solo puerto NIC. La formación de equipos NIC protege frente al error de un único puerto NIC (o el cable conectado a él). También agrega tráfico de red para un rendimiento más rápido. Para obtener más información, consulte [formación de equipos NIC](https://docs.microsoft.com/windows-server/networking/technologies/nic-teaming/nic-teaming).

Con Windows Server 2016 tiene dos maneras de realizar la formación de equipos:

1.  Solución de formación de equipos de Windows Server 2012

2.  Windows Server 2016 switch Embedded Teaming (SET)


## <a name="rsc-in-the-vswitch"></a>RSC en vSwitch

La fusión de segmentos de recepción (RSC) en el vSwitch es una característica que toma paquetes que forman parte del mismo flujo y llegan entre interrupciones de red y los combina en un solo paquete antes de entregarlos al sistema operativo. El conmutador virtual de Windows Server 2019 tiene esta característica. Para obtener más información acerca de esta característica, vea el apartado sobre [la fusión de segmentos de recepción en el vSwitch](https://docs.microsoft.com/windows-server/networking/technologies/hpn/rsc-in-the-vswitch).

## <a name="software-defined-networking-sdn-acls"></a>ACL de redes definidas por software (SDN)

La extensión de SDN en Windows Server 2016 mejoró la compatibilidad con las ACL. En la pila de Windows Server 2016 SDN V2, se usan las ACL de SDN en lugar de las ACL y las ACL extendidas. Puede usar la controladora de red para administrar las ACL de SDN. 

## <a name="sdn-quality-of-service-qos"></a>Calidad de servicio (QoS) de SDN

La extensión de SDN en Windows Server 2016 mejoró las maneras de proporcionar control de ancho de banda (reservas de salida, límites de salida y límites de entrada) en una 5-tupla. Normalmente, estas directivas se aplican en el nivel vNIC o vmNIC, pero puede hacerlas mucho más específicas. En la pila de Windows Server 2016 SDN V2, se usa la QoS de SDN en lugar de vmQoS. Puede usar la controladora de red para administrar la QoS de SDN.

## <a name="switch-embedded-teaming-set"></a>Cambiar la formación de equipos incrustada (SET)

SET es una solución alternativa para la formación de equipos NIC que puede usar en entornos que incluyen Hyper-V y la pila de redes definidas por software (SDN) en Windows Server 2016. El conjunto integra la funcionalidad de formación de equipos NIC en el conmutador virtual de Hyper-V. Para obtener información sobre cómo cambiar la formación de equipos incrustados en esta biblioteca, vea [acceso directo a memoria remota (RDMA) y switch Embedded Teaming (Set)](https://docs.microsoft.com/windows-server/virtualization/hyper-v-virtual-switch/rdma-and-switch-embedded-teaming).

## <a name="virtual-receive-side-scaling-vrss"></a>Ajuste de escala en lado de recepción virtual (vRSS)

El software vRSS se usa para distribuir el tráfico entrante destinado a una máquina virtual en varios procesadores lógicos (LPs) de la máquina virtual. El software vRSS proporciona a la máquina virtual la capacidad de controlar más tráfico de red que un solo LP podría controlar. Para obtener más información, vea [ajuste de escala en lado de recepción virtual (vRSS)](https://docs.microsoft.com/windows-server/networking/technologies/vrss/vrss-top).

## <a name="virtual-machine-quality-of-service-vmqos"></a>Calidad de servicio de la máquina virtual (vmQoS)

Calidad de servicio de la máquina virtual es una característica de Hyper-V que permite al conmutador establecer límites en el tráfico generado por cada máquina virtual. También permite que una máquina virtual Reserve una cantidad de ancho de banda en la conexión de red externa para que una máquina virtual no pueda privar a otra máquina virtual para el ancho de banda. En la pila de Windows Server 2016 SDN V2, la QoS de SDN reemplaza a vmQoS.

vmQoS puede establecer límites de salida y reservas de salida. Debe determinar el modo de reserva de salida (peso relativo o ancho de banda absoluto) antes de crear el conmutador de Hyper-V.

-  Determine el modo de reserva de salida con el parámetro – MinimumBandwidthMode del cmdlet de PowerShell New-VMSwitch.

-  Establezca el valor del límite de salida con el parámetro – MaximumBandwidth en el cmdlet de PowerShell Set-VMNetworkAdapter.

-  Establezca el valor de la reserva de salida con cualquiera de los siguientes parámetros del cmdlet Set VMNetworkAdapter PowerShell:

   -  Si el parámetro – MinimumBandwidthMode del cmdlet New-VMSwitch es absoluto, establezca el parámetro – MinimumBandwidthAbsolute en el cmdlet Set VMNetworkAdapter.

   -  Si el parámetro – MinimumBandwidthMode del cmdlet New-VMSwitch es weight, establezca el parámetro – MinimumBandwidthWeight en el cmdlet Set VMNetworkAdapter.

Debido a las limitaciones del algoritmo que se usa para esta característica, se recomienda que el peso más alto o el ancho de banda absoluto no sea más de 20 veces el menor peso o ancho de banda absoluto. Si se necesita más control, considere la posibilidad de usar la pila de SDN y la característica SDN-QoS.


---