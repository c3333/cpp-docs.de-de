---
title: CObList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
ms.openlocfilehash: f24965357e0b71f28ba39b82d045600e7e1a44e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749688"
---
# <a name="coblist-class"></a>CObList-Klasse

fUnterstützt geordnete Listen `CObject` nicht eindeutiger Zeiger, auf die sequenziell oder nach Zeigerwert zugegriffen werden kann.

## <a name="syntax"></a>Syntax

```
class CObList : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObList::CObList](#coblist)|Erstellt eine leere `CObject` Liste für Zeiger.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObList::AddHead](#addhead)|Fügt dem Kopf der Liste ein Element (oder alle Elemente in einer anderen Liste) hinzu (macht einen neuen Kopf).|
|[CObList::AddTail](#addtail)|Fügt ein Element (oder alle Elemente in einer anderen Liste) am Ende der Liste hinzu (macht einen neuen Schwanz).|
|[CObList::Suchen](#find)|Ruft die Position eines Elements ab, das durch den Zeigerwert angegeben wird.|
|[CObList::FindIndex](#findindex)|Ruft die Position eines Elements ab, das durch einen nullbasierten Index angegeben wird.|
|[CobList::Getat](#getat)|Ruft das Element an einer bestimmten Position ab.|
|[CObList::GetCount](#getcount)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CObList::GetHead](#gethead)|Gibt das Kopfelement der Liste zurück (kann nicht leer sein).|
|[CObList::GetHeadPosition](#getheadposition)|Gibt die Position des Kopfelements der Liste zurück.|
|[CObList::GetNext](#getnext)|Ruft das nächste Element zum Iterieren ab.|
|[CObList::GetPrev](#getprev)|Ruft das vorherige Element zum Iterieren ab.|
|[CObList::GetSize](#getsize)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CObList::GetTail](#gettail)|Gibt das Tail-Element der Liste zurück (kann nicht leer sein).|
|[CObList::GetTailPosition](#gettailposition)|Gibt die Position des Schwanzelements der Liste zurück.|
|[CObList::InsertAfter](#insertafter)|Fügt ein neues Element nach einer bestimmten Position ein.|
|[CobList::InsertBefore](#insertbefore)|Fügt ein neues Element vor einer bestimmten Position ein.|
|[CobList::IsEmpty](#isempty)|Tests für die leere Listenbedingung (keine Elemente).|
|[CObList::Alle entfernen](#removeall)|Entfernt alle Elemente aus dieser Liste.|
|[CobList::Removeat](#removeat)|Entfernt ein Element aus dieser Liste, das durch Position angegeben wird.|
|[CObList::RemoveHead](#removehead)|Entfernt das Element vom Kopf der Liste.|
|[CObList::RemoveTail](#removetail)|Entfernt das Element vom Ende der Liste.|
|[CobList::Setat](#setat)|Legt das Element an einer bestimmten Position fest.|

## <a name="remarks"></a>Bemerkungen

`CObList`Listen verhalten sich wie doppelt verknüpfte Listen.

Eine Variable vom Typ POSITION ist ein Schlüssel für die Liste. Sie können eine POSITION-Variable sowohl als Iterator verwenden, um eine Liste sequenziell zu durchlaufen, als auch als Lesezeichen, um einen Ort zu halten. Eine Position ist jedoch nicht identisch mit einem Index.

Das Einfügen von Elementen erfolgt sehr schnell am Listenkopf, am Schwanz und an einer bekannten POSITION. Eine sequenzielle Suche ist erforderlich, um ein Element nach Wert oder Index zu suchen. Diese Suche kann langsam sein, wenn die Liste lang ist.

`CObList`enthält das IMPLEMENT_SERIAL Makro, um die Serialisierung und das Dumping seiner Elemente zu unterstützen. Wenn eine `CObject` Liste von Zeigern in einem Archiv gespeichert wird, entweder `Serialize` mit einem `CObject` überladenen Einfügeoperator oder mit der Memberfunktion, wird jedes Element nacheinander serialisiert.

Wenn Sie ein Dump `CObject` einzelner Elemente in der Liste benötigen, müssen Sie die Tiefe des Dumpkontexts auf 1 oder höher festlegen.

Wenn `CObList` ein Objekt gelöscht wird oder wenn seine `CObject` Elemente entfernt werden, werden nur die Zeiger entfernt, nicht die Objekte, auf die sie verweisen.

Sie können Ihre eigenen `CObList`Klassen von ableiten. Die neue Listenklasse, die Zeiger auf von `CObject`abgeleitete Objekte enthält, fügt neue Datenmember und neue Memberfunktionen hinzu. Beachten Sie, dass die resultierende Liste nicht streng `CObject` sicher ist, da sie das Einfügen eines beliebigen Zeigers ermöglicht.

> [!NOTE]
> Sie müssen [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) das IMPLEMENT_SERIAL-Makros bei der Implementierung der abgeleiteten Klasse verwenden, wenn Sie die Liste serialisieren möchten.

Weitere Informationen zur `CObList`Verwendung finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxcoll.h

## <a name="coblistaddhead"></a><a name="addhead"></a>CObList::AddHead

Fügt dem Kopf dieser Liste ein neues Element oder eine Liste von Elementen hinzu.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Parameter

*Newelement*<br/>
Der `CObject` Zeiger, der dieser Liste hinzugefügt werden soll.

*pNewList*<br/>
Ein Zeiger auf `CObList` eine andere Liste. Die Elemente in *pNewList* werden dieser Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den POSITION-Wert des neu eingefügten Elements zurück.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::AddHead`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddHead( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddHead(const CString&** `newElement` **);**<br /><br /> **POSITION AddHead(LPCTSTR** `newElement` **);**<br /><br /> **void AddHead(CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Bemerkungen

Die Liste kann vor dem Vorgang leer sein.

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

## <a name="coblistaddtail"></a><a name="addtail"></a>CObList::AddTail

Fügt ein neues Element oder eine Liste von Elementen am Ende dieser Liste hinzu.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Parameter

*Newelement*<br/>
Der `CObject` Zeiger, der dieser Liste hinzugefügt werden soll.

*pNewList*<br/>
Ein Zeiger auf `CObList` eine andere Liste. Die Elemente in *pNewList* werden dieser Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den POSITION-Wert des neu eingefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Die Liste kann vor dem Vorgang leer sein.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::AddTail`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddTail( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddTail( const CString&** `newElement` **);**<br /><br /> **POSITION AddTail( LPCTSTR** `newElement` **);**<br /><br /> **void AddTail( CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

## <a name="coblistcoblist"></a><a name="coblist"></a>CObList::CObList

Erstellt eine `CObject` leere Zeigerliste.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parameter

*nBlockSize*<br/>
Die Speicherzuweisungsgranularität zum Erweitern der Liste.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste wächst, wird der Speicher in Einheiten von *nBlockSize-Einträgen* zugewiesen. Wenn eine Speicherzuweisung `CMemoryException` fehlschlägt, wird eine ausgelöst.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::CObList`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList( INT_PTR** `nBlockSize` **= 10 );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>Beispiel

  Im Folgenden finden `CObject`Sie eine `CAge` Liste der -derived-Klasse, die in allen Sammlungsbeispielen verwendet wird:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Im Folgenden finden `CObList` Sie ein Beispiel für die Verwendung des Konstruktors:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

## <a name="coblistfind"></a><a name="find"></a>CObList::Suchen

Durchsucht die Liste sequenziell, `CObject` um den `CObject` ersten Zeiger zu finden, der dem angegebenen Zeiger entspricht.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parameter

*searchValue*<br/>
Der Objektzeiger, der in dieser Liste gefunden werden soll.

*startAfter*<br/>
Die Startposition für die Suche.

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn das Objekt nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass die Zeigerwerte verglichen werden, nicht der Inhalt der Objekte.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::Find`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION Find( void** <strong>\*</strong> `searchValue` **, POSITION** `startAfter` **= NULL ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION Find( LPCTSTR** `searchValue` **, POSITION** `startAfter` **= NULL ) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

## <a name="coblistfindindex"></a><a name="findindex"></a>CObList::FindIndex

Verwendet den Wert von *nIndex* als Index in der Liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der nullbasierte Index des zu findenden Listenelements.

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn *nIndex* zu groß ist. (Das Framework generiert eine Assertion, wenn *nIndex* negativ ist.)

### <a name="remarks"></a>Bemerkungen

Es startet einen sequenziellen Scan vom Kopf der Liste und stoppt auf dem *n*th-Element.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::FindIndex`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION FindIndex( INT_PTR** `nIndex` **) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION FindIndex( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

## <a name="coblistgetat"></a><a name="getat"></a>CobList::Getat

Eine Variable vom Typ POSITION ist ein Schlüssel für die Liste.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parameter

*position*<br/>
Ein POSITION-Wert, `GetHeadPosition` der `Find` von einem vorherigen oder Memberfunktionsaufruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Siehe die Rückgabewertbeschreibung für [GetHead](#gethead).

### <a name="remarks"></a>Bemerkungen

Es ist nicht dasselbe wie ein Index, und Sie können nicht selbst mit einem POSITION-Wert arbeiten. `GetAt`ruft den `CObject` Zeiger ab, der einer bestimmten Position zugeordnet ist.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::GetAt`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* void& GetAt( POSITION** *position* **) const;**<br /><br /> **void\*& GetAt( POSITION** *Position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetAt( POSITION** *position* **) const;**<br /><br /> **CString& GetAt( POSITION** *Position* **);**|

### <a name="example"></a>Beispiel

  Siehe Beispiel für [FindIndex](#findindex).

## <a name="coblistgetcount"></a><a name="getcount"></a>CObList::GetCount

Ruft die Anzahl der Elemente in dieser Liste ab.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Ganzzahlwert, der die Elementanzahl enthält.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::GetCount`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

## <a name="coblistgethead"></a><a name="gethead"></a>CObList::GetHead

Ruft `CObject` den Zeiger ab, der das Kopfelement dieser Liste darstellt.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn auf die Liste über einen `const CObList`Zeiger `GetHead` auf `CObject` eine zugegriffen wird, wird ein Zeiger zurückgegeben. Dadurch kann die Funktion nur auf der rechten Seite einer Zuweisungsanweisung verwendet werden und schützt so die Liste vor Änderungen.

Wenn auf die Liste direkt oder über `CObList`einen `GetHead` Zeiger auf `CObject` eine zugegriffen wird, wird ein Verweis auf einen Zeiger zurückgegeben. Dadurch kann die Funktion auf beiden Seiten einer Zuweisungsanweisung verwendet werden und so können die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `GetHead`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](#isempty) um zu überprüfen, ob die Liste Elemente enthält.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::GetHead`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* void& GetHead( ) const; void\*& GetHead( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetHead( ) const; CString& GetHead( );**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

Das folgende Beispiel veranschaulicht `GetHead` die Verwendung von auf der linken Seite einer Zuweisungsanweisung.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

## <a name="coblistgetheadposition"></a><a name="getheadposition"></a>CObList::GetHeadPosition

Ruft die Position des Kopfelements dieser Liste ab.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn die Liste leer ist.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::GetHeadPosition`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition( ) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

## <a name="coblistgetnext"></a><a name="getnext"></a>CObList::GetNext

Ruft das durch *rPosition*identifizierte Listenelement `POSITION` ab und legt *dann rPosition* auf den Wert des nächsten Eintrags in der Liste fest.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*Rposition*<br/>
Ein Verweis auf einen POSITION-Wert, der von einem vorherigen `GetNext`, `GetHeadPosition`oder einem anderen Memberfunktionsaufruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Siehe die Rückgabewertbeschreibung für [GetHead](#gethead).

### <a name="remarks"></a>Bemerkungen

Sie können `GetNext` in einer Vorwärtsiterationsschleife verwendet werden, `GetHeadPosition` wenn `Find`Sie die Anfangsposition mit einem Aufruf von oder festlegen.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Wenn das abgerufene Element das letzte in der Liste ist, wird der neue Wert von *rPosition* auf NULL gesetzt.

Es ist möglich, ein Element während einer Iteration zu entfernen. Siehe Beispiel für [RemoveAt](#removeat).

> [!NOTE]
> Ab MFC 8.0 wurde die const-Version `const CObject*` dieser `const CObject*&`Methode geändert, um anstelle von zurückzugeben.  Diese Änderung wurde vorgenommen, um den Compiler in Übereinstimmung mit dem C++-Standard zu bringen.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::GetNext`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

## <a name="coblistgetprev"></a><a name="getprev"></a>CObList::GetPrev

Ruft das durch *rPosition*identifizierte Listenelement ab und legt *dann rPosition* auf den POSITION-Wert des vorherigen Eintrags in der Liste fest.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*Rposition*<br/>
Ein Verweis auf einen POSITION-Wert, der von einem vorherigen `GetPrev` oder anderen Memberfunktionsaufruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Siehe die Rückgabewertbeschreibung für [GetHead](#gethead).

### <a name="remarks"></a>Bemerkungen

Sie können `GetPrev` in einer umgekehrten Iterationsschleife verwenden, `GetTailPosition` wenn `Find`Sie die Anfangsposition mit einem Aufruf von oder festlegen.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Wenn das abgerufene Element das erste in der Liste ist, wird der neue Wert von *rPosition* auf NULL gesetzt.

> [!NOTE]
> Ab MFC 8.0 wurde die const-Version `const CObject*` dieser `const CObject*&`Methode geändert, um anstelle von zurückzugeben.  Diese Änderung wurde vorgenommen, um den Compiler in Übereinstimmung mit dem C++-Standard zu bringen.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::GetPrev`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

## <a name="coblistgetsize"></a><a name="getsize"></a>CObList::GetSize

Gibt die Anzahl der Listenelemente zurück.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Liste.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Liste abzurufen.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::GetSize`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

## <a name="coblistgettail"></a><a name="gettail"></a>CObList::GetTail

Ruft `CObject` den Zeiger ab, der das Endelement dieser Liste darstellt.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Rückgabewert

Siehe die Rückgabewertbeschreibung für [GetHead](#gethead).

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `GetTail`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](#isempty) um zu überprüfen, ob die Liste Elemente enthält.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::GetTail`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* void& GetTail( ) const; void\*& GetTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetTail( ) const; CString& GetTail( );**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

## <a name="coblistgettailposition"></a><a name="gettailposition"></a>CObList::GetTailPosition

Ruft die Position des Tail-Elements dieser Liste ab. **NULL,** wenn die Liste leer ist.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn die Liste leer ist.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::GetTailPosition`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition( ) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

## <a name="coblistinsertafter"></a><a name="insertafter"></a>CObList::InsertAfter

Fügt dieser Liste ein Element nach dem Element an der angegebenen Position hinzu.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*position*<br/>
Ein POSITION-Wert, `GetNext`der `GetPrev`von `Find` einem vorherigen , oder Memberfunktionsaufruf zurückgegeben wird.

*Newelement*<br/>
Der Objektzeiger, der dieser Liste hinzugefügt werden soll.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::InsertAfter`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertAfter( POSITION** *Position* , **void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertAfter( POSITION** *position* , const **CString&** `newElement` **);**<br /><br /> **POSITION InsertAfter( POSITION** *Position* , **LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der mit dem *Positionsparameter* identisch ist.

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

## <a name="coblistinsertbefore"></a><a name="insertbefore"></a>CobList::InsertBefore

Fügt dieser Liste ein Element vor dem Element an der angegebenen Position hinzu.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*position*<br/>
Ein POSITION-Wert, `GetNext`der `GetPrev`von `Find` einem vorherigen , oder Memberfunktionsaufruf zurückgegeben wird.

*Newelement*<br/>
Der Objektzeiger, der dieser Liste hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der für den Iterations- oder Objektzeigerabruf verwendet werden kann; NULL, wenn die Liste leer ist.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::InsertBefore`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertBefore( POSITION** *Position* , **void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertBefore( POSITION** *position* , const **CString&** `newElement` **);**<br /><br /> **POSITION InsertBefore( POSITION** *Position* , **LPCTSTR** `newElement` **);**|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

## <a name="coblistisempty"></a><a name="isempty"></a>CobList::IsEmpty

Gibt an, ob diese Liste keine Elemente enthält.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn diese Liste leer ist; andernfalls 0.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::IsEmpty`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty( ) const;**|

### <a name="example"></a>Beispiel

  Siehe Beispiel für [RemoveAll](#removeall).

## <a name="coblistremoveall"></a><a name="removeall"></a>CObList::Alle entfernen

Entfernt alle Elemente aus dieser Liste und `CObList` gibt den zugeordneten Speicher frei.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Es wird kein Fehler generiert, wenn die Liste bereits leer ist.

Wenn Sie Elemente `CObList`aus einem entfernen, entfernen Sie die Objektzeiger aus der Liste. Es liegt in Ihrer Verantwortung, die Objekte selbst zu löschen.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::RemoveAll`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

## <a name="coblistremoveat"></a><a name="removeat"></a>CobList::Removeat

Entfernt das angegebene Element aus dieser Liste.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parameter

*position*<br/>
Die Position des Elements, das aus der Liste entfernt werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Element `CObList`aus einem entfernen, entfernen Sie den Objektzeiger aus der Liste. Es liegt in Ihrer Verantwortung, die Objekte selbst zu löschen.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::RemoveAt`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt( POSITION** *Position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt( POSITION** *Position* **);**|

### <a name="example"></a>Beispiel

  Seien Sie vorsichtig, wenn Sie ein Element während einer Listeniteration entfernen. Das folgende Beispiel zeigt eine Entfernungstechnik, die einen gültigen **POSITION-Wert** für [GetNext](#getnext)garantiert.

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

## <a name="coblistremovehead"></a><a name="removehead"></a>CObList::RemoveHead

Entfernt das Element vom Kopf der Liste und gibt einen Zeiger darauf zurück.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Rückgabewert

Der `CObject` Zeiger zuvor an der Spitze der Liste.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `RemoveHead`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](#isempty) um zu überprüfen, ob die Liste Elemente enthält.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::RemoveHead`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead( );**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

## <a name="coblistremovetail"></a><a name="removetail"></a>CObList::RemoveTail

Entfernt das Element vom Ende der Liste und gibt einen Zeiger darauf zurück.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Objekt, das sich am Ende der Liste befand.

### <a name="remarks"></a>Bemerkungen

Sie müssen sicherstellen, dass die `RemoveTail`Liste nicht leer ist, bevor Sie aufrufen. Wenn die Liste leer ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt. Verwenden Sie [IsEmpty,](#isempty) um zu überprüfen, ob die Liste Elemente enthält.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::RemoveTail`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Cstring RemoveTail( );**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

## <a name="coblistsetat"></a><a name="setat"></a>CobList::Setat

Legt das Element an einer bestimmten Position fest.

```cpp
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Die POSITION des festzulegenden Elements.

*Newelement*<br/>
Der `CObject` Zeiger, der in die Liste geschrieben werden soll.

### <a name="remarks"></a>Bemerkungen

Eine Variable vom Typ POSITION ist ein Schlüssel für die Liste. Es ist nicht dasselbe wie ein Index, und Sie können nicht selbst mit einem POSITION-Wert arbeiten. `SetAt`schreibt `CObject` den Zeiger auf die angegebene Position in der Liste.

Sie müssen sicherstellen, dass Ihr POSITION-Wert eine gültige Position in der Liste darstellt. Wenn sie ungültig ist, wird die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObList::SetAt`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt( POSITION** `pos` **, const CString&** `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt( POSITION** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge` Klasse finden Sie unter [CObList::CObList.](#coblist)

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CStringList-Klasse](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList-Klasse](../../mfc/reference/cptrlist-class.md)
