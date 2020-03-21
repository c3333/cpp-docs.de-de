---
title: /FORCE (Dateiausgabe erzwingen)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: d1d85174290faa95e73c63a25f7d80c554e83ace
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079632"
---
# <a name="force-force-file-output"></a>/FORCE (Dateiausgabe erzwingen)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>Bemerkungen

Die/Force-Option weist den Linker an, eine gültige exe-Datei oder dll zu erstellen, auch wenn auf ein Symbol verwiesen wird, aber nicht definiert oder multipliziert definiert ist.

Die/Force-Option kann ein optionales Argument annehmen:

- Verwenden Sie/Force: Multiple, um eine Ausgabedatei zu erstellen, unabhängig davon, ob Link mehr als eine Definition für ein Symbol findet oder nicht.

- Verwenden Sie/Force: nicht aufgelöst, um eine Ausgabedatei zu erstellen, unabhängig davon, ob Link ein nicht definiertes Symbol findet /Force: nicht aufgelöste wird ignoriert, wenn das Einstiegspunkt Symbol nicht aufgelöst wird.

/Force ohne Argumente impliziert sowohl mehrfach als auch nicht aufgelöst.

Eine mit dieser Option erstellte Datei kann möglicherweise nicht wie erwartet ausgeführt werden. Der Linker wird nicht inkrementell verknüpft, wenn die/Force-Option angegeben wird.

Wenn ein Modul mit **/CLR**kompiliert wird, erstellt **/Force** kein Image.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus.

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die Eigenschaftenseite **Befehlszeile** .

1. Geben Sie die Option im Feld **zusätzliche Optionen** ein.

Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
