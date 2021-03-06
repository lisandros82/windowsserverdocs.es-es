---
title: Introducción al panel en Windows Server Essentials
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f70a79de-9c56-4496-89b5-20a1bff2293e
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 2322fa3f4617e8a8450aaf7fd5ead702574bf759
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433135"
---
# <a name="overview-of-the-dashboard-in-windows-server-essentials"></a>Introducción al panel en Windows Server Essentials

>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
 
 Windows Server Essentials y Windows Server 2012 R2 Standard con el rol Experiencia con Windows Server Essentials habilitado incluyen un panel de administración que simplifica las tareas que lleve a cabo para administrar la red y el servidor de Windows Server Essentials. Al usar el panel de Windows Server Essentials puede:  
  
- Finalizar la configuración del servidor  
  
- Tener acceso y realizar tareas administrativas comunes  
  
- Ver alertas del servidor y realizar acciones relacionadas con ellas  
  
- Configurar y cambiar la configuración del servidor  
  
- Tener acceso o buscar temas de ayuda en la Web  
  
- Tener acceso a recursos de la comunidad en la Web  
  
- Administrar cuentas de usuario  
  
- Administrar dispositivos y copias de seguridad  
  
- Administrar el acceso y la configuración de carpetas de servidor y unidades de disco duro  
  
- Ver y administrar aplicaciones de complementos  
  
- Integrarse con los servicios en línea de Microsoft  
  
  Este tema incluye:  
  
