---
title: CMFCColorButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
ms.openlocfilehash: cf24c162d0eda272f73c69c434589ae6ef3332a4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752565"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton-Klasse

Die `CMFCColorButton` und [CMFCColorBar-Klassenklassen](../../mfc/reference/cmfccolorbar-class.md) werden zusammen verwendet, um ein Farbauswahlsteuerelement zu implementieren.

## <a name="syntax"></a>Syntax

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Erstellt ein neues `CMFCColorButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Aktiviert und deaktiviert eine "automatische" Schaltfläche, die über den regulären Farbschaltflächen positioniert ist. (Die Standard-System-Automatik-Taste ist mit **Automatisch**beschriftet.)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Aktiviert und deaktiviert eine "andere" Schaltfläche, die sich unterhalb der regulären Farbschaltflächen befindet. (Das Standardsystem "andere" Taste ist mit **Mehr Farben**beschriftet .)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Ruft die aktuelle automatische Farbe ab.|
|[CMFCColorButton::GetColor](#getcolor)|Ruft die Farbe einer Schaltfläche ab.|
|[CMFCColorButton::SetColor](#setcolor)|Legt die Farbe einer Schaltfläche fest.|
|[CMFCColorButton::SetColorName](#setcolorname)|Legt einen Farbnamen fest.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Legt die Anzahl der Spalten im Dialogfeld Farbauswahl fest.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Gibt eine Liste dokumentspezifischer Farben an, die im Dialogfeld Farbauswahl angezeigt werden.|
|[CMFCColorButton::SetPalette](#setpalette)|Gibt eine Palette von Standardanzeigefarben an.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Ändert die Größe des Schaltflächensteuerelements, abhängig von seiner Text- und Bildgröße.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Gibt an, ob die aktuelle Farbschaltfläche im visuellen Stil von Windows XP angezeigt wird.|
|[CMFCColorButton::OnDraw](#ondraw)|Wird vom Framework aufgerufen, um ein Bild der Schaltfläche anzuzeigen.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Wird vom Framework aufgerufen, um den Rahmen der Schaltfläche anzuzeigen.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Wird vom Framework aufgerufen, um ein Fokusrechteck anzuzeigen, wenn die Schaltfläche einen Fokus hat.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Wird vom Framework aufgerufen, wenn das Dialogfeld Farbauswahl angezeigt wird.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Initialisiert das `m_pPalette` geschützte Datenelement auf die angegebene Palette oder die Standardsystempalette.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Wird vom Framework aufgerufen, wenn der Benutzer eine Farbe aus der Palette des Dialogfelds Farbauswahl auswählt.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|`m_bAltColorDlg`|Ein boolescher Wert. Wenn TRUE, zeigt das Framework das Farbdialogfeld [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) an, wenn auf die *andere* Schaltfläche geklickt wird, oder wenn FALSE, das Dialogfeld Systemfarbe. Der Standardwert ist TRUE. Weitere Informationen finden Sie unter [CMFCColorButton::EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Ein boolescher Wert. Wenn TRUE, legt das Framework den Fokus auf das Farbmenü fest, wenn das Menü angezeigt wird, oder wenn FALSE, ändert den Fokus nicht. Der Standardwert ist TRUE.|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Gibt an, ob der Anpassungsmodus für die Farbschaltfläche aktiviert ist.|
|`m_Color`|Ein [COLORREF-Wert.](/windows/win32/gdi/colorref) Enthält die aktuell ausgewählte Farbe.|
|`m_ColorAutomatic`|Ein [COLORREF-Wert.](/windows/win32/gdi/colorref) Enthält die aktuell ausgewählte Standardfarbe.|
|`m_Colors`|Ein [CArray](../../mfc/reference/carray-class.md) von [COLORREF-Werten.](/windows/win32/gdi/colorref) Enthält die aktuell verfügbaren Farben.|
|`m_lstDocColors`|Eine [CList](../../mfc/reference/clist-class.md) mit [COLORREF-Werten.](/windows/win32/gdi/colorref) Enthält die aktuellen Dokumentfarben.|
|`m_nColumns`|Eine ganze Zahl Enthält die Anzahl der Spalten, die im Farbraster in einem Farbauswahlmenü angezeigt werden sollen.|
|`m_pPalette`|Ein Zeiger auf eine [CPalette](../../mfc/reference/cpalette-class.md). Enthält die Farben, die im aktuellen Farbauswahlmenü verfügbar sind.|
|`m_pPopup`|Ein Zeiger auf ein [CMFCColorPopupMenu-Klassenobjekt.](../../mfc/reference/cmfccolorpopupmenu-class.md) Das Farbauswahlmenü, das angezeigt wird, wenn Sie auf die Schaltfläche Farbe klicken.|
|`m_strAutoColorText`|Eine Zeichenfolge. Die Beschriftung der Schaltfläche "automatisch" in einem Farbauswahlmenü.|
|`m_strDocColorsText`|Eine Zeichenfolge. Die Beschriftung der Schaltfläche in einem Farbauswahlmenü, in dem die Dokumentfarben angezeigt werden.|
|`m_strOtherText`|Eine Zeichenfolge. Die Beschriftung der Schaltfläche "Sonstige" in einem Farbauswahlmenü.|

## <a name="remarks"></a>Bemerkungen

Standardmäßig verhält `CMFCColorButton` sich die Klasse wie eine Drucktaste, die ein Dialogfeld für die Farbauswahl öffnet. Das Dialogfeld Farbauswahl enthält ein Array kleiner Farbschaltflächen und eine Schaltfläche "Sonstiges", die eine benutzerdefinierte Farbauswahl anzeigt. (Das Standardsystem "andere" Taste ist mit **Mehr Farben**beschriftet .) Wenn ein Benutzer eine neue `CMFCColorButton` Farbe auswählt, spiegelt das Objekt die Änderung wider und zeigt die ausgewählte Farbe an.

Erstellen Sie ein Farbschaltflächensteuerelement entweder direkt im Code oder mithilfe des **ClassWizard-Tools** und einer Dialogfeldvorlage. Wenn Sie ein Farbschaltflächensteuerelement `CMFCColorButton` direkt erstellen, fügen Sie der Anwendung `Create` eine `CMFCColorButton` Variable hinzu, und rufen Sie dann den Konstruktor und die Methoden des Objekts auf. Wenn Sie den **ClassWizard** `CButton` verwenden, fügen Sie ihrer Anwendung eine Variable `CButton` `CMFCColorButton`hinzu, und ändern Sie dann den Typ der Variablen von in .

Das Dialogfeld "Farbauswahl" ( [CMFCColorBar-Klasse](../../mfc/reference/cmfccolorbar-class.md)) wird von der [CMFCColorButton::OnShowColorPopup-Methode](#onshowcolorpopup) angezeigt, wenn das Framework den `OnLButtonDown` Ereignishandler aufruft. Die [CMFCColorButton::OnShowColorPopup-Methode](#onshowcolorpopup) kann überschrieben werden, um die benutzerdefinierte Farbauswahl zu unterstützen.

Das `CMFCColorButton` Objekt benachrichtigt das übergeordnete Element, dass sich eine Farbe ändert, indem es ihm eine WM_COMMAND | BN_CLICKED Benachrichtigung. Das übergeordnete Element verwendet die [CMFCColorButton::GetColor-Methode,](#getcolor) um die aktuelle Farbe abzurufen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie eine `CMFCColorButton` Farbschaltfläche mithilfe verschiedener Methoden in der Klasse konfigurieren. Die Methoden legen die Farbe der Farbschaltfläche und ihre Anzahl der Spalten fest und aktivieren die automatische und die anderen Schaltflächen. Dieses Beispiel ist Teil des [Beispiels statusbar Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxcolorbutton.h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton

Erstellt ein neues `CMFCColorButton`-Objekt.

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton

Aktivieren oder deaktivieren Sie die Schaltfläche "Automatisch" eines Farbauswahlsteuerelements und legen Sie die automatische (Standard-)Farbe fest.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Gibt den Text der automatischen Schaltfläche an.

*colorAutomatic*<br/>
[in] Ein RGB-Wert, der die Standardfarbe der automatischen Schaltfläche angibt.

*bEnable*<br/>
[in] Gibt an, ob die automatische Schaltfläche aktiviert oder deaktiviert ist.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton

Aktivieren oder deaktivieren Sie die Schaltfläche "Sonstiges", die unter den regulären Farbschaltflächen angezeigt wird.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Gibt den Text der Schaltfläche an.

*bAltColorDlg*<br/>
[in] Gibt an, ob das Dialogfeld [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) oder das Dialogfeld Systemfarbe geöffnet wird, wenn der Benutzer auf die Schaltfläche klickt.

*bEnable*<br/>
[in] Gibt an, ob die Schaltfläche "Andere" aktiviert oder deaktiviert ist.

### <a name="remarks"></a>Bemerkungen

Klicken Sie auf die Schaltfläche "Andere", um ein Farbdialogfeld anzuzeigen. Wenn der Parameter *bAltColorDlg* TRUE ist, wird die [CMFCColorDialog-Klasse](../../mfc/reference/cmfccolordialog-class.md) angezeigt. Andernfalls wird das Dialogfeld Systemfarbe angezeigt.

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor

Ruft die aktuelle automatische (Standard-)Farbe ab.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein RGB-Wert, der die aktuelle automatische Farbe darstellt.

### <a name="remarks"></a>Bemerkungen

Die aktuelle automatische Farbe wird von der [CMFCColorButton::EnableAutomaticButton-Methode](#enableautomaticbutton) festgelegt.

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a>CMFCColorButton::GetColor

Ruft die aktuell ausgewählte Farbe ab.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein RGB-Wert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme

Gibt an, ob die aktuelle Farbschaltfläche im visuellen Stil von Windows XP angezeigt wird.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn visuelle Stile unterstützt werden und die aktuelle Farbschaltfläche im visuellen Stil von Windows XP angezeigt wird. andernfalls FALSE.

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode

Legt eine Farbschaltfläche in den Anpassungsmodus fest.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie der Seite eines Anpassungsdialogfelds eine Farbschaltfläche hinzufügen müssen (oder dem Benutzer erlauben `m_bEnabledInCustomizeMode` müssen, während der Anpassung eine andere Farbauswahl vorzunehmen), aktivieren Sie die Schaltfläche, indem Sie das Element auf TRUE festlegen. Standardmäßig ist dieses Element auf FALSE festgelegt.

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a>CMFCColorButton::OnDraw

Wird vom Framework aufgerufen, um ein Bild der Schaltfläche zu rendern.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeigt auf den Gerätekontext, der zum Rendern des Bildes der Schaltfläche verwendet wird.

*Rect*<br/>
[in] Ein Rechteck, das die Schaltfläche umgrenzt.

*uiState*<br/>
[in] Gibt den visuellen Status der Schaltfläche an.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um den Renderprozess anzupassen.

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder

Wird vom Framework aufgerufen, um den Rahmen der Schaltfläche anzuzeigen.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeigt auf den Gerätekontext, der zum Zeichnen des Rahmens verwendet wird.

*rectClient*<br/>
[in] Ein Rechteck im Gerätekontext, das durch den *pDC-Parameter* angegeben wird, der die Grenzen der zu zeichnenden Schaltfläche definiert.

*uiState*<br/>
[in] Gibt den visuellen Status der Schaltfläche an.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Rahmendarstellung der Farbschaltfläche anzupassen.

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect

Wird vom Framework aufgerufen, um ein Fokusrechteck anzuzeigen, wenn die Schaltfläche den Fokus hat.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeigt auf den Gerätekontext, der zum Zeichnen des Fokusrechtecks verwendet wird.

*rectClient*<br/>
[in] Ein Rechteck im Gerätekontext, das durch den *pDC-Parameter* angegeben wird, der die Grenzen der Schaltfläche definiert.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um die Darstellung des Fokusrechtecks anzupassen.

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup

Wird aufgerufen, bevor die Popup-Farbleiste angezeigt wird.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette

Initialisiert das `m_pPalette` geschützte Datenelement auf die angegebene Palette oder die Standardsystempalette.

```cpp
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pPal*|[in] Ein Zeiger auf eine logische Palette oder NULL. Wenn NULL, wird die Standardsystempalette verwendet.|

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCColorButton::SetColor

