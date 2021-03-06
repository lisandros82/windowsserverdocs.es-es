---
title: freedisk
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91c15166-5baa-4b80-9e0c-4cd815d00530
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8e417a8f9768706fe391f705adde37c62ceaa818
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377028"
---
# <a name="freedisk"></a>freedisk

>Se aplica a: Windows Server (canal semianual), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Comprueba si la cantidad especificada de espacio en disco está disponible antes de continuar con un proceso de instalación.

## <a name="syntax"></a>Sintaxis
```
freedisk [/s <computer> [/u [<Domain>\]<User> [/p [<Password>]]]] [/d <Drive>] [<Value>]
```
## <a name="parameters"></a>Parámetros

|       Parámetro       |                                                                                         Descripción                                                                                          |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     /s <computer>     | Especifica el nombre o la dirección IP de un equipo remoto (no use barras diagonales inversas). El valor predeterminado es el equipo local. Este parámetro se aplica a todos los archivos y carpetas especificados en el comando. |
| /u [<Domain>\\]<User> |                                            Ejecuta el script con los permisos de la cuenta de usuario especificada. El valor predeterminado es los permisos del sistema.                                            |
|    /p [<Password>]    |                                                           Especifica la contraseña de la cuenta de usuario especificada en **/u**.                                                            |
|      /d <Drive>       |                              Especifica la unidad para la que desea averiguar la disponibilidad de espacio disponible. Debe especificar <Drive>para un equipo remoto.                               |
|        <Value>        |                                     Comprueba una cantidad específica de espacio libre en disco. Puede especificar <Value>en bytes, KB, MB, GB, TB, PB, EB, ZB o YB.                                      |

## <a name="remarks"></a>Observaciones
- El uso de las opciones de línea de comandos **/s**, **/u**y **/p** solo está disponible cuando se utiliza **/s**. Debe usar **/p** con **/u**para proporcionar la contraseña del usuario.
- en el caso de las instalaciones desatendidas, puede usar **FREEDISK** en archivos por lotes de instalación para comprobar el espacio disponible en la cantidad de requisitos previos antes de continuar con la instalación.
- Cuando se usa **FREEDISK** en un archivo por lotes, devuelve **0** si hay espacio suficiente y un **1** si no hay suficiente espacio.
  ## <a name="BKMK_examples"></a>Example
  Para determinar si hay al menos 50 MB de espacio libre disponible en la unidad C:, escriba:
  ```
  freedisk 50mb 
  ```
  En la pantalla aparece un resultado similar al siguiente:
  ```
  INFO: The specified 52,428,800 byte(s) of free space is available on current drive.
  ```
  ## <a name="additional-references"></a>referencias adicionales
  [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)
