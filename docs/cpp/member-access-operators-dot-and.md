---
title: Member-Zugriffs Operatoren:. und-&gt;
ms.date: 11/04/2016
f1_keywords:
- .
- ->
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators [C++]
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
ms.openlocfilehash: 05bab55e1646783e0f8ab9b414d608c912f60a0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178014"
---
# <a name="member-access-operators--and--gt"></a>Member-Zugriffs Operatoren:. und-&gt;

## <a name="syntax"></a>Syntax

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Bemerkungen

Die Member-Zugriffs Operatoren **.** und **->** werden verwendet, um auf Member von Strukturen, Unions und Klassen zu verweisen. Memberzugriffsausdrücke haben den Wert und Typ des ausgewählten Members.

Es gibt zwei Arten von Memberzugriffsausdrücken:

1. In der ersten Form stellt *Postfix-Expression* einen Wert vom Typ "struct", "Class" oder "Union" dar, und *Name* benennt einen Member der angegebenen Struktur, Union oder Klasse. Der Wert des Vorgangs entspricht dem *Namen* und ist ein l-Wert, wenn *Postfix-Expression* ein l-Wert ist.

1. In der zweiten Form stellt *Postfix-Expression* einen Zeiger auf eine Struktur, eine Union oder eine Klasse dar, und *Name* benennt einen Member der angegebenen Struktur, Union oder Klasse. Der Wert ist der *Name* und ist ein l-Wert. Der **->** -Operator dereferenziert den-Zeiger. Aus diesem Grund ergeben die Ausdrücke `e->member` und `(*e).member` (wobei *e* einen Zeiger darstellt) identische Ergebnisse (außer wenn die Operatoren **->** oder <strong>\*</strong> überladen werden).

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden beide Formen des Memberzugriffsoperators dargestellt.

```cpp
// expre_Selection_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Date {
   Date(int i, int j, int k) : day(i), month(j), year(k){}
   int month;
   int day;
   int year;
};

int main() {
   Date mydate(1,1,1900);
   mydate.month = 2;
   cout  << mydate.month << "/" << mydate.day
         << "/" << mydate.year << endl;

   Date *mydate2 = new Date(1,1,2000);
   mydate2->month = 2;
   cout  << mydate2->month << "/" << mydate2->day
         << "/" << mydate2->year << endl;
   delete mydate2;
}
```

```Output
2/1/1900
2/1/2000
```

## <a name="see-also"></a>Weitere Informationen

[Postfixausdrücke](../cpp/postfix-expressions.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Klassen und Strukturen](../cpp/classes-and-structs-cpp.md)<br/>
[Struktur- und Unionmember](../c-language/structure-and-union-members.md)
