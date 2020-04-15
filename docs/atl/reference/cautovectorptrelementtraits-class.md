---
title: CAutoVectorPtrElementTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 956fe39c4d3ba89bb9def2f996dca59905753edb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318747"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits-Klasse

Diese Klasse stellt Methoden, statische Funktionen und typdefs bereit, die beim Erstellen von Auflistungen intelligenter Zeiger mit Vektorneu- und Löschoperatoren nützlich sind.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <typename T>
class CAutoVectorPtrElementTraits :
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Zeigertyp.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden, statische Funktionen und typedefs bereit, um die Erstellung von Auflistungsklassenobjekten zu unterstützen, die intelligente Zeiger enthalten. Im Gegensatz zu [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)verwendet diese Klasse Vektor-Neu- und Löschoperatoren.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cautovectorptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoVectorPtrElementTraits::INARGTYPE

Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

## <a name="cautovectorptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoVectorPtrElementTraits::OUTARGTYPE

Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>Siehe auch

[CDefaultElementTraits-Klasse](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CAutoVectorPtr-Klasse](../../atl/reference/cautovectorptr-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
