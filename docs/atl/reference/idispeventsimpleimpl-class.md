---
title: IDispEventSimpleImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: 779e143094760c7bd868ad33f590f7fd8f004762
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329735"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl-Klasse

Diese Klasse stellt Implementierungen der `IDispatch` Methoden bereit, ohne Typinformationen aus einer Typbibliothek abzubekommen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parameter

*nID*<br/>
Ein eindeutiger Bezeichner für das Quellobjekt. Wenn `IDispEventSimpleImpl` die Basisklasse für ein zusammengesetztes Steuerelement ist, verwenden Sie die Ressourcen-ID des gewünschten enthaltenen Steuerelements für diesen Parameter. In anderen Fällen verwenden Sie eine beliebige positive ganze Zahl.

*T*<br/>
Die Klasse des Benutzers, `IDispEventSimpleImpl`die von abgeleitet wird.

*pdiid*<br/>
Der Zeiger auf die IID des Ereignisdispinterfaces, das von dieser Klasse implementiert wurde.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IDispEventSimpleImpl::Beratung](#advise)|Stellt eine Verbindung mit der Standardereignisquelle her.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Stellt eine Verbindung mit der Ereignisquelle her.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Bricht die Verbindung mit der Ereignisquelle.|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Gibt E_NOTIMPL zurück.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Gibt E_NOTIMPL zurück.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Gibt E_NOTIMPL zurück.|
|[IDispEventSimpleImpl::Invoke](#invoke)|Ruft die ereignishandler auf, die in der Ereignissenkenzuordnung aufgeführt sind.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Unterbricht die Verbindung mit der Standardereignisquelle.|

## <a name="remarks"></a>Bemerkungen

`IDispEventSimpleImpl`bietet eine Möglichkeit zum Implementieren einer Ereignisdispinterface, ohne dass Sie Implementierungscode für jede Methode/jedes Ereignis auf dieser Schnittstelle bereitstellen müssen. `IDispEventSimpleImpl`stellt Implementierungen `IDispatch` der Methoden bereit. Sie müssen nur Implementierungen für die Ereignisse bereitstellen, die Sie behandeln möchten.

`IDispEventSimpleImpl`funktioniert in Verbindung mit der Ereignissenkenzuordnung in Ihrer Klasse, um Ereignisse an die entsprechende Handlerfunktion weiterzuleiten. So verwenden Sie diese Klasse:

- Fügen Sie der Ereignissenkenzuordnung für jedes Ereignis für jedes Objekt, das Sie behandeln möchten, ein [SINK_ENTRY_INFO-Makro](composite-control-macros.md#sink_entry_info) hinzu.

- Geben Sie Typinformationen für jedes Ereignis an, indem Sie einen Zeiger an eine [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) Struktur als Parameter für jeden Eintrag übergeben. Auf der x86-Plattform muss der `_ATL_FUNC_INFO.cc` Wert mit der Callback-Funktion CC_CDECL werden, die die Aufrufmethode __stdcall.

- Rufen Sie [DispEventAdvise](#dispeventadvise) auf, um die Verbindung zwischen dem Quellobjekt und der Basisklasse herzustellen.

- Rufen Sie [DispEventUnadvise](#dispeventunadvise) auf, um die Verbindung zu unterbrechen.

Sie müssen für `IDispEventSimpleImpl` jedes Objekt, für das Sie Ereignisse verarbeiten müssen, von (mit einem eindeutigen Wert für *nID*) ableiten. Sie können die Basisklasse wiederverwenden, indem Sie die Empfehlung für ein Quellobjekt aufdecken und dann von einem anderen Quellobjekt abberaten, `IDispEventSimpleImpl` aber die maximale Anzahl von Quellobjekten, die von einem einzelnen Objekt gleichzeitig behandelt werden können, wird durch die Anzahl der Basisklassen begrenzt.

`IDispEventSimplImpl`bietet die gleiche Funktionalität wie [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), es sei denn, es werden keine Typinformationen über die Schnittstelle von einer Typbibliothek abgerufen. Die Assistenten generieren Code, `IDispEventImpl`der nur `IDispEventSimpleImpl` auf basiert, Sie können den Code jedoch von Hand hinzufügen. Verwenden `IDispEventSimpleImpl` Sie diese Datei, wenn Sie nicht über eine Typbibliothek verfügen, die die Ereignisschnittstelle beschreibt, oder wenn Sie den mit der Verwendung der Typbibliothek verbundenen Overhead vermeiden möchten.

> [!NOTE]
> `IDispEventImpl`und `IDispEventSimpleImpl` stellen Sie `IUnknown::QueryInterface` eine `IDispEventImpl` eigene `IDispEventSimpleImpl` Implementierung bereit, die es jeder oder jeder Basisklasse ermöglicht, als separate COM-Identität zu fungieren, während gleichzeitig der direkte Zugriff auf Klassenmember in Ihrem Haupt-COM-Objekt möglich ist.

Die CE ATL-Implementierung von ActiveX-Ereignissenken unterstützt nur Rückgabewerte vom Typ HRESULT oder void von Ihren Ereignishandlermethoden. Jeder andere Rückgabewert wird nicht unterstützt, und sein Verhalten ist nicht definiert.

Weitere Informationen finden Sie unter [Unterstützen von IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a>IDispEventSimpleImpl::Beratung

Rufen Sie diese Methode auf, um eine Verbindung mit der Ereignisquelle herzustellen, die durch *pUnk*dargestellt wird.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des Ereignisquellobjekts.

### <a name="return-value"></a>Rückgabewert

S_OK oder einen Fehler-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Sobald die Verbindung hergestellt wurde, werden Ereignisse, die von *pUnk* ausgelöst werden, über die Ereignissenkenzuordnung an Handler in Ihrer Klasse weitergeleitet.

> [!NOTE]
> Wenn Ihre Klasse von `IDispEventSimpleImpl` mehreren Klassen stammt, müssen Sie Aufrufe dieser Methode disambiguieren, indem Sie den Aufruf mit der bestimmten Basisklasse, an der Sie interessiert sind, schneiden.

`Advise`stellt eine Verbindung mit der Standardereignisquelle her, sie ruft die IID der Standardereignisquelle des Objekts ab, die von [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)bestimmt wird.

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a>IDispEventSimpleImpl::DispEventAdvise

Rufen Sie diese Methode auf, um eine Verbindung mit der Ereignisquelle herzustellen, die durch *pUnk*dargestellt wird.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des Ereignisquellobjekts.

*piid*<br/>
Ein Zeiger auf die IID des Ereignisquellobjekts.

### <a name="return-value"></a>Rückgabewert

S_OK oder einen Fehler-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Anschließend werden Ereignisse, die von *pUnk* ausgelöst werden, über die Ereignissenkenzuordnung an Handler in Ihrer Klasse weitergeleitet.

> [!NOTE]
> Wenn Ihre Klasse von `IDispEventSimpleImpl` mehreren Klassen stammt, müssen Sie Aufrufe dieser Methode disambiguieren, indem Sie den Aufruf mit der bestimmten Basisklasse, an der Sie interessiert sind, schneiden.

`DispEventAdvise`stellt eine Verbindung mit der `pdiid`in angegebenen Ereignisquelle her.

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a>IDispEventSimpleImpl::DispEventUnadvise

Unterbricht die Verbindung mit der Ereignisquelle, die durch *pUnk*dargestellt wird.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des Ereignisquellobjekts.

*piid*<br/>
Ein Zeiger auf die IID des Ereignisquellobjekts.

### <a name="return-value"></a>Rückgabewert

S_OK oder einen Fehler-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Sobald die Verbindung unterbrochen ist, werden Ereignisse nicht mehr an die Handlerfunktionen weitergeleitet, die in der Ereignissenkenzuordnung aufgeführt sind.

> [!NOTE]
> Wenn Ihre Klasse von `IDispEventSimpleImpl` mehreren Klassen stammt, müssen Sie Aufrufe dieser Methode disambiguieren, indem Sie den Aufruf mit der bestimmten Basisklasse, an der Sie interessiert sind, schneiden.

`DispEventAdvise`bricht eine Verbindung, die mit der `pdiid`in angegebenen Ereignisquelle hergestellt wurde.

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames

Diese Implementierung `IDispatch::GetIDsOfNames` von Retouren E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Bemerkungen

Siehe [iDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) im Windows SDK.

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo

Diese Implementierung `IDispatch::GetTypeInfo` von Retouren E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) im Windows SDK.

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount

Diese Implementierung `IDispatch::GetTypeInfoCount` von Retouren E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Bemerkungen

Siehe [iDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) im Windows SDK.

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a>IDispEventSimpleImpl::Invoke

Diese Implementierung `IDispatch::Invoke` von Aufrufen der Ereignishandler, die in der Ereignissenkenzuordnung aufgeführt sind.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a>IDispEventSimpleImpl::Unadvise

Unterbricht die Verbindung mit der Ereignisquelle, die durch *pUnk*dargestellt wird.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des Ereignisquellobjekts.

### <a name="return-value"></a>Rückgabewert

S_OK oder einen Fehler-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Sobald die Verbindung unterbrochen ist, werden Ereignisse nicht mehr an die Handlerfunktionen weitergeleitet, die in der Ereignissenkenzuordnung aufgeführt sind.

> [!NOTE]
> Wenn Ihre Klasse von `IDispEventSimpleImpl` mehreren Klassen stammt, müssen Sie Aufrufe dieser Methode disambiguieren, indem Sie den Aufruf mit der bestimmten Basisklasse, an der Sie interessiert sind, schneiden.

`Unadvise`bricht eine Verbindung, die mit der `pdiid`in angegebenen Standardereignisquelle hergestellt wurde.

`Unavise`unterbricht eine Verbindung mit der Standardereignisquelle, ruft sie die IID der Standardereignisquelle des Objekts ab, die von [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)bestimmt wird.

## <a name="see-also"></a>Siehe auch

[_ATL_FUNC_INFO Struktur](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl-Klasse](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl-Klasse](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
