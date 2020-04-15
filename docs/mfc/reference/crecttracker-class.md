---
title: CRectTracker-Klasse
ms.date: 11/19/2018
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
ms.openlocfilehash: 4d262ab5f88481d56de1c236effb66fcbf6a706a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368377"
---
# <a name="crecttracker-class"></a>CRectTracker-Klasse

Ermöglicht die Anzeige, Beschreibung und Größe eines Elements auf unterschiedliche Weise.

## <a name="syntax"></a>Syntax

```
class CRectTracker
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|Erstellt ein `CRectTracker`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|Wird aufgerufen, wenn die Größe des Rechtecks geändert wird.|
|[CRectTracker::Draw](#draw)|Rendert das Rechteck.|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Wird beim Zeichnen des `CRectTracker` Rahmens eines Objekts aufgerufen.|
|[CRectTracker::GetHandleMask](#gethandlemask)|Wird aufgerufen, um `CRectTracker` die Maske der Ziehpunkte für die Größenänderung eines Elements abzusuchen.|
|[CRectTracker::GetTrueRect](#gettruerect)|Gibt Breite und Höhe des Rechtecks zurück, einschließlich Größenänderungsziehpunkte.|
|[CRectTracker::HitTest](#hittest)|Gibt die aktuelle Position des `CRectTracker` Cursors zurück, der sich auf das Objekt bezieht.|
|[CRectTracker::NormalizeHit](#normalizehit)|Normalisiert einen Treffertestcode.|
|[CRectTracker::OnChangedRect](#onchangedrect)|Wird aufgerufen, wenn die Größe des Rechtecks geändert oder verschoben wurde.|
|[CRectTracker::SetCursor](#setcursor)|Legt den Cursor in Abhängigkeit von seiner Position über dem Rechteck fest.|
|[CRectTracker::Track](#track)|Ermöglicht es dem Benutzer, das Rechteck zu bearbeiten.|
|[CRectTracker::TrackRubberBand](#trackrubberband)|Ermöglicht es dem Benutzer, die Auswahl "gummi-band" zu machen.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Bestimmt die Größe der Ziehpunkte für die Größenänderung.|
|[CRectTracker::m_nStyle](#m_nstyle)|Aktuelle Stile des Trackers.|
|[CRectTracker::m_rect](#m_rect)|Aktuelle Position (in Pixel) des Rechtecks.|
|[CRectTracker::m_sizeMin](#m_sizemin)|Bestimmt die minimale Rechteckbreite und -höhe.|

## <a name="remarks"></a>Bemerkungen

`CRectTracker`hat keine Basisklasse.

Obwohl `CRectTracker` die Klasse so konzipiert ist, dass der Benutzer mit OLE-Elementen mithilfe einer grafischen Oberfläche interagieren kann, ist ihre Verwendung nicht auf OLE-fähige Anwendungen beschränkt. Es kann überall dort verwendet werden, wo eine solche Benutzeroberfläche benötigt wird.

`CRectTracker`Rahmen können durchgezogene oder gepunktete Linien sein. Das Element kann einen geschlüpften Rahmen oder überlagert mit einem schraffierten Muster erhalten, um verschiedene Zustände des Elements anzuzeigen. Sie können acht Ziehpunkte zur Größenänderung entweder am äußeren oder am inneren Rand des Elements platzieren. (Eine Erläuterung der Ziehpunkte zur Größenänderung finden Sie unter [GetHandleMask](#gethandlemask).) Schließlich können `CRectTracker` Sie mit a die Ausrichtung eines Elements während der Größenänderung ändern.

Um `CRectTracker`zu verwenden, erstellen Sie ein `CRectTracker` Objekt und geben Sie an, welche Anzeigezustände initialisiert werden. Sie können diese Schnittstelle dann verwenden, um dem Benutzer visuelles Feedback `CRectTracker` zum aktuellen Status des OLE-Elements zu geben, das dem Objekt zugeordnet ist.

Weitere Informationen zur `CRectTracker`Verwendung finden Sie im Artikel [Trackers](../../mfc/trackers.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CRectTracker`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxext.h

## <a name="crecttrackeradjustrect"></a><a name="adjustrect"></a>CRectTracker::AdjustRect

Wird vom Framework aufgerufen, wenn die Größe des Nachverfolgungsrechtecks mithilfe eines Ziehpunkts zum Ändern der Größe geändert wird.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parameter

*nHandle*<br/>
Index des verwendeten Handles.

*lpRect*<br/>
Zeiger auf die aktuelle Größe des Rechtecks. (Die Größe eines Rechtecks wird durch seine Höhe und Breite angegeben.)

### <a name="remarks"></a>Bemerkungen

