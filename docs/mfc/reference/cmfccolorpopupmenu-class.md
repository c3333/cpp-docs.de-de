---
title: CMFCColorPopupMenu-Klasse
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
ms.openlocfilehash: bcdf60c974ecdc437b90891d2b46a5eec94859d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367678"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu-Klasse

Stellt ein Popupmenü dar, mit dem Benutzer Farben in einem Dokument oder einer Anwendung auswählen.

## <a name="syntax"></a>Syntax

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Erstellt ein `CMFCColorPopupMenu`-Objekt.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Erstellt eine andockbare Abreißfarbe. (Überschreibt [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Gibt die [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) zurück, die in das Popupmenü eingebettet ist. (Überschreibt [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|
|`CMFCColorPopupMenu::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Legt das Eigenschaftenraster-Steuerelementobjekt `CMFCColorBar` des eingebetteten Objekts fest.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|Name|BESCHREIBUNG|
|`m_bEnabledInCustomizeMode`|Ein boolescher Wert, der bestimmt, ob der Farbbalken angezeigt werden soll.|
|`m_wndColorBar`|Das `CMFCColorBar` Objekt, das eine Farbauswahl bereitstellt.|

### <a name="remarks"></a>Bemerkungen

Diese Klasse erbt die Popupmenüfunktionalität `CMFCPopupMenu` der Klasse `CMFCColorBar` und verwaltet ein Objekt, das eine Farbauswahl bereitstellt. Wenn sich das Symbolleistenframework im `m_bEnabledInCustomizeMode` Anpassungsmodus befindet und das Element auf FALSE festgelegt ist, wird das Farbbalkenobjekt nicht angezeigt. Weitere Informationen zum Anpassungsmodus finden Sie unter [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Weitere Informationen `CMFCColorBar`zu finden Sie unter [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxcolorpopupmenu.h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a>CMFCColorPopupMenu::CMFCColorPopupMenu

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

*Farben*<br/>
[in] Ein Array von Farben, das das Framework im Popupmenü anzeigt.

*Farbe*<br/>
[in] Die standardmäßig ausgewählte Farbe.

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

*nHorzDockRows*<br/>
[in] Die Anzahl der Zeilen, die die Farbleiste hat, wenn sie horizontal angedockt wird.

*nVertDockColumns*<br/>
[in] Die Anzahl der Spalten, die die Farbleiste enthält, wenn sie vertikal angedockt wird.

*colorAutomatic*<br/>
[in] Die Standardfarbe, die das Framework anwendet, wenn Sie auf die automatische Schaltfläche klicken.

*uiCommandID*<br/>
[in] Die Befehls-ID für die Farbleistesteuerung.

*bStdColorDlg*<br/>
[in] Ein boolescher Wert, der angibt, ob das Standardmäßige Systemfarbdialogfeld oder das Dialogfeld [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) angezeigt werden soll.

*pParentBtn*<br/>
[in] Ein Zeiger auf eine übergeordnete Schaltfläche.

*nID*<br/>
[in] Die Befehls-ID.

### <a name="remarks"></a>Bemerkungen

Jeder überladene Konstruktor legt den `m_bEnabledInCustomizeMode` Member auf FALSE fest.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCColorPopupMenu` veranschaulicht, wie ein Objekt erstellt wird.

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a>CMFCColorPopupMenu::CreateTearOffBar

Erstellt eine andockbare Abreißfarbe.

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*pWndMain*|[in] Zeigen Sie auf das übergeordnete Fenster der Abreißleiste.|
|*uiID*|[in] Die Befehls-ID der Abreißleiste.|
|*lpszName*|[in] Der Fenstertext der Abreißleiste.|

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neue Abreißsteuerungsleistenobjekt.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt ein [CMFCColorBar-Klassenobjekt](../../mfc/reference/cmfccolorbar-class.md) und wird in einen [CPane-Klassenzeiger](../../mfc/reference/cpane-class.md) umgeworfen. Sie können diesen Wert in einen [CMFCColorBar-Klassenzeiger](../../mfc/reference/cmfccolorbar-class.md) zurückwerfen, indem Sie eines der in [Typumwandlung von MFC-Klassenobjekten](../../mfc/reference/type-casting-of-mfc-class-objects.md)beschriebenen Umwandlungsmakros verwenden.

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a>CMFCColorPopupMenu::GetMenuBar

Gibt die [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) zurück, die in das Popupmenü eingebettet ist.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CMFCPopupMenuBar`die eingebettete .

### <a name="remarks"></a>Bemerkungen

Das Farb-Popup-Menü verfügt über ein eingebettetes [CMFCPopupMenuBar-Klassenobjekt.](../../mfc/reference/cmfcpopupmenubar-class.md) Überschreiben Sie diese Methode in einer abgeleiteten Klasse, wenn Ihre Anwendung einen anderen eingebetteten Typ verwendet.

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a>CMFCColorPopupMenu::SetPropList

Legt das Eigenschaftenraster-Steuerelementobjekt `CMFCColorBar` des eingebetteten Objekts fest.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parameter

*pWndList*<br/>
[in] Zeiger auf ein Eigenschaftenraster-Steuerelementobjekt.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
