---
title: CMFCColorMenuButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
ms.openlocfilehash: 22208aec505033d372f5a80ba2a9641b1bd15874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367707"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton-Klasse

Die `CMFCColorMenuButton` Klasse unterstützt einen Menübefehl oder eine Symbolleistenschaltfläche, die ein Dialogfeld für die Farbauswahl startet.

## <a name="syntax"></a>Syntax

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Erstellt ein `CMFCColorMenuButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Aktiviert und deaktiviert eine "automatische" Schaltfläche, die über den regulären Farbschaltflächen positioniert ist. (Die Standard-System-Automatik-Taste ist mit **Automatisch**beschriftet.)|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Ermöglicht die Anzeige dokumentspezifischer Farben anstelle von Systemfarben.|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Aktiviert und deaktiviert eine "andere" Schaltfläche, die sich unterhalb der regulären Farbschaltflächen befindet. (Das Standardsystem "andere" Taste ist mit **Mehr Farben**beschriftet .)|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Ermöglicht die Möglichkeit, einen Farbbereich abzureißen.|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Ruft die aktuelle automatische Farbe ab.|
|[CMFCColorMenuButton::GetColor](#getcolor)|Ruft die Farbe der aktuellen Schaltfläche ab.|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Ruft die Farbe ab, die einer angegebenen Befehls-ID entspricht.|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Wird vom Framework aufgerufen, wenn sich das übergeordnete Fenster ändert.|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Öffnet ein Dialogfeld für die Farbauswahl.|
|[CMFCColorMenuButton::SetColor](#setcolor)|Legt die Farbe der aktuellen Farbschaltfläche fest.|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Legt die Farbe der angegebenen Farbmenüschaltfläche fest.|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Legt einen neuen Namen für die angegebene Farbe fest.|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Legt die Anzahl der Spalten `CMFCColorBar` fest, die von einem Objekt angezeigt werden.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Kopiert eine weitere Symbolleistenschaltfläche auf die aktuelle Schaltfläche.|
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Erstellt ein Dialogfeld für die Farbauswahl.|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Gibt an, ob leere Menüs unterstützt werden.|
|[CMFCColorMenuButton::OnDraw](#ondraw)|Wird vom Framework aufgerufen, um ein Bild auf einer Schaltfläche anzuzeigen.|
|[CMFCColorMenuButton::OnDrawonCustomizeList](#ondrawoncustomizelist)|Wird vom Framework `CMFCColorMenuButton` aufgerufen, bevor ein Objekt in der Liste eines Dialogfelds für die Werkzeugleistenanpassung angezeigt wird.|

## <a name="remarks"></a>Bemerkungen

Um den ursprünglichen Menübefehl oder die `CMFCColorMenuButton` Symbolleistenschaltfläche `CMFCColorMenuButton` durch ein Objekt zu ersetzen, erstellen Sie `ReplaceButton` das Objekt, legen Sie alle geeigneten [CMFCColorBar-Klassenstile](../../mfc/reference/cmfccolorbar-class.md) fest, und rufen Sie dann die Methode der [CMFCToolBar-Klassenklasse](../../mfc/reference/cmfctoolbar-class.md) auf. Wenn Sie eine Symbolleiste anpassen, rufen Sie die [CMFCToolBarsCustomizeDialog::ReplaceButton-Methode](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) auf.

Das Dialogfeld Farbauswahl wird während der Verarbeitung des [Ereignishandlers CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) erstellt. Der Ereignishandler benachrichtigt den übergeordneten Frame mit einer WM_COMMAND Nachricht. Das `CMFCColorMenuButton` Objekt sendet die Steuer-ID, die dem ursprünglichen Menübefehl oder der Symbolleistenschaltfläche zugewiesen ist.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie eine Farbmenüschaltfläche mithilfe verschiedener Methoden in der `CMFCColorMenuButton` Klasse erstellen und konfigurieren. Im Beispiel wird `CPalette` zuerst ein Objekt erstellt und dann `CMFCColorMenuButton` zum Erstellen eines Objekts der Klasse verwendet. Das `CMFCColorMenuButton` Objekt wird dann konfiguriert, indem die automatischen und anderen Schaltflächen aktiviert und die Farbe und die Anzahl der Spalten festgelegt werden. Dieser Code ist Teil des [Word Pad-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxcolormenubutton.h

## <a name="cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a>CMFCColorMenuButton::CMFCColorMenuButton

Erstellt ein `CMFCColorMenuButton`-Objekt.

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parameter

*uiCmdID*<br/>
[in] Eine Schaltflächenbefehls-ID.

*lpszText*<br/>
[in] Der Schaltflächentext.

*pPalette*<br/>
[in] Ein Zeiger auf die Farbpalette der Schaltfläche.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor ist der Standardkonstruktor. Die aktuelle Farbe und die automatische Farbe des Objekts werden in Schwarz initialisiert (RGB(0, 0, 0)).

Der zweite Konstruktor initialisiert die Schaltfläche auf die Farbe, die der angegebenen Befehls-ID entspricht.

## <a name="cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFCColorMenuButton::CopyFrom

Kopiert ein [VON der CMFCToolBarMenuButton-Klasse](../../mfc/reference/cmfctoolbarmenubutton-class.md)abgeleitetes Objekt in ein anderes.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
[in] Quellschaltfläche zum Kopieren.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um `CMFCColorMenuButton` Objekte zu kopieren, die vom Objekt abgeleitet werden.

## <a name="cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFCColorMenuButton::CreatePopupMenu

Erstellt ein Dialogfeld für die Farbauswahl.

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Rückgabewert

Ein Objekt, das ein Dialogfeld für die Farbauswahl darstellt.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Framework aufgerufen, wenn der Benutzer eine Farbmenüschaltfläche drückt.

## <a name="cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorMenuButton::EnableAutomaticButton

Aktiviert und deaktiviert eine "automatische" Schaltfläche, die über den regulären Farbschaltflächen positioniert ist. (Die Standard-System-Automatik-Taste ist mit **Automatisch**beschriftet.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Gibt den Schaltflächentext an, der angezeigt wird, wenn die Schaltfläche automatisch wird.

*colorAutomatic*<br/>
[in] Gibt eine neue automatische Farbe an.

*bEnable*<br/>
[in] Gibt an, ob die Schaltfläche automatisch ist oder nicht.

### <a name="remarks"></a>Bemerkungen

Die automatische Schaltfläche wendet die aktuelle Standardfarbe an.

## <a name="cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a>CMFCColorMenuButton::EnableDocumentColors

Ermöglicht die Anzeige dokumentspezifischer Farben anstelle von Systemfarben.

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Gibt den Schaltflächentext an.

*bEnable*<br/>
[in] TRUE, um dokumentspezifische Farben oder FALSE zur Anzeige von Systemfarben anzuzeigen.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die aktuellen Dokumentfarben oder die Systempalettenfarben anzuzeigen, wenn der Benutzer auf eine Schaltfläche im Farbmenü klickt.

## <a name="cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorMenuButton::EnableOtherButton

Aktiviert und deaktiviert eine "andere" Schaltfläche, die sich unterhalb der regulären Farbschaltflächen befindet. (Das Standardsystem "andere" Taste ist mit **Mehr Farben**beschriftet .)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Gibt den Schaltflächentext an.

*bAltColorDlg*<br/>
[in] Geben Sie TRUE `CMFCColorDialog` an, um das Dialogfeld anzuzeigen, oder FALSE, um das Standard-Systemfarbdialogfeld anzuzeigen.

*bEnable*<br/>
[in] Geben Sie TRUE an, um die Schaltfläche "Sonstige" anzuzeigen. andernfalls FALSE. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a>CMFCColorMenuButton::EnableTearOff

Ermöglicht die Möglichkeit, einen Farbbereich abzureißen.

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>Parameter

*uiID*<br/>
[in] Gibt die ID für den Abreißbereich an.

*nVertDockColumns*<br/>
[in] Gibt die Anzahl der Spalten im vertikal angedockten Farbbereich im Abreißzustand an.

*nHorzDockRows*<br/>
[in] Gibt die Anzahl der Zeilen für den horizontal angedockten Farbbereich im Abreißzustand an.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die "Tear-off"-Funktion `CMFCColorMenuButton` für den Farbbereich zu aktivieren, der beim Drücken der Schaltfläche angezeigt wird.

## <a name="cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorMenuButton::GetAutomaticColor

Ruft die aktuelle automatische Farbe ab.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein RGB-Farbwert, der die aktuelle automatische Farbe darstellt.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die automatische Farbe abzurufen, die von [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)festgelegt wird.

## <a name="cmfccolormenubuttongetcolor"></a><a name="getcolor"></a>CMFCColorMenuButton::GetColor

Ruft die Farbe der aktuellen Schaltfläche ab.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die Farbe der Schaltfläche.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a>CMFCColorMenuButton::GetColorByCmdID

Ruft die Farbe ab, die einer angegebenen Befehls-ID entspricht.

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>Parameter

*uiCmdID*<br/>
[in] Eine Befehls-ID.

### <a name="return-value"></a>Rückgabewert

Die Farbe, die der angegebenen Befehls-ID entspricht.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, wenn Sie mehrere Farbschaltflächen in einer Anwendung haben. Wenn der Benutzer auf eine Farbschaltfläche klickt, sendet die Schaltfläche ihre Befehls-ID in einer WM_COMMAND Nachricht an das übergeordnete Element. Die `GetColorByCmdID` Methode verwendet die Befehls-ID, um die entsprechende Farbe abzurufen.

## <a name="cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFCColorMenuButton::IsEmptyMenuAllowed

Gibt an, ob leere Menüs unterstützt werden.

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn leere Menüs zulässig sind; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Leere Menüs werden standardmäßig unterstützt. Überschreiben Sie diese Methode, um dieses Verhalten in der abgeleiteten Klasse zu ändern.

## <a name="cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCColorMenuButton::OnChangeParentWnd

Wird vom Framework aufgerufen, wenn sich das übergeordnete Fenster ändert.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Ein Zeiger auf das neue übergeordnete Fenster.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolormenubuttonondraw"></a><a name="ondraw"></a>CMFCColorMenuButton::OnDraw

Wird vom Framework aufgerufen, um ein Bild auf einer Schaltfläche anzuzeigen.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz=TRUE,
    BOOL bCustomizeMode=FALSE,
    BOOL bHighlight=FALSE,
    BOOL bDrawBorder=TRUE,
    BOOL bGrayDisabledButtons=TRUE);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Ein Rechteck, das den neu zu zeichnenden Bereich begrenzt.

*pImages*<br/>
[in] Zeigt auf eine Liste von Symbolleistenbildern.

*bHorz*<br/>
[in] TRUE, um anzugeben, dass sich die Symbolleiste in einem horizontal angedockten Zustand befindet; andernfalls FALSE. Der Standardwert ist TRUE.

*bCustomizeMode*<br/>
[in] TRUE, um anzugeben, dass sich die Anwendung im Anpassungsmodus befindet; andernfalls FALSE. Der Standardwert lautet FALSE.

*bHighlight*<br/>
[in] TRUE, um anzugeben, dass die Schaltfläche hervorgehoben ist; andernfalls FALSE. Der Standardwert lautet FALSE.

*bDrawBorder*<br/>
[in] TRUE, um anzugeben, dass der Rahmen der Schaltfläche angezeigt wird; andernfalls FALSE. Der Standardwert ist TRUE.

*bGrayDisabledButtons*<br/>
[in] TRUE, um anzugeben, dass deaktivierte Schaltflächen abgeblendet (abgeblendet) sind; andernfalls FALSE. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCColorMenuButton::OnDrawonCustomizeList

Wird vom Framework `CMFCColorMenuButton` aufgerufen, bevor ein Objekt in der Liste eines Dialogfelds für die Werkzeugleistenanpassung angezeigt wird.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Ein Rechteck, das die zu zeichnende Schaltfläche begrenzt.

*bAusgewählt*<br/>
[in] TRUE gibt an, dass sich die Schaltfläche im ausgewählten Zustand befindet. andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

Die Breite der Schaltfläche.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Framework `CMFCColorMenuButton` aufgerufen, wenn ein Objekt während des Werkzeugleistenanpassungsprozesses im Listenfeld angezeigt wird.

## <a name="cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a>CMFCColorMenuButton::OpenColorDialog

Öffnet ein Dialogfeld für die Farbauswahl.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parameter

*colorDefault*<br/>
[in] Die Im Dialogfeld Farbe ausgewählte Standardfarbe.

*colorRes*<br/>
[out] Gibt die Farbe zurück, die der Benutzer im Farbdialogfeld auswählt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn der Benutzer eine neue Farbe auswählt; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Wenn auf die Menüschaltfläche geklickt wird, rufen Sie diese Methode auf, um ein Farbdialogfeld zu öffnen. Wenn der Rückgabewert ungleich Null ist, wird die vom Benutzer ausgewählte Farbe im Parameter *colorRes* gespeichert. Verwenden Sie die [CMFCColorMenuButton::EnableOtherButton-Methode,](#enableotherbutton) um zwischen dem Standardfarbdialogfeld und dem Dialogfeld [CMFCColorDialog-Klasse](../../mfc/reference/cmfccolordialog-class.md) zu wechseln.

## <a name="cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a>CMFCColorMenuButton::SetColor

Legt die Farbe der aktuellen Farbschaltfläche fest.

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>Parameter

*Clr*<br/>
[in] Ein RGB-Farbwert.

*bNotify*<br/>
[in] TRUE, um die *Clr-Parameterfarbe* auf eine beliebige zugehörige Menüschaltfläche oder Symbolleistenschaltfläche anzuwenden; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Farbe der aktuellen Farbschaltfläche zu ändern. Wenn der Parameter *bNotify* ungleich Null ist, wird die Farbe der entsprechenden Schaltfläche in einem zugeordneten Popupmenü oder einer Symbolleiste in die durch den *Parameter clr* angegebene Farbe geändert.

## <a name="cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a>CMFCColorMenuButton::SetColorByCmdID

Legt die Farbe der angegebenen Farbmenüschaltfläche fest.

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>Parameter

*uiCmdID*<br/>
[in] Die Ressourcen-ID einer Farbmenüschaltfläche.

*Farbe*<br/>
[in] Ein RGB-Farbwert.

## <a name="cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorMenuButton::SetColorName

Legt einen neuen Namen für die angegebene Farbe fest.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Der RGB-Wert der Farbe, deren Name sich ändert.

*strName*<br/>
[in] Der neue Name der Farbe.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorMenuButton::SetColumnsNumber

Legt die Anzahl der Spalten fest, die in einem Farbauswahlsteuerelement [(CMFCColorBar-Objekt)](../../mfc/reference/cmfccolorbar-class.md) angezeigt werden sollen.

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parameter

*nColumns*<br/>
[in] Die Anzahl der anzuzeigenden Spalten.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar-Klasse](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog-Klasse](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton-Klasse](../../mfc/reference/cmfccolorbutton-class.md)
