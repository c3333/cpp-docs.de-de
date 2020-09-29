---
title: for each, in
description: C++/CLI für jede, in der Anweisungs Beschreibung und in Beispielen.
ms.date: 09/25/2020
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: 7f228a773dfcbe791e26ea3e1bd8cfba7f3ab028
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413918"
---
# <a name="for-each-in"></a>for each, in

Durchläuft ein Array oder eine Auflistung. Dieses nicht standardmäßige Schlüsselwort ist sowohl in C++/CLI und nativen C++-Projekten verfügbar. Die Verwendung wird jedoch nicht empfohlen. Verwenden Sie stattdessen eine Standard [Bereichs basierte for-Anweisung (C++)](../cpp/range-based-for-statement-cpp.md) .

## <a name="all-runtimes"></a>Alle Laufzeiten

### <a name="syntax"></a>Syntax

> **for each (** *Typbezeichner* *identifier* **in** *Ausdruck* **) {**\
> &nbsp;&nbsp;&nbsp;&nbsp;*Äußerungen*\
> **}**

### <a name="parameters"></a>Parameter

*type*<br/>
Der `identifier`-Typ.

*identifier*<br/>
Die Iterationsvariable, die das Auflistungselement darstellt.  Wenn `identifier` ein nach [Verfolgungs Verweis Operator](../extensions/tracking-reference-operator-cpp-component-extensions.md)ist, können Sie das Element ändern.

*expression*<br/>
Ein Arrayausdruck oder eine Auflistung. Das Auflistungselement muss zulassen, dass der Compiler es in den Typ `identifier` konvertieren kann.

*Äußerungen*<br/>
Eine oder mehrere auszuführende Anweisungen.

### <a name="remarks"></a>Bemerkungen

Die `for each`-Anweisung wird zum Durchlaufen einer Auflistung verwendet. Sie können Elemente in einer Auflistung ändern, aber Sie können keine Elemente hinzufügen oder löschen.

Die- *Anweisungen* werden für jedes Element im Array oder in der Auflistung ausgeführt. Nachdem die Iteration alle Elemente in der Auflistung durchlaufen hat, wird die Steuerung an die nächste Anweisung, die auf den `for each`-Block folgt, übergeben.

`for each` und `in` sind [kontextabhängige Schlüsselwörter](../extensions/context-sensitive-keywords-cpp-component-extensions.md).

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

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Bemerkungen

Die CLR-Syntax ist identisch mit der Syntax **all Runtimes** , außer wie folgt.

*expression*<br/>
Ein verwalteter Arrayausdruck oder eine Auflistung. Das Auflistungs Element muss so lauten, dass der Compiler es von <xref:System.Object> in den *Bezeichnertyp* konvertieren kann.

*Expression* wertet einen Typ aus, der <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> oder einen Typ implementiert, der eine `GetEnumerator` Methode definiert, die entweder einen Typ zurückgibt, der implementiert <xref:System.Collections.IEnumerator> oder alle in definierten Methoden deklariert `IEnumerator` .

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

```Output
abcd

Testing
```

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md)\
[Range-based for-Anweisung (C++)](../cpp/range-based-for-statement-cpp.md)
