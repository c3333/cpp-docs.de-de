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
ms.openlocfilehash: 32bfc29b7bc645dd37ae4aaaf498823c0d139dfc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224707"
---
# <a name="num_put-class"></a>num_put-Klasse

Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema Aspekt dienen kann, um Konvertierungen numerischer Werte in Sequenzen vom Typ zu steuern `CharType` .

## <a name="syntax"></a>Syntax

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parameter

*CharType*\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

*OutputIterator*\
Der Typ des Iterators, in den die numerischen Put-Funktionen ihre Ausgabe schreiben.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[num_put](#num_put)|Der Konstruktor für Objekte des Typs `num_put`.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[iter_type](#iter_type)|Ein Typ, der einen Ausgabeiterator beschreibt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[do_put](#do_put)|Eine virtuelle Funktion, die aufgerufen wird, um eine Zahl in eine Sequenz von `CharType`-Objekten zu konvertieren, die die Zahl darstellt, die für ein bestimmtes Gebietsschema formatiert ist.|
|[stellte](#put)|Konvertiert eine Zahl in eine Sequenz von `CharType`-Objekten, die die Zahl darstellt, die für ein bestimmtes Gebietsschema formatiert wird.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<locale>

**Namespace:** std

## <a name="num_putchar_type"></a><a name="char_type"></a>Num_put:: char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `CharType` dar.

## <a name="num_putdo_put"></a><a name="do_put"></a>Num_put::d o_put

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

*weiter*\
Ein Iterator, der das erste Element in der eingefügten Zeichenfolge adressiert.

*_Iosbase*\
Gibt den Datenstrom an, der ein Gebietsschema mit numpunct-Facets enthält, die die Satzzeichen für die Ausgabe und die Flags für das Formatieren der Ausgabe erstellen.

*_Fill*\
Ein Zeichen, das Leerzeichen einfügt.

*ster*\
Die Nummer oder der boolesche Typ, der ausgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die erste Position nach dem jeweils letzten Element verweist.

### <a name="remarks"></a>Bemerkungen

Die erste virtuelle geschützte Member-Funktion generiert sequenzielle Elemente, beginnend bei *Next* , um ein ganzzahliges Ausgabefeld aus dem Wert von *Val*zu erzeugen. Die Funktion gibt einen Iterator zurück, der die nächste Stelle zum Einfügen eines Elements nach dem generierten Ausgabefeld für ganze Zahlen festlegt.

Das ganzzahlige Ausgabefeld wird von denselben Regeln generiert, die von den Druckfunktionen verwendet werden, um eine Reihe von **`char`** Elementen in einer Datei zu generieren. Bei jedem solchen char-Element wird davon ausgegangen, dass es einem entsprechenden Element vom Typ `CharType` durch eine einfache 1-zu-Eins-Zuordnung zugeordnet wird. Wenn eine Druckfunktion ein Feld entweder mit Leerzeichen oder mit der Ziffer 0 füllt, `do_put` verwendet jedoch stattdessen `fill` . Die entsprechende Druckkonvertierungsspezifikation wird wie folgt bestimmt:

- Wenn **iosbase**. [flags](../standard-library/ios-base-class.md#flags)  &  `ios_base::basefield` Flags  ==  `ios_base::` im [Oktober](../standard-library/ios-functions.md#oct)ist die Konvertierungsspezifikation `lo` .

- Wenn **iosbase. Flags**  &  **ios_base:: basefield**  ==  `ios_base::` [Hex](../standard-library/ios-functions.md#hex), ist die Konvertierungsspezifikation `lx` .

- Andernfalls ist die Konvertierungsspezifikation `ld`.

Wenn **iosbase**. [width](../standard-library/ios-base-class.md#width) ungleich null ist, wird eine Feldbreite dieses Werts vorangestellt. Die Funktion ruft **iosbase**. **width**(0) auf, um die Feldbreite auf null zurückzusetzen.

Auffüllung erfolgt nur, wenn die minimale Anzahl von Elementen *N*, die zur Angabe des Ausgabefelds erforderlich ist, kleiner als **iosbase**. [Breite](../standard-library/ios-base-class.md#width). Diese Auffüllung besteht aus einer Sequenz von *N*-  -  **breiten** Kopien von **Fill**. Das Auffüllen erfolgt folgendermaßen:

- Wenn **iosbase**. **flags**  &  `ios_base::adjustfield` Flags  ==  `ios_base::` [Links](../standard-library/ios-functions.md#left)ist das Flag **-** vorangestellt. (Abstand tritt nach dem generierten Text auf.)

- Wenn **iosbase. Flags**  &  **ios_base::-Feld**  ==  `ios_base::` [intern](../standard-library/ios-functions.md#internal)ist, wird das Flag **0** vorangestellt. (Für ein numerisches Ausgabefeld tritt der Abstand dort auf, wo die Druckfunktionen mit 0 auffüllen.)

- Andernfalls wird kein zusätzliches Flag vorangestellt. (Abstand tritt vor der generierten Sequenz auf.)

Letzter Schritt:

- Wenn **iosbase**. **flags**  &  Flags `ios_base::` [Showpos](../standard-library/ios-functions.md#showpos) ist ungleich NULL. das Flag **+** wird der Konvertierungsspezifikation vorangestellt.

- Wenn **iosbase**. **Flags**  &  **ios_base::**[Showbase](../standard-library/ios-functions.md#showbase) ungleich NULL ist, wird das Flag **#** der Konvertierungsspezifikation vorangestellt.

Das Format eines ganzzahligen Ausgabe Felds wird weiter durch das Gebiets Schema- [facetyp](../standard-library/locale-class.md#facet_class)bestimmt, das vom [aufrufuse_facet](../standard-library/locale-functions.md#use_facet)**fac**  <  [Numpunct](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**) zurückgegeben wurde. [getloc](../standard-library/ios-base-class.md#getloc)) zurückgegeben wird. Genauer gesagt:

- **fac**. die [Gruppierung](../standard-library/numpunct-class.md#grouping) bestimmt, wie Ziffern auf der linken Seite eines Dezimal Trennzeichens gruppiert werden.

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) bestimmt die Sequenz, die Gruppen von Ziffern auf der linken Seite eines Dezimal Trennzeichens trennt.

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

- Wenn **iosbase**. **flags**  &  `ios_base::floatfield` Flags  ==  `ios_base::` [korrigiert](../standard-library/ios-functions.md#fixed): die Konvertierungsspezifikation ist `lf` .

- Wenn **iosbase**. **Flags**  &  **ios_base:: floatfield**  ==  `ios_base::` [wissenschaftlich](../standard-library/ios-functions.md#scientific)ist die Konvertierungsspezifikation `le` . Wenn **iosbase**. **flags**  &  Flags `ios_base::` [Großbuchstabe](../standard-library/ios-functions.md#uppercase) ist ungleich 0 (null), `e` wird durch ersetzt `E` .

- Andernfalls ist die Konvertierungsspezifikation **lg**. Wenn **iosbase**. **Flags**  &  **ios_base:: Großbuchstaben** ungleich NULL ist, `g` wird durch ersetzt `G` .

Wenn **iosbase**. **Flags**  &  **ios_base:: Fixed** ist ungleich 0 (null) oder, wenn **iosbase**. [precision](../standard-library/ios-base-class.md#precision) größer als null ist, wird eine Genauigkeit mit dem Wert **iosbase**. **precision** der Konvertierungsspezifikation vorangestellt. Abstände verhalten sich genauso wie bei einem Ausgabefeld für ganze Zahlen. Das Füllzeichen ist **fill**. Letzter Schritt:

- Wenn **iosbase**. **flags**  &  Flags `ios_base::` [Showpos](../standard-library/ios-functions.md#showpos) ist ungleich NULL. das Flag **+** wird der Konvertierungsspezifikation vorangestellt.

- Wenn **iosbase**. **flags**  &  Flags `ios_base::` [showpoint](../standard-library/ios-functions.md#showpoint) ist ungleich NULL. das Flag **#** wird der Konvertierungsspezifikation vorangestellt.

Die vierte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

verhält sich wie das dritte, mit der Ausnahme, dass der Qualifizierer `l` in der Konvertierungsspezifikation durch ersetzt wird `L` .

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

verhält sich wie die erste, mit der Ausnahme, dass ein boolesches Ausgabefeld aus *Val*generiert wird.

Ein boolesches Ausgabefeld nimmt eine von zwei Formen an. Wenn `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) ist **`false`** , gibt die Member-Funktion zurück `do_put(_Next, _Iosbase, _Fill, (long)val)` , die in der Regel eine generierte Sequenz von entweder 0 (für **`false`** ) oder 1 (für **`true`** ) erzeugt. Andernfalls ist die generierte Sequenz entweder *FAC*. [falsename](../standard-library/numpunct-class.md#falsename) (für **`false`** ) oder *FAC*.[ Truename](../standard-library/numpunct-class.md#truename) (für **`true`** ).

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

## <a name="num_putiter_type"></a><a name="iter_type"></a>Num_put:: iter_type

Ein Typ, der einen Ausgabeiterator beschreibt.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter **OutputIterator**.

## <a name="num_putnum_put"></a><a name="num_put"></a>Num_put:: Num_put

Der Konstruktor für Objekte des Typs `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
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

Der Konstruktor initialisiert sein Basisobjekt mit **locale::**[facet](../standard-library/locale-class.md#facet_class)(_ *Refs*).

## <a name="num_putput"></a><a name="put"></a>Num_put::p UT

Konvertiert eine Zahl in eine Sequenz von `CharType` s, die die Zahl darstellt, die für ein bestimmtes Gebiets Schema formatiert ist.

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

*dest*\
Ein Iterator, der das erste Element in der eingefügten Zeichenfolge adressiert.

*_Iosbase*\
Gibt den Datenstrom an, der ein Gebietsschema mit numpunct-Facets enthält, die die Satzzeichen für die Ausgabe und die Flags für das Formatieren der Ausgabe erstellen.

*_Fill*\
Ein Zeichen, das Leerzeichen einfügt.

*ster*\
Die Nummer oder der boolesche Typ, der ausgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die erste Position nach dem jeweils letzten Element verweist.

### <a name="remarks"></a>Bemerkungen

Alle Member-Funktionen geben [Do_put](#do_put)zurück ( `next` , `_Iosbase` , `_Fill` , `val` ).

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

[\<locale>](../standard-library/locale.md)\
[facetklasse](../standard-library/locale-class.md#facet_class)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
