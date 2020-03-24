---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: a100ece1a0c67be01b31f38bdca17e78c2e1b6f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179106"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

Der Einschränkungsspezifizierer kann auf Funktions- und Lambda-Deklarationen angewendet werden. Er erzwingt Einschränkungen für den Code in der Funktion und das Verhalten der Funktion in Anwendungen, die C++ Accelerated Massive Parallelism(C++ AMP)-Laufzeit verwenden.

> [!NOTE]
>  Informationen zum **Einschränkungs** Schlüsselwort, das Bestandteil der **__declspec** -Speicher Klassenattribute ist, finden Sie unter [einschränken](../cpp/restrict.md).

Die **Einschränkungs** Klausel hat die folgenden Formen:

|Klausel|BESCHREIBUNG|
|------------|-----------------|
|`restrict(cpu)`|Die Funktion kann die vollständige C++-Programmiersprache verwenden. Es können nur andere Funktionen, die durch die Verwendung von restrict(cpu)-Funktionen deklariert werden, die Funktion aufrufen.|
|`restrict(amp)`|Die Funktion kann nur die Teilmenge der Programmiersprache C++ verwenden, die mit C++ AMP beschleunigt werden kann.|
|Eine Sequenz von `restrict(cpu)` und `restrict(amp)`.|Die Funktion muss den Einschränkungen von `restrict(cpu)` und `restrict(amp)` folgen. Die Funktion kann von Funktionen aufgerufen werden, die durch die Verwendung von `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` oder `restrict(amp, cpu)` deklariert werden.<br /><br /> Das Formular `restrict(A) restrict(B)` kann als `restrict(A,B)` geschrieben werden.|

## <a name="remarks"></a>Bemerkungen

Das **Einschränkungs** Schlüsselwort ist ein Kontext Schlüsselwort Die Einschränkungsspezifizierer, `cpu` und `amp` sind keine reservierten Wörter. Die Liste der Spezifizierer ist nicht erweiterbar. Eine Funktion, die nicht über eine **Einschränkungs** Klausel verfügt, ist identisch mit einer Funktion, die über die `restrict(cpu)`-Klausel verfügt.

Eine Funktion, die über die `restrict(amp)`-Klausel verfügt, hat folgende Einschränkungen:

- Die Funktion kann nur Funktionen aufrufen, die die `restrict(amp)`-Klausel enthalten.

- Die Funktion muss inlinable sein.

- Die Funktion kann nur die Variablen " **int**", " **Ganzzahl ohne Vorzeichen int**", " **float**" und " **Double** " sowie Klassen und Strukturen deklarieren, die nur diese Typen enthalten. **boolescher** Wert ist ebenfalls zulässig, muss jedoch 4-Byte-ausgerichtet sein, wenn Sie ihn in einem Verbund-Typ verwenden.

- Lambda-Funktionen können nicht als Verweis erfassten und können keine Zeiger erfassen.

- Verweise und Einzeldereferenzierungszeiger werden nur als lokale Variablen, Funktionsargumente und Rückgabetypen unterstützt.

- Folgendes ist nicht zulässig:

   - Rekursion.

   - Mit dem [volatile](../cpp/volatile-cpp.md) -Schlüsselwort deklarierte Variablen.

   - Virtuelle Funktionen.

   - Zeiger auf Funktionen.

   - Zeiger auf die Memberfunktionen.

   - Zeiger in Strukturen.

   - Zeiger auf Zeiger.

   - **goto** -Anweisungen.

   - Anweisungen mit Bezeichnung.

   - **try**-, **catch**-oder **throw** -Anweisungen.

   - Globale Variablen.

   - Statische Variablen. Verwenden Sie stattdessen [tile_static-Schlüsselwort](../cpp/tile-static-keyword.md) .

   - **dynamic_cast** Umwandlungen.

   - Der **typeid** -Operator.

   - ASM-Deklarationen.

   - Varargs.

Eine Erläuterung der Funktionseinschränkungen finden Sie unter [Einschränkungen für Einschränkungen (amp)](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie die `restrict(amp)`-Klausel verwendet wird.

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>Weitere Informationen

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
