---
title: CMapStringToString-Klasse
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
ms.openlocfilehash: 544154569c50369b805ba296aa975849f245d4ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370121"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString-Klasse

Unterstützt Zuordnungen von `CString` -Objekten mit `CString` -Objekten als Schlüssel.

## <a name="syntax"></a>Syntax

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Member

Die Memberfunktionen `CMapStringToString` von ähneln den Memberfunktionen der Klasse [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CMapStringToOb`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. Überall dort, `CObject` wo Sie einen Zeiger als Rückgabewert oder "Output"-Funktionsparameter sehen, ersetzen Sie einen Zeiger durch **char**. Überall dort, `CObject` wo Sie einen Zeiger als "Eingabe"-Funktionsparameter sehen, ersetzen Sie einen Zeiger durch **char**.

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

Beispielsweise übersetzt zu

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Öffentliche Strukturen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMapStringToString::Cpair](#cpair)|Eine geschachtelte Struktur, die einen Schlüsselwert und den Wert des zugeordneten Zeichenfolgenobjekts enthält.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMapstringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMapStringToString::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[CmapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Bestimmt die aktuelle Anzahl von Elementen in der Hashtabelle.|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Ruft das nächste Element zum Iterieren ab.|
|[CMapStringToString::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[CmapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Berechnet den Hashwert eines angegebenen Schlüssels.|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialisiert die Hashtabelle.|
|[CmapStringToString::Isempty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Tests für die Leerzuordnungsbedingung (keine Elemente).|
|[CMapStringToString::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Sucht einen leeren Zeiger basierend auf dem leeren Zeigerschlüssel. Der Zeigerwert, nicht die Entität, auf die er verweist, wird für den Schlüsselvergleich verwendet.|
|[CMapStringToString::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.|
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Ruft einen Zeiger auf `CString` den ersten Inder in der Karte ab.|
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|Ruft einen Zeiger auf `CString` den nächsten zum Iterieren ab.|
|[CMapStringToString::PLookup](#plookup)|Gibt einen Zeiger `CString` auf einen zurück, dessen Wert mit dem angegebenen Wert übereinstimmt.|
|[CMapStringToString::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Entfernt alle Elemente aus dieser Karte.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[CmapstringtoString::Setat](../../mfc/reference/cmapstringtoob-class.md#setat)|Fügt ein Element in die Karte ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMapStringToString::operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Fügt ein Element in die Karte `SetAt`ein – Operatorersetzung für .|

## <a name="remarks"></a>Bemerkungen

`CMapStringToString`enthält das `IMPLEMENT_SERIAL` Makro, um die Serialisierung und das Dumping seiner Elemente zu unterstützen. Jedes Element wird nacheinander serialisiert, wenn eine Karte in einem **<<** Archiv gespeichert wird, entweder mit dem überladenen Einfügeoperator ( ) oder mit der `Serialize` Memberfunktion.

Wenn Sie ein Dump `CString` -  `CString` einzelner Elemente benötigen, müssen Sie die Tiefe des Dumpkontexts auf 1 oder höher festlegen.

Wenn `CMapStringToString` ein Objekt gelöscht wird oder wenn `CString` seine Elemente entfernt werden, werden die Objekte entsprechend entfernt.

Weitere Informationen `CMapStringToString`zu finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxcoll.h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a>CMapStringToString::Cpair

Enthält einen Schlüsselwert und den Wert des zugeordneten Zeichenfolgenobjekts.

### <a name="remarks"></a>Bemerkungen

Dies ist eine geschachtelte Struktur innerhalb der Klasse [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

Die Struktur besteht aus zwei Bereichen:

- `key`Der tatsächliche Wert des Schlüsseltyps.

- `value`Der Wert des zugeordneten Objekts.

Es wird verwendet, um die Rückgabewerte von [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)und [CMapStringToString::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Beispiel

  Ein Beispiel für die Verwendung finden Sie im Beispiel für [CMapStringToString::PLookup](#plookup).

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMapStringToString::PGetFirstAssoc

Gibt den ersten Eintrag des Kartenobjekts zurück.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den ersten Eintrag in der Karte; siehe [CMapStringToString::CPair](#cpair). Wenn die Karte leer ist, ist der Wert NULL.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um einen Zeiger auf das erste Element im Kartenobjekt zurückzugeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a>CMapStringToString::PGetNextAssoc

Ruft das Kartenelement ab, auf das *pAssocRec*zeigt.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Parameter

*pAssoc*<br/>
Verweist auf einen Karteneintrag, der von einem vorherigen [PGetNextAssoc-](#pgetnextassoc) oder [PGetFirstAssoc-Aufruf](#pgetfirstassoc) zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den nächsten Eintrag in der Karte; siehe [CMapStringToString::CPair](#cpair). Wenn das Element das letzte element in der Karte ist, ist der Wert NULL.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um alle Elemente in der Karte zu durchlaufen. Rufen Sie das erste `PGetFirstAssoc` Element mit einem Aufruf von ab, `PGetNextAssoc`und durchlaufen Sie dann die Karte mit aufeinanderfolgenden Aufrufen von .

### <a name="example"></a>Beispiel

  Siehe beispiel für [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a>CMapStringToString::PLookup

Sucht den Wert, der einem bestimmten Schlüssel zugeordnet ist.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Ein Zeiger auf den Schlüssel für das zu durchsuchende Element.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den angegebenen Schlüssel.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um nach einem Kartenelement mit einem Schlüssel zu suchen, der genau mit dem angegebenen Schlüssel übereinstimmt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel COLLECT](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
