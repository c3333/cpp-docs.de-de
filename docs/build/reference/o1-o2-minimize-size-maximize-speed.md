---
title: /O1, /O2 (Größe minimieren, Geschwindigkeit maximieren)
description: Die MSVC-Compileroptionen/O1 und/O2 geben alle Optimierungen für minimale Größe oder maximale Geschwindigkeit an.
ms.date: 07/08/2020
f1_keywords:
- /O2
- /O1
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
ms.openlocfilehash: c1eda8395e604468cbb23572ec930d6171984fe4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180902"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>`/O1`, `/O2` (Größe minimieren, Geschwindigkeit maximieren)

Wählt einen vordefinierten Satz von Optionen aus, der sich auf die Größe und Geschwindigkeit des generierten Codes auswirkt.

## <a name="syntax"></a>Syntax

> **`/O1`**\
> **`/O2`**

## <a name="remarks"></a>Bemerkungen

Die **`/O1`** **`/O2`** Compileroptionen und sind eine schnelle Möglichkeit, mehrere spezifische Optimierungs Optionen gleichzeitig festzulegen. Mit der- **`/O1`** Option werden die einzelnen Optimierungs Optionen festgelegt, mit denen der kleinste Code in den meisten Fällen erstellt wird. Mit der- **`/O2`** Option werden die Optionen festgelegt, die den schnellsten Code in den meisten Fällen erstellen. Die **`/O2`** Option ist die Standardeinstellung für Releasebuilds. Diese Tabelle zeigt die spezifischen Optionen an, die von und festgelegt werden **`/O1`** **`/O2`** :

| Option | Entspricht |
|--|--|
| **`/O1`**(Größe minimieren) | [`/Og`](og-global-optimizations.md) [`/Os`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |
| **`/O2`**(Geschwindigkeit maximieren) | [`/Og`](og-global-optimizations.md) [`/Oi`](oi-generate-intrinsic-functions.md) [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |

**`/O1`** und **`/O2`** schließen sich gegenseitig aus.

> [!NOTE]
> **x86-spezifisch**\
> Diese Optionen implizieren die Verwendung der Option Frame Zeiger ausgelassen ( [`/Oy`](oy-frame-pointer-omission.md) ).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Optimierung** aus.

1. Ändern Sie die Eigenschaft **Optimierung** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Weitere Informationen

[`/O`Optionen (Code optimieren)](o-options-optimize-code.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[`/EH`(Ausnahme Behandlungsmodell)](eh-exception-handling-model.md)
