---
title: CScrollBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
ms.openlocfilehash: 761d7e9db650c6d95e916c85bd7456d9b1c647c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318535"
---
# <a name="cscrollbar-class"></a>CScrollBar-Klasse

Stellt die Funktionalität eines Windows-Bildlaufleisten-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CScrollBar : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CScrollBar::CScrollBar](#cscrollbar)|Erstellt ein `CScrollBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CScrollBar::Erstellen](#create)|Erstellt die Windows-Bildlaufleiste und `CScrollBar` fügt sie an das Objekt an.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Aktiviert oder deaktiviert einen oder beide Pfeile auf einer Scrollleiste.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Ruft Informationen über die Bildlaufleiste mithilfe einer `SCROLLBARINFO` Struktur ab.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Ruft Informationen zur Bildlaufleiste ab.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Ruft das Limit der Bildlaufleiste ab|
|[CScrollBar::GetScrollPos](#getscrollpos)|Ruft die aktuelle Position eines Scrollfelds ab.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Ruft die aktuellen minimalen und maximalen Bildlaufleistenpositionen für die angegebene Bildlaufleiste ab.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Legt die Informationen über die Bildlaufleiste fest.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Legt die aktuelle Position eines Bildlauffelds fest.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Legt die minimalen und maximalen Positionswerte für die angegebene Scrollleiste fest.|
|[CScrollBar::ShowScrollBar](#showscrollbar)|Zeigt eine Bildlaufleiste ein oder blendet sie aus.|

## <a name="remarks"></a>Bemerkungen

Sie erstellen ein Bildlaufleistensteuerelement in zwei Schritten. Rufen Sie zunächst `CScrollBar` den Konstruktor auf, um das `CScrollBar` Objekt zu erstellen, und rufen Sie dann die [Memberfunktion Erstellen](#create) auf, um das Windows-Scrollleistensteuerelement zu erstellen und es an das `CScrollBar` Objekt anzuhängen.

Wenn Sie `CScrollBar` ein Objekt in einem Dialogfeld (über eine Dialogfeldressource) erstellen, wird dieser `CScrollBar` automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie `CScrollBar` ein Objekt in einem Fenster erstellen, müssen Sie es möglicherweise auch zerstören.

Wenn Sie `CScrollBar` das Objekt auf dem Stapel erstellen, wird es automatisch zerstört. Wenn Sie `CScrollBar` das Objekt auf dem Heap mithilfe der **neuen** Funktion erstellen, müssen Sie **das Objekt** löschen aufrufen, um es zu zerstören, wenn der Benutzer die Windows-Bildlaufleiste beendet.

Wenn Sie Speicher im `CScrollBar` Objekt zuweisen, `CScrollBar` überschreiben Sie den Destruktor, um die Zuordnungen zu entsorgen.

Weitere Informationen zur `CScrollBar`Verwendung finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar::Erstellen

Erstellt die Windows-Bildlaufleiste und `CScrollBar` fügt sie an das Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil der Bildlaufleiste an. Wenden Sie eine beliebige Kombination von [Bildlaufleistenstilen](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) auf die Bildlaufleiste an.

*Rect*<br/>
Gibt die Größe und Position der Bildlaufleiste an. Kann entweder `RECT` eine Struktur `CRect` oder ein Objekt sein.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster der Bildlaufleiste an, in der Regel ein `CDialog` Objekt. Es darf nicht NULL sein.

*nID*<br/>
Die Steuer-ID der Bildlaufleiste.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CScrollBar` ein Objekt in zwei Schritten. Rufen Sie zunächst den Konstruktor `CScrollBar` auf, der das Objekt erstellt. rufen `Create`Sie dann auf , wodurch die zugehörige Windows-Bildlaufleiste erstellt und initialisiert und an das `CScrollBar` Objekt angefügt wird.

Wenden Sie die folgenden [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf eine Bildlaufleiste an:

- WS_CHILD Immer

- WS_VISIBLE In der Regel

- WS_DISABLED Selten

- WS_GROUP Zu Gruppensteuerelementen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar::CScrollBar

Erstellt ein `CScrollBar`-Objekt.

```
CScrollBar();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie nach dem `Create` Erstellen des Objekts die Memberfunktion auf, um die Windows-Bildlaufleiste zu erstellen und zu initialisieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar::EnableScrollBar

Aktiviert oder deaktiviert einen oder beide Pfeile auf einer Scrollleiste.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parameter

*nArrowFlags*<br/>
Gibt an, ob die Bildlaufpfeile aktiviert oder deaktiviert sind und welche Pfeile aktiviert oder deaktiviert sind. Dieser Parameter kann einer der folgenden Werte sein:

- ESB_ENABLE_BOTH Aktiviert beide Pfeile einer Bildlaufleiste.

- ESB_DISABLE_LTUP Deaktiviert den linken Pfeil einer horizontalen Bildlaufleiste oder den Pfeil nach oben einer vertikalen Bildlaufleiste.

- ESB_DISABLE_RTDN Deaktiviert den rechten Pfeil einer horizontalen Bildlaufleiste oder den Abwärtspfeil einer vertikalen Bildlaufleiste.

- ESB_DISABLE_BOTH Deaktiviert beide Pfeile einer Bildlaufleiste.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Pfeile wie angegeben aktiviert oder deaktiviert sind; andernfalls 0, was angibt, dass sich die Pfeile bereits im angeforderten Zustand befinden oder dass ein Fehler aufgetreten ist.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CScrollBar::SetScrollRange](#setscrollrange).

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar::GetScrollBarInfo

Ruft die Informationen ab, die von der `SCROLLBARINFO`-Struktur über eine Scrollleiste verwaltet werden.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parameter

*pScrollInfo*<br/>
Ein Zeiger auf die [SCROLLBARINFO-Struktur.](/windows/win32/api/winuser/ns-winuser-scrollbarinfo)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der [SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo) Nachricht, wie im Windows SDK beschrieben.

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

Ruft die Informationen ab, die von der `SCROLLINFO`-Struktur über eine Scrollleiste verwaltet werden.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parameter

*lpScrollInfo*<br/>
Ein Zeiger auf eine [SCROLLINFO-Struktur.](/windows/win32/api/winuser/ns-winuser-scrollinfo) Weitere Informationen zu dieser Struktur finden Sie im Windows SDK.

*nMaske*<br/>
Gibt die abzurufenbalkenparameter an, die abgerufen werden sollen. Typische Verwendung, SIF_ALL, gibt eine Kombination aus SIF_PAGE, SIF_POS, SIF_TRACKPOS und SIF_RANGE an. Weitere `SCROLLINFO` Informationen zu den nMask-Werten finden Sie unter .

### <a name="return-value"></a>Rückgabewert

Wenn die Nachricht Werte abgerufen hat, lautet die Rückgabe TRUE. Andernfalls ist es FALSE.

### <a name="remarks"></a>Bemerkungen

`GetScrollInfo`ermöglicht anwendungen die Verwendung von 32-Bit-Bildlaufpositionen.

Die [SCROLLINFO-Struktur](/windows/win32/api/winuser/ns-winuser-scrollinfo) enthält Informationen über eine Bildlaufleiste, einschließlich der minimalen und maximalen Bildlaufpositionen, der Seitengröße und der Position des Bildlauffelds (Daumen). Weitere `SCROLLINFO` Informationen zum Ändern der Strukturstandards finden Sie im Strukturthema im Windows SDK.

Die MFC Windows-Nachrichtenhandler, die die Bildlaufleistenposition [CWnd::OnHScroll und [CWnd::OnVScroll "](../../mfc/reference/cwnd-class.md#onvscroll)angeben, stellen nur 16 Bits Positionsdaten bereit. `GetScrollInfo`und `SetScrollInfo` stellen Sie 32 Bit Bildlaufleistenpositionsdaten bereit. Daher kann eine `GetScrollInfo` Anwendung während `CWnd::OnHScroll` `CWnd::OnVScroll` der Verarbeitung entweder aufrufen oder 32-Bit-Bildlaufleistenpositionsdaten abrufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

Ruft die maximale Bildlaufposition der Bildlaufleiste ab.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Rückgabewert

Gibt die maximale Position einer Bildlaufleiste an, wenn sie erfolgreich ist. andernfalls 0.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar::GetScrollPos

Ruft die aktuelle Position eines Scrollfelds ab.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die aktuelle Position des Bildlauffelds an, wenn dies erfolgreich ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die aktuelle Position ist ein relativer Wert, der vom aktuellen Bildlaufbereich abhängt. Wenn der Bildlaufbereich beispielsweise 100 bis 200 beträgt und sich das Bildlauffeld in der Mitte des Balkens befindet, ist die aktuelle Position 150.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::GetScrollRange

Kopiert die aktuellen minimalen und maximalen Bildlaufleistenpositionen für die angegebene Bildlaufleiste an die von *lpMinPos* und *lpMaxPos*angegebenen Positionen .

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parameter

*lpMinPos*<br/>
Zeigt auf die Ganzzahlvariable, die die Mindestposition erhalten soll.

*lpMaxPos*<br/>
Zeigt auf die Ganzzahlvariable, die die maximale Position erhalten soll.

### <a name="remarks"></a>Bemerkungen

Der Standardbereich für ein Scrollleistensteuerelement ist leer (beide Werte sind 0).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

Legt die Informationen `SCROLLINFO` fest, die die Struktur für eine Bildlaufleiste verwaltet.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*lpScrollInfo*<br/>
Ein Zeiger auf eine [SCROLLINFO-Struktur.](/windows/win32/api/winuser/ns-winuser-scrollinfo)

*bZeichnung*<br/>
Gibt an, ob die Bildlaufleiste neu gezeichnet werden soll, um die neuen Informationen widerzuspiegeln. Wenn *bRedraw* TRUE ist, wird die Bildlaufleiste neu gezeichnet. Wenn es FALSE ist, wird es nicht neu gezeichnet. Die Bildlaufleiste wird standardmäßig neu gezeichnet.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, lautet die Rückgabe TRUE. Andernfalls ist es FALSE.

### <a name="remarks"></a>Bemerkungen

Sie müssen die Werte `SCROLLINFO` angeben, die für die Strukturparameter erforderlich sind, einschließlich der Flagwerte.

Die `SCROLLINFO` Struktur enthält Informationen über eine Bildlaufleiste, einschließlich der minimalen und maximalen Bildlaufpositionen, der Seitengröße und der Position des Bildlauffelds (Daumen). Weitere Informationen zum Ändern der Strukturstandards finden Sie im Thema [scrollINFO-Struktur](/windows/win32/api/winuser/ns-winuser-scrollinfo) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::SetScrollPos

Legt die aktuelle Position eines Bildlauffelds auf die von *nPos* angegebene Position fest und zeichnet, falls angegeben, die Bildlaufleiste neu, um die neue Position widerzuspiegeln.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Gibt die neue Position für das Bildlauffeld an. Sie muss sich innerhalb des Bildlaufbereichs befinden.

*bZeichnung*<br/>
Gibt an, ob die Bildlaufleiste neu gezeichnet werden soll, um die neue Position widerzuspiegeln. Wenn *bRedraw* TRUE ist, wird die Bildlaufleiste neu gezeichnet. Wenn es FALSE ist, wird es nicht neu gezeichnet. Die Bildlaufleiste wird standardmäßig neu gezeichnet.

### <a name="return-value"></a>Rückgabewert

Gibt die vorherige Position des Bildlauffelds an, wenn es erfolgreich ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Legen Sie *bRedraw* auf FALSE fest, wenn die Bildlaufleiste durch einen nachfolgenden Aufruf einer anderen Funktion neu gezeichnet wird, um zu vermeiden, dass die Bildlaufleiste innerhalb eines kurzen Intervalls zweimal neu gezeichnet wird.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CScrollBar::SetScrollRange](#setscrollrange).

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::SetScrollRange

Legt die minimalen und maximalen Positionswerte für die angegebene Scrollleiste fest.

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*nMinPos*<br/>
Gibt die minimale Bildlaufposition an.

*nMaxPos*<br/>
Gibt die maximale Bildlaufposition an.

*bZeichnung*<br/>
Gibt an, ob die Bildlaufleiste neu gezeichnet werden soll, um die Änderung widerzuspiegeln. Wenn *bRedraw* TRUE ist, wird die Bildlaufleiste neu gezeichnet. wenn FALSE, wird es nicht neu gezeichnet. Sie wird standardmäßig neu gezeichnet.

### <a name="remarks"></a>Bemerkungen

Legen Sie *nMinPos* und *nMaxPos* auf 0 fest, um Standard-Scrollleisten auszublenden.

Rufen Sie diese Funktion nicht auf, um eine Bildlaufleiste auszublenden, während Sie eine Bildlaufleistenbenachrichtigung verarbeiten.

Wenn ein `SetScrollRange` Aufruf unmittelbar auf `SetScrollPos` einen Aufruf der Memberfunktion `SetScrollPos` folgt, setzen Sie *bRedraw* in auf 0, um zu verhindern, dass die Bildlaufleiste zweimal neu gezeichnet wird.

Die Differenz zwischen den von *nMinPos* und *nMaxPos* angegebenen Werten darf nicht größer als 32.767 sein. Der Standardbereich für ein Scrollleistensteuerelement ist leer (sowohl *nMinPos* als auch *nMaxPos* sind 0).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar::ShowScrollBar

Zeigt eine Bildlaufleiste ein oder blendet sie aus.

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
Gibt an, ob die Bildlaufleiste angezeigt oder ausgeblendet wird. Wenn dieser Parameter TRUE ist, wird die Bildlaufleiste angezeigt. andernfalls ist es ausgeblendet.

### <a name="remarks"></a>Bemerkungen

Eine Anwendung sollte diese Funktion nicht aufrufen, um eine Bildlaufleiste auszublenden, während eine Bildlaufleistenbenachrichtigung verarbeitet wird.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CScrollBar::Create](#create).

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)<br/>
[CStatic-Klasse](../../mfc/reference/cstatic-class.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
