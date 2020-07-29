---
title: dynamic_cast-Operator
description: Übersicht über den C++-sprach dynamic_cast Operator.
ms.date: 02/03/2020
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 15609aeaef815ff89ca196876e1143090c65221b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221639"
---
# <a name="dynamic_cast-operator"></a>dynamic_cast-Operator

Konvertiert den Operanden `expression` in ein Objekt vom Typ `type-id`.

## <a name="syntax"></a>Syntax

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>Bemerkungen

`type-id` muss ein Zeiger oder ein Verweis auf einen zuvor definierten Klassentyp oder ein "Zeiger auf void" sein. Der `expression`-Typ muss ein Zeiger sein, wenn `type-id` ein Zeiger ist, oder ein lvalue, wenn `type-id` ein Verweis ist.

Eine Erläuterung des Unterschieds zwischen statischen und dynamischen Umwandlungs Konvertierungen finden Sie unter [static_cast](../cpp/static-cast-operator.md) .

Es gibt zwei wichtige Änderungen im Verhalten von **`dynamic_cast`** in verwaltetem Code:

- **`dynamic_cast`** Ein Zeiger auf den zugrunde liegenden Typ einer geschachtelten Aufzählung schlägt zur Laufzeit fehl und gibt 0 anstelle des konvertierten Zeigers zurück.

- **`dynamic_cast`** löst keine Ausnahme mehr aus, wenn `type-id` ein innerer Zeiger auf einen Werttyp ist, bei dem die Umwandlung zur Laufzeit fehlschlägt.  Die Umwandlung gibt jetzt den 0-Zeigerwert zurück, statt auszulösen.

Wenn `type-id` ein Zeiger auf eine eindeutig zugreifbare direkte oder indirekte Basisklasse von `expression` ist, ist ein Zeiger auf das eindeutige Unterobjekt vom Typ `type-id` das Ergebnis. Beispiel:

```cpp
// dynamic_cast_1.cpp
// compile with: /c
class B { };
class C : public B { };
class D : public C { };

void f(D* pd) {
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class
                                   // pc points to C subobject of pd
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class
                                   // pb points to B subobject of pd
}
```

Diese Art der Konvertierung wird als "Typumwandlung nach oben (Upcast)" bezeichnet, da ein Zeiger in einer Klassenhierarchie nach oben verschoben wird, von einer abgeleiteten Klasse zu der Klasse, von der sie abgeleitet wurde. Eine Typumwandlung nach oben ist eine implizite Konvertierung.

Wenn `type-id` "void*" ist, wird eine Laufzeitüberprüfung durchgeführt, um den tatsächlichen Typ von `expression` zu bestimmen. Das Ergebnis ist ein Zeiger auf das vollständige Objekt, auf das durch `expression` gezeigt wird. Beispiel:

```cpp
// dynamic_cast_2.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = new B;
   void* pv = dynamic_cast<void*>(pa);
   // pv now points to an object of type A

   pv = dynamic_cast<void*>(pb);
   // pv now points to an object of type B
}
```

Wenn `type-id` nicht "void*" ist, wird eine Laufzeitüberprüfung durchgeführt, um festzustellen, ob das Objekt, auf das durch `expression` gezeigt wird, in einen Typ konvertiert werden kann, auf den durch `type-id` gezeigt wird.

Wenn der Typ von `expression` eine Basisklasse vom Typ `type-id` ist, wird eine Laufzeitüberprüfung durchgeführt, um festzustellen, ob `expression` tatsächlich auf ein vollständiges Objekt vom Typ `type-id` zeigt. Wenn dies der Fall ist, ist das Ergebnis ein Zeiger auf ein vollständiges Objekt vom Typ `type-id`. Beispiel:

```cpp
// dynamic_cast_3.cpp
// compile with: /c /GR
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   B* pb = new D;   // unclear but ok
   B* pb2 = new B;

   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D
}
```

Diese Art der Konvertierung wird als "Typumwandlung" bezeichnet, da ein Zeiger in einer Klassenhierarchie nach unten verschoben wird, von einer angegebenen Klasse zu einer von dieser abgeleiteten Klasse.

