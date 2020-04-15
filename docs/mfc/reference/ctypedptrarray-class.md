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
ms.openlocfilehash: a996bca471ce82a7c2adaaad67670ddef417eda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373281"
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
Basisklasse der typisierten Zeigerarrayklasse; muss eine Arrayklasse `CObArray` `CPtrArray`sein ( oder ).

*TYP*<br/>
Typ der elemente, die im Array der Basisklasse gespeichert sind.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTypedPtrArray::Hinzufügen](#add)|Fügt ein neues Element am Ende eines Arrays hinzu. Vergrößert das Array bei Bedarf|
|[CTypedPtrArray::Anfügen](#append)|Fügt den Inhalt eines Arrays am Ende eines anderen Arrays hinzu. Vergrößert das Array bei Bedarf|
|[CTypedPtrArray::Kopieren](#copy)|Kopiert ein anderes Array in das Array; vergrößert das Array bei Bedarf.|
|[CTypedPtrArray::ElementAt](#elementat)|Gibt einen temporären Verweis auf den Elementzeiger innerhalb des Arrays zurück.|
|[CTypedPtrArray::GetAt](#getat)|Gibt den Wert an einem bestimmten Index zurück.|
|[CTypedPtrArray::InsertAt](#insertat)|Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.|
|[CTypedPtrArray::SetAt](#setat)|Legt den Wert für einen bestimmten Index fest; Array darf nicht vergrößert werden.|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Legt den Wert für einen bestimmten Index fest; vergrößert das Array bei Bedarf.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTypedPtrArray::Operator \[\]](#operator_at)|Legt das Element am angegebenen Index fest oder ruft es ab.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie `CTypedPtrArray` anstelle `CPtrArray` `CObArray`von oder verwenden, hilft die C++-Typüberprüfungsfunktion, Fehler zu beseitigen, die durch nicht übereinstimmende Zeigertypen verursacht werden.

Darüber hinaus `CTypedPtrArray` führt der Wrapper einen Großteil des Castings `CPtrArray`durch, das erforderlich wäre, wenn Sie oder verwenden. `CObArray`

Da `CTypedPtrArray` alle Funktionen inline sind, wirkt sich die Verwendung dieser Vorlage nicht wesentlich auf die Größe oder Geschwindigkeit des Codes aus.

Weitere Informationen zur `CTypedPtrArray`Verwendung finden Sie in den Artikeln [Sammlungen](../../mfc/collections.md) und [Vorlagenbasierte Klassen](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Anforderungen

**Header:** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray::Hinzufügen

Diese Memberfunktion `BASE_CLASS`ruft **::Add**auf.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ des Elements angibt, das dem Array hinzugefügt werden soll.

*Newelement*<br/>
Das Element, das diesem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des hinzugefügten Elements.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Bemerkungen finden Sie unter [CObArray::Add](../../mfc/reference/cobarray-class.md#add).

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray::Anfügen

Diese Memberfunktion `BASE_CLASS`ruft ::Append** auf.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parameter

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeigerarrayklasse; muss eine Arrayklasse sein ( [CObArray](../../mfc/reference/cobarray-class.md) oder [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ der elemente, die im Array der Basisklasse gespeichert sind.

*src*<br/>
Quelle der Elemente, die an ein Array angehängt werden sollen.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten angehängten Elements.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Anmerkungen finden Sie unter [CObArray::Append](../../mfc/reference/cobarray-class.md#append).

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray::Kopieren

Diese Memberfunktion `BASE_CLASS`ruft **::Copy**auf.

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parameter

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeigerarrayklasse; muss eine Arrayklasse sein ( [CObArray](../../mfc/reference/cobarray-class.md) oder [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ der elemente, die im Array der Basisklasse gespeichert sind.

*src*<br/>
Quelle der Elemente, die in ein Array kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Bemerkungen finden Sie unter [CObArray::Kopieren](../../mfc/reference/cobarray-class.md#copy).

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray::ElementAt

Diese Inlinefunktion `BASE_CLASS`ruft **::ElementAt**auf.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der in diesem Array gespeicherten Elemente angibt.

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder `BASE_CLASS`gleich dem von **::GetUpperBound**zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Ein temporärer Verweis auf das Element an der von *nIndex*angegebenen Position . Dieses Element ist vom Typ, der durch den Vorlagenparameter *TYPE*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Bemerkungen finden Sie unter [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray::GetAt

Diese Inlinefunktion `BASE_CLASS`ruft **::GetAt**auf.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der im Array gespeicherten Elemente angibt.

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder `BASE_CLASS`gleich dem von **::GetUpperBound**zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Eine Kopie des Elements an der von *nIndex*angegebenen Position . Dieses Element ist vom Typ, der durch den Vorlagenparameter *TYPE*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Bemerkungen finden Sie unter [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray::InsertAt

Diese Memberfunktion `BASE_CLASS`ruft **::InsertAt**auf.

```
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
Ein ganzzahliger Index, der größer sein kann als der von [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)zurückgegebene Wert.

*TYP*<br/>
Typ der elemente, die im Array der Basisklasse gespeichert sind.

*Newelement*<br/>
Der Objektzeiger, der in diesem Array platziert werden soll. Ein *neuesElement* des Wertes **NULL** ist zulässig.

*nCount*<br/>
Die Häufigkeit, mit der dieses Element eingefügt werden soll (Standardwert 1).

*nStartIndex*<br/>
Ein Ganzzahlindex, der größer sein kann `CObArray::GetUpperBound`als der von zurückgegebene Wert.

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeigerarrayklasse; muss eine Arrayklasse sein ( [CObArray](../../mfc/reference/cobarray-class.md) oder [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*pNewArray*<br/>
Ein weiteres Array, das Elemente enthält, die diesem Array hinzugefügt werden sollen.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Anmerkungen finden Sie unter [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray::operator [ ]

Diese Inline-Operatoren rufen `BASE_CLASS` **::operator [ ]** auf.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der im Array gespeicherten Elemente angibt.

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder `BASE_CLASS`gleich dem von **::GetUpperBound**zurückgegebenen Wert ist.

### <a name="remarks"></a>Bemerkungen

Der erste Operator, der für Arrays aufgerufen wird, die nicht **const**sind, kann entweder auf der rechten (r-Wert) oder auf der linken (l-Wert) einer Zuweisungsanweisung verwendet werden. Die zweite, die **const** für const-Arrays aufgerufen wird, kann nur auf der rechten Seite verwendet werden.

Die Debug-Version der Bibliothek bestätigt, ob das Subskript (entweder auf der linken oder rechten Seite einer Zuweisungsanweisung) a-bounds ist.

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray::SetAt

Diese Memberfunktion `BASE_CLASS`ruft **::SetAt**auf.

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder gleich dem von [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)zurückgegebenen Wert ist.

*TYP*<br/>
Typ der elemente, die im Array der Basisklasse gespeichert sind.

*Ptr*<br/>
Ein Zeiger auf das Element, das in das Array am nIndex eingefügt werden soll. Ein NULL-Wert ist zulässig.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Anmerkungen finden Sie unter [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray::SetAtGrow

Diese Memberfunktion `BASE_CLASS`ruft **::SetAtGrow**auf.

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 ist.

*TYP*<br/>
Typ der elemente, die im Array der Basisklasse gespeichert sind.

*Newelement*<br/>
Der Objektzeiger, der diesem Array hinzugefügt werden soll. Ein **NULL-Wert** ist zulässig.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Anmerkungen finden Sie unter [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray-Klasse](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray-Klasse](../../mfc/reference/cobarray-class.md)
