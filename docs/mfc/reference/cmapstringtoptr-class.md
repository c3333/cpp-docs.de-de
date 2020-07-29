---
title: Cmapstringtoptr-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMapStringToPtr
- AFXCOLL/CMapStringToPtr
- AFXCOLL/CMapStringToPtr::CMapStringToPtr
- AFXCOLL/CMapStringToPtr::GetCount
- AFXCOLL/CMapStringToPtr::GetHashTableSize
- AFXCOLL/CMapStringToPtr::GetNextAssoc
- AFXCOLL/CMapStringToPtr::GetSize
- AFXCOLL/CMapStringToPtr::GetStartPosition
- AFXCOLL/CMapStringToPtr::HashKey
- AFXCOLL/CMapStringToPtr::InitHashTable
- AFXCOLL/CMapStringToPtr::IsEmpty
- AFXCOLL/CMapStringToPtr::Lookup
- AFXCOLL/CMapStringToPtr::LookupKey
- AFXCOLL/CMapStringToPtr::RemoveAll
- AFXCOLL/CMapStringToPtr::RemoveKey
- AFXCOLL/CMapStringToPtr::SetAt
helpviewer_keywords:
- CMapStringToPtr [MFC], CMapStringToPtr
- CMapStringToPtr [MFC], GetCount
- CMapStringToPtr [MFC], GetHashTableSize
- CMapStringToPtr [MFC], GetNextAssoc
- CMapStringToPtr [MFC], GetSize
- CMapStringToPtr [MFC], GetStartPosition
- CMapStringToPtr [MFC], HashKey
- CMapStringToPtr [MFC], InitHashTable
- CMapStringToPtr [MFC], IsEmpty
- CMapStringToPtr [MFC], Lookup
- CMapStringToPtr [MFC], LookupKey
- CMapStringToPtr [MFC], RemoveAll
- CMapStringToPtr [MFC], RemoveKey
- CMapStringToPtr [MFC], SetAt
ms.assetid: 1ac11143-eb0a-4511-a662-2df0d1d9005b
ms.openlocfilehash: 26a606d5813a68b55d8fc555025ccef270a25766
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223017"
---
# <a name="cmapstringtoptr-class"></a>Cmapstringtoptr-Klasse

Unterstützt Zuordnungen von void-Zeigern mit `CString` -Objekten als Schlüssel.

## <a name="syntax"></a>Syntax

```
class CMapStringToPtr : public CObject
```

## <a name="members"></a>Member

Die Member-Funktionen von `CMapStringToPtr` ähneln den Element Funktionen der Klasse [cmapstringyob](../../mfc/reference/cmapstringtoob-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CMapStringToOb`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. `CObject`Wenn ein Zeiger als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie einen Zeiger auf **`void`** .

`BOOL CMapStringToPtr::Lookup( LPCTSTR <key>, void*& <rValue> ) const;`

Beispielsweise übersetzt zu

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Cmapstringtoptr:: cmapstringtoptr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Cmapstringtoptr:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapstringtoptr:: gethashtablesize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Bestimmt die aktuelle Anzahl der Elemente in der Hash Tabelle.|
|[Cmapstringtoptr:: GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Ruft das nächste Element für die Iteration ab.|
|[Cmapstringtoptr:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapstringtoptr:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[Cmapstringtoptr:: hashkey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Berechnet den Hashwert eines angegebenen Schlüssels.|
|[Cmapstringtoptr:: inithashtable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialisiert die Hash Tabelle.|
|[Cmapstringtoptr:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testet auf die leere Zuordnungs Bedingung (keine Elemente).|
|[Cmapstringtoptr:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Sucht einen void-Zeiger auf der Grundlage der void-Zeiger Taste. Der Zeiger Wert, nicht die Entität, auf die er verweist, wird für den Schlüssel Vergleich verwendet.|
|[Cmapstringtoptr:: lookupkey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.|
|[Cmapstringtoptr:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Entfernt alle Elemente aus dieser Zuordnung.|
|[Cmapstringtoptr:: removekey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[Cmapstringtoptr::](../../mfc/reference/cmapstringtoob-class.md#setat)|Fügt ein Element in die Zuordnung ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Cmapstringtoptr::-Operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Fügt ein Element in die Map –-Operator Ersetzung für ein `SetAt` .|

## <a name="remarks"></a>Bemerkungen

`CMapStringToPtr`integriert das IMPLEMENT_DYNAMIC Makro, um den Lauf Zeittyp Zugriff zu unterstützen und auf ein-Objekt zu sichern `CDumpContext` . Wenn Sie ein Abbild einzelner Kartenelemente benötigen, müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Zeichen folgen-zu-Zeiger-Zuordnungen können nicht serialisiert werden.

Wenn ein `CMapStringToPtr` -Objekt gelöscht wird oder wenn seine Elemente entfernt werden, `CString` werden die Schlüssel Objekte und die Wörter entfernt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToPtr`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
