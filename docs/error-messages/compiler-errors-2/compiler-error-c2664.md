---
title: Compilerfehler C2664
ms.date: 11/04/2016
f1_keywords:
- C2664
helpviewer_keywords:
- C2664
ms.assetid: 3595d66e-cf87-4fda-a896-c0cd81f95db4
ms.openlocfilehash: 8bb9ecef2e08e1f65a817e1a6496a421e727eb13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221119"
---
# <a name="compiler-error-c2664"></a>Compilerfehler C2664

'function': Kann Argument n nicht von 'type1' zu 'type2' konvertieren

Dieses Problem mit der Parameter Konvertierung kann auftreten, wenn eine Instanz einer Klasse erstellt wird und eine implizite Konvertierung für einen mit dem Schlüsselwort markierten Konstruktor versucht wird **`explicit`** . Weitere Informationen zu expliziten Konvertierungen finden Sie unter [benutzerdefinierte Typkonvertierungen](../../cpp/user-defined-type-conversions-cpp.md).

Wenn ein temporäres Objekt an eine Funktion übergeben wird, die einen Verweis auf ein Objekt als Parameter annimmt, muss dieser Verweis ein **`const`** Verweis sein.

Wenn die Funktion mit einem Parameter übergeben wird, der nicht den von der Funktion erwarteten Typ aufweist, wird mithilfe des entsprechenden Konstruktors ein temporäres Objekt erstellt. Dieses temporäre Objekt wird dann an die Funktion übergeben. In diesem Fall wird das temporäre Objekt zur Initialisierung des Verweises verwendet. In früheren Versionen der Sprache war es möglich, alle Verweise durch temporäre Objekte zu initialisieren.

So beheben Sie C2664

- Überprüfen Sie den Prototyp der jeweiligen Funktion erneut, und korrigieren Sie das in der Fehlermeldung angegebene Argument.

- Geben Sie, falls erforderlich, eine explizite Konvertierung an.

C2664 kann auch generiert werden, wenn durch eine Klasse ein Member in einer seiner Basisklassen verborgen wird.

Weitere Informationen finden Sie unter Gewusst [wie: Konvertieren von System:: String in wchar_t * oder \* char](../../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2664 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2664.cpp
// C2664
struct A {
   void f(int i) {};
};

struct B : public A {
   // To fix, uncomment the following line.
   // using A::f;
   void f(A a) {};
};

int main() {
   B b;
   int i = 1;
   b.f(i);   // B::F hides A::f Uncomment the using declaration in B.
}
```

## <a name="example"></a>Beispiel

In diesem Beispiel wird auch C2664 generiert und gezeigt, wie Sie dies beheben.

```cpp
// C2664b.cpp
// C2664 expected
struct A {
   // To fix, uncomment the following line.
   // A(int i){}
};

void func( int, A ) {}

int main() {
   func( 1, 1 );   // No conversion from int to A.
}
```

## <a name="example"></a>Beispiel

Im nächsten Beispiel wird C2664 mithilfe einen Zeichenfolgenliterals zum Aufrufen von `Test` und dessen Behebung veranschaulicht. Da es sich bei dem Parameter um einen `szString`-Verweis handelt, muss der entsprechende Konstruktor ein Objekt erstellen. Das Resultat ist ein temporäres Objekt, das nicht zur Initialisierung des Verweises verwendet werden kann.

```cpp
// C2664c.cpp
// compile with: /EHsc
// C2664 expected
#include <iostream>
#include <string.h>
using namespace std;

class szString {
   int slen;
   char *str;

public:
   szString(const char *);
   int len() const {
      return slen;
   }
};

// Simple reference cannot bind to temp var.
void Test(szString &a) {}

// To fix, uncomment the following line.
// void Test(const szString &a) {}

szString::szString(const char * newstr) : slen(0), str(NULL) {
   slen=strlen(newstr);
   str = new char[slen + 1];
   if (str)
      strcpy_s(str, (slen + 1), newstr);
}

int main() {
   Test("hello");
}
```

## <a name="example"></a>Beispiel

Der Compiler erzwingt die C++-Standardanforderungen für die Anwendung von **`const`** . Dieses Beispiel generiert C2664:

```cpp
// C2664d.cpp
// C2664 expected
#include <windows.h>

void func1(LPCSTR &s)
{

}

void func2(LPSTR &s)
{
   func1(s);
}

int main()
{
   return 0;
}
```

## <a name="example"></a>Beispiel

Hier liegt eine komplexere Situation vor, wo C2664 generiert wird, einschließlich Anweisungen über die entsprechende Behebung:

```cpp
// C2664e.cpp
// compile with: /EHsc
// C2664 expected
#define _INTL
#include <locale>
#include <iostream>

using namespace std;
#define LEN 90

int main( ) {
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));

   // To fix, delete the following line.
   char* pszNext;

   // To fix, uncomment the following line.
   // const char* pszNext;

   wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).in( state,
      pszExt, &pszExt[strlen(pszExt)], pszNext,
      pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   // See earlier comment.
      pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error) ?
                       L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;

   exit(-1);
}
```

## <a name="example"></a>Beispiel

Eine Enumerationsvariable wird nicht in den ihr zugrunde liegenden Typ konvertiert, sodass einem Funktionsaufruf entsprochen wird. Weitere Informationen finden Sie unter [Enumerationsklasse](../../extensions/enum-class-cpp-component-extensions.md). Im folgenden Beispiel wird C2664 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2664f.cpp
// compile with: /clr
using namespace System;
public enum class A : Char {
   None = 0,
   NonSilent = 1,
};

void Test(Char c) {}

int main() {
   A aa = A::None;
   Test(aa);   // C2664
   Test(Char(aa));   // OK - fix by using a conversion cast
}
```

