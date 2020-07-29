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
ms.openlocfilehash: e4e21bd0c1323afdc2c81a0e581c3557b8040193
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202440"
---
# <a name="ostreambuf_iterator-class"></a>ostreambuf_iterator Class

Die Klassen Vorlage ostreambuf_iterator beschreibt ein ausgabeiteratorobjekt, das aufeinander folgende Zeichen Elemente mit dem Extraktions **Operator>>** in den Ausgabestream schreibt. Die `ostreambuf_iterator` unterscheiden sich von denen der [ostream_iterator-Klasse](../standard-library/ostream-iterator-class.md) insofern, als dass sie über Zeichen anstelle eines generischen Typs im Hinblick auf den Objekttyp verfügen, der in den Ausgabestream eingefügt wird.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parameter

*CharType*\
Der Typ, der den Zeichentyp für das ostreambuf_iterator-Objekt darstellt. Dieses Argument ist optional, und der Standardwert ist **`char`** .

*Aufweisen*\
Der Typ, der den Zeichentyp für das ostreambuf_iterator-Objekt darstellt. Dieses Argument ist optional, und der Standardwert ist `char_traits` \< *CharType> . *

## <a name="remarks"></a>Bemerkungen

Die ostreambuf_iterator-Klasse muss den Anforderungen für einen Ausgabeiterator entsprechen. Algorithmen können mit `ostreambuf_iterator` direkt in Ausgabestreams geschrieben werden. Die Klasse bietet einen Streamiterator auf niedriger Ebene, der Zugriff auf den unformatierten E/A-Stream in Form von Zeichen und die Fähigkeit erlaubt, die Pufferung und die Zeichenumsetzungen zu umgehen, die mit den Streamiteratoren auf hoher Ebene verbunden sind.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Erstellt einen `ostreambuf_iterator`, der zum Schreiben von Zeichen in den Ausgabestream initialisiert wird.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, der für den Zeichentyp von `ostreambuf_iterator` bereitgestellt wird.|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Ein Typ, der für den Streamtyp von `ostream_iterator` bereitgestellt wird.|
|[streambuf_type](#streambuf_type)|Ein Typ, der für den Streamtyp von `ostreambuf_iterator` bereitgestellt wird.|
|[traits_type](#traits_type)|Ein Typ, der für den Merkmaltyp von `ostream_iterator` bereitgestellt wird.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[erreicht](#failed)|Testet eine Einfügung in den Ausgabestreampuffer auf Fehler.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[KOM](#op_star)|Dereferenzierungsoperator, der zum Implementieren des ausgabeiteratorausdrucks verwendet wird \* `i`  =  `x` .|
|[Operator + +](#op_add_add)|Ein nicht funktionaler Inkrementoperator, der einen `ostreambuf_iterator` zum gleichen Objekt zurückgibt, das er adressiert hat, bevor der Vorgang aufgerufen wurde.|
|[Operator =](#op_eq)|Der Operator fügt ein Zeichen in den zugeordneten Streampuffer ein.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<iterator>

**Namespace:** std

## <a name="ostreambuf_iteratorchar_type"></a><a name="char_type"></a>Ostreambuf_iterator:: char_type

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

## <a name="ostreambuf_iteratorfailed"></a><a name="failed"></a>Ostreambuf_iterator:: failed

Testet eine Einfügung in den Ausgabestreampuffer auf Fehler.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Rückgabewert

**`true`** Wenn keine Einfügung in den ausgabestreampuffer zuvor fehlgeschlagen ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt zurück **`true`** , wenn der-Befehl von `operator=` **subf**_-> bei jeder früheren Verwendung von " `sputc` **EOF**" zurückgegeben hat.

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

## <a name="ostreambuf_iteratoroperator"></a><a name="op_star"></a>Ostreambuf_iterator::-Operator\*

Ein nicht funktionaler Dereferenzierungsoperator, der zum Implementieren des ausgabeiteratorausdrucks \* *i*  =  *x*verwendet wird.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Rückgabewert

Das ostreambuf-Iteratorobjekt.

### <a name="remarks"></a>Bemerkungen

Dieser Operator funktioniert nur im ausgabeiteratorausdruck \* *i*  =  *x* , um Zeichen in den Streampuffer auszugeben. Wird auf einen Ostreambuf-Iterator angewendet, der den Iterator zurückgibt. ** \* ITER** gibt **ITER**zurück,

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

## <a name="ostreambuf_iteratoroperator"></a><a name="op_add_add"></a>Ostreambuf_iterator:: Operator + +

Ein nicht funktionaler Inkrementoperator, der einen ostream-Iterator zum gleichen Zeichen zurückgibt, das er adressiert hat, bevor der Vorgang aufgerufen wurde.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das ursprünglich adressierte Zeichen oder auf ein von der Implementierung definiertes Objekt, das in konvertierbar ist `ostreambuf_iterator` \< **CharType**, **Traits**> .

### <a name="remarks"></a>Bemerkungen

Der-Operator wird zum Implementieren des ausgabeiteratorausdrucks \* *i*  =  *x*verwendet.

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

## <a name="ostreambuf_iteratoroperator"></a><a name="op_eq"></a>Ostreambuf_iterator:: Operator =

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

Zuweisungs Operator, der zum Implementieren des ausgabeiteratorausdrucks \* *i*  =  *x* zum Schreiben in einen Ausgabestream verwendet wird.

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

## <a name="ostreambuf_iteratorostreambuf_iterator"></a><a name="ostreambuf_iterator_ostreambuf_iterator"></a>Ostreambuf_iterator:: ostreambuf_iterator

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

Der erste Konstruktor initialisiert den Ausgabestream-Puffer Zeiger mit " *strinbuf*".

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

## <a name="ostreambuf_iteratorostream_type"></a><a name="ostreambuf_iterator_ostream_type"></a>Ostreambuf_iterator:: ostream_type

Ein Typ, der für den Streamtyp von `ostream_iterator` bereitgestellt wird.

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für.`basicOstream`\< **CharType**, **Traits**>

### <a name="example"></a>Beispiel

Unter [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) finden Sie ein Beispiel für das Deklarieren und Verwenden von `ostream_type`.

## <a name="ostreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>Ostreambuf_iterator:: streambuf_type

Ein Typ, der für den Streamtyp von `ostreambuf_iterator` bereitgestellt wird.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `basic_streambuf` \< **CharType**, **Traits**> , eine Streamklasse für e/a-Puffer, die `streambuf` bei der Spezialisierung auf den Zeichentyp wird **`char`** .

### <a name="example"></a>Beispiel

Unter [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) finden Sie ein Beispiel für das Deklarieren und Verwenden von `streambuf_type`.

## <a name="ostreambuf_iteratortraits_type"></a><a name="traits_type"></a>Ostreambuf_iterator:: traits_type

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

## <a name="see-also"></a>Weitere Informationen

[\<iterator>](../standard-library/iterator.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
