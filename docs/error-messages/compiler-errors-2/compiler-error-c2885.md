---
title: Compilerfehler C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 9b6b7bb54d5dce48dc6fce517eb0c909b0284da2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233443"
---
# <a name="compiler-error-c2885"></a>Compilerfehler C2885

"Class:: Identifier": keine gültige using-Deklaration im nicht Klassen Bereich.

Sie haben fälschlicherweise eine [using](../../cpp/using-declaration.md) -Deklaration verwendet.

## <a name="example"></a>Beispiel

Dieser Fehler kann als Folge von compilerübereinstimmungs-Voreinstellungen generiert werden, die für Visual Studio 2005 ausgeführt wurden: Es ist nicht mehr zulässig, eine **`using`** Deklaration für einen schsted Typ zu haben. Sie müssen explizit jeden Verweis qualifizieren, den Sie für den schsted Typ vornehmen, den Typ in einen Namespace einfügen oder eine typedef erstellen.

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

## <a name="example"></a>Beispiel

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
