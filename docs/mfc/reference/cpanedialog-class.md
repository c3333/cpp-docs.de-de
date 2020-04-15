---
title: CPaneDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: ad1225034cc5eca8ca53b042ebe3b55db4a2cf09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364124"
---
# <a name="cpanedialog-class"></a>CPaneDialog-Klasse

Die `CPaneDialog` Klasse unterstützt ein modusloses, andockbares Dialogfeld.

## <a name="syntax"></a>Syntax

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Der Standardkonstruktor.|
|`CPaneDialog::~CPaneDialog`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPaneDialog::Erstellen](#create)|Erstellt ein andockbares Dialogfeld `CPaneDialog` und fügt es an ein Objekt an.|
|`CPaneDialog::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CPaneDialog::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Behandelt die [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) Nachricht. (Neudefiniert `CBasePane::HandleInitDialog`.)|
|`CPaneDialog::OnEraseBkgnd`|Behandelt die [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) Nachricht. (Neudefiniert [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Behandelt die [WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk) Nachricht. (Neudefiniert [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Behandelt die [WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown) Nachricht. (Definiert [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Wird vom Framework aufgerufen, um das Dialogfeldfenster zu aktualisieren. (Überschreibt [CDockablePane::OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Behandelt die [WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging) Nachricht. (Definiert [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetoccDialogInfo](#setoccdialoginfo)|Gibt die Vorlage für ein Dialogfeld an, das ein OLE-Steuerelementcontainer ist.|

## <a name="remarks"></a>Bemerkungen

Erstellen `CPaneDialog` Sie ein Objekt in zwei Schritten. Erstellen Sie zunächst das Objekt im Code. Zweitens rufen Sie [CPaneDialog::Create](#create)auf. Sie müssen einen gültigen Ressourcenvorlagennamen oder eine gültige Vorlagen-ID angeben und einen Zeiger an das übergeordnete Fenster übergeben. Andernfalls schlägt der Erstellungsprozess fehl. Das Dialogfeld muss den Stil WS_CHILD und WS_VISIBLE angeben. Es wird empfohlen, auch die Stile WS_CLIPCHILDREN und WS_CLIPSIBLINGS anzugeben. Weitere Informationen finden Sie unter [Fensterstile](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxpanedialog.h

## <a name="cpanedialogcreate"></a><a name="create"></a>CPaneDialog::Erstellen

Erstellt ein Andockdialogfeld und fügt `CPaneDialog` es an ein Objekt an.

```
BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID,
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*lpszWindowName*<br/>
[in] Der Name des Andockdialogfelds.

*pParentWnd*<br/>
[in] Zeigt auf das übergeordnete Fenster.

*bHasGripper*<br/>
[in] TRUE, um das Andockdialogfeld mit einer Beschriftung (Greifer) zu erstellen; andernfalls FALSE.

*lpszTemplateName*<br/>
[in] Der Name der Ressourcendialogvorlage.

*nStyle*<br/>
[in] Der Windows-Stil.

*nID*<br/>
[in] Die Steuerelement-ID.

*nIDTemplate*<br/>
[in] Die Ressourcen-ID der Dialogfeldvorlage.

*dwTabbedStyle*<br/>
[in] Der Stil des Registerkartenfensters, der entsteht, wenn der Benutzer einen anderen Steuerbereich auf die Beschriftung dieses Steuerbereichs zieht. Der Standardwert ist AFX_CBRS_REGULAR_TABS. Weitere Informationen finden Sie im Abschnitt "Hinweise" der [CBasePane::CreateEx-Methode.](../../mfc/reference/cbasepane-class.md#createex)

*dwControlBarStyle*<br/>
[in] Zusätzliche Stilattribute. Der Standardwert ist AFX_DEFAULT_DOCKING_PANE_STYLE. Weitere Informationen finden Sie im Abschnitt "Hinweise" der [CBasePane::CreateEx-Methode.](../../mfc/reference/cbasepane-class.md#createex)

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `Create` veranschaulicht, `CPaneDialog` wie die Methode in der Klasse verwendet wird. Dieses Beispiel ist Teil des [Beispiels Bereichgröße festlegen](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

## <a name="cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a>CPaneDialog::HandleInitDialog

Behandelt die [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) Nachricht.

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*wParam*<br/>
[in] Behandeln Sie das Steuerelement, das den Standardtastaturfokus erhalten soll.

*lParam*<br/>
[in] Gibt zusätzliche Initialisierungsdaten an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE. Darüber hinaus legt TRUE den Tastaturfokus auf das steuerelement fest, das durch den *Parameter wParam* angegeben wird. FALSE verhindert, dass der Standardtastaturfokus festgelegt wird.

### <a name="remarks"></a>Bemerkungen

Das Framework verwendet diese Methode, um Steuerelemente und die Darstellung eines Dialogfelds zu initialisieren. Das Framework ruft diese Methode auf, bevor das Dialogfeld angezeigt wird.

## <a name="cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a>CPaneDialog::SetoccDialogInfo

Gibt die Vorlage für ein Dialogfeld an, das ein OLE-Steuerelementcontainer ist.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parameter

*pOccDialogInfo*<br/>
[in] Zeigen Sie auf eine Dialogfeldvorlage, die zum Erstellen des Dialogfeldobjekts verwendet wird. Der Wert dieses Parameters wird anschließend an die [COccManager::CreateDlgControls-Methode](../../mfc/reference/coccmanager-class.md#createdlgcontrols) übergeben.

### <a name="return-value"></a>Rückgabewert

Immer TRUE.

### <a name="remarks"></a>Bemerkungen

Diese Methode unterstützt die [COccManager-Klasse,](../../mfc/reference/coccmanager-class.md) die OLE-Steuerstandorte und ActiveX-Steuerelemente verwaltet. Die _AFX_OCC_DIALOG_INFO-Struktur ist in der Headerdatei afxocc.h definiert.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane-Klasse](../../mfc/reference/cdockablepane-class.md)<br/>
[Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles)
