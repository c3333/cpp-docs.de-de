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
ms.openlocfilehash: 035cc4e7b9cfac262979509bf7b4570e2c55336c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377425"
---
# <a name="money_put-class"></a>money_put-Klasse

Die Klassenvorlage beschreibt ein Objekt, das als Gebietsschema dienen kann, um Konvertierungen von monetären Werten in Sequenzen vom Typ `CharType`zu steuern.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Parameter

*Chartype*\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

*OutputIterator*\
Der Typ des Iterators, in den die monetären Put-Funktionen ihre Ausgabe schreiben.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[money_put](#money_put)|Der Konstruktor für Objekte des Typs `money_put`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[iter_type](#iter_type)|Ein Typ, der einen Ausgabeiterator beschreibt.|
|[string_type](#string_type)|Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen vom Typ `CharType` enthält.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[do_put](#do_put)|Eine virtuelle Funktion, die aufgerufen wird, um entweder eine Zahl oder eine Zeichenfolge in eine Zeichenfolge zu konvertieren, die einen monetären Wert darstellt.|
|[setzen](#put)|Konvertiert entweder eine Zahl oder eine Zeichenfolge in eine Zeichenfolge, die einen monetären Wert darstellt.|

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="money_putchar_type"></a><a name="char_type"></a>money_put::char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter **CharType** dar.

## <a name="money_putdo_put"></a><a name="do_put"></a>money_put::do_put

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

*nächster*\
Ein Iterator, der das erste Element in der eingefügten Zeichenfolge adressiert.

*_Intl*\
Ein boolescher Wert, der den Typ des in der Sequenz vorgesehenen Währungssymbols angibt (**TRUE**, wenn international; **FALSE**, wenn national).

*_iosbase*\
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*_Fill*\
Ein Zeichen, das Leerzeichen einfügt.

*Val*\
Ein zu konvertierendes Zeichenfolgenobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die erste Position nach dem jeweils letzten Element verweist.

### <a name="remarks"></a>Bemerkungen

Die erste virtual protected Member-Funktion generiert sequenzielle Elemente, die *nebenan* beginnen, um ein monetäres Ausgabefeld aus dem [string_type-Objekt](#string_type) *val*zu erzeugen. Die von *val* gesteuerte Sequenz muss mit einer oder mehreren Dezimalstellen beginnen, optional vor einem Minuszeichen (-), das den Betrag darstellt. Die Funktion gibt einen Iterator zurück, der das erste Element nach dem generierten Ausgabefeld für monetäre Werte festlegt.

Die zweite virtuelle geschützte Memberfunktion verhält sich genauso wie die erste, mit der Ausnahme, dass sie effektiv zuerst *val* in eine Folge von Dezimalstellen konvertiert, optional einem Minuszeichen vorangestellt ist, und dann diese Sequenz wie oben konvertiert.

Das Format eines Eingabefelds für monetäre Werte richtet sich nach dem [Gebietsschemafacet](../standard-library/locale-class.md#facet_class) „fac“, das durch den (effektiven) Aufruf [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) zurückgegeben wird.

Dies gilt insbesondere in folgenden Fällen:

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

Wenn **iosbase**. [Flags](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) ist ungleich Null, die Zeichenfolge **fac**. `curr_symbol` dort generiert, wo das dem **money_base::symbol** entsprechende Element im Formatmuster angezeigt wird. Andernfalls wird kein Währungssymbol generiert.

Erfolgen keine Gruppierungseinschränkungen durch **fac**. **grouping** (sein erstes Element weist den Wert CHAR_MAX auf), werden keine Instanzen von **fac**. `thousands_sep` im Wertteil des Ausgabefelds für monetäre Werte generiert (in dem das dem **money_base::symbol** entsprechende Element im Formatmuster angezeigt wird). Wenn **fac**. `frac_digits` 0 (null) ist, wird keine Instanz von **fac**. `decimal_point` nach den Dezimalstellen generiert. Ansonsten platziert das jeweilige Ausgabefeld für monetäre Werte die niederwertigen **fac**. `frac_digits`-Dezimalstellen auf der rechten Seite des Dezimaltrennzeichens.

Abstände treten wie bei Ausgabefeldern für numerische Werte auf. Wenn **iosbase**. **flags** & **iosbase**. [internal](../standard-library/ios-functions.md#internal) ungleich 0 (null) ist, werden jedoch alle internen Abstände dort generiert, wo das dem **money_base::space** entsprechende Element im Formatmuster angezeigt wird (sofern es angezeigt wird). Andernfalls treten interne Abstände vor der generierten Sequenz auf. Das Füllzeichen ist **fill**.

Die Funktion ruft **iosbase**. **width**(0) auf, um die Feldbreite auf null zurückzusetzen.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [put](#put), bei dem die virtuelle Memberfunktion durch **put** aufgerufen wird.

## <a name="money_putiter_type"></a><a name="iter_type"></a>money_put::iter_type

Ein Typ, der einen Ausgabeiterator beschreibt.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter **OutputIterator**.

## <a name="money_putmoney_put"></a><a name="money_put"></a>money_put::money_put

Der Konstruktor für Objekte des Typs `money_put`.

```cpp
explicit money_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parameter

*_refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *parameter _Refs* und deren Signifikanz sind:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \>1: Diese Werte sind nicht definiert.

Direkte Beispiele sind nicht möglich, da der Destruktor geschützt ist.

Der Konstruktor initialisiert sein Basisobjekt mit **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="money_putput"></a><a name="put"></a>money_put::put

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

*nächster*\
Ein Iterator, der das erste Element in der eingefügten Zeichenfolge adressiert.

*_Intl*\
Ein boolescher Wert, der den Typ des in der Sequenz vorgesehenen Währungssymbols angibt (**TRUE**, wenn international; **FALSE**, wenn national).

*_iosbase*\
Ein Formatkennzeichen, das bei Verwendung angibt, dass das Währungssymbol optional ist. Ansonsten ist das Währungssymbol erforderlich.

*_Fill*\
Ein Zeichen, das Leerzeichen einfügt.

*Val*\
Ein zu konvertierendes Zeichenfolgenobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die erste Position nach dem jeweils letzten Element verweist.

### <a name="remarks"></a>Bemerkungen

Beide Memberfunktionen [do_put](#do_put)geben `next` `_Intl`do_put `_Iosbase` `_Fill`zurück `val`( , , , , .

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

## <a name="money_putstring_type"></a><a name="string_type"></a>money_put::string_type

Ein Typ, der eine Zeichenfolge beschreibt, die Zeichen vom Typ `CharType` enthält.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung von [Klassenvorlagenbasic_string](../standard-library/basic-string-class.md) deren Objekte Sequenzen von Elementen aus der Quellsequenz speichern können.

## <a name="see-also"></a>Siehe auch

[\<Gebietsschema>](../standard-library/locale.md)\
[Facette Klasse](../standard-library/locale-class.md#facet_class)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
