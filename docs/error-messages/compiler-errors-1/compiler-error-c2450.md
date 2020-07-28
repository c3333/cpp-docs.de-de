---
title: Compilerfehler C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 55c7f7ba8708e1475404a474f85df7dbe37fcec0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220352"
---
# <a name="compiler-error-c2450"></a>Compilerfehler C2450

der Switch-Ausdruck vom Typ "Type" ist unzulässig.

Der **`switch`** Ausdruck wird zu einem ungültigen Typ ausgewertet. Es muss zu einem ganzzahligen Typ oder einem Klassentyp mit eindeutiger Konvertierung in einen ganzzahligen Typ ausgewertet werden. Wenn ein benutzerdefinierter Typ ausgewertet wird, müssen Sie einen Konvertierungs Operator bereitstellen.

Im folgenden Beispiel wird C2450 generiert:

```cpp
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```
