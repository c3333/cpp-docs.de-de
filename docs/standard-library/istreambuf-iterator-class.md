---
title: istreambuf_iterator-Klasse
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
ms.openlocfilehash: b76e327c46a180c1e7ae7287ee9fe49573f3a7a6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217700"
---
# <a name="istreambuf_iterator-class"></a>istreambuf_iterator-Klasse

Die Klassen Vorlage istreambuf_iterator beschreibt ein eingabeiteratorobjekt, das Zeichen Elemente aus einem Eingabestreampuffer extrahiert, auf den es durch ein Objekt, auf das er speichert, vom Typ Zeiger auf zugreift `basic_streambuf` \< **CharType**, **Traits**> .

## <a name="syntax"></a>Syntax

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>Parameter

*CharType*\
Der Typ, der den Zeichentyp für das istreambuf_iterator-Objekt darstellt.

*Aufweisen*\
Der Typ, der den Zeichentyp für das istreambuf_iterator-Objekt darstellt. Dieses Argument ist optional, und der Standardwert ist `char_traits` \< *CharType> . *

## <a name="remarks"></a>Bemerkungen

Die istreambuf_iterator-Klasse muss die Anforderungen für einen Eingabeiterator erfüllen.

Nachdem ein Objekt der istreambuf_iterator-Klasse mit einem als nicht null gespeicherten Zeiger erstellt oder inkrementiert wurde, versucht das Objekt effektiv, ein Objekt vom Typ *CharType* aus dem zugeordneten Eingabestream zu extrahieren und zu speichern. Die Extraktion kann jedoch verzögert werden, bis das Objekt tatsächlich dereferenziert oder kopiert wurde. Wenn die Extraktion fehlschlägt, ersetzt das Objekt den gespeicherten Zeiger durch einen NULL-Zeiger und erstellt so einen Indikator für das Ende der Sequenz.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|Erstellt ein `istreambuf_iterator`-Objekt, das initialisiert wird, um Zeichen aus dem Eingabestream zu lesen.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, der für den Zeichentyp von `ostreambuf_iterator` bereitgestellt wird.|
|[int_type](#int_type)|Ein Typ, der einen Ganzzahltyp für ein `istreambuf_iterator`-Objekt bereitstellt.|
|[istream_type](#istream_type)|Ein Typ, der für den Streamtyp von `istream_iterator` bereitgestellt wird.|
|[streambuf_type](#streambuf_type)|Ein Typ, der für den Streamtyp von `istreambuf_iterator` bereitgestellt wird.|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Ein Typ, der für den Merkmaltyp von `istream_iterator` bereitgestellt wird.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[hoch](#equal)|Testet zwei Eingabestreampufferiteratoren auf Gleichheit.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[KOM](#op_star)|Der Dereferenzierungsoperator gibt das folgende Zeichen im Stream zurück.|
|[Operator + +](#op_add_add)|Gibt entweder das folgende Zeichen im Eingabestream zurück oder kopiert das Objekt vor dem Inkrementieren und gibt die Kopie zurück.|
|[Operator->](#op_arrow)|Gibt den Wert eines Members zurück, falls vorhanden.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<iterator>

**Namespace:** std

## <a name="istreambuf_iteratorchar_type"></a><a name="char_type"></a>Istreambuf_iterator:: char_type

Ein Typ, der für den Zeichentyp von `ostreambuf_iterator` bereitgestellt wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter *CharType* dar.

### <a name="example"></a>Beispiel

```cpp
// istreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="istreambuf_iteratorequal"></a><a name="equal"></a>Istreambuf_iterator:: Equal

Testet zwei Eingabestream-Pufferiteratoren auf Äquivalenz.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Iterator für die Durchführung von Gleichheitsüberprüfungen.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn es sich bei beiden um `istreambuf_iterator` End-of-Stream-Iteratoren handelt, oder wenn keines der beiden ein Streamende-Iterator ist; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Ein Bereich wird von der `istreambuf_iterator` bis zur aktuellen Position und dem End-of-Stream-Iterator definiert, aber da alle nicht-End-of-Stream-Iteratoren unter der Member-Funktion äquivalent sind `equal` , ist es nicht möglich, Unterbereiche mit s zu definieren `istreambuf_iterator` . Die `==`- und `!=`-Operatoren weisen die gleiche Semantik auf.

### <a name="example"></a>Beispiel

```cpp
// istreambuf_iterator_equal.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "(Try the example: 'Hello world!'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   istreambuf_iterator<char> charReadIn1 ( cin );
   istreambuf_iterator<char> charReadIn2 ( cin );

   bool b1 = charReadIn1.equal ( charReadIn2 );

   if (b1)
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

## <a name="istreambuf_iteratorint_type"></a><a name="int_type"></a>Istreambuf_iterator:: int_type

Ein Typ, der einen Ganzzahltyp für ein `istreambuf_iterator`-Objekt bereitstellt.

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `Traits::int_type`.

### <a name="example"></a>Beispiel

```cpp
// istreambuf_iterator_int_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;
   istreambuf_iterator<char>::int_type inttype1 = 100;
   cout << "The inttype1 = " << inttype1 << "." << endl;
}
/* Output:
The inttype1 = 100.
*/
```

## <a name="istreambuf_iteratoristream_type"></a><a name="istream_type"></a>Istreambuf_iterator:: istream_type

Ein Typ, der für den Streamtyp von `istreambuf_iterator` bereitgestellt wird.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `basic_istream` \< **CharType**, **Traits**> .

### <a name="example"></a>Beispiel

Unter [istreambuf_iterator](#istreambuf_iterator) finden Sie ein Beispiel für das Deklarieren und Verwenden von `istream_type`.

## <a name="istreambuf_iteratoristreambuf_iterator"></a><a name="istreambuf_iterator"></a>Istreambuf_iterator:: istreambuf_iterator

Erstellt einen istreambuf_iterator, der initialisiert wird, um Zeichen aus dem Eingabestream zu lesen.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>Parameter

*strbuf*\
Der Eingabestreampuffer, dem der `istreambuf_iterator` angefügt wird.

*_Istr*\
Der Eingabestream, dem der `istreambuf_iterator` angefügt wird.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert den Eingabestream-Puffer Zeiger mit " *strinbuf*". Der zweite Konstruktor initialisiert den Eingabestream-Puffer Zeiger mit *_Istr*. `rdbuf`, und schließlich wird versucht, ein Objekt vom Typ zu extrahieren und zu speichern `CharType` .

### <a name="example"></a>Beispiel

```cpp
// istreambuf_iterator_istreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Following declarations will not compile:
   istreambuf_iterator<char>::istream_type &istrm = cin;
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );

   cout << "(Try the example: 'Oh what a world!'\n"
      << " then an Enter key to insert into the output,\n"
      << " & use a ctrl-Z Enter key combination to exit): ";
   istreambuf_iterator<char> charReadIn ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with hyphen-separators
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),
      charOut , ' ' , '-' );
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_star"></a>Istreambuf_iterator:: Operator *

Der Dereferenzierungsoperator gibt das folgende Zeichen im Stream zurück.

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>Rückgabewert

Das nächste Zeichen im Stream.

### <a name="example"></a>Beispiel

```cpp
// istreambuf_iterator_operator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;   //Put value of outpos equal to inpos
      ++inpos;
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_add_add"></a>Istreambuf_iterator:: Operator + +

Gibt entweder das folgende Zeichen im Eingabestream zurück oder kopiert das Objekt vor dem Inkrementieren und gibt die Kopie zurück.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Ein `istreambuf_iterator` oder ein Verweis auf `istreambuf_iterator`.

### <a name="remarks"></a>Bemerkungen

Der erste Operator versucht schließlich, ein Objekt vom Typ `CharType` aus dem zugeordneten Eingabestream zu extrahieren und zu speichern. Der zweite Operator erstellt eine Kopie des Objekts, inkrementiert das Objekt und gibt dann die Kopie zurück.

### <a name="example"></a>Beispiel

```cpp
// istreambuf_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;
      ++inpos;   //Increment istreambuf_iterator
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator-gt"></a><a name="op_arrow"></a>Istreambuf_iterator:: Operator-&gt;

Gibt den Wert eines Members zurück, falls vorhanden.

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Der Operator gibt ** & \* \* dieses**zurück.

## <a name="istreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>Istreambuf_iterator:: streambuf_type

Ein Typ, der für den Streamtyp von „istreambuf_iterator“ bereitgestellt wird.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `basic_streambuf` \< **CharType**, **Traits**> .

### <a name="example"></a>Beispiel

Unter [istreambuf_iterator](#istreambuf_iterator) finden Sie ein Beispiel für das Deklarieren und Verwenden von `istreambuf_type`.

## <a name="istreambuf_iteratortraits_type"></a><a name="traits_type"></a>Istreambuf_iterator:: traits_type

Ein Typ, der für den Merkmaltyp von `istream_iterator` bereitgestellt wird.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter *Merkmale* dar.

### <a name="example"></a>Beispiel

```cpp
// istreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="see-also"></a>Weitere Informationen

[iteratorstruktur](../standard-library/iterator-struct.md)\
[\<iterator>](../standard-library/iterator.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
