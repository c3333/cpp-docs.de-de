---
title: CDHtmlDialog-Klasse
ms.date: 03/27/2019
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: 9cc01c94357d7aac7fa6fa98127628a60746e1e8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842883"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog-Klasse

Wird verwendet, um Dialogfelder zu erstellen, die anstelle von Dialogfeldern HTML verwenden, um Ihre Benutzeroberfläche zu implementieren.

## <a name="syntax"></a>Syntax

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CDHtmlDialog:: CDHtmlDialog](#cdhtmldialog)|Erstellt ein CDHtmlDialog-Objekt.|
|[CDHtmlDialog:: ~ CDHtmlDialog](#_dtorcdhtmldialog)|Zerstört ein CDHtmlDialog-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CDHtmlDialog:: canaccessexternal](#canaccessexternal)|Über schreibbar, die als Zugriffs Überprüfung aufgerufen wird, um zu überprüfen, ob Skript Objekte auf der geladenen Seite auf den externen Dispatch der Steuerungs Website zugreifen können. Prüft, ob die Verteilung entweder sicher für die Skripterstellung ist oder die aktuelle Zone Objekte zulässt, die für die Skripterstellung nicht sicher sind.|
|[CDHtmlDialog:: "kreatecontrolsite"](#createcontrolsite)|Über schreibbar verwendet, um eine Steuerelement-Website Instanz zum Hosten des Webbrowser-Steuer Elements im Dialogfeld zu erstellen.|
|[CDHtmlDialog::D DX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Tauscht Daten zwischen einer Element Variablen und dem Eigenschafts Wert eines ActiveX-Steuer Elements auf einer HTML-Seite aus.|
|[CDHtmlDialog::D DX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Tauscht Daten zwischen einer Element Variablen und einem Kontrollkästchen auf einer HTML-Seite aus.|
|[CDHtmlDialog::D DX_DHtml_ElementText](#ddx_dhtml_elementtext)|Tauscht Daten zwischen einer Element Variablen und einer beliebigen HTML-Element Eigenschaft auf einer HTML-Seite aus.|
|[CDHtmlDialog::D DX_DHtml_Radio](#ddx_dhtml_radio)|Tauscht Daten zwischen einer Element Variablen und einem Optionsfeld auf einer HTML-Seite aus.|
|[CDHtmlDialog::D DX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Ruft den Index eines Listen Felds auf einer HTML-Seite ab oder legt diesen fest.|
|[CDHtmlDialog::D DX_DHtml_SelectString](#ddx_dhtml_selectstring)|Ruft den Anzeige Text eines Listenfeld Eintrags (basierend auf dem aktuellen Index) auf einer HTML-Seite ab oder legt diesen fest.|
|[CDHtmlDialog::D DX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Ruft den Wert eines Listenfeld Eintrags (basierend auf dem aktuellen Index) auf einer HTML-Seite ab oder legt diesen fest.|
|[CDHtmlDialog::D estroymodeless](#destroymodeless)|Zerstört ein nicht modalem Dialogfeld.|
|[CDHtmlDialog:: enablemodeless](#enablemodeless)|Aktiviert Dialogfelder ohne Modus.|
|[CDHtmlDialog:: filterdataobject](#filterdataobject)|Ermöglicht dem Dialog zum Filtern von Zwischenablage Datenobjekten, die vom gehosteten Browser erstellt wurden.|
|[CDHtmlDialog:: getcontroldispatch](#getcontroldispatch)|Ruft die- `IDispatch` Schnittstelle auf einem ActiveX-Steuerelement ab, das im HTML-Dokument eingebettet ist|
|[CDHtmlDialog:: getcontrolproperty](#getcontrolproperty)|Ruft die angeforderte Eigenschaft des angegebenen ActiveX-Steuer Elements ab.|
|[CDHtmlDialog:: getcurrenturl](#getcurrenturl)|Ruft den Uniform Resource Locator (URL) ab, der dem aktuellen Dokument zugeordnet ist.|
|[CDHtmlDialog:: getdhtmldocument](#getdhtmldocument)|Ruft die IHTMLDocument2-Schnittstelle für das derzeit geladene HTML-Dokument ab.|
|[CDHtmlDialog:: getdroptarget](#getdroptarget)|Wird von dem enthaltenen Webbrowser-Steuerelement aufgerufen, wenn es als Ablage Ziel verwendet wird, damit das Dialogfeld eine Alternative [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)-Schnittstelle bereitstellen kann.|
|[CDHtmlDialog:: getElements](#getelement)|Ruft eine-Schnittstelle für ein HTML-Element ab.|
|[CDHtmlDialog:: getelementhtml](#getelementhtml)|Ruft die- `innerHTML` Eigenschaft eines HTML-Elements ab.|
|[CDHtmlDialog:: getelementinterface](#getelementinterface)|Ruft den angeforderten Schnittstellen Zeiger aus einem HTML--Element ab.|
|[CDHtmlDialog:: getelementproperty](#getelementproperty)|Ruft den Wert der-Eigenschaft eines HTML-Elements ab.|
|[CDHtmlDialog:: getelementtext](#getelementtext)|Ruft die- `innerText` Eigenschaft eines HTML-Elements ab.|
|[CDHtmlDialog:: GetEvent](#getevent)|Ruft den `IHTMLEventObj` Zeiger auf das aktuelle Ereignis Objekt ab.|
|[CDHtmlDialog:: getexternal](#getexternal)|Ruft die-Schnittstelle des Hosts ab `IDispatch` .|
|[CDHtmlDialog:: gethostinfo](#gethostinfo)|Ruft die Benutzeroberflächen Funktionen des Hosts ab.|
|[CDHtmlDialog:: getoptionkeypath](#getoptionkeypath)|Ruft den Registrierungsschlüssel ab, unter dem die Benutzereinstellungen gespeichert werden.|
|[CDHtmlDialog:: HideUI](#hideui)|Blendet die Benutzeroberfläche des Hosts aus.|
|[CDHtmlDialog:: isexternaldispatchsafe](#isexternaldispatchsafe)|Gibt an, ob die `IDispatch` Schnittstelle des Hosts für die Skripterstellung sicher ist.|
|[CDHtmlDialog:: loadfromresource](#loadfromresource)|Lädt die angegebene Ressource in das WebBrowser-Steuerelement.|
|[CDHtmlDialog:: Navigate](#navigate)|Navigiert zur angegebenen URL.|
|[CDHtmlDialog:: onbeforenavigate](#onbeforenavigate)|Wird von Framework aufgerufen, bevor ein Navigations Ereignis ausgelöst wird.|
|[CDHtmlDialog:: OnDocumentComplete](#ondocumentcomplete)|Wird von Framework aufgerufen, um eine Anwendung zu benachrichtigen, wenn ein Dokument den READYSTATE_COMPLETE Zustand erreicht hat.|
|[CDHtmlDialog:: ondocwindowaktivierungs](#ondocwindowactivate)|Wird von Framework aufgerufen, wenn das Dokument Fenster aktiviert oder deaktiviert wird.|
|[CDHtmlDialog:: onframewindowaktivierungs](#onframewindowactivate)|Wird von Framework aufgerufen, wenn das Rahmen Fenster aktiviert oder deaktiviert wird.|
|[CDHtmlDialog:: OnInitDialog](#oninitdialog)|Wird als Antwort auf die WM_INITDIALOG Nachricht aufgerufen.|
|[CDHtmlDialog:: onnavigatecomplete](#onnavigatecomplete)|Wird von Framework aufgerufen, nachdem ein Navigations Ereignis abgeschlossen wurde.|
|[CDHtmlDialog:: resizeborder](#resizeborder)|Benachrichtigt das-Objekt, dass es die Größe seines Rahmen Raums ändern muss.|
|[CDHtmlDialog:: setcontrolproperty](#setcontrolproperty)|Legt die-Eigenschaft eines ActiveX-Steuer Elements auf einen neuen Wert fest.|
|[CDHtmlDialog:: ctelementhtml](#setelementhtml)|Legt die- `innerHTML` Eigenschaft eines HTML-Elements fest.|
|[CDHtmlDialog:: ab.](#setelementproperty)|Legt eine Eigenschaft eines HTML-Elements fest.|
|[CDHtmlDialog:: abtextzeile](#setelementtext)|Legt die- `innerText` Eigenschaft eines HTML-Elements fest.|
|[CDHtmlDialog:: abtexternaldispatch](#setexternaldispatch)|Legt die-Schnittstelle des Hosts fest `IDispatch` .|
|[CDHtmlDialog:: lthostflags](#sethostflags)|Legt die Benutzeroberflächen-Flags des Hosts fest.|
|[CDHtmlDialog:: ShowContextMenu](#showcontextmenu)|Wird aufgerufen, wenn ein Kontextmenü angezeigt wird.|
|[CDHtmlDialog:: showUI](#showui)|Zeigt die Benutzeroberfläche des Hosts an.|
|[CDHtmlDialog:: TranslateAccelerator](#translateaccelerator)|Wird aufgerufen, um Menü Zugriffstasten-Meldungen zu verarbeiten.|
|[CDHtmlDialog:: translateurl](#translateurl)|Wird aufgerufen, um die zu ladende URL zu ändern.|
|[CDHtmlDialog:: UpdateUI](#updateui)|Wird aufgerufen, um den Host zu benachrichtigen, dass sich der Befehlsstatus geändert hat.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CDHtmlDialog:: m_bUseHtmlTitle](#m_busehtmltitle)|Gibt an, ob der Titel des HTML-Dokuments als Dialog Beschriftung verwendet werden soll.|
|[CDHtmlDialog:: m_nHtmlResID](#m_nhtmlresid)|Die Ressourcen-ID der HTML-Ressource, die angezeigt werden soll.|
|[CDHtmlDialog:: m_pBrowserApp](#m_pbrowserapp)|Ein Zeiger auf eine Webbrowser Anwendung.|
|[CDHtmlDialog:: m_spHtmlDoc](#m_sphtmldoc)|Ein Zeiger auf ein HTML-Dokument.|
|[CDHtmlDialog:: m_strCurrentUrl](#m_strcurrenturl)|Die aktuelle URL.|
|[CDHtmlDialog:: m_szHtmlResID](#m_szhtmlresid)|Zeichen folgen Version der HTML-Ressourcen-ID.|

## <a name="remarks"></a>Bemerkungen

`CDHtmlDialog` kann den HTML-Code laden, der entweder von einer HTML-Ressource oder einer URL angezeigt wird.

`CDHtmlDialog` kann auch einen Datenaustausch mit HTML-Steuerelementen ausführen und Ereignisse von HTML-Steuerelementen wie Schaltflächen Klicks verarbeiten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdhtml. h

## <a name="ddx_dhtml-helper-macros"></a><a name="ddx_dhtml_helper_macros"></a> DDX_DHtml Hilfsobjekte

Die DDX_DHtml-Hilfsobjekte ermöglichen den einfachen Zugriff auf die häufig verwendeten Eigenschaften von Steuerelementen auf einer HTML-Seite.

### <a name="data-exchange-macros"></a>Datenaustausch Makros

|Name|Beschreibung|
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Legt die Value-Eigenschaft des ausgewählten Steuer Elements fest oder ruft Sie ab.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Legt den Text zwischen den Start-und Endtags des aktuellen Elements fest oder ruft diesen ab.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Legt den HTML-Code zwischen den Start-und Endtags des aktuellen Elements fest oder ruft diesen ab.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Legt die Ziel-URL oder den Ankerpunkt fest oder ruft Sie ab.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Legt das Zielfenster oder den Zielrahmen fest oder ruft es ab.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Legt den Namen eines Bilds oder eines Videoclips im Dokument fest oder ruft ihn ab.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Legt die URL des zugeordneten Frames fest oder ruft Sie ab.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Legt die URL des zugeordneten Frames fest oder ruft Sie ab.|

## <a name="cdhtmldialogcanaccessexternal"></a><a name="canaccessexternal"></a> CDHtmlDialog:: canaccessexternal

Über schreibbar, die als Zugriffs Überprüfung aufgerufen wird, um zu überprüfen, ob Skript Objekte auf der geladenen Seite auf den externen Dispatch der Steuerungs Website zugreifen können. Prüft, ob die Verteilung entweder sicher für die Skripterstellung ist oder die aktuelle Zone Objekte zulässt, die für die Skripterstellung nicht sicher sind.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="cdhtmldialogcdhtmldialog"></a><a name="cdhtmldialog"></a> CDHtmlDialog:: CDHtmlDialog

Erstellt ein Ressourcen basiertes Dynamic HTML Dialogfeld.

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*lpsztemplatename*<br/>
Die auf NULL endenden Zeichenfolge, die der Name einer Dialogfeld Vorlagen Ressource ist.

*szhtmlresid*<br/>
Die NULL-terminierte Zeichenfolge, die den Namen einer HTML-Ressource ist.

*pparser*<br/>
Ein Zeiger auf das übergeordnete oder Besitzer Fenster Objekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialog Objekt gehört. Wenn der Wert NULL ist, wird das übergeordnete Fenster des Dialog Objekts auf das Hauptanwendungsfenster festgelegt.

*nidtemplate*<br/>
Enthält die ID-Nummer einer Dialogfeld Vorlagen-Ressource.

*nhtmlresid*<br/>
Enthält die ID-Nummer einer HTML-Ressource.

### <a name="remarks"></a>Bemerkungen

Die zweite Form des Konstruktors ermöglicht den Zugriff auf die Dialog Ressource über den Vorlagen Namen. Die dritte Form des Konstruktors ermöglicht den Zugriff auf die Dialog Ressource über die ID der Ressourcen Vorlage. Normalerweise beginnt die ID mit dem **IDD_** -Präfix.

## <a name="cdhtmldialogcdhtmldialog"></a><a name="_dtorcdhtmldialog"></a> CDHtmlDialog:: ~ CDHtmlDialog

Zerstört ein CDHtmlDialog-Objekt.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Bemerkungen

Die [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow) -Member-Funktion muss verwendet werden, um die von [CDialog:: Create](../../mfc/reference/cdialog-class.md#create)erstellten nicht modalem Dialogfelder zu zerstören.

## <a name="cdhtmldialogcreatecontrolsite"></a><a name="createcontrolsite"></a> CDHtmlDialog:: "kreatecontrolsite"

Über schreibbar verwendet, um eine Steuerelement-Website Instanz zum Hosten des Webbrowser-Steuer Elements im Dialogfeld zu erstellen.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parameter

*pContainer*<br/>
Ein Zeiger auf das [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md) -Objekt.

*ppsite*<br/>
Ein Zeiger auf einen Zeiger auf eine [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie können diese Member-Funktion überschreiben, um eine Instanz Ihrer eigenen Steuerelement-Website Klasse zurückzugeben.

## <a name="cdhtmldialogddx_dhtml_axcontrol"></a><a name="ddx_dhtml_axcontrol"></a> CDHtmlDialog::D DX_DHtml_AxControl

Tauscht Daten zwischen einer Element Variablen und dem Eigenschafts Wert eines ActiveX-Steuer Elements auf einer HTML-Seite aus.

```cpp
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*szid*<br/>
Der Wert des ID-Parameters des Objekttags in der HTML-Quelle für das ActiveX-Steuerelement.

*dispId*<br/>
Die Dispatch-ID der Eigenschaft, mit der Daten ausgetauscht werden sollen.

*szpropname*<br/>
Den Namen der Eigenschaft.

*var*<br/>
Der Datenmember des Typs Variant, [COleVariant](../../mfc/reference/colevariant-class.md)oder [CComVariant](../../atl/reference/ccomvariant-class.md), der den mit der ActiveX-Steuerelement Eigenschaft ausgetauschten Wert enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

## <a name="cdhtmldialogddx_dhtml_checkbox"></a><a name="ddx_dhtml_checkbox"></a> CDHtmlDialog::D DX_DHtml_CheckBox

Tauscht Daten zwischen einer Element Variablen und einem Kontrollkästchen auf einer HTML-Seite aus.

```cpp
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*szid*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*value*<br/>
Der ausgetauschte Wert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

## <a name="cdhtmldialogddx_dhtml_elementtext"></a><a name="ddx_dhtml_elementtext"></a> CDHtmlDialog::D DX_DHtml_ElementText

Tauscht Daten zwischen einer Element Variablen und einer beliebigen HTML-Element Eigenschaft auf einer HTML-Seite aus.

```cpp
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*szid*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*dispId*<br/>
Die Dispatch-ID des HTML-Elements, mit dem Daten ausgetauscht werden sollen.

*value*<br/>
Der ausgetauschte Wert.

## <a name="cdhtmldialogddx_dhtml_radio"></a><a name="ddx_dhtml_radio"></a> CDHtmlDialog::D DX_DHtml_Radio

Tauscht Daten zwischen einer Element Variablen und einem Optionsfeld auf einer HTML-Seite aus.

```cpp
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*szid*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*value*<br/>
Der ausgetauschte Wert.

## <a name="cdhtmldialogddx_dhtml_selectindex"></a><a name="ddx_dhtml_selectindex"></a> CDHtmlDialog::D DX_DHtml_SelectIndex

Ruft den Index eines Listen Felds auf einer HTML-Seite ab oder legt diesen fest.

```cpp
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*szid*<br/>
Der Wert, den Sie für den-Parameter des HTML-Steuer Elements angegeben haben `id` .

*value*<br/>
Der ausgetauschte Wert.

## <a name="cdhtmldialogddx_dhtml_selectstring"></a><a name="ddx_dhtml_selectstring"></a> CDHtmlDialog::D DX_DHtml_SelectString

Ruft den Anzeige Text eines Listenfeld Eintrags (basierend auf dem aktuellen Index) auf einer HTML-Seite ab oder legt diesen fest.

```cpp
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*szid*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*value*<br/>
Der ausgetauschte Wert.

## <a name="cdhtmldialogddx_dhtml_selectvalue"></a><a name="ddx_dhtml_selectvalue"></a> CDHtmlDialog::D DX_DHtml_SelectValue

Ruft den Wert eines Listenfeld Eintrags (basierend auf dem aktuellen Index) auf einer HTML-Seite ab oder legt diesen fest.

```cpp
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*szid*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*value*<br/>
Der ausgetauschte Wert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

## <a name="cdhtmldialogdestroymodeless"></a><a name="destroymodeless"></a> CDHtmlDialog::D estroymodeless

Trennt ein nicht modalem Dialogfeld von dem `CDHtmlDialog` -Objekt und zerstört das-Objekt.

```cpp
void DestroyModeless();
```

## <a name="cdhtmldialogenablemodeless"></a><a name="enablemodeless"></a> CDHtmlDialog:: enablemodeless

Aktiviert Dialogfelder ohne Modus.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parameter

*fenckbar*<br/>
Weitere Informationen finden Sie unter " *fEnable* " in " [IDocHostUIHandler:: enablemodeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) " in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: enablemodeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialogfilterdataobject"></a><a name="filterdataobject"></a> CDHtmlDialog:: filterdataobject

Ermöglicht dem Dialog zum Filtern von Zwischenablage Datenobjekten, die vom gehosteten Browser erstellt wurden.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parameter

*ausgelöst*<br/>
Siehe *pDO* in [IDocHostUIHandler:: filterdataobject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) in der Windows SDK.

*ppdoret*<br/>
Siehe *ppdoret* in `IDocHostUIHandler::FilterDataObject` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: filterdataobject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialoggetcontroldispatch"></a><a name="getcontroldispatch"></a> CDHtmlDialog:: getcontroldispatch

Ruft die `IDispatch` Schnittstelle für ein ActiveX-Steuerelement ab, das in das von [getdhtmldocument](#getdhtmldocument)zurückgegebene HTML-Dokument eingebettet ist.

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parameter

*szid*<br/>
Die HTML-ID eines ActiveX-Steuer Elements.

*ppdisp*<br/>
Die- `IDispatch` Schnittstelle des Steuer Elements, wenn Sie auf der Webseite gefunden wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="cdhtmldialoggetcontrolproperty"></a><a name="getcontrolproperty"></a> CDHtmlDialog:: getcontrolproperty

Ruft die angeforderte Eigenschaft des angegebenen ActiveX-Steuer Elements ab.

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>Parameter

*szid*<br/>
Die HTML-ID eines ActiveX-Steuer Elements.

*szpropname*<br/>
Der Name einer Eigenschaft im Standard Gebiets Schema des aktuellen Benutzers.

*pdispcontrol*<br/>
Der `IDispatch` Zeiger eines ActiveX-Steuer Elements.

*dispId*<br/>
Die Dispatch-ID einer Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Eine Variante, die die angeforderte Eigenschaft oder eine leere Variante enthält, wenn das Steuerelement oder die Eigenschaft nicht gefunden werden konnte.

### <a name="remarks"></a>Bemerkungen

Die über Ladungen sind unten im unteren Bereich der effizientesten aufgeführt.

## <a name="cdhtmldialoggetcurrenturl"></a><a name="getcurrenturl"></a> CDHtmlDialog:: getcurrenturl

Ruft den Uniform Resource Locator (URL) ab, der dem aktuellen Dokument zugeordnet ist.

```cpp
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parameter

*szURL*<br/>
Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt, das die abzurufende URL enthält.

## <a name="cdhtmldialoggetdhtmldocument"></a><a name="getdhtmldocument"></a> CDHtmlDialog:: getdhtmldocument

Ruft die [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) -Schnittstelle für das derzeit geladene HTML-Dokument ab.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parameter

* \* \* pphtmldoc* ein Zeiger auf einen Zeiger auf ein HTML-Dokument.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard. Gibt S_OK zurück, wenn erfolgreich.

## <a name="cdhtmldialoggetdroptarget"></a><a name="getdroptarget"></a> CDHtmlDialog:: getdroptarget

Wird von dem enthaltenen Webbrowser-Steuerelement aufgerufen, wenn es als Ablage Ziel verwendet wird, damit das Dialogfeld eine Alternative [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)-Schnittstelle bereitstellen kann.

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parameter

*pdroptarget*<br/>
Siehe *pdroptarget* in [IDocHostUIHandler:: getdroptarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) in der Windows SDK.

*ppdroptarget*<br/>
Weitere Informationen finden Sie in der Windows SDK unter *ppdroptarget* `IDocHostUIHandler::GetDropTarget` .

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: getdroptarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialoggetelement"></a><a name="getelement"></a> CDHtmlDialog:: getElements

Gibt eine Schnittstelle für das von *szelementid*angegebene HTML-Element zurück.

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>Parameter

*szelementid*<br/>
Die ID eines HTML-Elements.

*ppdisp*<br/>
Ein `IDispatch` Zeiger auf das angeforderte Element oder die Auflistung von Elementen.

*pbcollection*<br/>
Ein boolescher Wert, der angibt, ob das durch *ppdisp* dargestellte Objekt ein einzelnes Element oder eine Auflistung von Elementen ist.

*pphtmlelement*<br/>
Ein `IHTMLElement` Zeiger auf das angeforderte Element.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die erste Überladung, wenn Sie Bedingungen behandeln müssen, bei denen möglicherweise mehr als ein Element mit der angegebenen ID vorhanden ist. Mit dem letzten Parameter können Sie feststellen, ob der zurückgegebene Schnittstellen Zeiger auf eine Auflistung oder ein einzelnes Element festgelegt ist. Wenn sich der Schnittstellen Zeiger auf eine Auflistung bezieht, können Sie die Abfragen `IHTMLElementCollection` und die-Eigenschaft verwenden, um `item` auf die Elemente anhand der Ordinalposition zu verweisen.

Die zweite Überladung schlägt fehl, wenn mehr als ein Element mit derselben ID auf der Seite vorhanden ist.

## <a name="cdhtmldialoggetelementhtml"></a><a name="getelementhtml"></a> CDHtmlDialog:: getelementhtml

Ruft die- `innerHTML` Eigenschaft des HTML-Elements ab, das von *szelementid*identifiziert wird.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parameter

*szelementid*<br/>
Die ID eines HTML-Elements.

### <a name="return-value"></a>Rückgabewert

Die- `innerHTML` Eigenschaft des HTML-Elements, das von *szelementid* identifiziert wird, oder NULL, wenn das Element nicht gefunden wurde.

## <a name="cdhtmldialoggetelementinterface"></a><a name="getelementinterface"></a> CDHtmlDialog:: getelementinterface

Ruft den angeforderten Schnittstellen Zeiger aus dem HTML-Element ab, das von *szelementid*identifiziert wird.

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>Parameter

*szelementid*<br/>
Die ID eines HTML-Elements.

*ppvObj*<br/>
Adresse eines Zeigers, der mit dem angeforderten Schnittstellen Zeiger gefüllt wird, wenn das Element gefunden wird und die Abfrage erfolgreich ist.

*REFIID*<br/>
Die Schnittstellen-ID (IID) der angeforderten Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

## <a name="cdhtmldialoggetelementproperty"></a><a name="getelementproperty"></a> CDHtmlDialog:: getelementproperty

Ruft den Wert der durch *DISPID* identifizierten Eigenschaft aus dem durch *szelementid*identifizierten HTML-Element ab.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Parameter

*szelementid*<br/>
Die ID eines HTML-Elements.

*dispId*<br/>
Die Dispatch-ID einer Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Der Wert der Eigenschaft oder eine leere Variante, wenn die Eigenschaft oder das Element nicht gefunden werden konnte.

## <a name="cdhtmldialoggetelementtext"></a><a name="getelementtext"></a> CDHtmlDialog:: getelementtext

Ruft die- `innerText` Eigenschaft des HTML-Elements ab, das von *szelementid*identifiziert wird.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parameter

*szelementid*<br/>
Die ID eines HTML-Elements.

### <a name="return-value"></a>Rückgabewert

Die- `innerText` Eigenschaft des HTML-Elements, das von *szelementid* identifiziert wird, oder NULL, wenn die Eigenschaft oder das Element nicht gefunden wurde.

## <a name="cdhtmldialoggetevent"></a><a name="getevent"></a> CDHtmlDialog:: GetEvent

Gibt den `IHTMLEventObj` Zeiger auf das aktuelle Ereignis Objekt zurück.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parameter

*ppeer-obj*<br/>
Adresse eines Zeigers, der mit dem `IHTMLEventObj` Schnittstellen Zeiger gefüllt wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte nur innerhalb eines DHTML-Ereignis Handlers aufgerufen werden.

## <a name="cdhtmldialoggetexternal"></a><a name="getexternal"></a> CDHtmlDialog:: getexternal

Ruft die-Schnittstelle des Hosts ab `IDispatch` .

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parameter

*ppdispatch*<br/>
Weitere Informationen finden Sie unter *ppdispatch* in [IDocHostUIHandler:: getexternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder E_NOTIMPL bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: getexternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialoggethostinfo"></a><a name="gethostinfo"></a> CDHtmlDialog:: gethostinfo

Ruft die Benutzeroberflächen Funktionen des Hosts ab.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parameter

*pinfo*<br/>
Siehe *pinfo* in [IDocHostUIHandler:: gethostinfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: gethostinfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialoggetoptionkeypath"></a><a name="getoptionkeypath"></a> CDHtmlDialog:: getoptionkeypath

Ruft den Registrierungsschlüssel ab, unter dem die Benutzereinstellungen gespeichert werden.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parameter

*pchkey*<br/>
Weitere Informationen finden Sie unter " *pchkey* " in " [IDocHostUIHandler:: getoptionkeypath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) " in der Windows SDK.

*dw*<br/>
Weitere Informationen finden Sie unter *DW* in `IDocHostUIHandler::GetOptionKeyPath` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: getoptionkeypath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialoghideui"></a><a name="hideui"></a> CDHtmlDialog:: HideUI

Blendet die Benutzeroberfläche des Hosts aus.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialogisexternaldispatchsafe"></a><a name="isexternaldispatchsafe"></a> CDHtmlDialog:: isexternaldispatchsafe

Gibt an, ob die `IDispatch` Schnittstelle des Hosts für die Skripterstellung sicher ist.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Rückgabewert

Gibt false zurück.

## <a name="cdhtmldialogloadfromresource"></a><a name="loadfromresource"></a> CDHtmlDialog:: loadfromresource

Lädt die angegebene Ressource in das WebBrowser-Steuerelement im DHTML-Dialogfeld.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Parameter

*lpszresource*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der zu ladenden Ressource enthält.

*NRES*<br/>
Die ID der zu ladenden Ressource

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

## <a name="cdhtmldialogm_busehtmltitle"></a><a name="m_busehtmltitle"></a> CDHtmlDialog:: m_bUseHtmlTitle

Gibt an, ob der Titel des HTML-Dokuments als Dialog Beschriftung verwendet werden soll.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Bemerkungen

Wenn **m**_ **busehtmltitle** den Wert true hat, wird die Beschriftung des Dialog Felds auf den Titel des HTML-Dokuments festgelegt. Andernfalls wird die Beschriftung in der Dialogfeld Ressource verwendet.

## <a name="cdhtmldialogm_nhtmlresid"></a><a name="m_nhtmlresid"></a> CDHtmlDialog:: m_nHtmlResID

Die Ressourcen-ID der HTML-Ressource, die angezeigt werden soll.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

## <a name="cdhtmldialogm_pbrowserapp"></a><a name="m_pbrowserapp"></a> CDHtmlDialog:: m_pBrowserApp

Ein Zeiger auf eine Webbrowser Anwendung.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

## <a name="cdhtmldialogm_sphtmldoc"></a><a name="m_sphtmldoc"></a> CDHtmlDialog:: m_spHtmlDoc

Ein Zeiger auf ein HTML-Dokument.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

## <a name="cdhtmldialogm_strcurrenturl"></a><a name="m_strcurrenturl"></a> CDHtmlDialog:: m_strCurrentUrl

Die aktuelle URL.

```
CString m_strCurrentUrl;
```

## <a name="cdhtmldialogm_szhtmlresid"></a><a name="m_szhtmlresid"></a> CDHtmlDialog:: m_szHtmlResID

Zeichen folgen Version der HTML-Ressourcen-ID.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

## <a name="cdhtmldialognavigate"></a><a name="navigate"></a> CDHtmlDialog:: Navigate

Navigiert zu der Ressource, die durch die URL identifiziert wird, die von *lpszurl*angegeben wird.

```cpp
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>Parameter

*lpszurl*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu zielende URL enthält.

*dwFlags*<br/>
Die Flags einer Variablen, die angibt, ob die Ressource der Verlaufs Liste hinzugefügt werden soll, ob in den Cache gelesen oder aus dem Cache geschrieben werden soll und ob die Ressource in einem neuen Fenster angezeigt werden soll. Bei der Variablen kann es sich um eine Kombination der Werte handeln, die von der [browsernavconstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) -Enumeration definiert werden.

*lpsztargetframename*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Frames enthält, in dem die Ressource angezeigt werden soll.

*lpszheaders*<br/>
Ein Zeiger auf einen-Wert, der die HTTP-Header angibt, die an den Server gesendet werden sollen. Diese Header werden den Internet Explorer-Standard Headern hinzugefügt. Die Header können solche Informationen wie die für den Server erforderliche Aktion, den Typ der an den Server übergebenen Daten oder einen Statuscode angeben. Dieser Parameter wird ignoriert, wenn es sich bei der URL nicht um eine HTTP-URL handelt.

*lpvpostdata*<br/>
Ein Zeiger auf die Daten, die mit der HTTP-Post-Transaktion gesendet werden sollen. Beispielsweise wird die Post-Transaktion zum Senden von Daten verwendet, die von einem HTML-Formular gesammelt werden. Wenn dieser Parameter keine Post-Daten angibt, `Navigate` gibt eine HTTP Get-Transaktion aus. Dieser Parameter wird ignoriert, wenn es sich bei der URL nicht um eine HTTP-URL handelt.

*dwpostdatalen*<br/>
Daten, die mit der HTTP-Post-Transaktion gesendet werden sollen. Beispielsweise wird die Post-Transaktion zum Senden von Daten verwendet, die von einem HTML-Formular gesammelt werden. Wenn dieser Parameter keine Post-Daten angibt, `Navigate` gibt eine HTTP Get-Transaktion aus. Dieser Parameter wird ignoriert, wenn URL keine http-URL ist.

## <a name="cdhtmldialogonbeforenavigate"></a><a name="onbeforenavigate"></a> CDHtmlDialog:: onbeforenavigate

Wird von Framework aufgerufen, um zu bewirken, dass ein Ereignis ausgelöst wird, bevor eine Navigation auftritt.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
Ein Zeiger auf ein `IDispatch` -Objekt.

*szURL*<br/>
Ein Zeiger auf eine Zeichenfolge mit der URL, zu der navigiert werden soll.

## <a name="cdhtmldialogondocumentcomplete"></a><a name="ondocumentcomplete"></a> CDHtmlDialog:: OnDocumentComplete

Wird von Framework aufgerufen, um eine Anwendung zu benachrichtigen, wenn ein Dokument den READYSTATE_COMPLETE Zustand erreicht hat.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
Ein Zeiger auf ein `IDispatch` -Objekt.

*szURL*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält, zu der navigiert wurde.

## <a name="cdhtmldialogondocwindowactivate"></a><a name="ondocwindowactivate"></a> CDHtmlDialog:: ondocwindowaktivierungs

Wird von Framework aufgerufen, wenn das Dokument Fenster aktiviert oder deaktiviert wird.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parameter

*faktivate*<br/>
Weitere Informationen finden Sie unter *faktivate* in [IDocHostUIHandler:: ondocwindowaktivierungs](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: ondocwindowaktivierung](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialogonframewindowactivate"></a><a name="onframewindowactivate"></a> CDHtmlDialog:: onframewindowaktivierungs

Wird von Framework aufgerufen, wenn das Rahmen Fenster aktiviert oder deaktiviert wird.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parameter

*faktivate*<br/>
Weitere Informationen finden Sie unter *faktivate* in [IDocHostUIHandler:: onframewindowaktivierungs](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: onframewindowaktivierungs](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialogoninitdialog"></a><a name="oninitdialog"></a> CDHtmlDialog:: OnInitDialog

Wird als Antwort auf die WM_INITDIALOG Nachricht aufgerufen.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt true zurück.

### <a name="remarks"></a>Bemerkungen

Diese Meldung wird während der Aufrufe, oder an das Dialogfeld gesendet `Create` `CreateIndirect` `DoModal` , die unmittelbar vor dem Anzeigen des Dialog Felds auftreten.

Überschreiben Sie diese Member-Funktion, wenn Sie beim Initialisieren des Dialog Felds eine spezielle Verarbeitung ausführen müssen. In der überschriebenen Version wird zuerst die Basisklasse aufgerufen, `OnInitDialog` aber der Rückgabewert wird ignoriert. Normalerweise wird von der überschriebenen Member-Funktion "true" zurückgegeben.

Die Funktion wird `OnInitDialog` von Windows über die standardmäßige globale Dialogfeld Prozedur aufgerufen, die für alle Microsoft Foundation Class-Bibliothek Dialogfelder und nicht über die Meldungs Zuordnung gilt. Daher benötigen Sie keinen Nachrichten Zuordnungs Eintrag für diese Element Funktion.

## <a name="cdhtmldialogonnavigatecomplete"></a><a name="onnavigatecomplete"></a> CDHtmlDialog:: onnavigatecomplete

Wird vom Framework aufgerufen, nachdem die Navigation zur angegebenen URL abgeschlossen wurde.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
Ein Zeiger auf ein `IDispatch` -Objekt.

*szURL*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält, zu der navigiert wurde.

## <a name="cdhtmldialogresizeborder"></a><a name="resizeborder"></a> CDHtmlDialog:: resizeborder

Benachrichtigt das-Objekt, dass es die Größe seines Rahmen Raums ändern muss.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parameter

*prcborder*<br/>
Siehe *prcborder* in [IDocHostUIHandler:: resizeborder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) in der Windows SDK.

*puiwindow*<br/>
Siehe *puiwindow* in `IDocHostUIHandler::ResizeBorder` im Windows SDK.

*fframewindow*<br/>
Siehe *fframewindow* in `IDocHostUIHandler::ResizeBorder` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

## <a name="cdhtmldialogsetcontrolproperty"></a><a name="setcontrolproperty"></a> CDHtmlDialog:: setcontrolproperty

Legt die-Eigenschaft eines ActiveX-Steuer Elements auf einen neuen Wert fest.

```cpp
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parameter

*szelementid*<br/>
Die HTML-ID eines ActiveX-Steuer Elements.

*dispId*<br/>
Die Dispatch-ID der festzulegenden Eigenschaft.

*pVar*<br/>
Zeiger auf einen Variant-Wert, der den neuen Eigenschafts Wert enthält.

*pdispcontrol*<br/>
Zeiger auf die-Schnittstelle eines ActiveX-Steuer Elements `IDispatch` .

*szpropname*<br/>
Zeichenfolge, die den Namen der festzulegenden Eigenschaft enthält.

## <a name="cdhtmldialogsetelementhtml"></a><a name="setelementhtml"></a> CDHtmlDialog:: ctelementhtml

Legt die- `innerHTML` Eigenschaft eines HTML-Elements fest.

```cpp
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parameter

*szelementid*<br/>
Die ID eines HTML-Elements.

*bstrautext*<br/>
Der neue Wert der `innerHTML` -Eigenschaft.

*punkelem*<br/>
Der `IUnknown` Zeiger eines HTML-Elements.

## <a name="cdhtmldialogsetelementproperty"></a><a name="setelementproperty"></a> CDHtmlDialog:: ab.

Legt eine Eigenschaft eines HTML-Elements fest.

```cpp
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parameter

*szelementid*<br/>
Die ID eines HTML-Elements.

*dispId*<br/>
Die Dispatch-ID der festzulegenden Eigenschaft.

*pVar*<br/>
Der neue Wert der Eigenschaft.

## <a name="cdhtmldialogsetelementtext"></a><a name="setelementtext"></a> CDHtmlDialog:: abtextzeile

Legt die- `innerText` Eigenschaft eines HTML-Elements fest.

```cpp
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parameter

*szelementid*<br/>
Die ID eines HTML-Elements.

*bstrautext*<br/>
Der neue Wert der `innerText` -Eigenschaft.

*punkelem*<br/>
Der `IUnknown` Zeiger eines HTML-Elements.

## <a name="cdhtmldialogsetexternaldispatch"></a><a name="setexternaldispatch"></a> CDHtmlDialog:: abtexternaldispatch

Legt die-Schnittstelle des Hosts fest `IDispatch` .

```cpp
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parameter

*pdispextern*<br/>
Die neue- `IDispatch` Schnittstelle.

## <a name="cdhtmldialogsethostflags"></a><a name="sethostflags"></a> CDHtmlDialog:: lthostflags

Legt die hostbenutzeroberflächenflags fest.

```cpp
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Mögliche Werte finden Sie unter [dochostuiflag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) in der Windows SDK.

## <a name="cdhtmldialogshowcontextmenu"></a><a name="showcontextmenu"></a> CDHtmlDialog:: ShowContextMenu

Wird aufgerufen, wenn ein Kontextmenü angezeigt wird.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parameter

*dwID*<br/>
Siehe *dwID* in [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) in der Windows SDK.

*PPT*<br/>
Siehe *PPT* in `IDocHostUIHandler::ShowContextMenu` im Windows SDK.

*pcmdtreserved*<br/>
Weitere Informationen finden Sie unter *pcmdtreserved* in `IDocHostUIHandler::ShowContextMenu` der Windows SDK.

*pdistreuserved*<br/>
Siehe *pdispree served* in `IDocHostUIHandler::ShowContextMenu` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialogshowui"></a><a name="showui"></a> CDHtmlDialog:: showUI

Zeigt die Benutzeroberfläche des Hosts an.

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>Parameter

*dwID*<br/>
Siehe *dwID* in [IDocHostUIHandler:: showUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) in der Windows SDK.

*pactiveobject*<br/>
Weitere Informationen finden Sie unter *d pactiveobject* in `IDocHostUIHandler::ShowUI` der Windows SDK.

*pcommandtarget*<br/>
Weitere Informationen finden Sie unter *pcommandtarget* in `IDocHostUIHandler::ShowUI` der Windows SDK.

*pFrame*<br/>
Siehe *pFrame* in `IDocHostUIHandler::ShowUI` im Windows SDK.

*pDoc*<br/>
Weitere Informationen finden Sie unter *Pdoc* in `IDocHostUIHandler::ShowUI` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: showUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialogtranslateaccelerator"></a><a name="translateaccelerator"></a> CDHtmlDialog:: TranslateAccelerator

Wird aufgerufen, um Menü Zugriffstasten-Meldungen zu verarbeiten.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parameter

*lpmsg*<br/>
Weitere Informationen finden Sie unter *lpmsg* in [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) in der Windows SDK.

*pguidcmdgroup*<br/>
Siehe *pguidcmdgroup* in `IDocHostUIHandler::TranslateAccelerator` im Windows SDK.

*nCmdId*<br/>
Weitere Informationen finden Sie unter *nCmdId* in `IDocHostUIHandler::TranslateAccelerator` der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialogtranslateurl"></a><a name="translateurl"></a> CDHtmlDialog:: translateurl

Wird aufgerufen, um die zu ladende URL zu ändern.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parameter

*dwtranslation*<br/>
Weitere Informationen finden Sie unter *dwtranslation* in [IDocHostUIHandler:: translateurl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) im Windows SDK.

*pchurlin*<br/>
Siehe *pchurlin* in `IDocHostUIHandler::TranslateUrl` im Windows SDK.

*ppabwanderung*<br/>
Weitere Informationen finden *Sie unter ppchurlout* in `IDocHostUIHandler::TranslateUrl` der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: translateurl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="cdhtmldialogupdateui"></a><a name="updateui"></a> CDHtmlDialog:: UpdateUI

Wird aufgerufen, um den Host zu benachrichtigen, dass sich der Befehlsstatus geändert hat.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion ist die CDHtmlDialog-Implementierung von [IDocHostUIHandler:: UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), wie im Windows SDK beschrieben.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel DHtmlExplore](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml Hilfsobjekte](#ddx_dhtml_helper_macros)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
