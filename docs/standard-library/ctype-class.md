---
title: ctype-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
ms.openlocfilehash: 640b2cc8506e498006feedbea6825a0e51a88209
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427170"
---
# <a name="ctype-class"></a>ctype-Klasse

Eine Klasse, die ein Facet bereitstellt, das verwendet wird, um Zeichen zu klassifizieren, zwischen Groß- und Kleinbuchstaben zu wechseln und zwischen dem systemeigenen Zeichensatz und dem vom Gebietsschema verwendeten Zeichensatz zu konvertieren.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parameter

*CharType* -\
Der Typ, der innerhalb eines Programms verwendet wird, um Zeichen zu codieren.

## <a name="remarks"></a>Hinweise

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in `id` gespeichert. Für Klassifizierungskriterien wird ein geschachtelter Bitmaskentyp in der ctype_base-Basisklasse bereitgestellt.

Die C++ Standard Bibliothek definiert zwei explizite spezizierungen dieser Klassen Vorlage:

- `ctype<char>`, eine explizite Spezialisierung, deren Unterschiede separat beschrieben werden. Weitere Informationen finden Sie unter [CType&lt;char&gt; Class](../standard-library/ctype-char-class.md).

- `ctype<wchar_t>`, das Elemente als breit Zeichen behandelt.

Andere Spezialisierungs `ctype<CharType>`der Klassen Vorlagen-:

- Konvertiert einen Wert *ch* vom Typ *CharType* in einen Wert vom Typ **char** mit dem Ausdruck `(char)ch`.

- Konvertiert ein *bytebyte* vom Typ **char** in einen Wert vom Typ *CharType* mit dem Ausdruck `CharType(byte)`.

