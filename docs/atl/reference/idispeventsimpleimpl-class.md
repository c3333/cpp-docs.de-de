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
ms.openlocfilehash: 3ceb436e4f20a17ecd086fb68f9c1cfdcbe0be3e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423081"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl-Klasse

Diese Klasse stellt Implementierungen der `IDispatch` Methoden bereit, ohne Typinformationen aus einer Typbibliothek zu erhalten.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parameter

*NID*<br/>
Ein eindeutiger Bezeichner für das Quell Objekt. Wenn `IDispEventSimpleImpl` die Basisklasse für ein zusammengesetztes Steuerelement ist, verwenden Sie die Ressourcen-ID des gewünschten enthaltenen Steuer Elements für diesen Parameter. Verwenden Sie in anderen Fällen eine beliebige positive ganze Zahl.

*T*<br/>
Die Klasse des Benutzers, die von `IDispEventSimpleImpl`abgeleitet ist.

*pdiid*<br/>
Der Zeiger auf die IID der Ereignis dispinterface, die von dieser Klasse implementiert wird.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[IDispEventSimpleImpl:: Empfehlung](#advise)|Stellt eine Verbindung mit der Standard Ereignis Quelle her.|
|[IDispEventSimpleImpl::D ispeventrat](#dispeventadvise)|Stellt eine Verbindung mit der Ereignis Quelle her.|
|[IDispEventSimpleImpl::D ispeventunrat](#dispeventunadvise)|Unterbricht die Verbindung mit der Ereignis Quelle.|
|[IDispEventSimpleImpl:: GetIDsOfNames](#getidsofnames)|Gibt E_NOTIMPL zurück.|
|[IDispEventSimpleImpl:: gettypeingefo](#gettypeinfo)|Gibt E_NOTIMPL zurück.|
|[IDispEventSimpleImpl:: gettypanfocount](#gettypeinfocount)|Gibt E_NOTIMPL zurück.|
|[IDispEventSimpleImpl:: aufrufen](#invoke)|Ruft die Ereignishandler auf, die in der Ereignis Senk Karte aufgeführt sind.|
|[IDispEventSimpleImpl:: nicht Empfehlung](#unadvise)|Unterbricht die Verbindung mit der Standard Ereignis Quelle.|

## <a name="remarks"></a>Hinweise

`IDispEventSimpleImpl` bietet eine Möglichkeit, eine Ereignis-dispinterface zu implementieren, ohne dass Sie Implementierungs Code für jede Methode bzw. jedes Ereignis an dieser Schnittstelle bereitstellen müssen. `IDispEventSimpleImpl` stellt Implementierungen der `IDispatch` Methoden bereit. Sie müssen nur Implementierungen für die Ereignisse bereitstellen, die Sie behandeln möchten.

`IDispEventSimpleImpl` in Verbindung mit der Zuordnung der Ereignis Senke in der-Klasse, um Ereignisse an die entsprechende Handlerfunktion weiterzuleiten. So verwenden Sie diese Klasse:

- Fügen Sie der Ereignis senkenzuordnung für jedes Ereignis für jedes Objekt, das Sie verarbeiten möchten, ein [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) Makro hinzu.

- Geben Sie für jedes Ereignis Typinformationen an, indem Sie einen Zeiger auf eine [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) Struktur als Parameter an jeden Eintrag übergeben. Auf der x86-Plattform muss der `_ATL_FUNC_INFO.cc` Wert mit der Rückruffunktion CC_CDECL-Methode von __stdcall werden.

- Wenden Sie [dispeventempfehlung](#dispeventadvise) an, um die Verbindung zwischen dem Quell Objekt und der Basisklasse herzustellen.

- Bitten Sie [dispeventunempfehlung](#dispeventunadvise) , die Verbindung zu unterbrechen.

Sie müssen für jedes Objekt, für das Ereignisse behandelt werden müssen, von `IDispEventSimpleImpl` (mit einem eindeutigen Wert für *NID*) abgeleitet werden. Sie können die Basisklasse wieder verwenden, indem Sie für ein Quell Objekt keine Ratschläge mehr verwenden, und dann eine Beratung für ein anderes Quell Objekt durchgeführt haben. die maximale Anzahl von Quell Objekten, die von einem einzelnen Objekt gleichzeitig verarbeitet werden können, wird jedoch durch die Anzahl der `IDispEventSimpleImpl` Basisklassen beschränkt.

`IDispEventSimplImpl` bietet die gleiche Funktionalität wie [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), mit dem Unterschied, dass keine Typinformationen über die Schnittstelle aus einer Typbibliothek abgerufen werden. Die Assistenten generieren Code, der nur auf `IDispEventImpl`basiert, aber Sie können `IDispEventSimpleImpl` verwenden, indem Sie den Code per Hand hinzufügen. Verwenden Sie `IDispEventSimpleImpl`, wenn Sie nicht über eine Typbibliothek verfügen, die die Ereignis Schnittstelle beschreibt, oder den Aufwand vermeiden möchten, der mit der Verwendung der Typbibliothek verknüpft ist.

> [!NOTE]
> `IDispEventImpl` und `IDispEventSimpleImpl` stellen eine eigene Implementierung von bereit, `IUnknown::QueryInterface` jede `IDispEventImpl` oder `IDispEventSimpleImpl` Basisklasse als separate com-Identität fungieren und gleichzeitig direkten Zugriff auf Klassenmember in Ihrem Haupt-com-Objekt zulässt.

Die CE-ATL-Implementierung von ActiveX-Ereignis senken unterstützt nur Rückgabewerte vom Typ HRESULT oder void aus den Ereignishandlermethoden. alle anderen Rückgabewerte werden nicht unterstützt, und ihr Verhalten ist nicht definiert.

Weitere Informationen finden Sie [unter Unterstützung von IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Voraussetzungen

**Header:** Atlcom. h

##  <a name="advise"></a>IDispEventSimpleImpl:: Empfehlung

Mit dieser Methode können Sie eine Verbindung mit der von *Punk*dargestellten Ereignis Quelle herstellen.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parameter

*Kro*<br/>
in Ein Zeiger auf die `IUnknown`-Schnittstelle des Ereignis Quell Objekts.

### <a name="return-value"></a>Rückgabewert

S_OK oder ein HRESULT-Fehlerwert.

### <a name="remarks"></a>Hinweise

Nachdem die Verbindung hergestellt wurde, werden Ereignisse, die von *Punk* ausgelöst werden, mithilfe der Ereignis Senk Karte an Handler in ihrer Klasse weitergeleitet.

> [!NOTE]
>  Wenn Ihre Klasse von mehreren `IDispEventSimpleImpl` Klassen abgeleitet ist, müssen Sie Aufrufe dieser Methode unterscheiden, indem Sie den Aufruf mit der jeweiligen Basisklasse, an der Sie interessiert sind, einplanen.

`Advise` eine Verbindung mit der Standard Ereignis Quelle herstellt, ruft Sie die IID der Standard Ereignis Quelle des Objekts ab, die von [atlgetobjectsourceinterface](composite-control-global-functions.md#atlgetobjectsourceinterface)bestimmt wird.

##  <a name="dispeventadvise"></a>IDispEventSimpleImpl::D ispeventrat

Mit dieser Methode können Sie eine Verbindung mit der von *Punk*dargestellten Ereignis Quelle herstellen.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parameter

*Kro*<br/>
in Ein Zeiger auf die `IUnknown`-Schnittstelle des Ereignis Quell Objekts.

*piid*<br/>
Ein Zeiger auf die IID des Ereignis Quell Objekts.

### <a name="return-value"></a>Rückgabewert

S_OK oder ein HRESULT-Fehlerwert.

### <a name="remarks"></a>Hinweise

Anschließend werden Ereignisse, die von *Punk* ausgelöst werden, mithilfe der Ereignis Senk Karte an Handler in ihrer Klasse weitergeleitet.

> [!NOTE]
>  Wenn Ihre Klasse von mehreren `IDispEventSimpleImpl` Klassen abgeleitet ist, müssen Sie Aufrufe dieser Methode unterscheiden, indem Sie den Aufruf mit der jeweiligen Basisklasse, an der Sie interessiert sind, einplanen.

`DispEventAdvise` stellt eine Verbindung mit der in `pdiid`angegebenen Ereignis Quelle her.

##  <a name="dispeventunadvise"></a>IDispEventSimpleImpl::D ispeventunrat

Unterbricht die Verbindung mit der durch *Punk*dargestellten Ereignis Quelle.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parameter

*Kro*<br/>
in Ein Zeiger auf die `IUnknown`-Schnittstelle des Ereignis Quell Objekts.

*piid*<br/>
Ein Zeiger auf die IID des Ereignis Quell Objekts.

### <a name="return-value"></a>Rückgabewert

S_OK oder ein HRESULT-Fehlerwert.

### <a name="remarks"></a>Hinweise

Nachdem die Verbindung getrennt wurde, werden die Ereignisse nicht mehr an die Handlerfunktionen weitergeleitet, die in der Ereignis Senk Karte aufgeführt sind.

> [!NOTE]
>  Wenn Ihre Klasse von mehreren `IDispEventSimpleImpl` Klassen abgeleitet ist, müssen Sie Aufrufe dieser Methode unterscheiden, indem Sie den Aufruf mit der jeweiligen Basisklasse, an der Sie interessiert sind, einplanen.

`DispEventAdvise` unterbricht eine Verbindung, die mit der in `pdiid`angegebenen Ereignis Quelle hergestellt wurde.

##  <a name="getidsofnames"></a>IDispEventSimpleImpl:: GetIDsOfNames

Diese Implementierung von `IDispatch::GetIDsOfNames` gibt E_NOTIMPL zurück.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) im Windows SDK.

##  <a name="gettypeinfo"></a>IDispEventSimpleImpl:: gettypeingefo

Diese Implementierung von `IDispatch::GetTypeInfo` gibt E_NOTIMPL zurück.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [IDispatch:: gettypeingefo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) im Windows SDK.

##  <a name="gettypeinfocount"></a>IDispEventSimpleImpl:: gettypanfocount

Diese Implementierung von `IDispatch::GetTypeInfoCount` gibt E_NOTIMPL zurück.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [IDispatch:: gettypeingefocount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) in der Windows SDK.

##  <a name="invoke"></a>IDispEventSimpleImpl:: aufrufen

Bei dieser Implementierung von `IDispatch::Invoke` werden die in der Ereignis senkenzuordnung aufgeführten Ereignishandler aufgerufen.

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

### <a name="remarks"></a>Hinweise

Siehe [IDispatch:: Aufrufen](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

##  <a name="unadvise"></a>IDispEventSimpleImpl:: nicht Empfehlung

Unterbricht die Verbindung mit der durch *Punk*dargestellten Ereignis Quelle.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parameter

*Kro*<br/>
in Ein Zeiger auf die `IUnknown`-Schnittstelle des Ereignis Quell Objekts.

### <a name="return-value"></a>Rückgabewert

S_OK oder ein HRESULT-Fehlerwert.

### <a name="remarks"></a>Hinweise

Nachdem die Verbindung getrennt wurde, werden die Ereignisse nicht mehr an die Handlerfunktionen weitergeleitet, die in der Ereignis Senk Karte aufgeführt sind.

> [!NOTE]
>  Wenn Ihre Klasse von mehreren `IDispEventSimpleImpl` Klassen abgeleitet ist, müssen Sie Aufrufe dieser Methode unterscheiden, indem Sie den Aufruf mit der jeweiligen Basisklasse, an der Sie interessiert sind, einplanen.

`Unadvise` unterbricht eine Verbindung, die mit der in `pdiid`angegebenen Standard Ereignis Quelle hergestellt wurde.

`Unavise` eine Verbindung mit der Standard Ereignis Quelle unterbricht, ruft Sie die IID der Standard Ereignis Quelle des Objekts ab, die von [atlgetobjectsourceinterface](composite-control-global-functions.md#atlgetobjectsourceinterface)bestimmt wird.

## <a name="see-also"></a>Siehe auch

[_ATL_FUNC_INFO-Struktur](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl-Klasse](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl-Klasse](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)
