---
title: /C (Kommentare bei der Vorverarbeitung beibehalten)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: f80ebf45dd396a3f92d9b755c56522d4731bb2d0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440278"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Kommentare bei der Vorverarbeitung beibehalten)

Behält Kommentare beim Präprozessorlauf bei

## <a name="syntax"></a>Syntax

```
/C
```

## <a name="remarks"></a>Bemerkungen

Diese Compileroption erfordert die Option **/E**, **/P**oder **/EP** .

Im folgenden Codebeispiel wird der Quell Code Kommentar angezeigt.

```cpp
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

In diesem Beispiel wird die folgende Ausgabe erzeugt.

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaften Seite **Präprozessor** .

1. Ändern Sie die Eigenschaft **Kommentare beibehalten** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[/E (In StdOut vorverarbeiten)](e-preprocess-to-stdout.md)<br/>
[/P (In einer Datei vorverarbeiten)](p-preprocess-to-a-file.md)<br/>
[/EP (In StdOut ohne #line-Anweisungen vorverarbeiten)](ep-preprocess-to-stdout-without-hash-line-directives.md)
