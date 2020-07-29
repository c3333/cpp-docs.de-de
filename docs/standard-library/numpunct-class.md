---
title: numpunct-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct
- xlocnum/std::numpunct::char_type
- xlocnum/std::numpunct::string_type
- xlocnum/std::numpunct::decimal_point
- xlocnum/std::numpunct::do_decimal_point
- xlocnum/std::numpunct::do_falsename
- xlocnum/std::numpunct::do_grouping
- xlocnum/std::numpunct::do_thousands_sep
- xlocnum/std::numpunct::do_truename
- xlocnum/std::numpunct::falsename
- xlocnum/std::numpunct::grouping
- xlocnum/std::numpunct::thousands_sep
- xlocnum/std::numpunct::truename
helpviewer_keywords:
- std::numpunct [C++]
- std::numpunct [C++], char_type
- std::numpunct [C++], string_type
- std::numpunct [C++], decimal_point
- std::numpunct [C++], do_decimal_point
- std::numpunct [C++], do_falsename
- std::numpunct [C++], do_grouping
- std::numpunct [C++], do_thousands_sep
- std::numpunct [C++], do_truename
- std::numpunct [C++], falsename
- std::numpunct [C++], grouping
- std::numpunct [C++], thousands_sep
- std::numpunct [C++], truename
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
ms.openlocfilehash: 602d8edef80f0e4d4abe4cb6773b774d174e1cbe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202817"
---
# <a name="numpunct-class"></a>numpunct-Klasse

Eine Klassen Vorlage, die ein Objekt beschreibt, das als lokaler Aspekt dienen kann, um die Sequenzen vom Typ zu beschreiben, `CharType` mit denen Informationen zur Formatierung und Interpunktions Zeichen von numerischen und booleschen Ausdrücken dargestellt werden.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType>
class numpunct : public locale::facet;
```

### <a name="parameters"></a>Parameter

*CharType*\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[numpunct](#numpunct)|Der Konstruktor für Objekte des Typs `numpunct`.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[string_type](#string_type)|Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen vom Typ `CharType` enthält.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[decimal_point](#decimal_point)|Gibt ein gebietsschemaspezifisches Element zurück, das als Dezimaltrennzeichen verwendet werden soll.|
|[do_decimal_point](#do_decimal_point)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um ein gebietsschemaspezifisches Element zurückzugeben, das als Dezimaltrennzeichen verwendet werden soll.|
|[do_falsename](#do_falsename)|Eine geschützte virtuelle Member-Funktion, die aufgerufen wird, um eine Zeichenfolge zurückzugeben, die als Textdarstellung des Werts verwendet werden soll **`false`** .|
|[do_grouping](#do_grouping)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Regel zur Bestimmung zurückzugeben, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden.|
|[do_thousands_sep](#do_thousands_sep)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um ein gebietsschemaspezifisches Element zurückzugeben, das als Tausendertrennzeichen verwendet werden soll.|
|[do_truename](#do_truename)|Eine geschützte virtuelle Member-Funktion, die aufgerufen wird, um eine Zeichenfolge zurückzugeben, die als Textdarstellung des Werts verwendet werden soll **`true`** .|
|[falsename](#falsename)|Gibt eine Zeichenfolge zurück, die als Textdarstellung des Werts verwendet werden soll **`false`** .|
|[Bündelung](#grouping)|Gibt eine gebietsschemaspezifische Regel zur Bestimmung zurück, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden sollen.|
|[thousands_sep](#thousands_sep)|Gibt ein gebietsschemaspezifisches Element zurück, das als Tausendertrennzeichen verwendet werden soll.|
|[truename](#truename)|Gibt eine Zeichenfolge zurück, die als Textdarstellung des Werts verwendet werden soll **`true`** .|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<locale>

**Namespace:** std

## <a name="numpunctchar_type"></a><a name="char_type"></a>Numpunct:: char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter **CharType.**

## <a name="numpunctdecimal_point"></a><a name="decimal_point"></a>Numpunct::d ecimal_point

Gibt ein gebietsschemaspezifisches Element zurück, das als Dezimaltrennzeichen verwendet werden soll.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Rückgabewert

Ein gebietsschemaspezifisches Element, das als Dezimaltrennzeichen verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_decimal_point](#do_decimal_point) zurück.

### <a name="example"></a>Beispiel

```cpp
// numpunct_decimal_point.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet <numpunct <char> >( loc);
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="numpunctdo_decimal_point"></a><a name="do_decimal_point"></a>Numpunct::d o_decimal_point

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um ein gebietsschemaspezifisches Element zurückzugeben, das als Dezimaltrennzeichen verwendet werden soll.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Rückgabewert

