---
title: Cmapstringdestring-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToString::CMapStringToString
- AFXCOLL/CMapStringToString::GetCount
- AFXCOLL/CMapStringToString::GetHashTableSize
- AFXCOLL/CMapStringToString::GetNextAssoc
- AFXCOLL/CMapStringToString::GetSize
- AFXCOLL/CMapStringToString::GetStartPosition
- AFXCOLL/CMapStringToString::HashKey
- AFXCOLL/CMapStringToString::InitHashTable
- AFXCOLL/CMapStringToString::IsEmpty
- AFXCOLL/CMapStringToString::Lookup
- AFXCOLL/CMapStringToString::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToString::RemoveAll
- AFXCOLL/CMapStringToString::RemoveKey
- AFXCOLL/CMapStringToString::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToString [MFC], CMapStringToString
- CMapStringToString [MFC], GetCount
- CMapStringToString [MFC], GetHashTableSize
- CMapStringToString [MFC], GetNextAssoc
- CMapStringToString [MFC], GetSize
- CMapStringToString [MFC], GetStartPosition
- CMapStringToString [MFC], HashKey
- CMapStringToString [MFC], InitHashTable
- CMapStringToString [MFC], IsEmpty
- CMapStringToString [MFC], Lookup
- CMapStringToString [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToString [MFC], RemoveAll
- CMapStringToString [MFC], RemoveKey
- CMapStringToString [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: a2ffcf7ce7ee6eccc56382501a5969ddec6c9e22
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442593"
---
# <a name="cmapstringtostring-class"></a>Cmapstringdestring-Klasse

Unterstützt Zuordnungen von `CString` -Objekten mit `CString` -Objekten als Schlüssel.

## <a name="syntax"></a>Syntax

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Members

Die Element Funktionen von `CMapStringToString` ähneln den Element Funktionen der Klasse [cmapstringyob](../../mfc/reference/cmapstringtoob-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CMapStringToOb`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. Wenn ein `CObject` Zeiger als Rückgabewert oder Output-Funktionsparameter angezeigt wird, ersetzen Sie einen Zeiger auf **char**. Wenn Sie einen `CObject` Zeiger als Eingabe Funktionsparameter sehen, ersetzen Sie einen Zeiger auf **char**.

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

Beispielsweise übersetzt zu

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Öffentliche Strukturen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMapStringToString:: cpair](#cpair)|Eine-Struktur, die einen Schlüsselwert und den Wert des zugeordneten Zeichen folgen Objekts enthält.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmapstringdestring:: cmapstringdestring](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmapstringdestring:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapstringdestring:: gethashtablesize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Bestimmt die aktuelle Anzahl der Elemente in der Hash Tabelle.|
|[Cmapstringdestring:: GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Ruft das nächste Element für die Iteration ab.|
|[Cmapstringdestring:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapstringdestring:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[CMapStringToString:: hashkey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Berechnet den Hashwert eines angegebenen Schlüssels.|
|[Cmapstringdestring:: inithashtable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialisiert die Hash Tabelle.|
|[Cmapstringdestring:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testet auf die leere Zuordnungs Bedingung (keine Elemente).|
|[Cmapstringdestring:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Sucht einen void-Zeiger auf der Grundlage der void-Zeiger Taste. Der Zeiger Wert, nicht die Entität, auf die er verweist, wird für den Schlüssel Vergleich verwendet.|
|[CMapStringToString:: lookupkey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.|
|[Cmapstringdestring::P getfirstassoc](#pgetfirstassoc)|Ruft einen Zeiger auf den ersten `CString` in der Karte ab.|
|[Cmapstringdestring::P GetNextAssoc](#pgetnextassoc)|Ruft einen Zeiger auf den nächsten `CString` zum Iterieren ab.|
|[Cmapstringdestring::P Suche](#plookup)|Gibt einen Zeiger auf einen `CString` zurück, dessen Wert mit dem angegebenen Wert übereinstimmt.|
|[Cmapstringdestring:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Entfernt alle Elemente aus dieser Zuordnung.|
|[CMapStringToString:: removekey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[Cmapstringdestring::](../../mfc/reference/cmapstringtoob-class.md#setat)|Fügt ein Element in die Zuordnung ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmapstringdestring:: Operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Fügt ein Element in die Map –-Operator Ersetzung für `SetAt`ein.|

## <a name="remarks"></a>Bemerkungen

`CMapStringToString` enthält das `IMPLEMENT_SERIAL`-Makro, um die Serialisierung und das Absichern der zugehörigen Elemente zu unterstützen. Jedes Element wird wiederum serialisiert, wenn eine Karte in einem Archiv gespeichert wird, entweder mit dem überladenen Einfügungs Operator ( **<<** ) oder mit der `Serialize` Member-Funktion.

Wenn Sie ein Abbild einzelner `CString`- `CString` Elemente benötigen, müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Wenn ein `CMapStringToString` Objekt gelöscht wird oder wenn seine Elemente entfernt werden, werden die `CString` Objekte nach Bedarf entfernt.

Weitere Informationen zu `CMapStringToString`finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

##  <a name="cpair"></a>CMapStringToString:: cpair

Enthält einen Schlüsselwert und den Wert des zugeordneten Zeichen folgen Objekts.

### <a name="remarks"></a>Bemerkungen

Dies ist eine geschachtelte Struktur innerhalb der Klasse " [cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)".

Die Struktur besteht aus zwei Feldern:

- `key` den tatsächlichen Wert des Schlüssel Typs.

- `value` den Wert des zugeordneten-Objekts.

Sie wird zum Speichern der Rückgabewerte aus [cmapstringdestring::P Lookup](#plookup), [cmapstringdestring::P getfirstassoc](#pgetfirstassoc)und [cmapstringdestring::P GetNextAssoc](#pgetnextassoc)verwendet.

### <a name="example"></a>Beispiel

  Ein Beispiel für die Verwendung finden Sie im Beispiel für [cmapstringdestring::P Lookup](#plookup).

##  <a name="pgetfirstassoc"></a>Cmapstringdestring::P getfirstassoc

Gibt den ersten Eintrag des Map-Objekts zurück.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den ersten Eintrag in der Zuordnung. Weitere Informationen finden Sie unter [CMapStringToString:: cpair](#cpair). Wenn die Zuordnung leer ist, ist der Wert NULL.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, um einen Zeiger auf das erste Element im Map-Objekt zurückzugeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

##  <a name="pgetnextassoc"></a>Cmapstringdestring::P GetNextAssoc

Ruft das Kartenelement ab, auf das von *passokrec*verwiesen wird.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Parameter

*passoc*<br/>
Verweist auf einen Karten Eintrag, der von einem vorherigen [pgetnextassoc](#pgetnextassoc) -oder [pgetfirstassoc](#pgetfirstassoc) -Befehl zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den nächsten Eintrag in der Zuordnung. Weitere Informationen finden Sie unter [CMapStringToString:: cpair](#cpair). Wenn das Element das letzte in der Zuordnung ist, ist der Wert NULL.

### <a name="remarks"></a>Bemerkungen

Ruft diese Methode auf, um alle Elemente in der Zuordnung zu durchlaufen. Rufen Sie das erste Element mit einem Aufruf von `PGetFirstAssoc` ab, und durchlaufen Sie dann die Zuordnung mit aufeinander folgenden Aufrufen `PGetNextAssoc`.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [cmapstringdestring::P getfirstassoc](#pgetfirstassoc).

##  <a name="plookup"></a>Cmapstringdestring::P Suche

Sucht den Wert, der einem angegebenen Schlüssel zugeordnet ist.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Ein Zeiger auf den Schlüssel für das Element, nach dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den angegebenen Schlüssel.

### <a name="remarks"></a>Bemerkungen

Ruft diese Methode auf, um nach einem Kartenelement mit einem Schlüssel zu suchen, der exakt mit dem angegebenen Schlüssel übereinstimmt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel Sammlung](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
