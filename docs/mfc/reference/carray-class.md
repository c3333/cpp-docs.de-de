---
title: CArray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: f73666f3a20488d14a82b7c56d682f3f5b2386df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195173"
---
# <a name="carray-class"></a>CArray-Klasse

Unterstützt Arrays, die wie C-Arrays aussehen, aber je nach Bedarf dynamisch reduzieren und vergrößern können.

## <a name="syntax"></a>Syntax

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der im Array gespeicherten Objekte angibt. *Type* ist ein Parameter, der von zurückgegeben wird `CArray` .

*ARG_TYPE*<br/>
Ein Vorlagen Parameter, der den Argumenttyp angibt, der verwendet wird, um auf im Array gespeicherte Objekte zuzugreifen. Häufig ein Verweis auf den *Typ*. *Arg_type* ist ein Parameter, der an übergeben wird `CArray` .

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CArray:: CArray](#carray)|Erstellt ein leeres Array.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CArray:: Add](#add)|Fügt am Ende des Arrays ein Element hinzu; vergrößert das Array bei Bedarf.|
|[CArray:: Append](#append)|Fügt ein anderes Array an das Array an. vergrößert das Array bei Bedarf|
|[CArray:: Copy](#copy)|Kopiert ein anderes Array in das Array; vergrößert das Array bei Bedarf.|
|[CArray:: ElementAt](#elementat)|Gibt einen temporären Verweis auf den Elementzeiger innerhalb des Arrays zurück.|
|[CArray:: freextra](#freeextra)|Gibt den gesamten nicht verwendeten Arbeitsspeicher über der aktuellen Obergrenze frei.|
|[CArray:: GetAt](#getat)|Gibt den Wert an einem bestimmten Index zurück.|
|[CArray:: GetCount](#getcount)|Ruft die Anzahl der Elemente im Array ab.|
|[CArray:: GetData](#getdata)|Ermöglicht den Zugriff auf Elemente im Array. Kann den Wert NULL haben.|
|[CArray:: GetSize](#getsize)|Ruft die Anzahl der Elemente im Array ab.|
|[CArray:: GetUpperBound](#getupperbound)|Gibt den größten gültigen Index zurück.|
|[CArray:: InsertAt](#insertat)|Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.|
|[CArray:: IsEmpty](#isempty)|Bestimmt, ob das Array leer ist.|
|[CArray:: RemoveAll](#removeall)|Entfernt alle Elemente aus diesem Array.|
|[CArray:: RemoveAt](#removeat)|Entfernt ein Element an einem spezifischen Index.|
|[CArray:: *](#setat)|Legt den Wert für einen bestimmten Index fest; Array darf nicht vergrößert werden.|
|[CArray:: antatgrow](#setatgrow)|Legt den Wert für einen bestimmten Index fest; vergrößert das Array bei Bedarf.|
|[CArray:: SetSize](#setsize)|Legt die Anzahl der Elemente im Array fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|Legt das Element am angegebenen Index fest oder ruft es ab.|

## <a name="remarks"></a>Bemerkungen

Array Indizes beginnen immer an Position 0. Sie können entscheiden, ob die obere Grenze behoben oder das Array erweitert werden soll, wenn Sie Elemente hinter der aktuellen Grenze hinzufügen. Der Arbeitsspeicher wird der oberen Grenze zusammenhängend zugewiesen, auch wenn einige Elemente NULL sind.

> [!NOTE]
> Bei den meisten Methoden, die die Größe eines- `CArray` Objekts ändern oder Elemente hinzufügen, wird [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) zum Verschieben von Elementen verwendet. Dies ist ein Problem `memcpy_s` , da nicht mit Objekten kompatibel ist, für die der Konstruktor aufgerufen werden muss. Wenn die Elemente in `CArray` nicht mit kompatibel sind `memcpy_s` , müssen Sie eine neue `CArray` der entsprechenden Größe erstellen. Anschließend müssen Sie [CArray:: Copy](#copy) und [CArray::](#setat) * verwenden, um das neue Array zu füllen, da diese Methoden einen Zuweisungs Operator anstelle von verwenden `memcpy_s` .

Wie bei einem C-Array ist die Zugriffszeit für ein `CArray` indiziertes Element konstant und unabhängig von der Array Größe.

> [!TIP]
> Bevor Sie ein Array verwenden, verwenden Sie [SetSize](#setsize) , um seine Größe festzulegen und Arbeitsspeicher zuzuweisen. Wenn Sie `SetSize` nicht verwenden, kann das Hinzufügen von Elementen zu Ihrem Array dazu führen, dass es häufig neu zugeordnet und kopiert wird. Häufige Neuzuordnungen und Kopiervorgänge sind ineffizient und können zu einer Fragmentierung des Arbeitsspeichers führen.

Wenn Sie ein Abbild einzelner Elemente in einem Array benötigen, müssen Sie die Tiefe des [CDumpContext](../../mfc/reference/cdumpcontext-class.md) -Objekts auf 1 oder größer festlegen.

Bestimmte Element Funktionen dieser Klasse können globale Hilfsfunktionen aufzurufen, die für die meisten Verwendungen der-Klasse angepasst werden müssen `CArray` . Weitere Informationen finden Sie in den Themen Auflistungs [Klassen](../../mfc/reference/collection-class-helpers.md) Hilfsprogramme im Abschnitt MFC-Makros und Globals.

Die Ableitung der Array Klasse ist wie die Listen Ableitung.

Weitere Informationen zur Verwendung von finden Sie `CArray` im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a>CArray:: Add

Fügt am Ende eines Arrays ein neues Element hinzu, wobei das Array um 1 vergrößert wird.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*ARG_TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Argumente angibt, die auf Elemente in diesem Array verweisen.

*newElement*<br/>
Das Element, das diesem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des hinzugefügten Elements.

### <a name="remarks"></a>Bemerkungen

Wenn [SetSize](#setsize) mit einem `nGrowBy` Wert größer als 1 verwendet wurde, kann zusätzlicher Arbeitsspeicher zugeordnet werden. Die obere Grenze wird jedoch nur um 1 erhöht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a>CArray:: Append

Diese Member-Funktion wird aufgerufen, um den Inhalt eines Arrays am Ende eines anderen Arrays hinzuzufügen.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
Quelle der Elemente, die an ein Array angefügt werden sollen.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten angefügten Elements.

### <a name="remarks"></a>Bemerkungen

Die Arrays müssen denselben Typ aufweisen.

Bei Bedarf `Append` kann zusätzlichen Arbeitsspeicher zuordnen, um die an das Array angefügten Elemente anzupassen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a>CArray:: CArray

Erstellt ein leeres Array.

```
CArray();
```

### <a name="remarks"></a>Bemerkungen

Das Array wächst jeweils ein Element.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a>CArray:: Copy

Verwenden Sie diese Member-Funktion, um die Elemente eines Arrays in ein anderes Array zu kopieren.

```cpp
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
Quelle der Elemente, die in ein Array kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird aufgerufen, um die Elemente eines Arrays mit den Elementen eines anderen Arrays zu überschreiben.

`Copy`gibt keinen Arbeitsspeicher frei; bei Bedarf `Copy` kann jedoch zusätzlichen Arbeitsspeicher zuordnen, um die Elemente zu verarbeiten, die in das Array kopiert werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a>CArray:: ElementAt

Gibt einen temporären Verweis auf das angegebene Element innerhalb des Arrays zurück.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem von [GetUpperBound](#getupperbound)zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein Array Element.

### <a name="remarks"></a>Bemerkungen

Es wird verwendet, um den linksseitigen Zuweisungs Operator für Arrays zu implementieren.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für " [GetSize](#getsize)".

## <a name="carrayfreeextra"></a><a name="freeextra"></a>CArray:: freextra

Gibt zusätzlichen Arbeitsspeicher frei, der zugeordnet wurde, während das Array vergrößert wurde.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion hat keine Auswirkung auf die Größe oder die obere Grenze des Arrays.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für " [GetData](#getdata)".

## <a name="carraygetat"></a><a name="getat"></a>CArray:: GetAt

Gibt das Array Element am angegebenen Index zurück.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Array Elemente angibt.

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem von [GetUpperBound](#getupperbound)zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Das Array Element, das sich derzeit an diesem Index befinden.

### <a name="remarks"></a>Bemerkungen

Wenn ein negativer Wert oder ein Wert, der größer als der von zurückgegebene Wert ist, übergeben `GetUpperBound` wird, führt dies zu einer fehlgeschlagenen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a>CArray:: GetCount

Gibt die Anzahl der Array Elemente zurück.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Array.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente im Array abzurufen. Da Indizes NULL basiert sind, ist die Größe 1 größer als der größte Index. Wenn Sie diese Methode aufrufen, wird dasselbe Ergebnis wie bei der [CArray:: GetSize](#getsize) -Methode generiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a>CArray:: GetData

Verwenden Sie diese Member-Funktion, um direkten Zugriff auf die Elemente in einem Array zu erhalten.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Array Elemente angibt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Array Element.

### <a name="remarks"></a>Bemerkungen

Wenn keine Elemente verfügbar sind, wird `GetData` ein NULL-Wert zurückgegeben.

Während der direkte Zugriff auf die Elemente eines Arrays Ihnen helfen kann, schneller zu arbeiten, sollten Sie beim Aufrufen von Vorsicht walten `GetData` lassen. alle Fehler, die Sie direkt vornehmen, wirken sich direkt auf die Elemente des Arrays aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a>CArray:: GetSize

Gibt die Größe des Arrays zurück.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Bemerkungen

Da Indizes NULL basiert sind, ist die Größe 1 größer als der größte Index. Wenn Sie diese Methode aufrufen, wird dasselbe Ergebnis wie bei der [CArray:: GetCount](#getcount) -Methode generiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a>CArray:: GetUpperBound

Gibt die aktuelle obere Grenze dieses Arrays zurück.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Bemerkungen

Da Array Indizes NULL basiert sind, gibt diese Funktion einen Wert zurück, der kleiner als ist `GetSize` .

Die Bedingung `GetUpperBound( )` =-1 gibt an, dass das Array keine Elemente enthält.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CArray:: GetAt](#getat).

## <a name="carrayinsertat"></a><a name="insertat"></a>CArray:: InsertAt

Die erste Version von `InsertAt` Fügt ein Element (oder mehrere Kopien eines Elements) an einem angegebenen Index in einem Array ein.

```cpp
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der möglicherweise größer als der von zurückgegebene Wert ist `GetUpperBound` .

*ARG_TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente in diesem Array angibt.

*newElement*<br/>
Das Element, das in diesem Array platziert werden soll.

*nCount*<br/>
Gibt an, wie oft dieses Element eingefügt werden soll (Standardwert ist 1).

*nstartindex*<br/>
Ein ganzzahliger Index, der möglicherweise größer als der von [GetUpperBound](#getupperbound)zurückgegebene Wert ist.

*pberwarray*<br/>
Ein weiteres Array, das Elemente enthält, die diesem Array hinzugefügt werden sollen.

### <a name="remarks"></a>Bemerkungen

Beim Prozess wird das vorhandene Element an diesem Index (durch Inkrementieren des Indexes) nach oben verschoben, und alle darin liegenden Elemente werden verschoben.

In der zweiten Version werden alle Elemente aus einer anderen Auflistung eingefügt `CArray` , beginnend an der *nstartindex* -Position.

Die `SetAt` -Funktion ersetzt dagegen ein angegebenes Array Element und verschiebt keine Elemente.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a>CArray:: IsEmpty

Bestimmt, ob das Array leer ist.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Array keine Elemente enthält; andernfalls 0.

## <a name="carrayoperator-"></a><a name="operator_at"></a>CArray::-Operator\[\]

Diese tief gestellten Operatoren sind eine bequeme Ersetzung für [die Funktionen](#setat) "-Funktion" und " [GetAt](#getat) ".

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente in diesem Array angibt.

*nIndex*<br/>
Der Index des Elements, auf das zugegriffen werden soll.

### <a name="remarks"></a>Bemerkungen

Der erste Operator, der für Arrays aufgerufen wird, die nicht sind **`const`** , kann entweder auf der rechten Seite (r-Wert) oder auf der linken Seite (l-Wert) einer Zuweisungsanweisung verwendet werden. Die zweite, die für **`const`** Arrays aufgerufen wird, kann nur auf der rechten Seite verwendet werden.

Die Debugversion der Bibliothek bestätigt, ob der Index (entweder auf der linken oder rechten Seite einer Zuweisungsanweisung) außerhalb des gültigen Bereichs liegt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a>CArray:: relocateelements

Gibt Daten in einem neuen Puffer neu, wenn das Array vergrößert oder verkleinert werden soll.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parameter

*pnewdata*<br/>
Ein neuer Puffer für das Array von-Elementen.

*pData*<br/>
Das alte Array von-Elementen.

*nCount*<br/>
Anzahl der Elemente im alten Array.

### <a name="remarks"></a>Bemerkungen

*pnewdata* ist immer groß genug, um alle *pData* -Elemente aufzunehmen.

Die [CArray](../../mfc/reference/carray-class.md) -Implementierung verwendet diese Methode, um die alten Daten in einen neuen Puffer zu kopieren, wenn das Array vergrößert oder verkleinert werden soll (wenn [SetSize](#setsize) oder " [freextra](#freeextra) " aufgerufen wird). Die Standard Implementierung kopiert nur die Daten.

Für Arrays, bei denen ein Element einen Zeiger auf einen seiner eigenen Member enthält, oder eine andere Struktur einen Zeiger auf eines der Array Elemente enthält, werden die Zeiger nicht in der einfachen Kopie aktualisiert. In diesem Fall können Sie Zeiger korrigieren, indem Sie eine Spezialisierung von `RelocateElements` mit den entsprechenden Typen implementieren. Sie sind auch für das Kopieren von Daten verantwortlich.

## <a name="carrayremoveall"></a><a name="removeall"></a>CArray:: RemoveAll

Entfernt alle Elemente aus diesem Array.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Array bereits leer ist, funktioniert die Funktion weiterhin.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a>CArray:: RemoveAt

Entfernt ein oder mehrere Elemente, beginnend bei einem angegebenen Index in einem Array.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem von [GetUpperBound](#getupperbound)zurückgegebenen Wert ist.

*nCount*<br/>
Die Anzahl der zu entfernenden Elemente.

### <a name="remarks"></a>Bemerkungen

Im Prozess werden alle Elemente oberhalb der entfernten Elemente nach unten verschoben. Die obere Grenze des Arrays wird verringert, aber es wird kein Arbeitsspeicher freigegeben.

Wenn Sie versuchen, mehr Elemente zu entfernen, als im Array oberhalb des Entfernungs Punkts enthalten sind, wird die Debugversion der Bibliothek bestätigt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a>CArray:: *

Legt das Array Element am angegebenen Index fest.

```cpp
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem von [GetUpperBound](#getupperbound)zurückgegebenen Wert ist.

*ARG_TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Argumente angibt, die zum Verweisen auf Array Elemente verwendet werden.

*newElement*<br/>
Der neue Elementwert, der an der angegebenen Position gespeichert werden soll.

### <a name="remarks"></a>Bemerkungen

`SetAt`bewirkt nicht, dass das Array vergrößert wird. Verwenden Sie " [tartatgrow](#setatgrow) ", wenn das Array automatisch vergrößert werden soll.

Sie müssen sicherstellen, dass der Indexwert eine gültige Position im Array darstellt. Wenn Sie außerhalb des gültigen Bereichs liegt, wird die Debugversion der Bibliothek bestätigt.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [GetAt](#getat).

## <a name="carraysetatgrow"></a><a name="setatgrow"></a>CArray:: antatgrow

Legt das Array Element am angegebenen Index fest.

```cpp
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 (null) ist.

*ARG_TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente im Array angibt.

*newElement*<br/>
Das Element, das diesem Array hinzugefügt werden soll. Ein NULL-Wert ist zulässig.

### <a name="remarks"></a>Bemerkungen

Das Array wird bei Bedarf automatisch vergrößert (d. h., die obere Grenze wird an das neue Element angepasst).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a>CArray:: SetSize

Legt die Größe eines leeren oder vorhandenen Arrays fest. weist bei Bedarf Arbeitsspeicher zu.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parameter

*nnewSize*<br/>
Die neue Array Größe (Anzahl der Elemente). Muss mindestens 0 sein.

*ngrowby*<br/>
Die Mindestanzahl der zuzuordnenden Element Slots, wenn eine Größen Erhöhung erforderlich ist.

### <a name="remarks"></a>Bemerkungen

Wenn die neue Größe kleiner als die alte Größe ist, wird das Array abgeschnitten, und es wird der gesamte nicht verwendete Arbeitsspeicher freigegeben.

Verwenden Sie diese Funktion, um die Größe des Arrays festzulegen, bevor Sie mit der Verwendung des Arrays beginnen. Wenn Sie `SetSize` nicht verwenden, kann das Hinzufügen von Elementen zu Ihrem Array dazu führen, dass es häufig neu zugeordnet und kopiert wird. Häufige Neuzuordnungen und Kopiervorgänge sind ineffizient und können zu einer Fragmentierung des Arbeitsspeichers führen.

Der *ngrowby* -Parameter wirkt sich auf die interne Speicher Belegung aus, während das Array wächst. Seine Verwendung wirkt sich nie auf die Array Größe aus, die von [GetSize](#getsize) und [GetUpperBound](#getupperbound)gemeldet wird. Wenn der Standardwert verwendet wird, ordnet MFC Speicher in einer berechneten Weise zu, um Speicherfragmentierung zu vermeiden und die Effizienz für die meisten Fälle zu optimieren.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für " [GetData](#getdata)".

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel Sammlung](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CObArray-Klasse](../../mfc/reference/cobarray-class.md)<br/>
[Auflistungs Klassen Hilfsprogramme](../../mfc/reference/collection-class-helpers.md)
