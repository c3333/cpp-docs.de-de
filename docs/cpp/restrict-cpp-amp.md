---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 31db9e8c6f18879e65596593c10a8b3413c5cea9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213267"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

Der Einschränkungsspezifizierer kann auf Funktions- und Lambda-Deklarationen angewendet werden. Er erzwingt Einschränkungen für den Code in der Funktion und das Verhalten der Funktion in Anwendungen, die C++ Accelerated Massive Parallelism(C++ AMP)-Laufzeit verwenden.

> [!NOTE]
> Informationen über das **`restrict`** Schlüsselwort, das Teil der **`__declspec`** Speicher Klassenattribute ist, finden Sie unter [einschränken](../cpp/restrict.md).

Die- **`restrict`** Klausel hat die folgenden Formen:

|Klausel|BESCHREIBUNG|
|------------|-----------------|
|`restrict(cpu)`|Die Funktion kann die vollständige C++-Programmiersprache verwenden. Es können nur andere Funktionen, die durch die Verwendung von restrict(cpu)-Funktionen deklariert werden, die Funktion aufrufen.|
|`restrict(amp)`|Die Funktion kann nur die Teilmenge der Programmiersprache C++ verwenden, die mit C++ AMP beschleunigt werden kann.|
|Eine Sequenz von `restrict(cpu)` und `restrict(amp)`.|Die Funktion muss den Einschränkungen von `restrict(cpu)` und `restrict(amp)` folgen. Die Funktion kann von Funktionen aufgerufen werden, die durch die Verwendung von `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` oder `restrict(amp, cpu)` deklariert werden.<br /><br /> Das Formular `restrict(A) restrict(B)` kann als `restrict(A,B)` geschrieben werden.|

## <a name="remarks"></a>Bemerkungen

Das **`restrict`** Schlüsselwort ist ein kontextbezogenes Schlüsselwort. Die Einschränkungsspezifizierer, `cpu` und `amp` sind keine reservierten Wörter. Die Liste der Spezifizierer ist nicht erweiterbar. Eine Funktion, die keine- **`restrict`** Klausel aufweist, ist dieselbe wie eine Funktion, die über die- `restrict(cpu)` Klausel verfügt.

Eine Funktion, die über die `restrict(amp)`-Klausel verfügt, hat folgende Einschränkungen:

- Die Funktion kann nur Funktionen aufrufen, die die `restrict(amp)`-Klausel enthalten.

- Die Funktion muss inlinable sein.

- Die-Funktion kann nur **`int`** **`unsigned int`** -, **`float`** -,-und- **`double`** Variablen sowie Klassen und Strukturen deklarieren, die nur diese Typen enthalten. **`bool`** ist ebenfalls zulässig, muss jedoch 4-Byte-ausgerichtet sein, wenn Sie es in einem Verbund-Typ verwenden.

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

  - **`goto`** Äußerungen.

  - Anweisungen mit Bezeichnung.

  - **`try`**-,- **`catch`** oder- **`throw`** Anweisungen.

  - Globale Variablen.

  - Statische Variablen. Verwenden Sie stattdessen [tile_static-Schlüsselwort](../cpp/tile-static-keyword.md) .

  - **`dynamic_cast`** Würfen.

  - Der **`typeid`** Operator.

  - ASM-Deklarationen.

  - Varargs.

Eine Erläuterung der Funktionseinschränkungen finden Sie unter [Einschränkungen für Einschränkungen (amp)](/archive/blogs/nativeconcurrency/restrictamp-restrictions-part-0-of-n-introduction).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie die-Klausel verwendet wird `restrict(amp)` .

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
