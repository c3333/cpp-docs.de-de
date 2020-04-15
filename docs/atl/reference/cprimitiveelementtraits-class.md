---
title: CPrimitiveElementTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: 6b45d93420d1832091cc451a3e6eb309f61d07a3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331436"
---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits-Klasse

Diese Klasse stellt Standardmethoden und -funktionen für eine Auflistungsklasse bereit, die aus primitiven Datentypen besteht.

## <a name="syntax"></a>Syntax

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die im Auflistungsklassenobjekt gespeichert werden sollen.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.|
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bietet statische Standardfunktionen und -methoden zum Verschieben, Kopieren, Vergleichen und Hashing primitiver Datentypelemente, die in einem Auflistungsklassenobjekt gespeichert sind.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cprimitiveelementtraitsinargtype"></a><a name="inargtype"></a>CPrimitiveElementTraits::INARGTYPE

Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.

```
typedef T INARGTYPE;
```

## <a name="cprimitiveelementtraitsoutargtype"></a><a name="outargtype"></a>CPrimitiveElementTraits::OUTARGTYPE

Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Siehe auch

[CDefaultElementTraits-Klasse](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
