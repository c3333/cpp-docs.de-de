---
title: CMFCVisualManagerWindows7-Klasse
ms.date: 03/27/2019
f1_keywords:
- CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::OnFillMenuImageRect
helpviewer_keywords:
- CMFCVisualManagerWindows7 Class [MFC]
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
ms.openlocfilehash: 6686afecc2b8ef97ea24ef45ff5225433677a954
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319845"
---
# <a name="cmfcvisualmanagerwindows7-class"></a>CMFCVisualManagerWindows7-Klasse

Der `CMFCVisualManagerWindows7` gibt einer Anwendung das Erscheinungsbild einer Windows 7-Anwendung.

## <a name="syntax"></a>Syntax

```
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7)|Der Standardkonstruktor.|
|[CMFCVisualManagerWindows7::-CMFCVisualManagerWindows7](#_dtorcmfcvisualmanagerwindows7)|Standard-Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCVisualManagerWindows7::CleanStyle`|Löscht den aktuellen visuellen Stil und setzt den standardmäßigen visuellen Stil zurück.|
|`CMFCVisualManagerWindows7::CleanUp`|Löscht alle Objekte in der Benutzeroberfläche und setzt die Menüs zurück.|
|`CMFCVisualManagerWindows7::DrawNcBtn`|Zeichnet eine Schaltfläche im Nicht-Client-Bereich auf dem Frame. Das Framework verwendet diese Methode, um Schaltflächen in der oberen rechten Ecke des Fensterrahmens zu minimieren, zu maximieren, zu schließen und wiederherzustellen. Diese Methode wird nur aufgerufen, `Aero` wenn das Programm ein Design verwendet.|
|`CMFCVisualManagerWindows7::DrawNcText`|Zeichnet Text im Nicht-Client-Bereich auf dem Frame. Das Framework verwendet diese Methode, um den Anwendungstitel in der Titelleiste am oberen Rand des Rahmenfensters zu zeichnen.|
|`CMFCVisualManagerWindows7::DrawSeparator`|Zeichnet ein Trennzeichen für die [CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md).|
|`CMFCVisualManagerWindows7::GetRibbonBar`|Ruft die [CMFCRibbonBar-Klasse](../../mfc/reference/cmfcribbonbar-class.md) ab, die der Benutzeroberfläche zugeordnet ist.|
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](#getribboneditbackgroundcolor)|Ruft eine Multifunktionsleisten-Bearbeitungsfeld-Hintergrundfarbe ab.|
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|Überschreibt [CMFCVisualManager::GetRibbonPopupBorderSize](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|Überschreibt [CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|Überschreibt [CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin)|
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|Überschreibt [CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem)|
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|Überschreibt [CMFCVisualManager::IsOwnerDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck)|
|`CMFCVisualManagerWindows7::IsRibbonPresent`|Bestimmt, `CMFCRibbonBar` ob ein vorhanden und sichtbar ist.|
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|Überschreibt [CMFCVisualManagerWindows::OnDrawButtonBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|Überschreibt [CMFCVisualManagerWindows::OnDrawCheckBoxEx](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex)|
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|Überschreibt [CMFCVisualManagerWindows::OnDrawComboDropButton](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton)|
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|Überschreibt [CMFCVisualManager::OnDrawDefaultRibbonImage](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage)|
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|Überschreibt [CMFCVisualManagerWindows::OnDrawMenuBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder)|
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|Überschreibt [CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)|
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|Überschreibt [CMFCVisualManager::OnDrawMenuLabel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel)|
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|Überschreibt `CMFCVisualManager::OnDrawRadioButton`.|
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|Überschreibt [CMFCVisualManager::OnDrawRibbonApplicationButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|Überschreibt [CMFCVisualManager::OnDrawRibbonButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|Überschreibt [CMFCVisualManager::OnDrawRibbonCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|Überschreibt [CMFCVisualManager::OnDrawRibbonCaptionButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|Überschreibt [CMFCVisualManager::OnDrawRibbonCategory](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|Überschreibt [CMFCVisualManager::OnDrawRibbonCategoryTab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)|
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|Überschreibt [CMFCVisualManager::OnDrawRibbonDefaultPaneButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|Überschreibt [CMFCVisualManager::OnDrawRibbonGalleryButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|Überschreibt `CMFCVisualManager::OnDrawRibbonLaunchButton`.|
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|Überschreibt [CMFCVisualManager::OnDrawRibbonMenuCheckFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|Überschreibt [CMFCVisualManager::OnDrawRibbonPanel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|Überschreibt [CMFCVisualManager::OnDrawRibbonPanelCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|Überschreibt [CMFCVisualManager::OnDrawRibbonProgressBar](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)|
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|Überschreibt [CMFCVisualManager::OnDrawRibbonRecentFilesFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|Überschreibt [CMFCVisualManager::OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|Überschreibt [CMFCVisualManager::OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|Überschreibt [CMFCVisualManager::OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|Überschreibt [CMFCVisualManager::OnDrawRibbonStatusBarPane](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane)|
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|Überschreibt [CMFCVisualManager::OnDrawRibbonTabsFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe)|
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|Überschreibt [CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox)|
|`CMFCVisualManagerWindows7::OnFillBarBackground`|Überschreibt [CMFCVisualManagerWindows::OnFillBarBackground](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground)|
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|Überschreibt [CMFCVisualManagerWindows::OnFillButtonInterior](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior)|
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](#onfillmenuimagerect)|Das Framework ruft diese Methode auf, wenn es den Bereich um Menüelementbilder ausfüllt.|
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|Überschreibt [CMFCVisualManager::OnFillRibbonButton](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton)|
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|Überschreibt [CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup)|
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|Überschreibt [CMFCVisualManagerWindows::OnHighlightMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem)|
|`CMFCVisualManagerWindows7::OnNcActivate`|Überschreibt [CMFCVisualManager::OnNcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate)|
|`CMFCVisualManagerWindows7::OnNcPaint`|Überschreibt [CMFCVisualManager::OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint)|
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|Überschreibt [CMFCVisualManagerWindows::OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors)|
|`CMFCVisualManagerWindows7::SetResourceHandle`|Legt das Ressourcenhandle fest, das die Attribute des visuellen Managers beschreibt.|
|`CMFCVisualManagerWindows7::SetStyle`|Legt das Farbschema `CMFCVisualManagerWindows7` der GUI fest.|

## <a name="remarks"></a>Bemerkungen

Verwenden `CMFCVisualManagerWindows7` Sie die Klasse, um das Erscheinungsbild Ihrer Anwendung zu ändern, um eine Standardanwendung für Windows 7 nachzuahmen. Diese Klasse ist möglicherweise nicht gültig, wenn Ihre Anwendung unter einer Windows-Version vor Windows 7 ausgeführt wird. In diesem Szenario verwendet die Anwendung den in [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)definierten visuellen Standard-Manager .

Der CMFCVisualManagerWindows7 erbt mehrere Methoden sowohl von der [CMFCVisualManagerWindows-Klasse](../../mfc/reference/cmfcvisualmanagerwindows-class.md) als auch von der `CMFCVisualManager` Klasse. Die im vorherigen Abschnitt aufgeführten Methoden `CMFCVisualManagerWindows7` sind Methoden, die für die Klasse neu sind.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

`CMFCVisualManagerWindows7`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxvisualmanagerwindows7.h

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="_dtorcmfcvisualmanagerwindows7"></a>CMFCVisualManagerWindows7::-CMFCVisualManagerWindows7

Standard-Destruktor.

```
virtual ~CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="cmfcvisualmanagerwindows7"></a>CMFCVisualManagerWindows7::CMFCVisualManagerWindows7

Der Standardkonstruktor.

```
CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7getribboneditbackgroundcolor"></a><a name="getribboneditbackgroundcolor"></a>CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor

Ruft die Hintergrundfarbe eines Menübandbearbeitungsfelds ab.

```
virtual COLORREF GetRibbonEditBackgroundColor (
    CMFCRibbonRichEditCtrl* pEdit,
    BOOL bIsHighlighted,
    BOOL bIsPaneHighlighted,
    BOOL bIsDisabled);
```

### <a name="parameters"></a>Parameter

*Pedit*<br/>
[in] Ein Zeiger auf das Bearbeitungssteuerelement. Dieser Wert kann nicht NULL sein.

*bIsHighlighted*<br/>
[out] Gibt zurück, ob das Menübandfeld hervorgehoben ist.

*bIsPaneHighlighted*<br/>
[out] Gibt TRUE zurück, wenn das Menübandbedienfeld, das *pEdit* enthält, hervorgehoben ist.

*bIsDisabled*<br/>
[out] Gibt zurück, ob *pEdit* deaktiviert ist.

### <a name="return-value"></a>Rückgabewert

Die Hintergrundfarbe des Bearbeitungsfelds *pBearbeiten*.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcvisualmanagerwindows7onfillmenuimagerect"></a><a name="onfillmenuimagerect"></a>CMFCVisualManagerWindows7::OnFillMenuImageRect

Das Framework ruft diese Methode auf, wenn es den Bereich um ein Menüelementbild ausfüllt.

```
virtual void OnFillMenuImageRect(
    CDC* pDC,
    CMFCToolBarButton* pButton,
    CRect rectangle,
    CMFCVisualManager::AFX_BUTTON_STATE state);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf den Gerätekontext einer Menüschaltfläche.

*pButton*<br/>
[in] Ein Zeiger auf `CMFCToolBarButton`eine . Das Framework füllt den Hintergrund für diese Schaltfläche.

*Rechteck*<br/>
[in] Ein Rechteck, das die Grenzen des Bildbereichs der Menüschaltfläche angibt.

*Staat*<br/>
[in] Der Schaltflächenstatus.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager-Klasse](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerWindows-Klasse](../../mfc/reference/cmfcvisualmanagerwindows-class.md)
