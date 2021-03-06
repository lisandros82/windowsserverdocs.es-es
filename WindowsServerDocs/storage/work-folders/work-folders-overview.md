---
ms.assetid: c91c7196-ee0d-4856-8cfb-4c38494ccf1f
title: Introducción a Carpetas de trabajo
ms.prod: windows-server
ms.technology: storage-work-folders
ms.topic: article
author: JasonGerend
manager: dougkim
ms.author: jgerend
ms.date: 06/07/2019
description: 'Introducción a Carpetas de trabajo: es un rol de servidor en Windows Server que proporciona a los usuarios un modo coherente de acceder a los archivos de trabajo desde equipos y dispositivos.'
ms.openlocfilehash: ca76412a6e623b42718fc4f7589f7053073e0f64
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2020
ms.locfileid: "75950194"
---
# <a name="work-folders-overview"></a>Introducción a Carpetas de trabajo

>Se aplica a: Windows Server (canal semianual), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows 10, Windows 8.1, Windows 7

En este tema se explica Carpetas de trabajo, un servicio de rol para servidores de archivo que ejecutan Windows Server y que proporciona a los usuarios un modo coherente de acceder a los archivos de trabajo desde sus equipos y dispositivos.  
  
Si busca descargar o usar carpetas de trabajo en Windows 10, Windows 7 o en un dispositivo iOS o Android, consulte lo siguiente:

