---
title: 'Address-of-Operator: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: 4c9ae9aedaec202c8798ab454ee5df1a68278a6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181602"
---
# <a name="address-of-operator-amp"></a>Address-of-Operator: &amp;

## <a name="syntax"></a>Syntax

```
& cast-expression
```

## <a name="remarks"></a>Bemerkungen

Der unäre address-of-Operator ( **&** ) übernimmt die Adresse seines Operanden. Der Operand des address-of-Operators kann entweder ein Funktions Kenn Zeichner oder ein l-Wert sein, der ein Objekt angibt, das kein Bitfeld ist.

Der address-of-Operator kann nur auf Variablen vom Typ "Basis", "Struktur", "Klasse" oder "Union" angewendet werden, die auf Dateibereichsebene deklariert wurden, oder auf indizierte Arrayverweise. In diesen Ausdrücken kann ein konstanter Ausdruck, der nicht den address-of-Operator einschließt, dem address-of-Ausdruck hinzugefügt oder von diesem subtrahiert werden.

Bei Anwendung auf Funktionen oder L-Werte ist das Ergebnis des Ausdrucks ein Zeigertyp (ein R-Wert), der vom Typ des Operanden abgeleitet wird. Wenn der Operand z. b. vom Typ " **char**" ist, ist das Ergebnis des Ausdrucks vom Typ "Zeiger" auf " **char**". Der Address-of-Operator, der **auf Konstante** oder **flüchtige** Objekte angewendet wird, wird zu `const type *` oder `volatile type *`ausgewertet, wobei **Type** der Typ des ursprünglichen Objekts ist.

Wenn der Address-of-Operator auf einen qualifizierten Namen angewendet wird, hängt das Ergebnis davon ab, ob der *qualifizierte Name* ein statisches Element angibt. Wenn dies der Fall ist, ist das Ergebnis ein Zeiger auf den Typ, der in der Deklaration des Members angegeben wird. Wenn der Member nicht statisch ist, ist das Ergebnis ein Zeiger auf den Element *Namen* der Klasse, die durch *qualified-class-Name*angegeben wird. (Weitere Informationen zum *qualified-class-Name*finden Sie unter [Primary Expressions](../cpp/primary-expressions.md) .) Das folgende Code Fragment zeigt, wie sich das Ergebnis unterscheidet, je nachdem, ob der Member statisch ist:

```cpp
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```

In diesem Beispiel ergibt der Ausdruck `&PTM::fValue` den Typ `float *` anstelle von Typ `float PTM::*`, da `fValue` ein statischer Member ist.

Die Adresse einer überladenen Funktion kann nur verwendet werden, wenn klar ist, auf welche Version der Funktion verwiesen wird. Weitere Informationen zum Abrufen der Adresse einer bestimmten überladenen Funktion finden Sie unter [Funktions Überladung](function-overloading.md) .

Die Anwendung des address-of-Operators auf einen Referenztyp führt zum gleichen Ergebnis wie die Anwendung des Operators auf das Objekt, an das der Verweis gebunden ist. Beispiel:

## <a name="example"></a>Beispiel

```cpp
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```

## <a name="output"></a>Output

```Output
&d equals &rd
```

Im folgenden Beispiel wird der address-of-Operator benutzt, um ein Zeigerargument an eine Funktion zu übergeben:

```cpp
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```

## <a name="output"></a>Output

```Output
25
```

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Lvalue-Verweisdeklarator: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Dereferenzierungs- und Address-of-Operatoren](../c-language/indirection-and-address-of-operators.md)
