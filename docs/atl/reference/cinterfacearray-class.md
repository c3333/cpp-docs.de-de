---
title: CInterfaceArray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: e6efe31989b06f0977ecff156a8f64053dc64ad1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326802"
---
# <a name="cinterfacearray-class"></a>CInterfaceArray-Klasse

Diese Klasse stellt Methoden bereit, die beim Erstellen eines Arrays von COM-Schnittstellenzeigern nützlich sind.

## <a name="syntax"></a>Syntax

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parameter

*Ⅰ*<br/>
Eine COM-Schnittstelle, die den Typ des zu speichernden Zeigers angibt.

*piid*<br/>
Ein Zeiger auf die IID von *I*.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Der Konstruktor für das Schnittstellenarray.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt einen Konstruktor und abgeleitete Methoden zum Erstellen eines Arrays von COM-Schnittstellenzeigern bereit. Verwenden Sie [CInterfaceList,](../../atl/reference/cinterfacelist-class.md) wenn eine Liste erforderlich ist.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cinterfacearraycinterfacearray"></a><a name="cinterfacearray"></a>CInterfaceArray::CInterfaceArray

Der Konstruktor.

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert das smarte Zeigerarray.

## <a name="see-also"></a>Siehe auch

[CAtlArray-Klasse](../../atl/reference/catlarray-class.md)<br/>
[CComQIPtr-Klasse](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits-Klasse](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
