---
title: CCtrlView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
ms.openlocfilehash: f77f1c265920bd160da790647ef754c55e6dbda3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369358"
---
# <a name="cctrlview-class"></a>CCtrlView-Klasse

Passt die Dokument-/Ansichtarchitektur den allgemeinen Steuerelemente an, die von Windows 98 und Windows NT-Versionen 3,51 (und höher) unterstützt werden.

## <a name="syntax"></a>Syntax

```
class CCtrlView : public CView
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCtrlView::CCtrlView](#cctrlview)|Erstellt ein `CCtrlView`-Objekt.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCtrlView::OnDraw](#ondraw)|Wird vom Framework aufgerufen, um mit dem angegebenen Gerätekontext zu zeichnen.|
|[CCtrlView::PreCreateWindow](#precreatewindow)|Wird vor der Erstellung des an diesem `CCtrlView`-Objekt angefügten Windows-Fensters aufgerufen.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Enthält den Standardstil für die Ansichtsklasse.|
|[CCtrlView::m_strClass](#m_strclass)|Enthält den Windows-Klassennamen für die Ansichtsklasse.|

## <a name="remarks"></a>Bemerkungen

Die `CCtrlView` Klasse und ihre Ableitungen, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md)und [CRichEditView](../../mfc/reference/cricheditview-class.md), passen die Dokumentansichtsarchitektur an die neuen allgemeinen Steuerelemente an, die von Windows 95/98 und Windows NT-Versionen 3.51 und höher unterstützt werden. Weitere Informationen zur Dokumentansichtsarchitektur finden Sie unter [Dokument-/Ansichtsarchitektur](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cctrlviewcctrlview"></a><a name="cctrlview"></a>CCtrlView::CCtrlView

Erstellt ein `CCtrlView`-Objekt.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Parameter

*lpszKlasse*<br/>
Windows-Klassenname der Ansichtsklasse.

*dwStyle*<br/>
Stil der Ansichtsklasse.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft den Konstruktor auf, wenn ein neues Rahmenfenster erstellt oder ein Fenster geteilt wird. Überschreiben Sie [CView::OnInitialUpdate,](../../mfc/reference/cview-class.md#oninitialupdate) um die Ansicht zu initialisieren, nachdem das Dokument angefügt wurde. Rufen Sie [CWnd::Create](../../mfc/reference/cwnd-class.md#create) oder [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) auf, um das Windows-Objekt zu erstellen.

## <a name="cctrlviewm_strclass"></a><a name="m_strclass"></a>CCtrlView::m_strClass

Enthält den Windows-Klassennamen für die Ansichtsklasse.

```
CString m_strClass;
```

## <a name="cctrlviewm_dwdefaultstyle"></a><a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle

Enthält den Standardstil für die Ansichtsklasse.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Bemerkungen

Dieser Stil wird angewendet, wenn ein Fenster erstellt wird.

## <a name="cctrlviewondraw"></a><a name="ondraw"></a>CCtrlView::OnDraw

Wird vom Framework aufgerufen, um `CCtrlView` den Inhalt des Objekts mithilfe des angegebenen Gerätekontexts zu zeichnen.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger auf den Gerätekontext, in dem die Zeichnung ausgeführt wird.

### <a name="remarks"></a>Bemerkungen

`OnDraw`wird in der Regel für die Bildschirmanzeige aufgerufen, die einen von *pDC*angegebenen Bildschirmgerätekontext übergibt.

## <a name="cctrlviewprecreatewindow"></a><a name="precreatewindow"></a>CCtrlView::PreCreateWindow

Wird vor der Erstellung des an diesem `CWnd`-Objekt angefügten Windows-Fensters aufgerufen.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parameter

*Cs*<br/>
Eine [CREATESTRUCT-Struktur.](/windows/win32/api/winuser/ns-winuser-createstructw)

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Fenstererstellung fortgesetzt werden soll; 0, um einen Erstellungsfehler anzuzeigen.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion niemals direkt auf.

Die Standardimplementierung dieser Funktion sucht nach einem NULL-Fensterklassennamen und ersetzt einen entsprechenden Standardwert. Überschreiben Sie diese Memberfunktion, um die `CREATESTRUCT` Struktur zu ändern, bevor das Fenster erstellt wird.

Jede Klasse, `CCtrlView` die von der Außerkraftsetzung von `PreCreateWindow`abgeleitet wird, fügt ihre eigene Funktionalität hinzu. Diese Ableitungen von `PreCreateWindow` sind gestalterweise nicht dokumentiert. Um die Stile zu bestimmen, die für jede Klasse geeignet sind, und die Interdependenzen zwischen den Stilen, können Sie den MFC-Quellcode für die Basisklasse Ihrer Anwendung untersuchen. Wenn Sie überschreiben `PreCreateWindow`möchten, können Sie mithilfe der aus dem MFC-Quellcode gesammelten Informationen bestimmen, ob die in der Basisklasse Ihrer Anwendung verwendeten Stile die Erforderliche bieten.

Weitere Informationen zum Ändern von Fensterstilen finden Sie unter [Ändern der Stile eines fensters, das von MFC erstellt wurde.](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Siehe auch

[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CTreeView-Klasse](../../mfc/reference/ctreeview-class.md)<br/>
[CListView-Klasse](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView-Klasse](../../mfc/reference/cricheditview-class.md)
