---
title: Compilerfehler C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: f5780c299eb4da03ece3611ee55062ee7ebcdaae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212786"
---
# <a name="compiler-error-c2273"></a>Compilerfehler C2273

"Typ": unzulässig als Rechte Seite des Operators "->".

Ein Typ wird als rechter Operand eines Operators angezeigt `->` .

Dieser Fehler kann verursacht werden, wenn versucht wird, auf eine benutzerdefinierte Typkonvertierung zuzugreifen. Verwenden Sie das **`operator`** -Schlüsselwort zwischen-> und `type` .

Im folgenden Beispiel wird C2273 generiert:

```cpp
// C2273.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};
int main() {
   MyClass * ClassPtr = new MyClass;
   int i = ClassPtr->int();   // C2273
   int j = ClassPtr-> operator int();   // OK
}
```
