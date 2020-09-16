---
title: Linkertoolfehler LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 6fd4859e4f8cad657de57e8039bd647e5e2b99a9
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684637"
---
# <a name="linker-tools-error-lnk2020"></a>Linkertoolfehler LNK2020

nicht aufgelöstes Token "Token"

Ähnlich wie ein nicht definierter externer Fehler, mit dem Unterschied, dass der Verweis über Metadaten erfolgt. In den Metadaten müssen alle Funktionen und Daten definiert werden.

Behebung:

- Definieren Sie die fehlenden Funktionen oder Daten, oder

- Fügen Sie die Objektdatei oder-Bibliothek ein, in der die fehlenden Funktionen oder Daten bereits definiert sind.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird Linkertoolfehler LNK2020 generiert.

```cpp
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

Linkertoolfehler LNK2020 tritt auch auf, wenn Sie eine Variable eines verwalteten Vorlagen Typs erstellen, aber nicht auch den Typ instanziieren.

Im folgenden Beispiel wird Linkertoolfehler LNK2020 generiert.

```cpp
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```
