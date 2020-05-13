---
title: CStringRefElementTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
ms.openlocfilehash: b4dd76b9592b255a1553be3ca7a249f58fb2672e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330586"
---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits-Klasse

Diese Klasse stellt statische Funktionen bereit, die sich auf Zeichenfolgen beziehen, die in Auflistungsklassenobjekten gespeichert sind. Die Zeichenfolgenobjekte werden als Referenzen behandelt.

## <a name="syntax"></a>Syntax

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die in der Auflistung gespeichert werden sollen.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente für die Gleichheit zu vergleichen.|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente zu vergleichen.|
|[CStringRefElementTraits::Hash](#hash)|Rufen Sie diese statische Funktion auf, um einen Hashwert für das angegebene Zeichenfolgenelement zu berechnen.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bietet statische Funktionen zum Vergleichen von Zeichenfolgen und zum Erstellen eines Hashwerts. Diese Funktionen sind nützlich, wenn Sie eine Auflistungsklasse zum Speichern von zeichenfolgenbasierten Daten verwenden. Im Gegensatz zu [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) und [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) `CStringRefElementTraits` bewirkt, dass `CString` die Argumente als **const-Referenzen** `CString&` übergeben werden.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElementTraits::CompareElements

Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente für die Gleichheit zu vergleichen.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Parameter

*Element1*<br/>
Das erste Zeichenfolgenelement.

*Element2*<br/>
Das zweite Zeichenfolgenelement.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Elemente gleich sind, andernfalls false.

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElementTraits::CompareElementsOrdered

Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente zu vergleichen.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste Zeichenfolgenelement.

*str2*<br/>
Das zweite Zeichenfolgenelement.

### <a name="return-value"></a>Rückgabewert

Null, wenn die Zeichenfolgen identisch sind, < 0, wenn *str1* kleiner als *str2*ist, oder > 0, wenn *str1* größer als *str2*ist. Die [CStringT::Compare-Methode](../../atl-mfc-shared/reference/cstringt-class.md#compare) wird verwendet, um die Vergleiche durchzuführen.

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>CStringRefElementTraits::Hash

Rufen Sie diese statische Funktion auf, um einen Hashwert für das angegebene Zeichenfolgenelement zu berechnen.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Das Zeichenfolgenelement.

### <a name="return-value"></a>Rückgabewert

Gibt einen Hashwert zurück, der mit dem Inhalt der Zeichenfolge berechnet wird.

## <a name="see-also"></a>Siehe auch

[CElementTraitsBase-Klasse](../../atl/reference/celementtraitsbase-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
