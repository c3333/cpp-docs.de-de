---
title: 'Gewusst wie: Definieren und Verarbeiten von Enumerationen in C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: cf3bb23069b2692c0ca4ce270a5b8060195becf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370177"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Gewusst wie: Definieren und Verarbeiten von Enumerationen in C++/CLI

In diesem Thema werden Enumerungen in C++/CLI behandelt.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Angeben des zugrunde liegenden Typs einer Enumere

Standardmäßig ist `int`der zugrunde liegende Typ einer Enumeration .  Sie können jedoch den Typ angeben, der `int`signiert `short` `long`e.V. oder nicht signiert werden soll, und , , , `__int32`, oder `__int64`.  Sie können auch `char` verwenden.

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

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Konvertieren zwischen verwalteten und Standard-Enumerationen

Es gibt keine Standardkonvertierung zwischen einer Enumerat und einem integralen Typ. eine Besetzung erforderlich ist.

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

## <a name="operators-and-enums"></a>Operatoren und Enumerungen

Die folgenden Operatoren sind für Enumerungen in C++/CLI gültig:

|Operator|
|--------------|
|== != \<  >  \<= >=|
|+ -|
|&#124; &|
|++ --|
|sizeof|

Operatoren &#124; - & - ++ -- werden nur für Enumerationen mit integralen zugrunde liegenden Typen definiert, ohne bool.  Beide Operanden müssen vom Enumerationstyp sein.

Der Compiler überprüft keine statische oder dynamische Überprüfung des Ergebnisses eines Enumeratvorgangs. Ein Vorgang kann dazu führen, dass sich ein Wert nicht im Bereich der gültigen Enumeratoren der Enumerate befindet.

> [!NOTE]
> C++11 führt Enumerierungsklassentypen in nicht verwaltetem Code ein, die sich erheblich von verwalteten Enumerumklassen in C++/CLI unterscheiden. Insbesondere unterstützt der C++11-Enumerationsklassentyp nicht dieselben Operatoren wie der verwaltete Enumerationsklassentyp in C++/CLI, und C++/CLI-Quellcode muss einen Eingabehilfenbezeichner in verwalteten Enumerationsklassendeklarationen bereitstellen, um sie von nicht verwalteten (C++11)-Enumerationsklassendeklarationen zu unterscheiden. Weitere Informationen zu Enumerumklassen in C++/CLI, C++/CX und C++11 finden Sie unter [enum class](../extensions/enum-class-cpp-component-extensions.md).

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

[enum class](../extensions/enum-class-cpp-component-extensions.md)
