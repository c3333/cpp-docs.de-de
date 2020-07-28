---
title: Compilerfehler C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: 5e2dd6b01db5f7d3026f14c5032ab4623eb6fb58
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220287"
---
# <a name="compiler-error-c2662"></a>Compilerfehler C2662

"Funktion": der this-Zeiger kann nicht von "Typ1" in "Typ2" konvertiert werden.

Der Compiler konnte den Zeiger nicht **`this`** von `type1` in konvertieren `type2` .

Dieser Fehler kann verursacht werden, wenn eine nicht- **`const`** Member-Funktion für ein-Objekt aufgerufen wird **`const`** .  Mögliche Lösungen:

- Entfernen Sie **`const`** aus der Objekt Deklaration.

- Fügen Sie **`const`** der Member-Funktion hinzu.

Im folgenden Beispiel wird C2662 generiert:

```cpp
// C2662.cpp
class C {
public:
   void func1();
   void func2() const{}
} const c;

int main() {
   c.func1();   // C2662
   c.func2();   // OK
}
```

Beim Kompilieren mit **/CLR**können Sie keine Funktion für einen oder einen **`const`** **`volatile`** qualifizierten verwalteten Typ abrufen. Sie können keine konstantenmember-Funktion einer verwalteten Klasse deklarieren, sodass Sie keine Methoden für verwaltete verwaltete Objekte abrufen können.

```cpp
// C2662_b.cpp
// compile with: /c /clr
ref struct M {
   property M^ Type {
      M^ get() { return this; }
   }

   void operator=(const M %m) {
      M ^ prop = m.Type;   // C2662
   }
};

ref struct N {
   property N^ Type {
      N^ get() { return this; }
   }

   void operator=(N % n) {
      N ^ prop = n.Type;   // OK
   }
};
```

Im folgenden Beispiel wird C2662 generiert:

```cpp
// C2662_c.cpp
// compile with: /c
// C2662 expected
typedef int ISXVD;
typedef unsigned char BYTE;

class LXBASE {
protected:
    BYTE *m_rgb;
};

class LXISXVD:LXBASE {
public:
   // Delete the following line to resolve.
   ISXVD *PMin() { return (ISXVD *)m_rgb; }

   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK
};

void F(const LXISXVD *plxisxvd, int iDim) {
   ISXVD isxvd;
   // Delete the following line to resolve.
   isxvd = plxisxvd->PMin()[iDim];

   isxvd = plxisxvd->PMin2()[iDim];
}
```
