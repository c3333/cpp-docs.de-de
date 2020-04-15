---
title: CMFCHeaderCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: 0a6b0cf39861ba995acff71fc40cf44ae5114642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367460"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class

Die `CMFCHeaderCtrl` Klasse unterstützt das Sortieren mehrerer Spalten in einem Headersteuerelement.

## <a name="syntax"></a>Syntax

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|Erstellt ein `CMFCHeaderCtrl`-Objekt.|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Aktiviert oder deaktiviert den *Sortiermodus mehrerer Spalten* für das aktuelle Headersteuerelement.|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Gibt an, ob eine Spalte nicht sortiert oder in aufsteigender oder absteigender Reihenfolge sortiert ist.|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Ruft den nullbasierten Index der ersten sortierten Spalte im Headersteuerelement ab.|
|`CMFCHeaderCtrl::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCHeaderCtrl::IsAscending](#isascending)|Gibt an, ob eine Spalte im Kopfkopfsteuerelement in aufsteigender Reihenfolge sortiert ist.|
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Gibt an, ob das übergeordnete Fenster des aktuellen Kopfkopfsteuerelements ein Dialogfeld ist.|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Gibt an, ob sich das aktuelle Headersteuerelement im *Sortiermodus mehrerer Spalten* befindet.|
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Entfernt die angegebene Spalte aus der Liste der Sortierspalten.|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Legt die Sortierreihenfolge einer angegebenen Spalte in einem Kopfsteuerelement fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Wird vom Framework aufgerufen, um eine Headersteuerelementspalte zu zeichnen.|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Wird vom Framework aufgerufen, um den Sortierpfeil zu zeichnen.|
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Wird vom Framework aufgerufen, um den Hintergrund einer Headersteuerelementspalte zu füllen.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCHeaderCtrl` wie ein Objekt der Klasse erstellt wird und wie der *Sortiermodus* für mehrere Spalten für das aktuelle Headersteuerelement aktiviert wird.

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>Bemerkungen

Die `CMFCHeaderCtrl` Klasse zeichnet einen Sortierpfeil in einer Kopfsteuerelementspalte, um anzugeben, dass die Spalte sortiert ist. Verwenden Sie den *Sortiermodus mehrerer Spalten,* wenn ein Satz von Spalten im übergeordneten Listensteuerelement ( [CMFCListCtrl-Klasse](../../mfc/reference/cmfclistctrl-class.md)) gleichzeitig sortiert werden kann.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxheaderctrl.h

## <a name="cmfcheaderctrlcmfcheaderctrl"></a><a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl

Erstellt ein `CMFCHeaderCtrl`-Objekt.

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>Bemerkungen

Dieser Konstruktor initialisiert die folgenden Membervariablen auf die angegebenen Werte:

|Membervariable|Wert|
|---------------------|-----------|
|`m_bIsMousePressed`|FALSE|
|`m_bMultipleSort`|FALSE|
|`m_bAscending`|TRUE|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|FALSE|
|`m_bIsDlgControl`|FALSE|
|`m_hFont`|NULL|

## <a name="cmfcheaderctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCHeaderCtrl::EnableMultipleSort

Aktiviert oder deaktiviert den *Sortiermodus mehrerer Spalten* für das aktuelle Headersteuerelement.

