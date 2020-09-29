---
title: 'Vorgehensweise: definieren und Verarbeiten von Klassen und Strukturen (C++/CLI)'
description: Erstellen und Verwenden von benutzerdefinierten Klassen-und Strukturtypen im C++/CLI-Code.
ms.date: 09/25/2020
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 17d0885d42febc1d2789c8711b54a76066ee8176
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414580"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Vorgehensweise: definieren und Verarbeiten von Klassen und Strukturen (C++/CLI)

In diesem Artikel wird gezeigt, wie Sie benutzerdefinierte Verweis Typen und Werttypen in C++ definieren und verwenden können/CLI.

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a> Objekt Instanziierung

Verweis Typen (Ref) können nur auf dem verwalteten Heap instanziiert werden, nicht auf dem Stapel oder auf dem systemeigenen Heap. Werttypen können auf dem Stapel oder dem verwalteten Heap instanziiert werden.

```cpp
// mcppv2_ref_class2.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;

   // nested class
   ref class MyClass2 {
   public:
      int i;
   };

   // nested interface
   interface struct MyInterface {
      void f();
   };
};

ref class MyClass2 : public MyClass::MyInterface {
public:
   virtual void f() {
      System::Console::WriteLine("test");
   }
};

public value struct MyStruct {
   void f() {
      System::Console::WriteLine("test");
   }
};

int main() {
   // instantiate ref type on garbage-collected heap
   MyClass ^ p_MyClass = gcnew MyClass;
   p_MyClass -> i = 4;

   // instantiate value type on garbage-collected heap
   MyStruct ^ p_MyStruct = gcnew MyStruct;
   p_MyStruct -> f();

   // instantiate value type on the stack
   MyStruct p_MyStruct2;
   p_MyStruct2.f();

   // instantiate nested ref type on garbage-collected heap
   MyClass::MyClass2 ^ p_MyClass2 = gcnew MyClass::MyClass2;
   p_MyClass2 -> i = 5;
}
```

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a> Implizit abstrakte Klassen

Eine *implizit abstrakte Klasse* kann nicht instanziiert werden. Eine Klasse ist implizit abstrakt, wenn Folgendes gilt:

- der Basistyp der-Klasse ist eine Schnittstelle.
- die-Klasse implementiert nicht alle Member-Funktionen der-Schnittstelle.

Möglicherweise können Sie keine Objekte aus einer Klasse erstellen, die von einer Schnittstelle abgeleitet ist. Der Grund hierfür könnte sein, dass die Klasse implizit abstrakt ist. Weitere Informationen zu abstrakten Klassen finden Sie unter [abstract](../extensions/abstract-cpp-component-extensions.md).

Im folgenden Codebeispiel wird veranschaulicht, dass die `MyClass` Klasse nicht instanziiert werden kann, da die Funktion `MyClass::func2` nicht implementiert ist. Damit das Beispiel kompiliert werden kann, heben Sie die Auskommentierung der `MyClass::func2`-Funktion auf.

```cpp
// mcppv2_ref_class5.cpp
// compile with: /clr
interface struct MyInterface {
   void func1();
   void func2();
};

ref class MyClass : public MyInterface {
public:
   void func1(){}
   // void func2(){}
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;   // C2259
                                          // To resolve, uncomment MyClass::func2.
}
```

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a> Typsichtbarkeit

Sie können die Sichtbarkeit von Common Language Runtime (CLR)-Typen steuern. Wenn auf die Assembly verwiesen wird, Steuern Sie, ob die Typen in der Assembly außerhalb der Assembly sichtbar oder nicht sichtbar sind.

`public` Gibt an, dass ein Typ für jede Quelldatei sichtbar ist, die eine- `#using` Direktive für die Assembly enthält, die den Typ enthält.  `private` Gibt an, dass ein Typ für Quelldateien nicht sichtbar ist, die eine- `#using` Direktive für die Assembly enthalten, die den Typ enthält. Allerdings sind private Typen in der gleichen Assembly sichtbar. Standardmäßig ist die Sichtbarkeit für eine Klasse auf `private` eingestellt.