Im Fall der Mehrfachvererbung werden Möglichkeiten für Mehrdeutigkeit eingeführt. Betrachten Sie die Klassenhierarchie, die in der folgenden Abbildung gezeigt wird.

Bei CLR-Typen **`dynamic_cast`** ergibt entweder eine No-op-Anweisung, wenn die Konvertierung implizit durchgeführt werden kann, oder eine MSIL `isinst` -Anweisung, die eine dynamische Prüfung ausführt und zurückgibt, **`nullptr`** Wenn die Konvertierung fehlschlägt.

Im folgenden Beispiel **`dynamic_cast`** wird verwendet, um zu bestimmen, ob eine Klasse eine Instanz eines bestimmten Typs ist:

```cpp
// dynamic_cast_clr.cpp
// compile with: /clr
using namespace System;

void PrintObjectType( Object^o ) {
   if( dynamic_cast<String^>(o) )
      Console::WriteLine("Object is a String");
   else if( dynamic_cast<int^>(o) )
      Console::WriteLine("Object is an int");
}

int main() {
   Object^o1 = "hello";
   Object^o2 = 10;

   PrintObjectType(o1);
   PrintObjectType(o2);
}
```

![Klassenhierarchie mit mehrfacher Vererbung](../cpp/media/vc39011.gif "Klassenhierarchie mit mehrfacher Vererbung") <br/>
Klassenhierarchie mit mehrfacher Vererbung

Ein Zeiger auf ein Objekt vom Typ `D` kann sicher in `B` oder `C` umgewandelt werden. Wenn jedoch `D` umgewandelt wird, um auf ein `A`-Objekt zu zeigen, welche Instanz von `A` würde daraus resultieren? Dies führt zu einem Fehler aufgrund mehrdeutiger Umwandlung. Um dieses Problem zu umgehen, können Sie zwei eindeutige Umwandlungen ausführen. Beispiel:

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A {virtual void f();};
class D : public B, public C {virtual void f();};

