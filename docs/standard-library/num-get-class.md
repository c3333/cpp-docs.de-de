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
ms.openlocfilehash: d5a88e904c437e79eabfa854a196aa48dbad955e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228166"
---
# <a name="num_get-class"></a>num_get-Klasse

Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema-Facette dienen kann, um Konvertierungen von Sequenzen vom Typ `CharType` in numerische Werte zu steuern.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parameter

*CharType*\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

*InputIterator*\
Der Typ des Iterators, von dem die numerische get-Funktionen ihre Eingabe lesen.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[num_get](#num_get)|Der Konstruktor für Objekte vom Typ `num_get`, die verwendet werden, um numerische Werte aus Sequenzen zu extrahieren.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[iter_type](#iter_type)|Ein Typ, der einen Eingabeiterator beschreibt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[do_get](#do_get)|Eine virtuelle Funktion, die aufgerufen wird, um einen numerischen oder booleschen Wert aus einer Zeichenfolge aufzurufen.|
|[get](#get)|Extrahiert einen numerischen oder booleschen Wert aus einer Zeichenfolge.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<locale>

**Namespace:** std

## <a name="num_getchar_type"></a><a name="char_type"></a>Num_get:: char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter **CharType** dar.

## <a name="num_getdo_get"></a><a name="do_get"></a>Num_get::d o_get

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

*erstes*\
Der Anfang des Zeichenbereichs, aus dem die Zahl gelesen wird.

*letzten*\
Das Ende des Zeichenbereichs, aus dem die Zahl gelesen wird.

*iosbase*\
Die [ios_base](../standard-library/ios-base-class.md), deren Flags durch die Konvertierung verwendet werden.

*Land*\
Der Zustand, zu dem die Failbit (siehe [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)) bei einem Fehler hinzugefügt wird.

*ster*\
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

gleicht sequenzielle Elemente ab, beginnend an *erster Stelle* in der Sequenz `[first, last)` , bis Sie ein ganzes, nicht leeres ganzzahliges Eingabefeld erkannt hat. Im Erfolgsfall konvertiert Sie dieses Feld in den entsprechenden Wert als Typ **`long`** und speichert das Ergebnis in *Val*. Sie gibt einen Iterator zurück, der das erste Element nach dem numerischen Eingabefeld festlegt. Andernfalls speichert die Funktion nichts im *Val* und legt `ios_base::failbit` in fest `state` . Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Eingabefelds für ganze Zahlen festlegt. In beiden Fällen legt die Funktion `state` für `ios_base::eofbit` fest, wenn der Rückgabewert `last` entspricht.

Das ganzzahlige Eingabefeld wird von denselben Regeln konvertiert, die von den Scanfunktionen verwendet werden, um eine Reihe von **`char`** Elementen aus einer Datei zu vergleichen und zu konvertieren. (Bei jedem solchen **`char`** Element wird davon ausgegangen, dass es einem entsprechenden Element vom Typ `Elem` durch eine einfache Zuordnung vom Typ "eins zu eins" zugeordnet wird.) Die entsprechende Scan Konvertierungsspezifikation wird wie folgt bestimmt:

Wenn `iosbase.` [ios_base:: Flags](../standard-library/ios-base-class.md#flags) `() & ios_base::basefield == ios_base::` [Oct](../standard-library/ios-functions.md#oct), ist die Konvertierungsspezifikation `lo` .

Wenn `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), ist die Konvertierungsspezifikation `lx`.

Wenn `iosbase.flags() & ios_base::basefield == 0`, ist die Konvertierungsspezifikation `li`.

Andernfalls ist die Konvertierungsspezifikation `ld`.

Das Format eines ganzzahligen Eingabe Felds wird weiter von dem Gebiets Schema [Aspekt](../standard-library/locale-class.md#facet_class) bestimmt, der `fac` durch den Aufrufen [Use_facet](../standard-library/locale-functions.md#use_facet) `<` [Numpunct](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [ios_base:: getloc](../standard-library/ios-base-class.md#getloc)zurückgegeben wurde `())` . Genauer gesagt:

`fac.`[Numpunct:: Gruppierung](../standard-library/numpunct-class.md#grouping) `()` bestimmt, wie Ziffern auf der linken Seite eines Dezimal Trennzeichens gruppiert werden.

`fac.`[Numpunct:: thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` bestimmt die Sequenz, die Gruppen von Ziffern auf der linken Seite eines Dezimal Trennzeichens trennt.

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

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `lu` ersetzt. Wenn erfolgreich, konvertiert Sie das numerische Eingabefeld in einen Wert vom Typ **`unsigned long`** und speichert diesen Wert in *Val*.

Die fünfte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `lld` ersetzt. Wenn erfolgreich, konvertiert Sie das numerische Eingabefeld in einen Wert vom Typ **`long long`** und speichert diesen Wert in *Val*.

Die sechste virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `llu` ersetzt. Wenn erfolgreich, konvertiert Sie das numerische Eingabefeld in einen Wert vom Typ **`unsigned long long`** und speichert diesen Wert in *Val*.

Die siebte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres Gleitkommaeingabefeld zu finden. `fac.`[Numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point) `()` bestimmt die Sequenz, die die ganzzahligen Ziffern von den Bruch Ziffern trennt. Der entsprechende Überprüfungsonvertierungsspezifizierer ist `lf`.

Die achte virtuell, geschützte Memberfunktion:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres Gleitkommaeingabefeld zu finden. `fac.`[Numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point) `()` bestimmt die Sequenz, die die ganzzahligen Ziffern von den Bruch Ziffern trennt. Der entsprechende Überprüfungsonvertierungsspezifizierer ist `lf`.

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

Die zehnte virtuelle geschützte Member-Funktion:

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

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres boolesches Eingabefeld zu finden. Wenn erfolgreich, konvertiert Sie das boolesche Eingabefeld in einen Wert vom Typ **`bool`** und speichert diesen Wert in *Val*.

Ein boolesches Eingabefeld akzeptiert eine von zwei Formen. Wenn `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) falsch ist, ist es mit einem Eingabefeld für ganze Zahlen identisch, mit der Ausnahme, dass der konvertierte Wert entweder 0 (für FALSE) oder 1 (für TRUE) sein muss. Andernfalls muss die Sequenz entweder `fac.` [Numpunct:: falsename](../standard-library/numpunct-class.md#falsename) `()` (für false) oder `fac.` [Numpunct:: Truename](../standard-library/numpunct-class.md#truename) `()` (für true) entsprechen.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [get](#get), bei dem die virtuelle Memberfunktion durch `do_get` aufgerufen wird.

## <a name="num_getget"></a><a name="get"></a>Num_get:: Get

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

*erstes*\
Der Anfang des Zeichenbereichs, aus dem die Zahl gelesen wird.

*letzten*\
Das Ende des Zeichenbereichs, aus dem die Zahl gelesen wird.

*iosbase*\
Die [ios_base](../standard-library/ios-base-class.md), deren Flags durch die Konvertierung verwendet werden.

*Land*\
Der Zustand, zu dem die Failbit (siehe [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)) bei einem Fehler hinzugefügt wird.

*ster*\
Der gelesene Wert.

### <a name="return-value"></a>Rückgabewert

Der Iterator, nachdem der Wert gelesen wurde.

### <a name="remarks"></a>Bemerkungen

Alle Member-Funktionen geben [do_get](#do_get)zurück `( first, last, iosbase, state, val)` .

Die erste virtuelle geschützte Memberfunktion versucht, sequenzielle Elemente zuzuordnen. Sie beginnt zuerst in der Sequenz [ `first`, `last`), bis sie ein vollständiges, nicht leeres Eingabefeld für ganze Zahlen erkannt hat. Im Erfolgsfall konvertiert Sie dieses Feld in den entsprechenden Wert als Typ **`long`** und speichert das Ergebnis in *Val*. Sie gibt einen Iterator zurück, der das erste Element nach dem numerischen Eingabefeld festlegt. Andernfalls speichert die Funktion nichts im *Val* und legt den `ios_base::failbit` *Zustand fest*. Sie gibt einen Iterator zurück, der das erste Element nach jedem Präfix eines gültigen Eingabefelds für ganze Zahlen festlegt. In beiden Fällen legt die Funktion den *last* `ios_base::eofbit` *Status fest*, wenn der Rückgabewert "Last" ist.

Das ganzzahlige Eingabefeld wird von denselben Regeln konvertiert, die von den Scanfunktionen verwendet werden, um eine Reihe von **`char`** Elementen aus einer Datei zu vergleichen und zu konvertieren. **`char`** Es wird davon ausgegangen, dass jedes dieser Elemente einem entsprechenden Element vom Typ `CharType` durch eine einfache 1-zu-Eins-Zuordnung zugeordnet wird. Die entsprechende Überprüfungskonvertierungsspezifikation wird wie folgt bestimmt:

- Wenn `iosbase.` [Flags](../standard-library/ios-base-class.md#flags) `& ios_base::basefield == ios_base::` [Okt](../standard-library/ios-functions.md#oct), ist die Konvertierungsspezifikation `lo` .

- Wenn `iosbase.flags & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), ist die Konvertierungsspezifikation `lx`.

- Wenn `iosbase.flags & ios_base::basefield == 0`, ist die Konvertierungsspezifikation `li`.

- Andernfalls ist die Konvertierungsspezifikation `ld`.

Das Format eines ganzzahligen Eingabe Felds wird weiter von dem Gebiets Schema [Aspekt](../standard-library/locale-class.md#facet_class) bestimmt, der `fac` durch den Aufrufen [Use_facet](../standard-library/locale-functions.md#use_facet) `<` [`numpunct`](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [getloc](../standard-library/ios-base-class.md#getloc)zurückgegeben wurde `())` . Genauer gesagt:

- `fac.`die [Gruppierung](../standard-library/numpunct-class.md#grouping) bestimmt, wie Ziffern auf der linken Seite eines Dezimal Trennzeichens gruppiert werden.

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep) bestimmt die Sequenz, die Gruppen von Ziffern auf der linken Seite eines Dezimal Trennzeichens trennt.

Wenn keine Instanzen von `fac.thousands_sep` im numerischen Eingabefeld auftreten, wird keine Gruppierungseinschränkung auferlegt. Andernfalls werden alle Gruppierungs Einschränkungen, die von auferlegt werden, `fac.grouping` erzwungen, und Trennzeichen werden entfernt, bevor die Scan Konvertierung erfolgt.

Die zweite virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

verhält sich wie die erste, außer dass sie eine Konvertierungsspezifikation von `ld` durch `lu` ersetzt. Im Erfolgsfall konvertiert Sie das numerische Eingabefeld in einen Wert vom Typ **`unsigned long`** und speichert diesen Wert in *Val*.

Die dritte virtuelle geschützte Memberfunktion:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres Gleitkommaeingabefeld zu finden. `fac.`[DECIMAL_POINT](../standard-library/numpunct-class.md#decimal_point) bestimmt die Sequenz, die die ganzzahligen Ziffern von den Bruch Ziffern trennt. Der entsprechende Überprüfungsonvertierungsspezifizierer ist `lf`.

Die vierte virtuelle geschützte Member-Funktion:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

verhält sich wie das dritte, mit der Ausnahme, dass der entsprechende Scan Konvertierungsspezifizierer ist `Lf` .

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

verhält sich wie die erste, außer dass sie versucht, eine Übereinstimmung für ein vollständiges, nicht leeres boolesches Eingabefeld zu finden. Wenn erfolgreich, konvertiert Sie das boolesche Eingabefeld in einen Wert vom Typ **`bool`** und speichert diesen Wert in *Val*.

Ein boolesches Eingabefeld nimmt eine von zwei Formen an. Wenn `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) ist **`false`** , ist es das gleiche wie ein ganzzahliges Eingabefeld, mit dem Unterschied, dass der konvertierte Wert entweder 0 (für **`false`** ) oder 1 (für) sein muss **`true`** . Andernfalls muss die Sequenz entweder `fac.` [falsename](../standard-library/numpunct-class.md#falsename) (für **`false`** ) oder `fac.` [Truename](../standard-library/numpunct-class.md#truename) (für **`true`** ) entsprechen.

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

## <a name="num_getiter_type"></a><a name="iter_type"></a>Num_get:: iter_type

Ein Typ, der einen Eingabeiterator beschreibt.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `InputIterator` dar.

## <a name="num_getnum_get"></a><a name="num_get"></a>Num_get:: Num_get

Der Konstruktor für Objekte vom Typ `num_get`, die verwendet werden, um numerische Werte aus Sequenzen zu extrahieren.

```cpp
explicit num_get(size_t refs = 0);
```

### <a name="parameters"></a>Parameter

*Refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *Refs* -Parameter und ihre Bedeutung lauten:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \>1: diese Werte sind nicht definiert.

Direkte Beispiele sind nicht möglich, da der Destruktor geschützt ist.

Der Konstruktor initialisiert sein Basisobjekt mit `locale::` [Facette](../standard-library/locale-class.md#facet_class) `(refs)` .

## <a name="see-also"></a>Weitere Informationen

[\<locale>](../standard-library/locale.md)\
[facetklasse](../standard-library/locale-class.md#facet_class)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
