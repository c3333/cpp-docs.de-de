---
title: Cmapptrto Word-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
- AFXCOLL/CMapPtrToWord::CMapPtrToWord
- AFXCOLL/CMapPtrToWord::GetCount
- AFXCOLL/CMapPtrToWord::GetHashTableSize
- AFXCOLL/CMapPtrToWord::GetNextAssoc
- AFXCOLL/CMapPtrToWord::GetSize
- AFXCOLL/CMapPtrToWord::GetStartPosition
- AFXCOLL/CMapPtrToWord::HashKey
- AFXCOLL/CMapPtrToWord::InitHashTable
- AFXCOLL/CMapPtrToWord::IsEmpty
- AFXCOLL/CMapPtrToWord::Lookup
- AFXCOLL/CMapPtrToWord::LookupKey
- AFXCOLL/CMapPtrToWord::RemoveAll
- AFXCOLL/CMapPtrToWord::RemoveKey
- AFXCOLL/CMapPtrToWord::SetAt
helpviewer_keywords:
- CMapPtrToWord [MFC], CMapPtrToWord
- CMapPtrToWord [MFC], GetCount
- CMapPtrToWord [MFC], GetHashTableSize
- CMapPtrToWord [MFC], GetNextAssoc
- CMapPtrToWord [MFC], GetSize
- CMapPtrToWord [MFC], GetStartPosition
- CMapPtrToWord [MFC], HashKey
- CMapPtrToWord [MFC], InitHashTable
- CMapPtrToWord [MFC], IsEmpty
- CMapPtrToWord [MFC], Lookup
- CMapPtrToWord [MFC], LookupKey
- CMapPtrToWord [MFC], RemoveAll
- CMapPtrToWord [MFC], RemoveKey
- CMapPtrToWord [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
ms.openlocfilehash: 254659a9f00ff7c0c27174cfbea4c131993150f3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223030"
---
# <a name="cmapptrtoword-class"></a>Cmapptrto Word-Klasse

Unterstützt Zuordnungen von 16-Bit-Wörtern mit void-Zeigern als Schlüssel.

## <a name="syntax"></a>Syntax

```
class CMapPtrToWord : public CObject
```

## <a name="members"></a>Member

Die Member-Funktionen von `CMapPtrToWord` ähneln den Element Funktionen der Klasse [cmapstringyob](../../mfc/reference/cmapstringtoob-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CMapStringToOb`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. `CObject`Wenn ein Zeiger als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie Word. `CString`Wenn ein oder ein **`const`** Zeiger auf **`char`** als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie einen Zeiger auf **`void`** .

`BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`

Beispielsweise übersetzt zu

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Cmapptrto Word:: cmapptrwortzword](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Cmapptrto Word:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapptrto Word:: gethashtablesize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Bestimmt die aktuelle Anzahl der Elemente in der Hash Tabelle.|
|[Cmapptrto Word:: GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Ruft das nächste Element für die Iteration ab.|
|[Cmapptrto Word:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapptrto Word:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[Cmapptrtoword:: hashkey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Berechnet den Hashwert eines angegebenen Schlüssels.|
|[Cmapptrto Word:: inithashtable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialisiert die Hash Tabelle.|
|[Cmapptrto Word:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testet auf die leere Zuordnungs Bedingung (keine Elemente).|
|[Cmapptryword:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Sucht einen void-Zeiger auf der Grundlage der void-Zeiger Taste. Der Zeiger Wert, nicht die Entität, auf die er verweist, wird für den Schlüssel Vergleich verwendet.|
|[Cmapptrtoword:: lookupkey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.|
|[Cmapptrto Word:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Entfernt alle Elemente aus dieser Zuordnung.|
|[Cmapptrtoword:: removekey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[Cmapptrto Word::](../../mfc/reference/cmapstringtoob-class.md#setat)|Fügt ein Element in die Zuordnung ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Cmapptrto Word::-Operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Fügt ein Element in die Map –-Operator Ersetzung für ein `SetAt` .|

## <a name="remarks"></a>Bemerkungen

`CMapWordToPtr`integriert das IMPLEMENT_DYNAMIC Makro, um den Lauf Zeittyp Zugriff zu unterstützen und auf ein-Objekt zu sichern `CDumpContext` . Wenn Sie ein Abbild einzelner Kartenelemente benötigen, müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Zeiger-zu-Wort-Zuordnungen können nicht serialisiert werden.

Wenn ein `CMapPtrToWord` -Objekt gelöscht wird oder wenn seine Elemente entfernt werden, werden die Zeiger und die Wörter entfernt. Die Entitäten, auf die die Schlüssel Zeiger verweisen, werden nicht entfernt.

Weitere Informationen zu finden Sie im `CMapPtrToWord` Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToWord`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
