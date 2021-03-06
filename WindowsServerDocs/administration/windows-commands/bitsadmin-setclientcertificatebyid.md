---
title: bitsadmin setclientcertificatebyid
description: El tema comandos de Windows para **bitsadmin setclientcertificatebyid** especifica el identificador del certificado de cliente que se va a usar para la autenticación de cliente en una solicitud HTTPS (SSL).
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8585a7a1-7472-437b-b04a-a11925782a3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 53b6fa4c65397cf710d0497fbae889afd31ec136
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380730"
---
# <a name="bitsadmin-setclientcertificatebyid"></a>bitsadmin setclientcertificatebyid



Especifica el identificador del certificado de cliente que se va a usar para la autenticación de cliente en una solicitud HTTPS (SSL).

## <a name="syntax"></a>Sintaxis

```
bitsadmin /SetClientCertificateByID <Job> <store_location> <store_name> hexa-decimal_cert_id>
```

## <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------|-----------|
|Trabajo|El nombre para mostrar del trabajo o el GUID|
|Store_location|Identifica la ubicación de un almacén del sistema que se va a usar para buscar el certificado. Los valores posibles son:</br>1 (CURRENT_USER)</br>2 (LOCAL_MACHINE)</br>3 (CURRENT_SERVICE)</br>4 (SERVICIOS)</br>5 (USUARIOS)</br>6 (CURRENT_USER_GROUP_POLICY)</br>7 (LOCAL_MACHINE_GROUP_POLICY)</br>8 (LOCAL_MACHINE_ENTERPRISE)|
|Store_name|Nombre del almacén de certificados. Los valores posibles son:</br>CA (certificados de entidad de certificación)</br>MIS (certificados personales)</br>RAÍZ (certificados raíz)</br>SPC (certificado de editor de software)|
|Hexadecimal_cert_id|Un número hexadecimal que representa el hash del certificado.|

## <a name="BKMK_examples"></a>Example

En el ejemplo siguiente se especifica el identificador del certificado de cliente que se va a utilizar para la autenticación del cliente en una solicitud HTTPS (SSL) para el trabajo denominado *myJob*.
```
C:\>bitsadmin Bitsadmin /SetClientCertificateByID myJob BG_CERT_STORE_LOCATION_CURRENT_USER MY A106B52356D3FBCD1853A41B619358BD 
```

#### <a name="additional-references"></a>Referencias adicionales

[Clave de sintaxis de línea de comandos](command-line-syntax-key.md)