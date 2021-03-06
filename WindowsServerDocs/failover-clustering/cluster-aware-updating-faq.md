---
ms.assetid: 6416d125-bcaf-433d-971a-2f0283bca2c2
title: 'Actualización compatible con clústeres: preguntas más frecuentes'
ms.topic: article
ms.prod: windows-server
manager: dongill
ms.author: jgerend
author: JasonGerend
ms.date: 04/28/2017
description: Respuestas a las preguntas más frecuentes sobre la actualización compatible con clústeres en Windows Server.
ms.openlocfilehash: 736b49222ae4c9e2a27229341f0d886bd3e0343c
ms.sourcegitcommit: 07c9d4ea72528401314e2789e3bc2e688fc96001
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76822138"
---
# <a name="cluster-aware-updating-frequently-asked-questions"></a>Actualización compatible con clústeres: Preguntas más frecuentes

> Se aplica a: Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 y Windows Server 2012

[La actualización compatible con clústeres](cluster-aware-updating.md) \(Cau\) es una característica que coordina las actualizaciones de software en todos los servidores de un clúster de conmutación por error de forma que no afecte a la disponibilidad del servicio más que una conmutación por error planeada de un nodo de clúster. En el caso de algunas aplicaciones con características de disponibilidad continua \(como Hyper\-V con migración en vivo o un servidor de archivos SMB 3. x con conmutación por error transparente de SMB\), la CAU puede coordinar la actualización de clústeres automatizada sin afectar a la disponibilidad del servicio.

## <a name="does-cau-support-updating-storage-spaces-direct-clusters"></a>¿Admite la CAU la actualización de clústeres de Espacios de almacenamiento directo?  
Sí. La CAU admite la actualización de clústeres de [espacios de almacenamiento directo](../storage/storage-spaces/storage-spaces-direct-overview.md) independientemente del tipo de implementación: hiperconvergido o convergente. En concreto, la orquestación de CAU garantiza que la suspensión de cada nodo del clúster espera a que el espacio de almacenamiento en clúster subyacente sea correcto.

## <a name="does-cau-work-with-windowsserver-2008r2-or-windows7"></a>¿Funciona la CAU con Windows Server 2008 R2 o Windows 7?  
No. La CAU coordina la operación de actualización de clústeres solo desde equipos que ejecutan Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows 10, Windows 8.1 o Windows 8. El clúster de conmutación por error que se está actualizando debe ejecutar Windows Server 2016, Windows Server 2012 R2 o Windows Server 2012.
  
## <a name="is-cau-limited-to-specific-clustered-applications"></a>¿La CAU está limitada a aplicaciones en clúster específicas?  
No. La CAU es válida para distintos tipos de aplicaciones en clúster. La CAU es un clúster externo\-la solución de actualización que se superpone a las API de agrupación en clústeres y a los cmdlets de PowerShell. Como tal, la CAU puede coordinar la actualización para cualquier aplicación en clúster que esté configurada en un clúster de conmutación por error de Windows Server.  
  
> [!NOTE]  
> Actualmente, se prueban y certifican las siguientes cargas de trabajo en clúster para la CAU: SMB, Hyper\-V, Replicación DFS, espacios de nombres DFS, iSCSI y NFS.  
  
## <a name="does-cau-support-updates-from-microsoft-update-and-windows-update"></a>¿Admite la CAU actualizaciones de Microsoft Update y Windows Update?  
Sí. De forma predeterminada, la CAU está configurada con un\-de conexión en que utiliza las API de la utilidad de Windows Update Agent \(WUA\) en los nodos del clúster. La infraestructura de WUA puede configurarse para que apunte a Microsoft Update y Windows Update o Windows Server Update Services \(WSUS\) como origen de las actualizaciones.  
  
## <a name="does-cau-support-wsus-updates"></a>¿Admite la CAU actualizaciones de WSUS?  
Sí. De forma predeterminada, la CAU está configurada con un\-de conexión en que utiliza las API de la utilidad de Windows Update Agent \(WUA\) en los nodos del clúster. La infraestructura de WUA puede configurarse para que apunte a Microsoft Update y Windows Update o a un Windows Server Update Services local \(servidor WSUS\) como su origen de actualizaciones.  
  
