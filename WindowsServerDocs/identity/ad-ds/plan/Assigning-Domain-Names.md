---
ms.assetid: 73897497-b189-4305-b234-e057ffda163a
title: Asignar nombres de dominio
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 357c136f108c6d8e9e2a15dd9449ab61663079e2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408998"
---
# <a name="assigning-domain-names"></a>Asignar nombres de dominio

>Se aplica a: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Debe asignar un nombre a cada dominio del plan. Los dominios de Active Directory Domain Services (AD DS) tienen dos tipos de nombres: Nombres del sistema de nombres de dominio (DNS) y nombres NetBIOS. En general, ambos nombres son visibles para los usuarios finales. Los nombres DNS de Active Directory dominios incluyen dos partes, un prefijo y un sufijo. Al crear nombres de dominio, determine primero el prefijo DNS. Esta es la primera etiqueta en el nombre DNS del dominio. El sufijo se determina cuando se selecciona el nombre del dominio raíz del bosque. En la tabla siguiente se enumeran las reglas de nomenclatura de prefijos para los nombres DNS.  
  
|Regla|Explicación|  
|--------|---------------|  
|Seleccione un prefijo que no sea probable que quede obsoleto.|Evite nombres como una línea de productos o un sistema operativo que podrían cambiar en el futuro. Se recomienda usar nombres geográficos.|  
|Seleccione un prefijo que incluya solo caracteres estándar de Internet.|A-Z, a-z, 0-9 y (-), pero no totalmente numérica.|  
|Incluya 15 caracteres o menos en el prefijo.|Si elige una longitud de prefijo de 15 caracteres o menos, el nombre NetBIOS es el mismo que el prefijo.|  
  
Para obtener más información, consulte convenciones de nomenclatura en Active Directory para equipos, dominios, sitios y unidades organizativas ([https://go.microsoft.com/fwlink/?LinkId=106629](https://go.microsoft.com/fwlink/?LinkId=106629)).  
  
> [!NOTE]  
>  Aunque Dcpromo.exe en Windows Server 2008 y Windows Server 2003 le permite crear un nombre de dominio DNS de etiqueta única, no debe usar un nombre DNS de etiqueta única para un dominio por varias razones. En Windows Server 2008 R2, Dcpromo.exe no permite crear un nombre DNS de etiqueta única para un dominio. Para obtener más información, vea [https://go.microsoft.com/fwlink/?LinkId=92467.](https://go.microsoft.com/fwlink/?LinkId=92467)   
  
Si el nombre NetBIOS actual del dominio no es apropiado para representar la región o no cumple las reglas de nomenclatura de prefijos, seleccione un nuevo prefijo. En este caso, el nombre NetBIOS del dominio es diferente del prefijo DNS del dominio.  
  
Para cada nuevo dominio que implemente, seleccione un prefijo adecuado para la región y que cumpla las reglas de nomenclatura de prefijos. Se recomienda que el nombre NetBIOS del dominio sea el mismo que el prefijo DNS.  
  
Documente el prefijo DNS y los nombres NetBIOS que seleccione para cada dominio del bosque. Puede Agregar la información de nombres DNS y NetBIOS a la hoja de cálculo "planeamiento de dominios" que creó para documentar el plan de dominios nuevos y actualizados. Para abrirlo, descargue Job_Aids_Designing_and_Deploying_Directory_and_Security_Services. zip de la ayuda del trabajo para el kit de implementación de Windows Server 2003 ([https://go.microsoft.com/fwlink/?LinkID=102558](https://go.microsoft.com/fwlink/?LinkID=102558)) y abra "planeamiento de dominios" (DSSLOGI_5. doc).  
  


