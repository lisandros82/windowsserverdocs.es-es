---
title: 'Roles, servicios de rol y características no en los contenedores Server Core: Windows Server, versión 1803'
description: Obtenga información sobre los roles y las características que se han quitado de la imagen de contenedor Server Core para Windows Server.
ms.prod: windows-server
ms.mktglfcycl: manage
ms.sitesec: library
author: lizap
ms.localizationpriority: medium
ms.date: 05/07/2018
ms.openlocfilehash: 41b5a9ac32066f1b2a41de84f66b9be79252c336
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383409"
---
# <a name="roles-role-services-and-features-not-in-server-core-containers---windows-server-version-1803"></a>Roles, servicios de rol y características no en los contenedores Server Core: Windows Server, versión 1803

> Se aplica a: Windows Server, versión 1803

En Windows Server, versión 1803, hemos [reducido el tamaño total de la imagen de contenedor Server Core a **1,58 GB**](https://blogs.technet.microsoft.com/virtualization/2018/01/22/a-smaller-windows-server-core-container-with-better-application-compatibility/). La manera de hacerlo es optimizar la arquitectura y quitar las cosas que no necesita en un [contenedor Server Core](https://docs.microsoft.com/virtualization/windowscontainers/about/). Algunos eran cosas que no funcionaban en los contenedores, algunos eran roles y características que no se usaban. 

> [!IMPORTANT]
> Se han quitado de la imagen de **contenedor** Server Core, no de [Server Core](server-core-roles-and-services.md). 

Esta es la lista completa de las características y los roles que se han quitado de la imagen de contenedor Server Core:

<div style='font-size:9.0pt'>

<br>ADCertificateServicesRole
<br>AuthManager
<br>BitLocker-utilidades
<br>BitLocker
<br>BITS
<br>BITSExtensions: carga
<br>CCFFilter
<br>CertificateEnrollmentPolicyServer
<br>CertificateEnrollmentServer
<br>CertificateServices
<br>Infraestructura de ClientForNFS
<br>Contenedores
<br>CoreFileServer
<br>DataCenterBridging-LLDP-herramientas
<br>DataCenterBridging
<br>Desduplicación: núcleo
<br>DeviceHealthAttestationService
<br>DFSN: servidor
<br>DFSR-Infrastructure-ServerEdition
<br>DirectoryServices: ADAM
<br>DirectoryServices-DomainController
<br>Desmontaje-QoS
<br>EnhancedStorage
<br>FailoverCluster-AdminPak
<br>FailoverCluster-AutomationServer
<br>FailoverCluster-CmdInterface
<br>FailoverCluster-FullServer
<br>FailoverCluster: PowerShell
<br>Servicios de archivo
<br>FileServerVSSAgent
<br>Infraestructura de FRS
<br>FSRM-Infrastructure-Services
<br>FSRM-infraestructura
<br>HardenedFabricEncryptionTask
<br>HostGuardian
<br>Paquete HostGuardianService
<br>IdentityServer-SecurityTokenService
<br>IPAMClientFeature
<br>IPAMServerFeature
<br>iSCSITargetServer: PowerShell
<br>iSCSITargetServer
<br>iSCSITargetStorageProviders
<br>iSNS_Service
<br>Concesión de licencias
<br>LightweightServer
<br>Microsoft-Hyper-V-Management-clients
<br>Microsoft-Hyper-V-sin conexión
<br>Microsoft-Hyper-V-en línea
<br>Microsoft-Hyper-V
<br>Paquete Microsoft-Windows-FCI-Client-
<br>Microsoft-Windows-GroupPolicy-ServerAdminTools-Update
<br>Microsoft-Windows-Subsystem-Linux
<br>Infraestructura de MSRDC
<br>MultipathIo
<br>NetworkController
<br>NetworkControllerTools
<br>NetworkDeviceEnrollmentServices
<br>NetworkLoadBalancingFullServer
<br>NetworkVirtualization
<br>OnlineRevocationServices
<br>P2P-PnrpOnly
<br>PeerDist
<br>Impresión: cliente-GUI
<br>Impresión: LPDPrintService
<br>Impresión-Server-Foundation-Features
<br>Impresión: rol de servidor
<br>QWAVE
<br>RasRoutingProtocols
<br>Servicios de escritorio remoto
<br>RemoteAccess
<br>RemoteAccessMgmtTools
<br>RemoteAccessPowerShell
<br>RemoteAccessServer
<br>ResumeKeyFilter
<br>RightsManagementServices: rol
<br>RightsManagementServices
<br>RMS-Federación
<br>SBMgr-UI
<br>ServerCore-drivers-general-WOW64
<br>ServerCore-drivers-general
<br>Infraestructura de ServerForNFS
<br>ServerManager-Core-RSAT-Feature-Tools
<br>ServerMediaFoundation
<br>ServerMigration
<br>SessionDirectory
<br>SetupAndBootEventCollection
<br>ShieldedVMToolsAdminPack
<br>SMB1Protocol: servidor
<br>SmbDirect
<br>SMBHashGeneration
<br>SmbWitness
<br>SNMP
<br>SoftwareLoadBalancer
<br>Storage-réplica-AdminPack
<br>Réplica de almacenamiento
<br>TPM-PSH-cmdlets
<br>UpdateServices-base de datos
<br>UpdateServices-servicios
<br>UpdateServices-WidDatabase
<br>UpdateServices
<br>VmHostAgent
<br>VolumeActivation: rol completo
<br>Proxy de aplicación Web
<br>WebAccess
<br>WebEnrollmentServices
<br>Windows-Defender
<br>WindowsServerBackup
<br>WindowsStorageManagementService
<br>WINSRuntime
<br>WMISnmpProvider
<br>WorkFolders: servidor
<br>WSS-Product-Package

</div>