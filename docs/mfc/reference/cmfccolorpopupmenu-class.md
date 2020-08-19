---
title: Cmfccolorpopupmenu-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
ms.openlocfilehash: d668a7bd2b5226de906ca146c7b7e882b97f4640
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560984"
---
# <a name="cmfccolorpopupmenu-class"></a>Cmfccolorpopupmenu-Klasse

Stellt ein Popup Menü dar, das Benutzer zum Auswählen von Farben in einem Dokument oder einer Anwendung verwenden.

## <a name="syntax"></a>Syntax

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|name|BESCHREIBUNG|
|[Cmfccolorpopupmenu:: cmfccolorpopupmenu](#cmfccolorpopupmenu)|Erstellt ein `CMFCColorPopupMenu`-Objekt.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|name|BESCHREIBUNG|
|[Cmfccolorpopupmenu:: kreatetearoffbar](#createtearoffbar)|Erstellt eine andockbare Farbleiste. (Überschreibt [cmfcpopupmenu:: kreatetearoffbar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[Cmfccolorpopupmenu:: getmenubar](#getmenubar)|Gibt den [cmfcpopupmenubar](../../mfc/reference/cmfcpopupmenubar-class.md) -Wert zurück, der in das Popupmenü eingebettet ist. (Überschreibt [cmfcpopupmenu:: getmenubar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|
|`CMFCColorPopupMenu::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Objekt abzurufen, das diesem Klassentyp zugeordnet ist.|
|[Cmfccolorpopupmenu:: setproplist](#setproplist)|Legt das Eigenschaften Raster-Steuerelement Objekt des eingebetteten `CMFCColorBar` Objekts fest.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|Name|BESCHREIBUNG|
|`m_bEnabledInCustomizeMode`|Ein boolescher Wert, der bestimmt, ob die Farbleiste angezeigt werden soll.|
|`m_wndColorBar`|Das `CMFCColorBar` Objekt, das die Farbauswahl bereitstellt.|

### <a name="remarks"></a>Bemerkungen

Diese Klasse erbt die Popup-Menü Funktionalität der `CMFCPopupMenu` -Klasse und verwaltet ein- `CMFCColorBar` Objekt, das die Farbauswahl bereitstellt. Wenn sich das Symbolleisten Framework im Anpassungsmodus befindet und der `m_bEnabledInCustomizeMode` Member auf false festgelegt ist, wird das Farb leisten Objekt nicht angezeigt. Weitere Informationen zum Anpassungsmodus finden Sie unter [cmfctoolbar:: iscustomizemode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Weitere Informationen zu `CMFCColorBar` finden Sie unter [cmfccolorbar-Klasse](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[Cmfccolorpopupmenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcolorpopupmenu. h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a> Cmfccolorpopupmenu:: cmfccolorpopupmenu

Erstellt ein `CMFCColorPopupMenu`-Objekt.

```
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    int nHorzDockRows,
    int nVertDockColumns,
    COLORREF colorAutomatic,
    UINT uiCommandID,
    BOOL bStdColorDlg = FALSE);

CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic);

CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*Ellen*<br/>
in Ein Array von Farben, das das Framework im Popup Menü anzeigt.

*color*<br/>
in Die Standardfarbe der ausgewählten Farbe.

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

*nhorzdockrows*<br/>
in Die Anzahl der Zeilen, die in der Farbleiste angezeigt werden, wenn Sie horizontal angedockt wird.

*nvertdockcolumns*<br/>
in Die Anzahl der Spalten, die in der Farbleiste angezeigt werden, wenn Sie vertikal angedockt ist.

*ColorAutomatic*<br/>
in Die Standardfarbe, die das Framework anwendet, wenn Sie auf die Schaltfläche automatisch klicken.

*uicommandid*<br/>
in Die Befehls-ID des Farb leisten-Steuer Elements.

*bstdcolordlg*<br/>
in Ein boolescher Wert, der angibt, ob das Standard Dialogfeld für die System Farbe oder das Dialogfeld [cmfccolordialog](../../mfc/reference/cmfccolordialog-class.md) angezeigt werden soll.

*pbientbtn*<br/>
in Ein Zeiger auf eine übergeordnete Schaltfläche.

*nID*<br/>
in Die Befehls-ID.

### <a name="remarks"></a>Bemerkungen

Jeder überladene Konstruktor legt den `m_bEnabledInCustomizeMode` Member auf false fest.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein-Objekt erstellt wird `CMFCColorPopupMenu` .

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a> Cmfccolorpopupmenu:: kreatetearoffbar

Erstellt eine andockbare Farbleiste.

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*pwndmain*\
in Zeiger auf das übergeordnete Fenster der abzurufenden Leiste.

*uiid*\
in Die Befehls-ID der deaktivierten Leiste.

*lpszname*\
in Der Fenster Text der abtrenn Leiste.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neue abzurufbare Steuer leisten Objekt.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt ein [cmfccolorbar-Klassen](../../mfc/reference/cmfccolorbar-class.md) Objekt und wandelt es in einen [CPANE-Klassen](../../mfc/reference/cpane-class.md) Zeiger um. Sie können diesen Wert wieder in einen [cmfccolorbar-Klassen](../../mfc/reference/cmfccolorbar-class.md) Zeiger umwandeln, indem Sie eines der in [Typumwandlung von MFC-Klassen Objekten](../../mfc/reference/type-casting-of-mfc-class-objects.md)beschriebenen Umwandlungs Makros verwenden.

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a> Cmfccolorpopupmenu:: getmenubar

Gibt den [cmfcpopupmenubar](../../mfc/reference/cmfcpopupmenubar-class.md) -Wert zurück, der in das Popupmenü eingebettet ist.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die eingebettete `CMFCPopupMenuBar` .

### <a name="remarks"></a>Bemerkungen

Das Popup Menü für die Farbe verfügt über ein eingebettetes [cmfcpopupmenubar-Klassen](../../mfc/reference/cmfcpopupmenubar-class.md) Objekt. Überschreiben Sie diese Methode in einer abgeleiteten Klasse, wenn Ihre Anwendung einen anderen eingebetteten Typ verwendet.

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a> Cmfccolorpopupmenu:: setproplist

Legt das Eigenschaften Raster-Steuerelement Objekt des eingebetteten `CMFCColorBar` Objekts fest.

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parameter

*pwndlist*<br/>
in Zeiger auf ein Eigenschaften Raster-Steuerelement Objekt.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
