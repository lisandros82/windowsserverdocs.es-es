---
title: dfsrmig
description: 'Tema de los comandos de Windows para ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1b6a464-6a93-4e66-9969-04f175226d8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: da05aec5ca5a5634585c5f5406181c5c90ee3a30
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856946"
---
# <a name="dfsrmig"></a>dfsrmig

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

El `dfsrmig` comando migra desde el servicio de replicación de archivos (FRS) de la replicación de SYSvol para la replicación del sistema de archivos distribuido (DFS), se proporciona información sobre el progreso de la migración y modifica los objetos de Active Directory Domain Services (AD DS) para admite la migración.
Para obtener ejemplos de cómo usar este comando, consulte el [ejemplos](#BKMK_examples) sección más adelante en este documento.
## <a name="syntax"></a>Sintaxis
```
dfsrmig [/SetGlobalState <state> | /GetGlobalState | /GetMigrationState | /createGlobalObjects | 
/deleteRoNtfrsMember [<read_only_domain_controller_name>] | /deleteRoDfsrMember [<read_only_domain_controller_name>] | /?]
```
## <a name="parameters"></a>Parámetros
|Parámetro|Descripción|
|-------|--------|
|/ SetGlobalState <state>|Establece el estado de migración global deseado para el dominio en el estado que se corresponde con el valor especificado por *estado*.<br /><br />Para continuar a través de los procesos de reversión o de la migración, use este comando para recorrer cíclicamente los estados válidos. Esta opción le permite iniciar y controlar el proceso de migración estableciendo el estado de migración global en AD DS en el emulador de PDC. Si el emulador de PDC no está disponible, este comando produce un error.<br /><br /> Solo se puede establecer el estado de migración global a un estado estable. Los valores válidos para *estado*, por lo tanto, son **0** para el estado de inicio, **1** para el estado preparado, **2** para el estado redirigido, y **3** para el estado eliminado.<br /><br />Migración en el estado de eliminación es irreversible y no es posible deshacer desde ese estado, así que use un valor de **3** para *estado* solo cuando esté totalmente committd al uso de la replicación DFS para SYSvol replicación.|
|/GetGlobalState|Recupera el estado actual de la migración global para el dominio de la copia local de la base de datos de AD DS, cuando se ejecuta en el emulador de PDC.<br /><br />Use esta opción para confirmar que se establece el estado de migración global correctos. Solo los Estados de migración estable pueden ser Estados globales de migración, por lo que los resultados que la **dfsrmig** comando informes con el **/GetGlobalState** opción corresponden a los Estados que se puede establecer con el **/SetGlobalState** opción.<br /><br />Debe ejecutar el **dfsrmig** comando con el **/GetGlobalState** opción únicamente en el emulador de PDC. replicación de Active Directory replica el estado global a otros controladores de dominio en el dominio, pero las latencias de replicación pueden provocar incoherencias si se ejecuta el **dfsrmig** comando con el **/GetGlobalState**  opción en un controlador de dominio que no sea el emulador de PDC. Para comprobar el estado de migración local de un controlador de dominio que no sea el emulador de PDC, use el **/GetMigrationState** opción en su lugar.|
|/GetMigrationState|Recupera el estado actual de la migración local para todos los controladores de dominio en el dominio y determina si esos Estados locales coinciden con el estado de migración global actual.<br /><br />Use esta opción para determinar si todos los controladores de dominio han alcanzado el estado de migración global. La salida de la **dsfrmig** comando cuando se usa el **/GetMigrationState** opción indica si completada la migración del estado global actual y muestra el estado de migración local para cualquier controladores de dominio que no han alcanzado el estado de migración global actual. Estado de migración local de los controladores de dominio puede incluir Estados de transición para controladores de dominio que no han alcanzado el estado de migración global actual.|
|/createGlobalObjects|crea los objetos globales y la configuración de AD DS que usa la replicación DFS.<br /><br />No es necesario usar esta opción durante un proceso de migración normal, ya que el servicio de replicación DFS crea automáticamente estos objetos de AD DS y la configuración durante la migración del estado start al estado preparado. Use esta opción para crear manualmente estos objetos y configuraciones en las situaciones siguientes:<br /><br />-   **Un nuevo controlador de dominio de solo lectura se promueve durante la migración**. El servicio de replicación DFS crea automáticamente la configuración para la replicación DFS y los objetos de AD DS durante la migración del estado start al estado preparado. Si se promueve un nuevo controlador de dominio de solo lectura en el dominio después de esta transición, pero antes de la migración al estado eliminado, a continuación, los objetos que se corresponden con el controlador de dominio de solo lectura recién creada no se crean en AD DS, provocando la replicación y migración a un error.<br />-En este caso, puede ejecutar el **dfsrmig** comando wth el **/createGlobalObjects** opción para crear manualmente los objetos en cualquier controlador de dominio de solo lectura que ya no las tiene. Ejecutar este comando no afecta a los controladores de dominio que ya tienen los objetos y valores para el servicio de replicación DFS.<br />-   **La configuración global para el servicio de replicación DFS faltan o que se eliminaron**. Si faltan estos valores para un controlador de dominio en particular, la migración del estado start al estado preparado se detiene en el estado de transición de preparación para el controlador de dominio. En este caso, puede usar el **dfsrmig** comando con el **/createGlobalObjects** opción para crear manualmente la configuración. **Nota:** Dado que la configuración global de AD DS para el servicio de replicación DFS para un controlador de dominio de solo lectura se crea en el emulador de PDC, esta configuración necesita para replicar en el controlador de dominio de solo lectura desde el emulador PDC antes que el servicio de replicación DFS en el controlador de dominio de sólo lectura puede usar esta configuración. Debido a las latencias de replicación de active directorio, esta replicación puede tardar algún tiempo en producirse.|
|/deleteRoNtfrsMember [<read_only_domain_controller_name>]|elimina la configuración global de AD DS para la replicación de FRS que se corresponde con el controlador de dominio de solo lectura especificado o elimina la configuración global de AD DS para la replicación de FRS para todos los controladores de dominio de solo lectura si se especifica ningún valor para *read_only_ nombreControladorDominio*.<br /><br />No es necesario usar esta opción durante un proceso de migración normal, porque el servicio de replicación DFS elimina automáticamente esta configuración de AD DS durante la migración del estado redirigido al estado eliminado. Dado que los controladores de dominio de solo lectura no pueden eliminar esta configuración de AD DS, el emulador de PDC realiza esta operación y los cambios finalmente se repliquen a controladores de dominio de solo lectura después de las latencias aplicables para la replicación de Active Directory.<br /><br />Use esta opción para eliminar manualmente la configuración de AD DS solo cuando la eliminación automática se produce un error en un controlador de dominio de solo lectura y detiene el controlador de dominio de solo lectura para un ime mucho durante la migración del estado redirigido al estado eliminado.|
|/deleteRoDfsrMember [< read_only_domain_controller_name >]|elimina la configuración global de AD DS para la replicación DFS que se corresponde con el controlador de dominio de solo lectura especificado o elimina la configuración global de AD DS para la replicación DFS para todos los controladores de dominio de solo lectura si se especifica ningún valor para *read_only_ nombreControladorDominio*.<br /><br />Use esta opción para eliminar manualmente la configuración de AD DS solo cuando la eliminación automática se produce un error en un controlador de dominio de solo lectura y el controlador de dominio de solo lectura detiene durante mucho tiempo al revertir la migración desde el estado preparado para el estado de inicio.|
|/?|Muestra la ayuda en el símbolo del sistema. Equivale a ejecutar **dfsrmig** sin ninguna opción.|
## <a name="remarks"></a>Comentarios
-   DFSRMIG.exe, la herramienta de migración para el servicio replicación DFS, se instala con el servicio de replicación DFS.
    para un nuevo servidor de Windows Server 2008, Dcpromo.exe instala e inicia el servicio de replicación DFS al promocionar el equipo a un controlador de dominio. Al actualizar un servidor de Windows Server 2003 a Windows Server 2008, el proceso de actualización de instala y se inicia el servicio de replicación DFS. No es necesario instalar el servicio de rol de replicación DFS para que el servicio de replicación DFS instalado e iniciado.
-   El **dfsrmig** herramienta solo se admite en controladores de dominio que se ejecutan en el nivel funcional del dominio de Windows Server 2008, porque la migración SYSvol de FRS a replicación DFS sólo es posible en los controladores de dominio que operan en el  Nivel funcional del dominio de Windows Server 2008.
-   Puede ejecutar el **dfsrmig** objetos de comando en cualquier controlador de dominio, pero las operaciones que crean o manipulan AD DS solo se permiten en los controladores de dominio capaz de lectura y escritura (no en los controladores de dominio de solo lectura).
-   Ejecutando **dfsrmig** sin ninguna opción muestra la Ayuda en el símbolo del sistema.
## <a name="BKMK_examples"></a>Ejemplos
Para establecer el estado de migración global preparada (**1**) e iniciar la migración a o revertir desde el estado preparado, tipo:
```
dfsrmig /SetGlobalState 1
```
Para establecer el estado de migración global para iniciar (**0**) e iniciar la reversión para el estado de inicio, escriba:
```
dfsrmig /SetGlobalState 0
```
Para mostrar el estado global de migración, escriba:
```
dfsrmig /GetGlobalState
```
En este ejemplo se muestra el resultado típico de la **dfsrmig /GetGlobalState** comando.
```
Current DFSR global state:  Prepared 
Succeeded.
```
Para mostrar la información sobre si los Estados de migración local en todos los controladores de dominio coincide con el estado global de migración y los Estados de migración local de los controladores de dominio donde el estado local no coincide con el estado global, escriba:
```
dfsrmig /GetMigrationState
```
En este ejemplo se muestra el resultado típico de la **dfsrmig /GetMigrationState** cuando los Estados de migración local en todos los controladores de dominio coincide con el estado de migración global de comandos.
```
All Domain Controllers have migrated successfully to Global state ( Prepared ).
Migration has reached a consistent state on all Domain Controllers.
Succeeded.
```
En este ejemplo se muestra el resultado típico de la **dfsrmig /GetMigrationState** cuando los Estados de migración local en algunos controladores de dominio no coincide con el estado de migración global de comandos.
```
The following Domain Controllers are not in sync with Global state ( Prepared ):
Domain Controller (Local Migration State)   DC type
=========
CONTOSO-DC2 ( start )   ReadOnly DC
CONTOSO-DC3 ( Preparing )   Writable DC
Migration has not yet reached a consistent state on all domain controllers
State information might be stale due to AD latency.
```
Para crear los objetos globales y la configuración que usa la replicación DFS en AD DS en controladores de dominio donde esa configuración no se crearon automáticamente durante la migración o que faltan esos valores, escriba:
```
dfsrmig /createGlobalObjects
```
Para eliminar la configuración global de AD DS para la replicación de FRS para un controlador de dominio de solo lectura denominada contoso-dc2 si esa configuración no se eliminaron eliminará automáticamente el proceso de migración, escriba:
```
dfsrmig /deleteRoNtfrsMember contoso-dc2
```
Para eliminar la configuración global de AD DS para la replicación de FRS para todos los controladores de dominio de solo lectura si esa configuración no se han eliminado automáticamente por el proceso de migración, escriba:
```
dfsrmig /deleteRoNtfrsMember
```
Para eliminar la configuración global de AD DS para la replicación DFS para un controlador de dominio de solo lectura denominada contoso-dc2 si esa configuración no se han eliminado automáticamente por el proceso de migración, escriba:
```
dfsrmig /deleteRoDfsrMember contoso-dc2
```
Para eliminar la configuración global de AD DS para la replicación DFS para todos los controladores de dominio de solo lectura si esa configuración no se han eliminado automáticamente por el proceso de migración, escriba:
```
dfsrmig /deleteRoDfsrMember
```
## <a name="additional-references"></a>Referencias adicionales
[Clave de sintaxis de línea de comandos](https://go.microsoft.com/fwlink/?LinkId=122056)

[Serie de migración de SYSvol: Part 2 dfsrmig.exe: La herramienta de migración SYSvol](https://go.microsoft.com/fwlink/?LinkID=121757)