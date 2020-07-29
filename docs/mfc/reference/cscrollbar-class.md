---
title: Cscrollbar-Klasse
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
ms.openlocfilehash: 1ab25ad26357abe9091d273637f3ae9f77457342
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230479"
---
# <a name="cscrollbar-class"></a>Cscrollbar-Klasse

Stellt die Funktionalität eines Windows-Bildlaufleisten-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CScrollBar : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cscrollbar:: cscrollbar](#cscrollbar)|Erstellt ein `CScrollBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Cscrollbar:: Create](#create)|Erstellt die Windows-Scrollleiste und fügt Sie an das- `CScrollBar` Objekt an.|
|[Cscrollbar:: enablescrollbar](#enablescrollbar)|Aktiviert oder deaktiviert einen oder beide Pfeile auf einer Scrollleiste.|
|[Cscrollbar:: getscrollbarinfo](#getscrollbarinfo)|Ruft Informationen über die Bild Lauf Leiste mithilfe einer- `SCROLLBARINFO` Struktur ab.|
|[Cscrollbar:: getscrollinfo](#getscrollinfo)|Ruft Informationen über die Scrollleiste ab.|
|[Cscrollbar:: getscrolllimit](#getscrolllimit)|Ruft den Grenzwert der Bild Lauf Leiste ab.|
|[Cscrollbar:: getscrollpos](#getscrollpos)|Ruft die aktuelle Position eines Scrollfelds ab.|
|[Cscrollbar:: getscrollrange](#getscrollrange)|Ruft die aktuellen minimalen und maximalen Schiebe leisten Positionen für die angegebene Bild Lauf Leiste ab.|
|[Cscrollbar:: setScrollInfo](#setscrollinfo)|Legt die Informationen über die Bildlaufleiste fest.|
|[Cscrollbar:: setscrollpos](#setscrollpos)|Legt die aktuelle Position eines scrollfelds fest.|
|[Cscrollbar:: setscrollrange](#setscrollrange)|Legt die minimalen und maximalen Positionswerte für die angegebene Scrollleiste fest.|
|[Cscrollbar:: ShowScrollbar](#showscrollbar)|Zeigt eine Schiebe Leiste an oder blendet sie aus.|

## <a name="remarks"></a>Bemerkungen

Sie erstellen ein ScrollBar-Steuerelement in zwei Schritten. Rufen Sie zuerst den-Konstruktor `CScrollBar` auf, um das-Objekt zu erstellen `CScrollBar` , und rufen Sie dann die [Create](#create) Member-Funktion auf, um das Windows-Bild Lauf leisten-Steuerelement zu erstellen und es an das `CScrollBar`

Wenn Sie ein- `CScrollBar` Objekt in einem Dialogfeld (über eine Dialogfeld Ressource) erstellen, `CScrollBar` wird automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie ein- `CScrollBar` Objekt in einem-Fenster erstellen, müssen Sie es möglicherweise auch zerstören.

Wenn Sie das `CScrollBar` Objekt auf dem Stapel erstellen, wird es automatisch zerstört. Wenn Sie das- `CScrollBar` Objekt auf dem Heap mithilfe der- **`new`** Funktion erstellen, müssen Sie für das-Objekt aufzurufen, **`delete`** um es zu zerstören, wenn der Benutzer die Windows-Scrollleiste beendet.

Wenn Sie im Objektspeicher zuweisen `CScrollBar` , überschreiben Sie den `CScrollBar` Dekonstruktor, um die Zuweisungen zu verwerfen.

Weitere Informationen zum Verwenden von `CScrollBar` finden Sie unter Steuer [Elemente](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>Cscrollbar:: Create

Erstellt die Windows-Scrollleiste und fügt Sie an das- `CScrollBar` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Gibt den Stil der Scrollleiste an. Wendet eine beliebige Kombi [Nation von Bild](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) Lauf leisten Formaten auf die Bild Lauf Leiste an.

*Rect*<br/>
Gibt die Größe und Position der Scrollleiste an. Kann entweder eine `RECT` Struktur oder ein- `CRect` Objekt sein.

*pparser*<br/>
Gibt das übergeordnete Fenster der Scrollleiste an, in der Regel ein- `CDialog` Objekt. Er darf nicht NULL sein.

*nID*<br/>
Die Steuerelement-ID der Scrollleiste.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie erstellen ein- `CScrollBar` Objekt in zwei Schritten. Zuerst wird der-Konstruktor aufgerufen, der das- `CScrollBar` Objekt erstellt. anschließend `Create` wird aufgerufen, wodurch die zugeordnete Windows-Scrollleiste erstellt und initialisiert und an das-Objekt angefügt wird `CScrollBar` .

Wenden Sie die folgenden [Fenster Stile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf eine Schiebe Leiste an:

- Immer WS_CHILD

- WS_VISIBLE in der Regel

- WS_DISABLED selten

- WS_GROUP zum Gruppieren von Steuerelementen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>Cscrollbar:: cscrollbar

Erstellt ein `CScrollBar`-Objekt.

```
CScrollBar();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie nach dem Erstellen des Objekts die `Create` Member-Funktion auf, um die Windows-Bild Lauf Leiste zu erstellen und zu initialisieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>Cscrollbar:: enablescrollbar

Aktiviert oder deaktiviert einen oder beide Pfeile auf einer Scrollleiste.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parameter

*schmalflags*<br/>
Gibt an, ob die Bild Lauf Pfeile aktiviert oder deaktiviert sind und welche Pfeile aktiviert oder deaktiviert werden. Dieser Parameter kann einen der folgenden Werte aufweisen:

- ESB_ENABLE_BOTH aktiviert beide Pfeile einer Schiebe Leiste.

- ESB_DISABLE_LTUP deaktiviert den Pfeil nach Links einer horizontalen Schiebe Leiste oder den Pfeil nach oben einer vertikalen Schiebe Leiste.

- ESB_DISABLE_RTDN deaktiviert den Pfeil nach rechts einer horizontalen Schiebe Leiste oder den Pfeil nach unten einer vertikalen Schiebe Leiste.

- ESB_DISABLE_BOTH deaktiviert beide Pfeile einer Schiebe Leiste.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Pfeile wie angegeben aktiviert oder deaktiviert werden. andernfalls 0 (null) gibt an, dass sich die Pfeile bereits im angeforderten Zustand befinden oder dass ein Fehler aufgetreten ist.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [cscrollbar:: setscrollrange](#setscrollrange).

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>Cscrollbar:: getscrollbarinfo

Ruft die Informationen ab, die von der `SCROLLBARINFO`-Struktur über eine Scrollleiste verwaltet werden.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parameter

*pscrollinfo*<br/>
Ein Zeiger auf die [scrollbarinfo](/windows/win32/api/winuser/ns-winuser-scrollbarinfo) -Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion emuliert die Funktionalität der [SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo) Nachricht, wie in der Windows SDK beschrieben.

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>Cscrollbar:: getscrollinfo

Ruft die Informationen ab, die von der `SCROLLINFO`-Struktur über eine Scrollleiste verwaltet werden.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parameter

*lpscrollinfo*<br/>
Ein Zeiger auf eine [ScrollInfo](/windows/win32/api/winuser/ns-winuser-scrollinfo) -Struktur. Weitere Informationen zu dieser Struktur finden Sie in der Windows SDK.

*nmask*<br/>
Gibt die abzurufenden ScrollBar-Parameter an. Typische Verwendung, SIF_ALL, gibt eine Kombination von SIF_PAGE, SIF_POS, SIF_TRACKPOS und SIF_RANGE an. `SCROLLINFO`Weitere Informationen zu den nmask-Werten finden Sie unter.

### <a name="return-value"></a>Rückgabewert

Wenn die Nachricht Werte abgerufen hat, ist die Rückgabe true. Andernfalls ist Sie false.

### <a name="remarks"></a>Bemerkungen

`GetScrollInfo`ermöglicht Anwendungen die Verwendung von 32-Bit-scrollpositionen.

Die [ScrollInfo](/windows/win32/api/winuser/ns-winuser-scrollinfo) -Struktur enthält Informationen zu einer Schiebe Leiste, einschließlich der minimalen und maximalen scrollpositionen, der Seitengröße und der Position des Bild Lauf Felds (Ziehpunkt). `SCROLLINFO`Weitere Informationen zum Ändern der Struktur Standardwerte finden Sie im Thema zur Struktur des Windows SDK.

Die MFC-Windows-Meldungs Handler, die die Position der Scrollleiste angeben ([CWnd:: OnHScroll und [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)), stellen nur 16 Bits von Positionsdaten bereit. `GetScrollInfo`und `SetScrollInfo` stellen 32 Bits von Positions leisten-Positionsdaten bereit. Daher kann eine Anwendung bei der `GetScrollInfo` Verarbeitung `CWnd::OnHScroll` `CWnd::OnVScroll` von oder zum Abrufen von 32-Bit-Scrollleisten-Positionsdaten aufruft.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>Cscrollbar:: getscrolllimit

Ruft die maximale Scrollposition der Scrollleiste ab.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Rückgabewert

Gibt die maximale Position einer Schiebe Leiste an, wenn erfolgreich. andernfalls 0.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>Cscrollbar:: getscrollpos

Ruft die aktuelle Position eines Scrollfelds ab.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die aktuelle Position des Bild Lauf Felds an, wenn erfolgreich. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die aktuelle Position ist ein relativer Wert, der vom aktuellen scrollbereich abhängig ist. Wenn der scrollbereich beispielsweise 100 bis 200 und das Bild Lauf Feld in der Mitte des Balkens liegt, ist die aktuelle Position 150.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>Cscrollbar:: getscrollrange

Kopiert die aktuellen minimalen und maximalen Schiebe leisten Positionen für die angegebene Bild Lauf Leiste an die von *lpminpos* und *lpmaxpos*angegebenen Speicherorte.

```cpp
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parameter

*lpminpos*<br/>
Verweist auf die ganzzahlige Variable, die die minimale Position erhalten soll.

*lpmaxpos*<br/>
Verweist auf die ganzzahlige Variable, die die maximale Position erhalten soll.

### <a name="remarks"></a>Bemerkungen

Der Standardbereich für ein Bild Lauf leisten-Steuerelement ist leer (beide Werte sind 0).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>Cscrollbar:: setScrollInfo

Legt die Informationen fest, die von der- `SCROLLINFO` Struktur über eine Schiebe Leiste verwaltet werden.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*lpscrollinfo*<br/>
Ein Zeiger auf eine [ScrollInfo](/windows/win32/api/winuser/ns-winuser-scrollinfo) -Struktur.

*bredraw*<br/>
Gibt an, ob die Bild Lauf Leiste neu gezeichnet werden soll, um die neuen Informationen widerzuspiegeln. Wenn *bredraw* den Wert true hat, wird die Scrollleiste neu gezeichnet. Wenn der Wert false ist, wird er nicht neu gezeichnet. Die Bild Lauf Leiste wird standardmäßig neu gezeichnet.

### <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung ist die Rückgabe true. Andernfalls ist Sie false.

### <a name="remarks"></a>Bemerkungen

Sie müssen die Werte angeben, die für die `SCROLLINFO` Struktur Parameter erforderlich sind, einschließlich der Flagwerte.

Die `SCROLLINFO` Struktur enthält Informationen zu einer Schiebe Leiste, einschließlich der minimalen und maximalen scrollpositionen, der Seitengröße und der Position des Bild Lauf Felds (Ziehpunkt). Weitere Informationen zum Ändern der Struktur Standardwerte finden Sie im Thema [ScrollInfo](/windows/win32/api/winuser/ns-winuser-scrollinfo) -Struktur im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>Cscrollbar:: setscrollpos

Legt die aktuelle Position eines Bild Lauf Felds auf das von *NPOs* angegebene fest und zeichnet, falls angegeben, die Schiebe Leiste neu, um die neue Position widerzuspiegeln.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*NPOs*<br/>
Gibt die neue Position für das Bild Lauf Feld an. Er muss innerhalb des scrollbereichs liegen.

*bredraw*<br/>
Gibt an, ob die Bild Lauf Leiste neu gezeichnet werden soll, um die neue Position widerzuspiegeln. Wenn *bredraw* den Wert true hat, wird die Scrollleiste neu gezeichnet. Wenn der Wert false ist, wird er nicht neu gezeichnet. Die Bild Lauf Leiste wird standardmäßig neu gezeichnet.

### <a name="return-value"></a>Rückgabewert

Gibt die vorherige Position des Bild Lauf Felds an, wenn erfolgreich. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Legen Sie *bredraw* auf false fest, wenn die Bild Lauf Leiste durch einen nachfolgenden Aufruf einer anderen Funktion neu gezeichnet wird, um zu vermeiden, dass die Bild Lauf Leiste zweimal innerhalb eines kurzen Intervalls neu gezeichnet wird.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [cscrollbar:: setscrollrange](#setscrollrange).

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>Cscrollbar:: setscrollrange

Legt die minimalen und maximalen Positionswerte für die angegebene Scrollleiste fest.

```cpp
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*nminpos*<br/>
Gibt die minimale Bild Lauf Position an.

*nmaxpos*<br/>
Gibt die maximale Scrollposition an.

*bredraw*<br/>
Gibt an, ob die Bild Lauf Leiste neu gezeichnet werden soll, um die Änderung widerzuspiegeln. Wenn *bredraw* den Wert true hat, wird die Scrollleiste neu gezeichnet. Wenn der Wert false ist, wird er nicht neu gezeichnet. Sie wird standardmäßig neu gezeichnet.

### <a name="remarks"></a>Bemerkungen

Legen Sie *nminpos* und *nmaxpos* auf 0 fest, um Standard Scrollleisten auszublenden.

Diese Funktion kann nicht aufgerufen werden, um beim Verarbeiten einer Benachrichtigungs Meldung der Bild Lauf Leiste eine Bild Lauf Leiste auszublenden.

Wenn ein Aufrufen von `SetScrollRange` unmittelbar auf einen Aufrufen der `SetScrollPos` Member-Funktion folgt, legen Sie *bredraw* in `SetScrollPos` auf 0 fest, um zu verhindern, dass die Bild Lauf Leiste zweimal neu gezeichnet wird.

Der Unterschied zwischen den von *nminpos* und *nmaxpos* angegebenen Werten darf nicht größer als 32.767 sein. Der Standardbereich für ein Bild Lauf leisten-Steuerelement ist leer (sowohl *nminpos* als auch *nmaxpos* sind 0).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>Cscrollbar:: ShowScrollbar

Zeigt eine Schiebe Leiste an oder blendet sie aus.

```cpp
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
Gibt an, ob die Bild Lauf Leiste angezeigt oder ausgeblendet wird. Wenn dieser Parameter true ist, wird die Scrollleiste angezeigt. Andernfalls wird Sie ausgeblendet.

### <a name="remarks"></a>Bemerkungen

Eine Anwendung sollte diese Funktion nicht zum Ausblenden einer Schiebe Leiste bei der Verarbeitung einer Benachrichtigungs Meldung für eine Schiebe Leiste ausführen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [cscrollbar:: Create](#create).

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit-Klasse](../../mfc/reference/cedit-class.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)<br/>
[Cstatic-Klasse](../../mfc/reference/cstatic-class.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
