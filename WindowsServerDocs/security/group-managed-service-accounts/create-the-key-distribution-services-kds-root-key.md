---
title: Crear la clave raíz del Servicio de distribución de claves (KDS)
description: Seguridad de Windows Server
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: security-gmsa
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 42e5db8f-1516-4d42-be0a-fa932f5588e9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: fd335d61eae7cf753d09436d54f14c7d6004d643
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386904"
---
# <a name="create-the-key-distribution-services-kds-root-key"></a>Crear la clave raíz del Servicio de distribución de claves (KDS)

>Se aplica a: Windows Server (canal semianual), Windows Server 2016

En este tema para profesionales de TI se describe cómo crear una clave raíz del servicio de distribución de claves (kdssvc. dll) de Microsoft en el controlador de dominio mediante Windows PowerShell para generar contraseñas de cuentas de servicio administradas de grupo en Windows Server 2012 o posterior.

Los controladores de dominio (DC) requieren una clave raíz para comenzar a generar contraseñas de gMSA. Antes de permitir la creación de una gMSA, todos los controladores de dominio esperarán hasta 10 horas desde el momento de la creación para que converjan sus replicaciones de AD. Las 10 horas son una medida de seguridad para evitar que la generación de contraseñas se produzca antes de que todos los controladores de dominio del entorno sean capaces de responder a las peticiones de gMSA.  Si intenta usar una gMSA demasiado pronto, es posible que la clave no se haya replicado en todos los controladores de dominio y, por lo tanto, podría producirse un error en la recuperación de contraseña cuando el host de gMSA intente recuperar la contraseña. Los errores de recuperación de contraseña de gMSA también pueden ocurrir si se usan controladores de dominio con programaciones de replicación limitadas o si hay un problema de replicación.

> [!NOTE]
> Eliminar y volver a crear la clave raíz puede dar lugar a problemas en los que la clave antigua siga utilizándose después de la eliminación debido al almacenamiento en caché de la clave. El servicio de distribución de claves (KDC) debe reiniciarse en todos los controladores de dominio si se vuelve a crear la clave raíz.

Para poder realizar este procedimiento, es necesario, como mínimo, pertenecer a **Admins. del dominio**, **Administradores de empresas** o a otro grupo equivalente. Para ver información detallada sobre el uso de las cuentas adecuadas y las pertenencias a grupos, consulte [Grupos predeterminados locales y de dominio](https://technet.microsoft.com/library/dd728026(WS.10).aspx).

> [!NOTE]
> Se necesita una arquitectura de 64 bits para ejecutar los comandos de Windows PowerShell que se usan para administrar cuentas de servicio administradas de grupo.

#### <a name="to-create-the-kds-root-key-using-the-add-kdsrootkey-cmdlet"></a>Para crear la clave raíz de KDS con el cmdlet Add-KdsRootKey

1.  En el controlador de dominio de Windows Server 2012 o posterior, ejecute Windows PowerShell desde la barra de tareas.

2.  Escribe los siguientes comandos en el símbolo del sistema del módulo de Active Directory de Windows PowerShell y, luego, presiona ENTRAR:

    **Add-KdsRootKey-EffectiveImmediately**

    > [!TIP]
    > El parámetro Effective time se puede usar para dar a las claves tiempo para que se propaguen a todos los controladores de dominio antes de su uso. El uso de Add-KdsRootKey-EffectiveImmediately agregará una clave raíz al controlador de dominio de destino que usará el servicio KDS inmediatamente. Sin embargo, otros controladores de dominio no podrán usar la clave raíz hasta que la replicación sea correcta.

Para los entornos de prueba con solo un controlador de dominio, puedes usar el procedimiento siguiente para crear una clave raíz de KDS y establecer la hora de inicio en el pasado para evitar el intervalo de espera. Comprueba que se haya registrado un evento 4004 en el registro de eventos de KDS.

#### <a name="to-create-the-kds-root-key-in-a-test-environment-for-immediate-effectiveness"></a>Para crear la clave raíz de KDS en un entorno de pruebas para que sea efectivo de forma inmediata

1.  En el controlador de dominio de Windows Server 2012 o posterior, ejecute Windows PowerShell desde la barra de tareas.

2.  Escribe los siguientes comandos en el símbolo del sistema del módulo de Active Directory de Windows PowerShell y, luego, presiona ENTRAR:

    **$a = get-Date**

    **$b = $a. AddHours (-10)**

    **Add-KdsRootKey-EffectiveTime $b**

    O usa un solo comando

    **Add-KdsRootKey-EffectiveTime ((get-Date). AddHours (-10))**

## <a name="see-also"></a>Vea también
[Introducción a las cuentas de servicio administradas de grupo](getting-started-with-group-managed-service-accounts.md)


