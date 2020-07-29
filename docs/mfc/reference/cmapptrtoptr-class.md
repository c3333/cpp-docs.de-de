---
title: CMapPtrToPtr-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::GetCount
- AFXCOLL/CMapPtrToPtr::GetHashTableSize
- AFXCOLL/CMapPtrToPtr::GetNextAssoc
- AFXCOLL/CMapPtrToPtr::GetSize
- AFXCOLL/CMapPtrToPtr::GetStartPosition
- AFXCOLL/CMapPtrToPtr::HashKey
- AFXCOLL/CMapPtrToPtr::InitHashTable
- AFXCOLL/CMapPtrToPtr::IsEmpty
- AFXCOLL/CMapPtrToPtr::Lookup
- AFXCOLL/CMapPtrToPtr::LookupKey
- AFXCOLL/CMapPtrToPtr::RemoveAll
- AFXCOLL/CMapPtrToPtr::RemoveKey
- AFXCOLL/CMapPtrToPtr::SetAt
helpviewer_keywords:
- CMapPtrToPtr [MFC], CMapPtrToPtr
- CMapPtrToPtr [MFC], GetCount
- CMapPtrToPtr [MFC], GetHashTableSize
- CMapPtrToPtr [MFC], GetNextAssoc
- CMapPtrToPtr [MFC], GetSize
- CMapPtrToPtr [MFC], GetStartPosition
- CMapPtrToPtr [MFC], HashKey
- CMapPtrToPtr [MFC], InitHashTable
- CMapPtrToPtr [MFC], IsEmpty
- CMapPtrToPtr [MFC], Lookup
- CMapPtrToPtr [MFC], LookupKey
- CMapPtrToPtr [MFC], RemoveAll
- CMapPtrToPtr [MFC], RemoveKey
- CMapPtrToPtr [MFC], SetAt
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
ms.openlocfilehash: f8fc69007d35927daaa7128de1bc0ceb0b44c746
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223043"
---
# <a name="cmapptrtoptr-class"></a>CMapPtrToPtr-Klasse

Unterstützt void-Zeigerzuordnungen mit void-Zeigern als Schlüssel.

## <a name="syntax"></a>Syntax

```
class CMapPtrToPtr : public CObject
```

## <a name="members"></a>Member

Die Member-Funktionen von `CMapPtrToPtr` ähneln den Element Funktionen der Klasse [cmapstringyob](../../mfc/reference/cmapstringtoob-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CMapStringToOb`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. `CObject`Wenn ein Zeiger als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie einen Zeiger auf **`void`** . `CString`Wenn ein oder ein **`const`** Zeiger auf **`char`** als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie einen Zeiger auf **`void`** .

`BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`

Beispielsweise übersetzt zu

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CMapPtrToPtr:: CMapPtrToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CMapPtrToPtr:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[CMapPtrToPtr:: gethashtablesize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Bestimmt die aktuelle Anzahl der Elemente in der Hash Tabelle.|
|[CMapPtrToPtr:: GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Ruft das nächste Element für die Iteration ab.|
|[CMapPtrToPtr:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[CMapPtrToPtr:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[CMapPtrToPtr:: hashkey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Berechnet den Hashwert eines angegebenen Schlüssels.|
|[CMapPtrToPtr:: inithashtable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialisiert die Hash Tabelle.|
|[CMapPtrToPtr:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testet auf die leere Zuordnungs Bedingung (keine Elemente).|
|[CMapPtrToPtr:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Sucht einen void-Zeiger auf der Grundlage der void-Zeiger Taste. Der Zeiger Wert, nicht die Entität, auf die er verweist, wird für den Schlüssel Vergleich verwendet.|
|[CMapPtrToPtr:: lookupkey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.|
|[CMapPtrToPtr:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Entfernt alle Elemente aus dieser Zuordnung.|
|[CMapPtrToPtr:: removekey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[CMapPtrToPtr::](../../mfc/reference/cmapstringtoob-class.md#setat)|Fügt ein Element in die Zuordnung ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CMapPtrToPtr::-Operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Fügt ein Element in die Map –-Operator Ersetzung für ein `SetAt` .|

## <a name="remarks"></a>Bemerkungen

`CMapPtrToPtr`integriert das IMPLEMENT_DYNAMIC Makro, um den Lauf Zeittyp Zugriff zu unterstützen und auf ein-Objekt zu sichern `CDumpContext` . Wenn Sie ein Dump einzelner Kartenelemente (Zeiger Werte) benötigen, müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Zeiger-zu-Zeiger-Zuordnungen können nicht serialisiert werden.

Wenn ein `CMapPtrToPtr`-Objekt gelöscht wird oder dessen Elemente entfernt werden, werden nur die Zeiger, und nicht die Entitäten, auf die sie verweisen, entfernt.

Weitere Informationen zu finden Sie im `CMapPtrToPtr` Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToPtr`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
