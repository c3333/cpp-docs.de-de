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
ms.openlocfilehash: b74ecb9af2decf92f873cef8d016907b6c9474cf
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353076"
---
# <a name="caxwindow-class"></a>CAxWindow-Klasse

Diese Klasse stellt Methoden zum Bearbeiten eines Fensters bereit, das ein ActiveX-Steuerelement gehostet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Funktion|BESCHREIBUNG|
|-|-|
|[AttachControl](#attachcontrol)|Fügt ein vorhandenes ActiveX-Steuerelement an das- `CAxWindow` Objekt an.|
|[CAxWindow](#caxwindow)|Erstellt ein `CAxWindow`-Objekt.|
|[CreateControl](#createcontrol)|Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im- `CAxWindow` Fenster.|
|["Kreatecontrolex"](#createcontrolex)|Erstellt ein ActiveX-Steuerelement und Ruft einen Schnittstellen Zeiger (oder Zeiger) aus dem-Steuerelement ab.|
|[Getwndclassname](#getwndclassname)|Kum Ruft den vordefinierten Klassennamen des Objekts ab `CAxWindow` .|
|[Querycontrol](#querycontrol)|Ruft den `IUnknown` des gehosteten ActiveX-Steuer Elements ab.|
|[QueryHost](#queryhost)|Ruft den `IUnknown` Zeiger des- `CAxWindow` Objekts ab.|
|["Abtexternaldispatch"](#setexternaldispatch)|Legt die externe Dispatchschnittstelle fest, die vom-Objekt verwendet wird `CAxWindow` .|
|["Abtexternaluihandler"](#setexternaluihandler)|Legt die `IDocHostUIHandler` vom-Objekt verwendete externe Schnittstelle fest `CAxWindow` .|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator =](#operator_eq)|Weist einem vorhandenen-Objekt ein HWND zu `CAxWindow` .|

## <a name="remarks"></a>Hinweise

Diese Klasse stellt Methoden zum Bearbeiten eines Fensters bereit, das ein ActiveX-Steuerelement hostet. Das Hosting wird von " **AtlAxWin80"** bereitgestellt, das von umschließt wird `CAxWindow` .

`CAxWindow`Die Klasse wird als Spezialisierung der- `CAxWindowT` Klasse implementiert. Diese Spezialisierung wird wie folgt deklariert:

`typedef CAxWindowT<CWindow> CAxWindow;`

Wenn Sie die Basisklasse ändern müssen, können Sie verwenden `CAxWindowT` und die neue Basisklasse als Vorlagen Argument angeben.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a> CAxWindow:: AttachControl

Erstellt ein neues Host Objekt, wenn es noch nicht vorhanden ist, und fügt das angegebene Steuerelement an den Host an.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parameter

*pControl*<br/>
in Ein Zeiger auf den `IUnknown` des Steuer Elements.

*ppunkcontainer*<br/>
vorgenommen Ein Zeiger auf den `IUnknown` des Hosts (das- `AxWin` Objekt).

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Das anzufügende Steuerelement Objekt muss vor dem Aufrufen von ordnungsgemäß initialisiert werden `AttachControl` .

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a> CAxWindow:: CAxWindow

Erstellt ein- `CAxWindow` Objekt mit einem vorhandenen Fenster Objekt handle.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle für ein vorhandenes Fenster Objekt.

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a> CAxWindow:: kreatecontrol

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

*lpszname*<br/>
Ein Zeiger auf eine Zeichenfolge zum Erstellen des Steuer Elements. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID, z. b. `"MSCAL.Calendar.7"`

- Eine CLSID, z. b. `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie `"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. b. `"file://\\\Documents\MyDoc.doc"`

- Ein Fragment von HTML, z. b. `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` muss dem HTML-Fragment vorangestellt sein, damit es als MSHTML-Stream festgelegt ist. Nur die ProgID und CLSID werden auf Windows Mobile-Plattformen unterstützt. Windows CE Embedded-Plattformen (außer Windows Mobile) mit Unterstützung für CE IE unterstützen alle Typen, einschließlich ProgID, CLSID, URL, Verweis auf aktives Dokument und HTML-Fragmente.

*pStream*<br/>
in Ein Zeiger auf einen Stream, der verwendet wird, um die Eigenschaften des Steuer Elements zu initialisieren. Kann den Wert NULL haben.

*ppunkcontainer*<br/>
vorgenommen Die Adresse eines Zeigers, der den `IUnknown` des Containers empfängt. Kann den Wert NULL haben.

*dwresid*<br/>
Die Ressourcen-ID einer HTML-Ressource. Das WebBrowser-Steuerelement wird erstellt und mit der angegebenen Ressource geladen.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Wenn die zweite Version dieser Methode verwendet wird, wird ein HTML-Steuerelement erstellt und an die durch *dwresid*identifizierte Ressource gebunden.

Diese Methode gibt Ihnen dasselbe Ergebnis wie das Aufrufen von:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Weitere Informationen finden Sie unter [CAxWindow2T:: kreatecontrollic](../../atl/reference/caxwindow2t-class.md#createcontrollic) zum Erstellen, initialisieren und Hosten eines lizenzierten ActiveX-Steuer Elements.

### <a name="example"></a>Beispiel

Ein Beispiel, das verwendet, finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CreateControl` .

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a> CAxWindow:: kreatecontrolex

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

*lpszname*<br/>
Ein Zeiger auf eine Zeichenfolge zum Erstellen des Steuer Elements. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID, z. b. `"MSCAL.Calendar.7"`

- Eine CLSID, z. b. `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie `"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. b. `"file://\\\Documents\MyDoc.doc"`

- Ein Fragment von HTML, z. b. `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` muss dem HTML-Fragment vorangestellt sein, damit es als MSHTML-Stream festgelegt ist. Nur die ProgID und CLSID werden auf Windows Mobile-Plattformen unterstützt. Windows CE Embedded-Plattformen (außer Windows Mobile) mit Unterstützung für CE IE unterstützen alle Typen, einschließlich ProgID, CLSID, URL, Verweis auf aktives Dokument und HTML-Fragmente.

*pStream*<br/>
in Ein Zeiger auf einen Stream, der verwendet wird, um die Eigenschaften des Steuer Elements zu initialisieren. Kann den Wert NULL haben.

*ppunkcontainer*<br/>
vorgenommen Die Adresse eines Zeigers, der den `IUnknown` des Containers empfängt. Kann den Wert NULL haben.

*ppunkcontrol*<br/>
vorgenommen Die Adresse eines Zeigers, der den `IUnknown` des Steuer Elements empfängt. Kann den Wert NULL haben.

*iidsink*<br/>
in Der Schnittstellen Bezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt. Kann IID_NULL werden.

*punksink*<br/>
in Ein Zeiger auf die- `IUnknown` Schnittstelle des Sink-Objekts, das mit dem Verbindungspunkt für das von *iidsink*angegebene enthaltene Objekt verbunden werden soll.

*dwresid*<br/>
in Die Ressourcen-ID einer HTML-Ressource. Das WebBrowser-Steuerelement wird erstellt und mit der angegebenen Ressource geladen.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Diese Methode ähnelt [CAxWindow:: anatecontrol](#createcontrol), aber im Gegensatz zu dieser Methode `CreateControlEx` können Sie auch einen Schnittstellen Zeiger auf das neu erstellte Steuerelement empfangen und eine Ereignis Senke für den Empfang von Ereignissen einrichten, die vom Steuerelement ausgelöst werden.

Weitere Informationen finden Sie unter [CAxWindow2T:: anatecontrollicex](../../atl/reference/caxwindow2t-class.md#createcontrollicex) zum Erstellen, initialisieren und Hosten eines lizenzierten ActiveX-Steuer Elements.

### <a name="example"></a>Beispiel

Ein Beispiel, das verwendet, finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CreateControlEx` .

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a> CAxWindow:: getwndclassname

Ruft den Namen der Fenster Klasse ab.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Zeichenfolge, die den Namen der Fenster Klasse enthält, die nicht lizenzierte ActiveX-Steuerelemente hosten kann.

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a> CAxWindow:: Operator =

Weist einem vorhandenen-Objekt ein HWND zu `CAxWindow` .

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle für ein vorhandenes Fenster.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das aktuelle `CAxWindow`-Objekt zurück.

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a> CAxWindow:: querycontrol

Ruft die angegebene Schnittstelle des gehosteten Steuer Elements ab.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parameter

*IID*<br/>
in Gibt die IID der-Schnittstelle des Steuer Elements an.

*ppUnk*<br/>
vorgenommen Ein Zeiger auf die-Schnittstelle des Steuer Elements. In der Vorlagen Version dieser Methode ist keine Verweis-ID erforderlich, solange eine typisierte Schnittstelle mit einer zugeordneten UUID übermittelt wird.

*Q1*<br/>
in Die Schnittstelle, für die abgefragt wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a> CAxWindow:: QueryHost

Gibt die angegebene Schnittstelle des Hosts zurück.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parameter

*IID*<br/>
in Gibt die IID der-Schnittstelle des Steuer Elements an.

*ppUnk*<br/>
vorgenommen Ein Zeiger auf die-Schnittstelle auf dem Host. In der Vorlagen Version dieser Methode ist keine Verweis-ID erforderlich, solange eine typisierte Schnittstelle mit einer zugeordneten UUID übermittelt wird.

*Q1*<br/>
in Die Schnittstelle, für die abgefragt wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die-Schnittstelle des Hosts ermöglicht den Zugriff auf die zugrunde liegende Funktionalität des Fenster-hostingcodes, der von implementiert wird `AxWin` .

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> CAxWindow:: abtexternaldispatch

Legt die externe Dispatchschnittstelle für das- `CAxWindow` Objekt fest.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
in Ein Zeiger auf eine- `IDispatch` Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> CAxWindow:: abtexternaluihandler

Legt die externe [idochostuihandlerdispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) -Schnittstelle für das- `CAxWindow` Objekt fest.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parameter

*puihandler*<br/>
in Ein Zeiger auf eine- `IDocHostUIHandlerDispatch` Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die externe `IDocHostUIHandlerDispatch` Schnittstelle wird von Steuerelementen verwendet, die die Host Website nach der- `IDocHostUIHandlerDispatch` Schnittstelle Abfragen. Das WebBrowser-Steuerelement ist ein Steuerelement, das dies bewirkt.

## <a name="see-also"></a>Weitere Informationen

[ATLCON-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[CWindow-Klasse](../../atl/reference/cwindow-class.md)<br/>
[Grundlagen von zusammengesetzten Steuerelementen](../../atl/atl-composite-control-fundamentals.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Fragen und Antworten zur Steuerelementkapselung](../../atl/atl-control-containment-faq.md)
