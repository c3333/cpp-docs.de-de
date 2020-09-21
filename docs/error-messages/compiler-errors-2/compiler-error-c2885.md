---
title: Compilerfehler C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 1953cb8fb9f80c5c1f967e10583c2b7303075f59
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742670"
---
# <a name="compiler-error-c2885"></a>Compilerfehler C2885

"Class:: Identifier": keine gültige using-Deklaration im nicht Klassen Bereich.

Sie haben fälschlicherweise eine [using](../../cpp/using-declaration.md) -Deklaration verwendet.

Dieser Fehler kann als Folge von compilerübereinstimmungs-Voreinstellungen generiert werden, die für Visual Studio 2005 ausgeführt wurden: Es ist nicht mehr zulässig, eine **`using`** Deklaration für einen schsted Typ zu haben. Sie müssen explizit jeden Verweis qualifizieren, den Sie für den schsted Typ vornehmen, den Typ in einen Namespace einfügen oder eine typedef erstellen.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2885 generiert.

```cpp
// C2885.cpp
namespace MyNamespace {
   class X1 {};
}

struct MyStruct {
   struct X1 {
      int i;
   };
};

int main () {
   using MyStruct::X1;   // C2885

   // OK
   using MyNamespace::X1;
   X1 myX1;

   MyStruct::X1 X12;

   typedef MyStruct::X1 abc;
   abc X13;
   X13.i = 9;
}
```

Wenn Sie das- **`using`** Schlüsselwort mit einem Klassenmember verwenden, erfordert C++, dass Sie dieses Element in einer anderen Klasse (einer abgeleiteten Klasse) definieren.

Im folgenden Beispiel wird C2885 generiert.

```cpp
// C2885_b.cpp
// compile with: /c
class A {
public:
   int i;
};

void z() {
   using A::i;   // C2885 not in a class
}

class B : public A {
public:
   using A::i;
};
```
