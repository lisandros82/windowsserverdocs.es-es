---
title: Scwcmd registrar
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe4d126a-9f27-4076-b7b1-fbefa45f378a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2e892f7c08461e88d12a072dfb171f9523558ef7
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371218"
---
# <a name="scwcmd-register"></a>Scwcmd: register

> Se aplica a: Windows Server 2012 R2, Windows Server 2012

Extiende o Personaliza la base de datos de configuración de seguridad del Asistente para configuración de seguridad (SCW) registrando un archivo de base de datos de configuración de seguridad que contiene definiciones de roles, tareas, servicios o puertos.

## <a name="syntax"></a>Sintaxis

```
scwcmd register /kbname:<MyApp> [/kbfile:<kb.xml>] [/kb:<path>] [/d]
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|/kbname:\<MyApp >|Especifica el nombre con el que se registrará la extensión de la base de datos de configuración de seguridad. Se debe especificar este parámetro.|
|/KBFile:\<KB. XML >|Especifica la ruta de acceso y el nombre del archivo de base de datos de configuración de seguridad que se utilizará para extender o personalizar la base de datos de configuración de seguridad base. Para validar que el archivo de base de datos de configuración de seguridad es compatible con el esquema de SCW, use el archivo de definición de esquema%windir%\security\KBRegistrationInfo.xsd. Se debe proporcionar esta opción a menos que se especifique el parámetro **/d** .|
|/KB:\<ruta de acceso >|Especifica la ruta de acceso al directorio que contiene los archivos de base de datos de configuración de seguridad de SCW que se van a actualizar. Si no se especifica esta opción, se utiliza%WINDIR%\security\msscw\kbs.|
|/d|Anula el registro de una extensión de base de datos de configuración de seguridad de la base de datos de configuración de seguridad. La extensión a la que se va a anular el registro se especifica mediante el parámetro/kbname. (No se debe especificar el parámetro **/KBFile** ). La base de datos de configuración de seguridad de la que se va a anular el registro de la extensión se especifica mediante el parámetro **/KB** .|
|/?|Muestra la ayuda en el símbolo del sistema.|

## <a name="remarks"></a>Observaciones

Scwcmd. exe solo está disponible en equipos que ejecutan Windows Server 2008 R2, Windows Server 2008 o Windows Server 2003.

## <a name="BKMK_Examples"></a>Example

Para registrar el archivo de base de datos de configuración de seguridad denominado SCWKBForMyApp. XML bajo el nombre MyApp en la ubicación \\\\kbserver\kb, escriba:
```
scwcmd register /kbfile:d:\SCWKBForMyApp.xml /kbname:MyApp /kb:\\kbserver\kb
```
Para anular el registro de la base de datos de configuración de seguridad MyApp ubicada en \\\\kbserver\kb, escriba:
```
scwcmd register /d /kbname:MyApp /kb:\\kbserver\kb
```

#### <a name="additional-references"></a>Referencias adicionales

-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)