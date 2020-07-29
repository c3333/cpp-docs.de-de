---
title: collate-Klasse
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate
- locale/std::collate::char_type
- locale/std::collate::string_type
- locale/std::collate::compare
- locale/std::collate::do_compare
- locale/std::collate::do_hash
- locale/std::collate::do_transform
- locale/std::collate::hash
- locale/std::collate::transform
helpviewer_keywords:
- std::collate [C++]
- std::collate [C++], char_type
- std::collate [C++], string_type
- std::collate [C++], compare
- std::collate [C++], do_compare
- std::collate [C++], do_hash
- std::collate [C++], do_transform
- std::collate [C++], hash
- std::collate [C++], transform
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
ms.openlocfilehash: ccdf05a7a41fc7f646852e7d326832b86c41dde8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230103"
---
# <a name="collate-class"></a>collate-Klasse

Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema Aspekt dienen kann, um die Reihenfolge und Gruppierung von Zeichen innerhalb einer Zeichenfolge zu steuern, Vergleiche zwischen Ihnen und dem Hashwert von Zeichen folgen.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parameter

*CharType*\
Der Typ, der innerhalb eines Programms verwendet wird, um Zeichen zu codieren.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in `id` gespeichert. In einigen Sprachen werden Zeichen gruppiert und als einzelnes Zeichen behandelt. In anderen Sprachen hingegen werden einzelne Zeichen als zwei Zeichen behandelt. Die sortierenden Dienste, die von der collate-Klasse bereitgestellt werden, bieten die Möglichkeit zum Sortieren dieser Fälle.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[COLLATE](#collate)|Der Konstruktor für Objekte der `collate`-Klasse, die als Gebietsschemafacet dient, um Zeichenfolgensortierungskonventionen zu bearbeiten.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, der ein Zeichen vom Typ `CharType` beschreibt.|
|[string_type](#string_type)|Ein Typ, der eine Zeichenfolge vom Typ `basic_string` beschreibt, die Zeichen vom Typ `CharType` enthält.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[vergleichbar](#compare)|Vergleicht zwei Zeichensequenzen nach ihren facetspezifischen Regeln für Gleichheit oder Ungleichheit.|
|[do_compare](#do_compare)|Eine virtuelle Funktion, die aufgerufen wird, um zwei Zeichensequenzen gemäß ihren facetspezifischen Regeln in Bezug auf Gleichheit oder Ungleichheit zu vergleichen.|
|[do_hash](#do_hash)|Eine virtuelle Funktion, die aufgerufen wird, um den Hashwert der Sequenzen anhand der facetspezifischen Regeln zu bestimmen.|
|[do_transform](#do_transform)|Eine virtuelle Funktion, die aufgerufen wird, um eine Zeichenfolge aus einem Gebietsschema in eine Zeichenfolge zu konvertieren, die in den lexikografischen Vergleichen mit anderen Zeichensequenzen verwendet werden kann, die auf ähnliche Weise aus demselben Gebietsschema konvertiert wurden.|
|[hash](#hash)|Bestimmt den Hashwert der Sequenz nach ihren facetspezifischen Regeln.|
|[Sin](#transform)|Konvertiert eine Zeichenfolge von einem Gebietsschema in eine Zeichenfolge, die in den lexikografischen Vergleichen mit anderen Zeichenfolgen verwendet wird, die auf ähnliche Weise aus dem gleichen Gebietsschema konvertiert wurden.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<locale>

**Namespace:** std

## <a name="collatechar_type"></a><a name="char_type"></a>COLLATE:: char_type

Ein Typ, der ein Zeichen vom Typ `CharType` beschreibt.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `CharType` dar.

## <a name="collatecollate"></a><a name="collate"></a>COLLATE:: COLLATE

Der Konstruktor für Objekte der collate-Klasse, die als Gebietsschemafacet dient, um Sortierungskonventionen für Zeichenfolgen zu behandeln.

```cpp
public:
    explicit collate(
    size_t _Refs = 0);

protected:
    collate(
const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parameter

*_Refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

*_Locname*\
Der Name des Gebietsschemas.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *_Refs* -Parameter und ihre Bedeutung lauten:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \>1: diese Werte sind nicht definiert.

Der Konstruktor initialisiert sein Basisobjekt mit **locale::**[Face(](../standard-library/locale-class.md#facet_class) `_Refs` ).

## <a name="collatecompare"></a><a name="compare"></a>COLLATE:: Compare

Vergleicht zwei Zeichensequenzen nach ihren facetspezifischen Regeln für Gleichheit oder Ungleichheit.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parameter

*First1*\
Zeiger auf das erste Element in der ersten zu vergleichenden Sequenz.

*Last1*\
Zeiger auf das letzte Element in der ersten zu vergleichenden Sequenz.

*First2*\
Zeiger auf das erste Element in der zweiten zu vergleichenden Sequenz.

*Last2*\
Zeiger auf das letzte Element in der zweiten zu vergleichenden Sequenz.

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt Folgendes zurück:

- -1, wenn die erste Sequenz im Vergleich kleiner ist als die zweite Sequenz.

- +1, wenn die zweite Sequenz kleiner als die erste Sequenz ist.

- 0, wenn die Sequenzen gleichwertig sind.

### <a name="remarks"></a>Bemerkungen

Die erste Sequenz ist im Vergleich kleiner, wenn sie im frühesten ungleichen Paar in den Sequenzen das kleinere Element enthält oder wenn zwar keine ungleichen Paare vorhanden sind, die erste Sequenz aber kürzer ist.

Die Member-Funktion gibt [Do_compare](#do_compare)( `first1` , `last1` , `first2` ,) zurück `last2` .

### <a name="example"></a>Beispiel

```cpp
// collate_compare.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare ( s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result2 << endl;
}
```

## <a name="collatedo_compare"></a><a name="do_compare"></a>COLLATE::d o_compare

Eine virtuelle Funktion, die aufgerufen wird, um zwei Zeichensequenzen gemäß ihren facetspezifischen Regeln in Bezug auf Gleichheit oder Ungleichheit zu vergleichen.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parameter

*First1*\
Zeiger auf das erste Element in der ersten zu vergleichenden Sequenz.

*Last1*\
Zeiger auf das letzte Element in der ersten zu vergleichenden Sequenz.

*First2*\
Zeiger auf das erste Element in der zweiten zu vergleichenden Sequenz.

*Last2*\
Zeiger auf das letzte Element in der zweiten zu vergleichenden Sequenz.

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt Folgendes zurück:

- -1, wenn die erste Sequenz im Vergleich kleiner ist als die zweite Sequenz.

- +1, wenn die zweite Sequenz kleiner als die erste Sequenz ist.

- 0, wenn die Sequenzen gleichwertig sind.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Member-Funktion vergleicht die Sequenz bei [* First1, Last1) * mit der Sequenz bei *[First2, Last2*). Er vergleicht Werte, indem er `operator<` zwischen Paaren entsprechender Elemente vom Typ anwendet `CharType` . Die erste Sequenz ist im Vergleich kleiner, wenn sie im frühesten ungleichen Paar in den Sequenzen das kleinere Element enthält oder wenn zwar keine ungleichen Paare vorhanden sind, die erste Sequenz aber kürzer ist.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [collate::compare](#compare), mit dem `do_compare` aufgerufen wird.

## <a name="collatedo_hash"></a><a name="do_hash"></a>COLLATE::d o_hash

Eine virtuelle Funktion, die aufgerufen wird, um den Hashwert der Sequenzen anhand der facetspezifischen Regeln zu bestimmen.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*erstes*\
Ein Zeiger auf das erste Zeichen in der Sequenz, dessen Hashwert bestimmt werden soll.

*letzten*\
Ein Zeiger auf das letzte Zeichen in der Sequenz, dessen Hashwert bestimmt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Hashwert des Typs **`long`** für die Sequenz.

### <a name="remarks"></a>Bemerkungen

Ein Hashwert kann beispielsweise nützlich sein, um Sequenzen pseudozufällig auf ein Array von Listen zu verteilen.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [hash](#hash), mit dem `do_hash` aufgerufen wird.

## <a name="collatedo_transform"></a><a name="do_transform"></a>COLLATE::d o_transform

Eine virtuelle Funktion, die aufgerufen wird, um eine Zeichenfolge aus einem Gebietsschema in eine Zeichenfolge zu konvertieren, die in den lexikografischen Vergleichen mit anderen Zeichensequenzen verwendet werden kann, die auf ähnliche Weise aus demselben Gebietsschema konvertiert wurden.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*erstes*\
Ein Zeiger auf das erste Zeichen in der zu konvertierenden Sequenz.

*letzten*\
Ein Zeiger auf das letzte Zeichen in der zu konvertierenden Sequenz.

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, bei der es sich um die transformierte Zeichensequenz handelt.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Member-Funktion gibt ein Objekt der-Klasse zurück [string_type](#string_type) dessen gesteuerte Sequenz eine Kopie der Sequenz [ `first` ,) ist `last` . Wenn eine Klasse, die von COLLATE abgeleitet \< **CharType**> ist, [Do_compare](#do_compare)überschreibt, sollte Sie auch überschreiben, `do_transform` um abzugleichen. Bei der Übergabe an `collate::compare` müssen zwei transformierte Zeichenfolgen zu demselben Ergebnis führen, das Sie erhalten würden, wenn die untransformierten Zeichenfolgen für den Vergleich in der abgeleiteten Klasse übergeben würden.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [transform](#transform), mit dem `do_transform` aufgerufen wird.

## <a name="collatehash"></a><a name="hash"></a>COLLATE:: Hash

Bestimmt den Hashwert der Sequenz nach ihren facetspezifischen Regeln.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*erstes*\
Ein Zeiger auf das erste Zeichen in der Sequenz, dessen Hashwert bestimmt werden soll.

*letzten*\
Ein Zeiger auf das letzte Zeichen in der Sequenz, dessen Hashwert bestimmt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Hashwert des Typs **`long`** für die Sequenz.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [do_hash](#do_hash)( `first` ,) zurück `last` .

Ein Hashwert kann beispielsweise nützlich sein, um Sequenzen pseudozufällig auf ein Array von Listen zu verteilen.

### <a name="example"></a>Beispiel

```cpp
// collate_hash.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("\x00dfzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet
   _TCHAR * s2 = _T("zzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet

   long r1 = use_facet< collate<_TCHAR> > ( loc ).
      hash (s1, &s1[_tcslen( s1 )-1 ]);
   long r2 =  use_facet< collate<_TCHAR> > ( loc ).
      hash (s2, &s2[_tcslen( s2 )-1 ] );
   cout << r1 << " " << r2 << endl;
}
```

```Output
541187293 551279837
```

## <a name="collatestring_type"></a><a name="string_type"></a>COLLATE:: string_type

Ein Typ, der eine Zeichenfolge vom Typ `basic_string` beschreibt, die Zeichen vom Typ `CharType` enthält.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung von Klassen Vorlagen [basic_string](../standard-library/basic-string-class.md) , deren Objekte Kopien der Quell Sequenz speichern können.

### <a name="example"></a>Beispiel

Unter [transform](#transform) finden Sie ein Beispiel für das Deklarieren und Verwenden von `string_type`.

## <a name="collatetransform"></a><a name="transform"></a>COLLATE:: Transform

Konvertiert eine Zeichenfolge von einem Gebietsschema in eine Zeichenfolge, die in den lexikografischen Vergleichen mit anderen Zeichenfolgen verwendet wird, die auf ähnliche Weise aus dem gleichen Gebietsschema konvertiert wurden.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*erstes*\
Ein Zeiger auf das erste Zeichen in der zu konvertierenden Sequenz.

*letzten*\
Ein Zeiger auf das letzte Zeichen in der zu konvertierenden Sequenz.

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die die transformierte Zeichensequenz enthält.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [Do_transform](#do_transform)( `first` ,) zurück `last` .

### <a name="example"></a>Beispiel

```cpp
// collate_transform.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   _TCHAR* s1 = _T("\x00dfzz abc.");
   // \x00df is the German sharp-s (looks like beta),
   // it comes before z in the alphabet
   _TCHAR* s2 = _T("zzz abc.");

   collate<_TCHAR>::string_type r1;   // OK for typedef
   r1 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s1, &s1[_tcslen( s1 )-1 ]);

   cout << r1 << endl;

   basic_string<_TCHAR> r2 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s2, &s2[_tcslen( s2 )-1 ]);

   cout << r2 << endl;

   int result1 = use_facet<collate<_TCHAR> > ( loc ).compare
      (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );

   cout << _tcscmp(r1.c_str( ),r2.c_str( )) << result1
      << _tcscmp(s1,s2) <<endl;
}
```

```Output

-1-11
```

## <a name="see-also"></a>Weitere Informationen

[\<locale>](../standard-library/locale.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
