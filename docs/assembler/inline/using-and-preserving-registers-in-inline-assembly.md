---
title: Verwenden und Beibehalten von Registern in der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 99ca0093bb27e859854dfd1ca64addea923e5a5c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191507"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Verwenden und Beibehalten von Registern in der Inlineassembly

**Microsoft-spezifisch**

Im Allgemeinen sollten Sie nicht davon ausgehen, dass ein Register über einen angegebenen Wert verfügt, wenn ein **`__asm`** Block beginnt. Es ist nicht garantiert, dass Register Werte über separate Blöcke hinweg beibehalten werden **`__asm`** . Wenn Sie einen Block von Inline Code beenden und einen anderen starten, können Sie sich nicht darauf verlassen, dass die Register im zweiten Block ihre Werte aus dem ersten Block behalten. Ein- **`__asm`** Block erbt alle Registerwerte, die sich aus dem normalen Ablauf Steuerungs Ergebnis ergeben.

Wenn Sie die **`__fastcall`** Aufruf Konvention verwenden, übergibt der Compiler Funktionsargumente in Registern anstelle von im Stapel. Dadurch können Probleme in Funktionen mit Blöcken erstellt werden **`__asm`** , da eine Funktion nicht über die Möglichkeit verfügt, den Parameter zu ermitteln, in dem sich die Registrierung befindet. Wenn die Funktion einen Parameter in EAX empfängt und sofort etwas anderes in EAX speichert, geht der ursprüngliche Parameter verloren. Außerdem müssen Sie das ECX-Register in jeder mit deklarierten Funktion beibehalten **`__fastcall`** .

Um solche Registrierungs Konflikte zu vermeiden, verwenden Sie die- **`__fastcall`** Konvention nicht für Funktionen, die einen- **`__asm`** Block enthalten. Wenn Sie die **`__fastcall`** Konvention Global mit der/GR-Compileroption angeben, deklarieren Sie jede Funktion, die einen-Block enthält, **`__asm`** mit **`__cdecl`** oder **`__stdcall`** . (Das- **`__cdecl`** Attribut weist den Compiler an, die C-Aufruf Konvention für diese Funktion zu verwenden.) Wenn Sie nicht mit/GR kompilieren, sollten Sie die Funktion nicht mit dem-Attribut deklarieren **`__fastcall`** .

Wenn **`__asm`** Sie verwenden, um Assemblysprache in C/C++-Funktionen zu schreiben, müssen Sie die Register eax, EBX, ecx, EDX, ESI oder EDI nicht beibehalten. Beispielsweise im power2. C Beispiel beim [Schreiben von Funktionen mit der Inlineassembly](../../assembler/inline/writing-functions-with-inline-assembly.md) `power2` behält die Funktion den Wert im EAX-Register nicht bei. Die Verwendung dieser Register wirkt sich jedoch auf die Codequalität aus, da Sie von der Register Zuweisung nicht zum Zwischenspeichern von Werten verwendet werden kann **`__asm`** . Außerdem erzwingen Sie mithilfe von EBX, ESI oder EDI im Inline-Assemblycode, dass der Compiler diese Register im Funktions Prolog und Epilog speichert und wiederherstellt.

Sie sollten die anderen von Ihnen verwendeten Register (z. b. DS, SS, SP, BP und Flags-Register) für den Bereich des **`__asm`** Blocks beibehalten. Sie sollten die ESP-und EBP-Register beibehalten, es sei denn, Sie haben einen Grund, Sie zu ändern (z. b. zum Wechseln von Stapeln). Siehe auch [Optimieren der Inlineassembly](../../assembler/inline/optimizing-inline-assembly.md).

Einige SSE-Typen erfordern eine 8-Byte-Stapel Ausrichtung, wodurch der Compiler gezwungen wird, dynamischen Stapel Ausrichtungs Code auszugeben. Um auf die lokalen Variablen und die Funktionsparameter nach der Ausrichtung zugreifen zu können, verwaltet der Compiler zwei Frame Zeiger.  Wenn der Compiler die Frame Zeiger Auslassung (FPO) ausführt, werden EBP und ESP verwendet.  Wenn der Compiler keine voll qualifizierte Funktion ausführt, werden EBX und EBP verwendet. Um sicherzustellen, dass der Code ordnungsgemäß ausgeführt wird, ändern Sie EBX nicht im ASM-Code, wenn die Funktion eine dynamische Stapel Ausrichtung erfordert, da Sie den Frame Zeiger ändern könnte. Verschieben Sie die mit acht Bytes ausgerichteten Typen aus der Funktion, oder vermeiden Sie die Verwendung von ebx.

> [!NOTE]
> Wenn der Inline-Assemblycode das richtungsflag mithilfe der Std-oder CLD-Anweisungen ändert, müssen Sie das Flag auf seinen ursprünglichen Wert zurücksetzen.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Inline Assembler](../../assembler/inline/inline-assembler.md)<br/>
