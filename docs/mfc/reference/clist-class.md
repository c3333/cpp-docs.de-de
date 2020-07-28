---
title: CLIST-Klasse
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
ms.openlocfilehash: 7ba85445e3aba1df853d7d3666c92fdabdfa3970
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182875"
---
# <a name="clist-class"></a>CLIST-Klasse

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
|[CLIST:: CLIST](#clist)|Erstellt eine leere geordnete Liste.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CLIST:: AddHead](#addhead)|Fügt ein Element (oder alle Elemente in einer anderen Liste) zum Anfang der Liste hinzu (erstellt einen neuen Kopf).|
|[CLIST:: AddTail](#addtail)|Fügt ein Element (oder alle Elemente in einer anderen Liste) zum Ende der Liste hinzu (führt ein neues Ende aus).|
|[CLIST:: Find](#find)|Ruft die Position eines Elements ab, das durch einen Zeiger Wert angegeben wird.|
|[CLIST:: FindIndex](#findindex)|Ruft die Position eines Elements ab, das durch einen NULL basierten Index angegeben wird.|
|[CLIST:: GetAt](#getat)|Ruft das Element an einer angegebenen Position ab.|
|[CLIST:: GetCount](#getcount)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CLIST:: gezeige AD](#gethead)|Gibt das Head-Element der Liste zurück (darf nicht leer sein).|
|[CLIST:: getheiadposition](#getheadposition)|Gibt die Position des Head-Elements der Liste zurück.|
|[CLIST:: GetNext](#getnext)|Ruft das nächste Element für die Iteration ab.|
|[CLIST:: GetPrev](#getprev)|Ruft das vorherige Element für die Iteration ab.|
|[CLIST:: GetSize](#getsize)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CLIST:: gettail](#gettail)|Gibt das Tail-Element der Liste zurück (darf nicht leer sein).|
|[CLIST:: gettailposition](#gettailposition)|Gibt die Position des Tail-Elements der Liste zurück.|
|[CLIST:: InsertAfter](#insertafter)|Fügt ein neues Element nach einer angegebenen Position ein.|
|[CList::InsertBefore](#insertbefore)|Fügt ein neues Element vor einer angegebenen Position ein.|
|[CLIST:: IsEmpty](#isempty)|Testet auf die leere Listen Bedingung (keine Elemente).|
|[CLIST:: RemoveAll](#removeall)|Entfernt alle Elemente aus dieser Liste.|
|[CLIST:: RemoveAt](#removeat)|Entfernt ein Element aus dieser Liste, das durch die Position angegeben wird.|
|[CLIST:: RemoveHead](#removehead)|Entfernt das Element am Anfang der Liste.|
|[CLIST:: removetail](#removetail)|Entfernt das Element aus dem Ende der Liste.|
|[CLIST::](#setat)|Legt das Element an einer angegebenen Position fest.|

#### <a name="parameters"></a>Parameter

*TYPE*<br/>
Der Typ des in der Liste gespeicherten Objekts.

*ARG_TYPE*<br/>
Der Typ, der zum Verweisen auf in der Liste gespeicherte Objekte verwendet wird. Kann ein Verweis sein.

## <a name="remarks"></a>Bemerkungen

`CList`Listen Verhalten sich wie doppelt verknüpfte Listen.

Eine Variable vom Typ Position ist ein Schlüssel für die Liste. Sie können eine Positions Variable als Iterator verwenden, um eine Liste sequenziell und als Lesezeichen zu durchlaufen, um einen Ort zu speichern. Eine Position ist jedoch nicht mit einem Index identisch.

Das Einfügen von Elementen ist am Listen Kopf am Ende und an einer bekannten Position sehr schnell. Eine sequenzielle Suche ist erforderlich, um ein Element nach Wert oder Index zu suchen. Diese Suche kann langsam sein, wenn die Liste lang ist.

Wenn Sie ein Dump einzelner Elemente in der Liste benötigen, müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Bestimmte Element Funktionen dieser Klasse können globale Hilfsfunktionen aufzurufen, die für die meisten Verwendungen der-Klasse angepasst werden müssen `CList` . Weitere Informationen finden Sie im Abschnitt "Makros und Globals" unter Auflistungs [Klassen](../../mfc/reference/collection-class-helpers.md) -Hilfsprogramme.

Weitere Informationen zur Verwendung von `CList` finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>CLIST:: AddHead

Fügt dem Anfang dieser Liste ein neues Element oder eine Liste von Elementen hinzu.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Parameter

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*newElement*<br/>
Das neue Element.

*pnewlist*<br/>
Ein Zeiger auf eine andere `CList` Liste. Die Elemente in " *pnewlist* " werden der Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den Positionswert des neu eingefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Die Liste kann vor dem Vorgang leer sein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CLIST:: AddTail

Fügt dem Ende dieser Liste ein neues Element oder eine Liste von Elementen hinzu.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>Parameter

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*newElement*<br/>
Das Element, das der Liste hinzugefügt werden soll.

*pnewlist*<br/>
Ein Zeiger auf eine andere `CList` Liste. Die Elemente in " *pnewlist* " werden der Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den Positionswert des neu eingefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Die Liste kann vor dem Vorgang leer sein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>CLIST:: CLIST

Erstellt eine leere geordnete Liste.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parameter

*nblocksize*<br/>
Die Granularität der Speicher Belegung für die Erweiterung der Liste.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste zunimmt, wird der Arbeitsspeicher in Einheiten von *nblocksize* -Einträgen zugeordnet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>CLIST:: Find

Durchsucht die Liste sequenziell, um das erste Element zu finden, das mit dem angegebenen *searchValue*übereinstimmt.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parameter

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*searchValue*<br/>
Der Wert, der in der Liste gefunden werden soll.

*startafter*<br/>
Die Startposition für die Suche. Wenn kein Wert angegeben wird, beginnt die Suche mit dem Head-Element.

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn das Objekt nicht gefunden wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>CLIST:: FindIndex

Verwendet den Wert von *nIndex* als Index in der Liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der null basierte Index des Listen Elements, das gefunden werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn *nIndex* negativ oder zu groß ist.

### <a name="remarks"></a>Bemerkungen

Dabei wird ein sequenzieller Scan von der Spitze der Liste gestartet, wobei das *n*-te Element angehalten wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>CLIST:: GetAt

Ruft das List-Element an einer angegebenen Position ab.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Objekttyp in der Liste angibt.

*gebracht*<br/>
Die Position in der Liste des aufzurufenden Elements.

### <a name="return-value"></a>Rückgabewert

Weitere Informationen finden Sie in der Beschreibung des Rückgabewerts für `GetHead` .

### <a name="remarks"></a>Bemerkungen

`GetAt`Gibt das Element (oder einen Verweis auf das Element) zurück, das einer bestimmten Position zugeordnet ist. Sie ist nicht mit einem Index identisch, und Sie können selbst keinen Positionswert verwenden. Eine Variable vom Typ Position ist ein Schlüssel für die Liste.

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CLIST:: GE-Adposition](#getheadposition).

## <a name="clistgetcount"></a><a name="getcount"></a>CLIST:: GetCount

Ruft die Anzahl der Elemente in dieser Liste ab.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Ein ganzzahliger Wert, der die Element Anzahl enthält.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Methode aufrufen, wird dasselbe Ergebnis wie bei der [CLIST:: GetSize](#getsize) -Methode generiert.

### <a name="example"></a>Beispiel

  Sehen Sie sich das Beispiel für [CLIST:: RemoveHead](#removehead)an.

## <a name="clistgethead"></a><a name="gethead"></a>CLIST:: gezeige AD

Ruft das Head-Element (oder einen Verweis auf das Head-Element) dieser Liste ab.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Objekttyp in der Liste angibt.

### <a name="return-value"></a>Rückgabewert

Wenn die Liste ist **`const`** , wird `GetHead` eine Kopie des Elements an der Spitze der Liste zurückgegeben. Dadurch kann die-Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden, und die Liste wird vor Änderungen geschützt.

Wenn die Liste nicht ist **`const`** , wird `GetHead` ein Verweis auf das Element am Anfang der Liste zurückgegeben. Dies ermöglicht die Verwendung der-Funktion auf beiden Seiten einer Zuweisungsanweisung und ermöglicht so, dass die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die Liste nicht leer ist, bevor Sie aufrufen `GetHead` . Wenn die Liste leer ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert. Verwenden Sie [IsEmpty](#isempty) , um zu überprüfen, ob die Liste Elemente enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CLIST:: getheiadposition

Ruft die Position des Head-Elements dieser Liste ab.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CLIST:: GetNext

Ruft das von *rPosition*identifizierte Listenelement ab und legt dann *rPosition* auf den Positionswert des nächsten Eintrags in der Liste fest.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente in der Liste angibt.

*rPosition zurück*<br/>
Ein Verweis auf einen Positionswert, der von einem Previous- `GetNext` , [geteadposition](#getheadposition)-oder anderen Member-Funktions Aufrufwert zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Wenn die Liste ist **`const`** , wird `GetNext` eine Kopie eines Elements der Liste zurückgegeben. Dadurch kann die-Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden, und die Liste wird vor Änderungen geschützt.

Wenn die Liste nicht ist **`const`** , wird `GetNext` von ein Verweis auf ein Element der Liste zurückgegeben. Dies ermöglicht die Verwendung der-Funktion auf beiden Seiten einer Zuweisungsanweisung und ermöglicht so, dass die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie können `GetNext` in einer Forward-Iterations Schleife verwenden, wenn Sie die ursprüngliche Position mit einem-oder-Aufrufe festlegen `GetHeadPosition` `Find` .

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

Wenn das abgerufene Element das letzte in der Liste ist, wird der neue Wert von `rPosition` auf NULL festgelegt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CLIST:: GetPrev

Ruft das von identifizierte Listenelement ab `rPosition` und legt dann `rPosition` den Positionswert des vorherigen Eintrags in der Liste fest.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente in der Liste angibt.

*rPosition zurück*<br/>
Ein Verweis auf einen Positionswert, der von einem vorherigen `GetPrev` oder einem anderen Element Funktions Aufrufwert zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Wenn die Liste ist **`const`** , wird `GetPrev` eine Kopie des Elements an der Spitze der Liste zurückgegeben. Dadurch kann die-Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden, und die Liste wird vor Änderungen geschützt.

Wenn die Liste nicht ist **`const`** , wird `GetPrev` von ein Verweis auf ein Element der Liste zurückgegeben. Dies ermöglicht die Verwendung der-Funktion auf beiden Seiten einer Zuweisungsanweisung und ermöglicht so, dass die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie können `GetPrev` in einer Reverse-Iterations Schleife verwenden, wenn Sie die ursprüngliche Position mit einem-oder-Aufrufe festlegen `GetTailPosition` `Find` .

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

Wenn das abgerufene Element das erste Element in der Liste ist, wird der neue Wert von *rPosition* auf NULL festgelegt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>CLIST:: GetSize

Gibt die Anzahl der Listenelemente zurück.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Liste.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Liste abzurufen.  Wenn Sie diese Methode aufrufen, wird dasselbe Ergebnis wie bei der [CLIST:: GetCount](#getcount) -Methode generiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>CLIST:: gettail

Ruft den `CObject` Zeiger ab, der das Endelement dieser Liste darstellt.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente in der Liste angibt.

### <a name="return-value"></a>Rückgabewert

Weitere Informationen finden Sie in der Beschreibung des Rückgabewerts für [gezeige AD](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die Liste nicht leer ist, bevor Sie aufrufen `GetTail` . Wenn die Liste leer ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert. Verwenden Sie [IsEmpty](../../mfc/reference/coblist-class.md#isempty) , um zu überprüfen, ob die Liste Elemente enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>CLIST:: gettailposition

Ruft die Position des Tail-Elements dieser Liste ab. NULL, wenn die Liste leer ist.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CLIST:: InsertAfter

Fügt dieser Liste nach dem-Element an der angegebenen Position ein Element hinzu.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*gebracht*<br/>
Ein Positionswert, der von einem vorherigen-,-oder-Element `GetNext` `GetPrev` `Find` Funktions Aufrufwert zurückgegeben

*ARG_TYPE*<br/>
Ein Vorlagen Parameter, der den Typ des Listen Elements angibt.

*newElement*<br/>
Das Element, das der Liste hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der zur Iteration oder zum Abruf von Listenelementen verwendet werden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CLIST:: InsertBefore

Fügt dieser Liste ein Element vor dem Element an der angegebenen Position hinzu.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*gebracht*<br/>
Ein Positionswert, der von einem vorherigen-,-oder-Element `GetNext` `GetPrev` `Find` Funktions Aufrufwert zurückgegeben

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*newElement*<br/>
Das Element, das der Liste hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der zur Iteration oder zum Abruf von Listenelementen verwendet werden kann.

### <a name="remarks"></a>Bemerkungen

Wenn *Position* NULL ist, wird das Element am Anfang der Liste eingefügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CLIST:: IsEmpty

Gibt an, ob diese Liste keine Elemente enthält.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn diese Liste leer ist. andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CLIST:: RemoveAll

Entfernt alle Elemente aus dieser Liste und gibt den zugeordneten Speicher frei.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Wenn die Liste bereits leer ist, wird kein Fehler generiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>CLIST:: RemoveAt

Entfernt das angegebene Element aus der Liste.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parameter

*gebracht*<br/>
Die Position des Elements, das aus der Liste entfernt werden soll.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>CLIST:: RemoveHead

Entfernt das Element am Anfang der Liste und gibt einen Zeiger darauf zurück.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente in der Liste angibt.

### <a name="return-value"></a>Rückgabewert

Das Element, das sich zuvor an der Spitze der Liste befand.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die Liste nicht leer ist, bevor Sie aufrufen `RemoveHead` . Wenn die Liste leer ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert. Verwenden Sie [IsEmpty](#isempty) , um zu überprüfen, ob die Liste Elemente enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>CLIST:: removetail

Entfernt das Element aus dem Ende der Liste und gibt einen Zeiger darauf zurück.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente in der Liste angibt.

### <a name="return-value"></a>Rückgabewert

Das Element, das sich am Ende der Liste befand.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die Liste nicht leer ist, bevor Sie aufrufen `RemoveTail` . Wenn die Liste leer ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert. Verwenden Sie [IsEmpty](#isempty) , um zu überprüfen, ob die Liste Elemente enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CLIST::

Eine Variable vom Typ Position ist ein Schlüssel für die Liste.

```cpp
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Die Position des festzulegenden Elements.

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ des Listenelements angibt (kann ein Verweis sein).

*newElement*<br/>
Das Element, das der Liste hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Sie ist nicht mit einem Index identisch, und Sie können selbst keinen Positionswert verwenden. `SetAt`schreibt das Element an die angegebene Position in der Liste.

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel Sammlung](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Cmap-Klasse](../../mfc/reference/cmap-class.md)<br/>
[CArray-Klasse](../../mfc/reference/carray-class.md)
