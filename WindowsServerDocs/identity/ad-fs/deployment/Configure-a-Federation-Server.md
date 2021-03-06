---
ms.assetid: 434fd617-373a-405e-bae4-da324ea83efc
title: Guía de implementación de AD FS en Windows Server 2012 R2
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: c549b52f697db889bf638470aca03f02e1323ed5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359732"
---
# <a name="configure-a-federation-server"></a>Configurar un servidor de federación

Después de instalar el servicio \(de\) rol de servicios de Federación de Active Directory (AD FS) AD FS en el equipo, está listo para configurar este equipo para que se convierta en un servidor de Federación. Puede realizar una de las acciones siguientes:  
  
-   [Configurar el primer servidor de Federación en una nueva granja de servidores de Federación](assetId:///e340cf8f-acf3-4cba-8135-a9353b85e714#BKMK_1)  
  
-   [Agregar un servidor de Federación a una granja de servidores de Federación existente](assetId:///e340cf8f-acf3-4cba-8135-a9353b85e714#BKMK_2)  
  
## <a name="BKMK_1"></a>Configurar el primer servidor de Federación en una nueva granja de servidores de Federación  
  
### <a name="to-configure-the-first-federation-server-in-a-new-federation-server-farm-by-using-the-active-directory-federation-service-configuration-wizard"></a>Para configurar el primer servidor de Federación en una nueva granja de servidores de Federación mediante el Asistente para configuración de Active Directory Servicio de federación  
  
> [!NOTE]  
> Asegúrese de que tiene permisos de administrador de dominio o tiene credenciales de administrador de dominio disponibles antes de realizar este procedimiento.  
  
1.  En la página **Panel** del Administrador del servidor, haz clic en la marca **Notificaciones** y, a continuación, en **Configurar el servicio de federación en el servidor**.  
  
    Se abre el **Asistente para configuración de Servicios de federación de Active Directory** .  
  
2.  En la **Página principal** , selecciona **Crear el primer servidor de federación en una granja de servidores de federación**y haz clic en **Siguiente**.  
  
3.  En la página **conectar con AD DS** , especifique una cuenta con permisos de administrador de dominio para el \(dominio\) de Active Directory ad al que está unido este equipo y, a continuación, haga clic en **siguiente**.  
  
4.  En la página **Especificar propiedades del servicio**, haz lo que se explica a continuación y, después, haz clic en **Siguiente**:  
  
    -   Importe el archivo. pfx que contiene el certificado SSL \(\) de capa de sockets seguros y la clave que ha obtenido anteriormente. En [el paso 2: Inscribir un certificado SSL para AD FS](../../ad-fs/deployment/Enroll-an-SSL-Certificate-for-AD-FS.md), ha obtenido este certificado y lo ha copiado en el equipo que desea configurar como servidor de Federación. Para importar el archivo. pfx a través del asistente, haga clic en **importar**y, a continuación, vaya a la ubicación del archivo. Escriba la contraseña del archivo. pfx cuando se le solicite.  
  
    -   Proporcione un nombre para el servicio de Federación. Por ejemplo, **FS.contoso.com**. Este nombre debe coincidir con uno de los nombres alternativos del sujeto o del firmante en el certificado.  
  
    -   Proporcione un nombre para mostrar para el servicio de Federación. Por ejemplo, **contoso Corporation**. Los usuarios verán este nombre en \(la\) página\-de inicio de sesión de servicios de Federación de Active Directory (AD FS) AD FS.  
  
5.  En la página **especificar cuenta de servicio** , especifique una cuenta de servicio. Puede crear o usar una cuenta \(de servicio administrada de grupo existente gMSA\) o usar una cuenta de usuario de dominio existente. Si selecciona la opción para crear una nueva cuenta de gMSA, especifique un nombre para la nueva cuenta. Si selecciona la opción para usar una cuenta de dominio o gMSA existente, haga clic en **seleccionar** para seleccionar una cuenta.  
  
    > [!NOTE]  
    > La ventaja de usar una cuenta de gMSA es su\-característica de actualización de contraseñas negociada automáticamente.  
  
    > [!WARNING]  
    > Si desea usar una cuenta de gMSA, debe tener al menos un controlador de dominio en el entorno que ejecute el sistema operativo Windows Server 2012.  
    >   
    > Si la opción gMSA está deshabilitada y aparece un mensaje de error, como **las cuentas de servicio administradas de grupo no están disponibles porque no se ha establecido la clave raíz de KDS**, puede habilitar gMSA en el dominio mediante la ejecución del siguiente comando de Windows PowerShell en un dominio. controlador, que ejecuta Windows Server 2012 o posterior, en el dominio de Active Directory `Add-KdsRootKey –EffectiveTime (Get-Date).AddHours(-10)`:. A continuación, vuelva al asistente, haga clic en **anterior**y, a continuación\-, haga clic en **siguiente** para volver a escribir la página **especificar cuenta de servicio** . Ahora debe estar habilitada la opción gMSA. Puede seleccionarlo y escribir un nombre de cuenta de gMSA que quiera usar.  
  
6.  En la página **especificar base de datos de configuración** , especifique una base de datos de configuración de AD FS y, a continuación, haga clic en **siguiente**. Puede crear una base de datos en este equipo mediante el uso de Windows \(Internal\)Database WID, o puede especificar la ubicación y el nombre de instancia de Microsoft SQL Server.  
  
    Para obtener más información, consulta [Rol de la base de datos de configuración de AD FS](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md).  
  
    > [!IMPORTANT]  
    > Si desea crear una granja de AD FS y usar SQL Server para almacenar los datos de configuración, puede usar SQL Server 2008 y versiones más recientes, incluidas SQL Server 2012 y SQL Server 2014.  
  
7.  En la página **Revisar opciones**, comprueba la configuración que has seleccionado y haz clic en **Siguiente**.  
  
8.  En la **\-página comprobaciones de requisitos** previos, compruebe que todas las comprobaciones de requisitos previos se han completado correctamente y, a continuación, haga clic en **configurar**.  
  
9. En la página **resultados** , revise los resultados y compruebe si la configuración se completó correctamente y, a continuación, haga clic en **pasos siguientes necesarios para completar la implementación del servicio de Federación**. Para obtener más información, consulte [pasos siguientes para completar la instalación de AD FS](https://go.microsoft.com/fwlink/p/?LinkId=286704). Haga clic en **Cerrar** para salir del asistente.  
  
### <a name="BKMK_3"></a>Para configurar el primer servidor de Federación en una nueva granja de servidores de Federación a través de Windows PowerShell  
Puede crear una nueva granja de servidores de Federación mediante una cuenta gMSA nueva o existente o una cuenta de usuario de dominio existente.  
  
-   **Si desea crear un nuevo servidor de Federación con una nueva cuenta de gMSA, haga lo siguiente:**  
  
    > [!IMPORTANT]  
    > Debes tener permisos de administrador de dominio para crear el primer servidor de Federación en una nueva granja de servidores de Federación.  
  
    1.  En el equipo que deseas configurar como servidor de Federación, asegúrate de que el certificado SSL necesario se ha importado en el directorio **My\\Store del equipo local** . Para comprobar si el certificado SSL se ha importado, ejecute el siguiente comando en la ventana de comandos de Windows `dir Cert:\LocalMachine\My`PowerShell:. El certificado se muestra por su huella digital en el directorio **My\\Store del equipo local** .  
  
    2.  En el controlador de dominio, abra la ventana de comandos de Windows PowerShell y ejecute el siguiente comando para comprobar si se ha creado la clave raíz KDS en `Get-KdsRootKey –EffectiveTime (Get-Date).AddHours(-10)`su dominio:. Si no se ha creado para que la salida no muestre ninguna información, ejecute el siguiente comando para crear la clave: `Add-KdsRootKey –EffectiveTime (Get-Date).AddHours(-10)`.  
  
    3.  En el equipo que deseas configurar como servidor de Federación, abre la ventana de comandos de Windows PowerShell y ejecuta el siguiente comando:  
  
        ```  
        Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -GroupServiceAccountIdentifier <domain>\<GMSA_Name>$  
        ```  
  
        > [!WARNING]  
        > El `$` signo que se encuentra al final del comando anterior es obligatorio.  
  
        Para obtener el valor de `<certificate_thumbprint>`, ejecute `dir Cert:\LocalMachine\My`y, a continuación, seleccione la huella digital del certificado SSL. El valor de `<federation_service_name>` es el nombre del servicio de Federación, por ejemplo, **FS.contoso.com**.  
  
        > [!NOTE]  
        > Si no es la primera vez que ejecuta este comando, agregue el `OverwriteConfiguration` parámetro.  
  
        > [!NOTE]  
        > El comando anterior crea una granja WID. Si desea crear una granja de servidores de SQL Server, debe tener una instancia de SQL Server ya instalada y operativa.  
        >   
        > Puede usar el siguiente comando para crear el primer servidor de Federación en una nueva granja que use una instancia de SQL Server: `Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -GroupServiceAccountIdentifier <domain>\<GMSA_name>$ -SQLConnectionString "Data Source=<SQL_Host_Name?\<SQL_instance_ name>;Integrated Security=True"` donde **< nombre\_de\_host SQL >** es el nombre del servidor en el que se está ejecutando SQL Server y **< nombre\_de\_instancia de SQL >** es el nombre de la instancia de SQL Server. Si usa la instancia predeterminada de SQL Server, use un valor **SQLConnectionString** de "**origen\=de datos < nombre de\_host de\_SQL >;\=seguridad integrada true**".  
  
        > [!IMPORTANT]  
        > Si desea crear una granja de AD FS y usar SQL Server para almacenar los datos de configuración, puede usar SQL Server 2008 y versiones posteriores, incluido SQL Server 2012.  
  
-   **Si desea crear un nuevo servidor de Federación mediante una cuenta de usuario de dominio existente, haga lo siguiente:**  
  
    1.  En el equipo que deseas configurar como servidor de Federación, asegúrate de que el certificado SSL necesario se ha importado en el directorio **My\\Store del equipo local** . Para comprobar si el certificado SSL se ha importado, ejecute el siguiente comando en la ventana de comandos de Windows `dir Cert:\LocalMachine\My`PowerShell:. El certificado se muestra por su huella digital en el directorio **My\\Store del equipo local** .  
  
    2.  En el equipo que deseas configurar como servidor de Federación, abre la ventana de comandos de Windows PowerShell y, después, ejecuta el siguiente `$fscred = Get-Credential`comando:. Escriba las credenciales de la cuenta de usuario de dominio que desea usar para la cuenta de servicio de\\Federación con el formato nombre de usuario de dominio.  
  
    3.  En la misma ventana de Windows PowerShell, ejecute el siguiente comando:  
  
        ```  
        Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -ServiceAccountCredential $fscred  
        ```  
  
        Para obtener el valor de **< huella\_digital del certificado >** , ejecute `dir Cert:\LocalMachine\My`y, a continuación, seleccione la huella digital del certificado SSL. El valor de **< nombre\_de\_servicio de Federación >** es el nombre del servicio de Federación, por ejemplo, FS.contoso.com.  
  
        > [!NOTE]  
        > Si no es la primera vez que ejecuta este comando, agregue el `OverwriteConfiguration` parámetro.  
  
        > [!NOTE]  
        > El comando anterior crea una granja WID. Si desea crear una granja de SQL Server, debe tener la instancia de SQL Server ya instalada y operativa.  
        >   
        > Puede usar el siguiente comando para crear el primer servidor de Federación en una nueva granja de servidores que use una instancia de `Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -ServiceAccountCredential $fscredential -SQLConnectionString "Data Source=<SQL_Host_Name>\<SQL_instance_ name>;Integrated Security=True"` SQL Server: donde **el nombre de\_host\_de SQL** es el nombre del servidor en el que se ejecuta SQL Server y **SQL nombrede\_instancia es el nombre de la instancia de SQL Server. \_** Si usa la instancia predeterminada de SQL Server, use un valor **SQLConnectionString** de "**origen\=de datos < nombre de\_host de\_SQL >;\=seguridad integrada true**".  
  
        > [!IMPORTANT]  
        > Si desea crear una granja de AD FS y usar SQL Server para almacenar los datos de configuración, puede usar SQL Server 2008 y versiones más recientes, incluidas SQL Server 2012 y SQL Server 2014.  
  
## <a name="BKMK_2"></a>Agregar un servidor de Federación a una granja de servidores de Federación existente  
  
> [!IMPORTANT]  
> Asegúrese de que ha completado [el paso 3: Instale el servicio](../../ad-fs/deployment/Install-the-AD-FS-Role-Service.md)de rol AD FS antes de iniciar cualquiera de los procedimientos de esta sección.  
  
> [!IMPORTANT]  
> Antes de completar este procedimiento, asegúrese de que ha obtenido un certificado de autenticación de servidor SSL válido.  
  
### <a name="to-add-a-federation-server-to-an-existing-federation-server-farm-via-the-active-directory-federation-service-configuration-wizard"></a>Para agregar un servidor de Federación a una granja de servidores de Federación existente mediante el Asistente para configuración de Active Directory Servicio de federación  
  
1.  En la página **Panel** del Administrador del servidor, haz clic en la marca **Notificaciones** y, a continuación, en **Configurar el servicio de federación en el servidor**.  
  
    Se abre el **Asistente para configuración de Servicios de federación de Active Directory** .  
  
2.  En la página de **bienvenida** , seleccione **Agregar un servidor de Federación a una granja de servidores de Federación**y, a continuación, haga clic en **siguiente**.  
  
3.  En la página **conectar con AD DS** , especifique una cuenta con permisos de administrador de dominio para el dominio de ad al que está unido este equipo y, a continuación, haga clic en **siguiente**.  
  
4.  En la página **especificar granja** , proporcione el nombre del servidor de Federación principal en una granja que use WID o especifique el nombre de host de base de datos y el nombre de la instancia de base de datos de una granja de servidores de Federación existente que use SQL Server.  
  
    > [!WARNING]  
    > En Windows Server® 2012 R2, existe una solución alternativa para especificar la instancia predeterminada de SQL Server. La solución alternativa es no usar la interfaz de usuario. En su lugar, siga los pasos de [para configurar el primer servidor de Federación en una nueva granja de servidores de Federación a través de Windows PowerShell](Configure-a-Federation-Server.md#BKMK_3).  
  
    > [!IMPORTANT]  
    > Si desea crear una granja de AD FS y usar SQL Server para almacenar los datos de configuración, puede usar SQL Server 2008 y versiones posteriores, incluido SQL Server 2012.  
  
5.  En la página **especificar certificado SSL** , importe el archivo. pfx que contiene el certificado SSL y la clave que ha obtenido anteriormente. Este certificado es el certificado de autenticación de servicio necesario. En [el paso 2: Inscribir un certificado SSL para AD FS](../../ad-fs/deployment/Enroll-an-SSL-Certificate-for-AD-FS.md), ha obtenido este certificado y lo ha copiado en el equipo que desea configurar como servidor de Federación. Para importar el archivo. pfx a través del asistente, haga clic en **importar** y busque la ubicación del archivo. Escriba la contraseña del archivo. pfx cuando se le solicite.  
  
6.  En la página **especificar cuenta de servicio** , especifique la misma cuenta de servicio que configuró al crear el primer servidor de Federación en la granja. Puede usar una cuenta de servicio administrada de grupo existente o una cuenta de usuario de dominio existente.  
  
    > [!IMPORTANT]  
    > La cuenta que especifique debe ser la misma cuenta que la cuenta que se usó en el servidor de Federación principal de esta granja.  
  
7.  En la página **Revisar opciones**, comprueba la configuración que has seleccionado y haz clic en **Siguiente**.  
  
8.  En la **\-página comprobaciones de requisitos** previos, compruebe que todas las comprobaciones de requisitos previos se han completado correctamente y, a continuación, haga clic en **configurar**.  
  
9. En la página **resultados** , revise los resultados y compruebe si la configuración se completó correctamente y, a continuación, haga clic en **pasos siguientes necesarios para completar la implementación del servicio de Federación**. Para obtener más información, consulte [pasos siguientes para completar la instalación de AD FS](https://go.microsoft.com/fwlink/p/?LinkId=286704). Haga clic en **Cerrar** para salir del asistente.  
  
### <a name="to-add-a-federation-server-to-an-existing-federation-server-farm-via-windows-powershell"></a>Para agregar un servidor de Federación a una granja de servidores de Federación existente mediante Windows PowerShell  
Puede Agregar un servidor de Federación a una granja existente mediante una cuenta de gMSA existente o una cuenta de usuario de dominio existente.  
  
-   Si desea unir un servidor de Federación a una granja mediante una cuenta de gMSA existente, haga lo siguiente:  
  
    1.  En el equipo que deseas configurar como servidor de Federación, asegúrate de que el certificado SSL necesario se ha importado en el directorio **My\\Store del equipo local** . Para comprobar si el certificado SSL se ha importado, ejecute el siguiente comando en la ventana de comandos de Windows `dir Cert:\LocalMachine\My`PowerShell:. El certificado se muestra por su huella digital en el directorio **My\\Store del equipo local** .  
  
    2.  En el equipo que deseas configurar como servidor de Federación, abre la ventana de comandos de Windows PowerShell y ejecuta el siguiente comando.  
  
        ```  
        Add-AdfsFarmNode -GroupServiceAccountIdentifier <domain>\<GMSA_name>$ -PrimaryComputerName <first_federation_server_hostname> -CertificateThumbprint <certificate_thumbprint>  
        ```  
  
        `<domain>\<GMSA_name>`es el dominio de AD y el nombre de la cuenta de gMSA en ese dominio. `<first_federation_server_hostname>`es el nombre de host del servidor de Federación principal de esta granja de servidores existente.  
  
        Puede obtener el valor de `<certificate_thumbprint>` ejecutando `dir Cert:\LocalMachine\My` en el paso anterior.  
  
        > [!NOTE]  
        > Si no es la primera vez que ejecuta este comando, agregue el `OverwriteConfiguration` parámetro.  
  
        > [!NOTE]  
        > El comando anterior crea un nodo de la granja WID. Si desea crear un nodo de granja de servidores de equipos que ejecutan SQL Server, debe tener la instancia de SQL Server ya instalada y operativa.  
        >   
        > Puede usar el siguiente comando para agregar un servidor de Federación a una granja existente que use una instancia de SQL Server: `Add-AdfsFarmNode -GroupServiceAccountIdentifier <domain>\<GMSA_name>$ -SQLConnectionString "Data Source=<SQL_Host_Name>\<SQL_instance_ name>;Integrated Security=True"` donde nombre de **host\_SQL\_** es el nombre del servidor en el que se ejecuta SQL Server y **SQL nombrede\_instancia es el nombre de la instancia de SQL Server. \_** Si usa la instancia predeterminada de SQL Server, use un valor **SQLConnectionString** de "**origen\=de datos < nombre de\_host de\_SQL >;\=seguridad integrada true**".  
  
        > [!IMPORTANT]  
        > Si desea crear una granja de AD FS y usar SQL Server para almacenar los datos de configuración, puede usar SQL Server 2008 y versiones más recientes, incluidas SQL Server 2012 y SQL Server 2014.  
  
-   Si desea unir un servidor de Federación a una granja de servidores mediante una cuenta de usuario de dominio existente, haga lo siguiente:  
  
    1.  En el equipo que desea configurar como servidor de Federación, abra la ventana de Windows PowerShellcommand y, a continuación, ejecute el siguiente comando `$fscred = get-credential`:. Escriba las credenciales de la cuenta de usuario de dominio que desea usar para la cuenta de servicio de\\Federación con el formato nombre de usuario de dominio.  
  
    2.  En el equipo que deseas configurar como servidor de Federación, asegúrate de que el certificado SSL necesario se ha importado en el directorio **My\\Store del equipo local** . Para comprobar si el certificado SSL se ha importado, ejecute el siguiente comando en la ventana de Windows PowerShellcommand `dir Cert:\LocalMachine\My`:. El certificado se muestra por su huella digital en el directorio **My\\Store del equipo local** .  
  
    3.  En la misma ventana de comandos de Windows PowerShell, ejecute el siguiente comando.  
  
        ```  
        Add-AdfsFarmNode -ServiceAccountCredential $fscred -PrimaryComputerName <first_federation_server_hostname> -CertificateThumbprint <certificate_thumbprint>  
        ```  
  
        > [!NOTE]  
        > Si no es la primera vez que ejecuta este comando, agregue el `OverwriteConfiguration` parámetro.  
  
        > [!NOTE]  
        > El comando anterior crea un nodo de la granja WID. Si desea crear un nodo de granja de servidores de equipos que ejecutan SQL Server, debe tener la instancia de SQL Server ya instalada y operativa. Puede usar el siguiente comando para agregar un servidor de Federación a una granja existente mediante una instancia de SQL Server: donde `Add-AdfsFarmNode -ServiceAccountCredential $fscred -SQLConnectionString "Data Source=<SQL_Host_Name>\<SQL_instance_ name>;Integrated Security=True"` **nombre de\_host\_SQL** es el nombre del servidor en el que se ejecuta la instancia de SQL Server. **Nombre\_deinstancia\_de SQL** es el nombre de la instancia de SQL Server. Si usa la instancia predeterminada de SQL Server, use un valor **SQLConnectionString** de "**origen\=de datos < nombre de\_host de\_SQL >;\=seguridad integrada true**".  
  
        > [!IMPORTANT]  
        > Si desea crear una granja de AD FS y usar SQL Server para almacenar los datos de configuración, puede usar SQL Server 2008 y versiones más recientes, incluidas SQL Server 2012 y SQL Server 2014.  
  
## <a name="see-also"></a>Vea también 

[Implementación de AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Guía de implementación de AD FS de Windows Server 2012 R2](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Implementar una granja de servidores de federación](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  