void f() {
   D* pd = new D;
   A* pa = dynamic_cast<A*>(pd);   // C4540, ambiguous cast fails at runtime
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

Alle anderen Mehrdeutigkeiten können eingeführt werden, wenn Sie virtuelle Basisklassen verwenden. Betrachten Sie die Klassenhierarchie, die in der folgenden Abbildung gezeigt wird.

![Klassenhierarchie mit virtuellen Basisklassen](../cpp/media/vc39012.gif "Klassenhierarchie mit virtuellen Basisklassen") <br/>
Klassenhierarchie mit virtuellen Basisklassen

In dieser Hierarchie ist `A` eine virtuelle Basisklasse. Bei einer Instanz der `E` -Klasse und einem Zeiger auf das unter `A` Objekt schlägt ein-Zeiger auf einen Zeiger **`dynamic_cast`** auf `B` aufgrund von Mehrdeutigkeit fehl. Sie müssen in das vollständige `E`-Objekt zurückumwandeln und anschließend auf eine eindeutige Weise entlang die Hierarchie arbeiten, um zu dem richtigen `B`-Objekt zu gelangen.

Betrachten Sie die Klassenhierarchie, die in der folgenden Abbildung gezeigt wird.

![Klassenhierarchie mit doppelten Basisklassen](../cpp/media/vc39013.gif "Klassenhierarchie mit doppelten Basisklassen") <br/>
Klassenhierarchie mit doppelten Basisklassen

Bei einem Objekt vom Typ `E` und einem Zeiger auf das `D`-Unterobjekt können drei Konvertierungen vorgenommen werden, um vom `D`-Unterobjekt auf das `A`-Unterobjekt zu navigieren, das sich am weitesten links befindet. Sie können eine **`dynamic_cast`** Konvertierung vom `D` Zeiger auf einen `E` Zeiger, dann eine Konvertierung (entweder **`dynamic_cast`** oder eine implizite Konvertierung) von `E` in `B` und schließlich eine implizite Konvertierung von `B` in Ausführen `A` . Beispiel:

```cpp
// dynamic_cast_5.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   E* pe = dynamic_cast<E*>(pd);
   B* pb = pe;   // upcast, implicit conversion
   A* pa = pb;   // upcast, implicit conversion
}
```

Der **`dynamic_cast`** Operator kann auch verwendet werden, um eine "Kreuz Umwandlung" auszuführen. Bei Verwenden der gleichen Klassenhierarchie ist es beispielsweise möglich, einen Zeiger aus dem `B`-Unterobjekt in das `D`-Unterobjekt umzuwandeln, solange das vollständige Objekt vom Typ `E` ist.

Im Fall von übergreifenden Umwandlungen ist es tatsächlich möglich, in nur zwei Schritten die Konvertierung von einem Zeiger auf `D` in einen Zeiger auf das `A`-Unterobjekt, das am weitesten links steht, durchzuführen. Sie können eine übergreifende Umwandlung von `D` in `B` und dann eine implizite Konvertierung von `B` in `A` ausführen. Beispiel:

```cpp
// dynamic_cast_6.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   B* pb = dynamic_cast<B*>(pd);   // cross cast
   A* pa = pb;   // upcast, implicit conversion
}
```

Ein NULL-Zeiger Wert wird durch in den NULL-Zeiger Wert des Zieltyps konvertiert **`dynamic_cast`** .

Wenn Sie `dynamic_cast < type-id > ( expression )` verwenden, wenn `expression` nicht sicher in den Typ `type-id` konvertiert werden kann, führt die Laufzeitüberprüfung zu einem Umwandlungsfehler. Beispiel:

```cpp
// dynamic_cast_7.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;
   // B not derived from A
}
```

Der Wert eines Fehlers bei einer Umwandlung in einen Zeigertyp ist der NULL-Zeiger. Eine fehlgeschlagene Umwandlung in einen Verweistyp löst eine [bad_cast Ausnahme](../cpp/bad-cast-exception.md)aus.   Wenn `expression` nicht auf ein gültiges-Objekt verweist oder darauf verweist, `__non_rtti_object` wird eine-Ausnahme ausgelöst.

Eine Erläuterung der Ausnahme finden Sie unter [typeid](../cpp/typeid-operator.md) `__non_rtti_object` .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der Basisklassenzeiger (Struktur A) auf ein Objekt (Struktur C) erstellt.  Dies sowie die Tatsache, dass virtuelle Funktionen vorhanden sind, ermöglicht Laufzeitpolymorphie.

In dem Beispiel wird außerdem eine nicht virtuelle Funktion in der Hierarchie aufgerufen.

```cpp
// dynamic_cast_8.cpp
// compile with: /GR /EHsc
#include <stdio.h>
#include <iostream>

struct A {
    virtual void test() {
        printf_s("in A\n");
   }
};

struct B : A {
    virtual void test() {
        printf_s("in B\n");
    }

    void test2() {
        printf_s("test2 in B\n");
    }
};

struct C : B {
    virtual void test() {
        printf_s("in C\n");
    }

    void test2() {
        printf_s("test2 in C\n");
    }
};

void Globaltest(A& a) {
    try {
        C &c = dynamic_cast<C&>(a);
        printf_s("in GlobalTest\n");
    }
    catch(std::bad_cast) {
        printf_s("Can't cast to C\n");
    }
}

int main() {
    A *pa = new C;
    A *pa2 = new B;

    pa->test();

    B * pb = dynamic_cast<B *>(pa);
    if (pb)
        pb->test2();

    C * pc = dynamic_cast<C *>(pa2);
    if (pc)
        pc->test2();

    C ConStack;
    Globaltest(ConStack);

   // will fail because B knows nothing about C
    B BonStack;
    Globaltest(BonStack);
}
```

```Output
in C
test2 in B
in GlobalTest
Can't cast to C
```

## <a name="see-also"></a>Weitere Informationen

[Umwandlungs Operatoren](../cpp/casting-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
