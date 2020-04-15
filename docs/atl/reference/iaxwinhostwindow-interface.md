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
ms.openlocfilehash: ebecc611660a788ce59bb11beb95bd60eacaf01b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329998"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow-Schnittstelle

Diese Schnittstelle stellt Methoden zum Bearbeiten eines Steuerelements und seines Hostobjekts bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[AttachControl](#attachcontrol)|Fügt dem Hostobjekt ein vorhandenes Steuerelement an.|
|[CreateControl](#createcontrol)|Erstellt ein Steuerelement und fügt es an das Hostobjekt an.|
|[CreateControlEx](#createcontrolex)|Erstellt ein Steuerelement, fügt es an das Hostobjekt an und richtet optional einen Ereignishandler ein.|
|[QueryControl](#querycontrol)|Gibt einen Schnittstellenzeiger an das gehostete Steuerelement zurück.|
|[SetExternalDispatch](#setexternaldispatch)|Legt die `IDispatch` externe Schnittstelle fest.|
|[SetExternalUIHandler](#setexternaluihandler)|Legt die `IDocHostUIHandlerDispatch` externe Schnittstelle fest.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle wird von ATLs ActiveX-Steuerelementhostingobjekten verfügbar gemacht. Rufen Sie die Methoden auf dieser Schnittstelle auf, um ein Steuerelement zu erstellen und/oder an das Hostobjekt anzufügen, eine Schnittstelle von einem gehosteten Steuerelement abzurufen oder die externe Dispinterface oder den UI-Handler für die Verwendung beim Hosten des Webbrowsers festzulegen.

## <a name="requirements"></a>Anforderungen

Die Definition dieser Schnittstelle ist als IDL oder C++ verfügbar, wie unten gezeigt.

|Definitionstyp|Datei|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (auch in ATLBase.h enthalten)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Fügt ein vorhandenes (und zuvor initialisiertes) Steuerelement mithilfe des von *hWnd*identifizierten Fensters an das Hostobjekt an.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parameter

*pUnkControl*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des Steuerelements, das an das Hostobjekt angefügt werden soll.

*hWnd*<br/>
[in] Ein Handle zum Fenster, das zum Hosten verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::CreateControl

Erstellt ein Steuerelement, initialisiert es und hostet es in dem von *hWnd*identifizierten Fenster.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parameter

*lpTricsDaten*<br/>
[in] Eine Zeichenfolge, die das zu erstellende Steuerelement identifiziert. Kann eine CLSID (muss die geschweiften Klammern enthalten), ProgID, URL oder unformatiertes HTML **(voranms:**) sein.

*hWnd*<br/>
[in] Ein Handle zum Fenster, das zum Hosten verwendet werden soll.

*pStream*<br/>
[in] Ein Schnittstellenzeiger für einen Stream, der Initialisierungsdaten für das Steuerelement enthält. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Dieses Fenster wird vom Hostobjekt unterklassen, das diese Schnittstelle bereitstellt, sodass Nachrichten an das Steuerelement zurückgesendet werden können und andere Container-Features funktionieren.

Das Aufrufen dieser Methode entspricht dem Aufrufen von [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Informationen zum Erstellen eines lizenzierten ActiveX-Steuerelements finden Sie unter [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [IAxWinHostWindow::CreateControl](#createcontrol).

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

*lpTricsDaten*<br/>
[in] Eine Zeichenfolge, die das zu erstellende Steuerelement identifiziert. Kann eine CLSID (muss die geschweiften Klammern enthalten), ProgID, URL oder unformatiertes HTML (mit **MSHTML:** vorangestellt) sein.

*hWnd*<br/>
[in] Ein Handle zum Fenster, das zum Hosten verwendet werden soll.

*pStream*<br/>
[in] Ein Schnittstellenzeiger für einen Stream, der Initialisierungsdaten für das Steuerelement enthält. Kann den Wert NULL haben.

*ppUnk*<br/>
[out] Die Adresse eines Zeigers, `IUnknown` der die Schnittstelle des erstellten Steuerelements empfängt. Kann den Wert NULL haben.

*riidAdvise*<br/>
[in] Der Schnittstellenbezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt. Kann IID_NULL werden.

*punkAdvise*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des Senkenobjekts, der mit dem `iidSink`Verbindungspunkt des enthaltenen Objekts verbunden werden soll, das von angegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Im `CreateControl` Gegensatz `CreateControlEx` zur Methode können Sie auch einen Schnittstellenzeiger auf das neu erstellte Steuerelement empfangen und eine Ereignissenke einrichten, um Ereignisse zu empfangen, die vom Steuerelement ausgelöst werden.

Informationen zum Erstellen eines lizenzierten ActiveX-Steuerelements finden Sie unter [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Gibt den angegebenen Schnittstellenzeiger zurück, der vom gehosteten Steuerelement bereitgestellt wird.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
[in] Die ID einer Schnittstelle für das angeforderte Steuerelement.

*ppvObject*<br/>
[out] Die Adresse eines Zeigers, der die angegebene Schnittstelle des erstellten Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Legt die externe Dispinterface fest, die für enthaltene Steuerelemente über die [IDocHostUIHandlerDispatch::GetExternal-Methode](../../atl/reference/idochostuihandlerdispatch-interface.md) verfügbar ist.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
[in] Ein Zeiger auf `IDispatch` eine Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Rufen Sie diese Funktion auf, um die externe `CAxWindow` [IDocHostUIHandlerDispatch-Schnittstelle](../../atl/reference/idochostuihandlerdispatch-interface.md) für das Objekt festzulegen.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
[in] Ein Zeiger auf `IDocHostUIHandlerDispatch` eine Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird von Steuerelementen (z. B. dem Webbrowsersteuerelement) `IDocHostUIHandlerDispatch` verwendet, die die Hostwebsite nach der Schnittstelle abfragen.

## <a name="see-also"></a>Siehe auch

[IAxWinAmbientDispatch-Schnittstelle](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
