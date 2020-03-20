---
title: 'Gewusst wie: Definieren und Verarbeiten von Enumerationen in C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: 68f8e113f6199d3b320bc6d241ee3396d2b70a1a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544982"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Gewusst wie: Definieren und Verarbeiten von Enumerationen in C++/CLI

In diesem Thema werden Aufstände C++in/CLI. erläutert.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Angeben des zugrunde liegenden Typs einer Aufzählung

Standardmäßig ist der zugrunde liegende Typ einer Enumeration `int`.  Sie können jedoch den Typ, der signiert werden soll, oder nicht signierte Formen von `int`, `short`, `long`, `__int32`oder `__int64`angeben.  Sie können auch `char` verwenden.

```cpp
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**Ausgabe**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Konvertieren zwischen verwalteten und Standardenumerationen

Es gibt keine Standard Konvertierung zwischen einer Enumeration und einem ganzzahligen Typ. eine Umwandlung ist erforderlich.

```cpp
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**Ausgabe**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>Operatoren und Aufstände

Die folgenden Operatoren sind für aufkommenden in C++/CLI gültig:

|Operator|
|--------------|
|= =! = \< > \<= > =|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

Operatoren &#124; ^ & ~ + +--werden nur für Enumerationen mit ganzzahligen zugrunde liegenden Typen definiert, ohne bool.  Beide Operanden müssen den Enumerationstyp aufweisen.

Der Compiler führt keine statische oder dynamische Überprüfung des Ergebnisses eines Aufzählungs Vorgangs durch. ein Vorgang kann zu einem Wert führen, der sich nicht im Bereich der gültigen Enumeratoren der Enumeration befindet.

> [!NOTE]
>  C++ 11 führt Enumerationstypen Typen in nicht verwaltetem Code ein, die sich deutlich von verwalteten C++Enumerationsklassen in/CLI. unterscheiden. Der c++ 11-Enumerationstypen unterstützt insbesondere nicht dieselben Operatoren wie der verwaltete enumerationstypclass in C++/CLI C++, und/CLI-Quellcode muss einen Zugriffsspezifizierer in verwalteten enumerationsklassendeklarationen bereitstellen, um Sie von nicht verwalteten (c++ 11) enumerationklassendeklarationen zu unterscheiden. Weitere Informationen zu Enumerationsklassen in C++/CLI, C++/CX und c++ 11 finden Sie unter Enumerationsklasse. [enum class](../extensions/enum-class-cpp-component-extensions.md)

```cpp
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```cpp
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**Ausgabe**

```Output
4
1
True
```

## <a name="see-also"></a>Siehe auch

[Enumerationsklasse](../extensions/enum-class-cpp-component-extensions.md)
