---
title: Intrinsische Compilerfunktionen
ms.date: 09/02/2019
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 7438c90eec8b1f88a4c1608953ce21772254f02c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230531"
---
# <a name="compiler-intrinsics"></a>Intrinsische Compilerfunktionen

Die meisten Funktionen sind in Bibliotheken enthalten, aber einige Funktionen sind in den Compiler integriert (das heißt, sie sind systemintern). Diese werden als intrinsische Funktionen bezeichnet.

## <a name="remarks"></a>Bemerkungen

Wenn eine Funktion systemintern ist, wird der Code für diese Funktion normalerweise inline eingefügt, damit wird der Mehraufwand eines Funktionsaufrufs vermieden und es können äußerst effiziente Computerbefehle für diese Funktion ausgegeben werden. Eine systeminterne Funktion ist häufig schneller als die entsprechende Inlineassembly, da der Optimierer über integriertes Wissen über das Verhalten vieler systeminterner Funktionen verfügt, sodass einige Optimierungen verfügbar sein können, die bei Verwendung von Inlineassemblys nicht verfügbar sind. Außerdem kann der Optimierer die systeminterne Funktion anders erweitern, Puffer anders ausrichten oder je nach Kontext und den Argumenten des Aufrufs andere Anpassungen vornehmen.

Die Verwendung systeminterner Funktionen beeinflusst die Portabilität des Codes, da die in Visual C++ verfügbaren systeminternen Funktionen möglicherweise nicht zur Verfügung stehen, wenn der Code mit anderen Compilern und einigen systeminternen Funktionen kompiliert wird, die möglicherweise für einige aber nicht für alle Zielarchitekturen verfügbar sind. Allerdings sind systeminterne Funktionen in der Regel besser portierbar als Inlineassemblys. Systeminternen Funktionen sind auf 64-Bit-Architekturen erforderlich, auf denen Inlineassemblys nicht unterstützt werden.

Einige systeminterne Funktionen, wie z. b. **`__assume`** und `__ReadWriteBarrier` , stellen dem Compiler Informationen zur Verfügung, die sich auf das Verhalten des Optimierers auswirken.

Einige systeminterne Funktionen sind nur als systeminterne Funktionen verfügbar, und einige sind sowohl in Funktionsimplementierungen als auch in systeminternen Implementierungen verfügbar. Sie können den Compiler anweisen, die systeminterne Implementierung auf einer von zwei Arten zu verwenden, je nach dem, ob Sie nur bestimmte Funktionen aktivieren möchten, oder ob Sie alle systeminternen Funktionen aktivieren möchten. Die erste Möglichkeit ist die Verwendung von " `#pragma intrinsic(` *intrinsischer Funktionsname-List*" `)` . Das Pragma kann verwendet werden, um eine einzelne systeminterne Funktion oder mehrere durch Trennzeichen getrennte systeminterne Funktionen angeben. Die zweite Möglichkeit besteht darin, die Compileroption [/Oi (systeminterne Funktionen generieren)](../build/reference/oi-generate-intrinsic-functions.md) zu verwenden, die alle systeminternen Funktionen auf einer bestimmten Plattform verfügbar macht. Verwenden **/Oi**Sie unter/Oi `#pragma function(` die *Funktion intrinsische Funktion-Name-List* `)` , um die Verwendung eines Funktions Aufrufes anstelle einer systeminternen Funktion zu erzwingen. Wenn in der Dokumentation für eine bestimmte systeminterne Funktion festgestellt wird, dass die Routine nur als systeminterne Funktion verfügbar ist, wird die systeminterne Implementierung unabhängig davon verwendet, ob **/Oi** oder `#pragma intrinsic` angegeben ist. In allen Fällen wird der Optimierer, der die systeminterne Funktion verwendet, durch **/Oi** oder `#pragma intrinsic` erlaubt, aber nicht erzwungen. Die Funktion kann vom Optimierer noch immer aufgerufen werden.

Einige C bzw. C++-Standardbibliotheksfunktionen sind in den systeminternen Implementierungen einiger Architekturen verfügbar. Wenn eine CRT-Funktion aufgerufen wird, wird die systeminterne Implementierung verwendet, wenn **/Oi** in der Befehlszeile angegeben wird.

Eine Header Datei, \<intrin.h> , ist verfügbar, die Prototypen für die allgemeinen intrinsischen Funktionen deklariert. Herstellerspezifische systeminterne Funktionen sind in den \<immintrin.h> -und- \<ammintrin.h> Header Dateien verfügbar. Außerdem deklarieren bestimmte Windows-Header Funktionen, die auf eine systeminterne Compilerfunktion zuordnen.

In den folgenden Abschnitten werden alle systeminternen Funktionen aufgeführt, die auf verschiedenen Architekturen verfügbar sind. Weitere Informationen zu der Funktionsweise systeminterner Funktionen auf dem bestimmten Zielprozessor finden Sie in der Referenzdokumentation des Herstellers.

- [Intrinsische ARM-Funktionen](../intrinsics/arm-intrinsics.md)

- [Intrinsische ARM64-Funktionen](../intrinsics/arm64-intrinsics.md)

- [Liste der intrinsischen Funktionen für x86](../intrinsics/x86-intrinsics-list.md)

- [Liste der intrinsischen Funktionen für x64 (amd64)](../intrinsics/x64-amd64-intrinsics-list.md)

- [Intrinsische Funktionen für alle Architekturen](../intrinsics/intrinsics-available-on-all-architectures.md)

- [Alphabetische Liste der intrinsischen Funktionen](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>Weitere Informationen

[Arm-Assembler-Verweis](../assembler/arm/arm-assembler-reference.md)<br/>
[Microsoft Macro Assembler-Referenz](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[C-Lauf Zeit Bibliotheks Referenz](../c-runtime-library/c-run-time-library-reference.md)
