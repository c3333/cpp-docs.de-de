---
title: Compilerfehler C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 7d3fc71a331d13416f65d841502fdd1d908653bd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225448"
---
# <a name="compiler-error-c2635"></a>Compilerfehler C2635

' Bezeichner1 * ' kann nicht in ' Bezeichner2 ' konvertiert werden \* ; die Konvertierung einer virtuellen Basisklasse wird impliziert

Die Konvertierung erfordert eine Umwandlung von einer **`virtual`** Basisklasse in eine abgeleitete Klasse, die nicht zulässig ist.

Im folgenden Beispiel wird C2635 generiert:

```cpp
// C2635.cpp
class B {};
class D : virtual public B {};
class E : public B {};

int main() {
   B b;
   D d;
   E e;

   D * pD = &d;
   E * pE = &e;
   pD = (D*)&b;   // C2635
   pE = (E*)&b;   // OK
}
```