Das Standardverhalten dieser Funktion ermöglicht es, die `Track` Ausrichtung `TrackRubberBand` des Rechtecks nur zu ändern, wenn und aufgerufen werden, wenn invertieren erlaubt.

Überschreiben Sie diese Funktion, um die Anpassung des Nachverfolgungsrechtecks während eines Ziehvorgangs zu steuern. Eine Methode besteht darin, die von *lpRect* angegebenen Koordinaten vor der Rückgabe anzupassen.

Spezielle Funktionen, die nicht `CRectTracker`direkt von unterstützt werden, wie Snap-to-Grid oder Keep-Aspect-Ratio, können durch Überschreiben dieser Funktion implementiert werden.

## <a name="crecttrackercrecttracker"></a><a name="crecttracker"></a>CRectTracker::CRectTracker

Erstellt und initialisiert ein `CRectTracker`-Objekt.

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>Parameter

*lpSrcRect*<br/>
Die Koordinaten des Rechteckobjekts.

*nStyle*<br/>
Gibt den Stil `CRectTracker` des Objekts an. Die folgenden Stile werden unterstützt:

- `CRectTracker::solidLine`Verwenden Sie eine durchgezogene Linie für den Rechteckrahmen.

- `CRectTracker::dottedLine`Verwenden Sie eine gepunktete Linie für den Rechteckrahmen.

- `CRectTracker::hatchedBorder`Verwenden Sie ein Schraffurmuster für den Rechteckrahmen.

- `CRectTracker::resizeInside`Ändern der Größe von Ziehgriffen, die sich innerhalb des Rechtecks befinden.

- `CRectTracker::resizeOutside`Ändern der Größe von Ziehgriffen, die sich außerhalb des Rechtecks befinden.

- `CRectTracker::hatchInside`Das Schraffurmuster bedeckt das gesamte Rechteck.

### <a name="remarks"></a>Bemerkungen

Der Standardkonstruktor initialisiert `CRectTracker` das Objekt mit den Werten aus *lpSrcRect* und initialisiert andere Größen in Systemstandards. Wenn das Objekt ohne Parameter `m_rect` erstellt `m_nStyle` wird, werden die und die Datenmember nicht initialisiert.

## <a name="crecttrackerdraw"></a><a name="draw"></a>CRectTracker::Draw

Rufen Sie diese Funktion auf, um die äußeren Linien und den inneren Bereich des Rechtecks zu zeichnen.

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf den Gerätekontext, auf den gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Der Stil des Trackers bestimmt, wie die Zeichnung ausgeführt wird. Weitere Informationen zu `CRectTracker` den verfügbaren Stilen finden Sie im Konstruktor.

## <a name="crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a>CRectTracker::DrawTrackerRect

Wird vom Framework aufgerufen, wenn sich die `Track` Position `TrackRubberBand` des Trackers innerhalb der oder Memberfunktion geändert hat.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigen Sie `RECT` mit dem, der das zu zeichnende Rechteck enthält.

*pWndClipTo*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das zum Ausschneiden des Rechtecks verwendet werden soll.

*pDC*<br/>
Zeiger auf den Gerätekontext, auf den gezeichnet werden soll.

*pWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, in dem die Zeichnung ausgeführt wird.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung ruft `CDC::DrawFocusRect`einen auf, der ein gepunktetes Rechteck zeichnet.

Überschreiben Sie diese Funktion, um während des Überwachungsvorgangs unterschiedliches Feedback bereitzustellen.

## <a name="crecttrackergethandlemask"></a><a name="gethandlemask"></a>CRectTracker::GetHandleMask

Das Framework ruft diese Memberfunktion auf, um die Maske für die Größenänderungshandles eines Rechtecks abzurufen.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>Rückgabewert

Die Maske `CRectTracker` der Ziehpunkte für die Größenänderung eines Elements.

### <a name="remarks"></a>Bemerkungen

Die Ziehpunkte zur Größenänderung werden an den Seiten und Ecken des Rechtecks angezeigt und ermöglichen es dem Benutzer, die Form und Größe des Rechtecks zu steuern.

Ein Rechteck hat 8 Ziehpunkte zur Größenänderung mit der Nummer 0-7. Jeder Ziehpunkt zur Größenänderung wird durch ein Bit in der Maske dargestellt. Der Wert dieses Bits ist 2 *n*, wobei *n* die Größe der Handlenummer ist. Bits 0-3 entsprechen den Eckgrößengriffen, beginnend oben links im Uhrzeigersinn. Bits 4-7 entsprechen den seitlichen Größenänderungsgriffen, die oben im Uhrzeigersinn beginnen. Die folgende Abbildung zeigt die Größenänderungshandles eines Rechtecks und die entsprechenden Ziehgriffzahlen und -werte für die Größenänderung:

