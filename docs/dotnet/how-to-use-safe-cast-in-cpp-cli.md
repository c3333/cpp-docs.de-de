---
title: 'Vorgehensweise: Verwenden von safe_cast in C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- safe_cast keyword [C++], upcasting
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
ms.openlocfilehash: 56ac19871bcdc5162b959f6d60103387551ac2a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225656"
---
# <a name="how-to-use-safe_cast-in-ccli"></a>Vorgehensweise: Verwenden von safe_cast in C++/CLI

In diesem Artikel wird gezeigt, wie Sie safe_cast in C++/CLI-Anwendungen verwenden. Informationen zu safe_cast in C++/CX finden Sie unter [safe_cast](../extensions/safe-cast-cpp-component-extensions.md).

## <a name="upcasting"></a>Umwandeln

Ein umgewandelt ist eine Umwandlung von einem abgeleiteten Typ in eine seiner Basisklassen. Diese Umwandlung ist sicher und erfordert keine explizite Umwandlungs Notation. Im folgenden Beispiel wird gezeigt, wie ein Upcast mit und ohne diesen Vorgang durchgeführt wird `safe_cast` .

```cpp
// safe_upcast.cpp
// compile with: /clr
using namespace System;
interface class A {
   void Test();
};

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test");
   }

   void Test2() {
      Console::WriteLine("in B::Test2");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test");
   };
};

int main() {
   C ^ c = gcnew C;

   // implicit upcast
   B ^ b = c;
   b->Test();
   b->Test2();

   // upcast with safe_cast
   b = nullptr;
   b = safe_cast<B^>(c);
   b->Test();
   b->Test2();
}
```

```Output
in C::Test
in B::Test2
in C::Test
in B::Test2
```

## <a name="downcasting"></a>Dass

Ein Typumwandlung ist eine Umwandlung von einer Basisklasse in eine Klasse, die von der Basisklasse abgeleitet ist.  Ein Typumwandlung ist nur dann sicher, wenn das Objekt, das zur Laufzeit adressiert wird, tatsächlich ein abgeleitetes Klassenobjekt adressiert.  Anders **`static_cast`** als `safe_cast` führt eine dynamische Überprüfung durch und löst aus, <xref:System.InvalidCastException> Wenn die Konvertierung fehlschlägt.

```cpp
// safe_downcast.cpp
// compile with: /clr
using namespace System;

interface class A { void Test(); };

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test()");
   }

   void Test2() {
      Console::WriteLine("in B::Test2()");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test()");
   }
};

interface class I {};

value struct V : public I {};

int main() {
   A^ a = gcnew C();
   a->Test();
   B^ b = safe_cast<B^>(a);
   b->Test();
   b->Test2();

   V v;
   I^ i = v;   // i boxes V
   V^ refv = safe_cast<V^>(i);

   Object^ o = gcnew B;
   A^ a2= safe_cast<A^>(o);
}
```

```Output
in C::Test()
in C::Test()
in B::Test2()
```

## <a name="safe_cast-with-user-defined-conversions"></a>safe_cast mit benutzerdefinierten Konvertierungen

Im nächsten Beispiel wird gezeigt, wie Sie verwenden können `safe_cast` , um benutzerdefinierte Konvertierungen aufzurufen.

```cpp
// safe_cast_udc.cpp
// compile with: /clr
using namespace System;
value struct V;

ref struct R {
   int x;
   R() {
      x = 1;
   }

   R(int argx) {
      x = argx;
   }

   static operator R::V^(R^ r);
};

value struct V {
   int x;
   static operator R^(V& v) {
      Console::WriteLine("in operator R^(V& v)");
      R^ r = gcnew R();
      r->x = v.x;
      return r;
   }

   V(int argx) {
      x = argx;
   }
};

   R::operator V^(R^ r) {
      Console::WriteLine("in operator V^(R^ r)");
      return gcnew V(r->x);
   }

int main() {
   bool fReturnVal = false;
   V v(2);
   R^ r = safe_cast<R^>(v);   // should invoke UDC
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC
}
```

