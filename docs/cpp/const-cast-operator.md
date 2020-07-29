---
title: const_cast-Operator
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: 36de296d1e871ca759108497922973ddea8e3382
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227555"
---
# <a name="const_cast-operator"></a>const_cast-Operator

Entfernt das **`const`** **`volatile`** -Attribut, das-Attribut und das- **`__unaligned`** Attribut aus einer-Klasse.

## <a name="syntax"></a>Syntax

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Bemerkungen

Ein Zeiger auf einen beliebigen Objekttyp oder einen Zeiger auf einen Datenmember kann explizit in einen Typ konvertiert werden, der mit Ausnahme der **`const`** Qualifizierer, und identisch ist **`volatile`** **`__unaligned`** . Für Zeiger und Verweise verweist das Ergebnis auf das ursprüngliche Objekt. Für Zeiger auf Datenmember, verweist das Ergebnis auf denselben Member wie der ursprüngliche (uncast) Zeiger auf Datenmember. Je nach Typ des verweisenden Objekts, führt ein Schreibvorgang durch den resultierenden Zeiger, Verweis oder Zeiger auf Datenmember möglicherweise zu nicht definiertem Verhalten.

Der-Operator kann nicht verwendet werden **`const_cast`** , um den konstanten Status einer Konstanten Variablen direkt zu überschreiben.

Der- **`const_cast`** Operator konvertiert einen NULL-Zeiger Wert in den NULL-Zeiger Wert des Zieltyps.

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

In der Zeile, die enthält **`const_cast`** , ist der Datentyp des **`this`** Zeigers `const CCTest *` . Der- **`const_cast`** Operator ändert den Datentyp des **`this`** Zeigers in `CCTest *` , sodass der Member `number` geändert werden kann. Die Umwandlung erfolgt nur für den Rest der Anweisung, in der er angezeigt wird.

## <a name="see-also"></a>Siehe auch

[Umwandlungs Operatoren](../cpp/casting-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
