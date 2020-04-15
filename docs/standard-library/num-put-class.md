---
title: num_put-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
ms.openlocfilehash: 3f65d7140bb5c691fa58ec9d74ceda5573280ddb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373643"
---
# <a name="num_put-class"></a>num_put-Klasse

Eine Klassenvorlage, die ein Objekt beschreibt, das als Gebietsschema dienen kann, um `CharType`Konvertierungen numerischer Werte in Sequenzen vom Typ zu steuern.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parameter

*Chartype*\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

*OutputIterator*\
Der Typ des Iterators, in den die numerischen Put-Funktionen ihre Ausgabe schreiben.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[num_put](#num_put)|Der Konstruktor für Objekte des Typs `num_put`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[iter_type](#iter_type)|Ein Typ, der einen Ausgabeiterator beschreibt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[do_put](#do_put)|Eine virtuelle Funktion, die aufgerufen wird, um eine Zahl in eine Sequenz von `CharType`-Objekten zu konvertieren, die die Zahl darstellt, die für ein bestimmtes Gebietsschema formatiert ist.|
|[setzen](#put)|Konvertiert eine Zahl in eine Sequenz von `CharType`-Objekten, die die Zahl darstellt, die für ein bestimmtes Gebietsschema formatiert wird.|

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="num_putchar_type"></a><a name="char_type"></a>num_put::char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `CharType` dar.

## <a name="num_putdo_put"></a><a name="do_put"></a>num_put::do_put

Eine virtuelle Funktion, die aufgerufen wird, um eine Zahl in eine Sequenz von `CharType`-Objekten zu konvertieren, die die Zahl darstellt, die für ein bestimmtes Gebietsschema formatiert ist.

```cpp
virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const unsigned long long val) const;
```

### <a name="parameters"></a>Parameter

*nächster*\
Ein Iterator, der das erste Element in der eingefügten Zeichenfolge adressiert.

*_iosbase*\
Gibt den Datenstrom an, der ein Gebietsschema mit numpunct-Facets enthält, die die Satzzeichen für die Ausgabe und die Flags für das Formatieren der Ausgabe erstellen.

*_Fill*\
Ein Zeichen, das Leerzeichen einfügt.

*Val*\
Die Nummer oder der boolesche Typ, der ausgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die erste Position nach dem jeweils letzten Element verweist.

### <a name="remarks"></a>Bemerkungen

Die erste virtual protected Member-Funktion generiert sequenzielle Elemente, die *nebenbei* beginnen, um ein ganzzahliges Ausgabefeld aus dem Wert von *val*zu erzeugen. Die Funktion gibt einen Iterator zurück, der die nächste Stelle zum Einfügen eines Elements nach dem generierten Ausgabefeld für ganze Zahlen festlegt.

Das Ganzzahlausgabefeld wird von den gleichen Regeln generiert, die von den Druckfunktionen zum Generieren einer Reihe von **Zeichenelementen** in einer Datei verwendet werden. Es wird davon ausgegangen, dass jedes dieser `CharType` char-Elemente einem äquivalenten Element des Typs durch eine einfache 1:1-Zuordnung zugeordnet wird. Wenn eine Druckfunktion jedoch ein Feld mit Leerzeichen `do_put` oder `fill`der Ziffer 0 auffüllt, wird stattdessen verwendet. Die entsprechende Druckkonvertierungsspezifikation wird wie folgt bestimmt:

- Wenn **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & Flags ==  `lo`oct , die Konvertierungsspezifikation ist .[oct](../standard-library/ios-functions.md#oct)`ios_base::basefield``ios_base::`

- Wenn **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), `lx`lautet die Konvertierungsspezifikation .

- Andernfalls ist die Konvertierungsspezifikation `ld`.

Wenn **iosbase**. [width](../standard-library/ios-base-class.md#width) ungleich null ist, wird eine Feldbreite dieses Werts vorangestellt. Die Funktion ruft **iosbase**. **width**(0) auf, um die Feldbreite auf null zurückzusetzen.

Auffüllung erfolgt nur, wenn die minimale Anzahl von Elementen *N*, die zur Angabe des Ausgabefelds erforderlich ist, kleiner als **iosbase**. [Breite](../standard-library/ios-base-class.md#width). Eine solche Polsterung besteht aus einer Sequenz von - **N-Breite** Kopien der **Füllung**. *N* Das Auffüllen erfolgt folgendermaßen:

- Wenn **iosbase**. **Links,** & `ios_base::adjustfield`[left](../standard-library/ios-functions.md#left)wird **-** dem Flag vorangestellt. == `ios_base::` (Abstand tritt nach dem generierten Text auf.)

- Wenn **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal), wird dem Flag **0** vorangestellt. (Für ein numerisches Ausgabefeld tritt der Abstand dort auf, wo die Druckfunktionen mit 0 auffüllen.)

- Andernfalls wird kein zusätzliches Flag vorangestellt. (Abstand tritt vor der generierten Sequenz auf.)

Letzter Schritt:

- Wenn **iosbase**. **flags** & Flags`ios_base::`[showpos](../standard-library/ios-functions.md#showpos) ist ungleich **+** Null, das Flag wird der Konvertierungsspezifikation vorangestellt.

- Wenn **iosbase**. **Flags** & **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) ist ungleich Null, das Flag **#** wird der Konvertierungsspezifikation vorangestellt.

Das Format eines Ausgabefelds für ganze Zahlen hängt darüber hinaus von der [localefacet](../standard-library/locale-class.md#facet_class)**fac** ab, die vom Aufruf [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**> ( **iosbase** zurückgegeben wird. [getloc](../standard-library/ios-base-class.md#getloc)) zurückgegeben wird. Dies gilt insbesondere in folgenden Fällen:

- **fac**. [Die Gruppierung](../standard-library/numpunct-class.md#grouping) bestimmt, wie Ziffern links von einem Dezimaltrennzeichen gruppiert werden

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) bestimmt die Reihenfolge, die Zifferngruppen links von einem Beliebigen trennt

Erfolgen keine Gruppierungseinschränkungen durch **fac**. **grouping** (sein erstes Element weist den Wert CHAR_MAX auf), werden keine Instanzen von **fac**. `thousands_sep` im Ausgabefeld generiert. Andernfalls werden Trennzeichen eingefügt, nachdem die Druckkonvertierung erfolgt.

Die zweite virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `lu` ersetzt.

Die dritte virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

verhält sich wie die erste, außer dass sie ein Gleitkommaausgabefeld aus dem Wert **val** erzeugt. **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) bestimmt die Sequenz, die ganzzahlige Ziffern von Bruchziffern trennt. Die entsprechende Druckkonvertierungsspezifikation wird wie folgt bestimmt:

- Wenn **iosbase**. **flags** & Flags ==  `lf`behoben, lautet die Konvertierungsspezifikation .[fixed](../standard-library/ios-functions.md#fixed)`ios_base::floatfield``ios_base::`

- Wenn **iosbase**. **Flags** & **ios_base::floatfield** == `ios_base::`[scientific](../standard-library/ios-functions.md#scientific), `le`die Konvertierungsspezifikation ist . Wenn **iosbase**. **flags** & Flags`ios_base::`[Großbuchstabe](../standard-library/ios-functions.md#uppercase) ist `e` ungleich `E`Null, wird durch ersetzt.

- Andernfalls ist die Konvertierungsspezifikation **lg**. Wenn **iosbase**. **Flags** & **ios_base::großist** ungleich `g` Null, `G`wird durch ersetzt.

Wenn **iosbase**. **Flags** & **ios_base::fixed** ist ungleich Null oder wenn **iosbase**. [precision](../standard-library/ios-base-class.md#precision) größer als null ist, wird eine Genauigkeit mit dem Wert **iosbase**. **precision** der Konvertierungsspezifikation vorangestellt. Abstände verhalten sich genauso wie bei einem Ausgabefeld für ganze Zahlen. Das Füllzeichen ist **fill**. Letzter Schritt:

- Wenn **iosbase**. **flags** & Flags`ios_base::`[showpos](../standard-library/ios-functions.md#showpos) ist ungleich **+** Null, das Flag wird der Konvertierungsspezifikation vorangestellt.

- Wenn **iosbase**. **flags** & Flags`ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) ist ungleich **#** Null, das Flag wird der Konvertierungsspezifikation vorangestellt.

Die vierte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

verhält sich gleich wie der dritte, mit der Ausnahme, dass der Qualifizierer `l` in der Konvertierungsspezifikation durch `L`ersetzt wird.

Die fünfte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

verhält sich wie die erste, außer dass die Konvertierungsspezifikation `p`**,** sowie alle Qualifizierer Abstand angeben müssen.

Die sechste virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

verhält sich wie das erste, außer dass es ein boolesches Ausgabefeld von *val*generiert.

Ein boolesches Ausgabefeld nimmt eine von zwei Formen an. Wenn `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) **false**ist, `do_put(_Next, _Iosbase, _Fill, (long)val)`gibt die Memberfunktion zurück , die in der Regel eine generierte Sequenz von 0 (für **false**) oder 1 (für **true)** erzeugt. Andernfalls ist die generierte Sequenz entweder *fac*. [falsename](../standard-library/numpunct-class.md#falsename) (für **false**) oder *fac*. [truename](../standard-library/numpunct-class.md#truename) (für **true**).

Die siebte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `lld` ersetzt.

Die achte virtuell, geschützte Memberfunktion:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `llu` ersetzt.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [put](#put), mit dem `do_put` aufgerufen wird.

## <a name="num_putiter_type"></a><a name="iter_type"></a>num_put::iter_type

Ein Typ, der einen Ausgabeiterator beschreibt.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter **OutputIterator**.

## <a name="num_putnum_put"></a><a name="num_put"></a>num_put::num_put

Der Konstruktor für Objekte des Typs `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
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

Der Konstruktor initialisiert sein Basisobjekt mit **locale::**[facet](../standard-library/locale-class.md#facet_class)(_ *Refs*).

## <a name="num_putput"></a><a name="put"></a>num_put::put

Konvertiert eine Zahl in `CharType`eine Sequenz von s, die die für ein bestimmtes Gebietsschema formatierte Zahl darstellt.

```cpp
iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Unsigned long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;
```

### <a name="parameters"></a>Parameter

*Dest*\
Ein Iterator, der das erste Element in der eingefügten Zeichenfolge adressiert.

*_iosbase*\
Gibt den Datenstrom an, der ein Gebietsschema mit numpunct-Facets enthält, die die Satzzeichen für die Ausgabe und die Flags für das Formatieren der Ausgabe erstellen.

*_Fill*\
Ein Zeichen, das Leerzeichen einfügt.

*Val*\
Die Nummer oder der boolesche Typ, der ausgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die erste Position nach dem jeweils letzten Element verweist.

### <a name="remarks"></a>Bemerkungen

Alle Memberfunktionen [do_put](#do_put)geben `next` `_Iosbase`do_put `_Fill` `val`zurück ( , , , ).

### <a name="example"></a>Beispiel

```cpp
// num_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );
   basic_stringstream<char> psz2;
   ios_base::iostate st = 0;
   long double fVal;
   cout << "The thousands separator is: "
        << use_facet < numpunct <char> >(loc).thousands_sep( )
        << endl;

   psz2.imbue( loc );
   use_facet < num_put < char > >
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),
                    psz2, ' ', fVal=1000.67);

   if ( st & ios_base::failbit )
      cout << "num_put( ) FAILED" << endl;
   else
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;
}
```

```Output
The thousands separator is: .
num_put( ) = 1.000,67
```

## <a name="see-also"></a>Siehe auch

[\<Gebietsschema>](../standard-library/locale.md)\
[Facette Klasse](../standard-library/locale-class.md#facet_class)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