```Output
in operator R^(V& v
in operator V^(R^ r)
```

## <a name="safe_cast-and-boxing-operations"></a>safe_cast-und boxingvorgänge

### <a name="boxing"></a>Boxing

Boxing ist als eine vom Compiler eingefügte, benutzerdefinierte Konvertierung definiert.  Daher können Sie verwenden `safe_cast` , um einen Wert für den CLR-Heap zu verwenden.

Das folgende Beispiel zeigt das Boxing mit einfachen und benutzerdefinierten Werttypen.  Ein `safe_cast` Kästchen eine Werttyp Variable, die sich auf dem systemeigenen Stapel befindet, sodass Sie einer Variablen im Heap der Garbage Collection zugewiesen werden kann.

```cpp
// safe_cast_boxing.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct V : public I {
   int m_x;

   V(int i) : m_x(i) {}
};

int main() {
   // box a value type
   V v(100);
   I^ i = safe_cast<I^>(v);

   int x = 100;
   V^ refv = safe_cast<V^>(v);
   int^ refi = safe_cast<int^>(x);
}
```

Im nächsten Beispiel wird gezeigt, dass Boxing über eine benutzerdefinierte Konvertierung in einem- `safe_cast` Vorgang Priorität hat.

```cpp
// safe_cast_boxing_2.cpp
// compile with: /clr
static bool fRetval = true;

interface struct I {};
value struct V : public I {
   int x;

   V(int argx) {
      x = argx;
   }

   static operator I^(V v) {
      fRetval = false;
      I^ pi = v;
      return pi;
   }
};

ref struct R {
   R() {}
   R(V^ pv) {}
};

int main() {
   V v(10);
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"
}
```

### <a name="unboxing"></a>Unboxing

Unboxing ist als eine vom Compiler eingefügte, benutzerdefinierte Konvertierung definiert.  Daher können Sie verwenden, `safe_cast` um einen Wert für den CLR-Heap zu entheften.

Unboxing ist eine benutzerdefinierte Konvertierung, aber im Gegensatz zu Boxing muss das Unboxing explizit erfolgen – d. h., es muss von einer- **`static_cast`** , C-oder C-Umwandlung ausgeführt werden, oder das `safe_cast` Unboxing kann nicht implizit ausgeführt werden.

```cpp
// safe_cast_unboxing.cpp
// compile with: /clr
int main() {
   System::Object ^ o = 42;
   int x = safe_cast<int>(o);
}
```

Das folgende Beispiel zeigt das Unboxing mit Werttypen und primitiven Typen.

```cpp
// safe_cast_unboxing_2.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct VI : public I {};

void test1() {
   Object^ o = 5;
   int x = safe_cast<Int32>(o);
}

value struct V {
   int x;
   String^ s;
};

void test2() {
   V localv;
   Object^ o = localv;
   V unboxv = safe_cast<V>(o);
}

void test3() {
   V localv;
   V^ o2 = localv;
   V unboxv2 = safe_cast<V>(o2);
}

void test4() {
   I^ refi = VI();
   VI vi  = safe_cast<VI>(refi);
}

int main() {
   test1();
   test2();
   test3();
   test4();
}
```

## <a name="safe_cast-and-generic-types"></a>safe_cast und generische Typen

Im nächsten Beispiel wird gezeigt, wie Sie verwenden können `safe_cast` , um einen Typumwandlung mit einem generischen Typ auszuführen.

```cpp
// safe_cast_generic_types.cpp
// compile with: /clr
interface struct I {};

generic<class T> where T:I
ref struct Base {
   T t;
   void test1() {}
};

generic<class T> where T:I
ref struct Derived:public Base <T> {};

ref struct R:public I {};

typedef Base<R^> GBase_R;
typedef Derived<R^> GDerived_R;

int main() {
   GBase_R^ br = gcnew GDerived_R();
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);
}
```

## <a name="see-also"></a>Siehe auch

[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)