```
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um den sortiermodus für mehrere Spalten zu aktivieren; FALSE, um den Sortiermodus mehrerer Spalten zu deaktivieren und alle Spalten aus der Liste der sortierten Spalten zu entfernen. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um den Sortiermodus für mehrere Spalten zu aktivieren oder zu deaktivieren. Zwei oder mehr Spalten können an einer Sortierung teilnehmen, wenn sich das Headersteuerelement im Sortiermodus für mehrere Spalten befindet.

## <a name="cmfcheaderctrlgetcolumnstate"></a><a name="getcolumnstate"></a>CMFCHeaderCtrl::GetColumnState

Gibt an, ob eine Spalte unsortiert oder in aufsteigender oder absteigender Reihenfolge sortiert ist.

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>Parameter

*iColumn*<br/>
[in] Der nullbasierte Index einer Spalte.

### <a name="return-value"></a>Rückgabewert

Ein Wert, der den Sortierstatus der angegebenen Spalte angibt. Die folgende Tabelle enthält die möglichen Werte:

|Wert|Beschreibung|
|-----------|-----------------|
|-1|Sortiert in absteigender Reihenfolge.|
|0|Nicht sortiert.|
|1|Sortiert in aufsteigender Reihenfolge.|

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcheaderctrlgetsortcolumn"></a><a name="getsortcolumn"></a>CMFCHeaderCtrl::GetSortColumn

Ruft den nullbasierten Index der ersten sortierten Spalte im Headersteuerelement ab.

```
int GetSortColumn() const;
```

### <a name="return-value"></a>Rückgabewert

Der Index einer sortierten Spalte oder -1, wenn keine sortierte Spalte gefunden wird.

### <a name="remarks"></a>Bemerkungen

Wenn sich das Headersteuerelement im *Modus für mehrere Spalten sortiert* und Sie die Anwendung im Debugmodus kompiliert haben, wird diese Methode bestätigt und rät Ihnen, stattdessen die [CMFCHeaderCtrl::GetColumnState-Methode](#getcolumnstate) zu verwenden. Wenn sich das Headersteuerelement im Modus für die Sortierung mehrerer Spalten befindet und Sie die Anwendung im Einzelhandelsmodus kompiliert haben, gibt diese Methode -1 zurück.

## <a name="cmfcheaderctrlisascending"></a><a name="isascending"></a>CMFCHeaderCtrl::IsAscending

Gibt an, ob eine Spalte im Kopfkopfsteuerelement in aufsteigender Reihenfolge sortiert ist.

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn eine Spalte im Headersteuerelement in aufsteigender Reihenfolge sortiert wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Der von dieser Methode zurückgegebene Wert wird verwendet, um den entsprechenden Sortierpfeil auf dem Kopfsteuerelementelement anzuzeigen. Verwenden Sie die [CMFCHeaderCtrl::SetSortColumn-Methode,](#setsortcolumn) um die Sortierreihenfolge festzulegen.

## <a name="cmfcheaderctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCHeaderCtrl::IsDialogControl

Gibt an, ob das übergeordnete Fenster des aktuellen Kopfkopfsteuerelements ein Dialogfeld ist.

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das übergeordnete Fenster des aktuellen Headersteuerelements ein Dialogfeld ist; andernfalls FALSE.

## <a name="cmfcheaderctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCHeaderCtrl::IsMultipleSort

Gibt an, ob sich das aktuelle Headersteuerelement im *Sortiermodus mehrerer Spalten* befindet.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Sortiermodus mehrerer Spalten aktiviert ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CMFCHeaderCtrl::EnableMultipleSort-Methode,](#enablemultiplesort) um den Sortiermodus für mehrere Spalten zu aktivieren oder zu deaktivieren. Zwei oder mehr Spalten können an einer Sortierung teilnehmen, wenn sich das Headersteuerelement im Sortiermodus für mehrere Spalten befindet.

## <a name="cmfcheaderctrlondrawitem"></a><a name="ondrawitem"></a>CMFCHeaderCtrl::OnDrawItem

Wird vom Framework aufgerufen, um eine Headersteuerelementspalte zu zeichnen.

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*iItem*<br/>
[in] Der nullbasierte Index des zu zeichnenden Elements.

*Rect*<br/>
[in] Das umgrenzende Rechteck des zu zeichnenden Elements.

*bIsPressed*<br/>
[in] TRUE, um das Element in gedrückten Zustand zu zeichnen; andernfalls FALSE.

*bIsHighlighted*<br/>
[in] TRUE, um das Element in hervorgehobenen Zustand zu zeichnen; andernfalls FALSE.

## <a name="cmfcheaderctrlondrawsortarrow"></a><a name="ondrawsortarrow"></a>CMFCHeaderCtrl::OnDrawSortArrow

Wird vom Framework aufgerufen, um den Sortierpfeil zu zeichnen.

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*rectArrow*<br/>
[in] Das umgrenzende Rechteck des Sortierpfeils.

## <a name="cmfcheaderctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCHeaderCtrl::OnFillBackground

Wird vom Framework aufgerufen, um den Hintergrund einer Headersteuerelementspalte zu füllen.

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcheaderctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCHeaderCtrl::RemoveSortColumn

Entfernt die angegebene Spalte aus der Liste der Sortierspalten.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parameter

*iColumn*<br/>
[in] Der nullbasierte Index der zu entfernenden Spalte.

## <a name="cmfcheaderctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCHeaderCtrl::SetSortColumn

Legt die Sortierreihenfolge einer angegebenen Spalte in einem Kopfsteuerelement fest.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>Parameter

*iColumn*<br/>
[in] Der nullbasierte Index einer Headersteuerelementspalte. Wenn dieser Parameter kleiner als Null ist, entfernt diese Methode alle Spalten aus der Liste der Sortierspalten.

*bAufstieg*<br/>
[in] Gibt die Sortierreihenfolge der Spalte an, die der *iColumn-Parameter* angibt. TRUE, um aufsteigende Reihenfolge festzulegen; FALSE, um die absteigende Reihenfolge festzulegen. Der Standardwert ist TRUE.

*bHinzufügen*<br/>
[in] TRUE, um die Sortierreihenfolge der Spalte festzulegen, die der *iColumn-Parameter* angibt.

Wenn sich das aktuelle Headersteuerelement im *Modus für die Sortierung mehrerer Spalten* befindet, fügt diese Methode die angegebene Spalte zur Liste der Sortierspalten hinzu. Verwenden Sie [CMFCHeaderCtrl::EnableMultipleSort,](#enablemultiplesort) um den Sortiermodus für mehrere Spalten festzulegen.

Wenn der Sortiermodus mehrerer Spalten nicht festgelegt ist und diese Methode im Debugmodus kompiliert wird, wird diese Methode bestätigt. Wenn der Sortiermodus für mehrere Spalten nicht festgelegt ist und diese Methode im Einzelhandelsmodus kompiliert wird, entfernt diese Methode zunächst alle Spalten aus der Liste der Sortierspalten und fügt dann die angegebene Spalte zur Liste hinzu.

FALSE, um zuerst alle Spalten aus der Liste der Sortierspalten zu entfernen und dann die angegebene Spalte zur Liste hinzuzufügen. Der Standardwert ist FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Sortierreihenfolge einer Spalte festzulegen. Bei Bedarf fügt diese Methode die Spalte zur Liste der Sortierspalten hinzu. Das Headersteuerelement verwendet die Sortierreihenfolge, um einen Sortierpfeil zu zeichnen, der nach oben oder unten zeigt.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl-Klasse](../../mfc/reference/cmfclistctrl-class.md)
