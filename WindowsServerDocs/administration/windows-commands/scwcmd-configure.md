---
title: Scwcmd configure
description: 'Tema de comandos de Windows para * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6528b9dc-3d82-4228-b734-ed717458d74c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 43bd70c33294b09f63b9718e4c0f2cdc6cace156
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384291"
---
# <a name="scwcmd-configure"></a>Scwcmd: configure

> Se aplica a: Windows Server 2012 R2, Windows Server 2012

Aplica una directiva de seguridad generada por el Asistente para configuración de seguridad (SCW) a un equipo. Esta herramienta de línea de comandos también acepta una lista de nombres de equipo como entrada.

## <a name="syntax"></a>Sintaxis

```
scwcmd configure [[[/m:<ComputerName> | /ou:<OuName>] /p:<Policy>] | /i:<ComputerList>] [/u:<UserName>] [/pw:<Password>] [/t:<Threads>]
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|/m:\<ComputerName >|Especifica el nombre NetBIOS, el nombre DNS o la dirección IP del equipo que se va a configurar. Si se especifica el parámetro **/m** , también se debe especificar el parámetro **/p** .|
|/ou:\<OuName >|Especifica el nombre de dominio completo (FQDN) de una unidad organizativa (OU) en Active Directory Domain Services. Si se especifica el parámetro **/ou** , también se debe especificar el parámetro **/p** . Todos los equipos de la unidad organizativa se analizarán según la Directiva especificada.|
|/p:\<Directiva >|Especifica la ruta de acceso y el nombre del archivo de directiva. XML que se va a usar para realizar la configuración.|
|/i:\<ComputerList >|Especifica la ruta de acceso y el nombre de un archivo. XML que contiene una lista de equipos junto con los archivos de directivas esperados. Todos los equipos del archivo. XML se configurarán según sus archivos de directiva correspondientes. Un archivo. XML de ejemplo es%windir%\security\SampleMachineList.xml.|
|/u:\<nombre de usuario >|Especifica una credencial de usuario alternativa para usar al configurar un equipo remoto. El valor predeterminado es el usuario que ha iniciado sesión.|
|/PW:\<contraseña >|Especifica una credencial de usuario alternativa para usar al configurar un equipo remoto. El valor predeterminado es la contraseña del usuario que ha iniciado sesión.|
|/t:\<subprocesos >|Especifica el número de operaciones de configuración pendientes simultáneas que se deben mantener durante el proceso de configuración (DefaultValue = 40, MinValue = 1, MaxValue = 1000).|
|/?|Muestra la ayuda en el símbolo del sistema.|

## <a name="remarks"></a>Observaciones

Scwcmd. exe solo está disponible en equipos que ejecutan Windows Server 2008 R2, Windows Server 2008 o Windows Server 2003.

## <a name="BKMK_Examples"></a>Example

Para configurar una directiva de seguridad en el archivo webpolicy. XML, escriba:
```
scwcmd configure /p:webpolicy.xml
```
Para configurar una directiva de seguridad para el equipo en 172.16.0.0 con el archivo webpolicy. XML mediante las credenciales de la cuenta WebAdmin, escriba:
```
scwcmd configure /m:172.16.0.0 /p:webpolicy.xml /u:webadmin
```
Para configurar una directiva de seguridad en todos los equipos de la lista campusmachines. XML con un máximo de 100 subprocesos, escriba:
```
scwcmd configure /i:campusmachines.xml /t:100
```
Para configurar una directiva de seguridad en todos los equipos de la unidad organizativa WebServers en el archivo webpolicy. XML con las credenciales de la cuenta de el servidor de archivos, escriba:
```
scwcmd configure /ou:OU=WebServers,DC=Marketing,DC=ABCCompany,DC=com /p:webpolicy.xml /u:DomainAdmin
```

#### <a name="additional-references"></a>Referencias adicionales

-   [Clave de sintaxis de línea de comandos](command-line-syntax-key.md)