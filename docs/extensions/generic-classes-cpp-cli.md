---
title: Generische Klassen (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
ms.openlocfilehash: 78f4bf3abb98aab5e626e8ada538a22bdbca2912
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172359"
---
# <a name="generic-classes-ccli"></a>Generische Klassen (C++/CLI)

Eine generische Klasse wird in der folgenden Form deklariert:

## <a name="syntax"></a>Syntax

```cpp
[attributes]
generic <class-key type-parameter-identifier(s)>
[constraint-clauses]
[accessibility-modifiers] ref class identifier  [modifiers]
[: base-list]
{
class-body
} [declarators] [;]
```

## <a name="remarks"></a>Bemerkungen

In der oben stehenden Syntax werden die folgenden Begriffe verwendet:

*attributes*<br/>
(Optional) Zusätzliche deklarative Informationen. Weitere Informationen zu Attributen und Attributklassen finden Sie unter „Attribute“.

*class-key*<br/>
Entweder **class** oder **typename**.

*type-parameter-identifier(s)* : durch Trennzeichen getrennte Liste der Bezeichner, die die Namen der Typparameter angeben.

*constraint-clauses*<br/>
Eine (nicht durch Trennzeichen getrennte) Liste von **where**-Klauseln, die die Einschränkungen für die Typparameter angeben. Nimmt folgende Form an:

> **Where** *Type-Parameter-Identifier* **:** Einschränkungs *Liste*  **...**

*constraint-list*<br/>
*Class-or-Interface*[`,` *...* ]

*accessibility-modifiers*<br/>
Zugriffsmodifizierer für die generische Klasse. Für die Windows-Runtime ist **private** der einzige zulässige Modifizierer. Für die Common Language Runtime sind **private** und **public** die zulässigen Modifizierer.

*identifier*<br/>
Der Name der generischen Klasse – ein beliebiger gültiger C++-Bezeichner.

*modifiers*<br/>
(Optional) Zulässige Modifizierer sind **sealed** und **abstract**.

*base-list*<br/>
Eine Liste, die eine Basisklasse und alle implementierten Schnittstellen enthält, jeweils durch Trennzeichen getrennt.

*class-body*<br/>
Der Text der Klasse, einschließlich Feldern, Memberfunktionen usw.

*declarators*<br/>
Deklarationen aller Variablen dieses Typs. Beispielsweise: `^`*identifier*[`,` ...]

Sie können generische Klassen wie diese deklarieren (beachten Sie, dass das Schlüsselwort **class** anstelle von **typename** verwendet werden kann). In diesem Beispiel sind `ItemType`, `KeyType` und `ValueType` unbekannte Typen, die an dem Punkt angegeben werden, an dem der Typ `HashTable<int, int>` ein konstruierter Typ des generischen Typs `HashTable<KeyType, ValueType>` ist. Aus einem einzelnen generischen Typ kann eine Reihe verschiedener konstruierter Typen konstruiert werden. Aus generischen Klassen konstruierte Typen werden wie jeder andere Verweisklassentyp behandelt.

```cpp
// generic_classes_1.cpp
// compile with: /clr
using namespace System;
generic <typename ItemType>
ref struct Stack {
   // ItemType may be used as a type here
   void Add(ItemType item) {}
};

generic <typename KeyType, typename ValueType>
ref class HashTable {};

// The keyword class may be used instead of typename:
generic <class ListItem>
ref class List {};

int main() {
   HashTable<int, Decimal>^ g1 = gcnew HashTable<int, Decimal>();
}
```

Sowohl Werttypen (entweder integrierte Typen wie **int** oder **double** oder benutzerdefinierte Werttypen) als auch Verweistypen können als generisches Typargument verwendet werden. Die Syntax innerhalb der generischen Definition ist davon unbenommen die gleiche. Syntaktisch gesehen wird der unbekannte Typ so behandelt, als wäre es ein Verweistyp. Die Runtime kann jedoch ermitteln, ob der tatsächlich verwendete Typ ein Werttyp ist, und den entsprechenden generierten Code für den Direktzugriff auf Member ersetzen. Für Werttypen, die als generische Typargumente verwendet werden, wird kein Boxing durchgeführt. Daher gelten für diese auch nicht die Leistungseinbußen, die mit Boxing einhergehen. Die im Text des generischen Typarguments verwendete Syntax sollte `T^` und `->` anstelle von `.` lauten. Die Verwendung von [ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md) für den Typparameter wird von der Runtime entsprechend als einfache Erstellung eines Werttyps interpretiert, wenn das Typargument ein Werttyp ist.

Sie können auch eine generische Klasse mit [Einschränkungen für generische Typparameter (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) für die Typen deklarieren, die als Typparameter verwendet werden können. Im folgenden Beispiel muss jeder für `ItemType` verwendete Typ die `IItem`-Schnittstelle implementieren. Der Versuch, **int** zu verwenden – der `IItem` nicht implementiert –, löst einen Kompilierzeitfehler aus, weil das Typargument die Einschränkung nicht erfüllt.

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

Generische Klassen im gleichen Namespace können nicht überladen werden, indem einfach nur die Anzahl oder die Typen von Typparametern geändert werden. Wenn sich jedoch jede Klasse in einem anderen Namespace befindet, können sie überladen werden. Sehen Sie sich beispielsweise die beiden Klassen `MyClass` und `MyClass<ItemType>` in den Namespaces `A` und `B` an. Die beiden Klassen können in einem dritten Namespace, C, überladen werden:

```cpp
// generic_classes_3.cpp
// compile with: /clr /c
namespace A {
   ref class MyClass {};
}

namespace B {
   generic <typename ItemType>
   ref class MyClass2 { };
}

namespace C {
   using namespace A;
   using namespace B;

   ref class Test {
      static void F() {
         MyClass^ m1 = gcnew MyClass();   // OK
         MyClass2<int>^ m2 = gcnew MyClass2<int>();   // OK
      }
   };
}
```

Die Basisklasse und die Basisschnittstellen können keine Typparameter sein. Die Basisklasse kann jedoch den Typparameter als Argument enthalten, wie in folgendem Fall:

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

Konstruktoren und Destruktoren werden (wie gewohnt) einmal für jede Objektinstanz ausgeführt, statische Konstruktoren werden einmal für jeden konstruierten Typ ausgeführt.

## <a name="fields-in-generic-classes"></a>Felder in generischen Klassen

Dieser Abschnitt veranschaulicht die Verwendung von Instanz- und statischen Feldern in generischen Klassen.

### <a name="instance-variables"></a>Instanzvariablen

Instanzvariablen einer generischen Klasse können Typen und Variableninitialisierer aufweisen, die beliebige Typparameter aus der einschließenden Klasse enthalten.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden drei verschiedene Instanzen der generischen Klasse „MyClass\<ItemType>“ erstellt. Dabei werden die geeigneten Typargumente verwendet (**int**, **double** und **string**).

```cpp
// generics_instance_fields1.cpp
// compile with: /clr
// Instance fields on generic classes
using namespace System;

generic <typename ItemType>
ref class MyClass {
// Field of the type ItemType:
public :
   ItemType field1;
   // Constructor using a parameter of the type ItemType:
   MyClass(ItemType p) {
   field1 = p;
   }
};

int main() {
   // Instantiate an instance with an integer field:
   MyClass<int>^ myObj1 = gcnew MyClass<int>(123);
   Console::WriteLine("Integer field = {0}", myObj1->field1);

   // Instantiate an instance with a double field:
   MyClass<double>^ myObj2 = gcnew MyClass<double>(1.23);
   Console::WriteLine("Double field = {0}", myObj2->field1);

   // Instantiate an instance with a String field:
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>("ABC");
   Console::WriteLine("String field = {0}", myObj3->field1);
   }
```

```Output
Integer field = 123
Double field = 1.23
String field = ABC
```

## <a name="static-variables"></a>Statische Variablen

Bei Erstellung eines neuen generischen Typs werden neue Instanzen aller statischen Variablen erstellt und alle statischen Konstruktoren für diesen Typ ausgeführt.

Statische Variablen können beliebige Typparameter aus der einschließenden Klasse verwenden.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung statischer Felder und eines statischen Konstruktors innerhalb einer generischen Klasse.

```cpp
// generics_static2.cpp
// compile with: /clr
using namespace System;

interface class ILog {
   void Write(String^ s);
};

ref class DateTimeLog : ILog {
public:
   virtual void Write(String^ s) {
      Console::WriteLine( "{0}\t{1}", DateTime::Now, s);
   }
};

ref class PlainLog : ILog {
public:
   virtual void Write(String^ s) { Console::WriteLine(s); }
};

generic <typename LogType>
where LogType : ILog
ref class G {
   static LogType s_log;

public:
   G(){}
   void SetLog(LogType log) { s_log = log; }
   void F() { s_log->Write("Test1"); }
   static G() { Console::WriteLine("Static constructor called."); }
};

int main() {
   G<PlainLog^>^ g1 = gcnew G<PlainLog^>();
   g1->SetLog(gcnew PlainLog());
   g1->F();

   G<DateTimeLog^>^ g2 = gcnew G<DateTimeLog^>();
   g2->SetLog(gcnew DateTimeLog());

   // prints date
   // g2->F();
}
```

```Output
Static constructor called.
Static constructor called.
Static constructor called.
Test1
```

## <a name="methods-in-generic-classes"></a>Methoden in generischen Klassen

Methoden in generischen Klassen können selbst generisch sein; nicht generische Methoden werden vom Klassentypparameter implizit parametrisiert.

Die folgenden Sonderregeln gelten für Methoden in generischen Klassen:

- Methoden in generischen Klassen können Typparameter als Parameter, Rückgabetypen oder lokale Variablen verwenden.

- Methoden in generischen Klassen können offene oder geschlossene konstruierte Typen als Parameter, Rückgabetypen oder lokale Variablen verwenden.

### <a name="non-generic-methods-in-generic-classes"></a>Nicht generische Methoden in generischen Klassen

Methoden in generischen Klassen, die keine zusätzlichen Typparameter aufweisen, werden üblicherweise als „nicht generisch“ bezeichnet, obwohl sie von der einschließenden generischen Klasse implizit parametrisiert werden.

Die Signatur einer nicht generischen Methode kann einen oder mehrere Typparameter der einschließenden Klasse enthalten, entweder direkt oder in einem offenen konstruierten Typ. Beispiel:

`void MyMethod(MyClass<ItemType> x) {}`

Der Text solcher Methoden kann auch diese Typparameter verwenden.

## <a name="example"></a>Beispiel

Das folgende Beispiel deklariert die nicht generische Methode `ProtectData` in der generischen Klasse `MyClass<ItemType>`. Die Methode verwendet den Klassentypparameter `ItemType` in ihrer Signatur in einem offenen konstruierten Typ.

```cpp
// generics_non_generic_methods1.cpp
// compile with: /clr
// Non-generic methods within a generic class.
using namespace System;

generic <typename ItemType>
ref class MyClass {
public:
   String^ name;
   ItemType data;

   MyClass(ItemType x) {
      data = x;
   }

   // Non-generic method using the type parameter:
   virtual void ProtectData(MyClass<ItemType>^ x) {
      data = x->data;
   }
};

// ItemType defined as String^
ref class MyMainClass: MyClass<String^> {
public:
   // Passing "123.00" to the constructor:
   MyMainClass(): MyClass<String^>("123.00") {
      name = "Jeff Smith";
   }

   virtual void ProtectData(MyClass<String^>^ x) override {
      x->data = String::Format("${0}**", x->data);
   }

   static void Main() {
      MyMainClass^ x1 = gcnew MyMainClass();

      x1->ProtectData(x1);
      Console::WriteLine("Name: {0}", x1->name);
      Console::WriteLine("Amount: {0}", x1->data);
   }
};

int main() {
   MyMainClass::Main();
}
```

```Output
Name: Jeff Smith
Amount: $123.00**
```

## <a name="generic-methods-in-generic-classes"></a>Generische Methoden in generischen Klassen

Sie können generische Methoden sowohl in generischen als auch in nicht generischen Klassen deklarieren. Beispiel:

## <a name="example"></a>Beispiel

```cpp
// generics_method2.cpp
// compile with: /clr /c
generic <typename Type1>
ref class G {
public:
   // Generic method having a type parameter
   // from the class, Type1, and its own type
   // parameter, Type2
   generic <typename Type2>
   void Method1(Type1 t1, Type2 t2) { F(t1, t2); }

   // Non-generic method:
   // Can use the class type param, Type1, but not Type2.
   void Method2(Type1 t1) { F(t1, t1); }

   void F(Object^ o1, Object^ o2) {}
};
```

Die nicht generische Methode ist dennoch generisch in dem Sinne, dass sie vom Typparameter der Klasse parametrisiert wird, aber keine zusätzlichen Typparameter aufweist.

Alle Typen von Methoden in generischen Klassen können generisch sein, einschließlich statischer, virtueller und Instanzmethoden.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Deklarieren und Verwenden von generischen Methoden innerhalb von generischen Klassen:

```cpp
// generics_generic_method2.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class MyClass {
public:
   // Declare a generic method member.
   generic <class Type1>
   String^ MyMethod(ItemType item, Type1 t) {
      return String::Concat(item->ToString(), t->ToString());
   }
};

int main() {
   // Create instances using different types.
   MyClass<int>^ myObj1 = gcnew MyClass<int>();
   MyClass<String^>^ myObj2 = gcnew MyClass<String^>();
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>();

   // Calling MyMethod using two integers.
   Console::WriteLine("MyMethod returned: {0}",
            myObj1->MyMethod<int>(1, 2));

   // Calling MyMethod using an integer and a string.
   Console::WriteLine("MyMethod returned: {0}",
            myObj2->MyMethod<int>("Hello #", 1));

   // Calling MyMethod using two strings.
   Console::WriteLine("MyMethod returned: {0}",
       myObj3->MyMethod<String^>("Hello ", "World!"));

   // generic methods can be called without specifying type arguments
   myObj1->MyMethod<int>(1, 2);
   myObj2->MyMethod<int>("Hello #", 1);
   myObj3->MyMethod<String^>("Hello ", "World!");
}
```

```Output
MyMethod returned: 12
MyMethod returned: Hello #1
MyMethod returned: Hello World!
```

## <a name="using-nested-types-in-generic-classes"></a>Verwenden von geschachtelten Typen in generischen Klassen

Genau wie bei normalen Klassen können Sie andere Typen innerhalb einer generischen Klasse deklarieren. Die Deklaration der geschachtelten Klasse wird von den Typparametern der äußeren Klassendeklaration implizit parametrisiert. Daher wird für jeden konstruierten äußeren Typ eine eigene geschachtelte Klasse definiert. Sehen Sie sich als Beispiel diese Deklaration an:

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

Der Typ `Outer<int>::Inner` ist nicht der gleiche wie der Typ `Outer<double>::Inner`.

Ebenso wie bei generischen Methoden in generischen Klassen können zusätzliche Typparameter für den geschachtelten Typ definiert werden. Wenn Sie den gleichen Typparameter in der inneren und äußeren Klasse verwenden, verbirgt der innere Typparameter den äußeren Typparameter.

```cpp
// generic_classes_6.cpp
// compile with: /clr /c
generic <typename ItemType>
ref class Outer {
   ItemType outer_item;   // refers to outer ItemType

   generic <typename ItemType>
   ref class Inner {
      ItemType inner_item;   // refers to Inner ItemType
   };
};
```

Da es keine Möglichkeit gibt, auf den äußeren Typparameter zu verweisen, gibt der Compiler in dieser Situation eine Warnung aus.

Wenn konstruierte geschachtelte generische Typen benannt werden, wird der Typparameter für den äußeren Typ nicht in der Typparameterliste für den inneren Typ eingeschlossen, auch wenn der innere Typ durch den Typparameter des äußeren Typs implizit parametrisiert wird. Im oben genannten Fall würde der Name eines konstruierten Typs `Outer<int>::Inner<string>` lauten.

Das folgende Beispiel veranschaulicht das Erstellen und Lesen einer verknüpften Liste mithilfe von geschachtelten Typen in generischen Klassen.

## <a name="example"></a>Beispiel

```cpp
// generics_linked_list.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class LinkedList {
// The node class:
public:
   ref class Node {
   // The link field:
   public:
      Node^ next;
      // The data field:
      ItemType item;
   } ^first, ^current;
};

ref class ListBuilder {
public:
   void BuildIt(LinkedList<double>^ list) {
      /* Build the list */
      double m[5] = {0.1, 0.2, 0.3, 0.4, 0.5};
      Console::WriteLine("Building the list:");

      for (int n=0; n<=4; n++) {
         // Create a new node:
         list->current = gcnew LinkedList<double>::Node();

         // Assign a value to the data field:
         list->current->item = m[n];

         // Set the link field "next" to be the same as
         // the "first" field:
         list->current->next = list->first;

         // Redirect "first" to the new node:
         list->first = list->current;

         // Display node's data as it builds:
         Console::WriteLine(list->current->item);
      }
   }

   void ReadIt(LinkedList<double>^ list) {
      // Read the list
      // Make "first" the "current" link field:
      list->current = list->first;
      Console::WriteLine("Reading nodes:");

      // Read nodes until current == null:
      while (list->current != nullptr) {
         // Display the node's data field:
         Console::WriteLine(list->current->item);

         // Move to the next node:
         list->current = list->current->next;
      }
   }
};

int main() {
   // Create a list:
   LinkedList<double>^ aList = gcnew LinkedList<double>();

   // Initialize first node:
   aList->first = nullptr;

   // Instantiate the class, build, and read the list:
   ListBuilder^ myListBuilder = gcnew ListBuilder();
   myListBuilder->BuildIt(aList);
   myListBuilder->ReadIt(aList);
}
```

```Output
Building the list:
0.1
0.2
0.3
0.4
0.5
Reading nodes:
0.5
0.4
0.3
0.2
0.1
```

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>Eigenschaften, Ereignisse, Indexer und Operatoren in generischen Klassen

- Eigenschaften, Ereignisse, Indexer und Operatoren können die Typparameter der einschließenden generischen Klasse als Rückgabewerte, Parameter oder lokale Variablen verwenden, z.B. dann, wenn `ItemType` ein Typparameter einer Klasse ist:

    ```cpp
    public ItemType MyProperty {}
    ```

- Eigenschaften, Ereignisse, Indexer und Operatoren selbst können nicht parametrisiert werden.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt Deklarationen einer Instanzeigenschaft innerhalb einer generischen Klasse.

```cpp
// generics_generic_properties1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref class MyClass {
private:
   property ItemType myField;

public:
   property ItemType MyProperty {
      ItemType get() {
         return myField;
      }
      void set(ItemType value) {
         myField = value;
      }
   }
};

int main() {
   MyClass<String^>^ c = gcnew MyClass<String^>();
   MyClass<int>^ c1 = gcnew MyClass<int>();

   c->MyProperty = "John";
   c1->MyProperty = 234;

   Console::Write("{0}, {1}", c->MyProperty, c1->MyProperty);
}
```

```Output
John, 234
```

## <a name="example"></a>Beispiel

Das nächste Beispiel zeigt eine generische Klasse mit einem Ereignis.

```cpp
// generics_generic_with_event.cpp
// compile with: /clr
// Declare a generic class with an event and
// invoke events.
using namespace System;

// declare delegates
generic <typename ItemType>
delegate void ClickEventHandler(ItemType);

// generic class that defines events
generic <typename ItemType>
ref class EventSource {
public:
   // declare the event OnClick
   event ClickEventHandler<ItemType>^ OnClick;
   void FireEvents(ItemType item) {
      // raises events
      OnClick(item);
   }
};

// generic class that defines methods that will called when
// event occurs
generic <typename ItemType>
ref class EventReceiver {
public:
   void OnMyClick(ItemType item) {
   Console::WriteLine("OnClick: {0}", item);
   }
};

int main() {
   EventSource<String^>^ MyEventSourceString =
                   gcnew EventSource<String^>();
   EventSource<int>^ MyEventSourceInt = gcnew EventSource<int>();
   EventReceiver<String^>^ MyEventReceiverString =
                   gcnew EventReceiver<String^>();
   EventReceiver<int>^ MyEventReceiverInt = gcnew EventReceiver<int>();

   // hook handler to event
   MyEventSourceString->OnClick += gcnew ClickEventHandler<String^>(
       MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick += gcnew ClickEventHandler<int>(
             MyEventReceiverInt, &EventReceiver<int>::OnMyClick);

   // invoke events
   MyEventSourceString->FireEvents("Hello");
   MyEventSourceInt->FireEvents(112);

   // unhook handler to event
   MyEventSourceString->OnClick -= gcnew ClickEventHandler<String^>(
        MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick -= gcnew ClickEventHandler<int>(
        MyEventReceiverInt, &EventReceiver<int>::OnMyClick);
}
```

## <a name="generic-structs"></a>Generische Strukturen

Die Regeln für das Deklarieren und Verwenden von generischen Strukturen sind die gleichen wie die für generische Klassen, mit Ausnahme der Unterschiede, die in der Visual C++-Sprachreferenz dokumentiert sind.

## <a name="example"></a>Beispiel

Das folgende Beispiel deklariert die generische Struktur `MyGenStruct` mit einem Feld, `myField`, und weist diesem Feld Werte verschiedener Typen zu (**int**, **double**, `String^`).

```cpp
// generics_generic_struct1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref struct MyGenStruct {
public:
   ItemType myField;

   ItemType AssignValue(ItemType item) {
      myField = item;
      return myField;
   }
};

int main() {
   int myInt = 123;
   MyGenStruct<int>^ myIntObj = gcnew MyGenStruct<int>();
   myIntObj->AssignValue(myInt);
   Console::WriteLine("The field is assigned the integer value: {0}",
            myIntObj->myField);

   double myDouble = 0.123;
   MyGenStruct<double>^ myDoubleObj = gcnew MyGenStruct<double>();
   myDoubleObj->AssignValue(myDouble);
   Console::WriteLine("The field is assigned the double value: {0}",
            myDoubleObj->myField);

   String^ myString = "Hello Generics!";
   MyGenStruct<String^>^ myStringObj = gcnew MyGenStruct<String^>();
   myStringObj->AssignValue(myString);
   Console::WriteLine("The field is assigned the string: {0}",
            myStringObj->myField);
}
```

```Output
The field is assigned the integer value: 123
The field is assigned the double value: 0.123
The field is assigned the string: Hello Generics!
```

## <a name="see-also"></a>Weitere Informationen

[Generics](generics-cpp-component-extensions.md)
