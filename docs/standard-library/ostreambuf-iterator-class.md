---
title: ostreambuf_iterator Class
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
ms.openlocfilehash: 8e9fa10888b511ad2a500f64faf610dc7dd5ba03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373564"
---
# <a name="ostreambuf_iterator-class"></a>ostreambuf_iterator Class

Die Klassenvorlage ostreambuf_iterator ein Ausgabeiteratorobjekt beschreibt, das aufeinanderfolgende Zeichenelemente mit dem **Extraktionsoperator>>** in den Ausgabestream schreibt. Die `ostreambuf_iterator` unterscheiden sich von denen der [ostream_iterator-Klasse](../standard-library/ostream-iterator-class.md) insofern, als dass sie über Zeichen anstelle eines generischen Typs im Hinblick auf den Objekttyp verfügen, der in den Ausgabestream eingefügt wird.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parameter

*Chartype*\
Der Typ, der den Zeichentyp für das ostreambuf_iterator-Objekt darstellt. Dieses Argument ist optional, und der Standardwert ist **char**.

*Merkmale*\
Der Typ, der den Zeichentyp für das ostreambuf_iterator-Objekt darstellt. Dieses Argument ist optional, und der Standardwert ist `char_traits`\< *CharType>.*

## <a name="remarks"></a>Bemerkungen

