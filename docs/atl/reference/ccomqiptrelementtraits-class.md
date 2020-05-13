---
title: CComQIPtrElementTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
ms.openlocfilehash: 19f2669c157310be02f746672b22f6c0ed005075
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327413"
---
# <a name="ccomqiptrelementtraits-class"></a>CComQIPtrElementTraits-Klasse

Diese Klasse stellt Methoden, statische Funktionen und typdefs bereit, die beim Erstellen von Auflistungen von COM-Schnittstellenzeigern nützlich sind.

## <a name="syntax"></a>Syntax

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>Parameter

*Ⅰ*<br/>
Eine COM-Schnittstelle, die den Typ des zu speichernden Zeigers angibt.

*piid*<br/>
Ein Zeiger auf die IID von *I*.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse leitet Methoden ab und stellt eine typedef bereit, die beim Erstellen einer Auflistungsklasse von [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM-Schnittstellenzeigerobjekten nützlich ist. Diese Klasse wird sowohl von den [Klassen CInterfaceArray](../../atl/reference/cinterfacearray-class.md) als auch [CInterfaceList](../../atl/reference/cinterfacelist-class.md) verwendet.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="ccomqiptrelementtraitsinargtype"></a><a name="inargtype"></a>CComQIPtrElementTraits::INARGTYPE

Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>Siehe auch

[CDefaultElementTraits-Klasse](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
