---
title: Paso 9 configurar EDGE1
description: 'Este tema forma parte de la guía del laboratorio de pruebas: demostración de una implementación multisitio de DirectAccess para Windows Server 2016'
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6e8d85b-de65-43b3-bf3e-ec84471a1fcc
ms.author: pashort
author: shortpatti
ms.openlocfilehash: ce86a75ac5b8d53874d2fc5c6743979506591680
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71388230"
---
# <a name="step-9-configure-edge1"></a>Paso 9 configurar EDGE1

>Se aplica a: Windows Server (canal semianual), Windows Server 2016

Los procedimientos siguientes se realizan en el servidor de EDGE1:  
  
1. Configure los servidores DNS en EDGE1. Es necesario configurar el servidor DNS del dominio corp2.corp.contoso.com en EDGE1.  
  
2. Configurar el enrutamiento entre subredes. Configure el enrutamiento en EDGE1 para habilitar la comunicación entre las subredes corporativas y 2-CorpNet.  
  
## <a name="IPv6"></a>Configurar los servidores DNS en EDGE1  
  
1.  En la consola de Administrador del servidor, haga clic en **servidor local**y, a continuación, en el área **propiedades** , junto a **CorpNet**, haga clic en el vínculo.  
  
2.  En la ventana conexiones de red, haga clic con el botón secundario en **CorpNet**y, a continuación, haga clic en **propiedades**.  
  
3.  Haga clic en **Protocolo de Internet versión 4 (TCP/IPv4)** y, a continuación, en **Propiedades**.  
  
4.  En **servidor DNS alternativo**, escriba **10.2.0.1**. A continuación, haga clic en **Aceptar**.  
  
5.  Haga clic en **Protocolo de Internet versión 6 (TCP/IPv6)** y, a continuación, haga clic en **Propiedades**.  
  
6.  En **servidor DNS alternativo**, escriba **2001: db8:2:: 1** y, a continuación, haga clic en **Aceptar**.  
  
7.  En el cuadro de diálogo **propiedades de CorpNet** , haga clic en **cerrar**.  
  
8.  Cierre la ventana **Conexiones de red**.  
  
## <a name="ConfigRouting"></a>Configurar el enrutamiento entre subredes  
  
1.  En la pantalla **Inicio** , escriba**cmd. exe**, haga clic con el botón secundario en **cmd**, haga clic en **Opciones avanzadas**y, a continuación, haga clic en **Ejecutar como administrador**. Si aparece el cuadro de diálogo **Control de cuentas de usuario** , confirme que la acción que se muestra es la esperada y, a continuación, haga clic en **Sí**.  
  
2.  En la ventana del símbolo del sistema, escriba los siguientes comandos. Después de escribir cada comando, presione Entrar.  
  
    ```  
    netsh interface IPv4 add route 10.2.0.0/24 Corpnet 10.0.0.254  
    netsh interface IPv6 add route 2001:db8:2::/64 Corpnet 2001:db8:1::fe  
    ```  
  
3.  Cierre la ventana del símbolo del sistema.  
  


