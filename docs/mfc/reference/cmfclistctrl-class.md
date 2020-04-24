---
title: CMFCListCtrl-Klasse
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
ms.openlocfilehash: 099ec086bd95a1180af4cf5a8f6a9fa7f1d099ea
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754234"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl-Klasse

Die `CMFCListCtrl` Klasse erweitert die Funktionalität der [CListCtrl-Klassenklasse,](../../mfc/reference/clistctrl-class.md) indem sie die erweiterte Headersteuerungsfunktionalität der [CMFCHeaderCtrl-Klasse](../../mfc/reference/cmfcheaderctrl-class.md)unterstützt.

## <a name="syntax"></a>Syntax

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Ermöglicht die Möglichkeit, eine sortierte Spalte mit einer anderen Hintergrundfarbe zu markieren.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Aktiviert den Mehrfachsorsermodus.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Gibt einen Verweis auf das unterstrichene Headersteuerelement zurück.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Überprüft, ob sich das Listensteuerelement im Mehrfachsorsermodus befindet.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Wird vom Framework aufgerufen, wenn es zwei Listensteuerelemente vergleichen muss.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Wird vom Framework aufgerufen, wenn es die Hintergrundfarbe einer einzelnen Zelle bestimmen muss.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Wird vom Framework aufgerufen, wenn es die Schriftart für die gezeichnete Zelle abrufen muss.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Wird vom Framework aufgerufen, wenn es die Textfarbe einer einzelnen Zelle bestimmen muss.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Entfernt eine Sortierspalte aus der Liste der sortierten Spalten.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Legt die aktuelle sortierte Spalte und die Sortierreihenfolge fest.|
|[CMFCListCtrl::Sortieren](#sort)|Sortiert das Listensteuerelement.|

## <a name="remarks"></a>Bemerkungen

`CMFCListCtrl`bietet zwei Erweiterungen der [CListCtrl-Klassenklasse.](../../mfc/reference/clistctrl-class.md) Zunächst wird angegeben, dass die Spaltensortierung eine verfügbare Option ist, indem automatisch ein Sortierpfeil auf der Kopfzeile gezeichnet wird. Zweitens unterstützt es die Datensortierung mehrerer Spalten gleichzeitig.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCListCtrl` -Klasse. Das Beispiel zeigt, wie Sie ein Listensteuerelement erstellen, Spalten einfügen, Elemente einfügen, den Text eines Elements festlegen und die Schriftart des Listensteuerelements festlegen. Dieser Codeausschnitt ist Teil des [Visual Studio Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxlistctrl.h

## <a name="cmfclistctrlenablemarksortedcolumn"></a><a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

Markiert die sortierten Spalten mit einer anderen Hintergrundfarbe.

```cpp
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*bMark*<br/>
[in] Ein boolescher Parameter, der bestimmt, ob eine andere Hintergrundfarbe aktiviert werden soll.

*bZeichnung*<br/>
[in] Ein boolescher Parameter, der bestimmt, ob das Steuerelement sofort neu gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

`EnableMarkSortedColumn`verwendet die `CDrawingManager::PixelAlpha` Methode, um zu berechnen, welche Farbe für sortierte Spalten verwendet werden soll. Die gewählte Farbe basiert auf der regulären Hintergrundfarbe.

## <a name="cmfclistctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

Ermöglicht das Sortieren der Datenzeilen im Listensteuerelement nach mehreren Spalten.

```cpp
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] Ein boolescher Wert, der angibt, ob der Sortiermodus für mehrere Spalten aktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die Sortierung basierend auf mehreren Spalten aktivieren, verfügen die Spalten über eine Hierarchie. Die Datenzeilen werden zuerst nach der primären Spalte sortiert. Alle äquivalenten Werte werden dann nach jeder nachfolgenden Spalte basierend auf der Priorität sortiert.

## <a name="cmfclistctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

Gibt einen Verweis auf das Headersteuerelement zurück.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das zugrunde liegende [CMFCHeaderCtrl-Objekt.](../../mfc/reference/cmfcheaderctrl-class.md)

### <a name="remarks"></a>Bemerkungen

Das Headersteuerelement für ein Listensteuerelement ist das Fenster, das die Titel für die Spalten enthält. Es befindet sich in der Regel direkt über den Spalten.

## <a name="cmfclistctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

Überprüft, ob das Listensteuerelement derzeit das Sortieren nach mehreren Spalten unterstützt.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Listensteuerelement mehrere Sortierungen unterstützt; FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Wenn eine [CMFCListCtrl-Klasse](../../mfc/reference/cmfclistctrl-class.md) mehrere Sortierungen unterstützt, kann der Benutzer die Daten im Listensteuerelement nach mehreren Spalten sortieren. Um die mehrfache Sortierung zu aktivieren, rufen Sie [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)auf.

## <a name="cmfclistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

Das Framework ruft diese Methode auf, wenn es zwei Elemente vergleicht.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parameter

*lParam1*<br/>
[in] Das erste zu vergleichende Element.

*lParam2*<br/>
[in] Das zweite zu vergleichende Element.

*iColumn*<br/>
[in] Der Index der Spalte, die diese Methode sortiert.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die die relative Position der beiden Elemente angibt. Ein negativer Wert gibt an, dass das erste Element dem zweiten vorangestellt werden soll, ein positiver Wert gibt an, dass das erste Element dem zweiten folgen soll, und Null bedeutet, dass die beiden Elemente äquivalent sind.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung gibt immer 0 zurück. Überschreiben Sie diese Funktion, um einen eigenen Sortieralgorithmus bereitzustellen.

## <a name="cmfclistctrlongetcellbkcolor"></a><a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

Das Framework ruft diese Methode auf, wenn es die Hintergrundfarbe einer einzelnen Zelle bestimmen muss.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parameter

*nRow*<br/>
[in] Die Zeile der betreffenden Zelle.

*nColumn*<br/>
[in] Die Spalte der betreffenden Zelle.

### <a name="return-value"></a>Rückgabewert

Ein COLOREF-Wert, der die Hintergrundfarbe der Zelle angibt.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung `OnGetCellBkColor` von verwendet nicht die angegebenen `GetBkColor`Eingabeparameter und ruft stattdessen einfach auf. Daher hat das gesamte Listensteuerelement standardmäßig dieselbe Hintergrundfarbe. Sie können `OnGetCellBkColor` in einer abgeleiteten Klasse überschreiben, um einzelne Zellen mit einer separaten Hintergrundfarbe zu markieren.

## <a name="cmfclistctrlongetcellfont"></a><a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

Das Framework ruft diese Methode auf, wenn die Schriftart für eine einzelne Zelle abruft.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Parameter

*nRow*<br/>
[in] Die Zeile der betreffenden Zelle.

*nColumn*<br/>
[in] Die Spalte der betreffenden Zelle.

*dwData*<br/>
[in] Benutzerdefinierte Daten. Die Standardimplementierung verwendet diesen Parameter nicht.

### <a name="return-value"></a>Rückgabewert

Ein Handle für die Schriftart, das für die aktuelle Zelle verwendet wird.

### <a name="remarks"></a>Bemerkungen

Standardmäßig gibt diese Methode NULL zurück. Alle Zellen in einem Listensteuerelement haben dieselbe Schriftart. Überschreiben Sie diese Methode, um verschiedene Schriftarten für verschiedene Zellen bereitzustellen.

## <a name="cmfclistctrlongetcelltextcolor"></a><a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

Das Framework ruft diese Methode auf, wenn es die Textfarbe einer einzelnen Zelle bestimmen muss.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parameter

*nRow*<br/>
[in] Die Zeile der betreffenden Zelle.

*nColumn*<br/>
[in] Die Spalte der betreffenden Zelle.

### <a name="return-value"></a>Rückgabewert

Ein COLOREF-Wert, der die Textfarbe der Zelle angibt.

### <a name="remarks"></a>Bemerkungen

Standardmäßig ruft diese `GetTextColor` Methode unabhängig von Eingabeparametern auf. Das gesamte Listensteuerelement hat dieselbe Textfarbe. Sie können `OnGetCellTextColor` in einer abgeleiteten Klasse überschreiben, um einzelne Zellen mit einer separaten Textfarbe zu markieren.

## <a name="cmfclistctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn

Entfernt eine Sortierspalte aus der Liste der sortierten Spalten.

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parameter

*iColumn*<br/>
[in] Die zu entfernende Spalte.

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt eine Sortierspalte aus dem Headersteuerelement. Es ruft [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)auf.

## <a name="cmfclistctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

Legt die aktuelle sortierte Spalte und die Sortierreihenfolge fest.

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parameter

*iColumn*<br/>
[in] Die zu sortierende Spalte.

*bAufstieg*<br/>
[in] Ein boolescher Wert, der die Sortierreihenfolge angibt.

*bHinzufügen*<br/>
[in] Ein boolescher Wert, der angibt, ob die Methode die durch *iColumn* angegebene Spalte zur Liste der Sortierspalten hinzufügt.

### <a name="remarks"></a>Bemerkungen

Diese Methode übergibt die Eingabeparameter an das Headersteuerelement mithilfe der Methode [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

## <a name="cmfclistctrlsort"></a><a name="sort"></a>CMFCListCtrl::Sortieren

Sortiert das Listensteuerelement.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parameter

*iColumn*<br/>
[in] Die zu sortierende Spalte.

*bAufstieg*<br/>
[in] Ein boolescher Wert, der die Sortierreihenfolge angibt.

*bHinzufügen*<br/>
[in] Ein boolescher Wert, der angibt, ob diese Methode die durch *iColumn* angegebene Spalte zur Liste der Sortierspalten hinzufügt.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl-Klasse](../../mfc/reference/clistctrl-class.md)
