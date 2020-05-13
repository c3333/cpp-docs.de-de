---
title: /Yc (Datei der vorkompilierten Header erstellen)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
ms.openlocfilehash: 71a05df3adc74edfd814bb6dc15121e4a343dc4d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825755"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Datei der vorkompilierten Header erstellen)

Weist den Compiler an, eine vorkompilierte Header Datei (. pch) zu erstellen, die den Zustand der Kompilierung zu einem bestimmten Zeitpunkt darstellt.

## <a name="syntax"></a>Syntax

> __/Yc__\
> __/Yc__*Dateiname*

## <a name="arguments"></a>Argumente

*Einfügen*<br/>
Gibt eine Header Datei (. h) an. Wenn dieses Argument verwendet wird, kompiliert der Compiler den gesamten Code bis einschließlich der h-Datei.

## <a name="remarks"></a>Bemerkungen

Wenn **/Yc** ohne ein Argument angegeben wird, kompiliert der Compiler den gesamten Code bis zum Ende der Basis Quelldatei oder bis zu dem Punkt in der Basisdatei, an dem eine [hdrend](../../preprocessor/hdrstop.md) -Direktive auftritt. Die resultierende PCH-Datei hat denselben Basis Namen wie die Basis Quelldatei, es sei denn, Sie geben einen anderen Dateinamen mithilfe des **hdrstopps** -Pragmas oder der **/FP** -Option an.

Der vorkompilierte Code wird in einer Datei gespeichert, deren Name aus dem Basis Namen der mit der **/Yc** -Option und der Erweiterung ". pch" angegebenen Datei erstellt wurde. Sie können auch den [/fp (Name) verwenden. PCH-Datei)](fp-name-dot-pch-file.md) , um einen Namen für die vorkompilierte Header Datei anzugeben.

Wenn Sie __/Yc__*filename*verwenden, kompiliert der Compiler den gesamten Code bis einschließlich der angegebenen Datei für die nachfolgende Verwendung mit der [/Yu-Option (Vorkompilierte Header Datei verwenden)](yu-use-precompiled-header-file.md) .

Wenn die Optionen __/Yc__*filename* und __/Yu__*filename* in derselben Befehlszeile und sowohl auf den Verweis als auch auf den gleichen Dateinamen auftreten, hat __/Yc__*filename* Vorrang. Diese Funktion vereinfacht das Schreiben von Makefiles.

Weitere Informationen zu vorkompilierten Headern finden Sie unter:

- [/Y (Vorkompilierte Header)](y-precompiled-headers.md)

- [Vorkompilierte Header Dateien](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Wählen Sie eine CPP-Datei aus. Die CPP-Datei muss die. h-Datei #include, die vorkompilierte Header Informationen enthält. Die **/Yc** -Einstellung des Projekts kann auf Dateiebene überschrieben werden.

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Öffnen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**, **C/C++**, **Vorkompilierte Header** .

1. Ändern Sie die Eigenschaft des **vorkompilierten Headers** .

1. Um den Dateinamen festzulegen, ändern Sie die Eigenschaft der **vorkompilierten Header Datei** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Prüfen Sie <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> und <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a>Beispiel

Betrachten Sie folgenden Code:

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

Wenn dieser Code mit dem-Befehl `CL /YcMYAPP.H PROG.CPP`kompiliert wird, speichert der Compiler die gesamte Vorverarbeitung für "AFXWIN. h", "Resource. h" und "MyApp. h" in einer vorkompilierten Header Datei namens "MyApp. pch".

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[Vorkompilierte Header Dateien](../creating-precompiled-header-files.md)
