---
title: CAtlList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
ms.openlocfilehash: 0e4ea8eef51431c100f5d3119d7f75e9673e276e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748734"
---
# <a name="catllist-class"></a>CAtlList-Klasse

Diese Klasse stellt Methoden zum Erstellen und Verwalten eines Listenobjekts bereit.

## <a name="syntax"></a>Syntax

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

#### <a name="parameters"></a>Parameter

*E*<br/>
Der Elementtyp.

*ETraits*<br/>
Der Code, der zum Kopieren oder Verschieben von Elementen verwendet wird. Weitere Informationen finden Sie unter [CElementTraits-Klasse.](../../atl/reference/celementtraits-class.md)

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|Der Konstruktor.|
|[CAtlList::'CAtlList](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|Rufen Sie diese Methode auf, um dem Kopf der Liste ein Element hinzuzufügen.|
|[CAtlList::AddHeadList](#addheadlist)|Rufen Sie diese Methode auf, um dem Kopf der Liste eine vorhandene Liste hinzuzufügen.|
|[CAtlList::AddTail](#addtail)|Rufen Sie diese Methode auf, um ein Element am Ende dieser Liste hinzuzufügen.|
|[CAtlList::AddTailList](#addtaillist)|Rufen Sie diese Methode auf, um eine vorhandene Liste am Ende dieser Liste hinzuzufügen.|
|[CAtlList::AssertValid](#assertvalid)|Rufen Sie diese Methode auf, um zu bestätigen, dass die Liste gültig ist.|
|[CAtlList::Suchen](#find)|Rufen Sie diese Methode auf, um die Liste nach dem angegebenen Element zu durchsuchen.|
|[CAtlList::FindIndex](#findindex)|Rufen Sie diese Methode auf, um die Position eines Elements mit einem Indexwert zu erhalten.|
|[CAtlList::GetAt](#getat)|Rufen Sie diese Methode auf, um das Element an einer angegebenen Position in der Liste zurückzugeben.|
|[CAtlList::GetCount](#getcount)|Rufen Sie diese Methode auf, um die Anzahl der Objekte in der Liste zurückzugeben.|
|[CAtlList::GetHead](#gethead)|Rufen Sie diese Methode auf, um das Element an der Spitze der Liste zurückzugeben.|
|[CAtlList::GetHeadPosition](#getheadposition)|Rufen Sie diese Methode auf, um die Position des Kopfes der Liste zu erhalten.|
|[CAtlList::GetNext](#getnext)|Rufen Sie diese Methode auf, um das nächste Element aus der Liste zurückzugeben.|
|[CAtlList::GetPrev](#getprev)|Rufen Sie diese Methode auf, um das vorherige Element aus der Liste zurückzugeben.|
|[CAtlList::GetTail](#gettail)|Rufen Sie diese Methode auf, um das Element am Ende der Liste zurückzugeben.|
|[CAtlList::GetTailPosition](#gettailposition)|Rufen Sie diese Methode auf, um die Position des Teils der Liste zu erhalten.|
|[CAtlList::InsertAfter](#insertafter)|Rufen Sie diese Methode auf, um ein neues Element nach der angegebenen Position in die Liste einzufügen.|
|[CAtlList::InsertBefore](#insertbefore)|Rufen Sie diese Methode auf, um ein neues Element vor der angegebenen Position in die Liste einzufügen.|
|[CAtlList::IsEmpty](#isempty)|Rufen Sie diese Methode auf, um zu ermitteln, ob die Liste leer ist.|
|[CAtlList::MoveToHead](#movetohead)|Rufen Sie diese Methode auf, um das angegebene Element an den Kopf der Liste zu verschieben.|
|[CAtlList::MoveToTail](#movetotail)|Rufen Sie diese Methode auf, um das angegebene Element an den Endes der Liste zu verschieben.|
|[CAtlList::Alle entfernen](#removeall)|Rufen Sie diese Methode auf, um alle Elemente aus der Liste zu entfernen.|
|[CAtlList::RemoveAt](#removeat)|Rufen Sie diese Methode auf, um ein einzelnes Element aus der Liste zu entfernen.|
|[CAtlList::RemoveHead](#removehead)|Rufen Sie diese Methode auf, um das Element am Anfang der Liste zu entfernen.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Rufen Sie diese Methode auf, um das Element am Anfang der Liste zu entfernen, ohne einen Wert zurückzugeben.|
|[CAtlList::RemoveTail](#removetail)|Rufen Sie diese Methode auf, um das Element am Ende der Liste zu entfernen.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Rufen Sie diese Methode auf, um das Element am Ende der Liste zu entfernen, ohne einen Wert zurückzugeben.|
|[CAtlList::SetAt](#setat)|Rufen Sie diese Methode auf, um den Wert des Elements an einer bestimmten Position in der Liste festzulegen.|
|[CAtlList::SwapElements](#swapelements)|Rufen Sie diese Methode auf, um Elemente in der Liste auszutauschen.|

## <a name="remarks"></a>Bemerkungen

Die `CAtlList` Klasse unterstützt geordnete Listen nicht eindeutiger Objekte, auf die sequenziell oder nach Wert zugegriffen werden kann. `CAtlList`Listen verhalten sich wie doppelt verknüpfte Listen. Jede Liste hat einen Kopf und einen Schwanz, und neue Elemente (oder Listen in einigen Fällen) können entweder am Ende der Liste hinzugefügt oder vor oder nach bestimmten Elementen eingefügt werden.

Die meisten `CAtlList` Methoden verwenden einen Positionswert. Dieser Wert wird von den Methoden verwendet, um auf den tatsächlichen Speicherort des Speichers zu verweisen, an dem die Elemente gespeichert sind, und sollte nicht direkt berechnet oder vorhergesagt werden. Wenn der Zugriff auf das *n*th-Element in der Liste erforderlich ist, gibt die Methode [CAtlList::FindIndex](#findindex) den entsprechenden Positionswert für einen bestimmten Index zurück. Die Methoden [CAtlList::GetNext](#getnext) und [CAtlList::GetPrev](#getprev) können verwendet werden, um die Objekte in der Liste zu durchlaufen.

Weitere Informationen zu den mit ATL verfügbaren Auflistungsklassen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlcoll.h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::AddHead

Rufen Sie diese Methode auf, um dem Kopf der Liste ein Element hinzuzufügen.

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*Element*<br/>
Das neue Element.

### <a name="return-value"></a>Rückgabewert

Gibt die Position des neu hinzugefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die erste Version verwendet wird, wird ein leeres Element mit dem Standardkonstruktor und nicht mit dem Kopierkonstruktor erstellt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

Rufen Sie diese Methode auf, um dem Kopf der Liste eine vorhandene Liste hinzuzufügen.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parameter

*plNeu*<br/>
Die hinzuzufügende Liste.

### <a name="remarks"></a>Bemerkungen

Die von *plNew* angeführte Liste wird am Anfang der vorhandenen Liste eingefügt. In Debugbuilds tritt ein Assertionsfehler auf, wenn *plNew* gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList::AddTail

Rufen Sie diese Methode auf, um ein Element am Ende dieser Liste hinzuzufügen.

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*Element*<br/>
Das hinzuzufügende Element.

### <a name="return-value"></a>Rückgabewert

Gibt die POSITION des neu hinzugefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die erste Version verwendet wird, wird ein leeres Element mit dem Standardkonstruktor und nicht mit dem Kopierkonstruktor erstellt. Das Element wird am Ende der Liste hinzugefügt, und so wird es nun zum Schwanz. Diese Methode kann mit einer leeren Liste verwendet werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

Rufen Sie diese Methode auf, um eine vorhandene Liste am Ende dieser Liste hinzuzufügen.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parameter

*plNeu*<br/>
Die hinzuzufügende Liste.

### <a name="remarks"></a>Bemerkungen

Die von *plNew* gezeigte Liste wird nach dem letzten Element (falls vorhanden) in das Listenobjekt eingefügt. Das letzte Element in der *plNew-Liste* wird daher zum Schwanz. In Debugbuilds tritt ein Assertionsfehler auf, wenn *plNew* gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::AssertValid

Rufen Sie diese Methode auf, um zu bestätigen, dass die Liste gültig ist.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn das Listenobjekt ungültig ist. Um gültig zu sein, muss eine leere Liste sowohl den Kopf als auch den Schwanz haben, der auf NULL zeigt, und eine Liste, die nicht leer ist, muss sowohl den Kopf als auch den Schwanz haben, der auf gültige Adressen verweist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

Der Konstruktor.

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parameter

*nBlockSize*<br/>
Die Blockgröße.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor `CAtlList` für das Objekt. Die Blockgröße ist ein Maß für die Speichermenge, die zugewiesen wird, wenn ein neues Element erforderlich ist. Größere Blockgrößen reduzieren Aufrufe von Speicherzuweisungsroutinen, verwenden jedoch mehr Ressourcen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList::'CAtlList

Der Destruktor.

```
~CAtlList() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei, einschließlich eines Aufrufs von [CAtlList::RemoveAll,](#removeall) um alle Elemente aus der Liste zu entfernen.

In Debugbuilds tritt ein Assertionsfehler auf, wenn die `RemoveAll`Liste nach dem Aufruf von noch einige Elemente enthält.

## <a name="catllistfind"></a><a name="find"></a>CAtlList::Suchen

Rufen Sie diese Methode auf, um die Liste nach dem angegebenen Element zu durchsuchen.

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parameter

*Element*<br/>
Das Element, das in der Liste zu finden ist.

*posStartAfter*<br/>
Die Startposition für die Suche. Wenn kein Wert angegeben ist, beginnt die Suche mit dem Head-Element.

### <a name="return-value"></a>Rückgabewert

Gibt den POSITION-Wert des Elements zurück, falls gefunden, andernfalls wird NULL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn das Listenobjekt ungültig ist oder wenn der *posStartAfter-Wert* anicht zulässig ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList::FindIndex

Rufen Sie diese Methode auf, um die Position eines Elements mit einem Indexwert zu erhalten.

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parameter

*Ielement*<br/>
Der nullbasierte Index des erforderlichen Listenelements.

### <a name="return-value"></a>Rückgabewert

Gibt den entsprechenden POSITION-Wert oder NULL zurück, wenn *iElement* anicht in Reichweite liegt.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt die POSITION zurück, die einem bestimmten Indexwert entspricht, sodass Sie auf das *n*th-Element in der Liste zugreifen können.

In Debugbuilds tritt ein Assertionsfehler auf, wenn das Listenobjekt ungültig ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList::GetAt

Rufen Sie diese Methode auf, um das Element an einer angegebenen Position in der Liste zurückzugeben.

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der POSITION-Wert, der ein bestimmtes Element angibt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf oder eine Kopie des Elements.

### <a name="remarks"></a>Bemerkungen

Wenn die **const**Liste `GetAt` const ist, gibt eine Kopie des Elements zurück. Dadurch kann die Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt die Liste vor Änderungen.

Wenn die Liste **const**nicht `GetAt` const ist, gibt ein Verweis auf das Element zurück. Dadurch kann die Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden und somit die Listeneinträge geändert werden.

In Debugbuilds tritt ein Assertionsfehler auf, wenn *pos* gleich NULL ist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::FindIndex](#findindex).

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList::GetCount

Rufen Sie diese Methode auf, um die Anzahl der Objekte in der Liste zurückzugeben.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl von Elementen in der Liste zurück.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::Find](#find).

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList::GetHead

Rufen Sie diese Methode auf, um das Element an der Spitze der Liste zurückzugeben.

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das Element am Anfang der Liste oder eine Kopie des Elements zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die **const**Liste `GetHead` const ist, gibt eine Kopie des Elements am Anfang der Liste zurück. Dadurch kann die Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt die Liste vor Änderungen.

Wenn die Liste **const**nicht `GetHead` const ist, gibt ein Verweis auf das Element am Anfang der Liste zurück. Dadurch kann die Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden und somit die Listeneinträge geändert werden.

Bei Debugbuilds tritt ein Assertionsfehler auf, wenn der Kopf der Liste auf NULL verweist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::AddHead](#addhead).

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

Rufen Sie diese Methode auf, um die Position des Kopfes der Liste zu erhalten.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den POSITION-Wert zurück, der dem Element am Anfang der Liste entspricht.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste leer ist, lautet der zurückgegebene Wert NULL.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList::GetNext

Rufen Sie diese Methode auf, um das nächste Element aus der Liste zurückzugeben.

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Ein POSITION-Wert, der von `GetNext`einem vorherigen Aufruf von , [CAtlList::GetHeadPosition](#getheadposition)oder einer anderen `CAtlList` Methode zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Wenn die **const**Liste `GetNext` const ist, gibt eine Kopie des nächsten Elements der Liste zurück. Dadurch kann die Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt die Liste vor Änderungen.

Wenn die Liste **const**nicht `GetNext` const ist, wird ein Verweis auf das nächste Element der Liste zurückgegeben. Dadurch kann die Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden und somit die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Der POSITION-Zähler *pos*wird aktualisiert, um auf das nächste Element in der Liste zu verweisen, oder NULL, wenn keine weiteren Elemente vorhanden sind. In Debugbuilds tritt ein Assertionsfehler auf, wenn *pos* gleich NULL ist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::GetHeadPosition](#getheadposition).

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList::GetPrev

Rufen Sie diese Methode auf, um das vorherige Element aus der Liste zurückzugeben.

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Ein POSITION-Wert, der von `GetPrev`einem vorherigen Aufruf von , [CAtlList::GetTailPosition](#gettailposition)oder einer anderen `CAtlList` Methode zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Wenn die **const**Liste `GetPrev` const ist, gibt eine Kopie eines Elements der Liste zurück. Dadurch kann die Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt die Liste vor Änderungen.

Wenn die Liste **const**nicht `GetPrev` const ist, gibt ein Verweis auf ein Element der Liste zurück. Dadurch kann die Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden und somit die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Der POSITION-Zähler *pos*wird aktualisiert, um auf das vorherige Element in der Liste zu verweisen, oder NULL, wenn keine weiteren Elemente vorhanden sind. In Debugbuilds tritt ein Assertionsfehler auf, wenn *pos* gleich NULL ist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::GetTailPosition](#gettailposition).

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList::GetTail

Rufen Sie diese Methode auf, um das Element am Ende der Liste zurückzugeben.

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das Element am Ende der Liste oder eine Kopie des Elements zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die **const**Liste `GetTail` const ist, gibt eine Kopie des Elements am Anfang der Liste zurück. Dadurch kann die Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt die Liste vor Änderungen.

Wenn die Liste **const**nicht `GetTail` const ist, gibt ein Verweis auf das Element am Anfang der Liste zurück. Dadurch kann die Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden und somit die Listeneinträge geändert werden.

Bei Debugbuilds tritt ein Assertionsfehler auf, wenn der Teil der Liste auf NULL verweist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::AddTail](#addtail).

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

Rufen Sie diese Methode auf, um die Position des Teils der Liste zu erhalten.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den POSITION-Wert zurück, der dem Element am Ende der Liste entspricht.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste leer ist, lautet der zurückgegebene Wert NULL.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

Typ, der verwendet wird, wenn ein Element als Eingabeargument übergeben wird.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList::InsertAfter

Rufen Sie diese Methode auf, um ein neues Element nach der angegebenen Position in die Liste einzufügen.

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der POSITION-Wert, nach dem das neue Element eingefügt wird.

*Element*<br/>
Das element, das eingefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt den POSITION-Wert des neuen Elements zurück.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste ungültig ist, wenn die Einfügung fehlschlägt oder wenn versucht wird, das Element nach dem Abstrich einzufügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList::InsertBefore

Rufen Sie diese Methode auf, um ein neues Element vor der angegebenen Position in die Liste einzufügen.

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Das neue Element wird vor diesem POSITION-Wert in die Liste eingefügt.

*Element*<br/>
Das element, das eingefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt den POSITION-Wert des neuen Elements zurück.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste ungültig ist, wenn die Einfügung fehlschlägt oder wenn versucht wird, das Element vor den Kopf einzufügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList::IsEmpty

Rufen Sie diese Methode auf, um zu ermitteln, ob die Liste leer ist.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Liste keine Objekte enthält, andernfalls false.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

Rufen Sie diese Methode auf, um das angegebene Element an den Kopf der Liste zu verschieben.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der POSITION-Wert des zu verschiebenden Elements.

### <a name="remarks"></a>Bemerkungen

Das angegebene Element wird von seiner aktuellen Position an den Kopf der Liste verschoben. In Debugbuilds tritt ein Assertionsfehler auf, wenn *pos* gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

Rufen Sie diese Methode auf, um das angegebene Element an den Endes der Liste zu verschieben.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der POSITION-Wert des zu verschiebenden Elements.

### <a name="remarks"></a>Bemerkungen

Das angegebene Element wird von seiner aktuellen Position an den Ende der Liste verschoben. In Debugbuilds tritt ein Assertionsfehler auf, wenn *pos* gleich NULL ist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::MoveToHead](#movetohead).

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList::Alle entfernen

Rufen Sie diese Methode auf, um alle Elemente aus der Liste zu entfernen.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt alle Elemente aus der Liste und gibt den zugewiesenen Speicher frei. In Debugbuilds wird ein ATLASSERT ausgelöst, wenn nicht alle Elemente gelöscht werden oder die Listenstruktur beschädigt wurde.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::IsEmpty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList::RemoveAt

Rufen Sie diese Methode auf, um ein einzelnes Element aus der Liste zu entfernen.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der POSITION-Wert des zu entfernenden Elements.

### <a name="remarks"></a>Bemerkungen

Das Element, auf das von *pos* verwiesen wird, wird entfernt, und der Speicher wird freigegeben. Es ist akzeptabel, den Kopf oder Schwanz der Liste zu entfernen. `RemoveAt`

In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste ungültig ist oder wenn das Element durch Das Entfernen des Elements auf den Speicher zugreift, der nicht Teil der Listenstruktur ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

Rufen Sie diese Methode auf, um das Element am Anfang der Liste zu entfernen.

```
E RemoveHead();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Element am Anfang der Liste zurück.

### <a name="remarks"></a>Bemerkungen

Das Head-Element wird aus der Liste gelöscht, und der Speicher wird freigegeben. Eine Kopie des Elements wird zurückgegeben. In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

Rufen Sie diese Methode auf, um das Element am Anfang der Liste zu entfernen, ohne einen Wert zurückzugeben.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Head-Element wird aus der Liste gelöscht, und der Speicher wird freigegeben. In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::IsEmpty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

Rufen Sie diese Methode auf, um das Element am Ende der Liste zu entfernen.

```
E RemoveTail();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Element am Ende der Liste zurück.

### <a name="remarks"></a>Bemerkungen

Das tail-Element wird aus der Liste gelöscht, und der Speicher wird freigegeben. Eine Kopie des Elements wird zurückgegeben. In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

Rufen Sie diese Methode auf, um das Element am Ende der Liste zu entfernen, ohne einen Wert zurückzugeben.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Bemerkungen

Das tail-Element wird aus der Liste gelöscht, und der Speicher wird freigegeben. In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlList::IsEmpty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList::SetAt

Rufen Sie diese Methode auf, um den Wert des Elements an einer bestimmten Position in der Liste festzulegen.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der POSITION-Wert, der dem zu ändernden Element entspricht.

*Element*<br/>
Der neue Elementwert.

### <a name="remarks"></a>Bemerkungen

Ersetzt den vorhandenen Wert durch *das Element*. In Debugbuilds tritt ein Assertionsfehler auf, wenn *pos* gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

Rufen Sie diese Methode auf, um Elemente in der Liste auszutauschen.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parameter

*pos1*<br/>
Der erste POSITION-Wert.

*pos2*<br/>
Der zweite POSITION-Wert.

### <a name="remarks"></a>Bemerkungen

Tauscht die Elemente an den beiden angegebenen Positionen. In Debugbuilds tritt ein Assertionsfehler auf, wenn einer der Positionswerte gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Weitere Informationen

[CList-Klasse](../../mfc/reference/clist-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
