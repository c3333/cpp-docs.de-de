---
title: CMFCRibbonColorButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
ms.openlocfilehash: 528b883d75889589c7021f462324dd9dcb71be25
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754841"
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton-Klasse

Die `CMFCRibbonColorButton` -Klasse implementiert eine Farbenschaltfläche, die einer Menübandleiste hinzugefügt werden kann. Die Menüband-Farbenschaltfläche zeigt ein Dropdownmenü an, das eine oder mehrere Farbpaletten enthält.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonColorButton : public CMFCRibbonGallery
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|Fügt dem normalen Farbbereich eine Gruppe Farben hinzu.|
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|Gibt an, ob die Schaltfläche **Automatisch** aktiviert ist.|
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|Aktiviert die Schaltfläche **Weitere** .|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFCRibbonColorButton::GetColor](#getcolor)|Gibt die aktuell ausgewählte Farbe zurück.|
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|Gibt die Größe der Farbelemente zurück, die in der Farbleiste angezeigt werden.|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|Gibt die Farbe des aktuell in der Popup-Farbpalette ausgewählten Elements zurück.|
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|Entfernt alle Farbgruppen aus dem normalen Farbbereich.|
|[CMFCRibbonColorButton::SetColor](#setcolor)|Wählt eine Farbe aus dem normalen Farbbereich aus.|
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|Legt die Größe aller Farbelemente fest, die in der Farbleiste angezeigt werden.|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|Gibt eine Liste mit RGB-Werten für die Anzeige im Farbbereich des Dokuments an.|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>Bemerkungen

Die Farbenschaltfläche im Menüband zeigt eine Farbleiste an, wenn ein Benutzer drauf drückt. Standardmäßig enthält diese Farbleiste eine Farbauswahlpalette, die als normaler Farbbereich bezeichnet wird. Optional kann die Farbleiste eine Schaltfläche **Automatisch** , die dem Benutzer die Auswahl einer Standardfarbe ermöglicht, und eine Schaltfläche **Weitere** anzeigen, die eine Popupfarbpalette anzeigt, die weitere Farben enthält.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCRibbonColorButton` -Klasse. Im Beispiel wird gezeigt, wie ein `CMFCRibbonColorButton` -Objekt konstruiert wird, das große Bild festgelegt wird, die Schaltfläche **Automatisch** aktiviert wird, die Schaltfläche **Weitere** aktiviert wird, die Spaltenanzahl festgelegt wird, die Größe aller Farbelemente festgelegt wird, die auf der Farbleiste angezeigt werden, dem normalen Farbbereich eine Gruppe Farben hinzugefügt wird, und eine Liste mit RGB-Werten für die Anzeige im Farbbereich des Dokuments angegeben wird. Dieser Codeausschnitt ist Teil des [Draw Client-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxribboncolorbutton.h

## <a name="cmfcribboncolorbuttonaddcolorsgroup"></a><a name="addcolorsgroup"></a>CMFCRibbonColorButton::AddColorsGroup

Fügt dem normalen Farbbereich eine Gruppe Farben hinzu.

```cpp
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
[in] Der Gruppenname.

*lstColors*<br/>
[in] Die Liste der Farben.

*bContiguousColumns*<br/>
[in] Steuert, wie die Farbelemente in der Gruppe angezeigt werden. Wenn TRUE, werden die Farbelemente ohne vertikalen Abstand gezeichnet. Wenn FALSE, werden die Farbelemente mit einem vertikalen Abstand gezeichnet.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um das Farb-Pop-up mehrere Gruppen von Farben anzuzeigen. Sie können steuern, wie die Farben in der Gruppe angezeigt werden.

## <a name="cmfcribboncolorbuttoncmfcribboncolorbutton"></a><a name="cmfcribboncolorbutton"></a>CMFCRibbonColorButton::CMFCRibbonColorButton

Erstellt ein `CMFCRibbonColorButton`-Objekt.

```
CMFCRibbonColorButton();

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex,
    COLORREF color = RGB(0, 0, 0));

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    BOOL bSimpleButtonLook,
    int nSmallImageIndex,
    int nLargeImageIndex,
    COLORREF color = RGB(0, 0, 0));
```

### <a name="parameters"></a>Parameter

*nID*<br/>
[in] Gibt die Befehls-ID des Befehls an, der ausgeführt werden soll, wenn ein Benutzer auf die Schaltfläche klickt.

*lpszText*<br/>
[in] Gibt den Text an, der auf der Schaltfläche angezeigt werden soll.

*nSmallImageIndex*<br/>
[in] Der nullbasierte Index des kleinen Bildes, der auf der Schaltfläche angezeigt werden soll.

*Farbe*<br/>
[in] Die Farbe der Schaltfläche (Standardschwarz).

*bSimpleButtonLook*<br/>
[in] Wenn TRUE, wird die Schaltfläche als einfaches Rechteck gezeichnet.

*nLargeImageIndex*<br/>
[in] Der nullbasierte Index des großen Bildes, der auf der Schaltfläche angezeigt werden soll.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCRibbonColorButton::EnableAutomaticButton

Gibt an, ob die Schaltfläche **Automatisch** aktiviert ist.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Die Bezeichnung für die Schaltfläche **Automatisch.**

*colorAutomatic*<br/>
[in] Ein RGB-Wert, der die Standardfarbe der **Schaltfläche "Automatisch"** angibt.

*bEnable*<br/>
[in] TRUE, wenn die Schaltfläche **Automatisch** aktiviert ist; FALSE, wenn es deaktiviert ist.

*lpszToolTip*<br/>
[in] Die QuickInfo der **Schaltfläche Automatisch.**

*bOnTop*<br/>
[in] Gibt an, ob sich die Schaltfläche **Automatisch** oben und vor der Farbpalette befindet.

*bDrawBorder*<br/>
[in] TRUE, wenn die Anwendung einen Rahmen um die Farbleiste auf der Farbschaltfläche des Menübands zeichnet. Die Farbleiste zeigt die aktuell ausgewählte Farbe an. FALSE, wenn die Anwendung keinen Rahmen zeichnet

## <a name="cmfcribboncolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCRibbonColorButton::EnableOtherButton

Aktiviert die Schaltfläche **Weitere** .

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
Die Beschriftung der Schaltfläche.

*lpszToolTip*<br/>
Der QuickInfo-Text für die Schaltfläche **Andere.**

### <a name="remarks"></a>Bemerkungen

Die Schaltfläche **Andere** ist die Schaltfläche, die unter der Farbengruppe angezeigt wird. Wenn der Benutzer auf die Schaltfläche **Andere** klickt, wird ein Farbdialogfeld angezeigt.

## <a name="cmfcribboncolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCRibbonColorButton::GetAutomaticColor

Ruft die aktuelle Farbe der automatischen Schaltfläche ab.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein RGB-Farbwert, der die aktuelle Farbe der automatischen Schaltfläche darstellt.

### <a name="remarks"></a>Bemerkungen

Die Farbe des automatischen Knopfes wird durch den Parameter festgelegt, der `colorAutomatic` an die `CMFCRibbonColorButton::EnableAutomaticButton` Methode übergeben wird.

## <a name="cmfcribboncolorbuttongetcolor"></a><a name="getcolor"></a>CMFCRibbonColorButton::GetColor

Gibt die aktuell ausgewählte Farbe zurück.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die Farbe, die durch Klicken auf die Schaltfläche ausgewählt wurde.

## <a name="cmfcribboncolorbuttongetcolorboxsize"></a><a name="getcolorboxsize"></a>CMFCRibbonColorButton::GetColorBoxSize

Gibt die Größe der Farbelemente zurück, die in der Farbleiste angezeigt werden.

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe der Farbschaltflächen in der Dropdown-Farbpalette.

## <a name="cmfcribboncolorbuttongetcolumns"></a><a name="getcolumns"></a>CMFCRibbonColorButton::GetColumns

Ruft die Anzahl der Elemente in einer Zeile der Galerieanzeige der Menübandfarbe ab.

```
int GetColumns() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Symbole in jeder Zeile zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncolorbuttongethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCRibbonColorButton::GetHighlightedColor

Gibt die Farbe des aktuell ausgewählten Elements in der Popup-Farbpalette zurück.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die Farbe des aktuell ausgewählten Elements in der Popup-Farbpalette.

## <a name="cmfcribboncolorbuttonremoveallcolorgroups"></a><a name="removeallcolorgroups"></a>CMFCRibbonColorButton::RemoveAllColorGroups

Entfernt alle Farbgruppen aus dem normalen Farbbereich.

```cpp
void RemoveAllColorGroups();
```

## <a name="cmfcribboncolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCRibbonColorButton::SetColor

Wählt eine Farbe aus dem normalen Farbbereich aus.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Eine Farbe, die festgelegt werden soll.

## <a name="cmfcribboncolorbuttonsetcolorboxsize"></a><a name="setcolorboxsize"></a>CMFCRibbonColorButton::SetColorBoxSize

Legt die Größe aller Farbelemente fest, die in der Farbleiste angezeigt werden.

```cpp
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>Parameter

*sizeBox*<br/>
[in] Die neue Größe der Farbschaltflächen in der Farbpalette.

## <a name="cmfcribboncolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCRibbonColorButton::SetColorName

Legt einen neuen Namen für eine angegebene Farbe fest.

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Der RGB-Wert einer Farbe.

*strName*<br/>
[in] Der neue Name für die angegebene Farbe.

### <a name="remarks"></a>Bemerkungen

Da diese `CMFCColorBar::SetColorName`Methode aufruft, ändert sie den `CMFCColorBar` Namen der angegebenen Farbe in allen Objekten in der Anwendung.

## <a name="cmfcribboncolorbuttonsetcolumns"></a><a name="setcolumns"></a>CMFCRibbonColorButton::SetColumns

Legt die Anzahl der Spalten fest, die in der Farbtabelle angezeigt werden, die dem Benutzer während des Farbauswahlprozesses des Benutzers angezeigt wird.

```cpp
void SetColumns(int nColumns);
```

### <a name="parameters"></a>Parameter

*nColumns*<br/>
[in] Die Anzahl der Farbsymbole, die in jeder Zeile angezeigt werden sollen.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCRibbonColorButton::SetDocumentColors

Gibt eine Liste mit RGB-Werten für die Anzeige im Farbbereich des Dokuments an.

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
[in] Der Text, der mit den Dokumentfarben angezeigt werden soll.

*lstColors*<br/>
[in] Ein Verweis auf eine Liste von RGB-Werten.

## <a name="cmfcribboncolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCRibbonColorButton::SetPalette

Gibt die Standardfarben an, die in der Farbtabelle angezeigt werden sollen, die auf der Farbschaltfläche angezeigt werden.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parameter

*pPalette*<br/>
[in] Ein Zeiger auf eine Farbpalette.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCRibbonColorButton::UpdateColor

Wird vom Framework aufgerufen, wenn der Benutzer eine Farbe aus der Farbtabelle auswählt, die angezeigt wird, wenn der Benutzer auf die Schaltfläche "Farbe" klickt.

```cpp
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Eine vom Benutzer ausgewählte Farbe.

### <a name="remarks"></a>Bemerkungen

Die `CMFCRibbonColorButton::UpdateColor` Methode ändert die Farbe der aktuell ausgewählten Schaltfläche und benachrichtigt das übergeordnete Element, indem eine WM_COMMAND Nachricht mit einer BN_CLICKED Standardbenachrichtigung gesendet wird. Verwenden Sie die [CMFCRibbonColorButton::GetColor-Methode,](#getcolor) um die ausgewählte Farbe abzurufen.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery-Klasse](../../mfc/reference/cmfcribbongallery-class.md)
