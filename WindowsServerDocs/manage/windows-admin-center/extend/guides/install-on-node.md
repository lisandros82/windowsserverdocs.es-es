---
title: Desarrollar una extensión de herramienta
description: Desarrollar una extensión de herramienta SDK del centro de administración de Windows (proyecto Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 3a93a1105862ffbf4fcbd1d23b15d9bcaa6010dc
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2020
ms.locfileid: "75950501"
---
# <a name="install-extension-payload-on-a-managed-node"></a>Instalar la carga de la extensión en un nodo administrado

>Se aplica a: Windows Admin Center, Versión preliminar de Windows Admin Center

## <a name="setup"></a>Configuración
> [!NOTE]
> Para seguir esta guía, necesitará la compilación 1.2.1904.02001 o una versión posterior. Para comprobar el número de compilación, abra el centro de administración de Windows y haga clic en el signo de interrogación en la parte superior derecha.

Si todavía no lo ha hecho, cree una [extensión de herramienta](../develop-tool.md) para el centro de administración de Windows. Una vez completada esta anotación, anote los valores que se usan al crear una extensión:

| Valor | Explicación | Ejemplo |
| ----- | ----------- | ------- |
| ```{!Company Name}``` | El nombre de su empresa (con espacios) | ```Contoso``` |
| ```{!Tool Name}``` | El nombre de la herramienta (con espacios) | ```InstallOnNode``` |

Dentro de la carpeta de extensión de herramienta, cree una carpeta de ```Node``` (```{!Tool Name}\Node```). Cualquier cosa que se coloque en esta carpeta se copiará en el nodo administrado al usar esta API. Agregue los archivos necesarios para su caso de uso. 

Cree también un script ```{!Tool Name}\Node\installNode.ps1```. Este script se ejecutará en el nodo administrado una vez que se copien todos los archivos de la carpeta ```{!Tool Name}\Node``` en el nodo administrado. Agregue cualquier lógica adicional para su caso de uso. Un ejemplo de archivo ```{!Tool Name}\Node\installNode.ps1```:

``` ps1
# Add logic for installing payload on managed node
echo 'Success'
```

> [!NOTE]
> ```{!Tool Name}\Node\installNode.ps1``` tiene un nombre específico que la API buscará. Al cambiar el nombre de este archivo se producirá un error.


## <a name="integration-with-ui"></a>Integración con la interfaz de usuario

Actualice ```\src\app\default.component.ts``` a lo siguiente:

``` ts
import { Component } from '@angular/core';
import { AppContextService } from '@microsoft/windows-admin-center-sdk/angular';
import { Observable } from 'rxjs';

@Component({
  selector: 'default-component',
  templateUrl: './default.component.html',
  styleUrls: ['./default.component.css']
})

export class DefaultComponent {
  constructor(private appContextService: AppContextService) { }

  public response: any;
  public loading = false;

  public installOnNode() {
    this.loading = true;
    this.post('{!Company Name}.{!Tool Name}', '1.0.0',
      this.appContextService.activeConnection.nodeName).subscribe(
        (response: any) => {
          console.log(response);
          this.response = response;
          this.loading = false;
        },
        (error) => {
          console.log(error);
          this.response = error;
          this.loading = false;
        }
      );
  }

  public post(id: string, version: string, targetNode: string): Observable<any> {
    return this.appContextService.node.post(targetNode,
      `features/extensions/${id}/versions/${version}/install`);
  }

}
```
Actualice los marcadores de posición a los valores que se usaron al crear la extensión:
``` ts
this.post('contoso.install-on-node', '1.0.0',
      this.appContextService.activeConnection.nodeName).subscribe(
        (response: any) => {
          console.log(response);
          this.response = response;
          this.loading = false;
        },
        (error) => {
          console.log(error);
          this.response = error;
          this.loading = false;
        }
      );
```

Actualice también ```\src\app\default.component.html``` a:
``` html
<button (click)="installOnNode()">Click to install</button>
<sme-loading-wheel *ngIf="loading" size="large"></sme-loading-wheel>
<p *ngIf="response">{{response}}</p>
```
Y, por último, ```\src\app\default.module.ts```:
``` ts
import { CommonModule } from '@angular/common';
import { NgModule } from '@angular/core';

import { LoadingWheelModule } from '@microsoft/windows-admin-center-sdk/angular';
import { DefaultComponent } from './default.component';
import { Routing } from './default.routing';

@NgModule({
  imports: [
    CommonModule,
    LoadingWheelModule,
    Routing
  ],
  declarations: [DefaultComponent]
})
export class DefaultModule { }

```

## <a name="creating-and-installing-a-nuget-package"></a>Creación e instalación de un paquete NuGet

El último paso es compilar un paquete NuGet con los archivos que hemos agregado y luego instalar ese paquete en el centro de administración de Windows.

Siga la guía de [Publishing Extensions](../publish-extensions.md) si no ha creado previamente un paquete de extensión. 
> [!IMPORTANT]
> En el archivo. nuspec para esta extensión, es importante que el valor de ```<id>``` coincida con el nombre del ```manifest.json``` del proyecto y que el ```<version>``` coincida con lo que se agregó a ```\src\app\default.component.ts```. Agregue también una entrada en ```<files>```: 
> 
> ```<file src="Node\**\*.*" target="Node" />```.

``` xml
<?xml version="1.0" encoding="utf-8"?>
<package xmlns="https://schemas.microsoft.com/packaging/2011/08/nuspec.xsd">
  <metadata>
    <id>contoso.install-on-node</id>
    <version>1.0.0</version>
    <authors>Contoso</authors>
    <owners>Contoso</owners>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <projectUrl>https://msft-sme.myget.org/feed/windows-admin-center-feed/package/nuget/contoso.sme.install-on-node-extension</projectUrl>
    <licenseUrl>http://YourLicenseLink</licenseUrl>
    <iconUrl>http://YourLogoLink</iconUrl>
    <description>Install on node extension by Contoso</description>
    <copyright>(c) Contoso. All rights reserved.</copyright> 
  </metadata>
    <files>
    <file src="bundle\**\*.*" target="ux" />
    <file src="package\**\*.*" target="gateway" />
    <file src="Node\**\*.*" target="Node" />
  </files>
</package>
```

Una vez creado este paquete, agregue una ruta de acceso a dicha fuente. En el centro de administración de Windows, vaya a Configuración > Extensiones > fuentes y agregue la ruta de acceso a la ubicación en la que se encuentra el paquete. Cuando haya terminado de instalar la extensión, podrá hacer clic en el botón ```install``` y se llamará a la API.  