---
title: /O1, /O2 (Größe minimieren, Geschwindigkeit maximieren)
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: 3daf5dd5f9912194fd5d8aaeb4c7a312be142b69
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825343"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Größe minimieren, Geschwindigkeit maximieren)

Wählt einen vordefinierten Satz von Optionen aus, der sich auf die Größe und Geschwindigkeit des generierten Codes auswirkt.

## <a name="syntax"></a>Syntax

> O1
> /O2

## <a name="remarks"></a>Bemerkungen

Die **/O1** -und **/O2** -Compileroptionen sind eine schnelle Möglichkeit, mehrere spezifische Optimierungs Optionen gleichzeitig festzulegen. Die Option **/O1** legt die einzelnen Optimierungs Optionen fest, mit denen der kleinste Code in den meisten Fällen erstellt wird. Die Option **/O2** legt die Optionen fest, mit denen der schnellste Code in den meisten Fällen erstellt wird. Die **/O2** -Option ist die Standardeinstellung für Releasebuilds. Diese Tabelle zeigt die spezifischen Optionen an, die von **/O1** und **/O2**festgelegt werden:

|Option|Entspricht|
|------------|-------------------|
|**/O1** (Größe minimieren)|[/Og](og-global-optimizations.md) [/OS](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|
|**/O2** (Geschwindigkeit maximieren)|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/OT](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|

**/O1** und **/O2** schließen sich gegenseitig aus.

> [!NOTE]
> **x86-spezifisch**\
> Diese Optionen implizieren die Verwendung der Option Frame Zeiger ausgelassen ([/Oy](oy-frame-pointer-omission.md)).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Öffnen Sie unter **Konfigurations Eigenschaften**die Option **C/C++** , und wählen Sie dann die Eigenschaften Seite **Optimierung** aus.

1. Ändern Sie die Eigenschaft **Optimierung** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Weitere Informationen

[/O-Optionen (Code optimieren)](o-options-optimize-code.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[/EH (Ausnahmebehandlungsmodell)](eh-exception-handling-model.md)
