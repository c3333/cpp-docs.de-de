---
title: /O-Optionen (Code optimieren)
description: Die MSVC/O-Compileroptionen geben die zu verwendenden Compileroptimierungen an.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: 36ef582787a3ec2d7aee1e589c70b48712d9d552
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180876"
---
# <a name="o-options-optimize-code"></a>`/O`Optionen (Code optimieren)

Die **`/O`** Optionen steuern verschiedene Optimierungen, die Sie beim Erstellen von Code für die maximale Geschwindigkeit oder minimale Größe unterstützen.

- [`/O1`](o1-o2-minimize-size-maximize-speed.md)legt eine Kombination von Optimierungen fest, die einen minimalen Größen Code generieren.

- [`/O2`](o1-o2-minimize-size-maximize-speed.md)legt eine Kombination von Optimierungen fest, mit denen der Code für die maximale Geschwindigkeit optimiert wird.

- [`/Ob`](ob-inline-function-expansion.md)steuert die Inline Funktionserweiterung.

- [`/Od`](od-disable-debug.md)deaktiviert die Optimierung, um die Kompilierung zu beschleunigen und das Debugging zu vereinfachen.

- [`/Og`](og-global-optimizations.md)(veraltet) ermöglicht globale Optimierungen.

- [`/Oi`](oi-generate-intrinsic-functions.md)generiert intrinsische Funktionen für entsprechende Funktionsaufrufe.

- [`/Os`](os-ot-favor-small-code-favor-fast-code.md)weist den Compiler an, Optimierungen für die Größe gegenüber Optimierungen für die Geschwindigkeit zu bevorzugen.

- [`/Ot`](os-ot-favor-small-code-favor-fast-code.md)(eine Standardeinstellung) weist den Compiler an, Optimierungen für Geschwindigkeit gegenüber Optimierungen für die Größe zu bevorzugen.

- [`/Ox`](ox-full-optimization.md)bei handelt es sich um eine Kombination, die mehrere Optimierungen mit einem Schwerpunkt auf Geschwindigkeit auswählt. **`/Ox`** ist eine strikte Teilmenge der **`/O2`** Optimierungen.

- [`/Oy`](oy-frame-pointer-omission.md)unterdrückt die Erstellung von Frame Zeigern in der Aufruf Stapel für schnellere Funktionsaufrufe.

## <a name="remarks"></a>Bemerkungen

Sie können mehrere **`/O`** Optionen in einer einzelnen Options Anweisung kombinieren. Beispielsweise **`/Odi`** ist identisch mit **`/Od /Oi`** . Bestimmte Optionen schließen sich gegenseitig aus und verursachen einen Compilerfehler, wenn Sie gemeinsam verwendet werden. Weitere Informationen finden Sie unter den einzelnen **`/O`** Optionen.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