Ein gebietsschemaspezifisches Element, das als Dezimaltrennzeichen verwendet werden soll.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [decimal_point](#decimal_point), bei dem die virtuelle Memberfunktion durch `decimal_point` aufgerufen wird.

## <a name="numpunctdo_falsename"></a><a name="do_falsename"></a>Numpunct::d o_falsename

Die geschützte virtuelle Member-Funktion gibt eine Sequenz zurück, die als Textdarstellung des Werts verwendet werden soll **`false`** .

```cpp
virtual string_type do_falsename() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die eine Sequenz enthält, die als Textdarstellung des Werts verwendet werden soll **`false`** .

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt die Zeichenfolge "false" zurück, die den Wert in allen Gebiets Schemas darstellt **`false`** .

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [falsename](#falsename), bei dem die virtuelle Memberfunktion durch `falsename` aufgerufen wird.

## <a name="numpunctdo_grouping"></a><a name="do_grouping"></a>Numpunct::d o_grouping

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Regel zur Bestimmung zurückzugeben, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Regel, die festlegt, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Memberfunktion gibt eine gebietsschemaspezifische Regel zur Bestimmung zurück, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden. Die Codierung ist dieselbe wie für **lconv::grouping**.

### <a name="example"></a>Beispiel

Siehe das Beispiel für die [Gruppierung](#grouping), bei der die Funktion des virtuellen Members von aufgerufen wird `grouping` .

## <a name="numpunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>Numpunct::d o_thousands_sep

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um ein gebietsschemaspezifisches Element zurückzugeben, das als Tausendertrennzeichen verwendet werden soll.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt ein gebietsschemaspezifisches Element zurück, das als Tausendertrennzeichen verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Member-Funktion gibt ein Gebiets Schema spezifisches Element vom Typ zurück `CharType` , das auf der linken Seite eines Dezimal Trennzeichens als Gruppen Trennzeichen verwendet werden soll.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [thousands_sep](#thousands_sep), bei dem die virtuelle Memberfunktion durch `thousands_sep` aufgerufen wird.

## <a name="numpunctdo_truename"></a><a name="do_truename"></a>Numpunct::d o_truename

Eine geschützte virtuelle Member-Funktion, die aufgerufen wird, um eine Zeichenfolge zurückzugeben, die als Textdarstellung des Werts verwendet werden soll **`true`** .

```cpp
virtual string_type do_truename() const;
```

### <a name="remarks"></a>Bemerkungen

Eine Zeichenfolge, die als Textdarstellung des Werts verwendet werden soll **`true`** .

Alle Gebiets Schemas geben eine Zeichenfolge "true" zurück, um den Wert darzustellen **`true`** .

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [truename](#truename), bei dem die virtuelle Memberfunktion durch `truename` aufgerufen wird.

## <a name="numpunctfalsename"></a><a name="falsename"></a>Numpunct:: falsename

Gibt eine Zeichenfolge zurück, die als Textdarstellung des Werts verwendet werden soll **`false`** .

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge mit einer Sequenz von `CharType` s, die als Textdarstellung des Werts verwendet werden soll **`false`** .

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt die Zeichenfolge "false" zurück, die den Wert in allen Gebiets Schemas darstellt **`false`** .

Die Memberfunktion gibt [do_falsename](#do_falsename) zurück.

### <a name="example"></a>Beispiel

```cpp
// numpunct_falsename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2( "French" );
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="numpunctgrouping"></a><a name="grouping"></a>Numpunct:: Gruppierung

Gibt eine gebietsschemaspezifische Regel zur Bestimmung zurück, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden sollen.

```cpp
string grouping() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Regel, die festlegt, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_grouping](#do_grouping) zurück.

### <a name="example"></a>Beispiel

```cpp
// numpunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany");

   const numpunct <char> &npunct =
       use_facet < numpunct <char> >( loc );
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(npunct.grouping ( )[i])
           << endl;
   }
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
```

## <a name="numpunctnumpunct"></a><a name="numpunct"></a>Numpunct:: Numpunct

Der Konstruktor für Objekte des Typs `numpunct`.

```cpp
explicit numpunct(size_t _Refs = 0);
```

### <a name="parameters"></a>Parameter

*_Refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *_Refs* -Parameter und ihre Bedeutung lauten:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \>1: diese Werte sind nicht definiert.

Direkte Beispiele sind nicht möglich, da der Destruktor geschützt ist.

Der Konstruktor initialisiert sein Basisobjekt mit **locale::**[Face(](../standard-library/locale-class.md#facet_class) `_Refs` ).

## <a name="numpunctstring_type"></a><a name="string_type"></a>Numpunct:: string_type

Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen des Typs **CharType** enthält.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [basic_string](../standard-library/basic-string-class.md) , deren Objekte Kopien der Interpunktions Sequenzen speichern können.

## <a name="numpunctthousands_sep"></a><a name="thousands_sep"></a>Numpunct:: thousands_sep

Gibt ein gebietsschemaspezifisches Element zurück, das als Tausendertrennzeichen verwendet werden soll.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Rückgabewert

Ein gebietsschemaspezifisches Element, das als Tausendertrennzeichen verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_thousands_sep](#do_thousands_sep) zurück.

### <a name="example"></a>Beispiel

```cpp
// numpunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet < numpunct < char > >( loc );
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="numpuncttruename"></a><a name="truename"></a>Numpunct:: Truename

Gibt eine Zeichenfolge zurück, die als Textdarstellung des Werts verwendet werden soll **`true`** .

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die als Textdarstellung des Werts verwendet werden soll **`true`** .

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_truename](#do_truename) zurück.

Alle Gebiets Schemas geben eine Zeichenfolge "true" zurück, um den Wert darzustellen **`true`** .

### <a name="example"></a>Beispiel

```cpp
// numpunct_truename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2("French");
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="see-also"></a>Weitere Informationen

[\<locale>](../standard-library/locale.md)\
[facetklasse](../standard-library/locale-class.md#facet_class)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
