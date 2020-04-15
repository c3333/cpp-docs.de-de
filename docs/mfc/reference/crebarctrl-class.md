---
title: CReBarCtrl-Klasse
ms.date: 11/19/2018
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
ms.openlocfilehash: 776892d71e2cb0f5d57512754cd7fa12730eb044
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367449"
---
# <a name="crebarctrl-class"></a>CReBarCtrl-Klasse

Kapselt die Funktionalität eines Grundleisten-Steuerelements. Dabei handelt es sich um einen Container für ein untergeordnetes Fenster.

## <a name="syntax"></a>Syntax

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|Erstellt ein `CReBarCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|Platziert das Bewehrungssteuerelement in den Drag-and-Drop-Modus.|
|[CReBarCtrl::Erstellen](#create)|Erstellt das Bewehrungssteuerelement und `CReBarCtrl` fügt es an das Objekt an.|
|[CReBarCtrl::CreateEx](#createex)|Erstellt ein Bewehrungssteuerelement mit den angegebenen erweiterten `CReBarCtrl` Windows-Stilen und fügt es an ein Objekt an.|
|[CReBarCtrl::DeleteBand](#deleteband)|Löscht ein Band aus einem Bewehrungssteuerelement.|
|[CReBarCtrl::DragMove](#dragmove)|Aktualisiert die Ziehposition im Bewehrungssteuerelement nach einem Aufruf von `BeginDrag`.|
|[CReBarCtrl::EndDrag](#enddrag)|Beendet den Drag-and-Drop-Vorgang des Bewehrungssteuerelements.|
|[CReBarCtrl::GetBandBorders](#getbandborders)|Ruft die Ränder einer Band ab.|
|[CReBarCtrl::GetBandCount](#getbandcount)|Ruft die Anzahl der Bänder ab, die sich derzeit im Bewehrungssteuerelement befinden.|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Ruft Informationen zu einem angegebenen Band in einem Bewehrungssteuerelement ab.|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Ruft die Ränder eines Bands ab.|
|[CReBarCtrl::GetBarHeight](#getbarheight)|Ruft die Höhe des Bewehrungssteuerelements ab.|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Ruft Informationen über das Bewehrungssteuerelement und die von ihm verwendete Bildliste ab.|
|[CReBarCtrl::GetBkColor](#getbkcolor)|Ruft die Standardhintergrundfarbe eines Bewehrungssteuerelements ab.|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Ruft die [COLORSCHEME-Struktur ab,](/windows/win32/api/commctrl/ns-commctrl-colorscheme) die dem Bewehrungssteuerelement zugeordnet ist.|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Ruft den Schnittstellenzeiger eines `IDropTarget` Bewehrungssteuerelements ab.|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Ruft den erweiterten Stil des aktuellen Bewehrungssteuerelements ab.|
|[CReBarCtrl::GetImageList](#getimagelist)|Ruft die Bildliste ab, die einem Bewehrungssteuerelement zugeordnet ist.|
|[CReBarCtrl::GetPalette](#getpalette)|Ruft die aktuelle Palette des Bewehrungssteuerelements ab.|
|[CReBarCtrl::GetRect](#getrect)|Ruft das umschließende Rechteck für ein bestimmtes Band in einem Bewehrungssteuerelement ab.|
|[CReBarCtrl::GetRowCount](#getrowcount)|Ruft die Anzahl der Bandzeilen in einem Bewehrungssteuerelement ab.|
|[CReBarCtrl::GetRowHeight](#getrowheight)|Ruft die Höhe einer angegebenen Zeile in einem Bewehrungssteuerelement ab.|
|[CReBarCtrl::GetTextColor](#gettextcolor)|Ruft die Standardtextfarbe eines Bewehrungssteuerelements ab.|
|[CReBarCtrl::GetToolTipps](#gettooltips)|Ruft das Handle zu jedem QuickInfo-Steuerelement ab, das dem Bewehrungssteuerelement zugeordnet ist.|
|[CReBarCtrl::HitTest](#hittest)|Bestimmt, welcher Teil eines Bewehrungsbandes sich an einem bestimmten Punkt auf dem Bildschirm befindet, wenn an diesem Punkt ein Bewehrungsband vorhanden ist.|
|[CReBarCtrl::IDToIndex](#idtoindex)|Konvertiert einen Bandbezeichner (ID) in einen Bandindex in einem Bewehrungssteuerelement.|
|[CReBarCtrl::InsertBand](#insertband)|Fügt ein neues Band in ein Bewehrungssteuerelement ein.|
|[CReBarCtrl::MaximizeBand](#maximizeband)|Ändert die Größe eines Bands in einem Bewehrungssteuerelement auf seine größte Größe.|
|[CReBarCtrl::MinimizeBand](#minimizeband)|Ändert die Größe eines Bands in einem Bewehrungssteuerelement auf die kleinste Größe.|
|[CReBarCtrl::MoveBand](#moveband)|Verschiebt ein Band von einem Index in einen anderen.|
|[CReBarCtrl::PushChevron](#pushchevron)|Programmatisch schiebt ein Chevron.|
|[CReBarCtrl::RestoreBand](#restoreband)|Ändert die Größe eines Bands in einem Bewehrungssteuerelement auf seine ideale Größe.|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Legt die Eigenschaften eines vorhandenen Bands in einem Bewehrungssteuerelement fest.|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Legt die Breite des angegebenen angedockten Bandes im aktuellen Bewehrungssteuerelement fest.|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Legt die Eigenschaften eines Bewehrungssteuerelements fest.|
|[CReBarCtrl::SetBkColor](#setbkcolor)|Legt die Standardhintergrundfarbe eines Bewehrungssteuerelements fest.|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Legt das Farbschema für die Schaltflächen auf einem Bewehrungssteuerelement fest.|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Legt die erweiterten Stile für das aktuelle Bewehrungssteuerelement fest.|
|[CReBarCtrl::SetImageList](#setimagelist)|Legt die Bildliste eines Bewehrungssteuerelements fest.|
|[CReBarCtrl::SetOwner](#setowner)|Legt das Besitzerfenster eines Bewehrungssteuerelements fest.|
|[CReBarCtrl::SetPalette](#setpalette)|Legt die aktuelle Palette des Bewehrungssteuerelements fest.|
|[CReBarCtrl::SetTextColor](#settextcolor)|Legt die Standardtextfarbe eines Bewehrungssteuerelements fest.|
|[CReBarCtrl::SetToolTips](#settooltips)|Ordnet dem Bewehrungssteuerelement ein Werkzeugspitzensteuerelement zu.|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Legt den visuellen Stil des Bewehrungssteuerelements fest.|
|[CReBarCtrl::ShowBand](#showband)|Zeigt ein bestimmtes Band in einem Bewehrungssteuerelement an oder blendet es aus.|
|[CReBarCtrl::SizeToRect](#sizetorect)|Passt ein Bewehrungssteuerelement an ein angegebenes Rechteck an.|

## <a name="remarks"></a>Bemerkungen

Die Anwendung, in der sich das Bewehrungssteuerelement befindet, weist dem Bewehrungsband das untergeordnete Fenster zu, das im Bewehrungssteuerelement enthalten ist. Das untergeordnete Fenster ist in der Regel ein weiteres gängiges Steuerelement.

Bewehrungssteuerelemente enthalten ein oder mehrere Bänder. Jedes Band kann eine Kombination aus einer Greiferleiste, einer Bitmap, einer Textbeschriftung und einem untergeordneten Fenster enthalten. Das Band kann nur eines dieser Elemente enthalten.

Das Bewehrungssteuerelement kann das untergeordnete Fenster über einer angegebenen Hintergrundbitmap anzeigen. Alle Bewehrungsarmbänder können in der Größe geändert werden, mit Ausnahme derjenigen, die den RBBS_FIXEDSIZE-Stil verwenden. Wenn Sie ein Bewehrungssteuerelement neu positionieren oder die Größe ändern, verwaltet das Bewehrungssteuerelement die Größe und Position des untergeordneten Fensters, das diesem Band zugewiesen ist. Um die Größe der Bänder innerhalb des Steuerelements zu ändern oder zu ändern, klicken und ziehen Sie die Greiferleiste eines Bands.

Die folgende Abbildung zeigt ein Bewehrungssteuerelement mit drei Bändern:

- Band 0 enthält eine flache, transparente Werkzeugleistensteuerung.

- Band 1 enthält sowohl transparente Standard- als auch transparente Dropdown-Tasten.

- Band 2 enthält eine Kombinationsbox und vier Standardtasten.

   ![Beispiel eines Grundleistenmenüs](../../mfc/reference/media/vc4scc1.gif "Beispiel eines Grundleistenmenüs")

## <a name="rebar-control"></a>Bewehrungssteuerung

Unterstützung für Bewehrungssteuerelemente:

- Bildlisten.

- Nachrichtenverarbeitung.

- Benutzerdefinierte Zeichnungsfunktionalität.

- Eine Vielzahl von Steuerungsstilen zusätzlich zu Standardfensterstilen. Eine Liste dieser Stile finden Sie unter [Bewehrungssteuerungsstile](/windows/win32/Controls/rebar-control-styles) im Windows SDK.

Weitere Informationen finden Sie unter [Verwenden von CReBarCtrl](../../mfc/using-crebarctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>Anforderungen

**Header:** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a>CReBarCtrl::BeginDrag

Implementiert das Verhalten der Win32-RB_BEGINDRAG , wie im Windows SDK beschrieben. [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Nullbasierter Index des Bands, auf den sich der Drag-and-Drop-Vorgang auswirkt.

*dwPos*<br/>
Ein DWORD-Wert, der die Startmauskoordinaten enthält. Die horizontale Koordinate ist im LOWORD und die vertikale Koordinate im HIWORD enthalten. Wenn Sie (DWORD)-1 übergeben, verwendet das Bewehrungssteuerelement die Position der `GetMessage` Maus, wenn der Thread des Steuerelements das letzte Mal aufgerufen hat oder `PeekMessage`.

## <a name="crebarctrlcreate"></a><a name="create"></a>CReBarCtrl::Erstellen

Erstellt das Bewehrungssteuerelement und `CReBarCtrl` fügt es an das Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt die Kombination von Bewehrungssteuerungsstilen an, die auf das Steuerelement angewendet werden. Eine Liste der unterstützten Stile finden Sie unter [Bewehrungssteuerungsstile](/windows/win32/Controls/rebar-control-styles) im Windows SDK.

*Rect*<br/>
Ein Verweis auf ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) d. h. die Position und Größe des Bewehrungssteuerelements.

*pParentWnd*<br/>
Ein Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das übergeordnete Fenster des Bewehrungssteuerelements ist. Es darf nicht NULL sein.

*nID*<br/>
Gibt die Steuerungs-ID des Bewehrungssteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Erstellen Sie ein Bewehrungssteuerelement in zwei Schritten:

1. Rufen Sie [CReBarCtrl](#crebarctrl) auf, um ein `CReBarCtrl` Objekt zu erstellen.

1. Rufen Sie diese Memberfunktion auf, die das Windows-Bewehrungssteuerelement erstellt und an das `CReBarCtrl` Objekt anfügt.

Wenn Sie `Create`aufrufen, werden die allgemeinen Steuerelemente initialisiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a>CReBarCtrl::CreateEx

Erstellt ein Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CReBarCtrl` Objekt zu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwExStyle*<br/>
Gibt den erweiterten Stil des zu erstellenden Steuerelements an. Eine Liste der erweiterten Windows-Stile finden Sie im *dwExStyle-Parameter* für [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*dwStyle*<br/>
Gibt die Kombination von Bewehrungssteuerungsstilen an, die auf das Steuerelement angewendet werden. Eine Liste der unterstützten Stile finden Sie unter [Bewehrungssteuerungsstile](/windows/win32/Controls/rebar-control-styles) im Windows SDK.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Erstellen,](#create) um erweiterte Windows-Formatvorlagen anzuwenden, die durch das Erweiterte Windows-Stilvorwort **WS_EX_** angegeben werden.

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a>CReBarCtrl::CReBarCtrl

Erstellt ein `CReBarCtrl` -Objekt.

```
CReBarCtrl();
```

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CReBarCtrl::Create](#create).

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a>CReBarCtrl::DeleteBand

Implementiert das Verhalten der Win32-RB_DELETEBAND , wie im Windows SDK beschrieben. [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband)

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Nullbasierter Index des zu löschenden Bands.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Band erfolgreich gelöscht wurde; andernfalls Null.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a>CReBarCtrl::DragMove

Implementiert das Verhalten der Win32-RB_DRAGMOVE , wie im Windows SDK beschrieben. [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove)

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parameter

*dwPos*<br/>
Ein DWORD-Wert, der die neuen Mauskoordinaten enthält. Die horizontale Koordinate ist im LOWORD und die vertikale Koordinate im HIWORD enthalten. Wenn Sie (DWORD)-1 übergeben, verwendet das Bewehrungssteuerelement die Position der `GetMessage` Maus, wenn der Thread des Steuerelements das letzte Mal aufgerufen hat oder `PeekMessage`.

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a>CReBarCtrl::EndDrag

Implementiert das Verhalten der Win32-RB_ENDDRAG , wie im Windows SDK beschrieben. [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)

```
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a>CReBarCtrl::GetBandBorders

Implementiert das Verhalten der Win32-RB_GETBANDBORDERS , wie im Windows SDK beschrieben. [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders)

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Nullbasierter Index des Bands, für das die Rahmen abgerufen werden.

*Vr china*<br/>
Ein Zeiger auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Bandgrenzen empfängt. Wenn das Bewehrungssteuerelement den stil RBS_BANDBORDERS hat, erhält jedes Element dieser Struktur die Anzahl der Pixel auf der entsprechenden Seite des Bands, die den Rahmen bilden. Wenn das Bewehrungssteuerelement nicht über den RBS_BANDBORDERS-Stil verfügt, erhält nur das linke Element dieser Struktur gültige Informationen. Eine Beschreibung der Bewehrungssteuerungsstile finden Sie unter [Bewehrungssteuerungsstile](/windows/win32/Controls/rebar-control-styles) im Windows SDK.

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a>CReBarCtrl::GetBandCount

Implementiert das Verhalten der Win32-RB_GETBANDCOUNT , wie im Windows SDK beschrieben. [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount)

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der dem Steuerelement zugewiesenen Bänder.

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a>CReBarCtrl::GetBandInfo

Implementiert das Verhalten der Win32-RB_GETBANDINFO wie im Windows SDK beschrieben. [RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo)

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Nullbasierter Index des Bands, für das die Informationen abgerufen werden.

*prbbi*<br/>
Ein Zeiger auf eine [REBARBANDINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) um die Bandinformationen zu erhalten. Sie müssen `cbSize` den Member dieser `sizeof(REBARBANDINFO)` Struktur `fMask` auf die Elemente festlegen, die Sie abrufen möchten, und das Element auf die Elemente festlegen, die Sie abrufen möchten, bevor Sie diese Nachricht senden.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a>CReBarCtrl::GetBandMargins

Ruft die Ränder des Bands ab.

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>Parameter

*pMargins*<br/>
Ein Zeiger auf [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins)eine MARGINS-Struktur, die die Informationen empfängt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der [RB_GETBANDMARGINS](/windows/win32/Controls/rb-getbandmargins) Nachricht, wie im Windows SDK beschrieben.

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a>CReBarCtrl::GetBarHeight

Ruft die Höhe der Bewehrungsleiste ab.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>Rückgabewert

Wert, der die Höhe des Steuerelements in Pixel darstellt.

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a>CReBarCtrl::GetBarInfo

Implementiert das Verhalten der Win32-RB_GETBARINFO , wie im Windows SDK beschrieben. [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo)

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>Parameter

*prbi*<br/>
Ein Zeiger auf eine [REBARINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) die die Bewehrungssteuerungsinformationen empfängt. Sie müssen den *cbSize-Member* `sizeof(REBARINFO)` dieser Struktur auf festlegen, bevor Sie diese Nachricht senden.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a>CReBarCtrl::GetBkColor

Implementiert das Verhalten der Win32-RB_GETBKCOLOR , wie im Windows SDK beschrieben. [RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor)

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein COLORREF-Wert, der die aktuelle Standardhintergrundfarbe darstellt.

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a>CReBarCtrl::GetColorScheme

Ruft die [COLORSCHEME-Struktur](/windows/win32/api/commctrl/ns-commctrl-colorscheme) für das Bewehrungssteuerelement ab.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parameter

*lpcs*<br/>
Ein Zeiger auf eine [COLORSCHEME-Struktur,](/windows/win32/api/commctrl/ns-commctrl-colorscheme) wie im Windows SDK beschrieben.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `COLORSCHEME` Struktur enthält die Schaltflächenhervorhebungsfarbe und die Schaltflächenschattenfarbe.

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a>CReBarCtrl::GetDropTarget

Implementiert das Verhalten der Win32-RB_GETDROPTARGET , wie im Windows SDK beschrieben. [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine [IDropTarget-Schnittstelle.](/windows/win32/api/oleidl/nn-oleidl-idroptarget)

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CReBarCtrl::GetExtendedStyle

Ruft die erweiterten Stile des aktuellen Bewehrungssteuerelements ab.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Eine bitweise Kombination (OR) von Flags, die die erweiterten Stile angeben. Die möglichen Flaggen werden RBS_EX_SPLITTER und RBS_EX_TRANSPARENT. Weitere Informationen finden Sie im *dwMask-Parameter* der [CReBarCtrl::SetExtendedStyle-Methode.](#setextendedstyle)

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [RB_GETEXTENDEDSTYLE](/windows/win32/Controls/rb-dragmove) Nachricht, die im Windows SDK beschrieben wird.

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a>CReBarCtrl::GetImageList

Ruft `CImageList` das Objekt ab, das einem Bewehrungssteuerelement zugeordnet ist.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CImageList-Objekt.](../../mfc/reference/cimagelist-class.md) Gibt NULL zurück, wenn keine Bildliste für das Steuerelement festgelegt ist.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion verwendet Größen- und Maskeninformationen, die in der [REBARINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) gespeichert sind, wie im Windows SDK beschrieben.

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a>CReBarCtrl::GetPalette

Ruft die aktuelle Palette des Bewehrungssteuerelements ab.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CPalette-Objekt,](../../mfc/reference/cpalette-class.md) das die aktuelle Palette des Bewehrungssteuerelements angibt.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass `CPalette` diese Memberfunktion ein Objekt als Rückgabewert anstelle eines HPALETTE verwendet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a>CReBarCtrl::GetRect

Implementiert das Verhalten der Win32-RB_GETRECT , wie im Windows SDK beschrieben. [RB_GETRECT](/windows/win32/Controls/rb-getrect)

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Nullbasierter Index eines Bands im Bewehrungssteuerelement.

*Vr china*<br/>
Ein Zeiger auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Grenzen des Bewehrungsbandes empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a>CReBarCtrl::GetRowCount

Implementiert das Verhalten der Win32-RB_GETROWCOUNT , wie im Windows SDK beschrieben. [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount)

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>Rückgabewert

Ein UINT-Wert, der die Anzahl der Bandzeilen im Steuerelement darstellt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a>CReBarCtrl::GetRowHeight

Implementiert das Verhalten der Win32-RB_GETROWHEIGHT , wie im Windows SDK beschrieben. [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>Parameter

*uRow*<br/>
Nullbasierter Index des Bands, dessen Höhe abgerufen wird.

### <a name="return-value"></a>Rückgabewert

Ein UINT-Wert, der die Zeilenhöhe in Pixel darstellt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a>CReBarCtrl::GetTextColor

Implementiert das Verhalten der Win32-RB_GETTEXTCOLOR , wie im Windows SDK beschrieben. [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor)

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein COLORREF-Wert, der die aktuelle Standardtextfarbe darstellt.

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a>CReBarCtrl::GetToolTipps

Implementiert das Verhalten der Win32-RB_GETTOOLTIPS , wie im Windows SDK beschrieben. [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips)

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CToolTipCtrl-Objekt.](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass `GetToolTips` die MFC-Implementierung `CToolTipCtrl`von einen Zeiger auf eine zurückgibt, anstatt auf eine HWND.

## <a name="crebarctrlhittest"></a><a name="hittest"></a>CReBarCtrl::HitTest

Implementiert das Verhalten der Win32-RB_HITTEST , wie im Windows SDK beschrieben. [RB_HITTEST](/windows/win32/Controls/rb-hittest)

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>Parameter

*prbht*<br/>
Ein Zeiger auf eine [RBHITTESTINFO-Struktur.](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo) Vor dem Senden `pt` der Nachricht muss das Element dieser Struktur in Clientkoordinaten so initialisiert werden, dass es getestet wird.

### <a name="return-value"></a>Rückgabewert

Der Null-basierte Index des Bands am angegebenen Punkt oder -1, wenn sich kein Bewehrungsband am Punkt befand.

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a>CReBarCtrl::IDToIndex

Implementiert das Verhalten der Win32-RB_IDTOINDEX , wie im Windows SDK beschrieben. [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex)

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>Parameter

*uBandID*<br/>
Der anwendungsdefinierte Bezeichner des angegebenen `wID` Bands, der im Member der [REBARBANDINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) übergeben wird, wenn das Band eingefügt wird.

### <a name="return-value"></a>Rückgabewert

Der Null-basierte Bandindex, wenn er erfolgreich ist, oder -1 andernfalls. Wenn doppelte Bandindizes vorhanden sind, wird der erste zurückgegeben.

## <a name="crebarctrlinsertband"></a><a name="insertband"></a>CReBarCtrl::InsertBand

Implementiert das Verhalten der Win32-RB_INSERTBAND , wie im Windows SDK beschrieben. [RB_INSERTBAND](/windows/win32/Controls/rb-insertband)

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parameter

*uIndex*<br/>
Nullbasierter Index der Position, an der das Band eingefügt wird. Wenn Sie diesen Parameter auf -1 setzen, fügt das Steuerelement das neue Band an der letzten Position hinzu.

*prbbi*<br/>
Ein Zeiger auf eine [REBARBANDINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) die das einzufügende Band definiert. Sie müssen den *cbSize-Member* `sizeof(REBARBANDINFO)` dieser Struktur auf festlegen, bevor Sie diese Funktion aufrufen.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a>CReBarCtrl::MaximizeBand

Ändert die Größe eines Bands in einem Bewehrungssteuerelement auf seine größte Größe.

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Zero-basierter Index des zu maximierenden Bands.

### <a name="remarks"></a>Bemerkungen

Implementiert das Verhalten der Win32-RB_MAXIMIZEBAND mit [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) `fIdeal` der Einstellung 0, wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a>CReBarCtrl::MinimizeBand

Ändert die Größe eines Bands in einem Bewehrungssteuerelement auf die kleinste Größe.

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Nullbasierter Index des zu minimierenden Bands.

### <a name="remarks"></a>Bemerkungen

Implementiert das Verhalten der Win32-RB_MINIMIZEBAND , wie im Windows SDK beschrieben. [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a>CReBarCtrl::MoveBand

Implementiert das Verhalten der Win32-RB_MOVEBAND , wie im Windows SDK beschrieben. [RB_MOVEBAND](/windows/win32/Controls/rb-moveband)

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>Parameter

*uAus*<br/>
Nullbasierter Index des zu verschiebenden Bands.

*Uto*<br/>
Nullbasierter Index der neuen Bandposition. Dieser Parameterwert darf niemals größer sein als die Anzahl der Bänder minus eins. Um die Anzahl der Bänder zu erhalten, rufen Sie [GetBandCount](#getbandcount)an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a>CReBarCtrl::PushChevron

Implementiert das Verhalten der Win32-RB_PUSHCHEVRON , wie im Windows SDK beschrieben. [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Null-basierter Index der Band, deren Chevron geschoben werden soll.

*lAppValue*<br/>
Ein anwendungsdefinierter 32-Bit-Wert. Siehe *lAppValue* in [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron) im Windows SDK.

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a>CReBarCtrl::RestoreBand

Ändert die Größe eines Bands in einem Bewehrungssteuerelement auf seine ideale Größe.

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Zero-basierter Index des zu maximierenden Bands.

### <a name="remarks"></a>Bemerkungen

Implementiert das Verhalten der Win32-RB_MAXIMIZEBAND mit [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) `fIdeal` satz 1, wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a>CReBarCtrl::SetBandInfo

Implementiert das Verhalten der Win32-RB_SETBANDINFO , wie im Windows SDK beschrieben. [RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo)

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Nullbasierter Index des Bands, um die neuen Einstellungen zu erhalten.

*prbbi*<br/>
Zeiger auf eine [REBARBANDINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) die das einzufügende Band definiert. Sie müssen `cbSize` den Member dieser `sizeof(REBARBANDINFO)` Struktur auf festlegen, bevor Sie diese Nachricht senden.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a>CReBarCtrl::SetBandWidth

Legt die Breite des angegebenen angedockten Bandes im aktuellen Bewehrungssteuerelement fest.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*uBand*|[in] Nullbasierter Index eines Bewehrungsbandes.|
|*cxWidth*|[in] Neue Breite des Bewehrungsbandes in Pixel.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [RB_SETBANDWIDTH](/windows/win32/Controls/rb-setbandwidth) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_rebar`die Variable , definiert, die für den Zugriff auf das aktuelle Bewehrungssteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird festgelegt, dass jedes Bewehrungsband die gleiche Breite aufweist.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a>CReBarCtrl::SetBarInfo

Implementiert das Verhalten der Win32-RB_SETBARINFO , wie im Windows SDK beschrieben. [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>Parameter

*prbi*<br/>
Ein Zeiger auf eine [REBARINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) die die festzulegenden Informationen enthält. Sie müssen `cbSize` den Member dieser `sizeof(REBARINFO)` Struktur auf festlegen, bevor Sie diese Nachricht senden.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a>CReBarCtrl::SetBkColor

Implementiert das Verhalten der Win32-Meldung [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor), wie im Windows SDK beschrieben.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parameter

*Clr*<br/>
Der COLORREF-Wert, der die neue Standardhintergrundfarbe darstellt.

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die vorherige Standardhintergrundfarbe darstellt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Festlegen der Hintergrundfarbe und zum Festlegen der Standardeinstellung finden Sie in diesem Thema.

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a>CReBarCtrl::SetColorScheme

Legt das Farbschema für die Schaltflächen auf einem Bewehrungssteuerelement fest.

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parameter

*lpcs*<br/>
Ein Zeiger auf eine [COLORSCHEME-Struktur,](/windows/win32/api/commctrl/ns-commctrl-colorscheme) wie im Windows SDK beschrieben.

### <a name="remarks"></a>Bemerkungen

Die `COLORSCHEME` Struktur enthält sowohl die Schaltflächenhervorhebungsfarbe als auch die Schaltflächenschattenfarbe.

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CReBarCtrl::SetExtendedStyle

Legt die erweiterten Stile für das aktuelle Bewehrungssteuerelement fest.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*dwMask*|[in] Eine bitweise Kombination (OR) von Flags, die angeben, welche Flags im *parameter dwStyleEx* angewendet werden. Verwenden Sie einen oder mehrere der folgenden Werte:<br /><br /> RBS_EX_SPLITTER: Zeigen Sie standardmäßig den Splitter unten im horizontalen Modus und rechts im vertikalen Modus an.<br /><br /> RBS_EX_TRANSPARENT: Leiten Sie die [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) Nachricht an das übergeordnete Fenster weiter.|
|*dwStyleEx*|[in] Eine bitweise Kombination (OR) von Flags, die die anzuwendenden Stile angeben. Um einen Stil festzulegen, geben Sie dasselbe Flag an, das im *Parameter dwMask* verwendet wird. Um einen Stil zurückzusetzen, geben Sie binäre Null an.|

### <a name="return-value"></a>Rückgabewert

Der vorherige erweiterte Stil.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle) Nachricht, die im Windows SDK beschrieben wird.

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a>CReBarCtrl::SetImageList

Weist einem Bewehrungssteuerelement eine Bildliste zu.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parameter

*pImageList*<br/>
Ein Zeiger auf ein [CImageList-Objekt,](../../mfc/reference/cimagelist-class.md) das die Bildliste enthält, die dem Bewehrungssteuerelement zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

## <a name="crebarctrlsetowner"></a><a name="setowner"></a>CReBarCtrl::SetOwner

Implementiert das Verhalten der Win32-RB_SETPARENT , wie im Windows SDK beschrieben. [RB_SETPARENT](/windows/win32/Controls/rb-setparent)

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf `CWnd` ein Objekt, das als Besitzer des Bewehrungssteuerelements festgelegt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das der aktuelle Besitzer des Bewehrungssteuerelements ist.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass diese Memberfunktion Zeiger auf `CWnd` Objekte sowohl für den aktuellen als auch für den ausgewählten Besitzer des Bewehrungssteuerelements verwendet, anstatt auf Fenster zu verarbeiten.

> [!NOTE]
> Diese Memberfunktion ändert nicht das tatsächliche übergeordnete Element, das beim Erstellen des Steuerelements festgelegt wurde. Stattdessen werden Benachrichtigungen an das von Ihnen angegebene Fenster gesendet.

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a>CReBarCtrl::SetPalette

Implementiert das Verhalten der Win32-RB_SETPALETTE , wie im Windows SDK beschrieben. [RB_SETPALETTE](/windows/win32/Controls/rb-setpalette)

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>Parameter

*hPal*<br/>
Eine HPALETTE, die die neue Palette angibt, die das Bewehrungssteuerelement verwendet.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CPalette-Objekt,](../../mfc/reference/cpalette-class.md) das die vorherige Palette des Bewehrungssteuerelements angibt.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass `CPalette` diese Memberfunktion ein Objekt als Rückgabewert anstelle eines HPALETTE verwendet.

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a>CReBarCtrl::SetTextColor

