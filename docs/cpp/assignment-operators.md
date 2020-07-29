---
title: Zuweisungsoperatoren
description: Die Syntax und Verwendung der C++-Standard sprach Zuweisungs Operatoren.
ms.date: 07/24/2020
f1_keywords:
- =
- '*='
- /=
- '%='
- +=
- -=
- <<=
- '>>='
- '&='
- ^=
- '|='
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], C++
- '&= operator'
- ^= operator
- += operator
- '>>= operator'
- '|= operator'
- operator>>=
- '*= operator'
- '%= operator'
- ^= operator
- operator >>=
- = operator
- -= operator
- /= operator
- <<= operator
ms.assetid: b028cf35-2ff1-4f14-9027-fd53ebec8aa0
ms.openlocfilehash: 91346d06c6fab4f3cd83c5318c88e738daf8d249
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229219"
---
# <a name="assignment-operators"></a>Zuweisungsoperatoren

## <a name="syntax"></a>Syntax

*Ausdrucks* *Zuweisung-Operator* *Ausdruck*

*assignment-operator*: eines der folgenden Zeichen:<br/>
&emsp;**`=`**&emsp;**`*=`**&emsp;**`/=`**&emsp;**`%=`**&emsp;**`+=`**&emsp;**`-=`**&emsp;**`<<=`**&emsp;**`>>=`**&emsp;**`&=`**&emsp;**`^=`**&emsp;**`|=`**

## <a name="remarks"></a>Bemerkungen

Zuweisungs Operatoren speichern einen Wert in dem Objekt, das durch den linken Operanden angegeben wird. Es gibt zwei Arten von Zuweisungs Vorgängen:

- *einfache Zuweisung*, bei der der Wert des zweiten Operanden in dem Objekt gespeichert wird, das durch den ersten Operanden angegeben wird.

- *Verbund Zuweisung*, in der eine arithmetische, verschiebe-oder bitweise Operation ausgeführt wird, bevor das Ergebnis gespeichert wird.

Alle Zuweisungs Operatoren in der folgenden Tabelle, ausgenommen der- **`=`** Operator, sind Verbund Zuweisungs Operatoren.

### <a name="assignment-operators-table"></a>Tabelle Zuweisungs Operatoren

| Operator | Bedeutung |
|--|--|
| **`=`** | Speichern Sie den Wert des zweiten Operanden in dem Objekt, das durch den ersten Operanden angegeben wird (einfache Zuweisung). |
| **`*=`** | Multiplizieren Sie den Wert des ersten Operanden mit dem Wert des zweiten Operanden. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |
| **`/=`** | Dividieren Sie den Wert des ersten Operanden durch den Wert des zweiten Operanden. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |
| **`%=`** | Errechnen Sie den Modul des ersten Operanden, der vom Wert des zweiten Operanden angegeben wird. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |
| **`+=`** | Addieren Sie den Wert des zweiten Operanden zu dem Wert des ersten Operanden. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |
| **`-=`** | Subtrahieren Sie den Wert des zweiten Operanden von dem Wert des ersten Operanden. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |
| **`<<=`** | Verschieben Sie den Wert des ersten Operanden links der Anzahl von Bits, die durch den Wert des zweiten Operanden angegeben werden. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |
| **`>>=`** | Verschieben Sie den Wert des ersten Operanden rechts der Anzahl von Bits, die durch den Wert des zweiten Operanden angegeben werden. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |
| **`&=`** | Rufen Sie den bitweisen AND-Operator des ersten und zweiten Operanden auf. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |
| **`^=`** | Rufen Sie den bitweisen exklusiven OR-Operator des ersten und zweiten Operanden auf. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |
| **`|=`** | Rufen Sie den bitweisen inklusiven OR-Operator des ersten und zweiten Operanden auf. Speichern Sie das Ergebnis in dem Objekt, das durch den ersten Operanden angegeben wird. |

### <a name="operator-keywords"></a>Operator Schlüsselwörter

Drei der Verbund Zuweisungs Operatoren verfügen über Schlüsselwort Entsprechungen. Sie lauten wie folgt:

| Operator | Entsprechung |
|--|--|
| **`&=`** | **`and_eq`** |
| **`|=`** | **`or_eq`** |
| **`^=`** | **`xor_eq`** |

