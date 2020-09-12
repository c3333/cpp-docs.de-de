---
title: /DRIVER (Treiber für den Kernelmodus von Windows NT)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
ms.openlocfilehash: c935c20d6c1c009cff64d48e0c0122c8b91bbba3
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041158"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Treiber für den Kernelmodus von Windows NT)

>/Driver [: UPONLY |: WDM]

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die Option **/Driver** Linker, um einen Windows NT-Kernelmodustreiber zu erstellen.

**/Driver:** der Linker bewirkt, dass der Linker das **IMAGE_FILE_UP_SYSTEM_ONLY** Bit den Merkmalen im Ausgabe Header hinzufügt, um anzugeben, dass es sich um einen Uniprozessor-Treiber (up) handelt. Das Betriebssystem wird das Laden eines uptreibers auf einem Multiprozessorsystem (MP) ablehnen.

**/Driver: WDM** bewirkt, dass der Linker das **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** -Bit im DllCharacteristics-Feld des optionalen Headers festgelegt hat.

Wenn **/Driver** nicht angegeben ist, werden diese Bits nicht vom Linker festgelegt.

Wenn **/Driver** angegeben wird:

- **/Fixed: No** ist in Kraft. Weitere Informationen finden Sie unter [/Fixed (Fixed base address)](fixed-fixed-base-address.md).

- Die Erweiterung der Ausgabedatei wird auf. sys festgelegt. Verwenden Sie **/out** , um den Standard Dateinamen und die Erweiterung zu ändern Weitere Informationen finden Sie unter [/out (Name der Ausgabedatei)](out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die Eigenschaften Seite **System** .

1. Ändern Sie die **Treiber** Eigenschaft.

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe [VCLinkerTool. Driver-Eigenschaft](/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver).

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
