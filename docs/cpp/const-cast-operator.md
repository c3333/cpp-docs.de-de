---
title: const_cast-Operator
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: d2711142e4aa73cc0119949876e7e593067cd45d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180341"
---
# <a name="const_cast-operator"></a>const_cast-Operator

Entfernt die **Konstanten**, **flüchtigen**und **__unaligned** Attribute aus einer Klasse.

## <a name="syntax"></a>Syntax

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Bemerkungen

Ein Zeiger auf einen beliebigen Objekttyp oder einen Zeiger auf einen Datenmember kann explizit in einen Typ konvertiert werden, der mit Ausnahme der **Konstanten für Konstanten**, **flüchtiger**und **__unaligned** identisch ist. Für Zeiger und Verweise verweist das Ergebnis auf das ursprüngliche Objekt. Für Zeiger auf Datenmember, verweist das Ergebnis auf denselben Member wie der ursprüngliche (uncast) Zeiger auf Datenmember. Je nach Typ des verweisenden Objekts, führt ein Schreibvorgang durch den resultierenden Zeiger, Verweis oder Zeiger auf Datenmember möglicherweise zu nicht definiertem Verhalten.

Mit dem **const_cast** -Operator können Sie den konstanten Status einer Konstanten Variablen nicht direkt überschreiben.

Der **const_cast** -Operator konvertiert einen NULL-Zeiger Wert in den NULL-Zeiger Wert des Zieltyps.

## <a name="example"></a>Beispiel

```cpp
// expre_const_cast_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CCTest {
public:
   void setNumber( int );
   void printNumber() const;
private:
   int number;
};

void CCTest::setNumber( int num ) { number = num; }

void CCTest::printNumber() const {
   cout << "\nBefore: " << number;
   const_cast< CCTest * >( this )->number--;
   cout << "\nAfter: " << number;
}

int main() {
   CCTest X;
   X.setNumber( 8 );
   X.printNumber();
}
```

In der Zeile, die die **const_cast**enthält, ist der Datentyp **dieses** Zeigers `const CCTest *`. Der **const_cast** -Operator ändert den Datentyp des **this** -Zeigers in `CCTest *`, sodass der Member `number` geändert werden kann. Die Umwandlung erfolgt nur für den Rest der Anweisung, in der er angezeigt wird.

## <a name="see-also"></a>Weitere Informationen

[Umwandlungsoperatoren](../cpp/casting-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
