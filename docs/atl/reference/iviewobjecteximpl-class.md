---
title: IViewObjectExImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
ms.openlocfilehash: 59c5657dcd892544f7e790b52325cb9ecba0dd56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326344"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl-Klasse

Diese Klasse `IUnknown` implementiert und stellt Standardimplementierungen der [Schnittstellen IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)und [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IViewObjectExImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Zeichnet eine Darstellung des Steuerelements in einem Gerätekontext.|
|[IViewObjectExImpl::Einfrieren](#freeze)|Friert die gezeichnete Darstellung eines Steuerelements ein, damit sie sich erst ändert, wenn eine `Unfreeze`. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Ruft eine vorhandene beratende Senkenverbindung für das Steuerelement ab, falls vorhanden.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Gibt die logische Palette zurück, die vom Steuerelement für das Zeichnen verwendet wird. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IViewObjectExImpl::GetExtent](#getextent)|Ruft die Anzeigegröße des Steuerelements in HIMETRIC-Einheiten (0,01 Millimeter pro Einheit) vom Steuerklassendatenmember [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)ab.|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Stellt Größenhinweise aus dem Container für das Objekt bereit, das beim Anpassen der Größe des Objekts verwendet werden soll.|
|[IViewObjectExImpl::GetRect](#getrect)|Gibt ein Rechteck zurück, das einen angeforderten Zeichnungsaspekt beschreibt. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Gibt Informationen über die Deckkraft des Objekts und die unterstützten Zeichnungsaspekte zurück.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Überprüft, ob sich der angegebene Punkt im angegebenen `pHitResult`Rechteck befindet, und gibt einen [HITRESULT-Wert](/windows/win32/api/ocidl/ne-ocidl-hitresult) in zurück.|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Überprüft, ob das Anzeigerechteck des Steuerelements einen beliebigen Punkt im angegebenen `pHitResult`Positionsrechteck überlappt, und gibt einen HITRESULT-Wert in zurück.|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Richtet eine Verbindung zwischen dem Steuerelement und einer Beratungssenke ein, damit die Senke über Änderungen in der Ansicht des Steuerelements benachrichtigt werden kann.|
|[IViewObjectExImpl::Einfrieren aufheben](#unfreeze)|Wenn Sie die gezeichnete Darstellung des Steuerelements aufheben. Die ATL-Implementierung gibt E_NOTIMPL zurück.|

## <a name="remarks"></a>Bemerkungen

Die [Schnittstellen IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)und [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) ermöglichen es einem Steuerelement, sich selbst direkt anzuzeigen und eine Beratungssenke zu erstellen und zu verwalten, um den Container über Änderungen in der Steuerelementanzeige zu benachrichtigen. Die `IViewObjectEx` Schnittstelle bietet Unterstützung für erweiterte Steuerungsfunktionen wie flimmerfreies Zeichnen, nicht rechteckige und transparente Steuerelemente und Treffertests (z. B. wie nah ein Mausklick auf dem Steuerelement sein muss). Class `IViewObjectExImpl` stellt eine Standardimplementierung dieser Schnittstellen `IUnknown` und Implementierungen bereit, indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="iviewobjecteximpldraw"></a><a name="draw"></a>IViewObjectExImpl::Draw

Zeichnet eine Darstellung des Steuerelements in einem Gerätekontext.

```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```

### <a name="remarks"></a>Bemerkungen

Diese Methode `CComControl::OnDrawAdvanced` ruft auf, die wiederum `OnDraw` die Methode der Kontrollklasse aufruft. Eine `OnDraw` Methode wird automatisch zu ihrer Steuerelementklasse hinzugefügt, wenn Sie das Steuerelement mit dem ATL-Steuerelement-Assistenten erstellen. Der Standardwert `OnDraw` des Assistenten zeichnet ein Rechteck mit der Bezeichnung "ATL 3.0".

Siehe [IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) im Windows SDK.

## <a name="iviewobjecteximplfreeze"></a><a name="freeze"></a>IViewObjectExImpl::Einfrieren

Friert die gezeichnete Darstellung eines Steuerelements ein, damit sie sich erst ändert, wenn eine `Unfreeze`. Die ATL-Implementierung gibt E_NOTIMPL zurück.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IViewObject::Freeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) im Windows SDK.

## <a name="iviewobjecteximplgetadvise"></a><a name="getadvise"></a>IViewObjectExImpl::GetAdvise

Ruft eine vorhandene beratende Senkenverbindung für das Steuerelement ab, falls vorhanden.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Bemerkungen

Die beratende Senke wird im Steuerelementklassendatenmember [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)gespeichert.

Siehe [IViewObject::GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) im Windows SDK.

## <a name="iviewobjecteximplgetcolorset"></a><a name="getcolorset"></a>IViewObjectExImpl::GetColorSet

Gibt die logische Palette zurück, die vom Steuerelement für das Zeichnen verwendet wird. Die ATL-Implementierung gibt E_NOTIMPL zurück.

```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IViewObject::GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) im Windows SDK.

## <a name="iviewobjecteximplgetextent"></a><a name="getextent"></a>IViewObjectExImpl::GetExtent

Ruft die Anzeigegröße des Steuerelements in HIMETRIC-Einheiten (0,01 Millimeter pro Einheit) vom Steuerklassendatenmember [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)ab.

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IViewObject2::GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) im Windows SDK.

## <a name="iviewobjecteximplgetnaturalextent"></a><a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent

Stellt Größenhinweise aus dem Container für das Objekt bereit, das beim Anpassen der Größe des Objekts verwendet werden soll.

```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```

### <a name="remarks"></a>Bemerkungen

Wenn `dwAspect` DVASPECT_CONTENT und *pExtentInfo->dwExtentMode* DVEXTENT_CONTENT `psizel` ist, legt * auf das Datenmember [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)der Steuerklasse fest. Andernfalls wird ein Fehler HRESULT zurückgegeben.

Siehe [IViewObjectEx::GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) im Windows SDK.

## <a name="iviewobjecteximplgetrect"></a><a name="getrect"></a>IViewObjectExImpl::GetRect

Gibt ein Rechteck zurück, das einen angeforderten Zeichnungsaspekt beschreibt. Die ATL-Implementierung gibt E_NOTIMPL zurück.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IViewObjectEx::GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) im Windows SDK.

## <a name="iviewobjecteximplgetviewstatus"></a><a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus

Gibt Informationen über die Deckkraft des Objekts und die unterstützten Zeichnungsaspekte zurück.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig gibt ATL `pdwStatus` an, dass das Steuerelement VIEWSTATUS_OPAQUE unterstützt (mögliche Werte befinden sich in der VIEWSTATUS-Enumeration). [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus)

Siehe [IViewObjectEx::GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) im Windows SDK.

## <a name="iviewobjecteximplqueryhitpoint"></a><a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint

Überprüft, ob sich der angegebene Punkt im angegebenen `pHitResult`Rechteck befindet, und gibt einen [HITRESULT-Wert](/windows/win32/api/ocidl/ne-ocidl-hitresult) in zurück.

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Bemerkungen

Der Wert kann entweder HITRESULT_HIT oder HITRESULT_OUTSIDE sein.

Wenn `dwAspect` [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)gleich ist, gibt die Methode S_OK zurück. Andernfalls gibt die Methode E_FAIL zurück.

Siehe [IViewObjectEx::QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) im Windows SDK.

## <a name="iviewobjecteximplqueryhitrect"></a><a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect

Überprüft, ob das Anzeigerechteck des Steuerelements einen beliebigen Punkt im angegebenen `pHitResult`Positionsrechteck überlappt, und gibt einen [HITRESULT-Wert](/windows/win32/api/ocidl/ne-ocidl-hitresult) in zurück.

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Bemerkungen

Der Wert kann entweder HITRESULT_HIT oder HITRESULT_OUTSIDE sein.

Wenn `dwAspect` [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)gleich ist, gibt die Methode S_OK zurück. Andernfalls gibt die Methode E_FAIL zurück.

Siehe [IViewObjectEx::QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) im Windows SDK.

## <a name="iviewobjecteximplsetadvise"></a><a name="setadvise"></a>IViewObjectExImpl::SetAdvise

Richtet eine Verbindung zwischen dem Steuerelement und einer Beratungssenke ein, damit die Senke über Änderungen in der Ansicht des Steuerelements benachrichtigt werden kann.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Bemerkungen

Der Zeiger auf die [IAdviseSink-Schnittstelle](/windows/win32/api/objidl/nn-objidl-iadvisesink) auf der Beratungssenke wird im Steuerelementklassendatenmember [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)gespeichert.

Siehe [IViewObject::SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) im Windows SDK.

## <a name="iviewobjecteximplunfreeze"></a><a name="unfreeze"></a>IViewObjectExImpl::Einfrieren aufheben

Wenn Sie die gezeichnete Darstellung des Steuerelements aufheben. Die ATL-Implementierung gibt E_NOTIMPL zurück.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IViewObject::Unfreeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze) im Windows SDK.

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle

Implementieren Sie diese Methode, um das diesem Objekt zugeordnete Handle zu schließen.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parameter

*hHandle*<br/>
Der zu schließende Griff.

### <a name="return-value"></a>Rückgabewert

Geben Sie S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das an diese Methode übergebene Handle wurde diesem Objekt zuvor durch einen Aufruf von [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)zugeordnet.

### <a name="example"></a>Beispiel

Der folgende Code zeigt `IWorkerThreadClient::CloseHandle`eine einfache Implementierung von .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Ausführen

Implementieren Sie diese Methode, um Code auszuführen, wenn das diesem Objekt zugeordnete Handle signalisiert wird.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parameter

*dwParam*<br/>
Der Benutzerparameter.

*hObject*<br/>
Der Griff, der signalisiert wurde.

### <a name="return-value"></a>Rückgabewert

Geben Sie S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das handle und der DWORD/Pointer, der an diese Methode übergeben wurde, wurden diesem Objekt zuvor durch einen Aufruf von [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)zugeordnet.

### <a name="example"></a>Beispiel

Der folgende Code zeigt `IWorkerThreadClient::Execute`eine einfache Implementierung von .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Siehe auch

[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX-Steuerelementschnittstellen](/windows/win32/com/activex-controls-interfaces)<br/>
[Tutorial](../../atl/active-template-library-atl-tutorial.md)<br/>
[Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
