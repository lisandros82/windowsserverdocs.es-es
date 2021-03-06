---
title: Conversión de un disco GPT (tabla de particiones GUID) en un disco MBR (registro de arranque maestro)
description: Describe cómo convertir un disco con el estilo de partición de tabla de particiones GUID (GPT) en un disco con el estilo de partición de registro de arranque maestro (MBR).
ms.date: 06/19/2018
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 5c6efb0697af663b32ce6f0e27634c3962eca492
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402105"
---
# <a name="convert-a-gpt-disk-into-an-mbr-disk"></a>Conversión de un disco GPT en un disco MBR

> **Se aplica a:** Windows 10, Windows 8.1, Windows Server (canal semianual), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 y Windows Server 2012

Los discos MBR (registro de arranque maestro) usan la tabla de particiones de BIOS estándar. Los discos GPT (tabla de particiones GUID) usan Unified Extensible Firmware Interface (UEFI). Los discos MBR no admiten más de cuatro particiones en cada disco. El método de partición MBR no se recomienda para discos de más de dos terabytes (TB).

Puedes cambiar un disco de un estilo de partición GPT a un estilo de partición MBR siempre que esté vacío y no contenga volúmenes.

> [!NOTE]
> Antes de convertir un disco, realiza una copia de seguridad de sus datos y cierra todos los programas que accedan al mismo.

> [!NOTE]
> Debes ser miembro del grupo **Operadores de copia de seguridad** o **Administradores**, como mínimo, para completar estos pasos.

## <a name="converting-using-the-windows-interface"></a>Conversión mediante la interfaz de Windows

1.  Realiza una copia de seguridad o mueve todos los volúmenes del disco GPT básico que quieras convertir en disco MBR.

2.  Si el disco contiene particiones o volúmenes, haz clic con el botón derecho en cada uno de ellos y después en **Eliminar volumen**.

3.  Haz clic con el botón derecho en el disco GPT que quieres convertir en un disco MBR y luego en **Convertir en disco MBR**.

## <a name="converting-using-a-command-line"></a>Conversión desde la línea de comandos

1.  Realiza una copia de seguridad o mueve todos los volúmenes del disco GPT básico que quieras convertir en disco MBR.

2.  Abre un símbolo del sistema con privilegios elevados, para lo que debes hacer clic con el botón derecho en **Símbolo del sistema** y luego Elegir **Ejecutar como administrador**.

3. Escriba `diskpart`. Si el disco no contiene particiones ni volúmenes, dirígete al paso 6.

4.  En el símbolo del sistema **DISKPART**, escribe `list disk`. Anota el número de disco que quieres eliminar.

5.  En el símbolo del sistema **DISKPART**, escribe `select disk <disknumber>`.

6.  En el símbolo del sistema **DISKPART**, escribe `clean`.

    > [!IMPORTANT]
    > Al ejecutar el comando **clean**, se eliminarán todas las particiones o volúmenes del disco.

7.  En el símbolo del sistema **DISKPART**, escribe `convert mbr`.

|                Valor                  |      Descripción   |
| ------------------------------------- | -----------------  |
|  <strong>list disk</strong>  | Muestra una lista de discos e información sobre ellos, como su tamaño, la cantidad de espacio disponible, si se trata de un disco básico o dinámico y si el disco utiliza el estilo de partición de Registro de arranque maestro (MBR) o Tabla de particiones GUID (GPT). El disco marcado con un asterisco (\*) tiene el foco. |
| <strong>select disk</strong> |                                                                                                          Selecciona el disco especificado, donde <em>disknumber</em> es el número de disco y el que recibe el foco.                                                                                                           |
| <strong>convert mbr</strong> |                                                                               Convierte un disco básico vacío con el estilo de partición de tabla de particiones GUID (GPT) en un disco básico con el estilo de partición de registro de arranque maestro (MBR).                                                                                |

## <a name="see-also"></a>Consulta también

-   [Notación de sintaxis de línea de comandos](https://technet.microsoft.com/library/cc742449(v=ws.11).aspx)