![Ändern der Größe von Handlenummern](../../mfc/reference/media/vc35dp1.gif "Nummern der Ziehpunkte zur Größenänderung")

Die Standardimplementierung `GetHandleMask` von gibt die Maske der Bits zurück, sodass die Ziehpunkte zur Größenänderung angezeigt werden. Wenn das einzelne Bit eingeschaltet ist, wird der entsprechende Ziehpunkt zur Größenänderung gezeichnet.

Überschreiben Sie diese Memberfunktion, um die angegebenen Ziehpunkte zur Größenänderung auszublenden oder anzuzeigen.

## <a name="crecttrackergettruerect"></a><a name="gettruerect"></a>CRectTracker::GetTrueRect

Rufen Sie diese Funktion auf, um die Koordinaten des Rechtecks abzurufen.

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>Parameter

*lpTrueRect*<br/>
Zeigen Sie `RECT` mit dem Zeiger auf die `CRectTracker` Struktur, die die Gerätekoordinaten des Objekts enthält.

### <a name="remarks"></a>Bemerkungen

Die Abmessungen des Rechtecks umfassen die Höhe und Breite aller Ziehpunkte für die Größenänderung, die sich am äußeren Rand befinden. Bei der Rückkehr ist *lpTrueRect* immer ein normalisiertes Rechteck in den Gerätekoordinaten.

## <a name="crecttrackerhittest"></a><a name="hittest"></a>CRectTracker::HitTest

Rufen Sie diese Funktion auf, um herauszufinden, ob der Benutzer ein Handle zum Ändern der Größe gegriffen hat.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Der Punkt in den Gerätekoordinaten, der getestet werden soll.

### <a name="return-value"></a>Rückgabewert

