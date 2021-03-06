---
ms.assetid: 7d230527-f4fe-4572-8838-0b354ee0b06b
title: Agregar una descripción de notificación
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: ff50ac8d41a5bbde282b1d5b93c85610f841b5ab
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407782"
---
# <a name="add-a-claim-description"></a>Agregar una descripción de notificación


En una organización de asociado de cuenta, los administradores crean notificaciones para representar la pertenencia de un usuario a un grupo o rol, o para representar algunos datos sobre un usuario, por ejemplo, el número de identificación de empleado de un usuario.

En una organización del asociado de recurso, los administradores crean las notificaciones correspondientes para representar grupos y usuarios que se pueden reconocer como usuarios de recursos. Dado que las notificaciones salientes de la organización del asociado de cuenta se asignan a las notificaciones entrantes en la organización del asociado de recurso, el asociado de recurso puede aceptar las credenciales proporcionadas por el asociado de cuenta. 

Puede usar el siguiente procedimiento para agregar una demanda.

El requisito mínimo para realizar este procedimiento es pertenecer al grupo **Administradores** o un grupo equivalente en el equipo local.  Revise los detalles sobre el uso de las cuentas y pertenencias a grupos adecuadas en [grupos predeterminados locales y de dominio](https://go.microsoft.com/fwlink/?LinkId=83477).

## <a name="to-add-a-claim-description"></a>Para agregar una descripción de la demanda

1. En Administrador del servidor, haga clic en **herramientas**y, a continuación, seleccione **Administración de AD FS**. 

2. Expanda **servicio** y, a la derecha, haga clic en **Agregar Descripción de notificaciones**.
   ![Agregar Descripción de notificaciones](media/Add-a-Claim-Description/claimdesc1.png)

3. En el cuadro de diálogo Agregar una descripción de notificaciones, en **nombre para mostrar**, escriba un nombre único que identifique el grupo o el rol para esta demanda.

4. Agregue un **nombre corto**.

5. En **identificador de notificaciones**, escriba un URI asociado al grupo o rol de la demanda que va a usar.

6. En **Descripción**, escriba el texto que mejor describa el propósito de esta demanda.

7. En función de las necesidades de su organización, seleccione una de las siguientes casillas, según corresponda, para publicar esta demanda en metadatos de Federación:


~~~
- To publish this claim to make partners aware that this server can accept this claim, click **Publish this claim in federation metadata as a claim type that this Federation Service can accept**.
- To publish this claim to make partners aware that this server can issue this claim, click **Publish this claim in federation metadata as a claim type that this Federation Service can send**.
~~~

8. Haga clic en **Aceptar**.

![Agregar Descripción de notificaciones](media/Add-a-Claim-Description/claimdesc2.png)


## <a name="see-also"></a>Vea también  
[Operaciones de AD FS](../../ad-fs/AD-FS-2016-Operations.md) 
