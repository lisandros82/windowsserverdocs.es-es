---
title: Disminuir de nivel y quitar el servidor de origen de la nueva network1 de Windows Server Essentials
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9f18b29-8e03-439e-bdf0-1dac5e4f70c5
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: e5bcdd58f4d88f7a555151d755bf427ecc9b5108
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432999"
---
# <a name="demote-and-remove-the-source-server-from-the-new-windows-server-essentials-network1"></a>Disminuir de nivel y quitar el servidor de origen de la nueva network1 de Windows Server Essentials

>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Después de finalizar la instalación de Windows Server Essentials y completar las tareas en el Asistente para migración, debe realizar las siguientes tareas:  
  

1.  [Desinstalar Exchange Server 2003](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_UninstallExchangeServer2003).  
  
2.  [Desconectar las impresoras que están conectadas directamente al servidor de origen](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_PhysicallyDisconnect).  
  
3.  [Disminuir el nivel del servidor de origen](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_DemoteTheSourceServer).  
  
4.  [Mover el rol servidor DHCP del servidor de origen al enrutador](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_MoveTheDHCPRole).  
  
5.  [Quitar y reasignar el servidor de origen](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_RemoveTheSourceServer).  

1.  [Desinstalar Exchange Server 2003](../migrate/Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_UninstallExchangeServer2003).  
  
2.  [Desconectar las impresoras que están conectadas directamente al servidor de origen](../migrate/Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_PhysicallyDisconnect).  
  
3.  [Disminuir el nivel del servidor de origen](../migrate/Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_DemoteTheSourceServer).  
  
4.  [Mover el rol servidor DHCP del servidor de origen al enrutador](../migrate/Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_MoveTheDHCPRole).  
  
5.  [Quitar y reasignar el servidor de origen](../migrate/Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_RemoveTheSourceServer).  

  
###  <a name="BKMK_UninstallExchangeServer2003"></a> Desinstalar Exchange Server 2003  
  
> [!IMPORTANT]
>  Si agrega las cuentas de usuario después de mover los buzones al servidor de destino y antes de desinstalar Exchange Server 2003 desde el servidor de origen, se agregan los buzones en el servidor de origen. Esto es así por diseño. Debe mover los buzones al servidor de destino para todas las cuentas de usuario que se agreguen durante este tiempo. Repita las instrucciones de configuración y los buzones de mover el servidor de Exchange para la migración de Windows Server Essentials antes de desinstalar Exchange Server 2003.  
  
 Debe desinstalar Exchange Server 2003 desde el servidor de origen antes de degradarlo. Esto quita todas las referencias en Active Directory Domain Services (AD DS) para Exchange Server en el servidor de origen. Debe tener el medio de Windows Small Business Server 2003 para quitar Exchange Server 2003.  
  
##### <a name="to-uninstall-exchange-server-2003-from-the-source-server"></a>Desinstalar Exchange Server 2003 desde el servidor de origen  
  
1. Inicie sesión en el servidor de origen como administrador.  
  
2. Haga clic en **Inicio**, haga clic en **Panel de Control** y, a continuación, haga clic en **Agregar o quitar programas**.  
  
3. En la lista de programas, seleccione **Windows Small Business Server 2003**y, a continuación, haga clic en **cambiar o quitar**.  
  
4. En el asistente para la instalación, haga clic en **Siguiente** hasta que aparezca la página **Selección de componentes**.  
  
