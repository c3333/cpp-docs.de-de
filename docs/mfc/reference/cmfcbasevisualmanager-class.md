---
title: CMFCBaseVisualManager-Klasse
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
ms.openlocfilehash: ac64a3feac5d124c2bfa67fc857dad5045c2dd28
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754892"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager-Klasse

Eine Ebene zwischen abgeleiteten visuellen Managern und der Windows-Theme-API.

`CMFCBaseVisualManager`lädt UxTheme.dll, sofern verfügbar, und verwaltet den Zugriff auf Windows Theme-API-Methoden.

Diese Klasse ist nur für den internen Gebrauch vorgesehen.

## <a name="syntax"></a>Syntax

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Erstellt und initialisiert ein `CMFCBaseVisualManager`-Objekt.|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Zeichnet ein Kontrollkästchen-Steuerelement mithilfe des aktuellen Windows-Designs.|
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Zeichnet einen Kombinationsrahmen mit dem aktuellen Windows-Design.|
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Zeichnet eine Dropdown-Schaltfläche für Kombinationsfelder mit dem aktuellen Windows-Design.|
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Zeichnet eine Drucktaste mit dem aktuellen Windows-Design.|
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Zeichnet ein Optionsfeldsteuerelement mithilfe des aktuellen Windows-Designs.|
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Zeichnet eine Statusleiste für ein Statusleistensteuerelement ( [CMFCStatusBar-Klasse](../../mfc/reference/cmfcstatusbar-class.md)) mit dem aktuellen Windows-Design.|
|[CMFCBaseVisualManager::FillrebarPane](#fillrebarpane)|Füllt den Hintergrund des Bewehrungssteuerelements mithilfe des aktuellen Windows-Designs.|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Ruft das aktuelle Windows-Design ab.|

### <a name="protected-methods"></a>Geschützte Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Aufrufe `CloseThemeData` für alle Handles, die in `UpdateSystemColors`erhalten wurden.|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Aufrufe `OpenThemeData` zum Abrufen von Handles zum Zeichnen verschiedener Steuerelemente: Fenster, Symbolleisten, Schaltflächen usw.|

## <a name="remarks"></a>Bemerkungen

Sie müssen Objekte dieser Klasse nicht direkt instanziieren.

Da es sich um eine Basisklasse für alle visuellen Manager handelt, können Sie einfach [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)aufrufen, einen Zeiger auf den aktuellen Visual Manager abrufen und auf die Methoden für `CMFCBaseVisualManager` die Verwendung dieses Zeigers zugreifen. Wenn Sie jedoch ein Steuerelement mithilfe des aktuellen Windows-Designs anzeigen `CMFCVisualManagerWindows` müssen, ist es besser, die Schnittstelle zu verwenden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxvisualmanager.h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a>CMFCBaseVisualManager::CleanUpThemes

Aufrufe `CloseThemeData` für alle Handles, die in `UpdateSystemColors`erhalten wurden.

```cpp
void CleanUpThemes();
```

### <a name="remarks"></a>Bemerkungen

Nur zur internen Verwendung.

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a>CMFCBaseVisualManager::CMFCBaseVisualManager

Erstellt und initialisiert ein `CMFCBaseVisualManager`-Objekt.

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a>CMFCBaseVisualManager::DrawCheckBox

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

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext

*Rect*<br/>
[in] Das umgrenzende Rechteck des Kontrollkästchens.

*bHervorgehoben*<br/>
[in] Gibt an, ob das Kontrollkästchen hervorgehoben ist.

*nState*<br/>
[in] 0 für ungeprüft, 1 für geprüfte Normale,

2 für gemischte Normale.

*bAktiviert*<br/>
[in] Gibt an, ob das Kontrollkästchen aktiviert ist.

*bPressed*<br/>
[in] Gibt an, ob das Kontrollkästchen aktiviert ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Die Werte von *nState* entsprechen den folgenden Kontrollkästchenstilen.

|nState|Kontrollkästchen-Stil|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a>CMFCBaseVisualManager::DrawComboBorder

Zeichnet den Kombinationsfeldrahmen mit dem aktuellen Windows-Design.

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Umgebendes Rechteck des Kombinationsfeldrahmens.

*bDeaktiviert*<br/>
[in] Gibt an, ob der Rahmen des Kombinationsfelds deaktiviert ist.

*bIsDropped*<br/>
[in] Gibt an, ob der Rahmen des Kombinationsfelds heruntergelassen wird.

*bIsHighlighted*<br/>
[in] Gibt an, ob der Rahmen des Kombinationsfelds hervorgehoben ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist; andernfalls FALSE.

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a>CMFCBaseVisualManager::DrawComboDropButton

Zeichnet eine Dropdown-Schaltfläche für Kombinationsfelder mit dem aktuellen Windows-Design.

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pDC*|[in] Ein Zeiger auf einen Gerätekontext.|
|*Rect*|[in] Das umschließende Rechteck der Dropdown-Schaltfläche des Kombinationsfelds.|
|*bDeaktiviert*|[in] Gibt an, ob die Dropdown-Schaltfläche für das Kombinationsfeld deaktiviert ist.|
|*bIsDropped*|[in] Gibt an, ob die Dropdown-Schaltfläche für das Kombinationsfeld heruntergelassen wird.|
|*bIsHighlighted*|[in] Gibt an, ob die Dropdown-Schaltfläche für das Kombinationsfeld hervorgehoben ist.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist; andernfalls FALSE.

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a>CMFCBaseVisualManager::DrawPushButton

Zeichnet eine Drucktaste mit dem aktuellen Windows-Design.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Das umgrenzende Rechteck der Drucktaste.

*pButton*<br/>
[in] Ein Zeiger auf das zu zeichnende [CMFCButton-Klassenobjekt.](../../mfc/reference/cmfcbutton-class.md)

*uiState*<br/>
[in] Ignoriert. Der Status wird von *pButton*übernommen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist; andernfalls FALSE.

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a>CMFCBaseVisualManager::DrawRadioButton

Zeichnet ein Optionsfeldsteuerelement mithilfe des aktuellen Windows-Designs.

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

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Das umgrenzende Rechteck des Optionsfelds.

*bHervorgehoben*<br/>
[in] Gibt an, ob das Optionsfeld hervorgehoben ist.

*bGeprüft*<br/>
[in] Gibt an, ob das Optionsfeld aktiviert ist.

*bAktiviert*<br/>
[in] Gibt an, ob das Optionsfeld aktiviert ist.

*bPressed*<br/>
[in] Gibt an, ob das Optionsfeld gedrückt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist; andernfalls FALSE.

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a>CMFCBaseVisualManager::DrawStatusBarProgress

Zeichnet die Statusleistenleiste für das Statusleistensteuerelement ( [CMFCStatusBar-Klasse](../../mfc/reference/cmfcstatusbar-class.md)) mit dem aktuellen Windows-Design.

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

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*pStatusBar*<br/>
[in] Ein Zeiger auf die Statusleiste. Dieser Wert wird ignoriert.

*rectProgress*<br/>
[in] Das umgrenzende Rechteck der Fortschrittsleiste in *pDC-Koordinaten.*

*nProgressTotal*<br/>
[in] Der Gesamtfortschrittswert.

*nProgressCurr*<br/>
[in] Der aktuelle Fortschrittswert.

*clrBar*<br/>
[in] Die Startfarbe. `CMFCBaseVisualManager`ignoriert dies. Abgeleitete Klassen können sie für Farbverläufe verwenden.

*clrProgressBarDest*<br/>
[in] Die Endfarbe. `CMFCBaseVisualManager`ignoriert dies. Abgeleitete Klassen können sie für Farbverläufe verwenden.

*clrProgressText*<br/>
[in] Fortschrittstextfarbe. `CMFCBaseVisualManager`ignoriert dies. Die Textfarbe wird `afxGlobalData.clrBtnText`durch definiert.

*bProgressText*<br/>
[in] Gibt an, ob Fortschrittstext angezeigt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist; andernfalls FALSE.

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a>CMFCBaseVisualManager::FillrebarPane

Füllt den Hintergrund des Bewehrungssteuerelements mithilfe des aktuellen Windows-Designs.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Pbar*<br/>
[in] Ein Zeiger auf einen Bereich, dessen Hintergrund gezeichnet werden soll.

*rectClient*<br/>
[in] Das umgrenzende Rechteck des auszufüllenden Bereichs.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Theme-API aktiviert ist; andernfalls FALSE.

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a>CMFCBaseVisualManager::GetStandardWindowsTheme

Ruft das aktuelle Windows-Design ab.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Rückgabewert

Die aktuell ausgewählte Windows-Designfarbe. Es kann einer der folgenden aufgezählten Werte sein:

- `WinXpTheme_None`- es ist kein Thema aktiviert.

- `WinXpTheme_NonStandard`- Nicht-Standard-Design ausgewählt ist (d.h. ein Thema ist ausgewählt, aber keines aus der Liste unten).

- `WinXpTheme_Blue`- blaues Thema (Luna).

- `WinXpTheme_Olive`- Oliventhema.

- `WinXpTheme_Silver`- Silber Thema.

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a>CMFCBaseVisualManager::UpdateSystemColors

Aufrufe `OpenThemeData` zum Abrufen von Handles zum Zeichnen verschiedener Steuerelemente: Fenster, Symbolleisten, Schaltflächen usw.

```cpp
void UpdateSystemColors();
```

### <a name="remarks"></a>Bemerkungen

Nur zur internen Verwendung.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
