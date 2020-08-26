---
title: Idochostuihandlerdispatch-Schnittstelle
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 4d80934a5768eda917c90345ddeeff017edf0eae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835440"
---
# <a name="idochostuihandlerdispatch-interface"></a>Idochostuihandlerdispatch-Schnittstelle

Eine Schnittstelle zum Microsoft HTML-Modul für die-und-Rendering-Engine.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

> [!NOTE]
> Die Links in der folgenden Tabelle beziehen sich auf die inet SDK-Referenz Themen für die Member der [idocuihusthandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) -Schnittstelle. `IDocHostUIHandlerDispatch` verfügt über die gleiche Funktionalität wie `IDocUIHostHandler` , mit dem Unterschied, dass `IDocHostUIHandlerDispatch` eine dispinterface ist, während `IDocUIHostHandler` eine benutzerdefinierte Schnittstelle ist.

|Name|Beschreibung|
|-|-|
|[Enablemodeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Wird von der MSHTML-Implementierung von [IOleInPlaceActiveObject:: enablemodeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)aufgerufen. Wird auch aufgerufen, wenn MSHTML eine modale Benutzeroberfläche anzeigt.|
|[Filterdataobject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Wird auf dem Host von MSHTML aufgerufen, um dem Host das Ersetzen des Datenobjekts von MSHTML zu ermöglichen.|
|[Getdroptarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Wird von MSHTML aufgerufen, wenn es als Ablage Ziel verwendet wird, um dem Host die Bereitstellung eines alternativen [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)zu ermöglichen.|
|[Getexternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Wird von MSHTML aufgerufen, um die IDispatch-Schnittstelle des Hosts zu erhalten.|
|[Gethostinfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Ruft die Benutzeroberflächen Funktionen des MSHTML-Hosts ab.|
|[Getoptionkeypath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Gibt den Registrierungsschlüssel zurück, unter dem MSHTML Benutzereinstellungen speichert.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Wird aufgerufen, wenn MSHTML seine Menüs und Symbolleisten entfernt.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Wird von der MSHTML-Implementierung von [IOleInPlaceActiveObject:: ondocwindowaktivierungs](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)aufgerufen.|
|[OnFrameWindowActivate aufgerufen](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Wird von der MSHTML-Implementierung von [IOleInPlaceActiveObject:: onframewindowaktivierungs](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)aufgerufen.|
|[Resizeborder in](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Wird von der MSHTML-Implementierung von [IOleInPlaceActiveObject:: resizeborder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)aufgerufen.|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Wird von MSHTML aufgerufen, um ein Kontextmenü anzuzeigen.|
|[Wenn showUI auf](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Ermöglicht es dem Host, MSHTML-Menüs und Symbolleisten zu ersetzen.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Wird von MSHTML aufgerufen, wenn [IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) oder [iolecontrolsite:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) aufgerufen wird.|
|[Translateurl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Wird von MSHTML aufgerufen, um dem Host die Möglichkeit zu geben, die zu ladende URL zu ändern.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Benachrichtigt den Host, dass sich der Befehlsstatus geändert hat.|

## <a name="remarks"></a>Bemerkungen

Ein Host kann durch Implementieren dieser Schnittstelle die Menüs, Symbolleisten und Kontextmenüs ersetzen, die von der Microsoft HTML-Modell-und-Rendering-Engine (MSHTML) verwendet werden.

## <a name="requirements"></a>Requirements (Anforderungen)

Die Definition dieser Schnittstelle ist als IDL oder C++ verfügbar, wie unten gezeigt.

|Definitionstyp|Datei|
|---------------------|----------|
|IDL|Atliface. idl|
|C++|Atliface. h (auch in "atlbase. h" enthalten)|

## <a name="see-also"></a>Weitere Informationen

[Idocuihusthandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
