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
ms.openlocfilehash: 2de019f908942a58b232877fcd9eebc4689d8e22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187478"
---
# <a name="void-c"></a>void (C++)

Wenn das **void** -Schlüsselwort als Funktions Rückgabetyp verwendet wird, gibt es an, dass die Funktion keinen Wert zurückgibt. Bei Verwendung für die Parameterliste einer Funktion gibt **void** an, dass die Funktion keine Parameter annimmt. Bei Verwendung in der Deklaration eines Zeigers gibt **void** an, dass der Zeiger "Universal" ist.

Wenn der Typ eines Zeigers **void\*** ist, kann der Zeiger auf eine beliebige Variable verweisen, die nicht mit dem Schlüsselwort " **Konstanten** " oder " **volatile** " deklariert ist. Ein **void-\*** Zeiger kann nicht dereferenziert werden, es sei denn, er wird in einen anderen Typ umgewandelt. Ein **void-\*** Zeiger kann in beliebige andere Typen von Daten Zeigern konvertiert werden.

Ein **void** -Zeiger kann auf eine Funktion verweisen, jedoch nicht auf einen Klassenmember in C++.

Eine Variable vom Typ " **void**" kann nicht deklariert werden.

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
