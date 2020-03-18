---
title: messages-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: 704ee2ce40b4026cc066213181c96cf0f744d152
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425430"
---
# <a name="messages-class"></a>messages-Klasse

Die Klassen Vorlage beschreibt ein Objekt, das als Gebiets Schema Aspekt dienen kann, um lokalisierte Nachrichten aus einem Katalog mit internationalisierten Nachrichten für ein bestimmtes Gebiets Schema abzurufen.

Während die Nachrichtenklasse implementiert wird, sind derzeit keine Meldungen vorhanden.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Parameter

*CharType* -\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

## <a name="remarks"></a>Hinweise

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

Dieses Facet öffnet im Grunde einen Katalog von Meldungen, die in der messages_base-Basisklasse definiert sind, ruft die erforderlichen Informationen ab und schließt den Katalog.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[messages](#messages)|Die Meldungsfacet-Konstruktorfunktion.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Zeichentyp, mit dem Meldungen angezeigt werden.|
|[string_type](#string_type)|Ein Typ, der eine Zeichenfolge vom Typ `basic_string` beschreibt, die Zeichen vom Typ `CharType` enthält.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|Beschreibung|
|-|-|
|[close](#close)|Schließt den Meldungskatalog.|
|[do_close](#do_close)|Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog zu schließen.|
|[do_get](#do_get)|Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog abzurufen.|
|[do_open](#do_open)|Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog zu öffnen.|
|[get](#get)|Ruft den Meldungskatalog ab.|
|[open](#open)|Öffnet den Meldungskatalog.|

## <a name="requirements"></a>Voraussetzungen

**Header:** \<Gebiets Schema >

**Namespace:** std

## <a name="char_type"></a> messages::char_type

Ein Zeichentyp, mit dem Meldungen angezeigt werden.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für den Vorlagenparameter **CharType**.

## <a name="close"></a> messages::close

Schließt den Meldungskatalog.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parameter

*_Catval*\
Der zu schließende Katalog.

### <a name="remarks"></a>Hinweise

Die Memberfunktion ruft [do_close](#do_close)(_ *Catval*) auf.

## <a name="do_close"></a> messages::do_close

Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog zu schließen.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parameter

*_Catval*\
Der zu schließende Katalog.

### <a name="remarks"></a>Hinweise

Die geschützte Member-Funktion schließt den Message Catalog- *_Catval*, der von einem früheren [Do_open](#do_open)geöffnet werden muss.

*_Catval* muss aus einem vorher geöffneten Katalog abgerufen werden, der nicht geschlossen wurde.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [close](#close), mit dem `do_close` aufgerufen wird.

## <a name="do_get"></a> messages::do_get

Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog abzurufen.

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parameter

*_Catval*\
Der Identifikationswert, der den zu suchenden Katalog angibt.

*_Set*\
Der erste identifizierte, der zum Finden einer Meldung in einem Meldungskatalog verwendet wird.

*_Message*\
Der zweite identifizierte, der zum Finden einer Meldung in einem Meldungskatalog verwendet wird.

*_Dfault*\
Die Zeichenfolge, die zurückgegeben werden soll, wenn ein Fehler auftritt.

### <a name="return-value"></a>Rückgabewert

Bei einem Fehler wird eine Kopie der *_Dfault* zurückgegeben. Andernfalls gibt er eine Kopie einer angegebenen Meldungssequenz zurück.

### <a name="remarks"></a>Hinweise

Die geschützte Member-Funktion versucht, eine Nachrichten Sequenz aus dem *_Catval*des Nachrichten Katalogs abzurufen. Dabei können *_Set*, *_message*und *_Dfault* verwendet werden.

### <a name="example"></a>Beispiel

Informationen hierzu finden Sie im Beispiel für [get](#get), das `do_get` aufruft.

## <a name="do_open"></a> messages::do_open

Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog zu öffnen.

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parameter

*_Catname*\
Der Name des zu suchenden Katalogs.

*_Loc*\
Das Gebietsschema, nach dem im Katalog gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Er gibt einen Wert zurück, der bei einem Fehler kleiner als null ist. Andernfalls kann der Rückgabewert als erstes Argument bei einem späteren Aufruf an [get](#get) verwendet werden.

### <a name="remarks"></a>Hinweise

Die geschützte Member-Funktion versucht, einen Meldungs Katalog zu öffnen, dessen Name *_Catname*ist. Dabei kann das Gebiets Schema *_Loc* verwendet werden.

Der Rückgabewert sollte als Argument für einen späteren Aufruf an [close](#close) verwendet werden.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [open](#open), mit dem `do_open` aufgerufen wird.

## <a name="get"></a> messages::get

Ruft den Meldungskatalog ab.

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parameter

*_Catval*\
Der Identifikationswert, der den zu suchenden Katalog angibt.

*_Set*\
Der erste identifizierte, der zum Finden einer Meldung in einem Meldungskatalog verwendet wird.

*_Message*\
Der zweite identifizierte, der zum Finden einer Meldung in einem Meldungskatalog verwendet wird.

*_Dfault*\
Die Zeichenfolge, die zurückgegeben werden soll, wenn ein Fehler auftritt.

### <a name="return-value"></a>Rückgabewert

Bei einem Fehler wird eine Kopie der *_Dfault* zurückgegeben. Andernfalls gibt er eine Kopie einer angegebenen Meldungssequenz zurück.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [do_get](#do_get)(`_Catval`,`_Set``_Message`,`_Dfault`) zurück.

## <a name="messages"></a> messages::messages

Die Meldungsfacet-Konstruktorfunktion.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parameter

*_Refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

*_Locname*\
Der Name des Gebietsschemas.

### <a name="remarks"></a>Hinweise

Die möglichen Werte für den *_Refs* -Parameter und ihre Bedeutung lauten:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \> 1: diese Werte sind nicht definiert.

Direkte Beispiele sind nicht möglich, da der Destruktor geschützt ist.

Der Konstruktor initialisiert sein Basisobjekt mit **locale::** [facet](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="open"></a> messages::open

Öffnet den Meldungskatalog.

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parameter

*_Catname*\
Der Name des zu suchenden Katalogs.

*_Loc*\
Das Gebietsschema, nach dem im Katalog gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Er gibt einen Wert zurück, der bei einem Fehler kleiner als null ist. Andernfalls kann der Rückgabewert als erstes Argument bei einem späteren Aufruf an [get](#get) verwendet werden.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [do_open](#do_open)(`_Catname`,`_Loc`) zurück.

## <a name="string_type"></a> messages::string_type

Ein Typ, der eine Zeichenfolge vom Typ `basic_string` beschreibt, die Zeichen vom Typ `CharType` enthält.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung von Klassen Vorlagen [basic_string](../standard-library/basic-string-class.md) , deren Objekte Kopien der Nachrichten Sequenzen speichern können.

## <a name="see-also"></a>Siehe auch

[\<locale>](../standard-library/locale.md)\
[messages_base-Klasse](../standard-library/messages-base-class.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
