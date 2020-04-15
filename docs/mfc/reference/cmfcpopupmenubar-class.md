---
title: CMFCPopupMenuBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
ms.openlocfilehash: b4693e316fd78948cfae262433fee8ca8b6ab23c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375362"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar-Klasse

Eine Menüleiste, die in einem Popupmenü eingebettet ist.

## <a name="syntax"></a>Syntax

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Berechnet sofort das Layout eines Bereichs neu. (Überschreibt [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Lädt Popupmenüelemente aus einer angegebenen Menüressource.|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Schließt eine verzögerte Popupmenüschaltfläche.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Erstellt ein Menü aus den Popup-Menü-Schaltflächen.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Sucht die Symbolleiste, auf der ein angegebener Punkt liegt.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Gibt die Größe der Menü-Button-Bilder an.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Gibt den Bezeichner des Standardmenüelements zurück.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Ruft den Index des zuletzt aufgerufenen Menübefehls ab.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Ruft den Zeilenversatz der Popupmenüleiste ab.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importiert Popupmenüschaltflächen aus einem angegebenen Menü.|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Gibt an, ob sich die Popupmenüleiste im Dropdown-Listenmodus befindet.|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Gibt an, ob sich die Popupmenüleiste im Palettenmodus befindet.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Gibt an, ob es sich um ein Multifunktionsleistenbedienfeld handelt (standardmäßig FALSE).|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Gibt an, ob es sich um ein Multifunktionsleistenbedienfeld im regulären Modus handelt (standardmäßig FALSE).|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Lädt ein archiviertes Menü.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Stellt eine verzögerte Menüschaltfläche zum Schließen der Popupmenüleiste wieder her.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Legt den Stil der Symbolleistenschaltfläche am angegebenen Index fest. (Überschreibt [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Legt den Zeilenversatz der Popupmenüleiste fest.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Startet den Timer für eine angegebene verzögerte Popup-Menüschaltfläche.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Gibt an, ob die graue Seitenleiste angezeigt wird, wenn die Anwendung eine Windows XP-Darstellung hat.|

## <a name="remarks"></a>Bemerkungen

Die `CMFCPopupMenuBar` wird gleichzeitig mit einer [CMFCPopupMenu-Klasse](../../mfc/reference/cmfcpopupmenu-class.md) erstellt und darin eingebettet. Der `CMFCPopupMenuBar` deckt den gesamten `CMFCPopupMenu` Clientbereich des Objekts ab. Es unterstützt Tastatur- und Mauseingabe. Es kommuniziert diese Eingabe `CMFCPopupMenu` auch an das und an das Framefenster der obersten Ebene.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein `CMFCPopupMenuBar` Objekt aus einem Objekt initialisiert wird. `CMFCPopupMenu` Dieser Codeausschnitt ist Teil des [Draw Client-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxpopupmenubar.h

## <a name="cmfcpopupmenubaradjustsizeimmediate"></a><a name="adjustsizeimmediate"></a>CMFCPopupMenuBar::AdjustSizeImmediate

Berechnet sofort das Layout des Popup-Menüleistenbereichs neu. (Überschreibt [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>Parameter

*bRecalcLayout*<br/>
[in] TRUE, um das Layout des Popup-Menüleistenbereichs automatisch neu zu berechnen; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarbuildorigitems"></a><a name="buildorigitems"></a>CMFCPopupMenuBar::BuildOrigItems

Lädt Popupmenüelemente aus einer angegebenen Menüressource.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>Parameter

*uiMenuResID*<br/>
[in] Gibt die Menü-ID der zu ladenden Menüressource an.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn erfolgreich oder FALSE, wenn nicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarclosedelayedsubmenu"></a><a name="closedelayedsubmenu"></a>CMFCPopupMenuBar::CloseDelayedSubMenu

Schließt eine Popupmenüschaltfläche, die verzögert wurde.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarexporttomenu"></a><a name="exporttomenu"></a>CMFCPopupMenuBar::ExportToMenu

Erstellt ein Menü aus den Popup-Menüschaltflächen.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt ein Handle an das neue Menü zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarfinddestintationtoolbar"></a><a name="finddestintationtoolbar"></a>CMFCPopupMenuBar::FindDestintationToolBar

Sucht die Symbolleiste, auf der ein angegebener Punkt liegt.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
[in] Ein Punkt auf dem Bildschirm.

### <a name="return-value"></a>Rückgabewert

Gibt einen Handle an die Symbolleiste zurück, in der der Punkt liegt, falls vorhanden, oder NULL, falls nicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubargetcurrentmenuimagesize"></a><a name="getcurrentmenuimagesize"></a>CMFCPopupMenuBar::GetCurrentMenuImageSize

Gibt die Größe der Menü-Button-Bilder an.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Größe der Menü-Schaltflächenbilder in der Symbolleiste zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubargetdefaultmenuid"></a><a name="getdefaultmenuid"></a>CMFCPopupMenuBar::GetDefaultMenuId

Gibt den Bezeichner des Standardmenüelements zurück.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den Bezeichner des Standardmenüelements in der Popupmenüleiste zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubargetlastcommandindex"></a><a name="getlastcommandindex"></a>CMFCPopupMenuBar::GetLastCommandIndex

Ruft den Index des zuletzt aufgerufenen Menübefehls ab.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Index des letzten Menübefehls zurück, der aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubargetoffset"></a><a name="getoffset"></a>CMFCPopupMenuBar::GetOffset

Ruft den Zeilenversatz der Popupmenüleiste ab.

```
int GetOffset() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den Zeilenversatz der Popupmenüleiste zurück.

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird mit [CMFCPopupMenuBar::SetOffset](#setoffset)festgelegt.

## <a name="cmfcpopupmenubarimportfrommenu"></a><a name="importfrommenu"></a>CMFCPopupMenuBar::ImportFromMenu

Importiert Popupmenüschaltflächen aus einem angegebenen Menü.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>Parameter

*Hmenu*<br/>
[in] Das Menü, aus dem die Popupmenüschaltflächen importiert werden sollen.

*bShowAllCommands*<br/>
[in] TRUE, wenn alle Befehle im Menü importiert werden sollen, oder FALSE, wenn selten verwendete Befehle ausgeblendet werden können.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Menüschaltflächen erfolgreich aus dem Menü importiert wurden, oder FALSE, falls nicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarisdropdownlistmode"></a><a name="isdropdownlistmode"></a>CMFCPopupMenuBar::IsDropDownListMode

Gibt an, ob sich die Popupmenüleiste im Dropdown-Listenmodus befindet.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn sich die Popupmenüleiste im Dropdown-Listenmodus befindet, oder FALSE, falls nicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarispalettemode"></a><a name="ispalettemode"></a>CMFCPopupMenuBar::IsPaletteMode

Gibt an, ob sich die Popupmenüleiste im Palettenmodus befindet.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Palettenmodus aktiviert ist, oder FALSE, falls nicht.

### <a name="remarks"></a>Bemerkungen

Wenn die Menüleiste auf den Palettenmodus eingestellt ist, werden Menüelemente in mehreren Spalten und einer begrenzten Anzahl von Zeilen angezeigt.

## <a name="cmfcpopupmenubarisribbonpanel"></a><a name="isribbonpanel"></a>CMFCPopupMenuBar::IsRibbonPanel

Gibt an, ob es sich um ein Multifunktionsleistenbedienfeld handelt (standardmäßig FALSE).

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt false standardmäßig zurück, was darauf hinweist, dass es sich nicht um ein Multifunktionsleistenfenster handelt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarisribbonpanelinregularmode"></a><a name="isribbonpanelinregularmode"></a>CMFCPopupMenuBar::IsRibbonPanelInRegularMode

Gibt an, ob es sich um ein Multifunktionsleistenbedienfeld im regulären Modus handelt (standardmäßig FALSE).

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt false standardmäßig zurück, was darauf hinweist, dass es sich nicht um ein Multifunktionsleistenfenster im regulären Modus handelt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarloadfromhash"></a><a name="loadfromhash"></a>CMFCPopupMenuBar::LoadFromHash

Lädt ein archiviertes Menü.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>Parameter

*Hmenu*<br/>
[in] Ein Handle für das archivierte Menü zum Laden.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das Menü erfolgreich geladen wurde, oder FALSE, falls nicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarm_bdisablesidebarinxpmode"></a><a name="m_bdisablesidebarinxpmode"></a>CMFCPopupMenuBar::m_bDisableSideBarInXPMode

Ein boolescher Parameter, der angibt, ob Ihre Anwendung eine graue Seitenleiste hat, wenn sie eine Windows XP-Darstellung hat.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Bemerkungen

Wenn diese Membervariable auf FALSE festgelegt ist und Ihre Anwendung eine Windows XP-Darstellung hat, zeichnet das Framework eine graue Seitenleiste in ihrer Anwendung.

Der Standardwert ist FALSE.

## <a name="cmfcpopupmenubarrestoredelayedsubmenu"></a><a name="restoredelayedsubmenu"></a>CMFCPopupMenuBar::RestoreDelayedSubMenu

Stellt eine verzögerte Menüschaltfläche zum Schließen der Popupmenüleiste wieder her.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CMFCPopupMenuBar::SetButtonStyle

Legt den Stil der Symbolleistenschaltfläche am angegebenen Index fest. (Überschreibt [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Der nullbasierte Index der Symbolleistenschaltfläche, deren Stil festgelegt werden soll.

*nStyle*<br/>
[in] Der Stil der Schaltfläche. Die Liste der verfügbaren Symbolleistenschaltflächenstile finden Sie unter [ToolBar-Steuerelementstile.](../../mfc/reference/toolbar-control-styles.md)

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarsetoffset"></a><a name="setoffset"></a>CMFCPopupMenuBar::SetOffset

Legt den Zeilenversatz der Popupmenüleiste fest.

```
void SetOffset(int iOffset);
```

### <a name="parameters"></a>Parameter

*iOffset*<br/>
[in] Die Anzahl der Zeilen, die die Popupmenüleiste versetzt werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcpopupmenubarstartpopupmenutimer"></a><a name="startpopupmenutimer"></a>CMFCPopupMenuBar::StartPopupMenuTimer

Startet den Timer für eine angegebene verzögerte Popup-Menüschaltfläche.

```
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>Parameter

*pMenuButton*<br/>
[in] Zeigen Sie auf die Menüschaltfläche, für die der Verzögerungszeitgeber eingestellt werden soll.

*nDelayFactor*<br/>
[in] Ein Verzögerungsfaktor, der mindestens einem entspricht, um mit der Standardmenüverzögerungszeit zu multiplizieren (in der Regel zwischen einer halben Sekunde und fünf Sekunden).

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar-Klasse](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu-Klasse](../../mfc/reference/cmfcpopupmenu-class.md)
