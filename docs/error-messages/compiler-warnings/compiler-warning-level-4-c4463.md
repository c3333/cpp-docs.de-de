---
title: Compilerwarnung (Stufe 4) C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: acc7957493942a9c0e19ce098b74ed0b5d75a12d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214359"
---
# <a name="compiler-warning-level-4-c4463"></a>Compilerwarnung (Stufe 4) C4463

> Läufen Zuweisen eines *Werts* zu einem Bitfeld, das nur Werte aus *low_value* enthalten kann, die *high_value*

Der zugewiesene *Wert* liegt außerhalb des Bereichs von Werten, die das Bitfeld enthalten kann. Signierte bitfeldtypen verwenden das höchst wertige Bit für das Vorzeichen, d. h., wenn *n* die bitfeldgröße ist, ist der Bereich für signierte Bitfelder-2<sup>n-1</sup> bis 2<sup>n-1</sup>-1, während nicht signierte Bitfelder einen Bereich von 0 bis 2<sup>n</sup>-1 aufweisen.

## <a name="example"></a>Beispiel

In diesem Beispiel wird C4463 generiert, da versucht wird, einen Wert von 3 einem Bitfeld vom Typ **`int`** mit einer Größe von 2 zuzuweisen, der einen Bereich zwischen-2 und 1 aufweist.

Um dieses Problem zu beheben, können Sie den zugewiesenen Wert in einen Wert im zulässigen Bereich ändern. Wenn das Bitfeld für die Aufbewahrung von Werten ohne Vorzeichen im Bereich von 0 bis 3 vorgesehen ist, können Sie den Deklarationstyp in ändern **`unsigned`** . Wenn das Feld Werte im Bereich von-4 bis 3 enthalten soll, können Sie die bitfeldgröße in 3 ändern.

```cpp
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S {
    int x : 2; // int type treats high-order bit as sign
};

int main() {
    S s;
    s.x = 3; // warning C4463: overflow; assigning 3
    // to bit-field that can only hold values from -2 to 1
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type
    // to unsigned.
}
```
