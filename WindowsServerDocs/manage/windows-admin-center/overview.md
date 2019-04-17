---
title: Información general de Windows Admin Center
description: Obtén información sobre cómo administrar Windows Server con Windows Admin Center (Proyecto Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: high
ms.prod: windows-server-threshold
ms.openlocfilehash: d941e9884dced40ce750645b662d8df73503bc41
ms.sourcegitcommit: 475292afc919c6d17569f05007a97bc6b92dd225
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "9267781"
---
# Windows Admin Center

>Se aplica a: Windows Admin Center, Versión preliminar de Windows Admin Center

¡Bienvenido a Windows Admin Center!

**Windows Admin Center** (con nombre en código **Proyecto Honolulu**) es una evolución de las herramientas de administración incluidas de Windows Server; es un panel único que consolida todos los aspectos de administración de servidores locales y remotos. Al tratarse de una experiencia de administración basada en explorador implementada localmente, no se requiere una conexión a Internet ni Azure. Centro de administración de Windows le ofrece control total de todos los aspectos de la implementación, incluidas redes privadas que no están conectadas a Internet.

## Introducción

>[!VIDEO https://www.youtube.com/embed/PcQj6ZklmK0]

![Infografía de Windows Admin Center](media/WAC1809Poster_thumb.PNG)

[Descargar el PDF](https://github.com/MicrosoftDocs/windowsserverdocs/raw/master/WindowsServerDocs/manage/windows-admin-center/media/WindowsAdminCenter1809Poster.pdf)

## Inicio rápido

Puedes tener Windows Admin Center en funcionamiento y ejecutándose en tu entorno en minutos:

1. [Descargar](https://aka.ms/windowsadmincenter)
2. [Instalar](deploy/install.md)
3. [Comenzar](use/get-started.md)

## Contenido resumido

<table>
    <tr></tr>
    <tr>
        <td style="vertical-align: top;">
            <h3>Comprender</h3>
            <ul>
            <li><a href="understand/what-is.md">¿Qué es Windows Admin Center?</a>
            <li><a href="understand/faq.md">Preguntas más frecuentes</a>
            <li><a href="understand/case-studies.md">Casos prácticos</a>
            <li><a href="understand/related-management.md">Productos de administración relacionadas</a>
            <li><a href="understand/videos.md">Vídeos</a>
            </ul>
        </td>
        <td style="vertical-align: top;">
            <h3>Plan</h3>
            <ul>
            <li><a href="plan/installation-options.md">¿Qué tipo de instalación es el adecuado para ti?</a>
            <li><a href="plan/user-access-options.md">Opciones de acceso de usuario</a>
            <li><a href="plan/azure-integration-options.md">¿Qué opciones de integración de Azure existen?</a>
            <br>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: top;">
            <h3>Implementar</h3>
            <ul>
            <li><a href="deploy/prepare-environment.md">Preparar el entorno</a>
            <li><a href="deploy/install.md">Instalar Windows Admin Center</a>
            <li><a href="deploy/high-availability.md">Habilitar la alta disponibilidad</a>
         </ul>
        </td>
        <td style="vertical-align: top;">
            <h3>Configurar</h3>
            <ul>
            <li><a href="configure/settings.md">Configuración de Windows Admin Center</a>
            <li><a href="configure/user-access-control.md">Permisos y control de acceso de usuarios</a>
            <li><a href="configure/using-extensions.md">Extensiones</a>
            <li><a href="configure/azure-integration.md">Integrar con Azure</a>
            <li><a href="configure/manage-azure-vms.md">Administrar las VM de Azure con Windows Admin Center</a>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: top;">
            <h3>Usar</h3>
            <ul>
            <li><a href="use/get-started.md">Iniciar y agregar conexiones</a>
            <li><a href="use/manage-servers.md">Administrar servidores</a>
            <li><a href="use/manage-hyper-converged.md">Administrar la infraestructura hiperconvergida</a>
            <li><a href="use/manage-failover-clusters.md">Administrar clústeres de conmutación por error</a>
            <li><a href="use/manage-virtual-machines.md">Administrar máquinas virtuales</a>
            <li><a href="use/azure-services.md">Aprovechar los servicios de Azure</a>
            <li><a href="use/troubleshooting.md">Pasos de solución de problemas comunes</a>
            <li><a href="use/logging.md">Registro</a>
            <li><a href="use/known-issues.md">Problemas conocidos</a>
            </ul>
        </td>
        <td style="vertical-align: top;">
            <h3>Ampliar</h3>
            <ul>
            <li><a href="extend/extensibility-overview.md">Información general de extensiones</a>
            <li><a href="extend/understand-extensions.md">Descripción de extensiones</a>
            <li><a href="extend/developing-extensions.md">Desarrollar una extensión</a>
            <li><a href="extend/publish-extensions.md">Guías</a>
            <li><a href="extend/publish-extensions.md">Publicar extensiones</a>
            </ul>
        </td>
    </tr>

</table>

## Historial de versiones

Obtén información sobre nuestras últimas funciones:

- La versión [1903] (https://aka.ms/wac1903) lleva las notificaciones por correo electrónico desde el Azure Monitor, la capacidad de agregar las conexiones de servidor o PC desde Active Directory y las nuevas herramientas para administrar Active Directory, DHCP y DNS.
- La versión [1902] (https://aka.ms/wac1902) agregó una lista de conexiones compartidas y mejoras a la administración de redes definidas por software (SDN), incluidas nuevas herramientas de SDN para administrar ACL, conexiones de puerta de enlace y redes lógicas.
- La versión [1812](https://aka.ms/wac1812) agregó un tema oscuro (en versión preliminar), opciones de configuración de energía, información BMC y compatibilidad con PowerShell para administrar [las extensiones](./configure/using-extensions.md#manage-extensions-with-powershell) y [las conexiones](./use/get-started.md#use-powershell-to-import-or-export-your-connections-with-tags).
- La versión [1809.5](https://aka.ms/wac1809.5) es una actualización acumulativa de disponibilidad general que incluye una serie de mejoras de calidad y funcionales, así como correcciones de errores en toda la plataforma y algunas nuevas funciones en la solución de administración de la infraestructura hiperconvergida.
- La versión [1809](https://cloudblogs.microsoft.com/windowsserver/2018/09/20/windows-admin-center-1809-and-sdk-now-generally-available/) era una versión de disponibilidad general que aportó funciones que anteriormente estaban en la vista previa en el canal de disponibilidad general.
- La versión [1808](https://aka.ms/WACPreview1808-InsiderBlog) agregó la herramienta Aplicaciones instaladas, una gran cantidad de mejoras de fondo y actualizaciones importantes del SDK de vista previa.
- La versión [1807](https://aka.ms/WACPreview1807-InsiderBlog) agregó una experiencia de conexión optimizada de Azure, mejoras en la página de inventario de VM, funcionalidad de uso compartido de archivos, integración de administración de actualizaciones en Azure y mucho más. 
- La versión [1806](https://aka.ms/WACPreview1806-InsiderBlog) agregó mostrar el script de PowerShell, administración SDN, conexiones de 2008 R2, SDN, tareas programadas y muchas otras mejoras.
- Versión 1804.25 - Actualización de mantenimiento para admitir usuarios instalando Windows Admin Center en entornos completamente sin conexión.
- Versión [1804](https://cloudblogs.microsoft.com/windowsserver/2018/04/12/announcing-windows-admin-center-our-reimagined-management-experience/) - El Proyecto Honolulu se convierte en Windows Admin Center y agrega características de seguridad y control de acceso basado en roles. Nuestra primera versión de disponibilidad general.
- La versión [1803](https://blogs.windows.com/windowsexperience/2018/03/13/announcing-project-honolulu-technical-preview-1803-and-rsat-insider-preview-for-windows-10) agregó compatibilidad para control de acceso de Azure AD, registro detallado, reajuste de tamaño de contenido y un montón de mejoras de herramientas.
- La versión [1802](https://blogs.windows.com/windowsexperience/2018/02/13/announcing-windows-server-insider-preview-build-17093-project-honolulu-technical-preview-1802) agregó compatibilidad para accesibilidad, localización, implementaciones de alta disponibilidad, etiquetado, configuración del host de Hyper-V y autenticación de puerta de enlace.
- La versión [1712](https://blogs.windows.com/windowsexperience/2017/12/19/announcing-project-honolulu-technical-preview-1712-build-05002) agregó más características de máquina virtual y mejoras de rendimiento en las herramientas.
- La versión [1711](https://cloudblogs.microsoft.com/windowsserver/2017/12/01/1711-update-to-project-honolulu-technical-preview-is-now-available/) agregó herramientas altamente anticipadas (Escritorio remoto y PowerShell) junto con otras mejoras.
- La versión [1709](https://cloudblogs.microsoft.com/windowsserver/2017/09/22/project-honolulu-technical-preview-is-now-available-for-download/) se lanzó como nuestra primera versión preliminar pública.

## Mantenerse actualizado

<a target="_blank" class="mscom-link twitter-follow-link" title="Síguenos en Twitter" aria-label="Follow us on Twitter" data-info="Twitter" href="https://twitter.com/servermgmt"><picture><source srcset="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOolR" media="(min-width:0)"><img srcset="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOolR" alt="Follow us on Twitter" src="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOolR"></picture></a>
 | 
<a target="_blank" class="mscom-link blogs-follow-link" title="Leer nuestros blogs" aria-label="Visit our Blogs" data-info="Blogs" href="https://blogs.technet.microsoft.com/servermanagement/"><picture><source srcset="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOtyw" media="(min-width:0)"><img srcset="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOtyw" alt="Follow us on Blogs" src="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOtyw"></picture></a>