---
title: Benutzerdefinierte Konvertierungen (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
ms.openlocfilehash: bb7a30382bc586f4d324d47ef6e6757fac83f5ae
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545132"
---
# <a name="user-defined-conversions-ccli"></a>Benutzerdefinierte Konvertierungen (C++/CLI)

In diesem Abschnitt werden benutzerdefinierte Konvertierungen (UDC) erläutert, wenn einer der Typen in der Konvertierung ein Verweis oder eine Instanz eines Werttyps oder Verweistyps ist.

## <a name="implicit-and-explicit-conversions"></a>Implizite und explizite Konvertierungen

Eine benutzerdefinierte Konvertierung kann entweder implizit oder explizit sein.  Ein UDC sollte implizit sein, wenn die Konvertierung keinen Informationsverlust zur Folge hat. Andernfalls sollte ein expliziter UDC definiert werden.

Der Konstruktor einer nativen Klasse kann verwendet werden, um einen Verweis-oder Werttyp in eine native Klasse zu konvertieren.

Weitere Informationen zu Konvertierungen finden Sie unter [Boxing](../extensions/boxing-cpp-component-extensions.md) und [Standard Konvertierungen](../cpp/standard-conversions.md).

```cpp
// mcpp_User_Defined_Conversions.cpp
// compile with: /clr
#include "stdio.h"
ref class R;
class N;

value class V {
   static operator V(R^) {
      return V();
   }
};

ref class R {
public:
   static operator N(R^);
   static operator V(R^) {
      System::Console::WriteLine("in R::operator N");
      return V();
   }
};

class N {
public:
   N(R^) {
      printf("in N::N\n");
   }
};

R::operator N(R^) {
   System::Console::WriteLine("in R::operator N");
   return N(nullptr);
}

int main() {
   // Direct initialization:
   R ^r2;
   N n2(r2);   // direct initialization, calls constructor
   static_cast<N>(r2);   // also direct initialization

   R ^r3;
   // ambiguous V::operator V(R^) and R::operator V(R^)
   // static_cast<V>(r3);
}
```

**Ausgabe**

```Output
in N::N
in N::N
```

## <a name="convert-from-operators"></a>Convert-From-Operatoren

Convert-from-Operatoren erstellen ein Objekt der Klasse, in der der Operator aus einem Objekt einer anderen Klasse definiert wird.

Der C++ Standard unterstützt keine Convert-from-Operatoren. Standard C++ verwendet für diesen Zweck Konstruktoren. Bei Verwendung von CLR-Typen bietet Visual C++ jedoch syntaktische Unterstützung für das Aufrufen von Convert-from-Operatoren.

Um mit anderen CLS-kompatiblen Sprachen gut zusammenzuarbeiten, können Sie jeden benutzerdefinierten unären Konstruktor für eine bestimmte Klasse mit einem entsprechenden Convert-from-Operator umschließen.

Convert-from-Operatoren:

- Muss als statische Funktionen definiert werden.

- Kann entweder implizit (bei Konvertierungen, die keine Genauigkeit verlieren, z. b. kurz zu int) oder explizit sein, wenn es zu einem Genauigkeits Verlust kommen kann.

- Gibt ein Objekt der enthaltenden Klasse zurück.

- Der Typ "from" muss als einziger Parametertyp angegeben werden.

Im folgenden Beispiel wird ein impliziter und expliziter benutzerdefinierter Konvertierungs Operator (UDC) gezeigt.

```cpp
// clr_udc_convert_from.cpp
// compile with: /clr
value struct MyDouble {
   double d;

   MyDouble(int i) {
      d = static_cast<double>(i);
      System::Console::WriteLine("in constructor");
   }

   // Wrap the constructor with a convert-from operator.
   // implicit UDC because conversion cannot lose precision
   static operator MyDouble (int i) {
      System::Console::WriteLine("in operator");
      // call the constructor
      MyDouble d(i);
      return d;
   }

   // an explicit user-defined conversion operator
   static explicit operator signed short int (MyDouble) {
      return 1;
   }
};

int main() {
   int i = 10;
   MyDouble md = i;
   System::Console::WriteLine(md.d);

   // using explicit user-defined conversion operator requires a cast
   unsigned short int j = static_cast<unsigned short int>(md);
   System::Console::WriteLine(j);
}
```

**Ausgabe**

```Output
in operator
in constructor
10
1
```

## <a name="convert-to-operators"></a>Convert-to-Operatoren

Convert-to-Operatoren konvertieren ein Objekt der Klasse, in der der Operator definiert ist, in ein anderes Objekt. Im folgenden Beispiel wird ein impliziter benutzerdefinierter Konvertierungs Operator (Convert-to) veranschaulicht:

```cpp
// clr_udc_convert_to.cpp
// compile with: /clr
using namespace System;
value struct MyInt {
   Int32 i;

   // convert MyInt to String^
   static operator String^ ( MyInt val ) {
      return val.i.ToString();
   }

   MyInt(int _i) : i(_i) {}
};

int main() {
   MyInt mi(10);
   String ^s = mi;
   Console::WriteLine(s);
}
```

**Ausgabe**

```Output
10
```

Ein expliziter benutzerdefinierter Konvertierungs Operator für Konvertierungen eignet sich für Konvertierungen, bei denen Daten möglicherweise auf irgendeine Weise verloren gehen. Um einen expliziten Convert-to-Operator aufzurufen, muss eine Umwandlung verwendet werden.

```cpp
// clr_udc_convert_to_2.cpp
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
   d.d = 10.3;
   System::Console::WriteLine(d.d);
   int i = 0;
   i = static_cast<int>(d);
   System::Console::WriteLine(i);
}
```

**Ausgabe**

```Output
10.3
10
```

## <a name="to-convert-generic-classes"></a>So konvertieren Sie generische Klassen

Sie können eine generische Klasse in T konvertieren.

```cpp
// clr_udc_generics.cpp
// compile with: /clr
generic<class T>
public value struct V {
   T mem;
   static operator T(V v) {
      return v.mem;
   }

   void f(T t) {
      mem = t;
   }
};

int main() {
   V<int> v;
   v.f(42);
   int i = v;
   i += v;
   System::Console::WriteLine(i == (42 * 2) );
}
```

**Ausgabe**

```Output
True
```

Ein konvertierender Konstruktor nimmt einen Typ an und verwendet ihn, um ein Objekt zu erstellen.  Ein konvertierender Konstruktor wird nur mit direkter Initialisierung aufgerufen. Umwandlungen rufen keine konvertierungskonstruktoren auf. Standardmäßig sind konvertierungskonstruktoren für CLR-Typen explizit.

```cpp
// clr_udc_converting_constructors.cpp
// compile with: /clr
public ref struct R {
   int m;
   char c;

   R(int i) : m(i) { }
   R(char j) : c(j) { }
};

public value struct V {
   R^ ptr;
   int m;

   V(R^ r) : ptr(r) { }
   V(int i) : m(i) { }
};

int main() {
   R^ r = gcnew R(5);

   System::Console::WriteLine( V(5).m);
   System::Console::WriteLine( V(r).ptr);
}
```

**Ausgabe**

```Output
5
R
```

In diesem Codebeispiel bewirkt eine implizite statische Konvertierungs Funktion dasselbe wie ein expliziter konvertierungskonstruktor.

```
public value struct V {
   int m;
   V(int i) : m(i) {}
   static operator V(int i) {
      V v(i*100);
      return v;
   }
};

public ref struct R {
   int m;
   R(int i) : m(i) {}
   static operator R^(int i) {
      return gcnew R(i*100);
   }
};

int main() {
   V v(13);   // explicit
   R^ r = gcnew R(12);   // explicit

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);

   // explicit ctor can't be called here: not ambiguous
   v = 5;
   r = 20;

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);
}
```

**Ausgabe**

```Output
13
12
500
2000
```

## <a name="see-also"></a>Siehe auch

[Klassen und Strukturen](../extensions/classes-and-structs-cpp-component-extensions.md)