Der zurückgegebene Wert basiert auf dem `CRectTracker::TrackerHit` aufgezählten Typ und kann einen der folgenden Werte aufweisen:

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight`1

- `CRectTracker::hitBottomRight`2

- `CRectTracker::hitBottomLeft`3

- `CRectTracker::hitTop`4

- `CRectTracker::hitRight`5

- `CRectTracker::hitBottom`6

- `CRectTracker::hitLeft`7

- `CRectTracker::hitMiddle`8

## <a name="crecttrackerm_nhandlesize"></a><a name="m_nhandlesize"></a>CRectTracker::m_nHandleSize

Die Größe der `CRectTracker` Ziehpunkte zur Größenänderung in Pixel.

```
int m_nHandleSize;
```

### <a name="remarks"></a>Bemerkungen

Initialisiert mit dem Standardsystemwert.

## <a name="crecttrackerm_rect"></a><a name="m_rect"></a>CRectTracker::m_rect

Die aktuelle Position des Rechtecks in den Clientkoordinaten (Pixel).

```
CRect m_rect;
```

## <a name="crecttrackerm_sizemin"></a><a name="m_sizemin"></a>CRectTracker::m_sizeMin

Die Minimale Größe des Rechtecks.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Bemerkungen

Sowohl die `cx` Standardwerte als auch `cy`der werden aus dem Standardsystemwert für die Rahmenbreite berechnet. Dieses Datenelement wird nur `AdjustRect` von der Memberfunktion verwendet.

## <a name="crecttrackerm_nstyle"></a><a name="m_nstyle"></a>CRectTracker::m_nStyle

Aktueller Stil des Rechtecks.

```
UINT m_nStyle;
```

### <a name="remarks"></a>Bemerkungen

Eine Liste möglicher Stile finden Sie unter [CRectTracker::CRectTracker.](#crecttracker)

## <a name="crecttrackernormalizehit"></a><a name="normalizehit"></a>CRectTracker::NormalizeHit

Rufen Sie diese Funktion auf, um ein potenziell invertiertes Handle zu konvertieren.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>Parameter

*nHandle*<br/>
Handle, das vom Benutzer ausgewählt wurde.

### <a name="return-value"></a>Rückgabewert

Der Index des normalisierten Handles.

### <a name="remarks"></a>Bemerkungen

Wenn `CRectTracker::Track` `CRectTracker::TrackRubberBand` oder wenn invertieren erlaubt aufgerufen wird, ist es möglich, dass das Rechteck auf der x-Achse, der y-Achse oder beidem invertiert wird. Wenn dies `HitTest` geschieht, werden Handles zurückgegeben, die auch in Bezug auf das Rechteck invertiert sind. Dies ist für das Zeichnen von Cursorfeedback ungeeignet, da das Feedback von der Bildschirmposition des Rechtecks abhängt, nicht von dem Teil der Rechteckdatenstruktur, der geändert wird.

## <a name="crecttrackeronchangedrect"></a><a name="onchangedrect"></a>CRectTracker::OnChangedRect

Wird vom Framework aufgerufen, wenn sich das `Track`Tracker-Rechteck während eines Aufrufs von geändert hat.

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>Parameter

*rectOld*<br/>
Enthält die alten Gerätekoordinaten des `CRectTracker` Objekts.

### <a name="remarks"></a>Bemerkungen

Wenn diese Funktion aufgerufen wird, wurde `DrawTrackerRect` das gesamte mit gezeichnete Feedback entfernt. Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt.

Überschreiben Sie diese Funktion, wenn Sie Aktionen ausführen möchten, nachdem die Größe des Rechtecks geändert wurde.

## <a name="crecttrackersetcursor"></a><a name="setcursor"></a>CRectTracker::SetCursor

Rufen Sie diese Funktion auf, um `CRectTracker` die Cursor-Form zu ändern, während sie sich über dem Bereich des Objekts befindet.

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, das derzeit den Cursor enthält.

*nHitTest*<br/>
Ergebnisse des vorherigen Treffertests aus der WM_SETCURSOR Meldung.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn sich der vorherige Treffer über dem Tracker-Rechteck befand. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion innerhalb der Funktion Ihres Fensters `OnSetCursor`auf, das die WM_SETCURSOR Nachricht verarbeitet (normalerweise ).

## <a name="crecttrackertrack"></a><a name="track"></a>CRectTracker::Track

Rufen Sie diese Funktion auf, um die Benutzeroberfläche zum Ändern der Größe des Rechtecks anzuzeigen.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Das Fensterobjekt, das das Rechteck enthält.

*Punkt*<br/>
Gerätekoordinaten der aktuellen Mausposition relativ zum Clientbereich.

*bAllowInvert*<br/>
Wenn TRUE, kann das Rechteck entlang der x-Achse oder y-Achse invertiert werden. andernfalls FALSE.

*pWndClipTo*<br/>
Das Fenster, in das Zeichnungsvorgänge abgeschnitten werden. Wenn NULL, wird *pWnd* als Clipping-Rechteck verwendet.

### <a name="return-value"></a>Rückgabewert

Wenn die ESC-Taste gedrückt wird, wird der Verfolgungsprozess angehalten, das im Tracker gespeicherte Rechteck wird nicht geändert, und 0 wird zurückgegeben. Wenn die Änderung festgeschrieben wird, wird durch Bewegen der Maus und Loslassen der linken Maustaste die neue Position und/oder Größe im Rechteck des Trackers aufgezeichnet und ein Wert von ungleich Null zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Dies wird in der Regel von innerhalb `WM_LBUTTONDOWN` der Funktion `OnLButtonDown`Ihrer Anwendung aufgerufen, die die Nachricht verarbeitet (in der Regel ).

Diese Funktion erfasst die Maus, bis der Benutzer die linke Maustaste loslässt, die ESC-Taste drückt oder die rechte Maustaste drückt. Wenn der Benutzer den Mauszeiger bewegt, `DrawTrackerRect` wird `OnChangedRect`das Feedback durch Aufrufen und aktualisiert.

Wenn *bAllowInvert* TRUE ist, kann das Tracking-Rechteck entweder auf der x-Achse oder auf der y-Achse invertiert werden.

## <a name="crecttrackertrackrubberband"></a><a name="trackrubberband"></a>CRectTracker::TrackRubberBand

Rufen Sie diese Funktion auf, um die Gummibandauswahl zu erledigen.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Das Fensterobjekt, das das Rechteck enthält.

*Punkt*<br/>
Gerätekoordinaten der aktuellen Mausposition relativ zum Clientbereich.

*bAllowInvert*<br/>
Wenn TRUE, kann das Rechteck entlang der x-Achse oder y-Achse invertiert werden. andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn sich die Maus bewegt hat und das Rechteck nicht leer ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Es wird in der Regel von innerhalb der Funktion Ihrer `OnLButtonDown`Anwendung aufgerufen, die die WM_LBUTTONDOWN Nachricht verarbeitet (in der Regel ).

Diese Funktion erfasst die Maus, bis der Benutzer die linke Maustaste loslässt, die ESC-Taste drückt oder die rechte Maustaste drückt. Wenn der Benutzer den Mauszeiger bewegt, `DrawTrackerRect` wird `OnChangedRect`das Feedback durch Aufrufen und aktualisiert.

Die Verfolgung erfolgt mit einer Gummiband-Auswahl vom unteren rechten Griff. Wenn invertieren zulässig ist, kann die Größe des Rechtecks durch Ziehen nach oben und nach links oder unten und nach rechts geändert werden.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel-TRACKER](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar-Klasse](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect-Klasse](../../atl-mfc-shared/reference/crect-class.md)
