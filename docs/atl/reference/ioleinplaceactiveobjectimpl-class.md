---
title: IOleInPlaceActiveObjectImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
ms.openlocfilehash: b39ba2845a5483444dac53d1616654e902969c77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326585"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl-Klasse

Diese Klasse stellt Methoden zur Unterstützung der Kommunikation zwischen einem ortsgesteuerten Steuerelement und seinem Container bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IOleInPlaceActiveObjectImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Aktiviert kontextsensitive Hilfe. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Aktiviert moduslose Dialogfelder. Die ATL-Implementierung gibt S_OK zurück.|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Ruft einen Fensterhandle ab.|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Benachrichtigt das Steuerelement, wenn das Dokumentfenster des Containers aktiviert oder deaktiviert wird. Die ATL-Implementierung gibt S_OK zurück.|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Benachrichtigt das Steuerelement, wenn das Rahmenfenster der obersten Ebene des Containers aktiviert oder deaktiviert wird. Die ATL-Implementierung gibt|
|[IOleInPlaceActiveObjectImpl::ResizeBorder ändern](#resizeborder)|Informiert die Kontrolle, die es benötigt, um die Größe seiner Grenzen zu ändern. Die ATL-Implementierung gibt S_OK zurück.|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Verarbeitet Menübeschleuniger-Schlüsselmeldungen aus dem Container. Die ATL-Implementierung gibt E_NOTIMPL zurück.|

## <a name="remarks"></a>Bemerkungen

Die [IOleInPlaceActiveObject-Schnittstelle](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) unterstützt die Kommunikation zwischen einem ortsansässigen Steuerelement und seinem Container. Z. B. die Kommunikation des aktiven Status des Steuerelements und containers und die Information des Steuerelements, das zum Ändern der Größe selbst erforderlich ist. Die `IOleInPlaceActiveObjectImpl` Klasse stellt `IOleInPlaceActiveObject` eine `IUnknown` Standardimplementierung von und unterstützt sie, indem Informationen in Debugbuilds an das Dump-Gerät gesendet werden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

Aktiviert kontextsensitive Hilfe.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) im Windows SDK.

## <a name="ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless

Aktiviert moduslose Dialogfelder.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleInPlaceActiveObject::EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) im Windows SDK.

## <a name="ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceActiveObjectImpl::GetWindow

Der Container ruft diese Funktion auf, um den Fenstergriff des Steuerelements abzubekommen.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Bemerkungen

Einige Container funktionieren nicht mit einem Steuerelement, das fensterlos war, auch wenn es derzeit gefenstert ist. Wenn der Datenmember in `CComControl::m_bWasOnceWindowless` der ATL-Implementierung TRUE ist, gibt die Funktion E_FAIL zurück. Andernfalls `GetWindow` weist \* phwnd dem Datenmember `m_hWnd` der Steuerelementklasse *phwnd* zu, wenn *phwnd* nicht NULL ist, und gibt S_OK zurück.

Siehe [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) im Windows SDK.

## <a name="ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a>IOleInPlaceActiveObjectImpl::OnDocWindowActivate

Benachrichtigt das Steuerelement, wenn das Dokumentfenster des Containers aktiviert oder deaktiviert wird.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) im Windows SDK.

## <a name="ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a>IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

Benachrichtigt das Steuerelement, wenn das Rahmenfenster der obersten Ebene des Containers aktiviert oder deaktiviert wird.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) im Windows SDK.

## <a name="ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder ändern

Informiert die Kontrolle, die es benötigt, um die Größe seiner Grenzen zu ändern.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleInPlaceActiveObject::ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) im Windows SDK.

## <a name="ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator

Verarbeitet Menübeschleuniger-Schlüsselmeldungen aus dem Container.

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>Rückgabewert

Diese Methode unterstützt die folgenden Rückgabewerte:

S_OK, ob die Nachricht erfolgreich übersetzt wurde.

S_FALSE, wenn die Nachricht nicht übersetzt wurde.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleInPlaceActiveObject::TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX-Steuerelementschnittstellen](/windows/win32/com/activex-controls-interfaces)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
