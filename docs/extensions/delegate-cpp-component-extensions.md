---
title: delegate (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 77cd17eb8c164a08af9ec783f8aba422785609b6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219728"
---
# <a name="delegate--ccli-and-ccx"></a>delegate (C++/CLI und C++/CX)

Deklariert einen Typ, der einen Funktionszeiger repräsentiert.

## <a name="all-runtimes"></a>Alle Laufzeiten

Sowohl Windows-Runtime als auch Common Language Runtime unterstützen Delegaten.

### <a name="remarks"></a>Bemerkungen

**delegate** ist ein kontextbezogenes Schlüsselwort. Weitere Informationen finden Sie unter [Kontextbezogene Schlüsselwörter](context-sensitive-keywords-cpp-component-extensions.md).

Um zur Kompilierzeit zu ermitteln, ob ein Typ ein Delegat ist, verwenden Sie das Typmerkmal `__is_delegate()`. Weitere Informationen finden Sie unter [Compilerunterstützung für Typmerkmale](compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows-Runtime

C++/CX unterstützt Delegaten mit der folgenden Syntax.

### <a name="syntax"></a>Syntax

```cpp
access
delegate
return-type
delegate-type-identifier
(
[ parameters ]
)
```

### <a name="parameters"></a>Parameter

*zu*<br/>
optionale Der Zugriff auf den Delegaten, der **`public`** (Standardeinstellung) oder sein kann **`private`** . Der Funktionsprototyp kann auch mit den **`const`** Schlüsselwörtern oder qualifiziert werden **`volatile`** .

*Rückgabetyp*<br/>
Der Rückgabetyp des Funktionsprototyps.

*delegate-type-identifier*<br/>
Der Name des deklarierten Delegattyps.

*parameters*<br/>
(Optional) Die Typen und Bezeichner des Funktionsprototyps.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie den *delegate-type-identifier*, um ein Ereignis mit dem gleichen Prototypen wie der Delegat zu deklarieren. Weitere Informationen finden Sie unter [Delegaten (C++/CX)](../cppcx/delegates-c-cx.md).

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Die Common Language Runtime unterstützt Delegaten mit der folgenden Syntax.

### <a name="syntax"></a>Syntax

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>Parameter

*zu*<br/>
(Optional) Der Zugriff auf den Delegaten außerhalb der Assembly kann „public“ oder „private“ lauten.  Der Standardwert ist „private“.  Innerhalb einer Klasse kann ein Delegat einen beliebigen Zugriff aufweisen.

*function_declaration*<br/>
Die Signatur der Funktion, die an den Delegaten gebunden werden kann. Der Rückgabetyp eines Delegaten kann jeder verwaltete Typ sein. Aus Gründen der Interoperabilität empfiehlt es sich, dass der Rückgabetyp eines Delegaten ein CLS-Typ ist.

Um einen ungebundenen Delegaten zu definieren, sollte der erste Parameter in *Function_declaration* der Typ des **`this`** Zeigers für das Objekt sein.

### <a name="remarks"></a>Bemerkungen

Delegaten unterstützen eine mehrfache Umwandlung: Der Funktionszeiger kann an eine oder mehrere Methoden innerhalb einer verwalteten Klasse gebunden sein. Das Schlüsselwort **delegate** definiert einen Multicastdelegattypen mit einer bestimmten Methodensignatur.

Ein Delegat kann auch an die Methode einer Wertklasse gebunden sein, wie beispielsweise im Fall einer statischen Methode.

Ein Delegat weist die folgenden Merkmale auf:

- Er erbt von `System::MulticastDelegate`.

- Er verfügt über einen Konstruktor, der zwei Argumente akzeptiert: einen Zeiger auf eine verwaltete Klasse oder NULL (im Fall der Bindung an eine statische Methode) und eine vollständig qualifizierte Methode des angegebenen Typs.

- Er verfügt über eine Methode mit dem Namen `Invoke`, deren Signatur der deklarierten Signatur des Delegaten entspricht.

Wenn ein Delegat aufgerufen wird, werden die entsprechenden Funktionen in der Reihenfolge aufgerufen, in der sie angefügt wurden.

Der Rückgabewert eines Delegaten ist der Rückgabewert aus der letzten angefügten Memberfunktion.

Delegaten können nicht überladen werden.

Delegaten können gebunden oder nicht gebunden sein.

Wenn Sie einen gebundenen Delegaten instanziieren, muss das erste Argument ein Objektverweis sein. Das zweite Argument einer Delegatinstanziierung muss entweder die Adresse einer Methode eines verwalteten Klassenobjekts oder ein Zeiger auf eine Methode eines Werttyps sein. Das zweite Argument einer Delegatinstanziierung muss die Methode mit der vollständigen Syntax im Gültigkeitsbereich der Klasse benennen und den address-of-Operator anwenden.

Wenn Sie einen nicht gebundenen Delegaten instanziieren, muss das zweite Argument entweder die Adresse einer Methode eines verwalteten Klassenobjekts oder ein Zeiger auf eine Methode eines Werttyps sein. Das Argument muss die Methode mit der vollständigen Syntax im Gültigkeitsbereich der Klasse benennen und den address-of-Operator anwenden.

Beim Erstellen eines Delegaten für eine statische oder globale Funktion ist nur ein Parameter erforderlich: die Funktion (optional die Adresse der Funktion).

Weitere Informationen über Delegaten finden Sie unter folgenden Links:

- [Vorgehensweise: Definieren und Verwenden von Delegaten (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [Generische Delegaten (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Beispiel zeigt, wie Sie Delegaten deklarieren, initialisieren und aufrufen.

```cpp
// mcppv2_delegate.cpp
// compile with: /clr
using namespace System;

// declare a delegate
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      Console::WriteLine("in func1 {0}", i);
   }

   void func2(int i) {
      Console::WriteLine("in func2 {0}", i);
   }

   static void func3(int i) {
      Console::WriteLine("in static func3 {0}", i);
   }
};

int main () {
   A ^ a = gcnew A;

   // declare a delegate instance
   MyDel^ DelInst;

   // test if delegate is initialized
   if (DelInst)
      DelInst(7);

   // assigning to delegate
   DelInst = gcnew MyDel(a, &A::func1);

   // invoke delegate
   if (DelInst)
      DelInst(8);

   // add a function
   DelInst += gcnew MyDel(a, &A::func2);

   DelInst(9);

   // remove a function
   DelInst -= gcnew MyDel(a, &A::func1);

   // invoke delegate with Invoke
   DelInst->Invoke(10);

   // make delegate to static function
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);
   StaticDelInst(11);
}
```

```Output
in func1 8

in func1 9

in func2 9

in func2 10

in static func3 11
```

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
