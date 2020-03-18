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
ms.openlocfilehash: 065735c13a3e763208142eb6bc989d3a496221f0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426798"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd-Klasse

Stellt die Funktionalität eines unterteilten Fensters bereit. Dabei handelt es sich um ein Fenster, das mehrere Bereiche enthält.

## <a name="syntax"></a>Syntax

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CSplitterWnd:: CSplitterWnd](#csplitterwnd)|Ruft auf, um ein `CSplitterWnd` Objekt zu erstellen.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CSplitterWnd:: activatenext](#activatenext)|Führt den nächsten Bereich oder den vorherigen Bereich-Befehl aus.|
|[CSplitterWnd:: canactivatenext](#canactivatenext)|Prüft, ob der nächste Bereich oder der vorherige Bereich-Befehl derzeit möglich ist.|
|[CSplitterWnd:: Create](#create)|Rufen Sie auf, um ein dynamisches Splitter Fenster zu erstellen und an das `CSplitterWnd` Objekt anzufügen.|
|[CSplitterWnd:: kreatescrollbarctrl](#createscrollbarctrl)|Erstellt ein frei gegebenes ScrollBar-Steuerelement.|
|[CSplitterWnd:: foratestatic](#createstatic)|Rufen Sie auf, um ein statisches Splitter Fenster zu erstellen und an das `CSplitterWnd` Objekt anzufügen.|
|[CSplitterWnd:: ansichtsansicht](#createview)|Rufen Sie auf, um einen Bereich in einem Splitter Fenster zu erstellen.|
|[CSplitterWnd::D eletecolumn](#deletecolumn)|Löscht eine Spalte aus dem Splitter Fenster.|
|[CSplitterWnd::D eleterow](#deleterow)|Löscht eine Zeile aus dem Splitter Fenster.|
|[CSplitterWnd::D eleteview](#deleteview)|Löscht eine Ansicht aus dem Splitter Fenster.|
|[CSplitterWnd::D okeyboardsplit](#dokeyboardsplit)|Führt den Befehl für die Tastatur Teilung aus, normalerweise "Fenster Aufteilung".|
|[CSplitterWnd::D oscroll.](#doscroll)|Führt den synchronisierten Bildlauf von geteilten Fenstern aus.|
|[CSplitterWnd::D oscrollby](#doscrollby)|Führt einen Bildlauf mit einer angegebenen Anzahl von Pixeln durch.|
|[CSplitterWnd:: getactivepane](#getactivepane)|Bestimmt den aktiven Bereich aus dem Fokus oder der aktiven Ansicht im Frame.|
|[CSplitterWnd:: GetColumnCount](#getcolumncount)|Gibt die Spalten Anzahl des aktuellen Bereichs zurück.|
|[CSplitterWnd:: GetColumnInfo](#getcolumninfo)|Gibt Informationen über die angegebene Spalte zurück.|
|[CSplitterWnd:: GetPane](#getpane)|Gibt den Bereich in der angegebenen Zeile und Spalte zurück.|
|[CSplitterWnd:: GetRowCount](#getrowcount)|Gibt die Zeilen Anzahl des aktuellen Bereichs zurück.|
|[CSplitterWnd:: getrowinfo](#getrowinfo)|Gibt Informationen über die angegebene Zeile zurück.|
|[CSplitterWnd:: getscrollstyle](#getscrollstyle)|Gibt den freigegebenen scrollbarstil zurück.|
|[CSplitterWnd:: idfromrowcol](#idfromrowcol)|Gibt die untergeordnete Fenster-ID des Bereichs an der angegebenen Zeile und Spalte zurück.|
|[CSplitterWnd:: ischildpane](#ischildpane)|Ruft auf, um zu bestimmen, ob das Fenster derzeit ein untergeordneter Bereich dieses Splitter Fensters ist.|
|[CSplitterWnd:: istracking](#istracking)|Bestimmt, ob die Splitter Leiste gerade verschoben wird.|
|[CSplitterWnd:: Neuberechnung](#recalclayout)|Aufrufen, um das Splitter Fenster erneut anzuzeigen, nachdem die Zeilen-oder Spaltengröße angepasst wurde.|
|[CSplitterWnd:: abtativepane](#setactivepane)|Legt einen Bereich fest, der der aktive im Frame ist.|
|[CSplitterWnd:: setcolumninfo](#setcolumninfo)|Ruft auf, um die angegebenen Spalten Informationen festzulegen.|
|[CSplitterWnd:: "abtrowinfo"](#setrowinfo)|Ruft auf, um die angegebenen Zeilen Informationen festzulegen.|
|[CSplitterWnd:: setscrollstyle](#setscrollstyle)|Gibt den neuen Schiebe leisten Stil für die freigegebene Scrollleisten-Unterstützung des Splitter Fensters an.|
|[CSplitterWnd:: SplitColumn](#splitcolumn)|Gibt an, wo ein Rahmen Fenster vertikal aufgeteilt wird.|
|[CSplitterWnd:: splitrow](#splitrow)|Gibt an, wo ein Rahmen Fenster horizontal aufgeteilt wird.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CSplitterWnd:: OnDraw](#ondraw)|Wird von Framework aufgerufen, um das Splitter Fenster zu zeichnen.|
|[CSplitterWnd:: ondrawsplitter](#ondrawsplitter)|Rendert ein Bild eines geteilten Fensters.|
|[CSplitterWnd:: oninverttracker](#oninverttracker)|Rendert das Bild eines geteilten Fensters in dieselbe Größe und Form wie das Rahmen Fenster.|

## <a name="remarks"></a>Hinweise

Ein Bereich ist in der Regel ein anwendungsspezifisches Objekt, das von [CView](../../mfc/reference/cview-class.md)abgeleitet ist. es kann jedoch ein beliebiges [CWnd](../../mfc/reference/cwnd-class.md) -Objekt mit der entsprechenden untergeordneten Fenster-ID sein.

Ein `CSplitterWnd`-Objekt ist in der Regel in ein übergeordnetes [CFrameWnd](../../mfc/reference/cframewnd-class.md) -oder [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) -Objekt eingebettet. Erstellen Sie mithilfe der folgenden Schritte ein `CSplitterWnd`-Objekt:

1. Bettet eine `CSplitterWnd` Member-Variable in den übergeordneten Frame ein.

2. Überschreiben Sie die Member-Funktion von [CFrameWnd:: onkreateclient](../../mfc/reference/cframewnd-class.md#oncreateclient) für den übergeordneten Frame.

3. Rufen Sie innerhalb des überschriebenen `OnCreateClient`die [Create](#create) - [oder die](#createstatic) -Member-Funktion von "`CSplitterWnd`" auf.

Rufen Sie die `Create` Member-Funktion auf, um ein dynamisches Splitter Fenster zu erstellen. Ein dynamisches Splitter Fenster wird in der Regel verwendet, um eine Reihe einzelner Bereiche oder Ansichten desselben Dokuments zu erstellen und durch einen Bildlauf durchführen. Das Framework erstellt automatisch einen Ausgangsbereich für den Splitter. Das Framework erstellt, ändert seine Größe und gibt zusätzliche Bereiche frei, während der Benutzer die Steuerelemente des Splitter Fensters betreibt.

Wenn Sie `Create`aufzurufen, geben Sie eine minimale Zeilenhöhe und Spaltenbreite an, die bestimmen, wann die Bereiche zu klein sind, um vollständig angezeigt zu werden. Nachdem Sie `Create`aufgerufen haben, können Sie diese Mindestgebühren anpassen, indem Sie die Member-Funktionen [setcolumninfo](#setcolumninfo) und [setrowinfo](#setrowinfo) aufrufen.

Verwenden Sie außerdem die Funktionen `SetColumnInfo` und `SetRowInfo` Member, um eine "ideale" Breite für eine Spalte und eine "ideale" Höhe für eine Zeile festzulegen. Wenn das Framework ein Splitter Fenster anzeigt, wird zuerst der übergeordnete Frame und dann das Splitter Fenster angezeigt. Das Framework gibt dann die Bereiche in Spalten und Zeilen entsprechend Ihren idealen Dimensionen aus, die von oben links nach unten rechts im Client Bereich des Splitter Fensters funktionieren.

Alle Bereiche in einem dynamischen Splitter Fenster müssen von derselben Klasse sein. Vertraute Anwendungen, die dynamische Splitter Fenster unterstützen, sind Microsoft Word und Microsoft Excel.

Verwenden Sie die `CreateStatic` Member-Funktion, um ein statisches Splitter Fenster zu erstellen. Der Benutzer kann nur die Größe der Bereiche in einem statischen Splitter Fenster ändern, nicht deren Anzahl oder Reihenfolge.

Beim Erstellen des statischen Splitters müssen Sie insbesondere alle Bereiche der statischen Splitter erstellen. Stellen Sie sicher, dass Sie alle Bereiche erstellen, bevor die `OnCreateClient` Member-Funktion des übergeordneten Frames zurückgibt, oder das Fenster wird vom Framework nicht ordnungsgemäß angezeigt.

Die `CreateStatic` Member-Funktion initialisiert automatisch einen statischen Splitter mit einer minimalen Zeilenhöhe und Spaltenbreite von 0. Nachdem Sie `Create`aufgerufen haben, passen Sie diese Mindestgebühren an, indem Sie die Member-Funktionen [setcolumninfo](#setcolumninfo) und [setrowinfo](#setrowinfo) aufrufen. Verwenden Sie außerdem `SetColumnInfo` und `SetRowInfo`, nachdem Sie `CreateStatic` aufgerufen haben, um die gewünschten idealen Bereichs Dimensionen anzugeben.

Die einzelnen Bereiche eines statischen Splitters gehören häufig zu unterschiedlichen Klassen. Beispiele für statische Splitter Fenster finden Sie im Grafik-Editor und im Windows-Datei-Manager.

Ein Splitter Fenster unterstützt besondere Schiebe leisten (abgesehen von den Bild Lauf leisten, die Bereiche enthalten können). Diese Bild Lauf leisten sind untergeordnete Elemente des `CSplitterWnd` Objekts und werden für die Bereiche freigegeben.

Sie erstellen diese speziellen Schiebe leisten, wenn Sie das Splitter Fenster erstellen. Beispielsweise wird eine `CSplitterWnd`, die über eine Zeile, zwei Spalten und den WS_VSCROLL Stil verfügt, eine vertikale Schiebe Leiste anzeigen, die von den beiden Bereichen gemeinsam genutzt wird. Wenn der Benutzer die Bild Lauf Leiste verschiebt, werden WM_VSCROLL Meldungen an beide Bereiche gesendet. Wenn die Bereiche die Bild Lauf leisten Position festlegen, wird die freigegebene Scrollleiste festgelegt.

Weitere Informationen zu Splitter Fenstern finden Sie in der [technischen Notiz 29](../../mfc/tn029-splitter-windows.md).

Weitere Informationen zum Erstellen dynamischer Splitter Fenster finden Sie unter:

- MFC-Beispiel [Scribble](../../overview/visual-cpp-samples.md)

- MFC-Beispiel- [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Voraussetzungen

**Header:** Afxext. h

##  <a name="activatenext"></a>CSplitterWnd:: activatenext

Wird von Framework aufgerufen, um den nächsten Bereich oder den vorherigen Bereich-Befehl auszuführen.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parameter

*bprev*<br/>
Gibt an, welches Fenster aktiviert werden soll. **True** für Previous; **False** für Next.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion ist ein allgemeiner Befehl, der von der [CView](../../mfc/reference/cview-class.md) -Klasse verwendet wird, um an die `CSplitterWnd`-Implementierung zu delegieren.

##  <a name="canactivatenext"></a>CSplitterWnd:: canactivatenext

Wird von Framework aufgerufen, um zu überprüfen, ob der Befehl Nächster Bereich oder vorheriger Bereich aktuell möglich ist.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parameter

*bprev*<br/>
Gibt an, welches Fenster aktiviert werden soll. **True** für Previous; **False** für Next.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Diese Member-Funktion ist ein allgemeiner Befehl, der von der [CView](../../mfc/reference/cview-class.md) -Klasse verwendet wird, um an die `CSplitterWnd`-Implementierung zu delegieren.

##  <a name="create"></a>CSplitterWnd:: Create

Um ein dynamisches Splitter Fenster zu erstellen, rufen Sie die `Create` Member-Funktion auf.

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

*pparser*<br/>
Das übergeordnete Rahmen Fenster des Splitter Fensters.

*nmaxrows*<br/>
Die maximale Anzahl von Zeilen im Splitter Fenster. Dieser Wert darf nicht größer sein als 2.

*nmaxcols*<br/>
Die maximale Anzahl von Spalten im Splitter Fenster. Dieser Wert darf nicht größer sein als 2.

*sizemin*<br/>
Gibt die Mindestgröße an, mit der ein Bereich angezeigt werden kann.

*pContext*<br/>
Ein Zeiger auf eine [ckreatecontext](../../mfc/reference/ccreatecontext-structure.md) -Struktur. In den meisten Fällen kann dies der *pContext* sein, der an das übergeordnete Rahmen Fenster übergeben wird.

*dwstyle*<br/>
Gibt den Fenster Stil an.

*NID*<br/>
Die ID des untergeordneten Fensters des Fensters. Die ID kann AFX_IDW_PANE_FIRST werden, es sei denn, das Splitter Fenster ist in einem anderen Splitter Fenster geschachtelt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Sie können eine `CSplitterWnd` in ein übergeordnetes [CFrameWnd](../../mfc/reference/cframewnd-class.md) -oder [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) -Objekt einbetten, indem Sie die folgenden Schritte ausführen:

1. Bettet eine `CSplitterWnd` Member-Variable in den übergeordneten Frame ein.

1. Überschreiben Sie die Member-Funktion von [CFrameWnd:: onkreateclient](../../mfc/reference/cframewnd-class.md#oncreateclient) für den übergeordneten Frame.

1. Ruft die `Create` Member-Funktion innerhalb der überschriebenen `OnCreateClient`auf.

Wenn Sie in einem übergeordneten Frame ein Splitter Fenster erstellen, übergeben Sie den *pContext* -Parameter des übergeordneten Frames an das Splitter Fenster. Andernfalls kann dieser Parameter NULL sein.

Die anfängliche minimale Zeilenhöhe und Spaltenbreite eines dynamischen Splitter Fensters werden durch den *sizemin* -Parameter festgelegt. Diese Minimums, die bestimmen, ob ein Bereich zu klein ist, um vollständig dargestellt zu werden, können mit den Member-Funktionen [setrowinfo](#setrowinfo) und [setcolumninfo](#setcolumninfo) geändert werden.

Weitere Informationen zu dynamischen Splitter Fenstern finden Sie unter "Splitter Fenster" im Artikel [mehrere Dokumenttypen, Ansichten und Rahmen Fenster](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technische Notiz 29](../../mfc/tn029-splitter-windows.md)und die Übersicht über die `CSplitterWnd`-Klasse.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>CSplitterWnd:: kreatescrollbarctrl

Wird von Framework aufgerufen, um ein frei gegebenes ScrollBar-Steuerelement zu erstellen.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Gibt den Fenster Stil an.

*NID*<br/>
Die ID des untergeordneten Fensters des Fensters. Die ID kann AFX_IDW_PANE_FIRST werden, es sei denn, das Splitter Fenster ist in einem anderen Splitter Fenster geschachtelt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Überschreiben Sie `CreateScrollBarCtrl`, um zusätzliche Steuerelemente neben einer Schiebe Leiste einzuschließen. Standardmäßig werden normale Steuerelemente der Windows-Scrollleiste erstellt.

##  <a name="createstatic"></a>CSplitterWnd:: foratestatic

Um ein statisches Splitter Fenster zu erstellen, rufen Sie die `CreateStatic` Member-Funktion auf.

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parameter

*pparser*<br/>
Das übergeordnete Rahmen Fenster des Splitter Fensters.

*nRows*<br/>
Die Anzahl von Zeilen. Dieser Wert darf nicht länger als 16 sein.

*ncols*<br/>
Die Anzahl von Spalten. Dieser Wert darf nicht länger als 16 sein.

*dwstyle*<br/>
Gibt den Fenster Stil an.

*NID*<br/>
Die ID des untergeordneten Fensters des Fensters. Die ID kann AFX_IDW_PANE_FIRST werden, es sei denn, das Splitter Fenster ist in einem anderen Splitter Fenster geschachtelt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Eine `CSplitterWnd` wird in der Regel in ein übergeordnetes `CFrameWnd` oder [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) -Objekt eingebettet, indem die folgenden Schritte ausgeführt werden:

1. Bettet eine `CSplitterWnd` Member-Variable in den übergeordneten Frame ein.

1. Überschreiben Sie die `OnCreateClient` Member-Funktion des übergeordneten Frames.

1. Aufrufen der `CreateStatic` Member-Funktion innerhalb des überschriebenen [CFrameWnd:: onkreateclient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Ein statisches Splitter Fenster enthält eine Reihe fester Bereiche, häufig aus unterschiedlichen Klassen.

Wenn Sie ein statisches Splitter Fenster erstellen, müssen Sie gleichzeitig alle Bereiche erstellen. Die Member-Funktion von "Member" wird [in der Regel](#createview) für diesen Zweck verwendet, aber Sie können auch andere nicht-Ansichts Klassen erstellen.

Die anfängliche minimale Zeilenhöhe und Spaltenbreite für ein statisches Splitter Fenster beträgt 0. Diese Minimums, die bestimmen, wann ein Bereich zu klein ist, um vollständig dargestellt zu werden, können mit den Member-Funktionen [setrowinfo](#setrowinfo) und [setcolumninfo](#setcolumninfo) geändert werden.

Um einem statischen Splitter Fenster Bild Lauf leisten hinzuzufügen, fügen Sie " *dwstyle*" die WS_HSCROLL-und WS_VSCROLL Stile hinzu.

Weitere Informationen zu statischen Splitter Fenstern finden Sie unter "Splitter Fenster" im Artikel [mehrere Dokumenttypen, Ansichten und Rahmen Fenster](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technische Notiz 29](../../mfc/tn029-splitter-windows.md)und die Übersicht über die `CSplitterWnd`-Klasse.

##  <a name="createview"></a>CSplitterWnd:: ansichtsansicht

Erstellt die Bereiche für ein statisches Splitter Fenster.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parameter

*row*<br/>
Gibt die Splitter Fenster Zeile an, in der die neue Ansicht platziert werden soll.

*col*<br/>
Gibt die Splitter Fenster Spalte an, in der die neue Ansicht platziert werden soll.

*pviewclass*<br/>
Gibt die [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) der neuen Ansicht an.

*sizeingeit*<br/>
Gibt die Anfangs Größe der neuen Ansicht an.

*pContext*<br/>
Ein Zeiger auf einen Erstellungs Kontext, der zum Erstellen der Sicht verwendet wird (in der Regel der *pContext* , der an die überschriebene [CFrameWnd:: onup](../../mfc/reference/cframewnd-class.md#oncreateclient) -Member-Funktion des übergeordneten Frames übergeben wird, in der das Splitter Fenster erstellt wird).

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Alle Bereiche eines statischen Splitter Fensters müssen erstellt werden, bevor das Framework den Splitter anzeigt.

Das Framework ruft auch diese Member-Funktion auf, um neue Bereiche zu erstellen, wenn der Benutzer eines dynamischen Splitter Fensters einen Bereich, eine Zeile oder eine Spalte teilt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>CSplitterWnd:: CSplitterWnd

Ruft auf, um ein `CSplitterWnd` Objekt zu erstellen.

```
CSplitterWnd();
```

### <a name="remarks"></a>Hinweise

Erstellen Sie ein `CSplitterWnd`-Objekt in zwei Schritten. Rufen Sie zuerst den-Konstruktor auf, der das `CSplitterWnd`-Objekt erstellt, und rufen Sie dann die [Create](#create) Member-Funktion auf, die das Splitter Fenster erstellt und an das `CSplitterWnd`-Objekt anfügt.

##  <a name="deletecolumn"></a>CSplitterWnd::D eletecolumn

Löscht eine Spalte aus dem Splitter Fenster.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parameter

*coldelete*<br/>
Gibt die zu löschende Spalte an.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird vom Framework aufgerufen, um die Logik des dynamischen Splitter Fensters zu implementieren (d. h., wenn das Splitter Fenster den SPLS_DYNAMIC_SPLIT Stil hat). Es kann zusammen mit der virtuellen Funktion " [kreateview](#createview)" angepasst werden, um erweiterte dynamische Splitters zu implementieren.

##  <a name="deleterow"></a>CSplitterWnd::D eleterow

Löscht eine Zeile aus dem Splitter Fenster.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parameter

*RowDelete*<br/>
Gibt die zu löschende Zeile an.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird vom Framework aufgerufen, um die Logik des dynamischen Splitter Fensters zu implementieren (d. h., wenn das Splitter Fenster den SPLS_DYNAMIC_SPLIT Stil hat). Es kann zusammen mit der virtuellen Funktion " [kreateview](#createview)" angepasst werden, um erweiterte dynamische Splitters zu implementieren.

##  <a name="deleteview"></a>CSplitterWnd::D eleteview

Löscht eine Ansicht aus dem Splitter Fenster.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parameter

*row*<br/>
Gibt die Splitter Fenster Zeile an, in der die Ansicht gelöscht werden soll.

*col*<br/>
Gibt die Splitter Fenster Spalte an, in der die Ansicht gelöscht werden soll.

### <a name="remarks"></a>Hinweise

Wenn die aktive Ansicht gelöscht wird, wird die nächste Ansicht aktiviert. Die Standard Implementierung geht davon aus, dass die Sicht in [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)automatisch gelöscht wird.

Diese Member-Funktion wird vom Framework aufgerufen, um die Logik des dynamischen Splitter Fensters zu implementieren (d. h., wenn das Splitter Fenster den SPLS_DYNAMIC_SPLIT Stil hat). Es kann zusammen mit der virtuellen Funktion " [kreateview](#createview)" angepasst werden, um erweiterte dynamische Splitters zu implementieren.

##  <a name="dokeyboardsplit"></a>CSplitterWnd::D okeyboardsplit

Führt den Befehl für die Tastatur Teilung aus, normalerweise "Fenster Aufteilung".

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Diese Member-Funktion ist ein allgemeiner Befehl, der von der [CView](../../mfc/reference/cview-class.md) -Klasse verwendet wird, um an die `CSplitterWnd`-Implementierung zu delegieren.

##  <a name="doscroll"></a>CSplitterWnd::D oscroll.

Führt den synchronisierten Bildlauf von geteilten Fenstern aus.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parameter

*pviewfrom*<br/>
Ein Zeiger auf die Ansicht, von der die scrollnachricht stammt.

*nscrollcode*<br/>
Ein Bild Lauf leisten Code, der die scrollanforderung des Benutzers angibt. Dieser Parameter setzt sich aus zwei Teilen zusammen: einem Byte mit niedriger Reihenfolge, das den Typ des horizontalen Bildlaufs bestimmt, und einem Byte mit hoher Reihenfolge, das den Typ des vertikal auftretenden Bildlaufs bestimmt:

    - SB_BOTTOM einen Bildlauf nach unten durch.

    - SB_LINEDOWN führt einen Bildlauf nach unten durch.

    - SB_LINEUP führt einen Bildlauf nach oben aus.

    - SB_PAGEDOWN führt einen Bildlauf nach unten durch.

    - SB_PAGEUP Scrollt eine Seite nach oben.

    - SB_TOP einen Bildlauf nach oben durch.

*bdoscroll*<br/>
Bestimmt, ob die angegebene scrollaktion auftritt. Wenn *bdoscroll* true ist (d. h., wenn ein untergeordnetes Fenster vorhanden ist, und wenn die geteilten Fenster einen scrollbereich aufweisen), kann die angegebene scrollaktion stattfinden. Wenn *bdoscroll* false ist (d. h., wenn kein untergeordnetes Fenster vorhanden ist oder die geteilten Sichten keinen Bild Laufbereich aufweisen), erfolgt kein Bildlauf.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn synchronisierter Bildlauf auftritt andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird vom Framework aufgerufen, um ein synchronisiertes Scrollen von geteilten Fenstern auszuführen, wenn die Ansicht eine Bild Lauf Nachricht empfängt. Überschreiben Sie, um eine Aktion durch den Benutzer anzufordern, bevor das Synchronisierungs Verhalten zulässig ist.

##  <a name="doscrollby"></a>CSplitterWnd::D oscrollby

Führt einen Bildlauf mit einer angegebenen Anzahl von Pixeln durch.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parameter

*pviewfrom*<br/>
Ein Zeiger auf die Ansicht, von der die scrollnachricht stammt.

*sizescroll*<br/>
Die Anzahl der Pixel, die horizontal und vertikal durch scrollt werden soll.

*bdoscroll*<br/>
Bestimmt, ob die angegebene scrollaktion auftritt. Wenn *bdoscroll* true ist (d. h., wenn ein untergeordnetes Fenster vorhanden ist, und wenn die geteilten Fenster einen scrollbereich aufweisen), kann die angegebene scrollaktion stattfinden. Wenn *bdoscroll* false ist (d. h., wenn kein untergeordnetes Fenster vorhanden ist oder die geteilten Sichten keinen Bild Laufbereich aufweisen), erfolgt kein Bildlauf.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn synchronisierter Bildlauf auftritt andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird vom Framework als Reaktion auf eine Bild Lauf Nachricht aufgerufen, um das synchronisierte Scrollen der geteilten Fenster um den von *sizescroll*gekennzeichneten Wert in Pixel auszuführen. Positive Werte geben den Bildlauf nach unten und nach rechts an. negative Werte geben den Bildlauf nach oben und nach links an.

Überschreiben Sie, um eine Aktion durch den Benutzer anzufordern, bevor Sie scrollvorgang zulassen.

##  <a name="getactivepane"></a>CSplitterWnd:: getactivepane

Bestimmt den aktiven Bereich aus dem Fokus oder der aktiven Ansicht im Frame.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parameter

*Prow*<br/>
Ein Zeiger auf einen **int** -Wert, mit dem die Zeilennummer des aktiven Bereichs abgerufen wird.

*PCOL*<br/>
Ein Zeiger auf einen **int** -Wert zum Abrufen der Spaltennummer des aktiven Bereichs.

### <a name="return-value"></a>Rückgabewert

Zeiger auf den aktiven Bereich. NULL, wenn kein aktiver Bereich vorhanden ist.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird vom Framework aufgerufen, um den aktiven Bereich in einem Splitter Fenster zu bestimmen. Überschreiben Sie, um eine Aktion durch den Benutzer vor dem aktiven Bereich anzufordern.

##  <a name="getcolumncount"></a>CSplitterWnd:: GetColumnCount

Gibt die Spalten Anzahl des aktuellen Bereichs zurück.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die aktuelle Anzahl der Spalten im Splitter zurück. Bei einem statischen Splitter ist dies auch die maximale Anzahl von Spalten.

##  <a name="getcolumninfo"></a>CSplitterWnd:: GetColumnInfo

Gibt Informationen über die angegebene Spalte zurück.

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parameter

*col*<br/>
Gibt eine Spalte an.

*cxcur*<br/>
Ein Verweis auf einen **int** -Wert, der auf die aktuelle Breite der Spalte festgelegt wird.

*cxMin*<br/>
Ein Verweis auf einen **int** -Wert, der auf die aktuelle minimale Breite der Spalte festgelegt wird.

##  <a name="getpane"></a>CSplitterWnd:: GetPane

Gibt den Bereich in der angegebenen Zeile und Spalte zurück.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parameter

*row*<br/>
Gibt eine Zeile an.

*col*<br/>
Gibt eine Spalte an.

### <a name="return-value"></a>Rückgabewert

Gibt den Bereich in der angegebenen Zeile und Spalte zurück. Der zurückgegebene Bereich ist normalerweise eine von [CView](../../mfc/reference/cview-class.md)abgeleitete Klasse.

##  <a name="getrowcount"></a>CSplitterWnd:: GetRowCount

Gibt die Zeilen Anzahl des aktuellen Bereichs zurück.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die aktuelle Anzahl von Zeilen im Splitter Fenster zurück. Bei einem statischen Splitter Fenster ist dies auch die maximale Anzahl von Zeilen.

##  <a name="getrowinfo"></a>CSplitterWnd:: getrowinfo

Gibt Informationen über die angegebene Zeile zurück.

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parameter

*row*<br/>
Gibt eine Zeile an.

*cycur*<br/>
Verweis auf den **int** -Wert, der auf die aktuelle Höhe der Zeile in Pixel festgelegt wird.

*Cymin*<br/>
Verweis auf den **int** -Wert, der auf die aktuelle Mindesthöhe der Zeile in Pixel festgelegt werden soll.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Member-Funktion auf, um Informationen über die angegebene Zeile abzurufen. Der *cycur* -Parameter wird mit der aktuellen Höhe der angegebenen Zeile und *Cymin* mit der Mindesthöhe der Zeile aufgefüllt.

##  <a name="getscrollstyle"></a>CSplitterWnd:: getscrollstyle

Gibt den freigegebenen scrollbarstil für das Splitter Fenster zurück.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Mindestens eines der folgenden Windows-stilflags, wenn erfolgreich:

    - WS_HSCROLL, wenn der Splitter derzeit freigegebene horizontale Schiebe leisten verwaltet.

    - WS_VSCROLL, wenn der Splitter derzeit freigegebene vertikale Scrollleisten verwaltet.

Wenn der Wert 0 (null) ist, verwaltet das Splitter Fenster momentan keine freigegebenen Scrollleisten.

##  <a name="idfromrowcol"></a>CSplitterWnd:: idfromrowcol

Ruft die ID des untergeordneten Fensters für den Bereich in der angegebenen Zeile und Spalte ab.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parameter

*row*<br/>
Gibt die Splitter Fenster Zeile an.

*col*<br/>
Gibt die Splitter Fenster Spalte an.

### <a name="return-value"></a>Rückgabewert

Die ID des untergeordneten Fensters für den Bereich.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird zum Erstellen von nicht Sichten als Bereiche verwendet und kann aufgerufen werden, bevor der Bereich vorhanden ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>CSplitterWnd:: ischildpane

Bestimmt, ob *pwnd* zurzeit ein untergeordneter Bereich dieses Splitter Fensters ist.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Ein Zeiger auf ein zu testende [CWnd](../../mfc/reference/cwnd-class.md) -Objekt.

*Prow*<br/>
Ein Zeiger auf einen **int** -Wert, in dem die Zeilennummer gespeichert werden soll.

*PCOL*<br/>
Ein Zeiger auf einen **int** -Wert, in dem eine Spaltennummer gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn der Wert ungleich 0 (null) ist, ist *pwnd* zurzeit ein untergeordneter Bereich dieses Splitter Fensters, und *Prow* und *pCol* werden mit der Position des Bereichs im Splitter Fenster ausgefüllt. Wenn *pwnd* kein untergeordneter Bereich dieses Splitter Fensters ist, wird 0 zurückgegeben.

### <a name="remarks"></a>Hinweise

In visuellen C++ Versionen vor 6,0 wurde diese Funktion als

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Diese Version ist mittlerweile veraltet und sollte nicht verwendet werden.

##  <a name="istracking"></a>CSplitterWnd:: istracking

Mit dieser Member-Funktion können Sie ermitteln, ob die Splitter Leiste im Fenster gerade verschoben wird.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn ein Splitter Vorgang ausgeführt wird. andernfalls 0.

##  <a name="ondrawsplitter"></a>CSplitterWnd:: ondrawsplitter

Rendert ein Bild eines geteilten Fensters.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger auf den Gerätekontext, in dem gezeichnet werden soll. Wenn *PDC* den Wert NULL hat, wird [CWnd:: redrawwindow](../../mfc/reference/cwnd-class.md#redrawwindow) vom Framework aufgerufen, und es wird kein geteiltes Fenster gezeichnet.

*nType*<br/>
Ein Wert des `enum ESplitType`, bei dem es sich um einen der folgenden Werte handeln kann:

    - `splitBox` das Zieh Feld Splitter.

    - `splitBar` die Leiste, die zwischen den beiden geteilten Fenstern angezeigt wird.

    - `splitIntersection` die Schnittmenge der geteilten Fenster an. Dieses Element wird nicht aufgerufen, wenn es unter Windows 95/98 ausgeführt wird.

    - `splitBorder` den Rahmen des geteilten Fensters.

*Rect*<br/>
Ein Verweis auf ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt, das die Größe und Form der geteilten Fenster angibt.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird vom Framework aufgerufen, um Sie zu zeichnen und die exakten Merkmale eines Splitter Fensters anzugeben. Überschreiben Sie `OnDrawSplitter` für die erweiterte Anpassung der Bilder für die verschiedenen grafischen Komponenten eines Splitter Fensters. Die Standardbilder ähneln dem Splitter in Microsoft Works für Windows oder Microsoft Windows 95/98, da die Schnittpunkte der Splitter leisten zusammengemischt werden.

Weitere Informationen zu dynamischen Splitter Fenstern finden Sie unter "Splitter Fenster" im Artikel [mehrere Dokumenttypen, Ansichten und Rahmen Fenster](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technische Notiz 29](../../mfc/tn029-splitter-windows.md)und die Übersicht über die `CSplitterWnd`-Klasse.

##  <a name="oninverttracker"></a>CSplitterWnd:: oninverttracker

Rendert das Bild eines geteilten Fensters in dieselbe Größe und Form wie das Rahmen Fenster.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Verweis auf ein `CRect` Objekt, das das nach Verfolgungs Rechteck angibt.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird von Framework aufgerufen, während die Größe der Splitters geändert wird. Überschreiben Sie `OnInvertTracker` für die erweiterte Anpassung der Bilder des Splitter Fensters. Die Standardbilder ähneln dem Splitter in Microsoft Works für Windows oder Microsoft Windows 95/98, da die Schnittpunkte der Splitter leisten zusammengemischt werden.

Weitere Informationen zu dynamischen Splitter Fenstern finden Sie unter "Splitter Fenster" im Artikel [mehrere Dokumenttypen, Ansichten und Rahmen Fenster](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technische Notiz 29](../../mfc/tn029-splitter-windows.md)und die Übersicht über die `CSplitterWnd`-Klasse.

##  <a name="recalclayout"></a>CSplitterWnd:: Neuberechnung

Aufrufen, um das Splitter Fenster erneut anzuzeigen, nachdem die Zeilen-oder Spaltengröße angepasst wurde.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Hinweise

Mit dieser Member-Funktion können Sie das Splitter Fenster ordnungsgemäß erneut anzeigen, nachdem Sie die Zeilen-und Spaltengrößen mit den Member-Funktionen [setrowinfo](#setrowinfo) und [setcolumninfo](#setcolumninfo) angepasst haben. Wenn Sie die Zeilen-und Spaltengrößen im Rahmen des Erstellungs Prozesses ändern, bevor das Splitter Fenster sichtbar ist, ist es nicht erforderlich, diese Member-Funktion aufzurufen.

Das Framework ruft diese Member-Funktion immer dann auf, wenn der Benutzer die Größe des Splitter Fensters ändert oder eine Teilung verschiebt.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CSplitterWnd:: setcolumninfo](#setcolumninfo).

##  <a name="setactivepane"></a>CSplitterWnd:: abtativepane

Legt einen Bereich fest, der der aktive im Frame ist.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parameter

*row*<br/>
Wenn *pwnd* NULL ist, gibt die Zeile im Bereich an, die aktiv sein wird.

*col*<br/>
Wenn *pwnd* NULL ist, gibt die Spalte im Bereich an, die aktiv sein wird.

*folgenden*<br/>
Ein Zeiger auf ein `CWnd` -Objekt. Wenn der Wert NULL ist, wird der durch *Row* und *Col* angegebene Bereich als aktiv festgelegt. Wenn nicht NULL, wird der Bereich angegeben, der als aktiv festgelegt ist.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird vom Framework aufgerufen, um einen Bereich als aktiv festzulegen, wenn der Benutzer den Fokus auf einen Bereich im Rahmen Fenster ändert. Sie können `SetActivePane` explizit aufzurufen, um den Fokus auf die angegebene Ansicht zu ändern.

Geben Sie den Bereich an, indem Sie entweder Zeile und Spalte **oder** *pwnd*bereitstellen.

##  <a name="setcolumninfo"></a>CSplitterWnd:: setcolumninfo

Ruft auf, um die angegebenen Spalten Informationen festzulegen.

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parameter

*col*<br/>
Gibt eine Splitter Fenster Spalte an.

*cxideal*<br/>
Gibt eine ideale Breite für die Splitter Fenster Spalte in Pixel an.

*cxMin*<br/>
Gibt eine minimale Breite für die Splitter Fenster Spalte in Pixel an.

### <a name="remarks"></a>Hinweise

Mit dieser Member-Funktion können Sie eine neue minimale Breite und ideale Breite für eine Spalte festlegen. Der minimale Spaltenwert bestimmt, wann die Spalte zu klein ist, damit Sie vollständig angezeigt wird.

Wenn das-Framework das Splitter Fenster anzeigt, werden die Bereiche in den Spalten und Zeilen entsprechend Ihren idealen Dimensionen angeordnet, wobei von links oben nach unten in der unteren rechten Ecke des Client Bereichs des Splitter Fensters gearbeitet wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>CSplitterWnd:: "abtrowinfo"

Ruft auf, um die angegebenen Zeilen Informationen festzulegen.

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parameter

*row*<br/>
Gibt eine Splitter Fenster Zeile an.

*cyideal*<br/>
Gibt eine ideale Höhe für die Splitter Fenster Zeile in Pixel an.

*Cymin*<br/>
Gibt die minimale Höhe der Splitter Fenster Zeile in Pixel an.

### <a name="remarks"></a>Hinweise

Mit dieser Member-Funktion können Sie eine neue Mindesthöhe und eine optimale Höhe für eine Zeile festlegen. Der minimale Zeilen Wert bestimmt, wann die Zeile zu klein ist, damit Sie vollständig angezeigt wird.

Wenn das-Framework das Splitter Fenster anzeigt, werden die Bereiche in den Spalten und Zeilen entsprechend Ihren idealen Dimensionen angeordnet, wobei von links oben nach unten in der unteren rechten Ecke des Client Bereichs des Splitter Fensters gearbeitet wird.

##  <a name="setscrollstyle"></a>CSplitterWnd:: setscrollstyle

Gibt den neuen scrollstil für die freigegebene Schiebe leisten Unterstützung des Splitter Fensters an.

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Der neue scrollstil für die freigegebene Scrollleisten-Unterstützung des Splitter Fensters, bei dem es sich um einen der folgenden Werte handeln kann:

- WS_HSCROLL horizontale, freigegebene Schiebe leisten erstellen/anzeigen.

- WS_VSCROLL vertikale, freigegebene Schiebe leisten erstellen/anzeigen.

### <a name="remarks"></a>Hinweise

Nachdem eine Schiebe Leiste erstellt wurde, wird Sie nicht zerstört, auch wenn `SetScrollStyle` ohne diesen Stil aufgerufen wird. Stattdessen werden diese Scrollleisten ausgeblendet. Dies ermöglicht es den Bild Lauf leisten, ihren Zustand beizubehalten, auch wenn Sie ausgeblendet sind. Nach dem Aufrufen von `SetScrollStyle` muss " [Neuberechnen](#recalclayout) " aufgerufen werden, damit alle Änderungen wirksam werden.

##  <a name="splitcolumn"></a>CSplitterWnd:: SplitColumn

Gibt an, wo ein Rahmen Fenster vertikal aufgeteilt wird.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parameter

*cxbefore*<br/>
Die Position in Pixel, vor der die Teilung erfolgt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird aufgerufen, wenn ein vertikales Splitter Fenster erstellt wird. `SplitColumn` gibt den Standard Speicherort an, an dem die Teilung erfolgt.

`SplitColumn` wird vom Framework aufgerufen, um die Logik des dynamischen Splitter Fensters zu implementieren (d. h., wenn das Splitter Fenster den SPLS_DYNAMIC_SPLIT Stil hat). Es kann zusammen mit der virtuellen Funktion " [kreateview](#createview)" angepasst werden, um erweiterte dynamische Splitters zu implementieren.

##  <a name="splitrow"></a>CSplitterWnd:: splitrow

Gibt an, wo ein Rahmen Fenster horizontal aufgeteilt wird.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parameter

*cybefore*<br/>
Die Position in Pixel, vor der die Teilung erfolgt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird aufgerufen, wenn ein horizontales Splitter Fenster erstellt wird. `SplitRow` gibt den Standard Speicherort an, an dem die Teilung erfolgt.

`SplitRow` wird vom Framework aufgerufen, um die Logik des dynamischen Splitter Fensters zu implementieren (d. h., wenn das Splitter Fenster den SPLS_DYNAMIC_SPLIT Stil hat). Es kann zusammen mit der virtuellen Funktion " [kreateview](#createview)" angepasst werden, um erweiterte dynamische Splitters zu implementieren.

##  <a name="ondraw"></a>CSplitterWnd:: OnDraw

Wird von Framework aufgerufen, um das Splitter Fenster zu zeichnen.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger zu einem Gerätekontext.

### <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel-VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)
