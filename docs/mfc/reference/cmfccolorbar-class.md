---
title: Cmfccolorbar-Klasse
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
ms.openlocfilehash: ca28f8a07938e787fcf2d91d714c9dc82092194f
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561036"
---
# <a name="cmfccolorbar-class"></a>Cmfccolorbar-Klasse

Die `CMFCColorBar` Klasse stellt eine andockbare Steuerleiste dar, mit der Farben in einem Dokument oder einer Anwendung ausgewählt werden können.

## <a name="syntax"></a>Syntax

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmfccolorbar:: cmfccolorbar](#cmfccolorbar)|Erstellt ein `CMFCColorBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Cmfccolorbar:: contextbacksize](#contexttosize)|Berechnet die vertikalen und horizontalen Ränder, die erforderlich sind, um die Schaltflächen auf dem Farb leisten-Steuerelement zu enthalten, und passt dann die Position dieser Schaltflächen an.|
|[Cmfccolorbar:: kreatecontrol](#createcontrol)|Erstellt ein Farb leisten-Steuerelement Fenster, fügt es an das `CMFCColorBar` -Objekt an und ändert die Größe des-Steuer Elements, sodass es die angegebene Palette von Farben enthält.|
|[Cmfccolorbar:: Create](#create)|Erstellt ein Farb leisten-Steuerelement Fenster und fügt es an das- `CMFCColorBar` Objekt an.|
|[Cmfccolorbar:: enableautomaticbutton](#enableautomaticbutton)|Zeigt die Schaltfläche automatisch an oder blendet sie aus.|
|[Cmfccolorbar:: enableotherbutton](#enableotherbutton)|Aktiviert oder deaktiviert die Anzeige eines Dialog Felds, in dem Benutzer mehr Farben auswählen können.|
|[Cmfccolorbar:: GetColor](#getcolor)|Ruft die aktuell ausgewählte Farbe ab.|
|[Cmfccolorbar:: getcommandid](#getcommandid)|Ruft die Befehls-ID des aktuellen Farb leisten-Steuer Elements ab.|
|[Cmfccolorbar:: gethighlightedcolor](#gethighlightedcolor)|Ruft die Farbe ab, die angibt, dass eine Farb Schaltfläche den Fokus besitzt. Das heißt, die Schaltfläche ist " *Hot*".|
|[Cmfccolorbar:: gethorzmargin](#gethorzmargin)|Ruft den horizontalen Rand ab, der den Abstand zwischen der linken oder rechten farbzelle und der Client Bereichs Grenze darstellt.|
|[Cmfccolorbar:: getvertmargin](#getvertmargin)|Ruft den vertikalen Rand ab, der den Abstand zwischen der oberen oder untersten farbzelle und der Client Bereichs Grenze darstellt.|
|[Cmfccolorbar:: isTearOff](#istearoff)|Gibt an, ob die aktuelle Farbleiste Andock Bar ist.|
|[Cmfccolorbar:: setColor](#setcolor)|Legt die Farbe fest, die derzeit ausgewählt ist.|
|[Cmfccolorbar:: setcolorname](#setcolorname)|Legt einen neuen Namen für eine angegebene Farbe fest.|
|[Cmfccolorbar:: setcommandid](#setcommandid)|Legt eine neue Befehls-ID für ein Farb leisten-Steuerelement fest.|
|[Cmfccolorbar:: setdocumentcolors](#setdocumentcolors)|Legt die Liste der Farben fest, die im aktuellen Dokument verwendet werden.|
|[Cmfccolorbar:: Abbild-Rand](#sethorzmargin)|Legt den horizontalen Rand fest, der den Abstand zwischen der linken oder rechten farbzelle und der Client Bereichs Grenze darstellt.|
|[Cmfccolorbar:: setvertmargin](#setvertmargin)|Legt den vertikalen Rand fest. Hierbei handelt es sich um den Leerraum zwischen der oberen oder untersten farbzelle und der Grenze des Client Bereichs.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmfccolorbar:: Anpassungen](#adjustlocations)|Passt die Positionen der Farb Schaltflächen auf dem Farb leisten-Steuerelement an.|
|[Cmfccolorbar:: allowchangetextlabels](#allowchangetextlabels)|Gibt an, ob die Text Bezeichnung von Farb Schaltflächen geändert werden kann.|
|[Cmfccolorbar:: allowshowonlist](#allowshowonlist)|Gibt an, ob das Farb leisten-Steuerelement Objekt während des Anpassungs Vorgangs in einer Symbolleisten Liste angezeigt werden kann.|
|[Cmfccolorbar:: calcsize](#calcsize)|Wird von Framework als Teil des layoutberechnungs Prozesses aufgerufen.|
|[Cmfccolorbar:: CreatePalette](#createpalette)|Initialisiert eine Palette mit den Farben in einem angegebenen Array von Farben.|
|[Cmfccolorbar:: getcolorgridsize](#getcolorgridsize)|Berechnet die Anzahl der Zeilen und Spalten im Raster eines Farb leisten-Steuer Elements.|
|[Cmfccolorbar:: getextraheight](#getextraheight)|Berechnet die zusätzliche Höhe, die in der aktuellen Farbleiste zum Anzeigen verschiedener Benutzeroberflächen Elemente erforderlich ist, wie z. b. die **andere** Schaltfläche, Dokument Farben usw.|
|[Cmfccolorbar:: initcolors](#initcolors)|Initialisiert ein Array von Farben mit den Farben in einer angegebenen Palette oder der Standardpalette des Systems.|
|[Cmfccolorbar:: OnKey](#onkey)|Wird von Framework aufgerufen, wenn ein Benutzer eine Tastatur Taste drückt.|
|[Cmfccolorbar:: onsendcommand](#onsendcommand)|Wird von Framework aufgerufen, um eine Hierarchie von Popup Steuerelementen zu schließen.|
|[Cmfccolorbar:: OnUpdateCmdUI](#onupdatecmdui)|Wird von Framework aufgerufen, um ein Benutzeroberflächen Element eines Farb leisten-Steuer Elements zu aktivieren oder zu deaktivieren, bevor das Element angezeigt wird.|
|[Cmfccolorbar:: opencolordialog](#opencolordialog)|Öffnet ein Farb Dialogfeld.|
|[Cmfccolorbar:: Rebuild](#rebuild)|Zeichnet das Farb leisten-Steuerelement vollständig neu.|
|[Cmfccolorbar:: SelectPalette](#selectpalette)|Legt die logische Palette des angegebenen Geräte Kontexts auf die Palette der übergeordneten Schaltfläche des aktuellen Farb leisten-Steuer Elements fest.|
|[Cmfccolorbar:: setproplist](#setproplist)|Legt den `m_pWndPropList` geschützten Datenmember auf den angegebenen Zeiger auf ein Eigenschaften Raster-Steuerelement fest.|
|[Cmfccolorbar:: showcommandmessagestring](#showcommandmessagestring)|Fordert das Rahmen Fenster, das das Farb leisten-Steuerelement besitzt, zum Aktualisieren der Nachrichtenzeile in der Statusleiste auf.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|`m_bInternal`|Ein boolesches Feld, das bestimmt, ob Mausereignisse verarbeitet werden. Normalerweise werden Mausereignisse verarbeitet, wenn dieses Feld den Wert true hat und der Anpassungsmodus false ist.|
|`m_bIsEnabled`|Ein boolescher Wert, der angibt, ob ein-Steuerelement aktiviert ist.|
|`m_bIsTearOff`|Ein boolescher Wert, der angibt, ob das Farb leisten Steuerelement andocken unterstützt|
|`m_BoxSize`|Ein [CSize](../../atl-mfc-shared/reference/csize-class.md) -Objekt, das die Größe einer Zelle in einem Farb leisten Raster angibt.|
|`m_bShowDocColorsWhenDocked`|Ein boolescher Wert, der angibt, ob Dokument Farben angezeigt werden sollen, wenn die Farbleiste angedockt ist. Weitere Informationen finden Sie unter [cmfccolorbar:: setdocumentcolors](#setdocumentcolors).|
|`m_bStdColorDlg`|Ein boolescher Wert, der angibt, ob das Standard Dialogfeld für die System Farbe oder das Dialogfeld [cmfccolordialog](../../mfc/reference/cmfccolordialog-class.md) angezeigt werden soll. Weitere Informationen finden Sie unter [cmfccolorbar:: enableotherbutton](#enableotherbutton).|
|`m_ColorAutomatic`|Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der die aktuelle automatische Farbe speichert. Weitere Informationen finden Sie unter [cmfccolorbar:: enableotherbutton](#enableotherbutton).|
|`m_ColorNames`|Ein [cmap](../../mfc/reference/cmap-class.md) -Objekt, das einen Satz von RGB-Farben seinen Namen zuordnet.|
|`m_colors`|Ein [Karray](../../mfc/reference/carray-class.md) von [COLORREF](/windows/win32/gdi/colorref) -Werten, das die Farben enthält, die im Farb leisten-Steuerelement angezeigt werden.|
|`m_ColorSelected`|Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der die Farbe darstellt, die der Benutzer momentan aus dem Farb leisten-Steuerelement ausgewählt hat.|
|`m_lstDocColors`|Ein [CLIST](../../mfc/reference/clist-class.md) von [COLORREF](/windows/win32/gdi/colorref) -Werten, die die Farben enthalten, die derzeit in einem Dokument verwendet werden.|
|`m_nCommandID`|Eine Ganzzahl ohne Vorzeichen, die die Befehls-ID einer Farb Schaltfläche ist.|
|`m_nHorzMargin`|Eine ganze Zahl, die den horizontalen Rand zwischen den Farb Schaltflächen in einem Raster von Farben ist.|
|`m_nHorzOffset`|Eine ganze Zahl, die den horizontalen Offset zur Mitte der Farb Schaltfläche ist. Dieser Wert ist signifikant, wenn die Schaltfläche Text oder ein Bild zusätzlich zu einer Farbe anzeigt.|
|`m_nNumColumns`|Eine ganze Zahl, die die Anzahl der Spalten in einem Farb leisten-Steuerelement Raster von Farben ist.|
|`m_nNumColumnsVert`|Eine ganze Zahl, die die Anzahl der Spalten in einem vertikal ausgerichteten Raster von Farben ist.|
|`m_nNumRowsHorz`|Eine ganze Zahl, die die Anzahl der Spalten in einem horizontal ausgerichteten Raster von Farben ist.|
|`m_nRowHeight`|Eine ganze Zahl, die die Höhe einer Zeile mit Farb Schaltflächen in einem Raster von Farben ist.|
|`m_nVertMargin`|Eine ganze Zahl, die der vertikale Rand zwischen den Farb Schaltflächen in einem Raster von Farben ist.|
|`m_nVertOffset`|Eine ganze Zahl, die der vertikale Offset zur Mitte der Farb Schaltfläche ist. Dieser Wert ist signifikant, wenn die Schaltfläche Text oder ein Bild zusätzlich zu einer Farbe anzeigt.|
|`m_Palette`|Eine [CPalette](../../mfc/reference/cpalette-class.md) der Farben, die im Farb leisten-Steuerelement verwendet werden.|
|`m_pParentBtn`|Ein Zeiger auf ein [cmfccolorbutton](../../mfc/reference/cmfccolorbutton-class.md) -Objekt, das das übergeordnete Element der aktuellen Schaltfläche ist. Dieser Wert ist signifikant, wenn sich die Farb Schaltfläche in einer Hierarchie von Symbolleisten-Steuerelementen befindet oder sich in einem Farbeigenschaften Raster-Steuerelement|
|`m_pParentRibbonBtn`|Ein Zeiger auf ein [cmfcribboncolorbutton](../../mfc/reference/cmfcribboncolorbutton-class.md) -Objekt, das sich auf dem Menüband befindet und die übergeordnete Schaltfläche der aktuellen Schaltfläche ist. Dieser Wert ist signifikant, wenn sich die Farb Schaltfläche in einer Hierarchie von Symbolleisten-Steuerelementen befindet oder sich in einem Farbeigenschaften Raster-Steuerelement|
|`m_pWndPropList`|Ein Zeiger auf ein [cmfcpropertygridctrl](../../mfc/reference/cmfcpropertygridctrl-class.md) -Objekt.|
|`m_strAutoColor`|Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) , bei dem es sich um den Text handelt, der auf der **automatischen** Schaltfläche angezeigt wird. Weitere Informationen finden Sie unter [cmfccolorbar:: enableautomaticbutton](#enableautomaticbutton).|
|`m_strDocColors`|Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) , bei dem es sich um den Text handelt, der auf der Schaltfläche Dokument Farben angezeigt wird. Weitere Informationen finden Sie unter [cmfccolorbar:: setdocumentcolors](#setdocumentcolors).|
|`m_strOtherColor`|Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) , bei dem es sich um den Text handelt, der auf der *anderen* Schaltfläche angezeigt wird. Weitere Informationen finden Sie unter [cmfccolorbar:: enableotherbutton](#enableotherbutton).|

## <a name="remarks"></a>Bemerkungen

Normalerweise erstellen Sie kein- `CMFCColorBar` Objekt direkt. Stattdessen erstellt die [cmfccolormenubutton-Klasse](../../mfc/reference/cmfccolormenubutton-class.md) (die in Menüs und Symbolleisten verwendet wird) oder die [cmfccolorbutton-Klasse](../../mfc/reference/cmfccolorbutton-class.md) das- `CMFCColorBar` Objekt.

Die- `CMFCColorBar` Klasse bietet die folgenden Funktionen:

- Passt automatisch die Liste der Dokument Farben an.

- Speichert den Zustand und stellt ihn wieder her, sowie den Dokument Zustand.

- Verwaltet die Schaltfläche "automatisch".

- Verwendet das [cmfccolorpickerctrl-Klassen](../../mfc/reference/cmfccolorpickerctrl-class.md) Steuerelement, um eine benutzerdefinierte Farbe auszuwählen.

- Unterstützt den Zustand "Abbrechen" (wenn er mit der [cmfccolormenubutton-Klasse](../../mfc/reference/cmfccolormenubutton-class.md)erstellt wird).

So integrieren `CMFCColorBar` Sie die Funktionalität in Ihre Anwendung:

1. Erstellen Sie eine reguläre Menü Schaltfläche, und weisen Sie Ihr eine ID zu, beispielsweise ID_CHAR_COLOR.

1. Überschreiben Sie in der Rahmen Fenster Klasse die [CFrameWndEx:: onshowpopupmenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) -Methode, und ersetzen Sie die reguläre Menü Schaltfläche durch ein [cmfccolormenubutton-Klassen](../../mfc/reference/cmfccolormenubutton-class.md) Objekt (durch Aufrufen von [cmfctoolbar:: replacebutton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Legen Sie alle Stile fest, und aktivieren oder deaktivieren Sie die Funktionen des `CMFCColorBar` Objekts während der Erstellung der [cmfccolormenubutton-Klasse](../../mfc/reference/cmfccolormenubutton-class.md) . Das- `CMFCColorMenuButton` Objekt erstellt das-Objekt dynamisch, `CMFCColorBar` nachdem das Framework die-Methode aufgerufen hat `CreatePopupMenu` .

Wenn der Benutzer auf eine Farb leisten-Schaltfläche klickt, verwendet das Framework das- `ON_COMMAND` Makro, um das übergeordnete Element des Farb leisten-Steuer Elements zu benachrichtigen. Im-Makro ist der Befehls-ID-Parameter der Wert, den Sie in Schritt 1 der Farb leisten-Steuerelement Schaltfläche zugewiesen haben (ID_CHAR_COLOR in diesem Beispiel). Weitere Informationen finden Sie in den Klassen [cmfccolormenubutton](../../mfc/reference/cmfccolormenubutton-class.md), [cmfccolorbutton Class](../../mfc/reference/cmfccolorbutton-class.md), [cmfccolorpickerctrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)und [cmfctoolbar Class](../../mfc/reference/cmfctoolbar-class.md) .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie eine Farbleiste mithilfe verschiedener Methoden in der- `CMFCColorBar` Klasse konfiguriert wird. Mit den Methoden werden die horizontale und vertikale Ränder festgelegt, die andere Schaltfläche aktiviert, ein Farb leisten-Steuerelement Fenster erstellt und die aktuell ausgewählte Farbe festgelegt. Dieses Beispiel ist Teil des Beispiels " [neue Steuerelemente](../../overview/visual-cpp-samples.md)".

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[Cmfcbasetoolbar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcolorbar. h

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a> Cmfccolorbar:: Anpassungen

Passt die Positionen der Farb Schaltflächen auf dem Farb leisten-Steuerelement an.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von Framework während WM_SIZE Nachrichtenverarbeitung aufgerufen.

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a> Cmfccolorbar:: allowchangetextlabels

Gibt an, ob die Text Bezeichnung von Farb Schaltflächen geändert werden kann.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Rückgabewert

Immer FALSE

### <a name="remarks"></a>Bemerkungen

Standardmäßig gibt diese Methode immer false zurück, was bedeutet, dass Text Bezeichnungen nicht geändert werden können. Überschreiben Sie diese Methode, um das Ändern von Text Bezeichnungen zu aktivieren

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a> Cmfccolorbar:: allowshowonlist

Gibt an, ob das Farb leisten-Steuerelement Objekt während des Anpassungs Vorgangs in einer Symbolleisten Liste angezeigt werden kann.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Rückgabewert

Immer TRUE.

### <a name="remarks"></a>Bemerkungen

Standardmäßig gibt diese Methode immer true zurück, was bedeutet, dass das Framework während des Anpassungs Vorgangs das Farb leisten-Steuerelement anzeigen kann. Überschreiben Sie diese Methode, um ein anderes Verhalten zu implementieren.

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a> Cmfccolorbar:: calcsize

Wird von Framework als Teil des layoutberechnungs Prozesses aufgerufen.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parameter

*bvertdock*<br/>
in TRUE, um anzugeben, dass das Farb leisten-Steuerelement vertikal angedockt ist. FALSE, um anzugeben, dass das Farb leisten-Steuerelement horizontal angedockt wird.

### <a name="return-value"></a>Rückgabewert

Die Größe des Arrays von Farb Schaltflächen in einem Farb leisten-Steuerelement.

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a> Cmfccolorbar:: cmfccolorbar

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

*Ellen*<br/>
in Ein Array von Farben, das das Framework auf dem Farb leisten-Steuerelement anzeigt.

*color*<br/>
in Die anfangs ausgewählte Farbe.

*lpszautocolor*<br/>
in Die Text Bezeichnung der *automatischen* (Standard-) Farb Schaltfläche oder NULL.

Die Standard Bezeichnung für die automatische Schaltfläche ist **automatisch**.

*lpszothercolor*<br/>
in Die Text Bezeichnung der *anderen* Schaltfläche, die mehr Farboptionen anzeigt, oder NULL.

Die Standard Bezeichnung für die andere Schaltfläche ist **mehr Farben...**.

*lpszdoccolors*<br/>
in Die Text Bezeichnung der Schaltfläche "Dokument Farben". In der Palette Dokument Farben sind alle Farben aufgelistet, die im Dokument aktuell verwendet werden.

*lstdoccolors*<br/>
in Eine Liste der Farben, die das Dokument momentan verwendet.

*nColumns*<br/>
in Die Anzahl der Spalten, die das Array von Farben besitzt.

*nrowsdockhorz*<br/>
in Die Anzahl der Zeilen, die in der Farbleiste angezeigt werden, wenn Sie horizontal angedockt wird.

*ncoldockvert*<br/>
in Die Anzahl der Spalten, die in der Farbleiste angezeigt werden, wenn Sie vertikal angedockt ist.

*ColorAutomatic*<br/>
in Die Standardfarbe, die das Framework anwendet, wenn Sie auf die Schaltfläche automatisch klicken.

*nCommandID*<br/>
in Die Befehls-ID des Farb leisten-Steuer Elements.

*pbientbtn*<br/>
in Ein Zeiger auf eine übergeordnete Schaltfläche.

*src*<br/>
in Ein vorhandenes- `CMFCColorBar` Objekt, das in das neue-Objekt kopiert werden soll `CMFCColorBar` .

*uicommandid*<br/>
in Die Befehls-ID.

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a> Cmfccolorbar:: contextbacksize

Berechnet die vertikalen und horizontalen Ränder, die zum enthalten der Schaltflächen auf dem Farb leisten-Steuerelement erforderlich sind, und passt die Position dieser Schaltflächen an.

```cpp
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parameter

*bsquarebuttons*\
in TRUE, um anzugeben, dass die Form der Schaltflächen auf einem Farb leisten Steuerelement quadratisch ist. andernfalls false. Der Standardwert ist TRUE.

*bcenterbuttons*\
in TRUE, um anzugeben, dass der Inhalt auf der Vorderseite einer Farb leisten-Steuerelement Schaltfläche zentriert ist. andernfalls false. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbarcreate"></a><a name="create"></a> Cmfccolorbar:: Create

Erstellt ein Farb leisten-Steuerelement Fenster und fügt es an das- `CMFCColorBar` Objekt an.

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

*pparser*<br/>
in Zeiger auf das übergeordnete Fenster.

*dwstyle*<br/>
in Eine bitweise Kombination (or) von [Fenster Stilen](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
in Die Befehls-ID.

*pPalette*<br/>
in Zeiger auf eine Palette von Farben. Die Standardeinstellung ist NULL.

*nColumns*<br/>
in Die Anzahl der Spalten im Farb leisten-Steuerelement. Die Standardeinstellung ist 0.

*nrowsdockhorz*<br/>
in Die Anzahl der Zeilen im Farb leisten-Steuerelement, wenn es horizontal angedockt wird. Die Standardeinstellung ist 0.

*ncoldockvert*<br/>
in Die Anzahl der Spalten im Farb leisten-Steuerelement, wenn es vertikal angedockt wird. Die Standardeinstellung ist 0.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Um ein-Objekt zu erstellen, müssen Sie `CMFCColorBar` den Klassenkonstruktor und dann diese Methode abrufen. Die `Create` -Methode erstellt das Windows-Steuerelement und Initialisiert eine Liste mit Farben.

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a> Cmfccolorbar:: kreatecontrol

Erstellt ein Farb leisten-Steuerelement Fenster, fügt es an das `CMFCColorBar` -Objekt an und ändert die Größe des Steuerelement Fensters, sodass es die angegebene Palette von Farben enthält.

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parameter

*pparser*<br/>
in Zeiger auf das übergeordnete Fenster. Lässt keine NULL-Werte zu.

*Rect*<br/>
in Ein Begrenzungs Rechteck, das angibt, wo das Farb leisten Steuerelement gezeichnet werden soll.

*nID*<br/>
in Die Steuerelement-ID.

*nColumns*<br/>
in Die ideale Anzahl von Spalten im Farb leisten-Steuerelement. Diese Methode ändert diese Zahl, sodass Sie der angegebenen Palette von Farben entspricht. Der Standardwert ist-1. Dies bedeutet, dass dieser Parameter nicht angegeben wird.

*pPalette*<br/>
in Zeiger auf eine Palette von Farben oder NULL. Wenn dieser Parameter NULL ist, berechnet diese Methode die Größe des Farb leisten-Steuer Elements, als ob 20 Farben angegeben wurden. Die Standardeinstellung ist NULL.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die Parameter *Rect*, *nColumns*und *pPalette* , um die entsprechende Anzahl oder Zeilen und Spalten im Farb leisten-Steuerelement zu berechnen, und ruft dann die [cmfccolorbar:: Create](#create) -Methode auf.

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a> Cmfccolorbar:: CreatePalette

Initialisiert eine Palette mit den Farben in einem angegebenen Array von Farben.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parameter

*arcolors*\
in Ein Array von Farben.

*Messer*\
in Eine Palette von Farben.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a> Cmfccolorbar:: enableautomaticbutton

Zeigt die Schaltfläche automatisch an oder blendet sie aus.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszlabel*<br/>
in Die Text Bezeichnung der *automatischen* (Standard-) Farb Schaltfläche oder NULL.

Die Standard Bezeichnung für die automatische Schaltfläche ist **automatisch**.

*ColorAutomatic*<br/>
in Die Standardfarbe, die das Framework anwendet, wenn Sie auf die Schaltfläche automatisch klicken.

*benabel*<br/>
in TRUE, wenn die automatische Schaltfläche aktiviert werden soll. FALSE zum Deaktivieren der automatischen Schaltfläche. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Die Text Bezeichnung der automatischen Schaltfläche wird gelöscht, wenn der *lpszlabel* -Parameter NULL ist oder der *benable* -Parameter false ist.

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a> Cmfccolorbar:: enableotherbutton

Aktiviert oder deaktiviert die Anzeige eines Dialog Felds, in dem Benutzer mehr Farben auswählen können.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*lpszlabel*<br/>
in Die Text Bezeichnung der *anderen* Schaltfläche, die mehr Farboptionen anzeigt, oder NULL.

Die Standard Bezeichnung für diese Schaltfläche ist **mehr Farben...**.

*baltcolordlg*<br/>
in TRUE, wenn das Dialogfeld [cmfccolordialog](../../mfc/reference/cmfccolordialog-class.md) angezeigt werden soll. FALSE, um das Standard Dialogfeld [CColorDialog](../../mfc/reference/ccolordialog-class.md) anzuzeigen. Der Standardwert ist TRUE.

*benabel*<br/>
in TRUE, wenn die Schaltfläche aktiviert werden soll. FALSE, um die Schaltfläche zu deaktivieren. Der Standardwert ist TRUE.

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a> Cmfccolorbar:: GetColor

Ruft die aktuell ausgewählte Farbe ab.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuell ausgewählte Farbe.

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a> Cmfccolorbar:: getcolorgridsize

Berechnet die Anzahl der Zeilen und Spalten im Raster eines Farb leisten-Steuer Elements.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parameter

*bvertdock*\
in TRUE, um die Berechnung für ein vertikales angedocktes Farb leisten Steuerelement auszuführen. Andernfalls führen Sie die Berechnung für ein horizontal angedocktes Steuerelement aus.

### <a name="return-value"></a>Rückgabewert

Ein [CSize](../../atl-mfc-shared/reference/csize-class.md) -Objekt, dessen `cx` Komponente die Anzahl der Spalten enthält und deren `cy` Komponente die Anzahl der Zeilen enthält.

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a> Cmfccolorbar:: getcommandid

Ruft die Befehls-ID des aktuellen Farb leisten-Steuer Elements ab.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Befehls-ID.

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer eine neue Farbe auswählt, sendet das Framework die Befehls-ID in einer WM_COMMAND Nachricht, um das übergeordnete Element des Objekts zu benachrichtigen `CMFCColorBar` .

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a> Cmfccolorbar:: getextraheight

Berechnet die zusätzliche Höhe, die in der aktuellen Farbleiste zum Anzeigen verschiedener Elemente der Benutzeroberfläche erforderlich ist, z. b. die **anderen** Schaltflächen-oder Dokument Farben.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parameter

*nnumcolumns*\
in Wenn das Farb leisten-Steuerelement Dokument Farben enthält, wird die Anzahl der Spalten im Raster der Dokument Farben angezeigt. Andernfalls wird dieser Wert nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Die berechnete zusätzliche Höhe, die benötigt wird.

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a> Cmfccolorbar:: gethighlightedcolor

Ruft die Farbe ab, die angibt, dass eine Farb Schaltfläche den Fokus besitzt. Das heißt, die Schaltfläche ist " *Hot*".

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein RGB-Wert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a> Cmfccolorbar:: gethorzmargin

Ruft den horizontalen Rand ab, der den Abstand zwischen der linken oder rechten farbzelle und der Client Bereichs Grenze darstellt.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Rückgabewert

Der horizontale Rand.

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a> Cmfccolorbar:: getvertmargin

Ruft den vertikalen Rand ab, der den Abstand zwischen der oberen oder untersten farbzelle und der Client Bereichs Grenze darstellt.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Rückgabewert

Der vertikale Rand.

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a> Cmfccolorbar:: initcolors

Initialisiert ein Array von Farben mit den Farben in einer angegebenen Palette oder mit der Standardpalette des Systems.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parameter

*pPalette*\
in Ein Zeiger auf ein Palettenobjekt oder NULL. Wenn dieser Parameter NULL ist, verwendet diese Methode die Standardpalette des Betriebssystems.

*arcolors*\
in Ein Array von Farben.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Array von Farben.

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a> Cmfccolorbar:: isTearOff

Gibt an, ob die aktuelle Farbleiste Andock Bar ist.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das aktuelle Farb leisten Steuerelement Andock Bar ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn das Farb leisten-Steuerelement andockbar ist, kann es aus einer Steuerleiste entfernt und an einem anderen Speicherort angedockt werden.

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a> Cmfccolorbar:: OnKey

Wird von Framework aufgerufen, wenn ein Benutzer eine Tastatur Taste drückt.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parameter

*NCHAR*<br/>
in Der Code des virtuellen Schlüssels für den Schlüssel, den ein Benutzer gedrückt hat.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode den angegebenen Schlüssel verarbeitet. andernfalls false.

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a> Cmfccolorbar:: onsendcommand

Wird von Framework aufgerufen, um eine Hierarchie von Popup Steuerelementen zu schließen.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parameter

*pbutton*\
in Zeiger auf ein Steuerelement, das sich auf einer Symbolleiste befindet.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a> Cmfccolorbar:: OnUpdateCmdUI

Wird von Framework aufgerufen, um ein Benutzeroberflächen Element eines Farb leisten-Steuer Elements zu aktivieren oder zu deaktivieren, bevor das Element angezeigt wird.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parameter

*pTARGET*<br/>
in Zeiger auf ein Fenster, das ein zu aktualisierenden Benutzeroberflächen Element enthält.

*bdisableifnohndler*<br/>
in TRUE, wenn das Element der Benutzeroberfläche deaktiviert werden soll, wenn kein Handler in einer Meldungs Zuordnung definiert ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn ein Benutzer der Anwendung auf ein Benutzeroberflächen Element klickt, muss das Element wissen, ob es als aktiviert oder deaktiviert angezeigt werden soll. Das Ziel der Befehls Meldung liefert diese Informationen durch Implementieren eines ON_UPDATE_COMMAND_UI Befehls Handlers. Verwenden Sie diese Methode, um den Befehl zu verarbeiten. Weitere Informationen finden Sie unter [CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md).

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a> Cmfccolorbar:: opencolordialog

Öffnet ein Farb Dialogfeld.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parameter

*colordefault*<br/>
in Die Farbe, die standardmäßig ausgewählt wird, wenn das Dialogfeld Farbe geöffnet wird.

*colorres*<br/>
vorgenommen Die Farbe, die ein Benutzer ausgewählt hat.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Benutzer eine Farbe ausgewählt hat. FALSE, wenn der Benutzer das Dialogfeld Farbe abgebrochen hat.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a> Cmfccolorbar:: Rebuild

Zeichnet das Farb leisten-Steuerelement vollständig neu.

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a> Cmfccolorbar:: SelectPalette

Legt die logische Palette des angegebenen Geräte Kontexts auf die Palette der übergeordneten Schaltfläche des aktuellen Farb leisten-Steuer Elements fest.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*PDC*\
in Zeiger auf den Gerätekontext der übergeordneten Schaltfläche des aktuellen Farb leisten-Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Palette, die durch die Palette der übergeordneten Schaltfläche des aktuellen Farb leisten-Steuer Elements ersetzt wird.

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a> Cmfccolorbar:: setColor

Legt die Farbe fest, die derzeit ausgewählt ist.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*color*<br/>
in Ein RGB-Farbwert.

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a> Cmfccolorbar:: setcolorname

Legt einen neuen Namen für eine angegebene Farbe fest.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parameter

*color*<br/>
in Der RGB-Wert einer Farbe.

*strName*<br/>
in Der neue Name für die angegebene Farbe.

### <a name="remarks"></a>Bemerkungen

Diese Methode ändert den Namen der angegebenen Farbe in allen `CMFCColorBar` Objekten in der Anwendung.

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a> Cmfccolorbar:: setcommandid

Legt eine neue Befehls-ID für ein Farb leisten-Steuerelement fest.

```cpp
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parameter

*nCommandID*<br/>
in Eine Befehls-ID.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode können Sie die Befehls-ID eines Farb leisten-Steuer Elements ändern und das übergeordnete Fenster des Steuer Elements Benachrichtigen, dass sich die ID geändert hat.

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a> Cmfccolorbar:: setdocumentcolors

Legt die Liste der Farben fest, die im aktuellen Dokument verwendet werden.

```cpp
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parameter

*lpszcaption*<br/>
in Eine Beschriftung, die angezeigt wird, wenn das Farb leisten-Steuerelement nicht angedockt ist.

*lstdoccolors*<br/>
in Eine Liste von Farben, die die aktuellen Dokument Farben ersetzen.

*bShow-angedockt*<br/>
in TRUE, wenn die Dokument Farben angezeigt werden, wenn das Farb leisten Steuerelement angedockt ist. andernfalls false. Der Standardwert ist FALSE.

### <a name="remarks"></a>Bemerkungen

*Dokument Farben* sind die Farben, die derzeit in einem Dokument verwendet werden. Das Framework verwaltet automatisch eine Liste mit Dokument Farben, aber Sie können diese Methode verwenden, um die Liste zu ändern.

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a> Cmfccolorbar:: Abbild-Rand

Legt den horizontalen Rand fest. Hierbei handelt es sich um den Abstand zwischen der linken oder rechten farbzelle und der Grenze des Client Bereichs.

```cpp
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parameter

*nhorzmargin*<br/>
in Der horizontale Rand in Pixel.

### <a name="remarks"></a>Bemerkungen

Standardmäßig legt der [cmfccolorbar:: cmfccolorbar](#cmfccolorbar) -Konstruktor den horizontalen Rand auf 4 Pixel fest.

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a> Cmfccolorbar:: setproplist

Legt den `m_pWndPropList` geschützten Datenmember auf den angegebenen Zeiger auf ein Eigenschaften Raster-Steuerelement fest.

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parameter

*pwndlist*\
in Zeiger auf das Eigenschaften Raster-Steuerelement Objekt.

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a> Cmfccolorbar:: setvertmargin

Legt den vertikalen Rand fest. Hierbei handelt es sich um den Leerraum zwischen der oberen oder untersten farbzelle und der Grenze des Client Bereichs.

```cpp
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parameter

*nvertmargin*<br/>
in Der vertikale Rand in Pixel.

### <a name="remarks"></a>Bemerkungen

Standardmäßig legt der [cmfccolorbar:: cmfccolorbar](#cmfccolorbar) -Konstruktor den vertikalen Rand auf 4 Pixel fest.

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a> Cmfccolorbar:: showcommandmessagestring

Fordert das Rahmen Fenster, das das Farb leisten-Steuerelement besitzt, zum Aktualisieren der Nachrichtenzeile in der Statusleiste auf.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parameter

*uicmdid*<br/>
in Eine Befehls-ID. (Dieser Parameter wird ignoriert.)

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die WM_SETMESSAGESTRING Nachricht an den Besitzer des Farb leisten-Steuer Elements.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
