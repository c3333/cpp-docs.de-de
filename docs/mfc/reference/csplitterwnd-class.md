---
title: CSplitterWnd-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSplitterWnd
- AFXEXT/CSplitterWnd
- AFXEXT/CSplitterWnd::CSplitterWnd
- AFXEXT/CSplitterWnd::ActivateNext
- AFXEXT/CSplitterWnd::CanActivateNext
- AFXEXT/CSplitterWnd::Create
- AFXEXT/CSplitterWnd::CreateScrollBarCtrl
- AFXEXT/CSplitterWnd::CreateStatic
- AFXEXT/CSplitterWnd::CreateView
- AFXEXT/CSplitterWnd::DeleteColumn
- AFXEXT/CSplitterWnd::DeleteRow
- AFXEXT/CSplitterWnd::DeleteView
- AFXEXT/CSplitterWnd::DoKeyboardSplit
- AFXEXT/CSplitterWnd::DoScroll
- AFXEXT/CSplitterWnd::DoScrollBy
- AFXEXT/CSplitterWnd::GetActivePane
- AFXEXT/CSplitterWnd::GetColumnCount
- AFXEXT/CSplitterWnd::GetColumnInfo
- AFXEXT/CSplitterWnd::GetPane
- AFXEXT/CSplitterWnd::GetRowCount
- AFXEXT/CSplitterWnd::GetRowInfo
- AFXEXT/CSplitterWnd::GetScrollStyle
- AFXEXT/CSplitterWnd::IdFromRowCol
- AFXEXT/CSplitterWnd::IsChildPane
- AFXEXT/CSplitterWnd::IsTracking
- AFXEXT/CSplitterWnd::RecalcLayout
- AFXEXT/CSplitterWnd::SetActivePane
- AFXEXT/CSplitterWnd::SetColumnInfo
- AFXEXT/CSplitterWnd::SetRowInfo
- AFXEXT/CSplitterWnd::SetScrollStyle
- AFXEXT/CSplitterWnd::SplitColumn
- AFXEXT/CSplitterWnd::SplitRow
- AFXEXT/CSplitterWnd::OnDraw
- AFXEXT/CSplitterWnd::OnDrawSplitter
- AFXEXT/CSplitterWnd::OnInvertTracker
helpviewer_keywords:
- CSplitterWnd [MFC], CSplitterWnd
- CSplitterWnd [MFC], ActivateNext
- CSplitterWnd [MFC], CanActivateNext
- CSplitterWnd [MFC], Create
- CSplitterWnd [MFC], CreateScrollBarCtrl
- CSplitterWnd [MFC], CreateStatic
- CSplitterWnd [MFC], CreateView
- CSplitterWnd [MFC], DeleteColumn
- CSplitterWnd [MFC], DeleteRow
- CSplitterWnd [MFC], DeleteView
- CSplitterWnd [MFC], DoKeyboardSplit
- CSplitterWnd [MFC], DoScroll
- CSplitterWnd [MFC], DoScrollBy
- CSplitterWnd [MFC], GetActivePane
- CSplitterWnd [MFC], GetColumnCount
- CSplitterWnd [MFC], GetColumnInfo
- CSplitterWnd [MFC], GetPane
- CSplitterWnd [MFC], GetRowCount
- CSplitterWnd [MFC], GetRowInfo
- CSplitterWnd [MFC], GetScrollStyle
- CSplitterWnd [MFC], IdFromRowCol
- CSplitterWnd [MFC], IsChildPane
- CSplitterWnd [MFC], IsTracking
- CSplitterWnd [MFC], RecalcLayout
- CSplitterWnd [MFC], SetActivePane
- CSplitterWnd [MFC], SetColumnInfo
- CSplitterWnd [MFC], SetRowInfo
- CSplitterWnd [MFC], SetScrollStyle
- CSplitterWnd [MFC], SplitColumn
- CSplitterWnd [MFC], SplitRow
- CSplitterWnd [MFC], OnDraw
- CSplitterWnd [MFC], OnDrawSplitter
- CSplitterWnd [MFC], OnInvertTracker
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
ms.openlocfilehash: 8c8ce90f5e36d6cdc2592233588bc3bd7bf2c9d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371695"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd-Klasse

Stellt die Funktionalität eines unterteilten Fensters bereit. Dabei handelt es sich um ein Fenster, das mehrere Bereiche enthält.

