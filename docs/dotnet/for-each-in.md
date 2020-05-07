---
title: for each, in
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: f1f5523eb22bd8a839da9b3f73dd6c3718b4fd63
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825791"
---
# <a name="for-each-in"></a>for each, in

Durchläuft ein Array oder eine Auflistung. Dieses nicht standardmäßige Schlüsselwort ist sowohl in C++/CLI und nativen C++-Projekten verfügbar. Seine Verwendung wird jedoch nicht empfohlen. Verwenden Sie stattdessen eine Standard [Bereichs basierte for-Anweisung (C++)](../cpp/range-based-for-statement-cpp.md) .

## <a name="all-runtimes"></a>Alle Laufzeiten

### <a name="syntax"></a>Syntax

> **for each (** *Typbezeichner* *identifier* **in** *Ausdruck* **) {**\
> &nbsp;&nbsp;&nbsp;&nbsp;*Äußerungen*\
> **}**

### <a name="parameters"></a>Parameter

*type*<br/>
Der `identifier`-Typ.

*Bezeichner*<br/>
Die Iterationsvariable, die das Auflistungselement darstellt.  Wenn `identifier` ein nach [Verfolgungs Verweis Operator](../extensions/tracking-reference-operator-cpp-component-extensions.md)ist, können Sie das Element ändern.

*expression*<br/>
Ein Arrayausdruck oder eine Auflistung. Das Auflistungselement muss zulassen, dass der Compiler es in den Typ `identifier` konvertieren kann.

*Äußerungen*<br/>
Eine oder mehrere auszuführende Anweisungen.

### <a name="remarks"></a>Bemerkungen

Die `for each`-Anweisung wird zum Durchlaufen einer Auflistung verwendet. Sie können Elemente in einer Auflistung ändern, aber keine Elemente hinzufügen oder löschen.

Die- *Anweisungen* werden für jedes Element im Array oder in der Auflistung ausgeführt. Nachdem die Iteration alle Elemente in der Auflistung durchlaufen hat, wird die Steuerung an die nächste Anweisung, die auf den `for each`-Block folgt, übergeben.

`for each`und `in` sind [kontextabhängige Schlüsselwörter](../extensions/context-sensitive-keywords-cpp-component-extensions.md).

Weitere Informationen finden Sie unter:

- [Eine C++-Standardbibliotheksauflistung mit der for-each-Klausel durchlaufen](../dotnet/iterating-over-stl-collection-by-using-for-each.md)

- [Vorgehensweise: Durchlaufen von Arrays mit der for-each-Klausel](../dotnet/how-to-iterate-over-arrays-with-for-each.md)

- [Vorgehensweise: Durchlaufen einer generischen Auflistung mit der for-each-Klausel](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)

- [Vorgehensweise: Durchlaufen einer benutzerdefinierten Auflistung mit der for-each-Klausel](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: **/ZW**

### <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie `for each` zum Durchlaufen einer Zeichenfolge verwendet wird.

```cpp
// for_each_string1.cpp
// compile with: /ZW
#include <stdio.h>
using namespace Platform;

ref struct MyClass {
   property String^ MyStringProperty;
};

int main() {
   String^ MyString = ref new String("abcd");

   for each ( char c in MyString )
      wprintf("%c", c);

   wprintf("/n");

   MyClass^ x = ref new MyClass();
   x->MyStringProperty = "Testing";

   for each( char c in x->MyStringProperty )
      wprintf("%c", c);
}
```

**Ausgabe**

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>Common Language Runtime

**Anmerkungen**

Die CLR-Syntax ist identisch mit der Syntax **all Runtimes** , außer wie folgt.

*expression*<br/>
Ein verwalteter Arrayausdruck oder eine Auflistung. Das Auflistungs Element muss so lauten, dass der Compiler es <xref:System.Object> von in den *Bezeichnertyp* konvertieren kann.

*Expression* wertet einen Typ aus, der <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>oder einen Typ implementiert, der eine `GetEnumerator` Methode definiert, die entweder einen Typ zurück <xref:System.Collections.IEnumerator> gibt, der implementiert oder alle in `IEnumerator`definierten Methoden deklariert.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: **/clr**

### <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie `for each` zum Durchlaufen einer Zeichenfolge verwendet wird.

```cpp
// for_each_string2.cpp
// compile with: /clr
using namespace System;

ref struct MyClass {
   property String ^ MyStringProperty;
};

int main() {
   String ^ MyString = gcnew String("abcd");

   for each ( Char c in MyString )
      Console::Write(c);

   Console::WriteLine();

   MyClass ^ x = gcnew MyClass();
   x->MyStringProperty = "Testing";

   for each( Char c in x->MyStringProperty )
      Console::Write(c);
}
```

**Ausgabe**

```Output
abcd

Testing
```

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md)
