---
title: copia de seguridad de inicio de Wbadmin
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 56f3e752-d99a-4c3d-8e97-10303c37dd78
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c8eb017e8bf49191c33cd2d9f0cf4a62b08ebb07
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362344"
---
# <a name="wbadmin-start-backup"></a>copia de seguridad de inicio de Wbadmin



Crea una copia de seguridad con los parámetros especificados. Si no se especifica ningún parámetro y se ha creado una copia de seguridad diaria programada, este subcomando crea la copia de seguridad mediante la configuración de la copia de seguridad programada. Si se especifican parámetros, se crea una copia de seguridad de copia de Servicio de instantáneas de volumen (VSS) y no se actualizará el historial de los archivos de los que se realiza una copia de seguridad.

Para crear una copia de seguridad única con este subcomando, debe ser miembro del grupo operadores de **copia de seguridad** o del grupo **administradores** , o bien tener delegados los permisos adecuados. Además, debe ejecutar **Wbadmin** desde un símbolo del sistema con privilegios elevados. (Para abrir un símbolo del sistema con privilegios elevados, haga clic con el botón secundario en **símbolo del sistema** y haga clic en **Ejecutar como administrador**).

Para obtener ejemplos de cómo usar este subcomando, vea [ejemplos](#BKMK_examples).

## <a name="syntax"></a>Sintaxis

Sintaxis para Windows ° Vista y Windows Server 2008:
```
wbadmin start backup
[-backupTarget:{<BackupTargetLocation> | <TargetNetworkShare>}]
[-include:<VolumesToInclude>]
[-allCritical]
[-noVerify]
[-user:<UserName>]
[-password:<Password>]
[-noinheritAcl]
[-vssFull]
[-quiet]
```
Sintaxis para Windows ° 7 y Windows Server 2008 R2 y versiones posteriores:
```
Wbadmin start backup
[-backupTarget:{<BackupTargetLocation> | <TargetNetworkShare>}]
[-include:<ItemsToInclude>]
[-nonRecurseInclude:<ItemsToInclude>]
[-exclude:<ItemsToExclude>]
[-nonRecurseExclude:<ItemsToExclude>]
[-allCritical]
[-systemState]
[-noVerify]
[-user:<UserName>]
[-password:<Password>]
[-noInheritAcl]
[-vssFull | -vssCopy] 
[-quiet]
```

## <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|-backupTarget|Especifica la ubicación de almacenamiento para esta copia de seguridad. Requiere una letra de unidad de disco duro (f:), una ruta de acceso basada en GUID de volumen con el formato \\\\?\\volumen {GUID} o una ruta de acceso de Convención de nomenclatura universal (UNC) a una carpeta compartida remota (\\\\\<ServerName >\\\<nombreDeRecursoCompartido >\\). De forma predeterminada, la copia de seguridad se guardará en: \\\\\<ServerName >\\\<nombreDeRecursoCompartido >\\**WindowsImageBackup**\\\<ComputerBackedUp >\\.</br>Importante: Si guarda una copia de seguridad en una carpeta compartida remota, la copia de seguridad se sobrescribirá si usa la misma carpeta para hacer una copia de seguridad del mismo equipo de nuevo. Además, si se produce un error en la operación de copia de seguridad, es posible que no se realice ninguna copia de seguridad porque se sobrescribirá la copia de seguridad anterior, pero no se podrá usar la copia de seguridad más reciente. Para evitar esto, puede crear subcarpetas en la carpeta compartida remota para organizar las copias de seguridad. Si lo hace, las subcarpetas necesitarán el doble de espacio que la carpeta principal.|
|-incluir|En Windows ° Vista y Windows Server 2008, especifica la lista delimitada por comas de las letras de unidad del volumen, los puntos de montaje del volumen o los nombres de los volúmenes basados en GUID que se van a incluir en la copia de seguridad. Este parámetro solo se debe usar cuando se usa el parámetro **-backupTarget** .</br>En Windows ° 7 y Windows Server 2008 R2 y versiones posteriores, especifica la lista de elementos delimitados por comas que se van a incluir en la copia de seguridad. Se pueden incluir varios archivos, carpetas o volúmenes. Las rutas de acceso a los volúmenes se pueden especificar mediante letras de unidad, puntos de montaje o nombres basados en identificadores GUID. Si usa un nombre de volumen basado en GUID, debe terminar con una barra diagonal inversa (\\). Puede usar el carácter comodín (\*) en el nombre de archivo al especificar una ruta de acceso a un archivo. Solo se debe usar cuando se usa el parámetro **-backupTarget** .|
|-excluir|En Windows ° 7 y Windows Server 2008 R2 y versiones posteriores, especifica la lista de elementos delimitados por comas que se van a excluir de la copia de seguridad. Puede excluir archivos, carpetas o volúmenes. Las rutas de acceso a los volúmenes se pueden especificar mediante letras de unidad, puntos de montaje o nombres basados en identificadores GUID. Si usa un nombre de volumen basado en GUID, debe terminar con una barra diagonal inversa (\\). Puede usar el carácter comodín (\*) en el nombre de archivo al especificar una ruta de acceso a un archivo. Solo se debe usar cuando se usa el parámetro **-backupTarget** .|
|-nonRecurseInclude|En Windows ° 7 y Windows Server 2008 R2 y versiones posteriores, especifica la lista de elementos no recursivos delimitados por comas que se van a incluir en la copia de seguridad. Se pueden incluir varios archivos, carpetas o volúmenes. Las rutas de acceso a los volúmenes se pueden especificar mediante letras de unidad, puntos de montaje o nombres basados en identificadores GUID. Si usa un nombre de volumen basado en GUID, debe terminar con una barra diagonal inversa (\\). Puede usar el carácter comodín (\*) en el nombre de archivo al especificar una ruta de acceso a un archivo. Solo se debe usar cuando se usa el parámetro **-backupTarget** .|
|-nonRecurseExclude|En Windows ° 7 y Windows Server 2008 R2 y versiones posteriores, especifica la lista de elementos no recursivos delimitados por comas que se van a excluir de la copia de seguridad. Puede excluir archivos, carpetas o volúmenes. Las rutas de acceso a los volúmenes se pueden especificar mediante letras de unidad, puntos de montaje o nombres basados en identificadores GUID. Si usa un nombre de volumen basado en GUID, debe terminar con una barra diagonal inversa (\\). Puede usar el carácter comodín (\*) en el nombre de archivo al especificar una ruta de acceso a un archivo. Solo se debe usar cuando se usa el parámetro **-backupTarget** .|
|-allCritical|Especifica que todos los volúmenes críticos (volúmenes que contienen el estado del sistema operativo) se incluyan en las copias de seguridad. Este parámetro es útil si va a crear una copia de seguridad para la reconstrucción completa. Solo debe usarse cuando se especifica **-backupTarget** , de lo contrario se producirá un error en el comando. Se puede usar con la opción **-include** .</br>Sugerencia: el volumen de destino de una copia de seguridad de un volumen crítico puede ser una unidad local, pero no puede ser ninguno de los volúmenes incluidos en la copia de seguridad.|
|-systemState|En Windows ° 7 y Windows Server 2008 R2 y versiones posteriores, crea una copia de seguridad que incluye el estado del sistema además de cualquier otro elemento que se haya especificado con el parámetro **-include** . El estado del sistema contiene los archivos de arranque (boot. ini, NDTLDR, NTDetect.com), el registro de Windows, incluida la configuración de COM, SYSVOL (directivas de grupo y scripts de inicio de sesión), el Active Directory y NTDS. DIT en controladores de dominio y, si el servicio de certificados está instalado, el almacén de certificados. Si el servidor tiene instalado el rol de servidor Web, se incluirá el metadirectorio de IIS. Si el servidor forma parte de un clúster, también se incluirá la información del servicio de Cluster Server.|
|-noverify|Especifica que las copias de seguridad guardadas en medios extraíbles (por ejemplo, un DVD) no se comprueban en busca de errores. Si no usa este parámetro, se comprueba si hay errores en las copias de seguridad guardadas en un medio extraíble.|
|-usuario|Si la copia de seguridad se guarda en una carpeta compartida remota, especifica el nombre de usuario con permiso de escritura en la carpeta.|
|-contraseña|Especifica la contraseña para el nombre de usuario proporcionado por el parámetro **-User**.|
|-noInheritAcl|Aplica los permisos de la lista de control de acceso (ACL) que corresponden a las credenciales proporcionadas por los parámetros **-User** y **-password** para \\\\\<ServerName >\\\<sharename >\\WindowsImageBackup\\\<ComputerBackedUp >\\ (la carpeta que contiene la copia de seguridad). Para tener acceso a la copia de seguridad más adelante, debe usar estas credenciales o ser miembro del grupo administradores o del grupo operadores de copia de seguridad en el equipo con la carpeta compartida. Si no se usa **-noInheritAcl** , los permisos de la ACL de la carpeta compartida remota se aplican a la carpeta \\\<ComputerBackedUp > de forma predeterminada para que cualquier persona con acceso a la carpeta compartida remota pueda tener acceso a la copia de seguridad.|
|-vssFull|Realiza una copia de seguridad completa mediante el Servicio de instantáneas de volumen (VSS). Se realiza una copia de seguridad de todos los archivos, el historial de cada archivo se actualiza para reflejar que se ha realizado una copia de seguridad y se pueden truncar los registros de las copias de seguridad anteriores. Si no se usa este parámetro, **Wbadmin Start Backup** realiza una copia de seguridad de copia, pero no se actualiza el historial de archivos de los que se realiza la copia de seguridad.</br>PRECAUCIÓN: no use este parámetro si usa un producto que no sea Copias de seguridad de Windows Server para realizar copias de seguridad de las aplicaciones que se encuentran en los volúmenes incluidos en la copia de seguridad actual. Si lo hace, es posible que se interrumpa el tipo incremental, diferencial u otro tipo de copias de seguridad que crea el otro producto de copia de seguridad, ya que el historial en el que están confiando determina la cantidad de datos que se van a crear y podrían llevar a cabo una copia de seguridad completa. innecesariamente.|
|-vssCopy|En Windows 7 y Windows Server 2008 R2 y versiones posteriores, realiza una copia de seguridad de copia mediante VSS. Se realiza una copia de seguridad de todos los archivos, pero el historial de los archivos de los que se hace la copia de seguridad no se actualiza, de modo que se conserva toda la información sobre los archivos que se han modificado, eliminado, etc., así como los archivos de registro de la aplicación. El uso de este tipo de copia de seguridad no afecta a la secuencia de copias de seguridad incrementales y diferenciales que podrían producirse independientemente de esta copia de seguridad de copia. Este es el valor predeterminado.</br>ADVERTENCIA: no se puede usar una copia de seguridad de copia para copias de seguridad o restauraciones incrementales o diferenciales.|
|-quiet|Ejecuta el subcomando sin preguntar al usuario.|

## <a name="BKMK_examples"></a>Example

En los siguientes ejemplos se muestra cómo se puede usar el comando **Wbadmin Start Backup** en distintos escenarios de copia de seguridad:

Escenario #1
- ¿Crear una copia de seguridad de volúmenes e:, d:\\mountpoint y \\\\?\\volumen {cc566d14-4410-11d9-9d93-806e6f6e6963}
- Guarde la copia de seguridad en el volumen f:
  ```
  wbadmin start backup -backupTarget:f: -include:e:,d:\mountpoint,\\?\Volume{cc566d14-44a0-11d9-9d93-806e6f6e6963}\
  ```
  Escenario #2
- Realice una copia de seguridad única de *f:\\Folder1* y *h:\\Carpeta2* al volumen *d:* .
- Copia de seguridad del estado del sistema
- Realice una copia de seguridad de copia para que la copia de seguridad diferencial programada normalmente no se vea afectada.
  ```
  wbadmin start backup –backupTarget:d: -include:g\folder1,h:\folder2 –systemstate -vsscopy
  ```
  Escenario #3
- Realice una copia de seguridad única de *d:\\Folder1* de la que se debe realizar una copia de seguridad de forma no recursiva.
- Realice una copia de seguridad de la carpeta en la ubicación de red *\\\\copiaseguridad\\1*
- Restrinja el acceso a la copia de seguridad a los miembros del grupo **administradores** o **operadores de copia de seguridad** .
  ```
  wbadmin start backup –backupTarget: \\backupshare\backup1 -noinheritacl -nonrecurseinclude:d:\folder1
  ```

#### <a name="additional-references"></a>Referencias adicionales

-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
