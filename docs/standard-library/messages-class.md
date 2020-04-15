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
ms.openlocfilehash: deb9eaedba3c99bb2fcb8399ac412ccedb11545f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375920"
---
# <a name="messages-class"></a>messages-Klasse

Die Klassenvorlage beschreibt ein Objekt, das als Gebietsschema dienen kann, um lokalisierte Nachrichten aus einem Katalog von internationalisierten Nachrichten für ein bestimmtes Gebietsschema abzurufen.

Während die Nachrichtenklasse implementiert wird, sind derzeit keine Meldungen vorhanden.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Parameter

*Chartype*\
Der Typ, der innerhalb eines Programms zum Codieren von Zeichen in einem Gebietsschema verwendet wird.

## <a name="remarks"></a>Bemerkungen

Wie bei jedem Gebietsschemafacet hat die statische Objekt-ID einen anfänglichen gespeicherten Wert von NULL. Beim ersten Versuch, auf den gespeicherten Wert zuzugreifen, wird ein eindeutiger positiver Wert in **id** gespeichert.

Dieses Facet öffnet im Grunde einen Katalog von Meldungen, die in der messages_base-Basisklasse definiert sind, ruft die erforderlichen Informationen ab und schließt den Katalog.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[Nachrichten](#messages)|Die Meldungsfacet-Konstruktorfunktion.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Ein Zeichentyp, mit dem Meldungen angezeigt werden.|
|[string_type](#string_type)|Ein Typ, der eine Zeichenfolge vom Typ `basic_string` beschreibt, die Zeichen vom Typ `CharType` enthält.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Schließen](#close)|Schließt den Meldungskatalog.|
|[do_close](#do_close)|Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog zu schließen.|
|[do_get](#do_get)|Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog abzurufen.|
|[do_open](#do_open)|Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog zu öffnen.|
|[get](#get)|Ruft den Meldungskatalog ab.|
|[open](#open)|Öffnet den Meldungskatalog.|

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="messageschar_type"></a><a name="char_type"></a>Nachrichten::char_type

Ein Zeichentyp, mit dem Meldungen angezeigt werden.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter **CharType** dar.

## <a name="messagesclose"></a><a name="close"></a>Nachrichten::schließen

Schließt den Meldungskatalog.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parameter

*_Catval*\
Der zu schließende Katalog.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ruft [do_close](#do_close)(_ *Catval*) auf.

## <a name="messagesdo_close"></a><a name="do_close"></a>Nachrichten::do_close

Eine virtuelle Funktion, die aufgerufen wird, um den Meldungskatalog zu schließen.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parameter

*_Catval*\
Der zu schließende Katalog.

### <a name="remarks"></a>Bemerkungen

Die geschützte Memberfunktion schließt den Nachrichtenkatalog *_Catval*, der durch einen früheren Aufruf [von do_open](#do_open)geöffnet worden sein muss.

*_Catval* muss aus einem vorher geöffneten Katalog abgerufen werden, der nicht geschlossen wurde.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [close](#close), mit dem `do_close` aufgerufen wird.

## <a name="messagesdo_get"></a><a name="do_get"></a>Meldungen::do_get

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

*_set*\
Der erste identifizierte, der zum Finden einer Meldung in einem Meldungskatalog verwendet wird.

*_Message*\
Der zweite identifizierte, der zum Finden einer Meldung in einem Meldungskatalog verwendet wird.

*_Dfault*\
Die Zeichenfolge, die zurückgegeben werden soll, wenn ein Fehler auftritt.

### <a name="return-value"></a>Rückgabewert

Es gibt eine Kopie von *_Dfault* bei einem Fehler zurück. Andernfalls gibt er eine Kopie einer angegebenen Meldungssequenz zurück.

### <a name="remarks"></a>Bemerkungen

Die geschützte Memberfunktion versucht, eine Nachrichtensequenz aus dem Nachrichtenkatalog *_Catval*abzuverweisen. Sie kann *dabei _Set*, *_Message*und *_Dfault* nutzen.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [get](#get), mit dem `do_get` aufgerufen wird.

## <a name="messagesdo_open"></a><a name="do_open"></a>Nachrichten::do_open

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

### <a name="remarks"></a>Bemerkungen

Die geschützte Memberfunktion versucht, einen Nachrichtenkatalog zu öffnen, dessen Name *_Catname*lautet. Sie kann dabei die *Gebietsschema-_Loc*

Der Rückgabewert sollte als Argument für einen späteren Aufruf an [close](#close) verwendet werden.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [open](#open), mit dem `do_open` aufgerufen wird.

## <a name="messagesget"></a><a name="get"></a>Nachrichten::get

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

*_set*\
Der erste identifizierte, der zum Finden einer Meldung in einem Meldungskatalog verwendet wird.

*_Message*\
Der zweite identifizierte, der zum Finden einer Meldung in einem Meldungskatalog verwendet wird.

*_Dfault*\
Die Zeichenfolge, die zurückgegeben werden soll, wenn ein Fehler auftritt.

### <a name="return-value"></a>Rückgabewert

Es gibt eine Kopie von *_Dfault* bei einem Fehler zurück. Andernfalls gibt er eine Kopie einer angegebenen Meldungssequenz zurück.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion [do_get](#do_get)gibt `_Catval` `_Set`do_get `_Message` `_Dfault`zurück ( , , , ).

## <a name="messagesmessages"></a><a name="messages"></a>Nachrichten::Nachrichten

Die Meldungsfacet-Konstruktorfunktion.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parameter

*_refs*\
Integerwert, der zum Angeben des Speicherverwaltungstyps für das Objekt verwendet wird.

*_Locname*\
Der Name des Gebietsschemas.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für den *parameter _Refs* und deren Signifikanz sind:

- 0: Die Lebensdauer des Objekts wird von den Gebietsschemas verwaltet, in denen es enthalten ist.

- 1: Die Lebensdauer des Objekts muss manuell verwaltet werden.

- \>1: Diese Werte sind nicht definiert.

Direkte Beispiele sind nicht möglich, da der Destruktor geschützt ist.

Der Konstruktor initialisiert sein Basisobjekt mit **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="messagesopen"></a><a name="open"></a>Meldungen::öffnen

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

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `_Catname` `_Loc` [do_open](#do_open)zurück ( , ).

## <a name="messagesstring_type"></a><a name="string_type"></a>Nachrichten::string_type

Ein Typ, der eine Zeichenfolge vom Typ `basic_string` beschreibt, die Zeichen vom Typ `CharType` enthält.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung von [Klassenvorlagenbasic_string](../standard-library/basic-string-class.md) deren Objekte Kopien der Nachrichtensequenzen speichern können.

## <a name="see-also"></a>Siehe auch

[\<Gebietsschema>](../standard-library/locale.md)\
[messages_base-Klasse](../standard-library/messages-base-class.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
