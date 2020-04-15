---
title: CList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: 253cf12033af497115ad600e457630ae834cc69c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372236"
---
# <a name="clist-class"></a>CList-Klasse

Unterstützt sortierte Listen mit Objekten, die nicht eindeutig sein müssen, und auf die sequenziell oder über den Wert zugegriffen werden kann.

## <a name="syntax"></a>Syntax

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CList::CList](#clist)|Erstellt eine leere geordnete Liste.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CList::AddHead](#addhead)|Fügt dem Kopf der Liste ein Element (oder alle Elemente in einer anderen Liste) hinzu (macht einen neuen Kopf).|
|[CList::AddTail](#addtail)|Fügt ein Element (oder alle Elemente in einer anderen Liste) am Ende der Liste hinzu (macht einen neuen Schwanz).|
|[CList::Suchen](#find)|Ruft die Position eines Elements ab, das durch den Zeigerwert angegeben wird.|
|[CList::FindIndex](#findindex)|Ruft die Position eines Elements ab, das durch einen nullbasierten Index angegeben wird.|
|[CList::GetAt](#getat)|Ruft das Element an einer bestimmten Position ab.|
|[CList::GetCount](#getcount)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CList::GetHead](#gethead)|Gibt das Kopfelement der Liste zurück (kann nicht leer sein).|
|[CList::GetHeadPosition](#getheadposition)|Gibt die Position des Kopfelements der Liste zurück.|
|[CList::GetNext](#getnext)|Ruft das nächste Element zum Iterieren ab.|
|[CList::GetPrev](#getprev)|Ruft das vorherige Element zum Iterieren ab.|
|[CList::GetSize](#getsize)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CList::GetTail](#gettail)|Gibt das Tail-Element der Liste zurück (kann nicht leer sein).|
|[CList::GetTailPosition](#gettailposition)|Gibt die Position des Schwanzelements der Liste zurück.|
|[CList::InsertAfter](#insertafter)|Fügt ein neues Element nach einer bestimmten Position ein.|
|[CList::InsertBefore](#insertbefore)|Fügt ein neues Element vor einer bestimmten Position ein.|
|[CList::IsEmpty](#isempty)|Tests für die leere Listenbedingung (keine Elemente).|
|[CList::Alle entfernen](#removeall)|Entfernt alle Elemente aus dieser Liste.|
|[CList::RemoveAt](#removeat)|Entfernt ein Element aus dieser Liste, das durch Position angegeben wird.|
|[CList::RemoveHead](#removehead)|Entfernt das Element vom Kopf der Liste.|
|[CList::RemoveTail](#removetail)|Entfernt das Element vom Ende der Liste.|
|[CList::SetAt](#setat)|Legt das Element an einer bestimmten Position fest.|

#### <a name="parameters"></a>Parameter

*TYP*<br/>
Typ des in der Liste gespeicherten Objekts.

*ARG_TYPE*<br/>
Typ, der zum Verweisen auf in der Liste gespeicherte Objekte verwendet wird. Kann eine Referenz sein.

## <a name="remarks"></a>Bemerkungen

`CList`Listen verhalten sich wie doppelt verknüpfte Listen.

Eine Variable vom Typ POSITION ist ein Schlüssel für die Liste. Sie können eine POSITION-Variable als Iterator verwenden, um eine Liste sequenziell und als Lesezeichen für einen Ort zu durchlaufen. Eine Position ist jedoch nicht identisch mit einem Index.

Das Einfügen von Elementen erfolgt sehr schnell am Listenkopf, am Schwanz und an einer bekannten POSITION. Eine sequenzielle Suche ist erforderlich, um ein Element nach Wert oder Index zu suchen. Diese Suche kann langsam sein, wenn die Liste lang ist.

Wenn Sie ein Dump einzelner Elemente in der Liste benötigen, müssen Sie die Tiefe des Dumpkontexts auf 1 oder höher festlegen.

Bestimmte Memberfunktionen dieser Klasse rufen globale Hilfsfunktionen auf, die `CList` für die meisten Verwendungen der Klasse angepasst werden müssen. Weitere Informationen finden Sie unter [Sammlungsklassenhilfen](../../mfc/reference/collection-class-helpers.md) im Abschnitt "Makros und Globale".

Weitere Informationen zur `CList`Verwendung finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Anforderungen

**Header:** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>CList::AddHead

Fügt dem Kopf dieser Liste ein neues Element oder eine Liste von Elementen hinzu.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Parameter

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*Newelement*<br/>
Das neue Element.

*pNewList*<br/>
Ein Zeiger auf `CList` eine andere Liste. Die Elemente in *pNewList* werden dieser Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den POSITION-Wert des neu eingefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Die Liste kann vor dem Vorgang leer sein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CList::AddTail

Fügt ein neues Element oder eine Liste von Elementen am Ende dieser Liste hinzu.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>Parameter

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*Newelement*<br/>
Das Element, das der Liste hinzugefügt werden soll.

*pNewList*<br/>
Ein Zeiger auf `CList` eine andere Liste. Die Elemente in *pNewList* werden dieser Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den POSITION-Wert des neu eingefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Die Liste kann vor dem Vorgang leer sein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>CList::CList

Erstellt eine leere geordnete Liste.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parameter

*nBlockSize*<br/>
Die Speicherzuweisungsgranularität zum Erweitern der Liste.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste wächst, wird der Speicher in Einheiten von *nBlockSize-Einträgen* zugewiesen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>CList::Suchen

Durchsucht die Liste sequenziell, um das erste Element zu finden, das dem angegebenen *searchValue*entspricht.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parameter

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*searchValue*<br/>
Der Wert, der in der Liste zu finden ist.

*startAfter*<br/>
Die Startposition für die Suche. Wenn kein Wert angegeben ist, beginnt die Suche mit dem Head-Element.

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn das Objekt nicht gefunden wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>CList::FindIndex

Verwendet den Wert von *nIndex* als Index in der Liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der nullbasierte Index des zu findenden Listenelements.

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn *nIndex* negativ oder zu groß ist.

### <a name="remarks"></a>Bemerkungen

Es startet einen sequenziellen Scan vom Kopf der Liste und stoppt auf dem *n*th-Element.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>CList::GetAt

Ruft das Listenelement an einer bestimmten Position ab.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Objekttyp in der Liste angibt.

*Position*<br/>
Die Position in der Liste des zu erhaltenden Elements.

### <a name="return-value"></a>Rückgabewert

Siehe die Rückgabewertbeschreibung für `GetHead`.

### <a name="remarks"></a>Bemerkungen

`GetAt`gibt das Element (oder einen Verweis auf das Element) zurück, das einer bestimmten Position zugeordnet ist. Es ist nicht dasselbe wie ein Index, und Sie können nicht selbst mit einem POSITION-Wert arbeiten. Eine Variable vom Typ POSITION ist ein Schlüssel für die Liste.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CList::GetHeadPosition](#getheadposition).

## <a name="clistgetcount"></a><a name="getcount"></a>CList::GetCount

Ruft die Anzahl der Elemente in dieser Liste ab.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Ganzzahlwert, der die Elementanzahl enthält.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Methode aufrufen, wird das gleiche Ergebnis wie die [CList::GetSize-Methode](#getsize) generiert.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CList::RemoveHead](#removehead).

## <a name="clistgethead"></a><a name="gethead"></a>CList::GetHead

Ruft das Head-Element (oder einen Verweis auf das Kopfelement) dieser Liste ab.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Objekttyp in der Liste angibt.

### <a name="return-value"></a>Rückgabewert

Wenn die **const**Liste `GetHead` const ist, gibt eine Kopie des Elements am Anfang der Liste zurück. Dadurch kann die Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt die Liste vor Änderungen.

Wenn die Liste **const**nicht `GetHead` const ist, gibt ein Verweis auf das Element am Anfang der Liste zurück. Dadurch kann die Funktion auf beiden Seiten einer Zuweisungsanweisung verwendet werden und so können die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `GetHead`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](#isempty) um zu überprüfen, ob die Liste Elemente enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CList::GetHeadPosition

Ruft die Position des Kopfelements dieser Liste ab.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CList::GetNext

Ruft das durch *rPosition*identifizierte Listenelement ab und legt *dann rPosition* auf den POSITION-Wert des nächsten Eintrags in der Liste fest.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der Elemente in der Liste angibt.

*Rposition*<br/>
Ein Verweis auf einen POSITION-Wert, der von einem vorherigen `GetNext`, [GetHeadPosition](#getheadposition)- oder einem anderen Memberfunktionsaufruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Wenn die **const**Liste `GetNext` const ist, gibt eine Kopie eines Elements der Liste zurück. Dadurch kann die Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt die Liste vor Änderungen.

Wenn die Liste **const**nicht `GetNext` const ist, gibt ein Verweis auf ein Element der Liste zurück. Dadurch kann die Funktion auf beiden Seiten einer Zuweisungsanweisung verwendet werden und so können die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie können `GetNext` in einer Vorwärtsiterationsschleife verwendet werden, `GetHeadPosition` wenn `Find`Sie die Anfangsposition mit einem Aufruf von oder festlegen.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Wenn das abgerufene Element das letzte in der `rPosition` Liste ist, wird der neue Wert von auf NULL gesetzt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CList::GetPrev

Ruft das von `rPosition`identifizierte `rPosition` Listenelement ab und legt dann den POSITION-Wert des vorherigen Eintrags in der Liste fest.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der Elemente in der Liste angibt.

*Rposition*<br/>
Ein Verweis auf einen POSITION-Wert, der von einem vorherigen `GetPrev` oder anderen Memberfunktionsaufruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Wenn die **const**Liste `GetPrev` const ist, gibt eine Kopie des Elements am Anfang der Liste zurück. Dadurch kann die Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt die Liste vor Änderungen.

Wenn die Liste **const**nicht `GetPrev` const ist, gibt ein Verweis auf ein Element der Liste zurück. Dadurch kann die Funktion auf beiden Seiten einer Zuweisungsanweisung verwendet werden und so können die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie können `GetPrev` in einer umgekehrten Iterationsschleife verwenden, `GetTailPosition` wenn `Find`Sie die Anfangsposition mit einem Aufruf von oder festlegen.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Wenn das abgerufene Element das erste in der Liste ist, wird der neue Wert von *rPosition* auf NULL gesetzt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>CList::GetSize

Gibt die Anzahl der Listenelemente zurück.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Liste.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Liste abzurufen.  Wenn Sie diese Methode aufrufen, wird das gleiche Ergebnis wie die [CList::GetCount-Methode](#getcount) generiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>CList::GetTail

Ruft `CObject` den Zeiger ab, der das Endelement dieser Liste darstellt.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der Elemente in der Liste angibt.

### <a name="return-value"></a>Rückgabewert

Siehe die Rückgabewertbeschreibung für [GetHead](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `GetTail`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) um zu überprüfen, ob die Liste Elemente enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>CList::GetTailPosition

Ruft die Position des Tail-Elements dieser Liste ab. NULL, wenn die Liste leer ist.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CList::InsertAfter

Fügt dieser Liste ein Element nach dem Element an der angegebenen Position hinzu.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*Position*<br/>
Ein POSITION-Wert, `GetNext`der `GetPrev`von `Find` einem vorherigen , oder Memberfunktionsaufruf zurückgegeben wird.

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt.

*Newelement*<br/>
Das Element, das der Liste hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der zur Iteration oder zum Abruf von Listenelementen verwendet werden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CList::InsertBefore

Fügt dieser Liste ein Element vor dem Element an der angegebenen Position hinzu.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*Position*<br/>
Ein POSITION-Wert, `GetNext`der `GetPrev`von `Find` einem vorherigen , oder Memberfunktionsaufruf zurückgegeben wird.

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*Newelement*<br/>
Das Element, das der Liste hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der zur Iteration oder zum Abruf von Listenelementen verwendet werden kann.

### <a name="remarks"></a>Bemerkungen

Wenn *Position* NULL ist, wird das Element an der Spitze der Liste eingefügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList::IsEmpty

Gibt an, ob diese Liste keine Elemente enthält.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn diese Liste leer ist; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CList::Alle entfernen

Entfernt alle Elemente aus dieser Liste und gibt den zugeordneten Speicher frei.

```
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Es wird kein Fehler generiert, wenn die Liste bereits leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>CList::RemoveAt

Entfernt das angegebene Element aus dieser Liste.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parameter

*Position*<br/>
Die Position des Elements, das aus der Liste entfernt werden soll.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>CList::RemoveHead

Entfernt das Element vom Kopf der Liste und gibt einen Zeiger darauf zurück.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der Elemente in der Liste angibt.

### <a name="return-value"></a>Rückgabewert

Das Element, das zuvor an der Spitze der Liste stand.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `RemoveHead`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](#isempty) um zu überprüfen, ob die Liste Elemente enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>CList::RemoveTail

Entfernt das Element vom Ende der Liste und gibt einen Zeiger darauf zurück.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der Elemente in der Liste angibt.

### <a name="return-value"></a>Rückgabewert

Das Element, das sich am Ende der Liste befand.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `RemoveTail`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](#isempty) um zu überprüfen, ob die Liste Elemente enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CList::SetAt

Eine Variable vom Typ POSITION ist ein Schlüssel für die Liste.

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Die POSITION des festzulegenden Elements.

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*Newelement*<br/>
Das Element, das der Liste hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Es ist nicht dasselbe wie ein Index, und Sie können nicht selbst mit einem POSITION-Wert arbeiten. `SetAt`schreibt das Element an die angegebene Position in der Liste.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel COLLECT](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CMap-Klasse](../../mfc/reference/cmap-class.md)<br/>
[CArray-Klasse](../../mfc/reference/carray-class.md)
