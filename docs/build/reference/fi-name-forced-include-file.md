---
title: /FI (Name der expliziten Includedatei)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ForcedIncludes
- VC.Project.VCCLCompilerTool.ForcedIncludeFiles
- VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles
helpviewer_keywords:
- FI compiler option [C++]
- -FI compiler option [C++]
- /FI compiler option [C++]
- preprocess header file compiler option [C++]
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
ms.openlocfilehash: 6460f75e2cad81bc1dcc540e3c687de5d0dc0d32
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439804"
---
# <a name="fi-name-forced-include-file"></a>/FI (Name der expliziten Includedatei)

Bewirkt, dass der Präprozessor die angegebene Header Datei verarbeitet.

## <a name="syntax"></a>Syntax

```
/FI[ ]pathname
```

## <a name="remarks"></a>Bemerkungen

Diese Option hat dieselbe Auswirkung wie das Angeben der Datei mit doppelten Anführungszeichen in einer `#include`-Direktive in der ersten Zeile jeder Quelldatei, die in der CL-Umgebungsvariablen oder in einer Befehlsdatei angegeben ist. Wenn Sie mehrere **/fi** -Optionen verwenden, werden die Dateien in der Reihenfolge eingeschlossen, in der Sie von cl verarbeitet werden.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaften Seite **erweitert** .

1. Ändern Sie die Eigenschaft **erzwungene Includedatei** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.

## <a name="see-also"></a>Weitere Informationen

[Ausgabedatei (/F) Optionen](output-file-f-options.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[Festlegen des Pfadnamens](specifying-the-pathname.md)