Standardmäßig hatten Native Typen vor Visual Studio 2005 öffentliche Zugriffsmöglichkeiten außerhalb der Assembly. Aktivieren Sie [Compilerwarnung (Stufe 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) , damit Sie erkennen können, wo private Native Typen falsch verwendet werden. Verwenden Sie das [make_public](../preprocessor/make-public.md) -Pragma, um öffentlichen Zugriff auf einen systemeigenen Typ in einer Quell Code Datei zu geben, die Sie nicht ändern können.

Weitere Information finden Sie unter [#using Directive (#using-Direktive)](../preprocessor/hash-using-directive-cpp.md).

Das folgende Beispiel zeigt, wie Typen deklariert und ihr Zugriff angegeben werden können und wie dann in der Assembly auf diese Typen zugegriffen werden kann. Wenn auf eine Assembly mit privaten Typen mithilfe von verwiesen wird `#using` , sind nur öffentliche Typen in der Assembly sichtbar.

```cpp
// type_visibility.cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// default accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   Private_Class ^ b = gcnew Private_Class;
   b->Test();

   Private_Class_2 ^ c = gcnew Private_Class_2;
   c->Test();
}
```

**Ausgabe**

```Output
in Public_Class
in Private_Class
in Private_Class_2
```

Nun schreiben wir das vorherige Beispiel so um, dass es als DLL erstellt wird.

```cpp
// type_visibility_2.cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside the assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// by default, accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};
```

Im folgenden Beispiel wird der Zugriff auf Typen außerhalb der Assembly veranschaulicht. In diesem Beispiel verwendet der Client die Komponente, die im vorherigen Beispiel erstellt wurde.

```cpp
// type_visibility_3.cpp
// compile with: /clr
#using "type_visibility_2.dll"
int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   // private types not accessible outside the assembly
   // Private_Class ^ b = gcnew Private_Class;
   // Private_Class_2 ^ c = gcnew Private_Class_2;
}
```

**Ausgabe**

```Output
in Public_Class
```

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a> Element Sichtbarkeit

Sie können den Zugriff auf einen Member einer öffentlichen Klasse innerhalb derselben Assembly von außerhalb der Assembly unterscheiden, indem Sie Paare der Zugriffsspezifizierer **`public`** , und verwenden. **`protected`****`private`**

In dieser Tabelle werden die Auswirkungen der unterschiedlichen Zugriffsspezifizierer zusammengefasst:

|Bezeichner|Wirkung|
|---------------|------------|
|`public`|Auf den Member kann innerhalb und außerhalb der Assembly leicht zugegriffen werden. Weitere Informationen finden Sie unter [`public`](../cpp/public-cpp.md).|
|`private`|Auf den Member kann nicht zugegriffen werden, sowohl innerhalb als auch außerhalb der Assembly.  Weitere Informationen finden Sie unter [`private`](../cpp/private-cpp.md).|
|`protected`|Auf den Member kann innerhalb und außerhalb der Assembly zugegriffen werden. Dies gilt jedoch nur für abgeleitete Typen. Weitere Informationen finden Sie unter [`protected`](../cpp/protected-cpp.md).|
|`internal`|Member ist innerhalb der Assembly öffentlich, aber außerhalb der Assembly privat. `internal` ist ein kontextbezogenes Schlüsselwort.  Weitere Informationen finden Sie unter [Kontextbezogene Schlüsselwörter](../extensions/context-sensitive-keywords-cpp-component-extensions.md).|
|`public protected` - oder - `protected public`|Der Member ist öffentlich innerhalb der Assembly und geschützt außerhalb der Assembly.|
|`private protected` - oder - `protected private`|Der Member ist geschützt innerhalb der Assembly und privat außerhalb der Assembly.|

Das folgende Beispiel zeigt einen öffentlichen Typ mit Membern, die mit den verschiedenen Zugriffsspezifizierer deklariert werden. Anschließend wird der Zugriff auf diese Member innerhalb der Assembly angezeigt.

```cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();
   a->Protected_Public_Function();
   a->Public_Protected_Function();

   // accessible inside but not outside the assembly
   a->Internal_Function();

   // call protected functions
   b->Test();

   // not accessible inside or outside the assembly
   // a->Private_Function();
}
```

**Ausgabe**

```Output
in Public_Function
in Protected_Public_Function
in Public_Protected_Function
in Internal_Function
=======================
in function of derived class
in Protected_Function
in Protected_Private_Function
in Private_Protected_Function
exiting function of derived class
=======================
```

Nun kann das vorherige Beispiel als DLL erstellt werden.

```cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};
```

Im folgenden Beispiel wird die-Komponente verwendet, die im vorherigen Beispiel erstellt wurde. Es wird gezeigt, wie auf die Member von außerhalb der Assembly zugegriffen wird.

```cpp
// compile with: /clr
#using "type_member_visibility_2.dll"
using namespace System;
// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Public_Function();
      Public_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();

   // call protected functions
   b->Test();

   // can't be called outside the assembly
   // a->Private_Function();
   // a->Internal_Function();
   // a->Protected_Private_Function();
   // a->Private_Protected_Function();
}
```

**Ausgabe**

```Output
in Public_Function
=======================
in function of derived class
in Protected_Function
in Protected_Public_Function
in Public_Protected_Function
exiting function of derived class
=======================
```

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a> Öffentliche und private systemeigene Klassen

Ein systemeigener Typ kann von einem verwalteten Typ referenziert werden.  Beispielsweise kann eine Funktion in einem verwalteten Typ einen Parameter aufnehmen, dessen Typ eine systemeigene Struktur ist.  Wenn der verwaltete Typ und die verwaltete Funktion in einer Assembly öffentlich sind, muss der systemeigene Typ ebenfalls öffentlich sein.

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

Anschließend erstellen Sie die Quellcodedatei, die den systemeigenen Typ verwendet:

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

Kompilieren Sie nun einen Client:

```cpp
// compile with: /clr
#using "mcppv2_ref_class3.dll"

#include "mcppv2_ref_class3.h"

int main() {
   R ^r = gcnew R;
   N n;
   r->f(n);
}
```

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a> Statische Konstruktoren

Ein CLR-Typ, z. B. eine Klasse oder Struktur, kann einen statischen Konstruktor enthalten, der zum Initialisieren von statischen Datenmembern verwendet werden kann.  Ein statischer Konstruktor wird höchstens einmal aufgerufen. Der Aufruf erfolgt, bevor auf einen statischen Member des Typs zum ersten Mal zugegriffen wird.

Ein Instanzkonstruktor wird immer nach einen statischen Konstruktor ausgeführt.

Der Compiler kann einen-Konstruktor nicht Inline aufzurufen, wenn die Klasse über einen statischen Konstruktor verfügt. Der Compiler kann einen Rückruf für eine Member-Funktion nicht Inline, wenn die Klasse ein Werttyp ist, über einen statischen Konstruktor verfügt und keinen Instanzkonstruktor aufweist. Die CLR kann den-Befehl Inline Inline, aber der Compiler nicht.

Definieren Sie einen statischen Konstruktor als private Member-Funktion, da er nur von der CLR aufgerufen werden soll.

Weitere Informationen zu statischen Konstruktoren finden Sie unter Gewusst [wie: Definieren eines statischen schnittstellenkonstruktors (C++/CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .

```cpp
// compile with: /clr
using namespace System;

ref class MyClass {
private:
   static int i = 0;

   static MyClass() {
      Console::WriteLine("in static constructor");
      i = 9;
   }

public:
   static void Test() {
      i++;
      Console::WriteLine(i);
   }
};

int main() {
   MyClass::Test();
   MyClass::Test();
}
```

**Ausgabe**

```Output
in static constructor
10
11
```

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a> Semantik des `this` Zeigers

Wenn Sie C++ \cli zum Definieren von Typen verwenden, **`this`** ist der Zeiger in einem Verweistyp vom Typ *handle*. Der **`this`** Zeiger in einem Werttyp ist vom Typ " *innerer Zeiger*".

Diese unterschiedliche Semantik des **`this`** Zeigers kann unerwartetes Verhalten verursachen, wenn ein Standardindexer aufgerufen wird. Im folgenden Beispiel wird die korrekte Methode zum Zugriff auf einen Standardindexer in einem Referenz- und in einem Werttyp veranschaulicht.

Weitere Informationen finden Sie unter [handle to Object Operator (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) und [interior_ptr (C++/CLI)](../extensions/interior-ptr-cpp-cli.md) .

```cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      // accessing default indexer
      Console::WriteLine("{0}", this[3.3]);
   }
};

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      // accessing default indexer
      Console::WriteLine("{0}", this->default[3.3]);
   }
};

int main() {
   A ^ mya = gcnew A();
   B ^ myb = gcnew B();
   myb->Test();
}
```

**Ausgabe**

```Output
10.89
10.89
```

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a> Funktionen zum Ausblenden nach Signatur

In Standard-C++ wird eine Funktion in einer Basisklasse durch eine Funktion ausgeblendet, die denselben Namen in einer abgeleiteten Klasse aufweist, auch wenn die Funktion der abgeleiteten Klasse nicht die gleiche Art oder Anzahl von Parametern hat. Dies wird als Semantik *nach Namen* bezeichnet. In einem Verweistyp wird eine Funktion in einer Basisklasse nur durch eine Funktion in einer abgeleiteten Klasse ausgeblendet, wenn sowohl der Name als auch die Parameterliste identisch sind. Es *wird* als eine verdeckte Semantik bezeichnet.

Eine Klasse gilt als nach Signatur verdeckte Klasse, wenn alle zugehörigen Funktionen in den Metadaten als `hidebysig` gekennzeichnet sind. Standardmäßig verfügen alle Klassen, die unter erstellt werden, **`/clr`** über `hidebysig` Funktionen. Wenn eine Klasse über `hidebysig`-Funktionen verfügt, blendet der Compiler keine Funktionen in den direkten Basisklassen nach Namen aus. Wenn der Compiler jedoch eine nach Namen verdeckte Klasse in einer Vererbungskette erkennt, wird dieses nach Namen verdeckte Verhalten fortgesetzt.

Wenn eine Funktion unter der nach Signatur verdeckten Semantik für ein Objekt aufgerufen wird, identifiziert der Compiler die am meisten abgeleitete Klasse, die eine Funktion enthält, die den Funktionsaufruf erfüllen kann. Wenn es nur eine Funktion in der Klasse gibt, die den Aufruf erfüllt, ruft der Compiler diese Funktion auf. Wenn es mehr als eine Funktion in der Klasse gibt, die den-Befehl erfüllen könnte, verwendet der Compiler Überladungs Auflösungs Regeln, um zu bestimmen, welche Funktion aufgerufen werden soll. Weitere Informationen zu Überladungs Regeln finden Sie unter [Funktions Überladung](../cpp/function-overloading.md).

Für einen angegebenen Funktionsaufruf kann eine Funktion in einer Basisklasse eine Signatur haben, mit der sie etwas besser übereinstimmt als eine Funktion in einer abgeleiteten Klasse. Wenn die Funktion jedoch explizit für ein Objekt der abgeleiteten Klasse aufgerufen wurde, wird die Funktion in der abgeleiteten Klasse aufgerufen.

Da der Rückgabewert nicht als Teil der Signatur einer Funktion betrachtet wird, wird eine Basisklassen Funktion ausgeblendet, wenn Sie denselben Namen hat und dieselbe Art und Anzahl von Argumenten wie eine abgeleitete Klassen Funktion annimmt, auch wenn Sie sich vom Typ des Rückgabewerts unterscheidet.

Das folgende Beispiel zeigt, dass eine Funktion in einer Basisklasse nicht durch eine Funktion in einer abgeleiteten Klasse ausgeblendet wird.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test() {
      Console::WriteLine("Base::Test");
   }
};

ref struct Derived : public Base {
   void Test(int i) {
      Console::WriteLine("Derived::Test");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Test() in the base class will not be hidden
   t->Test();
}
```

**Ausgabe**

```Output
Base::Test
```

Das nächste Beispiel zeigt, dass der Microsoft C++-Compiler eine Funktion in der am stärksten abgeleiteten Klasse aufruft – auch wenn eine Konvertierung erforderlich ist, um einen oder mehrere Parameter zu finden – und nicht eine Funktion in einer Basisklasse aufrufen, die für den Funktionsaufruf besser geeignet ist.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test2(Single d) {
      Console::WriteLine("Base::Test2");
   }
};

ref struct Derived : public Base {
   void Test2(Double f) {
      Console::WriteLine("Derived::Test2");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Base::Test2 is a better match, but the compiler
   // calls a function in the derived class if possible
   t->Test2(3.14f);
}
```

**Ausgabe**

```Output
Derived::Test2
```

Das folgende Beispiel zeigt, dass eine Funktion ausgeblendet werden kann, auch wenn die Basisklasse die gleiche Signatur wie die abgeleitete Klasse hat.

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   int Test4() {
      Console::WriteLine("Base::Test4");
      return 9;
   }
};

ref struct Derived : public Base {
   char Test4() {
      Console::WriteLine("Derived::Test4");
      return 'a';
   }
};

int main() {
   Derived ^ t = gcnew Derived;

   // Base::Test4 is hidden
   int i = t->Test4();
   Console::WriteLine(i);
}
```

**Ausgabe**

```Output
Derived::Test4
97
```

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a> Kopierkonstruktoren

Der C++-Standard besagt, dass ein Kopierkonstruktor aufgerufen wird, wenn ein Objekt so verschoben wird, dass ein Objekt an derselben Adresse erstellt und zerstört wird.

Wenn jedoch eine Funktion, die in MSIL kompiliert wird, eine native Funktion aufruft, bei der eine systemeigene Klasse – oder mehr als ein – als Wert übergeben wird und die native Klasse über einen Kopierkonstruktor oder einen Dekonstruktor verfügt, wird kein Kopierkonstruktor aufgerufen, und das Objekt wird an einer anderen Adresse zerstört, als es erstellt wurde. Dieses Verhalten kann zu Problemen führen, wenn die Klasse über einen Zeiger auf sich selbst verfügt oder wenn der Code Objekte nach Adresse nachverfolgt.

Weitere Informationen finden Sie unter [/CLR (Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md).

Im folgenden Beispiel wird veranschaulicht, wenn ein Kopierkonstruktor nicht generiert wird.

```cpp
// compile with: /clr
#include<stdio.h>

struct S {
   int i;
   static int n;

   S() : i(n++) {
      printf_s("S object %d being constructed, this=%p\n", i, this);
   }

   S(S const& rhs) : i(n++) {
      printf_s("S object %d being copy constructed from S object "
               "%d, this=%p\n", i, rhs.i, this);
   }

   ~S() {
      printf_s("S object %d being destroyed, this=%p\n", i, this);
   }
};

int S::n = 0;

#pragma managed(push,off)
void f(S s1, S s2) {
   printf_s("in function f\n");
}
#pragma managed(pop)

int main() {
   S s;
   S t;
   f(s,t);
}
```

**Ausgabe**

```Output
S object 0 being constructed, this=0018F378
S object 1 being constructed, this=0018F37C
S object 2 being copy constructed from S object 1, this=0018F380
S object 3 being copy constructed from S object 0, this=0018F384
S object 4 being copy constructed from S object 2, this=0018F2E4
S object 2 being destroyed, this=0018F380
S object 5 being copy constructed from S object 3, this=0018F2E0
S object 3 being destroyed, this=0018F384
in function f
S object 5 being destroyed, this=0018F2E0
S object 4 being destroyed, this=0018F2E4
S object 1 being destroyed, this=0018F37C
S object 0 being destroyed, this=0018F378
```

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a> Debugtoren und Finalizer

Dekrektoren in einem Verweistyp führen eine deterministische Bereinigung von Ressourcen durch. Finalizer Bereinigen nicht verwaltete Ressourcen und können vom-Garbage Collector entweder deterministisch oder nicht deterministisch aufgerufen werden. Weitere Informationen zu debugktoren in Standard C++ finden Sie unter [debugtoren](../cpp/destructors-cpp.md).

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Die CLR-Garbage Collector löscht nicht verwendete verwaltete Objekte und gibt Ihren Arbeitsspeicher frei, wenn Sie nicht mehr benötigt werden. Ein Typ kann jedoch Ressourcen verwenden, die dem Garbage Collector nicht bekannt sind, wie er freigegeben werden kann. Diese Ressourcen werden als *nicht verwaltete* Ressourcen (z. b. Native Datei Handles) bezeichnet. Es wird empfohlen, alle nicht verwalteten Ressourcen im Finalizer freizugeben. Der Garbage Collector gibt verwaltete Ressourcen nicht deterministisch frei, sodass es nicht sicher ist, auf verwaltete Ressourcen in einem Finalizer zu verweisen. Das liegt daran, dass es möglich ist, dass die Garbage Collector bereits bereinigt wurde.

Ein Visual C++ Finalizer ist nicht mit der- <xref:System.Object.Finalize%2A> Methode identisch. (In der CLR-Dokumentation werden Finalizer und die <xref:System.Object.Finalize%2A>-Methode synonym verwendet). Die <xref:System.Object.Finalize%2A>-Methode wird vom Garbage Collector aufgerufen, der jeden Finalizer in einer Klassenvererbungskette aufruft. Im Gegensatz zu Visual C++ debugktoren bewirkt ein abgeleiteter Klassen Finalizer nicht, dass der Compiler den Finalizer in allen Basisklassen aufruft.

Da der Microsoft C++-Compiler deterministisches Release von Ressourcen unterstützt, versuchen Sie nicht, die-Methode oder die-Methode zu implementieren <xref:System.IDisposable.Dispose%2A> <xref:System.Object.Finalize%2A> . Wenn Sie jedoch mit diesen Methoden vertraut sind, finden Sie hier ein Beispiel, wie ein Visual C++-Finalizer und ein Destruktor, der den Finalizer aufruft, zum <xref:System.IDisposable.Dispose%2A>-Muster zugeordnet werden:

```cpp
// Visual C++ code
ref class T {
   ~T() { this->!T(); }   // destructor calls finalizer
   !T() {}   // finalizer
};

// equivalent to the Dispose pattern
void Dispose(bool disposing) {
   if (disposing) {
      ~T();
   } else {
      !T();
   }
}
```

Ein verwalteter Typ verwendet möglicherweise auch verwaltete Ressourcen, die Sie lieber deterministisch freigeben möchten. Möglicherweise möchten Sie nicht, dass das Garbage Collector ein Objekt nicht deterministisch freigibt, wenn das Objekt nicht mehr benötigt wird. Durch die deterministische Freigabe von Ressourcen kann die Leistung erheblich gesteigert werden.

Der Microsoft C++-Compiler ermöglicht die Definition eines Dekonstruktors, um Objekte deterministisch zu bereinigen. Verwenden Sie den Destruktor, um alle Ressourcen freizugeben, die Sie deterministisch freigeben möchten.  Wenn ein Finalizer vorhanden ist, rufen Sie ihn im Destruktor auf, um Codeduplikate zu vermeiden.

```cpp
// compile with: /clr /c
ref struct A {
   // destructor cleans up all resources
   ~A() {
      // clean up code to release managed resource
      // ...
      // to avoid code duplication,
      // call finalizer to release unmanaged resources
      this->!A();
   }

   // finalizer cleans up unmanaged resources
   // destructor or garbage collector will
   // clean up managed resources
   !A() {
      // clean up code to release unmanaged resources
      // ...
   }
};
```

Wenn der Code, der ihren Typ verwendet, nicht den Dekonstruktor aufruft, gibt der Garbage Collector schließlich alle verwalteten Ressourcen frei.

Das vorhanden sein eines Debuggers impliziert nicht das vorhanden sein eines Finalizers. Allerdings bedeutet das Vorhandensein eines Finalizers, dass Sie einen Destruktor definieren und den Finalizer von diesem Destruktor aufrufen müssen. Dieser Befehl stellt für die deterministische Freigabe von nicht verwalteten Ressourcen bereit.

Durch Aufrufen des Destruktors wird der Abschluss des Objekts mithilfe von <xref:System.GC.SuppressFinalize%2A> unterdrückt. Wenn der debugtor nicht aufgerufen wird, wird der Finalizer des Typs schließlich vom Garbage Collector aufgerufen.

Sie können die Leistung verbessern, indem Sie den Dekonstruktor aufrufen, um die Ressourcen des Objekts deterministisch zu bereinigen, anstatt die CLR das Objekt nicht deterministisch zu finalisieren.

Code, der in Visual C++ geschrieben und mithilfe von kompiliert **`/clr`** wird, führt den Dekonstruktor eines Typs aus, wenn:

- Ein Objekt, das mithilfe von Stapelsemantik erstellt wird, liegt außerhalb des gültigen Bereichs. Weitere Informationen finden Sie unter [C++ Stack-Semantik für Verweis Typen](../dotnet/cpp-stack-semantics-for-reference-types.md).

- Während der Erstellung des Objekts wird eine Ausnahme ausgelöst.

- Das Objekt ist ein Member in einem Objekt, dessen Destruktor ausgeführt wird.

- Sie können den [Delete](../cpp/delete-operator-cpp.md) -Operator für ein Handle ([handle-to-Object-Operator (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)) aufzurufen.

- Sie rufen den Destruktor explizit auf.

Wenn ein Client, der in einer anderen Sprache geschrieben ist, ihren Typ verwendet, wird der Dekonstruktor wie folgt aufgerufen:

- Bei einem Aufruf von <xref:System.IDisposable.Dispose%2A>.

- Bei einem Aufruf von `Dispose(void)` für den Typ.

- , Wenn der Typ in einer c#-Anweisung den Gültigkeitsbereich verlässt **`using`** .

Wenn Sie keine Stapel Semantik für Verweis Typen verwenden und ein Objekt eines Verweis Typs auf dem verwalteten Heap erstellen, verwenden Sie die [try-schließlich-](../cpp/try-finally-statement.md) Syntax, um sicherzustellen, dass eine Ausnahme nicht verhindert, dass der Destruktor ausgeführt wird.

```cpp
// compile with: /clr
ref struct A {
   ~A() {}
};

int main() {
   A ^ MyA = gcnew A;
   try {
      // use MyA
   }
   finally {
      delete MyA;
   }
}
```

Wenn der Typ einen Destruktor enthält, generiert der Compiler eine `Dispose`-Methode, die <xref:System.IDisposable> implementiert. Wenn ein Typ, der in Visual C++ geschrieben wurde, einen Destruktor enthält, der von einer anderen Sprache verwendet wird, führt der Aufruf von `IDisposable::Dispose` für diesen Typ dazu, dass der Destruktor des Typs aufgerufen wird. Wenn der Typ von einem Visual C++-Client verwendet wird, kann nicht direkt aufgerufen werden. Sie können `Dispose` stattdessen den Dekonstruktor mit dem-Operator aufzurufen **`delete`** .

Wenn der Typ einen Finalizer enthält, generiert der Compiler eine `Finalize(void)`-Methode, die <xref:System.Object.Finalize%2A> überschreibt.

Wenn ein Typ entweder einen Finalizer oder einen Destruktor enthält, generiert der Compiler entsprechend dem Entwurfsmuster eine `Dispose(bool)`-Methode. (Informationen hierzu finden Sie unter Verwerfen eines [Musters](/dotnet/standard/design-guidelines/dispose-pattern)). In Visual C++ kann nicht explizit erstellt oder aufgerufen werden `Dispose(bool)` .

Wenn ein Typ über eine Basisklasse verfügt, die dem Entwurfsmuster entspricht, werden die Destruktoren für alle Basisklassen aufgerufen, wenn der Destruktor für die abgeleitete Klasse aufgerufen wird. (Wenn Ihr Typ in Visual C++ geschrieben ist, stellt der Compiler sicher, dass die Typen dieses Muster implementieren.) Mit anderen Worten, der destrukturtor einer Verweis Klasse wird gemäß dem C++-Standard an seine Basen und Member gebunden. Zuerst wird der Dekonstruktor der Klasse ausgeführt. Anschließend werden die destrukturtoren für ihre Member in umgekehrter Reihenfolge ausgeführt, in der Sie erstellt wurden. Schließlich werden die Dekonstruktoren für die Basisklassen in der Reihenfolge ausgeführt, in der Sie erstellt wurden.

Debugtoren und Finalizer sind innerhalb von Werttypen oder Schnittstellen nicht zulässig.

Ein Finalizer kann nur in einem Referenztyp definiert oder deklariert werden. Wie ein Konstruktor und Destruktor hat ein Finalizer keinen Rückgabetyp.

Nachdem der Finalizer eines Objekts ausgeführt wird, werden die Finalizer in den Basisklassen, beginnend mit dem am wenigsten abgeleiteten Typ, ebenfalls aufgerufen. Finalizer für Datenmember werden nicht automatisch mit dem Finalizer einer Klasse verkettet.

Wenn ein Finalizer einen systemeigenen Zeiger in einem verwalteten Typ löscht, müssen Sie sicherstellen, dass Verweise auf oder über den nativen Zeiger nicht vorzeitig erfasst werden. Ruft den Dekonstruktor für den verwalteten Typ auf, anstatt zu verwenden <xref:System.GC.KeepAlive%2A> .

Zur Kompilierzeit können Sie erkennen, ob ein Typ einen Finalizer oder einen Destruktor enthält. Weitere Informationen finden Sie unter [Compilerunterstützung für Typmerkmale](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

Das nächste Beispiel zeigt zwei Typen: eine mit nicht verwalteten Ressourcen und eine mit verwalteten Ressourcen, die deterministisch freigegeben werden.

```cpp
// compile with: /clr
#include <vcclr.h>
#include <stdio.h>
using namespace System;
using namespace System::IO;

ref class SystemFileWriter {
   FileStream ^ file;
   array<Byte> ^ arr;
   int bufLen;

public:
   SystemFileWriter(String ^ name) : file(File::Open(name, FileMode::Append)),
                                     arr(gcnew array<Byte>(1024)) {}

   void Flush() {
      file->Write(arr, 0, bufLen);
      bufLen = 0;
   }

   ~SystemFileWriter() {
      Flush();
      delete file;
   }
};

ref class CRTFileWriter {
   FILE * file;
   array<Byte> ^ arr;
   int bufLen;

   static FILE * getFile(String ^ n) {
      pin_ptr<const wchar_t> name = PtrToStringChars(n);
      FILE * ret = 0;
      _wfopen_s(&ret, name, L"ab");
      return ret;
   }

public:
   CRTFileWriter(String ^ name) : file(getFile(name)), arr(gcnew array<Byte>(1024) ) {}

   void Flush() {
      pin_ptr<Byte> buf = &arr[0];
      fwrite(buf, 1, bufLen, file);
      bufLen = 0;
   }

   ~CRTFileWriter() {
      this->!CRTFileWriter();
   }

   !CRTFileWriter() {
      Flush();
      fclose(file);
   }
};

int main() {
   SystemFileWriter w("systest.txt");
   CRTFileWriter ^ w2 = gcnew CRTFileWriter("crttest.txt");
}
```

## <a name="see-also"></a>Weitere Informationen

[Klassen und Strukturen](../extensions/classes-and-structs-cpp-component-extensions.md)
