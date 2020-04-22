---
title: CTypedPtrList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
ms.openlocfilehash: 9f4899d4470903a4145cc171579e4b251b984f95
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747185"
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList-Klasse

Stellt einen typsicheren Wrapper für Objekte der Klasse `CPtrList`bereit.

## <a name="syntax"></a>Syntax

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>Parameter

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeigerlistenklasse; muss eine Zeigerlistenklasse `CObList` sein `CPtrList`( oder ).

*TYP*<br/>
Typ der elemente, die in der Basisklassenliste gespeichert sind.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTypedPtrList::AddHead](#addhead)|Fügt dem Kopf der Liste ein Element (oder alle Elemente in einer anderen Liste) hinzu (macht einen neuen Kopf).|
|[CTypedPtrList::AddTail](#addtail)|Fügt ein Element (oder alle Elemente in einer anderen Liste) am Ende der Liste hinzu (macht einen neuen Schwanz).|
|[CTypedPtrList::GetAt](#getat)|Ruft das Element an einer bestimmten Position ab.|
|[CTypedPtrList::GetHead](#gethead)|Gibt das Kopfelement der Liste zurück (kann nicht leer sein).|
|[CTypedPtrList::GetNext](#getnext)|Ruft das nächste Element zum Iterieren ab.|
|[CTypedPtrList::GetPrev](#getprev)|Ruft das vorherige Element zum Iterieren ab.|
|[CTypedPtrList::GetTail](#gettail)|Gibt das Tail-Element der Liste zurück (kann nicht leer sein).|
|[CTypedPtrList::RemoveHead](#removehead)|Entfernt das Element vom Kopf der Liste.|
|[CTypedPtrList::RemoveTail](#removetail)|Entfernt das Element vom Ende der Liste.|
|[CTypedPtrList::SetAt](#setat)|Legt das Element an einer bestimmten Position fest.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie `CTypedPtrList` anstelle `CObList` `CPtrList`von oder verwenden, hilft die C++-Typüberprüfungsfunktion, Fehler zu beseitigen, die durch nicht übereinstimmende Zeigertypen verursacht werden.

Darüber hinaus `CTypedPtrList` führt der Wrapper einen Großteil des Castings `CPtrList`durch, das erforderlich wäre, wenn Sie oder verwenden. `CObList`

Da `CTypedPtrList` alle Funktionen inline sind, wirkt sich die Verwendung dieser Vorlage nicht wesentlich auf die Größe oder Geschwindigkeit des Codes aus.

Von listen `CObList` abgeleitete Listen können serialisiert werden, aber die von `CPtrList` nicht abgeleiteten.

Wenn ein `CTypedPtrList`-Objekt gelöscht wird oder dessen Elemente entfernt werden, werden nur die Zeiger, und nicht die Entitäten, auf die sie verweisen, entfernt.

Weitere Informationen zur `CTypedPtrList`Verwendung finden Sie in den Artikeln [Sammlungen](../../mfc/collections.md) und [Vorlagenbasierte Klassen](../../mfc/template-based-classes.md).

## <a name="example"></a>Beispiel

In diesem Beispiel `CTypedPtrList`wird eine Instanz von erstellt, ein Objekt hinzugefügt, die Liste auf dem Datenträger serialisiert und anschließend das Objekt gelöscht:

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxtempl.h

## <a name="ctypedptrlistaddhead"></a><a name="addhead"></a>CTypedPtrList::AddHead

Diese Memberfunktion `BASE_CLASS`ruft **::AddHead**auf.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Typ der elemente, die in der Basisklassenliste gespeichert sind.

*Newelement*<br/>
Der Objektzeiger, der dieser Liste hinzugefügt werden soll. Ein NULL-Wert ist zulässig.

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeigerlistenklasse; muss eine Zeigerlistenklasse sein ( [CObList](../../mfc/reference/coblist-class.md) oder [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Ein Zeiger auf ein anderes [CTypedPtrList-Objekt.](../../mfc/reference/ctypedptrlist-class.md) Die Elemente in *pNewList* werden dieser Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den POSITION-Wert des neu eingefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Die erste Version fügt ein neues Element vor dem Kopf der Liste hinzu. Die zweite Version fügt eine weitere Liste von Elementen vor dem Kopf hinzu.

## <a name="ctypedptrlistaddtail"></a><a name="addtail"></a>CTypedPtrList::AddTail

Diese Memberfunktion `BASE_CLASS`ruft **::AddTail**auf.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Typ der elemente, die in der Basisklassenliste gespeichert sind.

*Newelement*<br/>
Der Objektzeiger, der dieser Liste hinzugefügt werden soll. Ein NULL-Wert ist zulässig.

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeigerlistenklasse; muss eine Zeigerlistenklasse sein ( [CObList](../../mfc/reference/coblist-class.md) oder [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Ein Zeiger auf ein anderes [CTypedPtrList-Objekt.](../../mfc/reference/ctypedptrlist-class.md) Die Elemente in *pNewList* werden dieser Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den POSITION-Wert des neu eingefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Die erste Version fügt ein neues Element nach dem Ende der Liste hinzu. Die zweite Version fügt eine weitere Liste von Elementen nach dem Ende der Liste hinzu.

## <a name="ctypedptrlistgetat"></a><a name="getat"></a>CTypedPtrList::GetAt

Eine Variable vom Typ POSITION ist ein Schlüssel für die Liste.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der in der Liste gespeicherten Elemente angibt.

*position*<br/>
Ein POSITION-Wert, `GetHeadPosition` der `Find` von einem vorherigen oder Memberfunktionsaufruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Wenn auf die Liste über einen `const CTypedPtrList`Zeiger `GetAt` auf eine zugegriffen wird, wird ein Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt so die Liste vor Änderungen.

Wenn direkt oder über einen Zeiger auf `CTypedPtrList`eine `GetAt` auf die Liste zugegriffen wird, wird ein Verweis auf einen Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion auf beiden Seiten einer Zuweisungsanweisung verwendet werden und so können die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Es ist nicht dasselbe wie ein Index, und Sie können nicht selbst mit einem POSITION-Wert arbeiten. `GetAt`ruft den `CObject` Zeiger ab, der einer bestimmten Position zugeordnet ist.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Diese Inlinefunktion `BASE_CLASS`ruft **::GetAt**auf.

## <a name="ctypedptrlistgethead"></a><a name="gethead"></a>CTypedPtrList::GetHead

Ruft den Zeiger ab, der das Kopfelement dieser Liste darstellt.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der in der Liste gespeicherten Elemente angibt.

### <a name="return-value"></a>Rückgabewert

Wenn auf die Liste über einen `const CTypedPtrList`Zeiger `GetHead` auf eine zugegriffen wird, wird ein Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt so die Liste vor Änderungen.

Wenn direkt oder über einen Zeiger auf `CTypedPtrList`eine `GetHead` auf die Liste zugegriffen wird, wird ein Verweis auf einen Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion auf beiden Seiten einer Zuweisungsanweisung verwendet werden und so können die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `GetHead`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) um zu überprüfen, ob die Liste Elemente enthält.

## <a name="ctypedptrlistgetnext"></a><a name="getnext"></a>CTypedPtrList::GetNext

Ruft das durch *rPosition*identifizierte Listenelement ab und legt *dann rPosition* auf den POSITION-Wert des nächsten Eintrags in der Liste fest.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der in dieser Liste enthaltenen Elemente angibt.

*Rposition*<br/>
Ein Verweis auf einen POSITION-Wert, der von einem vorherigen `GetNext`, `GetHeadPosition`oder einem anderen Memberfunktionsaufruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Wenn auf die Liste über einen `const CTypedPtrList`Zeiger `GetNext` auf eine zugegriffen wird, wird ein Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt so die Liste vor Änderungen.

Wenn direkt oder über einen Zeiger auf `CTypedPtrList`eine `GetNext` auf die Liste zugegriffen wird, wird ein Verweis auf einen Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion auf beiden Seiten einer Zuweisungsanweisung verwendet werden und so können die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie können `GetNext` in einer Vorwärtsiterationsschleife verwenden, wenn `GetHeadPosition` Sie die Ausgangsposition mit einem Aufruf von oder [CPtrList::Find](../../mfc/reference/coblist-class.md#find)festlegen.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Wenn das abgerufene Element das letzte in der Liste ist, wird der neue Wert von *rPosition* auf NULL gesetzt.

Es ist möglich, ein Element während einer Iteration zu entfernen. Siehe Beispiel für [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).

## <a name="ctypedptrlistgetprev"></a><a name="getprev"></a>CTypedPtrList::GetPrev

Ruft das durch *rPosition*identifizierte Listenelement ab und legt *dann rPosition* auf den POSITION-Wert des vorherigen Eintrags in der Liste fest.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der in dieser Liste enthaltenen Elemente angibt.

*Rposition*<br/>
Ein Verweis auf einen POSITION-Wert, der von einem vorherigen `GetPrev` oder anderen Memberfunktionsaufruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Wenn auf die Liste über einen `const CTypedPtrList`Zeiger `GetPrev` auf eine zugegriffen wird, wird ein Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt so die Liste vor Änderungen.

Wenn direkt oder über einen Zeiger auf `CTypedPtrList`eine `GetPrev` auf die Liste zugegriffen wird, wird ein Verweis auf einen Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion auf beiden Seiten einer Zuweisungsanweisung verwendet werden und so können die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie können `GetPrev` in einer umgekehrten Iterationsschleife verwenden, `GetTailPosition` wenn `Find`Sie die Anfangsposition mit einem Aufruf von oder festlegen.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Wenn das abgerufene Element das erste in der Liste ist, wird der neue Wert von *rPosition* auf NULL gesetzt.

## <a name="ctypedptrlistgettail"></a><a name="gettail"></a>CTypedPtrList::GetTail

Ruft den Zeiger ab, der das Kopfelement dieser Liste darstellt.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der in der Liste gespeicherten Elemente angibt.

### <a name="return-value"></a>Rückgabewert

Wenn auf die Liste über einen `const CTypedPtrList`Zeiger `GetTail` auf eine zugegriffen wird, wird ein Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt so die Liste vor Änderungen.

Wenn direkt oder über einen Zeiger auf `CTypedPtrList`eine `GetTail` auf die Liste zugegriffen wird, wird ein Verweis auf einen Zeiger des Typs zurückgegeben, der durch den Vorlagenparameter *TYPE*angegeben wird. Dadurch kann die Funktion auf beiden Seiten einer Zuweisungsanweisung verwendet werden und so können die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `GetTail`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) um zu überprüfen, ob die Liste Elemente enthält.

## <a name="ctypedptrlistremovehead"></a><a name="removehead"></a>CTypedPtrList::RemoveHead

Entfernt das Element vom Kopf der Liste und gibt es zurück.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der in der Liste gespeicherten Elemente angibt.

### <a name="return-value"></a>Rückgabewert

Der Zeiger zuvor an der Spitze der Liste. Dieser Zeiger ist vom Typ, der durch den Vorlagenparameter *TYPE*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `RemoveHead`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) um zu überprüfen, ob die Liste Elemente enthält.

## <a name="ctypedptrlistremovetail"></a><a name="removetail"></a>CTypedPtrList::RemoveTail

Entfernt das Element vom Ende der Liste und gibt es zurück.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der in der Liste gespeicherten Elemente angibt.

### <a name="return-value"></a>Rückgabewert

Der Zeiger zuvor am Ende der Liste. Dieser Zeiger ist vom Typ, der durch den Vorlagenparameter *TYPE*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `RemoveTail`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) um zu überprüfen, ob die Liste Elemente enthält.

## <a name="ctypedptrlistsetat"></a><a name="setat"></a>CTypedPtrList::SetAt

Diese Memberfunktion `BASE_CLASS`ruft **::SetAt**auf.

```cpp
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Die POSITION des festzulegenden Elements.

*TYP*<br/>
Typ der elemente, die in der Basisklassenliste gespeichert sind.

*Newelement*<br/>
Der Objektzeiger, der in die Liste geschrieben werden soll.

### <a name="remarks"></a>Bemerkungen

Eine Variable vom Typ POSITION ist ein Schlüssel für die Liste. Es ist nicht dasselbe wie ein Index, und Sie können nicht selbst mit einem POSITION-Wert arbeiten. `SetAt`schreibt den Objektzeiger an die angegebene Position in der Liste.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Ausführlichere Anmerkungen finden Sie unter [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CPtrList-Klasse](../../mfc/reference/cptrlist-class.md)<br/>
[CObList-Klasse](../../mfc/reference/coblist-class.md)
