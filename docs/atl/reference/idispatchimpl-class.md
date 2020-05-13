---
title: IDispatchImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: 3b3899a0c4a49aa7fb1bd82af330f5f1cc7329c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329793"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl-Klasse

Stellt eine Standardimplementierung `IDispatch` für den Teil einer dualen Schnittstelle bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0,
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```

#### <a name="parameters"></a>Parameter

*T*<br/>
[in] Eine duale Schnittstelle.

*piid*<br/>
[in] Ein Zeiger auf die IID von *T*.

*plibid*<br/>
[in] Ein Zeiger auf die LIBID der Typbibliothek, die Informationen über die Schnittstelle enthält. Standardmäßig wird die Typbibliothek auf Serverebene übergeben.

*wMajor*<br/>
[in] Die Hauptversion der Typbibliothek. Standardmäßig ist der Wert 1.

*wMinor*<br/>
[in] Die Nebenversion der Typbibliothek. Standardmäßig ist der Wert 0.

*tihclass*<br/>
[in] Die Klasse, die zum Verwalten der Typinformationen für *T*verwendet wird. Standardmäßig ist `CComTypeInfoHolder`der Wert .

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Der Konstruktor. Ruft `AddRef` die geschützte Membervariable auf, die die Typinformationen für die duale Schnittstelle verwaltet. Der Destruktor ruft `Release` auf.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Ordnet eine Reihe von Namen einer entsprechenden Reihe von Dispatchbezeichnern zu.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Ruft die Typinformationen für die duale Schnittstelle ab.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Bestimmt, ob Typinformationen für die duale Schnittstelle verfügbar sind.|
|[IDispatchImpl::Invoke](#invoke)|Bietet Zugriff auf die Methoden und Eigenschaften, die von der dualen Schnittstelle verfügbar gemacht werden.|

## <a name="remarks"></a>Bemerkungen

`IDispatchImpl`stellt eine Standardimplementierung `IDispatch` für den Teil einer beliebigen dualen Schnittstelle für ein Objekt bereit. Eine duale Schnittstelle `IDispatch` leitet sich von nur Automation-kompatiblen Typen ab und verwendet diese. Wie eine Dispinterface unterstützt eine duale Schnittstelle frühe Bindung und späte Bindung; Eine duale Schnittstelle unterstützt jedoch auch die vtable-Bindung.

Das folgende Beispiel zeigt `IDispatchImpl`eine typische Implementierung von .

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Standardmäßig sucht `IDispatchImpl` die Klasse die Typinformationen für *T* in der Registrierung. Um eine nicht registrierte Schnittstelle zu `IDispatchImpl` implementieren, können Sie die Klasse verwenden, ohne auf die Registrierung zuzugreifen, indem Sie eine vordefinierte Versionsnummer verwenden. Wenn Sie `IDispatchImpl` ein Objekt mit 0xFFFF als Wert für *wMajor* und 0xFFFF `IDispatchImpl` als Wert für *wMinor*erstellen, ruft die Klasse die Typbibliothek aus der DLL-Datei anstelle der Registrierung ab.

`IDispatchImpl`enthält einen statischen `CComTypeInfoHolder` Typmember, der die Typinformationen für die duale Schnittstelle verwaltet. Wenn Sie über mehrere Objekte verfügen, die dieselbe `CComTypeInfoHolder` duale Schnittstelle implementieren, wird nur eine Instanz von verwendet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`T`

`IDispatchImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchImpl::GetIDsOfNames

Ordnet eine Reihe von Namen einer entsprechenden Reihe von Dispatchbezeichnern zu.

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Bemerkungen

Siehe [iDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) im Windows SDK.

## <a name="idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchImpl::GetTypeInfo

Ruft die Typinformationen für die duale Schnittstelle ab.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) im Windows SDK.

## <a name="idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount

Bestimmt, ob Typinformationen für die duale Schnittstelle verfügbar sind.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Bemerkungen

Siehe `IDispatch::GetTypeInfoCount` Windows SDK.

## <a name="idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl

Der Konstruktor. Ruft `AddRef` die geschützte Membervariable auf, die die Typinformationen für die duale Schnittstelle verwaltet. Der Destruktor ruft `Release` auf.

```
IDispatchImpl();
```

## <a name="idispatchimplinvoke"></a><a name="invoke"></a>IDispatchImpl::Invoke

Bietet Zugriff auf die Methoden und Eigenschaften, die von der dualen Schnittstelle verfügbar gemacht werden.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
