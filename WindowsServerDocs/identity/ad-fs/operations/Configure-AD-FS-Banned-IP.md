---
title: Configuración de AD FS IP prohibidas direcciones
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 06/28/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 2b518f92f80d06e4bd0854fde94013a412aae515
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407712"
---
# <a name="ad-fs-and-banned-ip-addresses"></a>AD FS y direcciones IP prohibidas


En junio de 2018, AD FS en Windows Server 2016 presentó **IP prohibidas** con la AD FS actualización del 2018 de junio.  Esta actualización le permite configurar un conjunto de direcciones IP globalmente en AD FS, de modo que las solicitudes procedentes de esas direcciones IP, o que tengan esas direcciones IP en los encabezados **x-forwarded-for** o **x-MS-forwarded-Client-IP** , se bloquearán mediante AD FS.

## <a name="adding-banned-ips"></a>Agregar direcciones IP prohibidas
Para agregar direcciones IP prohibidas a la lista global, use el siguiente cmdlet de PowerShell:

``` powershell
PS C:\ >Set-AdfsProperties -AddBannedIps "1.2.3.4", "::3", "1.2.3.4/16"
```

Formatos permitidos

1.  IPv6
2.  IPv6
3.  Formato CIDR con IPv4 o V6

Hay un límite de 300 entradas para las direcciones IP prohibidas. Puede usar CIDR o el formato de intervalo para denegar un bloque grande de entradas con una sola entrada.

## <a name="removing-banned-ips"></a>Quitar direcciones IP prohibidas
Para quitar direcciones IP prohibidas de la lista global, use el siguiente cmdlet de PowerShell:

``` powershell
PS C:\ >Set-AdfsProperties -RemoveBannedIps "1.2.3.4"
```

#### <a name="read-banned-ips"></a>Leer direcciones IP prohibidas
Para leer el conjunto actual de direcciones IP prohibidas, use el siguiente cmdlet de PowerShell:

``` powershell
PS C:\ >Get-AdfsProperties 
```

Ejemplo de resultado:

```
BannedIpList                   : {1.2.3.4, ::3,1.2.3.4/16}
```



## <a name="additional-references"></a>Referencias adicionales  
[Prácticas recomendadas para proteger Servicios de federación de Active Directory (AD FS)](../../ad-fs/deployment/best-practices-securing-ad-fs.md)

[Set-AdfsProperties](https://technet.microsoft.com/itpro/powershell/windows/adfs/set-adfsproperties)

[Operaciones de AD FS](../../ad-fs/AD-FS-2016-Operations.md)
