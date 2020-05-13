---
title: CStringElementTraitsI-Klasse
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
ms.openlocfilehash: 32980e19443cb17a3a688c85ff21195c60ed2124
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330592"
---
# <a name="cstringelementtraitsi-class"></a>CStringElementTraitsI-Klasse

Diese Klasse stellt statische Funktionen bereit, die sich auf Zeichenfolgen beziehen, die in Auflistungsklassenobjekten gespeichert sind. Es ähnelt [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), führt jedoch Vergleiche mit Groß-/Kleinschreibung durch.

## <a name="syntax"></a>Syntax

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die in der Auflistung gespeichert werden sollen.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente für die Gleichheit zu vergleichen, wobei Unterschiede im Fall ignoriert werden.|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente zu vergleichen, wobei Unterschiede im Fall ignoriert werden.|
|[CStringElementTraitsI::Hash](#hash)|Rufen Sie diese statische Funktion auf, um einen Hashwert für das angegebene Zeichenfolgenelement zu berechnen.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bietet statische Funktionen zum Vergleichen von Zeichenfolgen und zum Erstellen eines Hashwerts. Diese Funktionen sind nützlich, wenn Sie eine Auflistungsklasse zum Speichern von zeichenfolgenbasierten Daten verwenden. Verwenden Sie [CStringRefElementTraits,](../../atl/reference/cstringrefelementtraits-class.md) wenn die Zeichenfolgenobjekte als Referenzen behandelt werden sollen.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cstringelementtraitsicompareelements"></a><a name="compareelements"></a>CStringElementTraitsI::CompareElements

Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente für die Gleichheit zu vergleichen, wobei Unterschiede im Fall ignoriert werden.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste Zeichenfolgenelement.

*str2*<br/>
Das zweite Zeichenfolgenelement.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Elemente gleich sind, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Bei Vergleichen wird die Groß-/Kleinschreibung nicht berücksichtigt.

## <a name="cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraitsI::CompareElementsOrdered

Rufen Sie diese statische Funktion auf, um zwei Zeichenfolgenelemente zu vergleichen, wobei Unterschiede im Fall ignoriert werden.

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

### <a name="remarks"></a>Bemerkungen

Bei Vergleichen wird die Groß-/Kleinschreibung nicht berücksichtigt.

## <a name="cstringelementtraitsihash"></a><a name="hash"></a>CStringElementTraitsI::Hash

Rufen Sie diese statische Funktion auf, um einen Hashwert für das angegebene Zeichenfolgenelement zu berechnen.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Das Zeichenfolgenelement.

### <a name="return-value"></a>Rückgabewert

Gibt einen Hashwert zurück, der mit dem Inhalt der Zeichenfolge berechnet wird.

## <a name="cstringelementtraitsiinargtype"></a><a name="inargtype"></a>CStringElementTraitsI::INARGTYPE

Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsioutargtype"></a><a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE

Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Siehe auch

[CElementTraitsBase-Klasse](../../atl/reference/celementtraitsbase-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CStringElementTraits-Klasse](../../atl/reference/cstringelementtraits-class.md)
