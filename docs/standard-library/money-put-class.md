---
title: money_put-Klasse
ms.date: 11/01/2018
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
ms.openlocfilehash: d15667f4e30561dbba024f877530c4ff0f824f64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224746"
---
# <a name="money_put-class"></a>money_put-Klasse

In der Klassen Vorlage wird ein Objekt beschrieben, das als Gebiets Schema Aspekt dienen kann, um Konvertierungen von Währungswerten in Sequenzen vom Typ zu steuern `CharType` .

## <a name="syntax"></a>Syntax

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Parameter

*CharType*\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

*OutputIterator*\
Der Typ des Iterators, in den die monetären Put-Funktionen ihre Ausgabe schreiben.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[money_put](#money_put)|Der Konstruktor für Objekte des Typs `money_put`.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[iter_type](#iter_type)|Ein Typ, der einen Ausgabeiterator beschreibt.|
|[string_type](#string_type)|Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen vom Typ `CharType` enthält.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[do_put](#do_put)|Eine virtuelle Funktion, die aufgerufen wird, um entweder eine Zahl oder eine Zeichenfolge in eine Zeichenfolge zu konvertieren, die einen monetären Wert darstellt.|
|[stellte](#put)|Konvertiert entweder eine Zahl oder eine Zeichenfolge in eine Zeichenfolge, die einen monetären Wert darstellt.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<locale>

**Namespace:** std

## <a name="money_putchar_type"></a><a name="char_type"></a>Money_put:: char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter **CharType** dar.

## <a name="money_putdo_put"></a><a name="do_put"></a>Money_put::d o_put

Eine virtuelle Funktion, die aufgerufen wird, um entweder eine Zahl oder eine Zeichenfolge in eine Zeichenfolge zu konvertieren, die einen monetären Wert darstellt.

```cpp
virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Parameter

*weiter*\
Ein Iterator, der das erste Element in der eingefügten Zeichenfolge adressiert.

*_Intl*\
Ein boolescher Wert, der den Typ des Währungs Symbols angibt, der in der Sequenz erwartet wird: **`true`** , wenn International **`false`** .

*_Iosbase*\
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*_Fill*\
Ein Zeichen, das Leerzeichen einfügt.

*ster*\
Ein zu konvertierendes Zeichenfolgenobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die erste Position nach dem jeweils letzten Element verweist.

### <a name="remarks"></a>Bemerkungen

Die erste virtuelle geschützte Member-Funktion generiert sequenzielle Elemente, beginnend bei *Next* , um ein monetäre Ausgabefeld aus dem [string_type](#string_type) -Objekt *Val*zu erzeugen. Die von *Val* gesteuerte Sequenz muss mit einer oder mehreren Dezimalziffern beginnen, wobei optional ein Minuszeichen (-) vorangestellt wird, das den Betrag darstellt. Die Funktion gibt einen Iterator zurück, der das erste Element nach dem generierten Ausgabefeld für monetäre Werte festlegt.

Die zweite virtuelle geschützte Member-Funktion verhält sich wie die erste, mit der Ausnahme, dass Sie zuerst *Val* in eine Folge von Dezimalziffern konvertiert, optional mit einem Minuszeichen, und dann diese Sequenz wie oben beschrieben konvertiert.

Das Format eines monetären Ausgabe Felds wird durch den Gebiets Schema [locale facet](../standard-library/locale-class.md#facet_class) -factorybereich bestimmt, der durch den (effektiven) [calluse_facet](../standard-library/locale-functions.md#use_facet)  <  [Moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**> > ( **iosbase**) zurückgegeben wird. [getloc](../standard-library/ios-base-class.md#getloc)) zurückgegeben wird.

Genauer gesagt:

- **fac**. [pos_format](../standard-library/moneypunct-class.md#pos_format) bestimmt die Reihenfolge, in der Komponenten des Felds für einen nicht negativen Wert generiert werden.

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) bestimmt die Reihenfolge, in der Komponenten des Felds für einen negativen Wert generiert werden.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) bestimmt die Sequenz von Elementen, die für ein Währungssymbol erzeugt werden soll.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) bestimmt die Sequenz von Elementen, die für ein positives Vorzeichen generiert werden soll.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) bestimmt die Sequenz von Elementen, die für ein negatives Vorzeichen generiert werden soll.

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) bestimmt, wie Ziffern auf der linken Seite des Dezimaltrennzeichens gruppiert werden.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) bestimmt das Element, das Gruppen von Ziffern auf der linken Seite eines Dezimaltrennzeichens trennt.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) bestimmt das Element, das ganzzahlige Ziffern von Bruchziffern trennt.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) bestimmt die Anzahl signifikanter Ziffern auf der rechten Seite eines Dezimaltrennzeichens.

Wenn die Zeichenfolge ( **fac**. `negative_sign` oder **fac**. `positive_sign`) über mehr als ein Element verfügt, wird nur das erste Element generiert, bei dem das dem **money_base::sign** entsprechende Element im Formatmuster ( **fac**. `neg_format` oder **fac**. `pos_format`). Alle übrigen Elemente werden am Ende des Ausgabefelds für monetäre Werte generiert.

Wenn **iosbase**. [Flags](../standard-library/ios-base-class.md#flags)  &  [Showbase](../standard-library/ios-functions.md#showbase) ist ungleich 0 (null), die Zeichenfolge **FAC**. `curr_symbol` dort generiert, wo das dem **money_base::symbol** entsprechende Element im Formatmuster angezeigt wird. Andernfalls wird kein Währungssymbol generiert.

Erfolgen keine Gruppierungseinschränkungen durch **fac**. **grouping** (sein erstes Element weist den Wert CHAR_MAX auf), werden keine Instanzen von **fac**. `thousands_sep` im Wertteil des Ausgabefelds für monetäre Werte generiert (in dem das dem **money_base::symbol** entsprechende Element im Formatmuster angezeigt wird). Wenn **fac**. `frac_digits` 0 (null) ist, wird keine Instanz von **fac**. `decimal_point` nach den Dezimalstellen generiert. Ansonsten platziert das jeweilige Ausgabefeld für monetäre Werte die niederwertigen **fac**. `frac_digits`-Dezimalstellen auf der rechten Seite des Dezimaltrennzeichens.

Abstände treten wie bei Ausgabefeldern für numerische Werte auf. Wenn **iosbase**. **Flags**  &  **iosbase**. [internal](../standard-library/ios-functions.md#internal) ungleich 0 (null) ist, werden jedoch alle internen Abstände dort generiert, wo das dem **money_base::space** entsprechende Element im Formatmuster angezeigt wird (sofern es angezeigt wird). Andernfalls treten interne Abstände vor der generierten Sequenz auf. Das Füllzeichen ist **fill**.

Die Funktion ruft **iosbase**. **width**(0) auf, um die Feldbreite auf null zurückzusetzen.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [put](#put), bei dem die virtuelle Memberfunktion durch **put** aufgerufen wird.

## <a name="money_putiter_type"></a><a name="iter_type"></a>Money_put:: iter_type

Ein Typ, der einen Ausgabeiterator beschreibt.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter **OutputIterator**.

## <a name="money_putmoney_put"></a><a name="money_put"></a>Money_put:: Money_put

Der Konstruktor für Objekte des Typs `money_put`.

```cpp
explicit money_put(size_t _Refs = 0);
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

Der Konstruktor initialisiert sein Basisobjekt mit **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="money_putput"></a><a name="put"></a>Money_put::p UT

Konvertiert entweder eine Zahl oder eine Zeichenfolge in eine Zeichenfolge, die einen monetären Wert darstellt.

```cpp
iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Parameter

*weiter*\
Ein Iterator, der das erste Element in der eingefügten Zeichenfolge adressiert.

*_Intl*\
Ein boolescher Wert, der den Typ des Währungs Symbols angibt, der in der Sequenz erwartet wird: **`true`** , wenn International **`false`** .

*_Iosbase*\
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*_Fill*\
Ein Zeichen, das Leerzeichen einfügt.

*ster*\
Ein zu konvertierendes Zeichenfolgenobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die erste Position nach dem jeweils letzten Element verweist.

### <a name="remarks"></a>Bemerkungen

Beide Member-Funktionen geben [Do_put](#do_put)zurück ( `next` , `_Intl` , `_Iosbase` , `_Fill` , `val` ).

### <a name="example"></a>Beispiel

```cpp
// money_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

int main()
{
    std::locale loc( "german_germany" );
    std::basic_stringstream<char> psz;

    psz.imbue(loc);
    psz.flags(psz.flags() | std::ios_base::showbase); // force the printing of the currency symbol
    std::use_facet<std::money_put<char> >(loc).put(std::basic_ostream<char>::_Iter(psz.rdbuf()), true, psz, ' ', 100012);
    if (psz.fail())
        std::cout << "money_put() FAILED" << std::endl;
    else
        std::cout << "money_put() = \"" << psz.rdbuf()->str() << "\"" << std::endl;
}
```

```Output
money_put() = "EUR1.000,12"
```

## <a name="money_putstring_type"></a><a name="string_type"></a>Money_put:: string_type

Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen vom Typ `CharType` enthält.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung von Klassen Vorlagen [basic_string](../standard-library/basic-string-class.md) , deren Objekte Sequenzen von Elementen aus der Quell Sequenz speichern können.

## <a name="see-also"></a>Weitere Informationen

[\<locale>](../standard-library/locale.md)\
[facetklasse](../standard-library/locale-class.md#facet_class)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
