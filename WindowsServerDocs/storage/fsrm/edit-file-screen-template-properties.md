---
title: Editar las propiedades de la plantilla de filtro de archivos
description: En este artículo se describe cómo editar las propiedades de la plantilla de filtro de archivos
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 9e84545be86bdb8fcba09d0ff49ac98b44cd7bdf
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403123"
---
# <a name="edit-file-screen-template-properties"></a>Editar las propiedades de la plantilla de filtro de archivos

> Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Al realizar cambios en una plantilla de filtro de archivos, tienes la opción de ampliar estos cambios a los filtros de archivo que se crearon con la plantilla original de filtro de archivos. Puedes elegir entre modificar solo los filtros de archivos que coincidan con la plantilla original o todos los filtros de archivos que se derivan de la plantilla original, independientemente de las modificaciones que se han realizado en los filtros de archivos desde que se crearon. Esta característica simplifica el proceso de actualización de las propiedades de los filtros de archivos, ya que ofrece un punto central donde se pueden llevar a cabo todos los cambios.

> [!Note]
> Si los cambios se aplican a todos los filtros de archivos que se derivan de la plantilla original, se sobrescribirán las propiedades personalizadas de filtros de archivos que hayas creado.

## <a name="to-edit-file-screen-template-properties"></a>Para editar las propiedades de la plantilla de filtro de archivos

1.  En **Plantillas de filtro de archivos**, selecciona la plantilla que quieres modificar.

2.  Haga clic con el botón derecho en la plantilla de filtro de archivos y haga clic en **Editar propiedades** de la plantilla (o en el panel **acciones** , en **plantillas de filtro de archivos seleccionadas**, seleccione **Editar propiedades de plantilla**). Se abrirá el cuadro de diálogo Propiedades de la **plantilla de filtro de archivos** .

3.  Si quieres copiar las propiedades de otra plantilla para usarla como base de la plantilla modificada, selecciona una plantilla en la lista desplegable **Copiar propiedades de la plantilla**. Luego haz clic en **Copiar**.

4.  Realiza todos los cambios necesarios. Las opciones de notificación y configuración son idénticas a las que están disponibles cuando creas una plantilla de filtro de archivos.

5.  Cuando hayas terminados de editar las propiedades de la plantilla, haz clic en **Aceptar**. Se abrirá el cuadro de diálogo **Actualizar los filtros de archivos derivados de la plantilla**.

6.  Selecciona el tipo de actualización que quieres aplicar:

    -   Si tienes filtros de archivos que se han modificado desde que se crearon con la plantilla original y no quieres cambiarlos, haz clic en **Aplicar la plantilla solo a los filtros de archivos derivados que coinciden con la plantilla original**. Esta opción actualizará solo los filtros de archivos que no se han editado desde que se crearon con las propiedades de plantilla originales.
    -   Si quieres modificar todos los filtros de archivos existentes que se crearon con la plantilla original, haz clic en **Aplicar la plantilla a todos los filtros de archivos derivados**.
    -   Si quieres mantener los filtros de archivos existentes sin modificar, haz clic en **No aplicar la plantilla a los filtros de archivos derivados**.

7.  Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

-   [Administración del filtrado de archivos](file-screening-management.md)
-   [Crear una plantilla de filtro de archivos](create-file-screen-template.md)


