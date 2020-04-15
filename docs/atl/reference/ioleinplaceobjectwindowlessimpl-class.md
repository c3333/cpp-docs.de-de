---
title: IOleInPlaceObjectWindowlessImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
ms.openlocfilehash: b0438692161f38445eb7cbed54edcc8a0ba8c0d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326579"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl-Klasse

Diese Klasse `IUnknown` implementiert und stellt Methoden bereit, die es einem fensterlosen Steuerelement ermöglichen, Fensternachrichten zu empfangen und an Drag -and-Drop-Vorgängen teilzunehmen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IOleInPlaceObjectWindowlessImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Aktiviert kontextsensitive Hilfe. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Stellt `IDropTarget` die Schnittstelle für ein aktives, fensterloses Objekt bereit, das Drag & Drop unterstützt. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Ruft einen Fensterhandle ab.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Deaktiviert ein aktives In-Place-Steuerelement.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Sendet eine Nachricht aus dem Container an ein fensterloses Steuerelement, das an Ort und Stelle aktiv ist.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Reaktiviert ein zuvor deaktiviertes Steuerelement. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Gibt an, welcher Teil des ortsgesteuerten Steuerelements sichtbar ist.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Deaktiviert und entfernt die Benutzeroberfläche, die eine ortsspezifische Aktivierung unterstützt.|

## <a name="remarks"></a>Bemerkungen

Die [IOleInPlaceObject-Schnittstelle](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) verwaltet die Reaktivierung und Deaktivierung von ortsgesteuerten Steuerelementen und bestimmt, wie viel des Steuerelements sichtbar sein soll. Die [IOleInPlaceObjectWindowless-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) ermöglicht es einem fensterlosen Steuerelement, Fensternachrichten zu empfangen und an Drag-and-Drop-Vorgängen teilzunehmen. Die `IOleInPlaceObjectWindowlessImpl` Klasse stellt `IOleInPlaceObject` eine `IOleInPlaceObjectWindowless` Standardimplementierung `IUnknown` von und implementiert durch Senden von Informationen an das Dumpgerät in Debugbuilds.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="ioleinplaceobjectwindowlessimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Gibt E_NOTIMPL zurück.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) im Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetdroptarget"></a><a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget

Gibt E_NOTIMPL zurück.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IOleInPlaceObjectWindowless::GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) im Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl::GetWindow

Der Container ruft diese Funktion auf, um den Fenstergriff des Steuerelements abzubekommen.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Bemerkungen

Einige Container funktionieren nicht mit einem Steuerelement, das fensterlos war, auch wenn es derzeit gefenstert ist. Wenn der Datenmember `m_bWasOnceWindowless` der Steuerklasse in der ATL-Implementierung TRUE ist, gibt die Funktion E_FAIL zurück. Andernfalls legt *phwnd* auf den Datenmember `m_hWnd` der Steuerelementklasse fest, wenn *phwnd* nicht NULL ist, `GetWindow` \* und gibt S_OK zurück.

Siehe [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) im Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplinplacedeactivate"></a><a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

Wird vom Container aufgerufen, um ein aktives Steuerelement an Ort und Stelle zu deaktivieren.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Bemerkungen

Diese Methode führt eine vollständige oder teilweise Deaktivierung in Abhängigkeit vom Status des Steuerelements durch. Bei Bedarf wird die Benutzeroberfläche des Steuerelements deaktiviert, und das Fenster des Steuerelements wird ggf. zerstört. Der Container wird benachrichtigt, dass das Steuerelement nicht mehr aktiv ist. Die `IOleInPlaceUIWindow` Schnittstelle, die vom Container zum Aushandeln von Menüs und Rahmenräumen verwendet wird, wird freigegeben.

Siehe [IOleInPlaceObject::InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) im Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplonwindowmessage"></a><a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Sendet eine Nachricht von einem Container an ein fensterloses Steuerelement, das an Ort und Stelle aktiv ist.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Bemerkungen

Siehe [iOleInPlaceObjectWindowless::OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) im Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplreactivateandundo"></a><a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Gibt E_NOTIMPL zurück.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Bemerkungen

Siehe [IOleInPlaceObject::ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) im Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplsetobjectrects"></a><a name="setobjectrects"></a>IOleInPlaceObjectWindowlessImpl::SetObjectRects

Wird vom Container aufgerufen, um das Steuerelement darüber zu informieren, dass sich seine Größe und/oder Position geändert hat.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Bemerkungen

Aktualisiert das Datenelement des Steuerelements `m_rcPos` und die Steuerelementanzeige. Es wird nur der Teil des Steuerelements angezeigt, der den Clipbereich schneidet. Wenn die Anzeige eines Steuerelements zuvor abgeschnitten wurde, aber der Clipping entfernt wurde, kann diese Funktion aufgerufen werden, um eine vollständige Ansicht des Steuerelements neu zu zeichnen.

Siehe [IOleInPlaceObject::SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) im Windows SDK.

## <a name="ioleinplaceobjectwindowlessimpluideactivate"></a><a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate

Deaktiviert und entfernt die Benutzeroberfläche des Steuerelements, die eine ortsgesteuerte Aktivierung unterstützt.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Bemerkungen

Legt den Datenmember `m_bUIActive` der Steuerklasse auf FALSE fest. Die ATL-Implementierung dieser Funktion gibt immer S_OK zurück.

Siehe [IOleInPlaceObject::UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
