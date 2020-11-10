---
title: '`codecvt`-Klasse'
description: Beschreibt die Microsoft C-Lauf Zeit `codecvt` Klassen-API
ms.date: 11/09/2020
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
ms.openlocfilehash: 8d2970297cca199c70c101dca93f453c512317c4
ms.sourcegitcommit: b38485bb3a9d479e0c5d64ffc3d841fa2c2b366f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441280"
---
# <a name="codecvt-class"></a>`codecvt`-Klasse

Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema Aspekt fungieren kann. Sie kann Konvertierungen zwischen einer Sequenz von Werten steuern, die zum Codieren von Zeichen innerhalb des Programms verwendet werden, und einer Sequenz von Werten, die zum Codieren von Zeichen außerhalb des Programms verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parameter

*`CharType`*\
Der Typ, der innerhalb eines Programms verwendet wird, um Zeichen zu codieren.

*`Byte`*\
Ein Typ, mit dem Zeichen außerhalb eines Programms codiert werden.

*`StateType`*\
Ein Typ, der verwendet werden kann, um Zwischenzustände einer Konvertierung zwischen internen und externen Zeichendarstellungen darzustellen.

## <a name="remarks"></a>Bemerkungen

In der Klassen Vorlage wird ein Objekt beschrieben, das als Gebiets Schema [Aspekt](../standard-library/locale-class.md#facet_class)fungieren kann, um Konvertierungen zwischen einer Sequenz von Werten des Typs *`CharType`* und einer Sequenz von Werten des Typs zu steuern *`Byte`* . Die *`StateType`* -Klasse kennzeichnet die Transformation, und ein Objekt der-Klasse *`StateType`* speichert alle erforderlichen Zustandsinformationen während einer Konvertierung.

Die interne Codierung verwendet eine Darstellung mit einer bestimmten Anzahl von Bytes pro Zeichen, normalerweise entweder Typ **`char`** oder Typ **`wchar_t`** .

Wie bei jedem Gebietsschemafacet hat das statische Objekt `id` einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in `id` gespeichert.

Die Vorlagen Versionen von [`do_in`](#do_in) und [`do_out`](#do_out) geben immer zurück `codecvt_base::noconv` .

Die C++- Standardbibliothek definiert einige explizite Spezialisierungen:

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

konvertiert zwischen **`wchar_t`** -und- **`char`** Sequenzen.

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

konvertiert zwischen **`char16_t`** Sequenzen, die als UTF-16 codiert sind, und **`char`** als UTF-8 codierte Sequenzen.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

konvertiert zwischen **`char32_t`** Sequenzen, die als UTF-32 (UCS-4) codiert sind, und **`char`** als UTF-8 codierte Sequenzen.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[`codecvt`](#codecvt)|Der Konstruktor für Objekte der `codecvt`-Klasse, die als Gebietsschemafacet zur Behandlung von Konvertierungen dient.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[`extern_type`](#extern_type)|Ein Zeichentyp, der für externe Darstellungen verwendet wird.|
|[`intern_type`](#intern_type)|Ein Zeichentyp, der für interne Darstellungen verwendet wird.|
|[`state_type`](#state_type)|Ein Zeichentyp, der verwendet wird, um Zwischenzustände bei Konvertierungen zwischen externen und internen Darstellungen darzustellen.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[`always_noconv`](#always_noconv)|Testet, ob keine Konvertierungen ausgeführt werden müssen.|
|[`do_always_noconv`](#do_always_noconv)|Eine virtuelle Funktion, die aufgerufen wird, um zu testen, ob keine Konvertierungen ausgeführt werden müssen.|
|[`do_encoding`](#do_encoding)|Eine virtuelle Funktion, die testet, ob die Codierung des `Byte` Streams Zustands abhängig ist, ob das Verhältnis zwischen den `Byte` verwendeten Werten und den `CharType` erstellten Werten konstant ist, und wenn dies der Fall ist, wird der Wert dieses Verhältnisses bestimmt.|
|[`do_in`](#do_in)|Eine virtuelle Funktion, die aufgerufen wird, um eine Sequenz interner `Byte` Werte in eine Sequenz externer Werte zu konvertieren `CharType` .|
|[`do_length`](#do_length)|Eine virtuelle Funktion, die bestimmt, wie viele `Byte` Werte aus einer bestimmten Sequenz externer `Byte` Werte nicht mehr als eine angegebene Anzahl interner Werte ergeben, `CharType` und gibt diese Anzahl von `Byte` Werten zurück.|
|[`do_max_length`](#do_max_length)|Eine virtuelle Funktion, die die maximale Anzahl externer Bytes zurückgibt, die erforderlich sind, um ein internes `CharType`-Objekt zu erzeugen.|
|[`do_out`](#do_out)|Eine virtuelle Funktion, die aufgerufen wird, um eine Sequenz interner `CharType` Werte in eine Sequenz externer Bytes zu konvertieren.|
|[`do_unshift`](#do_unshift)|Eine virtuelle Funktion, die aufgerufen wird, um die Werte bereitzustellen, die `Byte` in einer Zustands abhängigen Konvertierung erforderlich sind, um das letzte Zeichen in einer Sequenz von- `Byte` Werten abzuschließen.|
|[`encoding`](#encoding)|Testet, ob die Codierung des `Byte` Streams Zustands abhängig ist, ob das Verhältnis zwischen den `Byte` verwendeten Werten und den `CharType` erstellten Werten konstant ist, und bestimmt, wenn dies der Fall ist, den Wert dieses Verhältnisses.|
|[`in`](#in)|Konvertiert eine externe Darstellung einer Sequenz von- `Byte` Werten in eine interne Darstellung einer Sequenz von- `CharType` Werten.|
|[`length`](#length)|Bestimmt, wie viele `Byte` Werte aus einer bestimmten Sequenz externer `Byte` Werte nicht mehr als eine angegebene Anzahl interner Werte ergeben `CharType` , und gibt diese Anzahl von `Byte` Werten zurück.|
|[`max_length`](#max_length)|Gibt die maximale Anzahl externer `Byte` Werte zurück, die erforderlich sind, um einen internen zu erzielen `CharType` .|
|[`out`](#out)|Konvertiert eine Sequenz interner `CharType` Werte in eine Sequenz externer `Byte` Werte.|
|[`unshift`](#unshift)|Stellt die externen `Byte` Werte bereit, die in einer Zustands abhängigen Konvertierung erforderlich sind, um das letzte Zeichen in der Sequenz von- `Byte` Werten abzuschließen.|

## <a name="requirements"></a>Anforderungen

**Header:**`<locale>`

**Namespace:** `std`

## <a name="codecvtalways_noconv"></a><a name="always_noconv"></a> `codecvt::always_noconv`

Testet, ob keine Konvertierungen ausgeführt werden müssen.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert, der ist, **`true`** Wenn keine Konvertierungen ausgeführt werden müssen;, **`false`** Wenn mindestens ein Vorgang durchgeführt werden muss.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt zurück [`do_always_noconv`](#do_always_noconv) .

### <a name="example"></a>Beispiel

```cpp
// codecvt_always_noconv.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = use_facet<codecvt<char, char, mbstate_t>>
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << '\n';
   else
      cout << "At least one conversion is required." << '\n';

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t>>
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << '\n';
   else
      cout << "At least one conversion is required." << '\n';
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvtcodecvt"></a><a name="codecvt"></a> `codecvt::codecvt`

Der Konstruktor für Objekte der Klasse „codecvt“, die als Gebietsschemafacet zur Handhabung von Konvertierungen dient.

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>Parameter

*`refs`*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *`refs`* Parameter und ihre Bedeutung lauten:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.


- 2: diese Werte sind nicht definiert.

Der Konstruktor initialisiert sein `locale::facet` Basisobjekt mit [`locale::facet`](../standard-library/locale-class.md#facet_class) `(refs)` .

## <a name="codecvtdo_always_noconv"></a><a name="do_always_noconv"></a> `codecvt::do_always_noconv`

Eine virtuelle Funktion, die aufgerufen wird, um zu testen, ob keine Konvertierungen ausgeführt werden müssen.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die geschützte virtuelle Member-Funktion gibt **`true`** nur dann zurück, wenn jeder Rückruf von [`do_in`](#do_in) oder [`do_out`](#do_out) zurückgibt `noconv` .

Die Vorlagen Version gibt immer zurück **`true`** .

### <a name="example"></a>Beispiel

Siehe das Beispiel für [`always_noconv`](#always_noconv) , das aufruft `do_always_noconv` .

## <a name="codecvtdo_encoding"></a><a name="do_encoding"></a> `codecvt::do_encoding`

Eine virtuelle Funktion, die testet, ob die Codierung des `Byte` Streams Zustands abhängig ist, ob das Verhältnis zwischen den `Byte` verwendeten Werten und den `CharType` erstellten Werten konstant ist und, wenn dies der Fall ist, den Wert dieses Verhältnisses bestimmt.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die geschützte virtuelle Memberfunktion gibt Folgendes zurück:

- -1, wenn die Codierung von Sequenzen vom Typ `extern_type` Zustands abhängig ist.

- 0, wenn die Codierung Sequenzen von variabler Länge umfasst.

- *`N`* , wenn die Codierung nur Sequenzen der Länge einschließt. *`N`*

### <a name="example"></a>Beispiel

Siehe das Beispiel für [encoding](#encoding), mit dem `do_encoding` aufgerufen wird.

## <a name="codecvtdo_in"></a><a name="do_in"></a> Codecvt::d o_in

Eine virtuelle Funktion, die aufgerufen wird, um eine Sequenz externer `Byte` Werte in eine Sequenz interner Werte zu konvertieren `CharType` .

```cpp
virtual result do_in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parameter

*`state`*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*`first1`*\
Zeiger auf den Anfang der zu konvertierenden Sequenz.

*`last1`*\
Zeiger auf das Ende der zu konvertierenden Sequenz.

*`next1`*\
Zeiger hinter das Ende der konvertierten Sequenz auf das erste nicht konvertierte Zeichen.

*`first2`*\
Zeiger auf den Anfang der konvertierten Sequenz.

*`last2`*\
Zeiger auf das Ende der konvertierten Sequenz.

*`next2`*\
Zeiger auf den, der `CharType` nach dem letzten konvertierten `CharType` steht, bis zum ersten nicht geänderten Zeichen in der Zielsequenz.

### <a name="return-value"></a>Rückgabewert

Ein Rückgabewert, der den Erfolg, den teilweisen Erfolg oder das Fehlschlagen des Vorgangs angibt. Die Funktion gibt Folgendes zurück:

- `codecvt_base::error` , wenn die Quell Sequenz nicht ordnungsgemäß formatiert ist.

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt.

- `codecvt_base::ok` , wenn die Konvertierung erfolgreich ist.

- `codecvt_base::partial` , wenn die Quelle unzureichend ist oder wenn das Ziel nicht groß genug ist, damit die Konvertierung erfolgreich ausgeführt werden kann.

### <a name="remarks"></a>Bemerkungen

*`state`* muss den ursprünglichen Konvertierungs Zustand am Anfang einer neuen Quell Sequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. Andernfalls ist der gespeicherte Wert unspezifiziert.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [`in`](#in) , das aufruft `do_in` .

## <a name="codecvtdo_length"></a><a name="do_length"></a> `codecvt::do_length`

Eine virtuelle Funktion, die bestimmt, wie viele `Byte` Werte aus einer bestimmten Sequenz externer `Byte` Werte nicht mehr als eine angegebene Anzahl interner Werte ergeben, `CharType` und gibt diese Anzahl von `Byte` Werten zurück.

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parameter

*`state`*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*`first1`*\
Zeiger auf den Anfang der externen Sequenz.

*`last1`*\
Zeiger auf das Ende der externen Sequenz.

*`len2`*\
Die maximale Anzahl von `Byte` Werten, die von der Member-Funktion zurückgegeben werden können.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die die maximale Anzahl von Konvertierungen darstellt, nicht größer als *len2* , die durch die externe Quell Sequenz bei [ `first1` , `last1` ) definiert wird.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Member-Funktion ruft effektiv den `do_in( state, first1, last1, next1, buf, buf + len2, next2)` *Status* (eine Kopie des Zustands), einen Puffer und `buf` Zeiger `next1` und auf `next2` .

Dann gibt es `next2` - `buf` zurück. Sie zählt die maximale Anzahl von Konvertierungen, nicht größer als *len2* , die durch die Quell Sequenz bei [ `first1` ,) definiert wird `last1` .

Die Vorlagen Version gibt immer den kleineren von *`last1`*  -  *`first1`* und zurück *`len2`* .

### <a name="example"></a>Beispiel

Siehe das Beispiel für [`length`](#length) , das aufruft `do_length` .

## <a name="codecvtdo_max_length"></a><a name="do_max_length"></a> `codecvt::do_max_length`

Eine virtuelle Funktion, die die maximale Anzahl externer Werte zurückgibt, die `Byte` erforderlich sind, um einen internen zu erzielen `CharType` .

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von `Byte` Werten, die für eine Erstellung erforderlich sind `CharType` .

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Member-Funktion gibt den größten zulässigen Wert zurück, der von [`do_length`](#do_length) `( first1, last1, 1)` für beliebige gültige Werte von und zurückgegeben werden kann *`first1`* *`last1`* .

### <a name="example"></a>Beispiel

Siehe das Beispiel für [`max_length`](#max_length) , das aufruft `do_max_length` .

## <a name="codecvtdo_out"></a><a name="do_out"></a> `codecvt::do_out`

Eine virtuelle Funktion, die aufgerufen wird, um eine Sequenz interner `CharType` Werte in eine Sequenz externer Werte zu konvertieren `Byte` .

```cpp
virtual result do_out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parameter

*`state`*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*`first1`*\
Zeiger auf den Anfang der zu konvertierenden Sequenz.

*`last1`*\
Zeiger auf das Ende der zu konvertierenden Sequenz.

*`next1`*\
Verweis auf einen Zeiger auf den ersten nicht konvertierten `CharType` , nach dem letzten `CharType` konvertierten.

*`first2`*\
Zeiger auf den Anfang der konvertierten Sequenz.

*`last2`*\
Zeiger auf das Ende der konvertierten Sequenz.

*`next2`*\
Verweis auf einen Zeiger auf den ersten nicht konvertierten `Byte` , nach dem letzten `Byte` konvertierten.

### <a name="return-value"></a>Rückgabewert

Die Funktion gibt Folgendes zurück:

- `codecvt_base::error` , wenn die Quell Sequenz nicht ordnungsgemäß formatiert ist.

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt.

- `codecvt_base::ok` , wenn die Konvertierung erfolgreich ist.

- `codecvt_base::partial` , wenn die Quelle unzureichend ist, oder, wenn das Ziel nicht groß genug ist, damit die Konvertierung erfolgreich ausgeführt werden kann.

### <a name="remarks"></a>Bemerkungen

*`state`* muss den ursprünglichen Konvertierungs Zustand am Anfang einer neuen Quell Sequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. Andernfalls ist der gespeicherte Wert unspezifiziert.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [out](#out), mit dem `do_out` aufgerufen wird.

## <a name="codecvtdo_unshift"></a><a name="do_unshift"></a> `codecvt::do_unshift`

Eine virtuelle Funktion, die aufgerufen wird, um die Werte bereitzustellen, die `Byte` in einer Zustands abhängigen Konvertierung erforderlich sind, um das letzte Zeichen in einer Sequenz von- `Byte` Werten abzuschließen.

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parameter

*`state`*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*`first2`*\
Zeiger auf die erste Position im Zielbereich.

*`last2`*\
Zeiger auf die letzte Position im Zielbereich.

*`next2`*\
Zeiger auf das erste unveränderte Element in der Zielsequenz.

### <a name="return-value"></a>Rückgabewert

Die Funktion gibt Folgendes zurück:

- `codecvt_base::error` Wenn der *Zustand* einen ungültigen Zustand darstellt

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt

- `codecvt_base::ok` Wenn die Konvertierung erfolgreich ist

- `codecvt_base::partial` Wenn das Ziel nicht groß genug ist, um die Konvertierung erfolgreich durchführen zu können

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Member-Funktion versucht, das Quell Element `CharType` (0) in eine Zielsequenz zu konvertieren, die in [ `first2` , `last2` ) gespeichert wird, mit Ausnahme des abschließenden Elements `Byte` (0). Er speichert immer in *`next2`* einem Zeiger auf das erste unveränderte Element in der Zielsequenz.

*`State`* muss den ursprünglichen Konvertierungs Zustand am Anfang einer neuen Quell Sequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. In der Regel bleibt beim Konvertieren des Quell Elements `CharType` (0) der aktuelle Zustand im ursprünglichen Konvertierungs Zustand.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [`unshift`](#unshift) , das aufruft `do_unshift` .

## <a name="codecvtencoding"></a><a name="encoding"></a> `codecvt::encoding`

Testet, ob die Codierung des `Byte` Streams Zustands abhängig ist, ob das Verhältnis zwischen den `Byte` verwendeten Werten und den `CharType` erstellten Werten konstant ist, und bestimmt, wenn dies der Fall ist, den Wert dieses Verhältnisses.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Rückgabewert

Wenn der Rückgabewert positiv ist, entspricht dieser Wert der Konstanten Anzahl von `Byte` Zeichen, die für die Erstellung des Zeichens erforderlich sind `CharType` .

Die geschützte virtuelle Memberfunktion gibt Folgendes zurück:

- -1, wenn die Codierung von Sequenzen vom Typ `extern_type` Zustands abhängig ist.

- 0, wenn die Codierung Sequenzen von variabler Länge umfasst.

- *`N`* , wenn die Codierung nur Sequenzen der Länge einschließt *`N`* .

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_encoding](#do_encoding) zurück.

### <a name="example"></a>Beispiel

```cpp
// codecvt_encoding.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   int result1 = use_facet<codecvt<char, char, mbstate_t>> ( loc ).encoding ( );
   cout << result1 << '\n';
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t>> ( loc ).encoding( );
   cout << result1 << '\n';
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t>> ( loc ).encoding( );
   cout << result1 << '\n';
}
```

```Output
1
1
1
```

## <a name="codecvtextern_type"></a><a name="extern_type"></a> `codecvt::extern_type`

Ein Zeichentyp, der für externe Darstellungen verwendet wird.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Byte` dar.

## <a name="codecvtin"></a><a name="in"></a> Codecvt:: in

Konvertiert eine externe Darstellung einer Sequenz von- `Byte` Werten in eine interne Darstellung einer Sequenz von- `CharType` Werten.

```cpp
result in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parameter

*`state`*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*`first1`*\
Zeiger auf den Anfang der zu konvertierenden Sequenz.

*`last1`*\
Zeiger auf das Ende der zu konvertierenden Sequenz.

*`next1`*\
Zeiger hinter das Ende der konvertierten Sequenz auf das erste nicht konvertierte Zeichen.

*`first2`*\
Zeiger auf den Anfang der konvertierten Sequenz.

*`last2`*\
Zeiger auf das Ende der konvertierten Sequenz.

*`next2`*\
Ein Zeiger auf den `CharType` , der nach dem letzten konvertierten `Chartype` in das erste nicht geänderte Zeichen in der Zielsequenz erfolgt.

### <a name="return-value"></a>Rückgabewert

Ein Rückgabewert, der den Erfolg, den teilweisen Erfolg oder das Fehlschlagen des Vorgangs angibt. Die Funktion gibt Folgendes zurück:

- `codecvt_base::error` , wenn die Quell Sequenz nicht ordnungsgemäß formatiert ist.

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt.

- `codecvt_base::ok` , wenn die Konvertierung erfolgreich ist.

- `codecvt_base::partial` , wenn die Quelle unzureichend ist, oder, wenn das Ziel nicht groß genug ist, damit die Konvertierung erfolgreich ausgeführt werden kann.

### <a name="remarks"></a>Bemerkungen

*`state`* muss den ursprünglichen Konvertierungs Zustand am Anfang einer neuen Quell Sequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. Nach einer partiellen Konvertierung *`state`* muss so festgelegt werden, dass die Konvertierung beim Eintreffen neuer Zeichen fortgesetzt werden kann.

Die Member-Funktion gibt zurück [`do_in`](#do_in) `( state, first1,  last1,  next1, first2, last2,  next2)` .

### <a name="example"></a>Beispiel

```cpp
// codecvt_in.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   const char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0}; // zero-initialization represents the initial conversion state for mbstate_t
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t>>
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( res!=codecvt_base::error ?  L"It worked! " : L"It didn't work! " )
       << L"The converted string is:\n ["
       << &pwszInt[0]
       << L"]" << '\n';
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="codecvtintern_type"></a><a name="intern_type"></a> `codecvt::intern_type`

Ein Zeichentyp, der für interne Darstellungen verwendet wird.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `CharType` dar.

## <a name="codecvtlength"></a><a name="length"></a> Codecvt:: length

Bestimmt, wie viele `Byte` Werte aus einer bestimmten Sequenz externer `Byte` Werte nicht mehr als eine angegebene Anzahl interner Werte ergeben `CharType` , und gibt diese Anzahl von `Byte` Werten zurück.

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parameter

*`state`*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*`first1`*\
Zeiger auf den Anfang der externen Sequenz.

*`last1`*\
Zeiger auf das Ende der externen Sequenz.

*`len2`*\
Die maximale Anzahl von Bytes, die von der Memberfunktion zurückgegeben werden kann.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die die Anzahl der maximal zulässigen Konvertierungen darstellt, nicht größer als *`len2`* , definiert durch die externe Quell Sequenz bei [ `first1` , `last1` ).

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt zurück [`do_length`](#do_length) `( state, first1, last1, len2)` .

### <a name="example"></a>Beispiel

```cpp
// codecvt_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   const char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0}; // zero-initialization represents the initial conversion state for mbstate_t
   locale loc("C"); // English_Britain"); //German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t>>
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << '\n';
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="codecvtmax_length"></a><a name="max_length"></a> `codecvt::max_length`

Gibt die maximale Anzahl externer `Byte` Werte zurück, die erforderlich sind, um einen internen zu erzielen `CharType` .

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von `Byte` Werten, die für eine Erstellung erforderlich sind `CharType` .

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt zurück [`do_max_length`](#do_max_length) .

### <a name="example"></a>Beispiel

```cpp
// codecvt_max_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc( "C");//English_Britain" );//German_Germany
   int res = use_facet<codecvt<char, char, mbstate_t>>
     ( loc ).max_length( );
   wcout << res << '\n';
}
```

```Output
1
```

## <a name="codecvtout"></a><a name="out"></a> `codecvt::out`

Konvertiert eine Sequenz interner `CharType` Werte in eine Sequenz externer `Byte` Werte.

```cpp
result out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parameter

*`state`*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*`first1`*\
Zeiger auf den Anfang der zu konvertierenden Sequenz.

*`last1`*\
Zeiger auf das Ende der zu konvertierenden Sequenz.

*`next1`*\
Verweis auf einen Zeiger auf den ersten, der `CharType` nach dem letzten `CharType` konvertierten nicht konvertiert wurde.

*`first2`*\
Zeiger auf den Anfang der konvertierten Sequenz.

*`last2`*\
Zeiger auf das Ende der konvertierten Sequenz.

*`next2`*\
Verweis auf einen Zeiger auf den ersten, der `Byte` nach dem letzten konvertierten nicht konvertiert wurde `Byte` .

### <a name="return-value"></a>Rückgabewert

Die Member-Funktion gibt zurück [`do_out`](#do_out) `( state, first1, last1, next1, first2, last2, next2)` .

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [`codecvt::do_out`](#do_out).

### <a name="example"></a>Beispiel

```cpp
// codecvt_out.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
#include <wchar.h>
using namespace std;
#define LEN 90
int main( )
{
    char pszExt[LEN + 1];
    const wchar_t* pwszInt = L"This is the wchar_t string to be converted.";
    memset(&pszExt[0], 0, (sizeof(char)) * (LEN + 1));
    char* pszNext;
    const wchar_t* pwszNext;
    mbstate_t state;
    locale loc("C");//English_Britain");//German_Germany
    int res = use_facet<codecvt<wchar_t, char, mbstate_t>>
        (loc).out(state,
            pwszInt, &pwszInt[wcslen(pwszInt)], pwszNext,
            pszExt, &pszExt[wcslen(pwszInt)], pszNext);
    pszExt[wcslen(pwszInt)] = 0;
    cout << (res != codecvt_base::error ? "It worked: " : "It didn't work: ")
        << "The converted string is:\n ["
        << &pszExt[0]
        << "]" << '\n';

}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="codecvtstate_type"></a><a name="state_type"></a> `codecvt::state_type`

Ein Zeichentyp, der verwendet wird, um Zwischenzustände bei Konvertierungen zwischen externen und internen Darstellungen darzustellen.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `StateType` dar.

## <a name="codecvtunshift"></a><a name="unshift"></a> Codecvt:: unshift

Stellt die `Byte` Werte bereit, die in einer Zustands abhängigen Konvertierung erforderlich sind, um das letzte Zeichen in einer Sequenz von- `Byte` Werten abzuschließen.

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parameter

*`state`*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*`first2`*\
Zeiger auf die erste Position im Zielbereich.

*`last2`*\
Zeiger auf die letzte Position im Zielbereich.

*`next2`*\
Zeiger auf das erste unveränderte Element in der Zielsequenz.

### <a name="return-value"></a>Rückgabewert

Die Funktion gibt Folgendes zurück:

- `codecvt_base::error` , wenn der Zustand einen ungültigen Status darstellt.

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt.

- `codecvt_base::ok` , wenn die Konvertierung erfolgreich ist.

- `codecvt_base::partial` Wenn das Ziel nicht groß genug ist, um die Konvertierung erfolgreich durchführen zu können.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Member-Funktion versucht, das Quell Element `CharType` (0) in eine Zielsequenz zu konvertieren, die in [ `first2` , `last2` ) gespeichert wird, mit Ausnahme des abschließenden Elements `Byte` (0). Er speichert immer in *`next2`* einem Zeiger auf das erste unveränderte Element in der Zielsequenz.

*`state`* muss den ursprünglichen Konvertierungs Zustand am Anfang einer neuen Quell Sequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. In der Regel bleibt beim Konvertieren des Quell Elements `CharType` (0) der aktuelle Zustand im ursprünglichen Konvertierungs Zustand.

Die Member-Funktion gibt zurück [`do_unshift`](#do_unshift) `( state, first2, last2, next2 )` .

## <a name="see-also"></a>Siehe auch

[`<locale>`](../standard-library/locale.md)\
[Codepages](../c-runtime-library/code-pages.md)\
[Gebiets Schema Namen, Sprachen und Länder-/regionszeichenfolgen](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
