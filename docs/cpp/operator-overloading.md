---
title: Operatorüberladung
ms.date: 11/04/2016
f1_keywords:
- operator_cpp
- operator
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
ms.openlocfilehash: a16f68088ffffd6c3cf38f5ae3adda5f2d59fb57
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188570"
---
# <a name="operator-overloading"></a>Überladen von Operatoren

Das **Operator** Schlüsselwort deklariert eine Funktion, die angibt, welches *Operator-Symbol* bei der Anwendung auf Instanzen einer Klasse bedeutet. Dadurch erhält der Operator mehrere Bedeutungen, oder er wird "überladen". Der Compiler unterscheidet zwischen verschiedenen Bedeutungen eines Operators, indem er die Typen seiner Operanden überprüft.

## <a name="syntax"></a>Syntax

> *Type* **Operator** *Operator-Symbol* **(** *Parameterliste* **)**

## <a name="remarks"></a>Bemerkungen

Sie können die Funktion der meisten integrierten Operatoren global oder klassenweise neu definieren. Überladene Operatoren werden als Funktionen implementiert.

Der Name eines überladenen Operators ist **Operator** *x*, wobei *x* der Operator ist, wie er in der folgenden Tabelle angezeigt wird. Wenn Sie z. b. den Additions Operator überladen möchten, definieren Sie eine Funktion mit dem Namen **Operator +** . Um den Additions-/Zuweisungs Operator **+=** zu überladen, definieren Sie eine Funktion mit dem Namen **Operator + =** .

### <a name="redefinable-operators"></a>Neu definierbare Operatoren

|Operator|Name|type|
|--------------|----------|----------|
|**,**|Komma|Binary|
|**!**|Logisches NOT|Unäroperatoren|
|**!=**|Ungleichheit|Binary|
|**%**|Modulus|Binary|
|**%=**|Modulozuweisung|Binary|
|**&**|Bitweises AND|Binary|
|**&**|Address-of|Unäroperatoren|
|**&&**|Logisches AND|Binary|
|**&=**|Bitweise AND-Zuweisung|Binary|
|**( )**|Funktionsaufruf|—|
|**( )**|Umwandlungsoperator|Unäroperatoren|
|**&#42;**|Multiplikation|Binary|
|**&#42;**|Zeiger-Dereferenzierung|Unäroperatoren|
|**&#42;=**|Multiplikationszuweisung|Binary|
|**+**|Addition|Binary|
|**+**|Unäres Plus|Unäroperatoren|
|**++**|<sup>1</sup> Inkrement|Unäroperatoren|
|**+=**|Additionszuweisung|Binary|
|**-**|Subtraktion|Binary|
|**-**|Unäre Negation|Unäroperatoren|
|**--**|Dekrement <sup>1</sup>|Unäroperatoren|
|**-=**|Subtraktionszuweisung|Binary|
|**->**|Memberauswahl|Binary|
|**->&#42;**|Pointer-to-member-Auswahl|Binary|
|**/**|Division|Binary|
|**/=**|Divisionszuweisung|Binary|
|**\<**|Kleiner als|Binary|
|**<<**|Nach links verschieben|Binary|
|**<<=**|Linksschiebezuweisung|Binary|
|**<=**|Kleiner als oder gleich|Binary|
|**=**|Zuweisung|Binary|
|**==**|Gleichheit|Binary|
|**>**|Größer als|Binary|
|**>=**|Größer als oder gleich|Binary|
|**>>**|Nach rechts verschieben|Binary|
|**>>=**|Rechtsschiebezuweisung|Binary|
|**[ ]**|Array-Subscript|—|
|**^**|Exklusives OR|Binary|
|**^=**|Exklusive OR-Zuweisung|Binary|
|**&#124;**|Bitweises inklusives OR|Binary|
|**&#124;=**|Bitweise inklusive OR-Zuweisung|Binary|
|**&#124;&#124;**|Logisches OR|Binary|
|**~**|Einerkomplement|Unäroperatoren|
|**delete**|Löschen|—|
|**Neu**|Neu|—|
|Konvertierungsoperatoren|Konvertierungsoperatoren|Unäroperatoren|

<sup>1</sup> es sind zwei Versionen der unären Inkrement-und Dekrementoperatoren vorhanden: "Preincrement" und "postincrement".

Weitere Informationen finden Sie unter [Allgemeine Regeln für die Überladung von Operatoren](../cpp/general-rules-for-operator-overloading.md) . Die Einschränkungen für die verschiedenen Kategorien von überladenen Operatoren werden in den folgenden Themen beschrieben:

- [Unary Operators (Unäre Operatoren)](../cpp/overloading-unary-operators.md)

- [Binäre Operatoren](../cpp/binary-operators.md)

- [Zuweisung](../cpp/assignment.md)

- [Funktionsaufruf](../cpp/function-call-cpp.md)

- [Indizierung](../cpp/subscripting.md)

- [Zugriff auf Klassenmember](../cpp/member-access.md)

- [Inkrement und Dekrement](../cpp/increment-and-decrement-operator-overloading-cpp.md).

- [Benutzerdefinierte Typkonvertierungen](../cpp/user-defined-type-conversions-cpp.md)

Die Operatoren, die in der folgenden Tabelle aufgeführt sind, können nicht überladen werden. Die Tabelle enthält die Präprozessorsymbole **#** und **##** .

### <a name="nonredefinable-operators"></a>Nicht neu definierbare Operatoren

|Operator|Name|
|-|-|
|**.**|Memberauswahl|
|**.&#42;**|Pointer-to-member-Auswahl|
|**::**|Bereichsauflösung|
|**? :**|Bedingt|
|**#**|Präprozessorkonvertierung in Zeichenfolge|
|**##**|Präprozessorverkettung|

Obwohl überladene Operatoren in der Regel vom Compiler implizit aufgerufen werden, wenn sie im Code auftreten, können sie explizit auf dieselbe Art und Weise aufgerufen werden, wie andere Member- oder Nichtmemberfunktionen aufgerufen werden:

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der **+** -Operator überladen, um zwei komplexe Zahlen hinzuzufügen und das Ergebnis zurückzugeben.

```cpp
// operator_overloading.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Complex {
   Complex( double r, double i ) : re(r), im(i) {}
   Complex operator+( Complex &other );
   void Display( ) {   cout << re << ", " << im << endl; }
private:
   double re, im;
};

// Operator overloaded using a member function
Complex Complex::operator+( Complex &other ) {
   return Complex( re + other.re, im + other.im );
}

int main() {
   Complex a = Complex( 1.2, 3.4 );
   Complex b = Complex( 5.6, 7.8 );
   Complex c = Complex( 0.0, 0.0 );

   c = a + b;
   c.Display();
}
```

```Output
6.8, 11.2
```

## <a name="in-this-section"></a>In diesem Abschnitt

- [Allgemeine Regeln für die Überladung von Operatoren](../cpp/general-rules-for-operator-overloading.md)

- [Überladen von unären Operatoren](../cpp/overloading-unary-operators.md)

- [Binäre Operatoren](../cpp/binary-operators.md)

- [Zuweisung](../cpp/assignment.md)

- [Funktionsaufruf](../cpp/function-call-cpp.md)

- [Indizierung](../cpp/subscripting.md)

- [Memberzugriff](../cpp/member-access.md)

## <a name="see-also"></a>Weitere Informationen

[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
