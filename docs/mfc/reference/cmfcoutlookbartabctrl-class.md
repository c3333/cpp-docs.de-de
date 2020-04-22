---
title: CMFCOutlookBarTabCtrl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: 9c5d7d5135c3b207bbf113970deb8cbeb186bcca
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749566"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

Ein Registerkarten-Steuerelement mit dem Aussehen des **Navigationsbereichs** in Microsoft Outlook verfügt.
Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Der Standardkonstruktor.|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Fügt ein Windows-Steuerelement als neue Registerkarte in der Outlook-Leiste hinzu.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Wird vom Framework aufgerufen, um die Dimensionen des Bearbeitungsfelds zu bestimmen, `CMFCBaseTabCtrl::CalcRectEdit`das angezeigt wird, wenn ein Benutzer eine Registerkarte umbenennt. (Überschreibt .)|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Wird vom Framework während der Größenänderungsvorgänge aufgerufen, um festzustellen, ob weniger Outlook-Registerkartenschaltflächen angezeigt werden können, als derzeit sichtbar sind.|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Wird vom Framework während der Größenänderungsvorgänge aufgerufen, um zu bestimmen, ob mehr Outlook-Leiste-Registerkartenschaltflächen angezeigt werden können, als derzeit sichtbar sind.|
|[CMFCOutlookBarTabCtrl::Erstellen](#create)|Erstellt das Outlook-Leisten-Registerkartensteuerelement.|
|`CMFCOutlookBarTabCtrl::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Gibt an, ob die Animation, die während des Wechsels zwischen aktiven Registerkarten auftritt, aktiviert ist.|
|[CMFCOutlookBarTabCtrl::EnableInPlaceBearbeiten](#enableinplaceedit)|Gibt an, ob ein Benutzer die Textbeschriftungen auf den Registerkartenschaltflächen der Outlook-Leiste ändern kann. (Überschreibt [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Wird vom Framework aufgerufen, um Schaltflächen zu aktivieren, mit denen der Benutzer im Outlook-Leistenbereich durch Schaltflächen scrollen kann.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identifiziert den Bereich, der einen angegebenen Punkt enthält. (Überschreibt [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Gibt die Rahmengröße des Outlook-Registerkartensteuerelements zurück.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|Ruft die Größe und Position des Tabstoppbereichs des Registerkartensteuerelements ab. (Überschreibt [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Bestimmt, ob die Animation aktiviert ist, die während des Wechsels zwischen aktiven Registerkarten auftritt.|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Bestimmt, ob sich das Outlook-Leisten-Registerkartensteuerelement in einem Modus befindet, der Microsoft Outlook 2003 emuliert.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Bestimmt, ob sich ein Punkt innerhalb des Registerkartenbereichs befindet. (Überschreibt [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Bestimmt, ob eine Registerkarte abnehmbar ist. (Überschreibt [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Wird vom Framework aufgerufen, wenn eine Registerkarte eingefügt oder entfernt wird. (Überschreibt `CMFCBaseTabCtrl::OnChangeTabs`.)|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Wird vom Framework aufgerufen, um die Anzahl der sichtbaren Schaltflächen auf der Registerkarte zu verringern.|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Wird vom Framework aufgerufen, um die Anzahl der sichtbaren Schaltflächen auf der Registerkarte zu erhöhen.|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Zeigt das Dialogfeld **Navigationsbereichsoptionen an.**|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Berechnet das interne Layout des Registerkartensteuerelements neu. (Überschreibt [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Legt die aktive Registerkarte fest. (Überschreibt [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Legt die Rahmengröße des Outlook-Registerkartensteuerelements fest.|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Legt die Ausrichtung der Textbeschriftungen auf den Registerkartenschaltflächen der Outlook-Leiste fest.|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Legt die Bitmap fest, die die Symbole enthält, die am unteren Rand der Outlook-Leiste im Outlook 2003-Modus angezeigt werden (siehe [CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md)).|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Bemerkungen

Um eine Outlook-Leiste mit Dockingunterstützung `CMFCOutlookBar` zu erstellen, verwenden Sie ein Objekt, um das Outlook-Leisten-Registerkartensteuerelement zu hosten. Weitere Informationen finden Sie unter [CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie `CMFCOutlookBarTabCtrl` ein `CMFCOutlookBarTabCtrl` Objekt initialisieren und verschiedene Methoden in der Klasse verwenden. Das Beispiel zeigt, wie Sie die ortsnahe Bearbeitung der Textbeschriftung auf den Schaltflächen auf der Registerkarte der Outlook-Leiste aktivieren, die Animation aktivieren, Bildlauf-Handles aktivieren, mit denen der Benutzer durch Schaltflächen im Outlook-Leistenbereich scrollen kann, die Rahmengröße des Outlook-Registerkartensteuerelements festlegen und die Ausrichtung der Textbeschriftungen auf den Registerkartenschaltflächen der Outlook-Leiste festlegen. Dieser Codeausschnitt ist Teil des [Outlook-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxoutlookbartabctrl.h

## <a name="cmfcoutlookbartabctrladdcontrol"></a><a name="addcontrol"></a>CMFCOutlookBarTabCtrl::AddControl

Fügt ein Windows-Steuerelement als neue Registerkarte in der Outlook-Leiste hinzu.

```cpp
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>Parameter

*pWndCtrl*<br/>
[in] Ein Zeiger auf ein hinzuzufügendes Steuerelement.

*lpszName*<br/>
[in] Gibt den Namen der Registerkarte an.

*bAbnehmbar*<br/>
[in] Wenn TRUE, wird die Seite als abnehmbar erstellt.

*nImageID*<br/>
[in] Bildindex in der internen Bildliste für das Bild, das auf der neuen Registerkarte angezeigt werden soll.

*dwControlBarStyle*<br/>
[in] Gibt den AFX_ CBRS_*-Stil für umschlossene Dockingbereiche an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um ein Steuerelement als neue Seite einer Outlookleiste hinzuzufügen.

Diese Funktion ruft intern [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)auf.

Wenn Sie *bDetachable* auf `AddControl` TRUE `CDockablePaneAdapter` setzen, erstellt intern ein Objekt und umschließt das hinzugefügte Steuerelement. Die Laufzeitklasse des Registerkartenfensters wird automatisch auf `CMFCOutlookBar` die Laufzeitklasse von und die `CMultiPaneFrameWnd`Laufzeitklasse des unverankerten Frames auf festgelegt.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `AddControl` veranschaulicht, `CMFCOutlookBarTabCtrl` wie die Methode in der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [Outlook-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

## <a name="cmfcoutlookbartabctrlcanshowfewerpagebuttons"></a><a name="canshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

Wird vom Framework während der Größenänderungsvorgänge aufgerufen, um zu bestimmen, ob weniger Outlook-Registerkartenschaltflächen angezeigt werden können, als derzeit sichtbar sind.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn mehr als eine Schaltfläche vorhanden ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Das Outlook-Leisten-Registerkartensteuerelement fügt Registerkarten dynamisch hinzu oder entfernt sie aus der Anzeige, je nachdem, wie viel Platz verfügbar ist. Diese Methode wird vom Framework verwendet, um diesen Prozess zu unterstützen.

## <a name="cmfcoutlookbartabctrlcanshowmorepagebuttons"></a><a name="canshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowMorePageButtons

Wird vom Framework während der Größenänderungsvorgänge aufgerufen, um zu bestimmen, ob mehr Outlook-Leiste-Registerkartenschaltflächen angezeigt werden können, als derzeit sichtbar sind.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn es Schaltflächen gibt, die derzeit nicht sichtbar sind; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Das Outlook-Leisten-Registerkartensteuerelement fügt Registerkarten dynamisch hinzu oder entfernt sie aus der Anzeige, je nachdem, wie viel Platz verfügbar ist. Diese Methode wird vom Framework verwendet, um diesen Prozess zu unterstützen.

## <a name="cmfcoutlookbartabctrlcreate"></a><a name="create"></a>CMFCOutlookBarTabCtrl::Erstellen

Erstellt das Outlook-Leisten-Registerkartensteuerelement.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Gibt die Anfangsgröße und -position in Pixel an.

*pParentWnd*<br/>
[in] Zeigt auf das übergeordnete Fenster. Darf nicht NULL sein.

*nID*<br/>
[in] Die Steuerelement-ID.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Steuerelement erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Normalerweise werden Outlook-Bar-Registerkartensteuerelemente erstellt, wenn [die CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md) die WM_CREATE Meldung des Prozesses steuert.

## <a name="cmfcoutlookbartabctrlenableanimation"></a><a name="enableanimation"></a>CMFCOutlookBarTabCtrl::EnableAnimation

Gibt an, ob die Animation, die während des Wechsels zwischen aktiven Registerkarten auftritt, aktiviert ist.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] Gibt an, ob die Animation aktiviert oder deaktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um Animationen zu aktivieren und zu deaktivieren. Wenn der Benutzer eine Registerkarte öffnet, wird die Beschriftung der Seite nach oben oder unten gegleitet, wenn die Animation aktiviert ist. Wenn die Animation deaktiviert ist, wird die Seite sofort aktiv.

Standardmäßig ist die Animation aktiviert.

## <a name="cmfcoutlookbartabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCOutlookBarTabCtrl::EnableInPlaceBearbeiten

Gibt an, ob ein Benutzer die Textbeschriftungen auf den Schaltflächen auf der Registerkarte der Outlook-Leiste ändern kann.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
Wenn TRUE, aktivieren Sie die ortsspezifische Bearbeitung der Textbeschriftung. Wenn FALSE, deaktivieren Sie die an Ort und Stelle Bearbeiten.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die ortsnahe Bearbeitung von Textbeschriftungen auf Schaltflächen auf der Registerkarte zu aktivieren oder zu deaktivieren. Standardmäßig ist die ortsbezogene Bearbeitung deaktiviert.

## <a name="cmfcoutlookbartabctrlenablescrollbuttons"></a><a name="enablescrollbuttons"></a>CMFCOutlookBarTabCtrl::EnableScrollButtons

Wird vom Framework aufgerufen, um Bildlaufhandles zu aktivieren, mit denen der Benutzer durch Schaltflächen im Outlook-Leistenbereich scrollen kann.

```cpp
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] Legt fest, ob die Bildlaufschaltflächen angezeigt werden.

*bIsUp*<br/>
[in] Legt fest, ob die obere Bildlaufleiste angezeigt wird.

*bIsDown*<br/>
[in] Bestimmt, ob die untere Bildlaufleiste angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Aktiviert die Anzeige der Bildlaufschaltflächen. Diese Methode wird vom Framework aufgerufen, wenn sich die aktive Registerkarte ändert, um die Bildlaufschaltflächen wiederherzustellen.

## <a name="cmfcoutlookbartabctrlgetbordersize"></a><a name="getbordersize"></a>CMFCOutlookBarTabCtrl::GetBorderSize

Gibt die Rahmengröße des Outlook-Registerkartensteuerelements zurück.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Rahmengröße in Pixel.

## <a name="cmfcoutlookbartabctrlgetvisiblepagebuttons"></a><a name="getvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcoutlookbartabctrlisanimation"></a><a name="isanimation"></a>CMFCOutlookBarTabCtrl::IsAnimation

Gibt an, ob die Animation, die während des Wechsels zwischen aktiven Registerkarten auftritt, aktiviert ist.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Animation aktiviert ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie die [Funktion CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) auf, um Animationen zu aktivieren oder zu deaktivieren.

## <a name="cmfcoutlookbartabctrlismode2003"></a><a name="ismode2003"></a>CMFCOutlookBarTabCtrl::IsMode2003

Bestimmt, ob sich das Outlook-Leisten-Registerkartensteuerelement in einem Modus befindet, der Microsoft Outlook 2003 emuliert.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich das Outlook-Leisten-Registerkartensteuerelement im Outlook 2003-Modus befindet; andernfalls FALSE;

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird durch [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003)festgelegt.

## <a name="cmfcoutlookbartabctrlonshowfewerpagebuttons"></a><a name="onshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

Wird vom Framework aufgerufen, um die Anzahl der sichtbaren Schaltflächen auf der Registerkarte zu verringern.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode passt die Anzahl der sichtbaren Seitenregisterkartenschaltflächen an, wenn die Größe des Steuerelements geändert wird.

## <a name="cmfcoutlookbartabctrlonshowmorepagebuttons"></a><a name="onshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowMorePageButtons

Wird vom Framework aufgerufen, um die Anzahl der sichtbaren Schaltflächen auf der Registerkarte zu erhöhen.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode passt die Anzahl der Schaltflächen auf der Registerkarte an, die sichtbar sind, wenn die Größe des Steuerelements geändert wird.

## <a name="cmfcoutlookbartabctrlonshowoptions"></a><a name="onshowoptions"></a>CMFCOutlookBarTabCtrl::OnShowOptions

Zeigt das Dialogfeld **Navigationsbereichsoptionen an.**

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Bemerkungen

Im Dialogfeld **Navigationsbereichoptionen** kann der Benutzer auswählen, welche Schaltflächen auf der Registerkarte angezeigt werden sollen und in welcher Reihenfolge sie angezeigt werden.

Diese Methode wird vom Framework aufgerufen, wenn der Benutzer das Menüelement **Navigationsbereichsoptionen** aus dem Anpassungsmenü des Steuerelements auswählt.

## <a name="cmfcoutlookbartabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCOutlookBarTabCtrl::SetActiveTab

Legt die aktive Registerkarte fest. Die aktive Registerkarte ist geöffnet, wobei ihr Inhalt sichtbar ist.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>Parameter

*Itab*<br/>
[in] Der nullbasierte Index einer zu öffnenden Registerkarte.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die angegebene Registerkarte erfolgreich geöffnet wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der visuelle Effekt des Festlegens der aktiven Registerkarte hängt davon ab, ob Sie die Animation aktiviert haben. Weitere Informationen finden Sie unter [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).

## <a name="cmfcoutlookbartabctrlsetbordersize"></a><a name="setbordersize"></a>CMFCOutlookBarTabCtrl::SetBorderSize

Legt die Rahmengröße des Outlook-Registerkartensteuerelements fest.

```cpp
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>Parameter

*nBorderSize*<br/>
[in] Gibt die neue Rahmengröße in Pixel an.

### <a name="remarks"></a>Bemerkungen

Legt die neue Rahmengröße fest und berechnet das Outlook-Fensterlayout neu.

## <a name="cmfcoutlookbartabctrlsetpagebuttontextalign"></a><a name="setpagebuttontextalign"></a>CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

Legt die Ausrichtung der Textbeschriftungen auf den Registerkartenschaltflächen der Outlook-Leiste fest.

```cpp
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parameter

*uiAlign*<br/>
[in] Gibt die Textausrichtung an.

*bZeichnung*<br/>
[in] Wenn TRUE, wird das Outlook-Fenster neu gezeichnet.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um die Textausrichtung für Seitenschaltflächen zu ändern.

*uiAlign* kann einer der folgenden Werte sein:

|Konstante|Bedeutung|
|--------------|-------------|
|TA_LEFT|Linke Ausrichtung|
|TA_CENTER|Mittelausrichtung|
|TA_RIGHT|Rechte Ausrichtung|

Der Standardwert ist TA_CENTER.

## <a name="cmfcoutlookbartabctrlsettoolbarimagelist"></a><a name="settoolbarimagelist"></a>CMFCOutlookBarTabCtrl::SetToolbarImageList

Legt die Bitmap fest, die die Symbole enthält, die unten in der Outlook-Leiste im Outlook 2003-Modus angezeigt werden.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>Parameter

*uiID*<br/>
[in] Gibt die Ressourcen-ID des zu ladenden Bildes an.

*Cx*<br/>
[in] Gibt die Breite eines Bildes in der Bildliste in Pixel an.

*clrTransp*<br/>
[in] Ein RGB-Wert, der die transparente Farbe angibt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn erfolgreich; andernfalls gibt FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um eine Bildliste anzuhängen, deren Bilder auf Symbolleistenschaltflächen im Microsoft Office 2003-Modus angezeigt werden. Bildindizes sollten Seitenindizes entsprechen.

Diese Methode sollte nicht aufgerufen werden, wenn sie nicht im Microsoft Office 2003-Modus ist. Weitere Informationen finden Sie unter [CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="cmfcoutlookbartabctrlsetvisiblepagebuttons"></a><a name="setvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```cpp
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>Parameter

[in] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane-Klasse](../../mfc/reference/cmfcoutlookbarpane-class.md)
