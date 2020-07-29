---
title: Cmapwordyob-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMapWordToOb
- AFXCOLL/CMapWordToOb
- AFXCOLL/CMapWordToOb::CMapWordToOb
- AFXCOLL/CMapWordToOb::GetCount
- AFXCOLL/CMapWordToOb::GetHashTableSize
- AFXCOLL/CMapWordToOb::GetNextAssoc
- AFXCOLL/CMapWordToOb::GetSize
- AFXCOLL/CMapWordToOb::GetStartPosition
- AFXCOLL/CMapWordToOb::HashKey
- AFXCOLL/CMapWordToOb::InitHashTable
- AFXCOLL/CMapWordToOb::IsEmpty
- AFXCOLL/CMapWordToOb::Lookup
- AFXCOLL/CMapWordToOb::LookupKey
- AFXCOLL/CMapWordToOb::RemoveAll
- AFXCOLL/CMapWordToOb::RemoveKey
- AFXCOLL/CMapWordToOb::SetAt
helpviewer_keywords:
- CMapWordToOb [MFC], CMapWordToOb
- CMapWordToOb [MFC], GetCount
- CMapWordToOb [MFC], GetHashTableSize
- CMapWordToOb [MFC], GetNextAssoc
- CMapWordToOb [MFC], GetSize
- CMapWordToOb [MFC], GetStartPosition
- CMapWordToOb [MFC], HashKey
- CMapWordToOb [MFC], InitHashTable
- CMapWordToOb [MFC], IsEmpty
- CMapWordToOb [MFC], Lookup
- CMapWordToOb [MFC], LookupKey
- CMapWordToOb [MFC], RemoveAll
- CMapWordToOb [MFC], RemoveKey
- CMapWordToOb [MFC], SetAt
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
ms.openlocfilehash: f360760bb5c04400ed77ef49c5968f8e9e7a6e59
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222991"
---
# <a name="cmapwordtoob-class"></a>Cmapwordyob-Klasse

Unterstützt Zuordnungen von `CObject` -Zeigern mit 16-Bit-Wörtern als Schlüssel.

## <a name="syntax"></a>Syntax

```
class CMapWordToOb : public CObject
```

## <a name="members"></a>Member

Die Member-Funktionen von `CMapWordToOb` ähneln den Element Funktionen der Klasse [cmapstringyob](../../mfc/reference/cmapstringtoob-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CMapStringToOb`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. `CString`Wenn ein oder ein **`const`** Zeiger auf **`char`** als Funktionsparameter oder Rückgabewert angezeigt wird, ersetzen Sie Word.

`BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`

Beispielsweise übersetzt zu

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Cmapwordto ob:: cmapwordumob](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Cmapwordchanob:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapwordthob:: gethashtablesize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Bestimmt die aktuelle Anzahl der Elemente in der Hash Tabelle.|
|[Cmapwordto ob:: GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Ruft das nächste Element für die Iteration ab.|
|[Cmapwordto ob:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapwordto ob:: GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[Cmapwordtoob:: hashkey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Berechnet den Hashwert eines angegebenen Schlüssels.|
|[Cmapwordthob:: inithashtable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialisiert die Hash Tabelle.|
|[Cmapwordto ob:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testet auf die leere Zuordnungs Bedingung (keine Elemente).|
|[Cmapwordto ob:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Sucht einen void-Zeiger auf der Grundlage der void-Zeiger Taste. Der Zeiger Wert, nicht die Entität, auf die er verweist, wird für den Schlüssel Vergleich verwendet.|
|[Cmapwordtoob:: lookupkey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.|
|[Cmapwordto ob:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Entfernt alle Elemente aus dieser Zuordnung.|
|[Cmapwordtoob:: removekey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[Cmapwordto ob::](../../mfc/reference/cmapstringtoob-class.md#setat)|Fügt ein Element in die Zuordnung ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Cmapwordto ob::-Operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Fügt ein Element in die Map –-Operator Ersetzung für ein `SetAt` .|

## <a name="remarks"></a>Bemerkungen

`CMapWordToOb`integriert das IMPLEMENT_SERIAL-Makro, um die Serialisierung und das Sichern der zugehörigen Elemente zu unterstützen. Jedes Element wird wiederum serialisiert, wenn eine Karte in einem Archiv gespeichert wird, entweder mit dem überladenen Einfügungs **<<** Operator () oder mit der `Serialize` Member-Funktion.

Wenn Sie ein Dump einzelner Word-Elemente benötigen `CObject` , müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Wenn ein- `CMapWordToOb` Objekt gelöscht wird oder wenn seine Elemente entfernt werden, `CObject` werden die Zeiger entfernt. Die Objekte, auf die durch die Zeiger verwiesen wird, `CObject` werden nicht zerstört.

Weitere Informationen zu finden Sie im `CMapWordToOb` Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToOb`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
