---
title: COleControlSite-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
ms.openlocfilehash: 6cf12d017db1a1558b0dd915d9f3ba85894bee19
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366153"
---
# <a name="colecontrolsite-class"></a>COleControlSite-Klasse

Stellt Unterstützung für benutzerdefinierte clientseitige Steuerelement-Schnittstellen bereit.

## <a name="syntax"></a>Syntax

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleControlSite::COleControlSite](#colecontrolsite)|Erstellt ein `COleControlSite`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Bindet die Standardeigenschaft des gehosteten Steuerelements an eine Datenquelle.|
|[COleControlSite::BindProperty](#bindproperty)|Bindet eine Eigenschaft des gehosteten Steuerelements an eine Datenquelle.|
|[COleControlSite::CreateControl](#createcontrol)|Erstellt ein gehostetes ActiveX-Steuerelement.|
|[COleControlSite::DestroyControl](#destroycontrol)|Zerstört das gehostete Steuerelement.|
|[COleControlSite::DoVerb](#doverb)|Führt ein bestimmtes Verb des gehosteten Steuerelements aus.|
|[COleControlSite::EnableDSC](#enabledsc)|Ermöglicht die Datenbeschaffung für einen Kontrollstandort.|
|[COleControlSite::EnableWindow](#enablewindow)|Aktiviert die Kontrollsite.|
|[COleControlSite::FreezeEvents](#freezeevents)|Gibt an, ob die Kontrollsite Ereignisse akzeptiert.|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Ruft den Standardschaltflächencode für das gehostete Steuerelement ab.|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Ruft den Bezeichner des Steuerelements ab.|
|[COleControlSite::GetEventIID](#geteventiid)|Ruft die ID einer Ereignisschnittstelle für ein gehostetes Steuerelement ab.|
|[COleControlSite::GetExStyle](#getexstyle)|Ruft die erweiterten Stile der Steuerelementsite ab.|
|[COleControlSite::GetProperty](#getproperty)|Ruft eine bestimmte Eigenschaft des gehosteten Steuerelements ab.|
|[COleControlSite::GetStyle](#getstyle)|Ruft die Stile der Steuerelementsite ab.|
|[COleControlSite::GetWindowText](#getwindowtext)|Ruft den Text des gehosteten Steuerelements ab.|
|[COleControlSite::InvokeHelper](#invokehelper)|Rufen Sie eine bestimmte Methode des gehosteten Steuerelements auf.|
|[COleControlSite::InvokeHelperV](#invokehelperv)|Rufen Sie eine bestimmte Methode des gehosteten Steuerelements mit einer Variablenliste von Argumenten auf.|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Bestimmt, ob das Steuerelement die Standardschaltfläche im Fenster ist.|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Überprüft den sichtbaren Status der Kontrollsite.|
|[COleControlSite::ModifyStyle](#modifystyle)|Ändert die aktuellen erweiterten Stile der Steuerelementsite.|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Ändert die aktuellen Stile der Steuerelementsite.|
|[COleControlSite::MoveWindow](#movewindow)|Ändert die Position der Kontrollstelle.|
|[COleControlSite::QuickActivate](#quickactivate)|Quick aktiviert das gehostete Steuerelement.|
|[COleControlSite::SafeSetProperty](#safesetproperty)|Legt eine Eigenschaft oder Methode des Steuerelements fest, ohne dass eine Ausnahme ausgelöst werden kann.|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Legt die Standardschaltfläche im Fenster fest.|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Ruft den Bezeichner des Steuerelements ab.|
|[COleControlSite::SetFocus](#setfocus)|Legt den Fokus auf die Kontrollsite fest.|
|[COleControlSite::SetProperty](#setproperty)|Legt eine bestimmte Eigenschaft des gehosteten Steuerelements fest.|
|[COleControlSite::SetPropertyV](#setpropertyv)|Legt eine bestimmte Eigenschaft des gehosteten Steuerelements mit einer Variablenliste von Argumenten fest.|
|[COleControlSite::SetWindowPos](#setwindowpos)|Legt die Position der Kontrollstelle fest.|
|[COleControlSite::SetWindowText](#setwindowtext)|Legt den Text des gehosteten Steuerelements fest.|
|[COleControlSite::Fenster anzeigen](#showwindow)|Zeigt die Kontrollsite an oder blendet sie aus.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Ruft Tastaturinformationen und mnemonics für das gehostete Steuerelement ab.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Bestimmt, ob es sich bei dem gehosteten Steuerelement um ein fensterloses Steuerelement handelt.|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Enthält Informationen zur Tastaturbehandlung für das Steuerelement.|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Das Cookie des Verbindungspunkts des Steuerelements.|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Die verschiedenen Zustände für das gehostete Steuerelement.|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|Das `IPropertyNotifySink` Cookie des Steuerelements.|
|[COleControlSite::m_dwStyle](#m_dwstyle)|Die Stile des gehosteten Steuerelements.|
|[COleControlSite::m_hWnd](#m_hwnd)|Das Handle der Kontrollstelle.|
|[COleControlSite::m_iidEvents](#m_iidevents)|Die ID der Ereignisschnittstelle für das gehostete Steuerelement.|
|[COleControlSite::m_nID](#m_nid)|Die ID des gehosteten Steuerelements.|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Ein Zeiger auf `IOleInPlaceActiveObject` das Objekt des gehosteten Steuerelements.|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Der Container des gehosteten Steuerelements.|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Ein Zeiger auf `IOleInPlaceObject` das Objekt des gehosteten Steuerelements.|
|[COleControlSite::m_pObject](#m_pobject)|Ein Zeiger auf `IOleObjectInterface` die Schnittstelle des Steuerelements.|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Ein Zeiger auf `IOleInPlaceObjectWindowless` die Schnittstelle des Steuerelements.|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Ein Zeiger auf das Fensterobjekt für das gehostete Steuerelement.|
|[COleControlSite::m_rect](#m_rect)|Die Dimensionen der Kontrollstelle.|

## <a name="remarks"></a>Bemerkungen

Diese Unterstützung ist das primäre Mittel, mit dem ein eingebettetes ActiveX-Steuerelement Informationen über den Standort und die Ausdehnung seiner Anzeigesite, seinen Moniker, seine Benutzeroberfläche, seine Umgebungseigenschaften und andere Ressourcen, die von seinem Container bereitgestellt werden, erhält. `COleControlSite`implementiert die [IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite), [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite), `IBoundObjectSite` `INotifyDBEvents` [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), , [, iRowSetNotify-Schnittstellen](../../data/oledb/irowsetnotifyimpl-class.md) vollständig. Darüber hinaus wird die IDispatch-Schnittstelle (die Unterstützung für Umgebungseigenschaften und Ereignissenken bietet) implementiert.

Um eine ActiveX-Steuerelementsite mit `COleControlSite`zu `COleControlSite`erstellen, leiten Sie eine Klasse von ab. In `CWnd`ihrer -derived-Klasse für den Container (z. `CWnd::CreateControlSite` B. Im Dialogfeld) überschreiben Sie die Funktion.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxocc.h

## <a name="colecontrolsitebinddefaultproperty"></a><a name="binddefaultproperty"></a>COleControlSite::BindDefaultProperty

Bindet die einfache gebundene Standardeigenschaft des aufrufenden Objekts, wie in der Typbibliothek markiert, an den zugrunde liegenden Cursor, der durch die DataSource-, UserName-, Password- und SQL-Eigenschaften des Datenquellensteuerelements definiert wird.

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Gibt die DISPID einer Eigenschaft für ein datengebundenes Steuerelement an, das an ein Datenquellensteuerelement gebunden werden soll.

*vtProp*<br/>
Gibt den Typ der zu bindenden Eigenschaft an, z. B. VT_BSTR, VT_VARIANT usw.

*szFieldName*<br/>
Gibt den Namen der Spalte im Cursor an, der vom Datenquellensteuerelement bereitgestellt wird und an den die Eigenschaft gebunden wird.

*pDSCWnd*<br/>
Ein Zeiger auf `CWnd`das -derived-Objekt, das das Datenquellensteuerelement hostet, an das die Eigenschaft gebunden wird.

### <a name="remarks"></a>Bemerkungen

Das `CWnd` Objekt, auf dem Sie diese Funktion aufrufen, muss ein datengebundenes Steuerelement sein.

## <a name="colecontrolsitebindproperty"></a><a name="bindproperty"></a>COleControlSite::BindProperty

Bindet die einfache gebundene Eigenschaft des aufrufenden Objekts, wie in der Typbibliothek markiert, an den zugrunde liegenden Cursor, der durch die DataSource-, UserName-, Password- und SQL-Eigenschaften des Datenquellensteuerelements definiert wird.

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>Parameter

*dwDispId*<br/>
Gibt die DISPID einer Eigenschaft für ein datengebundenes Steuerelement an, das an ein Datenquellensteuerelement gebunden werden soll.

*pWndDSC*<br/>
Ein Zeiger auf `CWnd`das -derived-Objekt, das das Datenquellensteuerelement hostet, an das die Eigenschaft gebunden wird.

### <a name="remarks"></a>Bemerkungen

Das `CWnd` Objekt, auf dem Sie diese Funktion aufrufen, muss ein datengebundenes Steuerelement sein.

## <a name="colecontrolsitecolecontrolsite"></a><a name="colecontrolsite"></a>COleControlSite::COleControlSite

Erstellt ein neues `COleControlSite`-Objekt.

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parameter

*pCtrlCont*<br/>
Ein Zeiger auf den Container des Steuerelements (der das Fenster darstellt, in dem das AtiveX-Steuerelement gehostet wird).

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird von der [Funktion COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) aufgerufen. Weitere Informationen zum Anpassen der Erstellung von Containern finden Sie unter [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).

## <a name="colecontrolsitecreatecontrol"></a><a name="createcontrol"></a>COleControlSite::CreateControl

Erstellt ein ActiveX-Steuerelement, `COleControlSite` das vom Objekt gehostet wird.

```
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);

virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>Parameter

*pWndCtrl*<br/>
Ein Zeiger auf das Fensterobjekt, das das Steuerelement darstellt.

*clsid*<br/>
Die eindeutige Klassen-ID des Steuerelements.

*lpszWindowName*<br/>
Ein Zeiger auf den Text, der im Steuerelement angezeigt werden soll. Legt den Wert der Beschriftungs- oder Texteigenschaft des winodw fest (falls vorhanden).

*dwStyle*<br/>
Windows-Stile. Die verfügbaren Stile sind im Abschnitt **"Bemerkungen"** aufgeführt.

*Rect*<br/>
Gibt die Größe und Position des Steuerelements an. Es kann entweder `CRect` ein `RECT` Objekt oder eine Struktur sein.

*nID*<br/>
Gibt die untergeordnete Fenster-ID des Steuerelements an.

*pPersist*<br/>
Ein Zeiger auf `CFile` einen, der den persistenten Zustand für das Steuerelement enthält. Der Standardwert ist NULL, was darauf hinweist, dass sich das Steuerelement selbst initialisiert, ohne seinen Status aus einem persistenten Speicher wiederherzustellen. Wenn nicht NULL, sollte es ein `CFile`Zeiger auf ein -derived-Objekt sein, das die persistenten Daten des Steuerelements in Form eines Streams oder eines Speichers enthält. Diese Daten hätten bei einer vorherigen Aktivierung des Clients gespeichert werden können. Der `CFile` kann andere Daten enthalten, muss jedoch den Lese-/Schreibzeiger auf das erste Byte `CreateControl`persistenter Daten zum Zeitpunkt des Aufrufs von festlegen.

*bSpeicher*<br/>
Gibt an, ob die Daten `IStorage` in `IStream` *pPersist* als oder als Daten interpretiert werden sollen. Wenn es sich bei den Daten in *pPersist* um einen Speicher handelt, sollte *bStorage* TRUE sein. Wenn es sich bei den Daten in *pPersist* um einen Stream handelt, sollte *bStorage* FALSE sein. Der Standardwert ist FALSE.

*bstrLicKey*<br/>
Optionale Lizenzschlüsseldaten. Diese Daten werden nur zum Erstellen von Steuerelementen benötigt, die einen Laufzeitlizenzschlüssel erfordern. Wenn das Steuerelement die Lizenzierung unterstützt, müssen Sie einen Lizenzschlüssel angeben, damit das Steuerelement erfolgreich ausgeführt werden kann. Der Standardwert ist NULL.

*Ppt*<br/>
Ein Zeiger auf `POINT` eine Struktur, die die obere linke Ecke des Steuerelements enthält. Die Größe des Steuerelements wird durch den Wert von *psize*bestimmt. Die *ppt-* und *psize-Werte* sind eine optionale Methode zur Angabe der Größe und Position opf des Steuerelements.

*psize*<br/>
Ein Zeiger auf `SIZE` eine Struktur, die die Größe des Steuerelements enthält. Die obere linke Ecke wird durch den Wert von *ppt*bestimmt. Die *ppt-* und *psize-Werte* sind eine optionale Methode zur Angabe der Größe und Position opf des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Nur eine Teilmenge der Windows *dwStyle-Flags* wird unterstützt von: `CreateControl`

- WS_VISIBLE Erstellt ein Fenster, das zunächst sichtbar ist. Erforderlich, wenn das Steuerelement wie normale Fenster sofort sichtbar sein soll.

- WS_DISABLED Erstellt ein Fenster, das zunächst deaktiviert ist. Ein deaktiviertes Fenster kann keine Eingaben vom Benutzer empfangen. Kann festgelegt werden, wenn das Steuerelement über eine Enabled-Eigenschaft verfügt.

- WS_BORDER Erstellt ein Fenster mit einem dünnen Rahmen. Kann festgelegt werden, wenn das Steuerelement über eine BorderStyle-Eigenschaft verfügt.

- WS_GROUP Gibt das erste Steuerelement einer Gruppe von Steuerelementen an. Der Benutzer kann den Tastaturfokus mithilfe der Richtungstasten von einem Steuerelement in der Gruppe zum nächsten ändern. Alle Steuerelemente, die nach dem ersten Steuerelement mit dem WS_GROUP-Stil definiert wurden, gehören zur gleichen Gruppe. Das nächste Steuerelement mit dem Stil WS_GROUP beendet die Gruppe und startet die nächste Gruppe.

- WS_TABSTOP Gibt ein Steuerelement an, das den Tastaturfokus empfangen kann, wenn der Benutzer die TAB-Taste drückt. Durch Drücken der TAB-Taste wird der Tastaturfokus auf das nächste Steuerelement des WS_TABSTOP-Stils geändert.

Verwenden Sie die zweite Überladung, um Steuerelemente in Der Standardgröße zu erstellen.

## <a name="colecontrolsitedestroycontrol"></a><a name="destroycontrol"></a>COleControlSite::DestroyControl

Zerstört das `COleControlSite`-Objekt.

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Nach Abschluss wird das Objekt aus dem Speicher freigegeben, und alle Zeiger auf das Objekt sind nicht mehr gültig.

## <a name="colecontrolsitedoverb"></a><a name="doverb"></a>COleControlSite::DoVerb

Führt das angegebene Verb aus.

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>Parameter

*nVerb*<br/>
Gibt das auszuführende Verb an. Es kann eine der folgenden enthalten:

|Wert|Bedeutung|Symbol|
|-----------|-------------|------------|
|0|Primäres Verb|OLEIVERB_PRIMARY|
|-1|Sekundäres Verb|(Keine)|
|1|Zeigt das Objekt zur Bearbeitung an.|OLEIVERB_SHOW|
|-2|Bebaut das Element in einem separaten Fenster.|OLEIVERB_OPEN|
|-3|Blendet das Objekt aus.|OLEIVERB_HIDE|
|–4|Aktiviert ein Steuerelement an Ort und Stelle.|OLEIVERB_UIACTIVATE|
|-5|Aktiviert ein Steuerelement an Ort und Stelle, ohne zusätzliche Benutzeroberflächenelemente.|OLEIVERB_INPLACEACTIVATE|
|-7|Zeigen Sie die Eigenschaften des Steuerelements an.|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
Zeigen Sie auf die Meldung, die dazu geführt hat, dass das Element aktiviert wurde.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ruft direkt über `IOleObject` die Schnittstelle des Steuerelements auf, um das angegebene Verb auszuführen. Wenn aufgrund dieses Funktionsaufrufs eine Ausnahme ausgelöst wird, wird ein HRESULT-Fehlercode zurückgegeben.

Weitere Informationen finden Sie unter [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) im Windows SDK.

## <a name="colecontrolsiteenabledsc"></a><a name="enabledsc"></a>COleControlSite::EnableDSC

Ermöglicht die Datenbeschaffung für den Kontrollstandort.

```
virtual void EnableDSC();
```

### <a name="remarks"></a>Bemerkungen

Wird vom Framework aufgerufen, um die Datenbeschaffung für die Kontrollsite zu aktivieren und zu initialisieren. Überschreiben Sie diese Funktion, um benutzerdefiniertes Verhalten bereitzustellen.

## <a name="colecontrolsiteenablewindow"></a><a name="enablewindow"></a>COleControlSite::EnableWindow

Aktiviert oder deaktiviert Maus- und Tastatureingaben für die Steuerungssite.

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
Gibt an, ob das Fenster aktiviert oder deaktiviert werden soll: TRUE, wenn die Fenstereingabe aktiviert werden soll, andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Fenster zuvor deaktiviert war, andernfalls 0.

## <a name="colecontrolsitefreezeevents"></a><a name="freezeevents"></a>COleControlSite::FreezeEvents

Gibt an, ob die Kontrollsite Ereignisse behandeln oder ignoriert, die von einem Steuerelement ausgelöst werden.

```
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parameter

*bEinfrieren*<br/>
Gibt an, ob die Steuerelementsite das Akzeptieren von Ereignissen beenden möchte. Ein Wert ungleich Null, wenn das Steuerelement keine Ereignisse akzeptiert; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Wenn *bFreeze* TRUE ist, fordert die Kontrollsite das Steuerelement auf, fring-Ereignisse zu beenden. Wenn *bFreeze* FALSE ist, fordert die Kontrollsite das Steuerelement an, die Löschereignisse fortzusetzen.

> [!NOTE]
> Das Steuerelement ist nicht erforderlich, um das Auslösen von Ereignissen zu beenden, wenn die Scontrol-Site dies erfordert. Es kann weiterhin ausgelöst werden, aber alle nachfolgenden Ereignisse werden von der Kontrollsite ignoriert.

## <a name="colecontrolsitegetcontrolinfo"></a><a name="getcontrolinfo"></a>COleControlSite::GetControlInfo

Ruft Informationen über das Tastaturmnemonik- und Tastaturverhalten eines Steuerelements ab.

```
void GetControlInfo();
```

### <a name="remarks"></a>Bemerkungen

Die Informationen werden in [COleControlSite::m_ctlInfo](#m_ctlinfo)gespeichert.

## <a name="colecontrolsitegetdefbtncode"></a><a name="getdefbtncode"></a>COleControlSite::GetDefBtnCode

Bestimmt, ob es sich bei dem Steuerelement um eine Standard-Push-Taste handelt.

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>Rückgabewert

Es kann sich um einen der folgenden Werte handeln:

- DLGC_DEFPUSHBUTTON Control ist die Standardschaltfläche im Dialogfeld.

- DLGC_UNDEFPUSHBUTTON Control ist nicht die Standardschaltfläche im Dialogfeld.

- **0** Die Steuerung ist keine Schaltfläche.

## <a name="colecontrolsitegetdlgctrlid"></a><a name="getdlgctrlid"></a>COleControlSite::GetDlgCtrlID

Ruft den Bezeichner des Steuerelements ab.

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>Rückgabewert

Der Dialogelementbezeichner des Steuerelements.

## <a name="colecontrolsitegeteventiid"></a><a name="geteventiid"></a>COleControlSite::GetEventIID

Ruft einen Zeiger auf die Standardereignisschnittstelle des Steuerelements ab.

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>Parameter

*piid*<br/>
Ein Zeiger auf eine Schnittstellen-ID.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0. Wenn dies erfolgreich ist, enthält *piid* die Schnittstellen-ID für die Standardereignisschnittstelle des Steuerelements.

## <a name="colecontrolsitegetexstyle"></a><a name="getexstyle"></a>COleControlSite::GetExStyle

Ruft die erweiterten Stile des Fensters ab.

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Die erweiterten Stile des Steuerelementfensters.

### <a name="remarks"></a>Bemerkungen

Um die regulären Stile abzurufen, rufen Sie [COleControlSite::GetStyle](#getstyle)auf.

## <a name="colecontrolsitegetproperty"></a><a name="getproperty"></a>COleControlSite::GetProperty

Ruft die von *dwDispID*angegebene Steuerelementeigenschaft ab.

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Identifiziert die Dispatch-ID der Eigenschaft, die `IDispatch` auf der Standardschnittstelle des Steuerelements gefunden wird, die abgerufen werden soll.

*vtProp*<br/>
Gibt den Typ der abzuholenden Eigenschaft an. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvProp*<br/>
Adresse der Variablen, die den Eigenschaftswert empfängt. Er muss mit dem von *vtProp*angegebenen Typ übereinstimmen.

### <a name="remarks"></a>Bemerkungen

Der Wert wird über *pvProp*zurückgegeben.

## <a name="colecontrolsitegetstyle"></a><a name="getstyle"></a>COleControlSite::GetStyle

Ruft die Stile der Steuerelementsite ab.

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Die Stile des Fensters.

### <a name="remarks"></a>Bemerkungen

Eine Liste möglicher Werte finden Sie unter [Windows-Formatvorlagen](../../mfc/reference/styles-used-by-mfc.md#window-styles). Um die erweiterten Stile der Steuerelementsite abzurufen, rufen Sie [COleControlSite::GetExStyle](#getexstyle)auf.

## <a name="colecontrolsitegetwindowtext"></a><a name="getwindowtext"></a>COleControlSite::GetWindowText

Ruft den aktuellen Text des Steuerelements ab.

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Ein Verweis `CString` auf ein Objekt, das den aktuellen Text des Steuerelements enthält.

### <a name="remarks"></a>Bemerkungen

Wenn das Steuerelement die Caption stock-Eigenschaft unterstützt, wird dieser Wert zurückgegeben. Wenn die Caption stock-Eigenschaft nicht unterstützt wird, wird der Wert für die Text-Eigenschaft zurückgegeben.

## <a name="colecontrolsiteinvokehelper"></a><a name="invokehelper"></a>COleControlSite::InvokeHelper

Ruft die von *dwDispID*angegebene Methode oder Eigenschaft in dem von *wFlags*angegebenen Kontext auf.

```
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Identifiziert die Dispatch-ID der Eigenschaft oder Methode, `IDispatch` die auf der Schnittstelle des Steuerelements gefunden wird, die aufgerufen werden soll.

*wFlags*<br/>
Flags, die den Kontext des Aufrufs von IDispatch::Invoke beschreiben. Mögliche *wFlags-Werte* `IDispatch::Invoke` finden Sie im Windows SDK.

*vtRet*<br/>
Gibt den Typ des Rückgabewerts an. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Die Adresse der Variablen, die den Eigenschaftswert oder Rückgabewert aufnimmt. Er muss mit dem von *vtRet*angegebenen Typ übereinstimmen.

*pbParamInfo*<br/>
Zeiger auf eine null-terminierte Bytes-Zeichenfolge, die die Typen der Parameter nach *pbParamInfo*angibt. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Variablenliste der Parameter der in *pbParamInfo*angegebenen Typen.

### <a name="remarks"></a>Bemerkungen

Der *Parameter pbParamInfo* gibt die Typen der Parameter an, die an die Methode oder Eigenschaft übergeben werden. Die variable Argumentliste wird in der Syntaxdeklaration durch ... dargestellt.

Diese Funktion konvertiert die Parameter in VARIANTARG-Werte und ruft dann die `IDispatch::Invoke` Methode für das Steuerelement auf. Bei einem Fehler des Aufrufs von `IDispatch::Invoke` löst diese Funktion eine Ausnahme aus. Wenn `IDispatch::Invoke` der von zurückgegebene `DISP_E_EXCEPTION`Statuscode `COleDispatchException` ist , löst `COleException`diese Funktion ein Objekt aus, andernfalls wird eine ausgelöst.

## <a name="colecontrolsiteinvokehelperv"></a><a name="invokehelperv"></a>COleControlSite::InvokeHelperV

Ruft die von *dwDispID*angegebene Methode oder Eigenschaft in dem von *wFlags*angegebenen Kontext auf.

```
virtual void InvokeHelperV(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo,
    va_list argList);
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Identifiziert die Dispatch-ID der Eigenschaft oder Methode, `IDispatch` die auf der Schnittstelle des Steuerelements gefunden wird, die aufgerufen werden soll.

*wFlags*<br/>
Flags, die den Kontext des Aufrufs von IDispatch::Invoke beschreiben.

*vtRet*<br/>
Gibt den Typ des Rückgabewerts an. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Die Adresse der Variablen, die den Eigenschaftswert oder Rückgabewert aufnimmt. Er muss mit dem von *vtRet*angegebenen Typ übereinstimmen.

*pbParamInfo*<br/>
Zeiger auf eine null-terminierte Bytes-Zeichenfolge, die die Typen der Parameter nach *pbParamInfo*angibt. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*Arglist*<br/>
Zeiger auf eine Variablenargumentliste.

### <a name="remarks"></a>Bemerkungen

Der *Parameter pbParamInfo* gibt die Typen der Parameter an, die an die Methode oder Eigenschaft übergeben werden. Zusätzliche Parameter für die aufgerufene Methode oder Eigenschaft können mit dem *Parameter va_list* übergeben werden.

In der Regel wird `COleControlSite::InvokeHelper`diese Funktion von aufgerufen.

## <a name="colecontrolsiteisdefaultbutton"></a><a name="isdefaultbutton"></a>COleControlSite::IsDefaultButton

Bestimmt, ob das Steuerelement die Standardschaltfläche ist.

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Steuerelement die Standardschaltfläche im Fenster ist, andernfalls Null.

## <a name="colecontrolsiteiswindowenabled"></a><a name="iswindowenabled"></a>COleControlSite::IsWindowEnabled

Bestimmt, ob die Kontrollsite aktiviert ist.

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Steuerelement aktiviert ist, andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Der Wert wird aus der Eigenschaft Aktiviert des Steuerelements abgerufen.

## <a name="colecontrolsitem_biswindowless"></a><a name="m_biswindowless"></a>COleControlSite::m_bIsWindowless

Bestimmt, ob es sich bei dem Objekt um ein fensterloses Steuerelement handelt.

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>Bemerkungen

Ein Wert ungleich Null, wenn das Steuerelement kein Fenster hat, andernfalls Null.

## <a name="colecontrolsitem_ctlinfo"></a><a name="m_ctlinfo"></a>COleControlSite::m_ctlInfo

Informationen darüber, wie Die Tastatureingabe vom Steuerelement verarbeitet wird.

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>Bemerkungen

Diese Informationen werden in einer [CONTROLINFO-Struktur](/windows/win32/api/ocidl/ns-ocidl-controlinfo) gespeichert.

## <a name="colecontrolsitem_dweventsink"></a><a name="m_dweventsink"></a>COleControlSite::m_dwEventSink

Enthält das Cookie des Verbindungspunkts aus der Ereignissenke des Steuerelements.

```
DWORD m_dwEventSink;
```

## <a name="colecontrolsitem_dwmiscstatus"></a><a name="m_dwmiscstatus"></a>COleControlSite::m_dwMiscStatus

Enthält verschiedene Informationen zum Steuerelement.

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)im Windows SDK.

## <a name="colecontrolsitem_dwpropnotifysink"></a><a name="m_dwpropnotifysink"></a>COleControlSite::m_dwPropNotifySink

Enthält das [IPropertyNotifySink-Cookie.](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)

```
DWORD m_dwPropNotifySink;
```

## <a name="colecontrolsitem_dwstyle"></a><a name="m_dwstyle"></a>COleControlSite::m_dwStyle

Enthält die Fensterstile des Steuerelements.

```
DWORD m_dwStyle;
```

## <a name="colecontrolsitem_hwnd"></a><a name="m_hwnd"></a>COleControlSite::m_hWnd

Enthält die HWND des Steuerelements oder NULL, wenn das Steuerelement fensterlos ist.

```
HWND m_hWnd;
```

## <a name="colecontrolsitem_iidevents"></a><a name="m_iidevents"></a>COleControlSite::m_iidEvents

Enthält die Schnittstellen-ID der Standardereignissenkenschnittstelle des Steuerelements.

```
IID m_iidEvents;
```

## <a name="colecontrolsitem_nid"></a><a name="m_nid"></a>COleControlSite::m_nID

Enthält die Dialogelement-ID des Steuerelements.

```
UINT m_nID;
```

## <a name="colecontrolsitem_pactiveobject"></a><a name="m_pactiveobject"></a>COleControlSite::m_pActiveObject

Enthält die [IOleInPlaceActiveObject-Schnittstelle](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) des Steuerelements.

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

## <a name="colecontrolsitem_pctrlcont"></a><a name="m_pctrlcont"></a>COleControlSite::m_pCtrlCont

Enthält den Container des Steuerelements (der das Formular darstellt).

```
COleControlContainer* m_pCtrlCont;
```

## <a name="colecontrolsitem_pinplaceobject"></a><a name="m_pinplaceobject"></a>COleControlSite::m_pInPlaceObject

Enthält `IOleInPlaceObject` die [IOleInPlaceObject-Schnittstelle](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) des Steuerelements.

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

## <a name="colecontrolsitem_pobject"></a><a name="m_pobject"></a>COleControlSite::m_pObject

Enthält `IOleObjectInterface` die Schnittstelle des Steuerelements.

```
LPOLEOBJECT m_pObject;
```

## <a name="colecontrolsitem_pwindowlessobject"></a><a name="m_pwindowlessobject"></a>COleControlSite::m_pWindowlessObject

Enthält `IOleInPlaceObjectWindowless`die [IOleInPlaceObjectWindowless-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) des Steuerelements.

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

## <a name="colecontrolsitem_pwndctrl"></a><a name="m_pwndctrl"></a>COleControlSite::m_pWndCtrl

Enthält einen Zeiger `CWnd` auf das Objekt, das das Steuerelement selbst darstellt.

```
CWnd* m_pWndCtrl;
```

## <a name="colecontrolsitem_rect"></a><a name="m_rect"></a>COleControlSite::m_rect

Enthält die Grenzen des Steuerelements relativ zum Fenster des Containers.

```
CRect m_rect;
```

## <a name="colecontrolsitemodifystyle"></a><a name="modifystyle"></a>COleControlSite::ModifyStyle

Ändert die Stile des Steuerelements.

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parameter

*dwRemove*<br/>
Die Stile, die aus den aktuellen Fensterstilen entfernt werden sollen.

*dwAdd*<br/>
Die Stile, die aus den aktuellen Fensterstilen hinzugefügt werden sollen.

*nFlags*<br/>
Fensterpositionierungsflags. Eine Liste möglicher Werte finden Sie unter [SetWindowPos-Funktion](/windows/win32/api/winuser/nf-winuser-setwindowpos) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Stile geändert werden, andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Die Eigenschaft "Bestand aktiviert" des Steuerelements wird entsprechend der Einstellung für WS_DISABLED geändert. Die Border Style-Eigenschaft des Steuerelements wird so geändert, dass sie der angeforderten Einstellung für WS_BORDER entspricht. Alle anderen Stile werden direkt auf das Fensterhandle des Steuerelements angewendet, sofern einer vorhanden ist.

Ändert die Fensterstile des Steuerelements. Stile, die hinzugefügt oder entfernt werden sollen, können mithilfe des bitweisen ODER- ( &#124; )-Operators kombiniert werden. Informationen zu den verfügbaren Fensterstilen finden Sie unter [CreateWindow-Funktion](/windows/win32/api/winuser/nf-winuser-createwindoww) im Windows SDK.

Wenn *nFlags* ungleich `ModifyStyle` Null ist, `SetWindowPos`ruft die Win32-Funktion auf und zeichnet das Fenster neu, indem *nFlags* mit den folgenden vier Flags kombiniert wird:

- SWP_NOSIZE Behält die aktuelle Größe bei.

- SWP_NOMOVE Behält die aktuelle Position bei.

- SWP_NOZORDER Behält die aktuelle Z-Reihenfolge bei.

- SWP_NOACTIVATE Aktiviert das Fenster nicht.

Um die erweiterten Stile eines Fensters zu ändern, rufen Sie [ModifyStyleEx](#modifystyleex)auf.

## <a name="colecontrolsitemodifystyleex"></a><a name="modifystyleex"></a>COleControlSite::ModifyStyleEx

Ändert die erweiterten Stile des Steuerelements.

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parameter

*dwRemove*<br/>
Die erweiterten Stile, die aus den aktuellen Fensterstilen entfernt werden sollen.

*dwAdd*<br/>
Die erweiterten Stile, die aus den aktuellen Fensterstilen hinzugefügt werden sollen.

*nFlags*<br/>
Fensterpositionierungsflags. Eine Liste möglicher Werte finden Sie unter [SetWindowPos-Funktion](/windows/win32/api/winuser/nf-winuser-setwindowpos) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Stile geändert werden, andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Die Eigenschaft "Bestandsdarstellung" des Steuerelements wird entsprechend der Einstellung für WS_EX_CLIENTEDGE geändert. Alle anderen erweiterten Fensterstile werden direkt auf das Fensterhandle des Steuerelements angewendet, sofern einer vorhanden ist.

Ändert die erweiterten Fensterstile des Steuerelementwebsiteobjekts. Stile, die hinzugefügt oder entfernt werden sollen, können mithilfe des bitweisen ODER- ( &#124; )-Operators kombiniert werden. Informationen zu den verfügbaren Fensterstilen finden Sie unter [CreateWindowEx-Funktion](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

Wenn *nFlags* ungleich `ModifyStyleEx` Null ist, `SetWindowPos`ruft die Win32-Funktion auf und zeichnet das Fenster neu, indem *nFlags* mit den folgenden vier Flags kombiniert wird:

- SWP_NOSIZE Behält die aktuelle Größe bei.

- SWP_NOMOVE Behält die aktuelle Position bei.

- SWP_NOZORDER Behält die aktuelle Z-Reihenfolge bei.

- SWP_NOACTIVATE Aktiviert das Fenster nicht.

Um die erweiterten Stile eines Fensters zu ändern, rufen Sie [ModifyStyle](#modifystyle)auf.

## <a name="colecontrolsitemovewindow"></a><a name="movewindow"></a>COleControlSite::MoveWindow

Ändert die Position des Steuerelements.

```
virtual void MoveWindow(
    int x,
    int y,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Die neue Position der linken Seite des Fensters.

*y*<br/>
Die neue Position der Oberseite des Fensters.

*nWidth*<br/>
Die neue Breite des Fensters

*nHeight*<br/>
Die neue Höhe des Fensters.

## <a name="colecontrolsitequickactivate"></a><a name="quickactivate"></a>COleControlSite::QuickActivate

Quick aktiviert die enthaltene Steuerung.

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Kontrollsite aktiviert wurde, andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte nur aufgerufen werden, wenn der Benutzer den Erstellungsprozess des Steuerelements überschreibt.

Die `IPersist*::Load` `IPersist*::InitNew` und Methoden sollten nach der schnellen Aktivierung aufgerufen werden. Das Steuerelement sollte während der schnellen Aktivierung Verbindungen zu den Senken des Containers herstellen. Diese Verbindungen sind jedoch `IPersist*::Load` erst `IPersist*::InitNew` dann live, wenn sie aufgerufen wurden oder aufgerufen wurden.

## <a name="colecontrolsitesafesetproperty"></a><a name="safesetproperty"></a>COleControlSite::SafeSetProperty

Legt die von *dwDispID*angegebene Steuerelementeigenschaft fest.

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Identifiziert die Dispatch-ID der Eigenschaft oder Methode, `IDispatch` die auf der Schnittstelle des Steuerelements gefunden wird, die festgelegt werden soll.

*vtProp*<br/>
Gibt den Typ der festzulegenden Eigenschaft an. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Ein einzelner Parameter des von *vtProp*angegebenen Typs .

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Im `SetProperty` `SetPropertyV`Gegensatz zu und , wenn ein Fehler auftritt (z. B. der Versuch, eine nicht vorhandene Eigenschaft festzulegen), wird keine Ausnahme ausgelöst.

## <a name="colecontrolsitesetdefaultbutton"></a><a name="setdefaultbutton"></a>COleControlSite::SetDefaultButton

Legt das Steuerelement als Standardschaltfläche fest.

```
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>Parameter

*bDefault*<br/>
Ein Wert ungleich Null, wenn das Steuerelement zur Standardschaltfläche werden soll; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Das Steuerelement muss die OLEMISC_ACTSLIKEBUTTON Statusbit festgelegt haben.

## <a name="colecontrolsitesetdlgctrlid"></a><a name="setdlgctrlid"></a>COleControlSite::SetDlgCtrlID

Ändert den Wert des Dialogelementbezeichners des Steuerelements.

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der neue Bezeichnerwert.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird der vorherige Dialogelementbezeichner des Fensters angezeigt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

## <a name="colecontrolsitesetfocus"></a><a name="setfocus"></a>COleControlSite::SetFocus

Legt den Fokus auf das Steuerelement fest.

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>Parameter

*lpmsg*<br/>
Ein Zeiger auf eine [MSG-Struktur](/windows/win32/api/winuser/ns-winuser-msg). Diese Struktur enthält die `SetFocus` Windows-Meldung, die die Anforderung für das Steuerelement auslöst, das in der aktuellen Kontrollsite enthalten ist.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Fenster, das zuvor den Fokus hatte.

## <a name="colecontrolsitesetproperty"></a><a name="setproperty"></a>COleControlSite::SetProperty

Legt die von *dwDispID*angegebene Steuerelementeigenschaft fest.

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Identifiziert die Dispatch-ID der Eigenschaft oder Methode, `IDispatch` die auf der Schnittstelle des Steuerelements gefunden wird, die festgelegt werden soll.

*vtProp*<br/>
Gibt den Typ der festzulegenden Eigenschaft an. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Ein einzelner Parameter des von *vtProp*angegebenen Typs .

### <a name="remarks"></a>Bemerkungen

Wenn `SetProperty` ein Fehler auftritt, wird eine Ausnahme ausgelöst.

Der Typ der Ausnahme wird durch den Rückgabewert des Versuchs bestimmt, die Eigenschaft oder Methode festzulegen. Wenn der Rückgabewert `DISP_E_EXCEPTION` `COleDispatchExcpetion` ist , wird ein ausgelöst; andernfalls `COleException`eine .

## <a name="colecontrolsitesetpropertyv"></a><a name="setpropertyv"></a>COleControlSite::SetPropertyV

Legt die von *dwDispID*angegebene Steuerelementeigenschaft fest.

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Identifiziert die Dispatch-ID der Eigenschaft oder Methode, `IDispatch` die auf der Schnittstelle des Steuerelements gefunden wird, die festgelegt werden soll.

*vtProp*<br/>
Gibt den Typ der festzulegenden Eigenschaft an. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*Arglist*<br/>
Zeiger auf die Liste der Argumente.

### <a name="remarks"></a>Bemerkungen

Zusätzliche Parameter für die aufgerufene Methode oder Eigenschaft können mit dem *Parameter arg_list* übergeben werden. Wenn `SetProperty` ein Fehler auftritt, wird eine Ausnahme ausgelöst.

Der Typ der Ausnahme wird durch den Rückgabewert des Versuchs bestimmt, die Eigenschaft oder Methode festzulegen. Wenn der Rückgabewert `DISP_E_EXCEPTION` `COleDispatchExcpetion` ist , wird ein ausgelöst; andernfalls `COleException`eine .

## <a name="colecontrolsitesetwindowpos"></a><a name="setwindowpos"></a>COleControlSite::SetWindowPos

Legt die Größe, Position und Z-Reihenfolge der Kontrollsite fest.

```
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,
    int x,
    int y,
    int cx,
    int cy,
    UINT nFlags);
```

### <a name="parameters"></a>Parameter

*pWndInsertAfter*<br/>
Ein Zeiger auf das Fenster.

*X*<br/>
Die neue Position der linken Seite des Fensters.

*y*<br/>
Die neue Position der Oberseite des Fensters.

*Cx*<br/>
Die neue Breite des Fensters

*Cy*<br/>
Die neue Höhe des Fensters.

*nFlags*<br/>
Gibt die Fenstergrößen- und Positionierungsflags an. Mögliche Werte finden Sie im Abschnitt Hinweise für [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ungleich Null bei Erfolg, andernfalls Null.

## <a name="colecontrolsitesetwindowtext"></a><a name="setwindowtext"></a>COleControlSite::SetWindowText

Legt den Text für die Steuerelementsite fest.

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parameter

*lpszString*<br/>
Zeiger auf eine null-beendete Zeichenfolge, die als neuer Titel oder Steuertext verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion versucht zunächst, die Caption stock-Eigenschaft festzulegen. Wenn die Caption stock-Eigenschaft nicht unterstützt wird, wird stattdessen die Text-Eigenschaft festgelegt.

## <a name="colecontrolsiteshowwindow"></a><a name="showwindow"></a>COleControlSite::Fenster anzeigen

Legt den Anzeigestatus des Fensters fest.

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parameter

*nCmdShow*<br/>
Gibt an, wie die Kontrollsite angezeigt werden soll. Es muss einer der folgenden Werte sein:

- SW_HIDE Blendet dieses Fenster aus und übergibt die Aktivierung an ein anderes Fenster.

- SW_MINIMIZE Minimiert das Fenster und aktiviert das Fenster der obersten Ebene in der Systemliste.

- SW_RESTORE Aktiviert und zeigt das Fenster an. Wenn das Fenster minimiert oder maximiert ist, stellt Windows die ursprüngliche Größe und Position wieder her.

- SW_SHOW Aktiviert das Fenster und zeigt es in seiner aktuellen Größe und Position an.

- SW_SHOWMAXIMIZED Aktiviert das Fenster und zeigt es als maximiertes Fenster an.

- SW_SHOWMINIMIZED Aktiviert das Fenster und zeigt es als Symbol an.

- SW_SHOWMINNOACTIVE Zeigt das Fenster als Symbol an. Das Fenster, das derzeit aktiv ist, bleibt aktiv.

- SW_SHOWNA Zeigt das Fenster im aktuellen Zustand an. Das Fenster, das derzeit aktiv ist, bleibt aktiv.

- SW_SHOWNOACTIVATE Zeigt das Fenster in seiner neuesten Größe und Position an. Das Fenster, das derzeit aktiv ist, bleibt aktiv.

- SW_SHOWNORMAL Aktiviert und zeigt das Fenster an. Wenn das Fenster minimiert oder maximiert ist, stellt Windows die ursprüngliche Größe und Position wieder her.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Fenster zuvor sichtbar war; 0, wenn das Fenster zuvor ausgeblendet war.

## <a name="see-also"></a>Siehe auch

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer-Klasse](../../mfc/reference/colecontrolcontainer-class.md)
