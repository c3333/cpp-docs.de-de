---
title: void (C++)
ms.date: 11/04/2016
f1_keywords:
- void_cpp
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
ms.openlocfilehash: fddfc2e3295552414a00692006ab12725dc07d52
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213111"
---
# <a name="void-c"></a>void (C++)

Wenn das Schlüsselwort als Funktions Rückgabetyp verwendet wird, gibt es an **`void`** , dass die Funktion keinen Wert zurückgibt. Gibt bei Verwendung für die Parameterliste einer Funktion an, **`void`** dass die Funktion keine Parameter annimmt. Gibt bei Verwendung in der Deklaration eines Zeigers an, **`void`** dass der Zeiger "Universal" ist.

Wenn der Typ eines Zeigers **void \* **ist, kann der Zeiger auf eine beliebige Variable verweisen, die nicht mit **`const`** dem **`volatile`** Schlüsselwort oder deklariert ist. Ein **void \* ** -Zeiger kann nicht dereferenziert werden, es sei denn, er wird in einen anderen Typ umgewandelt. Ein **void \* ** -Zeiger kann in beliebige andere Typen von Daten Zeigern konvertiert werden.

Ein **`void`** Zeiger kann auf eine Funktion verweisen, jedoch nicht auf einen Klassenmember in C++.

Sie können keine Variable vom Typ deklarieren **`void`** .

## <a name="example"></a>Beispiel

```cpp
// void.cpp
void vobject;   // C2182
void *pv;   // okay
int *pint; int i;
int main() {
   pv = &i;
   // Cast optional in C required in C++
   pint = (int *)pv;
}
```

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Integrierte Typen](../cpp/fundamental-types-cpp.md)
