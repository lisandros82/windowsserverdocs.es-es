---
title: Crear una plantilla de filtro de archivos
description: En este artículo se describe cómo crear una plantilla de filtro de archivos
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 63824f016180ce5a92d9a16b9ee0d26a46e5db72
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71394211"
---
# <a name="create-a-file-screen-template"></a>Crear una plantilla de filtro de archivos

> Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Una *plantilla de filtro de archivos* define un conjunto de grupos de archivos en los que se aplicará un filtro, el tipo de filtrado que se aplicará (activo o pasivo) y, de forma opcional, un conjunto de notificaciones que se generarán automáticamente cuando un usuario guarda, o trata de guardar, un archivo no autorizado.

El Administrador de recursos del servidor de archivos puede enviar mensajes de correo electrónico a los administradores o a usuarios específicos, registrar un evento, ejecutar un comando o script o generar informes. Puedes configurar más de un tipo de notificación para un evento de filtro de archivos.

Al crear filtros de archivos exclusivamente a partir de plantillas, es posible administrarlos centralmente actualizando las plantillas en lugar de repetir los cambios en cada uno de los filtros de archivos. Esta característica simplifica la implementación de los cambios de las directivas de almacenamiento ya que proporciona un punto central donde se pueden llevar a cabo todas las actualizaciones.

> [!Important]
> Para enviar notificaciones por correo electrónico y configurar los informes de almacenamiento con los parámetros adecuados para tu entorno de servidor, primero debes establecer las opciones generales del Administrador de recursos del servidor de archivos. Para obtener más información, consulta [Configurar las opciones del Administrador de recursos del servidor de archivos](setting-file-server-resource-manager-options.md).

## <a name="to-create-a-file-screen-template"></a>Para crear una plantilla de filtro de archivos

1.  En **Administración del filtrado de archivos**, haz clic en el nodo **Plantillas de filtro de archivos**.

2.  Haz clic con el botón derecho en **Plantillas de filtro de archivos** y haz clic en **Crear plantilla de filtro de archivos** (o selecciona **Crear plantilla de filtro de archivos** en el panel **Acciones**). Se abrirá el cuadro de diálogo **Crear plantilla de filtro de archivos**.

3.  Si quieres copiar las propiedades de una plantilla existente para usarla como base de la nueva plantilla, selecciona una plantilla en la lista desplegable **Copiar propiedades de la plantilla** y luego haz clic en **Copiar**.

    Tanto si ha elegido usar las propiedades de una plantilla existente como si está creando una nueva plantilla, modifique o defina los siguientes valores en la pestaña **Configuración**:

4.  En el cuadro de texto **Nombre de plantilla**, escribe el nombre de la nueva plantilla.

5.  En **Tipo de filtrado**, haz clic en las opciones **Filtrado activo** o **Filtrado pasivo**. (El filtrado activo impide que los usuarios guarden archivos que formen parte de los grupos de archivos bloqueados y genera notificaciones cuando los usuarios intentan guardar archivos no autorizados. El filtrado pasivo envía notificaciones configuradas, pero no impide que los usuarios guarden archivos).

6.  Para especificar los grupos de archivos a los que aplicar un filtro:

    En **Grupos de archivos**, selecciona cada grupo de archivos que quieres incluir. (Para seleccionar la casilla de verificación del grupo de archivos, haz doble clic en la etiqueta de grupo de archivos).

    Si desea ver los tipos de archivo que un grupo de archivos incluye y excluye, haga clic en la etiqueta del grupo de archivos y, a continuación, haga clic en **Editar**. Para crear un nuevo grupo de archivos, haga clic en **crear**.

    También puedes configurar el Administrador de recursos del servidor de archivos para generar una o varias notificaciones si estableces las siguientes opciones de las pestañas **Mensaje de correo electrónico**, **Registro de eventos**, **Comando** e **Informe**.

7.  Para configurar notificaciones por correo electrónico:

    En la pestaña **Mensaje de correo electrónico**, establece las siguientes opciones:

    -   Para notificar a los administradores que un usuario o aplicación está intentando guardar un archivo no autorizado, selecciona la casilla de verificación **Enviar mensaje de correo electrónico a los siguientes administradores** y luego escribe los nombres de las cuentas administrativas que recibirán las notificaciones. Usa el formato *cuenta*@*dominio* y usa punto y coma para separar varias cuentas.
    -   Para enviar un correo electrónico al usuario que intentó guardar el archivo, selecciona la casilla de verificación **Enviar correo electrónico al usuario que ha intentado guardar un archivo no autorizado**.
    -   Para configurar el mensaje, edita la línea de asunto y el cuerpo del mensaje predeterminados que se muestran. El texto que aparece entre paréntesis inserta información variable sobre el evento de filtro de archivos que originó la notificación. Por ejemplo, la variable \[**source IO Owner**\] inserta el nombre del usuario que ha intentado guardar un archivo no autorizado. Para insertar variables adicionales en el texto, haz clic en **Insertar variable**.
    -   Para configurar los encabezados adicionales (incluidos De, Cc, Bcc y Responder-a), haz clic en **Encabezados de correo electrónico adicionales**.

8.  Para registrar un error en el registro de eventos si un usuario trata de guardar un archivo no autorizado:

    En la pestaña **Registro de eventos**, selecciona la casilla de verificación **Enviar advertencia al registro de eventos** y edita la entrada de registro predeterminada.

9.  Para ejecutar un comando o script si un usuario trata de guardar un archivo no autorizado:

    En la pestaña **Comando**, selecciona loa casilla de verificación **Ejecutar este comando o script**. Luego escribe el comando o haz clic en **Examinar** para buscar la ubicación en la que está almacenado el script. También puedes especificar argumentos de comando; para ello, selecciona un directorio de trabajo para el comando o script o modifica la configuración de seguridad de comandos.

10. Para generar uno o varios informes de almacenamiento si un usuario trata de guardar un archivo no autorizado:

    En la pestaña **Informe**, selecciona la casilla de verificación **Generar informes** y luego selecciona los informes que quieres generar. (Puedes elegir uno o varios destinatarios de correos electrónicos administrativos para enviar el informe o puedes enviar por correo electrónico el informe al usuario que intentó guardar el archivo).

    El informe se guarda en la ubicación predeterminada para los informes de incidentes, que se puede modificar en el cuadro de diálogo **Opciones del Administrador de recursos del servidor de archivos**.

11. Después de seleccionar todas las propiedades de la plantilla de archivos que quieres usar, haz clic en **Aceptar** para guardar la plantilla.

## <a name="see-also"></a>Vea también

-   [Administración del filtrado de archivos](file-screening-management.md)
-   [Configurar las opciones del Administrador de recursos del servidor de archivos](setting-file-server-resource-manager-options.md)
-   [Editar las propiedades de la plantilla de filtro de archivos](edit-file-screen-template-properties.md)

