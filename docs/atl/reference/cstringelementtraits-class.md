---
title: CStringElementTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
ms.openlocfilehash: 078cfd5ff93bfcd8acc747904ea05e6a2e762bc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330625"
---
# <a name="cstringelementtraits-class"></a>CStringElementTraits-Klasse

Diese Klasse stellt statische Funktionen `CString` bereit, die von Auflistungsklassen verwendet werden, die Objekte speichern.

## <a name="syntax"></a>Syntax

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die in der Auflistung gespeichert werden sollen.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStringElementTraits::INARGTYPE](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.|
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStringElementTraits::CompareElements](#compareelements)|(Statisch) Rufen Sie diese Funktion auf, um zwei Zeichenfolgenelemente für die Gleichheit zu vergleichen.|
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Statisch) Rufen Sie diese Funktion auf, um zwei Zeichenfolgenelemente zu vergleichen.|
|[CStringElementTraits::CopyElements](#copyelements)|(Statisch) Rufen Sie diese `CString` Funktion auf, um Elemente zu kopieren, die in einem Auflistungsklassenobjekt gespeichert sind.|
|[CStringElementTraits::Hash](#hash)|(Statisch) Rufen Sie diese Funktion auf, um einen Hashwert für das angegebene Zeichenfolgenelement zu berechnen.|
|[CStringElementTraits::RelocateElements](#relocateelements)|(Statisch) Rufen Sie diese `CString` Funktion auf, um Elemente zu verschieben, die in einem Auflistungsklassenobjekt gespeichert sind.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bietet statische Funktionen zum Kopieren, Verschieben und Vergleichen von Zeichenfolgen und zum Erstellen eines Hashwerts. Diese Funktionen sind nützlich, wenn Sie eine Auflistungsklasse zum Speichern von zeichenfolgenbasierten Daten verwenden. Verwenden Sie [CStringElementTraitsI,](../../atl/reference/cstringelementtraitsi-class.md) wenn Beifallsdaten erforderlich sind. Verwenden Sie [CStringRefElementTraits,](../../atl/reference/cstringrefelementtraits-class.md) wenn die Zeichenfolgenobjekte als Referenzen behandelt werden sollen.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** cstringt.h

## <a name="cstringelementtraitscompareelements"></a><a name="compareelements"></a>CStringElementTraits::CompareElements

Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente für die Gleichheit zu vergleichen.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste Zeichenfolgenelement.

*str2*<br/>
Das zweite Zeichenfolgenelement.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Elemente gleich sind, andernfalls false.

## <a name="cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraits::CompareElementsOrdered

Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente zu vergleichen.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste Zeichenfolgenelement.

*str2*<br/>
Das zweite Zeichenfolgenelement.

### <a name="return-value"></a>Rückgabewert

Null, wenn die Zeichenfolgen identisch sind, < 0, wenn *str1* kleiner als *str2*ist, oder > 0, wenn *str1* größer als *str2*ist. Die [CStringT::Compare-Methode](../../atl-mfc-shared/reference/cstringt-class.md#compare) wird verwendet, um die Vergleiche durchzuführen.

## <a name="cstringelementtraitscopyelements"></a><a name="copyelements"></a>CStringElementTraits::CopyElements

Rufen Sie diese `CString` statische Funktion auf, um Elemente zu kopieren, die in einem Auflistungsklassenobjekt gespeichert sind.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parameter

*pDest*<br/>
Zeigen Sie mit dem Zeiger auf das erste Element, das die kopierten Daten empfängt.

*pSrc*<br/>
Zeigen Sie mit dem Zeiger auf das erste zu kopierende Element.

*nElements*<br/>
Die Anzahl der zu kopierenden Elemente.

### <a name="remarks"></a>Bemerkungen

Die Quell- und Zielelemente sollten sich nicht überlappen.

## <a name="cstringelementtraitshash"></a><a name="hash"></a>CStringElementTraits::Hash

Rufen Sie diese statische Funktion auf, um einen Hashwert für das angegebene Zeichenfolgenelement zu berechnen.

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Das Zeichenfolgenelement.

### <a name="return-value"></a>Rückgabewert

Gibt einen Hashwert zurück, der mit dem Inhalt der Zeichenfolge berechnet wird.

## <a name="cstringelementtraitsinargtype"></a><a name="inargtype"></a>CStringElementTraits::INARGTYPE

Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsoutargtype"></a><a name="outargtype"></a>CStringElementTraits::OUTARGTYPE

Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.

```
typedef T& OUTARGTYPE;
```

## <a name="cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a>CStringElementTraits::RelocateElements

Rufen Sie diese `CString` statische Funktion auf, um Elemente zu verschieben, die in einem Auflistungsklassenobjekt gespeichert sind.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parameter

*pDest*<br/>
Zeigen Sie mit dem Zeiger auf das erste Element, das die zurückgesierten Daten empfängt.

*pSrc*<br/>
Zeigen Sie mit dem Zeiger auf das erste zu verschiebende Element.

*nElements*<br/>
Die Anzahl der zu verschiebenden Elemente.

### <a name="remarks"></a>Bemerkungen

Diese statische Funktion ruft [memmove](../../c-runtime-library/reference/memmove-wmemmove.md)auf, was für die meisten Datentypen ausreicht. Wenn die verschobenen Objekte Zeiger auf ihre eigenen Member enthalten, muss diese statische Funktion überschrieben werden.

## <a name="see-also"></a>Siehe auch

[CElementTraitsBase-Klasse](../../atl/reference/celementtraitsbase-class.md)<br/>
[CStringElementTraitsI-Klasse](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
