---
title: money_get-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
ms.openlocfilehash: ab49dad1a24e57eb33834cc651d9ccdb50abe68c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224759"
---
# <a name="money_get-class"></a>money_get-Klasse

Die Klassen Vorlage beschreibt ein Objekt, das als Gebiets Schema Aspekt fungieren kann, um Konvertierungen von Sequenzen vom Typ `CharType` in monetäre Werte zu steuern.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parameter

*CharType*\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

*InputIterator*\
Der Typ des Iterators, von dem die get-Funktionen ihre Eingabe lesen.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[money_get](#money_get)|Der Konstruktor für Objekte vom Typ `money_get`, die verwendet werden, um numerische Werte aus Sequenzen zu extrahieren, die monetäre Werte darstellen.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[iter_type](#iter_type)|Ein Typ, der einen Eingabeiterator beschreibt.|
|[string_type](#string_type)|Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen vom Typ `CharType` enthält.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[do_get](#do_get)|Eine virtuelle Funktion, die aufgerufen wird, um einen Zahlenwert aus einer Zeichenfolge zu extrahieren, die einen monetären Wert darstellt.|
|[get](#get)|Extrahiert einen numerischen Wert aus einer Zeichenfolge, die einen monetären Wert darstellt.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<locale>

**Namespace:** std

## <a name="money_getchar_type"></a><a name="char_type"></a>Money_get:: char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter *CharType* dar.

## <a name="money_getdo_get"></a><a name="do_get"></a>Money_get::d o_get

Eine virtuelle Funktion, die aufgerufen wird, um einen Zahlenwert aus einer Zeichenfolge zu extrahieren, die einen monetären Wert darstellt.

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const
```

### <a name="parameters"></a>Parameter

*erstes*\
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*letzten*\
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*Intl*\
Ein boolescher Wert, der den Typ des Währungs Symbols angibt, der in der Sequenz erwartet wird: **`true`** , wenn International **`false`** .

*Iosbase*\
Ein Format-Flag, das wenn eingestellt angibt, dass das Währungssymbol optional ist, andernfalls ist es erforderlich.

*Land*\
Je nachdem, ob die Vorgänge erfolgreich waren, legt dieses Element die entsprechenden Bitmaskenelemente für den Streamstatus fest.

*ster*\
Eine Zeichenfolge zum Speichern der konvertierten Sequenz.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld für den monetären Wert adressiert.

### <a name="remarks"></a>Bemerkungen

Die erste virtuelle geschützte Memberfunktion versucht, sequenzielle Elemente zuzuordnen. Sie beginnt zuerst in der Sequenz [ `first`, `last`), bis sie ein vollständiges, nicht leeres Eingabefeld für monetäre Werte erkannt hat. Bei erfolgreichem Erfolg konvertiert Sie dieses Feld in eine Sequenz von einer oder mehreren Dezimalziffern, wobei optional ein Minuszeichen ( `-` ) vorangestellt wird, um den Betrag darzustellen, und speichert das Ergebnis im [string_type](#string_type) Objekt *Val*. Sie gibt einen Iterator zurück, der das erste Element nach dem Eingabefeld für monetäre Werte festlegt. Andernfalls speichert die Funktion eine leere Sequenz in *Val* und legt den `ios_base::failbit` *Status fest*. Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Eingabefelds für monetäre Werte festlegt. In beiden Fällen legt die Funktion `State` für `ios_base::eofbit` fest, wenn der Rückgabewert `last` entspricht.

Die zweite virtuelle geschützte Member-Funktion verhält sich wie die erste, mit der Ausnahme, dass bei erfolgreicher Ausführung die optional signierte Ziffern Sequenz in einen Wert des Typs konvertiert **`long double`** und dieser Wert in *Val*gespeichert wird.

Das Format eines monetären Eingabe Felds wird von dem Gebiets Schema- [faceter](../standard-library/locale-class.md#facet_class)**FAC** bestimmt, der durch den effektiven-aufrufuse_facet [use_facet](../standard-library/locale-functions.md#use_facet)  <  [Moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**>> ( **iosbase**) zurückgegeben wird. [getloc](../standard-library/ios-base-class.md#getloc)) zurückgegeben wird.

Genauer gesagt:

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) bestimmt die Reihenfolge, in der Komponenten des Felds auftreten.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) bestimmt die Sequenz der Elemente, aus der ein Währungssymbol besteht.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) bestimmt die Sequenz der Elemente, aus der ein positiven Vorzeichen besteht.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) bestimmt die Sequenz der Elemente, aus der ein negativen Vorzeichen besteht.

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) bestimmt, wie Ziffern auf der linken Seite des Dezimaltrennzeichens gruppiert werden.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) bestimmt das Element, das Gruppen von Ziffern auf der linken Seite eines Dezimaltrennzeichens trennt.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) bestimmt das Element, das ganzzahlige Ziffern von Bruchziffern trennt.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) bestimmt die Anzahl signifikanter Ziffern auf der rechten Seite eines Dezimaltrennzeichens. Wird ein Geldbetrag mit mehr Bruchziffern analysiert, als durch `frac_digits` aufgerufen werden, beendet `do_get` die Analyse, wenn höchstens `frac_digits`-Zeichen verbraucht wurden.

Wenn die Zeichenfolge ( **fac**. `negative_sign` oder **fac**. `positive_sign`) über mehr als ein Element verfügt, wird nur das erste Element zugeordnet, bei dem das dem **money_base::sign** entsprechende Element im Formatmuster ( **fac**. `neg_format`). Alle übrigen Elemente werden am Ende des Eingabefelds für monetäre Werte zugeordnet. Wenn keine Zeichenfolge über ein erstes Element verfügt, das dem nächsten Element im Eingabefeld für monetäre Werte entspricht, wird die Zeichenfolge als leer angenommen. Das Vorzeichen ist in diesem Fall positiv.

Wenn **iosbase**. [Flags](../standard-library/ios-base-class.md#flags)  &  [Showbase](../standard-library/ios-functions.md#showbase) ist ungleich 0 (null), die Zeichenfolge **FAC**. `curr_symbol` dort zugeordnet werden, wo das dem **money_base::symbol** entsprechende Element im Formatmuster angezeigt wird. Andernfalls gilt: Wenn **money_base::symbol** am Ende des Formatmusters auftritt und keine weiteren Elemente der Zeichenfolge verbleiben, wird das Währungssymbol nicht zugeordnet. Ansonsten wird das Währungssymbol optional zugeordnet.

Wenn keine Instanzen von **fac**. `thousands_sep` im Wertteil des Eingabefelds für monetäre Werte (in dem das dem **money_base::symbol** entsprechende Element im Formatmuster angezeigt wird) auftritt, erfolgt keine Gruppierungseinschränkung. Andernfalls werden alle durch **fac**. **grouping** auferlegte Gruppierungseinschränkungen erzwungen. Bitte beachten Sie, dass die resultierende Ziffernsequenz einer ganzen Zahl entspricht, deren niederwertige **fac**. `frac_digits`-Dezimalstellen auf der rechten Seite des Dezimaltrennzeichens berücksichtigt werden.

Dort, wo das dem **money_base::space** entsprechende Element im Formatmuster angezeigt wird, werden beliebig viele Leerstellen zugeordnet, wenn das Element nicht am Ende des Formatmusters angezeigt wird. Andernfalls werden keine internen Leerzeichen zugeordnet. Ein Element *ch* gilt als Leerraum, wenn [Use_facet](../standard-library/locale-functions.md#use_facet)  <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( **iosbase**). [getloc](../standard-library/ios-base-class.md#getloc)) zurückgegeben wird. [is](../standard-library/ctype-class.md#is)( **Ctype_base:: Space**, *ch*) ist **`true`** .

### <a name="example"></a>Beispiel

Siehe das Beispiel für [get](#get), mit dem `do_get` aufgerufen wird.

## <a name="money_getget"></a><a name="get"></a>Money_get:: Get

Extrahiert einen numerischen Wert aus einer Zeichenfolge, die einen monetären Wert darstellt.

```cpp
iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const;
```

### <a name="parameters"></a>Parameter

*erstes*\
Der Eingabeiterator, der den Anfang der zu konvertierenden Sequenz adressiert.

*letzten*\
Der Eingabeiterator, der das Ende der zu konvertierenden Sequenz adressiert.

*Intl*\
Ein boolescher Wert, der den Typ des Währungs Symbols angibt, der in der Sequenz erwartet wird: **`true`** , wenn International **`false`** .

*Iosbase*\
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*Land*\
Legt die entsprechenden Bitmaskenelemente für den Streamstatus fest, je nachdem, ob die Vorgänge erfolgreich waren.

*ster*\
Eine Zeichenfolge zum Speichern der konvertierten Sequenz.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator,der das erste Element nach dem Eingabefeld für den monetären Wert adressiert.

### <a name="remarks"></a>Bemerkungen

Beide Member-Funktionen geben [do_get](#do_get)zurück `(first, last, Intl, Iosbase, State, val)` .

### <a name="example"></a>Beispiel

```cpp
// money_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;

int main( )
{
   locale loc( "german_germany" );

   basic_stringstream< char > psz;
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";
   basic_stringstream< char > psz2;
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();

   ios_base::iostate st = 0;
   long double fVal;

   psz.flags( psz.flags( )|ios_base::showbase );
   // Which forced the READING the currency symbol
   psz.imbue(loc);
   use_facet < money_get < char > >( loc ).
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"
           << endl;
   else
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "
           << fVal/100.0 << endl;

   use_facet < money_get < char > >( loc ).
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"
           << endl;
   else
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "
           << fVal/100.0 << endl;
};
```

## <a name="money_getiter_type"></a><a name="iter_type"></a>Money_get:: iter_type

Ein Typ, der einen Eingabeiterator beschreibt.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter **InputIterator**.

## <a name="money_getmoney_get"></a><a name="money_get"></a>Money_get:: Money_get

Der Konstruktor für Objekte vom Typ `money_get`, die verwendet werden, um numerische Werte aus Sequenzen zu extrahieren, die monetäre Werte darstellen.

```cpp
explicit money_get(size_t _Refs = 0);
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

Der Konstruktor initialisiert sein Basisobjekt mit **locale::**[Face(](../standard-library/locale-class.md#facet_class)*_Refs*).

## <a name="money_getstring_type"></a><a name="string_type"></a>Money_get:: string_type

Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen des Typs **CharType** enthält.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Siehe auch

[\<locale>](../standard-library/locale.md)\
[facetklasse](../standard-library/locale-class.md#facet_class)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
