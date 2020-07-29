---
title: complex&lt;double&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<double>
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
ms.openlocfilehash: b9bf4780dd78800653804762301b36ff6bb30a92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230077"
---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;

Beschreibt ein Objekt, das ein geordnetes Paar von Objekten speichert, die beide den Typ **`double`** haben, wobei das erste Objekt dem reellen Teil einer komplexen Zahl und das zweite Objekt den imaginären Teil darstellt.

## <a name="syntax"></a>Syntax

```cpp
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as class template complex
};
```

### <a name="parameters"></a>Parameter

*RealVal*\
Der Wert des Typs **`double`** für den reellen Teil der komplexen Zahl, die erstellt wird.

*ImagVal*\
Der Wert des Typs **`double`** für den imaginären Teil der komplexen Zahl, die erstellt wird.

*complexnum*\
Die komplexe Zahl vom Typ **`float`** oder des Typs **`long double`** , deren reelle und imaginäre Teile zum Initialisieren einer komplexen Anzahl von konstruiertem Typ verwendet werden **`double`** .

## <a name="return-value"></a>Rückgabewert

Eine komplexe Zahl vom Typ **`double`** .

## <a name="remarks"></a>Bemerkungen

Die explizite Spezialisierung der Klassen Vorlage, die für eine komplexe Klasse des Typs Komplex ist, unter **`double`** scheidet sich von der Klassen Vorlage nur in den Konstruktoren, die Sie definiert. Die Konvertierung von **`float`** in **`double`** darf implizit erfolgen, aber die Konvertierung von **`long double`** in **`double`** ist erforderlich **`explicit`** . Die Verwendung von **`explicit`** schließt die Initiierung mit Typkonvertierung mithilfe der Zuweisungs Syntax aus.

Weitere Informationen zur Klassen Vorlage finden Sie unter `complex` [Complex-Klasse](../standard-library/complex-class.md). Eine Liste der Elemente der Klassen Vorlage finden Sie `complex` unter.

## <a name="example"></a>Beispiel

```cpp
// complex_comp_dbl.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << "as type double gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 4.0 , 5.0 );
   complex <double> c2double ( c2float );
   cout << "Implicit conversion from type float to type double,"
        << endl << "gives c2double = " << c2double << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 4.0 , 5.0 );
   complex <double> c3double ( c3longdouble );
   cout << "Explicit conversion from type float to type double,"
        << endl << "gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:" << endl
        << "arg ( c3 ) = " << argc3 << " radians, which is "
        << argc3 * 180 / pi << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type double gives c1 = (4,5)
Implicit conversion from type float to type double,
gives c2double = (4,5)
Explicit conversion from type float to type double,
gives c3longdouble = (4,5)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.
*/
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**:\<complex>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[komplexe Klasse](../standard-library/complex-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
