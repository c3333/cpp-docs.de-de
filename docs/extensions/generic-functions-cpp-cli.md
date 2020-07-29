---
title: Generische Funktionen (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
ms.openlocfilehash: 3d648a23176786985a7ca1e22165c7c5a695e601
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216010"
---
# <a name="generic-functions-ccli"></a>Generische Funktionen (C++/CLI)

Eine generische Funktion ist eine Funktion, die mit Typparametern deklariert wird. Beim Aufruf werden anstelle der Typparameter die tatsächlichen Typen verwendet.

## <a name="all-platforms"></a>Alle Plattformen

### <a name="remarks"></a>Bemerkungen

Dieses Feature kann nicht auf allen Plattformen angewendet werden.

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="remarks"></a>Bemerkungen

Dieses Feature wird in der Windows-Runtime nicht unterstützt.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Eine generische Funktion ist eine Funktion, die mit Typparametern deklariert wird. Beim Aufruf werden anstelle der Typparameter die tatsächlichen Typen verwendet.

### <a name="syntax"></a>Syntax

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>Parameter

*attributes*<br/>
(Optional) Zusätzliche deklarative Informationen. Weitere Informationen zu Attributen und Attributklassen finden Sie unter „Attribute“.

*Modifizierer*<br/>
(Optional) Ein Modifizierer für die Funktion, z.B. „static“.  **`virtual`** ist nicht zulässig, da virtuelle Methoden möglicherweise nicht generisch sind.

*Rückgabetyp*<br/>
Der von der Methode zurückgegebene Typ. Wenn der Rückgabetyp leer ist, wird kein Rückgabewert benötigt.

*identifier*<br/>
Der Funktionsname.

*type-parameter identifier(s)*<br/>
Durch Trennzeichen getrennte Liste mit Bezeichnern.

*formal-parameters*<br/>
(Optional) Parameterliste.

*type-parameter-constraints-clauses*<br/>
Gibt Einschränkungen für die Typen an, die als Typargumente verwendet werden können, und nimmt die Form an, die in [Einschränkungen für generische Typparameter (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) angegeben ist.

*Funktions Text*<br/>
Der Text der Methode, der auf die Bezeichner der Typparameter verweisen kann.

### <a name="remarks"></a>Bemerkungen

Generische Funktionen sind Funktionen, die mit einem generischen Typparameter deklariert werden. Es kann sich um Methoden in einer Klasse oder in einer Struktur oder um eigenständige Funktionen handeln. Eine einzelne generische Deklaration deklariert implizit eine Gruppe von Funktionen, die sich nur in der Ersetzung der tatsächlichen Typen für den generischen Typparameter unterscheiden.

Ein Klassen- oder Strukturkonstruktor kann nicht mit generischen Typparametern deklariert werden.

Beim Aufruf wird der generische Typparameter durch einen tatsächlichen Typ ersetzt. Der tatsächliche Typ kann in spitzen Klammern mit einer Syntax explizit angegeben werden, die der eines Vorlagenfunktionsaufrufs gleicht. Beim Aufruf ohne die Typparameter versucht der Compiler, den tatsächlichen Typ aus den im Funktionsaufruf übergebenen Parametern abzuleiten. Wenn das gewünschte Typargument nicht aus den verwendeten Parametern abgeleitet werden kann, gibt der Compiler einen Fehler aus.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Codebeispiel veranschaulicht eine generische Funktion.

```cpp
// generics_generic_function_1.cpp
// compile with: /clr
generic <typename ItemType>
void G(int i) {}

ref struct A {
   generic <typename ItemType>
   void G(ItemType) {}

   generic <typename ItemType>
   static void H(int i) {}
};

int main() {
   A myObject;

   // generic function call
   myObject.G<int>(10);

   // generic function call with type parameters deduced
   myObject.G(10);

   // static generic function call
   A::H<int>(10);

   // global generic function call
   G<int>(10);
}
```

Generische Funktionen können basierend auf Signatur oder Stelligkeit – der Anzahl von Typparametern in einer Funktion – überladen werden. Generische Funktionen können auch mit nicht gleichnamigen generischen Funktionen überladen werden, sofern sich die Funktionen in einigen Typparametern unterscheiden. Folgende Funktionen können beispielsweise überladen werden:

```cpp
// generics_generic_function_2.cpp
// compile with: /clr /c
ref struct MyClass {
   void MyMythod(int i) {}

   generic <class T>
   void MyMythod(int i) {}

   generic <class T, class V>
   void MyMythod(int i) {}
};
```

Das folgende Beispiel verwendet eine generische Funktion, um das erste Element in einem Array zu suchen. Es deklariert `MyClass`, die von der Basisklasse `MyBaseClass` erbt. `MyClass` enthält die generische Funktion `MyFunction`, die innerhalb der Basisklasse eine andere generische Funktion aufruft: `MyBaseClassFunction`. In `main` wird die generische Funktion `MyFunction` mithilfe von unterschiedlichen Typargumenten aufgerufen.

```cpp
// generics_generic_function_3.cpp
// compile with: /clr
using namespace System;

ref class MyBaseClass {
protected:
   generic <class ItemType>
   ItemType MyBaseClassFunction(ItemType item) {
      return item;
   }
};

ref class MyClass: public MyBaseClass {
public:
   generic <class ItemType>
   ItemType MyFunction(ItemType item) {
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);
   }
};

int main() {
   MyClass^ myObj = gcnew MyClass();

   // Call MyFunction using an int.
   Console::WriteLine("My function returned an int: {0}",
                           myObj->MyFunction<int>(2003));

   // Call MyFunction using a string.
   Console::WriteLine("My function returned a string: {0}",
   myObj->MyFunction<String^>("Hello generic functions!"));
}
```

```Output
My function returned an int: 2003
My function returned a string: Hello generic functions!
```

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)<br/>
[Generics](generics-cpp-component-extensions.md)
