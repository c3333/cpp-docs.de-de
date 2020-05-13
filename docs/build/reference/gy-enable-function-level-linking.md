---
title: /Gy (Funktionslevel-Linking aktivieren)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 8724ae4d018948c0f6aa9456f229db96878d7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328282"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Funktionslevel-Linking aktivieren)

Ermöglicht dem Compiler, einzelne Funktionen in Form von kompilierten Funktionen (COMDATs) zu kompilieren.

## <a name="syntax"></a>Syntax

```
/Gy[-]
```

## <a name="remarks"></a>Bemerkungen

Der Linker erfordert, dass Funktionen separat als COMDATs verpackt werden, um einzelne Funktionen in einer DLL- oder EXE-Datei auszuschließen oder zu bestellen.

Sie können die Linkeroption [/OPT (Optimierungen)](opt-optimizations.md) verwenden, um nicht referenzierte paketierte Funktionen aus der EXE-Datei auszuschließen.

Sie können die Linker-Option [/ORDER (Put Functions in Order)](order-put-functions-in-order.md) verwenden, um verpackte Funktionen in einer angegebenen Reihenfolge in die EXE-Datei aufzunehmen.

Inline-Funktionen werden immer verpackt, wenn sie als Aufrufe instanziiert werden (was z. B. auftritt, wenn das Inlining deaktiviert ist oder Sie eine Funktionsadresse verwenden). Darüber hinaus werden in der Klassendeklaration definierte C++-Memberfunktionen automatisch gepackt. andere Funktionen sind es nicht, und wenn Sie diese Option auswählen, müssen Sie sie als paketierte Funktionen kompilieren.

> [!NOTE]
> Die Option [/ZI,](z7-zi-zi-debug-information-format.md) die für Bearbeiten und Fortfahren verwendet wird, legt automatisch die Option **/Gy** fest.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaftenseite **Codegenerierung.**

1. Ändern Sie die **Funktionsverknüpfungseigenschaft "Funktionsebene aktivieren".**

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