Die ostreambuf_iterator-Klasse muss den Anforderungen für einen Ausgabeiterator entsprechen. Algorithmen können mit `ostreambuf_iterator` direkt in Ausgabestreams geschrieben werden. Die Klasse bietet einen Streamiterator auf niedriger Ebene, der Zugriff auf den unformatierten E/A-Stream in Form von Zeichen und die Fähigkeit erlaubt, die Pufferung und die Zeichenumsetzungen zu umgehen, die mit den Streamiteratoren auf hoher Ebene verbunden sind.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Erstellt einen `ostreambuf_iterator`, der zum Schreiben von Zeichen in den Ausgabestream initialisiert wird.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Ein Typ, der für den Zeichentyp von `ostreambuf_iterator` bereitgestellt wird.|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Ein Typ, der für den Streamtyp von `ostream_iterator` bereitgestellt wird.|
|[streambuf_type](#streambuf_type)|Ein Typ, der für den Streamtyp von `ostreambuf_iterator` bereitgestellt wird.|
|[traits_type](#traits_type)|Ein Typ, der für den Merkmaltyp von `ostream_iterator` bereitgestellt wird.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Fehlgeschlagen](#failed)|Testet eine Einfügung in den Ausgabestreampuffer auf Fehler.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator*](#op_star)|Dereferencing-Operator, der zum Implementieren des \* `i`  =  `x`Ausgabeiteratorausdrucks verwendet wird.|
|[Operator++](#op_add_add)|Ein nicht funktionaler Inkrementoperator, der einen `ostreambuf_iterator` zum gleichen Objekt zurückgibt, das er adressiert hat, bevor der Vorgang aufgerufen wurde.|
|[Operator=](#op_eq)|Der Operator fügt ein Zeichen in den zugeordneten Streampuffer ein.|

## <a name="requirements"></a>Anforderungen

**Header:** \<iterator>

**Namespace:** std

## <a name="ostreambuf_iteratorchar_type"></a><a name="char_type"></a>ostreambuf_iterator::char_type

Ein Typ, der für den Zeichentyp von `ostreambuf_iterator` bereitgestellt wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `CharType` dar.

### <a name="example"></a>Beispiel

```cpp
// ostreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="ostreambuf_iteratorfailed"></a><a name="failed"></a>ostreambuf_iterator::fehlgeschlagen

Testet eine Einfügung in den Ausgabestreampuffer auf Fehler.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn vorher kein Einfügen in den Ausgabestreampuffer fehlgeschlagen ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt **TRUE** zurück, sofern es sich um jede vorherige Verwendung des Members `operator=` handelt, der Aufruf von **subf**_-> `sputc` gibt **eof** zurück.

### <a name="example"></a>Beispiel

```cpp
// ostreambuf_iterator_failed.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'a';
   charOut ++;
*charOut  = 'b';
   charOut ++;
*charOut = 'c';
   cout << " are characters output individually." << endl;

   bool b1 = charOut.failed ( );
   if (b1)
       cout << "At least one insertion failed." << endl;
   else
       cout << "No insertions failed." << endl;
}
/* Output:
abc are characters output individually.
No insertions failed.
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_star"></a>ostreambuf_iterator::Operator\*

Ein nicht funktionaler Dereferencing-Operator, der zum \* Implementieren des Ausgabeiteratorausdrucks *i* = *x*verwendet wird.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Rückgabewert

Das ostreambuf-Iteratorobjekt.

### <a name="remarks"></a>Bemerkungen

Dieser \* Operator funktioniert nur im Ausgabe-Iterator-Ausdruck *i* = *x,* um Zeichen zum Stream-Puffer auszugeben. Auf einen Ostreambuf-Iterator angewendet, gibt er den Iterator zurück. iter gibt **iter**zurück , ** \***

### <a name="example"></a>Beispiel

```cpp
// ostreambuf_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;   // no effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_add_add"></a>ostreambuf_iterator::operator++

Ein nicht funktionaler Inkrementoperator, der einen ostream-Iterator zum gleichen Zeichen zurückgibt, das er adressiert hat, bevor der Vorgang aufgerufen wurde.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Zeichen, das ursprünglich behandelt wurde oder auf ein durch die Implementierung definiertes Objekt, das zu `ostreambuf_iterator`\< **CharType**, **Traits**> konvertiert werden kann.

### <a name="remarks"></a>Bemerkungen

Der Operator wird verwendet, um den \* Ausgabeiteratorausdruck *i* = *x*zu implementieren.

### <a name="example"></a>Beispiel

```cpp
// ostreambuf_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_eq"></a>ostreambuf_iterator::operator=

Der Operator fügt ein Zeichen in den zugeordneten Streampuffer ein.

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>Parameter

*_Char*\
Das in den Streampuffer einzufügende Zeichen.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das in den Streampuffer eingefügte Zeichen.

### <a name="remarks"></a>Bemerkungen

Zuweisungsoperator, der verwendet wird, \* um den Ausgabeiteratorausdruck *i* = *x* zum Schreiben in einen Ausgabestream zu implementieren.

### <a name="example"></a>Beispiel

```cpp
// ostreambuf_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratorostreambuf_iterator"></a><a name="ostreambuf_iterator_ostreambuf_iterator"></a>ostreambuf_iterator::ostreambuf_iterator

Erstellt einen `ostreambuf_iterator`, der zum Schreiben von Zeichen in den Ausgabestream initialisiert wird.

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>Parameter

*strbuf*\
Das zur Initialiserung des Ausgabestreampufferzeigers verwendete streambuf-Ausgabeobjekt.

*Ostr*\
Das zur Initialiserung des Ausgabestreampufferzeigers verwendete Streamausgabeobjekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert den Ausgabestream-Pufferzeiger mit *strbuf*.

Der zweite Konstruktor initialisiert den Zeiger auf den Ausgabestreampuffer mit `Ostr`. `rdbuf`. Der gespeicherte Zeiger darf kein NULL-Zeiger sein.

### <a name="example"></a>Beispiel

```cpp
// ostreambuf_iteratorOstreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'O';
   charOut ++;
*charOut  = 'U';
   charOut ++;
*charOut = 'T';
   cout << " are characters output individually." << endl;

   ostreambuf_iterator<char> strOut ( cout );
   string str = "These characters are being written to the output stream.\n ";
   copy ( str.begin ( ), str. end ( ), strOut );
}
/* Output:
OUT are characters output individually.
These characters are being written to the output stream.
*/
```

## <a name="ostreambuf_iteratorostream_type"></a><a name="ostreambuf_iterator_ostream_type"></a>ostreambuf_iterator::ostream_type

Ein Typ, der für den Streamtyp von `ostream_iterator` bereitgestellt wird.

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `basicOstream`\< **CharType**, **Traits**>

### <a name="example"></a>Beispiel

Unter [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) finden Sie ein Beispiel für das Deklarieren und Verwenden von `ostream_type`.

## <a name="ostreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>ostreambuf_iterator::streambuf_type

Ein Typ, der für den Streamtyp von `ostreambuf_iterator` bereitgestellt wird.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist `basic_streambuf` \< ein Synonym für **CharType**, **Traits**>, eine `streambuf` Streamklasse für E/A-Puffer, die auf den Zeichentyp **char**spezialisiert wird.

### <a name="example"></a>Beispiel

Unter [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) finden Sie ein Beispiel für das Deklarieren und Verwenden von `streambuf_type`.

## <a name="ostreambuf_iteratortraits_type"></a><a name="traits_type"></a>ostreambuf_iterator::traits_type

Ein Typ, der für den Merkmaltyp von `ostream_iterator` bereitgestellt wird.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Traits` dar.

### <a name="example"></a>Beispiel

```cpp
// ostreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="see-also"></a>Siehe auch

[\<iterator>](../standard-library/iterator.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standardbibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)
