---
title: istream_iterator-Klasse
ms.date: 11/04/2016
f1_keywords:
- iterator/std::istream_iterator
- iterator/std::istream_iterator::char_type
- iterator/std::istream_iterator::istream_type
- iterator/std::istream_iterator::traits_type
helpviewer_keywords:
- std::istream_iterator [C++]
- std::istream_iterator [C++], char_type
- std::istream_iterator [C++], istream_type
- std::istream_iterator [C++], traits_type
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
ms.openlocfilehash: 941d625e388edc75dfe25a2de0e609c6d955ff19
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78869889"
---
# <a name="istream_iterator-class"></a>istream_iterator-Klasse

Beschreibt ein Eingabeiteratorobjekt. Es werden Objekte der Klasse `Type` aus einem Eingabestream extrahiert. Der Zugriff darauf erfolgt durch ein gespeichertes Objekt vom Typ `pointer` auf `basic_istream`< `CharType`, `Traits`>.

## <a name="syntax"></a>Syntax

```cpp
template <class Type, class CharType = char, class Traits = char_traits<CharType>, class Distance = ptrdiff_t,>
class istream_iterator
: public iterator<
    input_iterator_tag, Type, Distance,
    const Type *,
    const Type&>;
```

### <a name="parameters"></a>Parameter

*Typ*\
Der Typ des Objekts, das aus dem Eingabestream extrahiert werden soll.

*CharType* -\
Der Typ, der den Zeichentyp für `istream_iterator` darstellt. Dieses Argument ist optional, und der Standardwert ist **char**.

*Merkmale*\
Der Typ, der den Zeichentyp für `istream_iterator` darstellt. Dieses Argument ist optional, und der Standardwert ist `char_traits`< `CharType`.

*Entfernungs*\
Ein ganzzahliger Typ mit Vorzeichen, der den Differenztyp für den `istream_iterator` darstellt. Dieses Argument ist optional, und der Standardwert ist `ptrdiff_t`.

