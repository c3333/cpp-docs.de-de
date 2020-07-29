---
title: Klasse "Klasse"
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
ms.openlocfilehash: 15830a30e8236a13f3911d1b84d3727d3246fc0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226671"
---
# <a name="catllist-class"></a>Klasse "Klasse"

Diese Klasse stellt Methoden zum Erstellen und Verwalten eines Listen Objekts bereit.

## <a name="syntax"></a>Syntax

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

### <a name="parameters"></a>Parameter

*Fresser*<br/>
Der Elementtyp.

*Echarakteristika*<br/>
Der Code, der zum Kopieren oder Verschieben von Elementen verwendet wird. Weitere Informationen finden Sie unter [celementtrait-Klasse](../../atl/reference/celementtraits-class.md) .

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|["": Inargtype](#inargtype)||

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|["":](#catllist)|Der Konstruktor.|
|[": ~-Llist"](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|["": AddHead](#addhead)|Rufen Sie diese Methode auf, um ein Element am Anfang der Liste hinzuzufügen.|
|[Kategorie:: addheadlist](#addheadlist)|Rufen Sie diese Methode auf, um eine vorhandene Liste zum Anfang der Liste hinzuzufügen.|
|["": AddTail](#addtail)|Mit dieser Methode können Sie dem Ende dieser Liste ein Element hinzufügen.|
|["": Addtaillist](#addtaillist)|Mit dieser Methode können Sie eine vorhandene Liste zum Ende dieser Liste hinzufügen.|
|["": AssertValid "](#assertvalid)|Mit dieser Methode können Sie bestätigen, dass die Liste gültig ist.|
|[: Suchen](#find)|Ruft diese Methode auf, um die Liste nach dem angegebenen Element zu durchsuchen.|
|["", "", "": FindIndex](#findindex)|Rufen Sie diese Methode auf, um die Position eines Elements zu erhalten, wenn ein Indexwert angegeben wird.|
|[": GetAt"](#getat)|Ruft diese Methode auf, um das Element an einer angegebenen Position in der Liste zurückzugeben.|
|["Update":: GetCount](#getcount)|Mit dieser Methode wird die Anzahl der Objekte in der Liste zurückgegeben.|
|["":](#gethead)|Rufen Sie diese Methode auf, um das Element am Anfang der Liste zurückzugeben.|
|["", "", "".](#getheadposition)|Rufen Sie diese Methode auf, um die Position des Hauptteils der Liste zu erhalten.|
|["": GetNext](#getnext)|Mit dieser Methode wird das nächste Element aus der Liste zurückgegeben.|
|[": GetPrev"](#getprev)|Ruft diese Methode auf, um das vorherige Element aus der Liste zurückzugeben.|
|["": Gettail](#gettail)|Ruft diese Methode auf, um das Element am Ende der Liste zurückzugeben.|
|["", "", "": Gettailposition](#gettailposition)|Rufen Sie diese Methode auf, um die Position des Endes der Liste zu erhalten.|
|[": InsertAfter": InsertAfter](#insertafter)|Mit dieser Methode wird ein neues Element nach der angegebenen Position in die Liste eingefügt.|
|["": InsertBefore](#insertbefore)|Mit dieser Methode wird vor der angegebenen Position ein neues Element in die Liste eingefügt.|
|["": IsEmpty](#isempty)|Ruft diese Methode auf, um zu bestimmen, ob die Liste leer ist.|
|["", "":](#movetohead)|Rufen Sie diese Methode auf, um das angegebene Element an den Anfang der Liste zu verschieben.|
|["", "":](#movetotail)|Ruft diese Methode auf, um das angegebene Element an das Ende der Liste zu verschieben.|
|[": RemoveAll"](#removeall)|Mit dieser Methode können Sie alle Elemente aus der Liste entfernen.|
|[": RemoveAt"](#removeat)|Mit dieser Methode können Sie ein einzelnes Element aus der Liste entfernen.|
|["": RemoveHead](#removehead)|Rufen Sie diese Methode auf, um das Element am Anfang der Liste zu entfernen.|
|["": Removeheadnoreturn](#removeheadnoreturn)|Rufen Sie diese Methode auf, um das Element an der Spitze der Liste zu entfernen, ohne einen Wert zurückzugeben.|
|["": Removetail](#removetail)|Mit dieser Methode wird das Element am Ende der Liste entfernt.|
|["": Removetailnoreturn](#removetailnoreturn)|Diese Methode wird aufgerufen, um das Element am Ende der Liste zu entfernen, ohne einen Wert zurückzugeben.|
|["":](#setat)|Ruft diese Methode auf, um den Wert des Elements an einer bestimmten Position in der Liste festzulegen.|
|["":](#swapelements)|Ruft diese Methode auf, um Elemente in der Liste auszutauschen.|

## <a name="remarks"></a>Bemerkungen

Die- `CAtlList` Klasse unterstützt geordnete Listen von nicht eindeutigen Objekten, auf die sequenziell oder nach Wert zugegriffen werden kann. `CAtlList`Listen Verhalten sich wie doppelt verknüpfte Listen. Jede Liste verfügt über einen Head-und einen Tail, und neue Elemente (oder Listen in einigen Fällen) können entweder am Ende der Liste oder vor oder nach bestimmten Elementen eingefügt werden.

Die meisten `CAtlList` Methoden verwenden einen Positionswert. Dieser Wert wird von den-Methoden verwendet, um auf den tatsächlichen Speicherort zu verweisen, in dem die Elemente gespeichert werden, und sollte nicht direkt berechnet oder vorhergesagt werden. Wenn für den Zugriff auf das *n*-te Element in der Liste erforderlich ist, gibt [die Methode "](#findindex) " "" "" "". Die Methoden ["](#getnext) ", "", "" [CAtlList::GetPrev](#getprev) , "", "", "", "", um die Objekte in der Liste zu durchlaufen.

Weitere Informationen zu den in ATL verfügbaren Sammlungs Klassen finden Sie unter [ATL](../../atl/atl-collection-classes.md)-Auflistungs Klassen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcoll. h

## <a name="catllistaddhead"></a><a name="addhead"></a>"": AddHead

Rufen Sie diese Methode auf, um ein Element am Anfang der Liste hinzuzufügen.

```cpp
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*gewisses*<br/>
Das neue Element.

### <a name="return-value"></a>Rückgabewert

Gibt die Position des neu hinzugefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die erste Version verwendet wird, wird ein leeres-Element mit seinem Standardkonstruktor und nicht mit seinem Kopierkonstruktor erstellt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>Kategorie:: addheadlist

Rufen Sie diese Methode auf, um eine vorhandene Liste zum Anfang der Liste hinzuzufügen.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parameter

*plnew*<br/>
Die hinzuzufügende Liste.

### <a name="remarks"></a>Bemerkungen

Die Liste, auf die von *plnew* verwiesen wird, wird am Anfang der vorhandenen Liste eingefügt. In Debugbuilds tritt ein Assertionsfehler auf, wenn *plnew* gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>"": AddTail

Mit dieser Methode können Sie dem Ende dieser Liste ein Element hinzufügen.

```cpp
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*gewisses*<br/>
Das hinzuzufügende Element.

### <a name="return-value"></a>Rückgabewert

Gibt die Position des neu hinzugefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die erste Version verwendet wird, wird ein leeres-Element mit seinem Standardkonstruktor und nicht mit seinem Kopierkonstruktor erstellt. Das-Element wird am Ende der Liste hinzugefügt und somit zum Ende. Diese Methode kann mit einer leeren Liste verwendet werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>"": Addtaillist

Mit dieser Methode können Sie eine vorhandene Liste zum Ende dieser Liste hinzufügen.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parameter

*plnew*<br/>
Die hinzuzufügende Liste.

### <a name="remarks"></a>Bemerkungen

Die Liste, auf die von *plnew* verwiesen wird, wird nach dem letzten-Element (sofern vorhanden) in das List-Objekt eingefügt. Das letzte Element in der *plnew* -Liste wird daher zum Ende. In Debugbuilds tritt ein Assertionsfehler auf, wenn *plnew* gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>"": AssertValid "

Mit dieser Methode können Sie bestätigen, dass die Liste gültig ist.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Fehler auf, wenn das Listen Objekt ungültig ist. Um gültig zu sein, muss eine leere Liste sowohl den Anfang als auch das Ende aufweisen, das auf NULL zeigt, und eine Liste, die nicht leer ist, muss sowohl die Kopfzeile als auch das Ende aufweisen, die auf gültige Adressen zeigen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>"":

Der Konstruktor.

```cpp
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parameter

*nblocksize*<br/>
Die Blockgröße.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor für das- `CAtlList` Objekt. Die Blockgröße ist ein Maß für die Menge an Arbeitsspeicher, die zugewiesen wird, wenn ein neues Element erforderlich ist. Größere Blockgrößen reduzieren Aufrufe von Speicher Belegungs Routinen, verwenden jedoch weitere Ressourcen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>": ~-Llist"

Der Destruktor.

```cpp
~CAtlList() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei, einschließlich eines aufzurufenden Aufrufes [:: RemoveAll](#removeall) , um alle Elemente aus der Liste zu entfernen.

In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste nach dem-Aufrufvorgang noch einige Elemente enthält `RemoveAll` .

## <a name="catllistfind"></a><a name="find"></a>: Suchen

Ruft diese Methode auf, um die Liste nach dem angegebenen Element zu durchsuchen.

```cpp
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parameter

*gewisses*<br/>
Das Element, das in der Liste gesucht werden soll.

*posstartafter*<br/>
Die Startposition für die Suche. Wenn kein Wert angegeben wird, beginnt die Suche mit dem Head-Element.

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert des Elements zurück, wenn es gefunden wird, andernfalls wird NULL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn das Listen Objekt ungültig ist oder der *posstartafter* -Wert außerhalb des gültigen Bereichs liegt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>"", "", "": FindIndex

Rufen Sie diese Methode auf, um die Position eines Elements zu erhalten, wenn ein Indexwert angegeben wird.

```cpp
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parameter

*IElement*<br/>
Der null basierte Index des erforderlichen Listen Elements.

### <a name="return-value"></a>Rückgabewert

Gibt den entsprechenden Positionswert oder NULL zurück, wenn *IElement* außerhalb des gültigen Bereichs liegt.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt die Position zurück, die einem bestimmten Indexwert entspricht, und ermöglicht den Zugriff auf das *n*-te Element in der Liste.

In Debugbuilds tritt ein Fehler auf, wenn das Listen Objekt ungültig ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>": GetAt"

Ruft diese Methode auf, um das Element an einer angegebenen Position in der Liste zurückzugeben.

```cpp
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positionswert, der ein bestimmtes Element angibt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Element oder eine Kopie von.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste ist **`const`** , wird `GetAt` eine Kopie des-Elements zurückgegeben. Dadurch kann die-Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden, und die Liste wird vor Änderungen geschützt.

Wenn die Liste nicht ist **`const`** , wird `GetAt` ein Verweis auf das-Element zurückgegeben. Dadurch kann die-Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden, sodass die Listeneinträge geändert werden können.

In Debugbuilds tritt ein Assertionsfehler auf, wenn *POS* gleich NULL ist.

### <a name="example"></a>Beispiel

Weitere [Informationen](#findindex)finden Sie im Beispiel für "":

## <a name="catllistgetcount"></a><a name="getcount"></a>"Update":: GetCount

Mit dieser Methode wird die Anzahl der Objekte in der Liste zurückgegeben.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl von Elementen in der Liste zurück.

### <a name="example"></a>Beispiel

Weitere [Informationen finden](#find)Sie im Beispiel für "":

## <a name="catllistgethead"></a><a name="gethead"></a>"":

Rufen Sie diese Methode auf, um das Element am Anfang der Liste zurückzugeben.

```cpp
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf oder eine Kopie von auf das Element am Anfang der Liste zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste ist **`const`** , wird `GetHead` eine Kopie des Elements an der Spitze der Liste zurückgegeben. Dadurch kann die-Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden, und die Liste wird vor Änderungen geschützt.

Wenn die Liste nicht ist **`const`** , wird `GetHead` ein Verweis auf das Element am Anfang der Liste zurückgegeben. Dadurch kann die-Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden, sodass die Listeneinträge geändert werden können.

In Debugbuilds tritt ein Fehler auf, wenn der Anfang der Liste auf NULL zeigt.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#addhead)

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>"", "", "".

Rufen Sie diese Methode auf, um die Position des Hauptteils der Liste zu erhalten.

```cpp
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert zurück, der dem Element am Anfang der Liste entspricht.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste leer ist, ist der zurückgegebene Wert NULL.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>"": GetNext

Mit dieser Methode wird das nächste Element aus der Liste zurückgegeben.

```cpp
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Ein Positionswert, der von einem vorherigen-Befehl, der-Methode, der-Methode, der-Methode oder der-Methode zurückgegeben wurde `GetNext` [CAtlList::GetHeadPosition](#getheadposition) `CAtlList` .

### <a name="return-value"></a>Rückgabewert

Wenn die Liste ist **`const`** , wird `GetNext` eine Kopie des nächsten Elements der Liste zurückgegeben. Dadurch kann die-Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden, und die Liste wird vor Änderungen geschützt.

Wenn die Liste nicht ist **`const`** , wird `GetNext` ein Verweis auf das nächste Element der Liste zurückgegeben. Dadurch kann die-Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden, sodass die Listeneinträge geändert werden können.

### <a name="remarks"></a>Bemerkungen

Der Positions-Counter, *POS*, wird aktualisiert, um auf das nächste Element in der Liste zu verweisen, oder NULL, wenn keine weiteren Elemente vorhanden sind. In Debugbuilds tritt ein Assertionsfehler auf, wenn *POS* gleich NULL ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "](#getheadposition)".

## <a name="catllistgetprev"></a><a name="getprev"></a>": GetPrev"

Ruft diese Methode auf, um das vorherige Element aus der Liste zurückzugeben.

```cpp
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Ein Positionswert, der von einem vorherigen-Befehl von, "", "", "", "", "", "" `GetPrev` [CAtlList::GetTailPosition](#gettailposition) `CAtlList` .

### <a name="return-value"></a>Rückgabewert

Wenn die Liste ist **`const`** , wird `GetPrev` eine Kopie eines Elements der Liste zurückgegeben. Dadurch kann die-Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden, und die Liste wird vor Änderungen geschützt.

Wenn die Liste nicht ist **`const`** , wird `GetPrev` von ein Verweis auf ein Element der Liste zurückgegeben. Dadurch kann die-Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden, sodass die Listeneinträge geändert werden können.

### <a name="remarks"></a>Bemerkungen

Der Positions-Counter, *POS*, wird aktualisiert, um auf das vorherige Element in der Liste zu verweisen, oder NULL, wenn keine weiteren Elemente vorhanden sind. In Debugbuilds tritt ein Assertionsfehler auf, wenn *POS* gleich NULL ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#gettailposition)

## <a name="catllistgettail"></a><a name="gettail"></a>"": Gettail

Ruft diese Methode auf, um das Element am Ende der Liste zurückzugeben.

```cpp
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf oder eine Kopie von auf das-Element am Ende der Liste zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste ist **`const`** , wird `GetTail` eine Kopie des Elements an der Spitze der Liste zurückgegeben. Dadurch kann die-Methode nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden, und die Liste wird vor Änderungen geschützt.

Wenn die Liste nicht ist **`const`** , wird `GetTail` ein Verweis auf das Element am Anfang der Liste zurückgegeben. Dadurch kann die-Methode auf beiden Seiten einer Zuweisungsanweisung verwendet werden, sodass die Listeneinträge geändert werden können.

In Debugbuilds tritt ein Fehler auf, wenn das Ende der Liste auf NULL zeigt.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#addtail)

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>"", "", "": Gettailposition

Rufen Sie diese Methode auf, um die Position des Endes der Liste zu erhalten.

```cpp
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert zurück, der dem Element am Ende der Liste entspricht.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste leer ist, ist der zurückgegebene Wert NULL.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>"": Inargtype

Der Typ, der verwendet wird, wenn ein Element als Eingabe Argument übermittelt wird.

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>": InsertAfter": InsertAfter

Mit dieser Methode wird ein neues Element nach der angegebenen Position in die Liste eingefügt.

```cpp
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positionswert, nach dem das neue Element eingefügt wird.

*gewisses*<br/>
Das einzufügende Element.

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert des neuen Elements zurück.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste nicht gültig ist, wenn die Einfügung fehlschlägt oder wenn versucht wird, das Element nach dem Ende einzufügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>"": InsertBefore

Mit dieser Methode wird vor der angegebenen Position ein neues Element in die Liste eingefügt.

```cpp
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Das neue Element wird vor diesem Positionswert in die Liste eingefügt.

*gewisses*<br/>
Das einzufügende Element.

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert des neuen Elements zurück.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste nicht gültig ist, wenn die Einfügung fehlschlägt oder wenn versucht wird, das Element vor dem Kopf einzufügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>"": IsEmpty

Ruft diese Methode auf, um zu bestimmen, ob die Liste leer ist.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Liste keine Objekte enthält, andernfalls false.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>"", "":

Rufen Sie diese Methode auf, um das angegebene Element an den Anfang der Liste zu verschieben.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positionswert des zu verschiebenden Elements.

### <a name="remarks"></a>Bemerkungen

Das angegebene Element wird von seiner aktuellen Position an den Anfang der Liste verschoben. In Debugbuilds tritt ein Assertionsfehler auf, wenn *POS* gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>"", "":

Ruft diese Methode auf, um das angegebene Element an das Ende der Liste zu verschieben.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positionswert des zu verschiebenden Elements.

### <a name="remarks"></a>Bemerkungen

Das angegebene Element wird von der aktuellen Position bis zum Ende der Liste verschoben. In Debugbuilds tritt ein Assertionsfehler auf, wenn *POS* gleich NULL ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#movetohead)

## <a name="catllistremoveall"></a><a name="removeall"></a>": RemoveAll"

Mit dieser Methode können Sie alle Elemente aus der Liste entfernen.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt alle Elemente aus der Liste und gibt den zugeordneten Arbeitsspeicher frei. Bei Builds Debuggen wird ein ATLASSERT ausgelöst, wenn alle Elemente nicht gelöscht werden oder wenn die Listenstruktur beschädigt ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für "": [: IsEmpty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>": RemoveAt"

Mit dieser Methode können Sie ein einzelnes Element aus der Liste entfernen.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positionswert des zu entfernenden Elements.

### <a name="remarks"></a>Bemerkungen

Das Element, auf das von *POS* verwiesen wird, wird entfernt, und der Speicher wird freigegeben Es ist akzeptabel, `RemoveAt` zu verwenden, um den Anfang oder das Ende der Liste zu entfernen.

In Debugbuilds tritt ein Assertionsfehler auf, wenn die Liste ungültig ist, oder wenn das Entfernen des Elements bewirkt, dass die Liste auf den Speicher zugreift, der nicht Teil der Listenstruktur ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>"": RemoveHead

Rufen Sie diese Methode auf, um das Element am Anfang der Liste zu entfernen.

```cpp
E RemoveHead();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Element am Anfang der Liste zurück.

### <a name="remarks"></a>Bemerkungen

Das Head-Element wird aus der Liste gelöscht, und der Arbeitsspeicher wird freigegeben. Eine Kopie des Elements wird zurückgegeben. In Debugbuilds tritt ein Fehler auf, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>"": Removeheadnoreturn

Rufen Sie diese Methode auf, um das Element an der Spitze der Liste zu entfernen, ohne einen Wert zurückzugeben.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Head-Element wird aus der Liste gelöscht, und der Arbeitsspeicher wird freigegeben. In Debugbuilds tritt ein Fehler auf, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für "": [: IsEmpty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>"": Removetail

Mit dieser Methode wird das Element am Ende der Liste entfernt.

```cpp
E RemoveTail();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Element am Ende der Liste zurück.

### <a name="remarks"></a>Bemerkungen

Das Tail-Element wird aus der Liste gelöscht, und der Arbeitsspeicher wird freigegeben. Eine Kopie des Elements wird zurückgegeben. In Debugbuilds tritt ein Fehler auf, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>"": Removetailnoreturn

Diese Methode wird aufgerufen, um das Element am Ende der Liste zu entfernen, ohne einen Wert zurückzugeben.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Tail-Element wird aus der Liste gelöscht, und der Arbeitsspeicher wird freigegeben. In Debugbuilds tritt ein Fehler auf, wenn die Liste leer ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für "": [: IsEmpty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>"":

Ruft diese Methode auf, um den Wert des Elements an einer bestimmten Position in der Liste festzulegen.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positionswert, der dem Element entspricht, das geändert werden soll.

*gewisses*<br/>
Der neue Elementwert.

### <a name="remarks"></a>Bemerkungen

Ersetzt den vorhandenen Wert durch das- *Element*. In Debugbuilds tritt ein Assertionsfehler auf, wenn *POS* gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>"":

Ruft diese Methode auf, um Elemente in der Liste auszutauschen.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parameter

*pos1*<br/>
Der erste Positionswert.

*pos2*<br/>
Der zweite Positionswert.

### <a name="remarks"></a>Bemerkungen

Tauscht die Elemente an den beiden angegebenen Positionen aus. In Debugbuilds tritt ein Assertionsfehler auf, wenn einer der Positionswerte gleich NULL ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Siehe auch

[CLIST-Klasse](../../mfc/reference/clist-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
