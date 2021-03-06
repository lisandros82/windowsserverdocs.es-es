---
title: Configuración de Servicio de mantenimiento
ms.prod: windows-server
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
ms.assetid: ''
author: cosmosdarwin
ms.date: 08/14/2017
ms.openlocfilehash: 1b10d7c5432b10262e8df85d427f17f402d4f64a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71361043"
---
# <a name="health-service-settings"></a>Configuración de Servicio de mantenimiento
> Se aplica a: Windows Server 2019 y Windows Server 2016

El Servicio de mantenimiento es una nueva característica de Windows Server 2016 que mejora la supervisión cotidiana y la experiencia operativa de los clústeres que ejecutan Espacios de almacenamiento directo.

Muchos de los parámetros que rigen el comportamiento del Servicio de mantenimiento se exponen como valores de configuración. Puede modificarlos para optimizar la intensidad de los errores o las acciones, activar o desactivar determinados comportamientos, etc.

Use el siguiente cmdlet de PowerShell para establecer o modificar la configuración.

### <a name="usage"></a>Uso

```PowerShell
Get-StorageSubSystem Cluster* | Set-StorageHealthSetting -Name <SettingName> -Value <Value>  
```

#### <a name="example"></a>Ejemplo

```PowerShell
Get-StorageSubSystem Cluster* | Set-StorageHealthSetting -Name "System.Storage.Volume.CapacityThreshold.Warning" -Value 70
```

### <a name="common-settings"></a>Configuración común

A continuación se enumeran algunas opciones de configuración que se modifican normalmente, junto con sus valores predeterminados.

#### <a name="volume-capacity-threshold"></a>Umbral de capacidad del volumen

```
"System.Storage.Volume.CapacityThreshold.Enabled"  = True
"System.Storage.Volume.CapacityThreshold.Warning"  = 80
"System.Storage.Volume.CapacityThreshold.Critical" = 90
```

#### <a name="pool-reserve-capacity-threshold"></a>Umbral de capacidad de reserva de grupo

```
"System.Storage.StoragePool.CheckPoolReserveCapacity.Enabled" = True
```

#### <a name="physical-disk-lifecycle"></a>Ciclo de vida del disco físico

```
"System.Storage.PhysicalDisk.AutoPool.Enabled"                             = True
"System.Storage.PhysicalDisk.AutoRetire.OnLostCommunication.Enabled"       = True
"System.Storage.PhysicalDisk.AutoRetire.OnUnresponsive.Enabled"            = True
"System.Storage.PhysicalDisk.AutoRetire.DelayMs"                           = 900000 (i.e. 15 minutes)
"System.Storage.PhysicalDisk.Unresponsive.Reset.CountResetIntervalSeconds" = 360 (i.e. 60 minutes)
"System.Storage.PhysicalDisk.Unresponsive.Reset.CountAllowed"              = 3
```

#### <a name="supported-components-document"></a>Documento de componentes admitidos

Vea la sección anterior.

#### <a name="firmware-rollout"></a>Lanzamiento de firmware

```
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.SingleDrive.Enabled"       = True
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.Enabled"           = True
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.LongDelaySeconds"  = 604800 (i.e. 7 days)
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.ShortDelaySeconds" = 86400 (i.e. 1 day)
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.LongDelayCount"    = 1
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.FailureTolerance"  = 3
```

#### <a name="platform--quiescence"></a>Plataforma/inactividad

```
"Platform.Quiescence.MinDelaySeconds" = 120 (i.e. 2 minutes)
"Platform.Quiescence.MaxDelaySeconds" = 420 (i.e. 7 minutes)
```

#### <a name="metrics"></a>metrics

```
"System.Reports.ReportingPeriodSeconds" = 1
```

#### <a name="debugging"></a>Depuración

```
"System.LogLevel" = 4
```

## <a name="see-also"></a>Vea también

- [Servicio de mantenimiento en Windows Server 2016](health-service-overview.md)
- [Espacios de almacenamiento directo en Windows Server 2016](../storage/storage-spaces/storage-spaces-direct-overview.md)