- [Carpetas de trabajo para Windows 10](https://support.microsoft.com/help/12370/windows-10-work-folders)
- [Carpetas de trabajo para Windows 7 (descarga de 64 bits)](https://www.microsoft.com/download/details.aspx?id=42558)
- [Carpetas de trabajo para Windows 7 (descarga de 32 bits)](https://www.microsoft.com/download/details.aspx?id=42559)
- [Carpetas de trabajo para iOS](https://itunes.apple.com/app/work-folders/id950878067)
- [Carpetas de trabajo para Android](https://play.google.com/store/apps/details?id=com.microsoft.workfolders)

## <a name="role-description"></a>Descripción del rol

 Con Carpetas de trabajo, los usuarios pueden almacenar y tener acceso a archivos de trabajo en equipos y dispositivos (lo que suele denominarse "Trae tu propio dispositivo [BYOD]"), así como a equipos corporativos. Los usuarios obtienen una ubicación adecuada para almacenar los archivos de trabajo y pueden tener acceso a ellos desde cualquier lugar. Las organizaciones mantienen el control sobre los datos corporativos almacenando los archivos en servidores de archivos administrados centralmente y, de manera opcional, especificando directivas de dispositivo de usuario como contraseñas de cifrado y de bloqueo de pantalla.  
  
 Puedes implementar Carpetas de trabajo con otras implementaciones como Redirección de carpetas, Archivos sin conexión y carpetas particulares. Asimismo, Carpetas de trabajo almacena archivos de usuario en una carpeta del servidor llamada *compartir sincronización*. Puedes especificar una carpeta que ya contenga datos de usuario, lo que te permitirá usar Carpetas de trabajo sin tener que migrar los datos y los servidores o sin tener que retirar inmediatamente la solución que ya estés usando.  
  
## <a name="practical-applications"></a>Aplicaciones prácticas

 Los administradores pueden usar Carpetas de trabajo para que los usuarios puedan tener acceso a sus archivos de trabajo, a la vez que mantienen el almacenamiento centralizado y un control total sobre los datos de la organización. Algunas aplicaciones específicas para Carpetas de trabajo incluyen las siguientes características:  
  
-   Proporcionan un único punto de acceso a los archivos de trabajo desde los equipos y dispositivos tanto del trabajo como personales de un usuario  
  
-   Permiten acceder a los archivos de trabajo aún sin conexión y, en cuanto el equipo o el dispositivo se conecta a Internet o a la intranet, se sincronizan con el servidor de archivos central  
  
-   Se implementan con implementaciones ya existentes como Redirección de carpetas, Archivos sin conexión y carpetas particulares  
  
-   Usan tecnología de administración del servidor de archivos (como, por ejemplo, clasificación de archivos y cuotas de carpetas) para administrar datos de usuario  
  
-   Especifican directivas de seguridad que sirven para indicar a los equipos y dispositivos de los usuarios que deben encriptar Carpetas de trabajo y usar una contraseña en la pantalla de bloqueo  
  
-   Usan clústeres de conmutación por error con Carpetas de trabajo para proporcionar una solución de alta disponibilidad  
  
## <a name="important-functionality"></a>Funcionalidad importante

 Carpetas de trabajo incluye las siguientes funcionalidades.  
  
| Funcionalidad | Disponibilidad | Descripción |  
| ------------------- | ------------------ | ----------------- |  
| Servicio de rol de Carpetas de trabajo en el Administrador del servidor | Windows Server 2019, Windows Server 2016 o Windows Server 2012 R2 | Los Servicios de almacenamiento y archivos son una buena manera de configurar los recursos compartidos de sincronización (es decir, carpetas que almacenan los archivos de trabajo del usuario), supervisar Carpetas de trabajo y administrar los recursos compartidos de sincronización y el acceso de los usuarios |
| Cmdlets de Carpetas de trabajo | Windows Server 2019, Windows Server 2016 o Windows Server 2012 R2 | Módulo de Windows PowerShell que contiene cmdlets completos para administrar los servidores de Carpetas de trabajo |  
| Integración de Carpetas de trabajo con Windows | 10 de Windows<br /><br /> Windows 8.1<br /><br /> Windows RT 8.1<br /><br /> Windows 7 (es necesario descargarlo) | Carpetas de trabajo proporciona las siguientes funcionalidades en los equipos de Windows:<br /><br /> -   Un elemento del Panel de control que configura y supervisa Carpetas de trabajo<br />-   Integración con el Explorador de archivos que te permite acceder fácilmente a los archivos de Carpetas de trabajo<br />-   Un motor de sincronización que transfiere los archivos hacia y desde un servidor de archivos central a la vez que maximiza la duración de la batería y el rendimiento del sistema |
| Aplicación Carpetas de trabajo para dispositivos | Android<br /><br /> Apple iPhone e iPad® | Gracias a esta aplicación, puedes acceder a los archivos que tienes en Carpetas de trabajo usando los dispositivos más populares |  
  
## <a name="new-and-changed-functionality"></a>Funcionalidad nueva y modificada
  
En la siguiente tabla se describen algunos de los principales cambios de Carpetas de trabajo.  
  
| Característica/funcionalidad | ¿Nueva o actualizada? | Descripción |
| ---------------------------- | --------------------- | ----------------- |
| Soporte técnico del Proxy de aplicación de Azure AD | Se ha agregado a la versión 1703 de Windows 10, Android, iOS | Los usuarios remotos pueden acceder de forma segura a sus archivos en el servidor de Carpetas de trabajo mediante el uso del Proxy de aplicación de Azure AD. |
| Replicación de cambio más rápida | Actualizada en Windows 10 y Windows Server 2016. | En Windows Server 2012 R2, cuando los cambios efectuados en el archivo se sincronizan con el servidor de Carpetas de trabajo, no se notifica el cambio a los clientes y estos esperan hasta 10 minutos para obtener la actualización. Cuando se usa Windows Server 2016, el servidor de carpetas de trabajo notifica inmediatamente a los clientes de Windows 10 y los cambios de archivo se sincronizan inmediatamente. Esta funcionalidad es nueva en Windows Server 2016 y requiere un cliente de Windows 10. Si usas un cliente anterior, o si el servidor de Carpetas de trabajo es Windows Server 2012 R2, el cliente seguirá buscando cambios cada 10 minutos. |  
| Se ha integrado con Windows Information Protection (WIP) | Se ha agregado a la versión 1607 de Windows 10 | Si un administrador implementa WIP, Carpetas de trabajo puede aplicar la protección de datos mediante el cifrado de los datos del equipo. El cifrado usa una clave asociada con el identificador de empresa, que puede ser borrado de forma remota mediante un paquete de administración de dispositivos móviles compatibles, como Microsoft Intune. |  
| Integración con Microsoft Office | Se ha agregado a la versión 1511 de Windows 10 | En Windows 8.1 puedes acceder a Carpetas de trabajo desde las mismas aplicaciones de Office haciendo clic o pulsando la opción "Este equipo" y, a continuación, accediendo a la ubicación de Carpetas de trabajo de tu PC. En Windows 10 es aún más fácil acceder a Carpetas de trabajo; para ello, debes agregar esta característica a la lista de ubicaciones que Office muestra al guardar o abrir archivos. Para obtener más información, consulta [Carpetas de trabajo en Windows 10](https://windows.microsoft.com/windows-10/work-folders-in-windows-10) y [Solucionar problemas al usar Carpetas de trabajo como un Lugar en Microsoft Office](https://social.technet.microsoft.com/wiki/contents/articles/32881.troubleshooting-using-work-folders-as-a-place-in-microsoft-office.aspx). |  
  
## <a name="software-requirements"></a>Requisitos de software

Carpetas de trabajo presenta los siguientes requisitos de software en cuanto a servidores de archivos e infraestructura de red:  
  
-   Un servidor que ejecute Windows Server 2019, Windows Server 2016 o Windows Server 2012 R2 para hospedar recursos compartidos de sincronización con archivos de usuario  
  
-   Un volumen con formato de sistema de archivos NTFS para almacenar archivos de usuario.  
  
-   Para aplicar directivas de contraseña en equipos con Windows 7, debes usar las directivas de contraseña de directiva de grupo. También debes excluir los equipos con Windows 7 de las directivas de contraseña de Carpetas de trabajo (si es que los usas).

-   Un certificado de servidor para cada servidor de archivos que se alojará en Carpetas de trabajo. Estos certificados deben proceder de una entidad de certificación (CA) de confianza para los usuarios; lo más indicado es que sea una entidad de certificación pública.

-   Opta Un bosque de Active Directory Domain Services con las extensiones de esquema en Windows Server 2012 R2 para admitir automáticamente la referencia de equipos y dispositivos al servidor de archivos correcto al usar varios servidores de archivos.  
  
Existen más requisitos para permitir que los usuarios se sincronicen a través de Internet:  
  
-   La capacidad de lograr que un servidor sea accesible desde Internet mediante la creación de reglas de publicación en el proxy inverso o la puerta de enlace de red de la organización.  
  
-   (Opcional) Un nombre de dominio registrado públicamente y la capacidad de crear más registros DNS públicos para el dominio.  
  
-   (Opcional) Una infraestructura de Servicios de federación de Active Directory (AD FS) cuando se use la autenticación de AD FS.  
  
Carpetas de trabajo presenta los siguientes requisitos de software relativos a los equipos cliente:  
  
-   El equipo y los dispositivos deben funcionar con uno de los siguientes sistemas operativos:  
  
    -   10 de Windows  
  
    -   Windows 8.1  
  
    -   Windows RT 8.1  
  
    -   Windows 7  
  
    -   Android 4.4 KitKat y versiones posteriores  
  
    -   iOS 10.2 y versiones posteriores  
  
-   Los equipos con Windows 7 deben ejecutar una de las siguientes ediciones de Windows:  
  
    -   Windows 7 Professional  
  
    -   Windows 7 Ultimate  
  
    -   Windows 7 Enterprise  
  
-   Los equipos con Windows 7 deben estar unidos al dominio de la organización (no pueden estar unidos a un grupo de trabajo).  
  
-   Debe haber espacio libre suficiente en una unidad local con formato NTFS para almacenar todos los archivos de usuario en Carpetas de trabajo, además de otros 6 GB extra de espacio libre en caso de que Carpetas de trabajo se encuentre en la unidad del sistema (como sucede de forma predeterminada). Carpetas de trabajo usa la siguiente ubicación de forma predeterminada **%USERPROFILE%\Work Folders**  
  
     No obstante, esta ubicación se puede modificar durante la instalación (se pueden usar ubicaciones como tarjetas microSD y unidades USB con el formato del sistema de archivos NTFS, pero cabe recordar que la sincronización se detendrá si se extraen las unidades).  
  
     El tamaño máximo de los archivos individuales es de 10 GB de forma predeterminada. No existe límite de almacenamiento por usuario, si bien los administradores pueden hacer uso de la función de cuotas del Administrador de recursos del servidor de archivos para implementar cuotas.  
  
-   Carpetas de trabajo no admite revertir el estado de máquina virtual de las máquinas virtuales cliente. En su lugar, debes realizar operaciones de copia de seguridad y restauración desde la máquina virtual cliente, ya sea por medio de Copia de seguridad de imagen del sistema o de cualquier otra aplicación de copia de seguridad.  
  
## <a name="work-folders-compared-to-other-sync-technologies"></a>Carpetas de trabajo en comparación con otras tecnologías de sincronización  

La siguiente tabla describe la posición de las distintas tecnologías de sincronización de Microsoft y cuándo debes usar cada una.  
  
| | Carpetas de trabajo | Archivos sin conexión | OneDrive para la Empresa | OneDrive |
| - | ------------------ | ------------------- | -------------------------- | -------------- |
| **Resumen de tecnología** | Sincroniza archivos que se almacenan en un servidor de archivos con otros equipos y dispositivos | Sincroniza archivos que se almacenan en un servidor de archivos con otros equipos que tienen acceso a la red corporativa (puede sustituirse por Carpetas de trabajo) | Sincroniza archivos que se almacenan en Office 365 o en SharePoint con otros equipos y dispositivos que se encuentran dentro o fuera de una red corporativa y proporciona la funcionalidad de colaboración de documentos | Sincroniza archivos personales almacenados en OneDrive con otros equipos, dispositivos y equipos Mac |
| **Diseñado para proporcionar acceso de usuario a los archivos de trabajo** | Sí | Sí | Sí | No |
| **Servicio en la nube** | Ninguna | Ninguna | Office 365 | Microsoft OneDrive |
| **Servidores de la red interna** | Servidores de archivos que ejecutan Windows Server 2012 R2 o Windows Server 2016 | Servidores de archivos | Servidor de SharePoint (opcional) | Ninguna |
| **Clientes compatibles** | Equipos, iOS, Android | Equipos de una red corporativa o que estén conectados a través de DirectAccess, VPN u otras tecnologías de acceso remoto | Equipos, iOS, Android, Windows Phone | Equipos, equipos Mac, Windows Phone, iOS, Android |
  
> [!NOTE]
>  Además de las tecnologías de sincronización de la tabla anterior, Microsoft te ofrece otras tecnologías de replicación como, por ejemplo, la replicación de DFS que está diseñada para la replicación de servidor a servidor y BranchCache, que está pensada para funcionar como una tecnología de aceleración WAN de la sucursal. Para obtener más información, consulta [Espacios de nombres y replicación DFS](https://technet.microsoft.com/library/jj127250(v=ws.11).aspx) e [Introducción a BranchCache](https://technet.microsoft.com/library/hh831696(v=ws.11).aspx) 
  
## <a name="server-manager-information"></a>Información sobre el Administrador del servidor  

Carpetas de trabajo forma parte del rol Servicios de archivos y almacenamiento. Puedes instalar Carpetas de trabajo mediante el asistente para agregar roles y características o el cmdlet `Install-WindowsFeature`. Ambos métodos realizan las siguientes acciones:  
  
-   Agregan la página de **Carpetas de trabajo** a **Servicios de archivos y almacenamiento** en el Administrador de servidores  
  
-   Instalan el servicio de recursos compartidos de sincronización de Windows que se usa en Windows Server para hospedar los recursos compartidos de sincronización  
  
-   Instalan el módulo SyncShare de Windows PowerShell para poder administrar Carpetas de trabajo en el servidor  
  
## <a name="interoperability-with-windows-azure-virtual-machines"></a>Interoperabilidad con las máquinas virtuales de Microsoft Azure

 Puedes ejecutar este servicio de rol de Windows Server en una máquina virtual en Microsoft Azure. Este escenario se ha probado con Windows Server 2012 R2 y Windows Server 2016.  
  
Para obtener más información acerca de cómo comenzar a usar las máquinas virtuales de Microsoft Azure, visita el [sitio web de Microsoft Azure](http://www.windowsazure.com/documentation/services/virtual-machines).  
  
## <a name="see-also"></a>Consulta también

 Para obtener más información relacionada, consulta los siguientes recursos.  
  
| Tipo de contenido | Referencias |
| ------------------ | ---------------- |
| **Evaluación del producto** | [carpetas de trabajo de -   para Android: publicado](https://blogs.technet.microsoft.com/filecab/2016/03/16/work-folders-for-android-released) (entrada de blog)<br />[carpetas de trabajo de -   para iOS: versión de la aplicación de iPad](https://blogs.technet.com/b/filecab/archive/2015/01/16/work-folders-for-ios-ipad-app-release.aspx) (entrada de blog)<br />-   [Introducción a las carpetas de trabajo en Windows Server 2012 R2](https://blogs.technet.com/b/filecab/archive/2013/07/09/introducing-work-folders-on-windows-server-2012-r2.aspx) (entrada de blog)<br />-   [Introducción a las carpetas de trabajo](https://channel9.msdn.com/posts/Introduction-to-Work-Folders) (vídeo de Channel 9)<br />-   de la [implementación del laboratorio de pruebas de carpetas de trabajo](https://blogs.technet.com/b/filecab/archive/2013/07/10/work-folders-test-lab-deployment.aspx) (entrada de blog)<br />-   [carpetas de trabajo para Windows 7](https://blogs.technet.com/b/filecab/archive/2014/04/24/work-folders-for-windows-7.aspx) (entrada de blog) |
| **Implementación** | -   [diseñar una implementación de carpetas de trabajo](plan-work-folders.md)<br />-   [implementar carpetas de trabajo](deploy-work-folders.md)<br />-   [implementar carpetas de trabajo con AD FS y proxy de aplicación web (WAP)](deploy-work-folders-adfs-overview.md)<br />-   [implementar carpetas de trabajo con Azure ad proxy de aplicación](https://blogs.technet.microsoft.com/filecab/2017/05/31/enable-remote-access-to-work-folders-using-azure-active-directory-application-proxy/)<br />[Guía de migración de - archivos sin conexión (CSC) a carpetas de trabajo](https://blogs.technet.microsoft.com/filecab/2016/08/12/offline-files-csc-to-work-folders-migration-guide/)<br />-   [consideraciones de rendimiento de las implementaciones de carpetas de trabajo](https://blogs.technet.com/b/filecab/archive/2013/11/01/performance-considerations-for-large-scale-work-folders-deployments.aspx)<br />-   [carpetas de trabajo para Windows 7 (descarga de 64 bits)](https://www.microsoft.com/download/details.aspx?id=42558)<br />-   [carpetas de trabajo para Windows 7 (descarga de 32 bits)](https://www.microsoft.com/download/details.aspx?id=42559) |
| **Operaciones** | -   [carpetas de trabajo de la aplicación de iPad: preguntas más frecuentes](https://windows.microsoft.com/windows/work-folders-ipad-faq) (para usuarios)<br />-   de [carpetas de trabajo](https://blogs.technet.com/b/filecab/archive/2013/08/09/work-folders-certificate-management.aspx) (entrada de blog)<br />-   [supervisar implementaciones de carpetas de trabajo de Windows Server 2012 R2](https://blogs.technet.com/b/filecab/archive/2013/10/15/monitoring-windows-server-2012-r2-work-folders-deployments.aspx) (entrada de blog)<br />[cmdlets de -   SyncShare (carpetas de trabajo) en Windows PowerShell](https://docs.microsoft.com/powershell/module/syncshare/?view=win10-ps)<br />[tarjeta de referencia rápida de los cmdlets de PowerShell de servicios de archivos y almacenamiento de -   para Windows Server 2012 R2 Preview Edition](https://blogs.technet.com/b/filecab/archive/2013/07/30/storage-and-file-services-powershell-cmdlets-quick-reference-card-for-windows-server-2012-r2-preview-edition.aspx) |
| **Solución de problemas** | -   [Windows Server 2012 R2: resolver conflictos de puerto con sitios web y carpetas de trabajo de IIS](https://blogs.technet.com/b/filecab/archive/2013/10/15/windows-server-2012-r2-resolving-port-conflict-with-iis-websites-and-work-folders.aspx) (entrada de blog)<br />-   [errores comunes en carpetas de trabajo](https://social.technet.microsoft.com/wiki/contents/articles/30578.common-errors-in-work-folders.aspx) |
| **Recursos de la comunidad** | -   [Foro de almacenamiento y servicios de archivos](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverfiles)<br />-   [el equipo de almacenamiento en el blog de Microsoft-File Cabinet](https://blogs.technet.com/b/filecab/)<br />-   [consultar al blog del equipo de servicios de directorio](https://blogs.technet.com/b/askds/) |  
| **Tecnologías relacionadas** | [almacenamiento -   en Windows Server 2016](../storage.md)<br>-   [servicios de archivos y almacenamiento](https://technet.microsoft.com/library/hh831487(v=ws.11).aspx)<br />-   [Administrador de recursos servidor de archivos](https://technet.microsoft.com/library/hh831701(v=ws.11).aspx)<br />-   de los [perfiles de usuario móvil, archivos sin conexión y redirección de carpetas](https://technet.microsoft.com/library/hh848267(v=ws.11).aspx)<br />-   [BranchCache](https://technet.microsoft.com/library/hh831696(v=ws.11).aspx)<br />-   [espacios de nombres DFS y replicación DFS](https://technet.microsoft.com/library/jj127250(v=ws.11).aspx) |
