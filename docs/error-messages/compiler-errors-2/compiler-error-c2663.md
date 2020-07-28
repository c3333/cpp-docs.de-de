---
title: Compilerfehler C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f9746ecb41e873fb1d929a939c78f1817dc0e2f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220274"
---
# <a name="compiler-error-c2663"></a>Compilerfehler C2663

"Funktion": Zahlen Überladungen weisen keine zulässigen Konvertierungen für den this-Zeiger auf.

Der Compiler konnte nicht **`this`** in eine der überladenen Versionen der Member-Funktion konvertieren.

Dieser Fehler kann verursacht werden, wenn eine nicht- **`const`** Member-Funktion für ein-Objekt aufgerufen wird **`const`** .  Mögliche Lösungen:

1. Entfernen Sie **`const`** aus der Objekt Deklaration.

1. Fügen Sie **`const`** einer der Element Funktions Überladungen hinzu.

Im folgenden Beispiel wird C2663 generiert:

```cpp
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```