Implementiert das Verhalten der Win32-RB_SETTEXTCOLOR , wie im Windows SDK beschrieben. [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parameter

*Clr*<br/>
Ein COLORREF-Wert, der die `CReBarCtrl` neue Textfarbe im Objekt darstellt.

### <a name="return-value"></a>Rückgabewert

Der [COLORREF-Wert,](/windows/win32/gdi/colorref) der die `CReBarCtrl` vorherige Textfarbe darstellt, die dem Objekt zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Sie wird bereitgestellt, um die Flexibilität der Textfarbe in einem Bewehrungssteuerelement zu unterstützen.

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a>CReBarCtrl::SetToolTips

Ordnet ein Werkzeugspitzensteuerelement einem Bewehrungssteuerelement zu.

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>Parameter

*pToolTip*<br/>
Ein Zeiger auf ein [CToolTipCtrl-Objekt](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Bemerkungen

Sie müssen `CToolTipCtrl` das Objekt zerstören, wenn Sie damit fertig sind.

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CReBarCtrl::SetWindowTheme

Legt den visuellen Stil des Bewehrungssteuerelements fest.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parameter

*pszSubAppName*<br/>
Ein Zeiger auf eine Unicode-Zeichenfolge, die den zu setzenden visuellen Bewehrungsstil enthält.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert wird nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der [RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme) Nachricht, wie im Windows SDK beschrieben.

## <a name="crebarctrlshowband"></a><a name="showband"></a>CReBarCtrl::ShowBand

Implementiert das Verhalten der Win32-RB_SHOWBAND , wie im Windows SDK beschrieben. [RB_SHOWBAND](/windows/win32/Controls/rb-showband)

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>Parameter

*uBand*<br/>
Nullbasierter Index eines Bands im Bewehrungssteuerelement.

*fShow*<br/>
Gibt an, ob das Band angezeigt oder ausgeblendet werden soll. Wenn dieser Wert TRUE ist, wird das Band angezeigt. Andernfalls wird die Band ausgeblendet.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a>CReBarCtrl::SizeToRect

Implementiert das Verhalten der Win32-RB_SIZETORECT , wie im Windows SDK beschrieben. [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect)

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Ein Verweis auf ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das das Rechteck angibt, auf das das Bewehrungssteuerelement angepasst werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass `CRect` diese Memberfunktion ein Objekt `RECT` als Parameter und nicht als Struktur verwendet.

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
