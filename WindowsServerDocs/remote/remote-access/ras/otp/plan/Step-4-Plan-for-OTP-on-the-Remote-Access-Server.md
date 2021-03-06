---
title: Paso 4 Plan para OTP en el servidor de acceso remoto
description: Este tema forma parte de la guía deploy Remote Access with OTP Authentication in Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b97b2fd-767a-45c1-a64e-5b3edd0c8a47
ms.author: pashort
author: shortpatti
ms.openlocfilehash: cc833ea2ae5d24754a445d6c1252f21a59cc6f13
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404391"
---
# <a name="step-4-plan-for-otp-on-the-remote-access-server"></a>Paso 4 Plan para OTP en el servidor de acceso remoto

>Se aplica a: Windows Server (canal semianual), Windows Server 2016

Después de planear la configuración del servidor RADIUS y el certificado de contraseña de un solo tiempo (OTP), el último paso en la planeación de una implementación de OTP de acceso remoto consiste en planear la configuración de OTP de cliente en el servidor de acceso remoto.  
  
|Tarea|Descripción|  
|----|--------|  
|[4,1 planeamiento de exenciones de cliente de OTP](#bkmk_4_1_Exemptions)|Planee las exenciones para los usuarios que no necesite para la autenticación mediante OTP.|  
|[4,2 plan para clientes de Windows 7](#bkmk_4_2_Win7)|Planear la implementación del asistente de conectividad de DirectAccess (DCA) 2,0 en los equipos cliente de Windows 7.|  
|[4,3 plan para tarjetas inteligentes](#BKMK_smartcard)|Planee el uso de tarjetas inteligentes para la autorización adicional.|  
  
## <a name="bkmk_4_1_Exemptions"></a>4,1 planeamiento de exenciones de cliente de OTP  
Cuando la autenticación de OTP está habilitada, de forma predeterminada, todos los usuarios deben autenticarse con una combinación de nombre de usuario y contraseña, y las credenciales de OTP. Sin embargo, puede permitir que los usuarios seleccionados se autentiquen solo con un nombre de usuario y contraseña, sin OTP. Para ello, cree un grupo de seguridad y agregue los usuarios que desee excluir de la autenticación de OTP.  
  
> [!NOTE]  
> Solo se pueden excluir los equipos cliente de un solo bosque debido al hecho de que solo se puede seleccionar un grupo de seguridad para las exenciones de cliente.  
  
## <a name="bkmk_4_2_Win7"></a>4,2 plan para clientes de Windows 7  
De forma predeterminada, los equipos cliente de Windows 7 no se pueden autenticar mediante OTP.  Los equipos cliente de Windows 7 requieren DCA 2,0 para autenticarse con OTP en una implementación de acceso remoto de Windows Server 2012. Para obtener más información sobre DCA 2,0, consulte [Asistente de conectividad de DirectAccess 2,0](https://go.microsoft.com/fwlink/?LinkId=253699) en el centro de descarga de Microsoft.  
  
## <a name="BKMK_smartcard"></a>4,3 plan para tarjetas inteligentes  
Cuando está habilitada la autenticación de OTP, está disponible la opción para habilitar el uso de tarjetas inteligentes para la autorización adicional. Cree un grupo de seguridad para permitir el acceso temporal en caso de que la tarjeta inteligente de un usuario no funcione.  
  
## <a name="BKMK_Links"></a>Vea también  
  
-   [Configuración de DirectAccess con autenticación OTP](https://technet.microsoft.com/windows-server-docs/networking/remote-access/ras/otp/deploy-ra-otp)  
  