Alle anderen Vorgänge werden für **char** -Werte auf die gleiche Weise wie für die explizite Spezialisierung `ctype<char>`ausgeführt.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[ctype](#ctype)|Konstruktor für Objekte der Klasse `ctype`, die als Gebietsschemafacets für Zeichen dienen.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Typ, der ein Zeichen beschreibt, das von einem Gebietsschema verwendet wird.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|Beschreibung|
|-|-|
|[do_is](#do_is)|Eine virtuelle Funktion, die aufgerufen wird, um zu testen, ob ein einzelnes Zeichen über ein bestimmtes Attribut verfügt, oder die Attribute jedes Zeichens in einem Bereich klassifiziert und in einem Array speichert.|
|[do_narrow](#do_narrow)|Eine virtuelle Funktion, die aufgerufen wird, um ein Zeichen vom Typ `CharType` von einem Gebiets Schema in das entsprechende Zeichen vom Typ " **char** " im systemeigenen Zeichensatz zu konvertieren.|
|[do_scan_is](#do_scan_is)|Eine virtuelle Funktion, die aufgerufen wird, um das erste Zeichen in einem Bereich zu suchen, der einer angegebenen Maske entspricht.|
|[do_scan_not](#do_scan_not)|Eine virtuelle Funktion, die aufgerufen wird, um das erste Zeichen in einem Bereich zu suchen, der einer angegebenen Maske nicht entspricht.|
|[do_tolower](#do_tolower)|Eine virtuelle Funktion, die aufgerufen wird, um ein Zeichen oder einen Zeichenbereich in Kleinbuchstaben umzuwandeln.|
|[do_toupper](#do_toupper)|Eine virtuelle Funktion, die aufgerufen wird, um ein Zeichen oder einen Zeichenbereich in Großbuchstaben umzuwandeln.|
|[do_widen](#do_widen)|Eine virtuelle Funktion, die aufgerufen wird, um ein Zeichen vom Typ " **char** " im systemeigenen Zeichensatz in das entsprechende Zeichen vom Typ zu konvertieren `CharType` von einem Gebiets Schema verwendet.|
|[is](#is)|Testet, ob ein einzelnes Zeichen über ein bestimmtes Attribut verfügt, oder klassifiziert die Attribute jedes Zeichens in einem Bereich und speichert sie in einem Array.|
|[narrow](#narrow)|Konvertiert ein Zeichen vom Typ `CharType`, das von einem Gebietsschema verwendet wird, in das entsprechende Zeichen vom Typ "char" im systemeigenen Zeichensatz.|
|[scan_is](#scan_is)|Sucht das erste Zeichen in einem Bereich, der einer bestimmten Maske entspricht.|
|[scan_not](#scan_not)|Sucht das erste Zeichen in einem Bereich, der einer bestimmten Maske nicht entspricht.|
|[tolower](#tolower)|Konvertiert ein Zeichen oder einen Zeichenbereich in Kleinbuchstaben.|
|[toupper](#toupper)|Konvertiert ein Zeichen oder einen Zeichenbereich in Großbuchstaben.|
|[widen](#widen)|Konvertiert ein Zeichen vom Typ " **char** " im systemeigenen Zeichensatz in das entsprechende Zeichen vom Typ `CharType` das von einem Gebiets Schema verwendet wird.|

## <a name="requirements"></a>Voraussetzungen

**Header:** \<Gebiets Schema >

**Namespace:** std

## <a name="char_type"></a> ctype::char_type

Ein Typ, der ein Zeichen beschreibt, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für den Vorlagenparameter *CharType*.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von [ als Rückgabewert finden Sie unter der Memberfunktion ](#widen)widen`char_type`.

## <a name="ctype"></a> ctype::ctype

Konstruktor für Objekte der Klasse ctype, die als Gebietsschemafacets für Zeichen dienen.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parameter

*_Refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Hinweise

Die möglichen Werte für den *_Refs* -Parameter und ihre Bedeutung lauten:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \> 1: diese Werte sind nicht definiert.

Direkte Beispiele sind nicht möglich, da der Destruktor geschützt ist.

Der Konstruktor initialisiert das entsprechende `locale::facet`-Basisobjekt mit **locale::** [facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="do_is"></a> ctype::do_is

Eine virtuelle Funktion, die aufgerufen wird, um zu testen, ob ein einzelnes Zeichen über ein bestimmtes Attribut verfügt, oder die Attribute jedes Zeichens in einem Bereich klassifiziert und in einem Array speichert.

```cpp
virtual bool do_is(
    mask maskVal,
    CharType ch) const;

virtual const CharType *do_is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parameter

*maskval* -\
Der Maskenwert, für den das Zeichen getestet werden soll.

*ch* -\
Das Zeichen, dessen Attribute getestet werden sollen.

*erste*\
Ein Zeiger auf das erste Zeichen in einem Bereich, dessen Attribute klassifiziert werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, dessen Attribute klassifiziert werden sollen.

*dest* -\
Ein Zeiger auf eine Stelle am Anfang des Arrays, an der die Maskenwerte, die die Attribute der einzelnen Zeichen beschreiben, gespeichert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die erste Memberfunktion gibt einen booleschen Wert zurück, der **wahr** ist, wenn das getestete Zeichen das vom Maskenwert beschriebene Attribut aufweist, und der **falsch** ist, wenn er das Attribut nicht aufweist.

Die zweite Memberfunktion gibt ein Array mit den Maskenwerten zurück, mit denen die Attribute der einzelnen Zeichen im Bereich beschrieben werden.

### <a name="remarks"></a>Hinweise

Die Maskenwerte, mit denen die Attribute der Zeichen beschrieben werden, werden von der [ctype_base](../standard-library/ctype-base-class.md)-Klasse bereitgestellt, von der ctype abgeleitet wird. Die erste Memberfunktion kann Ausdrücke für den ersten Parameter akzeptieren, die als Bitmasken bezeichnet werden und mit verschiedenen Maskenwerten mithilfe der logischen bitweisen Operatoren (&#124; , & , ^ , ~) gebildet werden.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [is](#is), mit dem `do_is` aufgerufen wird.

## <a name="do_narrow"></a> ctype::do_narrow

Eine virtuelle Funktion, die aufgerufen wird, um ein Zeichen vom Typ `CharType` von einem Gebiets Schema in das entsprechende Zeichen vom Typ " **char** " im systemeigenen Zeichensatz zu konvertieren.

```cpp
virtual char do_narrow(
    CharType ch,
    char default = '\0') const;

virtual const CharType* do_narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parameter

*ch* -\
Das zu konvertierende Zeichen vom Typ `Chartype`, das vom Gebietsschema verwendet wird.

*Standard*\
Der Standardwert, der von der Element Funktion den Zeichen vom Typ `CharType` zugewiesen werden soll, die keine Gegenstücke vom Typ " **char**" aufweisen.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Bereich, in dem Zeichen konvertiert werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, in dem Zeichen konvertiert werden sollen.

*dest* -\
Ein konstanter Zeiger auf das erste Zeichen vom Typ " **char** " im Zielbereich, in dem der konvertierte Zeichenbereich gespeichert wird.

### <a name="return-value"></a>Rückgabewert

Die erste geschützte Member-Funktion gibt das systemeigene Zeichen vom Typ char zurück, das dem-Parameter Zeichen vom Typ `CharType` entspricht, oder *default* , wenn keine Entsprechung definiert ist.

Die zweite geschützte Memberfunktion gibt einen Zeiger auf den Zielbereich mit nativen Zeichen zurück, die aus Zeichen vom Typ `CharType` konvertiert wurden.

### <a name="remarks"></a>Hinweise

Die zweite geschützte Member-Vorlagen Funktion speichert in `dest`[`I`] den Wert `do_narrow`(`first` [`I`], `default`), für `I` im Intervall [0, `last` - `first`).

### <a name="example"></a>Beispiel

Siehe das Beispiel für [narrow](#narrow), mit dem `do_narrow` aufgerufen wird.

## <a name="do_scan_is"></a> ctype::do_scan_is

Eine virtuelle Funktion, die aufgerufen wird, um das erste Zeichen in einem Bereich zu suchen, der einer angegebenen Maske entspricht.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*maskval* -\
Der Maskenwert, mit dem ein Zeichen übereinstimmen soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Bereich, in dem gesucht werden soll.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, in dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erste Zeichen in einem Bereich, der einer bestimmten Maske entspricht. Wenn kein solcher Wert vorhanden ist, gibt die Funktion *Last*zurück.

### <a name="remarks"></a>Hinweise

Die geschützte Member-Funktion gibt den kleinsten Zeiger `ptr` im Bereich [`first`, `last`) zurück, für den [do_is](#do_is)(`maskVal`, \* `ptr`) true ist.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [scan_is](#scan_is), mit dem `do_scan_is` aufgerufen wird.

## <a name="do_scan_not"></a> ctype::do_scan_not

Eine virtuelle Funktion, die aufgerufen wird, um das erste Zeichen in einem Bereich zu suchen, der einer angegebenen Maske nicht entspricht.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*maskval* -\
Der Maskenwert, mit dem ein Zeichen nicht übereinstimmen soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Bereich, in dem gesucht werden soll.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, in dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erste Zeichen in einem Bereich, der einer bestimmten Maske nicht entspricht. Wenn kein solcher Wert vorhanden ist, gibt die Funktion *Last*zurück.

### <a name="remarks"></a>Hinweise

Die geschützte Member-Funktion gibt den kleinsten Zeiger `ptr` im Bereich [`first`, `last`) zurück, für den [do_is](#do_is)(`maskVal`, \* `ptr`) false ist.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [scan_not](#scan_not), mit dem `do_scan_not` aufgerufen wird.

## <a name="do_tolower"></a> ctype::do_tolower

Eine virtuelle Funktion, die aufgerufen wird, um ein Zeichen oder einen Zeichenbereich in Kleinbuchstaben umzuwandeln.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*ch* -\
Das Zeichen, das in einen Kleinbuchstaben umgewandelt werden soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Zeichenbereich, in dem die Zeichen in Groß- bzw. Kleinbuchstaben umgewandelt werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Zeichenbereich, in dem die Zeichen in Groß- bzw. Kleinbuchstaben umgewandelt werden sollen.

### <a name="return-value"></a>Rückgabewert

Die erste geschützte Member-Funktion gibt die Kleinbuchstaben Form des-Parameters *ch*zurück. Wenn kein Formular aus Kleinbuchstaben vorhanden ist, wird *ch*zurückgegeben. Die zweite geschützte Member-Funktion gibt den *letzten*zurück.

### <a name="remarks"></a>Hinweise

Die zweite geschützte Member-Vorlagen Funktion ersetzt jedes Element `first` [`I`] für `I` im Intervall [0, `last` - `first`) mit `do_tolower`(`first` [`I`]).

### <a name="example"></a>Beispiel

Siehe das Beispiel für [tolower](#tolower), mit dem `do_tolower` aufgerufen wird.

## <a name="do_toupper"></a> ctype::do_toupper

Eine virtuelle Funktion, die aufgerufen wird, um ein Zeichen oder einen Zeichenbereich in Großbuchstaben umzuwandeln.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*ch* -\
Das Zeichen, das in einen Großbuchstaben umgewandelt werden soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Zeichenbereich, in dem die Zeichen in Groß- bzw. Kleinbuchstaben umgewandelt werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Zeichenbereich, in dem die Zeichen in Groß- bzw. Kleinbuchstaben umgewandelt werden sollen.

### <a name="return-value"></a>Rückgabewert

Die erste geschützte Member-Funktion gibt die Großbuchstaben Form des-Parameters *ch*zurück. Wenn kein Großbuchstabe vorhanden ist, wird " *ch*" zurückgegeben. Die zweite geschützte Member-Funktion gibt den *letzten*zurück.

### <a name="remarks"></a>Hinweise

Die zweite geschützte Member-Vorlagen Funktion ersetzt jedes Element `first` [`I`] für `I` im Intervall [0, `last` - `first`) mit `do_toupper`(`first` [`I`]).

### <a name="example"></a>Beispiel

Siehe das Beispiel für [toupper](#toupper), mit dem `do_toupper` aufgerufen wird.

## <a name="do_widen"></a> ctype::do_widen

Eine virtuelle Funktion, die aufgerufen wird, um ein Zeichen vom Typ " **char** " im systemeigenen Zeichensatz in das entsprechende Zeichen vom Typ zu konvertieren `CharType` von einem Gebiets Schema verwendet.

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parameter

*byte*\
Das Zeichen vom Typ " **char** " im systemeigenen Zeichensatz, das konvertiert werden soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Bereich, in dem Zeichen konvertiert werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, in dem Zeichen konvertiert werden sollen.

*dest* -\
Ein Zeiger auf das erste Zeichen vom Typ `CharType` in dem Zielbereich, in dem der konvertierte Zeichenbereich gespeichert wird.

### <a name="return-value"></a>Rückgabewert

Die erste geschützte Member-Funktion gibt das Zeichen vom Typ `CharType` zurück, das dem Parameter Zeichen des systemeigenen Typs **char**entspricht.

Die zweite geschützte Member-Funktion gibt einen Zeiger auf den Zielbereich von Zeichen vom Typ zurück `CharType` der von einem Gebiets Schema verwendet wird, das aus systemeigenen Zeichen vom Typ **char**konvertiert wurde.

### <a name="remarks"></a>Hinweise

Die zweite geschützte Membervorlagenfunktion speichert in `dest`[ `I`] den Wert `do_widen`( `first`[ `I`]), wobei `I` im Intervall [0, `last` - `first`] liegen muss.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [widen](#widen), mit dem `do_widen` aufgerufen wird.

## <a name="is"></a> ctype::is

Testet, ob ein einzelnes Zeichen über ein bestimmtes Attribut verfügt, oder klassifiziert die Attribute jedes Zeichens in einem Bereich und speichert sie in einem Array.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parameter

*maskval* -\
Der Maskenwert, für den das Zeichen getestet werden soll.

*ch* -\
Das Zeichen, dessen Attribute getestet werden sollen.

*erste*\
Ein Zeiger auf das erste Zeichen in einem Bereich, dessen Attribute klassifiziert werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, dessen Attribute klassifiziert werden sollen.

*dest* -\
Ein Zeiger auf eine Stelle am Anfang des Arrays, an der die Maskenwerte, die die Attribute der einzelnen Zeichen beschreiben, gespeichert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die erste Member-Funktion gibt **true** zurück, wenn das überprüfte Zeichen über das durch den Mask-Wert beschriebene Attribut verfügt. **false** , wenn das-Attribut nicht vorhanden ist.

Die zweite Memberfunktion gibt einen Zeiger auf das letzte Zeichen in dem Bereich zurück, dessen Attribute klassifiziert werden sollen.

### <a name="remarks"></a>Hinweise

Die Maskenwerte, mit denen die Attribute der Zeichen beschrieben werden, werden von der [ctype_base](../standard-library/ctype-base-class.md)-Klasse bereitgestellt, von der ctype abgeleitet wird. Die erste Memberfunktion kann Ausdrücke für den ersten Parameter akzeptieren, die als Bitmasken bezeichnet werden und mit verschiedenen Maskenwerten mithilfe der logischen bitweisen Operatoren (&#124; , & , ^ , ~) gebildet werden.

### <a name="example"></a>Beispiel

```cpp
// ctype_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main() {
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );

   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;

   char *string = "Hello, my name is John!";
   ctype<char>::mask maskarray[30];
   use_facet<ctype<char> > ( loc2 ).is(
      string, string + strlen(string), maskarray );
   for (unsigned int i = 0; i < strlen(string); i++) {
      cout << string[i] << ": "
           << (maskarray[i] & ctype_base::alpha  "alpha"
                                                : "not alpha")
           << endl;;
   };
}
```

## <a name="narrow"></a> ctype::narrow

Konvertiert Zeichen vom Typ `CharType` die von einem Gebiets Schema verwendet werden, in die entsprechenden Zeichen vom Typ " **char** " im systemeigenen Zeichensatz.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parameter

*ch* -\
Das zu konvertierende Zeichen vom Typ `Chartype`, das vom Gebietsschema verwendet wird.

*Standard*\
Der Standardwert, der von der Element Funktion den Zeichen vom Typ `CharType` zugewiesen werden soll, die keine Gegenstücke vom Typ " **char**" aufweisen.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Bereich, in dem Zeichen konvertiert werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, in dem Zeichen konvertiert werden sollen.

*dest* -\
Ein konstanter Zeiger auf das erste Zeichen vom Typ " **char** " im Zielbereich, in dem der konvertierte Zeichenbereich gespeichert wird.

### <a name="return-value"></a>Rückgabewert

Die erste Member-Funktion gibt das systemeigene Zeichen vom Typ **char** zurück, das dem-Parameter Zeichen vom Typ `CharType default` entspricht, wenn keine Entsprechung definiert ist.

Die zweite Memberfunktion gibt einen Zeiger auf den Zielbereich mit nativen Zeichen zurück, die aus Zeichen vom Typ `CharType` konvertiert wurden.

### <a name="remarks"></a>Hinweise

Die erste Member-Funktion gibt [do_narrow](#do_narrow)(`ch`, `default`) zurück. Die zweite Member-Funktion gibt [do_narrow](#do_narrow) (`first`, `last`, `default`, `dest`) zurück. Nur für die Basisquellzeichen ist sichergestellt, dass ein eindeutiges inverses `CharType`-Bild unter `narrow` vorhanden ist. Für diese Basisquellzeichen gilt folgende Invariante: `narrow` ( [widen](#widen) ( **c** ), 0 ) == **c**.

### <a name="example"></a>Beispiel

```cpp
// ctype_narrow.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "english" );
   wchar_t *str1 = L"\x0392fhello everyone";
   char str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996
   str2[wcslen(str1)] = '\0';
   wcout << str1 << endl;
   cout << &str2[0] << endl;
}
```

```Output
Xhello everyone
```

## <a name="scan_is"></a> ctype::scan_is

Sucht das erste Zeichen in einem Bereich, der einer bestimmten Maske entspricht.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*maskval* -\
Der Maskenwert, mit dem ein Zeichen übereinstimmen soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Bereich, in dem gesucht werden soll.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, in dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erste Zeichen in einem Bereich, der einer bestimmten Maske entspricht. Wenn kein solcher Wert vorhanden ist, gibt die Funktion *Last*zurück.

### <a name="remarks"></a>Hinweise

Die Member-Funktion gibt [do_scan_is](#do_scan_is)zurück (`maskVal`, `first`, `last`).

### <a name="example"></a>Beispiel

```cpp
// ctype_scan_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is
      ( ctype_base::punct, string, string + strlen(string) );
   cout << "The first punctuation is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
The first punctuation is "," at position: 5
```

## <a name="scan_not"></a> ctype::scan_not

Sucht das erste Zeichen in einem Bereich, der einer bestimmten Maske nicht entspricht.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*maskval* -\
Der Maskenwert, mit dem ein Zeichen nicht übereinstimmen soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Bereich, in dem gesucht werden soll.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, in dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erste Zeichen in einem Bereich, der einer bestimmten Maske nicht entspricht. Wenn kein solcher Wert vorhanden ist, gibt die Funktion *Last*zurück.

### <a name="remarks"></a>Hinweise

Die Member-Funktion gibt [Do_scan_not](#do_scan_not)zurück (`maskVal`, `first`, `last`).

### <a name="example"></a>Beispiel

```cpp
// ctype_scan_not.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not
      ( ctype_base::alpha, string, string + strlen(string) );
   cout << "First nonalpha character is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
First nonalpha character is "," at position: 5
```

## <a name="tolower"></a> ctype::tolower

Konvertiert ein Zeichen oder einen Zeichenbereich in Kleinbuchstaben.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*ch* -\
Das Zeichen, das in einen Kleinbuchstaben umgewandelt werden soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Zeichenbereich, in dem die Zeichen in Groß- bzw. Kleinbuchstaben umgewandelt werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Zeichenbereich, in dem die Zeichen in Groß- bzw. Kleinbuchstaben umgewandelt werden sollen.

### <a name="return-value"></a>Rückgabewert

Die erste Member-Funktion gibt die Kleinbuchstaben Form des-Parameters *ch*zurück. Wenn kein Formular aus Kleinbuchstaben vorhanden ist, wird *ch*zurückgegeben.

Die zweite Member-Funktion gibt den *letzten*zurück.

### <a name="remarks"></a>Hinweise

Die erste Member-Funktion gibt [Do_tolower](#do_tolower)(`ch`) zurück. Die zweite Member-Funktion gibt [Do_tolower](#do_tolower)(`first`, `last`) zurück.

### <a name="example"></a>Beispiel

```cpp
// ctype_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "HELLO, MY NAME IS JOHN";

   use_facet<ctype<char> > ( loc1 ).tolower
      ( string, string + strlen(string) );
   cout << "The lowercase string is: " << string << endl;
}
```

```Output
The lowercase string is: hello, my name is john
```

## <a name="toupper"></a> ctype::toupper

Konvertiert ein Zeichen oder einen Zeichenbereich in Großbuchstaben.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*ch* -\
Das Zeichen, das in einen Großbuchstaben umgewandelt werden soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Zeichenbereich, in dem die Zeichen in Groß- bzw. Kleinbuchstaben umgewandelt werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Zeichenbereich, in dem die Zeichen in Groß- bzw. Kleinbuchstaben umgewandelt werden sollen.

### <a name="return-value"></a>Rückgabewert

Die erste Member-Funktion gibt die Großbuchstaben Form des-Parameters *ch*zurück. Wenn kein Großbuchstabe vorhanden ist, wird " *ch*" zurückgegeben.

Die zweite Member-Funktion gibt den *letzten*zurück.

### <a name="remarks"></a>Hinweise

Die erste Member-Funktion gibt [Do_toupper](#do_toupper)(`ch`) zurück. Die zweite Memberfunktion gibt [do_toupper](#do_toupper)( `first`, `last`) zurück.

### <a name="example"></a>Beispiel

```cpp
// ctype_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "Hello, my name is John";

   use_facet<ctype<char> > ( loc1 ).toupper
      ( string, string + strlen(string) );
   cout << "The uppercase string is: " << string << endl;
}
```

```Output
The uppercase string is: HELLO, MY NAME IS JOHN
```

## <a name="widen"></a> ctype::widen

Konvertiert ein Zeichen vom Typ " **char** " im systemeigenen Zeichensatz in das entsprechende Zeichen vom Typ `CharType` das von einem Gebiets Schema verwendet wird.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parameter

*byte*\
Das Zeichen vom Typ char im nativen Zeichensatz, das umgewandelt werden soll.

*erste*\
Ein Zeiger auf das erste Zeichen in dem Bereich, in dem Zeichen konvertiert werden sollen.

*Letzter*\
Ein Zeiger auf das Zeichen direkt nach dem letzten Zeichen in dem Bereich, in dem Zeichen konvertiert werden sollen.

*dest* -\
Ein Zeiger auf das erste Zeichen vom Typ `CharType` in dem Zielbereich, in dem der konvertierte Zeichenbereich gespeichert wird.

### <a name="return-value"></a>Rückgabewert

Die erste Member-Funktion gibt das Zeichen vom Typ `CharType` zurück, das dem Parameter Zeichen des systemeigenen Typs **char**entspricht.

Die zweite Member-Funktion gibt einen Zeiger auf den Zielbereich von Zeichen vom Typ zurück `CharType` der von einem Gebiets Schema verwendet wird, das aus systemeigenen Zeichen vom Typ **char**konvertiert wurde.

### <a name="remarks"></a>Hinweise

Die erste Member-Funktion gibt [Do_widen](#do_widen)(`byte`) zurück. Die zweite Member-Funktion gibt [Do_widen](#do_widen)zurück (`first`, `last`, `dest`).

### <a name="example"></a>Beispiel

```cpp
// ctype_widen.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "English" );
   char *str1 = "Hello everyone!";
   wchar_t str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996
   str2[strlen(str1)] = '\0';
   cout << str1 << endl;
   wcout << &str2[0] << endl;

   ctype<wchar_t>::char_type charT;
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );
}
```

```Output
Hello everyone!
Hello everyone!
```

## <a name="see-also"></a>Siehe auch

[\<locale>](../standard-library/locale.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