- [Características básicas del panel](#BKMK_Design)  
  
- [Características de la página principal del panel](#BKMK_Home)  
  
- [Secciones administrativas del panel](#BKMK_Features)  
  
- [Tener acceso al panel de Windows Server Essentials](#BKMK_AccessDb)  
  
- [Uso del modo seguro](#BKMK_UseSafeMode)  
  
##  <a name="BKMK_Design"></a> Características básicas del panel  
 El panel de Windows Server Essentials le ayuda a tener acceso rápidamente a la información clave y a las características de administración del servidor. El panel incluye varias secciones. La tabla siguiente describe las secciones.  
  
 
  
|Elemento|Característica del panel|Descripción|  
|----------|-----------------------|-----------------|  
|1|Barra de navegación|Haga clic en una sección en la barra de navegación para tener acceso a la información y a las tareas asociadas a dicha sección. Cada vez que abra el panel aparecerá la página **Inicio** de manera predeterminada.|  
|2|Pestañas de subsección|Las pestañas de subsección proporcionan acceso a un segundo nivel de las tareas administrativas de Windows Server Essentials.|  
|3|Panel de lista|La vista de lista muestra los objetos que puede administrar e incluye información básica acerca de cada objeto.|  
|4|Panel de detalles|El panel de detalles muestra información adicional acerca de un objeto seleccionado en la vista de lista.|  
|5|Panel de tareas|El panel de tareas contiene vínculos a herramientas y a información que le ayudan a administrar las propiedades de un objeto específico (como una cuenta de usuario o un equipo) o de la configuración global de la categoría de objetos. El panel de tareas se divide en estas dos secciones:<br /><br /> **Objeto tareas** œ contiene vínculos a información y herramientas que le ayudarán a administración las propiedades de un objeto que seleccione en la vista de lista (por ejemplo, una cuenta de usuario o un equipo).<br /><br /> **Tareas globales** œ contiene vínculos a información y herramientas que le ayudarán a administran tareas globales para un área de características. Las tareas globales incluyen tareas para agregar nuevos objetos, establecer una directiva, etc.|  
|6|Información y configuración|En esta sección se proporciona acceso directo a la configuración del servidor y un vínculo de ayuda de información acerca de la página del panel que está visualizando.|  
|7|Estado de alertas|El estado de alertas proporciona una indicación visual rápida del estado del servidor. Haga clic en la imagen de alerta para ver las alertas críticas e importantes.<br /><br /> **Nota:** En Windows Server Essentials y Windows Server 2012 R2 Standard con el rol experiencia con Windows Server Essentials instalado, el estado de alertas está disponible en el **información y configuración** ficha.|  
|8|Barra de estado|La barra de estado muestra el número de objetos que aparecen en la vista de lista. Las aplicaciones de complementos también pueden mostrar otros estados.|  
  
##  <a name="BKMK_Home"></a> Características de la página principal del panel  
 Al abrir el panel aparece la página **Inicio** de manera predeterminada, con la categoría **CONFIGURACIÓN**. La página **Inicio** del panel de Windows Server Essentials ofrece acceso rápido a las tareas y la información que le ayudarán a personalizar el servidor y configurar características clave. La página de inicio está formada por cuatro áreas funcionales que muestran información y tareas de configuración de las opciones seleccionadas. La tabla siguiente describe las características.  
  
|Elemento|Característica|Descripción|  
|----------|-------------|-----------------|  
|1|Barra de navegación|Haga clic en una sección en la barra de navegación para tener acceso a la información y a las tareas asociadas a dicha sección. Cada vez que abra el panel se mostrará la página **Inicio** de manera predeterminada.|  
|2|Panel de categoría|Este panel muestra las áreas de características que proporcionan acceso rápido a la información y a las herramientas de configuración que le ayudarán a configurar y personalizar el servidor. Haga clic en una categoría para mostrar las tareas y los recursos que están asociados a dicha categoría.|  
|3|Panel de tareas|Este panel muestra vínculos a las tareas y la información que se aplican a una categoría seleccionada. Haga clic en una tarea o recurso para mostrar información adicional.|  
|4|Panel de acciones|Este panel proporciona una breve descripción de una característica o tarea y proporciona vínculos que abren asistentes de configuración y páginas de información. Haga clic en un vínculo para realizar una acción.|  
  
##  <a name="BKMK_Features"></a> Secciones administrativas del panel  
 El panel de Windows Server Essentials organiza la información de la red y las tareas administrativas en áreas funcionales. La página de administración de cada área funcional proporciona información acerca de los objetos asociados a ese área, por ejemplo **Usuarios**o **Dispositivos**. La página de administración también incluye tareas que puede usar para ver o cambiar la configuración, o para ejecutar programas que automatizan las tareas que requieren varios pasos.  
  
 En la tabla siguiente se describen las secciones de administración del panel que están disponibles de manera predeterminada después de la instalación. La tabla también muestra las tareas que están disponibles dentro de cada sección.  
  
|Section|Descripción|  
|-------------|-----------------|  
|Inicio|La página **Inicio** aparece de manera predeterminada cada vez que abre el panel. Incluye información y tareas en las siguientes categorías:<br /><br /> **El programa de instalación** œ completar las tareas de esta categoría para configurar el servidor por primera vez. Para obtener información acerca de estas tareas, consulte [instalar y configurar Windows Server Essentials](../install/Install-and-Configure-Windows-Server-Essentials.md).<br /><br /> **Correo electrónico** œ elija una opción en esta categoría para integrar un servicio de correo electrónico con el servidor.<br /><br /> **Nota:** Esta categoría solo está disponible en Windows Server Essentials.<br /><br /> **SERVICIOS** œ elija una tarea de esta categoría para integrar los servicios en línea de Microsoft con el servidor.<br /><br /> **Nota:** Esta categoría solo está disponible en Windows Server Essentials y Windows Server 2012 R2 Standard con el rol experiencia con Windows Server Essentials habilitado.<br /><br /> **ADD-INS** œ, haga clic en esta categoría para instalar valiosos complementos para su negocio.<br /><br /> **ESTADO rápido** œ muestra el estado de alto nivel de servidor. Haga clic en un estado para ver la información y las opciones de configuración de dicha característica. Si completa todas las tareas de la categoría CONFIGURACIÓN, esta categoría aparecerá en la parte superior del panel Categoría.<br /><br /> **Ayudar a** œ utilice el cuadro de búsqueda para buscar ayuda en la Web. Haga clic en un vínculo para visitar el sitio web de la opción de soporte seleccionada.|  
|Usuarios|Para que los usuarios puedan tener acceso a los recursos proporcionados por Windows Server Essentials deberá crear cuentas de usuario mediante el panel de Windows Server Essentials. Después de crear las cuentas de usuario puede administrarlas mediante las tareas disponibles en la página **Usuarios** del panel. Tareas que puede llevar a cabo en esta página:<br /><br /> -Ver una lista de cuentas de usuario.<br /><br /> -Ver y administrar propiedades de la cuenta de usuario.<br /><br /> -Activar o desactivar las cuentas de usuario.<br /><br /> -Agregar o quitar cuentas de usuario.<br /><br /> -Permite asignar cuentas de red local a cuentas de Microsoft online services, si el servidor está integrado con Office 365.<br /><br /> -Cambiar las contraseñas de cuentas de usuario y administrar la directiva de contraseñas.<br /><br /> Para obtener información acerca de cómo administrar cuentas de usuario, consulte [administrar cuentas de usuario](Manage-User-Accounts-in-Windows-Server-Essentials.md).|  
|Grupos de usuarios|**Nota:** Esta característica solo está disponible en Windows Server Essentials y Windows Server 2012 R2 Standard con el rol experiencia con Windows Server Essentials habilitado.<br /><br /> Tareas que puede llevar a cabo en esta página:<br /><br /> -Ver una lista de grupos de usuarios.<br /><br /> -Ver y administrar grupos de usuarios.<br /><br /> -Agregar o quitar grupos de usuarios.|  
|Grupos de distribución|**Nota:** Esta característica solo está disponible en Windows Server Essentials y Windows Server 2012 R2 Standard con el rol experiencia con Windows Server Essentials habilitado. Esta pestaña solo se muestra cuando Windows Server Essentials está integrado con Office 365.<br /><br /> Tareas que puede llevar a cabo en esta página:<br /><br /> -Ver una lista de grupos de distribución.<br /><br /> -Agregar o quitar grupos de distribución.|  
|Dispositivos|Después de conectar los equipos a la red de Windows Server Essentials puede administrarlos desde la página **Dispositivos** del panel. Tareas que puede llevar a cabo en esta página:<br /><br /> -Ver una lista de equipos que se unen a la red.<br /><br /> -Administración de dispositivos móviles mediante el aprovechamiento de la capacidad de administración de dispositivos móviles de Office 365.<br /><br /> **Nota:** Esta característica solo está disponible en Windows Server Essentials y Windows Server 2012 R2 Standard con el rol experiencia con Windows Server Essentials habilitado.<br /><br /> : Permite ver las propiedades de equipo y las alertas de estado para cada equipo.<br /><br /> : Configure y administre las copias de seguridad del equipo.<br /><br /> -Restaurar archivos y carpetas a los equipos.<br /><br /> -Establecer una conexión a Escritorio remoto a un equipo<br /><br /> -Personalizar la configuración de copia de seguridad del equipo y el historial de archivos<br /><br /> Para obtener información acerca de cómo administrar equipos y copias de seguridad, consulte [administrar dispositivos](Manage-Devices-in-Windows-Server-Essentials.md).|  
|Almacenamiento|En función de la versión de Windows Server Essentials que ejecute, la sección **Almacenamiento** del panel contendrá las siguientes secciones de manera predeterminada.<br /><br /> -El **las carpetas del servidor** subsección incluye tareas que le ayudarán a ver y administrar las propiedades de las carpetas del servidor. La página también incluye tareas para abrir y agregar carpetas del servidor.<br /><br /> -El **unidades de disco duro** página incluye tareas que le ayudarán a ver y comprobar el estado de las unidades que están conectados al servidor.<br /><br /> -En Windows Server Essentials y Windows Server 2012 R2 Standard con el rol de experiencia con Windows Server Essentials habilitado, el **las bibliotecas de SharePoint** página incluye tareas que le ayudarán a administrar las bibliotecas de SharePoint en Office 365 servicio.<br /><br /> Para obtener información acerca de cómo administrar las carpetas del servidor, consulte [administrar carpetas de servidor](Manage-Server-Folders-in-Windows-Server-Essentials.md).<br /><br /> Para obtener información acerca de cómo administrar unidades de disco duro, consulte [Manage Server Storage](Manage-Server-Storage-in-Windows-Server-Essentials.md).|  
|Aplicaciones|-El **aplicaciones** sección del panel de Windows Server Essentials contiene dos subsecciones de manera predeterminada.<br /><br /> Para obtener información acerca de cómo administrar las aplicaciones de complementos, consulte [administrar aplicaciones](Manage-Applications-in-Windows-Server-Essentials.md).<br /><br /> -El **complementos** subsección muestra una lista de complementos instalados y proporciona las tareas que permiten quitar un complemento y tener acceso a información adicional sobre un complemento seleccionado.<br /><br /> -El **Microsoft Pinpoint** subsección muestra una lista de aplicaciones que están disponibles en Microsoft Pinpoint.|  
|Office 365|La pestaña **Office 365** solo aparece cuando Windows Server Essentials está integrado con Microsoft Office 365. Esta sección contiene información de la cuenta de administrador y de la suscripción a Office 365.|  
  
> [!NOTE]
>  Si instala un complemento para el panel de Windows Server Essentials, el complemento puede crear secciones administrativas adicionales. Estas secciones pueden aparecer en la barra de navegación principal o en una pestaña de subsección.  
  
##  <a name="BKMK_AccessDb"></a> Tener acceso al panel de Windows Server Essentials  
 Puede tener acceso al panel mediante uno de los siguientes métodos. El método que elija dependerá de si tiene acceso al panel desde el servidor, desde un equipo conectado a la red de Windows Server Essentials o desde un equipo remoto.  
  
 Para ayudar a mantener una red segura, solo los usuarios que tienen permisos administrativos pueden tener acceso al panel de Windows Server Essentials. Además, no puede usar la cuenta de administrador integrada para iniciar sesión en el panel de Windows Server Essentials desde Launchpad.  
  
###  <a name="BKMK_Server"></a> Acceso al panel desde el servidor  
 Al instalar Windows Server Essentials, el proceso de instalación crea un acceso directo en el panel, en la pantalla **Inicio**, y también en el escritorio. Si el acceso directo no aparece en estas ubicaciones puede usar el panel **Búsqueda** para buscar y ejecutar el programa del panel.  
  
##### <a name="to-access-the-dashboard-from-the-server"></a>Para tener acceso al panel desde el servidor  
  
-   Inicie sesión en el servidor como administrador y, a continuación, realice una de las acciones siguientes:  
  
    -   En la pantalla **Inicio**, haga clic en **Panel**.  
  
    -   En el escritorio, haga doble clic en **Panel**.  
  
    -   En el panel **Búsqueda**, escriba **dashboard** y haga clic en **Panel** en los resultados de búsqueda.  
  
###  <a name="BKMK_Network"></a> Acceso al panel desde un equipo que está conectado a la red  
 En Windows Server Essentials, después de unir un equipo a la red, los administradores pueden usar Launchpad para tener acceso al panel del servidor desde el equipo.  
  
> [!WARNING]
>  En Windows Server Essentials, para conectarse al panel desde el equipo cliente, haga clic en el icono de bandeja y, a continuación, abra el panel en el menú contextual.  
  
##### <a name="to-access-the-dashboard-by-using-the-launchpad"></a>Para tener acceso al panel mediante Launchpad  
  
1.  Desde un equipo que esté unido a la red, abra **Launchpad**.  
  
2.  En el menú de Launchpad, haga clic en **Panel**.  
  
3.  En la página **Iniciar sesión** del panel, escriba las credenciales de administrador de red y, a continuación, presione ENTRAR.  
  
     Se abrirá una conexión remota al panel de Windows Server Essentials.  
  
###  <a name="BKMK_Remote"></a> Acceso al panel desde un equipo remoto  
 Cuando se trabaja desde un equipo remoto, puede acceder al panel de Windows Server Essentials mediante el sitio de acceso Web remoto.  
  
##### <a name="to-access-the-dashboard-by-using-remote-web-access"></a>Para obtener acceso al panel mediante Acceso Web remoto  
  
1.  En el equipo remoto, abra un explorador de Internet, como por ejemplo Internet Explorer.  
  
2.  En la barra de direcciones del explorador de Internet, escriba lo siguiente:**https://<DomainName\>/remote**, donde *DomainName* es el nombre de dominio externo de su organización (por ejemplo, contoso.com).  
  
3.  Escriba su nombre de usuario y contraseña para iniciar sesión el sitio de acceso Web remoto.  
  
4.  En el **equipos** sección del acceso Web remoto**inicio** página; busque el servidor y haga clic en **Connect**.  
  
     Se abrirá una conexión remota al panel.  
  
    > [!NOTE]
    >  Si el servidor no aparece en la sección **Equipos** de la página de inicio, haga clic en **Conectar a más equipos**, busque el servidor en la lista y, a continuación, haga clic en el servidor para conectarse a él.  
    >   
    >  Para conceder a un usuario permiso para tener acceso al panel de acceso Web remoto, abra la página de propiedades de la cuenta de usuario y, a continuación, seleccione el **panel Server** opción el **acceso desde cualquier lugar** ficha.  
  
##  <a name="BKMK_UseSafeMode"></a> Uso del modo seguro  
 La característica de modo seguro de Windows Server Essentials supervisa los complementos instalados en el servidor. Si el panel se vuelve inestable o no responde, el modo seguro detecta y aísla los complementos que podrían estar causando el problema y los muestra en la página **Configuración del Modo seguro** la próxima vez que abra el panel. En la página **Configuración del Modo seguro** puede habilitar y deshabilitar complementos uno por uno para determinar cuál está causando el problema. Puede dejar el complemento deshabilitado para futuros inicios o puede desinstalarlo.  
  
 En cualquier momento puede ver una lista de todos los complementos instalados en el servidor. También puede abrir el panel en el modo seguro, que deshabilita automáticamente todos los complementos que no sean de Microsoft. Windows Server Essentials también le permite tener acceso al panel en el modo seguro desde otro equipo de la red.  
  
#### <a name="to-view-a-list-of-installed-add-ins"></a>Para ver una lista de los complementos instalados  
  
-   En el panel, haga clic en **Ayuda**y, a continuación, haga clic en **Configuración del Modo seguro**.  
  
#### <a name="to-open-the-dashboard-in-safe-mode"></a>Para abrir el panel en Modo seguro  
  
-   En el panel **Búsqueda** , escriba **safe**y haga clic en **Panel (Modo seguro)** en los resultados de búsqueda.  
  
#### <a name="to-open-the-dashboard-in-safe-mode-from-another-computer-on-the-network"></a>Para abrir el panel en Modo seguro desde otro equipo de la red  
  
1.  Desde un equipo conectado a la red, abra Launchpad de Windows Server Essentials y haga clic en **Panel**.  
  
2.  En la página de inicio de sesión del panel, escriba el nombre de usuario y la contraseña de una cuenta que tenga permiso para iniciar sesión en el servidor, seleccione la casilla **Permitirme seleccionar los complementos que se van a cargar** y, a continuación, haga clic en la flecha para iniciar sesión.  
  
## <a name="see-also"></a>Vea también  
  
-   [Administración de aplicaciones](Manage-Applications-in-Windows-Server-Essentials.md)  
  
-   [Administrar Windows Server Essentials](Manage-Windows-Server-Essentials.md)