## <a name="example"></a>Beispiel

Ein Fehler im MIFL-Compiler führt dazu, dass ein wchar_t-Typ in der Typbibliothek als "unsigned short" ausgegeben wird. Um diesen Fehler zu beheben, wandeln Sie den Typ im C++-Quellcode um, oder definieren Sie den Typ als Zeichenfolge in der IDL-Datei.

```
// C2664g.idl
import "prsht.idl";

[ object, uuid(8402B8F1-BF7F-4B49-92D4-C2B9DF4543E9) ]

interface IMyObj1 : IUnknown {
   HRESULT  teststr([in, string] wchar_t *wstr);
   HRESULT  testarr([in, size_is(len)] wchar_t wstr[], [in] int len);
   HRESULT  testbstr([in] BSTR bstr);
};

[  uuid(44463307-CBFC-47A6-8B4F-13CD0A83B436) ]
library myproj1 {
   [  version(1.0), uuid(D8622C12-5448-42B8-8F0E-E3AD6B8470C1) ]
   coclass CMyObj1 { interface IMyObj1; };
}
```

C2664 wird auch mithilfe von ausgelöst **`wchar_t`** , wenn Code von Visual C++ 6,0 auf spätere Versionen portieren. In Visual C++ 6,0 und früher **`wchar_t`** war ein **`typedef`** für **`unsigned short`** und war daher implizit in diesen Typ konvertierbar. Nach Visual C++ 6,0 **`wchar_t`** ist ein eigener integrierter Typ, wie im C++-Standard angegeben, und ist nicht mehr implizit in konvertierbar **`unsigned short`** . Siehe [/Zc: wchar_t (wchar_t ist der Native Typ)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2664 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2664h.cpp
#import "C2664g.tlb"
using namespace myproj1;

int main() {
   IMyObj1Ptr ptr;

   wchar_t * mybuff = 0;
   BSTR bstr = 0;
   int len;
   ptr->teststr(mybuff);
   ptr->testbstr(bstr);
   ptr->testarr(mybuff, len);   // C2664
   ptr->testarr((unsigned short *)mybuff, len);   // OK - Fix by using a cast
}
```

## <a name="example"></a>Beispiel

C2664 wird auch verursacht, wenn der Compiler keine Vorlagenargumente herleiten konnte.

```cpp
// C2664i.cpp
#include <stdio.h>
template <class T, int iType=0>
class CTypedImg {
public:
   CTypedImg() {}
   void run() {}

   operator CTypedImg<T>& () {
      return *((CTypedImg<T>*)this);
    }
};

template <class t1>
void test(CTypedImg<t1>& myarg) {
   myarg.run();
}

int main() {
   CTypedImg<float,2> img;

   test((CTypedImg<float>&)img);   // OK
   test<float>(img);   // OK
   test(img);   // C2664 - qualify as above to fix
}
```
