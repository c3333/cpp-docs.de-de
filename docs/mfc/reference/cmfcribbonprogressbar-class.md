---
title: CMFCRibbonProgressBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
ms.openlocfilehash: 063f8ce560af84d350abc0114644f6a63f969f95
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368866"
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar-Klasse

Implementiert ein Steuerelement, das den Fortschritt einer längeren Operation visuell darstellt.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Erstellt und initialisiert ein `CMFCRibbonProgressBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonProgressBar::GetPos](#getpos)|Gibt den aktuellen Fortschritt zurück.|
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Gibt den Maximalwert des aktuellen Bereichs zurück.|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Gibt den Mindestwert des aktuellen Bereichs zurück.|
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Gibt die reguläre Größe des Menübandelements zurück. (Überschreibt [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Gibt an, ob die Fortschrittsleiste im unendlichen Modus arbeitet.|
|[CMFCRibbonProgressbar::OnDraw](#ondraw)|Wird vom Framework aufgerufen, um das Menübandelement zu zeichnen. (Überschreibt [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Legt fest, dass die Fortschrittsleiste im unendlichen Modus funktioniert.|
|[CMFCRibbonProgressBar::SetPos](#setpos)|Legt den aktuellen Fortschritt fest.|
|[CMFCRibbonProgressBar::SetRange](#setrange)|Legt die minimalen und maximalen Werte fest.|

## <a name="remarks"></a>Bemerkungen

A `CMFCRibbonProgressBar` kann in zwei Modi arbeiten: regelmäßig und unendlich. Im regulären Modus wird der Fortschrittsbalken von links nach rechts gefüllt und stoppt, wenn er den Maximalwert erreicht. Im unendlichen Modus wird der Fortschrittsbalken wiederholt vom Minimalwert zum Maximalwert gefüllt. Sie können den unendlichen Modus verwenden, um anzuzeigen, dass ein Vorgang fortläuft, die Fertigstellungszeit jedoch unbekannt ist.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCRibbonProgressBar` -Klasse. Das Beispiel zeigt, wie Sie die Fortschrittsleiste so einstellen, dass sie im unendlichen Modus funktioniert (wobei die Abschlusszeit eines Vorgangs unbekannt ist), die minimalen und maximalen Werte für den Fortschrittsbalken festlegen und die aktuelle Position des Fortschrittsbalkens festlegen. Dieser Codeausschnitt ist Teil des [MS Office 2007-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxRibbonProgressBar.h

## <a name="cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar

Erstellt und initialisiert ein [CMFCRibbonProgressBar-Objekt.](../../mfc/reference/cmfcribbonprogressbar-class.md)

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
[in] Gibt die Befehls-ID für die Multifunktionsleisten-Fortschrittleiste an.

*nWidth*<br/>
[in] Gibt die Breite der Multifunktionsleisten-Fortschrittsleiste in Pixel an.

*nHeight*<br/>
[in] Gibt die Höhe der Multifunktionsleisten-Fortschrittsleiste in Pixel an.

## <a name="cmfcribbonprogressbargetpos"></a><a name="getpos"></a>CMFCRibbonProgressBar::GetPos

Gibt die aktuelle Position des Fortschrittsbalkens zurück.

```
int GetPos () const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der die aktuelle Position des Fortschrittsbalkens darstellt.

### <a name="remarks"></a>Bemerkungen

Der festgelegte Bereich muss innerhalb des von der [CMFCRibbonProgressBar::SetRange-Methode](#setrange) angegebenen Bereichs liegen.

## <a name="cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax

Gibt den aktuellen Maximalwert des Fortschrittsbalkens zurück.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Rückgabewert

Der Maximalwert des aktuellen Bereichs.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin

Gibt den aktuellen Mindestbereichswert des Fortschrittsbalkens zurück.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Rückgabewert

Der Mindestwert des aktuellen Bereichs.

## <a name="cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode

Gibt an, ob die Fortschrittsleiste im unendlichen Modus arbeitet.

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich der Fortschrittsbalken im unendlichen Modus befindet; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Im unendlichen Modus füllt sich der Fortschrittsbalken wiederholt vom Minimalwert zum Maximalwert. Sie können den unendlichen Modus verwenden, um anzuzeigen, dass ein Vorgang fortläuft, die Fertigstellungszeit jedoch unbekannt ist.

## <a name="cmfcribbonprogressbarondraw"></a><a name="ondraw"></a>CMFCRibbonProgressbar::OnDraw

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode

Legt fest, dass die Fortschrittsleiste im unendlichen Modus funktioniert.

```
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parameter

*bSet*<br/>
[in] TRUE, um anzugeben, dass sich der Fortschrittsbalken im unendlichen Modus befindet; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn sich der Fortschrittsbalken im unendlichen Modus befindet, wird dem Benutzer in der Regel mitgeteilt, dass ein Vorgang fortläuft, die Fertigstellungszeit jedoch unbekannt ist. Somit wird der Fortschrittsbalken wiederholt vom Minimalwert zum Maximalwert gefüllt.

## <a name="cmfcribbonprogressbarsetpos"></a><a name="setpos"></a>CMFCRibbonProgressBar::SetPos

Legt die aktuelle Position des Fortschrittsbalkens fest.

```
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
[in] Gibt die Position an, an die die Fortschrittsleiste festgelegt ist.

*bZeichnung*<br/>
[in] Gibt an, ob der Fortschrittsbalken neu gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Der festgelegte Bereich muss innerhalb des von der [CMFCRibbonProgressBar::SetRange-Methode](#setrange) angegebenen Bereichs liegen.

## <a name="cmfcribbonprogressbarsetrange"></a><a name="setrange"></a>CMFCRibbonProgressBar::SetRange

Legt die minimalen und maximalen Werte für den Fortschrittsbalken fest.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parameter

*Nmin*<br/>
[in] Gibt den Mindestwert des Bereichs an.

*nMax*<br/>
[in] Gibt den maximalen Wert des Bereichs an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um den Bereich der Fortschrittsleiste zu definieren, indem Sie minimale und maximale Werte festlegen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement-Klasse](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar-Klasse](../../mfc/reference/cmfcribbonbar-class.md)