## <a name="can-cau-apply-limited-distribution-release-updates"></a>¿Puede la CAU aplicar actualizaciones de versiones de distribución limitada?  
Sí. La versión de distribución limitada \(los\) de las actualizaciones de LDR, también denominadas revisiones, no se publican a través de Microsoft Update o Windows Update, por lo que no se pueden descargar con el agente de Windows Update \(\) de la\-de la salida de la CAU que usa de forma predeterminada.  
  
Sin embargo, la CAU incluye un segundo\-de conexión en el que puede seleccionar la aplicación de actualizaciones de revisiones. Este complemento de revisión\-en también se puede personalizar para aplicar actualizaciones de controladores, firmware y BIOS que no sean\-de Microsoft.  
  
## <a name="can-i-use-cau-to-apply-cumulative-updates"></a>¿Puedo usar la CAU para aplicar actualizaciones acumulativas?  
Sí. Si las actualizaciones acumulativas son actualizaciones de versiones de distribución general o LDR, la CAU las puede aplicar.  
  
## <a name="can-i-schedule-updates"></a>¿Puedo programar actualizaciones?  
Sí. La CAU admite los siguientes modos de actualización (ambos permiten programar las actualizaciones):  
  
**Actualización de\-Self** Permite que el clúster se actualice automáticamente en función de un perfil definido y una programación regular, como durante una ventana de mantenimiento mensual. También puede iniciar una ejecución de actualización\-a petición en cualquier momento. Para habilitar el modo de actualización de\-, debe agregar el rol en clúster de la CAU al clúster. La característica de actualización de\-CAU se comporta como cualquier otra carga de trabajo en clúster y puede funcionar perfectamente con las conmutaciones por error planeadas y no planeadas de un equipo coordinador de actualizaciones.  
  
