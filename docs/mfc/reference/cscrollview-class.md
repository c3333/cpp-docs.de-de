---
title: CScrollView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
ms.openlocfilehash: c22f438623ca1d1c9022ea7c3efc50e0826ad302
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318490"
---
# <a name="cscrollview-class"></a>CScrollView-Klasse

Eine [CView](../../mfc/reference/cview-class.md) mit Bildlauffunktionen.

## <a name="syntax"></a>Syntax

```
class CScrollView : public CView
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|Erstellt ein `CScrollView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|Gibt an, ob die Bildlaufansicht über horizontale und vertikale Bildlaufleisten verfügt.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Füllt den Bereich einer Ansicht außerhalb des Bildlaufbereichs.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Ruft die aktuelle Bildlaufposition in Geräteeinheiten ab.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Ruft den aktuellen Zuordnungsmodus, die Gesamtgröße sowie die Linien- und Seitengrößen der scrollbaren Ansicht ab. Größen sind in Geräteeinheiten.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Ruft die aktuelle Bildlaufposition in logischen Einheiten ab.|
|[CScrollView::GetTotalSize](#gettotalsize)|Ruft die Gesamtgröße der Bildlaufansicht in logischen Einheiten ab.|
|[CScrollView::GrößevonParentToFit ändern](#resizeparenttofit)|Bewirkt, dass die Größe der Ansicht die Größe des Rahmens bestimmt.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Scrollt die Ansicht zu einem bestimmten Punkt, der in logischen Einheiten angegeben ist.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Versetzt die Bildlaufansicht in den Maßstabs-anpassungsmodus.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Legt den Zuordnungsmodus der Bildlaufansicht, die Gesamtgröße sowie horizontale und vertikale Bildlaufmengen fest.|

## <a name="remarks"></a>Bemerkungen

Sie können das Standard-Scrolling selbst `CView` in jeder Klasse verarbeiten, die von den Nachrichten zugeordneten [OnHScroll-](../../mfc/reference/cwnd-class.md#onhscroll) und [OnVScroll-Memberfunktionen](../../mfc/reference/cwnd-class.md#onvscroll) abgeleitet wird. Aber `CScrollView` fügt die folgenden `CView` Funktionen zu seinen Funktionen hinzu:

- Es verwaltet Fenster- und Ansichtsfenstergrößen und Zuordnungsmodi.

- Es scrollt automatisch als Antwort auf Scroll-Balken-Nachrichten.

- Es scrollt automatisch als Reaktion auf Nachrichten von der Tastatur, einer nicht scrollenden Maus oder dem IntelliMouse-Rad.

Um automatisch als Reaktion auf Nachrichten von der Tastatur zu scrollen, fügen Sie eine WM_KEYDOWN Nachricht hinzu, und testen Sie VK_DOWN, VK_PREV und rufen [SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos)auf.

Sie können das Scrollen des Mausrads selbst handhaben, indem Sie die Nachrichten-zugeordneten [OnMouseWheel-](../../mfc/reference/cwnd-class.md#onmousewheel) und [OnRegisteredMouseWheel-Memberfunktionen](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) überschreiben. Wie für `CScrollView`unterstützen diese Memberfunktionen das empfohlene Verhalten für [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel), die Raddrehmeldung.

Um die Vorteile des automatischen Scrollens `CScrollView` zu nutzen, leiten Sie ihre Ansichtsklasse von statt von ab. `CView` Wenn Sie die Größe der scrollbaren Ansicht basierend auf der Größe des Dokuments `SetScrollSizes` berechnen möchten, rufen Sie beim ersten Erstellen der Ansicht die Memberfunktion aus der Außerkraftsetzung von [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) oder [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)auf. (Sie müssen ihren eigenen Code schreiben, um die Größe des Dokuments abzufragen. Ein Beispiel finden Sie im [Scribble-Beispiel](../../overview/visual-cpp-samples.md).)

Der Aufruf `SetScrollSizes` der Memberfunktion legt den Zuordnungsmodus der Ansicht, die Gesamtabmessungen der Bildlaufansicht und die Beträge für einen horizontalen und vertikalen Bildlauf fest. Alle Größen sind in logischen Einheiten. Die logische Größe der Ansicht wird in der Regel aus den im Dokument gespeicherten Daten berechnet, in einigen Fällen möchten Sie jedoch möglicherweise eine feste Größe angeben. Beispiele für beide Ansätze finden Sie unter [CScrollView::SetScrollSizes](#setscrollsizes).

Sie geben die Beträge an, die horizontal und vertikal in logischen Einheiten gescrollt werden sollen. Wenn der Benutzer außerhalb des Bildlauffelds auf `CScrollView` eine Bildlaufleistenwelle klickt, scrollt standardmäßig eine "Seite". Wenn der Benutzer an beiden Enden einer Bildlaufleiste auf einen Bildlaufpfeil klickt, `CScrollView` scrollt eine "Linie". Standardmäßig ist eine Seite 1/10 der Gesamtgröße der Ansicht; eine Zeile ist 1/10 der Seitengröße. Überschreiben Sie diese Standardwerte, `SetScrollSizes` indem Sie benutzerdefinierte Größen in der Memberfunktion übergeben. Sie können z. B. die horizontale Größe auf einen Bruchteil der Breite der Gesamtgröße und der vertikalen Größe auf die Höhe einer Linie in der aktuellen Schriftart festlegen.

Anstatt zu scrollen, `CScrollView` kann die Ansicht automatisch auf die aktuelle Fenstergröße skaliert werden. In diesem Modus verfügt die Ansicht über keine Bildlaufleisten, und die logische Ansicht wird gestreckt oder verkleinert, um genau auf den Clientbereich des Fensters zu passen. Um diese Scale-to-Fit-Funktion zu verwenden, rufen Sie [CScrollView::SetScaleToFitSize](#setscaletofitsize)auf. (Rufen `SetScaleToFitSize` Sie `SetScrollSizes`entweder oder an, aber nicht beides.)

Bevor `OnDraw` die Memberfunktion der abgeleiteten `CScrollView` Ansichtsklasse aufgerufen wird, `CPaintDC` passt automatisch der Ansichtsfensterursprung für das Gerätekontextobjekt an, das `OnDraw`an übergibt wird.

Um den Ursprung des Ansichtsfensters `CScrollView` für das Bildlauffenster anzupassen, überschreibt [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Diese Anpassung erfolgt `CPaintDC` automatisch für `CScrollView` den `OnDraw`Gerätekontext, `CScrollView::OnPrepareDC` der an übergeht, aber Sie müssen `CClientDC`sich für alle anderen Gerätekontexte aufrufen, die Sie verwenden, z. B. eine . Sie können `CScrollView::OnPrepareDC` überschreiben, um stiften, die Hintergrundfarbe und andere Zeichnungsattribute festzulegen, rufen jedoch die Basisklasse auf, um die Skalierung zu übernehmen.

Bildlaufleisten können an drei Stellen relativ zu einer Ansicht angezeigt werden, wie in den folgenden Fällen gezeigt:

- Mit den WS_HSCROLL und WS_VSCROLL[Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles)können standardmäßige Bildlaufleisten im Fensterstil für die Ansicht festgelegt werden.

- Scrollleistensteuerelemente können auch dem Frame hinzugefügt werden, der die Ansicht enthält, in diesem Fall leitet das Framework WM_HSCROLL und WM_VSCROLL Nachrichten aus dem Rahmenfenster an die aktuell aktive Ansicht weiter.

- Das Framework leitet auch Bildlaufnachrichten von einem `CSplitterWnd` Splittersteuerelement an den aktuell aktiven Splitterbereich (eine Ansicht) weiter. Wenn ein `CScrollView` Objekt in einem [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) mit freigegebenen Bildlaufleisten platziert wird, verwendet es die freigegebenen, anstatt eigene zu erstellen.

Weitere Informationen zur `CScrollView`Verwendung finden Sie unter [Dokument-/Ansichtsarchitektur](../../mfc/document-view-architecture.md) und [abgeleitete Ansichtsklassen, die in MFC verfügbar sind.](../../mfc/derived-view-classes-available-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a>CScrollView::CheckScrollBars

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob die Bildlaufansicht über horizontale und vertikale Balken verfügt.

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Parameter

*bHasHorzBar*<br/>
Gibt an, dass die Anwendung über eine horizontale Bildlaufleiste verfügt.

*bHasVertBar*<br/>
Gibt an, dass die Anwendung über eine vertikale Bildlaufleiste verfügt.

## <a name="cscrollviewcscrollview"></a><a name="cscrollview"></a>CScrollView::CScrollView

Erstellt ein `CScrollView`-Objekt.

```
CScrollView();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `SetScrollSizes` entweder `SetScaleToFitSize` oder bevor die Bildlaufansicht verwendet werden kann.

## <a name="cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a>CScrollView::FillOutsideRect

Rufen `FillOutsideRect` Sie auf, den Bereich der Ansicht zu füllen, der außerhalb des Bildlaufbereichs angezeigt wird.

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Gerätekontext, in dem die Füllung erfolgen soll.

*pBrush*<br/>
Pinsel, mit dem der Bereich gefüllt werden soll.

### <a name="remarks"></a>Bemerkungen

Verwenden `FillOutsideRect` Sie die `OnEraseBkgnd` Handlerfunktion der Bildlaufansicht, um eine übermäßige Neulackierung des Hintergrunds zu verhindern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

## <a name="cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a>CScrollView::GetDeviceScrollPosition

Rufen `GetDeviceScrollPosition` Sie an, wenn Sie die aktuellen horizontalen und vertikalen Positionen der Bildlauffelder in den Bildlaufleisten benötigen.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Die horizontalen und vertikalen Positionen (in Geräteeinheiten) der Bildlauffelder als `CPoint` Objekt.

### <a name="remarks"></a>Bemerkungen

Dieses Koordinatenpaar entspricht der Position im Dokument, an die die obere linke Ecke der Ansicht gescrollt wurde. Dies ist nützlich, um Die Position des Mausgeräts auf Bildlaufgerätepositionen zu kompensieren.

`GetDeviceScrollPosition`gibt Werte in Geräteeinheiten zurück. Wenn Sie logische Einheiten `GetScrollPosition` wünschen, verwenden Sie stattdessen.

## <a name="cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a>CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes`ruft den aktuellen Zuordnungsmodus, die Gesamtgröße sowie die Linien- und Seitengrößen der scrollbaren Ansicht ab.

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Parameter

*nMapMode*<br/>
Gibt den aktuellen Zuordnungsmodus für diese Ansicht zurück. Eine Liste der möglichen Werte finden Sie unter `SetScrollSizes`.

*GrößeGesamt*<br/>
Gibt die aktuelle Gesamtgröße der Bildlaufansicht in Geräteeinheiten zurück.

*sizePage*<br/>
Gibt die aktuellen horizontalen und vertikalen Beträge zurück, um in jede Richtung als Antwort auf einen Mausklick in einer Scrollbalkenwelle zu scrollen. Das `cx` Element enthält den horizontalen Betrag. Das `cy` Element enthält den vertikalen Betrag.

*sizeLine*<br/>
Gibt die aktuellen horizontalen und vertikalen Beträge zurück, um in jede Richtung als Antwort auf einen Mausklick in einem Bildlaufpfeil zu scrollen. Das `cx` Element enthält den horizontalen Betrag. Das `cy` Element enthält den vertikalen Betrag.

### <a name="remarks"></a>Bemerkungen

Größen sind in Geräteeinheiten. Diese Memberfunktion wird selten aufgerufen.

## <a name="cscrollviewgetscrollposition"></a><a name="getscrollposition"></a>CScrollView::GetScrollPosition

Rufen `GetScrollPosition` Sie an, wenn Sie die aktuellen horizontalen und vertikalen Positionen der Bildlauffelder in den Bildlaufleisten benötigen.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Die horizontalen und vertikalen Positionen (in logischen Einheiten) der Bildlauffelder als `CPoint` Objekt.

### <a name="remarks"></a>Bemerkungen

Dieses Koordinatenpaar entspricht der Position im Dokument, an die die obere linke Ecke der Ansicht gescrollt wurde.

`GetScrollPosition`gibt Werte in logischen Einheiten zurück. Wenn Sie Geräteeinheiten `GetDeviceScrollPosition` wünschen, verwenden Sie stattdessen.

## <a name="cscrollviewgettotalsize"></a><a name="gettotalsize"></a>CScrollView::GetTotalSize

Rufen `GetTotalSize` Sie auf, um die aktuellen horizontalen und vertikalen Größen der Bildlaufansicht abzurufen.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Gesamtgröße der Bildlaufansicht in logischen Einheiten. Die horizontale Größe `cx` befindet `CSize` sich im Element des Rückgabewerts. Die vertikale Größe `cy` befindet sich im Element.

## <a name="cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a>CScrollView::GrößevonParentToFit ändern

Rufen `ResizeParentToFit` Sie auf, um die Größe der Ansicht die Größe des Rahmenfensters bestimmen zu lassen.

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parameter

*bShrinkOnly*<br/>
Die Art der Größenänderung, die ausgeführt werden soll. Der Standardwert TRUE verkleinert das Rahmenfenster bei Bedarf. Bildlaufleisten werden weiterhin für große Ansichten oder kleine Rahmenfenster angezeigt. Der Wert FALSE bewirkt, dass die Ansicht immer die Größe des Rahmenfensters genau zurücklässt. Dies kann etwas gefährlich sein, da das Rahmenfenster zu groß werden könnte, um in das MDI-Rahmenfenster (Multiple Document Interface) oder den Bildschirm zu passen.

### <a name="remarks"></a>Bemerkungen

Dies wird nur für Ansichten in untergeordneten MDI-Rahmenfenstern empfohlen. Wird `ResizeParentToFit` in `OnInitialUpdate` der Handlerfunktion `CScrollView` der abgeleiteten Klasse verwendet. Ein Beispiel für diese Memberfunktion finden Sie unter [CScrollView::SetScrollSizes](#setscrollsizes).

`ResizeParentToFit`geht davon aus, dass die Größe des Ansichtsfensters festgelegt wurde. Wenn die Größe des Ansichtsfensters beim Aufruf nicht festgelegt `ResizeParentToFit` wurde, erhalten Sie eine Assertion. Um sicherzustellen, dass dies nicht geschieht, `ResizeParentToFit`führen Sie vor dem Aufruf den folgenden Aufruf aus:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a>CScrollView::ScrollToPosition

Rufen `ScrollToPosition` Sie einen Bildlauf zu einem bestimmten Punkt in der Ansicht auf.

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Der Punkt, zu dem in logischen Einheiten gescrollt werden soll. Das `x` Element muss ein positiver Wert sein (größer oder gleich 0, bis zur Gesamtgröße der Ansicht). Dasselbe gilt für `y` das Element, wenn der Zuordnungsmodus MM_TEXT ist. Das `y` Element ist in anderen Zuordnungsmodi als MM_TEXT negativ.

### <a name="remarks"></a>Bemerkungen

Die Ansicht wird gescrollt, sodass sich dieser Punkt in der oberen linken Ecke des Fensters befindet. Diese Memberfunktion darf nicht aufgerufen werden, wenn die Ansicht so skaliert wird, dass sie passt.

## <a name="cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a>CScrollView::SetScaleToFitSize

Rufen `SetScaleToFitSize` Sie an, wenn Sie die Größe des Ansichtsfensters automatisch auf die aktuelle Fenstergröße skalieren möchten.

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parameter

*GrößeGesamt*<br/>
Die horizontalen und vertikalen Größen, auf die die Ansicht skaliert werden soll. Die Größe der Bildlaufansicht wird in logischen Einheiten gemessen. Die horizontale Größe `cx` ist im Element enthalten. Die vertikale Größe ist `cy` im Element enthalten. Beide `cx` `cy` und müssen größer oder gleich 0 sein.

### <a name="remarks"></a>Bemerkungen

Bei Bildlaufleisten kann jederzeit nur ein Teil der logischen Ansicht sichtbar sein. Mit der Skalierungsfunktion verfügt die Ansicht jedoch über keine Bildlaufleisten, und die logische Ansicht wird gestreckt oder verkleinert, um genau auf den Clientbereich des Fensters zu passen. Wenn die Größe des Fensters geändert wird, zeichnet die Ansicht ihre Daten in einem neuen Maßstab basierend auf der Größe des Fensters.

In der Regel platzieren `SetScaleToFitSize` Sie den Aufruf in Ihrer `OnInitialUpdate` Außerkraftsetzung der Memberfunktion der Ansicht. Wenn Sie keine automatische Skalierung `SetScrollSizes` wünschen, rufen Sie stattdessen die Memberfunktion auf.

`SetScaleToFitSize`kann verwendet werden, um einen "Zoom to Fit"-Vorgang zu implementieren. Verwenden `SetScrollSizes` Sie diese Option, um das Scrollen erneut zu initialisieren.

`SetScaleToFitSize`geht davon aus, dass die Größe des Ansichtsfensters festgelegt wurde. Wenn die Größe des Ansichtsfensters beim Aufruf nicht festgelegt `SetScaleToFitSize` wurde, erhalten Sie eine Assertion. Um sicherzustellen, dass dies nicht geschieht, `SetScaleToFitSize`führen Sie vor dem Aufruf den folgenden Aufruf aus:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a>CScrollView::SetScrollSizes

Rufen `SetScrollSizes` Sie an, wenn die Ansicht aktualisiert werden soll.

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parameter

*nMapMode*<br/>
Der Zuordnungsmodus, der für diese Ansicht festgelegt werden soll. Mögliche Werte sind:

|Zuordnungsmodus|Logische Einheit|Positive y-Achse Verlängert...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 Pixel|Nach unten|
|MM_HIMETRIC|0,01 mm|Aufwärts|
|MM_TWIPS|1/1440 in|Aufwärts|
|MM_HIENGLISH|0,001 in|Aufwärts|
|MM_LOMETRIC|0,1 mm|Aufwärts|
|MM_LOENGLISH|0,01 in|Aufwärts|

Alle diese Modi werden von Windows definiert. Zwei Standardzuordnungsmodi, MM_ISOTROPIC und MM_ANISOTROPIC, `CScrollView`werden nicht für verwendet. Die Klassenbibliothek `SetScaleToFitSize` stellt die Memberfunktion zum Skalieren der Ansicht auf die Fenstergröße bereit. Spalte drei in der obigen Tabelle beschreibt die Koordinatenausrichtung.

*GrößeGesamt*<br/>
Die Gesamtgröße der Bildlaufansicht. Das `cx` Element enthält die horizontale Ausdehnung. Das `cy` Element enthält die vertikale Ausdehnung. Größen sind in logischen Einheiten. Beide `cx` `cy` und müssen größer oder gleich 0 sein.

*sizePage*<br/>
Die horizontale und vertikale Menge, um in jede Richtung als Antwort auf einen Mausklick in einer Scroll-Balken-Welle zu scrollen. Das `cx` Element enthält den horizontalen Betrag. Das `cy` Element enthält den vertikalen Betrag.

*sizeLine*<br/>
Die horizontale und vertikale Menge, um in jede Richtung als Antwort auf einen Mausklick in einem Bildlaufpfeil zu scrollen. Das `cx` Element enthält den horizontalen Betrag. Das `cy` Element enthält den vertikalen Betrag.

### <a name="remarks"></a>Bemerkungen

Rufen Sie es in `OnUpdate` Ihrer Außerkraftsetzung der Memberfunktion auf, um die Bildlaufeigenschaften anzupassen, wenn z. B. das Dokument anfänglich angezeigt wird oder wenn sich die Größe ändert.

In der Regel erhalten Sie Größeninformationen aus dem zugeordneten Dokument `GetMyDocSize`der Ansicht, indem Sie eine Dokumentmemberfunktion aufrufen, die sie möglicherweise mit der abgeleiteten Dokumentklasse versorgen. Der folgende Code zeigt diesen Ansatz:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Alternativ müssen Sie manchmal eine feste Größe festlegen, wie im folgenden Code:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Sie müssen den Zuordnungsmodus auf einen der Windows-Zuordnungsmodi festlegen, mit Ausnahme MM_ISOTROPIC oder MM_ANISOTROPIC. Wenn Sie einen uneingeschränkten Zuordnungsmodus `SetScaleToFitSize` verwenden möchten, `SetScrollSizes`rufen Sie die Memberfunktion anstelle von auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd-Klasse](../../mfc/reference/csplitterwnd-class.md)
