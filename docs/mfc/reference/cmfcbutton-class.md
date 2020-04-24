---
title: CMFCButton-Klasse
ms.date: 08/28/2018
f1_keywords:
- CMFCButton
- AFXBUTTON/CMFCButton
- AFXBUTTON/CMFCButton::CleanUp
- AFXBUTTON/CMFCButton::EnableFullTextTooltip
- AFXBUTTON/CMFCButton::EnableMenuFont
- AFXBUTTON/CMFCButton::EnableWindowsTheming
- AFXBUTTON/CMFCButton::GetToolTipCtrl
- AFXBUTTON/CMFCButton::IsAutoCheck
- AFXBUTTON/CMFCButton::IsAutorepeatCommandMode
- AFXBUTTON/CMFCButton::IsCheckBox
- AFXBUTTON/CMFCButton::IsChecked
- AFXBUTTON/CMFCButton::IsHighlighted
- AFXBUTTON/CMFCButton::IsPressed
- AFXBUTTON/CMFCButton::IsPushed
- AFXBUTTON/CMFCButton::IsRadioButton
- AFXBUTTON/CMFCButton::IsWindowsThemingEnabled
- AFXBUTTON/CMFCButton::SetAutorepeatMode
- AFXBUTTON/CMFCButton::SetCheckedImage
- AFXBUTTON/CMFCButton::SetFaceColor
- AFXBUTTON/CMFCButton::SetImage
- AFXBUTTON/CMFCButton::SetMouseCursor
- AFXBUTTON/CMFCButton::SetMouseCursorHand
- AFXBUTTON/CMFCButton::SetStdImage
- AFXBUTTON/CMFCButton::SetTextColor
- AFXBUTTON/CMFCButton::SetTextHotColor
- AFXBUTTON/CMFCButton::SetTooltip
- AFXBUTTON/CMFCButton::SizeToContent
- AFXBUTTON/CMFCButton::OnDraw
- AFXBUTTON/CMFCButton::OnDrawBorder
- AFXBUTTON/CMFCButton::OnDrawFocusRect
- AFXBUTTON/CMFCButton::OnDrawText
- AFXBUTTON/CMFCButton::OnFillBackground
- AFXBUTTON/CMFCButton::SelectFont
- AFXBUTTON/CMFCButton::m_bDrawFocus
- AFXBUTTON/CMFCButton::m_bHighlightChecked
- AFXBUTTON/CMFCButton::m_bRightImage
- AFXBUTTON/CMFCButton::m_bTransparent
- AFXBUTTON/CMFCButton::m_nAlignStyle
- AFXBUTTON/CMFCButton::m_nFlatStyle
helpviewer_keywords:
- CMFCButton [MFC], CleanUp
- CMFCButton [MFC], EnableFullTextTooltip
- CMFCButton [MFC], EnableMenuFont
- CMFCButton [MFC], EnableWindowsTheming
- CMFCButton [MFC], GetToolTipCtrl
- CMFCButton [MFC], IsAutoCheck
- CMFCButton [MFC], IsAutorepeatCommandMode
- CMFCButton [MFC], IsCheckBox
- CMFCButton [MFC], IsChecked
- CMFCButton [MFC], IsHighlighted
- CMFCButton [MFC], IsPressed
- CMFCButton [MFC], IsPushed
- CMFCButton [MFC], IsRadioButton
- CMFCButton [MFC], IsWindowsThemingEnabled
- CMFCButton [MFC], SetAutorepeatMode
- CMFCButton [MFC], SetCheckedImage
- CMFCButton [MFC], SetFaceColor
- CMFCButton [MFC], SetImage
- CMFCButton [MFC], SetMouseCursor
- CMFCButton [MFC], SetMouseCursorHand
- CMFCButton [MFC], SetStdImage
- CMFCButton [MFC], SetTextColor
- CMFCButton [MFC], SetTextHotColor
- CMFCButton [MFC], SetTooltip
- CMFCButton [MFC], SizeToContent
- CMFCButton [MFC], OnDraw
- CMFCButton [MFC], OnDrawBorder
- CMFCButton [MFC], OnDrawFocusRect
- CMFCButton [MFC], OnDrawText
- CMFCButton [MFC], OnFillBackground
- CMFCButton [MFC], SelectFont
- CMFCButton [MFC], m_bDrawFocus
- CMFCButton [MFC], m_bHighlightChecked
- CMFCButton [MFC], m_bRightImage
- CMFCButton [MFC], m_bTransparent
- CMFCButton [MFC], m_nAlignStyle
- CMFCButton [MFC], m_nFlatStyle
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
ms.openlocfilehash: e949feaaac3570e1518cfb488cc1c42a471a1c46
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754873"
---
# <a name="cmfcbutton-class"></a>CMFCButton-Klasse

