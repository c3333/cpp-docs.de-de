---
title: Verweistyp-Funktionsargumente
ms.date: 08/27/2018
helpviewer_keywords:
- arguments [C++], function
- functions [C++], parameters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
ms.openlocfilehash: 5a409efbe2908954d394656cb989ad6b80a9ce22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233638"
---
# <a name="reference-type-function-arguments"></a>Verweistyp-Funktionsargumente

Häufig ist es effizienter, Verweise anstelle großer Objekte an Funktionen zu übergeben. Dies ermöglicht es dem Compiler, die Adresse des Objekts zu übergeben, während die Syntax beibehalten wird, die verwendet worden wäre, um auf das Objekt zuzugreifen. Betrachten Sie das folgende Beispiel, in dem die `Date`-Struktur verwendet wird:

```cpp
// reference_type_function_arguments.cpp
#include <iostream>

struct Date
{
    short Month;
    short Day;
    short Year;
};

// Create a date of the form DDDYYYY (day of year, year)
// from a Date.
long DateOfYear( Date& date )
{
    static int cDaysInMonth[] = {
        31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31
    };
    long dateOfYear = 0;

    // Add in days for months already elapsed.
    for ( int i = 0; i < date.Month - 1; ++i )
        dateOfYear += cDaysInMonth[i];

    // Add in days for this month.
    dateOfYear += date.Day;

    // Check for leap year.
    if ( date.Month > 2 &&
        (( date.Year % 100 != 0 || date.Year % 400 == 0 ) &&
        date.Year % 4 == 0 ))
        dateOfYear++;

    // Add in year.
    dateOfYear *= 10000;
    dateOfYear += date.Year;

    return dateOfYear;
}

int main()
{
    Date date{ 8, 27, 2018 };
    long dateOfYear = DateOfYear(date);
    std::cout << dateOfYear << std::endl;
}
```

Der vorangehende Code zeigt, dass auf Member einer Struktur, die als Verweis übertragen wird, mithilfe des Member-Selection-Operators (**.**) anstatt mit dem Member-Selection-Operator () zugegriffen wird **->** .

Obwohl Argumente, die als Verweis Typen übertragen werden, die Syntax von nicht Zeiger Typen beachten, behalten Sie ein wichtiges Merkmal von Zeiger Typen bei: Sie sind änderbar, es sei denn, Sie sind als deklariert **`const`** . Da die Absicht des vorangehenden Codes nicht in der Änderung des `date` -Objekts liegt, ist ein geeigneterer Funktionsprototyp:

```cpp
long DateOfYear( const Date& date );
```

Der Prototyp garantiert, dass die Funktion `DateOfYear` das Argument nicht ändert.

Jede Funktion, die einen Referenztyp annimmt, kann ein Objekt desselben Typs annehmen, da es eine Standard Konvertierung von *tykame* in *tykame*gibt <strong>&</strong> .

## <a name="see-also"></a>Siehe auch

[Referenzen](../cpp/references-cpp.md)<br/>