C++ gibt diese Operator Schlüsselwörter als Alternative rechtschreibweisen für die Verbund Zuweisungs Operatoren an. In C werden die alternativen rechtschreibweisen als Makros in der \<iso646.h> Kopfzeile bereitgestellt. In C++ sind die alternativen Schreibweisen Schlüsselwörter. die Verwendung von \<iso646.h> oder der C++-Entsprechung \<ciso646> ist als veraltet markiert. In Microsoft C++ ist die- [`/permissive-`](../build/reference/permissive-standards-conformance.md) oder- [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Compileroption erforderlich, um die alternative Schreibweise zu aktivieren.

## <a name="example"></a>Beispiel

```cpp
// expre_Assignment_Operators.cpp
// compile with: /EHsc
// Demonstrate assignment operators
#include <iostream>
using namespace std;
int main() {
   int a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555;

   a += b;      // a is 9
   b %= a;      // b is 6
   c >>= 1;      // c is 5
   d |= e;      // Bitwise--d is 0xFFFF

   cout  << "a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555" << endl
         << "a += b yields " << a << endl
         << "b %= a yields " << b << endl
         << "c >>= 1 yields " << c << endl
         << "d |= e yields " << hex << d << endl;
}
```

## <a name="simple-assignment"></a>Einfache Zuweisung

Der einfache Zuweisungs Operator ( **`=`** ) bewirkt, dass der Wert des zweiten Operanden in dem Objekt gespeichert wird, das durch den ersten Operanden angegeben wird. Wenn beide Objekte arithmetische Typen sind, wird der rechte Operand in den Typ der linken konvertiert, bevor der Wert gespeichert wird.

Objekte der **`const`** **`volatile`** Typen und können l-Werten von Typen zugewiesen werden, die nur sind **`volatile`** oder nicht oder sind **`const`** **`volatile`** .

Die Zuweisung zu Objekten des Klassen Typs **`struct`** ( **`union`** -,-und- **`class`** Typen) erfolgt durch eine Funktion mit dem Namen `operator=` . Das Standardverhalten dieser Operatorfunktion besteht darin, eine bitweise Kopie auszuführen. Allerdings kann dieses Verhalten mithilfe von überladenen Operatoren geändert werden. Weitere Informationen finden Sie unter [Operatorüberladung](../cpp/operator-overloading.md). Klassentypen können auch *kopierzuweisungs* -und Verschiebungs *Zuweisungs* Operatoren aufweisen. Weitere Informationen finden Sie unter [Kopierkonstruktoren und Kopier Zuweisungs Operatoren](copy-constructors-and-copy-assignment-operators-cpp.md) und [bewegungskonstruktoren und Bewegungs Zuweisungs Operatoren](move-constructors-and-move-assignment-operators-cpp.md).

Ein Objekt einer eindeutig abgeleiteten Klasse von einer angegebenen Basisklasse kann einem Objekt der Basisklasse zugewiesen werden. Das Gegenteil ist nicht der Fall, da es eine implizite Konvertierung von einer abgeleiteten Klasse in eine Basisklasse gibt, jedoch nicht von der Basisklasse zu einer abgeleiteten Klasse. Beispiel:

```cpp
// expre_SimpleAssignment.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
class ABase
{
public:
    ABase() { cout << "constructing ABase\n"; }
};

class ADerived : public ABase
{
public:
    ADerived() { cout << "constructing ADerived\n"; }
};

int main()
{
    ABase aBase;
    ADerived aDerived;

    aBase = aDerived; // OK
    aDerived = aBase; // C2679
}
```

Zuweisungen zu Verweistypen verhalten sich so, als ob die Zuweisung zu dem Objekt ausgeführt würde, auf das der Verweis zeigt.

Für Klassentypobjekte unterscheidet sich die Zuweisung von der Initialisierung. Um zu sehen, wie unterschiedlich Zuweisung und Initialisierung sein können, betrachten Sie diesen Code:

```cpp
UserType1 A;
UserType2 B = A;
```

Der vorhergehende Code zeigt einen Initialisierer; er ruft den Konstruktor für `UserType2` auf, der ein Argument vom Typ `UserType1` akzeptiert. Mit dem Code

```cpp
UserType1 A;
UserType2 B;

B = A;
```

kann die Zuweisungsanweisung

```cpp
B = A;
```

eine der folgenden Auswirkungen haben:

- Ruft die-Funktion `operator=` für auf `UserType2` , sofern `operator=` mit einem-Argument bereitgestellt wird `UserType1` .

- Aufruf der expliziten Konvertierungsfunktion `UserType1::operator UserType2`, wenn eine solche Funktion vorhanden ist.

- Aufruf eines Konstruktors `UserType2::UserType2`, sofern ein solcher Konstruktor vorhanden ist, der ein `UserType1`-Argument akzeptiert und das Ergebnis kopiert.

## <a name="compound-assignment"></a>Verbundzuweisung

Die Verbund Zuweisungs Operatoren werden in der [Tabelle der Zuweisungs Operatoren](#assignment-operators-table)angezeigt. Diese Operatoren haben das Format *E1* *op* =  *E2*, wobei *E1* ein nicht **`const`** änderbarer l-Wert und *E2* ist:

- arithmetischer Typ

- Ein-Zeiger, *op* wenn op **`+`** oder ist.**`-`**

Das *E1* *op* =  *E2* -Formular verhält sich wie *E1* **`=`** *E1* *op* *E2*, *E1* wird jedoch nur einmal ausgewertet.

Eine Verbundzuweisung für einen enumerierten Typ generiert eine Fehlermeldung. Wenn der linke Operand ein Zeigertyp ist, muss der rechte Operand ein Zeigertyp sein, oder es muss sich um einen konstanten Ausdruck handeln, der als 0 ausgewertet wird. Wenn der linke Operand ein ganzzahliger Typ ist, darf der rechte Operand kein Zeigertyp sein.

## <a name="result-of-assignment-operators"></a>Ergebnis von Zuweisungsoperatoren

Die Zuweisungsoperatoren geben den Wert des Objekts zurück, das vom linken Operanden nach der Zuweisung angegeben wird. Das Typergebnis ist der Typ des linken Operanden. Das Ergebnis eines Zuweisungsausdrucks ist immer ein l-value. Diese Operatoren weisen eine Assoziativität von rechts nach links auf. Der linke Operand muss ein veränderbarer L-Wert sein.

In ANSI C ist das Ergebnis eines Zuweisungs Ausdrucks kein l-Wert. Dies bedeutet, dass der rechtliche C++-Ausdruck `(a += b) += c` in C nicht zulässig ist.

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit binären Operatoren](../cpp/expressions-with-binary-operators.md)<br/>
[C++ integrierte Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C-Zuweisungs Operator](../c-language/c-assignment-operators.md)
