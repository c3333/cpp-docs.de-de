---
title: /Fo (Name der Objektdatei)
description: Referenzhandbuch für die Compileroption Microsoft C++ /Fo (Objektdateiname) in Visual Studio.
ms.date: 04/20/2020
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: cd22ba745128fe1df67853d98c1495491b9ca840
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748973"
---
# <a name="fo-object-file-name"></a>/Fo (Name der Objektdatei)

Gibt ein Objekt*`.obj`*( ) Dateiname oder Verzeichnis an, das anstelle des Standardwerts verwendet werden soll.

## <a name="syntax"></a>Syntax

> **`/Fo`**_Pfadnamen_

## <a name="remarks"></a>Bemerkungen

Sie können **`/Fo`** die Compileroption verwenden, um ein Ausgabeverzeichnis für alle vom CL-Compilerbefehl generierten Objektdateien festzulegen. Sie können es auch verwenden, um eine einzelne Objektdatei umzubenennen.

Standardmäßig werden die vom Compiler generierten Objektdateien im aktuellen Verzeichnis abgelegt. Sie erhalten den Basisnamen der Quelldatei *`.obj`* und eine Erweiterung.

Um die **`/Fo`** Option zum Umbenennen einer Objektdatei zu verwenden, geben Sie den Ausgabedateinamen als *pathname-Argument* an. Wenn Sie eine Objektdatei umbenennen, können Sie einen beliebigen Namen und *`.obj`* eine beliebige Erweiterung verwenden, aber die empfohlene Konvention ist die Verwendung von . Der Compiler generiert den Befehlszeilenfehler D8036, wenn Sie einen Dateinamen angeben, wenn **`/Fo`** Sie mehr als eine Quelldatei zum Kompilieren angegeben haben.

Um die **`/Fo`** Option zum Festlegen eines Ausgabeverzeichnisses für alle mit dem CL-Befehl erstellten Objektdateien zu verwenden, geben Sie das Verzeichnis als *Pathname-Argument* an. Ein Verzeichnis wird durch einen nachgestellten Schrägstrich im *Pathname-Argument* angezeigt. Das angegebene Verzeichnis muss vorhanden sein. es wird nicht automatisch erstellt.

## <a name="example"></a>Beispiel

Die folgende Befehlszeile erstellt eine Objektdatei mit dem * \\*Namen *sample.obj* in einem vorhandenen Verzeichnis, intermediate , auf Laufwerk D.

```cmd
CL /Fo"D:\intermediate\" /EHsc /c sample.cpp
```

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Festlegen der Option in Visual Studio oder programmgesteuert

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Eigenschaftenseite **Konfigurationseigenschaften** > **C/C++** > **Ausgabedateien** aus.

1. Ändern Sie die **Object File Name-Eigenschaft,** um das Ausgabeverzeichnis festzulegen. In der IDE muss die Objektdatei *`.obj`* die Erweiterung von haben.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="see-also"></a>Weitere Informationen

[Ausgabedatei (/F) Optionen](output-file-f-options.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[Festlegen des Pfadnamens](specifying-the-pathname.md)
