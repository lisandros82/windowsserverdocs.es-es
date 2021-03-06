---
title: Hyper-V en Windows Server
description: Proporciona vínculos a artículos clave sobre cómo probar, planear, implementar y administrar Hyper-V
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0baef6b8-598c-4fe0-9f31-5869fc4e0f69
author: KBDAzure
ms.author: kathydav
ms.date: 10/07/2016
ms.openlocfilehash: 558733e3472578d1df413fe220f1846debc0f358
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71366844"
---
# <a name="hyper-v-on-windows-server"></a>Hyper-V en Windows Server

>Se aplica a: Windows Server 2016, Windows Server 2019

El rol Hyper-V de Windows Server le permite crear un entorno informático virtualizado en el que puede crear y administrar máquinas virtuales. Puede ejecutar varios sistemas operativos en un equipo físico y aislar los sistemas operativos entre sí. Con esta tecnología, puede mejorar la eficacia de los recursos informáticos y liberar los recursos de hardware.

Vea los temas de la tabla siguiente para obtener más información acerca de Hyper-V en Windows Server.

## <a name="hyper-v-resources-for-it-pros"></a>Recursos de Hyper-V para profesionales de ti

|Tarea |Recursos|
|---|---|
|![Icono de marca de verificación y documento para mostrar que se cumplen los requisitos](media/All_Symbols_MeetsRequirements.png)|**Evaluación de Hyper-V**<br /><br />[información general sobre la tecnología de Hyper-V](Hyper-V-Technology-Overview.md) - <br />- las novedades [de Hyper-V en Windows Server](What-s-new-in-Hyper-V-on-Windows.md)<br />- [requisitos del sistema para Hyper-V en Windows Server](System-requirements-for-Hyper-V-on-Windows.md)<br />- [sistemas operativos invitados de Windows admitidos para Hyper-V](Supported-Windows-guest-operating-systems-for-Hyper-V-on-Windows.md) <br />- [máquinas virtuales Linux y FreeBSD compatibles](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)<br />[compatibilidad de características de - por generación e invitado](Hyper-V-feature-compatibility-by-generation-and-guest.md) <br /><br />**Planeación de Hyper-V**<br /><br />¿- debo [crear una máquina virtual de generación 1 o 2 en Hyper-V?](plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md) <br />[plan de - para la escalabilidad de Hyper-V en Windows Server](plan/plan-hyper-v-scalability-in-windows-server.md) <br />[plan de - para la red de Hyper-V en Windows Server](plan/plan-hyper-v-networking-in-windows-server.md) <br />[plan de - para la seguridad de Hyper-V en Windows Server](plan/plan-hyper-v-security-in-windows-server.md)|
|![Icono cursor y proyección solar](media/All_Symbols_GetStarted.png)|**Introducción a Hyper-V**<br /><br />- [Descargar e instalar Windows Server 2019](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019)<br /><br />**Opción de instalación Server Core o GUI de Windows Server 2019 como host de máquina virtual**<br /><br />- [instalar el rol de Hyper-V en Windows Server](get-started/Install-the-Hyper-V-role-on-Windows-Server.md)<br />- [crear un conmutador virtual para máquinas virtuales de Hyper-V](get-started/Create-a-virtual-switch-for-Hyper-V-virtual-machines.md)<br />- [crear una máquina virtual en Hyper-V](get-started/Create-a-virtual-machine-in-Hyper-V.md)|
|![Icono de personas y herramientas](media/All_Symbols_Administrator.png)|**Actualizar hosts de Hyper-V y máquinas virtuales**<br /><br />- [actualizar nodos de clúster de Windows Server](../../failover-clustering/Cluster-Operating-System-Rolling-Upgrade.md)<br />- [actualizar la versión de la máquina virtual](deploy/Upgrade-virtual-machine-version-in-Hyper-V-on-Windows-or-Windows-Server.md)<br /><br />**Configurar y administrar Hyper-V**<br /><br />- [configurar hosts para la migración en vivo sin clústeres de conmutación por error](deploy/Set-up-hosts-for-live-migration-without-Failover-Clustering.md)<br />- la [Administración de nano Server de forma remota](../../get-started/manage-nano-server.md)<br />- [elegir entre los puntos de control estándar o de producción](manage/Choose-between-standard-or-production-checkpoints-in-Hyper-V.md)<br />- [habilitar o deshabilitar puntos de control](manage/Enable-or-disable-checkpoints-in-Hyper-V.md)<br />- [administrar máquinas virtuales Windows con PowerShell Direct](manage/Manage-Windows-virtual-machines-with-PowerShell-Direct.md)<br />- [configurar la réplica de Hyper-V](manage/Set-up-Hyper-V-Replica.md)|
|![Icono de burbujas de conversación](media/All_Symbols_Chat.png)|**Blogs**<br /><br />Consulte las últimas publicaciones de los administradores de programas, jefes de producto, desarrolladores y evaluadores de los equipos de virtualización de Microsoft y Hyper-V.<br /><br />[blog de virtualización](https://blogs.technet.com/b/virtualization/) de - <br />Blog de - [Windows Server](https://blogs.technet.com/b/windowsserver/)<br />- [blog de virtualización de Ben Armstrong](https://blogs.msdn.com/b/virtual_pc_guy/) (archivado)|
|![Icono de grupo de usuarios](media/All_Symbols_Users_Group.png)|**Foro y grupos de noticias**<br /><br />¿Tiene alguna pregunta? Hable con sus compañeros, MVP y el equipo de producto de Hyper-V.<br /><br />- [comunidad de Windows Server](https://techcommunity.microsoft.com/t5/Windows-Server/ct-p/Windows-Server)<br />[Foro de TechNet sobre el - de Windows Server Hyper-V](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverhyperv)|

## <a name="related-technologies"></a>Tecnologías relacionadas

En la tabla siguiente se enumeran las tecnologías que puede usar en su entorno informático de virtualización.

|Tecnología|Descripción|
|--------------|---------------|
|[Cliente Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/index)|Tecnología de virtualización incluida con Windows 8, Windows 8.1 y Windows 10 que puede instalar a través de **programas y características** en el **Panel de control**.|
|[Clúster de conmutación por error](https://docs.microsoft.com/windows-server/failover-clustering/whats-new-in-failover-clustering)|Característica de Windows Server que proporciona alta disponibilidad para hosts de Hyper-V y máquinas virtuales.|
|[Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm/overview)|Componente de System Center que proporciona una solución de administración para el centro de recursos virtualizado. Puede configurar y administrar los hosts de virtualización, las redes y los recursos de almacenamiento para que pueda crear e implementar máquinas virtuales y servicios para nubes privadas que haya creado.|
|[Contenedores de Windows](https://docs.microsoft.com/virtualization/windowscontainers/)|Use los contenedores de Windows Server y Hyper-V para proporcionar entornos estandarizados para equipos de desarrollo, pruebas y producción.|