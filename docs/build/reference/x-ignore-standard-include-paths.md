---
title: /X (Standardincludepfade ignorieren)
ms.date: 07/31/2020
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 652feeb200b7106aaca1ed7264f1e25c088a3dab
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520407"
---
# <a name="x-ignore-standard-include-paths"></a>`/X`(Standardincludepfade ignorieren)

Verhindert, dass der Compiler in Verzeichnissen, die in den path-und INCLUDE-Umgebungsvariablen angegeben sind, nach Includedateien sucht.

## <a name="syntax"></a>Syntax

> **`/X`**

## <a name="remarks"></a>Bemerkungen

Sie können diese Option mit der Option [ `/I` (Zusätzliche Includeverzeichnisse)](i-additional-include-directories.md) verwenden, um einen alternativen Pfad zu den standardmäßigen Includedateien anzugeben.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Präprozessor** aus.

1. Ändern Sie die Eigenschaft **Standardincludepfad ignorieren** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Beispiel

Im folgenden Befehl **`/X`** weist den Compiler an, die durch den Pfad und INCLUDE-Umgebungsvariablen angegebenen Speicherorte zu ignorieren, und **`/I`** gibt das Verzeichnis an, in dem nach Includedateien gesucht werden soll:

```cmd
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
