---
title: time_put-Klasse
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
ms.openlocfilehash: 10691de0a583dc7d5a66c319968d90978bf59480
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368001"
---
# <a name="time_put-class"></a>time_put-Klasse

Die Klassenvorlage beschreibt ein Objekt, das als Gebietsschema dienen kann, um Konvertierungen von Zeitwerten in Sequenzen vom Typ `CharType`zu steuern.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parameter

*Chartype*\
Der Typ, der innerhalb eines Programms verwendet wird, um Zeichen zu codieren.

*OutputIterator*\
Der Typ des Iterators, in den die Time-Put-Funktionen ihre Ausgabe schreiben.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[time_put](#time_put)|Der Konstruktor für Objekte des Typs `time_put`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.|
|[iter_type](#iter_type)|Ein Typ, der einen Ausgabeiterator beschreibt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[do_put](#do_put)|Eine virtuelle Funktion, die Zeit- und Datumsinformationen als Sequenz von `CharType`-Objekten ausgibt.|
|[setzen](#put)|Gibt Zeit- und Datumsinformationen als Sequenz von `CharType`-Objekten aus.|

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="time_putchar_type"></a><a name="char_type"></a>time_put::char_type

Ein Typ, mit dem ein Zeichen beschrieben wird, das von einem Gebietsschema verwendet wird.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `CharType` dar.

## <a name="time_putdo_put"></a><a name="do_put"></a>time_put::do_put

Eine virtuelle Funktion, die Zeit- und Datumsinformationen als Sequenz von `CharType`-Objekten ausgibt.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parameter

*nächster*\
Ein Ausgabeiterator, in den die Zeichensequenz für Zeit und Datum eingefügt werden soll.

*_iosbase*\
Nicht verwendet.

*_pt*\
Die Zeit- und Datumsinformationen, die ausgegeben werden.

*_Fmt*\
Das Format der Ausgabe. Siehe [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) für gültige Werte.

*_Mod*\
Ein Modifizierer für das Format. Siehe [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) für gültige Werte.

### <a name="return-value"></a>Rückgabewert

Ein Iterator an die erste Position hinter dem letzten eingefügten Element.

### <a name="remarks"></a>Bemerkungen

Die Virtual Protected Member-Funktion `next` generiert sequenzielle Elemente \* `_Pt`ab `tm`Zeitwerten, die im Objekt vom Typ gespeichert sind. Die Funktion gibt einen Iterator zurück, der die nächste Stelle zum Einfügen eines Elements nach der generierten Ausgabe festlegt.

Die Ausgabe wird durch die `strftime`gleichen Regeln generiert, die von verwendet werden, mit dem letzten Argument *von _Pt*, um eine Reihe von **char-Elementen** in einem Array zu generieren. Es wird davon ausgegangen, dass jedes dieser `CharType` **char-Elemente** einem äquivalenten Element des Typs durch eine einfache 1:1-Zuordnung zugeordnet wird. Wenn *_Mod* gleich Null ist, ist das effektive Format "%F", wobei F durch *_Fmt*ersetzt wird. Andernfalls ist das effektive Format "%MF", wobei M durch *_Mod*ersetzt wird.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [put](#put), mit dem `do_put` aufgerufen wird.

## <a name="time_putiter_type"></a><a name="iter_type"></a>time_put::iter_type

Ein Typ, der einen Ausgabeiterator beschreibt.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `OutputIterator` dar.

## <a name="time_putput"></a><a name="put"></a>time_put::put

Gibt Zeit- und Datumsinformationen als Sequenz von `CharType`-Objekten aus.

```cpp
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parameter

*nächster*\
Ein Ausgabeiterator, in den die Zeichensequenz für Zeit und Datum eingefügt werden soll.

*_iosbase*\
Nicht verwendet.

*_Fill*\
Das Zeichen `CharType` des Typs, der für den Abstand verwendet wird.

*_pt*\
Die Zeit- und Datumsinformationen, die ausgegeben werden.

*_Fmt*\
Das Format der Ausgabe. Siehe [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) für gültige Werte.

*_Mod*\
Ein Modifizierer für das Format. Siehe [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) für gültige Werte.

*Ersten*\
Der Anfang der Formatierungszeichenfolge für die Ausgabe. Siehe [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) für gültige Werte.

*letzte*\
Das Ende der Formatierungszeichenfolge für die Ausgabe. Siehe [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) für gültige Werte.

### <a name="return-value"></a>Rückgabewert

Ein Iterator an die erste Position hinter dem letzten eingefügten Element.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion`next`gibt `_Iosbase` `_Fill` [do_put](#do_put)zurück `_Mod`( , , , `_Pt`, `_Fmt`, . Die zweite Memberfunktion \* `next` kopiert in ++ `first`jedes `last`Element im Intervall [ , ) mit einem Prozent (%). Für einen Prozentsatz gefolgt von einem `first`Zeichen `last` `next`  =  `do_put` *C* im Intervall `next`[ `_Iosbase` `_Fill`, `_Pt`) wertet die Funktion stattdessen ( , , , , *C*, 0) aus und überspringt *C*. Wenn *C* jedoch ein Qualifiziererzeichen aus dem Satz `C2` EOQ ist, gefolgt von `next`  =  `do_put`einem `next` `_Iosbase`Zeichen `_Fill` `_Pt`im `C2`Intervall `first`[ , `last`) wertet die Funktion stattdessen ( , , , , , , *C*) aus und überspringt . `C2`

### <a name="example"></a>Beispiel

```cpp
// time_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   t.tm_hour = 5;
   t.tm_min = 30;
   t.tm_sec = 40;
   t.tm_year = 00;
   t.tm_mday = 4;
   t.tm_mon = 6;

   pszPutI.imbue( loc );
   char *pattern = "x: %X %x";
   use_facet <time_put <char> >
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));

      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;

      char strftimebuf[255];
      strftime(&strftimebuf[0], 255, pattern, &t);
      cout << "strftime( ) = " << &strftimebuf[0] << endl;
}
```

```Output
num_put( ) = x: 05:30:40 07/04/00
strftime( ) = x: 05:30:40 07/04/00
```

## <a name="time_puttime_put"></a><a name="time_put"></a>time_put::time_put

Konstruktor für Objekte des Typs `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parameter

*_refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *parameter _Refs* und deren Signifikanz sind:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \>1: Diese Werte sind nicht definiert.

Der Konstruktor initialisiert sein Basisobjekt mit [locale::facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Siehe auch

[\<Gebietsschema>](../standard-library/locale.md)\
[time_base-Klasse](../standard-library/time-base-class.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
