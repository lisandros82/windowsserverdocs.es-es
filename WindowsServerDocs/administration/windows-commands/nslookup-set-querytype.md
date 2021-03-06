---
title: nslookup set querytype
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5af54ac5-fc1a-4af6-977b-f8e97c8eba90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc0eb19fd66e738b4bfc110a2bbc172153a12d98
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372903"
---
# <a name="nslookup-set-querytype"></a>nslookup set querytype

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Cambia el tipo de registro de recursos de la consulta.
## <a name="syntax"></a>Sintaxis
```
set querytype=<ResourceRecordtype>
```
## <a name="parameters"></a>Parámetros
<ResourceRecordtype> especifica un tipo de registro de recursos DNS. El tipo de registro de recursos predeterminado es. En la tabla siguiente se enumeran los valores válidos para este comando.

| Valor |                                                   Descripción                                                   |
|-------|-----------------------------------------------------------------------------------------------------------------|
|   A   |                                      Especifica la dirección&#39;IP de un equipo.                                      |
|  CUALQUIER  |                                     Especifica la dirección&#39;IP de un equipo.                                      |
| CNAME |                                    Especifica un nombre canónico para un alias.                                     |
|  GID  |                                  Especifica un identificador de grupo de un nombre de grupo.                                  |
| HINFO |                          Especifica la CPU&#39;y el tipo de sistema operativo de un equipo.                           |
|  MB   |                                        Especifica un nombre de dominio de buzón.                                         |
|  MG   |                                         Especifica un miembro del grupo de correo.                                          |
| MINFO |                                   Especifica la información de buzón o de lista de correo.                                   |
|  MR   |                                     Especifica el nombre de dominio del cambio de nombre de correo.                                      |
|  MX   |                                          Especifica el intercambiador de correo.                                          |
|  NS   |                                 Especifica un servidor de nombres DNS para la zona con nombre.                                 |
|  ANOTA  | Especifica un nombre de equipo si la consulta es una dirección IP; de lo contrario, especifica el puntero a otra información. |
|  Oriente  |                                Especifica el inicio de autoridad de una zona DNS.                                 |
|  TXT  |                                         Especifica la información de texto.                                         |
|  UID  |                                         Especifica el identificador de usuario.                                          |
| UINFO |                                         Especifica la información del usuario.                                         |
|  WKS  |                                         Describe un servicio bien conocido.                                         |
| {ayuda |                                                       ?}                                                        |

Muestra un breve resumen de los subcomandos de <strong>nslookup</strong>
## <a name="remarks"></a>Observaciones
- El comando <strong>set Type</strong> realiza la misma función que el comando <strong>set QueryType</strong> .
- Para obtener más información acerca de los tipos de registro de recursos, consulte la solicitud de comentarios (RFC) 1035.
  ## <a name="additional-references"></a>referencias adicionales
  <a href="command-line-syntax-key.md" data-raw-source="[Command-Line Syntax Key](command-line-syntax-key.md)">Clave de sintaxis de línea de comandos</a>
  <a href="nslookup-set-type.md" data-raw-source="[nslookup set type](nslookup-set-type.md)">tipo de conjunto nslookup</a>
