---
title: IDispEventImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: fa6e9f972accd0115d9f1e3248bd97ddde0c3c63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329760"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl-Klasse

Diese Klasse stellt Implementierungen der `IDispatch` Methoden bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>Parameter

*nID*<br/>
Ein eindeutiger Bezeichner für das Quellobjekt. Wenn `IDispEventImpl` die Basisklasse für ein zusammengesetztes Steuerelement ist, verwenden Sie die Ressourcen-ID des gewünschten enthaltenen Steuerelements für diesen Parameter. In anderen Fällen verwenden Sie eine beliebige positive ganze Zahl.

*T*<br/>
Die Klasse des Benutzers, `IDispEventImpl`die von abgeleitet wird.

*pdiid*<br/>
Der Zeiger auf die IID des Ereignisdispinterfaces, das von dieser Klasse implementiert wurde. Diese Schnittstelle muss in der Typbibliothek definiert sein, die mit *plibid*, *wMajor*und *wMinor*bezeichnet wird.

*plibid*<br/>
Ein Zeiger auf die Typbibliothek, die die Dispatchschnittstelle definiert, auf die *pdiid*. Wenn **&GUID_NULL**, wird die Typbibliothek aus dem Objekt geladen, das die Ereignisse bezieht.

*wMajor*<br/>
Die Hauptversion der Typbibliothek Der Standardwert ist 0.

*wMinor*<br/>
Die Nebenversion der Typbibliothek Der Standardwert ist 0.

*tihclass*<br/>
Die Klasse, die zum Verwalten der Typinformationen für *T*verwendet wird. Der Standardwert ist eine `CComTypeInfoHolder`Klasse vom Typ ; Sie können diesen Vorlagenparameter jedoch überschreiben, indem Sie `CComTypeInfoHolder`eine Klasse eines anderen Typs als angeben.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|Die Klasse, die zum Verwalten der Typinformationen verwendet wird. Standardmäßig `CComTypeInfoHolder`.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Sucht den Funktionsindex für den angegebenen Dispatch-Id.|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Ordnet ein einzelnes Element und einen optionalen Satz von Argumentnamen einem entsprechenden Satz ganzzahliger DISPIDs zu.|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Ruft die Typinformationen für ein Objekt ab.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Ruft die Anzahl der Typinformationsschnittstellen ab.|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Ruft den Basistyp eines benutzerdefinierten Typs ab.|

## <a name="remarks"></a>Bemerkungen

`IDispEventImpl`bietet eine Möglichkeit zum Implementieren einer Ereignisdispinterface, ohne dass Sie Implementierungscode für jede Methode/jedes Ereignis auf dieser Schnittstelle bereitstellen müssen. `IDispEventImpl`stellt Implementierungen `IDispatch` der Methoden bereit. Sie müssen nur Implementierungen für die Ereignisse bereitstellen, die Sie behandeln möchten.

`IDispEventImpl`funktioniert in Verbindung mit der Ereignissenkenzuordnung in Ihrer Klasse, um Ereignisse an die entsprechende Handlerfunktion weiterzuleiten. So verwenden Sie diese Klasse:

Fügen Sie der Ereignissenkenzuordnung für jedes Ereignis für jedes Objekt, das Sie behandeln möchten, ein [SINK_ENTRY](composite-control-macros.md#sink_entry) oder [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) Makro hinzu. Wenn `IDispEventImpl` Sie als Basisklasse eines zusammengesetzten Steuerelements verwenden, können Sie [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) aufrufen, um die Verbindung mit den Ereignisquellen für alle Einträge in der Ereignissenkenzuordnung herzustellen und zu unterbrechen. Rufen Sie in anderen Fällen oder für eine bessere Kontrolle [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) auf, um die Verbindung zwischen dem Quellobjekt und der Basisklasse herzustellen. Rufen Sie [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) auf, um die Verbindung zu unterbrechen.

Sie müssen für `IDispEventImpl` jedes Objekt, für das Sie Ereignisse verarbeiten müssen, von (mit einem eindeutigen Wert für *nID*) ableiten. Sie können die Basisklasse wiederverwenden, indem Sie die Empfehlung für ein Quellobjekt aufdecken und dann von einem anderen Quellobjekt abberaten, `IDispEventImpl` aber die maximale Anzahl von Quellobjekten, die von einem einzelnen Objekt gleichzeitig behandelt werden können, wird durch die Anzahl der Basisklassen begrenzt.

`IDispEventImpl`bietet die gleiche Funktionalität wie [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), außer es ruft Typinformationen über die Schnittstelle aus einer Typbibliothek ab, anstatt sie als Zeiger auf eine [_ATL_FUNC_INFO-Struktur](../../atl/reference/atl-func-info-structure.md) bereitzustellen. Verwenden `IDispEventSimpleImpl` Sie diese Datei, wenn Sie nicht über eine Typbibliothek verfügen, die die Ereignisschnittstelle beschreibt, oder wenn Sie den mit der Verwendung der Typbibliothek verbundenen Overhead vermeiden möchten.

> [!NOTE]
> `IDispEventImpl`und `IDispEventSimpleImpl` stellen Sie `IUnknown::QueryInterface` eine `IDispEventImpl` eigene `IDispEventSimpleImpl` Implementierung bereit, die es jeder Basisklasse ermöglicht, als separate COM-Identität zu fungieren, während gleichzeitig der direkte Zugriff auf Klassenmember in Ihrem Haupt-COM-Objekt möglich ist.

Die CE ATL-Implementierung von ActiveX-Ereignissenken unterstützt nur Rückgabewerte vom Typ HRESULT oder void von Ihren Ereignishandlermethoden. Jeder andere Rückgabewert wird nicht unterstützt, und sein Verhalten ist nicht definiert.

Weitere Informationen finden Sie unter [Unterstützen von IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoFromId

Sucht den Funktionsindex für den angegebenen Dispatch-Id.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Ein Verweis auf die ID der Funktion.

*dispidMember*<br/>
[in] Die Dispatch-ID der Funktion.

*lcid*<br/>
[in] Der Gebietsschemakontext der Funktions-ID.

*info*<br/>
[in] Die Struktur, die angibt, wie die Funktion aufgerufen wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="idispeventimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames

Ordnet einen einzelnen Member und einen optionalen Satz von Argumentnamen einem entsprechenden Satz ganzzahliger DISPIDs zu, die bei nachfolgenden Aufrufen von [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)verwendet werden können.

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

## <a name="idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo

Ruft die Typinformationen für ein Objekt ab, die dann zum Abrufen der Typinformationen für eine Schnittstelle verwendet werden können.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Bemerkungen

## <a name="idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount

Ruft die Anzahl der Schnittstellen mit Typinformationen ab, die von einem Objekt bereitgestellt werden (0 oder 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Bemerkungen

Siehe [iDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) im Windows SDK.

## <a name="idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefinedType

Ruft den Basistyp eines benutzerdefinierten Typs ab.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Parameter

*Pti*<br/>
[in] Ein Zeiger auf die [ITypeInfo-Schnittstelle,](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) die den benutzerdefinierten Typ enthält.

*Hrt*<br/>
[in] Ein Handle für die Typbeschreibung, die abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Der Typ der Variante.

### <a name="remarks"></a>Bemerkungen

Siehe [iTypeInfo::GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

## <a name="idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl

Der Konstruktor. Speichert die Werte der Klassenvorlagenparameter *plibid*, *pdiid*, *wMajor*und *wMinor*.

```
IDispEventImpl();
```

## <a name="idispeventimpltihclass"></a><a name="tihclass"></a>IDispEventImpl::tihclass

Dieser typedef ist eine Instanz des Klassenvorlagenparameters *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig ist `CComTypeInfoHolder`die Klasse . `CComTypeInfoHolder`verwaltet die Typinformationen für die Klasse.

## <a name="see-also"></a>Siehe auch

[_ATL_FUNC_INFO Struktur](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl-Klasse](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl-Klasse](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
