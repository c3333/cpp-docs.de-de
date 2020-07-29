---
title: interface-Klasse (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: e7847f71502354189e874d505414b4a45b74ab45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228699"
---
# <a name="interface-class--ccli-and-ccx"></a>interface-Klasse (C++/CLI und C++/CX)

Deklariert eine Schnittstelle.  Weitere Informationen zu nativen Schnittstellen finden Sie unter [__interface](../cpp/interface.md).

## <a name="all-runtimes"></a>Alle Laufzeiten

### <a name="syntax"></a>Syntax

```cpp
interface_access
interface class
name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>Parameter

*interface_access*<br/>
Die Möglichkeit des Zugriffs auf eine Schnittstelle außerhalb der Assembly.  Mögliche Werte sind **`public`** und **`private`** .  **`private`** der Standardwert ist. Geschachtelte Schnittstellen können keinen *interface_access*-Bezeichner haben.

*name*<br/>
Der Name der Schnittstelle.

*inherit_access*<br/>
Die Möglichkeit des Zugriffs auf *base_interface*.  Die einzige zulässige Barrierefreiheit für eine Basisschnittstelle ist **`public`** (Standard).

*base_interface*<br/>
(Optional) Eine Basisschnittstelle für die Schnittstelle *name*.

### <a name="remarks"></a>Bemerkungen

**interface struct** entspricht **interface class**.

Eine Schnittstelle kann Deklarationen für Funktionen, Ereignisse und Eigenschaften enthalten.  Auf alle Schnittstellenmember kann öffentlich zugegriffen werden. Eine Schnittstelle kann auch statische Datenelemente, Funktionen, Ereignisse und Eigenschaften enthalten, und diese statischen Member müssen in der Schnittstelle definiert werden.

Eine Schnittstelle definiert, wie eine Klasse implementiert werden kann. Eine Schnittstelle ist keine Klasse, und Klassen können nur Schnittstellen implementieren. Wenn eine Klasse eine Funktion definiert, die in einer Schnittstelle deklariert wird, wird die Funktion implementiert, nicht überschrieben. Aus diesem Grund umfasst die Namenssuche keine Schnittstellenmember.

Eine Klasse oder Struktur, die von einer Schnittstelle abgeleitet wird, muss alle Member der Schnittstelle implementieren. Bei der Implementierung des *Namens* der Schnittstelle müssen Sie auch die Schnittstellen in der `base_interface`-Liste implementieren.

Weitere Informationen finden Sie unter

- [Statische Schnittstellenkonstruktoren](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [Generische Schnittstellen (C++/CLI)](generic-interfaces-visual-cpp.md)

Informationen zu anderen CLR-Typen finden Sie unter [Klassen und Strukturen](classes-and-structs-cpp-component-extensions.md).

Sie können mit `__is_interface_class(type)` zum Zeitpunkt der Kompilierung ermitteln, ob ein Typ eine Schnittstelle ist. Weitere Informationen finden Sie unter [Compilerunterstützung für Typmerkmale](compiler-support-for-type-traits-cpp-component-extensions.md).

In der Entwicklungsumgebung können Sie F1-Hilfe zu diesen Schlüsselwörtern aufrufen, indem Sie das-Schlüsselwort (z. b **`interface class`** .) markieren und F1 drücken.

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="remarks"></a>Bemerkungen

(Es gibt keine Hinweise für diese Sprachfunktion, die nur für Windows-Runtime gelten.)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Bemerkungen

(Es gibt keine Hinweise für diese Sprachfunktion, die nur für Common Language Runtime gelten.)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Im folgenden Codebeispiel wird veranschaulicht, wie eine Schnittstelle das Verhalten einer Klickfunktion definieren kann.

```cpp
// mcppv2_interface_class.cpp
// compile with: /clr
using namespace System;

public delegate void ClickEventHandler(int, double);

// define interface with nested interface
public interface class Interface_A {
   void Function_1();

   interface class Interface_Nested_A {
      void Function_2();
   };
};

// interface with a base interface
public interface class Interface_B : Interface_A {
   property int Property_Block;
   event ClickEventHandler^ OnClick;
   static void Function_3() { Console::WriteLine("in Function_3"); }
};

// implement nested interface
public ref class MyClass : public Interface_A::Interface_Nested_A {
public:
   virtual void Function_2() { Console::WriteLine("in Function_2"); }
};

// implement interface and base interface
public ref class MyClass2 : public Interface_B {
private:
   int MyInt;

public:
   // implement non-static function
   virtual void Function_1() { Console::WriteLine("in Function_1"); }

   // implement property
   property int Property_Block {
      virtual int get() { return MyInt; }
      virtual void set(int value) { MyInt = value; }
   }
   // implement event
   virtual event ClickEventHandler^ OnClick;

   void FireEvents() {
      OnClick(7, 3.14159);
   }
};

// class that defines method called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }
};

int main() {
   // call static function in an interface
   Interface_B::Function_3();

   // instantiate class that implements nested interface
   MyClass ^ x = gcnew MyClass;
   x->Function_2();

   // instantiate class that implements interface with base interface
   MyClass2 ^ y = gcnew MyClass2;
   y->Function_1();
   y->Property_Block = 8;
   Console::WriteLine(y->Property_Block);

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   y->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // invoke events
   y->FireEvents();

   // unhook handler to event
   y->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // call implemented function via interface handle
   Interface_A^ hi = gcnew MyClass2();
   hi->Function_1();
}
```

```Output
in Function_3

in Function_2

in Function_1

8

OnClick: 7, 3.14159

in Function_1
```

Das folgende Codebeispiel zeigt zwei Möglichkeiten zum Implementieren von Funktionen mit derselben, in mehreren Schnittstellen deklarierten Signatur, und wo diese Schnittstellen von einer Klasse verwendet werden.

```cpp
// mcppv2_interface_class_2.cpp
// compile with: /clr /c
interface class I {
   void Test();
   void Test2();
};

interface class J : I {
   void Test();
   void Test2();
};

ref struct R : I, J {
   // satisfies the requirement to implement Test in both interfaces
   virtual void Test() {}

   // implement both interface functions with explicit overrides
   virtual void A() = I::Test2 {}
   virtual void B() = J::Test2 {}
};
```

## <a name="see-also"></a>Siehe auch

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
