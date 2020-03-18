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
ms.openlocfilehash: 71d79f9f57be2cdfe16c526bd50173a8ec3c5829
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442573"
---
# <a name="cmapwordtoptr-class"></a>Cmapwordtoptr-Klasse

Unterstützt Zuordnungen von void-Zeigern mit 16-Bit-Wörtern als Schlüssel.

## <a name="syntax"></a>Syntax

```
class CMapWordToPtr : public CObject
```

## <a name="members"></a>Members

Die Element Funktionen von `CMapWordToPtr` ähneln den Element Funktionen der Klasse [cmapstringyob](../../mfc/reference/cmapstringtoob-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CMapStringToOb`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. Wenn ein `CObject` Zeiger als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie einen Zeiger auf " **void**". Wenn Sie einen `CString` oder einen **Konstanten** Zeiger auf **char** als Funktionsparameter oder Rückgabewert sehen, ersetzen Sie Word.

`BOOL CMapWordToPtr::Lookup( WORD <key>, void*& <rValue> ) const;`

Beispielsweise übersetzt zu

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmapwordtoptr:: cmapwordtoptr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
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

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmapwordtoptr:: Operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Fügt ein Element in die Map –-Operator Ersetzung für `SetAt`ein.|

## <a name="remarks"></a>Bemerkungen

`CMapWordToPtr` enthält das IMPLEMENT_DYNAMIC-Makro, um den Lauf Zeittyp Zugriff und das Absichern eines `CDumpContext` Objekts zu unterstützen. Wenn Sie ein Abbild einzelner Kartenelemente benötigen, müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Die Zuordnung von Word-zu-Zeiger-Zuordnungen kann nicht serialisiert werden.

Wenn ein `CMapWordToPtr` Objekt gelöscht wird oder wenn seine Elemente entfernt werden, werden die Wörter und die Zeiger entfernt. Die Entitäten, auf die die Zeiger verweisen, werden nicht entfernt.

Weitere Informationen zu `CMapWordToPtr`finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToPtr`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
