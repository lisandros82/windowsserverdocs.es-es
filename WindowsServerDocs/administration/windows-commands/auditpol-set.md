---
title: AuditPol set
description: 'Windows Commands topic for **Auditpol Set** : establece la Directiva de auditoría por usuario, la Directiva de auditoría del sistema o las opciones de auditoría.'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4947486-87bd-48cb-ba81-7230c8e70895
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f3c9ec2fab4cad408e0bb845fe157cfdf94f8e09
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382397"
---
# <a name="auditpol-set"></a>AuditPol set

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Establece la Directiva de auditoría por usuario, la Directiva de auditoría del sistema o las opciones de auditoría.

## <a name="syntax"></a>Sintaxis
```
auditpol /set
[/user[:<username>|<{sid}>][/include][/exclude]]
[/category:<name>|<{guid}>[,:<name|<{guid}> ]]
[/success:<enable>|<disable>][/failure:<enable>|<disable>]
[/subcategory:<name>|<{guid}>[,:<name|<{guid}> ]]
[/success:<enable>|<disable>][/failure:<enable>|<disable>]
[/option:<option name> /value: <enable>|<disable>]
```
## <a name="parameters"></a>Parámetros

|  Parámetro   |                                                                                                                                          Descripción                                                                                                                                           |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /User     |                                        La entidad de seguridad para la que se establece la Directiva de auditoría por usuario especificada por la categoría o subcategoría. Se debe especificar la opción categoría o subcategoría, como un identificador de seguridad (SID) o un nombre.                                         |
|   /include   | Se especifica con/User; indica que la Directiva por usuario del usuario hará que se genere una auditoría incluso si no se especifica en la Directiva de auditoría del sistema. Esta configuración es la predeterminada y se aplica automáticamente si no se especifican explícitamente los parámetros/include ni/exclude. |
|   /exclude   |                                Se especifica con/User; indica que la Directiva por usuario del usuario hará que se elimine una auditoría independientemente de la Directiva de auditoría del sistema. Esta configuración se omite para los usuarios que son miembros del grupo local Administradores.                                |
|  /Category   |                                                                            Una o varias categorías de auditoría especificadas por el identificador único global (GUID) o el nombre. Si no se especifica ningún usuario, se establece la Directiva del sistema.                                                                             |
| /subcategory |                                                                                         Una o más subcategorías de auditoría especificadas por el GUID o el nombre. Si no se especifica ningún usuario, se establece la Directiva del sistema.                                                                                          |
|   /Success   |                 Especifica la auditoría de aciertos. Esta opción es la predeterminada y se aplica automáticamente si no se especifican explícitamente los parámetros/Success ni/Failure. Esta configuración debe usarse con un parámetro que indique si se va a habilitar o deshabilitar la configuración.                 |
|   /Failure   |                                                                                  Especifica la auditoría de errores. Esta configuración debe usarse con un parámetro que indique si se va a habilitar o deshabilitar la configuración.                                                                                   |
|   /Option    |                                                                                   Establece la Directiva de auditoría para las opciones CrashOnAuditFail, FullprivilegeAuditing, AuditBaseObjects o AuditBasedirectories.                                                                                    |
|     /SD      |                 Establece el descriptor de seguridad que se usa para delegar el acceso a la Directiva de auditoría. El descriptor de seguridad se debe especificar mediante el lenguaje de definición de descriptores de seguridad (SDDL). El descriptor de seguridad debe tener una lista de control de acceso discrecional (DACL).                 |
|      /?      |                                                                                                                              Muestra la ayuda en el símbolo del sistema.                                                                                                                              |

## <a name="remarks"></a>Comentarios
en el caso de todas las operaciones Set de la Directiva de usuario y la Directiva del sistema, debe tener el permiso de control total o de escritura en ese objeto establecido en el descriptor de seguridad. También puede realizar operaciones Set con el derecho de usuario **Administrar registro de seguridad y auditoría** (SeSecurityPrivilege). Sin embargo, este derecho permite el acceso adicional que no es necesario para realizar la operación SET.
## <a name="BKMK_examples"></a>Example
### <a name="examples-for-the-per-user-audit-policy"></a>Ejemplos de la Directiva de auditoría por usuario
Para establecer la Directiva de auditoría por usuario para todas las subcategorías de la categoría de seguimiento detallado para el usuario Mikedan de modo que se auditen todos los intentos correctos del usuario, escriba:
```
auditpol /set /user:mikedan /category:"detailed Tracking" /include /success:enable
```
Para establecer la Directiva de auditoría por usuario para las categorías especificadas por nombre y GUID, y las subcategorías especificadas por GUID para suprimir la auditoría de cualquier intento correcto o erróneo, escriba:
```
auditpol /set /user:mikedan /exclude /category:"Object Access","System",{6997984b-797a-11d9-bed3-505054503030} 
/subcategory:{0ccee9210-69ae-11d9-bed3-505054503030},:{0ccee9211-69ae-11d9-bed3-505054503030}, /success:enable /failure:enable
```
Para establecer la Directiva de auditoría por usuario para el usuario especificado en todas las categorías para la supresión de la auditoría de todos los intentos pero correctos, escriba:
```
auditpol /set /user:mikedan /exclude /category:* /success:enable
```
### <a name="examples-for-the-system-audit-policy"></a>Ejemplos de la Directiva de auditoría del sistema
Para establecer la Directiva de auditoría del sistema para todas las subcategorías de la categoría de seguimiento detallado para incluir la auditoría solo para los intentos correctos, escriba:
```
auditpol /set /category:"detailed Tracking" /success:enable
```
> [!NOTE]
> No se modifica el valor de error.
> Para establecer la Directiva de auditoría del sistema para las categorías de acceso a objetos y del sistema (que es implícita porque se enumeran las subcategorías) y las subcategorías especificadas por los GUID para la supresión de intentos erróneos y la auditoría de intentos correctos, escriba:
> ```
> auditpol /set /subcategory:{0ccee9210-69ae-11d9-bed3-505054503030},{0ccee9211-69ae-11d9-bed3-505054503030}, /failure:disable /success:enable
> ```
> ### <a name="example-for-auditing-options"></a>Ejemplo de opciones de auditoría
> Para establecer las opciones de auditoría en el estado habilitado para la opción CrashOnAuditFail, escriba:
> ```
> auditpol /set /option:CrashOnAuditFail /value:enable
> ```
> #### <a name="additional-references"></a>Referencias adicionales
> [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)
