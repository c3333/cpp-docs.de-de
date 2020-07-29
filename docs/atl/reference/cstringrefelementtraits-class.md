---
title: Cstrauingrefelementtrait-Klasse
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
ms.openlocfilehash: 6fa8772033a5a82940cf30b2a73d6ea356269d67
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226554"
---
# <a name="cstringrefelementtraits-class"></a>Cstrauingrefelementtrait-Klasse

Diese Klasse stellt statische Funktionen für Zeichen folgen bereit, die in Auflistungs Klassen Objekten gespeichert sind. Die Zeichen folgen Objekte werden als Verweise behandelt.

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

|name|Beschreibung|
|----------|-----------------|
|[Cstrauingrefelementtrait:: compareelements](#compareelements)|Ruft diese statische Funktion auf, um zwei Zeichen folgen Elemente auf Gleichheit zu vergleichen.|
|[Cstrauingrefelementtrait:: compareelementsordered](#compareelementsordered)|Nennen Sie diese statische Funktion, um zwei Zeichen folgen Elemente zu vergleichen.|
|[Cstrauingrefelementtrait:: Hash](#hash)|Ruft diese statische Funktion auf, um einen Hashwert für das angegebene Zeichen folgen Element zu berechnen.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt statische Funktionen zum Vergleichen von Zeichen folgen und zum Erstellen eines Hashwerts bereit. Diese Funktionen sind nützlich, wenn Sie eine Auflistungs Klasse zum Speichern von Zeichen folgen basierten Daten verwenden. Anders als [cstringelementtrait](../../atl/reference/cstringelementtraits-class.md) und [cstringelementtraitsi](../../atl/reference/cstringelementtraitsi-class.md) `CStringRefElementTraits` bewirkt, `CString` dass die Argumente als Verweise übergeben werden **`const`** `CString&` .

Weitere Informationen finden Sie unter [ATL](../../atl/atl-collection-classes.md)-Auflistungs Klassen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Celementtraitsbase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcoll. h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>Cstrauingrefelementtrait:: compareelements

Ruft diese statische Funktion auf, um zwei Zeichen folgen Elemente auf Gleichheit zu vergleichen.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Parameter

*Element1*<br/>
Das erste Zeichen folgen Element.

*Element2*<br/>
Das zweite Zeichen folgen Element.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Elemente gleich sind, andernfalls false.

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>Cstrauingrefelementtrait:: compareelementsordered

Nennen Sie diese statische Funktion, um zwei Zeichen folgen Elemente zu vergleichen.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste Zeichen folgen Element.

*str2*<br/>
Das zweite Zeichen folgen Element.

### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Zeichen folgen identisch sind, < 0, wenn *str1* kleiner als *str2*ist, oder > 0, wenn *str1* größer als *str2*ist. Die [CStringT:: Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) -Methode wird verwendet, um die Vergleiche auszuführen.

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>Cstrauingrefelementtrait:: Hash

Ruft diese statische Funktion auf, um einen Hashwert für das angegebene Zeichen folgen Element zu berechnen.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parameter

*str*<br/>
Das Zeichen folgen Element.

### <a name="return-value"></a>Rückgabewert

Gibt einen Hashwert zurück, der mit dem Inhalt der Zeichenfolge berechnet wird.

## <a name="see-also"></a>Siehe auch

[Celementtraitsbase-Klasse](../../atl/reference/celementtraitsbase-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
