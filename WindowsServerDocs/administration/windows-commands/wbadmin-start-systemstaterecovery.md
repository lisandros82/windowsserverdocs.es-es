---
title: Inicio de systemstaterecovery de Wbadmin
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 208b1be9-3452-4aba-bb49-46bc587fca96
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6ae534eed26629be264b698869edc57232e2b571
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362224"
---
# <a name="wbadmin-start-systemstaterecovery"></a>Inicio de systemstaterecovery de Wbadmin



Realiza una recuperación de estado del sistema en una ubicación y desde una copia de seguridad que especifique.

> [!NOTE]
> Copias de seguridad de Windows Server no realiza copias de seguridad ni recupera subárboles de usuario del registro (HKEY_CURRENT_USER) como parte de la copia de seguridad del estado del sistema o de la recuperación del estado del sistema.

Para realizar una recuperación del estado del sistema con este subcomando, debe ser miembro del grupo **operadores de copia de seguridad** o del grupo **administradores** , o bien tener delegados los permisos adecuados. Además, debe ejecutar **Wbadmin** desde un símbolo del sistema con privilegios elevados. (Para abrir un símbolo del sistema con privilegios elevados, haga clic con el botón secundario en **símbolo del sistema**y, a continuación, haga clic en **Ejecutar como administrador**).

Para obtener ejemplos de cómo utilizar este comando, consulte [Ejemplos](#BKMK_examples).

## <a name="syntax"></a>Sintaxis

Sintaxis para Windows Server 2008:
```
wbadmin start systemstaterecovery
-version:<VersionIdentifier>
-showsummary
[-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}]
[-machine:<BackupMachineName>]
[-recoveryTarget:<TargetPathForRecovery>]
[-authsysvol]
[-quiet]
```
Sintaxis para Windows Server 2008 R2 o posterior:
```
wbadmin start systemstaterecovery
-version:<VersionIdentifier>
-showsummary
[-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}]
[-machine:<BackupMachineName>]
[-recoveryTarget:<TargetPathForRecovery>]
[-authsysvol]
[-autoReboot]
[-quiet]
```

## <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|-versión|Especifica el identificador de la versión de la copia de seguridad que se va a recuperar en formato MM/DD/AAAA-HH: MM. Si no conoce el identificador de la versión, escriba **Wbadmin get Versions**.|
|-showsummary|Informa del Resumen de la última recuperación del estado del sistema (después del reinicio necesario para completar la operación). Este parámetro no puede ir acompañado de otros parámetros.|
|-backupTarget|Especifica la ubicación de almacenamiento que contiene la copia de seguridad o las copias de seguridad que desea recuperar. Este parámetro es útil cuando la ubicación de almacenamiento es diferente de donde se almacenan normalmente las copias de seguridad de este equipo.|
|-equipo|Especifica el nombre del equipo que desea recuperar. Este parámetro es útil cuando se ha realizado una copia de seguridad de varios equipos en la misma ubicación. Debe usarse cuando se especifica el parámetro **-backupTarget** .|
|-recoveryTarget|Especifica el directorio en el que se va a restaurar. Este parámetro es útil si la copia de seguridad se restaura en una ubicación alternativa.|
|-authsysvol|Si se usa, realiza una restauración autoritativa de SYSVOL (el directorio compartido del volumen del sistema).|
|-autoReboot|Especifica que se reinicie el sistema al final de la operación de recuperación del estado del sistema. Este parámetro solo es válido para una recuperación en la ubicación original. No se recomienda usar este parámetro si necesita realizar pasos después de la operación de recuperación.|
|-quiet|Ejecuta el subcomando sin preguntar al usuario.|

## <a name="BKMK_examples"></a>Example

- Para realizar una recuperación del estado del sistema de la copia de seguridad de 03/31/2013 a las 9:00 A.M., escriba:  
  ```
  wbadmin start systemstaterecovery -version:03/31/2013-09:00
  ```  
- Para realizar una recuperación del estado del sistema de la copia de seguridad de 04/30/2013 a las 9:00 A.M. que está almacenado en el recurso compartido \\\\servername\share para Server01, escriba:  
  ```
  wbadmin start systemstaterecovery -version:04/30/2013-09:00 -backupTarget:\\servername\share -machine:server01
  ```

#### <a name="additional-references"></a>Referencias adicionales

-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   Cmdlet [Start-WBSystemStateRecovery](https://technet.microsoft.com/library/jj902449.aspx)