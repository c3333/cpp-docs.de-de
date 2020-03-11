---
title: moneypunct-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct
- xlocmon/std::moneypunct::char_type
- xlocmon/std::moneypunct::string_type
- xlocmon/std::moneypunct::curr_symbol
- xlocmon/std::moneypunct::decimal_point
- xlocmon/std::moneypunct::do_curr_symbol
- xlocmon/std::moneypunct::do_decimal_point
- xlocmon/std::moneypunct::do_frac_digits
- xlocmon/std::moneypunct::do_grouping
- xlocmon/std::moneypunct::do_neg_format
- xlocmon/std::moneypunct::do_negative_sign
- xlocmon/std::moneypunct::do_pos_format
- xlocmon/std::moneypunct::do_positive_sign
- xlocmon/std::moneypunct::do_thousands_sep
- xlocmon/std::moneypunct::frac_digits
- xlocmon/std::moneypunct::grouping
- xlocmon/std::moneypunct::neg_format
- xlocmon/std::moneypunct::negative_sign
- xlocmon/std::moneypunct::pos_format
- xlocmon/std::moneypunct::positive_sign
- xlocmon/std::moneypunct::thousands_sep
helpviewer_keywords:
- std::moneypunct [C++]
- std::moneypunct [C++], char_type
- std::moneypunct [C++], string_type
- std::moneypunct [C++], curr_symbol
- std::moneypunct [C++], decimal_point
- std::moneypunct [C++], do_curr_symbol
- std::moneypunct [C++], do_decimal_point
- std::moneypunct [C++], do_frac_digits
- std::moneypunct [C++], do_grouping
- std::moneypunct [C++], do_neg_format
- std::moneypunct [C++], do_negative_sign
- std::moneypunct [C++], do_pos_format
- std::moneypunct [C++], do_positive_sign
- std::moneypunct [C++], do_thousands_sep
- std::moneypunct [C++], frac_digits
- std::moneypunct [C++], grouping
- std::moneypunct [C++], neg_format
- std::moneypunct [C++], negative_sign
- std::moneypunct [C++], pos_format
- std::moneypunct [C++], positive_sign
- std::moneypunct [C++], thousands_sep
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
ms.openlocfilehash: 7960ee8b5e9ce6b27494e896e38bbf6b5256fe7e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884005"
---
# <a name="moneypunct-class"></a>moneypunct-Klasse

