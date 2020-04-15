---
title: CMFCOutlookBar-Klasse
ms.date: 06/25/2018
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
ms.openlocfilehash: fe328cb0d857ff9154624d218b1b56362890ce81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369656"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar-Klasse

Eine Seite im Registerformat mit dem Aussehen des **Navigationsbereichs** in Microsoft Outlook 2000 oder Outlook 2003. Das `CMFCOutlookBar` Objekt enthält ein [CMFCOutlookBarTabCtrl-Klassenobjekt](../../mfc/reference/cmfcoutlookbartabctrl-class.md) und eine Reihe von Registerkarten. Die Registerkarten können entweder [CMFCOutlookBarPane-Klassenobjekte](../../mfc/reference/cmfcoutlookbarpane-class.md) oder `CWnd`-abgeleitete Objekte sein. Für den Benutzer wird die Outlook-Leiste in Form einer Reihe von Schaltflächen und eines Anzeigebereichs dargestellt. Wenn der Benutzer auf eine Schaltfläche klickt, wird der entsprechende Steuerelement- oder Schaltflächenbereich angezeigt.

## <a name="syntax"></a>Syntax

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|Der Standardkonstruktor.|
|`CMFCOutlookBar::~CMFCOutlookBar`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Gibt an, ob ein leerer Registerkartenbereich zerstört werden kann. (Überschreibt [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Legt fest, ob ein anderer Bereich an den Outlook-Leistenbereich angedockt werden kann. (Überschreibt CDockablePane::CanAcceptPane.)|
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Legt fest, ob die Beschriftung für den Registerkartenbereich denselben Text wie die aktive Registerkarte anzeigt. (Überschreibt [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|
|[CMFCOutlookBar::Erstellen](#create)|Erstellt das Outlook-Leistensteuerelement.|
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Erstellt eine benutzerdefinierte Outlook-Leiste-Registerkarte.|
|`CMFCOutlookBar::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Bestimmt, ob ein Benutzer eine Steuerleiste am äußeren Rand der Outlook-Leiste andocken kann.|
|[CMFCOutlookBar::FloatTab](#floattab)|Überschreibt einen Bereich, jedoch nur, wenn sich der Bereich derzeit in einer abnehmbaren Registerkarte befindet. (Überschreibt [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Gibt die Schriftart des Textes auf den Schaltflächen der Outlook-Leiste zurück.|
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Gibt die Größe und Position der Registerkartenbereiche in der Outlook-Leiste zurück. (Überschreibt [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Bestimmt, ob das Verhalten der Outlook-Leiste mit dem von Microsoft Office Outlook 2003 imitiert wird (siehe Anmerkungen).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Wird von [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) aufgerufen, nachdem die aktive Registerkarte mithilfe von Animationen festgelegt wurde.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Wird von [CMFCOutlookBarTabCtrl::SetActiveTab aufgerufen,](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) bevor eine Registerkarte mithilfe der Animation als aktive Registerkarte festgelegt wird.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Wird vom Framework aufgerufen, wenn die Outlook-Leiste nach oben oder unten scrollt.|
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Entfernt eine benutzerdefinierte Outlook-Leiste-Registerkarte.|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Legt die Schriftart des Textes auf den Schaltflächen der Outlook-Leiste fest.|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Gibt an, ob das Verhalten der Outlook-Leiste mit dem von Outlook 2003 imitiert wird (siehe Anmerkungen).|

## <a name="remarks"></a>Bemerkungen

Ein Beispiel für eine Outlook-Leiste finden Sie im [OutlookDemo-Beispiel: MFC OutlookDemo-Anwendung](../../overview/visual-cpp-samples.md).

## <a name="implementing-the-outlook-bar"></a>Implementieren der Outlook-Leiste

Befolgen Sie folgende Schritte, um das `CMFCOutlookBar`-Steuerelement in Ihrer Anwendung zu verwenden:

1. Betten Sie ein `CMFCOutlookBar`-Objekt in die Hauptframe-Fensterklasse ein.

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. Rufen Sie beim Verarbeiten der WM_CREATE Nachricht im Hauptframe die [CMFCOutlookBar::Create-Methode](#create) auf, um das Outlook-Leisten-Registerkartensteuerelement zu erstellen.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Rufen Sie mithilfe von `CMFCOutlookBarTabCtrl` [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)einen Zeiger auf den Basiswert ab.

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Erstellen Sie ein [CMFCOutlookBarPane-Klassenobjekt](../../mfc/reference/cmfcoutlookbarpane-class.md) für jede Registerkarte, die Schaltflächen enthält.

    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);

    // make the Outlook pane detachable (enable docking)
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

1. Rufen Sie [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) auf, um jede neue Registerkarte hinzuzufügen. Legen Sie den *parameter bDetachable* auf FALSE fest, um eine Seite nicht abnehmbar zu machen. Oder verwenden Sie [CMFCOutlookBarTabCtrl::AddControl,](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) um abnehmbare Seiten hinzuzufügen.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Um ein `CWnd`-derived-Steuerelement (z. B. [CMFCShellTreeCtrl-Klasse](../../mfc/reference/cmfcshelltreectrl-class.md)) als Registerkarte hinzuzufügen, erstellen Sie das Steuerelement und rufen [Sie CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) auf, um es der Outlook-Leiste hinzuzufügen.

> [!NOTE]
> Sie sollten eindeutige Steuerelement-IDs für jedes [CMFCOutlookBarPane-Klassenobjekt](../../mfc/reference/cmfcoutlookbarpane-class.md) und für jedes `CWnd`-abgeleitete Objekt verwenden.

Um neue Seiten zur Laufzeit dynamisch hinzuzufügen oder zu löschen, verwenden Sie [CMFCOutlookBar::CreateCustomPage](#createcustompage) und [CMFCOutlookBar::RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Outlook 2003-Modus

Im Outlook 2003-Modus werden die Registerkartenschaltflächen am unteren Rand des Outlook-Leistenbereichs positioniert. Wenn nicht genügend Platz zum Anzeigen der Schaltflächen vorhanden ist, werden sie als Symbole in einem Symbolleisten-ähnlichen Bereich am unteren Rand des Bereichs angezeigt.

Verwenden Sie [CMFCOutlookBar::SetMode2003,](#setmode2003) um den Outlook 2003-Modus zu aktivieren. Verwenden Sie [CMFCOutlookBarTabCtrl::SetToolbarImageList,](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) um die Bitmap festzulegen, die die Symbole enthält, die am unteren Rand der Outlook-Leiste angezeigt werden. Die Symbole in der Bitmap müssen nach Tab-Index sortiert werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxoutlookbar.h

## <a name="cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::AllowDestroyEmptyTabbedPane

Gibt an, ob ein leerer Registerkartenbereich zerstört werden kann.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein leerer Tabbed-Bereich zerstört werden kann; andernfalls FALSE. Die Standardimplementierung gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Wenn ein leerer Registerkartenbereich nicht zerstört werden kann, wird er stattdessen vom Framework ausgeblendet.

## <a name="cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane

Legt fest, ob ein anderer Bereich an den Outlook-Leistenbereich angedockt werden kann.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
[in] Ein Zeiger auf einen anderen Bereich, der an diesen Bereich angedockt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein anderer Bereich an den Outlook-Leistenbereich angedockt werden kann; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn sich die Outlook-Leiste im Outlook 2003-Modus befindet, wird das Andocken nicht unterstützt, sodass der Rückgabewert FALSE ist.

Wenn der *pBar-Parameter* NULL ist, gibt diese Methode FALSE zurück.

Andernfalls verhält sich diese Methode wie die Basismethode [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), mit der Ausnahme, dass eine Outlook-Leiste auch dann eine andere Outlook-Leiste daran andocken kann, dass sie angedockt wird, auch wenn das Andocken nicht aktiviert ist.

## <a name="cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetCaptionTextToTabName

Legt fest, ob die Beschriftung für den Registerkartenbereich denselben Text wie die aktive Registerkarte anzeigt.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Beschriftung des Outlook-Leistenfensters automatisch auf den Text der aktiven Registerkarte festgelegt wird. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [CBaseTabbedPane::EnableSetCaptionTextToTabName,](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) um diese Funktionalität zu aktivieren oder zu deaktivieren.

Im Outlook 2003-Modus ist diese Einstellung immer aktiviert.

## <a name="cmfcoutlookbarcreate"></a><a name="create"></a>CMFCOutlookBar::Erstellen

Erstellt das Outlook-Leistensteuerelement.

```cpp
virtual BOOL Create(
    LPCTSTR lpszCaption,
    CWnd* pParentWnd,
    const RECT& rect,
    UINT nID,
    DWORD dwStyle,
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parameter

*lpszCaption*<br/>
[in] Gibt die Fensterbeschriftung an.

*pParentWnd*<br/>
[in] Gibt einen Zeiger auf ein übergeordnetes Fenster an. Es darf nicht NULL sein.

*Rect*<br/>
[in] Gibt die Größe der Outlook-Leiste und die Position in Pixeln an.

*nID*<br/>
[in] Gibt die Steuerelement-ID an. Es muss von anderen Instand- und Steuer-IDs unterschieden werden, die in der Anwendung verwendet werden.

*dwStyle*<br/>
[in] Gibt den gewünschten Steuerelementleistenstil an. Mögliche Werte finden Sie unter [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwControlBarStyle*<br/>
[in] Gibt die speziellen bibliotheksdefinierten Stile an.

*pContext*<br/>
[in] Erstellen Sie Kontext.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CMFCOutlookBar` ein Objekt in zwei Schritten. Rufen Sie zuerst den Konstruktor auf, und rufen Sie dann `Create` `CMFCOutlookBar` auf, das das Outlook-Leistensteuerelement erstellt und an das Objekt anfügt.

Siehe [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) für die Liste der verfügbaren bibliotheksdefinierten Stile, die von *dwControlBarStyle*angegeben werden sollen.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `Create` veranschaulicht, `CMFCOutlookBar` wie die Methode der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [Outlook Multi Views-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

## <a name="cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a>CMFCOutlookBar::CreateCustomPage

Erstellt eine benutzerdefinierte Outlook-Leiste-Registerkarte.

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszPageName*<br/>
[in] Die Seitenbeschriftung.

*bActivatePage*<br/>
[in] Wenn TRUE, wird die Seite bei der Erstellung aktiv.

*dwEnabledDocking*<br/>
[in] Eine Kombination aus CBRS_ALIGN_-Flags, die die aktivierten Andockseiten angibt, wenn die Seite getrennt wird.

*bEnableTextLabels*<br/>
[in] Wenn TRUE, sind die Textbeschriftungen für die Schaltflächen aktiviert, die sich auf der Seite befinden.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die neu erstellte Seite oder NULL, wenn die Erstellung fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um den Benutzern das Erstellen benutzerdefinierter Outlook-Leistenseiten zu ermöglichen. Sie können bis zu 100 Seiten pro Anwendung erstellen. Die Seitensteuerungs-IDs beginnen bei 0xF000. Die Erstellung schlägt fehl, wenn die Gesamtzahl der benutzerdefinierten Outlook-Leistenseiten 100 überschreitet.

Verwenden Sie [CMFCOutlookBar::RemoveCustomPage,](#removecustompage) um benutzerdefinierte Seiten zu löschen.

## <a name="cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertBefore

Gibt an, ob ein Benutzer einen Bereich am äußeren Rand der Outlook-Leiste andocken kann.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Das Framework `DoesAllowDynInsertBefore` ruft die Methode auf, wenn es nach einem Speicherort sucht, an den ein dynamischer Bereich angedockt werden soll. Wenn die Funktion FALSE zurückgibt, lässt das Framework das Andocken eines dynamischen Bereichs an den äußeren Rändern des Bereichs nicht zu.

Normalerweise erstellen Sie eine Outlook-Leiste als statisches nicht schwebendes Steuerelement. Sie können diese Funktion in einer abgeleiteten Klasse überschreiben und TRUE zurückgeben, um dieses Verhalten zu ändern.

> [!NOTE]
> Da dynamische Bereiche den Status von angedockten statischen Bereichen beim Andocken überprüfen, sollten Sie dynamische Bereiche nach statischen Bereichen andocken, wann immer dies möglich ist.

## <a name="cmfcoutlookbarfloattab"></a><a name="floattab"></a>CMFCOutlookBar::FloatTab

Übergibt einen Bereich.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
[in] Ein Zeiger auf den zu schwebenden Bereich.

*nTabID*<br/>
[in] Der nullbasierte Index der Zu floatenden Registerkarte.

*dockMethode*<br/>
[in] Gibt die Methode an, die verwendet werden soll, um den Bereich float enden zu lassen.  Weitere Informationen finden Sie unter [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bHide*<br/>
[in] TRUE, um den Bereich vor dem Floating auszublenden; andernfalls FALSE. Im Gegensatz zur Basisklassenversion dieser Methode verfügt dieser Parameter nicht über einen Standardwert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich überlauft wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode ähnelt [CBaseTabbedPane::FloatTab,](../../mfc/reference/cbasetabbedpane-class.md#floattab) außer dass die letzte verbleibende Registerkarte in einem Outlook-Leistensteuerelement nicht zum Floaten aktiviert wird.

## <a name="cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a>CMFCOutlookBar::GetButtonsFont

Gibt die Schriftart des Textes auf den Seitenschaltflächen-Registerkarten der Outlook-Leiste zurück.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Schriftartobjekt, das zum Anzeigen von Text auf DenOkperseitenschaltflächen verwendet wird.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um die Schriftart abzurufen, die zum Anzeigen des Texts auf den Registerkarten der Outlook-Seitenschaltflächeverwendet wird. Sie können die Schriftart festlegen, indem Sie [cmFCOutlookBar::SetButtonsFont](#setbuttonsfont)aufrufen.

## <a name="cmfcoutlookbargettabarea"></a><a name="gettabarea"></a>CMFCOutlookBar::GetTabArea

Bestimmt die Größe und Position der Registerkartenbereiche in der Outlook-Leiste.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parameter

*rectTabAreaTop*<br/>
[out] Enthält die Größe und Position (in den Clientkoordinaten) des oberen Registerkartenbereichs, wenn die Funktion zurückkehrt.

*rectTabAreaBottom*<br/>
[out] Enthält die Größe und Position (in den Clientkoordinaten) des unteren Tabstoppbereichs, wenn die Funktion zurückkehrt.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, um den Typ des Andockens an den Zielbereich zu bestimmen. Wenn das Framework feststellt, dass der Benutzer den Bereich zieht, der über den Registerkartenbereich des Zielbereichs angedockt werden soll, versucht es, den ersten Bereich als neue Registerkarte des Zielbereichs hinzuzufügen. Andernfalls wird versucht, den ersten Bereich an einer entsprechenden Seite des Zielbereichs anzudocken. Das Framework erstellt einen neuen Container mit einem Schieberegler, um den zusätzlichen angedockten Bereich aufzunehmen.

Die Standardimplementierung `GetTabArea` von gibt den gesamten Clientbereich der Outlook-Leiste zurück, wenn die Outlook-Leiste statisch ist. das heißt, wenn die Outlook-Leiste nicht schweben kann. Andernfalls wird der Bereich zurückgegeben, den Seitenschaltflächen am oberen und unteren Rand des Outlook-Leistensteuerelements einnehmen.

Überschreiben Sie diese Methode `CMFCOutlookBar` in der Klasse, von der abgeleitet wird, um dieses Verhalten zu ändern.

## <a name="cmfcoutlookbarismode2003"></a><a name="ismode2003"></a>CMFCOutlookBar::IsMode2003

Gibt an, ob das Verhalten der Outlook-Leiste mit dem von Microsoft Office Outlook 2003 imitiert.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Outlook-Leiste im Microsoft Office 2003-Modus ausgeführt wird. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können diesen Modus aktivieren, indem Sie [CMFCOutlookBar::SetMode2003](#setmode2003)verwenden.

## <a name="cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation

Wird von [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) aufgerufen, nachdem die aktive Registerkarte mithilfe von Animationen festgelegt wurde.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Parameter

*nPage*<br/>
[in] Der nullbasierte Index der Registerkarte, der aktiviert wurde.

### <a name="remarks"></a>Bemerkungen

Der visuelle Effekt des Festlegens der aktiven Registerkarte hängt davon ab, ob Sie die Animation aktiviert haben. Weitere Informationen finden Sie unter [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

## <a name="cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation

Wird von [CMFCOutlookBarTabCtrl::SetActiveTab aufgerufen,](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) bevor eine Registerkarte mithilfe der Animation als aktive Registerkarte festgelegt wird.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Parameter

*nPage*<br/>
[in] Der nullbasierte Index der Registerkarte, die gerade aktiv eingestellt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn Animation zum Festlegen der neuen aktiven Registerkarte verwendet werden soll, oder FALSE, wenn die Animation deaktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcoutlookbaronscroll"></a><a name="onscroll"></a>CMFCOutlookBar::OnScroll

Wird vom Framework aufgerufen, wenn die Outlook-Leiste nach oben oder unten scrollt.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Parameter

*bDown*<br/>
[in] TRUE, wenn die Outlook-Leiste nach unten scrollt, oder FALSE, wenn sie nach oben scrollt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a>CMFCOutlookBar::RemoveCustomPage

Entfernt eine benutzerdefinierte Outlook-Leiste-Registerkarte.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Parameter

*uiPage*<br/>
[in] Nullbasierter Index der Seite im übergeordneten Outlook-Fenster.

*pTargetWnd*<br/>
[in] Zeigen Sie auf das übergeordnete Outlook-Fenster.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die benutzerdefinierte Seite erfolgreich entfernt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um benutzerdefinierte Seiten zu löschen. Wenn die Seite entfernt wird, wird ihre Steuerelement-ID an den Pool verfügbarer IDs zurückgegeben.

Sie müssen einen Zeiger auf das [CMFCOutlookBarTabCtrl-Klassenobjekt](../../mfc/reference/cmfcoutlookbartabctrl-class.md) bereitstellen, in dem sich die zu entfernende Seite derzeit befindet. Beachten Sie, dass ein Benutzer abnehmbare Seiten zwischen verschiedenen Outlook-Leisten verschieben kann, aber die Informationen über eine benutzerdefinierte Seite befinden sich im Outlook-Leiste-Objekt, für das Sie [CMFCOutlookBar::CreateCustomPage](#createcustompage)aufgerufen haben.

Verwenden Sie [CBaseTabbedPane::GetUnderlyingWindow,](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) um einen Zeiger auf das Outlook-Fenster abzuverweisen.

## <a name="cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont

Legt die Schriftart des Textes auf den Schaltflächen der Outlook-Leiste fest.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parameter

*pFont*<br/>
[in] Gibt die neue Schriftart an.

*bZeichnung*<br/>
[in] Wenn TRUE, wird die Outlook-Leiste neu gezeichnet.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um eine Schriftart für den Text festzulegen, der auf den Schaltflächen auf der Registerkarte Outlook angezeigt wird.

## <a name="cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a>CMFCOutlookBar::SetMode2003

Gibt an, ob das Verhalten der Outlook-Leiste mit dem von Outlook 2003 imitiert.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Parameter

*bMode2003*<br/>
[in] Wenn TRUE, ist der Office 2003-Modus aktiviert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um den Office 2003-Modus zu aktivieren oder zu deaktivieren. In diesem Modus verfügt die Outlook-Leiste über eine zusätzliche Symbolleiste mit einer Anpassungsschaltfläche. Das Verhalten der Outlook-Leiste entspricht dem Verhalten der Outlook-Leiste in Microsoft Office 2003.

Standardmäßig ist dieser Modus deaktiviert.

> [!NOTE]
> Diese Funktion muss vor [CMFCOutlookBar::Create](#create)aufgerufen werden.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane-Klasse](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl-Klasse](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane-Klasse](../../mfc/reference/cmfcoutlookbarpane-class.md)
