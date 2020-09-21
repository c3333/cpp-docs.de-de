---
title: Compilerfehler C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: 74c5032338b3f4cf30bdb75bdf070cee7b67ce58
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742111"
---
# <a name="compiler-error-c2440"></a>Compilerfehler C2440

'Konvertierung': Konvertierung von 'Typ1' in 'Typ2' nicht möglich

Der Compiler kann nicht von `type1` in umwandeln `type2` .

C2440 kann verursacht werden, wenn Sie versuchen, eine nicht-Konstante **`char*`** (oder `wchar_t*` ) mithilfe eines Zeichenfolgenliterals in C++-Code zu initialisieren, wenn die compilerübereinstimmungs Option [/Zc: strictstrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) festgelegt ist. In C ist der Typ eines Zeichenfolgenliterals ein Array von **`char`** , aber in C++ ist es ein Array von `const char` .

## <a name="examples"></a>Beispiele

Dieses Beispiel generiert C2440:

```cpp
// C2440s.cpp
// Build: cl /Zc:strictStrings /W3 C2440s.cpp
// When built, the compiler emits:
// error C2440: 'initializing' : cannot convert from 'const char [5]'
// to 'char *'
//        Conversion from string literal loses const qualifier (see
// /Zc:strictStrings)

int main() {
   char* s1 = "test"; // C2440
   const char* s2 = "tests"; // OK
}
```

C2440 kann auch verursacht werden, wenn Sie versuchen, einen Zeiger auf ein Element in "void*" zu konvertieren. Im nächsten Beispiel wird C2440 generiert:

```cpp
// C2440.cpp
class B {
public:
   void  f(){;}

   typedef void (B::*pf)();

   void f2(pf pf) {
       (this->*pf)();
       void* pp = (void*)pf;   // C2440
   }

   void f3() {
      f2(f);
   }
};
```

C2440 kann auch verursacht werden, wenn Sie versuchen, einen Typ umzuwandeln, der nur vorwärts deklariert jedoch nicht definiert ist. Dieses Beispiel generiert C2440:

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}
```

Die C2440-Fehler in den Zeilen 15 und 16 des folgenden Beispielcodes sind durch die Meldung `Incompatible calling conventions for UDT return value` gekennzeichnet. Ein *UDT* ist ein benutzerdefinierter Typ, z. b. eine Klasse, eine Struktur oder eine Union. Derartige Inkompatibilitätsfehler treten auf, wenn die Aufrufkonvention eines UDTs, die im Rückgabetyp einer Vorwärtsdeklaration festgelegt wurde, Konflikte mit der aktuellen Aufrufkonvention des UDTs verursacht und zugleich ein Funktionszeiger betroffen ist.

Das Beispiel enthält zunächst Vorwärtsdeklarationen für eine Struktur und für eine Funktion, durch die die Struktur zurückgegeben wird. Der Compiler geht davon aus, dass die Struktur die C++-Aufrufkonvention verwendet. Darauf folgt die Strukturdefinition, die standardmäßig die C-Aufrufkonvention verwendet. Da der Compiler die Aufrufkonvention der Struktur nicht kennt, solange die Struktur nicht vollständig eingelesen ist, setzt er voraus, dass die Aufrufkonvention für die Struktur im Rückgabetyp von `get_c2` ebenfalls C++ entspricht.

Auf die Struktur folgt eine weitere Funktionsdeklaration, durch die die Struktur zurückgegeben wird. Zu diesem Zeitpunkt weiß der Compiler jedoch bereits, dass die Struktur die C++-Aufrufkonvention verwendet. Entsprechend wird der Funktionszeiger, durch den die Struktur zurückgegeben wird, erst nach der Strukturdefinition definiert. Daher ist dem Compiler bekannt, dass die Struktur die C++-Aufrufkonvention verwendet.

Um den durch inkompatible Aufrufkonventionen hervorgerufenen Fehler C2440 zu beheben, sollten Sie Funktionen deklarieren, die einen UDT nach der UDT-Definition zurückgeben.

```cpp
// C2440b.cpp
struct MyStruct;

MyStruct get_c1();

struct MyStruct {
   int i;
   static MyStruct get_C2();
};

MyStruct get_C3();

typedef MyStruct (*FC)();

FC fc1 = &get_c1;   // C2440, line 15
FC fc2 = &MyStruct::get_C2;   // C2440, line 16
FC fc3 = &get_C3;

class CMyClass {
public:
   explicit CMyClass( int iBar)
      throw()   {
   }

   static CMyClass get_c2();
};

