---
title: Agregar una pestaña a Configuración
description: Describe cómo usar Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aac6b7f3-9020-46c3-a83f-b81542300385
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 9eaa1aa5a9c5e8d4c2e36f2000e0adecc83245d9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854986"
---
# <a name="add-a-tab-to-settings"></a>Agregar una pestaña a Configuración

>Se aplica a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Puede agregar una ficha a Configuración en el Panel; para ello, cree e instale un ensamblado de código usado por el Administrador de configuración en el sistema operativo.  
  
## <a name="add-a-tab-to-settings"></a>Agregar una ficha a Configuración  
 Complete las tareas siguientes para agregar una ficha a Configuración:  
  
-   [Agregue una implementación de la interfaz de ISettingsData al ensamblado](Add-a-Tab-to-Settings.md#BKMK_ISettingsData).  
  
-   [Sign the assembly with an Authenticode signature](Add-a-Tab-to-Settings.md#BKMK_SignAssembly).  
  
-   [Install the assembly on the reference computer](Add-a-Tab-to-Settings.md#BKMK_InstallAssembly).  
  
###  <a name="BKMK_ISettingsData"></a> Agregue una implementación de la interfaz de ISettingsData al ensamblado  
 La interfaz de ISettingsData está incluida en el espacio de nombres de Microsoft.WindowsServerSolutions.Settings del ensamblado AdminCommon.dll que se encuentra en \Archivos de programa\Windows Server\Bin.  
  
##### <a name="to-add-the-isettingsdata-code-to-the-assembly"></a>Para agregar el código ISettingsData al ensamblado  
  
1.  Abra Visual Studio 2010 como administrador; para ello, haga clic con el botón secundario en el menú **Inicio** y seleccione **Ejecutar como administrador**.  
  
2.  Haga clic en **Archivo**, **Nuevo**y a continuación haga clic en **Proyecto**.  
  
3.  En el cuadro de diálogo **Nuevo proyecto** , haga clic en **Visual C#**, en **Biblioteca de clases**, escriba **DashboardSettingsPage** como el nombre de la solución y después haga clic en **Aceptar**.  
  
    > [!IMPORTANT]
    >  El conjunto que se instala en el servidor debe nombrarse DashboardSettingsPage.dll y, a continuación, copiar la dll a %ProgramFiles%\Windows Server\Bin\OEM.  
  
4.  Cree el control que desee utilizar en la pestaña. En el ejemplo siguiente, el nombre del control de configuración es MySettingsControl.  
  
5.  Cambie el nombre del archivo Class1.cs. Por ejemplo, MySettingTab.cs.  
  
6.  Agregue una referencia al archivo AdminCommon.dll.  
  
7.  Agregue lo siguiente mediante la declaración:  
  
    ```c#  
    using Microsoft.WindowsServerSolutions.Settings;  
    ```  
  
8.  Cambie el espacio de nombres y el encabezado de la clase para que coincida con el ejemplo siguiente:  
  
    ```  
  
    namespace DashboardSettingsPage  
    {  
        public class MySettingTab : ISettingsData  
        {  
        }  
    }  
  
    ```  
  
9. Cree una instancia del control que haya creado para la pestaña. Por ejemplo:  
  
    ```c#  
    private MySettingsControl tab;  
    ```  
  
10. Agregue el constructor de la clase. En el siguiente ejemplo de código se muestra el constructor:  
  
    ```  
  
    public MySettingTab()  
    {  
       tab = new MySettingsControl();  
    }  
    ```  
  
11. Agregue el método Commit, que envía los cambios en la configuración. En el siguiente ejemplo de código se muestra el método Commit:  
  
    ```  
  
    void ISettingsData.Commit(bool dismissed)  
    {  
       // Implement the code that is required to submit your setting changes  
    }  
    ```  
  
12. Agregue el método TabControl, que identifica el control de la pestaña. En el siguiente ejemplo de código se muestra el método TabControl:  
  
    ```  
  
    System.Windows.Forms.Control ISettingsData.TabControl  
    {  
       get { return tab; }  
    }  
    ```  
  
13. Agregue el método TabId, que proporciona un identificador único a la pestaña. En el siguiente ejemplo de código se muestra el método TabId:  
  
    ```  
  
    private Guid id = Guid.NewGuid();  
  
    Guid ISettingsData.TabId  
    {  
       get { return id; }  
    }  
    ```  
  
14. Agregue el método TabOrder, que da como resultado el orden de la pestaña. En el siguiente ejemplo de código se muestra el método TabOrder:  
  
    ```  
  
    int ISettingsData.TabOrder  
    {  
       get { return 0; }  
    }  
    ```  
  
    > [!NOTE]
    >  El orden de las fichas se define utilizando números a partir de 0. Las pestañas integradas de configuración de Microsoft se muestran primero y a continuación las pestañas del usuario en función del orden establecido. Por ejemplo, si dispone de tres pestañas de configuración, puede especificar el orden como 0, 1 y 2, dependiendo del orden en que desee que aparezcan.  
  
15. Agregue el método TabTitle, que ofrece el título de la pestaña. En el siguiente ejemplo de código se muestra el método TabTitle:  
  
    ```  
  
    string ISettingsData.TabTitle  
    {  
      get { return "My Settings Tab"; }  
    }  
    ```  
  
    > [!NOTE]
    >  El texto del título también puede proceder de un archivo de recursos que se adapte a sus necesidades de localización.  
  
16. Guarde y genere la solución.  
  
###  <a name="BKMK_SignAssembly"></a> Firmar el ensamblado con una firma Authenticode  
 Para poder utilizar el ensamblado en el sistema operativo es necesario firmarlo mediante Authenticode. Para obtener más información acerca de cómo firmar el ensamblado, consulte [Signing and Checking Code with Authenticode (Firma y comprobación de código con Authenticode)](https://msdn.microsoft.com/library/ms537364\(VS.85\).aspx#SignCode).  
  
###  <a name="BKMK_InstallAssembly"></a> Instale al ensamblado en el equipo de referencia  
 Después de crear correctamente la solución, coloque una copia del archivo DashboardSettingsPage.dll en la siguiente carpeta del equipo de referencia:  
  
 **%Programfiles%\Windows Server\Bin\OEM**  
  
## <a name="see-also"></a>Vea también  
 [Crear y personalizar la imagen](Creating-and-Customizing-the-Image.md)   
 [Personalizaciones adicionales](Additional-Customizations.md)   
 [Preparar la imagen para la implementación](Preparing-the-Image-for-Deployment.md)   
 [Probar la experiencia del cliente](Testing-the-Customer-Experience.md)