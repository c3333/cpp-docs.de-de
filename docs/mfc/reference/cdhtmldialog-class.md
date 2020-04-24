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
ms.openlocfilehash: e2e4306320c52b8276d915848dfa6e460982c92b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753376"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog-Klasse

Wird verwendet, um Dialogfelder zu erstellen, die HTML anstelle von Dialogfeldressourcen zum Implementieren der Benutzeroberfläche verwenden.

## <a name="syntax"></a>Syntax

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|Erstellt ein CDHtmlDialog-Objekt.|
|[CDHtmlDialog::-CDHtmlDialog](#_dtorcdhtmldialog)|Zerstört ein CDHtmlDialog-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Overridable, das als Zugriffsüberprüfung aufgerufen wird, um festzustellen, ob Skriptobjekte auf der geladenen Seite auf den externen Dispatch der Kontrollwebsite zugreifen können. Überprüft, ob der Dispatch entweder sicher für Skripts ist oder die aktuelle Zone Objekte zulässt, die für Skripting nicht sicher sind.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Overridable wird verwendet, um eine Steuerelementsiteinstanz zu erstellen, um das WebBrowser-Steuerelement im Dialogfeld zu hosten.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Tauscht Daten zwischen einer Membervariablen und dem Eigenschaftswert eines ActiveX-Steuerelements auf einer HTML-Seite aus.|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Tauscht Daten zwischen einer Mitgliedsvariablen und einem Kontrollkästchen auf einer HTML-Seite aus.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|Tauscht Daten zwischen einer Membervariablen und einer beliebigen HTML-Elementeigenschaft auf einer HTML-Seite aus.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|Tauscht Daten zwischen einer Mitgliedsvariablen und einem Optionsfeld auf einer HTML-Seite aus.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Ruft den Index eines Listenfelds auf einer HTML-Seite ab oder legt er fest.|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|Ruft den Anzeigetext eines Listenfeldeintrags (basierend auf dem aktuellen Index) auf einer HTML-Seite ab oder legt er fest.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Ruft den Wert eines Listenfeldeintrags (basierend auf dem aktuellen Index) auf einer HTML-Seite ab oder legt den Wert fest.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Zerstört ein modusloses Dialogfeld.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Aktiviert moduslose Dialogfelder.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Ermöglicht dem Dialogfeld das Filtern von Zwischenablagedatenobjekten, die vom gehosteten Browser erstellt wurden.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|Ruft die `IDispatch` Schnittstelle für ein ActiveX-Steuerelement ab, das in das HTML-Dokument eingebettet ist.|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|Ruft die angeforderte Eigenschaft des angegebenen ActiveX-Steuerelements ab.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Ruft den URL (Uniform Resource Locator) ab, der dem aktuellen Dokument zugeordnet ist.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Ruft die IHTMLDocument2-Schnittstelle für das aktuell geladene HTML-Dokument ab.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Wird vom enthaltenen WebBrowser-Steuerelement aufgerufen, wenn es als Ablageziel verwendet wird, damit das Dialogfeld ein alternatives [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)bereitstellen kann.|
|[CDHtmlDialog::GetElement](#getelement)|Ruft eine Schnittstelle für ein HTML-Element ab.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|Ruft die `innerHTML` Eigenschaft eines HTML-Elements ab.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Ruft den angeforderten Schnittstellenzeiger aus einem HTML-Element ab.|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|Ruft den Wert der Eigenschaft eines HTML-Elements ab.|
|[CDHtmlDialog::GetElementText](#getelementtext)|Ruft die `innerText` Eigenschaft eines HTML-Elements ab.|
|[CDHtmlDialog::GetEvent](#getevent)|Ruft `IHTMLEventObj` den Zeiger auf das aktuelle Ereignisobjekt ab.|
|[CDHtmlDialog::GetExternal](#getexternal)|Ruft die Schnittstelle `IDispatch` des Hosts ab.|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Ruft die UI-Funktionen des Hosts ab.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Ruft den Registrierungsschlüssel ab, unter dem Benutzereinstellungen gespeichert werden.|
|[CDHtmlDialog::HideUI](#hideui)|Blendet die Benutzeroberfläche des Hosts aus.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Gibt an, ob `IDispatch` die Schnittstelle des Hosts für die Skripterstellung sicher ist.|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|Lädt die angegebene Ressource in das WebBrowser-Steuerelement.|
|[CDHtmlDialog::Navigieren](#navigate)|Navigiert zur angegebenen URL.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Wird vom Framework aufgerufen, bevor ein Navigationsereignis ausgelöst wird.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Wird vom Framework aufgerufen, um eine Anwendung zu benachrichtigen, wenn ein Dokument den Status READYSTATE_COMPLETE erreicht hat.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Wird vom Framework aufgerufen, wenn das Dokumentfenster aktiviert oder deaktiviert wird.|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|Wird vom Framework aufgerufen, wenn das Rahmenfenster aktiviert oder deaktiviert ist.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Wird als Reaktion auf die WM_INITDIALOG Nachricht aufgerufen.|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|Wird vom Framework aufgerufen, nachdem ein Navigationsereignis abgeschlossen wurde.|
|[CDHtmlDialog::GrößeVon Border ändern](#resizeborder)|Warnt das Objekt, dass es die Größe seines Rahmenraums ändern muss.|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|Legt die Eigenschaft eines ActiveX-Steuerelements auf einen neuen Wert fest.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|Legt `innerHTML` die Eigenschaft eines HTML-Elements fest.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Legt eine Eigenschaft eines HTML-Elements fest.|
|[CDHtmlDialog::SetElementText](#setelementtext)|Legt `innerText` die Eigenschaft eines HTML-Elements fest.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Legt die Schnittstelle `IDispatch` des Hosts fest.|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Legt die UI-Flags des Hosts fest.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Wird aufgerufen, wenn ein Kontextmenü angezeigt werden soll.|
|[CDHtmlDialog::ShowUI](#showui)|Zeigt die Benutzeroberfläche des Hosts an.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Wird aufgerufen, um Menübeschleuniger-Schlüsselmeldungen zu verarbeiten.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Wird aufgerufen, um die zu ladende URL zu ändern.|
|[CDHtmlDialog::UpdateUI](#updateui)|Wird aufgerufen, um den Host darüber zu informieren, dass sich der Befehlsstatus geändert hat.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Gibt an, ob der Titel des HTML-Dokuments als Dialogfeldbeschriftung verwendet werden soll.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|Ressourcen-ID der HTML-Ressource, die angezeigt werden soll.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Ein Zeiger auf eine Webbrowseranwendung.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Ein Zeiger auf ein HTML-Dokument.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|Die aktuelle URL.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Zeichenfolgenversion der HTML-Ressourcen-ID.|

## <a name="remarks"></a>Bemerkungen

`CDHtmlDialog`kann den HTML-Code laden, der entweder aus einer HTML-Ressource oder einer URL angezeigt werden soll.

`CDHtmlDialog`kann auch Datenaustausch mit HTML-Steuerelementen durchführen und Ereignisse von HTML-Steuerelementen verarbeiten, z. B. Schaltflächenklicks.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxdhtml.h

## <a name="ddx_dhtml-helper-macros"></a><a name="ddx_dhtml_helper_macros"></a>DDX_DHtml Hilfsmakros

Die DDX_DHtml Hilfsmakros ermöglichen einen einfachen Zugriff auf die häufig verwendeten Eigenschaften von Steuerelementen auf einer HTML-Seite.

### <a name="data-exchange-macros"></a>Datenaustauschmakros

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Legt die Value-Eigenschaft fest oder ruft sie aus dem ausgewählten Steuerelement ab.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Legt den Text zwischen den Start- und Endtags des aktuellen Elements fest oder ruft ihn ab.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Legt den HTML-Code zwischen den Start- und Endtags des aktuellen Elements fest oder ruft ihn ab.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Legt die Ziel-URL oder den Ankerpunkt fest oder ruft sie ab.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Legt das Zielfenster oder den Zielrahmen fest oder ruft es ab.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Legt den Namen eines Bildes oder eines Videoclips im Dokument fest oder ruft ihn ab.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Legt die URL des zugeordneten Frames fest oder ruft sie ab.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Legt die URL des zugeordneten Frames fest oder ruft sie ab.|

## <a name="cdhtmldialogcanaccessexternal"></a><a name="canaccessexternal"></a>CDHtmlDialog::CanAccessExternal

Overridable, das als Zugriffsüberprüfung aufgerufen wird, um festzustellen, ob Skriptobjekte auf der geladenen Seite auf den externen Dispatch der Kontrollwebsite zugreifen können. Überprüft, ob der Dispatch entweder sicher für Skripts ist oder die aktuelle Zone Objekte zulässt, die für Skripting nicht sicher sind.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="cdhtmldialogcdhtmldialog"></a><a name="cdhtmldialog"></a>CDHtmlDialog::CDHtmlDialog

Erstellt ein ressourcenbasiertes dynamisches HTML-Dialogfeld.

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

*lpszTemplateName*<br/>
Die null-terminierte Zeichenfolge, die der Name einer Dialogfeldvorlagenressource ist.

*szHtmlResID*<br/>
Die null-terminierte Zeichenfolge, die der Name einer HTML-Ressource ist.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete oder Besitzerfensterobjekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogobjekts auf das Hauptanwendungsfenster festgelegt.

*nIDTemplate*<br/>
Enthält die ID-Nummer einer Dialogfeldvorlagenressource.

*nHtmlResID*<br/>
Enthält die ID-Nummer einer HTML-Ressource.

### <a name="remarks"></a>Bemerkungen

Die zweite Form des Konstruktors ermöglicht den Zugriff auf die Dialogressource über den Vorlagennamen. Die dritte Form des Konstruktors ermöglicht den Zugriff auf die Dialogressource über die ID der Ressourcenvorlage. Normalerweise beginnt die ID mit dem **IDD_** Präfix.

## <a name="cdhtmldialogcdhtmldialog"></a><a name="_dtorcdhtmldialog"></a>CDHtmlDialog::-CDHtmlDialog

Zerstört ein CDHtmlDialog-Objekt.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Bemerkungen

Die [Memberfunktion CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) muss verwendet werden, um moduslose Dialogfelder zu zerstören, die von [CDialog::Create](../../mfc/reference/cdialog-class.md#create)erstellt werden.

## <a name="cdhtmldialogcreatecontrolsite"></a><a name="createcontrolsite"></a>CDHtmlDialog::CreateControlSite

Overridable wird verwendet, um eine Steuerelementsiteinstanz zu erstellen, um das WebBrowser-Steuerelement im Dialogfeld zu hosten.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parameter

*pContainer*<br/>
Ein Zeiger auf das [COleControlContainer-Objekt](../../mfc/reference/colecontrolcontainer-class.md)

*ppSite*<br/>
Ein Zeiger auf einen Zeiger auf eine [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie können diese Memberfunktion überschreiben, um eine Instanz Ihrer eigenen Steuerelementsiteklasse zurückzugeben.

## <a name="cdhtmldialogddx_dhtml_axcontrol"></a><a name="ddx_dhtml_axcontrol"></a>CDHtmlDialog::DDX_DHtml_AxControl

Tauscht Daten zwischen einer Membervariablen und dem Eigenschaftswert eines ActiveX-Steuerelements auf einer HTML-Seite aus.

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
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Der Wert des ID-Parameters des Objekttags in der HTML-Quelle für das ActiveX-Steuerelement.

*Dispid*<br/>
Die Dispatch-ID der Eigenschaft, mit der Sie Daten austauschen möchten.

*szPropName*<br/>
Der Name der Eigenschaft.

*var*<br/>
Das Datenelement vom Typ VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md)oder [CComVariant](../../atl/reference/ccomvariant-class.md), das den mit der ActiveX-Steuerelementeigenschaft ausgetauschten Wert enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

## <a name="cdhtmldialogddx_dhtml_checkbox"></a><a name="ddx_dhtml_checkbox"></a>CDHtmlDialog::DDX_DHtml_CheckBox

Tauscht Daten zwischen einer Mitgliedsvariablen und einem Kontrollkästchen auf einer HTML-Seite aus.

```cpp
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuerelements angegeben haben.

*value*<br/>
Der ausgetauschte Wert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

## <a name="cdhtmldialogddx_dhtml_elementtext"></a><a name="ddx_dhtml_elementtext"></a>CDHtmlDialog::DDX_DHtml_ElementText

Tauscht Daten zwischen einer Membervariablen und einer beliebigen HTML-Elementeigenschaft auf einer HTML-Seite aus.

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
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuerelements angegeben haben.

*Dispid*<br/>
Die Dispatch-ID des HTML-Elements, mit dem Sie Daten austauschen möchten.

*value*<br/>
Der ausgetauschte Wert.

## <a name="cdhtmldialogddx_dhtml_radio"></a><a name="ddx_dhtml_radio"></a>CDHtmlDialog::DDX_DHtml_Radio

Tauscht Daten zwischen einer Mitgliedsvariablen und einem Optionsfeld auf einer HTML-Seite aus.

```cpp
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuerelements angegeben haben.

*value*<br/>
Der ausgetauschte Wert.

## <a name="cdhtmldialogddx_dhtml_selectindex"></a><a name="ddx_dhtml_selectindex"></a>CDHtmlDialog::DDX_DHtml_SelectIndex

Ruft den Index eines Listenfelds auf einer HTML-Seite ab oder legt er fest.

```cpp
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Der Wert, den Sie für `id` den Parameter des HTML-Steuerelements angegeben haben.

*value*<br/>
Der ausgetauschte Wert.

## <a name="cdhtmldialogddx_dhtml_selectstring"></a><a name="ddx_dhtml_selectstring"></a>CDHtmlDialog::DDX_DHtml_SelectString

Ruft den Anzeigetext eines Listenfeldeintrags (basierend auf dem aktuellen Index) auf einer HTML-Seite ab oder legt er fest.

```cpp
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuerelements angegeben haben.

*value*<br/>
Der ausgetauschte Wert.

## <a name="cdhtmldialogddx_dhtml_selectvalue"></a><a name="ddx_dhtml_selectvalue"></a>CDHtmlDialog::DDX_DHtml_SelectValue

Ruft den Wert eines Listenfeldeintrags (basierend auf dem aktuellen Index) auf einer HTML-Seite ab oder legt den Wert fest.

```cpp
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuerelements angegeben haben.

*value*<br/>
Der ausgetauschte Wert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

## <a name="cdhtmldialogdestroymodeless"></a><a name="destroymodeless"></a>CDHtmlDialog::DestroyModeless

Trennt ein modusloses Dialogfeld `CDHtmlDialog` vom Objekt und zerstört das Objekt.

```cpp
void DestroyModeless();
```

## <a name="cdhtmldialogenablemodeless"></a><a name="enablemodeless"></a>CDHtmlDialog::EnableModeless

Aktiviert moduslose Dialogfelder.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parameter

*fEnable*<br/>
Siehe *fEnable* in [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialogfilterdataobject"></a><a name="filterdataobject"></a>CDHtmlDialog::FilterDataObject

Ermöglicht dem Dialogfeld das Filtern von Zwischenablagedatenobjekten, die vom gehosteten Browser erstellt wurden.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parameter

*Pdo*<br/>
Siehe *pDO* in [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) im Windows SDK.

*ppDORet*<br/>
Siehe *ppDORet* in `IDocHostUIHandler::FilterDataObject` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialoggetcontroldispatch"></a><a name="getcontroldispatch"></a>CDHtmlDialog::GetControlDispatch

Ruft die `IDispatch` Schnittstelle für ein ActiveX-Steuerelement ab, das in das html-Dokument eingebettet ist, das von [GetDHtmlDocument](#getdhtmldocument)zurückgegeben wird.

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parameter

*szId*<br/>
Die HTML-ID eines ActiveX-Steuerelements.

*ppdisp*<br/>
Die `IDispatch` Schnittstelle des Steuerelements, wenn sie auf der Webseite gefunden wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="cdhtmldialoggetcontrolproperty"></a><a name="getcontrolproperty"></a>CDHtmlDialog::GetControlProperty

Ruft die angeforderte Eigenschaft des angegebenen ActiveX-Steuerelements ab.

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

*szId*<br/>
Die HTML-ID eines ActiveX-Steuerelements.

*szPropName*<br/>
Der Name einer Eigenschaft im Standardgebietsschema des aktuellen Benutzers.

*pdispControl*<br/>
Der `IDispatch` Zeiger eines ActiveX-Steuerelements.

*Dispid*<br/>
Die Dispatch-ID einer Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Eine Variante, die die angeforderte Eigenschaft enthält, oder eine leere Variante, wenn das Steuerelement oder die Eigenschaft nicht gefunden werden konnte.

### <a name="remarks"></a>Bemerkungen

Die Überlastungen werden von der am wenigsten effizienten oben bis zur effizientesten am unteren Seite aufgelistet.

## <a name="cdhtmldialoggetcurrenturl"></a><a name="getcurrenturl"></a>CDHtmlDialog::GetCurrentUrl

Ruft den URL (Uniform Resource Locator) ab, der dem aktuellen Dokument zugeordnet ist.

```cpp
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parameter

*szUrl*<br/>
Ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das die abzurufende URL enthält.

## <a name="cdhtmldialoggetdhtmldocument"></a><a name="getdhtmldocument"></a>CDHtmlDialog::GetDHtmlDocument

Ruft die [IHTMLDocument2-Schnittstelle](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) für das aktuell geladene HTML-Dokument ab.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parameter

* \* \** Ein Zeiger auf einen Zeiger auf ein HTML-Dokument.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT. Gibt S_OK zurück, wenn dies erfolgreich ist.

## <a name="cdhtmldialoggetdroptarget"></a><a name="getdroptarget"></a>CDHtmlDialog::GetDropTarget

Wird vom enthaltenen WebBrowser-Steuerelement aufgerufen, wenn es als Ablageziel verwendet wird, damit das Dialogfeld ein alternatives [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)bereitstellen kann.

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parameter

*pDropTarget*<br/>
Siehe *pDropTarget* in [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) im Windows SDK.

*ppDropTarget*<br/>
Siehe *ppDropTarget* in `IDocHostUIHandler::GetDropTarget` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialoggetelement"></a><a name="getelement"></a>CDHtmlDialog::GetElement

Gibt eine Schnittstelle für das von *szElementId*angegebene HTML-Element zurück.

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

*szElementId*<br/>
Die ID eines HTML-Elements.

*ppdisp*<br/>
Ein `IDispatch` Zeiger auf das angeforderte Element oder die Auflistung von Elementen.

*pbCollection*<br/>
Ein BOOL, der angibt, ob das von *ppdisp* dargestellte Objekt ein einzelnes Element oder eine Auflistung von Elementen ist.

*pphtmlElement*<br/>
Ein `IHTMLElement` Zeiger auf das angeforderte Element.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die erste Überladung, wenn Sie Bedingungen behandeln müssen, bei denen möglicherweise mehr als ein Element mit der angegebenen ID vorhanden ist. Sie können den letzten Parameter verwenden, um herauszufinden, ob sich der zurückgegebene Schnittstellenzeiger auf eine Auflistung oder ein einzelnes Element begibt. Wenn sich der Schnittstellenzeiger in einer Auflistung `IHTMLElementCollection` befindet, `item` können Sie die abfragen und deren Eigenschaft verwenden, um auf die Elemente nach Ordinalposition zu verweisen.

Die zweite Überladung schlägt fehl, wenn mehr als ein Element mit derselben ID auf der Seite vorhanden ist.

## <a name="cdhtmldialoggetelementhtml"></a><a name="getelementhtml"></a>CDHtmlDialog::GetElementHtml

Ruft die `innerHTML` Eigenschaft des HTML-Elements ab, das von *szElementId*identifiziert wurde.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parameter

*szElementId*<br/>
Die ID eines HTML-Elements.

### <a name="return-value"></a>Rückgabewert

Die `innerHTML` Eigenschaft des HTML-Elements, das durch *szElementId* oder NULL identifiziert wurde, wenn das Element nicht gefunden werden konnte.

## <a name="cdhtmldialoggetelementinterface"></a><a name="getelementinterface"></a>CDHtmlDialog::GetElementInterface

Ruft den angeforderten Schnittstellenzeiger aus dem html-Element ab, das von *szElementId*identifiziert wurde.

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

*szElementId*<br/>
Die ID eines HTML-Elements.

*ppvObj*<br/>
Adresse eines Zeigers, der mit dem angeforderten Schnittstellenzeiger gefüllt wird, wenn das Element gefunden wird und die Abfrage erfolgreich ist.

*Refiid*<br/>
Die Schnittstellen-ID (IID) der angeforderten Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

## <a name="cdhtmldialoggetelementproperty"></a><a name="getelementproperty"></a>CDHtmlDialog::GetElementProperty

Ruft den Wert der Eigenschaft ab, die durch *dispId* aus dem html-Element identifiziert wurde, das von *szElementId*identifiziert wurde.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Parameter

*szElementId*<br/>
Die ID eines HTML-Elements.

*Dispid*<br/>
Die Dispatch-ID einer Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Der Wert der Eigenschaft oder eine leere Variante, wenn die Eigenschaft oder das Element nicht gefunden werden konnte.

## <a name="cdhtmldialoggetelementtext"></a><a name="getelementtext"></a>CDHtmlDialog::GetElementText

Ruft die `innerText` Eigenschaft des HTML-Elements ab, das von *szElementId*identifiziert wurde.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parameter

*szElementId*<br/>
Die ID eines HTML-Elements.

### <a name="return-value"></a>Rückgabewert

Die `innerText` Eigenschaft des HTML-Elements, das durch *szElementId* oder NULL identifiziert wurde, wenn die Eigenschaft oder das Element nicht gefunden werden konnte.

## <a name="cdhtmldialoggetevent"></a><a name="getevent"></a>CDHtmlDialog::GetEvent

Gibt `IHTMLEventObj` den Zeiger auf das aktuelle Ereignisobjekt zurück.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parameter

*ppEventObj*<br/>
Adresse eines Zeigers, der mit `IHTMLEventObj` dem Schnittstellenzeiger gefüllt wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte nur innerhalb eines DHTML-Ereignishandlers aufgerufen werden.

## <a name="cdhtmldialoggetexternal"></a><a name="getexternal"></a>CDHtmlDialog::GetExternal

Ruft die Schnittstelle `IDispatch` des Hosts ab.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parameter

*ppDispatch*<br/>
Siehe *ppDispatch* in [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder E_NOTIMPL bei Einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialoggethostinfo"></a><a name="gethostinfo"></a>CDHtmlDialog::GetHostInfo

Ruft die UI-Funktionen des Hosts ab.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parameter

*Pinfo*<br/>
Siehe *pInfo* in [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialoggetoptionkeypath"></a><a name="getoptionkeypath"></a>CDHtmlDialog::GetOptionKeyPath

Ruft den Registrierungsschlüssel ab, unter dem Benutzereinstellungen gespeichert werden.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parameter

*pchKey*<br/>
Siehe *pchKey* in [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) im Windows SDK.

*dw*<br/>
Siehe *dw* dw `IDocHostUIHandler::GetOptionKeyPath` in im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialoghideui"></a><a name="hideui"></a>CDHtmlDialog::HideUI

Blendet die Benutzeroberfläche des Hosts aus.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialogisexternaldispatchsafe"></a><a name="isexternaldispatchsafe"></a>CDHtmlDialog::IsExternalDispatchSafe

Gibt an, ob `IDispatch` die Schnittstelle des Hosts für die Skripterstellung sicher ist.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Rückgabewert

Gibt FALSE zurück.

## <a name="cdhtmldialogloadfromresource"></a><a name="loadfromresource"></a>CDHtmlDialog::LoadFromResource

Lädt die angegebene Ressource in das WebBrowser-Steuerelement im DHTML-Dialogfeld.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Parameter

*lpszResource*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der zu ladenden Ressource enthält.

*Nres*<br/>
Die ID der zu ladenden Ressource

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

## <a name="cdhtmldialogm_busehtmltitle"></a><a name="m_busehtmltitle"></a>CDHtmlDialog::m_bUseHtmlTitle

Gibt an, ob der Titel des HTML-Dokuments als Dialogfeldbeschriftung verwendet werden soll.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Bemerkungen

Wenn **m**_ **bUseHtmlTitle** TRUE ist, wird die Dialogbeschriftung gleich dem Titel des HTML-Dokuments festgelegt. Andernfalls wird die Beschriftung in der Dialogressource verwendet.

## <a name="cdhtmldialogm_nhtmlresid"></a><a name="m_nhtmlresid"></a>CDHtmlDialog::m_nHtmlResID

Ressourcen-ID der HTML-Ressource, die angezeigt werden soll.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

## <a name="cdhtmldialogm_pbrowserapp"></a><a name="m_pbrowserapp"></a>CDHtmlDialog::m_pBrowserApp

Ein Zeiger auf eine Webbrowseranwendung.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

## <a name="cdhtmldialogm_sphtmldoc"></a><a name="m_sphtmldoc"></a>CDHtmlDialog::m_spHtmlDoc

Ein Zeiger auf ein HTML-Dokument.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

## <a name="cdhtmldialogm_strcurrenturl"></a><a name="m_strcurrenturl"></a>CDHtmlDialog::m_strCurrentUrl

Die aktuelle URL.

```
CString m_strCurrentUrl;
```

## <a name="cdhtmldialogm_szhtmlresid"></a><a name="m_szhtmlresid"></a>CDHtmlDialog::m_szHtmlResID

Zeichenfolgenversion der HTML-Ressourcen-ID.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

## <a name="cdhtmldialognavigate"></a><a name="navigate"></a>CDHtmlDialog::Navigieren

Navigiert zu der Ressource, die durch die von *lpszURL*angegebene URL identifiziert wird.

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

*lpszURL*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält, auf die ausgerichtet werden soll.

*dwFlags*<br/>
Die Flags einer Variablen, die angibt, ob die Ressource der Verlaufsliste hinzugefügt werden soll, ob sie in den Cache gelesen oder aus dem Cache geschrieben werden soll und ob die Ressource in einem neuen Fenster angezeigt werden soll. Die Variable kann eine Kombination der durch die [BrowserNavConstants-Enumeration](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) definierten Werte sein.

*lpszTargetFrameName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Rahmens enthält, in dem die Ressource angezeigt werden soll.

*lpszHeaders*<br/>
Ein Zeiger auf einen Wert, der die HTTP-Header angibt, die an den Server gesendet werden sollen. Diese Header werden den Standard-Internet Explorer-Headern hinzugefügt. Die Header können informationen wie die vom Server benötigte Aktion, den Typ der an den Server übergebenen Daten oder einen Statuscode angeben. Dieser Parameter wird ignoriert, wenn die URL keine HTTP-URL ist.

*lpvPostData*<br/>
Ein Zeiger auf die Daten, die mit der HTTP-POST-Transaktion gesendet werden sollen. Die POST-Transaktion wird beispielsweise zum Senden von Daten verwendet, die über ein HTML-Formular gesammelt wurden. Wenn dieser Parameter keine Postdaten `Navigate` angibt, wird eine HTTP GET-Transaktion aus. Dieser Parameter wird ignoriert, wenn die URL keine HTTP-URL ist.

*dwPostDataLen*<br/>
Daten, die mit der HTTP-POST-Transaktion gesendet werden sollen. Die POST-Transaktion wird beispielsweise zum Senden von Daten verwendet, die über ein HTML-Formular gesammelt wurden. Wenn dieser Parameter keine Postdaten `Navigate` angibt, wird eine HTTP GET-Transaktion aus. Dieser Parameter wird ignoriert, wenn URL keine HTTP-URL ist.

## <a name="cdhtmldialogonbeforenavigate"></a><a name="onbeforenavigate"></a>CDHtmlDialog::OnBeforeNavigate

Wird vom Framework aufgerufen, um ein Auslösen eines Ereignisses zu verursachen, bevor eine Navigation stattfindet.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
Ein Zeiger auf ein `IDispatch` -Objekt.

*szUrl*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält, zu der navigiert werden soll.

## <a name="cdhtmldialogondocumentcomplete"></a><a name="ondocumentcomplete"></a>CDHtmlDialog::OnDocumentComplete

Wird vom Framework aufgerufen, um eine Anwendung zu benachrichtigen, wenn ein Dokument den Status READYSTATE_COMPLETE erreicht hat.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
Ein Zeiger auf ein `IDispatch` -Objekt.

*szUrl*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält, zu der navigiert wurde.

## <a name="cdhtmldialogondocwindowactivate"></a><a name="ondocwindowactivate"></a>CDHtmlDialog::OnDocWindowActivate

Wird vom Framework aufgerufen, wenn das Dokumentfenster aktiviert oder deaktiviert wird.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parameter

*fActivate*<br/>
Siehe *fActivate* in [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialogonframewindowactivate"></a><a name="onframewindowactivate"></a>CDHtmlDialog::OnFrameWindowActivate

Wird vom Framework aufgerufen, wenn das Rahmenfenster aktiviert oder deaktiviert ist.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parameter

*fActivate*<br/>
Siehe *fActivate* in [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialogoninitdialog"></a><a name="oninitdialog"></a>CDHtmlDialog::OnInitDialog

Wird als Reaktion auf die WM_INITDIALOG Nachricht aufgerufen.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Nachricht wird während der `Create`, `CreateIndirect`oder `DoModal` Anrufe an das Dialogfeld gesendet, die unmittelbar vor der Anzeige des Dialogfelds erfolgen.

Überschreiben Sie diese Memberfunktion, wenn Sie eine spezielle Verarbeitung durchführen müssen, wenn das Dialogfeld initialisiert wird. Rufen Sie in der überschriebenen `OnInitDialog` Version zuerst die Basisklasse auf, ignorieren jedoch ihren Rückgabewert. Normalerweise geben Sie TRUE von Ihrer überschriebenen Memberfunktion zurück.

Windows ruft `OnInitDialog` die Funktion über die standardmäßige globale Dialogfeldprozedur auf, die allen Dialogfeldern der Microsoft Foundation-Klassenbibliothek und nicht über Ihre Nachrichtenzuordnung gemeinsam ist, sodass Sie keinen Meldungszuordnungseintrag für diese Memberfunktion benötigen.

## <a name="cdhtmldialogonnavigatecomplete"></a><a name="onnavigatecomplete"></a>CDHtmlDialog::OnNavigateComplete

Wird vom Framework aufgerufen, nachdem die Navigation zur angegebenen URL abgeschlossen ist.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
Ein Zeiger auf ein `IDispatch` -Objekt.

*szUrl*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält, zu der navigiert wurde.

## <a name="cdhtmldialogresizeborder"></a><a name="resizeborder"></a>CDHtmlDialog::GrößeVon Border ändern

Warnt das Objekt, dass es die Größe seines Rahmenraums ändern muss.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parameter

*prcBorder*<br/>
Siehe *prcBorder* in [IDocHostUIHandler::ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) im Windows SDK.

*pUIWindow*<br/>
Siehe *pUIWindow* in `IDocHostUIHandler::ResizeBorder` im Windows SDK.

*fFrameWindow*<br/>
Siehe *fFrameWindow* in `IDocHostUIHandler::ResizeBorder` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

## <a name="cdhtmldialogsetcontrolproperty"></a><a name="setcontrolproperty"></a>CDHtmlDialog::SetControlProperty

Legt die Eigenschaft eines ActiveX-Steuerelements auf einen neuen Wert fest.

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

*szElementId*<br/>
Die HTML-ID eines ActiveX-Steuerelements.

*Dispid*<br/>
Die Dispatch-ID der festzulegenden Eigenschaft.

*pVar*<br/>
Zeiger auf einen VARIANT, der den neuen Eigenschaftswert enthält.

*pdispControl*<br/>
Zeiger auf die Schnittstelle eines `IDispatch` ActiveX-Steuerelements.

*szPropName*<br/>
Zeichenfolge, die den Namen der festzulegenden Eigenschaft enthält.

## <a name="cdhtmldialogsetelementhtml"></a><a name="setelementhtml"></a>CDHtmlDialog::SetElementHtml

Legt `innerHTML` die Eigenschaft eines HTML-Elements fest.

```cpp
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parameter

*szElementId*<br/>
Die ID eines HTML-Elements.

*bstrText*<br/>
Der neue Wert der `innerHTML`-Eigenschaft.

*punkElem*<br/>
Der `IUnknown` Zeiger eines HTML-Elements.

## <a name="cdhtmldialogsetelementproperty"></a><a name="setelementproperty"></a>CDHtmlDialog::SetElementProperty

Legt eine Eigenschaft eines HTML-Elements fest.

```cpp
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parameter

*szElementId*<br/>
Die ID eines HTML-Elements.

*Dispid*<br/>
Die Dispatch-ID der festzulegenden Eigenschaft.

*pVar*<br/>
Der neue Wert der Eigenschaft.

## <a name="cdhtmldialogsetelementtext"></a><a name="setelementtext"></a>CDHtmlDialog::SetElementText

Legt `innerText` die Eigenschaft eines HTML-Elements fest.

```cpp
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parameter

*szElementId*<br/>
Die ID eines HTML-Elements.

*bstrText*<br/>
Der neue Wert der `innerText`-Eigenschaft.

*punkElem*<br/>
Der `IUnknown` Zeiger eines HTML-Elements.

## <a name="cdhtmldialogsetexternaldispatch"></a><a name="setexternaldispatch"></a>CDHtmlDialog::SetExternalDispatch

Legt die Schnittstelle `IDispatch` des Hosts fest.

```cpp
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parameter

*pdispExtern*<br/>
Die `IDispatch` neue Schnittstelle.

## <a name="cdhtmldialogsethostflags"></a><a name="sethostflags"></a>CDHtmlDialog::SetHostFlags

Legt die Host-UI-Flags fest.

```cpp
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Mögliche Werte finden Sie unter [ABEROSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) im Windows SDK.

## <a name="cdhtmldialogshowcontextmenu"></a><a name="showcontextmenu"></a>CDHtmlDialog::ShowContextMenu

Wird aufgerufen, wenn ein Kontextmenü angezeigt werden soll.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parameter

*dwID*<br/>
Siehe *dwID* in [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) im Windows SDK.

*Ppt*<br/>
Siehe *ppt* `IDocHostUIHandler::ShowContextMenu` in im Windows SDK.

*pcmdtReserviert*<br/>
Siehe *pcmdtReserved* in `IDocHostUIHandler::ShowContextMenu` im Windows SDK.

*pdispReserved*<br/>
Siehe *pdispReserved* in `IDocHostUIHandler::ShowContextMenu` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialogshowui"></a><a name="showui"></a>CDHtmlDialog::ShowUI

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
Siehe *dwID* in [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) im Windows SDK.

*pActiveObject*<br/>
Siehe *d pActiveObject* in `IDocHostUIHandler::ShowUI` im Windows SDK.

*pCommandTarget*<br/>
Siehe *pCommandTarget* in `IDocHostUIHandler::ShowUI` im Windows SDK.

*pFrame*<br/>
Siehe *pFrame* in `IDocHostUIHandler::ShowUI` im Windows SDK.

*pDoc*<br/>
Siehe *pDoc* in `IDocHostUIHandler::ShowUI` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialogtranslateaccelerator"></a><a name="translateaccelerator"></a>CDHtmlDialog::TranslateAccelerator

Wird aufgerufen, um Menübeschleuniger-Schlüsselmeldungen zu verarbeiten.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parameter

*lpMsg*<br/>
Siehe *lpMsg* in [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) im Windows SDK.

*pguidCmdGroup*<br/>
Siehe *pguidCmdGroup* in `IDocHostUIHandler::TranslateAccelerator` im Windows SDK.

*nCmdID*<br/>
Siehe *nCmdID* in `IDocHostUIHandler::TranslateAccelerator` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialogtranslateurl"></a><a name="translateurl"></a>CDHtmlDialog::TranslateUrl

Wird aufgerufen, um die zu ladende URL zu ändern.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parameter

*dwTranslate*<br/>
Siehe *dwTranslate* in [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) im Windows SDK.

*pchURLIn*<br/>
Siehe *pchURLIn* in `IDocHostUIHandler::TranslateUrl` im Windows SDK.

*ppchURLOut*<br/>
Siehe *ppchURLOut* in `IDocHostUIHandler::TranslateUrl` im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt S_FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="cdhtmldialogupdateui"></a><a name="updateui"></a>CDHtmlDialog::UpdateUI

Wird aufgerufen, um den Host darüber zu informieren, dass sich der Befehlsstatus geändert hat.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist die Implementierung von [IDocHostUIHandler::UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))von CDHtmlDialog, wie im Windows SDK beschrieben.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel DHtmlExplore](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml-Hilfsmakros](#ddx_dhtml_helper_macros)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
