---
title: Compilerfehler C3538
ms.date: 11/04/2016
f1_keywords:
- C3538
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
ms.openlocfilehash: 290faa1a227920cd46f32a4adf0dd6a6f3687c6d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233365"
---
# <a name="compiler-error-c3538"></a>Compilerfehler C3538

In einer Deklaratorliste muss "auto" immer in denselben Typ hergeleitet werden.

Nicht alle deklarierten Variablen in einer Deklarationsliste werden in den gleichen Typ aufgelöst.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Stellen Sie sicher, dass alle **`auto`** Deklarationen in der Liste in denselben Typ abgeleitet werden.

## <a name="example"></a>Beispiel

Die folgenden Anweisungen erzeugen C3538. Jede-Anweisung deklariert mehrere Variablen, aber jede Verwendung des- **`auto`** Schlüssel Worts wird nicht in denselben Typ abgeleitet.

```cpp
// C3538.cpp
// Compile with /Zc:auto
// C3538 expected
int main()
{
// Variable x1 is a pointer to char, but y1 is a double.
   auto * x1 = "a", y1 = 3.14;
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;
// Variable x2 is an int, but y2 is a double and z is a char.
   auto x2(1), y2(0.0), z = 'a';
// Variable a is a pointer to int, but b is a pointer to double.
   auto *a = new auto(1), *b = new auto(2.0);
   return 0;
}
```

## <a name="see-also"></a>Siehe auch

[Auto-Schlüsselwort](../../cpp/auto-keyword.md)
