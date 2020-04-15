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
ms.openlocfilehash: 2c520a732edf54ebb36c07728ceb19791b351143
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377027"
---
# <a name="carray-class"></a>CArray-Klasse

Unterstützt Arrays, die wie C-Arrays sind, aber bei Bedarf dynamisch reduzieren und wachsen können.

## <a name="syntax"></a>Syntax

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der im Array gespeicherten Objekte angibt. *TYPE* ist ein Parameter, `CArray`der von zurückgegeben wird.

*ARG_TYPE*<br/>
Vorlagenparameter, der den Argumenttyp angibt, der für den Zugriff auf im Array gespeicherte Objekte verwendet wird. Oft ein Verweis auf *TYPE*. *ARG_TYPE* ist ein Parameter, `CArray`der an übergeben wird.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CArray::CArray](#carray)|Erstellt ein leeres Array.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CArray::Hinzufügen](#add)|Fügt am Ende des Arrays ein Element hinzu; vergrößert das Array bei Bedarf.|
|[CArray::Anfügen](#append)|Fügt ein anderes Array an das Array an. vergrößert das Array bei Bedarf|
|[CArray::Kopieren](#copy)|Kopiert ein anderes Array in das Array; vergrößert das Array bei Bedarf.|
|[CArray::ElementAt](#elementat)|Gibt einen temporären Verweis auf den Elementzeiger innerhalb des Arrays zurück.|
|[CArray::FreeExtra](#freeextra)|Gibt den gesamten nicht verwendeten Arbeitsspeicher über der aktuellen Obergrenze frei.|
|[CArray::GetAt](#getat)|Gibt den Wert an einem bestimmten Index zurück.|
|[CArray::GetCount](#getcount)|Ruft die Anzahl der Elemente im Array ab.|
|[CArray::GetData](#getdata)|Ermöglicht den Zugriff auf Elemente im Array. Kann den Wert NULL haben.|
|[CArray::GetSize](#getsize)|Ruft die Anzahl der Elemente im Array ab.|
|[CArray::GetUpperBound](#getupperbound)|Gibt den größten gültigen Index zurück.|
|[CArray::InsertAt](#insertat)|Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.|
|[CArray::IsEmpty](#isempty)|Bestimmt, ob das Array leer ist.|
|[CArray::Alle entfernen](#removeall)|Entfernt alle Elemente aus diesem Array.|
|[CArray::RemoveAt](#removeat)|Entfernt ein Element an einem spezifischen Index.|
|[CArray::SetAt](#setat)|Legt den Wert für einen bestimmten Index fest; Array darf nicht vergrößert werden.|
|[CArray::SetatGrow](#setatgrow)|Legt den Wert für einen bestimmten Index fest; vergrößert das Array bei Bedarf.|
|[CArray::SetSize](#setsize)|Legt die Anzahl der Elemente im Array fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|Legt das Element am angegebenen Index fest oder ruft es ab.|

## <a name="remarks"></a>Bemerkungen

Arrayindizes beginnen immer an Position 0. Sie können entscheiden, ob die obere Grenze behoben werden soll, oder ob das Array erweitert werden soll, wenn Sie Elemente über die aktuelle Grenze hinaus hinzufügen. Der Speicher wird der oberen Grenze zusammenhängend zugewiesen, auch wenn einige Elemente null sind.

> [!NOTE]
> Die meisten Methoden, `CArray` die die Größe eines Objekts ändern oder ihm Elemente hinzufügen, verwenden [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) zum Verschieben von Elementen. Dies ist `memcpy_s` ein Problem, da es nicht mit Objekten kompatibel ist, für die der Konstruktor aufgerufen werden muss. Wenn die Elemente `CArray` in der `memcpy_s`nicht kompatibel sind, müssen Sie eine neue `CArray` Größe in der erstellen. Sie müssen dann [CArray::Copy](#copy) und [CArray::SetAt](#setat) verwenden, um das neue Array `memcpy_s`aufzufüllen, da diese Methoden anstelle von einen Zuweisungsoperator verwenden.

Wie bei einem C-Array ist `CArray` die Zugriffszeit für ein indiziertes Element konstant und unabhängig von der Arraygröße.

> [!TIP]
> Bevor Sie ein Array verwenden, verwenden Sie [SetSize,](#setsize) um seine Größe festzulegen und ihm Speicher zuzuweisen. Wenn Sie `SetSize` nicht verwenden, kann das Hinzufügen von Elementen zu Ihrem Array dazu führen, dass es häufig neu zugeordnet und kopiert wird. Häufige Neuzuordnungen und Kopiervorgänge sind ineffizient und können zu einer Fragmentierung des Arbeitsspeichers führen.

Wenn Sie ein Dump einzelner Elemente in einem Array benötigen, müssen Sie die Tiefe des [CDumpContext-Objekts](../../mfc/reference/cdumpcontext-class.md) auf 1 oder größer festlegen.

Bestimmte Memberfunktionen dieser Klasse rufen globale Hilfsfunktionen auf, die `CArray` für die meisten Verwendungen der Klasse angepasst werden müssen. Weitere Informationen finden Sie im Thema [Sammlungsklassenhilfsprogramme](../../mfc/reference/collection-class-helpers.md) im Abschnitt MFC-Makros und Globale.

Arrayklassenableitung ist wie Listenableitung.

Weitere Informationen zur Verwendung `CArray`finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Anforderungen

**Header:** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a>CArray::Hinzufügen

Fügt ein neues Element am Ende eines Arrays hinzu, wodurch das Array um 1 erweitert wird.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ von Argumenten angibt, die auf Elemente in diesem Array verweisen.

*Newelement*<br/>
Das Element, das diesem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des hinzugefügten Elements.

### <a name="remarks"></a>Bemerkungen

Wenn [SetSize](#setsize) mit einem `nGrowBy` Wert größer als 1 verwendet wurde, kann zusätzlicher Speicher zugewiesen werden. Die Obergrenze wird jedoch nur um 1 erhöht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a>CArray::Anfügen

Rufen Sie diese Memberfunktion auf, um den Inhalt eines Arrays am Ende eines anderen Arrays hinzuzufügen.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
Quelle der Elemente, die an ein Array angehängt werden sollen.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten angehängten Elements.

### <a name="remarks"></a>Bemerkungen

Die Arrays müssen vom gleichen Typ sein.

Falls erforderlich, kann zusätzlichem Speicher zugewiesen werden, `Append` um die an das Array angehängten Elemente unterzubringen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a>CArray::CArray

Erstellt ein leeres Array.

```
CArray();
```

### <a name="remarks"></a>Bemerkungen

Das Array wächst jeweils um ein Element.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a>CArray::Kopieren

Verwenden Sie diese Memberfunktion, um die Elemente eines Arrays in ein anderes zu kopieren.

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
Quelle der Elemente, die in ein Array kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um die Elemente eines Arrays mit den Elementen eines anderen Arrays zu überschreiben.

`Copy`gibt keinen Speicher frei; Bei Bedarf kann `Copy` jedoch zusätzlicher Speicher zugewiesen werden, um die in das Array kopierten Elemente aufzunehmen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a>CArray::ElementAt

Gibt einen temporären Verweis auf das angegebene Element innerhalb des Arrays zurück.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder gleich dem von [GetUpperBound](#getupperbound)zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein Arrayelement.

### <a name="remarks"></a>Bemerkungen

Es wird verwendet, um den linken Zuweisungsoperator für Arrays zu implementieren.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [GetSize](#getsize).

## <a name="carrayfreeextra"></a><a name="freeextra"></a>CArray::FreeExtra

Gibt zusätzlichen Speicher frei, der beim Wachsen des Arrays zugewiesen wurde.

```
void FreeExtra();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion hat keine Auswirkungen auf die Größe oder Obergrenze des Arrays.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [GetData](#getdata).

## <a name="carraygetat"></a><a name="getat"></a>CArray::GetAt

Gibt das Arrayelement am angegebenen Index zurück.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der Arrayelemente angibt.

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder gleich dem von [GetUpperBound](#getupperbound)zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Das Arrayelement, das sich derzeit in diesem Index befindet.

### <a name="remarks"></a>Bemerkungen

Das Übergeben eines negativen Werts oder `GetUpperBound` eines Wertes, der größer als der von zurückgegebene Wert ist, führt zu einer fehlgeschlagenen Assertion.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a>CArray::GetCount

Gibt die Anzahl der Arrayelemente zurück.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Array.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente im Array abzurufen. Da Indizes nullbasiert sind, ist die Größe 1 größer als der größte Index. Wenn Sie diese Methode aufrufen, wird das gleiche Ergebnis wie die [CArray::GetSize-Methode](#getsize) generiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a>CArray::GetData

Verwenden Sie diese Memberfunktion, um direkten Zugriff auf die Elemente in einem Array zu erhalten.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der Arrayelemente angibt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Arrayelement.

### <a name="remarks"></a>Bemerkungen

Wenn keine Elemente `GetData` verfügbar sind, wird ein NULL-Wert zurückgegeben.

Während der direkte Zugriff auf die Elemente eines Arrays Ihnen `GetData`helfen kann, schneller zu arbeiten, sollten Sie beim Aufrufen Vorsicht walten lassen. Alle Fehler, die Sie machen, wirken sich direkt auf die Elemente Ihres Arrays aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a>CArray::GetSize

Gibt die Größe des Arrays zurück.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Bemerkungen

Da Indizes nullbasiert sind, ist die Größe 1 größer als der größte Index. Wenn Sie diese Methode aufrufen, wird das gleiche Ergebnis wie die [CArray::GetCount-Methode](#getcount) generiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a>CArray::GetUpperBound

Gibt die aktuelle Obergrenze dieses Arrays zurück.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Bemerkungen

Da Arrayindizes nullbasiert sind, gibt diese Funktion `GetSize`einen Wert 1 kleiner als zurück.

Die `GetUpperBound( )` Bedingung = -1 gibt an, dass das Array keine Elemente enthält.

### <a name="example"></a>Beispiel

  Siehe das Beispiel für [CArray::GetAt](#getat).

## <a name="carrayinsertat"></a><a name="insertat"></a>CArray::InsertAt

Die erste `InsertAt` Version von fügt ein Element (oder mehrere Kopien eines Elements) an einem angegebenen Index in einem Array ein.

```
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
Ein Ganzzahlindex, der größer sein kann `GetUpperBound`als der von zurückgegebene Wert.

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ der Elemente in diesem Array angibt.

*Newelement*<br/>
Das Element, das in diesem Array platziert werden soll.

*nCount*<br/>
Die Häufigkeit, mit der dieses Element eingefügt werden soll (Standardwert 1).

*nStartIndex*<br/>
Ein Ganzzahlindex, der größer sein kann als der von [GetUpperBound](#getupperbound)zurückgegebene Wert.

*pNewArray*<br/>
Ein weiteres Array, das Elemente enthält, die diesem Array hinzugefügt werden sollen.

### <a name="remarks"></a>Bemerkungen

Dabei verschiebt er das vorhandene Element an diesem Index (durch Inkrementieren des Indexes) nach oben und verschiebt alle darüber genannten Elemente nach oben.

Die zweite Version fügt alle `CArray` Elemente aus einer anderen Auflistung ein, beginnend an der *nStartIndex-Position.*

Die `SetAt` Funktion hingegen ersetzt ein angegebenes Arrayelement und verschiebt keine Elemente.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a>CArray::IsEmpty

Bestimmt, ob das Array leer ist.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Array keine Elemente enthält; andernfalls 0.

## <a name="carrayoperator-"></a><a name="operator_at"></a>CArray::Operator\[\]

Diese Subskriptoperatoren sind ein bequemer Ersatz für die [SetAt-](#setat) und [GetAt-Funktionen.](#getat)

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der Elemente in diesem Array angibt.

*nIndex*<br/>
Index des Elements, auf das zugegriffen werden soll.

### <a name="remarks"></a>Bemerkungen

Der erste Operator, der für Arrays aufgerufen wird, die nicht **const**sind, kann entweder auf der rechten (r-Wert) oder auf der linken (l-Wert) einer Zuweisungsanweisung verwendet werden. Die zweite, **const** für const-Arrays aufgerufen, darf nur auf der rechten Seite verwendet werden.

Die Debug-Version der Bibliothek bestätigt, ob das Subskript (entweder auf der linken oder rechten Seite einer Zuweisungsanweisung) a-bounds ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a>CArray::RelocateElements

Verschiebt Daten in einen neuen Puffer, wenn das Array vergrößert oder verkleinert werden soll.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parameter

*pNewData*<br/>
Ein neuer Puffer für das Array von Elementen.

*pData*<br/>
Das alte Array von Elementen.

*nCount*<br/>
Anzahl der Elemente im alten Array.

### <a name="remarks"></a>Bemerkungen

*pNewData* ist immer groß genug, um alle *pData-Elemente* zu enthalten.

Die [CArray-Implementierung](../../mfc/reference/carray-class.md) verwendet diese Methode, um die alten Daten in einen neuen Puffer zu kopieren, wenn das Array vergrößert oder verkleinert werden soll (wenn [SetSize](#setsize) oder [FreeExtra](#freeextra) aufgerufen werden). Die Standardimplementierung kopiert nur die Daten.

Bei Arrays, in denen ein Element einen Zeiger auf eines seiner eigenen Member oder eine andere Struktur einen Zeiger auf eines der Arrayelemente enthält, werden die Zeiger nicht in einfacher Kopie aktualisiert. In diesem Fall können Sie Zeiger korrigieren, indem `RelocateElements` Sie eine Spezialisierung der entsprechenden Typen implementieren. Sie sind auch für das Kopieren von Daten verantwortlich.

## <a name="carrayremoveall"></a><a name="removeall"></a>CArray::Alle entfernen

Entfernt alle Elemente aus diesem Array.

```
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Array bereits leer ist, funktioniert die Funktion weiterhin.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a>CArray::RemoveAt

Entfernt ein oder mehrere Elemente, die bei einem angegebenen Index in einem Array beginnen.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder gleich dem von [GetUpperBound](#getupperbound)zurückgegebenen Wert ist.

*nCount*<br/>
Die Anzahl der zu entfernenden Elemente.

### <a name="remarks"></a>Bemerkungen

Dabei verschiebt er alle Elemente über den entfernten Elementen nach unten. Es dekrementiert die obere Grenze des Arrays, gibt jedoch keinen Speicher frei.

Wenn Sie versuchen, mehr Elemente zu entfernen, als im Array über dem Entfernungspunkt enthalten sind, wird die Debug-Version der Bibliothek bestätigt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a>CArray::SetAt

Legt das Arrayelement auf den angegebenen Index fest.

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder gleich dem von [GetUpperBound](#getupperbound)zurückgegebenen Wert ist.

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ der Argumente angibt, die zum Verweisen auf Arrayelemente verwendet werden.

*Newelement*<br/>
Der neue Elementwert, der an der angegebenen Position gespeichert werden soll.

### <a name="remarks"></a>Bemerkungen

`SetAt`führt nicht dazu, dass das Array wächst. Verwenden Sie [SetAtGrow,](#setatgrow) wenn das Array automatisch vergrößert werden soll.

Sie müssen sicherstellen, dass der Indexwert eine gültige Position im Array darstellt. Wenn es aprioriert, wird die Debug-Version der Bibliothek bestätigt.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [GetAt](#getat).

## <a name="carraysetatgrow"></a><a name="setatgrow"></a>CArray::SetatGrow

Legt das Arrayelement auf den angegebenen Index fest.

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 ist.

*ARG_TYPE*<br/>
Vorlagenparameter, der den Typ der Elemente im Array angibt.

*Newelement*<br/>
Das Element, das diesem Array hinzugefügt werden soll. Ein NULL-Wert ist zulässig.

### <a name="remarks"></a>Bemerkungen

Das Array wird bei Bedarf automatisch vergrößert (d. h. die obere Grenze wird angepasst, um das neue Element aufzunehmen).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a>CArray::SetSize

Legt die Größe eines leeren oder vorhandenen Arrays fest. reserviert bei Bedarf Speicher.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parameter

*nNewSize*<br/>
Die neue Arraygröße (Anzahl der Elemente). Muss größer als oder gleich 0 sein.

*nGrowBy*<br/>
Die minimale Anzahl von Elementsteckplätzen, die zugewiesen werden sollen, wenn eine Größenerhöhung erforderlich ist.

### <a name="remarks"></a>Bemerkungen

Wenn die neue Größe kleiner als die alte Größe ist, wird das Array abgeschnitten, und der gesamte nicht verwendete Speicher wird freigegeben.

Verwenden Sie diese Funktion, um die Größe des Arrays festzulegen, bevor Sie mit der Verwendung des Arrays beginnen. Wenn Sie `SetSize` nicht verwenden, kann das Hinzufügen von Elementen zu Ihrem Array dazu führen, dass es häufig neu zugeordnet und kopiert wird. Häufige Neuzuordnungen und Kopiervorgänge sind ineffizient und können zu einer Fragmentierung des Arbeitsspeichers führen.

Der Parameter *nGrowBy* wirkt sich auf die interne Speicherzuweisung aus, während das Array wächst. Seine Verwendung wirkt sich nie auf die Arraygröße aus, wie von [GetSize](#getsize) und [GetUpperBound](#getupperbound)gemeldet. Wenn der Standardwert verwendet wird, weist MFC Speicher auf eine Weise zu, die berechnet wurde, um Speicherfragmentierung zu vermeiden und die Effizienz in den meisten Fällen zu optimieren.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [GetData](#getdata).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel COLLECT](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CObArray-Klasse](../../mfc/reference/cobarray-class.md)<br/>
[Hilfsfunktionen für die Auflistungsklasse](../../mfc/reference/collection-class-helpers.md)
