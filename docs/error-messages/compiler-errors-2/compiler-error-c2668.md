---
title: Compilerfehler C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: f59cb33bed15847ed1a7a2dbe99ea030babf3337
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177156"
---
# <a name="compiler-error-c2668"></a>Compilerfehler C2668

"Function": mehrdeutiger aufladener Funktions aufzurufen

Der angegebene überladene Funktions aufrufsbefehl konnte nicht aufgelöst werden. Möglicherweise möchten Sie einen oder mehrere der eigentlichen Parameter explizit umwandeln.

Dieser Fehler kann auch über die Vorlagen Verwendung angezeigt werden. Wenn Sie in derselben Klasse über eine reguläre Element Funktion und eine auf Vorlagen basierende Element Funktion mit derselben Signatur verfügen, muss die auf Vorlagen basierende Vorlage zuerst vorhanden sein. Dies ist eine Einschränkung der aktuellen Implementierung von Visual C++.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2668 generiert:

```cpp
// C2668.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};

void func( X, X ){}
void func( A, B ){}
D d;
int main() {
   func( d, d );   // C2668 D has an A, B, and X
   func( (X)d, (X)d );   // OK, uses func( X, X )
}
```

## <a name="example"></a>Beispiel

Eine andere Möglichkeit, diesen Fehler zu beheben, ist die [Verwendung einer using-Deklaration](../../cpp/using-declaration.md):

```cpp
// C2668b.cpp
// compile with: /EHsc /c
// C2668 expected
#include <iostream>
class TypeA {
public:
   TypeA(int value) {}
};

class TypeB {
   TypeB(int intValue);
   TypeB(double dbValue);
};

class TestCase {
public:
   void AssertEqual(long expected, long actual, std::string
                    conditionExpression = "");
};

class AppTestCase : public TestCase {
public:
   // Uncomment the following line to resolve.
   // using TestCase::AssertEqual;
   void AssertEqual(const TypeA expected, const TypeA actual,
                    std::string conditionExpression = "");
   void AssertEqual(const TypeB expected, const TypeB actual,
                    std::string conditionExpression = "");
};

class MyTestCase : public AppTestCase {
   void TestSomething() {
      int actual = 0;
      AssertEqual(0, actual, "Value");
   }
};
```

## <a name="example"></a>Beispiel

Dieser Fehler kann auch infolge einer compilerübereinstimmungs-Arbeit generiert werden, die für Visual Studio .NET 2003 ausgeführt wurde: mehrdeutige Konvertierung bei Umwandlung von Konstante 0.

Die Konvertierung in eine Typumwandlung mithilfe von Konstante 0 ist mehrdeutig, da int eine Konvertierung zwischen "Long" und "void *" erfordert. Um diesen Fehler zu beheben, wandeln Sie 0 in den exakten Typ des Funktions Parameters um, für den es verwendet wird, sodass keine Konvertierungen stattfinden müssen (dieser Code ist in den Visual Studio .NET 2003-und Visual Studio .net- C++Versionen von Visual Studio gültig).

```cpp
// C2668c.cpp
#include "stdio.h"
void f(long) {
   printf_s("in f(long)\n");
}
void f(void*) {
   printf_s("in f(void*)\n");
}
int main() {
   f((int)0);   // C2668

   // OK
   f((long)0);
   f((void*)0);
}
```

## <a name="example"></a>Beispiel

Dieser Fehler kann auftreten, wenn die CRT jetzt über float-und Double-Formen aller mathematischen Funktionen verfügt.

```cpp
// C2668d.cpp
#include <math.h>
int main() {
   int i = 0;
   float f;
   f = cos(i);   // C2668
   f = cos((float)i);   // OK
}
```

## <a name="example"></a>Beispiel

Dieser Fehler kann auftreten, wenn der Pow (int, int) aus Math. h in der CRT entfernt wurde.

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Beispiel

Dieser Code ist in Visual Studio 2015 erfolgreich, schlägt jedoch in Visual Studio 2017 und höher mit C2668 fehl. In Visual Studio 2015 behandelt der Compiler fälschlicherweise eine copy-list-Initialisierung auf die gleiche Weise wie eine Kopierinitialisierung. Er konvertiert nur die Konstruktoren für die Überladungsauflösung.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```