Die Klassen Vorlage beschreibt ein Objekt, das als Gebiets Schema Aspekt dienen kann, um die Sequenzen vom Typ *CharType* zu beschreiben, die zur Darstellung eines monetären Eingabe Felds oder eines monetären Ausgabe Felds verwendet werden. Wenn der Vorlagen Parameter " *Intl* " den Wert " *true*" hat, werden internationale Konventionen beachtet.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType, bool Intl>
class moneypunct;
```

### <a name="parameters"></a>Parameter

*CharType* -\
Der Typ, der innerhalb eines Programms verwendet wird, um Zeichen zu codieren.

*Intl* -\
Ein Flag, das festlegt, ob internationale Konventionen beachtet werden sollen.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

Das konstante statische Objekt „intl“ speichert den Wert des Vorlagenparameters *Intl*.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[moneypunct](#moneypunct)|Konstruktor von Objekten des Typs `moneypunct`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[string_type](#string_type)|Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen vom Typ `CharType` enthält.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[curr_symbol](#curr_symbol)|Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Währungssymbol verwendet werden soll.|
|[decimal_point](#decimal_point)|Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Dezimalzeichen verwendet werden soll.|
|[do_curr_symbol](#do_curr_symbol)|Eine geschützte virtuelle Memberfunktion, die eine gebietsschemaspezifische Sequenz von Elementen zurückgibt, die als Währungssymbol verwendet werden soll.|
|[do_decimal_point](#do_decimal_point)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Sequenz von Elementen zurückzugeben, die als Dezimaltrennzeichen verwendet werden soll.|
|[do_frac_digits](#do_frac_digits)|Die geschützte virtuelle Memberfunktion gibt eine gebietsschemaspezifische Anzahl von Ziffern zurück, die rechts vom Dezimaltrennzeichen angezeigt werden sollen.|
|[do_grouping](#do_grouping)|Die geschützte virtuelle Memberfunktion gibt eine gebietsschemaspezifische Regel zur Bestimmung zurück, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden.|
|[do_neg_format](#do_neg_format)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit negativen Zahlen zurückzugeben.|
|[do_negative_sign](#do_negative_sign)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Sequenz von Elementen zurückzugeben, die als Minuszeichen verwendet werden soll.|
|[do_pos_format](#do_pos_format)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit positiven Zahlen zurückzugeben.|
|[do_positive_sign](#do_positive_sign)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Sequenz von Elementen zurückzugeben, die als Pluszeichen verwendet werden soll.|
|[do_thousands_sep](#do_thousands_sep)|Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Sequenz von Elementen zurückzugeben, die als Tausendertrennzeichen verwendet werden soll.|
|[frac_digits](#frac_digits)|Gibt eine gebietsschemaspezifische Anzahl von Ziffern zurück, die auf der rechten Seite eines Dezimaltrennzeichens angezeigt werden sollen.|
|[grouping](#grouping)|Gibt eine gebietsschemaspezifische Regel zur Bestimmung zurück, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden sollen.|
|[neg_format](#neg_format)|Gibt eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit negativen Zahlen zurück.|
|[negative_sign](#negative_sign)|Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Minuszeichen verwendet werden soll.|
|[pos_format](#pos_format)|Gibt eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit positiven Zahlen zurück.|
|[positive_sign](#positive_sign)|Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Pluszeichen verwendet werden soll.|
|[thousands_sep](#thousands_sep)|Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Tausendertrennzeichen verwendet werden soll.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<Gebiets Schema >

**Namespace:** std

## <a name="char_type"></a> moneypunct::char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter **CharType**.

## <a name="curr_symbol"></a> moneypunct::curr_symbol

Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Währungssymbol verwendet werden soll.

```cpp
string_type curr_symbol() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die das Währungssymbol enthält.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_curr_symbol](#do_curr_symbol) zurück.

### <a name="example"></a>Beispiel

```cpp
// moneypunct_curr_symbol.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct < char, true > &mpunct = use_facet < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international currency symbol "<<  mpunct.curr_symbol( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic currency symbol "<<  mpunct2.curr_symbol( ) << endl;
};
```

## <a name="decimal_point"></a> moneypunct::decimal_point

Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Dezimalzeichen verwendet werden soll.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Sequenz von Elementen, die als Dezimaltrennzeichen verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_decimal_point](#do_decimal_point) zurück.

### <a name="example"></a>Beispiel

```cpp
// moneypunct_decimal_pt.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc("german_germany");

   const moneypunct < char, true > &mpunct = use_facet
      < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international decimal point "
        << mpunct.decimal_point( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet
      < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic decimal point "
        << mpunct2.decimal_point( ) << endl;
}
```

```Output
German_Germany.1252 international decimal point ,
German_Germany.1252 domestic decimal point ,
```

## <a name="do_curr_symbol"></a> moneypunct::do_curr_symbol

Eine geschützte virtuelle Memberfunktion, die eine gebietsschemaspezifische Sequenz von Elementen zurückgibt, die als Währungssymbol verwendet werden soll.

```cpp
virtual string_type do_curr_symbol() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Sequenz von Elementen, die als Dezimaltrennzeichen verwendet werden soll.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [curr_symbol](#curr_symbol), bei dem die virtuelle Memberfunktion durch `curr_symbol` aufgerufen wird.

## <a name="do_decimal_point"></a> moneypunct::do_decimal_point

Eine geschützte virtuelle Memberfunktion, die eine gebietsschemaspezifische Sequenz von Elementen zurückgibt, die als Dezimaltrennzeichen verwendet werden soll.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Sequenz von Elementen, die als Dezimaltrennzeichen verwendet werden soll.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [decimal_point](#decimal_point), bei dem die virtuelle Memberfunktion durch `decimal_point` aufgerufen wird.

## <a name="do_frac_digits"></a> moneypunct::do_frac_digits

Eine geschützte virtuelle Memberfunktion, die eine gebietsschemaspezifische Anzahl von Ziffern zurückgibt, die auf der rechten Seiten des Dezimaltrennzeichens angezeigt werden sollen.

```cpp
virtual int do_frac_digits() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Anzahl von Ziffern zurück, die auf der rechten Seiten des Dezimaltrennzeichens angezeigt werden sollen.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [frac_digits](#frac_digits), bei dem die virtuelle Memberfunktion durch `frac_digits` aufgerufen wird.

## <a name="do_grouping"></a> moneypunct::do_grouping

Eine geschützte virtuelle Memberfunktion, die eine gebietsschemaspezifische Regel zurückgibt, mit der festgelegt wird, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Regel, die festlegt, wie Ziffern auf der linken Seite eines Dezimaltrennzeichens gruppiert werden.

### <a name="example"></a>Beispiel

Siehe das Beispiel für die [Gruppierung](#grouping), bei der die Funktion des virtuellen Members von `grouping`aufgerufen wird.

## <a name="do_neg_format"></a> moneypunct::do_neg_format

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit negativen Zahlen zurückzugeben.

```cpp
virtual pattern do_neg_format() const;
```

### <a name="return-value"></a>Rückgabewert

Die geschützte virtuelle Memberfunktion gibt eine gebietsschemaspezifische Regel zurück, mit der festgelegt wird, wie für einen negativen Betrag Ausgabefelder für monetäre Werte generiert werden. Jedes der vier Elemente `pattern::field` kann die folgenden Werte aufweisen:

- `none`, um NULL oder mehr Leerzeichen abzugleichen oder nichts zu generieren.

- `sign`, um ein positives oder negatives Vorzeichen abzugleichen oder zu generieren.

- `space`, um NULL oder mehr Leerzeichen abzugleichen oder ein Leerzeichen zu generieren.

- `symbol`, um ein Währungssymbol abzugleichen oder zu generieren.

- `value`, um einen monetären Wert abzugleichen oder zu generieren.

Komponenten eines monetären Ausgabe Felds werden generiert, und die Komponenten eines monetären Eingabe Felds werden in der Reihenfolge abgeglichen, in der diese Elemente in `pattern::field`angezeigt werden. Jeder der Werte `sign`, `symbol`, `value`und entweder `none` oder `space` muss genau einmal angezeigt werden. Der Wert `none` darf nicht zuerst angezeigt werden. Der Wert **space** darf weder an erster noch an letzter Stelle angezeigt werden. Wenn `Intl` true ist, wird die Reihenfolge `symbol`, `sign`, `none`und dann `value`.

Die Vorlagen Version von `moneypunct`\< **CharType**, **Intl**> `{`**money_base:: Symbol**, **money_base:: Sign**, **money_base:: Value**, **money_base:: None**`}`zurück.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [neg_format](#neg_format), bei dem die virtuelle Memberfunktion durch `neg_format` aufgerufen wird.

## <a name="do_negative_sign"></a> moneypunct::do_negative_sign

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Sequenz von Elementen zurückzugeben, die als Minuszeichen verwendet werden soll.

```cpp
virtual string_type do_negative_sign() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Sequenz von Elementen, die als negatives Vorzeichen verwendet werden soll.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [negative_sign](#negative_sign), bei dem die virtuelle Memberfunktion durch `negative_sign` aufgerufen wird.

## <a name="do_pos_format"></a> moneypunct::do_pos_format

Eine geschützte virtuelle Memberfunktion, die aufgerufen wird, um eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit positiven Zahlen zurückzugeben.

```cpp
virtual pattern do_pos_format() const;
```

### <a name="return-value"></a>Rückgabewert

Die geschützte virtuelle Memberfunktion gibt eine gebietsschemaspezifische Regel zurück, die festlegt, wie für einen positiven Betrag Ausgabefelder für monetäre Werte generiert werden. (Außerdem wird festgelegt, wie die Komponenten eines monetären Eingabe Felds abgeglichen werden.) Die Codierung ist dieselbe wie für [Do_neg_format](#do_neg_format).

Die Vorlagen Version von Moneypunct\< **CharType**, **inputlterator**> gibt `{`**money_base:: Symbol**, **money_base:: Sign**, **money_base:: Value**, **money_base:: None**`}`zurück.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [pos_format](#pos_format), bei dem die virtuelle Memberfunktion durch `pos_format` aufgerufen wird.

## <a name="do_positive_sign"></a> moneypunct::do_positive_sign

Eine geschützte virtuelle Memberfunktion, die eine gebietsschemaspezifische Sequenz von Elementen zurückgibt, die als positives Vorzeichen verwendet werden soll.

```cpp
virtual string_type do_positive_sign() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Sequenz von Elementen, die als positives Vorzeichen verwendet werden soll.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [positive_sign](#positive_sign), bei dem die virtuelle Memberfunktion durch `positive_sign` aufgerufen wird.

## <a name="do_thousands_sep"></a> moneypunct::do_thousands_sep

Eine geschützte virtuelle Memberfunktion, die ein gebietsschemaspezifisches Element zurückgibt, das auf der linken Seite eines Dezimalzeichens als Gruppentrennzeichen verwendet werden soll.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Rückgabewert

Ein gebietsschemaspezifisches Element, das auf der linken Seite eines Dezimalzeichens als Gruppentrennzeichen verwendet werden soll.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [thousands_sep](#thousands_sep), bei dem die virtuelle Memberfunktion durch `thousands_sep` aufgerufen wird.

## <a name="frac_digits"></a> moneypunct::frac_digits

Gibt eine gebietsschemaspezifische Anzahl von Ziffern zurück, die auf der rechten Seite eines Dezimaltrennzeichens angezeigt werden sollen.

```cpp
int frac_digits() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Anzahl von Ziffern zurück, die auf der rechten Seiten des Dezimaltrennzeichens angezeigt werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_frac_digits](#do_frac_digits) zurück.

### <a name="example"></a>Beispiel

```cpp
// moneypunct_frac_digits.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >(loc);
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >(loc);
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="grouping"></a> moneypunct::grouping

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
// moneypunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >( loc );
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >( loc );
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunct"></a> moneypunct::moneypunct

Konstruktor von Objekten des Typs `moneypunct`.

```cpp
explicit moneypunct(size_t _Refs = 0);
```

### <a name="parameters"></a>Parameter

*_Refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *_Refs* -Parameter und ihre Bedeutung lauten:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \> 1: diese Werte sind nicht definiert.

Direkte Beispiele sind nicht möglich, da der Destruktor geschützt ist.

Der Konstruktor initialisiert sein Basisobjekt mit [locale::facet](../standard-library/locale-class.md#facet_class)(_ *Refs*).

## <a name="neg_format"></a> moneypunct::neg_format

Gibt eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit negativen Zahlen zurück.

```cpp
pattern neg_format() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit negativen Beträgen.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_neg_format](#do_neg_format) zurück.

### <a name="example"></a>Beispiel

```cpp
// moneypunct_neg_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( ) {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international negative number format: "
        << mpunct.neg_format( ).field[0]
        << mpunct.neg_format( ).field[1]
        << mpunct.neg_format( ).field[2]
        << mpunct.neg_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative number format: "
        << mpunct2.neg_format( ).field[0]
        << mpunct2.neg_format( ).field[1]
        << mpunct2.neg_format( ).field[2]
        << mpunct2.neg_format( ).field[3] << endl;
}
```

## <a name="negative_sign"></a> moneypunct::negative_sign

Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Minuszeichen verwendet werden soll.

```cpp
string_type negative_sign() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Minuszeichen verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_negative_sign](#do_negative_sign) zurück.

### <a name="example"></a>Beispiel

```cpp
// moneypunct_neg_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international negative sign: "
        << mpunct.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative sign: "
        << mpunct2.negative_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international negative sign: "
        << mpunct3.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic negative sign: "
        << mpunct4.negative_sign( ) << endl;
};
```

```Output
German_Germany.1252 international negative sign: -
German_Germany.1252 domestic negative sign: -
French_France.1252 international negative sign: -
French_France.1252 domestic negative sign: -
```

## <a name="pos_format"></a> moneypunct::pos_format

Gibt eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit positiven Zahlen zurück.

```cpp
pattern pos_format() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Regel zur Formatierung von Ausgaben mit positiven Beträgen.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_pos_format](#do_pos_format) zurück.

### <a name="example"></a>Beispiel

```cpp
// moneypunct_pos_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main() {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international positive number format: "
        << mpunct.pos_format( ).field[0]
        << mpunct.pos_format( ).field[1]
        << mpunct.pos_format( ).field[2]
        << mpunct.pos_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive number format: "
        << mpunct2.pos_format( ).field[0]
        << mpunct2.pos_format( ).field[1]
        << mpunct2.pos_format( ).field[2]
        << mpunct2.pos_format( ).field[3] << endl;
}
```

## <a name="positive_sign"></a> moneypunct::positive_sign

Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Pluszeichen verwendet werden soll.

```cpp
string_type positive_sign() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Sequenz von Elementen, die als positive Vorzeichen verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_positive_sign](#do_positive_sign) zurück.

### <a name="example"></a>Beispiel

```cpp
// moneypunct_pos_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international positive sign:"
        << mpunct.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive sign:"
        << mpunct2.positive_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international positive sign:"
        << mpunct3.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic positive sign:"
        << mpunct4.positive_sign( ) << endl;
};
```

```Output
German_Germany.1252 international positive sign:
German_Germany.1252 domestic positive sign:
French_France.1252 international positive sign:
French_France.1252 domestic positive sign:
```

## <a name="string_type"></a> moneypunct::string_type

Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen des Typs **CharType** enthält.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [basic_string](../standard-library/basic-string-class.md) , deren Objekte Kopien der Interpunktions Sequenzen speichern können.

## <a name="thousands_sep"></a> moneypunct::thousands_sep

Gibt eine gebietsschemaspezifische Sequenz von Elementen zurück, die als Tausendertrennzeichen verwendet werden soll.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Rückgabewert

Eine gebietsschemaspezifische Sequenz von Elementen, die als Tausendertrennzeichen verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_thousands_sep](#do_thousands_sep) zurück.

### <a name="example"></a>Beispiel

```cpp
// moneypunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international thousands separator: "
        << mpunct.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic thousands separator: "
        << mpunct2.thousands_sep( ) << endl << endl;

   locale loc2( "english_canada" );

   const moneypunct <char, true> &mpunct3 =
       use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international thousands separator: "
        << mpunct3.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic thousands separator: "
        << mpunct4.thousands_sep( ) << endl;
}
```

```Output
German_Germany.1252 international thousands separator: .
German_Germany.1252 domestic thousands separator: .

English_Canada.1252 international thousands separator: ,
English_Canada.1252 domestic thousands separator: ,
```

## <a name="see-also"></a>Weitere Informationen

[\<locale>](../standard-library/locale.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
