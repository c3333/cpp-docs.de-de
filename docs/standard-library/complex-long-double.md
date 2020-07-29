---
title: complex&lt;long double&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 73027ba76d608424b1a6da346e861b10c66989fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228387"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

Diese explizit spezialisierte Klassen Vorlage beschreibt ein Objekt, das ein geordnetes Paar von Objekten speichert, die beide den Typ **`long double`** haben, wobei das erste Objekt den reellen Teil einer komplexen Zahl und das zweite Objekt den imaginären Teil darstellt.

## <a name="syntax"></a>Syntax

```cpp
template <>
class complex<long double> {
public:
    constexpr complex(
    long double _RealVal = 0,
    long double _ImagVal = 0);

complex(
    constexpr complex<long double>& complexNum);

// rest same as class template complex
};
```

### <a name="parameters"></a>Parameter

*_RealVal*\
Der Wert des Typs **`long double`** für den reellen Teil der komplexen Zahl, die erstellt wird.

*_ImagVal*\
Der Wert des Typs **`long double`** für den imaginären Teil der komplexen Zahl, die erstellt wird.

*complexnum*\
Die komplexe Zahl vom Typ **`double`** oder des Typs **`float`** , deren reelle und imaginäre Teile zum Initialisieren einer komplexen Anzahl von konstruiertem Typ verwendet werden **`long double`** .

## <a name="return-value"></a>Rückgabewert

Eine komplexe Zahl vom Typ **`long double`** .

## <a name="remarks"></a>Bemerkungen

Die explizite Spezialisierung der Klassen Vorlage `complex` auf eine komplexe Klasse des Typs unter **`long double`** scheidet sich von der Klassen Vorlage nur in den Konstruktoren, die Sie definiert. Die Konvertierung von **`long double`** in **`float`** darf implizit erfolgen, aber die Konvertierung von **`double`** in **`long double`** ist erforderlich **`explicit`** . Die Verwendung von **`explicit`** schließt die Initiierung mit Typkonvertierung mithilfe der Zuweisungs Syntax aus.

Weitere Informationen zur Klassen Vorlage `complex` und ihren Membern finden Sie unter [Complex-Klasse](../standard-library/complex-class.md).

**Microsoft-spezifisch**: der **`long double`** - **`double`** Typ und der-Typ verfügen über die gleiche Darstellung, sind jedoch unterschiedliche Typen. Weitere Informationen finden Sie unter [integrierte Typen](../cpp/fundamental-types-cpp.md).

## <a name="example"></a>Beispiel

```cpp
// complex_comp_ld.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<long double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of complex number of type float
    complex<float> c2float( 1.0 , 3.0 );
    complex<long double> c2longdouble ( c2float );
    cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

    // The third constructor initializes values of the real &
    // imaginary parts using those of a complex number
    // of type double
    complex<double> c3double( 3.0 , 4.0 );
    complex<long double> c3longdouble( c3double );
    cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3longdouble );
    double argc3 = arg( c3longdouble );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

```Output
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg( c3 ) = 0.927295 radians, which is 53.1301 degrees.
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**:\<complex>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[komplexe Klasse](../standard-library/complex-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