**Actualización de\-remota** Permite iniciar una ejecución de actualización en cualquier momento desde un equipo que ejecuta Windows o Windows Server. Puede iniciar una ejecución de actualización a través de la ventana de actualización compatible con clústeres o mediante el cmdlet **Invoke\-CauRun** de PowerShell. La actualización remota de\-es el modo de actualización predeterminado de la CAU. Puede usar el Programador de tareas para ejecutar el cmdlet [Invoke-CauRun](https://technet.microsoft.com/itpro/powershell/windows/cluster-aware-updating/invoke-caurun) en un programa deseado desde un equipo remoto que no sea uno de los nodos del clúster.  
  
## <a name="can-i-schedule-updates-to-apply-during-a-backup"></a>¿Se pueden programar actualizaciones para que se apliquen durante una copia de seguridad?  
Sí. La CAU no impone ninguna restricción en este sentido. Sin embargo, no se recomienda realizar actualizaciones de software en un servidor \(con los posibles reinicios asociados\) mientras se está realizando una copia de seguridad del servidor. Tenga en cuenta que la CAU depende solo de las API en clúster para determinar conmutaciones por error y conmutación por recuperación de recursos; de este modo, la CAU ignora el estado de la copia de seguridad del servidor.  
  
## <a name="can-cau-work-with-configuration-manager"></a>¿Puede la CAU trabajar con Configuration Manager?  
La CAU es una herramienta que coordina las actualizaciones de software en un nodo de clúster y Configuration Manager también realiza actualizaciones de software de servidor. Es importante configurar estas herramientas para que no tengan una cobertura superpuesta de los mismos servidores en cualquier implementación del centro de recursos, incluido el uso de diferentes servidores de Windows Server Update Services. Esto garantiza que el objetivo subyacente al uso de la CAU no se derrota accidentalmente, porque Configuration Manager actualización controlada por\-no incorpora el conocimiento del clúster.  
  
## <a name="do-i-need-administrative-credentials-to-run-cau"></a>¿Necesito credenciales administrativas para ejecutar la CAU?  
Sí. Para ejecutar las herramientas de la CAU, esta necesita credenciales administrativas en el servidor local o necesita el derecho de usuario de **Suplantar a un cliente tras la autenticación** en el servidor local o en el equipo cliente en el que se está ejecutando. Sin embargo, para coordinar actualizaciones de software en los nodos del clúster, la CAU requiere credenciales administrativas del clúster en todos los nodos. Aunque la interfaz de usuario de CAU puede iniciarse sin las credenciales, pide las credenciales administrativas del clúster cuando se conecta a una instancia de clúster para obtener una vista previa o aplicar actualizaciones.  
  
## <a name="can-i-script-cau"></a>¿Se puede incluir en el script CAU?  
Sí. La CAU viene con cmdlets de PowerShell que ofrecen un amplio conjunto de opciones de scripting. Son los mismos cmdlets que la interfaz de usuario de la CAU llama para realizar acciones de la CAU.  

## <a name="what-happens-to-active-clustered-roles"></a>¿Qué ocurre con los roles en clúster activos?

Los roles en clúster \(anteriormente denominados aplicaciones y servicios\) que están activos en un nodo, conmutan por error a otros nodos antes de que pueda iniciarse la actualización de software. La CAU orquesta estas conmutaciones por error mediante el modo de mantenimiento, que pone en pausa y purga el nodo de todos los roles en clúster activos. Cuando finalizan las actualizaciones de software, la CAU reanuda el nodo y los roles en clúster vuelven a conmutar al nodo actualizado. Esto garantiza que la distribución de roles en clúster relacionados con nodos se mantenga igual durante las ejecuciones de actualización de la CAU de un clúster.  
  
## <a name="how-does-cau-select-target-nodes-for-clustered-roles"></a>¿Cómo selecciona la CAU los nodos de destino para los roles en clúster?

La CAU depende de las API en clúster para coordinar las conmutaciones por error. La implementación de la API de agrupación en clústeres selecciona los nodos de destino confiando en métricas internas y heurísticas de ubicación inteligente \(como los niveles de carga de trabajo\) a través de los nodos de destino.  
  
## <a name="does-cau-load-balance-the-clustered-roles"></a>¿Equilibra la carga de CAU los roles en clúster?

La CAU no equilibra la carga de los nodos en clúster, pero intenta preservar la distribución de los roles en clúster. Cuando la CAU finaliza la actualización de un nodo de clúster, intenta volver a conmutar a ese nodo los roles en clúster hospedados anteriormente. La CAU depende de API en clúster para volver a conmutar los recursos al principio del proceso de pausa. Por lo tanto, en ausencia de conmutaciones por error y de la configuración preferida del propietario, la distribución de roles en clúster debe permanecer sin cambios.  
  
## <a name="how-does-cau-select-the-order-of-nodes-to-update"></a>¿Cómo hace la CAU para seleccionar el orden de los nodos para actualizar?  
De manera predeterminada, la CAU selecciona el orden de los nodos para actualizar en función del nivel de actividad. Los nodos que hospedan la menor cantidad de roles en clúster se actualizan primero. Sin embargo, un administrador puede especificar un orden determinado para actualizar los nodos mediante la especificación de un parámetro para la ejecución de actualización en la interfaz de usuario de CAU o mediante los cmdlets de PowerShell.  
  
## <a name="what-happens-if-a-cluster-node-is-offline"></a>¿Qué ocurre si un nodo de clúster está sin conexión?

El administrador que inicializa una ejecución de actualización puede especificar el umbral aceptable para el número de nodos que pueden estar sin conexión. Por lo tanto, una ejecución de actualización puede continuar en un clúster aunque ninguno de los nodos de clúster esté en línea.  
  
## <a name="can-i-use-cau-to-update-only-a-single-node"></a>¿Puedo usar la CAU para actualizar solo un nodo?  
No. La CAU es una herramienta de actualización de ámbito de clúster\-, por lo que solo permite seleccionar clústeres para actualizar. Si desea actualizar un solo nodo, puede usar las herramientas de actualización existentes del servidor, independientemente de la CAU.  
  
## <a name="can-cau-report-updates-that-are-initiated-from-outside-cau"></a>¿Las actualizaciones de informes de CAU se pueden iniciar desde fuera de la CAU?  
No. La CAU solo puede informar de ejecuciones de actualización que se inicializan desde la CAU. Sin embargo, cuando se inicia una ejecución de actualización de CAU subsiguiente, las actualizaciones que se instalaron a través de métodos de CAU que no son\-se consideran adecuadas para determinar las actualizaciones adicionales que pueden ser aplicables a cada nodo de clúster.  
  
## <a name="can-cau-support-my-unique-it-process-needs"></a>¿Puede la CAU admitir mis necesidades de procesos de ti únicos?  
Sí. La CAU ofrece las siguientes dimensiones de flexibilidad para ajustarse a las necesidades únicas de procesos de TI de los clientes empresariales:  
  
**Scripts** de Una ejecución de actualización puede especificar un script de PowerShell de la versión anterior\-y un script de PowerShell de actualización posterior\-. El script de actualización anterior a la\-se ejecuta en cada nodo de clúster antes de que el nodo esté en pausa. El script post\-Update se ejecuta en cada nodo del clúster después de que se instalen las actualizaciones del nodo.  
  
> [!NOTE]  
> .NET Framework 4,6 o 4,5 y PowerShell deben estar instalados en cada nodo de clúster en el que desee ejecutar la actualización anterior a la\-y los scripts posteriores a la actualización de\-. También debe habilitar la comunicación remota de PowerShell en los nodos del clúster. Para obtener información detallada sobre los requisitos del sistema, consulte [requisitos y procedimientos recomendados para la actualización compatible con clústeres](cluster-aware-updating-requirements.md).  
  
**Opciones de ejecución de actualización avanzadas** Además, el administrador puede especificar desde un gran conjunto de opciones de ejecución de actualización avanzadas como el número máximo de veces que se vuelve a intentar el proceso de actualización en cada nodo. Estas opciones pueden especificarse mediante la interfaz de usuario de CAU o los cmdlets de PowerShell de CAU. Esta configuración personalizada se puede guardar en un perfil de ejecución de actualización y se puede volver a usar más adelante para las Ejecuciones de actualización.  
  
**\-de conexión pública en la arquitectura** La CAU incluye características para registrar, anular el registro y seleccionar complementos de\-. la CAU se suministra con dos complementos de\-predeterminados: uno coordina las API de Windows Update Agent \(WUA\) en cada nodo del clúster. el segundo aplica revisiones que se copian manualmente en un recurso compartido de archivos al que pueden tener acceso los nodos del clúster. Si una empresa tiene necesidades únicas que no se pueden cumplir con estos dos complementos\-, la empresa puede crear una nueva conexión de CAU\-de acuerdo con la especificación de la API pública. Para obtener más información, consulte [\-de complemento de actualización compatible con\-de clúster en referencia](https://msdn.microsoft.com/library/hh418084(VS.85).aspx).  
  
Para obtener información sobre la configuración y personalización de los complementos de CAU\-para admitir diferentes escenarios de actualización, vea [Cómo funcionan](assetId:///847b571b-12b3-473c-953f-75a5a1f51333)los complementos de\-.  
  
## <a name="how-can-i-export-the-cau-preview-and-update-results"></a>¿Cómo puedo exportar la vista previa de la CAU y actualizar los resultados?  
La CAU ofrece opciones de exportación a través de la interfaz de línea de comandos\-y a través de la interfaz de usuario.  
  
**Opciones de la interfaz de línea de\-de comandos:**  
  
-   Obtenga una vista previa de los resultados mediante el cmdlet de PowerShell **Invoke\-CauScan | ConvertTo\-XML**. Resultado: XML  
  
-   Informe de los resultados mediante el cmdlet de PowerShell **Invoke\-CauRun | ConvertTo\-XML**. Resultado: XML  
  
-   Informe de los resultados mediante el cmdlet de PowerShell **Get\-CauReport | Exportar\-CauReport**. Resultado: HTML, CSV  
  
**Opciones de la interfaz de usuario:**  
  
-   Copie los resultados del informe desde la pantalla **Vista previa de actualizaciones** . Resultado: CSV  
  
-   Copie los resultados del informe desde la pantalla **Generar informe** . Resultado: CSV  
  
-   Exporte los resultados del informe desde la pantalla **Generar informe** . Resultado: HTML  
  
## <a name="how-do-i-install-cau"></a>¿Cómo se instala la CAU?  
Una instalación de CAU se integra perfectamente en la característica de Clúster de conmutación por error. La CAU se instala de la siguiente manera:  
  
-   Cuando se instala la agrupación en clústeres de conmutación por error en un nodo de clúster, se instala automáticamente la Instrumental de administración de Windows CAU \(proveedor de\) WMI.  
  
-   Cuando se instala la característica herramientas de clúster de conmutación por error en un servidor o equipo cliente, la interfaz de usuario de actualización compatible con clústeres y los cmdlets de PowerShell se instalan automáticamente.
  
## <a name="does-cau-need-components-running-on-the-cluster-nodes-that-are-being-updated"></a>¿Necesita la CAU componentes que se ejecutan en los nodos de clúster que se están actualizando?  
La CAU no necesita un servicio que se ejecute en los nodos del clúster. Sin embargo, la CAU necesita un componente de software \(el proveedor WMI\) instalado en los nodos del clúster. Este componente se instala con la característica Clúster de conmutación por error.  
  
Para habilitar el modo de actualización de\-, el rol en clúster de la CAU también debe agregarse al clúster.  
  
## <a name="what-is-the-difference-between-using-cau-and-vmm"></a>¿Cuál es la diferencia entre el uso de CAU y VMM?  
  
-   System Center Virtual Machine Manager \(\) de VMM se centra en la actualización de clústeres de Hyper\-V, mientras que la CAU puede actualizar cualquier tipo de clúster de conmutación por error compatible, incluidos los clústeres de Hyper\-V.  
  
-   VMM requiere licencias adicionales, mientras que la CAU tiene licencia para todos los servidores de Windows. Las características, las herramientas y la interfaz de usuario de la CAU se instalan con los componentes de Clúster de conmutación por error.  
  
-   Si ya tiene una licencia de System Center, puede seguir usando VMM para actualizar clústeres de Hyper\-V porque ofrece una experiencia de actualización de software y administración integrada.  
  
-   La CAU solo se admite en clústeres que ejecutan Windows Server 2016, Windows Server 2012 R2 y Windows Server 2012. VMM también admite clústeres de Hyper\-V en equipos que ejecutan Windows Server 2008 R2 y Windows Server 2008.  
  
## <a name="can-i-use-remote-updating-on-a-cluster-that-is-configured-for-self-updating"></a>¿Puedo usar la actualización de\-remota en un clúster configurado para la actualización de auto\-?  
Sí. Un clúster de conmutación por error en una configuración de actualización de\-puede actualizarse a través de la actualización de\-remota en\-demanda, de la misma forma que puede forzar un análisis de Windows Update en cualquier momento del equipo, incluso si Windows Update está configurado para instalar las actualizaciones automáticamente. Sin embargo, debe asegurarse de que no haya una ejecución de actualización en curso.  
  
## <a name="can-i-reuse-my-cluster-update-settings-across-clusters"></a>¿Puedo volver a usar la configuración de actualización de clúster en otros clústeres?  
Sí. La CAU admite una cantidad de opciones de ejecución de actualización que determinan cómo se comporta la ejecución de actualización cuando actualiza el clúster. Estas opciones se pueden guardar como un perfil de ejecución de actualización y se pueden volver a usar en cualquier clúster. Se recomienda guardar y volver a usar la configuración en los clústeres de conmutación por error que tengan necesidades de actualización similares. Por ejemplo, puede crear un "Perfil de ejecución de actualización de clúster crítico SQL Server de negocio\-" para todos los clústeres de Microsoft SQL Server que admitan servicios críticos para la empresa\-.  
  
## <a name="where-is-the-cau-plug-in-specification"></a>¿Dónde se encuentra el\-de la CAU en la especificación?  
  
-   [\-de complemento de actualización compatible con\-de clúster en referencia](https://msdn.microsoft.com/library/hh418084(VS.85).aspx)  
  
-   [\-del complemento de actualización compatible con clústeres en el ejemplo](https://code.msdn.microsoft.com/windowsdesktop/Cluster-Aware-Updating-6a8854c9)  
  
## <a name="see-also"></a>Consulta también  
  
-   [Introducción a la actualización compatible con clústeres](cluster-aware-updating.md)  
  
