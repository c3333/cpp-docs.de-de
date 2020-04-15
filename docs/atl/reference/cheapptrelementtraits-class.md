---
title: CHeapPtrElementTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
ms.openlocfilehash: f09da968b264463eba759372e4e0756397e9978e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326875"
---
# <a name="cheapptrelementtraits-class"></a>CHeapPtrElementTraits-Klasse

Diese Klasse stellt Methoden, statische Funktionen und typdefs bereit, die beim Erstellen von Auflistungen von Heapzeigern nützlich sind.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Objekttyp, der in der Auflistungsklasse gespeichert werden soll.

*Zuweisung*<br/>
Die zu verwendende Speicherzuweisungsklasse. Der Standardwert ist [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.|
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden, statische Funktionen und typedefs bereit, um die Erstellung von Auflistungsklassenobjekten zu unterstützen, die Heapzeiger enthalten. Die `CHeapPtrList` Klasse leitet `CHeapPtrElementTraits`sich von ab.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cheapptrelementtraitsinargtype"></a><a name="inargtype"></a>CHeapPtrElementTraits::INARGTYPE

Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

## <a name="cheapptrelementtraitsoutargtype"></a><a name="outargtype"></a>CHeapPtrElementTraits::OUTARGTYPE

Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Siehe auch

[CDefaultElementTraits-Klasse](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CComHeapPtr-Klasse](../../atl/reference/ccomheapptr-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
