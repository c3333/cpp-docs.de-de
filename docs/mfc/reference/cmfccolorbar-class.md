---
title: CMFCColorBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
ms.openlocfilehash: 7b63fb66b800bd758c7f4c89c553e857ad9bbfbc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367767"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar-Klasse

Die `CMFCColorBar` Klasse stellt eine Andocksteuerungsleiste dar, die Farben in einem Dokument oder einer Anwendung auswählen kann.

## <a name="syntax"></a>Syntax

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|Erstellt ein `CMFCColorBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|Berechnet die vertikalen und horizontalen Ränder, die erforderlich sind, um die Schaltflächen auf dem Farbleistensteuerelement zu enthalten, und passt dann die Position dieser Schaltflächen an.|
|[CMFCColorBar::CreateControl](#createcontrol)|Erstellt ein Farbbalken-Steuerelementfenster, fügt `CMFCColorBar` es an das Objekt an, und ändert die Größe des Steuerelements so, dass es die angegebene Farbpalette enthält.|
|[CMFCColorBar::Erstellen](#create)|Erstellt ein Farbbalken-Steuerelementfenster und `CMFCColorBar` fügt es an das Objekt an.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Zeigt die automatische Schaltfläche ein oder blendet sie aus.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Aktiviert oder deaktiviert die Anzeige eines Dialogfelds, in dem der Benutzer weitere Farben auswählen kann.|
|[CMFCColorBar::GetColor](#getcolor)|Ruft die aktuell ausgewählte Farbe ab.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Ruft die Befehls-ID des aktuellen Farbleistensteuerelements ab.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Ruft die Farbe ab, die bedeutet, dass eine Farbschaltfläche den Fokus hat. das heißt, die Schaltfläche ist *heiß*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Ruft den horizontalen Rand ab, d. h. den Abstand zwischen der linken oder rechten Farbzelle und der Clientbereichsgrenze.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Ruft den vertikalen Rand ab, d. h. den Abstand zwischen der oberen oder unteren Farbzelle und der Clientbereichsgrenze.|
|[CMFCColorBar::Istearoff](#istearoff)|Gibt an, ob die aktuelle Farbleiste andockbar ist.|
|[CMFCColorBar::SetColor](#setcolor)|Legt die aktuell ausgewählte Farbe fest.|
|[CMFCColorBar::SetColorName](#setcolorname)|Legt einen neuen Namen für eine angegebene Farbe fest.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Legt eine neue Befehls-ID für ein Farbleistensteuerelement fest.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Legt die Liste der Farben fest, die im aktuellen Dokument verwendet werden.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Legt den horizontalen Rand fest, d. h. den Abstand zwischen der linken oder rechten Farbzelle und der Clientbereichsgrenze.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Legt den vertikalen Rand fest, d. h. den Abstand zwischen der oberen oder unteren Farbzelle und der Clientbereichsgrenze.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Passt die Positionen der Farbschaltflächen auf dem Farbleistensteuerelement an.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Gibt an, ob sich die Textbeschriftung von Farbschaltflächen ändern kann.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Gibt an, ob das Farbleistensteuerelementobjekt während des Anpassungsprozesses in einer Symbolleistenliste angezeigt werden kann.|
|[CMFCColorBar::CalcSize](#calcsize)|Wird vom Framework als Teil des Layoutberechnungsprozesses aufgerufen.|
|[CMFCColorBar::CreatePalette](#createpalette)|Initialisiert eine Palette mit den Farben in einem angegebenen Farbarray.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Berechnet die Anzahl der Zeilen und Spalten im Raster eines Farbbalkensteuerelements.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Berechnet die zusätzliche Höhe, die die aktuelle Farbleiste benötigt, um verschiedene Benutzeroberflächenelemente wie die Schaltfläche **Andere,** Dokumentfarben usw. anzuzeigen.|
|[CMFCColorBar::InitColors](#initcolors)|Initialisiert ein Array von Farben mit den Farben in einer angegebenen Palette oder der Systemstandardpalette.|
|[CMFCColorBar::OnKey](#onkey)|Wird vom Framework aufgerufen, wenn ein Benutzer eine Tastaturtaste drückt.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Wird vom Framework aufgerufen, um eine Hierarchie von Popup-Steuerelementen zu schließen.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Wird vom Framework aufgerufen, um ein Benutzeroberflächenelement eines Farbleistensteuerelements zu aktivieren oder zu deaktivieren, bevor das Element angezeigt wird.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Öffnet ein Farbdialogfeld.|
|[CMFCColorBar::Neuaufbau](#rebuild)|Zeichnet das Farbleistensteuerelement vollständig neu.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Legt die logische Palette des angegebenen Gerätekontexts auf die Palette der übergeordneten Schaltfläche des aktuellen Farbleistensteuerelements fest.|
|[CMFCColorBar::SetPropList](#setproplist)|Legt `m_pWndPropList` den geschützten Datenmember auf den angegebenen Zeiger auf ein Eigenschaftenrastersteuerelement fest.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Fordert das Rahmenfenster an, das das Farbleistensteuerelement besitzt, um die Meldungszeile in der Statusleiste zu aktualisieren.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|`m_bInternal`|Ein boolesches Feld, das bestimmt, ob Mausereignisse verarbeitet werden. In der Regel werden Mausereignisse verarbeitet, wenn dieses Feld TRUE und der Anpassungsmodus FALSE ist.|
|`m_bIsEnabled`|Ein boolescher Wert, der angibt, ob ein Steuerelement aktiviert ist.|
|`m_bIsTearOff`|Ein boolescher Wert, der angibt, ob das Farbleistensteuerelement das Andocken unterstützt.|
|`m_BoxSize`|Ein [CSize-Objekt,](../../atl-mfc-shared/reference/csize-class.md) das die Größe einer Zelle in einem Farbbalkenraster angibt.|
|`m_bShowDocColorsWhenDocked`|Ein boolescher Wert, der angibt, ob Dokumentfarben angezeigt werden sollen, wenn die Farbleiste angedockt ist. Weitere Informationen finden Sie unter [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Ein boolescher Wert, der angibt, ob das Standardmäßige Systemfarbdialogfeld oder das Dialogfeld [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) angezeigt werden soll. Weitere Informationen finden Sie unter [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|Ein [COLORREF,](/windows/win32/gdi/colorref) der die aktuelle automatische Farbe speichert. Weitere Informationen finden Sie unter [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|Ein [CMap-Objekt,](../../mfc/reference/cmap-class.md) das einen Satz von RGB-Farben ihren Namen zuordnet.|
|`m_colors`|Ein [CArray](../../mfc/reference/carray-class.md) von [COLORREF-Werten,](/windows/win32/gdi/colorref) das die Farben enthält, die im Farbleistensteuerelement angezeigt werden.|
|`m_ColorSelected`|Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die Farbe ist, die der Benutzer derzeit aus dem Farbbalkensteuerelement ausgewählt hat.|
|`m_lstDocColors`|Eine [CList](../../mfc/reference/clist-class.md) von [COLORREF-Werten,](/windows/win32/gdi/colorref) die die Farben enthält, die derzeit in einem Dokument verwendet werden.|
|`m_nCommandID`|Eine ganzzahlige Datei ohne Vorzeichen, die die Befehls-ID einer Farbschaltfläche ist.|
|`m_nHorzMargin`|Eine ganze Zahl, die den horizontalen Rand zwischen den Farbschaltflächen in einem Farbraster ist.|
|`m_nHorzOffset`|Eine ganze Zahl, die den horizontalen Versatz zur Mitte der Farbschaltfläche ist. Dieser Wert ist wichtig, wenn die Schaltfläche zusätzlich zu einer Farbe Text oder ein Bild anzeigt.|
|`m_nNumColumns`|Eine ganze Zahl, die die Anzahl der Spalten in einem Farbbalken-Steuerelementraster mit Farben ist.|
|`m_nNumColumnsVert`|Eine ganze Zahl, die die Anzahl der Spalten in einem vertikal ausgerichteten Raster mit Farben ist.|
|`m_nNumRowsHorz`|Eine ganze Zahl, die die Anzahl der Spalten in einem horizontal ausgerichteten Farbraster ist.|
|`m_nRowHeight`|Eine ganze Zahl, die die Höhe einer Reihe von Farbschaltflächen in einem Raster von Farben ist.|
|`m_nVertMargin`|Eine ganze Zahl, die den vertikalen Rand zwischen den Farbschaltflächen in einem Farbraster ist.|
|`m_nVertOffset`|Eine ganze Zahl, die den vertikalen Versatz zur Mitte der Farbschaltfläche ist. Dieser Wert ist wichtig, wenn die Schaltfläche zusätzlich zu einer Farbe Text oder ein Bild anzeigt.|
|`m_Palette`|Eine [CPalette](../../mfc/reference/cpalette-class.md) der Farben, die im Farbleistensteuerelement verwendet werden.|
|`m_pParentBtn`|Ein Zeiger auf ein [CMFCColorButton-Objekt,](../../mfc/reference/cmfccolorbutton-class.md) das das übergeordnete Element der aktuellen Schaltfläche ist. Dieser Wert ist wichtig, wenn sich die Farbschaltfläche in einer Hierarchie von Symbolleistensteuerelementen oder in einem Farbeigenschaftsrastersteuerelement befindet.|
|`m_pParentRibbonBtn`|Ein Zeiger auf ein [CMFCRibbonColorButton-Objekt,](../../mfc/reference/cmfcribboncolorbutton-class.md) das sich auf dem Menüband befindet und die übergeordnete Schaltfläche der aktuellen Schaltfläche ist. Dieser Wert ist wichtig, wenn sich die Farbschaltfläche in einer Hierarchie von Symbolleistensteuerelementen oder in einem Farbeigenschaftsrastersteuerelement befindet.|
|`m_pWndPropList`|Ein Zeiger auf ein [CMFCPropertyGridCtrl-Objekt.](../../mfc/reference/cmfcpropertygridctrl-class.md)|
|`m_strAutoColor`|Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der der Text ist, der auf der Schaltfläche **Automatisch** angezeigt wird. Weitere Informationen finden Sie unter [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der der Text ist, der auf der Schaltfläche "Dokumentfarben" angezeigt wird. Weitere Informationen finden Sie unter [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der der Text ist, der auf der *anderen* Schaltfläche angezeigt wird. Weitere Informationen finden Sie unter [CMFCColorBar::EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Bemerkungen

Normalerweise erstellen Sie ein `CMFCColorBar` Objekt nicht direkt. Stattdessen erstellt die [CMFCColorMenuButton-Klasse](../../mfc/reference/cmfccolormenubutton-class.md) (in Menüs und Symbolleisten) oder `CMFCColorBar` die [CMFCColorButton-Klasse](../../mfc/reference/cmfccolorbutton-class.md) das Objekt.

Die `CMFCColorBar` Klasse bietet die folgenden Funktionen:

- Passt die Liste der Dokumentfarben automatisch an.

- Speichert und stellt den Status zusammen mit dem Dokumentstatus wieder her.

- Verwaltet die Schaltfläche "automatisch".

- Verwendet das [CmFCColorPickerCtrl-Klassensteuerelement,](../../mfc/reference/cmfccolorpickerctrl-class.md) um eine benutzerdefinierte Farbe auszuwählen.

- Unterstützt einen "Tear-off"-Status (wenn er mithilfe der [CMFCColorMenuButton-Klasse](../../mfc/reference/cmfccolormenubutton-class.md)erstellt wird).

So integrieren `CMFCColorBar` Sie die Funktionalität in Ihre Anwendung:

1. Erstellen Sie eine normale Menüschaltfläche und weisen Sie ihr eine ID zu, z. B. ID_CHAR_COLOR.

1. Überschreiben Sie in ihrer Framefensterklasse die [CFrameWndEx::OnShowPopupMenu-Methode,](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) und ersetzen Sie die reguläre Menüschaltfläche durch ein [CMFCColorMenuButton-Klassenobjekt](../../mfc/reference/cmfccolormenubutton-class.md) (durch Aufrufen von [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Legen Sie alle Stile fest, und `CMFCColorBar` aktivieren oder deaktivieren Sie die Features des Objekts während der Erstellung der [CMFCColorMenuButton-Klasse.](../../mfc/reference/cmfccolormenubutton-class.md) Das `CMFCColorMenuButton` Objekt erstellt `CMFCColorBar` das Objekt dynamisch, nachdem das Framework die `CreatePopupMenu` Methode aufruft.

Wenn der Benutzer auf eine Schaltfläche für die `ON_COMMAND` Farbleiste-Steuerung klickt, verwendet das Framework das Makro, um das übergeordnete Steuerelement des Farbleistensteuerelements zu benachrichtigen. Im Makro ist der Befehls-ID-Parameter der Wert, den Sie der Schaltfläche "Farbbalkensteuerung" in Schritt 1 zugewiesen haben (ID_CHAR_COLOR in diesem Beispiel). Weitere Informationen finden Sie in den Klassen [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButtonButton Class](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)und [CMFCToolBar Class.](../../mfc/reference/cmfctoolbar-class.md)

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie sie eine `CMFCColorBar` Farbleiste mithilfe verschiedener Methoden in der Klasse konfigurieren. Die Methoden legen die horizontalen und vertikalen Ränder fest, aktivieren die andere Schaltfläche, erstellen ein Farbbalken-Steuerfenster und legen die aktuell ausgewählte Farbe fest. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxcolorbar.h

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a>CMFCColorBar::AdjustLocations

Passt die Positionen der Farbschaltflächen auf dem Farbleistensteuerelement an.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird während der WM_SIZE Nachrichtenverarbeitung vom Framework aufgerufen.

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels

Gibt an, ob sich die Textbeschriftung von Farbschaltflächen ändern kann.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Rückgabewert

Immer FALSE

### <a name="remarks"></a>Bemerkungen

Standardmäßig gibt diese Methode immer FALSE zurück, was bedeutet, dass Textbeschriftungen nicht geändert werden können. Überschreiben Sie diese Methode, um das Ändern von Textbeschriftungen zu aktivieren.

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList

Gibt an, ob das Farbleistensteuerelementobjekt während des Anpassungsprozesses in einer Symbolleistenliste angezeigt werden kann.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Rückgabewert

Immer TRUE.

### <a name="remarks"></a>Bemerkungen

Standardmäßig gibt diese Methode immer TRUE zurück, was bedeutet, dass das Framework das Farbleistensteuerelement während des Anpassungsprozesses anzeigen kann. Überschreiben Sie diese Methode, um ein anderes Verhalten zu implementieren.

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a>CMFCColorBar::CalcSize

Wird vom Framework als Teil des Layoutberechnungsprozesses aufgerufen.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parameter

*bVertDock*<br/>
[in] TRUE, um anzugeben, dass das Farbbalkensteuerelement vertikal angedockt ist; FALSE, um anzugeben, dass das Farbbalkensteuerelement horizontal angedockt ist.

### <a name="return-value"></a>Rückgabewert

Die Größe des Arrays von Farbschaltflächen in einem Farbleistensteuerelement.

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar

Erstellt ein `CMFCColorBar`-Objekt.

```
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    int nRowsDockHorz,
    int nColDockVert,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCColorButton* pParentBtn);

CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCRibbonColorButton* pParentRibbonBtn);

CMFCColorBar(
    CMFCColorBar& src,
    UINT uiCommandID);
```

### <a name="parameters"></a>Parameter

*Farben*<br/>
[in] Ein Array von Farben, das das Framework auf dem Farbleistensteuerelement anzeigt.

*Farbe*<br/>
[in] Die ursprünglich ausgewählte Farbe.

*lpszAutoColor*<br/>
[in] Die Textbeschriftung der *automatischen* (Standard-)Farbschaltfläche (NULL).

Das Standardetikett für die automatische Taste ist **Automatisch**.

*lpszOtherColor*<br/>
[in] Die Textbeschriftung der *anderen* Schaltfläche, die mehr Farbauswahlen anzeigt, oder NULL.

Die Standardbeschriftung für die andere Schaltfläche ist **More Colors...**.

*lpszDocColors*<br/>
[in] Die Textbeschriftung der Schaltfläche "Dokumentfarben". In der Palette der Dokumentfarben werden alle Farben aufgelistet, die das Dokument derzeit verwendet.

*lstDocColors*<br/>
[in] Eine Liste der Farben, die das Dokument derzeit verwendet.

*nColumns*<br/>
[in] Die Anzahl der Spalten, die das Farbarray enthält.

*nRowsDockHorz*<br/>
[in] Die Anzahl der Zeilen, die die Farbleiste hat, wenn sie horizontal angedockt wird.

*nColDockVert*<br/>
[in] Die Anzahl der Spalten, die die Farbleiste enthält, wenn sie vertikal angedockt wird.

*colorAutomatic*<br/>
[in] Die Standardfarbe, die das Framework anwendet, wenn Sie auf die automatische Schaltfläche klicken.

*nCommandID*<br/>
[in] Die Befehls-ID für die Farbleistesteuerung.

*pParentBtn*<br/>
[in] Ein Zeiger auf eine übergeordnete Schaltfläche.

*src*<br/>
[in] Ein `CMFCColorBar` vorhandenes Objekt, das `CMFCColorBar` in das neue Objekt kopiert werden soll.

*uiCommandID*<br/>
[in] Die Befehls-ID.

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a>CMFCColorBar::ContextToSize

Berechnet die vertikalen und horizontalen Ränder, die erforderlich sind, um die Schaltflächen im Farbleistensteuerelement zu enthalten, und passt die Position dieser Schaltflächen an.

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*bSquareButtons*|[in] TRUE, um anzugeben, dass die Form der Schaltflächen auf einem Farbbalkensteuerelement quadratisch ist; andernfalls FALSE. Der Standardwert ist TRUE.|
|*bCenterButtons*|[in] TRUE, um anzugeben, dass der Inhalt auf der Fläche einer Farbleisten-Steuerelementschaltfläche zentriert ist; andernfalls FALSE. Der Standardwert ist TRUE.|

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbarcreate"></a><a name="create"></a>CMFCColorBar::Erstellen

Erstellt ein Farbbalken-Steuerelementfenster und `CMFCColorBar` fügt es an das Objekt an.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID,
    CPalette* pPalette=NULL,
    int nColumns=0,
    int nRowsDockHorz=0,
    int nColDockVert=0);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
[in] Zeiger auf das übergeordnete Fenster.

*dwStyle*<br/>
[in] Eine bitweise Kombination (OR) von [Fensterstilen](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
[in] Die Befehls-ID.

*pPalette*<br/>
[in] Zeiger auf eine Farbpalette. Die Standardeinstellung ist NULL.

*nColumns*<br/>
[in] Die Anzahl der Spalten im Farbleistensteuerelement. Die Standardeinstellung ist 0.

*nRowsDockHorz*<br/>
[in] Die Anzahl der Zeilen im Farbleistensteuerelement, wenn es horizontal angedockt wird. Die Standardeinstellung ist 0.

*nColDockVert*<br/>
[in] Die Anzahl der Spalten im Farbbalkensteuerelement, wenn es vertikal angedockt wird. Die Standardeinstellung ist 0.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Um ein `CMFCColorBar` Objekt zu erstellen, rufen Sie den Klassenkonstruktor dann diese Methode auf. Die `Create` Methode erstellt das Windows-Steuerelement und initialisiert eine Liste von Farben.

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a>CMFCColorBar::CreateControl

Erstellt ein Farbleisten-Steuerelementfenster, fügt `CMFCColorBar` es an das Objekt an, und ändert die Größe des Steuerelementfensters so, dass es die angegebene Farbpalette enthält.

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
[in] Zeiger auf das übergeordnete Fenster. Lässt keine NULL-Werte zu.

*Rect*<br/>
[in] Ein umgrenzendes Rechteck, das angibt, wo das Farbbalkensteuerelement gezeichnet werden soll.

*nID*<br/>
[in] Die Steuerelement-ID.

*nColumns*<br/>
[in] Die ideale Anzahl von Spalten im Farbleistensteuerelement. Diese Methode ändert diese Zahl an die angegebene Farbpalette. Der Standardwert ist -1, d. h. dieser Parameter ist nicht angegeben.

*pPalette*<br/>
[in] Zeiger auf eine Farbpalette oder NULL. Wenn dieser Parameter NULL ist, berechnet diese Methode die Größe des Farbbalkensteuerelements, als ob 20 Farben angegeben worden wären. Die Standardeinstellung ist NULL.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die Parameter *rect*, *nColumns*und *pPalette,* um die entsprechende Zahl oder Zeilen und Spalten im Farbleistensteuerelement zu berechnen, und ruft dann die [CMFCColorBar::Create-Methode](#create) auf.

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a>CMFCColorBar::CreatePalette

Initialisiert eine Palette mit den Farben in einem angegebenen Farbarray.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*arColors*|[in] Ein Array von Farben.|
|*Palette (palette)*|[in] Eine Farbpalette.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton

Zeigt die automatische Schaltfläche ein oder blendet sie aus.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Die Textbeschriftung der *automatischen* (Standard-)Farbschaltfläche (NULL).

Das Standardetikett für die automatische Taste ist **Automatisch**.

*colorAutomatic*<br/>
[in] Die Standardfarbe, die das Framework anwendet, wenn Sie auf die automatische Schaltfläche klicken.

*bEnable*<br/>
[in] TRUE, um die automatische Taste zu aktivieren; FALSE, um die automatische Schaltfläche zu deaktivieren. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Die Textbeschriftung der automatischen Schaltfläche wird gelöscht, wenn der Parameter *lpszLabel* NULL oder der *Parameter bEnable* FALSE ist.

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton

Aktiviert oder deaktiviert die Anzeige eines Dialogfelds, in dem der Benutzer weitere Farben auswählen kann.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Die Textbeschriftung der *anderen* Schaltfläche, die mehr Farbauswahlen anzeigt, oder NULL.

Die Standardbezeichnung für diese Schaltfläche ist **Mehr Farben...**.

*bAltColorDlg*<br/>
[in] TRUE, um das Dialogfeld [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) anzuzeigen; FALSE, um das standardmäßige [Dialogfeld CColorDialog](../../mfc/reference/ccolordialog-class.md) anzuzeigen. Der Standardwert ist TRUE.

*bEnable*<br/>
[in] TRUE, um die Schaltfläche zu aktivieren; FALSE, um die Schaltfläche zu deaktivieren. Der Standardwert ist TRUE.

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a>CMFCColorBar::GetColor

Ruft die aktuell ausgewählte Farbe ab.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuell ausgewählte Farbe.

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a>CMFCColorBar::GetColorGridSize

Berechnet die Anzahl der Zeilen und Spalten im Raster eines Farbbalkensteuerelements.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*bVertDock*|[in] TRUE, um die Berechnung für ein vertikal angedocktes Farbbalkensteuerelement durchzuführen; Andernfalls führen Sie die Berechnung für ein horizontal angedocktes Steuerelement aus.|

### <a name="return-value"></a>Rückgabewert

Ein [CSize-Objekt,](../../atl-mfc-shared/reference/csize-class.md) dessen `cx` Komponente die `cy` Anzahl der Spalten und die Komponente die Anzahl der Zeilen enthält.

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a>CMFCColorBar::GetCommandID

Ruft die Befehls-ID des aktuellen Farbleistensteuerelements ab.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Befehls-ID.

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer eine neue Farbe auswählt, sendet das Framework die Befehls-ID in einer WM_COMMAND Nachricht, um das übergeordnete Element des `CMFCColorBar` Objekts zu benachrichtigen.

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a>CMFCColorBar::GetExtraHeight

Berechnet die zusätzliche Höhe, die die aktuelle Farbleiste benötigt, um verschiedene Benutzeroberflächenelemente anzuzeigen, z. B. die Schaltfläche **Andere** oder Dokumentfarben.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*nNumColumns*|[in] Wenn das Farbleistensteuerelement Dokumentfarben enthält, wird die Anzahl der Spalten angezeigt, die im Raster der Dokumentfarben angezeigt werden sollen. Andernfalls wird dieser Wert nicht verwendet.|

### <a name="return-value"></a>Rückgabewert

Die berechnete zusätzliche Höhe, die erforderlich ist.

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor

Ruft die Farbe ab, die bedeutet, dass eine Farbschaltfläche den Fokus hat. das heißt, die Schaltfläche ist *heiß*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein RGB-Wert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin

Ruft den horizontalen Rand ab, d. h. den Abstand zwischen der linken oder rechten Farbzelle und der Clientbereichsgrenze.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Rückgabewert

Der horizontale Rand.

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a>CMFCColorBar::GetVertMargin

Ruft den vertikalen Rand ab, d. h. den Abstand zwischen der oberen oder unteren Farbzelle und der Clientbereichsgrenze.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Rückgabewert

Der vertikale Rand.

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a>CMFCColorBar::InitColors

Initialisiert ein Array von Farben mit den Farben in einer angegebenen Palette oder mit der Systemstandardpalette.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pPalette*|[in] Ein Zeiger auf ein Palettenobjekt oder NULL. Wenn dieser Parameter NULL ist, verwendet diese Methode die Standardpalette des Betriebssystems.|
|*arColors*|[in] Ein Array von Farben.|

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Farbfeld.

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a>CMFCColorBar::Istearoff

Gibt an, ob die aktuelle Farbleiste andockbar ist.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das aktuelle Farbleistensteuerelement andockbar ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn das Farbleistensteuerelement andockbar ist, kann es von einer Steuerleiste abgerissen und an eine andere Position angedockt werden.

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a>CMFCColorBar::OnKey

Wird vom Framework aufgerufen, wenn ein Benutzer eine Tastaturtaste drückt.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parameter

*Nchar*<br/>
[in] Der Virtuelle-Schlüssel-Code für die Taste, die ein Benutzer gedrückt hat.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode den angegebenen Schlüssel verarbeitet; andernfalls FALSE.

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a>CMFCColorBar::OnSendCommand

Wird vom Framework aufgerufen, um eine Hierarchie von Popup-Steuerelementen zu schließen.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pButton*|[in] Zeiger auf ein Steuerelement, das sich auf einer Symbolleiste befindet.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI

Wird vom Framework aufgerufen, um ein Benutzeroberflächenelement eines Farbleistensteuerelements zu aktivieren oder zu deaktivieren, bevor das Element angezeigt wird.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parameter

*pTarget*<br/>
[in] Zeiger auf ein Fenster, das ein zu aktualisierendes Benutzeroberflächenelement enthält.

*bDisableIfNoHndler*<br/>
[in] TRUE, um das Benutzeroberflächenelement zu deaktivieren, wenn in einer Nachrichtenzuordnung kein Handler definiert ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn ein Benutzer Ihrer Anwendung auf ein Element der Benutzeroberfläche klickt, muss das Element wissen, ob es als aktiviert oder deaktiviert angezeigt werden soll. Das Ziel der Befehlsnachricht stellt diese Informationen bereit, indem ein ON_UPDATE_COMMAND_UI Befehlshandler implementiert wird. Verwenden Sie diese Methode, um den Befehl zu verarbeiten. Weitere Informationen finden Sie unter [CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md).

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a>CMFCColorBar::OpenColorDialog

Öffnet ein Farbdialogfeld.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parameter

*colorDefault*<br/>
[in] Die Farbe, die standardmäßig ausgewählt wird, wenn das Farbdialogfeld geöffnet wird.

*colorRes*<br/>
[out] Die Farbe, die ein Benutzer ausgewählt hat.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Benutzer eine Farbe ausgewählt hat; FALSE, wenn der Benutzer das Farbdialogfeld abgebrochen hat.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a>CMFCColorBar::Neuaufbau

Zeichnet das Farbleistensteuerelement vollständig neu.

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a>CMFCColorBar::SelectPalette

Legt die logische Palette des angegebenen Gerätekontexts auf die Palette der übergeordneten Schaltfläche des aktuellen Farbleistensteuerelements fest.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pDC*|[in] Zeiger auf den Gerätekontext der übergeordneten Schaltfläche des aktuellen Farbleistensteuerelements.|

### <a name="return-value"></a>Rückgabewert

Zeigen Sie mit dem Mauszeiger auf die Palette, die durch die Palette der übergeordneten Schaltfläche des aktuellen Farbleistensteuerelements ersetzt wird.

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a>CMFCColorBar::SetColor

Legt die aktuell ausgewählte Farbe fest.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Ein RGB-Farbwert.

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a>CMFCColorBar::SetColorName

Legt einen neuen Namen für eine angegebene Farbe fest.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Der RGB-Wert einer Farbe.

*strName*<br/>
[in] Der neue Name für die angegebene Farbe.

### <a name="remarks"></a>Bemerkungen

Diese Methode ändert den Namen der `CMFCColorBar` angegebenen Farbe in allen Objekten in der Anwendung.

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a>CMFCColorBar::SetCommandID

Legt eine neue Befehls-ID für ein Farbleistensteuerelement fest.

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parameter

*nCommandID*<br/>
[in] Eine Befehls-ID.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Befehls-ID eines Farbleistensteuerelements zu ändern und das übergeordnete Fenster des Steuerelements zu benachrichtigen, dass sich die ID geändert hat.

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors

Legt die Liste der Farben fest, die im aktuellen Dokument verwendet werden.

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parameter

*lpszCaption*<br/>
[in] Eine Beschriftung, die angezeigt wird, wenn das Farbleistensteuerelement nicht angedockt ist.

*lstDocColors*<br/>
[in] Eine Liste von Farben, die die aktuellen Dokumentfarben ersetzt.

*bShowWhenDocked*<br/>
[in] TRUE, um Dokumentfarben anzuzeigen, wenn das Farbleistensteuerelement angedockt ist; andernfalls FALSE. Der Standardwert ist FALSE.

### <a name="remarks"></a>Bemerkungen

*Dokumentfarben* sind die Farben, die derzeit in einem Dokument verwendet werden. Das Framework verwaltet automatisch eine Liste von Dokumentfarben, aber Sie können diese Methode verwenden, um die Liste zu ändern.

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin

Legt den horizontalen Rand fest, d. h. den Abstand zwischen der linken oder rechten Farbzelle und der Begrenzung des Clientbereichs.

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parameter

*nHorzMargin*<br/>
[in] Der horizontale Rand in Pixel.

### <a name="remarks"></a>Bemerkungen

Standardmäßig legt der [CmFCColorBar::CMFCColorBar-Konstruktor](#cmfccolorbar) den horizontalen Rand auf 4 Pixel fest.

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a>CMFCColorBar::SetPropList

Legt `m_pWndPropList` den geschützten Datenmember auf den angegebenen Zeiger auf ein Eigenschaftenrastersteuerelement fest.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pWndList*|[in] Zeiger auf das Eigenschaftenraster-Steuerelementobjekt.|

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a>CMFCColorBar::SetVertMargin

Legt den vertikalen Rand fest, d. h. den Abstand zwischen der oberen oder unteren Farbzelle und der Clientbereichsgrenze.

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parameter

*nVertMargin*<br/>
[in] Der vertikale Rand in Pixel.

### <a name="remarks"></a>Bemerkungen

Standardmäßig legt der [CmFCColorBar::CMFCColorBar-Konstruktor](#cmfccolorbar) den vertikalen Rand auf 4 Pixel fest.

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString

Fordert das Rahmenfenster an, das das Farbleistensteuerelement besitzt, um die Meldungszeile in der Statusleiste zu aktualisieren.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parameter

*uiCmdId*<br/>
[in] Eine Befehls-ID. (Dieser Parameter wird ignoriert.)

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die WM_SETMESSAGESTRING Nachricht an den Besitzer des Farbleistensteuerelements.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
