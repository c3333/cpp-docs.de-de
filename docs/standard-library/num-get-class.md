---
title: num_get-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 76d2832141c65ca67c42f1994a3c8f5b532f0092
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373661"
---
# <a name="num_get-class"></a>num_get-Klasse

Eine Klassenvorlage, die ein Objekt beschreibt, das als Gebietsschema dienen kann, um Konvertierungen von Sequenzen vom Typ `CharType` in numerische Werte zu steuern.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parameter

*Chartype*\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

*Inputiterator*\
Der Typ des Iterators, von dem die numerische get-Funktionen ihre Eingabe lesen.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[num_get](#num_get)|Der Konstruktor für Objekte vom Typ `num_get`, die verwendet werden, um numerische Werte aus Sequenzen zu extrahieren.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[iter_type](#iter_type)|Ein Typ, der einen Eingabeiterator beschreibt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[do_get](#do_get)|Eine virtuelle Funktion, die aufgerufen wird, um einen numerischen oder booleschen Wert aus einer Zeichenfolge aufzurufen.|
|[get](#get)|Extrahiert einen numerischen oder booleschen Wert aus einer Zeichenfolge.|

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="num_getchar_type"></a><a name="char_type"></a>num_get::char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter **CharType** dar.

## <a name="num_getdo_get"></a><a name="do_get"></a>num_get::do_get

Eine virtuelle Funktion, die aufgerufen wird, um einen numerischen oder booleschen Wert aus einer Zeichenfolge aufzurufen.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

### <a name="parameters"></a>Parameter

*Ersten*\
Der Anfang des Zeichenbereichs, aus dem die Zahl gelesen wird.

*letzte*\
Das Ende des Zeichenbereichs, aus dem die Zahl gelesen wird.

*iosbase*\
Die [ios_base](../standard-library/ios-base-class.md), deren Flags durch die Konvertierung verwendet werden.

*Staat*\
Der Zustand, zu dem die Failbit (siehe [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)) bei einem Fehler hinzugefügt wird.

*Val*\
Der gelesene Wert.

### <a name="return-value"></a>Rückgabewert

Der Iterator, nachdem der Wert gelesen wurde.

### <a name="remarks"></a>Bemerkungen

Die erste virtuelle geschützte Member-Funktion

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;
```

entspricht sequenziellen *first* Elementen, `[first, last)` die zunächst in der Sequenz beginnen, bis ein vollständiges, nicht leeres Ganzzahleingabefeld erkannt wurde. Bei Erfolg konvertiert es dieses Feld in den entsprechenden Wert als Typ **long**, und speichert das Ergebnis in *val*. Sie gibt einen Iterator zurück, der das erste Element nach dem numerischen Eingabefeld festlegt. Andernfalls speichert die Funktion nichts `ios_base::failbit` in `state` *val* und setzt in . Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Eingabefelds für ganze Zahlen festlegt. In beiden Fällen legt die Funktion `state` für `ios_base::eofbit` fest, wenn der Rückgabewert `last` entspricht.

Das Ganzzahl-Eingabefeld wird von den gleichen Regeln konvertiert, die von den Scanfunktionen zum Abgleichen und Konvertieren einer Reihe von **Zeichenelementen** aus einer Datei verwendet werden. (Jedes dieser **char-Elemente** wird angenommen, dass `Elem` es einem äquivalenten Element des Typs durch eine einfache Zuordnung zu eins zugeordnet wird.) Die entsprechende Scankonvertierungsspezifikation wird wie folgt bestimmt:

Wenn `iosbase.` [ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), `lo`lautet die Konvertierungsspezifikation .

Wenn `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), ist die Konvertierungsspezifikation `lx`.

Wenn `iosbase.flags() & ios_base::basefield == 0`, ist die Konvertierungsspezifikation `li`.

Andernfalls ist die Konvertierungsspezifikation `ld`.

Das Format eines ganzzahligen Eingabefelds wird weiter durch die [Gebietsschema-Facette](../standard-library/locale-class.md#facet_class) `fac` bestimmt, die vom Aufruf [zurückgegeben](../standard-library/locale-functions.md#use_facet) `<`wird use_facet [numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. Dies gilt insbesondere in folgenden Fällen:

`fac.`[numpunct::Gruppierung](../standard-library/numpunct-class.md#grouping) `()` bestimmt, wie Ziffern links von einem Dezimaltrennzeichen gruppiert werden

`fac.`[numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` bestimmt die Reihenfolge, die Zifferngruppen links von einem Beliebigen Dezimalkomma trennt.

Wenn keine Instanzen von `fac.thousands_sep()` im numerischen Eingabefeld auftreten, wird keine Gruppierungseinschränkung auferlegt. Andernfalls werden alle von `fac.grouping()` auferlegten Gruppierungseinschränkung erzwungen und Trennzeichen werden entfernt, bevor die Überprüfungskonvertierung auftritt.

Die vierte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `lu` ersetzt. Bei Erfolg konvertiert es das numerische Eingabefeld in einen Wert vom Typ **unsigned long** und speichert diesen Wert in *val*.

Die fünfte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `lld` ersetzt. Bei Erfolg konvertiert es das numerische Eingabefeld in einen Wert vom Typ **long long** und speichert diesen Wert in *val*.

Die sechste virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `llu` ersetzt. Bei Erfolg konvertiert es das numerische Eingabefeld in einen Wert vom Typ **unsigned long long** und speichert diesen Wert in *val*.

Die siebte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres Gleitkommaeingabefeld zu finden. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` bestimmt die Sequenz, die die ganzzahligen Ziffern von den Bruchziffern trennt. Der entsprechende Überprüfungsonvertierungsspezifizierer ist `lf`.

Die achte virtuell, geschützte Memberfunktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres Gleitkommaeingabefeld zu finden. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` bestimmt die Sequenz, die die ganzzahligen Ziffern von den Bruchziffern trennt. Der entsprechende Überprüfungsonvertierungsspezifizierer ist `lf`.

Die neunte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

verhält sich wie das achte, außer dass der entsprechende Überprüfungskonvertierungsspezifizierer `Lf` ist.

Die zehnte virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

verhält sich wie die erste, außer dass der entsprechende Überprüfungskonvertierungsspezifizierer `p` ist.

Die letzte (elfte) virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres boolesches Eingabefeld zu finden. Bei Erfolg konvertiert es das boolesche Eingabefeld in einen Wert vom Typ **bool** und speichert diesen Wert in *val*.

Ein boolesches Eingabefeld akzeptiert eine von zwei Formen. Wenn `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) falsch ist, ist es mit einem Eingabefeld für ganze Zahlen identisch, mit der Ausnahme, dass der konvertierte Wert entweder 0 (für FALSE) oder 1 (für TRUE) sein muss. Andernfalls muss die Sequenz `fac.`entweder [numpunct::falsename](../standard-library/numpunct-class.md#falsename) `()` (für false) oder `fac.` [numpunct::truename](../standard-library/numpunct-class.md#truename) `()` (für true) entsprechen.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [get](#get), bei dem die virtuelle Memberfunktion durch `do_get` aufgerufen wird.

## <a name="num_getget"></a><a name="get"></a>num_get::get

Extrahiert einen numerischen oder booleschen Wert aus einer Zeichenfolge.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

### <a name="parameters"></a>Parameter

*Ersten*\
Der Anfang des Zeichenbereichs, aus dem die Zahl gelesen wird.

*letzte*\
Das Ende des Zeichenbereichs, aus dem die Zahl gelesen wird.

*iosbase*\
Die [ios_base](../standard-library/ios-base-class.md), deren Flags durch die Konvertierung verwendet werden.

*Staat*\
Der Zustand, zu dem die Failbit (siehe [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)) bei einem Fehler hinzugefügt wird.

*Val*\
Der gelesene Wert.

### <a name="return-value"></a>Rückgabewert

Der Iterator, nachdem der Wert gelesen wurde.

### <a name="remarks"></a>Bemerkungen

Alle Memberfunktionen geben [do_get](#do_get)`( first, last, iosbase, state, val)`zurück.

Die erste virtuelle geschützte Memberfunktion versucht, sequenzielle Elemente zuzuordnen. Sie beginnt zuerst in der Sequenz [ `first`, `last`), bis sie ein vollständiges, nicht leeres Eingabefeld für ganze Zahlen erkannt hat. Wenn dies erfolgreich ist, konvertiert es dieses Feld in den entsprechenden Wert als Typ **long** und speichert das Ergebnis in *val*. Sie gibt einen Iterator zurück, der das erste Element nach dem numerischen Eingabefeld festlegt. Andernfalls speichert die Funktion *val* nichts `ios_base::failbit` im val und setzt sich in *den Zustand*. Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Eingabefelds für ganze Zahlen festlegt. In beiden Fällen, wenn der Rückgabewert gleich `ios_base::eofbit` *last*ist, setzt die Funktion im *Zustand*.

Das Ganzzahl-Eingabefeld wird von den gleichen Regeln konvertiert, die von den Scanfunktionen zum Abgleichen und Konvertieren einer Reihe von **Zeichenelementen** aus einer Datei verwendet werden. Es wird davon ausgegangen, dass jedes dieser `CharType` **char-Elemente** einem äquivalenten Element des Typs durch eine einfache 1:1-Zuordnung zugeordnet wird. Die entsprechende Überprüfungskonvertierungsspezifikation wird wie folgt bestimmt:

- Wenn `iosbase.` [Flags](../standard-library/ios-base-class.md#flags)`& ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), `lo`die Konvertierungsspezifikation ist .

- Wenn `iosbase.flags & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), ist die Konvertierungsspezifikation `lx`.

- Wenn `iosbase.flags & ios_base::basefield == 0`, ist die Konvertierungsspezifikation `li`.

- Andernfalls ist die Konvertierungsspezifikation `ld`.

Das Format eines ganzzahligen Eingabefeldes wird weiter durch die [Gebietsschema-Facette](../standard-library/locale-class.md#facet_class) `fac` bestimmt, die vom Aufruf [use_facet](../standard-library/locale-functions.md#use_facet)`<`[`numpunct`](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[getloc](../standard-library/ios-base-class.md#getloc)`())`zurückgegeben wird. Dies gilt insbesondere in folgenden Fällen:

- `fac.`[Die Gruppierung](../standard-library/numpunct-class.md#grouping) bestimmt, wie Ziffern links von einem Dezimaltrennzeichen gruppiert werden.

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep) bestimmt die Reihenfolge, die Zifferngruppen links von einem Beliebigen Dezimalkomma trennt.

Wenn keine Instanzen von `fac.thousands_sep` im numerischen Eingabefeld auftreten, wird keine Gruppierungseinschränkung auferlegt. Andernfalls werden alle von `fac.grouping` ihnen auferlegten Gruppierungseinschränkungen erzwungen, und Trennzeichen werden entfernt, bevor die Scankonvertierung erfolgt.

Die zweite virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `lu` ersetzt. Bei Erfolg konvertiert das numerische Eingabefeld in einen Wert vom Typ **unsigned long** und speichert diesen Wert in *val*.

Die dritte virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres Gleitkommaeingabefeld zu finden. `fac.`[decimal_point](../standard-library/numpunct-class.md#decimal_point) bestimmt die Reihenfolge, die die ganzzahligen Ziffern von den Bruchziffern trennt. Der entsprechende Überprüfungsonvertierungsspezifizierer ist `lf`.

Die vierte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

verhält sich gleich wie der dritte, mit der `Lf`Ausnahme, dass der entsprechende Scankonvertierungsbezeichner .

Die fünfte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

verhält sich wie die erste, außer dass der entsprechende Überprüfungskonvertierungsspezifizierer `p` ist.

Die sechste virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres boolesches Eingabefeld zu finden. Bei Erfolg konvertiert es das boolesche Eingabefeld in einen Wert vom Typ **bool** und speichert diesen Wert in *val*.

Ein boolesches Eingabefeld nimmt eine von zwei Formen an. Wenn `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) **false**ist, ist es dasselbe wie ein ganzzahliges Eingabefeld, mit der Ausnahme, dass der konvertierte Wert entweder 0 (für **false)** oder 1 (für **true)** sein muss. Andernfalls muss die Sequenz `fac.`entweder [mit falsename](../standard-library/numpunct-class.md#falsename) (für **false**) oder `fac.` [truename](../standard-library/numpunct-class.md#truename) (für **true**) übereinstimmen.

### <a name="example"></a>Beispiel

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="num_getiter_type"></a><a name="iter_type"></a>num_get::iter_type

Ein Typ, der einen Eingabeiterator beschreibt.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `InputIterator` dar.

## <a name="num_getnum_get"></a><a name="num_get"></a>num_get::num_get

Der Konstruktor für Objekte vom Typ `num_get`, die verwendet werden, um numerische Werte aus Sequenzen zu extrahieren.

```cpp
explicit num_get(size_t refs = 0);
```

### <a name="parameters"></a>Parameter

*Refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *refs-Parameter* und ihre Signifikanz sind:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \>1: Diese Werte sind nicht definiert.

Direkte Beispiele sind nicht möglich, da der Destruktor geschützt ist.

Der Konstruktor initialisiert sein `locale::`Basisobjekt mit [Facet](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="see-also"></a>Siehe auch

[\<Gebietsschema>](../standard-library/locale.md)\
[Facette Klasse](../standard-library/locale-class.md#facet_class)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
