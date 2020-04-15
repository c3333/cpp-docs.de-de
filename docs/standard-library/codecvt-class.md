---
title: codecvt-Klasse
ms.date: 11/04/2016
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
ms.openlocfilehash: 3dba971b112c23325e0529e53746cbee827df5e9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371952"
---
# <a name="codecvt-class"></a>codecvt-Klasse

Eine Klassenvorlage, die ein Objekt beschreibt, das als Gebietsschema-Facette dienen kann. Sie ist in der Lage, Konvertierungen zwischen einer Sequenz von Werten zu steuern, mit denen Zeichen innerhalb des Programms codiert werden, und einer Sequenz von Werten, mit denen Zeichen außerhalb des Programms codiert werden.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parameter

*Chartype*\
Der Typ, der innerhalb eines Programms verwendet wird, um Zeichen zu codieren.

*Byte*\
Ein Typ, mit dem Zeichen außerhalb eines Programms codiert werden.

*StateType*\
Ein Typ, der verwendet werden kann, um Zwischenzustände einer Konvertierung zwischen internen und externen Zeichendarstellungen darzustellen.

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage beschreibt ein Objekt, das als [Gebietsschema](../standard-library/locale-class.md#facet_class)dienen kann, um Konvertierungen zwischen einer Sequenz von Werten vom Typ *CharType* und einer Sequenz von Werten vom Typ *Byte*zu steuern. Die Klasse *StateType* charakterisiert die Transformation - und ein Objekt der Klasse *StateType* speichert alle erforderlichen Statusinformationen während einer Konvertierung.

Die interne Codierung verwendet eine Darstellung mit einer festen Anzahl von Bytes pro Zeichen, in der Regel entweder Typ **char** oder Typ **wchar_t**.

Wie bei jedem Gebietsschemafacet hat das statische Objekt `id` einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in `id` gespeichert.

Die Vorlagenversionen [do_in](#do_in) und [do_out](#do_out) geben immer `codecvt_base::noconv` zurück.

Die C++- Standardbibliothek definiert einige explizite Spezialisierungen:

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

konvertiert zwischen **wchar_t-** und **Zeichensequenzen.**

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

konvertiert zwischen `char16_t` Sequenzen, die als UTF-16 codiert sind, und **Zeichensequenzen,** die als UTF-8 codiert sind.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

konvertiert zwischen `char32_t` Sequenzen, die als UTF-32 (UCS-4) codiert sind, und **Zeichensequenzen,** die als UTF-8 codiert sind.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[Codecvt](#codecvt)|Der Konstruktor für Objekte der `codecvt`-Klasse, die als Gebietsschemafacet zur Behandlung von Konvertierungen dient.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[extern_type](#extern_type)|Ein Zeichentyp, der für externe Darstellungen verwendet wird.|
|[intern_type](#intern_type)|Ein Zeichentyp, der für interne Darstellungen verwendet wird.|
|[state_type](#state_type)|Ein Zeichentyp, der verwendet wird, um Zwischenzustände bei Konvertierungen zwischen externen und internen Darstellungen darzustellen.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[always_noconv](#always_noconv)|Testet, ob keine Konvertierungen ausgeführt werden müssen.|
|[do_always_noconv](#do_always_noconv)|Eine virtuelle Funktion, die aufgerufen wird, um zu testen, ob keine Konvertierungen ausgeführt werden müssen.|
|[do_encoding](#do_encoding)|Eine virtuelle Funktion, die testet, `Byte` ob die Codierung des Streams `Byte` zustandsabhängig `CharType` ist, ob das Verhältnis zwischen den verwendeten und den erzeugten Werten konstant ist, und, wenn ja, den Wert dieses Verhältnisses bestimmt.|
|[do_in](#do_in)|Eine virtuelle Funktion, die aufgerufen `Byte` wird, um `CharType` eine Sequenz interner Werte in eine Sequenz externer Werte zu konvertieren.|
|[do_length](#do_length)|Eine virtuelle Funktion, `Byte` die bestimmt, wie `Byte` viele Werte aus einer bestimmten `CharType` Sequenz externer Werte `Byte` nicht mehr als eine bestimmte Anzahl interner Werte erzeugen, und gibt diese Anzahl von Werten zurück.|
|[do_max_length](#do_max_length)|Eine virtuelle Funktion, die die maximale Anzahl externer Bytes zurückgibt, die erforderlich sind, um ein internes `CharType`-Objekt zu erzeugen.|
|[do_out](#do_out)|Eine virtuelle Funktion, die aufgerufen `CharType` wird, um eine Sequenz interner Werte in eine Sequenz externer Bytes zu konvertieren.|
|[do_unshift](#do_unshift)|Eine virtuelle Funktion, `Byte` die aufgerufen wird, um die Werte bereitzustellen, die `Byte` in einer zustandsabhängigen Konvertierung erforderlich sind, um das letzte Zeichen in einer Sequenz von Werten abzuschließen.|
|[Codierung](#encoding)|Testet, ob die `Byte` Codierung des Streams zustandsabhängig `Byte` ist, ob `CharType` das Verhältnis zwischen den verwendeten und den erzeugten Werten konstant ist, und bestimmt, falls ja, den Wert dieses Verhältnisses.|
|[in](#in)|Konvertiert eine externe Darstellung einer `Byte` Sequenz von Werten in `CharType` eine interne Darstellung einer Sequenz von Werten.|
|[length](#length)|Bestimmt, `Byte` wie viele Werte aus `Byte` einer bestimmten Sequenz externer `CharType` Werte nicht mehr `Byte` als eine bestimmte Anzahl interner Werte erzeugen, und gibt diese Anzahl von Werten zurück.|
|[Max_length](#max_length)|Gibt die maximale `Byte` Anzahl externer Werte `CharType`zurück, die zum Erstellen eines internen Wertes erforderlich sind.|
|[out](#out)|Konvertiert eine Sequenz `CharType` interner Werte in `Byte` eine Sequenz externer Werte.|
|[unshift](#unshift)|Stellt die `Byte` externen Werte bereit, die in einer zustandsabhängigen Konvertierung erforderlich sind, um das letzte Zeichen in der Sequenz von `Byte` Werten abzuschließen.|

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="codecvtalways_noconv"></a><a name="always_noconv"></a>codecvt::always_noconv

Testet, ob keine Konvertierungen durchgeführt werden müssen.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert, **der wahr** ist, wenn keine Konvertierungen durchgeführt werden müssen. **falsch,** wenn mindestens einer getan werden muss.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_always_noconv](#do_always_noconv) zurück.

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
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvtcodecvt"></a><a name="codecvt"></a>codecvt::codecvt

Der Konstruktor für Objekte der Klasse „codecvt“, die als Gebietsschemafacet zur Handhabung von Konvertierungen dient.

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>Parameter

*Refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *refs-Parameter* und ihre Signifikanz sind:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- 2: Diese Werte sind nicht definiert.

Der Konstruktor initialisiert `locale::facet` sein Basisobjekt mit [locale::facet](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="codecvtdo_always_noconv"></a><a name="do_always_noconv"></a>codecvt::do_always_noconv

Eine virtuelle Funktion, die aufgerufen wird, um zu testen, ob keine Konvertierungen durchgeführt werden müssen.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die geschützte virtuelle Memberfunktion gibt **true** nur zurück, wenn jeder Aufruf [von do_in](#do_in) oder [do_out](#do_out) zurückgegeben wird. `noconv`

Die Vorlagenversion gibt immer **TRUE** zurück.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [always_noconv](#always_noconv), das `do_always_noconv` aufruft.

## <a name="codecvtdo_encoding"></a><a name="do_encoding"></a>codecvt::do_encoding

Eine virtuelle Funktion, die testet, `Byte` ob die Codierung des Streams `Byte` zustandsabhängig `CharType` ist, ob das Verhältnis zwischen den verwendeten und den erzeugten Werten konstant ist und, falls ja, den Wert dieses Verhältnisses bestimmt.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die geschützte virtuelle Memberfunktion gibt Folgendes zurück:

- -1, wenn die Codierung von `extern_type` Sequenzen des Typs statusabhängig ist.

- 0, wenn die Codierung Sequenzen von variabler Länge umfasst.

- *N*, wenn die Codierung nur Sequenzen der Länge *N* umfasst

### <a name="example"></a>Beispiel

Siehe das Beispiel für [encoding](#encoding), mit dem `do_encoding` aufgerufen wird.

## <a name="codecvtdo_in"></a><a name="do_in"></a>codecvt::do_in

Eine virtuelle Funktion, die aufgerufen `Byte` wird, um `CharType` eine Sequenz externer Werte in eine Sequenz interner Werte zu konvertieren.

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

*Staat*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*first1*\
Zeiger auf den Anfang der zu konvertierenden Sequenz.

*zuletzt1*\
Zeiger auf das Ende der zu konvertierenden Sequenz.

*weiter1*\
Zeiger hinter das Ende der konvertierten Sequenz auf das erste nicht konvertierte Zeichen.

*first2*\
Zeiger auf den Anfang der konvertierten Sequenz.

*zuletzt2*\
Zeiger auf das Ende der konvertierten Sequenz.

*next2*\
Zeigen Sie `CharType` auf das, das `CharType`nach dem zuletzt konvertierten kommt, auf das erste unveränderte Zeichen in der Zielsequenz.

### <a name="return-value"></a>Rückgabewert

Ein Rückgabewert, der den Erfolg, den teilweisen Erfolg oder das Fehlschlagen des Vorgangs angibt. Die Funktion gibt Folgendes zurück:

- `codecvt_base::error`wenn die Quellsequenz falsch ausgebildet ist.

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt.

- `codecvt_base::ok`wenn die Konvertierung erfolgreich ist.

- `codecvt_base::partial`wenn die Quelle nicht ausreicht oder das Ziel nicht groß genug ist, damit die Konvertierung erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

*muss* der anfängliche Konvertierungsstatus am Anfang einer neuen Quellsequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. Andernfalls ist der gespeicherte Wert unspezifiziert.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [in](#in), mit dem `do_in` aufgerufen wird.

## <a name="codecvtdo_length"></a><a name="do_length"></a>codecvt::do_length

Eine virtuelle Funktion, `Byte` die bestimmt, wie `Byte` viele Werte aus einer bestimmten `CharType` Sequenz externer Werte `Byte` nicht mehr als eine bestimmte Anzahl interner Werte erzeugen, und gibt diese Anzahl von Werten zurück.

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parameter

*Staat*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*first1*\
Zeiger auf den Anfang der externen Sequenz.

*zuletzt1*\
Zeiger auf das Ende der externen Sequenz.

*len2*\
Die maximale `Byte` Anzahl von Werten, die von der Memberfunktion zurückgegeben werden können.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die eine Anzahl der maximalen Anzahl von Konvertierungen darstellt, nicht größer `first1` `last1`als *len2*, definiert durch die externe Quellsequenz unter [ , ).

### <a name="remarks"></a>Bemerkungen

Die geschützte funktion "Virtuelles Member" ruft `do_in( state, first1, last1, next1, buf, buf + len2, next2)` effektiv `buf` *status* (eine `next1` Kopie `next2`des Status), einige Puffer und Zeiger und auf.

Dann gibt es `next2` - `buf` zurück. Somit zählt es die maximale Anzahl von Konvertierungen, nicht größer als `first1` *len2*, definiert durch die Quellsequenz bei [ , `last1`).

Die Vorlagenversion gibt immer den Kleineren von *last1* - *first1* und *len2*zurück.

### <a name="example"></a>Beispiel

Siehe Beispiel für [Länge](#length) `do_length`, die aufruft .

## <a name="codecvtdo_max_length"></a><a name="do_max_length"></a>codecvt::do_max_length

Eine virtuelle Funktion, die die `Byte` maximale Anzahl externer Werte zurückgibt, die zum Erstellen eines internen `CharType`Wertes erforderlich sind.

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die maximale `Byte` Anzahl von Werten, die zum Erstellen eines `CharType`Wertes erforderlich sind.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Memberfunktion gibt den größten zulässigen Wert zurück, der von [do_length](#do_length) `( first1, last1, 1)` für beliebige gültige Werte von *first1* und *last1*zurückgegeben werden kann.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [max_length](#max_length), das `do_max_length` aufruft.

## <a name="codecvtdo_out"></a><a name="do_out"></a>codecvt::do_out

Eine virtuelle Funktion, die aufgerufen `CharType` wird, um `Byte` eine Sequenz interner Werte in eine Sequenz externer Werte zu konvertieren.

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

*Staat*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*first1*\
Zeiger auf den Anfang der zu konvertierenden Sequenz.

*zuletzt1*\
Zeiger auf das Ende der zu konvertierenden Sequenz.

*weiter1*\
Verweis auf einen Zeiger auf `CharType`den ersten `CharType` nicht konvertierten , nach der letzten konvertierten.

*first2*\
Zeiger auf den Anfang der konvertierten Sequenz.

*zuletzt2*\
Zeiger auf das Ende der konvertierten Sequenz.

*next2*\
Verweis auf einen Zeiger auf `Byte`den ersten `Byte` nicht konvertierten , nach der letzten konvertierten.

### <a name="return-value"></a>Rückgabewert

Die Funktion gibt Folgendes zurück:

- `codecvt_base::error`wenn die Quellsequenz falsch ausgebildet ist.

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt.

- `codecvt_base::ok`wenn die Konvertierung erfolgreich ist.

- `codecvt_base::partial`wenn die Quelle nicht ausreicht oder das Ziel nicht groß genug ist, damit die Konvertierung erfolgreich ausgeführt werden kann.

### <a name="remarks"></a>Bemerkungen

*muss* der anfängliche Konvertierungsstatus am Anfang einer neuen Quellsequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. Andernfalls ist der gespeicherte Wert unspezifiziert.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [out](#out), mit dem `do_out` aufgerufen wird.

## <a name="codecvtdo_unshift"></a><a name="do_unshift"></a>codecvt::do_unshift

Eine virtuelle Funktion, `Byte` die aufgerufen wird, um die Werte bereitzustellen, die `Byte` in einer zustandsabhängigen Konvertierung erforderlich sind, um das letzte Zeichen in einer Sequenz von Werten abzuschließen.

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parameter

*Staat*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*first2*\
Zeiger auf die erste Position im Zielbereich.

*zuletzt2*\
Zeiger auf die letzte Position im Zielbereich.

*next2*\
Zeiger auf das erste unveränderte Element in der Zielsequenz.

### <a name="return-value"></a>Rückgabewert

Die Funktion gibt Folgendes zurück:

- `codecvt_base::error`Wenn *der Status* einen ungültigen Zustand darstellt

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt

- `codecvt_base::ok`Wenn die Konvertierung erfolgreich ist

- `codecvt_base::partial`Wenn das Ziel nicht groß genug ist, damit die Konvertierung erfolgreich ist

### <a name="remarks"></a>Bemerkungen

Die funktion "Geschütztes virtuelles `CharType`Member" versucht, das Quellelement (0) in eine Zielsequenz zu konvertieren, die in [ `first2`, `last2`gespeichert wird, mit Ausnahme des beendenden Elements `Byte`(0). In *next2* wird immer ein Zeiger auf das erste unveränderte Element in der Zielsequenz gespeichert.

_ *State* muss den ursprünglichen Konvertierungszustand am Anfang einer neuen Quellsequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. In der Regel belässt das Konvertieren des Quellelements `CharType`(0) den aktuellen Status im ursprünglichen Konvertierungsstatus.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [unshift](#unshift), mit dem `do_unshift` aufgerufen wird.

## <a name="codecvtencoding"></a><a name="encoding"></a>codecvt::Codierung

Testet, ob die `Byte` Codierung des Streams zustandsabhängig `Byte` ist, ob `CharType` das Verhältnis zwischen den verwendeten und den erzeugten Werten konstant ist, und bestimmt, falls ja, den Wert dieses Verhältnisses.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Rückgabewert

Wenn der Rückgabewert positiv ist, ist `Byte` dieser Wert die `CharType` konstante Anzahl von Zeichen, die zum Erzeugen des Zeichens erforderlich sind.

Die geschützte virtuelle Memberfunktion gibt Folgendes zurück:

- -1, wenn die Codierung von `extern_type` Sequenzen des Typs statusabhängig ist.

- 0, wenn die Codierung Sequenzen von variabler Länge umfasst.

- *N*, wenn die Codierung nur Sequenzen der Länge *N* umfasst.

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
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
}
```

```Output
1
1
1
```

## <a name="codecvtextern_type"></a><a name="extern_type"></a>codecvt::extern_type

Ein Zeichentyp, der für externe Darstellungen verwendet wird.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Byte` dar.

## <a name="codecvtin"></a><a name="in"></a>codecvt::in

Konvertiert eine externe Darstellung einer `Byte` Sequenz von Werten in `CharType` eine interne Darstellung einer Sequenz von Werten.

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

*Staat*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*first1*\
Zeiger auf den Anfang der zu konvertierenden Sequenz.

*zuletzt1*\
Zeiger auf das Ende der zu konvertierenden Sequenz.

*weiter1*\
Zeiger hinter das Ende der konvertierten Sequenz auf das erste nicht konvertierte Zeichen.

*first2*\
Zeiger auf den Anfang der konvertierten Sequenz.

*zuletzt2*\
Zeiger auf das Ende der konvertierten Sequenz.

*next2*\
Zeigen Sie `CharType` auf das, das `Chartype` nach dem letzten konvertierten in das erste unveränderte Zeichen in der Zielsequenz kommt.

### <a name="return-value"></a>Rückgabewert

Ein Rückgabewert, der den Erfolg, den teilweisen Erfolg oder das Fehlschlagen des Vorgangs angibt. Die Funktion gibt Folgendes zurück:

- `codecvt_base::error`wenn die Quellsequenz falsch ausgebildet ist.

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt.

- `codecvt_base::ok`wenn die Konvertierung erfolgreich ist.

- `codecvt_base::partial`wenn die Quelle nicht ausreicht oder das Ziel nicht groß genug ist, damit die Konvertierung erfolgreich ausgeführt werden kann.

### <a name="remarks"></a>Bemerkungen

*muss* der anfängliche Konvertierungsstatus am Anfang einer neuen Quellsequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. Nach einer teilweisen Konvertierung muss der *Status* so eingestellt werden, dass die Konvertierung fortgesetzt werden kann, wenn neue Zeichen eintreffen.

Die Memberfunktion gibt [do_in](#do_in)`( state, first1,  last1,  next1, first2, last2,  next2)`zurück.

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
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="codecvtintern_type"></a><a name="intern_type"></a>codecvt::intern_type

Ein Zeichentyp, der für interne Darstellungen verwendet wird.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `CharType` dar.

## <a name="codecvtlength"></a><a name="length"></a>codecvt::länge

Bestimmt, `Byte` wie viele Werte aus `Byte` einer bestimmten Sequenz externer `CharType` Werte nicht mehr `Byte` als eine bestimmte Anzahl interner Werte erzeugen, und gibt diese Anzahl von Werten zurück.

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parameter

*Staat*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*first1*\
Zeiger auf den Anfang der externen Sequenz.

*zuletzt1*\
Zeiger auf das Ende der externen Sequenz.

*len2*\
Die maximale Anzahl von Bytes, die von der Memberfunktion zurückgegeben werden kann.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die eine Anzahl der maximalen Anzahl von Konvertierungen darstellt, nicht größer `first1` `last1`als *len2*, definiert durch die externe Quellsequenz unter [ , ).

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_length](#do_length)`( state, first1, last1, len2)`zurück.

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
   char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << endl;
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="codecvtmax_length"></a><a name="max_length"></a>codecvt::max_length

Gibt die maximale `Byte` Anzahl externer Werte `CharType`zurück, die zum Erstellen eines internen Wertes erforderlich sind.

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die maximale `Byte` Anzahl von Werten, die zum Erstellen eines `CharType`Wertes erforderlich sind.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [do_max_length](#do_max_length) zurück.

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
   int res = use_facet<codecvt<char, char, mbstate_t> >
     ( loc ).max_length( );
   wcout << res << endl;
}
```

```Output
1
```

## <a name="codecvtout"></a><a name="out"></a>codecvt::out

Konvertiert eine Sequenz `CharType` interner Werte in `Byte` eine Sequenz externer Werte.

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

*Staat*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*first1*\
Zeiger auf den Anfang der zu konvertierenden Sequenz.

*zuletzt1*\
Zeiger auf das Ende der zu konvertierenden Sequenz.

*weiter1*\
Verweis auf einen Zeiger auf `CharType` den ersten `CharType` nicht konvertierten nach der letzten konvertierten.

*first2*\
Zeiger auf den Anfang der konvertierten Sequenz.

*zuletzt2*\
Zeiger auf das Ende der konvertierten Sequenz.

*next2*\
Verweis auf einen Zeiger auf `Byte` den ersten `Byte`nicht konvertierten nach der letzten konvertierten .

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt [do_out zurück.](#do_out)`( state, first1, last1, next1, first2, last2, next2)`

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [codecvt::do_out](#do_out).

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
   char pszExt[LEN+1];
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );
   char* pszNext;
   const wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).out( state,
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );
   pszExt[wcslen( pwszInt )] = 0;
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )
   << "The converted string is:\n ["
   << &pszExt[0]
   << "]" << endl;
}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="codecvtstate_type"></a><a name="state_type"></a>codecvt::state_type

Ein Zeichentyp, der verwendet wird, um Zwischenzustände bei Konvertierungen zwischen externen und internen Darstellungen darzustellen.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `StateType` dar.

## <a name="codecvtunshift"></a><a name="unshift"></a>codecvt::unshift

Stellt `Byte` die Werte bereit, die in einer zustandsabhängigen `Byte` Konvertierung erforderlich sind, um das letzte Zeichen in einer Sequenz von Werten abzuschließen.

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parameter

*Staat*\
Der Konvertierungszustand, der zwischen den Aufrufen der Memberfunktion beibehalten wird.

*first2*\
Zeiger auf die erste Position im Zielbereich.

*zuletzt2*\
Zeiger auf die letzte Position im Zielbereich.

*next2*\
Zeiger auf das erste unveränderte Element in der Zielsequenz.

### <a name="return-value"></a>Rückgabewert

Die Funktion gibt Folgendes zurück:

- `codecvt_base::error`wenn der Status einen ungültigen Zustand darstellt.

- `codecvt_base::noconv`, wenn die Funktion keine Konvertierung ausführt.

- `codecvt_base::ok`wenn die Konvertierung erfolgreich ist.

- `codecvt_base::partial`wenn das Ziel nicht groß genug ist, damit die Konvertierung erfolgreich ausgeführt werden kann.

### <a name="remarks"></a>Bemerkungen

Die funktion "Geschütztes virtuelles `CharType`Member" versucht, das Quellelement (0) in eine Zielsequenz zu konvertieren, die in [ `first2`, `last2`gespeichert wird, mit Ausnahme des beendenden Elements `Byte`(0). In *next2* wird immer ein Zeiger auf das erste unveränderte Element in der Zielsequenz gespeichert.

*muss* der anfängliche Konvertierungsstatus am Anfang einer neuen Quellsequenz darstellen. Die Funktion ändert bei Bedarf ihren gespeicherten Wert, um den aktuellen Zustand einer erfolgreichen Konvertierung widerzuspiegeln. In der Regel belässt das Konvertieren des Quellelements `CharType`(0) den aktuellen Status im ursprünglichen Konvertierungsstatus.

Die Memberfunktion gibt [do_unshift](#do_unshift)`( state, first2, last2, next2 )`zurück.

## <a name="see-also"></a>Siehe auch

[\<Gebietsschema>](../standard-library/locale.md)\
[Codepages](../c-runtime-library/code-pages.md)\
[Gebietsschemanamen, Sprachen und Länder-/Regionszeichenfolgen](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
