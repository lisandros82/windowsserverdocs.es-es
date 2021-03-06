---
title: Cambio de una letra de unidad
description: Cómo cambiar o asignar una letra de unidad en Windows mediante Administración de discos.
ms.date: 10/24/2018
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 3e18092a71e12cadb86052204738fafc8a149ff4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386022"
---
# <a name="change-a-drive-letter"></a>Cambio de una letra de unidad

> **Se aplica a:** Windows 10, Windows 8.1, Windows 7, Windows Server (Canal semianual), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 y Windows Server 2012

Si no te gusta la letra que se ha asignado a una unidad o si tienes alguna unidad que aún no tenga una letra, puedes usar Administración de discos para cambiarla.

> [!IMPORTANT]
> Si cambias la letra de una unidad en la que estén instalados Windows o aplicaciones, es posible que estas últimas tengan problemas a la hora de ejecutarse o de encontrar dicha unidad. Por eso es aconsejable no cambiar la letra de la unidad en la que estén instalados Windows o aplicaciones.

Aquí se muestra cómo cambiar una letra de unidad (para montar la unidad en una carpeta vacía para que aparezca como otra carpeta, consulte [Asignar una ruta de acceso de carpeta de punto de montaje a una unidad](assign-a-mount-point-folder-path-to-a-drive.md)).

1. Abre Administración de discos con permisos de administrador. 
    Para ello, en el cuadro de búsqueda de la barra de tareas, escribe **Administración de discos**, selecciona y mantén pulsado (o haz clic con el botón derecho) **Administración de discos** y, después, selecciona **Ejecutar como administrador**  >  **Sí**. Si no puedes abrirlo como administrador, escribe **en Administración de equipos** en su lugar y, a continuación, vete a **Almacenamiento** > **Administración de discos**.
1. En Administración de discos, haz clic con el botón derecho en la unidad en la que deseas agrega una letra, o cambiarla, y selecciona **Cambiar la letra y rutas de acceso de unidad...** .

    ![Administración de discos muestra una unidad](media/change-drive-letter.png)
    > [!TIP]
    > Si no ves la opción **Cambiar la letra y rutas de acceso de unidad...** o bien está atenuada, es posible el volumen no esté listo para recibir una letra de unidad, algo que puede suceder si la unidad está sin asignar y debe [inicializarse](initialize-new-disks.md). También existe la posibilidad de que no se haya diseñado para que se pueda acceder a ella, lo que sucede en las particiones del sistema EFI y las particiones de recuperación. Si has confirmado que el volumen tiene formato y que puedes acceder a la letra de unidad, pero sigues sin poder cambiarla, es probable que este artículo no te sirva de ayuda, por lo que es aconsejable que te [pongas en contacto con Microsoft](https://support.microsoft.com/contactus/) o con el fabricante del equipo si necesitas más ayuda.

1. Para cambiar la letra de una unidad, selecciona **Cambiar**. Para agregar una letra de unidad, en caso de que la unidad aún no tenga, selecciona **Agregar**.

    ![El cuadro de diálogo Cambiar la letra y rutas de acceso de unidad](media/change-drive-letter2.png)
1. Selecciona la nueva letra de unidad, selecciona **Aceptar**y, finalmente, selecciona **Sí** cuando se te avise que los programas que dependen de la letra de unidad podrían no ejecutarse correctamente.

    ![El cuadro de diálogo Cambiar la letra y rutas de acceso de unidad que muestra el cambio de letra de unidad](media/change-drive-letter3.png)