Gibt die Farbe der Schaltfläche an.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Ein RGB-Wert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorButton::SetColorName

Gibt den Namen einer Farbe an.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Der RGB-Wert der Farbe.

*strName*<br/>
[in] Der Name der Farbe.

### <a name="remarks"></a>Bemerkungen

Die Liste der Farbnamen ist global pro Anwendung. Daher überträgt diese Methode ihre Parameter an [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber

Definiert die Anzahl der Spalten, die in der Farbtabelle angezeigt werden, die dem Benutzer während des Farbauswahlprozesses des Benutzers angezeigt wird.

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parameter

*nColumns*<br/>
[in] Gibt die Anzahl der Spalten an.

### <a name="remarks"></a>Bemerkungen

Der Benutzer kann eine Farbe aus einer Popup-Farbleiste auswählen, die eine Tabelle mit vordefinierten Farben anzeigt. Verwenden Sie diese Methode, um die Anzahl der Spalten in der Tabelle zu definieren.

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors

Gibt einen Satz von Farben und den Namen des Satzes an. Der Farbsatz wird mit einem [CMFCColorBar-Klassenobjekt](../../mfc/reference/cmfccolorbar-class.md) angezeigt.

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Gibt die Bezeichnung an, die mit dem Satz von Dokumentfarben angezeigt werden soll.

*lstColors*<br/>
[in] Ein Verweis auf eine Liste von RGB-Werten.

### <a name="remarks"></a>Bemerkungen

Ein `CMFCColorButton` Objekt verwaltet eine Liste von RGB-Werten, die an ein [CMFCColorBar-Klassenobjekt](../../mfc/reference/cmfccolorbar-class.md) übertragen werden. Wenn die Farbleiste angezeigt wird, werden diese Farben in einem speziellen Abschnitt angezeigt, dessen Bezeichnung durch den Parameter *lpszLabel* angegeben wird.

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCColorButton::SetPalette

Gibt die Standardfarben an, die auf der Popup-Farbleiste angezeigt werden sollen.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parameter

*pPalette*<br/>
[in] Ein Zeiger auf eine Farbpalette.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCColorButton::SizeToContent

Ändert die Größe des Schaltflächensteuerelements an den Text und das Bild.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parameter

*bCalcOnly*<br/>
[in] Bei ungleich Null wird die neue Größe des Schaltflächensteuerelements berechnet, die tatsächliche Größe wird jedoch nicht geändert.

### <a name="return-value"></a>Rückgabewert

Ein `CSize` Objekt, das eine neue Schaltflächensteuerelementgröße angibt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCColorButton::UpdateColor

Wird vom Framework aufgerufen, wenn der Benutzer eine Farbe aus der Farbleiste auswählt, die angezeigt wird, wenn der Benutzer auf die Schaltfläche "Farbe" klickt.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Eine vom Benutzer ausgewählte Farbe.

### <a name="remarks"></a>Bemerkungen

Die `UpdateColor` Funktion ändert die Farbe der aktuell ausgewählten Schaltfläche und benachrichtigt das übergeordnete Element, indem eine WM_COMMAND Nachricht mit einer BN_CLICKED Standardbenachrichtigung gesendet wird. Verwenden Sie die [CMFCColorButton::GetColor-Methode,](#getcolor) um die ausgewählte Farbe abzurufen.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton-Klasse](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar-Klasse](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette-Klasse](../../mfc/reference/cpalette-class.md)<br/>
[CArray-Klasse](../../mfc/reference/carray-class.md)<br/>
[CList-Klasse](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
