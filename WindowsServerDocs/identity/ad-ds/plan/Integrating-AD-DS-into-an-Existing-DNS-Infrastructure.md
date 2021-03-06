---
ms.assetid: 4981b32f-741e-4afc-8734-26a8533ac530
title: Integrar AD DS en una infraestructura de DNS existente
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: f4bb480be4696f15f0a63c20ab47042264584d2c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402552"
---
# <a name="integrating-ad-ds-into-an-existing-dns-infrastructure"></a>Integrar AD DS en una infraestructura de DNS existente

>Se aplica a: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Si su organización ya tiene un servicio de servidor de sistema de nombres de dominio (DNS), el propietario de DNS para Active Directory Domain Services (AD DS) debe trabajar con el propietario de DNS de su organización para integrar AD DS en la infraestructura existente. Esto implica la creación de un servidor DNS y una configuración de cliente DNS.  
  
## <a name="creating-a-dns-server-configuration"></a>Creación de una configuración de servidor DNS  
Al integrar AD DS con un espacio de nombres DNS existente, se recomienda hacer lo siguiente:  
  
-   Instale el servicio servidor DNS en todos los controladores de dominio del bosque. Esto proporciona tolerancia a errores si uno de los servidores DNS no está disponible. De esta manera, no es necesario que los controladores de dominio dependan de otros servidores DNS para la resolución de nombres. Esto también simplifica el entorno de administración porque todos los controladores de dominio tienen una configuración uniforme.  
  
-   Configure el controlador de dominio raíz del bosque de Active Directory para que hospede la zona DNS del bosque de Active Directory.  
  
-   Configure los controladores de dominio de cada dominio regional para hospedar las zonas DNS que corresponden a sus dominios de Active Directory.  
  
-   Configure la zona que contiene los registros de localizador de todo el bosque Active Directory (es decir, el dominio _ msdcs. *zona forestname* ) para replicar en todos los servidores DNS del bosque mediante la partición del directorio de aplicaciones DNS de todo el bosque.  
  
    > [!NOTE]  
    > Cuando el servicio servidor DNS se instala con el Asistente para instalación de Active Directory Domain Services (se recomienda esta opción), todas las tareas anteriores se realizan automáticamente. Para obtener más información, vea [implementar un dominio raíz del bosque de Windows Server 2008](https://technet.microsoft.com/library/cc731174.aspx).  
  
    > [!NOTE]  
    > AD DS usa registros de localizador para todo el bosque para permitir que los asociados de replicación se encuentren entre sí y para que los clientes puedan encontrar servidores de catálogo global. AD DS almacena los registros de localizador de todo el bosque en el _ msdcs. zona *forestname* . Dado que la información de la zona debe estar ampliamente disponible, esta zona se replica en todos los servidores DNS del bosque por medio de la partición de directorio de aplicaciones DNS de todo el bosque.  
  
La estructura DNS existente permanece intacta. No es necesario que mueva ningún servidor o zona. Solo tiene que crear una delegación a las zonas DNS integradas en Active Directory desde la jerarquía de DNS existente.  
  
## <a name="creating-the-dns-client-configuration"></a>Creación de la configuración del cliente DNS  
Para configurar DNS en los equipos cliente, el DNS de AD DS propietario debe especificar el esquema de nomenclatura del equipo y cómo los clientes ubicarán los servidores DNS. En la tabla siguiente se enumeran las configuraciones recomendadas para estos elementos de diseño.  
  
|Elemento Design|Configuración|  
|------------------|-----------------|  
|Nombres de equipos|Usar nombres predeterminados. Cuando un equipo basado en Windows 2000, Windows XP, Windows Server 2003, Windows Server 2008 o Windows Vista se une a un dominio, el equipo se asigna a sí mismo un nombre de dominio completo (FQDN) que incluye el nombre de host del equipo y el nombre del Dominio del directorio.|  
|Configuración de la resolución de cliente|Configure los equipos cliente para que apunten a cualquier servidor DNS de la red.|  
  
> [!NOTE]  
> Active Directory clientes y controladores de dominio pueden registrar dinámicamente sus nombres DNS aunque no señalen al servidor DNS que sea autoritativo para sus nombres.  
  
Es posible que un equipo tenga un nombre DNS diferente si la organización registró de forma estática el equipo en DNS o si la organización implementó previamente una solución integrada de protocolo de configuración dinámica de host (DHCP). Si los equipos cliente ya tienen un nombre DNS registrado, cuando el dominio al que se unen se actualiza a Windows Server 2008 AD DS, tendrán dos nombres diferentes:  
  
-   Nombre DNS existente  
  
-   El nuevo nombre de dominio completo (FQDN)  
  
Los clientes pueden seguir encontrando cualquier nombre. Cualquier solución DNS, DHCP o DNS integrada o DHCP existente se deja intacta. Los nuevos nombres primarios se crean automáticamente y se actualizan mediante la actualización dinámica. Se limpian automáticamente por medio de la eliminación de registros obsoletos.  
  
Si desea aprovechar la autenticación Kerberos al conectarse a un servidor que ejecuta Windows 2000, Windows Server 2003 o Windows Server 2008, debe asegurarse de que el cliente se conecte al servidor mediante el nombre principal.  
  