## <a name="syntax"></a>Syntax

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Rufen Sie `CSplitterWnd` auf, um ein Objekt zu erstellen.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSplitterWnd::ActivateNext](#activatenext)|Führt den Befehl Nächster Bereich oder Vorheriger Bereich aus.|
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Überprüft, ob der Befehl Nächster Bereich oder Vorheriger Bereich derzeit möglich ist.|
|[CSplitterWnd::Erstellen](#create)|Rufen Sie auf, um ein dynamisches Splitterfenster zu erstellen und es an das `CSplitterWnd` Objekt anzuhängen.|
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Erstellt ein gemeinsames Bildlaufleistensteuerelement.|
|[CSplitterWnd::CreateStatic](#createstatic)|Rufen Sie auf, um ein statisches Splitterfenster zu erstellen und es an das `CSplitterWnd` Objekt anzuhängen.|
|[CSplitterWnd::CreateView](#createview)|Rufen Sie an, einen Bereich in einem Splitterfenster zu erstellen.|
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Löscht eine Spalte aus dem Splitterfenster.|
|[CSplitterWnd::DeleteRow](#deleterow)|Löscht eine Zeile aus dem Splitterfenster.|
|[CSplitterWnd::DeleteView](#deleteview)|Löscht eine Ansicht aus dem Splitterfenster.|
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Führt den Befehl "Tastaturteilung" aus, in der Regel "Window Split".|
|[CSplitterWnd::DoScroll](#doscroll)|Führt ein synchronisiertes Scrollen von geteilten Fenstern durch.|
|[CSplitterWnd::DoScrollBy](#doscrollby)|Scrollen Sie geteilte Fenster um eine bestimmte Anzahl von Pixeln.|
|[CSplitterWnd::GetActivePane](#getactivepane)|Bestimmt den aktiven Bereich aus dem Fokus oder der aktiven Ansicht im Rahmen.|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Gibt die aktuelle Bereichsspaltenanzahl zurück.|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Gibt Informationen für die angegebene Spalte zurück.|
|[CSplitterWnd::GetPane](#getpane)|Gibt den Bereich an der angegebenen Zeile und Spalte zurück.|
|[CSplitterWnd::GetRowCount](#getrowcount)|Gibt die aktuelle Bereichszeilenanzahl zurück.|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Gibt Informationen für die angegebene Zeile zurück.|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Gibt den freigegebenen Bildlaufleistenstil zurück.|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Gibt die untergeordnete Fenster-ID des Bereichs an der angegebenen Zeile und Spalte zurück.|
|[CSplitterWnd::IsChildPane](#ischildpane)|Rufen Sie an, um zu ermitteln, ob es sich bei dem Fenster derzeit um einen untergeordneten Bereich dieses Splitterfensters handelt.|
|[CSplitterWnd::IsTracking](#istracking)|Bestimmt, ob die Splitterleiste gerade verschoben wird.|
|[CSplitterWnd::RecalcLayout](#recalclayout)|Rufen Sie den Aufruf auf, das Splitterfenster nach dem Anpassen der Zeilen- oder Spaltengröße erneut anzuzeigen.|
|[CSplitterWnd::SetActivePane](#setactivepane)|Legt einen Bereich fest, der im Rahmen aktiv ist.|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Rufen Sie den Aufruf auf, um die angegebenen Spalteninformationen festzulegen.|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Rufen Sie an, um die angegebenen Zeileninformationen festzulegen.|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Gibt den neuen Bildlaufleistenstil für die gemeinsam genutzte Bildlaufleistenunterstützung des Splitterfensters an.|
|[CSplitterWnd::SplitColumn](#splitcolumn)|Gibt an, wo ein Rahmenfenster vertikal geteilt wird.|
|[CSplitterWnd::SplitRow](#splitrow)|Gibt an, wo ein Rahmenfenster horizontal geteilt wird.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSplitterWnd::OnDraw](#ondraw)|Wird vom Framework aufgerufen, um das Splitterfenster zu zeichnen.|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Rendert ein Bild eines geteilten Fensters.|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Rendert das Bild eines geteilten Fensters so, dass es die gleiche Größe und Form wie das Rahmenfenster hat.|

## <a name="remarks"></a>Bemerkungen

Ein Bereich ist in der Regel ein anwendungsspezifisches Objekt, das von [CView](../../mfc/reference/cview-class.md)abgeleitet wird, kann jedoch jedes [CWnd-Objekt](../../mfc/reference/cwnd-class.md) sein, das über die entsprechende untergeordnete Fenster-ID verfügt.

Ein `CSplitterWnd` Objekt wird in der Regel in ein übergeordnetes [CFrameWnd-](../../mfc/reference/cframewnd-class.md) oder [CMDIChildWnd-Objekt](../../mfc/reference/cmdichildwnd-class.md) eingebettet. Erstellen `CSplitterWnd` Sie ein Objekt mit den folgenden Schritten:

1. Einbetten `CSplitterWnd` einer Membervariablen in den übergeordneten Frame.

2. Überschreiben Sie die [CFrameWnd::OnCreateClient-Memberfunktion](../../mfc/reference/cframewnd-class.md#oncreateclient) des übergeordneten Frames.

3. Rufen Sie innerhalb `OnCreateClient`der überschriebenen , die `CSplitterWnd` [Memberfunktion Create](#create) oder [CreateStatic](#createstatic) von auf.

Rufen `Create` Sie die Memberfunktion auf, um ein dynamisches Splitterfenster zu erstellen. Ein dynamisches Splitterfenster wird in der Regel verwendet, um eine Reihe von einzelnen Bereichen oder Ansichten desselben Dokuments zu erstellen und zu scrollen. Das Framework erstellt automatisch einen Anfangsbereich für den Splitter. dann erstellt, ändert und entsorgt das Framework zusätzliche Bereiche, während der Benutzer die Steuerelemente des Splitterfensters bedient.

Wenn Sie `Create`aufrufen, geben Sie eine minimale Zeilenhöhe und Spaltenbreite an, die bestimmen, wann die Bereiche zu klein sind, um vollständig angezeigt zu werden. Nach dem `Create`Aufruf können Sie diese Mindestwerte anpassen, indem Sie die Elementfunktionen [SetColumnInfo](#setcolumninfo) und [SetRowInfo](#setrowinfo) aufrufen.

Verwenden Sie `SetColumnInfo` `SetRowInfo` auch die und Member-Funktionen, um eine "ideale" Breite für eine Spalte und "ideale" Höhe für eine Zeile festzulegen. Wenn das Framework ein Splitterfenster anzeigt, wird zuerst der übergeordnete Rahmen und dann das Splitterfenster angezeigt. Das Framework legt dann die Bereiche in Spalten und Zeilen entsprechend ihren idealen Abmessungen fest und arbeitet von der oberen linken bis zur unteren rechten Ecke des Clientbereichs des Splitterfensters.

Alle Bereiche in einem dynamischen Splitterfenster müssen derselben Klasse andermaßen. Bekannte Anwendungen, die dynamische Splitterfenster unterstützen, sind Microsoft Word und Microsoft Excel.

Verwenden `CreateStatic` Sie die Memberfunktion, um ein statisches Splitterfenster zu erstellen. Der Benutzer kann nur die Größe der Bereiche in einem statischen Splitterfenster ändern, nicht deren Anzahl oder Reihenfolge.

Sie müssen beim Erstellen des statischen Splitters speziell alle Bereiche des statischen Splitters erstellen. Stellen Sie sicher, dass Sie alle Bereiche `OnCreateClient` erstellen, bevor die Memberfunktion des übergeordneten Frames zurückgegeben wird, oder das Framework zeigt das Fenster nicht ordnungsgemäß an.

Die `CreateStatic` Memberfunktion initialisiert automatisch einen statischen Splitter mit einer minimalen Zeilenhöhe und Spaltenbreite von 0. Passen Sie `Create`nach dem Aufruf diese Mindestwerte an, indem Sie die Memberfunktionen [SetColumnInfo](#setcolumninfo) und [SetRowInfo](#setrowinfo) aufrufen. Verwenden `SetColumnInfo` Sie `SetRowInfo` auch `CreateStatic` und nach dem Aufruf, um die gewünschten idealen Bereichsbemaßungen anzugeben.

Die einzelnen Bereiche eines statischen Splitters gehören oft zu verschiedenen Klassen. Beispiele für statische Splitterfenster finden Sie im Grafikeditor und im Windows-Datei-Manager.

Ein Splitterfenster unterstützt spezielle Bildlaufleisten (abgesehen von den Bildlaufleisten, die möglicherweise über Fenster verfügen). Diese Bildlaufleisten sind `CSplitterWnd` untergeordnete Elemente des Objekts und werden für die Bereiche freigegeben.

Sie erstellen diese speziellen Bildlaufleisten, wenn Sie das Splitterfenster erstellen. Beispielsweise zeigt `CSplitterWnd` eine, die eine Zeile, zwei Spalten und den stil WS_VSCROLL hat, eine vertikale Bildlaufleiste an, die von den beiden Bereichen gemeinsam genutzt wird. Wenn der Benutzer die Bildlaufleiste verschiebt, werden WM_VSCROLL Nachrichten an beide Bereiche gesendet. Wenn die Bereiche die Bildlaufleistenposition festlegen, wird die gemeinsame Bildlaufleiste gesetzt.

Weitere Informationen zu Splitterfenstern finden Sie unter [Technische Anmerkung 29](../../mfc/tn029-splitter-windows.md).

Weitere Informationen zum Erstellen dynamischer Splitterfenster finden Sie unter:

- MFC-Beispiel [Scribble](../../overview/visual-cpp-samples.md)

- MFC-Beispiel [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxext.h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterWnd::ActivateNext

Wird vom Framework aufgerufen, um den Befehl Nächster Bereich oder Vorheriger Bereich auszuführen.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parameter

*bPrev*<br/>
Gibt an, welches Fenster aktiviert werden soll. **TRUE** für vorherige; **FALSE** für den nächsten.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist ein Befehl auf hoher Ebene, der `CSplitterWnd` von der [CView-Klasse](../../mfc/reference/cview-class.md) verwendet wird, um an die Implementierung zu delegieren.

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterWnd::CanActivateNext

Wird vom Framework aufgerufen, um zu überprüfen, ob der Befehl Nächster Bereich oder Vorheriger Bereich derzeit möglich ist.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parameter

*bPrev*<br/>
Gibt an, welches Fenster aktiviert werden soll. **TRUE** für vorherige; **FALSE** für den nächsten.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist ein Befehl auf hoher Ebene, der `CSplitterWnd` von der [CView-Klasse](../../mfc/reference/cview-class.md) verwendet wird, um an die Implementierung zu delegieren.

## <a name="csplitterwndcreate"></a><a name="create"></a>CSplitterWnd::Erstellen

Um ein dynamisches Splitterfenster `Create` zu erstellen, rufen Sie die Memberfunktion auf.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    int nMaxRows,
    int nMaxCols,
    SIZE sizeMin,
    CCreateContext* pContext,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_HSCROLL | WS_VSCROLL | SPLS_DYNAMIC_SPLIT,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Das übergeordnete Rahmenfenster des Splitterfensters.

*nMaxRows*<br/>
Die maximale Anzahl von Zeilen im Splitterfenster. Dieser Wert darf 2 nicht überschreiten.

*nMaxCols*<br/>
Die maximale Anzahl von Spalten im Splitterfenster. Dieser Wert darf 2 nicht überschreiten.

*größeMin*<br/>
Gibt die Mindestgröße an, bei der ein Bereich angezeigt werden kann.

*pContext*<br/>
Ein Zeiger auf eine [CCreateContext-Struktur.](../../mfc/reference/ccreatecontext-structure.md) In den meisten Fällen kann dies der *pContext* sein, der an das übergeordnete Rahmenfenster übergeben wird.

*dwStyle*<br/>
Gibt den Fensterstil an.

*nID*<br/>
Die untergeordnete Fenster-ID des Fensters. Die ID kann AFX_IDW_PANE_FIRST werden, es sei denn, das Splitterfenster ist in einem anderen Splitterfenster verschachtelt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie können ein `CSplitterWnd` in ein übergeordnetes [CFrameWnd-](../../mfc/reference/cframewnd-class.md) oder [CMDIChildWnd-Objekt](../../mfc/reference/cmdichildwnd-class.md) einbetten, indem Sie die folgenden Schritte ausführen:

1. Einbetten `CSplitterWnd` einer Membervariablen in den übergeordneten Frame.

1. Überschreiben Sie die [CFrameWnd::OnCreateClient-Memberfunktion](../../mfc/reference/cframewnd-class.md#oncreateclient) des übergeordneten Frames.

1. Rufen `Create` Sie die Memberfunktion `OnCreateClient`innerhalb der überschriebenen auf.

Wenn Sie ein Splitterfenster innerhalb eines übergeordneten Frames erstellen, übergeben Sie den *pContext-Parameter* des übergeordneten Frames an das Splitterfenster. Andernfalls kann dieser Parameter NULL sein.

Die anfängliche minimale Zeilenhöhe und Spaltenbreite eines dynamischen Splitterfensters wird durch den *Parameter sizeMin* festgelegt. Diese Minimums, die bestimmen, ob ein Bereich zu klein ist, um vollständig angezeigt zu werden, können mit den Memberfunktionen [SetRowInfo](#setrowinfo) und [SetColumnInfo](#setcolumninfo) geändert werden.

Weitere Informationen zu dynamischen Splitterfenstern finden Sie unter "Splitter-Fenster" im Artikel [Mehrere Dokumenttypen, Ansichten und Frame-Fenster](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technische Anmerkung 29](../../mfc/tn029-splitter-windows.md)und die `CSplitterWnd` Klassenübersicht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterWnd::CreateScrollBarCtrl

Wird vom Framework aufgerufen, um ein gemeinsames Bildlaufleistensteuerelement zu erstellen.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Fensterstil an.

*nID*<br/>
Die untergeordnete Fenster-ID des Fensters. Die ID kann AFX_IDW_PANE_FIRST werden, es sei denn, das Splitterfenster ist in einem anderen Splitterfenster verschachtelt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Überschreiben, `CreateScrollBarCtrl` um zusätzliche Steuerelemente neben einer Bildlaufleiste einzuschließen. Das Standardverhalten besteht darin, normale Windows-Bildlaufleistensteuerelemente zu erstellen.

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterWnd::CreateStatic

Um ein statisches Splitterfenster `CreateStatic` zu erstellen, rufen Sie die Memberfunktion auf.

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Das übergeordnete Rahmenfenster des Splitterfensters.

*nRows*<br/>
Die Anzahl der Zeilen. Dieser Wert darf 16 nicht überschreiten.

*nCols*<br/>
Die Anzahl der Spalten. Dieser Wert darf 16 nicht überschreiten.

*dwStyle*<br/>
Gibt den Fensterstil an.

*nID*<br/>
Die untergeordnete Fenster-ID des Fensters. Die ID kann AFX_IDW_PANE_FIRST werden, es sei denn, das Splitterfenster ist in einem anderen Splitterfenster verschachtelt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

A `CSplitterWnd` wird in der `CFrameWnd` Regel in ein übergeordnetes oder [CMDIChildWnd-Objekt](../../mfc/reference/cmdichildwnd-class.md) eingebettet, indem die folgenden Schritte ausgeführt werden:

1. Einbetten `CSplitterWnd` einer Membervariablen in den übergeordneten Frame.

1. Überschreiben Sie die `OnCreateClient` Memberfunktion des übergeordneten Frames.

1. Rufen `CreateStatic` Sie die Memberfunktion innerhalb des überschriebenen [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)auf.

Ein statisches Splitterfenster enthält eine feste Anzahl von Bereichen, oft aus verschiedenen Klassen.

Wenn Sie ein statisches Splitterfenster erstellen, müssen Sie gleichzeitig alle bereiche erstellen. Die [CreateView-Memberfunktion](#createview) wird normalerweise für diesen Zweck verwendet, Aber Sie können auch andere Nicht-View-Klassen erstellen.

Die anfängliche minimale Zeilenhöhe und Spaltenbreite für ein statisches Splitterfenster ist 0. Diese Minimums, die bestimmen, wann ein Bereich zu klein ist, um vollständig angezeigt zu werden, können mit den Memberfunktionen [SetRowInfo](#setrowinfo) und [SetColumnInfo](#setcolumninfo) geändert werden.

Um Bildlaufleisten zu einem statischen Splitterfenster hinzuzufügen, fügen Sie die WS_HSCROLL- und WS_VSCROLL-Formatvorlagen zu *dwStyle*hinzu.

Weitere Informationen zu statischen Splitterfenstern finden Sie unter "Splitter Windows" im `CSplitterWnd` Artikel [Mehrere Dokumenttypen, Ansichten und Frame-Fenster](../../mfc/multiple-document-types-views-and-frame-windows.md), Technische Anmerkung [29](../../mfc/tn029-splitter-windows.md), und in der Klassenübersicht.

## <a name="csplitterwndcreateview"></a><a name="createview"></a>CSplitterWnd::CreateView

Erstellt die Bereiche für ein statisches Splitterfenster.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parameter

*Zeile*<br/>
Gibt die Splitterfensterzeile an, in der die neue Ansicht platziert werden soll.

*col*<br/>
Gibt die Spalte Splitterfenster an, in der die neue Ansicht platziert werden soll.

*pViewClass*<br/>
Gibt die [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) der neuen Ansicht an.

*sizeInit*<br/>
Gibt die Anfangsgröße der neuen Ansicht an.

*pContext*<br/>
Ein Zeiger auf einen Erstellungskontext, der zum Erstellen der Ansicht verwendet wird (in der Regel der *pContext,* der an die überschriebene [CFrameWnd::OnCreateClient-Memberfunktion](../../mfc/reference/cframewnd-class.md#oncreateclient) des übergeordneten Frames übergeben wird, in der das Splitterfenster erstellt wird).

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Alle Bereiche eines statischen Splitterfensters müssen erstellt werden, bevor das Framework den Splitter anzeigt.

Das Framework ruft diese Memberfunktion auch auf, um neue Bereiche zu erstellen, wenn der Benutzer eines dynamischen Splitterfensters einen Bereich, eine Zeile oder eine Spalte aufteilt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd

Rufen Sie `CSplitterWnd` auf, um ein Objekt zu erstellen.

```
CSplitterWnd();
```

### <a name="remarks"></a>Bemerkungen

Erstellen `CSplitterWnd` Sie ein Objekt in zwei Schritten. Rufen Sie zunächst den Konstruktor `CSplitterWnd` auf, der das Objekt erstellt, und rufen Sie dann `CSplitterWnd` die [Memberfunktion Erstellen](#create) auf, die das Splitterfenster erstellt und an das Objekt anfügt.

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterWnd::DeleteColumn

Löscht eine Spalte aus dem Splitterfenster.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parameter

*colDelete*<br/>
Gibt die zu löschende Spalte an.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework aufgerufen, um die Logik des dynamischen Splitterfensters zu implementieren (d. h., wenn das Splitterfenster den Stil SPLS_DYNAMIC_SPLIT hat). Es kann zusammen mit der virtuellen Funktion [CreateView](#createview)angepasst werden, um erweiterte dynamische Splitter zu implementieren.

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterWnd::DeleteRow

Löscht eine Zeile aus dem Splitterfenster.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parameter

*rowDelete*<br/>
Gibt die zu löschende Zeile an.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework aufgerufen, um die Logik des dynamischen Splitterfensters zu implementieren (d. h., wenn das Splitterfenster den Stil SPLS_DYNAMIC_SPLIT hat). Es kann zusammen mit der virtuellen Funktion [CreateView](#createview)angepasst werden, um erweiterte dynamische Splitter zu implementieren.

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterWnd::DeleteView

Löscht eine Ansicht aus dem Splitterfenster.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parameter

*Zeile*<br/>
Gibt die Splitterfensterzeile an, an der die Ansicht gelöscht werden soll.

*col*<br/>
Gibt die Spalte Splitterfenster an, in der die Ansicht gelöscht werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn die aktive Ansicht gelöscht wird, wird die nächste Ansicht aktiv. Die Standardimplementierung geht davon aus, dass die Ansicht automatisch in [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)gelöscht wird.

Diese Memberfunktion wird vom Framework aufgerufen, um die Logik des dynamischen Splitterfensters zu implementieren (d. h., wenn das Splitterfenster den Stil SPLS_DYNAMIC_SPLIT hat). Es kann zusammen mit der virtuellen Funktion [CreateView](#createview)angepasst werden, um erweiterte dynamische Splitter zu implementieren.

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterWnd::DoKeyboardSplit

Führt den Befehl "Tastaturteilung" aus, in der Regel "Window Split".

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist ein Befehl auf hoher Ebene, der `CSplitterWnd` von der [CView-Klasse](../../mfc/reference/cview-class.md) verwendet wird, um an die Implementierung zu delegieren.

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterWnd::DoScroll

Führt ein synchronisiertes Scrollen von geteilten Fenstern durch.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parameter

*pViewVon*<br/>
Ein Zeiger auf die Ansicht, aus der die Bildlaufnachricht stammt.

*nScrollCode*<br/>
Ein Bildlaufleistencode, der die Bildlaufanforderung des Benutzers angibt. Dieser Parameter besteht aus zwei Teilen: einem Byte niedriger Ordnung, das den horizontal auftretenden Scrolltyp bestimmt, und einem Byte hoher Ordnung, das den vertikal enkrechten Bildlauftyp bestimmt:

- SB_BOTTOM Scrolls nach unten.

- SB_LINEDOWN Scrollt eine Zeile nach unten.

- SB_LINEUP Scrollt eine Reihe nach oben.

- SB_PAGEDOWN Scrollt eine Seite nach unten.

- SB_PAGEUP Scrollt eine Seite nach oben.

- SB_TOP Scrolls nach oben.

*bDoScroll*<br/>
Bestimmt, ob die angegebene Bildlaufaktion erfolgt. Wenn *bDoScroll* TRUE ist (d. h., wenn ein untergeordnetes Fenster vorhanden ist und die geteilten Fenster einen Bildlaufbereich haben), kann die angegebene Bildlaufaktion stattfinden. Wenn *bDoScroll* FALSE ist (d. h., wenn kein untergeordnetes Fenster vorhanden ist oder die geteilten Ansichten keinen Bildlaufbereich haben), wird kein Bildlauf ausgeführt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn ein synchronisierter Bildlauf auftritt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework aufgerufen, um ein synchronisiertes Scrollen von geteilten Fenstern durchzuführen, wenn die Ansicht eine Bildlaufmeldung empfängt. Überschreiben, um eine Aktion des Benutzers zu verlangen, bevor ein synchronisiertes Scrollen zulässig ist.

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterWnd::DoScrollBy

Scrollen Sie geteilte Fenster um eine bestimmte Anzahl von Pixeln.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parameter

*pViewVon*<br/>
Ein Zeiger auf die Ansicht, aus der die Bildlaufnachricht stammt.

*sizeScroll*<br/>
Anzahl der Pixel, die horizontal und vertikal gescrollt werden sollen.

*bDoScroll*<br/>
Bestimmt, ob die angegebene Bildlaufaktion erfolgt. Wenn *bDoScroll* TRUE ist (d. h., wenn ein untergeordnetes Fenster vorhanden ist und die geteilten Fenster einen Bildlaufbereich haben), kann die angegebene Bildlaufaktion stattfinden. Wenn *bDoScroll* FALSE ist (d. h., wenn kein untergeordnetes Fenster vorhanden ist oder die geteilten Ansichten keinen Bildlaufbereich haben), wird kein Bildlauf ausgeführt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn ein synchronisierter Bildlauf auftritt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework als Reaktion auf eine Bildlaufnachricht aufgerufen, um ein synchronisiertes Scrollen der geteilten Fenster nach dem Betrag in Pixel durchzuführen, der durch *sizeScroll*angegeben wird. Positive Werte zeigen an, nach unten und rechts zu scrollen; negative Werte zeigen an, dass der Bildlauf nach oben und nach links führt.

Überschreiben, um eine Aktion des Benutzers zu verlangen, bevor ein Bildlauf zugelassen wird.

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterWnd::GetActivePane

Bestimmt den aktiven Bereich aus dem Fokus oder der aktiven Ansicht im Rahmen.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parameter

*pRow*<br/>
Ein Zeiger auf eine **Int,** um die Zeilennummer des aktiven Bereichs abzurufen.

*pCol*<br/>
Ein Zeiger auf eine **int,** um die Spaltennummer des aktiven Bereichs abzurufen.

### <a name="return-value"></a>Rückgabewert

Zeiger auf den aktiven Bereich. NULL, wenn kein aktiver Bereich vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework aufgerufen, um den aktiven Bereich in einem Splitterfenster zu bestimmen. Überschreiben, um eine Aktion durch den Benutzer zu verlangen, bevor der aktive Bereich abgreift.

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterWnd::GetColumnCount

Gibt die aktuelle Bereichsspaltenanzahl zurück.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die aktuelle Anzahl der Spalten im Splitter zurück. Bei einem statischen Splitter ist dies auch die maximale Anzahl von Spalten.

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterWnd::GetColumnInfo

Gibt Informationen für die angegebene Spalte zurück.

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parameter

*col*<br/>
Gibt eine Spalte an.

*cxCur*<br/>
Ein Verweis auf eine **int,** die auf die aktuelle Breite der Spalte festgelegt werden soll.

*cxMin*<br/>
Ein Verweis auf eine **int,** die auf die aktuelle Mindestbreite der Spalte festgelegt werden soll.

## <a name="csplitterwndgetpane"></a><a name="getpane"></a>CSplitterWnd::GetPane

Gibt den Bereich an der angegebenen Zeile und Spalte zurück.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parameter

*Zeile*<br/>
Gibt eine Zeile an.

*col*<br/>
Gibt eine Spalte an.

### <a name="return-value"></a>Rückgabewert

Gibt den Bereich an der angegebenen Zeile und Spalte zurück. Der zurückgegebene Bereich ist in der Regel eine [cView-abgeleitete](../../mfc/reference/cview-class.md)Klasse.

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterWnd::GetRowCount

Gibt die aktuelle Bereichszeilenanzahl zurück.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die aktuelle Anzahl der Zeilen im Splitterfenster zurück. Bei einem statischen Splitterfenster ist dies auch die maximale Anzahl von Zeilen.

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterWnd::GetRowInfo

Gibt Informationen für die angegebene Zeile zurück.

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parameter

*Zeile*<br/>
Gibt eine Zeile an.

*cyCur*<br/>
Verweis auf **int,** die auf die aktuelle Höhe der Zeile in Pixel eingestellt werden soll.

*cyMin*<br/>
Verweis auf **int,** die auf die aktuelle Mindesthöhe der Zeile in Pixel festgelegt werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um Informationen über die angegebene Zeile abzurufen. Der *parameter cyCur* wird mit der aktuellen Höhe der angegebenen Zeile gefüllt, und *cyMin* wird mit der Minimalhöhe der Zeile gefüllt.

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle

Gibt den freigegebenen Bildlaufleistenstil für das Splitterfenster zurück.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Eines oder mehrere der folgenden Windows-Stilflags, falls erfolgreich:

- WS_HSCROLL Wenn der Splitter derzeit freigegebene horizontale Bildlaufleisten verwaltet.

- WS_VSCROLL Wenn der Splitter derzeit freigegebene vertikale Bildlaufleisten verwaltet.

Bei Null verwaltet das Splitterfenster derzeit keine freigegebenen Bildlaufleisten.

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol

Ruft die untergeordnete Fenster-ID für den Bereich an der angegebenen Zeile und Spalte ab.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parameter

*Zeile*<br/>
Gibt die Splitterfensterzeile an.

*col*<br/>
Gibt die Spalte Splitterfenster an.

### <a name="return-value"></a>Rückgabewert

Die untergeordnete Fenster-ID für den Bereich.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird zum Erstellen von Nichtansichten als Bereiche verwendet und kann aufgerufen werden, bevor der Bereich vorhanden ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a>CSplitterWnd::IsChildPane

Bestimmt, ob *pWnd* derzeit ein untergeordneter Bereich dieses Splitterfensters ist.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf ein zu testendes [CWnd-Objekt.](../../mfc/reference/cwnd-class.md)

*pRow*<br/>
Ein Zeiger auf eine **Zeile,** in der die Zeilennummer gespeichert werden soll.

*pCol*<br/>
Ein Zeiger auf eine **Int,** in der eine Spaltennummer gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn der Wert ungleich Null ist, ist *pWnd* derzeit ein untergeordneter Bereich dieses Splitterfensters, und *pRow* und *pCol* werden mit der Position des Bereichs im Splitterfenster ausgefüllt. Wenn *pWnd* kein untergeordneter Bereich dieses Splitterfensters ist, wird 0 zurückgegeben.

### <a name="remarks"></a>Bemerkungen

In Visual C++-Versionen vor 6.0 wurde diese Funktion als

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Diese Version ist jetzt veraltet und sollte nicht verwendet werden.

## <a name="csplitterwndistracking"></a><a name="istracking"></a>CSplitterWnd::IsTracking

Rufen Sie diese Memberfunktion auf, um zu ermitteln, ob die Splitterleiste im Fenster gerade verschoben wird.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn ein Splittervorgang ausgeführt wird; andernfalls 0.

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter

Rendert ein Bild eines geteilten Fensters.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger auf den Gerätekontext, in dem gezeichnet werden soll. Wenn *pDC* NULL ist, wird [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) vom Framework aufgerufen, und es wird kein geteiltes Fenster gezeichnet.

*nType*<br/>
Ein Wert `enum ESplitType`der , der einer der folgenden werte:

- `splitBox`Das Splitter-Drag-Feld.

- `splitBar`Die Leiste, die zwischen den beiden geteilten Fenstern angezeigt wird.

- `splitIntersection`Der Schnittpunkt der geteilten Fenster. Dieses Element wird nicht aufgerufen, wenn es unter Windows 95/98 ausgeführt wird.

- `splitBorder`Die geteilten Fensterränder.

*Rect*<br/>
Ein Verweis auf ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das die Größe und Form der geteilten Fenster angibt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework aufgerufen, um die genauen Eigenschaften eines Splitterfensters zu zeichnen und anzugeben. Override `OnDrawSplitter` für die erweiterte Anpassung der Bilddaten für die verschiedenen grafischen Komponenten eines Splitterfensters. Die Standardbilddaten ähneln dem Splitter in Microsoft Works für Windows oder Microsoft Windows 95/98, da die Schnittpunkte der Splitterleisten miteinander vermischt werden.

Weitere Informationen zu dynamischen Splitterfenstern finden Sie unter "Splitter-Fenster" im Artikel [Mehrere Dokumenttypen, Ansichten und Frame-Fenster](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technische Anmerkung 29](../../mfc/tn029-splitter-windows.md)und die `CSplitterWnd` Klassenübersicht.

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker

Rendert das Bild eines geteilten Fensters so, dass es die gleiche Größe und Form wie das Rahmenfenster hat.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Verweis auf `CRect` ein Objekt, das das Nachverfolgungsrechteck angibt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework beim Größenänderungselement von Splittern aufgerufen. Überschreiben `OnInvertTracker` für die erweiterte Anpassung der Bilddaten des Splitterfensters. Die Standardbilddaten ähneln dem Splitter in Microsoft Works für Windows oder Microsoft Windows 95/98, da die Schnittpunkte der Splitterleisten miteinander vermischt werden.

Weitere Informationen zu dynamischen Splitterfenstern finden Sie unter "Splitter-Fenster" im Artikel [Mehrere Dokumenttypen, Ansichten und Frame-Fenster](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technische Anmerkung 29](../../mfc/tn029-splitter-windows.md)und die `CSplitterWnd` Klassenübersicht.

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterWnd::RecalcLayout

Rufen Sie den Aufruf auf, das Splitterfenster nach dem Anpassen der Zeilen- oder Spaltengröße erneut anzuzeigen.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um das Splitterfenster korrekt wieder anzuzeigen, nachdem Sie die Zeilen- und Spaltengrößen mit den Elementfunktionen [SetRowInfo](#setrowinfo) und [SetColumnInfo](#setcolumninfo) angepasst haben. Wenn Sie die Zeilen- und Spaltengrößen als Teil des Erstellungsprozesses ändern, bevor das Splitterfenster sichtbar ist, ist es nicht erforderlich, diese Memberfunktion aufzurufen.

Das Framework ruft diese Memberfunktion auf, wenn der Benutzer die Größe des Splitterfensters ändert oder eine Teilung verschiebt.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CSplitterWnd::SetColumnInfo](#setcolumninfo).

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterWnd::SetActivePane

Legt einen Bereich fest, der im Rahmen aktiv ist.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parameter

*Zeile*<br/>
Wenn *pWnd* NULL ist, gibt die Zeile im Bereich an, die aktiv sein wird.

*col*<br/>
Wenn *pWnd* NULL ist, gibt die Spalte im Bereich an, die aktiv sein wird.

*pWnd*<br/>
Ein Zeiger auf ein `CWnd`-Objekt. Wenn NULL, wird der nach *Zeile* und *col* angegebene Bereich aktiv festgelegt. Wenn nicht NULL, gibt den Bereich an, der aktiv festgelegt ist.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework aufgerufen, um einen Bereich als aktiv festzulegen, wenn der Benutzer den Fokus in einen Bereich innerhalb des Rahmenfensters ändert. Sie können `SetActivePane` explizit aufrufen, um den Fokus auf die angegebene Ansicht zu ändern.

Geben Sie den Bereich an, indem Sie entweder Zeile und Spalte **oder** *pWnd*angeben.

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo

Rufen Sie den Aufruf auf, um die angegebenen Spalteninformationen festzulegen.

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parameter

*col*<br/>
Gibt eine Spalte des Splitterfensters an.

*cxIdeal*<br/>
Gibt eine ideale Breite für die Spalte Splitterfenster in Pixel an.

*cxMin*<br/>
Gibt eine Mindestbreite für die Spalte Splitterfenster in Pixel an.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um eine neue Mindestbreite und eine ideale Breite für eine Spalte festzulegen. Der Mindestwert der Spalte bestimmt, wann die Spalte zu klein ist, um vollständig angezeigt zu werden.

Wenn das Framework das Splitterfenster anzeigt, legt es die Bereiche in Spalten und Zeilen entsprechend ihren idealen Abmessungen an, die von der oberen linken bis zur unteren rechten Ecke des Clientbereichs des Splitterfensters arbeiten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterWnd::SetRowInfo

Rufen Sie an, um die angegebenen Zeileninformationen festzulegen.

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parameter

*Zeile*<br/>
Gibt eine Splitterfensterzeile an.

*cyIdeal*<br/>
Gibt eine ideale Höhe für die Splitterfensterzeile in Pixel an.

*cyMin*<br/>
Gibt eine Mindesthöhe für die Splitterfensterzeile in Pixel an.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um eine neue Mindesthöhe und eine ideale Höhe für eine Zeile festzulegen. Der Zeilenmindestwert bestimmt, wann die Zeile zu klein ist, um vollständig angezeigt zu werden.

Wenn das Framework das Splitterfenster anzeigt, legt es die Bereiche in Spalten und Zeilen entsprechend ihren idealen Abmessungen an, die von der oberen linken bis zur unteren rechten Ecke des Clientbereichs des Splitterfensters arbeiten.

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle

Gibt den neuen Bildlaufstil für die gemeinsame Bildlaufleistenunterstützung des Splitterfensters an.

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Der neue Bildlaufstil für die gemeinsame Scrollleistenunterstützung des Splitterfensters, die einer der folgenden Werte sein kann:

- WS_HSCROLL erstellen/zeigen Sie horizontale gemeinsame Bildlaufleisten.

- WS_VSCROLL Erstellen/Anzeigen vertikaler gemeinsamer Bildlaufleisten.

### <a name="remarks"></a>Bemerkungen

Sobald eine Bildlaufleiste erstellt wurde, `SetScrollStyle` wird sie nicht zerstört, auch wenn sie ohne diesen Stil aufgerufen wird; Stattdessen sind diese Bildlaufleisten ausgeblendet. Dadurch können die Bildlaufleisten ihren Status beibehalten, obwohl sie ausgeblendet sind. Nach `SetScrollStyle` dem Aufruf ist es notwendig, [RecalcLayout](#recalclayout) aufzurufen, damit alle Änderungen wirksam werden.

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterWnd::SplitColumn

Gibt an, wo ein Rahmenfenster vertikal geteilt wird.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parameter

*cxBefore*<br/>
Die Position in Pixel, vor der die Teilung erfolgt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird aufgerufen, wenn ein vertikales Splitterfenster erstellt wird. `SplitColumn`gibt den Standardspeicherort an, an dem die Teilung erfolgt.

`SplitColumn`wird vom Framework aufgerufen, um die Logik des dynamischen Splitterfensters zu implementieren (d. h., wenn das Splitterfenster den SPLS_DYNAMIC_SPLIT Stil hat). Es kann zusammen mit der virtuellen Funktion [CreateView](#createview)angepasst werden, um erweiterte dynamische Splitter zu implementieren.

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterWnd::SplitRow

Gibt an, wo ein Rahmenfenster horizontal geteilt wird.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parameter

*cyBefore*<br/>
Die Position in Pixel, vor der die Teilung erfolgt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird aufgerufen, wenn ein horizontales Splitterfenster erstellt wird. `SplitRow`gibt den Standardspeicherort an, an dem die Teilung erfolgt.

`SplitRow`wird vom Framework aufgerufen, um die Logik des dynamischen Splitterfensters zu implementieren (d. h., wenn das Splitterfenster den SPLS_DYNAMIC_SPLIT Stil hat). Es kann zusammen mit der virtuellen Funktion [CreateView](#createview)angepasst werden, um erweiterte dynamische Splitter zu implementieren.

## <a name="csplitterwndondraw"></a><a name="ondraw"></a>CSplitterWnd::OnDraw

Wird vom Framework aufgerufen, um das Splitterfenster zu zeichnen.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger zu einem Gerätekontext.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)
