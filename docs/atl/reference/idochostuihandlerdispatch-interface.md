---
title: IDocHostUIHandlerDispatch-Schnittstelle
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: b7072b80b738aa12635427a2604b38fb3585b452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329722"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch-Schnittstelle

Eine Schnittstelle zum Microsoft HTML-Analyse- und Renderingmodul.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

> [!NOTE]
> Die Links in der folgenden Tabelle beziehen sich auf die INet SDK-Referenzthemen für die Mitglieder der [IDocUIHostHandler-Schnittstelle.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) `IDocHostUIHandlerDispatch`hat die gleiche `IDocUIHostHandler`Funktionalität wie , `IDocHostUIHandlerDispatch` mit dem Unterschied, dass eine Dispinterface ist, während `IDocUIHostHandler` eine benutzerdefinierte Schnittstelle ist.

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Wird von der MSHTML-Implementierung von [IOleInPlaceActiveObject::EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)aufgerufen. Wird auch aufgerufen, wenn MSHTML die modale Benutzeroberfläche anzeigt.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Wird vom Host von MSHTML aufgerufen, damit der Host das DATENobjekt von MSHTML ersetzen kann.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Wird von MSHTML aufgerufen, wenn es als Dropziel verwendet wird, damit der Host ein alternatives [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)bereitstellen kann.|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Wird von MSHTML aufgerufen, um die IDispatch-Schnittstelle des Hosts abzuerhalten.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Ruft die UI-Funktionen des MSHTML-Hosts ab.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Gibt den Registrierungsschlüssel zurück, unter dem MSHTML Benutzereinstellungen speichert.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Wird aufgerufen, wenn MSHTML seine Menüs und Symbolleisten entfernt.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Wird von der MSHTML-Implementierung von [IOleInPlaceActiveObject::OnDocWindowActivate aufgerufen.](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Wird von der MSHTML-Implementierung von [IOleInPlaceActiveObject::OnFrameWindowActivate aufgerufen.](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Wird von der MSHTML-Implementierung von [IOleInPlaceActiveObject::ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)aufgerufen.|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Wird von MSHTML aufgerufen, um ein Kontextmenü anzuzeigen.|
|[Showui](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Ermöglicht dem Host, MSHTML-Menüs und Symbolleisten zu ersetzen.|
|[Translateaccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Wird von MSHTML aufgerufen, wenn [IOleInPlaceActiveObject::TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) oder [IOleControlSite::TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) aufgerufen wird.|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Wird von MSHTML aufgerufen, damit der Host die zu ladende URL ändern kann.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Benachrichtigt den Host, dass sich der Befehlsstatus geändert hat.|

## <a name="remarks"></a>Bemerkungen

Ein Host kann die Menüs, Symbolleisten und Kontextmenüs ersetzen, die von der Microsoft HTML-Analyse- und Rendering-Engine (MSHTML) verwendet werden, indem diese Schnittstelle implementiert wird.

## <a name="requirements"></a>Anforderungen

Die Definition dieser Schnittstelle ist als IDL oder C++ verfügbar, wie unten gezeigt.

|Definitionstyp|Datei|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (auch in ATLBase.h enthalten)|

## <a name="see-also"></a>Siehe auch

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
