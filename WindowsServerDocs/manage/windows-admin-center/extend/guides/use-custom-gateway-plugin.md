---
title: Usar un complemento de puerta de enlace personalizado en la extensión de herramienta
description: 'Desarrollar una extensión de herramienta SDK del centro de administración de Windows (proyecto Honolulu): usar un complemento de puerta de enlace personalizado en la extensión de la herramienta'
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 829cbf6df8cc2738bf4066b36210b860595774ed
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385230"
---
# <a name="use-a-custom-gateway-plugin-in-your-tool-extension"></a>Usar un complemento de puerta de enlace personalizado en la extensión de herramienta

>Se aplica a: Windows Admin Center, Versión preliminar de Windows Admin Center

En este artículo, usaremos un complemento de puerta de enlace personalizado en una nueva extensión de herramienta vacía que hemos creado con la CLI del centro de administración de Windows.

## <a name="prepare-your-environment"></a>Preparar el entorno ##

Si todavía no lo ha hecho, siga las instrucciones de [desarrollo de una extensión de herramienta](../develop-tool.md) para preparar el entorno y crear una nueva extensión de herramienta vacía.

## <a name="add-a-module-to-your-project"></a>Agregar un módulo al proyecto ##

Si aún no lo ha hecho, agregue un nuevo [módulo vacío](add-module.md) al proyecto, que se usará en el paso siguiente.  

## <a name="add-integration-to-custom-gateway-plugin"></a>Incorporación de integración al complemento de puerta de enlace personalizada ##

Ahora vamos a usar un complemento de puerta de enlace personalizado en el nuevo módulo vacío que acabamos de crear.

### <a name="create-pluginservicets"></a>Crear plugin. Service. ts

Cambie al directorio del nuevo módulo de herramientas creado anteriormente (```\src\app\{!Module-Name}```) y cree un nuevo archivo ```plugin.service.ts```.

Agregue el código siguiente al archivo que acaba de crear:
``` ts
import { Injectable } from '@angular/core';
import { AppContextService, HttpService } from '@microsoft/windows-admin-center-sdk/angular';
import { Cim, Http, PowerShell, PowerShellSession } from '@microsoft/windows-admin-center-sdk/core';
import { AjaxResponse, Observable } from 'rxjs';

@Injectable()
export class PluginService {
    constructor(private appContextService: AppContextService, private http: Http) {
    }
    
    public getGatewayRestResponse(): Observable<any> {
        let callUrl = this.appContextService.activeConnection.nodeName;

        return this.appContextService.node.get(callUrl, 'features/Sample%20Uno').map(
            (response: any) => {
                return response;
            }
        )
    }
}
```

Cambie las referencias a ```Sample Uno``` y ```Sample%20Uno``` al nombre de la característica según corresponda.

[!WARNING]
> Se recomienda que el ```this.appContextService.node``` integrado se use para llamar a cualquier API que esté definida en el complemento de puerta de enlace personalizada. Esto garantizará que, si se requieren credenciales en el complemento de puerta de enlace, se controlarán correctamente.

### <a name="modify-modulets"></a>Modificar módulo. ts

Abra el archivo ```module.ts``` del nuevo módulo creado anteriormente (es decir, ```{!Module-Name}.module.ts```):

Agregue las siguientes instrucciones de importación:

``` ts
import { HttpService } from '@microsoft/windows-admin-center-sdk/angular';
import { Http } from '@microsoft/windows-admin-center-sdk/core';
import { PluginService } from './plugin.service';
```

Agregue los siguientes proveedores (después de las declaraciones):

``` ts
  ,
  providers: [
    HttpService,
    PluginService,
    Http
  ]
```

### <a name="modify-componentts"></a>Modificar componente. ts

Abra el archivo ```component.ts``` del nuevo módulo creado anteriormente (es decir, ```{!Module-Name}.component.ts```):

Agregue las siguientes instrucciones de importación:

``` ts
import { ActivatedRouteSnapshot } from '@angular/router';
import { AppContextService } from '@microsoft/windows-admin-center-sdk/angular';
import { Subscription } from 'rxjs';
import { Strings } from '../../generated/strings';
import { PluginService } from './plugin.service';
```

Agregue las siguientes variables:

``` ts
  private serviceSubscription: Subscription;
  private responseResult: string;
```

Modifique el constructor y modifique o agregue las siguientes funciones:

``` ts
  constructor(private appContextService: AppContextService, private plugin: PluginService) {
    //
  }

  public ngOnInit() {
    this.responseResult = 'click go to do something';
  }

  public onClick() {
    this.serviceSubscription = this.plugin.getGatewayRestResponse().subscribe(
      (response: any) => {
        this.responseResult = 'response: ' + response.message;
      },
      (error) => {
        console.log(error);
      }
    );
  }
```

### <a name="modify-componenthtml"></a>Modificar Component. html ###

Abra el archivo ```component.html``` del nuevo módulo creado anteriormente (es decir, ```{!Module-Name}.component.html```):

Agregue el siguiente contenido al archivo HTML:
``` html
<button (click)="onClick()" >go</button>
{{ responseResult }}
```

## <a name="build-and-side-load-your-extension"></a>Compilar y cargar la extensión

Ahora está listo para [compilar y cargar](../develop-tool.md#build-and-side-load-your-extension) la extensión en el centro de administración de Windows.
