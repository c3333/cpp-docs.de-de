---
title: CDefaultCompareTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: 8262800ef613424c37c53931d97dd4b1b1a71321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327074"
---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits-Klasse

Diese Klasse bietet standardmäßige Elementvergleichsfunktionen.

## <a name="syntax"></a>Syntax

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die in der Auflistung gespeichert werden sollen.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Statisch) Rufen Sie diese Funktion auf, um zwei Elemente für die Gleichheit zu vergleichen.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Statisch) Rufen Sie diese Funktion auf, um das größere und kleinere Element zu bestimmen.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse enthält zwei statische Funktionen zum Vergleichen von Elementen, die in einem Auflistungsklassenobjekt gespeichert sind. Diese Klasse wird von der [CDefaultElementTraits-Klasse](../../atl/reference/cdefaultelementtraits-class.md)verwendet.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cdefaultcomparetraitscompareelements"></a><a name="compareelements"></a>CDefaultCompareTraits::CompareElements

Rufen Sie diese Funktion auf, um zwei Elemente für die Gleichheit zu vergleichen.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parameter

*Element1*<br/>
Das erste Element.

*Element2*<br/>
Das zweite Element.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Elemente gleich sind, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion ist**==** der Gleichheitsoperator ( ). Bei anderen Objekten als einfachen Datentypen muss diese Funktion möglicherweise überschrieben werden.

## <a name="cdefaultcomparetraitscompareelementsordered"></a><a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered

Rufen Sie diese Funktion auf, um das größere und kleinere Element zu bestimmen.

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parameter

*Element1*<br/>
Das erste Element.

*Element2*<br/>
Das zweite Element.

### <a name="return-value"></a>Rückgabewert

Gibt eine ganze Zahl basierend auf der folgenden Tabelle zurück:

|Bedingung|Rückgabewert|
|---------------|------------------|
|*Element1* < *Element2*|<0|
|*Element1* == *Element2*|0|
|*Element1* > *Element2*|>0|

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung dieser Funktion **==** **\<** verwendet **>** die Operatoren , und Operatoren. Bei anderen Objekten als einfachen Datentypen muss diese Funktion möglicherweise überschrieben werden.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
