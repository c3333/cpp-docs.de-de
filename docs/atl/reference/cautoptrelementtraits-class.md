---
title: CAutoPtrElementTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: ac29116dc9beedf587c42cc0e52f8c9dbaf3d782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318877"
---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits-Klasse

Diese Klasse stellt Methoden, statische Funktionen und typdefs bereit, die beim Erstellen von Auflistungen intelligenter Zeiger nützlich sind.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Zeigertyp.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden, statische Funktionen und typedefs bereit, um die Erstellung von Auflistungsklassenobjekten zu unterstützen, die intelligente Zeiger enthalten. Die Klassen [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) und [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) leiten sich von ab. `CAutoPtrElementTraits` Wenn Sie eine Sammlung von intelligenten Zeigern erstellen, die Vektor-Neu- und Löschoperatoren erfordert, verwenden Sie stattdessen [CAutoVectorPtrElementTraits.](../../atl/reference/cautovectorptrelementtraits-class.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cautoptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoPtrElementTraits::INARGTYPE

Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.

```
typedef CAutoPtr<T>& INARGTYPE;
```

## <a name="cautoptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoPtrElementTraits::OUTARGTYPE

Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Siehe auch

[CDefaultElementTraits-Klasse](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
