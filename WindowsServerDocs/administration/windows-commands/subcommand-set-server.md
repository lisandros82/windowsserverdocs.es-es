---
title: Subcomando set-Server
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da55c29d-a94a-4d73-877b-af480f906ca0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 24ff739fa249fdcdae5009a46c8bd018d0be3c24
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383881"
---
# <a name="subcommand-set-server"></a>Subcomando: set-Server

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Configura los valores para un servidor de servicios de implementación de Windows.
## <a name="syntax"></a>Sintaxis
```
wdsutil [Options] /Set-Server [/Server:<Server name>]
    [/Authorize:{Yes | No}]
    [/RogueDetection:{Yes | No}]
    [/AnswerClients:{All | Known | None}]
    [/Responsedelay:<time in seconds>]
    [/AllowN12forNewClients:{Yes | No}]
    [/ArchitectureDiscovery:{Yes | No}]
    [/resetBootProgram:{Yes | No}]
    [/DefaultX86X64Imagetype:{x86 | x64 | Both}]
    [/UseDhcpPorts:{Yes | No}]
    [/DhcpOption60:{Yes | No}]
    [/RpcPort:<Port number>]
    [/PxepromptPolicy 
        [/Known:{OptIn | Noprompt | OptOut}]
        [/New:{OptIn | Noprompt | OptOut}] 
    [/BootProgram:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/N12BootProgram:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/BootImage:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/PreferredDC:<DC Name>]
    [/PreferredGC:<GC Name>]
    [/PrestageUsingMAC:{Yes | No}]
    [/NewMachineNamingPolicy:<Policy>]
    [/NewMachineOU]
         [/type:{Serverdomain | Userdomain | UserOU | Custom}]
         [/OU:<Domain name of OU>]
    [/DomainSearchOrder:{GCOnly | DCFirst}]
    [/NewMachineDomainJoin:{Yes | No}]
    [/OSCMenuName:<Name>]
    [/WdsClientLogging]
         [/Enabled:{Yes | No}]
         [/LoggingLevel:{None | Errors | Warnings | Info}]
    [/WdsUnattend]
         [/Policy:{Enabled | Disabled}]
         [/CommandlinePrecedence:{Yes | No}]
         [/File:<path>]
             /Architecture:{x86 | ia64 | x64}
    [/AutoaddPolicy]
         [/Policy:{AdminApproval | Disabled}]
         [/PollInterval:{time in seconds}]
         [/MaxRetry:{Retries}]
         [/Message:<Message>]
         [/RetentionPeriod]
             [/Approved:<time in days>]
             [/Others:<time in days>]
    [/AutoaddSettings]
         /Architecture:{x86 | ia64 | x64}
         [/BootProgram:<Relative path>]
         [/ReferralServer:<Server name>
         [/WdsClientUnattend:<Relative path>]
         [/BootImage:<Relative path>]
         [/User:<Owner>]
         [/JoinRights:{JoinOnly | Full}]
         [/JoinDomain:{Yes | No}]
    [/BindPolicy]
         [/Policy:{Include | Exclude}]
         [/add]
              /address:<IP or MAC address>
              /addresstype:{IP | MAC}
         [/remove]
              /address:<IP or MAC address>
              /addresstype:{IP | MAC}
    [/RefreshPeriod:<time in seconds>]
    [/BannedGuidPolicy]
         [/add]
              /Guid:<GUID>
         [/remove]
             /Guid:<GUID>
    [/BcdRefreshPolicy]
         [/Enabled:{Yes | No}]
         [/RefreshPeriod:<time in minutes>]
    [/Transport]
         [/ObtainIpv4From:{Dhcp | Range}]
             [/start:<start IP address>]
             [/End:<End IP address>]
         [/ObtainIpv6From:Range]
             [/start:<start IP address>]
             [/End:<End IP address>]
         [/startPort:<start Port>
             [/EndPort:<start Port>
        [/Profile:{10Mbps | 100Mbps | 1Gbps | Custom}]
        [/MulticastSessionPolicy]
             [/Policy:{None | AutoDisconnect | Multistream}]
                 [/Threshold:<Speed in KBps>]
                 [/StreamCount:{2 | 3}]
                 [/Fallback:{Yes | No}]    
        [/forceNative]
```
## <a name="parameters"></a>Parámetros
|Parámetro|Descripción|
|-------|--------|
|[/Server:<Server name>]|Especifica el nombre del servidor. Puede ser el nombre de NetBIOS o el nombre de dominio completo (FQDN). Si no se especifica ningún nombre de servidor, se utilizará el servidor local.|
|[/Authorize: {Yes &#124; no}]|Especifica si se autoriza este servidor en el protocolo de control de host dinámico (DHCP).|
|[/RogueDetection: {Yes &#124; no}]|Habilita o deshabilita la detección no autorizada de DHCP.|
|[/AnswerClients: {ALL &#124; known &#124; None}]|Especifica los clientes a los que responderá este servidor. Si establece este valor en **conocido**, un equipo debe preconfigurarse en los servicios de dominio de active directory (AD DS) antes de que el servidor de servicios de implementación de Windows lo responda.|
|[/Responsedelay: <time in seconds>]|La cantidad de tiempo que el servidor esperará antes de responder a un cliente de arranque. Esta configuración no se aplica a los equipos preconfigurados.|
|[/AllowN12forNewClients: {Yes &#124; no}]|en Windows Server 2008, especifica que los clientes desconocidos no tendrán que presionar la tecla F12 para iniciar un arranque de red. Los clientes conocidos recibirán el programa de arranque especificado para el equipo o, si no se especifica, el programa de arranque especificado para la arquitectura.<br /><br />en Windows Server 2008 R2, esta opción se ha reemplazado por el siguiente comando: WDSUtil/Set-Server/PxepromptPolicy/New: noprompt|
|[/ArchitectureDiscovery: {Yes &#124; no}]|Habilita o deshabilita la detección de arquitectura. Esto facilita la detección de clientes basados en x64 que no difunden su arquitectura correctamente.|
|[/resetBootProgram: {Yes &#124; no}]|Determina si la ruta de acceso de arranque se borrará para un cliente que se acaba de arrancar sin necesidad de presionar una tecla F12.|
|[/DefaultX86X64Imagetype: {x86 &#124; x64 &#124; ]|Controla las imágenes de arranque que se mostrarán a los clientes basados en x64.|
|[/UseDhcpPorts: {Yes &#124; no}]|Especifica si el servidor PXE debe intentar o no enlazar con el puerto DHCP, puerto TCP 67. Si DHCP y servicios de implementación de Windows se ejecutan en el mismo equipo, debe establecer esta opción en **no** para permitir que el servidor DHCP utilice el puerto y establecer el parámetro **/DhcpOption60** en **sí**. La configuración predeterminada para este valor es **sí**.|
|[/DhcpOption60: {Yes &#124; no}]|Especifica si la opción 60 de DHCP debe configurarse para la compatibilidad con PXE. Si DHCP y servicios de implementación de Windows se ejecutan en el mismo servidor, establezca esta opción en **sí** y establezca la opción **/UseDhcpPorts** en **no**. La configuración predeterminada para este valor es **no**.|
|[/RpcPort: <Port number>]|Especifica el número de puerto TCP que se va a usar para atender las solicitudes de cliente.|
|[/PxepromptPolicy]|Configura el modo en que los clientes conocidos (preconfigurados) y los nuevos inician un arranque PXE. Esta opción solo se aplica a Windows Server 2008 R2. Establezca la configuración con las siguientes opciones:<br /><br />-[/Known: {OptIn&#124;OptOut&#124;noprompt}]: establece la Directiva para los clientes preconfigurados.<br />-[/New: {OptIn&#124;OptOut&#124;noprompt}]: establece la Directiva para los nuevos clientes.<br /><br />**Optin** significa que el cliente debe presionar una tecla para el arranque PXE; de lo contrario, volverá al siguiente dispositivo de arranque.<br /><br />**Noprompt** significa que el cliente siempre realizará el arranque PXE.<br /><br />**OptOut** significa que el cliente realizará un arranque PXE a menos que se presione la tecla ESC.|
|[/BootProgram: <Relative path>]/Architecture: {x86 &#124; ia64 &#124; x64}|Especifica la ruta de acceso relativa al programa de arranque en la carpeta remoteInstall (por ejemplo, **boot\x86\pxeboot.N12**) y especifica la arquitectura del programa de arranque.|
|[/N12BootProgram: <Relative path>]/Architecture: {x86 &#124; ia64 &#124; x64}|Especifica la ruta de acceso relativa al programa de arranque que no requiere que se presione la tecla F12 (por ejemplo, **boot\x86\pxeboot.N12**) y especifica la arquitectura del programa de arranque.|
|[/BootImage: <Relative path>]/Architecture: {x86 &#124; ia64 &#124; x64}|Especifica la ruta de acceso relativa a la imagen de arranque que deben recibir los clientes de arranque y especifica la arquitectura de la imagen de arranque. Puede especificar esto para cada arquitectura.|
|[/PreferredDC: <DC Name>]|Especifica el nombre del controlador de dominio que deben usar los servicios de implementación de Windows. Puede ser el nombre NetBIOS o el FQDN.|
|[/PreferredGC: <GC Name>]|Especifica el nombre del servidor de catálogo global que deben usar los servicios de implementación de Windows. Puede ser el nombre NetBIOS o el FQDN.|
|[/PrestageUsingMAC: {Yes &#124; no}]|Especifica si servicios de implementación de Windows, al crear cuentas de equipo en AD DS, debe usar la dirección MAC en lugar del GUID/UUID para identificar el equipo.|
|[/NewMachineNamingPolicy: <Policy>]|Especifica el formato que se va a usar al generar nombres de equipo para clientes. Para obtener información sobre el formato que se va a utilizar para <policy>, haga clic con el botón secundario en el servidor en el complemento MMC, haga clic en **propiedades**y vea la pestaña **servicios de directorio** . Por ejemplo, **/NewMachineNamingPolicy:% 61Username% #** .|
|[/NewMachineOU]|Se usa para especificar la ubicación en AD DS donde se crearán las cuentas de equipo cliente. Especifique la ubicación con las siguientes opciones.<br /><br />-[/type: Serverdomain &#124; Userdomain &#124; UserOU &#124; Custom] especifica el tipo de ubicación. **Serverdomain** crea cuentas en el mismo dominio que el servidor de servicios de implementación de Windows. **Userdomain** crea cuentas en el mismo dominio que el usuario que realiza la instalación. **UserOU** crea cuentas en la unidad organizativa del usuario que realiza la instalación. **Personalizado** le permite especificar una ubicación personalizada (también debe especificar un valor para **/ou** con esta opción).<br />-[/OU: <Domain name of OU>]: Si especifica **Custom** para la opción **/Type** , esta opción especifica la unidad organizativa en la que se deben crear las cuentas de equipo.|
|[/DomainSearchOrder: {GCOnly &#124; DCFirst}]|Especifica la Directiva para buscar cuentas de equipo en AD DS (catálogo global o controlador de dominio).|
|[/NewMachineDomainJoin: {Yes &#124; no}]|Especifica si un equipo que aún no está preconfigurado en AD DS debe unirse al dominio durante la instalación. El valor predeterminado es **sí**.|
|/WdsClientLogging|Especifica el nivel de registro del servidor.<br /><br />-[/Enabled: {Yes &#124; no}]: habilita o deshabilita el registro de acciones de cliente de servicios de implementación de Windows.<br />-[/LoggingLevel: {None &#124; errores &#124; advertencias &#124; info}-establece el nivel de registro. **Ninguno** es equivalente a deshabilitar el registro. Los **errores** son el nivel más bajo de registro e indica que solo se registrarán los errores. **Advertencias** incluye advertencias y errores. **Info** es el nivel de registro más alto e incluye errores, advertencias y eventos informativos.|
|/WdsUnattend|Esta configuración controla el comportamiento de la instalación desatendida del cliente de servicios de implementación de Windows. Establezca la configuración con las siguientes opciones:<br /><br />-[/Policy: {Enabled &#124; Disabled}]: especifica si se utiliza la instalación desatendida.<br />-[/CommandlinePrecedence: {Yes &#124; no}]: especifica si se usará un archivo Autounattend. XML (si está presente en el cliente) o un archivo de instalación desatendida que se pasó directamente al cliente de servicios de implementación de Windows con la opción/Unattend en lugar de un archivo de instalación desatendida de imagen durante una instalación de cliente. La configuración predeterminada es **no**.<br />-[/File: <Relative path>/Architecture: {x86 &#124; ia64 &#124; x64}]: especifica el nombre de archivo, la ruta de acceso y la arquitectura del archivo de instalación desatendida.|
|[/AutoaddPolicy]|Esta configuración controla la Directiva de adición automática. Defina la configuración con las siguientes opciones:<br /><br />-[/Policy: {AdminApproval &#124; Disabled}]- **AdminApprove** hace que todos los equipos desconocidos se agreguen a una cola pendiente, donde el administrador puede revisar la lista de equipos y aprobar o rechazar cada solicitud, según corresponda. **Deshabilitado** indica que no se realiza ninguna acción adicional cuando un equipo desconocido intenta arrancar en el servidor.<br />-[/PollInterval: {Time in seconds}]: especifica el intervalo (en segundos) en el que el programa de arranque de red debe sondear el servidor de servicios de implementación de Windows.<br />-[/MaxRetry: <Number>]: especifica el número de veces que el programa de arranque de red debe sondear el servidor de servicios de implementación de Windows. Este valor, junto con **/PollInterval**, determina cuánto tiempo esperará el programa de arranque de red para que un administrador apruebe o rechace el equipo antes de que se agote el tiempo de espera. Por ejemplo, un valor de **MaxRetry** de 10 y un Vlue de **PollInterval** de 60 indicaría que el cliente debe sondear el servidor 10 veces, esperando 60 segundos entre los intentos. Por lo tanto, el cliente agotaría el tiempo de espera después de 10 minutos (10 x 60 segundos = 10 minutos).<br />-[/Message: <Message>]: especifica el mensaje que se muestra al cliente en la página del cuadro de diálogo del programa de arranque de red.<br />-[/RetentionPeriod]: especifica el número de días que un equipo puede estar en un estado pendiente antes de que se purgue automáticamente.<br />-[/Approved: <time in days>]: especifica el período de retención para los equipos aprobados. Debe usar este parámetro con la opción **/RetentionPeriod** .<br />-[/Others: <time in days>]: especifica el período de retención para equipos no aprobados (rechazados o pendientes). Debe usar este parámetro con la opción **/RetentionPeriod** .|
|[/AutoaddSettings]|Especifica la configuración predeterminada que se va a aplicar a cada equipo. Defina la configuración con las siguientes opciones:<br /><br />-/Architecture: {x86 &#124; ia64 &#124; x64}-especifica la arquitectura.<br />-[/BootProgram: <Relative path>]: especifica el programa de arranque que se envía al equipo aprobado. Si no se especifica ningún programa de arranque, se usará el valor predeterminado para la arquitectura del equipo (tal y como se especifica en el servidor).<br />-[/WdsClientUnattend: <Relative path>]: establece la ruta de acceso relativa al archivo de instalación desatendida que el cliente aprobado debe recibir.<br />-[/ReferralServer: <Server name>]: especifica el servidor de servicios de implementación de Windows que el cliente usará para descargar imágenes.<br />-[/BootImage: <Relative path>]: especifica la imagen de arranque que recibirá el cliente aprobado.<br />-[/User: < Dominio\usuario &#124; User@Domain >]: establece permisos en el objeto de cuenta de equipo para conceder al usuario especificado los derechos necesarios para unir el equipo al dominio.<br />-[JoinRights: {JoinOnly &#124; Full}]: especifica el tipo de derechos que se asignará al usuario. **JoinOnly** requiere que el administrador restablezca la cuenta de equipo antes de que el usuario pueda unir el equipo al dominio. **Full** proporciona acceso completo al usuario, incluido el derecho a unir el equipo al dominio.<br />-[/JoinDomain: {Yes &#124; no}]: especifica si el equipo debe unirse al dominio como esta cuenta de equipo durante una instalación de servicios de implementación de Windows. El valor predeterminado es **sí**.|
|/BindPolicy|Configura las interfaces de red para que el proveedor PXE escuche. La Directiva se define mediante las siguientes opciones:<br /><br />-[/Policy: {include &#124; Exclude}]: establece la Directiva de enlace de la interfaz para incluir o excluir las direcciones de la lista de interfaces.<br />-[/Add]: agrega una interfaz a la lista. También debe especificar/AddressType y/Address.<br />-[/Remove]: quita una interfaz de la lista. También debe especificar/AddressType y/Address.<br />-/Address: <IP or MAC address>: especifica la dirección IP o MAC de la interfaz que se va a agregar o quitar.<br />-/AddressType: {IP &#124; Mac}-indica el tipo de dirección especificado en la opción **/Address** .|
|[/RefreshPeriod: <seconds>]|Especifica la frecuencia (en segundos) con la que el servidor actualizará su configuración.|
|[/BannedGuidPolicy]|Administra la lista de identificadores GUID prohibidos con las siguientes opciones:<br /><br />-[/Add]/GUID: <GUID>: agrega el GUID especificado a la lista de identificadores GUID prohibidos. Cualquier cliente con este GUID se identificará mediante su dirección MAC en su lugar.<br />-[/Remove]/GUID: <GUID>: quita el GUID especificado de la lista de GUID prohibidos.|
|[/BcdRefreshPolicy]|Configura los valores para actualizar los archivos BCD con las siguientes opciones:<br /><br />-[/Enabled: {Yes &#124; no}]: especifica la Directiva de actualización de BCD. Cuando **/Enabled** se establece en **yes**, los archivos BCD se actualizan en el intervalo de tiempo especificado.<br />-[/ RefreshPeriod\:<time in minutes>]: especifica el intervalo de tiempo en el Bcd se actualizan los archivos.|
|/Seguridad|Configura las siguientes opciones\:<br /><br /><ul><li>[/ObtainIpv4From: {intervalo &#124; de DHCP}]: especifica el origen de las direcciones IPv4.<br /><br /><ul><li>[/ iniciar\: <starting Ipv4 address>]: especifica el inicio del intervalo de direcciones IP. Esta opción es obligatoria y válida solo si **/ObtainIpv4From** está establecido en **Range**</li><li>[/ End\: <Ending Ipv4 address>]: especifica el final del intervalo de direcciones IP. Esta opción es obligatoria y válida solo si **/ObtainIpv4From** está establecido en **Range**.</li></ul></li><li>[/ ObtainIpv6From:Range] [/ iniciar\:<start IP address>] [/ End\<End IP address>] Especifica el origen de las direcciones IPv6. Esta opción solo se aplica a Windows Server 2008 R2 y el único valor admitido es intervalo.</li><li>[/ puerto inicial <starting port>] especifica el inicio del intervalo de puertos.</li><li>[/ El puerto final <Ending port>] especifica el final del intervalo de puertos.</li><li>[/Profile: {10Mbps &#124; 100Mbps &#124; 1 Gbps &#124; Custom}]: especifica el perfil de red que se va a usar. Esta opción solo es compatible con forservers que ejecute Windows Server 2008.</li><li>[/MulticastSessionPolicy]  Configura las opciones de transferencia para las transmisiones de multidifusión. Este comando solo está disponible para Windows Server 2008 R2.<br /><br /><ul><li>[/Policy: {ninguna &#124; conexión automática &#124; Multistream}]: determina cómo se administran los clientes lentos. Ninguno significa mantener todos los clientes en una sesión a la misma velocidad. La desconexión automática significa que los clientes que se coloquen por debajo del/Threshold especificado se desconectarán. Multistream significa que los clientes se separarán en varias sesiones, tal como se especifica en/StreamCount.</li><li>[/Threshold: <Speed in KBps>]-para/Policy: autodisconnect, esta opción establece la velocidad de transferencia mínima en KBps. Los clientes que se descartan por debajo de esta tarifa se desconectarán de las transmisiones de multidifusión.</li><li>[/StreamCount: {2 &#124; 3}] [/Fallback: {Yes &#124; no}]-para/Policy: Multistream, esta opción determina el número de sesiones. 2 significa que dos sesiones (rápidas y lentas) 3 significan tres sesiones (lentas, medias y rápidas).</li><li>[/Fallback: {Yes&#124; no}]: determina si los clientes que están desconectados continuarán la transferencia mediante otro método (si el cliente lo admite). Si usa el cliente WDS, el equipo se reservará a la unidifusión. Wdsmcast. exe no admite un mecanismo de reserva. Esta opción también se aplica a los clientes que no admiten Multistream. En ese caso, el equipo revertirá a otro método en lugar de pasar a una sesión de transferencia más lenta.</li></ul></li></ul>|
## <a name="BKMK_examples"></a>Example
Para establecer que el servidor responda solo a los clientes conocidos, con un retraso de respuesta de 4 minutos, escriba:
```
wdsutil /Set-Server /AnswerClients:Known /Responsedelay:4
```
Para establecer el programa de arranque y la arquitectura para el servidor, escriba:
```
wdsutil /Set-Server /BootProgram:boot\x86\pxeboot.n12 /Architecture:x86
```
Para habilitar el registro en el servidor, escriba:
```
wdsutil /Set-Server /WdsClientLogging /Enabled:Yes /LoggingLevel:Warnings
```
Para habilitar Unattend en el servidor, así como la arquitectura y el archivo de instalación desatendida del cliente, escriba:
```
wdsutil /Set-Server /WdsUnattend /Policy:Enabled /File:WDSClientUnattend \unattend.xml /Architecture:x86
```
Para establecer el servidor de entorno de ejecución previo al arranque (PXE) para intentar enlazar con los puertos TCP 67 y 60, escriba:
```
wdsutil /Set-server /UseDhcpPorts:No /DhcpOption60:Yes
```
#### <a name="additional-references"></a>Referencias adicionales
[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)
[con el comando DISABLE-Server](using-the-disable-server-command.md)
[mediante el comando Enable-Server](using-the-enable-server-command.md)
[mediante el comando Get-Server](using-the-get-server-command.md)
[mediante el comando Initialize-Server](using-the-initialize-server-command.md)
[ Subcomando: Start-Server](subcommand-start-server.md)1[subcomando: Stop-Server](subcommand-stop-server.md)3[The UnInitialize-Server Option](the-uninitialize-server-option.md)
