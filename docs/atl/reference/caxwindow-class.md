---
title: CAxWindow-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 6f5629370bc1f821dac0a08cc76b5df1450f7a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318722"
---
# <a name="caxwindow-class"></a>CAxWindow-Klasse

Diese Klasse stellt Methoden zum Bearbeiten eines Fensters bereit, in dem ein ActiveX-Steuerelement gehostet wird.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[AttachControl](#attachcontrol)|Fügt dem `CAxWindow` Objekt ein vorhandenes ActiveX-Steuerelement an.|
|[CAxWindow](#caxwindow)|Erstellt ein `CAxWindow`-Objekt.|
|[CreateControl](#createcontrol)|Erstellt ein ActiveX-Steuerelement, initialisiert es und `CAxWindow` hostet es im Fenster.|
|[CreateControlEx](#createcontrolex)|Erstellt ein ActiveX-Steuerelement und ruft einen Schnittstellenzeiger (oder Zeiger) aus dem Steuerelement ab.|
|[GetWndClassName](#getwndclassname)|(Statisch) Ruft den vordefinierten Klassennamen `CAxWindow` des Objekts ab.|
|[QueryControl](#querycontrol)|Ruft das `IUnknown` des gehosteten ActiveX-Steuerelements ab.|
|[QueryHost](#queryhost)|Ruft den `IUnknown` Zeiger des `CAxWindow` Objekts ab.|
|[SetExternalDispatch](#setexternaldispatch)|Legt die externe Dispatchschnittstelle `CAxWindow` fest, die vom Objekt verwendet wird.|
|[SetExternalUIHandler](#setexternaluihandler)|Legt die `IDocHostUIHandler` vom `CAxWindow` Objekt verwendete externe Schnittstelle fest.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#operator_eq)|Weist einem vorhandenen `CAxWindow` Objekt eine HWND zu.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden zum Bearbeiten eines Fensters bereit, das ein ActiveX-Steuerelement hostet. Das Hosting wird von " **AtlAxWin80"** `CAxWindow`bereitgestellt, das von umschlossen wird.

Die `CAxWindow` Klasse wird als Spezialisierung `CAxWindowT` der Klasse implementiert. Diese Spezialisierung wird wie:

`typedef CAxWindowT<CWindow> CAxWindow;`

Wenn Sie die Basisklasse ändern müssen, können Sie die neue Basisklasse als Vorlagenargument verwenden `CAxWindowT` und angeben.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a>CAxWindow::AttachControl

Erstellt ein neues Hostobjekt, wenn es noch nicht vorhanden ist, und fügt das angegebene Steuerelement an den Host an.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parameter

*pControl*<br/>
[in] Ein Zeiger auf `IUnknown` das Steuerelement.

*ppUnkContainer*<br/>
[out] Ein Zeiger auf `IUnknown` den des `AxWin` Hosts (des Objekts).

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Das angehängte Steuerelementobjekt muss vor `AttachControl`dem Aufruf korrekt initialisiert werden.

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a>CAxWindow::CAxWindow

Erstellt ein `CAxWindow` Objekt mit einem vorhandenen Fensterobjekthandle.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle für ein vorhandenes Fensterobjekt.

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a>CAxWindow::CreateControl

Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.

```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, um das Steuerelement zu erstellen. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID wie`"MSCAL.Calendar.7"`

- Eine CLSID wie`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie`"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. B.`"file://\\\Documents\MyDoc.doc"`

- Ein HTML-Fragment wie`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`muss dem HTML-Fragment vorangestellt werden, damit es als MSHTML-Stream bezeichnet wird. Nur ProgID und CLSID werden in Windows Mobile-Plattformen unterstützt. Windows CE Embedded-Plattformen, mit Ausnahme von Windows Mobile mit Unterstützung für CE IE unterstützen alle Typen einschließlich ProgID, CLSID, URL, Verweis auf aktive saktivdokument und HTML-Fragment.

*pStream*<br/>
[in] Ein Zeiger auf einen Stream, der zum Initialisieren der Eigenschaften des Steuerelements verwendet wird. Kann den Wert NULL haben.

*ppUnkContainer*<br/>
[out] Die Adresse eines Zeigers, `IUnknown` der den Container empfängt. Kann den Wert NULL haben.

*dwResID*<br/>
Die Ressourcen-ID einer HTML-Ressource. Das WebBrowser-Steuerelement wird erstellt und mit der angegebenen Ressource geladen.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Wenn die zweite Version dieser Methode verwendet wird, wird ein HTML-Steuerelement erstellt und an die von *dwResID*identifizierte Ressource gebunden.

Diese Methode gibt Ihnen das gleiche Ergebnis wie das Aufrufen:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Siehe [CAxWindow2T::CreateControlLic,](../../atl/reference/caxwindow2t-class.md#createcontrollic) um ein lizenziertes ActiveX-Steuerelement zu erstellen, zu initialisieren und zu hosten.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen unter Verwendung von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das `CreateControl`verwendet.

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a>CAxWindow::CreateControlEx

Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.

```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, um das Steuerelement zu erstellen. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID wie`"MSCAL.Calendar.7"`

- Eine CLSID wie`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie`"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. B.`"file://\\\Documents\MyDoc.doc"`

- Ein HTML-Fragment wie`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`muss dem HTML-Fragment vorangestellt werden, damit es als MSHTML-Stream bezeichnet wird. Nur ProgID und CLSID werden in Windows Mobile-Plattformen unterstützt. Windows CE Embedded-Plattformen, mit Ausnahme von Windows Mobile mit Unterstützung für CE IE unterstützen alle Typen einschließlich ProgID, CLSID, URL, Verweis auf aktive saktivdokument und HTML-Fragment.

*pStream*<br/>
[in] Ein Zeiger auf einen Stream, der zum Initialisieren der Eigenschaften des Steuerelements verwendet wird. Kann den Wert NULL haben.

*ppUnkContainer*<br/>
[out] Die Adresse eines Zeigers, `IUnknown` der den Container empfängt. Kann den Wert NULL haben.

*ppUnkControl*<br/>
[out] Die Adresse eines Zeigers, `IUnknown` der die des Steuerelements empfängt. Kann den Wert NULL haben.

*iidSink*<br/>
[in] Der Schnittstellenbezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt. Kann IID_NULL werden.

*punkSink*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des Senkenobjekts, der mit dem Verbindungspunkt des enthaltenen Objekts verbunden werden soll, das von *iidSink*angegeben wird.

*dwResID*<br/>
[in] Die Ressourcen-ID einer HTML-Ressource. Das WebBrowser-Steuerelement wird erstellt und mit der angegebenen Ressource geladen.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Diese Methode ähnelt [CAxWindow::CreateControl](#createcontrol), `CreateControlEx` aber im Gegensatz zu dieser Methode können Sie auch einen Schnittstellenzeiger auf das neu erstellte Steuerelement empfangen und eine Ereignissenke einrichten, um Ereignisse zu empfangen, die vom Steuerelement ausgelöst werden.

Siehe [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) zum Erstellen, Initialisieren und Hosten eines lizenzierten ActiveX-Steuerelements.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen unter Verwendung von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das `CreateControlEx`verwendet.

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow::GetWndClassName

Ruft den Namen der Fensterklasse ab.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Zeichenfolge, die den Namen der Fensterklasse enthält, die nicht lizenzierte ActiveX-Steuerelemente hosten kann.

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a>CAxWindow::operator =

Weist einem vorhandenen `CAxWindow` Objekt eine HWND zu.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle für ein vorhandenes Fenster.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das aktuelle `CAxWindow`-Objekt zurück.

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a>CAxWindow::QueryControl

Ruft die angegebene Schnittstelle des gehosteten Steuerelements ab.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Gibt die IID der Benutzeroberfläche des Steuerelements an.

*ppUnk*<br/>
[out] Ein Zeiger auf die Schnittstelle des Steuerelements. In der Vorlagenversion dieser Methode ist keine Referenz-ID erforderlich, solange eine typisierte Schnittstelle mit einer zugeordneten UUID übergeben wird.

*Q*<br/>
[in] Die Schnittstelle, nach der abgefragt wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a>CAxWindow::QueryHost

Gibt die angegebene Schnittstelle des Hosts zurück.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Gibt die IID der Benutzeroberfläche des Steuerelements an.

*ppUnk*<br/>
[out] Ein Zeiger auf die Schnittstelle auf dem Host. In der Vorlagenversion dieser Methode ist keine Referenz-ID erforderlich, solange eine typisierte Schnittstelle mit einer zugeordneten UUID übergeben wird.

*Q*<br/>
[in] Die Schnittstelle, nach der abgefragt wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die Schnittstelle des Hosts ermöglicht den Zugriff auf die zugrunde `AxWin`liegende Funktionalität des Window-Hosting-Codes, implementiert von .

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

Legt die externe Dispatchschnittstelle für das `CAxWindow` Objekt fest.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
[in] Ein Zeiger auf `IDispatch` eine Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

Legt die externe [IDocHostUIHandlerDispatch-Schnittstelle](../../atl/reference/idochostuihandlerdispatch-interface.md) für das `CAxWindow` Objekt fest.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parameter

*pUIHandler*<br/>
[in] Ein Zeiger auf `IDocHostUIHandlerDispatch` eine Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die `IDocHostUIHandlerDispatch` externe Schnittstelle wird von Steuerelementen verwendet, `IDocHostUIHandlerDispatch` die die Hostsite für die Schnittstelle abfragen. Das WebBrowser-Steuerelement ist ein Steuerelement, das dies tut.

## <a name="see-also"></a>Siehe auch

[ATLCON-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[CWindow-Klasse](../../atl/reference/cwindow-class.md)<br/>
[Grundlagen von zusammengesetzten Steuerelementen](../../atl/atl-composite-control-fundamentals.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Fragen und Antworten zur Steuerelementkapselung](../../atl/atl-control-containment-faq.md)
