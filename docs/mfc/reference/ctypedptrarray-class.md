---
title: CTypedPtrArray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
ms.openlocfilehash: db24e3992e5db70895ccc2908dba108de843bcdc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215945"
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray-Klasse

Stellt einen typsicheren Wrapper für Objekte der Klasse `CPtrArray` oder `CObArray`bereit.

## <a name="syntax"></a>Syntax

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>Parameter

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeiger Array Klasse; muss eine Array Klasse ( `CObArray` oder `CPtrArray` ) sein.

*TYPE*<br/>
Der Typ der Elemente, die im basisklassenarray gespeichert werden.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CTypedPtrArray:: Add](#add)|Fügt am Ende eines Arrays ein neues Element hinzu. Vergrößert das Array bei Bedarf|
|[CTypedPtrArray:: Append](#append)|Fügt den Inhalt eines Arrays am Ende eines anderen Arrays ein. Vergrößert das Array bei Bedarf|
|[CTypedPtrArray:: Copy](#copy)|Kopiert ein anderes Array in das Array; vergrößert das Array bei Bedarf.|
|[CTypedPtrArray:: ElementAt](#elementat)|Gibt einen temporären Verweis auf den Elementzeiger innerhalb des Arrays zurück.|
|[CTypedPtrArray:: GetAt](#getat)|Gibt den Wert an einem bestimmten Index zurück.|
|[CTypedPtrArray:: InsertAt](#insertat)|Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.|
|[CTypedPtrArray:: Setup](#setat)|Legt den Wert für einen bestimmten Index fest; Array darf nicht vergrößert werden.|
|[CTypedPtrArray:: antatvergrößerung](#setatgrow)|Legt den Wert für einen bestimmten Index fest; vergrößert das Array bei Bedarf.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTypedPtrArray::-Operator \[\]](#operator_at)|Legt das Element am angegebenen Index fest oder ruft es ab.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie `CTypedPtrArray` anstelle `CPtrArray` von oder verwenden `CObArray` , können Sie durch die C++-Typüberprüfung Fehler vermeiden, die durch nicht übereinstimmende Zeiger Typen verursacht werden.

Außerdem führt der Wrapper einen Großteil der Umwandlung `CTypedPtrArray` aus, die erforderlich wäre, wenn Sie `CObArray` oder verwenden `CPtrArray` .

Da alle `CTypedPtrArray` Funktionen Inline sind, wirkt sich die Verwendung dieser Vorlage nicht maßgeblich auf die Größe oder Geschwindigkeit Ihres Codes aus.

Weitere Informationen zur Verwendung von `CTypedPtrArray` finden Sie in den [Collections](../../mfc/collections.md) Artikeln [Auflistungen und vorlagenbasierte Klassen](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray:: Add

Diese Member-Funktion ruft `BASE_CLASS` **:: Add**auf.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ des Elements angibt, das dem Array hinzugefügt werden soll.

*newElement*<br/>
Das Element, das diesem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des hinzugefügten Elements.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Hinweise finden Sie unter [CObArray:: Add](../../mfc/reference/cobarray-class.md#add).

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray:: Append

Diese Member-Funktion ruft Folgendes auf `BASE_CLASS` :: Append * *.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parameter

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeiger Array Klasse; muss eine Array Klasse ( [CObArray](../../mfc/reference/cobarray-class.md) oder [CPtrArray](../../mfc/reference/cptrarray-class.md)) sein.

*TYPE*<br/>
Der Typ der Elemente, die im basisklassenarray gespeichert werden.

*src*<br/>
Quelle der Elemente, die an ein Array angefügt werden sollen.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten angefügten Elements.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Hinweise finden Sie unter [CObArray:: Append](../../mfc/reference/cobarray-class.md#append).

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray:: Copy

Diese Member-Funktion ruft `BASE_CLASS` **:: Copy**auf.

```cpp
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parameter

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeiger Array Klasse; muss eine Array Klasse ( [CObArray](../../mfc/reference/cobarray-class.md) oder [CPtrArray](../../mfc/reference/cptrarray-class.md)) sein.

*TYPE*<br/>
Der Typ der Elemente, die im basisklassenarray gespeichert werden.

*src*<br/>
Quelle der Elemente, die in ein Array kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Hinweise finden Sie unter [CObArray:: Copy](../../mfc/reference/cobarray-class.md#copy).

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray:: ElementAt

Diese Inline Funktion ruft `BASE_CLASS` **:: ElementAt auf**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der in diesem Array gespeicherten Elemente angibt.

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem von `BASE_CLASS` **:: GetUpperBound**zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Ein temporärer Verweis auf das Element an der durch *nIndex*angegebenen Position. Dieses Element weist den Typ auf, der durch den Vorlagen *Parametertyp*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Hinweise finden Sie unter [CObArray:: ElementAt](../../mfc/reference/cobarray-class.md#elementat).

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray:: GetAt

Diese Inline Funktion ruft `BASE_CLASS` **:: GetAt auf**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der im Array gespeicherten Elemente angibt.

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem von `BASE_CLASS` **:: GetUpperBound**zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Eine Kopie des Elements an der durch *nIndex*angegebenen Position. Dieses Element weist den Typ auf, der durch den Vorlagen *Parametertyp*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Hinweise finden Sie unter [CObArray:: GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray:: InsertAt

Diese Member-Funktion ruft `BASE_CLASS` **:: InsertAt**auf.

```cpp
void InsertAt(
    INT_PTR nIndex,
    TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der möglicherweise größer als der von [CObArray:: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)zurückgegebene Wert ist.

*TYPE*<br/>
Der Typ der Elemente, die im basisklassenarray gespeichert werden.

*newElement*<br/>
Der Objekt Zeiger, der in dieses Array eingefügt werden soll. Ein *newElement* **null** -Wert ist zulässig.

*nCount*<br/>
Gibt an, wie oft dieses Element eingefügt werden soll (Standardwert ist 1).

*nstartindex*<br/>
Ein ganzzahliger Index, der möglicherweise größer als der von zurückgegebene Wert ist `CObArray::GetUpperBound` .

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeiger Array Klasse; muss eine Array Klasse ( [CObArray](../../mfc/reference/cobarray-class.md) oder [CPtrArray](../../mfc/reference/cptrarray-class.md)) sein.

*pberwarray*<br/>
Ein weiteres Array, das Elemente enthält, die diesem Array hinzugefügt werden sollen.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Hinweise finden Sie unter [CObArray:: InsertAt](../../mfc/reference/cobarray-class.md#insertat).

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray:: Operator []

Diese Inline Operatoren nennen `BASE_CLASS` **:: Operator []**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der im Array gespeicherten Elemente angibt.

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem von `BASE_CLASS` **:: GetUpperBound**zurückgegebenen Wert ist.

### <a name="remarks"></a>Bemerkungen

Der erste Operator, der für Arrays aufgerufen wird, die nicht sind **`const`** , kann entweder auf der rechten Seite (r-Wert) oder auf der linken Seite (l-Wert) einer Zuweisungsanweisung verwendet werden. Die zweite, die für **`const`** Arrays aufgerufen wird, kann nur auf der rechten Seite verwendet werden.

Die Debugversion der Bibliothek bestätigt, ob der Index (entweder auf der linken oder rechten Seite einer Zuweisungsanweisung) außerhalb des gültigen Bereichs liegt.

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray:: Setup

Diese Member-Funktion ruft " `BASE_CLASS` **::***" auf.

```cpp
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem von [CObArray:: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)zurückgegebenen Wert ist.

*TYPE*<br/>
Der Typ der Elemente, die im basisklassenarray gespeichert werden.

*ptr*<br/>
Ein Zeiger auf das Element, das in das Array am nIndex eingefügt werden soll. Ein NULL-Wert ist zulässig.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Hinweise finden Sie unter [CObArray::](../../mfc/reference/cobarray-class.md#setat)*.

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray:: antatvergrößerung

Diese Member-Funktion ruft `BASE_CLASS` **::**-enumerationsvergrößerung auf.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 (null) ist.

*TYPE*<br/>
Der Typ der Elemente, die im basisklassenarray gespeichert werden.

*newElement*<br/>
Der Objekt Zeiger, der diesem Array hinzugefügt werden soll. Ein **null** -Wert ist zulässig.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Hinweise finden Sie unter [CObArray:: antatgrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel Sammlung](../../overview/visual-cpp-samples.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray-Klasse](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray-Klasse](../../mfc/reference/cobarray-class.md)