Die `CMFCButton` Klasse fügt der [CButton-Klasse](../../mfc/reference/cbutton-class.md) Funktionen hinzu, z. B. das Ausrichten von Schaltflächentext, das Kombinieren von Schaltflächentext und einem Bild, das Auswählen eines Cursors und das Angeben einer QuickInfo.

## <a name="syntax"></a>Syntax

```
class CMFCButton : public CButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCButton::CMFCButton`|Der Standardkonstruktor.|
|`CMFCButton::~CMFCButton`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCButton::CleanUp](#cleanup)|Setzt interne Variablen zurück und gibt zugewiesene Ressourcen wie Bilder, Bitmaps und Symbole frei.|
|`CMFCButton::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCButton::DrawItem`|Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt einer vom Besitzer gezeichneten Schaltfläche geändert hat. (Überschreibt [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Gibt an, ob der Volltext einer QuickInfo in einem großen QuickInfo-Fenster oder eine abgeschnittene Version des Textes in einem kleinen QuickInfo-Fenster angezeigt werden soll.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Gibt an, ob die Schriftart des Schaltflächentexts mit der Schriftart des Anwendungsmenüs identisch ist.|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Gibt an, ob der Stil des Schaltflächenrahmens dem aktuellen Windows-Design entspricht.|
|`CMFCButton::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Gibt einen Verweis auf das zugrunde liegende QuickInfo-Steuerelement zurück.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Gibt an, ob es sich bei einem Kontrollkästchen oder Optionsfeld um eine automatische Schaltfläche handelt.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Gibt an, ob eine Schaltfläche auf den Automatischen Wiederholmodus eingestellt ist.|
|[CMFCButton::IsCheckBox](#ischeckbox)|Gibt an, ob es sich bei einer Schaltfläche um eine Kontrollkästchen-Schaltfläche handelt.|
|[CMFCButton::IsChecked](#ischecked)|Gibt an, ob die aktuelle Schaltfläche aktiviert ist.|
|[CMFCButton::Hervorgehoben](#ishighlighted)|Gibt an, ob eine Schaltfläche hervorgehoben ist.|
|[CMFCButton::IsPressed](#ispressed)|Gibt an, ob eine Schaltfläche gedrückt und hervorgehoben wird.|
|[CMFCButton::IsPushed](#ispushed)|Gibt an, ob eine Taste gedrückt wird.|
|[CMFCButton::IsRadioButton](#isradiobutton)|Gibt an, ob es sich bei einer Schaltfläche um ein Optionsfeld handelt.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Gibt an, ob der Stil des Schaltflächenrahmens dem aktuellen Windows-Design entspricht.|
|`CMFCButton::OnDrawParentBackground`|Zeichnet den Hintergrund des übergeordneten Zeichens einer Schaltfläche im angegebenen Bereich. (Überschreibt [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Übersetzt Fensternachrichten, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. (Überschreibt [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Legt eine Schaltfläche auf Auto-Repeat-Modus fest.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Legt das Bild für eine aktivierte Schaltfläche fest.|
|[CMFCButton::SetFaceColor](#setfacecolor)|Legt die Hintergrundfarbe für den Schaltflächentext fest.|
|[CMFCButton::SetImage](#setimage)|Legt das Bild für eine Schaltfläche fest.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Legt das Cursorbild fest.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Legt den Cursor auf das Bild einer Hand fest.|
|[CMFCButton::SetStdImage](#setstdimage)|Verwendet `CMenuImages` ein Objekt, um das Schaltflächenbild festzulegen.|
|[CMFCButton::SetTextColor](#settextcolor)|Legt die Farbe des Schaltflächentexts für eine Schaltfläche fest, die nicht ausgewählt ist.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Legt die Farbe des Schaltflächentexts für eine ausgewählte Schaltfläche fest.|
|[CMFCButton::SetTooltip](#settooltip)|Ordnet eine QuickInfo einer Schaltfläche zu.|
|[CMFCButton::SizeToContent](#sizetocontent)|Ändert die Größe einer Schaltfläche so, dass sie den Text und das Bild der Schaltfläche enthält.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCButton::OnDraw](#ondraw)|Wird vom Framework aufgerufen, um eine Schaltfläche zu zeichnen.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Wird vom Framework aufgerufen, um den Rahmen eines Buttons zu zeichnen.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Wird vom Framework aufgerufen, um das Fokusrechteck für eine Schaltfläche zu zeichnen.|
|[CMFCButton::OnDrawText](#ondrawtext)|Wird vom Framework aufgerufen, um den Schaltflächentext zu zeichnen.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Wird vom Framework aufgerufen, um den Hintergrund des Schaltflächentexts zu zeichnen.|
|[CMFCButton::SelectFont](#selectfont)|Ruft die Schriftart ab, die dem angegebenen Gerätekontext zugeordnet ist.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Gibt die Ausrichtung des Schaltflächentexts an.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Gibt an, ob Windows XP-Designs verwendet werden sollen.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Gibt an, ob ein Fokusrechteck um eine Schaltfläche gezeichnet werden soll.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Gibt den Stil der Schaltfläche an, z. B. randlos, flach, halbflach oder 3D.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|Wenn TRUE, kann eine deaktivierte Schaltfläche als abgeblendet gezeichnet werden.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Gibt an, ob eine Schaltfläche im BS_CHECKBOX-Stil hervorgehoben werden soll, wenn der Cursor darüber zeigt.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Gibt an, ob auf Button-Down-Ereignisse reagiert werden soll.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Gibt an, ob ein Bild auf der rechten Seite der Schaltfläche angezeigt werden soll.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Gibt an, ob sich das Bild oben auf der Schaltfläche befindet.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Gibt an, ob die Schaltfläche transparent ist.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Gibt an, ob das letzte Klickereignis ein Doppelklick war.|

## <a name="remarks"></a>Bemerkungen

Andere Arten von Schaltflächen `CMFCButton` werden von der Klasse abgeleitet, z. B. die `CMFCColorButton` [CMFCURLLinkButton-Klasse,](../../mfc/reference/cmfclinkctrl-class.md) die Hyperlinks unterstützt, und die Klasse, die ein Dialogfeld für die Farbauswahl unterstützt.

Der Stil `CMFCButton` eines Objekts kann *3D,* *flach,* *halbflach* oder *ohne Rahmen*sein. Schaltflächentext kann links, oben oder in der Mitte einer Schaltfläche ausgerichtet werden. Zur Laufzeit können Sie steuern, ob die Schaltfläche Text, ein Bild oder Text und ein Bild anzeigt. Sie können auch angeben, dass ein bestimmtes Cursorbild angezeigt wird, wenn der Cursor über eine Schaltfläche zeigt.

Erstellen Sie ein Schaltflächensteuerelement entweder direkt im Code oder mithilfe des **Tools MFC-Klassen-Assistent** und einer Dialogfeldvorlage. Wenn Sie ein Schaltflächensteuerelement `CMFCButton` direkt erstellen, fügen Sie der Anwendung `Create` eine `CMFCButton` Variable hinzu, und rufen Sie dann den Konstruktor und die Methoden des Objekts auf. Wenn Sie den **MFC-Klassen-Assistenten**verwenden, fügen Sie ihrer Anwendung `CButton` eine `CButton` `CMFCButton`Variable hinzu, und ändern Sie dann den Typ der Variablen von in .

Um Benachrichtigungen in einer Dialogfeldanwendung zu behandeln, fügen Sie für jede Benachrichtigung einen Meldungszuordnungseintrag und einen Ereignishandler hinzu. Die von einem `CMFCButton` Objekt gesendeten Benachrichtigungen entsprechen `CButton` denen, die von einem Objekt gesendet werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die Eigenschaften der `CMFCButton` Schaltfläche mithilfe verschiedener Methoden in der Klasse konfiguriert werden. Das Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxbutton.h

## <a name="cmfcbuttoncleanup"></a><a name="cleanup"></a>CMFCButton::CleanUp

Setzt interne Variablen zurück und gibt zugewiesene Ressourcen wie Bilder, Bitmaps und Symbole frei.

```
virtual void CleanUp();
```

## <a name="cmfcbuttonenablefulltexttooltip"></a><a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip

Gibt an, ob der Volltext einer QuickInfo in einem großen QuickInfo-Fenster oder eine abgeschnittene Version des Textes in einem kleinen QuickInfo-Fenster angezeigt werden soll.

```cpp
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Parameter

*Bon*<br/>
[in] TRUE, um den gesamten Text anzuzeigen; FALSE, um abgeschnittenen Text anzuzeigen.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonenablemenufont"></a><a name="enablemenufont"></a>CMFCButton::EnableMenuFont

Gibt an, ob die Schriftart des Schaltflächentexts mit der Schriftart des Anwendungsmenüs identisch ist.

```cpp
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parameter

*Bon*<br/>
[in] TRUE, um die Schriftart des Anwendungsmenüs als Schaltflächentextschriftart zu verwenden; FALSE, um die Systemschriftart zu verwenden. Der Standardwert ist TRUE.

*bZeichnung*<br/>
[in] TRUE, um den Bildschirm sofort neu zu zeichnen; andernfalls FALSE. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Methode nicht verwenden, um die Schriftart "Schaltflächentext" anzugeben, können Sie die Schriftart mit der [CWnd::SetFont-Methode](../../mfc/reference/cwnd-class.md#setfont) angeben. Wenn Sie überhaupt keine Schriftart angeben, legt das Framework eine Standardschriftart fest.

## <a name="cmfcbuttonenablewindowstheming"></a><a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming

Gibt an, ob der Stil des Schaltflächenrahmens dem aktuellen Windows-Design entspricht.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um das aktuelle Windows-Design zum Zeichnen von Schaltflächenrahmen zu verwenden; FALSE, um das Windows-Design nicht zu verwenden. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Diese Methode wirkt sich auf alle Schaltflächen in der Anwendung aus, die von der `CMFCButton` Klasse abgeleitet sind.

## <a name="cmfcbuttongettooltipctrl"></a><a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl

Gibt einen Verweis auf das zugrunde liegende QuickInfo-Steuerelement zurück.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das zugrunde liegende QuickInfo-Steuerelement.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonisautocheck"></a><a name="isautocheck"></a>CMFCButton::IsAutoCheck

Gibt an, ob es sich bei einem Kontrollkästchen oder Optionsfeld um eine automatische Schaltfläche handelt.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltfläche Stil BS_AUTOCHECKBOX oder BS_AUTORADIOBUTTON hat; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonisautorepeatcommandmode"></a><a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

Gibt an, ob eine Schaltfläche auf den Automatischen Wiederholmodus eingestellt ist.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltfläche auf den Auto-Repeat-Modus eingestellt ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CMFCButton::SetAutorepeatMode-Methode,](#setautorepeatmode) um eine Schaltfläche auf den Auto-Repeat-Modus einzustellen.

## <a name="cmfcbuttonischeckbox"></a><a name="ischeckbox"></a>CMFCButton::IsCheckBox

Gibt an, ob es sich bei einer Schaltfläche um eine Kontrollkästchen-Schaltfläche handelt.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltfläche entweder BS_CHECKBOX oder BS_AUTOCHECKBOX Stil hat; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonischecked"></a><a name="ischecked"></a>CMFCButton::IsChecked

Gibt an, ob die aktuelle Schaltfläche aktiviert ist.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die aktuelle Schaltfläche aktiviert ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Das Framework verwendet verschiedene Möglichkeiten, um anzuzeigen, dass verschiedene Arten von Schaltflächen überprüft werden. Beispielsweise wird ein Optionsfeld überprüft, wenn es einen Punkt enthält. ein Kontrollkästchen wird aktiviert, wenn es ein **X**enthält.

## <a name="cmfcbuttonishighlighted"></a><a name="ishighlighted"></a>CMFCButton::Hervorgehoben

Gibt an, ob eine Schaltfläche hervorgehoben ist.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltfläche hervorgehoben ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Eine Schaltfläche wird hervorgehoben, wenn die Maus über die Schaltfläche zeigt.

## <a name="cmfcbuttonispressed"></a><a name="ispressed"></a>CMFCButton::IsPressed

Gibt an, ob eine Schaltfläche gedrückt und hervorgehoben wird.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Taste gedrückt wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonispushed"></a><a name="ispushed"></a>CMFCButton::IsPushed

Gibt an, ob eine Taste gedrückt wird.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Taste gedrückt wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonisradiobutton"></a><a name="isradiobutton"></a>CMFCButton::IsRadioButton

Gibt an, ob es sich bei einer Schaltfläche um ein Optionsfeld handelt.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Schaltflächenstil BS_RADIOBUTTON oder BS_AUTORADIOBUTTON ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttoniswindowsthemingenabled"></a><a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled

Gibt an, ob der Stil des Schaltflächenrahmens dem aktuellen Windows-Design entspricht.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Stil des Schaltflächenrahmens dem aktuellen Windows-Design entspricht; andernfalls FALSE.

## <a name="cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton::m_bDontUseWinXPTheme

Gibt an, ob Windows XP-Designs beim Zeichnen der Schaltfläche verwendet werden sollen.

```
BOOL m_bDontUseWinXPTheme;
```

## <a name="cmfcbuttonm_bdrawfocus"></a><a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus

Gibt an, ob ein Fokusrechteck um eine Schaltfläche gezeichnet werden soll.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Bemerkungen

Legen `m_bDrawFocus` Sie das Element auf TRUE fest, um anzugeben, dass das Framework ein Fokusrechteck um den Text und das Bild der Schaltfläche zeichnet, wenn die Schaltfläche den Fokus erhält.

Der `CMFCButton` Konstruktor initialisiert dieses Element in TRUE.

## <a name="cmfcbuttonm_bgraydisabled"></a><a name="m_bGrayDisabled"></a>CMFCButton::m_bGrayDisabled

Wenn TRUE, kann eine deaktivierte Schaltfläche als abgeblendet gezeichnet werden.

```
BOOL m_bGrayDisabled;
```

## <a name="cmfcbuttonm_bhighlightchecked"></a><a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked

Gibt an, ob eine Schaltfläche im BS_CHECKBOX-Stil hervorgehoben werden soll, wenn der Cursor darüber zeigt.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Bemerkungen

Legen `m_bHighlightChecked` Sie das Element auf TRUE fest, um anzugeben, dass das Framework eine Schaltfläche im BS_CHECKBOX-Stil hervorhebt, wenn die Maus darüber schwebt.

## <a name="cmfcbuttonm_bresponseonbuttondown"></a><a name="m_bResponseOnButtonDown"></a>CMFCButton::m_bResponseOnButtonDown

Gibt an, ob auf Button-Down-Ereignisse reagiert werden soll.

```
BOOL m_bResponseOnButtonDown;
```

## <a name="cmfcbuttonm_brightimage"></a><a name="m_brightimage"></a>CMFCButton::m_bRightImage

Gibt an, ob ein Bild auf der rechten Seite der Schaltfläche angezeigt werden soll.

```
BOOL m_bRightImage;
```

## <a name="cmfcbuttonm_btopimagem_btopimage"></a><a name="m_bTopImage"></a>CMFCButton::m_bTopImage](#m_bTopImage)

Gibt an, ob sich das Bild oben auf der Schaltfläche befindet.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Bemerkungen

Legen `m_bRightImage` Sie den Member auf TRUE fest, um anzugeben, dass das Framework das Bild der Schaltfläche rechts neben der Textbeschriftung der Schaltfläche anzeigt.

## <a name="cmfcbuttonm_btransparent"></a><a name="m_btransparent"></a>CMFCButton::m_bTransparent

Gibt an, ob die Schaltfläche transparent ist.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Bemerkungen

Legen `m_bTransparent` Sie den Member auf TRUE fest, um anzugeben, dass das Framework die Schaltfläche transparent macht. Der `CMFCButton` Konstruktor initialisiert diesen Member in FALSE.

## <a name="cmfcbuttonm_nalignstyle"></a><a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle

Gibt die Ausrichtung des Schaltflächentexts an.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie einen `CMFCButton::AlignStyle` der folgenden Enumerationswerte, um die Ausrichtung des Schaltflächentexts anzugeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|ALIGN_CENTER|(Standard) Richtet den Schaltflächentext an der Mitte der Schaltfläche aus.|
|ALIGN_LEFT|Richtet den Schaltflächentext an der linken Seite der Schaltfläche aus.|
|ALIGN_RIGHT|Richtet den Schaltflächentext an der rechten Seite der Schaltfläche aus.|

Der `CMFCButton` Konstruktor initialisiert diesen Member, um ALIGN_CENTER.

## <a name="cmfcbuttonm_bwasdblclkm_bwasdblclk"></a><a name="m_bWasDblClk"></a>CMFCButton::m_bWasDblClk](#m_bWasDblClk)|

Gibt an, ob das letzte Klickereignis ein Doppelklick war.|

```
BOOL m_bWasDblClk;
```

## <a name="cmfcbuttonm_nflatstyle"></a><a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle

Gibt den Stil der Schaltfläche an, z. B. randlos, flach, halbflach oder 3D.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Bemerkungen

In der folgenden `CMFCButton::m_nFlatStyle` Tabelle sind die Enumerationswerte aufgeführt, die das Erscheinungsbild einer Schaltfläche angeben.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|BUTTONSTYLE_3D|(Standard) Die Taste scheint hohe, dreidimensionale Seiten zu haben. Wenn auf die Schaltfläche geklickt wird, wird die Schaltfläche in einen tiefen Einzug gedrückt.|
|BUTTONSTYLE_FLAT|Wenn die Maus nicht über die Schaltfläche pausiert, erscheint die Schaltfläche zweidimensional und hat keine erhöhten Seiten. Wenn die Maus über die Schaltfläche angehalten wird, scheint die Schaltfläche niedrige, dreidimensionale Seiten zu haben. Wenn auf die Schaltfläche geklickt wird, wird die Schaltfläche in einen flachen Einzug gedrückt.|
|BUTTONSTYLE_SEMIFLAT|Die Schaltfläche scheint niedrige, dreidimensionale Seiten zu haben. Wenn auf die Schaltfläche geklickt wird, wird die Schaltfläche in einen tiefen Einzug gedrückt.|
|BUTTONSTYLE_NOBORDERS|Die Schaltfläche hat keine seitlichen Seiten und erscheint immer zweidimensional. Die Schaltfläche scheint nicht in einen Einzug gedrückt zu werden, wenn sie angeklickt wird.|

Der `CMFCButton` Konstruktor initialisiert diesen Member, um BUTTONSTYLE_3D.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `m_nFlatStyle` wie die `CMFCButton` Werte der Membervariablen in der Klasse festgelegt werden. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

## <a name="cmfcbuttonondraw"></a><a name="ondraw"></a>CMFCButton::OnDraw

Wird vom Framework aufgerufen, um eine Schaltfläche zu zeichnen.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Ein Verweis auf ein Rechteck, das die Schaltfläche umgrenzt.

*uiState*<br/>
[in] Der aktuelle Schaltflächenstatus. Weitere Informationen finden `itemState` Sie im Thema [DRAWITEMSTRUCT Structure.](/windows/win32/api/winuser/ns-winuser-drawitemstruct)

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um Ihren eigenen Code zum Zeichnen einer Schaltfläche zu verwenden.

## <a name="cmfcbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCButton::OnDrawBorder

Wird vom Framework aufgerufen, um den Rahmen eines Buttons zu zeichnen.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*rectClient*<br/>
[in] Ein Verweis auf ein Rechteck, das die Schaltfläche umgrenzt.

*uiState*<br/>
[in] Der aktuelle Schaltflächenstatus. Weitere Informationen finden `itemState` Sie im Thema [DRAWITEMSTRUCT Structure.](/windows/win32/api/winuser/ns-winuser-drawitemstruct)

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um Ihren eigenen Code zum Zeichnen des Rahmens zu verwenden.

## <a name="cmfcbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect

Wird vom Framework aufgerufen, um das Fokusrechteck für eine Schaltfläche zu zeichnen.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*rectClient*<br/>
[in] Ein Verweis auf ein Rechteck, das die Schaltfläche umgrenzt.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um Ihren eigenen Code zum Zeichnen des Fokusrechtecks zu verwenden.

## <a name="cmfcbuttonondrawtext"></a><a name="ondrawtext"></a>CMFCButton::OnDrawText

Wird vom Framework aufgerufen, um den Schaltflächentext zu zeichnen.

```
virtual void OnDrawText(
    CDC* pDC,
    const CRect& rect,
    const CString& strText,
    UINT uiDTFlags,
    UINT uiState);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Ein Verweis auf ein Rechteck, das die Schaltfläche umgrenzt.

*strText*<br/>
[in] Der zu zeichnende Text.

*uiDTFlags*<br/>
[in] Flags, die angeben, wie der Text formatiert werden soll. Weitere Informationen finden Sie im *nFormat-Parameter* der [CDC::DrawText-Methode.](../../mfc/reference/cdc-class.md#drawtext)

*uiState*<br/>
[in]: Reserviert

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um Ihren eigenen Code zum Zeichnen des Schaltflächentextes zu verwenden.

## <a name="cmfcbuttononfillbackground"></a><a name="onfillbackground"></a>CMFCButton::OnFillBackground

Wird vom Framework aufgerufen, um den Hintergrund des Schaltflächentexts zu zeichnen.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*rectClient*<br/>
[in] Ein Verweis auf ein Rechteck, das die Schaltfläche umgrenzt.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um Ihren eigenen Code zum Zeichnen des Hintergrunds einer Schaltfläche zu verwenden.

## <a name="cmfcbuttonselectfont"></a><a name="selectfont"></a>CMFCButton::SelectFont

Ruft die Schriftart ab, die dem angegebenen Gerätekontext zugeordnet ist.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

### <a name="return-value"></a>Rückgabewert

Überschreiben Sie diese Methode, um Ihren eigenen Code zum Abrufen der Schriftart zu verwenden.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonsetautorepeatmode"></a><a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode

Legt eine Schaltfläche auf Auto-Repeat-Modus fest.

```cpp
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Parameter

*nTimeDelay*<br/>
[in] Eine nicht negative Zahl, die das Intervall zwischen Nachrichten angibt, die an das übergeordnete Fenster gesendet werden. Das Intervall wird in Millisekunden gemessen, der Standardwert beträgt 500 Millisekunden. Geben Sie Null an, um den Nachrichtenmodus für die automatische Wiederholung zu deaktivieren.

### <a name="remarks"></a>Bemerkungen

Diese Methode bewirkt, dass die Schaltfläche ständig WM_COMMAND Nachrichten an das übergeordnete Fenster sendet, bis die Schaltfläche freigegeben wird oder der Parameter *nTimeDelay* auf Null gesetzt ist.

## <a name="cmfcbuttonsetcheckedimage"></a><a name="setcheckedimage"></a>CMFCButton::SetCheckedImage

Legt das Bild für eine aktivierte Schaltfläche fest.

```cpp
void SetCheckedImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetCheckedImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetCheckedImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>Parameter

*hIcon*<br/>
[in] Behandeln Sie das Symbol, das die Bitmap und Maske für das neue Bild enthält.

*bAutoDestroy*<br/>
[in] TRUE, um anzugeben, dass Bitmapressourcen automatisch zerstört werden; andernfalls FALSE. Der Standardwert ist TRUE.

*hIconHot*<br/>
[in] Behandeln Sie das Symbol, das das Bild für den ausgewählten Status enthält.

*hBitmap*<br/>
[in] Behandeln Sie die Bitmap, die das Bild für den nicht ausgewählten Zustand enthält.

*hBitmapHot*<br/>
[in] Behandeln Sie die Bitmap, die das Bild für den ausgewählten Status enthält.

*bMap3dFarben*<br/>
[in] Gibt eine transparente Farbe für den Schaltflächenhintergrund an. das heißt, das Gesicht der Taste. TRUE, um den Farbwert RGB(192, 192, 192) zu verwenden; FALSE, um den von `AFX_GLOBAL_DATA::clrBtnFace`definierten Farbwert zu verwenden.

*uiBmpResId*<br/>
[in] Ressourcen-ID für das nicht ausgewählte Bild.

*uiBmpHotResId*<br/>
[in] Ressourcen-ID für das ausgewählte Bild.

*hIconDeaktiviert*<br/>
[in] Behandeln Sie das Symbol für das deaktivierte Bild.

*hBitmapDeaktiviert*<br/>
[in] Behandeln Sie die Bitmap, die das deaktivierte Bild enthält.

*uiBmpDsblResID*<br/>
[in] Ressourcen-ID der deaktivierten Bitmap.

*bAlphaBlend*<br/>
[in] TRUE, um nur 32-Bit-Bilder zu verwenden, die den Alphakanal verwenden; FALSE, um nicht nur Alphakanalbilder zu verwenden. Der Standardwert lautet FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonsetfacecolor"></a><a name="setfacecolor"></a>CMFCButton::SetFaceColor

Legt die Hintergrundfarbe für den Schaltflächentext fest.

```cpp
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parameter

*crFace*<br/>
[in] Ein RGB-Farbwert.

*bZeichnung*<br/>
[in] TRUE, um den Bildschirm sofort neu zu zeichnen; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um eine neue Füllfarbe für den Schaltflächenhintergrund (Gesicht) zu definieren. Beachten Sie, dass der Hintergrund nicht ausgefüllt wird, wenn die [Membervariable CMFCButton::m_bTransparent](#m_btransparent) TRUE ist.

## <a name="cmfcbuttonsetimage"></a><a name="setimage"></a>CMFCButton::SetImage

Legt das Bild für eine Schaltfläche fest.

```cpp
void SetImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>Parameter

*hIcon*<br/>
[in] Behandeln Sie das Symbol, das die Bitmap und Maske für das neue Bild enthält.

*bAutoDestroy*<br/>
[in] TRUE, um anzugeben, dass Bitmapressourcen automatisch zerstört werden; andernfalls FALSE. Der Standardwert ist TRUE.

*hIconHot*<br/>
[in] Behandeln Sie das Symbol, das das Bild für den ausgewählten Status enthält.

*hBitmap*<br/>
[in] Behandeln Sie die Bitmap, die das Bild für den nicht ausgewählten Zustand enthält.

*hBitmapHot*<br/>
[in] Behandeln Sie die Bitmap, die das Bild für den ausgewählten Status enthält.

*uiBmpResId*<br/>
[in] Ressourcen-ID für das nicht ausgewählte Bild.

*uiBmpHotResId*<br/>
[in] Ressourcen-ID für das ausgewählte Bild.

*bMap3dFarben*<br/>
[in] Gibt eine transparente Farbe für den Schaltflächenhintergrund an. das heißt, das Gesicht der Taste. TRUE, um den Farbwert RGB(192, 192, 192) zu verwenden; FALSE, um den von `AFX_GLOBAL_DATA::clrBtnFace`definierten Farbwert zu verwenden.

*hIconDeaktiviert*<br/>
[in] Behandeln Sie das Symbol für das deaktivierte Bild.

*hBitmapDeaktiviert*<br/>
[in] Behandeln Sie die Bitmap, die das deaktivierte Bild enthält.

*uiBmpDsblResID*<br/>
[in] Ressourcen-ID der deaktivierten Bitmap.

*bAlphaBlend*<br/>
[in] TRUE, um nur 32-Bit-Bilder zu verwenden, die den Alphakanal verwenden; FALSE, um nicht nur Alphakanalbilder zu verwenden. Der Standardwert lautet FALSE.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `SetImage` wie verschiedene `CMFCButton` Versionen der Methode in der Klasse verwendet werden. Das Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

## <a name="cmfcbuttonsetmousecursor"></a><a name="setmousecursor"></a>CMFCButton::SetMouseCursor

Legt das Cursorbild fest.

```cpp
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Parameter

*hcursor*<br/>
[in] Das Handle eines Cursors.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um der Schaltfläche ein Cursorbild, z. B. den Zeigercursor, zuzuordnen. Der Cursor wird aus den Anwendungsressourcen geladen.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `SetMouseCursor` veranschaulicht, `CMFCButton` wie die Methode in der Klasse verwendet wird. Das Beispiel ist Teil des Codes im [Beispiel "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

## <a name="cmfcbuttonsetmousecursorhand"></a><a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand

Legt den Cursor auf das Bild einer Hand fest.

```cpp
void SetMouseCursorHand();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um das Cursorbild einer Hand mit der Schaltfläche zu verknüpfen. Der Cursor wird aus den Anwendungsressourcen geladen.

## <a name="cmfcbuttonsetstdimage"></a><a name="setstdimage"></a>CMFCButton::SetStdImage

Verwendet `CMenuImages` ein Objekt, um das Schaltflächenbild festzulegen.

```cpp
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Einer der Schaltflächenbildbezeichner, `CMenuImage::IMAGES_IDS` der in der Enumeration definiert ist. Die Bildwerte geben Bilder wie Pfeile, Pins und Optionsfelder an.

*state*<br/>
[in] Einer der Schaltflächenbildstatusbezeichner, `CMenuImages::IMAGE_STATE` der in der Enumeration definiert ist. Die Bildzustände geben Schaltflächenfarben wie Schwarz, Grau, Hellgrau, Weiß und Dunkelgrau an. Der Standardwert ist `CMenuImages::ImageBlack`.

*idDeaktiviert*<br/>
[in] Einer der Schaltflächenbildbezeichner, `CMenuImage::IMAGES_IDS` der in der Enumeration definiert ist. Das Bild zeigt an, dass die Schaltfläche deaktiviert ist. Der Standardwert ist das `CMenuImages::IdArrowDown`erste Schaltflächenbild ( ).

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonsettextcolor"></a><a name="settextcolor"></a>CMFCButton::SetTextColor

Legt die Farbe des Schaltflächentexts für eine Schaltfläche fest, die nicht ausgewählt ist.

```cpp
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Parameter

*clrText*<br/>
[in] Ein RGB-Farbwert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonsettexthotcolor"></a><a name="settexthotcolor"></a>CMFCButton::SetTextHotColor

Legt die Farbe des Schaltflächentexts für eine ausgewählte Schaltfläche fest.

```cpp
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Parameter

*clrTextHot*<br/>
[in] Ein RGB-Farbwert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonsettooltip"></a><a name="settooltip"></a>CMFCButton::SetTooltip

Ordnet eine QuickInfo einer Schaltfläche zu.

```cpp
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Parameter

*lpszToolTipText*<br/>
[in] Zeiger auf den Text für die QuickInfo. Geben Sie NULL an, um die QuickInfo zu deaktivieren.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCButton::SizeToContent

Ändert die Größe einer Schaltfläche so, dass sie den Text und das Bild der Schaltfläche enthält.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parameter

*bCalcOnly*<br/>
[in] TRUE, um die neue Größe der Schaltfläche zu berechnen, aber nicht zu ändern; FALSE, um die Größe der Schaltfläche zu ändern. Der Standardwert lautet FALSE.

### <a name="return-value"></a>Rückgabewert

Ein `CSize` Objekt, das die neue Größe der Schaltfläche enthält.

### <a name="remarks"></a>Bemerkungen

Standardmäßig berechnet diese Methode eine neue Größe, die einen horizontalen Rand von 10 Pixeln und einen vertikalen Rand von 5 Pixeln enthält.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl-Klasse](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton-Klasse](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton-Klasse](../../mfc/reference/cmfcmenubutton-class.md)