Nachdem ein Objekt der Klasse istream_iterator mit einem ungleich NULL gespeicherten Zeiger erstellt oder erhöht wurde, versucht das Objekt, ein Objekt vom Typ `Type` aus dem zugewiesenen Eingabestream zu extrahieren und zu speichern. Wenn die Extraktion fehlschlägt, ersetzt das Objekt den gespeicherten Zeiger durch einen NULL-Zeiger und erstellt so einen Indikator für das Ende der Sequenz.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[istream_iterator](#istream_iterator)|Erstellt entweder einen End-of-Stream-Iterator als Standard-`istream_iterator` oder ein `istream_iterator`, der für den Streamtyp des Iterators initialisiert wird, von dem gelesen wird.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Ein Typ, der für den Zeichentyp von `istream_iterator` bereitgestellt wird.|
|[istream_type](#istream_type)|Ein Typ, der für den Streamtyp von `istream_iterator` bereitgestellt wird.|
|[traits_type](#traits_type)|Ein Typ, der für den Merkmaltyp von `istream_iterator` bereitgestellt wird.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[operator*](#op_star)|Der Dereferenzierungsoperator gibt das gespeicherte Objekt vom Typ `Type` zurück, das vom `istream_iterator` adressiert wird.|
|[operator->](#op_arrow)|Gibt den Wert eines Members zurück, falls vorhanden.|
|[operator++](#op_add_add)|Extrahiert entweder ein inkrementiertes Objekt im Eingabestream oder kopiert das Objekt vor dem Inkrementieren und gibt die Kopie zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<Iterator >

**Namespace:** std

## <a name="char_type"></a> istream_iterator::char_type

Ein Typ, der für den Zeichentyp von `istream_iterator` bereitgestellt wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Chartype`dar.

### <a name="example"></a>Beispiel

```cpp
// istream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '2 4 f' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iterator"></a> istream_iterator::istream_iterator

Erstellt entweder einen End-of-Stream-Iterator als Standard-`istream_iterator` oder ein `istream_iterator`, der für den Streamtyp des Iterators initialisiert wird, von dem gelesen wird.

```cpp
istream_iterator();

istream_iterator(istream_type& _Istr);
```

### <a name="parameters"></a>Parameter

*_Istr*\
Der zu lesende Eingabestream verwendet `istream_iterator` zum Initialisieren.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert den Eingabestreamzeiger mit einem NULL-Zeiger und erstellt einen End-of-Stream-Iterator. Der zweite Konstruktor initialisiert den Eingabestreamzeiger mit *& _Istr*und versucht dann, ein Objekt vom Typ `Type`zu extrahieren und zu speichern.

Der End-of-Stream-Iterator kann verwendet werden, um zu testen, ob ein `istream_iterator` das Ende eines Streams erreicht hat.

### <a name="example"></a>Beispiel

```cpp
// istream_iterator_istream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Used in conjunction with copy algorithm
   // to put elements into a vector read from cin
   vector<int> vec ( 4 );
   vector <int>::iterator Iter;

   cout << "Enter 4 integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";
   istream_iterator<int> intvecRead ( cin );

   // Default constructor will test equal to end of stream
   // for delimiting source range of vecor
   copy ( intvecRead , istream_iterator<int>( ) , vec.begin ( ) );
   cin.clear ( );

   cout << "vec = ";
   for ( Iter = vec.begin( ) ; Iter != vec.end( ) ; Iter++ )
      cout << *Iter << " "; cout << endl;
}
```

## <a name="istream_type"></a> istream_iterator::istream_type

Ein Typ, der für den Streamtyp von `istream_iterator` bereitgestellt wird.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `basic_istream`\< **CharType**, **Merkmale**>.

### <a name="example"></a>Beispiel

Unter [istream_iterator](#istream_iterator) finden Sie ein Beispiel für das Deklarieren und Verwenden eines `istream_type`.

## <a name="op_star"></a> istream_iterator::Operator*

Der Dereferenzierungsoperator gibt das gespeicherte Objekt vom Typ `Type` zurück, das vom `istream_iterator` adressiert wird.

```cpp
const Type& operator*() const;
```

### <a name="return-value"></a>Rückgabewert

Das gespeicherte Objekt vom Typ `Type`.

### <a name="example"></a>Beispiel

```cpp
// istream_iterator_operator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_arrow"></a> istream_iterator::Operator-&gt;

Gibt den Wert eines Members zurück, falls vorhanden.

```cpp
const Type* operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Der Wert eines Members, falls vorhanden.

### <a name="remarks"></a>Bemerkungen

`i->m` entspricht `(*i).m`

Der Operator gibt `&*this` zurück.

### <a name="example"></a>Beispiel

```cpp
// istream_iterator_operator_vm.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>
#include <complex>

using namespace std;

int main( )
{
   cout << "Enter complex numbers separated by spaces & then\n"
        << " a character pair ( try example: '(1,2) (3,4) (a,b)' ): ";

   // istream_iterator from stream cin
   istream_iterator< complex<double> > intRead ( cin );

   // End-of-stream iterator
   istream_iterator<complex<double> > EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading the real part: " << intRead ->real( ) << endl;
      cout << "Reading the imaginary part: " << intRead ->imag( ) << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_add_add"></a> istream_iterator::Operator++

Extrahiert entweder ein inkrementiertes Objekt im Eingabestream oder kopiert das Objekt vor dem Inkrementieren und gibt die Kopie zurück.

```cpp
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Der erste Member-Operator gibt einen Verweis auf das inkrementierte Objekt vom Typ zurück, `Type` aus dem Eingabestream extrahiert wurde, und die zweite Member-Funktion gibt eine Kopie des-Objekts zurück.

### <a name="example"></a>Beispiel

```cpp
// istream_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="traits_type"></a> istream_iterator::traits_type

Ein Typ, der für den Merkmaltyp von `istream_iterator` bereitgestellt wird.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter *Merkmale* dar.

### <a name="example"></a>Beispiel

```cpp
// istream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '10 20 a' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="see-also"></a>Weitere Informationen

[input_iterator_tag-Struktur](../standard-library/input-iterator-tag-struct.md)\
[iterator-Struktur](../standard-library/iterator-struct.md)\
[\<iterator>](../standard-library/iterator.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](../standard-library/cpp-standard-library-reference.md)