5. En la página Selección de componentes, expanda **Exchange Server** y elija **Quitar**.  
  
   > [!NOTE]
   > 
   >  Exchange Server comprobará que no haya ningún buzón ni carpeta pública en el servidor. Si sigue habiendo datos aparecerá un mensaje de error cuando haga clic en **Quitar**. Para evitar este problema, asegúrese de que ha completado todos los procedimientos en el tema [datos al servidor de destino y la configuración de mover SBS 2003](Move-Windows-SBS-2003-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  
   > 
   >  Exchange Server comprobará que no haya ningún buzón ni carpeta pública en el servidor. Si sigue habiendo datos aparecerá un mensaje de error cuando haga clic en **Quitar**. Para evitar este problema, asegúrese de que ha completado todos los procedimientos en el tema [datos al servidor de destino y la configuración de mover SBS 2003](../migrate/Move-Windows-SBS-2003-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  

  
6. Haz clic en **Siguiente**.  
  
7. Cuando se le solicite, inserte Windows Small Business Server 2003 CD #3 y siga las instrucciones en pantalla.  
  
###  <a name="BKMK_PhysicallyDisconnect"></a> Desconectar las impresoras que están conectadas directamente al servidor de origen  
 Antes de disminuir de nivel el servidor de origen, desconecte físicamente las impresoras que están conectadas directamente a este y se comparten a través de él. Asegúrese de que no haya ningún objeto de Active Directory en las impresoras que estaban conectadas directamente al servidor de origen. Las impresoras pueden, a continuación, se directamente conectadas al servidor de destino y se comparten desde Windows Server Essentials.  
  
###  <a name="BKMK_DemoteTheSourceServer"></a> Disminuir de nivel al servidor de origen  
 Antes de disminuir de nivel el servidor de origen (desde el rol del controlador de dominio de AD DS hasta el rol de un servidor miembro de dominio), asegúrese de que la configuración de directiva de grupo se aplica a todos los equipos cliente, tal como se describe en el procedimiento siguiente.  
  
> [!IMPORTANT]
>  Los servidores de origen y destino deben estar conectados a la red mientras se actualizan los cambios de la directiva de grupo en los equipos cliente.  
  
##### <a name="to-force-a-group-policy-update-on-a-client-computer"></a>Para forzar una actualización de directiva de grupo en un equipo cliente  
  
1.  Inicie sesión en el equipo cliente como administrador.  
  
2.  Abra una ventana del símbolo del sistema como administrador.  
  
3.  En el símbolo del sistema, escriba **gpupdate /force** y, después, presione ENTRAR.  
  
4.  El proceso puede requerir que cierre la sesión y vuelva a iniciarla para finalizar. Haga clic en **Sí** para confirmar.  
  
##### <a name="to-demote-the-source-server"></a>Para disminuir de nivel el servidor de origen:  
  
1. En el servidor de origen, haga clic en **Inicio** y **Ejecutar**, escriba **dcpromo** y haga clic en **Aceptar**.  
  
2. Haga clic en **Siguiente** dos veces.  
  
   > [!NOTE]
   >  No seleccione **Este servidor es el último controlador de dominio en el dominio**.  
  
3. Escriba una contraseña para la nueva cuenta de administrador en el servidor y, a continuación, haga clic en **Siguiente**.  
  
4. En el **resumen** cuadro de diálogo, se le informa de que AD DS se quitará del equipo y que el servidor se convertirá en un miembro del dominio. Haz clic en **Siguiente**.  
  
5. Haga clic en **Finalizar**. Se reinicia el servidor de origen.  
  
6. A continuación, agregue el servidor de origen como miembro de un grupo de trabajo antes de desconectarlo de la red.  
  
   Después de agregar el servidor de origen como miembro de un grupo de trabajo y desconectarlo de la red, debe quitarlo de AD DS en el servidor de destino.  
  
##### <a name="to-remove-the-source-server-from-active-directory"></a>Para quitar el servidor de origen de Active Directory  
  
1.  En el servidor de destino, abra **Equipos y usuarios de Active Directory**.  
  
2.  En el panel de navegación **Usuarios y equipos de Active Directory** , expanda el nombre de dominio y **Equipos**.  
  
3.  Si aún aparece en la lista de servidores, haga clic con el botón secundario en el nombre del servidor de origen y, con el botón primario, en **Eliminar** y **Sí**.  
  
4.  Compruebe que el servidor de origen no aparece en la lista y cierre **Usuarios y equipos de Active Directory**.  
  
###  <a name="BKMK_MoveTheDHCPRole"></a> Mover el rol servidor DHCP del servidor de origen al enrutador  
  
> [!NOTE]
> 
>  Si ya ha realizado esta tarea antes de iniciar el proceso de migración, continúe con la sección [Quitar y reasignar el servidor de origen](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_RemoveTheSourceServer).  
> 
>  Si ya ha realizado esta tarea antes de iniciar el proceso de migración, continúe con la sección [Quitar y reasignar el servidor de origen](../migrate/Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_RemoveTheSourceServer).  

  
 Si el servidor de origen ejecuta la función DHCP, efectúe los siguientes pasos para mover la función DHCP al enrutador.  
  
##### <a name="to-move-the-dhcp-role-from-the-source-server-to-the-router"></a>Para mover la función DHCP del servidor de origen al enrutador  
  
1.  Desactive el servicio DHCP en el servidor de origen del siguiente modo:  
  
    1.  En el servidor de origen, haga clic en **Inicio**, haga clic en **Herramientas administrativas**y, después, haga clic en **Servicios**.  
  
    2.  En la lista de servicios que se están ejecutando, haga clic con el botón derecho en **Windows Server** y, después, haga clic en **Propiedades**.  
  
    3.  En **Tipo de inicio**, seleccione **Deshabilitado**.  
  
    4.  Detenga el servicio.  
  
2.  Active la función DHCP en el enrutador.  
  
    1.  Siga las instrucciones de la documentación del enrutador para activar la función DHCP en el enrutador.  
  
    2.  Para asegurarse de que las direcciones IP emitidas por el servidor de origen sean las mismas, siga las instrucciones de la documentación del enrutador para configurar que el intervalo de DHCP del enrutador sea el mismo que el intervalo de DHCP del servidor de origen.  
  
    > [!IMPORTANT]
    >  Si no ha configurado reservas de DHCP o una dirección IP estática en el enrutador para el servidor de destino y el intervalo de DHCP no es el mismo que el servidor de origen, es posible que el enrutador emita una nueva dirección IP para el servidor de destino. Si ocurre, restablezca las reglas de reenvío del puerto del enrutador para hacer un reenvío a la nueva dirección IP del servidor de destino.  
  
###  <a name="BKMK_RemoveTheSourceServer"></a> Quitar y reasignar el servidor de origen  
 Desactive el servidor de origen y desconéctelo de la red. Se recomienda no volver a formatear el servidor de origen durante al menos una semana para asegurar que todos los datos necesarios se migren al servidor de destino. Después de comprobar que ha migrado todos los datos, puede reinstalar este servidor en la red como servidor secundario para otras tareas si es necesario.  
  
> [!NOTE]
>  Después de disminuir de nivel y quitar el servidor de origen, reinicie el servidor de destino.  
  
 Cuando se disminuye de nivel, el servidor de origen no se queda en el estado correcto. Si desea reasignar el servidor de origen, la forma más sencilla es volver a formatearlo, instalar un sistema operativo del servidor y configurarlo como servidor adicional.
