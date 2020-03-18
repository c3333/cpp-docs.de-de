---
title: CStringList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CStringList::CStringList
- AFXCOLL/CStringList::AddHead
- AFXCOLL/CStringList::AddTail
- AFXCOLL/CStringList::Find
- AFXCOLL/CStringList::FindIndex
- AFXCOLL/CStringList::GetAt
- AFXCOLL/CStringList::GetCount
- AFXCOLL/CStringList::GetHead
- AFXCOLL/CStringList::GetHeadPosition
- AFXCOLL/CStringList::GetNext
- AFXCOLL/CStringList::GetPrev
- AFXCOLL/CStringList::GetSize
- AFXCOLL/CStringList::GetTail
- AFXCOLL/CStringList::GetTailPosition
- AFXCOLL/CStringList::InsertAfter
- AFXCOLL/CStringList::InsertBefore
- AFXCOLL/CStringList::IsEmpty
- AFXCOLL/CStringList::RemoveAll
- AFXCOLL/CStringList::RemoveAt
- AFXCOLL/CStringList::RemoveHead
- AFXCOLL/CStringList::RemoveTail
- AFXCOLL/CStringList::SetAt
helpviewer_keywords:
- CStringList [MFC], CStringList
- CStringList [MFC], AddHead
- CStringList [MFC], AddTail
- CStringList [MFC], Find
- CStringList [MFC], FindIndex
- CStringList [MFC], GetAt
- CStringList [MFC], GetCount
- CStringList [MFC], GetHead
- CStringList [MFC], GetHeadPosition
- CStringList [MFC], GetNext
- CStringList [MFC], GetPrev
- CStringList [MFC], GetSize
- CStringList [MFC], GetTail
- CStringList [MFC], GetTailPosition
- CStringList [MFC], InsertAfter
- CStringList [MFC], InsertBefore
- CStringList [MFC], IsEmpty
- CStringList [MFC], RemoveAll
- CStringList [MFC], RemoveAt
- CStringList [MFC], RemoveHead
- CStringList [MFC], RemoveTail
- CStringList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
ms.openlocfilehash: 9eb7a713fc02cd3e51135d1985a41688d4c885d9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447558"
---
# <a name="cstringlist-class"></a>CStringList-Klasse

Unterstützt Listen von `CString` -Objekten.

## <a name="syntax"></a>Syntax

```
class CStringList : public CObject
```

## <a name="members"></a>Members

Die Element Funktionen von `CStringList` ähneln den Member-Funktionen der Klasse [CObList](../../mfc/reference/coblist-class.md). Aufgrund dieser Ähnlichkeit können Sie die `CObList`-Referenzdokumentation für Memberfunktionsbesonderheiten verwenden. Wenn ein `CObject` Zeiger als Rückgabewert angezeigt wird, ersetzen Sie einen `CString` (kein `CString` Zeiger). Wenn Sie einen `CObject` Zeiger als Funktionsparameter sehen, ersetzen Sie einen `LPCTSTR`.

`CObject*& CObList::GetHead() const;`

Beispielsweise übersetzt zu

`CString& CStringList::GetHead() const;`

and

`POSITION AddHead( CObject* <newElement> );`

wird übersetzt in

`POSITION AddHead( LPCTSTR <newElement> );`

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStringList:: CStringList](../../mfc/reference/coblist-class.md#coblist)|Erstellt eine leere Liste.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStringList:: AddHead](../../mfc/reference/coblist-class.md#addhead)|Fügt ein Element (oder alle Elemente in einer anderen Liste) zum Anfang der Liste hinzu (erstellt einen neuen Kopf).|
|[CStringList:: AddTail](../../mfc/reference/coblist-class.md#addtail)|Fügt ein Element (oder alle Elemente in einer anderen Liste) zum Ende der Liste hinzu (führt ein neues Ende aus).|
|[CStringList:: Find](../../mfc/reference/coblist-class.md#find)|Ruft die Position eines Elements ab, das durch einen Zeiger Wert angegeben wird.|
|[CStringList:: FindIndex](../../mfc/reference/coblist-class.md#findindex)|Ruft die Position eines Elements ab, das durch einen NULL basierten Index angegeben wird.|
|[CStringList:: GetAt](../../mfc/reference/coblist-class.md#getat)|Ruft das Element an einer angegebenen Position ab.|
|[CStringList:: GetCount](../../mfc/reference/coblist-class.md#getcount)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CStringList:: gezeige AD](../../mfc/reference/coblist-class.md#gethead)|Gibt das Head-Element der Liste zurück (darf nicht leer sein).|
|[CStringList:: GE-Adposition](../../mfc/reference/coblist-class.md#getheadposition)|Gibt die Position des Head-Elements der Liste zurück.|
|[CStringList:: GetNext](../../mfc/reference/coblist-class.md#getnext)|Ruft das nächste Element für die Iteration ab.|
|[CStringList:: GetPrev](../../mfc/reference/coblist-class.md#getprev)|Ruft das vorherige Element für die Iteration ab.|
|[CStringList:: GetSize](../../mfc/reference/coblist-class.md#getsize)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CStringList:: gettail](../../mfc/reference/coblist-class.md#gettail)|Gibt das Tail-Element der Liste zurück (darf nicht leer sein).|
|[CStringList:: gettailposition](../../mfc/reference/coblist-class.md#gettailposition)|Gibt die Position des Tail-Elements der Liste zurück.|
|[CStringList:: InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Fügt ein neues Element nach einer angegebenen Position ein.|
|[CStringList:: InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Fügt ein neues Element vor einer angegebenen Position ein.|
|[CStringList:: IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Testet auf die leere Listen Bedingung (keine Elemente).|
|[CStringList:: RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Entfernt alle Elemente aus dieser Liste.|
|[CStringList:: RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Entfernt ein Element aus dieser Liste, das durch die Position angegeben wird.|
|[CStringList:: RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Entfernt das Element am Anfang der Liste.|
|[CStringList:: removetail](../../mfc/reference/coblist-class.md#removetail)|Entfernt das Element aus dem Ende der Liste.|
|[CStringList::](../../mfc/reference/coblist-class.md#setat)|Legt das Element an einer angegebenen Position fest.|

## <a name="remarks"></a>Bemerkungen

Alle Vergleiche werden nach Wert durchgeführt. das bedeutet, dass die Zeichen in der Zeichenfolge anstelle der Adressen der Zeichen folgen verglichen werden.

`CStringList` enthält das IMPLEMENT_SERIAL-Makro, um die Serialisierung und das Absichern der zugehörigen Elemente zu unterstützen. Wenn eine Liste von `CString` Objekten in einem Archiv gespeichert wird, entweder mit einem überladenen einfügeoperator oder mit der `Serialize` Member-Funktion, wird jedes `CString` Element nacheinander serialisiert.

Wenn Sie ein Abbild einzelner `CString` Elemente benötigen, müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Weitere Informationen zur Verwendung von `CStringList`finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel Sammlung](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