int main() {
   CMyClass myclass = 2;   // C2440
   // try one of the following
   // CMyClass myclass{2};
   // CMyClass myclass(2);

   int *i;
   float j;
   j = (float)i;   // C2440, cannot cast from pointer to int to float
}
```

C2440 kann auch auftreten, wenn Sie einem inneren Zeiger 0 (null) zuweisen:

```cpp
// C2440c.cpp
// compile with: /clr
int main() {
   array<int>^ arr = gcnew array<int>(100);
   interior_ptr<int> ipi = &arr[0];
   ipi = 0;   // C2440
   ipi = nullptr;   // OK
}
```

C2440 kann auch bei nicht ordnungsgemäßer Verwendung einer benutzerdefinierten Konvertierung auftreten. Wenn ein Konvertierungs Operator z. b. als definiert wurde **`explicit`** , kann der Compiler ihn nicht in einer impliziten Konvertierung verwenden. Weitere Informationen zu benutzerdefinierten Konvertierungen finden Sie unter [benutzerdefinierte Konvertierungen (C++/CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)). Dieses Beispiel generiert C2440:

```cpp
// C2440d.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   int i;
   i = d;   // C2440
   // Uncomment the following line to resolve.
   // i = static_cast<int>(d);
}
```

C2440 kann auch bei dem Versuch auftreten, eine Instanz eines Visual C++-Arrays vom Typ <xref:System.Array> zu erstellen.  Weitere Informationen finden Sie unter [Arrays](../../extensions/arrays-cpp-component-extensions.md).  Im nächsten Beispiel wird C2440 generiert:

```cpp
// C2440e.cpp
// compile with: /clr
using namespace System;
int main() {
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440
   // try the following line instead
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));
}
```

C2440 kann auch aufgrund von Änderungen in der Attributfunktion auftreten.  Im folgenden Beispiel wird C2440 generiert.

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

Der Microsoft C++-Compiler lässt den [const_cast Operator](../../cpp/const-cast-operator.md) nicht mehr zu, wenn der Quellcode, der die **/CLR** -Programmierung verwendet, kompiliert wird.

Um den Fehler C2440 zu beheben, verwenden Sie den richtigen Umwandlungsoperator. Weitere Informationen finden Sie unter Umwandlungs [Operatoren](../../cpp/casting-operators.md).

Dieses Beispiel generiert C2440:

```cpp
// c2440g.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};
int main() {
   Derived ^d = gcnew Derived;
   Base ^b = d;
   d = const_cast<Derived^>(b);   // C2440
   d = dynamic_cast<Derived^>(b);   // OK
}
```

C2440 kann aufgrund von Konformitäts Änderungen des Compilers in Visual Studio 2015 Update 3 auftreten. Zuvor hat der Compiler bestimmte unterschiedliche Ausdrücke beim Identifizieren einer Vorlagen Übereinstimmung für einen Vorgang fälschlicherweise als denselben Typ behandelt **`static_cast`** . Der Compiler unterscheidet die Typen nun ordnungsgemäß, und Code, der auf das vorherige Verhalten beruhte, ist fehlerhaft **`static_cast`** . Um dieses Problem zu beheben, ändern Sie das Vorlagen Argument so, dass es dem Vorlagen Parametertyp entspricht, oder verwenden Sie eine Typumwandlung im **`reinterpret_cast`** C-Format.

Dieses Beispiel generiert C2440:

```cpp
// c2440h.cpp

template<int *a>
struct S1 {};

int g;
struct S2 : S1<&g> {
};

int main()
{
    S2 s;
    static_cast<S1<&*&g>>(s); // C2440 in VS 2015 Update 3
    // This compiles correctly:
    // static_cast<S1<&g>>(s);
}

This error can appear in ATL code that uses the SINK_ENTRY_INFO macro defined in <atlcom.h>.
```

### <a name="copy-list-initialization"></a>copy-list-Initialisierung

Visual Studio 2017 und höhere Versionen verursachen Compilerfehler im Zusammenhang mit der Objekt Erstellung mithilfe von Initialisiererlisten, die nicht in Visual Studio 2015 abgefangen wurden, und können zu Abstürzen oder nicht definiertem Laufzeitverhalten führen. In c++ 17 Copy-List-Initialization muss der Compiler einen expliziten Konstruktor für die Überladungs Auflösung in Erwägung ziehen, aber es muss ein Fehler ausgegeben werden, wenn die Überladung tatsächlich ausgewählt wird.

Das folgende Beispiel wird in Visual Studio 2015 kompiliert, jedoch nicht in Visual Studio 2017.

```cpp
// C2440j.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot
                         // convert from 'int' to 'const A &'
}
```

Verwenden Sie direkte Initialisierung, um den Fehler zu korrigieren:

```cpp
// C2440k.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2{ 1 };
}
```

### <a name="cv-qualifiers-in-class-construction"></a>CV-Qualifizierer in der Klassenkonstruktion

In Visual Studio 2015 ignoriert der Compiler beim Generieren eines Klassenobjekts über einen Konstruktoraufruf manchmal fälschlicherweise die CV-Qualifizierer. Dies kann potenziell zu einem Absturz oder zu unerwartetem Laufzeitverhalten führen. Im folgenden Beispiel wird in Visual Studio 2015 kompiliert, es wird jedoch ein Compilerfehler in Visual Studio 2017 und höher ausgelöst:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Deklarieren Sie den Operator int() als konstant, um den Fehler zu korrigieren.
