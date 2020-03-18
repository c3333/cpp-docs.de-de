---
title: CMF CListCtrl-Klasse
ms.date: 07/30/2019
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
ms.openlocfilehash: 599a00af28ee5b8effbabbe5b334022ceb49f91a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425820"
---
# <a name="cmfclistctrl-class"></a>CMF CListCtrl-Klasse

Die `CMFCListCtrl`-Klasse erweitert die Funktionen der [CListCtrl-Klassen](../../mfc/reference/clistctrl-class.md) Klasse durch Unterstützung der erweiterten Header Steuerungs Funktionalität der [CMF-STRG-Klasse](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Syntax

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CMF CListCtrl:: enablemarksortedcolumn](#enablemarksortedcolumn)|Ermöglicht das Markieren einer sortierten Spalte mit einer anderen Hintergrundfarbe.|
|[CMF CListCtrl:: enablemultiplesort](#enablemultiplesort)|Aktiviert den mehrfach Sortiermodus.|
|[CMF CListCtrl:: getheiaderctrl](#getheaderctrl)|Gibt einen Verweis auf das unterstrichene Header Steuerelement zurück.|
|[CMF CListCtrl:: ismultiplesort](#ismultiplesort)|Überprüft, ob sich das Listen Steuerelement im mehrfach Sortiermodus befindet.|
|[CMF CListCtrl:: oncompareitems](#oncompareitems)|Wird von Framework aufgerufen, wenn zwei Listen Steuerungselemente verglichen werden müssen.|
|[CMF CListCtrl:: ongetcellbkcolor](#ongetcellbkcolor)|Wird von Framework aufgerufen, wenn es die Hintergrundfarbe einer einzelnen Zelle bestimmen muss.|
|[CMF CListCtrl:: ongetcellfont](#ongetcellfont)|Wird von Framework aufgerufen, wenn es die Schriftart für die gezeichnete Zelle abrufen muss.|
|[CMF CListCtrl:: ongetcelltextcolor](#ongetcelltextcolor)|Wird von Framework aufgerufen, wenn es die Textfarbe einer einzelnen Zelle bestimmen muss.|
|[CMF CListCtrl:: removesortcolumn](#removesortcolumn)|Entfernt eine Sortier Spalte aus der Liste der sortierten Spalten.|
|[CMF CListCtrl:: setsortcolumn](#setsortcolumn)|Legt die aktuelle sortierte Spalte und die Sortierreihenfolge fest.|
|[CMF CListCtrl:: Sort](#sort)|Sortiert das Listen Steuerelement.|

## <a name="remarks"></a>Hinweise

`CMFCListCtrl` bietet zwei Verbesserungen an der [CListCtrl Class](../../mfc/reference/clistctrl-class.md) -Klasse. Zuerst zeigt dies an, dass die Spalten Sortierung eine verfügbare Option ist, indem automatisch ein Sortier Pfeil für den Header gezeichnet wird. Zweitens wird die Daten Sortierung für mehrere Spalten gleichzeitig unterstützt.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCListCtrl` -Klasse. Das Beispiel zeigt, wie ein Listen Steuerelement erstellt, Spalten eingefügt, Elemente eingefügt, der Text eines Elements festgelegt und die Schriftart des Listen Steuer Elements festgelegt wird. Dieser Code Ausschnitt ist Teil des [Visual Studio-Demo](../../overview/visual-cpp-samples.md)Beispiels.

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMF CListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Voraussetzungen

**Header:** afxlistctrl. h

##  <a name="enablemarksortedcolumn"></a>CMF CListCtrl:: enablemarksortedcolumn

Markiert die sortierten Spalten mit einer anderen Hintergrundfarbe.

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*BMARK*<br/>
in Ein boolescher Parameter, der bestimmt, ob eine andere Hintergrundfarbe aktiviert werden soll.

*bredraw*<br/>
in Ein boolescher Parameter, der bestimmt, ob das Steuerelement sofort neu gezeichnet werden soll.

### <a name="remarks"></a>Hinweise

`EnableMarkSortedColumn` verwendet die-Methode `CDrawingManager::PixelAlpha`, um zu berechnen, welche Farbe für sortierte Spalten verwendet werden soll. Die ausgewählte Farbe basiert auf der regulären Hintergrundfarbe.

##  <a name="enablemultiplesort"></a>CMF CListCtrl:: enablemultiplesort

Ermöglicht das Sortieren der Daten Zeilen im Listen Steuerelement durch mehrere Spalten.

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*benabel*<br/>
in Ein boolescher Wert, der angibt, ob der mehrere Spalten Sortiermodus aktiviert werden soll.

### <a name="remarks"></a>Hinweise

Wenn Sie die Sortierung auf der Grundlage mehrerer Spalten aktivieren, verfügen die Spalten über eine Hierarchie. Die Daten Zeilen werden zuerst nach der primären Spalte sortiert. Alle äquivalenten Werte werden dann basierend auf der Priorität nach jeder nachfolgenden Spalte sortiert.

##  <a name="getheaderctrl"></a>CMF CListCtrl:: getheiaderctrl

Gibt einen Verweis auf das Header Steuerelement zurück.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das zugrunde liegende [cmfcheaderctrl](../../mfc/reference/cmfcheaderctrl-class.md) -Objekt.

### <a name="remarks"></a>Hinweise

Das Header Steuerelement für ein Listen Steuerelement ist das Fenster, das die Titel für die Spalten enthält. Sie befindet sich normalerweise direkt oberhalb der Spalten.

##  <a name="ismultiplesort"></a>CMF CListCtrl:: ismultiplesort

Überprüft, ob das Listen Steuerelement momentan das Sortieren mehrerer Spalten unterstützt.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Listen Steuerelement mehrere Sortierungen unterstützt. Andernfalls false.

### <a name="remarks"></a>Hinweise

Wenn eine [CMF CListCtrl-Klasse](../../mfc/reference/cmfclistctrl-class.md) mehrere Sortierungen unterstützt, kann der Benutzer die Daten im Listen Steuerelement nach mehreren Spalten sortieren. Um mehrere Sortierungen zu aktivieren, muss [cmfclistctrl:: enablemultiplesort](#enablemultiplesort)aufgerufen werden.

##  <a name="oncompareitems"></a>CMF CListCtrl:: oncompareitems

Das Framework ruft diese Methode auf, wenn zwei Elemente verglichen werden.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parameter

*lParam1*<br/>
in Das erste zu vergleichende Element.

*lParam2*<br/>
in Das zweite zu vergleichende Element.

*icolumn*<br/>
in Der Index der Spalte, die von dieser Methode sortiert wird.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die die relative Position der beiden Elemente angibt. Ein negativer Wert gibt an, dass das erste Element dem zweiten vorangestellt wird. ein positiver Wert gibt an, dass das erste Element dem zweiten Element folgen soll, und 0 bedeutet, dass die beiden Elemente äquivalent sind.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung gibt immer 0 (null) zurück. Überschreiben Sie diese Funktion, um einen eigenen Sortieralgorithmus bereitzustellen.

##  <a name="ongetcellbkcolor"></a>CMF CListCtrl:: ongetcellbkcolor

Das Framework ruft diese Methode auf, wenn die Hintergrundfarbe einer einzelnen Zelle bestimmt werden muss.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parameter

*nzeile*<br/>
in Die Zeile der fraglichen Zelle.

*ncolumn*<br/>
in Die Spalte der fraglichen Zelle.

### <a name="return-value"></a>Rückgabewert

Ein coloref-Wert, der die Hintergrundfarbe der Zelle angibt.

### <a name="remarks"></a>Hinweise

Die Standard Implementierung von `OnGetCellBkColor` verwendet nicht die angegebenen Eingabeparameter und ruft stattdessen einfach `GetBkColor`auf. Daher hat das gesamte Listen Steuerelement standardmäßig dieselbe Hintergrundfarbe. Sie können `OnGetCellBkColor` in einer abgeleiteten Klasse überschreiben, um einzelne Zellen mit einer separaten Hintergrundfarbe zu markieren.

##  <a name="ongetcellfont"></a>CMF CListCtrl:: ongetcellfont

Das Framework ruft diese Methode auf, wenn die Schriftart für eine einzelne Zelle abgerufen wird.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Parameter

*nzeile*<br/>
in Die Zeile der fraglichen Zelle.

*ncolumn*<br/>
in Die Spalte der fraglichen Zelle.

*dwdata*<br/>
in Benutzerdefinierte Daten. Die Standard Implementierung verwendet diesen Parameter nicht.

### <a name="return-value"></a>Rückgabewert

Ein Handle für die Schriftart, die für die aktuelle Zelle verwendet wird.

### <a name="remarks"></a>Hinweise

Standardmäßig gibt diese Methode NULL zurück. Alle Zellen in einem Listen Steuerelement haben dieselbe Schriftart. Überschreiben Sie diese Methode, um verschiedene Schriftarten für verschiedene Zellen bereitzustellen.

##  <a name="ongetcelltextcolor"></a>CMF CListCtrl:: ongetcelltextcolor

Das Framework ruft diese Methode auf, wenn Sie die Textfarbe einer einzelnen Zelle bestimmen muss.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parameter

*nzeile*<br/>
in Die Zeile der fraglichen Zelle.

*ncolumn*<br/>
in Die Spalte der fraglichen Zelle.

### <a name="return-value"></a>Rückgabewert

Ein coloref-Wert, der die Textfarbe der Zelle angibt.

### <a name="remarks"></a>Hinweise

Standardmäßig ruft diese Methode `GetTextColor` unabhängig von den Eingabe Parametern auf. Das gesamte Listen Steuerelement hat dieselbe Textfarbe. Sie können `OnGetCellTextColor` in einer abgeleiteten Klasse überschreiben, um einzelne Zellen mit einer separaten Textfarbe zu markieren.

##  <a name="removesortcolumn"></a>CMF CListCtrl:: removesortcolumn

Entfernt eine Sortier Spalte aus der Liste der sortierten Spalten.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parameter

*icolumn*<br/>
in Die Spalte, die entfernt werden soll.

### <a name="remarks"></a>Hinweise

Mit dieser Methode wird eine Sortier Spalte aus dem Header Steuerelement entfernt. Sie ruft [CMF-Datei-STRG:: removesortcolumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)auf.

##  <a name="setsortcolumn"></a>CMF CListCtrl:: setsortcolumn

Legt die aktuelle sortierte Spalte und die Sortierreihenfolge fest.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parameter

*icolumn*<br/>
in Die zu sortierende Spalte.

*bascending*<br/>
in Ein boolescher Wert, der die Sortierreihenfolge angibt.

*Badd*<br/>
in Ein boolescher Wert, der angibt, ob die Methode die Spalte, die von *icolumn* angegeben wird, der Liste der Sortier Spalten hinzufügt.

### <a name="remarks"></a>Hinweise

Diese Methode übergibt die Eingabeparameter mithilfe der [cmfcheaderctrl:: setsortcolumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)-Methode an das Header-Steuerelement.

##  <a name="sort"></a>CMF CListCtrl:: Sort

Sortiert das Listen Steuerelement.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parameter

*icolumn*<br/>
in Die zu sortierende Spalte.

*bascending*<br/>
in Ein boolescher Wert, der die Sortierreihenfolge angibt.

*Badd*<br/>
in Ein boolescher Wert, der angibt, ob diese Methode die Spalte, die von *icolumn* angegeben wird, der Liste der Sortier Spalten hinzufügt.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl-Klasse](../../mfc/reference/clistctrl-class.md)
