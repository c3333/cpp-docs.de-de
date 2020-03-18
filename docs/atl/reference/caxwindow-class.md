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
ms.openlocfilehash: 6f5c178090a970906209e41da9298be61a61c639
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423387"
---
# <a name="caxwindow-class"></a>CAxWindow-Klasse

Diese Klasse stellt Methoden zum Bearbeiten eines Fensters bereit, das ein ActiveX-Steuerelement gehostet.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[AttachControl](#attachcontrol)|Fügt ein vorhandenes ActiveX-Steuerelement an das `CAxWindow` Objekt an.|
|[CAxWindow](#caxwindow)|Erstellt ein `CAxWindow`-Objekt.|
|[CreateControl](#createcontrol)|Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im `CAxWindow` Fenster.|
|["Kreatecontrolex"](#createcontrolex)|Erstellt ein ActiveX-Steuerelement und Ruft einen Schnittstellen Zeiger (oder Zeiger) aus dem-Steuerelement ab.|
|[Getwndclassname](#getwndclassname)|Kum Ruft den vordefinierten Klassennamen des `CAxWindow` Objekts ab.|
|[Querycontrol](#querycontrol)|Ruft den `IUnknown` des gehosteten ActiveX-Steuer Elements ab.|
|[QueryHost](#queryhost)|Ruft den `IUnknown` Zeiger des `CAxWindow` Objekts ab.|
|["Abtexternaldispatch"](#setexternaldispatch)|Legt die von der `CAxWindow` Objekt verwendete externe Dispatchschnittstelle fest.|
|["Abtexternaluihandler"](#setexternaluihandler)|Legt die externe `IDocHostUIHandler` Schnittstelle fest, die vom `CAxWindow`-Objekt verwendet wird.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#operator_eq)|Weist einem vorhandenen `CAxWindow`-Objekt ein HWND zu.|

## <a name="remarks"></a>Hinweise

Diese Klasse stellt Methoden zum Bearbeiten eines Fensters bereit, das ein ActiveX-Steuerelement hostet. Das Hosting wird von " **AtlAxWin80"** bereitgestellt, das von `CAxWindow`umschließt wird.

Class `CAxWindow` wird als Spezialisierung der `CAxWindowT`-Klasse implementiert. Diese Spezialisierung wird wie folgt deklariert:

`typedef CAxWindowT<CWindow> CAxWindow;`

Wenn Sie die Basisklasse ändern müssen, können Sie `CAxWindowT` verwenden und die neue Basisklasse als Vorlagen Argument angeben.

## <a name="requirements"></a>Voraussetzungen

**Header:** atlwin. h

##  <a name="attachcontrol"></a>CAxWindow:: AttachControl

Erstellt ein neues Host Objekt, wenn es noch nicht vorhanden ist, und fügt das angegebene Steuerelement an den Host an.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parameter

*pcontrol*<br/>
in Ein Zeiger auf den `IUnknown` des-Steuer Elements.

*ppunkcontainer*<br/>
vorgenommen Ein Zeiger auf den `IUnknown` des Hosts (das `AxWin` Objekt).

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Das anzufügende Steuerelement Objekt muss vor dem Aufrufen von `AttachControl`ordnungsgemäß initialisiert werden.

##  <a name="caxwindow"></a>CAxWindow:: CAxWindow

Erstellt ein `CAxWindow`-Objekt mit einem vorhandenen Fenster Objekt handle.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle für ein vorhandenes Fenster Objekt.

##  <a name="createcontrol"></a>CAxWindow:: kreatecontrol

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

- Eine ProgID wie `"MSCAL.Calendar.7"`

- Eine CLSID, z. b. `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie `"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. b. `"file://\\\Documents\MyDoc.doc"`

- Ein HTML-Fragment, z. b. `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` muss dem HTML-Fragment vorangestellt sein, damit es als MSHTML-Stream festgelegt ist. Nur die ProgID und CLSID werden auf Windows Mobile-Plattformen unterstützt. Windows CE Embedded-Plattformen (außer Windows Mobile) mit Unterstützung für CE IE unterstützen alle Typen, einschließlich ProgID, CLSID, URL, Verweis auf aktives Dokument und HTML-Fragmente.

*pStream*<br/>
in Ein Zeiger auf einen Stream, der verwendet wird, um die Eigenschaften des Steuer Elements zu initialisieren. Kann NULL sein.

*ppunkcontainer*<br/>
vorgenommen Die Adresse eines Zeigers, der die `IUnknown` des Containers empfängt. Kann NULL sein.

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

Ein Beispiel für die Verwendung von `CreateControl`finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="createcontrolex"></a>CAxWindow:: kreatecontrolex

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

- Eine ProgID wie `"MSCAL.Calendar.7"`

- Eine CLSID, z. b. `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie `"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. b. `"file://\\\Documents\MyDoc.doc"`

- Ein HTML-Fragment, z. b. `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` muss dem HTML-Fragment vorangestellt sein, damit es als MSHTML-Stream festgelegt ist. Nur die ProgID und CLSID werden auf Windows Mobile-Plattformen unterstützt. Windows CE Embedded-Plattformen (außer Windows Mobile) mit Unterstützung für CE IE unterstützen alle Typen, einschließlich ProgID, CLSID, URL, Verweis auf aktives Dokument und HTML-Fragmente.

*pStream*<br/>
in Ein Zeiger auf einen Stream, der verwendet wird, um die Eigenschaften des Steuer Elements zu initialisieren. Kann NULL sein.

*ppunkcontainer*<br/>
vorgenommen Die Adresse eines Zeigers, der die `IUnknown` des Containers empfängt. Kann NULL sein.

*ppunkcontrol*<br/>
vorgenommen Die Adresse eines Zeigers, der die `IUnknown` des Steuer Elements empfängt. Kann NULL sein.

*iidsink*<br/>
in Der Schnittstellen Bezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt. Kann IID_NULL werden.

*punksink*<br/>
in Ein Zeiger auf die `IUnknown`-Schnittstelle des Sink-Objekts, das mit dem Verbindungspunkt für das von *iidsink*angegebene enthaltene Objekt verbunden werden soll.

*dwresid*<br/>
in Die Ressourcen-ID einer HTML-Ressource. Das WebBrowser-Steuerelement wird erstellt und mit der angegebenen Ressource geladen.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Diese Methode ähnelt [CAxWindow:: anatecontrol](#createcontrol), aber im Gegensatz zu dieser Methode können `CreateControlEx` auch einen Schnittstellen Zeiger auf das neu erstellte Steuerelement empfangen und eine Ereignis Senke für den Empfang von Ereignissen einrichten, die vom Steuerelement ausgelöst werden.

Weitere Informationen finden Sie unter [CAxWindow2T:: anatecontrollicex](../../atl/reference/caxwindow2t-class.md#createcontrollicex) zum Erstellen, initialisieren und Hosten eines lizenzierten ActiveX-Steuer Elements.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `CreateControlEx`finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="getwndclassname"></a>CAxWindow:: getwndclassname

Ruft den Namen der Fenster Klasse ab.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Zeichenfolge, die den Namen der Fenster Klasse enthält, die nicht lizenzierte ActiveX-Steuerelemente hosten kann.

##  <a name="operator_eq"></a>CAxWindow:: Operator =

Weist einem vorhandenen `CAxWindow`-Objekt ein HWND zu.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle für ein vorhandenes Fenster.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das aktuelle `CAxWindow`-Objekt zurück.

##  <a name="querycontrol"></a>CAxWindow:: querycontrol

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

*Q*<br/>
in Die Schnittstelle, für die abgefragt wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

##  <a name="queryhost"></a>CAxWindow:: QueryHost

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

*Q*<br/>
in Die Schnittstelle, für die abgefragt wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die-Schnittstelle des Hosts ermöglicht den Zugriff auf die zugrunde liegende Funktionalität des Fenster-hostingcodes, der von `AxWin`implementiert wird.

##  <a name="setexternaldispatch"></a>CAxWindow:: abtexternaldispatch

Legt die externe Dispatchschnittstelle für das `CAxWindow` Objekt fest.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
in Ein Zeiger auf eine `IDispatch`-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

##  <a name="setexternaluihandler"></a>CAxWindow:: abtexternaluihandler

Legt die externe [idochostuihandlerdispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) -Schnittstelle für das `CAxWindow` Objekt fest.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parameter

*puihandler*<br/>
in Ein Zeiger auf eine `IDocHostUIHandlerDispatch`-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die externe `IDocHostUIHandlerDispatch`-Schnittstelle wird von Steuerelementen verwendet, die die Host Website nach der `IDocHostUIHandlerDispatch`-Schnittstelle Abfragen. Das WebBrowser-Steuerelement ist ein Steuerelement, das dies bewirkt.

## <a name="see-also"></a>Siehe auch

[ATLCON-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[CWindow-Klasse](../../atl/reference/cwindow-class.md)<br/>
[Grundlagen von zusammengesetzten Steuerelementen](../../atl/atl-composite-control-fundamentals.md)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)<br/>
[FAQ zu den Steuerungsmöglichkeiten](../../atl/atl-control-containment-faq.md)
