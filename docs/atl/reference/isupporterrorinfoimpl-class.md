---
title: ISupportErrorInfoImpl-Klasse
ms.date: 06/13/2019
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: 4c60b58ba697f00b146077a2cdecd727fe2cac02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326366"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl-Klasse

Diese Klasse stellt eine Standardimplementierung der [ISupportErrorInfo-Schnittstelle](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) bereit und kann verwendet werden, wenn nur eine einzelne Schnittstelle Fehler für ein Objekt generiert.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>Parameter

*piid*<br/>
Ein Zeiger auf die IID einer Schnittstelle, die [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)unterstützt.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Gibt an, ob `riid` die von der [IErrorInfo-Schnittstelle](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) identifizierte Schnittstelle unterstützt.|

## <a name="remarks"></a>Bemerkungen

Die [ISupportErrorInfo-Schnittstelle](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) stellt sicher, dass Fehlerinformationen an den Client zurückgegeben werden können. Die verwendenden `IErrorInfo` `ISupportErrorInfo`Objekte müssen implementieren.

Die `ISupportErrorInfoImpl` Klasse stellt `ISupportErrorInfo` eine Standardimplementierung von bereit und kann verwendet werden, wenn nur eine einzelne Schnittstelle Fehler für ein Objekt generiert. Beispiel:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="isupporterrorinfoimplinterfacesupportserrorinfo"></a><a name="interfacesupportserrorinfo"></a>ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Gibt an, ob `riid` die von der [IErrorInfo-Schnittstelle](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) identifizierte Schnittstelle unterstützt.

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
