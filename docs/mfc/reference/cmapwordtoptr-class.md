---
title: Cmapwordtoptr-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMapWordToPtr
- AFXCOLL/CMapWordToPtr
- AFXCOLL/CMapWordToPtr::CMapWordToPtr
- AFXCOLL/CMapWordToPtr::GetCount
- AFXCOLL/CMapWordToPtr::GetHashTableSize
- AFXCOLL/CMapWordToPtr::GetNextAssoc
- AFXCOLL/CMapWordToPtr::GetSize
- AFXCOLL/CMapWordToPtr::GetStartPosition
- AFXCOLL/CMapWordToPtr::HashKey
- AFXCOLL/CMapWordToPtr::InitHashTable
- AFXCOLL/CMapWordToPtr::IsEmpty
- AFXCOLL/CMapWordToPtr::Lookup
- AFXCOLL/CMapWordToPtr::LookupKey
- AFXCOLL/CMapWordToPtr::RemoveAll
- AFXCOLL/CMapWordToPtr::RemoveKey
- AFXCOLL/CMapWordToPtr::SetAt
helpviewer_keywords:
- CMapWordToPtr [MFC], CMapWordToPtr
- CMapWordToPtr [MFC], GetCount
- CMapWordToPtr [MFC], GetHashTableSize
- CMapWordToPtr [MFC], GetNextAssoc
- CMapWordToPtr [MFC], GetSize
- CMapWordToPtr [MFC], GetStartPosition
- CMapWordToPtr [MFC], HashKey
- CMapWordToPtr [MFC], InitHashTable
- CMapWordToPtr [MFC], IsEmpty
- CMapWordToPtr [MFC], Lookup
- CMapWordToPtr [MFC], LookupKey
- CMapWordToPtr [MFC], RemoveAll
- CMapWordToPtr [MFC], RemoveKey
- CMapWordToPtr [MFC], SetAt
ms.assetid: b204d87f-6427-43e1-93e3-a4b1bb41099f
ms.openlocfilehash: 3374b3123e150a4cac127e30bf7e9a6569371b5c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222978"
---
# <a name="cmapwordtoptr-class"></a>Cmapwordtoptr-Klasse

Unterstützt Zuordnungen von void-Zeigern mit 16-Bit-Wörtern als Schlüssel.

## <a name="syntax"></a>Syntax

```
class CMapWordToPtr : public CObject
```

## <a name="members"></a>Member

Die Member-Funktionen von `CMapWordToPtr` ähneln den Element Funktionen der Klasse [cmapstringyob](../../mfc/reference/cmapstringtoob-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CMapStringToOb`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. `CObject`Wenn ein Zeiger als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie einen Zeiger auf **`void`** . `CString`Wenn ein oder ein **`const`** Zeiger auf **`char`** als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie Word.

`BOOL CMapWordToPtr::Lookup( WORD <key>, void*& <rValue> ) const;`

Beispielsweise übersetzt zu

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Cmapwordtoptr:: cmapwordtoptr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Cmapwordtoptr:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapwordtoptr:: gethashtablesize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Bestimmt die aktuelle Anzahl der Elemente in der Hash Tabelle.|
|[Cmapwordtoptr:: GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Ruft das nächste Element für die Iteration ab.|
|[Cmapwordtoptr:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapwordtoptr:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[Cmapwordtoptr:: hashkey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Berechnet den Hashwert eines angegebenen Schlüssels.|
|[Cmapwordtoptr:: inithashtable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialisiert die Hash Tabelle.|
|[Cmapwordtoptr:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testet auf die leere Zuordnungs Bedingung (keine Elemente).|
|[Cmapwordtoptr:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Sucht einen void-Zeiger auf der Grundlage der void-Zeiger Taste. Der Zeiger Wert, nicht die Entität, auf die er verweist, wird für den Schlüssel Vergleich verwendet.|
|[Cmapwordtoptr:: lookupkey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.|
|[Cmapwordtoptr:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Entfernt alle Elemente aus dieser Zuordnung.|
|[Cmapwordtoptr:: removekey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[Cmapwordtoptr::](../../mfc/reference/cmapstringtoob-class.md#setat)|Fügt ein Element in die Zuordnung ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Cmapwordtoptr::-Operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Fügt ein Element in die Map –-Operator Ersetzung für ein `SetAt` .|

## <a name="remarks"></a>Bemerkungen

`CMapWordToPtr`integriert das IMPLEMENT_DYNAMIC Makro, um den Lauf Zeittyp Zugriff zu unterstützen und auf ein-Objekt zu sichern `CDumpContext` . Wenn Sie ein Abbild einzelner Kartenelemente benötigen, müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Die Zuordnung von Word-zu-Zeiger-Zuordnungen kann nicht serialisiert werden.

Wenn ein `CMapWordToPtr` -Objekt gelöscht wird oder wenn seine Elemente entfernt werden, werden die Wörter und die Zeiger entfernt. Die Entitäten, auf die die Zeiger verweisen, werden nicht entfernt.

Weitere Informationen zu finden Sie im `CMapWordToPtr` Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToPtr`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
