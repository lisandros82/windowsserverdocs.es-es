---
title: secedit
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58ed57ed-08e3-403d-a363-0620b358637a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5598f830ad4cef8d45c99594da12cbcdd84e7eef
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371113"
---
# <a name="secedit"></a>secedit



Configura y analiza la seguridad del sistema al comparar la configuración actual con las plantillas de seguridad especificadas.

## <a name="syntax"></a>Sintaxis

```
secedit 
[/analyze /db <database file name> /cfg <configuration file name> [/overwrite] /log <log file name> [/quiet]]
[/configure /db <database file name> [/cfg <configuration filename>] [/overwrite] [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]]
[/export /db <database file name> [/mergedpolicy] /cfg <configuration file name> [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>]]
[/generaterollback /db <database file name> /cfg <configuration file name> /rbk <rollback file name> [/log <log file name>] [/quiet]]
[/import /db <database file name> /cfg <configuration file name> [/overwrite] [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]]
[/validate <configuration file name>]
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|[Secedit:analyze](secedit-analyze.md)|Permite analizar la configuración actual de los sistemas con respecto a la configuración de línea de base almacenada en una base de datos.  Los resultados del análisis se almacenan en un área independiente de la base de datos y se pueden ver en el complemento configuración y análisis de seguridad.|
|[Secedit:configure](secedit-configure.md)|Permite configurar un sistema con una configuración de seguridad almacenada en una base de datos.|
|[Secedit:export](secedit-export.md)|Permite exportar la configuración de seguridad almacenada en una base de datos.|
|[Secedit:generaterollback](secedit-generaterollback.md)|Permite generar una plantilla de reversión con respecto a una plantilla de configuración.|
|[Secedit:import](secedit-import.md)|Permite importar una plantilla de seguridad en una base de datos de forma que la configuración especificada en la plantilla pueda aplicarse a un sistema o analizarse en un sistema.|
|[Secedit:validate](secedit-validate.md)|Permite validar la sintaxis de una plantilla de seguridad.|

## <a name="remarks"></a>Observaciones

En todos los nombres de archivo, se usa el directorio actual si no se especifica ninguna ruta de acceso.

Cuando se crea una plantilla de seguridad con el complemento plantilla de seguridad y se ejecuta el complemento configuración y análisis de seguridad, se crean los siguientes archivos:


|           Archivo           |                                                                                                                                                                                                                                                               Descripción                                                                                                                                                                                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        Scesrv. log        |                                                                                                                             **Ubicación**:%WINDIR%\security\logs</br>**Creado por**: sistema operativo</br>**Tipo de archivo**: texto</br>**Frecuencia de actualización**: se sobrescribe cuando se ejecutan secedit/Analyze,/configure,/Export o/Import.</br>**Contenido**: contiene los resultados del análisis agrupados por tipo de directiva.                                                                                                                             |
| *Nombre seleccionado por el usuario*. sdb |                                                                                    **Ubicación**:% windir%\*cuenta de usuario<em>\Documents\Security\Database</br></em>*creado por*<em>: ejecutar el complemento configuración y análisis de seguridad</br></em>*tipo de archivo*<em>: propietario</br>*frecuencia de actualización* de </em><em>: se actualiza cada vez que se crea una nueva plantilla de seguridad.</br></em>\*de *contenido* : directivas de seguridad local y plantillas de seguridad creadas por el usuario.                                                                                    |
| *Nombre seleccionado por el usuario*. log | **Ubicación**: definido por el usuario, pero el valor predeterminado es% windir%\*cuenta de usuario<em>\Documents\Security\Logs</br></em>*creado por*<em>: ejecutar los subcomandos/Analyze y/configure (o utilizar el complemento configuración y análisis de seguridad)</br></em>*tipo de archivo*<em>: texto</br>*frecuencia de actualización* de </em><em>: ejecutar los subcomandos/Analyze y/configure (o utilizar el complemento configuración y análisis de seguridad); sobrescribe.</br>\*de *contenido* </em>:</br>1. nombre de archivo de registro</br>2. fecha y hora</br>3. resultados del análisis o de la investigación. |
| *Nombre seleccionado por el usuario*. inf |                                                                                     **Ubicación**:% windir%\*cuenta de usuario<em>\Documents\Security\Templates</br></em>*creado por*<em>: ejecutar el complemento de plantilla de seguridad</br></em>*tipo de archivo*<em>: texto</br>*frecuencia de actualización* de </em><em>: cada vez que se actualiza la plantilla de seguridad</br></em>\*de *contenido* : contiene la información de configuración de la plantilla para cada directiva seleccionada mediante el complemento.                                                                                     |

> [!NOTE]
> Microsoft Management Console (MMC) y el complemento configuración y análisis de seguridad no están disponibles en Server Core.

#### <a name="additional-references"></a>Referencias adicionales

Para obtener ejemplos de cómo se puede usar este comando, consulte la sección ejemplos en cualquiera de los archivos de subcomando.
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)