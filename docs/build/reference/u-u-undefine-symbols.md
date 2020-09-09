---
title: /U, /u (Symboldefinitionen aufheben)
description: Verwenden Sie die Microsoft C/C++-Compiler/U-und/U-Optionen, um Präprozessorsymbole zu definieren.
ms.date: 09/03/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: 78effabba2fa72e5ab7f2dfc6ef91f22383b063f
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609192"
---
# <a name="u-u-undefine-symbols"></a>/U, /u (Symboldefinitionen aufheben)

Die- **`/U`** Compileroption definiert das angegebene Präprozessorsymbol nicht. Mit der- **`/u`** Compileroption werden die Microsoft-spezifischen Symbole, die der Compiler definiert, nicht definiert.

## <a name="syntax"></a>Syntax

> **`/U`**\[] (*Symbol* )\
> **`/u`**

## <a name="arguments"></a>Argumente

*Tick*<br/>
Das zu definierenden Präprozessorsymbol.

## <a name="remarks"></a>Hinweise

Keines der **`/U`** Optionen und **`/u`** kann die Definition eines Symbols aufheben, das mithilfe der- **`#define`** Direktive erstellt wurde.

Mit der- **`/U`** Option kann ein Symbol, das zuvor mit der-Option definiert wurde, nicht mehr definiert werden **`/D`** .

Standardmäßig kann der Compiler eine große Anzahl von Microsoft-spezifischen Symbolen definieren. Dies sind einige gängige:

| Symbol | Funktion |
|--|--|
| `_CHAR_UNSIGNED` | Der Standard Zeichentyp ist "unsigned". Wird definiert, wenn die [`/J`](j-default-char-type-is-unsigned.md) Option angegeben wird. |
| `_CPPRTTI` | Definiert für Code, der mit der-Option kompiliert wurde [`/GR`](gr-enable-run-time-type-information.md) . |
| `_CPPUNWIND` | Definiert für Code, der mit der-Option kompiliert wurde [`/EHsc`](eh-exception-handling-model.md) . |
| `_DLL` | Wird definiert, wenn die [`/MD`](md-mt-ld-use-run-time-library.md) Option angegeben wird. |
| `_M_IX86` | Standardmäßig auf 600 für x86-Ziele definiert. |
| `_MSC_VER` | Definiert als eindeutiger ganzzahliger Wert für jede Compilerversion. Weitere Informationen finden Sie unter [vordefinierte Makros](../../preprocessor/predefined-macros.md). |
| `_WIN32` | Definiert für Win32-Anwendungen. Immer definiert. |
| `_MT` | Wird definiert, wenn die [`/MD`](md-mt-ld-use-run-time-library.md) [`/MT`](md-mt-ld-use-run-time-library.md) Option oder angegeben wird. |

Eine komplette Liste der Microsoft-spezifischen vordefinierten Makros finden Sie unter [vordefinierte Makros](../../preprocessor/predefined-macros.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**  >  Seite Eigenschaften von**C/C++**  >  **erweitert** aus.

1. Ändern Sie die **Präprozessordefinitionen undefine** , oder deaktivieren Sie alle Eigenschaften der **Präprozessordefinitionen** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> oder <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[**`/J`** (Standardmäßiger char-Typ ist nicht signiert)](j-default-char-type-is-unsigned.md)<br/>
[**`/GR`** (Lauf Zeittyp Informationen aktivieren)](gr-enable-run-time-type-information.md)<br/>
[**`/EH`** (Ausnahme Behandlungsmodell)](eh-exception-handling-model.md)<br/>
[**`/MD`**, **`/MT`** , **`/LD`** (Lauf Zeit Bibliothek verwenden)](md-mt-ld-use-run-time-library.md)
