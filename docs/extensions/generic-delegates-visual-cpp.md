---
title: Generische Delegaten (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
ms.openlocfilehash: 4c579d0c0ab39a2ddcadfd116bdfed8ba9da2863
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182031"
---
# <a name="generic-delegates-ccli"></a>Generische Delegaten (C++/CLI)

Sie können generische Typparameter mit Delegaten verwenden. Weitere Informationen über Delegaten finden Sie unter [delegate (C++/CLI und C++/CX)](delegate-cpp-component-extensions.md).

## <a name="syntax"></a>Syntax

```cpp
[attributes]
generic < [class | typename] type-parameter-identifiers>
[type-parameter-constraints-clauses]
[accessibility-modifiers] delegate result-type identifier
([formal-parameters]);
```

### <a name="parameters"></a>Parameter

*attributes*<br/>
(Optional) Zusätzliche deklarative Informationen. Weitere Informationen zu Attributen und Attributklassen finden Sie unter „Attribute“.

*type-parameter-identifier(s)*<br/>
Durch Trennzeichen getrennte Liste von Bezeichnern für die Typparameter.

*type-parameter-constraints-clauses*<br/>
Nimmt die in [Einschränkungen für generische Typparameter (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) angegebene Form an.

*accessibility-modifiers*<br/>
(Optional) Zugriffsmodifizierer (z.B. **public**, **private**).

*result-type*<br/>
Der Rückgabetyp des Delegaten.

*identifier*<br/>
Der Name des Delegaten.

*formal-parameters*<br/>
(Optional) Die Parameterliste des Delegaten.

## <a name="example"></a>Beispiel

Die Delegattypparameter werden angegeben, wenn ein Delegatobjekt erstellt wird. Der Delegat und die zugeordnete Methode müssen dieselbe Signatur aufweisen. Im folgenden Beispiel wird ein generischer Delegat deklariert.

```cpp
// generics_generic_delegate1.cpp
// compile with: /clr /c
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);
```

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt Folgendes:

- Sie können nicht das gleiche Delegatobjekt mit unterschiedlichen konstruierten Typen verwenden. Erstellen Sie verschiedene Delegatobjekte für verschiedene Typen.

- Ein generischer Delegat kann einer generischen Methode zugeordnet werden.

- Wenn eine generische Methode ohne Angabe von Typargumenten aufgerufen wird, versucht der Compiler, die Typargumente für den Aufruf abzuleiten.

```cpp
// generics_generic_delegate2.cpp
// compile with: /clr
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);

generic <class ItemType>
ref struct MyGenClass {
   ItemType MyMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

ref struct MyClass {
   generic <class ItemType>
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

int main() {
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();
   GenDelegate<int>^ myDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   GenDelegate<double>^ myDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   GenDelegate<int>^ myDelegate =
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);
}
```

## <a name="example"></a>Beispiel

Das folgende Beispiel deklariert einen generischen Delegaten `GenDelegate<ItemType>` und instanziiert ihn dann, indem er der Methode `MyMethod` zugeordnet wird, die den Typparameter `ItemType` verwendet. Zwei Instanzen des Delegaten (Integer und Double) werden erstellt und aufgerufen.

```cpp
// generics_generic_delegate.cpp
// compile with: /clr
using namespace System;

// declare generic delegate
generic <typename ItemType>
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);

// Declare a generic class:
generic <typename ItemType>
ref class MyGenClass {
public:
   ItemType MyMethod(ItemType p1, ItemType% p2) {
      p2 = p1;
      return p1;
    }
};

int main() {
   int i = 0, j = 0;
   double m = 0.0, n = 0.0;

   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();

   // Instantiate a delegate using int.
   GenDelegate<int>^ MyDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   i = MyDelegate1(123, j);

   Console::WriteLine(
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);

   // Instantiate a delegate using double.
   GenDelegate<double>^ MyDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   m = MyDelegate2(0.123, n);

   Console::WriteLine(
      "Invoking the double delegate: m = {0}, n = {1}", m, n);
}
```

```Output
Invoking the integer delegate: i = 123, j = 123
Invoking the double delegate: m = 0.123, n = 0.123
```

## <a name="see-also"></a>Weitere Informationen

[Generics](generics-cpp-component-extensions.md)
