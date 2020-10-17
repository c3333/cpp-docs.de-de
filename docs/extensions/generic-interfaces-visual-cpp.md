---
title: Generische Schnittstellen (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generic interfaces
- interfaces, generic [C++}
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
ms.openlocfilehash: 61ab514d244c8b41d467d382fa97e30556ccbb32
ms.sourcegitcommit: ced5ff1431ffbd25b20d106901955532723bd188
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92135527"
---
# <a name="generic-interfaces-ccli"></a>Generische Schnittstellen (C++/CLI)

Die Einschränkungen, die für Typparameter in Klassen gelten, sind die gleichen, die auch für Typparameter in Schnittstellen gelten – siehe [Generische Klassen (C++/CLI](generic-classes-cpp-cli.md)).

Die Regeln, die das Überladen von Funktionen steuern, sind für die Funktionen innerhalb von generischen Klassen oder generischen Schnittstellen gleich.

Explizite Implementierungen von Schnittstellenmembern funktionieren mit konstruierten Schnittstellentypen auf die gleiche Weise wie mit einfachen Schnittstellentypen (siehe die folgenden Beispiele).

Weitere Informationen zu Schnittstellen finden Sie unter [Schnittstellenklasse](interface-class-cpp-component-extensions.md).

## <a name="syntax"></a>Syntax

```cpp
[attributes] generic <class-key type-parameter-identifier[, ...]>
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;
```

## <a name="remarks"></a>Hinweise

*attributes*<br/>
(Optional) Zusätzliche deklarative Informationen. Weitere Informationen zu Attributen und Attributklassen finden Sie unter **Attribute**.

*class-key*<br/>
**`class`** oder **`typename`**

*type-parameter-identifier(s)*<br/>
Durch Trennzeichen getrennte Liste mit Bezeichnern.

*type-parameter-constraints-clauses*<br/>
Nimmt die in [Einschränkungen für generische Typparameter (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) angegebene Form an.

*accessibility-modifiers*<br/>
(Optional) Zugriffsmodifizierer (z.B. **public, private**).

*identifier*<br/>
Der Name der Schnittstelle.

*base-list*<br/>
(Optional) Eine durch Trennzeichen getrennte Liste mit expliziten Basisschnittstellen.

*interface-body*<br/>
Deklarationen der Schnittstellenmember.

*Deklaratoren*<br/>
(Optional) Deklarationen von Variablen, basierend auf diesem Typ.

## <a name="example-how-to-declare-and-instantiate-a-generic-interface"></a>Beispiel: Deklarieren und Instanziieren einer generischen Schnittstelle

Das folgende Beispiel veranschaulicht, wie Sie eine generische Schnittstelle deklarieren und instanziieren. In diesem Beispiel wird die generische Schnittstelle `IList<ItemType>` deklariert. Sie wird durch zwei generische Klassen implementiert: `List1<ItemType>` und `List2<ItemType>`. Die Implementierungen unterscheiden sich.

```cpp
// generic_interface.cpp
// compile with: /clr
using namespace System;

// An exception to be thrown by the List when
// attempting to access elements beyond the
// end of the list.
ref class ElementNotFoundException : Exception {};

// A generic List interface
generic <typename ItemType>
public interface class IList {
   ItemType MoveFirst();
   bool Add(ItemType item);
   bool AtEnd();
   ItemType Current();
   void MoveNext();
};

// A linked list implementation of IList
generic <typename ItemType>
public ref class List1 : public IList<ItemType> {
   ref class Node {
      ItemType m_item;

   public:
      ItemType get_Item() { return m_item; };
      void set_Item(ItemType value) { m_item = value; };

      Node^ next;

      Node(ItemType item) {
         m_item = item;
         next = nullptr;
      }
   };

   Node^ first;
   Node^ last;
   Node^ current;

   public:
   List1() {
      first = nullptr;
      last = first;
      current = first;
   }

   virtual ItemType MoveFirst() {
      current = first;
      if (first != nullptr)
        return first->get_Item();
      else
         return ItemType();
   }

   virtual bool Add(ItemType item) {
      if (last != nullptr) {
         last->next = gcnew Node(item);
         last = last->next;
      }
      else {
         first = gcnew Node(item);
         last = first;
         current = first;
      }
      return true;
   }

   virtual bool AtEnd() {
      if (current == nullptr )
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
       if (current != nullptr)
         return current->get_Item();
       else
         throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current != nullptr)
       current = current->next;
      else
        throw gcnew ElementNotFoundException();
   }
};

// An array implementation of IList
generic <typename ItemType>
ref class List2 : public IList<ItemType> {
   array<ItemType>^ item_array;
   int count;
   int current;

   public:

   List2() {
      // not yet possible to declare an
      // array of a generic type parameter
      item_array = gcnew array<ItemType>(256);
      count = current = 0;
   }

   virtual ItemType MoveFirst() {
      current = 0;
      return item_array[0];
   }

   virtual bool Add(ItemType item) {
      if (count < 256)
         item_array[count++] = item;
      else
        return false;
      return true;
   }

   virtual bool AtEnd() {
      if (current >= count)
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
      if (current < count)
        return item_array[current];
      else
        throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current < count)
         ++current;
      else
         throw gcnew ElementNotFoundException();
   }
};

// Add elements to the list and display them.
generic <typename ItemType>
void AddStringsAndDisplay(IList<ItemType>^ list, ItemType item1, ItemType item2) {
   list->Add(item1);
   list->Add(item2);
   for (list->MoveFirst(); ! list->AtEnd(); list->MoveNext())
   Console::WriteLine(list->Current());
}

int main() {
   // Instantiate both types of list.

   List1<String^>^ list1 = gcnew List1<String^>();
   List2<String^>^ list2 = gcnew List2<String^>();

   // Use the linked list implementation of IList.
   AddStringsAndDisplay<String^>(list1, "Linked List", "List1");

   // Use the array implementation of the IList.
   AddStringsAndDisplay<String^>(list2, "Array List", "List2");
}
```

```Output
Linked List
List1
Array List
List2
```

## <a name="example-declare-a-generic-interface"></a>Beispiel: Deklarieren einer generischen Schnittstelle

Dieses Beispiel deklariert eine generische Schnittstelle `IMyGenIface` und zwei nicht generische Schnittstellen `IMySpecializedInt` und `ImySpecializedString`, die `IMyGenIface` spezialisieren. Die beiden spezialisierten Schnittstellen werden dann durch die beiden Klassen `MyIntClass` und `MyStringClass` implementiert. Das Beispiel zeigt, wie Sie generische Schnittstellen spezialisieren, generische und nicht generische Schnittstellen instanziieren und die explizit implementierten Member in den Schnittstellen aufrufen.

```cpp
// generic_interface2.cpp
// compile with: /clr
// Specializing and implementing generic interfaces.
using namespace System;

generic <class ItemType>
public interface class IMyGenIface {
   void Initialize(ItemType f);
};

public interface class IMySpecializedInt: public IMyGenIface<int> {
   void Display();
};

public interface class IMySpecializedString: public IMyGenIface<String^> {
   void Display();
};

public ref class MyIntClass: public IMySpecializedInt {
   int myField;

public:
   virtual void Initialize(int f) {
      myField = f;
   }

   virtual void Display() {
      Console::WriteLine("The integer field contains: {0}", myField);
   }
};

public ref struct MyStringClass: IMySpecializedString {
   String^ myField;

public:
   virtual void Initialize(String^ f) {
      myField = f;
    }

   virtual void Display() {
      Console::WriteLine("The String field contains: {0}", myField);
   }
};

int main() {
   // Instantiate the generic interface.
   IMyGenIface<int>^ myIntObj = gcnew MyIntClass();

   // Instantiate the specialized interface "IMySpecializedInt."
   IMySpecializedInt^ mySpIntObj = (IMySpecializedInt^) myIntObj;

   // Instantiate the generic interface.
   IMyGenIface<String^>^ myStringObj = gcnew MyStringClass();

   // Instantiate the specialized interface "IMySpecializedString."
   IMySpecializedString^ mySpStringObj =
            (IMySpecializedString^) myStringObj;

   // Call the explicitly implemented interface members.
   myIntObj->Initialize(1234);
   mySpIntObj->Display();

   myStringObj->Initialize("My string");
   mySpStringObj->Display();
}
```

```Output
The integer field contains: 1234
The String field contains: My string
```

## <a name="see-also"></a>Siehe auch

[Generics](generics-cpp-component-extensions.md)
