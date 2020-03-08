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
ms.openlocfilehash: 2fc3a3643c675394de555f1411030e278bcee775
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855295"
---
# <a name="coblist-class"></a>CObList-Klasse

funter stützt geordnete Listen mit nicht eindeutigen `CObject` Zeigern, auf die sequenziell oder durch einen Zeiger Wert zugegriffen werden kann

## <a name="syntax"></a>Syntax

```
class CObList : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObList:: CObList](#coblist)|Erstellt eine leere Liste für `CObject` Zeiger.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObList:: AddHead](#addhead)|Fügt ein Element (oder alle Elemente in einer anderen Liste) zum Anfang der Liste hinzu (erstellt einen neuen Kopf).|
|[CObList:: AddTail](#addtail)|Fügt ein Element (oder alle Elemente in einer anderen Liste) zum Ende der Liste hinzu (führt ein neues Ende aus).|
|[CObList:: Find](#find)|Ruft die Position eines Elements ab, das durch einen Zeiger Wert angegeben wird.|
|[CObList:: FindIndex](#findindex)|Ruft die Position eines Elements ab, das durch einen NULL basierten Index angegeben wird.|
|[CObList:: GetAt](#getat)|Ruft das Element an einer angegebenen Position ab.|
|[CObList:: GetCount](#getcount)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CObList:: gezeige AD](#gethead)|Gibt das Head-Element der Liste zurück (darf nicht leer sein).|
|[CObList:: GE-Adposition](#getheadposition)|Gibt die Position des Head-Elements der Liste zurück.|
|[CObList:: GetNext](#getnext)|Ruft das nächste Element für die Iteration ab.|
|[CObList:: GetPrev](#getprev)|Ruft das vorherige Element für die Iteration ab.|
|[CObList:: GetSize](#getsize)|Gibt die Anzahl der Elemente in dieser Liste zurück.|
|[CObList:: gettail](#gettail)|Gibt das Tail-Element der Liste zurück (darf nicht leer sein).|
|[CObList:: gettailposition](#gettailposition)|Gibt die Position des Tail-Elements der Liste zurück.|
|[CObList:: InsertAfter](#insertafter)|Fügt ein neues Element nach einer angegebenen Position ein.|
|[CObList:: InsertBefore](#insertbefore)|Fügt ein neues Element vor einer angegebenen Position ein.|
|[CObList:: IsEmpty](#isempty)|Testet auf die leere Listen Bedingung (keine Elemente).|
|[CObList:: RemoveAll](#removeall)|Entfernt alle Elemente aus dieser Liste.|
|[CObList:: RemoveAt](#removeat)|Entfernt ein Element aus dieser Liste, das durch die Position angegeben wird.|
|[CObList:: RemoveHead](#removehead)|Entfernt das Element am Anfang der Liste.|
|[CObList:: removetail](#removetail)|Entfernt das Element aus dem Ende der Liste.|
|[CObList::](#setat)|Legt das Element an einer angegebenen Position fest.|

## <a name="remarks"></a>Bemerkungen

`CObList` Listen Verhalten sich wie doppelt verknüpfte Listen.

Eine Variable vom Typ Position ist ein Schlüssel für die Liste. Sie können eine Positions Variable sowohl als Iterator verwenden, um eine Liste sequenziell zu durchlaufen, als auch als Lesezeichen, um einen Ort zu speichern. Eine Position ist jedoch nicht mit einem Index identisch.

Das Einfügen von Elementen ist am Listen Kopf am Ende und an einer bekannten Position sehr schnell. Eine sequenzielle Suche ist erforderlich, um ein Element nach Wert oder Index zu suchen. Diese Suche kann langsam sein, wenn die Liste lang ist.

`CObList` enthält das IMPLEMENT_SERIAL-Makro, um die Serialisierung und das Absichern der zugehörigen Elemente zu unterstützen. Wenn eine Liste von `CObject` Zeigern in einem Archiv gespeichert wird, entweder mit einem überladenen einfügeoperator oder mit der `Serialize` Member-Funktion, wird jedes `CObject` Element nacheinander serialisiert.

Wenn Sie ein Abbild einzelner `CObject` Elemente in der Liste benötigen, müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Wenn ein `CObList` Objekt gelöscht wird oder wenn seine Elemente entfernt werden, werden nur die `CObject` Zeiger entfernt, nicht die Objekte, auf die Sie verweisen.

Sie können Ihre eigenen Klassen von `CObList`ableiten. Die neue List-Klasse, die Zeiger auf Objekte enthalten soll, die von `CObject`abgeleitet sind, fügt neue Datenmember und neue Element Funktionen hinzu. Beachten Sie, dass die resultierende Liste nicht streng typsicher ist, da Sie das Einfügen eines beliebigen `CObject` Zeigers ermöglicht.

> [!NOTE]
>  Sie müssen das [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) -Makro in der Implementierung der abgeleiteten Klasse verwenden, wenn Sie beabsichtigen, die Liste zu serialisieren.

Weitere Informationen zur Verwendung von `CObList`finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

##  <a name="addhead"></a>CObList:: AddHead

Fügt dem Anfang dieser Liste ein neues Element oder eine Liste von Elementen hinzu.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Parameter

*newElement*<br/>
Der `CObject` Zeiger, der der Liste hinzugefügt werden soll.

*pnewlist*<br/>
Ein Zeiger auf eine andere `CObList` Liste. Die Elemente in " *pnewlist* " werden der Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den Positionswert des neu eingefügten Elements zurück.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::AddHead`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**AddHead positionieren (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position AddHead (Konstante CString &** `newElement` **);**<br /><br /> **Position AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Bemerkungen

Die Liste kann vor dem Vorgang leer sein.

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>CObList:: AddTail

Fügt dem Ende dieser Liste ein neues Element oder eine Liste von Elementen hinzu.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Parameter

*newElement*<br/>
Der `CObject` Zeiger, der der Liste hinzugefügt werden soll.

*pnewlist*<br/>
Ein Zeiger auf eine andere `CObList` Liste. Die Elemente in " *pnewlist* " werden der Liste hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt den Positionswert des neu eingefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Die Liste kann vor dem Vorgang leer sein.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::AddTail`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**AddTail positionieren (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position AddTail (Konstante CString &** `newElement` **);**<br /><br /> **Position AddTail (LPCTSTR** `newElement` **);**<br /><br /> **void AddTail (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>CObList:: CObList

Erstellt eine leere `CObject` Zeiger Liste.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parameter

*nblocksize*<br/>
Die Granularität der Speicher Belegung für die Erweiterung der Liste.

### <a name="remarks"></a>Bemerkungen

Wenn die Liste zunimmt, wird der Arbeitsspeicher in Einheiten von *nblocksize* -Einträgen zugeordnet. Wenn eine Speicher Belegung fehlschlägt, wird eine `CMemoryException` ausgelöst.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::CObList`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Beispiel

  Im folgenden finden Sie eine Liste der `CObject`abgeleiteten Klasse `CAge` die in allen Sammlungs Beispielen verwendet wird:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Im folgenden finden Sie ein Beispiel für die Verwendung `CObList` Konstruktors:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>CObList:: Find

Durchsucht die Liste sequenziell, um den ersten `CObject` Zeiger zu finden, der mit dem angegebenen `CObject` Zeiger übereinstimmt.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parameter

*searchValue*<br/>
Der Objekt Zeiger, der in dieser Liste gefunden werden soll.

*startafter*<br/>
Die Startposition für die Suche.

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn das Objekt nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass die Zeiger Werte und nicht der Inhalt der-Objekte verglichen werden.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::Find`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position suchen (void** <strong>\*</strong> `searchValue` **, Position** `startAfter` **= null) Konstanten;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position suchen (LPCTSTR** `searchValue` **, Position** `startAfter` **= null) Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>CObList:: FindIndex

Verwendet den Wert von *nIndex* als Index in der Liste.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der null basierte Index des Listen Elements, das gefunden werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn *nIndex* zu groß ist. (Das Framework generiert eine-Assertion, wenn *nIndex* negativ ist.)

### <a name="remarks"></a>Bemerkungen

Dabei wird ein sequenzieller Scan von der Spitze der Liste gestartet, wobei das *n*-te Element angehalten wird.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::FindIndex`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position FindIndex (INT_PTR** `nIndex` **) Konstanten;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position FindIndex (INT_PTR** `nIndex` **) Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>CObList:: GetAt

Eine Variable vom Typ Position ist ein Schlüssel für die Liste.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parameter

*position*<br/>
Ein Positionswert, der von einem vorherigen `GetHeadPosition` oder `Find` Member-Funktions aufrufzurück gegeben wurde.

### <a name="return-value"></a>Rückgabewert

Weitere Informationen finden Sie in der Beschreibung des Rückgabewerts für [gezeige AD](#gethead).

### <a name="remarks"></a>Bemerkungen

Sie ist nicht mit einem Index identisch, und Sie können selbst keinen Positionswert verwenden. `GetAt` Ruft den `CObject` Zeiger ab, der einer bestimmten Position zugeordnet ist.

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::GetAt`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|Konstante **void\*& GetAt (Positions** *Position* **) Konstanten;**<br /><br /> **void\*& GetAt (Positions** *Position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|Konstante **CString-& GetAt (Positions** *Position* **) Konstanten;**<br /><br /> **CString & GetAt (Positions** *Position* **);**|

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [FindIndex](#findindex).

##  <a name="getcount"></a>CObList:: GetCount

Ruft die Anzahl der Elemente in dieser Liste ab.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Ein ganzzahliger Wert, der die Element Anzahl enthält.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::GetCount`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount () Konstanten;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount () Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>CObList:: gezeige AD

Ruft den `CObject` Zeiger ab, der das Head-Element dieser Liste darstellt.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn der Zugriff auf die Liste über einen Zeiger auf einen `const CObList`erfolgt, gibt `GetHead` einen `CObject`-Zeiger zurück. Dies ermöglicht die Verwendung der-Funktion nur auf der rechten Seite einer Zuweisungsanweisung und schützt somit die Liste vor Änderungen.

Wenn der Zugriff auf die Liste direkt oder über einen Zeiger auf einen `CObList`erfolgt, gibt `GetHead` einen Verweis auf einen `CObject`-Zeiger zurück. Dies ermöglicht die Verwendung der-Funktion auf beiden Seiten einer Zuweisungsanweisung und ermöglicht so, dass die Listeneinträge geändert werden.

### <a name="remarks"></a>Bemerkungen

Vor dem Aufrufen von `GetHead`müssen Sie sicherstellen, dass die Liste nicht leer ist. Wenn die Liste leer ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert. Verwenden Sie [IsEmpty](#isempty) , um zu überprüfen, ob die Liste Elemente enthält.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::GetHead`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Konstante void\*& gezeige AD () Konstanten; void\*& gezeige AD ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Konstante CString & gezeige AD () Konstanten; CString & gezeige AD ();**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

Im folgenden Beispiel wird die Verwendung von `GetHead` auf der linken Seite einer Zuweisungsanweisung veranschaulicht.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>CObList:: GE-Adposition

Ruft die Position des Head-Elements dieser Liste ab.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn die Liste leer ist.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::GetHeadPosition`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position von gezeige Adposition () Konstanten;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position von gezeige Adposition () Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>CObList:: GetNext

Ruft das von *rPosition*identifizierte Listenelement ab und legt dann *rPosition* auf den `POSITION` Wert des nächsten Eintrags in der Liste fest.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*rPosition zurück*<br/>
Ein Verweis auf einen Positionswert, der von einem vorherigen `GetNext`, `GetHeadPosition`oder einem anderen Element Funktions Aufrufwert zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Weitere Informationen finden Sie in der Beschreibung des Rückgabewerts für [gezeige AD](#gethead).

### <a name="remarks"></a>Bemerkungen

Sie können `GetNext` in einer Forward-Iterations Schleife verwenden, wenn Sie die ursprüngliche Position mit einem `GetHeadPosition`-oder `Find`-Aufrufpunkt einrichten.

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

Wenn das abgerufene Element das letzte in der Liste ist, wird der neue Wert von *rPosition* auf NULL festgelegt.

Es ist möglich, ein Element während einer Iterationen zu entfernen. Weitere Informationen finden Sie im Beispiel für [RemoveAt](#removeat).

> [!NOTE]
>  Seit MFC 8,0 hat sich die Konstante Version dieser Methode geändert, sodass anstelle von `const CObject*&``const CObject*` zurückgegeben wird.  Diese Änderung wurde vorgenommen, um den Compiler in Übereinstimmung mit dem C++ Standard zu bringen.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::GetNext`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>CObList:: GetPrev

Ruft das von *rPosition*identifizierte Listenelement ab und legt dann *rPosition* auf den Positionswert des vorherigen Eintrags in der Liste fest.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parameter

*rPosition zurück*<br/>
Ein Verweis auf einen Positionswert, der von einem vorherigen `GetPrev` oder einem anderen Element Funktions Aufrufwert zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Weitere Informationen finden Sie in der Beschreibung des Rückgabewerts für [gezeige AD](#gethead).

### <a name="remarks"></a>Bemerkungen

Sie können `GetPrev` in einer Reverse-Iterations Schleife verwenden, wenn Sie die ursprüngliche Position mit einem `GetTailPosition`-oder `Find`-Aufrufpunkt einrichten.

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

Wenn das abgerufene Element das erste Element in der Liste ist, wird der neue Wert von *rPosition* auf NULL festgelegt.

> [!NOTE]
>  Seit MFC 8,0 hat sich die Konstante Version dieser Methode geändert, sodass anstelle von `const CObject*&``const CObject*` zurückgegeben wird.  Diese Änderung wurde vorgenommen, um den Compiler in Übereinstimmung mit dem C++ Standard zu bringen.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::GetPrev`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>CObList:: GetSize

Gibt die Anzahl der Listenelemente zurück.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Liste.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Liste abzurufen.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::GetSize`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize () Konstanten;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize () Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>CObList:: gettail

Ruft den `CObject` Zeiger ab, der das Endelement dieser Liste darstellt.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Rückgabewert

Weitere Informationen finden Sie in der Beschreibung des Rückgabewerts für [gezeige AD](#gethead).

### <a name="remarks"></a>Bemerkungen

Vor dem Aufrufen von `GetTail`müssen Sie sicherstellen, dass die Liste nicht leer ist. Wenn die Liste leer ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert. Verwenden Sie [IsEmpty](#isempty) , um zu überprüfen, ob die Liste Elemente enthält.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::GetTail`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Konstante void\*& gettail () Konstanten; void\*& gettail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Konstante CString & gettail () Konstanten; CString & gettail ();**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>CObList:: gettailposition

Ruft die Position des Tail-Elements dieser Liste ab. **Null** , wenn die Liste leer ist.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn die Liste leer ist.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::GetTailPosition`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position gettailposition () Konstanten;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position gettailposition () Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>CObList:: InsertAfter

Fügt dieser Liste nach dem-Element an der angegebenen Position ein Element hinzu.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*position*<br/>
Ein Positionswert, der von einem vorherigen `GetNext`, `GetPrev`oder `Find` Member-Funktions aufrufzurück gegeben wurde.

*newElement*<br/>
Der Objekt Zeiger, der der Liste hinzugefügt werden soll.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::InsertAfter`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position InsertAfter (Positions** *Position* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position InsertAfter (Positions** *Position* **, Konstante CString &** `newElement` **);**<br /><br /> **Position InsertAfter (Positions** *Position* **, LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der mit dem *Positions* Parameter identisch ist.

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>CObList:: InsertBefore

Fügt dieser Liste ein Element vor dem Element an der angegebenen Position hinzu.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*position*<br/>
Ein Positionswert, der von einem vorherigen `GetNext`, `GetPrev`oder `Find` Member-Funktions aufrufzurück gegeben wurde.

*newElement*<br/>
Der Objekt Zeiger, der der Liste hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der zum Abrufen von Iterationen oder Objekt Zeigern verwendet werden kann. NULL, wenn die Liste leer ist.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::InsertBefore`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position InsertBefore (Positions** *Position* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position InsertBefore (Positions** *Position* **, Konstante CString &** `newElement` **);**<br /><br /> **Position InsertBefore (Positions** *Position* **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>CObList:: IsEmpty

Gibt an, ob diese Liste keine Elemente enthält.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn diese Liste leer ist. andernfalls 0.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::IsEmpty`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Bool IsEmpty () Konstanten;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Bool IsEmpty () Konstanten;**|

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [RemoveAll](#removeall).

##  <a name="removeall"></a>CObList:: RemoveAll

Entfernt alle Elemente aus dieser Liste und gibt den zugeordneten `CObList` Arbeitsspeicher frei.

```
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Wenn die Liste bereits leer ist, wird kein Fehler generiert.

Wenn Sie Elemente aus einer `CObList`entfernen, entfernen Sie die Objekt Zeiger aus der Liste. Es liegt in ihrer Verantwortung, die Objekte selbst zu löschen.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::RemoveAll`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>CObList:: RemoveAt

Entfernt das angegebene Element aus der Liste.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parameter

*position*<br/>
Die Position des Elements, das aus der Liste entfernt werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Element aus einer `CObList`entfernen, entfernen Sie den Objekt Zeiger aus der Liste. Es liegt in ihrer Verantwortung, die Objekte selbst zu löschen.

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::RemoveAt`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (Positions** *Position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (Positions** *Position* **);**|

### <a name="example"></a>Beispiel

  Seien Sie vorsichtig, wenn Sie ein Element während einer Listen Iterations Liste entfernen. Das folgende Beispiel zeigt eine Entfernungs Technik, die einen gültigen **Positions** Wert für [GetNext](#getnext)sicherstellt.

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>CObList:: RemoveHead

Entfernt das Element am Anfang der Liste und gibt einen Zeiger darauf zurück.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Rückgabewert

Der `CObject` Zeiger zuvor am Anfang der Liste.

### <a name="remarks"></a>Bemerkungen

Vor dem Aufrufen von `RemoveHead`müssen Sie sicherstellen, dass die Liste nicht leer ist. Wenn die Liste leer ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert. Verwenden Sie [IsEmpty](#isempty) , um zu überprüfen, ob die Liste Elemente enthält.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::RemoveHead`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead ();**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>CObList:: removetail

Entfernt das Element aus dem Ende der Liste und gibt einen Zeiger darauf zurück.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Objekt, das sich am Ende der Liste befand.

### <a name="remarks"></a>Bemerkungen

Vor dem Aufrufen von `RemoveTail`müssen Sie sicherstellen, dass die Liste nicht leer ist. Wenn die Liste leer ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert. Verwenden Sie [IsEmpty](#isempty) , um zu überprüfen, ob die Liste Elemente enthält.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::RemoveTail`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* removetail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString removetail ();**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>CObList::

Legt das Element an einer angegebenen Position fest.

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*pos*<br/>
Die Position des festzulegenden Elements.

*newElement*<br/>
Der `CObject` Zeiger, der in die Liste geschrieben werden soll.

### <a name="remarks"></a>Bemerkungen

Eine Variable vom Typ Position ist ein Schlüssel für die Liste. Sie ist nicht mit einem Index identisch, und Sie können selbst keinen Positionswert verwenden. `SetAt` schreibt den `CObject` Zeiger an die angegebene Position in der Liste.

Sie müssen sicherstellen, dass der Positionswert eine gültige Position in der Liste darstellt. Wenn Sie ungültig ist, wird die Debugversion des Microsoft Foundation Class-Bibliothek Assert.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CObList::SetAt`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void-Ausdruck (Positions** `pos` **, Konstante CString &** `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void-Aktivität (Position** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Beispiel

  Eine Auflistung der `CAge`-Klasse finden Sie unter [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

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
