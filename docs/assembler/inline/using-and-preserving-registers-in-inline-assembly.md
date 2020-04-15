---
title: Verwenden und Beibehalten von Registern in der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 97db09ac7652c00e9599a6938f4114de080906c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318025"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Verwenden und Beibehalten von Registern in der Inlineassembly

**Microsoft Specific**

Im Allgemeinen sollten Sie nicht davon ausgehen, dass `__asm` ein Register einen bestimmten Wert hat, wenn ein Block beginnt. Registerwerte werden nicht garantiert über `__asm` separate Blöcke hinweg beibehalten. Wenn Sie einen Block von Inlinecode beenden und einen anderen blockieren, können Sie sich nicht darauf verlassen, dass die Register im zweiten Block ihre Werte aus dem ersten Block beibehalten. Ein `__asm` Block erbt, was auch immer Registerwerte aus dem normalen Kontrollfluss resultieren.

Wenn Sie `__fastcall` die aufrufende Konvention verwenden, übergibt der Compiler Funktionsargumente in Registern statt auf dem Stapel. Dies kann Zufall `__asm` von Problemen in Funktionen mit Blöcken, da eine Funktion keine Möglichkeit hat, zu sagen, welcher Parameter sich in welchem Register befindet. Wenn die Funktion zufällig einen Parameter in EAX empfängt und sofort etwas anderes in EAX speichert, geht der ursprüngliche Parameter verloren. Darüber hinaus müssen Sie das ECX-Register `__fastcall`in jeder Funktion beibehalten, die mit deklariert ist.

Um solche Registerkonflikte zu vermeiden, `__fastcall` verwenden Sie die `__asm` Konvention nicht für Funktionen, die einen Block enthalten. Wenn Sie `__fastcall` die Konvention global mit der Compileroption /Gr `__asm` angeben, deklarieren Sie jede Funktion, die einen Block mit `__cdecl` oder `__stdcall`enthält. (Das `__cdecl` Attribut weist den Compiler an, die C-Aufrufkonvention für diese Funktion zu verwenden.) Wenn Sie nicht mit /Gr kompilieren, vermeiden `__fastcall` Sie es, die Funktion mit dem Attribut zu deklarieren.

Wenn `__asm` Sie Assemblysprache in C/C++-Funktionen schreiben, müssen Sie die EAX-, EBX-, ECX-, EDX-, ESI- oder EDI-Register nicht beibehalten. Zum Beispiel im POWER2. C Beispiel in [Writing Functions with Inline Assembly](../../assembler/inline/writing-functions-with-inline-assembly.md), die `power2` Funktion behält den Wert im EAX-Register nicht bei. Die Verwendung dieser Register wirkt sich jedoch auf die Codequalität aus, `__asm` da der Registerallokator sie nicht zum Speichern von Werten über Blöcke hinweg verwenden kann. Darüber hinaus erzwingen Sie durch die Verwendung von EBX, ESI oder EDI im Inline-Assemblycode, dass der Compiler diese Register im Funktionsprolog und Epilog speichert und wiederherstellt.

Sie sollten andere Register beibehalten, die Sie für den Bereich des `__asm` Blocks verwenden (z. B. DS-, SS-, SP-, BP- und Flags-Register). Sie sollten die ESP- und EBP-Register beibehalten, es sei denn, Sie haben einen Grund, sie zu ändern (z. B. um Stacks zu wechseln). Siehe Optimierung [der Inline-Baugruppe](../../assembler/inline/optimizing-inline-assembly.md).

Einige SSE-Typen erfordern eine achtbyte Stapelausrichtung, wodurch der Compiler dynamischen Stapelausrichtungscode ausgibt. Um nach der Ausrichtung sowohl auf die lokalen Variablen als auch auf die Funktionsparameter zugreifen zu können, behält der Compiler zwei Framezeiger bei.  Wenn der Compiler Frame Pointer-Auslassung (FPO) ausführt, verwendet er EBP und ESP.  Wenn der Compiler FPO nicht ausführt, verwendet er EBX und EBP. Um sicherzustellen, dass Code ordnungsgemäß ausgeführt wird, ändern Sie EBX nicht im asm-Code, wenn die Funktion eine dynamische Stapelausrichtung erfordert, da sie den Framezeiger ändern könnte. Verschieben Sie entweder die acht Byte ausgerichteten Typen aus der Funktion, oder vermeiden Sie die Verwendung von EBX.

> [!NOTE]
> Wenn der Inline-Baugruppencode das Richtungsflag mithilfe der STD- oder CLD-Anweisungen ändert, müssen Sie das Flag auf den ursprünglichen Wert zurückführen.

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[Inlineassembler](../../assembler/inline/inline-assembler.md)<br/>
