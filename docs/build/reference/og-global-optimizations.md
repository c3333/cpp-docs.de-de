---
title: /Og (Globale Optimierungen)
description: Beschreibt die veraltete MSVC-Compileroption/og, die zuvor zum Aktivieren von globalen Optimierungen verwendet wurde.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: c1cab53ccb391bd7d6ca7660e2750f53aa7c72e4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180850"
---
# <a name="og-global-optimizations"></a>`/Og`(Globale Optimierungen)

Veraltet. Bietet lokale und globale Optimierungen, automatische Register Zuordnung und Schleifen Optimierung. Es wird empfohlen, stattdessen entweder [ `/O1` (Minimieren der Größe)](o1-o2-minimize-size-maximize-speed.md) oder [ `/O2` (Geschwindigkeit der Geschwindigkeit)](o1-o2-minimize-size-maximize-speed.md) zu verwenden.

## <a name="syntax"></a>Syntax

> **`/Og`**

## <a name="remarks"></a>Bemerkungen

**`/Og`** ist veraltet. Diese Optimierungen sind jetzt standardmäßig aktiviert, wenn Optimierungen aktiviert sind. Weitere Informationen zu Optimierungen finden Sie unter [ `/O1` , `/O2` (Minimieren der Größe, Maximieren der Geschwindigkeit)](o1-o2-minimize-size-maximize-speed.md)oder [ `/Ox` (aktivieren Sie die meisten Geschwindigkeits Optimierungen)](ox-full-optimization.md).

Die folgenden Optimierungen sind unter verfügbar **`/Og`** :

- Lokale und globale allgemeine Teil Ausdrucks Löschung

   In dieser Optimierung wird der Wert eines gemeinsamen Teil Ausdrucks einmal berechnet. Wenn sich die Werte von `b` und `c` zwischen den drei Ausdrücken nicht ändern, kann der Compiler im folgenden Beispiel die Berechnung von `b + c` einer temporären Variablen zuweisen und diese Variable für Folgendes verwenden `b + c` :

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   Für die lokale allgemeine Teil Ausdrucks Optimierung prüft der Compiler kurze Code Abschnitte für allgemeine Teil Ausdrücke. Bei der globalen allgemeinen Teil Ausdrucks Optimierung durchsucht der Compiler ganze Funktionen nach allgemeinen Teil Ausdrücken.

- Automatische Register Zuordnung

   Diese Optimierung ermöglicht es dem Compiler, häufig verwendete Variablen und Teil Ausdrücke in Registern zu speichern. Das `register` Schlüsselwort wird ignoriert.

- Schleifen Optimierung

   Diese Optimierung entfernt invariante Teil Ausdrücke aus dem Text einer-Schleife. Eine optimale Schleife enthält nur Ausdrücke, deren Werte sich durch jede Ausführung der Schleife ändern. Im folgenden Beispiel ändert sich der Ausdruck `x + y` nicht im Schleifen Text:

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   Nach der Optimierung `x + y` wird einmal berechnet, anstatt jedes Mal, wenn die Schleife ausgeführt wird:

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   Die Schleifen Optimierung ist viel effektiver, wenn der Compiler keine Aliasing annehmen kann, die Sie mit [`__restrict`](../../cpp/extension-restrict.md) , [`noalias`](../../cpp/noalias.md) oder festlegen [`restrict`](../../cpp/restrict.md) .

   > [!NOTE]
   > Sie können die globale Optimierung auf Funktionsweise aktivieren oder deaktivieren, indem Sie das- `optimize` pragma mit der- `g` Option verwenden.

Weitere Informationen finden Sie unter [ `/Oi` (generieren Sie intrinsische Funktionen)](oi-generate-intrinsic-functions.md) und [ `/Ox ` (aktivieren Sie die meisten Geschwindigkeits Optimierungen)](ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Geben Sie die Compileroption im Feld **zusätzliche Optionen** ein.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
