---
title: Argumentübergabe und Benennungskonventionen
ms.date: 12/17/2018
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
ms.openlocfilehash: e621db339102f1f40030bc7826d383d306a39be8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190767"
---
# <a name="argument-passing-and-naming-conventions"></a>Argumentübergabe und Benennungskonventionen

**Microsoft-spezifisch**

Die Microsoft C++ -Compiler ermöglichen das Angeben von Konventionen zum Übergeben von Argumenten und Rückgabe Werten zwischen Funktionen und Aufrufern. Nicht alle Konventionen sind auf allen unterstützten Plattformen verfügbar, und einige Konventionen verwenden plattformspezifische Implementierungen. In den meisten Fällen werden Schlüsselwörter oder Compilerschalter, die eine nicht unterstützte Konvention auf einer bestimmten Plattform angeben, ignoriert und die Plattformstandardkonvention wird verwendet.

Auf x86-Plattformen werden alle Argumente bei Übergabe auf 32 Bits erweitert. Rückgabewerte werden ebenfalls auf 32 Bit erweitert und im EAX-Register zurückgegeben. Eine Ausnahme bilden 8-Byte-Strukturen, die im EDX:EAX-Registerpaar zurückgegeben werden. Größere Strukturen werden im EAX-Register als Zeiger auf ausgeblendete Rückgabestrukturen zurückgegeben. Parameter werden auf von rechts nach links auf den Stapel verschoben. Strukturen, die keine PODs sind, werden nicht in Registern zurückgegeben.

Vom Compiler wird Prolog- und Epilogcode zum Speichern und Wiederherstellen von ESI-, EDI-, EBX- sowie EBP-Registern verwendet, sofern sie in der Funktion verwendet werden.

> [!NOTE]
> Wenn eine Struktur, Union oder Klasse nach Wert aus einer Funktion zurückgegeben wird, müssen alle Definitionen des Typs identisch sein, andernfalls können zur Laufzeit Fehler im Programm auftreten.

Informationen dazu, wie Sie Ihren eigenen Funktions Prolog und Epilogcode definieren, finden Sie unter [Naked-Funktionsaufrufe](../cpp/naked-function-calls.md).

Informationen zu den Standard Aufruf Konventionen in Code, der x64-Plattformen als Ziel hat, finden Sie unter [x64-Aufruf Konvention](../build/x64-calling-convention.md). Informationen zu den Aufrufen von Konventionen in Bezug auf Arm-Plattformen finden Sie unter [häufige Probleme bei der Migration von Visual C++ Arm](../build/common-visual-cpp-arm-migration-issues.md)

Die folgenden Aufrufkonventionen werden vom Visual C/C++-Compiler unterstützt.

|Schlüsselwort|Stapelcleanup|Parameterübergabe|
|-------------|-------------------|-----------------------|
|[__cdecl](../cpp/cdecl.md)|Caller|Schiebt Parameter in umgekehrter Reihenfolge (von rechts nach links) auf den Stapel|
|[__clrcall](../cpp/clrcall.md)|–|Parameter der Reihe nach (von links nach rechts) auf den CLR-Ausdrucksstapel laden.|
|[__stdcall](../cpp/stdcall.md)|Aufgerufener|Schiebt Parameter in umgekehrter Reihenfolge (von rechts nach links) auf den Stapel|
|[__fastcall](../cpp/fastcall.md)|Aufgerufener|Wird in Registern gespeichert und dann auf dem Stapel abgelegt|
|[__thiscall](../cpp/thiscall.md)|Aufgerufener|Auf Stapel verschoben; **dieser** Zeiger wird in ECX gespeichert.|
|[__vectorcall](../cpp/vectorcall.md)|Aufgerufener|Wird in Registern gespeichert und anschließend in umgekehrter Reihenfolge auf dem Stapel abgelegt (rechts nach links)|

Weitere Informationen finden Sie unter [Veraltete Aufruf Konventionen](../cpp/obsolete-calling-conventions.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Aufrufkonventionen](../cpp/calling-conventions.md)
