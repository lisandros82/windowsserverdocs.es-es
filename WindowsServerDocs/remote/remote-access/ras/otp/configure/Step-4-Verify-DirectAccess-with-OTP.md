---
title: Paso 4 comprobar DirectAccess con OTP
description: Este tema forma parte de la guía deploy Remote Access with OTP Authentication in Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed49a0a3-1c45-42e5-8f13-cad20c1c1d68
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 83ea3c4e4feefacde3e1ed7be6b605d8c0e644a3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71366973"
---
# <a name="step-4-verify-directaccess-with-otp"></a>Paso 4 comprobar DirectAccess con OTP

>Se aplica a: Windows Server (canal semianual), Windows Server 2016

En este tema se describe cómo comprobar que ha configurado correctamente DirectAccess con la implementación de OTP.
  
### <a name="to-verify-otp-health-on-the-remote-access-server"></a>Para comprobar el estado de OTP en el servidor de acceso remoto

1. En el servidor de acceso remoto, abra la consola de **Administración de acceso remoto** .  

2. En **servidores de acceso remoto** , haga clic en el servidor de acceso remoto que se ha configurado para la compatibilidad con OTP.  

3. Haga clic en **Estado de las operaciones**.  

4. Compruebe que el estado de OTP muestra el icono verde y que funciona.  
  
    > [!NOTE]  
    > El intervalo de actualización del estado de mantenimiento será un máximo de la suma de los valores de la clave del registro HKLM\SYSTEM\CCS\Services\Ramgmtsvc\parameters\HealthRefreshTimeout y el **intervalo de tiempo para la actividad del servidor** que se estableció en el acceso remoto. configuraciones.  
  
### <a name="to-verify-access-to-internal-resources-using-otp-authentication"></a>Para comprobar el acceso a los recursos internos mediante la autenticación de OTP  
  
1.  Conecte un equipo cliente de DirectAccess a la red corporativa y ejecute **gpupdate/force** desde el símbolo del sistema para obtener la Directiva de grupo.  
  
2.  Desconecte el equipo cliente de la red corporativa, conéctese a la red externa e intente tener acceso a los recursos internos. No debe tener acceso a los recursos internos.  
  
3.  En el caso de un token de software, acceda al token de cliente de OTP con las instrucciones del proveedor y anote el código de token actual. Cuando se use un token de hardware, siga las instrucciones del proveedor para la autenticación.  
  
4.  Haga clic en el icono **Conexiones de red** del área de notificación para tener acceso al Administrador de medios de DA.  
  
5.  Haga clic en la **conexión de DirectAccess**y haga clic en **continuar**.  
  
6.  Escriba el código de token indicado anteriormente y haga clic en **Aceptar**. Espere a que se complete la autenticación. El estado de la conexión del área de trabajo de DirectAccess ahora estará **conectado**.  
  
7.  Intento de obtener acceso a los recursos internos. Debe poder tener acceso a todos los recursos corporativos.  
  


