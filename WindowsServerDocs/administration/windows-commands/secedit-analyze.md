---
title: 'secedit: ANALYZE'
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3430cf9d-1411-48b1-b5a9-2e47701dc87f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6fd12d5055853a97b6bd253a83798d35effaa1f0
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371168"
---
# <a name="seceditanalyze"></a>secedit: ANALYZE



Permite analizar la configuración actual de los sistemas con respecto a la configuración de línea de base almacenada en una base de datos. Para obtener ejemplos de cómo se puede usar este comando, vea [ejemplos](#BKMK_Examples).

## <a name="syntax"></a>Sintaxis

```
Secedit /analyze /db <database file name> [/cfg <configuration file name>] [/overwrite] [/log <log file name>] [/quiet}]
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|bases|Obligatorio.</br>Especifica la ruta de acceso y el nombre de un archivo de base de datos que contiene la configuración almacenada en la que se realizará el análisis.</br>Si nombre de archivo especifica una base de datos que no tiene una plantilla de seguridad (tal como la representa el archivo de configuración) `/cfg \<configuration file name>` asociada, también se debe especificar la opción de línea de comandos.|
|cfg|Opcional.</br>Especifica la ruta de acceso y el nombre de archivo de la plantilla de seguridad que se importará en la base de datos para su análisis.</br>Esta opción/cfg solo es válida cuando se usa con `/db \<database file name>` el parámetro. Si no se especifica, el análisis se realiza en cualquier configuración que ya esté almacenada en la base de datos.|
|sobrescribir|Opcional.</br>Especifica si la plantilla de seguridad del parámetro/cfg debe sobrescribir cualquier plantilla o plantilla compuesta almacenada en la base de datos en lugar de anexar los resultados a la plantilla almacenada.</br>Esta opción de línea de comandos solo es válida cuando `/cfg \<configuration file name>` se usa también el parámetro. Si no se especifica, la plantilla del parámetro/cfg se anexa a la plantilla almacenada.|
|Inicia|Opcional.</br>Especifica la ruta de acceso y el nombre del archivo de registro que se va a utilizar en el proceso.|
|Actividad|Opcional.</br>Suprime la salida de la pantalla. Todavía puede ver los resultados del análisis mediante el complemento configuración y análisis de seguridad de Microsoft Management Console (MMC).|

## <a name="remarks"></a>Comentarios

Los resultados del análisis se almacenan en un área independiente de la base de datos y se pueden ver en el complemento configuración y análisis de seguridad de MMC.

Si no se proporciona la ruta de acceso del archivo de registro, se usa el archivode registro predeterminado,\*(SystemRoot \Documents and Settings cuentadeusuario<em>\*\Mis Documents\Security\Logs DatabaseName</em>. log).

En Windows Server 2008, `Secedit /refreshpolicy` se ha reemplazado `gpupdate`por. Para obtener información acerca de cómo actualizar la configuración de seguridad, consulte [gpupdate](gpupdate.md).

## <a name="BKMK_Examples"></a>Example

Realice el análisis de los parámetros de seguridad en la base de datos de seguridad, SecDbContoso. sdb, que creó con el complemento configuración y análisis de seguridad. Dirija la salida al archivo SecAnalysisContosoFY11 con la solicitud para que pueda comprobar que el comando se ejecutó correctamente.
```
Secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /log C:\Security\FY11\SecAnalysisContosoFY11.log
```
Supongamos que el análisis ha revelado algunos inadequacies, por lo que se ha modificado la plantilla de seguridad, SecContoso. inf. Vuelva a ejecutar el comando para incorporar los cambios y dirigir la salida al archivo SecAnalysisContosoFY11 existente sin preguntar.
```
Secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /cfg SecContoso.inf /overwrite /log C:\Security\FY11\SecAnalysisContosoFY11.xml /quiet
```

#### <a name="additional-references"></a>Referencias adicionales

-   [Secedit](secedit.md)
-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)