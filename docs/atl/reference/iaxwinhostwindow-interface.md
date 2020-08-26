---
title: IAxWinHostWindow-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
ms.openlocfilehash: 44681b94e0bd1dfd757ebfa19f83074785dd95f5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833373"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow-Schnittstelle

Diese Schnittstelle stellt Methoden zum Bearbeiten eines Steuer Elements und seines Host Objekts bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|Beschreibung|
|-|-|
|[AttachControl](#attachcontrol)|Fügt ein vorhandenes Steuerelement an das Host Objekt an.|
|[CreateControl](#createcontrol)|Erstellt ein-Steuerelement und fügt es an das Host Objekt an.|
|["Kreatecontrolex"](#createcontrolex)|Erstellt ein Steuerelement, fügt es an das Host Objekt an und richtet optional einen Ereignishandler ein.|
|[Querycontrol](#querycontrol)|Gibt einen Schnittstellen Zeiger auf das gehostete-Steuerelement zurück.|
|["Abtexternaldispatch"](#setexternaldispatch)|Legt die externe `IDispatch` Schnittstelle fest.|
|["Abtexternaluihandler"](#setexternaluihandler)|Legt die externe `IDocHostUIHandlerDispatch` Schnittstelle fest.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle wird durch die ActiveX-Steuerelemente des ATL-Steuer Elements verfügbar gemacht. Rufen Sie die-Methoden für diese Schnittstelle auf, um ein Steuerelement zu erstellen und/oder an das Host Objekt anzufügen, um eine Schnittstelle von einem gehosteten Steuerelement abzurufen oder die externe dispinterface oder den UI-Handler für die Verwendung beim Hosten des Webbrowsers festzulegen

## <a name="requirements"></a>Requirements (Anforderungen)

Die Definition dieser Schnittstelle ist als IDL oder C++ verfügbar, wie unten gezeigt.

|Definitionstyp|Datei|
|---------------------|----------|
|IDL|Atliface. idl|
|C++|Atliface. h (auch in "atlbase. h" enthalten)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a> IAxWinHostWindow:: AttachControl

Fügt ein vorhandenes (und zuvor initialisiertes) Steuerelement mithilfe des durch *HWND*identifizierten Fensters an das Host Objekt an.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parameter

*punkcontrol*<br/>
in Ein Zeiger auf die- `IUnknown` Schnittstelle des Steuer Elements, das an das Host Objekt angefügt werden soll.

*hWnd*<br/>
in Ein Handle für das Fenster, das für das Hosting verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a> IAxWinHostWindow:: kreatecontrol

Erstellt ein Steuerelement, initialisiert es und hostet es im durch *HWND*identifizierten Fenster.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parameter

*lpzcsdata*<br/>
in Eine Zeichenfolge zur Identifizierung des zu erstellenden Steuer Elements Kann eine CLSID (muss die geschweiften Klammern enthalten), ProgID, URL oder unformatierte HTML-Datei (mit dem Präfix **MSHTML:**) sein.

*hWnd*<br/>
in Ein Handle für das Fenster, das für das Hosting verwendet werden soll.

*pStream*<br/>
in Ein Schnittstellen Zeiger für einen Stream, der Initialisierungs Daten für das Steuerelement enthält. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Dieses Fenster wird durch das Host Objekt untergeordnet, das diese Schnittstelle verfügbar macht, sodass Nachrichten für das Steuerelement reflektiert werden können und andere Container Funktionen funktionieren.

Das Aufrufen dieser Methode entspricht dem Aufrufen von [IAxWinHostWindow:: createcontrolex](#createcontrolex).

Informationen zum Erstellen eines lizenzierten ActiveX-Steuer Elements finden Sie unter [iaxwinhostwindowlisch:: kreatecontrollic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a> IAxWinHostWindow:: kreatecontrolex

Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [IAxWinHostWindow:: kreatecontrol](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Parameter

*lpzcsdata*<br/>
in Eine Zeichenfolge zur Identifizierung des zu erstellenden Steuer Elements Kann eine CLSID (muss die geschweiften Klammern enthalten), ProgID, URL oder unformatierten HTML-Code (mit dem Präfix **MSHTML:**) sein.

*hWnd*<br/>
in Ein Handle für das Fenster, das für das Hosting verwendet werden soll.

*pStream*<br/>
in Ein Schnittstellen Zeiger für einen Stream, der Initialisierungs Daten für das Steuerelement enthält. Kann den Wert NULL haben.

*ppUnk*<br/>
vorgenommen Die Adresse eines Zeigers, der die- `IUnknown` Schnittstelle des erstellten Steuer Elements empfängt. Kann den Wert NULL haben.

*riidrat*<br/>
in Der Schnittstellen Bezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt. Kann IID_NULL werden.

*punkrat*<br/>
in Ein Zeiger auf die- `IUnknown` Schnittstelle des Sink-Objekts, das mit dem Verbindungspunkt auf dem durch angegebenen enthaltenen Objekt verbunden werden soll `iidSink` .

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Anders als bei der- `CreateControl` Methode `CreateControlEx` können Sie auch einen Schnittstellen Zeiger auf das neu erstellte Steuerelement empfangen und eine Ereignis Senke für den Empfang von Ereignissen einrichten, die vom Steuerelement ausgelöst werden.

Informationen zum Erstellen eines lizenzierten ActiveX-Steuer Elements finden Sie unter [iaxwinhostwindowlischen:: kreatecontrollicex](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a> IAxWinHostWindow:: querycontrol

Gibt den angegebenen vom gehosteten Steuerelement bereitgestellten Schnittstellen Zeiger zurück.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
in Die ID einer Schnittstelle für das angeforderte Steuerelement.

*ppvObject*<br/>
vorgenommen Die Adresse eines Zeigers, der die angegebene Schnittstelle des erstellten Steuer Elements empfängt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> IAxWinHostWindow:: abtexternaldispatch

Legt die externe dispinterface-Methode fest, die mit der [idochostuihandlerdispatch:: getexternal](../../atl/reference/idochostuihandlerdispatch-interface.md) -Methode für enthaltene Steuerelemente verfügbar ist.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
in Ein Zeiger auf eine- `IDispatch` Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> IAxWinHostWindow:: abtexternaluihandler

Mit dieser Funktion wird die externe [idochostuihandlerdispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) -Schnittstelle für das Objekt festgelegt `CAxWindow` .

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
in Ein Zeiger auf eine- `IDocHostUIHandlerDispatch` Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird von Steuerelementen (z. b. dem Webbrowser-Steuerelement) verwendet, die die Website des Hosts für die `IDocHostUIHandlerDispatch` Schnittstelle Abfragen.

## <a name="see-also"></a>Weitere Informationen

[IAxWinAmbientDispatch-Schnittstelle](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow:: QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
