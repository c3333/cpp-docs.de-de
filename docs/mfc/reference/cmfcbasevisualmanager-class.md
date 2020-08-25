---
title: Cmfcbasevisualmanager-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
ms.openlocfilehash: 79a3c0945fdd0df04e9ee52d7bad97dc0847fa91
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834296"
---
# <a name="cmfcbasevisualmanager-class"></a>Cmfcbasevisualmanager-Klasse

Eine Ebene zwischen abgeleiteten visuellen Managern und der Windows-Theme-API.

`CMFCBaseVisualManager` lädt UxTheme.dll, falls verfügbar, und verwaltet den Zugriff auf die API-Methoden des Windows-Designs.

Diese Klasse ist nur für die interne Verwendung vorgesehen.

## <a name="syntax"></a>Syntax

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|[Cmfcbasevisualmanager:: cmfcbasevisualmanager](#cmfcbasevisualmanager)|Erstellt und initialisiert ein `CMFCBaseVisualManager`-Objekt.|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[Cmfcbasevisualmanager::D rawcheckbox](#drawcheckbox)|Zeichnet ein Kontrollkästchen-Steuerelement mithilfe des aktuellen Windows-Designs.|
|[Cmfcbasevisualmanager::D rawcomboborder](#drawcomboborder)|Zeichnet einen Kombinations Feld Rahmen mithilfe des aktuellen Windows-Designs.|
|[Cmfcbasevisualmanager::D rawcombodropbutton](#drawcombodropbutton)|Zeichnet eine Kombinations Feld-Dropdown Schaltfläche mithilfe des aktuellen Windows-Designs.|
|[Cmfcbasevisualmanager::D rawpushbutton](#drawpushbutton)|Zeichnet eine Schaltfläche mit dem aktuellen Windows-Design.|
|[Cmfcbasevisualmanager::D rawradio Button](#drawradiobutton)|Zeichnet ein Optionsfeld-Steuerelement mithilfe des aktuellen Windows-Designs.|
|[Cmfcbasevisualmanager::D rawstatusbarprogress](#drawstatusbarprogress)|Zeichnet eine Statusleiste in einem Status leisten-Steuerelement ( [cmfcstatusbar-Klasse](../../mfc/reference/cmfcstatusbar-class.md)) unter Verwendung des aktuellen Windows-Designs.|
|[Cmfcbasevisualmanager:: fillrebarpane](#fillrebarpane)|Füllt den Hintergrund des Grund leisten-Steuer Elements mithilfe des aktuellen Windows-Designs.|
|[Cmfcbasevisualmanager:: getstandardwindowstheme](#getstandardwindowstheme)|Ruft das aktuelle Windows-Design ab.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|-|-|
|[Cmfcbasevisualmanager:: cleanupthemes](#cleanupthemes)|Ruft `CloseThemeData` für alle in abgerufenen Handles auf `UpdateSystemColors` .|
|[Cmfcbasevisualmanager:: updatesystemcolors](#updatesystemcolors)|Aufrufe `OpenThemeData` zum Abrufen von Handles zum Zeichnen verschiedener Steuerelemente: Fenster, Symbolleisten, Schaltflächen usw.|

## <a name="remarks"></a>Bemerkungen

Es ist nicht erforderlich, Objekte dieser Klasse direkt zu instanziieren.

Da es sich um eine Basisklasse für alle visuellen Manager handelt, können Sie einfach [CMFCVisualManager:: GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)aufrufen, einen Zeiger auf den aktuellen visuellen Manager abrufen und auf die Methoden zum `CMFCBaseVisualManager` verwenden dieses Zeigers zugreifen. Wenn Sie jedoch ein Steuerelement mit dem aktuellen Windows-Design anzeigen müssen, ist es besser, die- `CMFCVisualManagerWindows` Schnittstelle zu verwenden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[Cmfcbasevisualmanager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxvisualmanager. h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a> Cmfcbasevisualmanager:: cleanupthemes

Ruft `CloseThemeData` für alle in abgerufenen Handles auf `UpdateSystemColors` .

```cpp
void CleanUpThemes();
```

### <a name="remarks"></a>Bemerkungen

Nur für interne Verwendung.

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a> Cmfcbasevisualmanager:: cmfcbasevisualmanager

Erstellt und initialisiert ein `CMFCBaseVisualManager`-Objekt.

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a> Cmfcbasevisualmanager::D rawcheckbox

Zeichnet ein Kontrollkästchen-Steuerelement mithilfe des aktuellen Windows-Designs.

```
virtual BOOL DrawCheckBox(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    int nState,
    BOOL bEnabled,
    BOOL bPressed);

);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
in Ein Zeiger auf einen Gerätekontext

*Rect*<br/>
in Das umgebende Rechteck des Kontrollkästchens.

*bhervor gehoben*<br/>
in Gibt an, ob das Kontrollkästchen markiert ist.

*nstatusinformationen*<br/>
[in] 0 für deaktiviert, 1 für aktivierte normale,

2 für gemischtes normales.

*benabled*<br/>
in Gibt an, ob das Kontrollkästchen aktiviert ist.

*bgedrückt*<br/>
in Gibt an, ob das Kontrollkästchen gedrückt ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Die Werte von *nState* entsprechen den folgenden Kontrollkästchen-Stilen.

|nstatusinformationen|Kontrollkästchen Stil|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a> Cmfcbasevisualmanager::D rawcomboborder

Zeichnet den Kombinations Feld Rahmen mithilfe des aktuellen Windows-Designs.

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
in Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
in Umschließendes Rechteck des Kombinations Feld Rahmens.

*bDeaktiviert*<br/>
in Gibt an, ob der Kombinations Feld Rahmen deaktiviert ist.

*bisdrop*<br/>
in Gibt an, ob der Kombinations Feld Rahmen nach unten gelöscht wird.

*bishighbeleuchtet*<br/>
in Gibt an, ob der Kombinations Feld Rahmen hervorgehoben ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist. andernfalls false.

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a> Cmfcbasevisualmanager::D rawcombodropbutton

Zeichnet eine Kombinations Feld-Dropdown Schaltfläche mithilfe des aktuellen Windows-Designs.

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parameter

*PDC*\
in Ein Zeiger auf einen Gerätekontext.

*Rect*\
in Das umgebende Rechteck der Dropdown Schaltfläche für das Kombinations Feld.

*bDeaktiviert*\
in Gibt an, ob die Dropdown Schaltfläche für das Kombinations Feld deaktiviert ist.

*bisdrop*\
in Gibt an, ob die Dropdown Schaltfläche für das Kombinations Feld gelöscht wird.

*bishighbeleuchtet*\
in Gibt an, ob die Dropdown Schaltfläche für das Kombinations Feld hervorgehoben ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist. andernfalls false.

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a> Cmfcbasevisualmanager::D rawpushbutton

Zeichnet eine Schaltfläche mit dem aktuellen Windows-Design.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
in Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
in Das umgebende Rechteck der Schaltfläche "Push".

*pbutton*<br/>
in Ein Zeiger auf das zu zeichnende [cmfcbutton-Klassen](../../mfc/reference/cmfcbutton-class.md) Objekt.

*uistate*<br/>
in Erten. Der Zustand wird von *pbutton*übernommen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist. andernfalls false.

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a> Cmfcbasevisualmanager::D rawradio Button

Zeichnet ein Optionsfeld-Steuerelement mithilfe des aktuellen Windows-Designs.

```
virtual BOOL DrawRadioButton(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    BOOL bChecked,
    BOOL bEnabled,
    BOOL bPressed);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
in Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
in Das umgebende Rechteck des Options Felds.

*bhervor gehoben*<br/>
in Gibt an, ob das Optionsfeld hervorgehoben ist.

*bCheck*<br/>
in Gibt an, ob das Optionsfeld aktiviert ist.

*benabled*<br/>
in Gibt an, ob das Optionsfeld aktiviert ist.

*bgedrückt*<br/>
in Gibt an, ob die Options Schaltfläche gedrückt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist. andernfalls false.

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a> Cmfcbasevisualmanager::D rawstatusbarprogress

Zeichnet die Statusanzeige auf dem Status leisten-Steuerelement ( [cmfcstatusbar-Klasse](../../mfc/reference/cmfcstatusbar-class.md)) unter Verwendung des aktuellen Windows-Designs.

```
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,
    CMFCStatusBar* pStatusBar,
    CRect rectProgress,
    int nProgressTotal,
    int nProgressCurr,
    COLORREF clrBar,
    COLORREF clrProgressBarDest,
    COLORREF clrProgressText,
    BOOL bProgressText);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
in Ein Zeiger auf einen Gerätekontext.

*pstatusbar*<br/>
in Ein Zeiger auf die Statusleiste. Dieser Wert wird ignoriert.

*rectprogress*<br/>
in Das umschließende Rechteck der Statusanzeige in *PDC* -Koordinaten.

*nProgressTotal*<br/>
in Der Gesamtstatus Wert.

*nProgressCurr*<br/>
in Der aktuelle Fortschritts Wert.

*clrbar*<br/>
in Die Start Farbe. `CMFCBaseVisualManager` ignoriert dieses. Abgeleitete Klassen können Sie für Farbverläufe verwenden.

*clrProgressBarDest*<br/>
in Die Endfarbe. `CMFCBaseVisualManager` ignoriert dieses. Abgeleitete Klassen können Sie für Farbverläufe verwenden.

*clrProgressText*<br/>
in Fortschritts Textfarbe. `CMFCBaseVisualManager` ignoriert dieses. Die Textfarbe wird von definiert `afxGlobalData.clrBtnText` .

*bProgressText*<br/>
in Gibt an, ob Fortschritts Text angezeigt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist. andernfalls false.

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a> Cmfcbasevisualmanager:: fillrebarpane

Füllt den Hintergrund des Grund leisten-Steuer Elements mithilfe des aktuellen Windows-Designs.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
in Ein Zeiger auf einen Gerätekontext.

*pbar*<br/>
in Ein Zeiger auf einen Bereich, dessen Hintergrund gezeichnet werden soll.

*rectclient*<br/>
in Das umgebende Rechteck des Bereichs, der ausgefüllt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist. andernfalls false.

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a> Cmfcbasevisualmanager:: getstandardwindowstheme

Ruft das aktuelle Windows-Design ab.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Rückgabewert

Die aktuell ausgewählte Windows-Design Farbe. Kann einer der folgenden Enumerationswerte sein:

- `WinXpTheme_None` -Das Design ist nicht aktiviert.

- `WinXpTheme_NonStandard` -ein nicht standardmäßiges Design ist ausgewählt (was bedeutet, dass ein Design ausgewählt ist, aber keines aus der Liste unten).

- `WinXpTheme_Blue` -Blue Theme (Luna).

- `WinXpTheme_Olive` -Olive-Design.

- `WinXpTheme_Silver` -Silver-Design.

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a> Cmfcbasevisualmanager:: updatesystemcolors

Aufrufe `OpenThemeData` zum Abrufen von Handles zum Zeichnen verschiedener Steuerelemente: Fenster, Symbolleisten, Schaltflächen usw.

```cpp
void UpdateSystemColors();
```

### <a name="remarks"></a>Bemerkungen

Nur für interne Verwendung.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
