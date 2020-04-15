---
title: CListBox-Klasse
description: Eine Beschreibung der MFC CListBox-Klasse und ihrer Memberfunktionen.
ms.date: 01/22/2020
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
ms.openlocfilehash: 5bc66ab2775ebb9023c65c9decae205604c978c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372228"
---
# <a name="clistbox-class"></a>CListBox-Klasse

Stellt die Funktionalität eines Windows-Listenfelds bereit.

## <a name="syntax"></a>Syntax

```
class CListBox : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Erstellt ein `CListBox`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CListBox::AddString](#addstring)|Fügt einem Listenfeld eine Zeichenfolge hinzu.|
|[CListBox::CharToItem](#chartoitem)|Überschreiben, um benutzerdefinierte WM_CHAR Für Besitzer-Zeichnungslistenfelder bereitzustellen, die keine Zeichenfolgen haben.|
|[CListBox::CompareItem](#compareitem)|Wird vom Framework aufgerufen, um die Position eines neuen Elements in einem sortierten Listenfeld für die Besitzerzeichnung zu bestimmen.|
|[CListBox::Erstellen](#create)|Erstellt das Windows-Listenfeld und `CListBox` fügt es an das Objekt an.|
|[CListBox::DeleteItem](#deleteitem)|Wird vom Framework aufgerufen, wenn der Benutzer ein Element aus einem Listenfeld für besitzerzeichnenlöscht.|
|[CListBox::DeleteString](#deletestring)|Löscht eine Zeichenfolge aus einem Listenfeld.|
|[CListBox::Dir](#dir)|Fügt Dateinamen, Laufwerke oder beides aus dem aktuellen Verzeichnis zu einem Listenfeld hinzu.|
|[CListBox::DrawItem](#drawitem)|Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines Listenfelds für die Besitzerzeichnung ändert.|
|[CListBox::FindString](#findstring)|Sucht nach einer Zeichenfolge in einem Listenfeld.|
|[CListBox::FindStringExact](#findstringexact)|Sucht die erste Listenfeldzeichenfolge, die einer angegebenen Zeichenfolge entspricht.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Ruft den nullbasierten Index des aktuellen Ankerelements in einem Listenfeld ab.|
|[CListBox::GetCaretIndex](#getcaretindex)|Bestimmt den Index des Elements mit dem Fokusrechteck in einem Listenfeld mit mehreren Auswahlen.|
|[CListBox::GetCount](#getcount)|Gibt die Anzahl der Zeichenfolgen in einem Listenfeld zurück.|
|[CListBox::GetCurSel](#getcursel)|Gibt den nullbasierten Index der aktuell ausgewählten Zeichenfolge in einem Listenfeld zurück.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Gibt die Breite in Pixel zurück, in der ein Listenfeld horizontal gescrollt werden kann.|
|[CListBox::GetItemData](#getitemdata)|Gibt einen Wert zurück, der dem Listenfeldelement zugeordnet ist.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Gibt einen Zeiger auf ein Listenfeldelement zurück.|
|[CListBox::GetItemHeight](#getitemheight)|Bestimmt die Höhe von Elementen in einem Listenfeld.|
|[CListBox::GetItemRect](#getitemrect)|Gibt das umgrenzende Rechteck des Listenfeldelements zurück, wie es derzeit angezeigt wird.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Ruft die Anzahl der Elemente pro Spalte ab.|
|[CListBox::GetLocale](#getlocale)|Ruft den Gebietsschemabezeichner für ein Listenfeld ab.|
|[CListBox::GetSel](#getsel)|Gibt den Auswahlstatus eines Listenfeldelements zurück.|
|[CListBox::GetSelCount](#getselcount)|Gibt die Anzahl der Zeichenfolgen zurück, die derzeit in einem Listenfeld mit mehreren Auswahlen ausgewählt sind.|
|[CListBox::GetSelItems](#getselitems)|Gibt die Indizes der Zeichenfolgen zurück, die derzeit in einem Listenfeld ausgewählt sind.|
|[CListBox::GetText](#gettext)|Kopiert ein Listenfeldelement in einen Puffer.|
|[CListBox::GetTextLen](#gettextlen)|Gibt die Länge in Bytes eines Listenfeldelements zurück.|
|[CListBox::GetTopIndex](#gettopindex)|Gibt den Index der ersten sichtbaren Zeichenfolge in einem Listenfeld zurück.|
|[CListBox::InitStorage](#initstorage)|Ordnet Speicherblöcke für Listenfeldelemente und Zeichenfolgen vorab zu.|
|[CListBox::InsertString](#insertstring)|Fügt eine Zeichenfolge an einer bestimmten Position in einem Listenfeld ein.|
|[CListBox::ItemFromPoint](#itemfrompoint)|Gibt den Index des Listenfeldelements zurück, das einem Punkt am nächsten liegt.|
|[CListBox::MeasureItem](#measureitem)|Wird vom Framework aufgerufen, wenn ein Listenfeld für besitzerzeichnenerstellt wird, um Listenfelddimensionen zu bestimmen.|
|[CListBox::ResetContent](#resetcontent)|Löscht alle Einträge aus einem Listenfeld.|
|[CListBox::SelectString](#selectstring)|Sucht eine Zeichenfolge in einem Listenfeld mit einer Auswahl und wählt sie aus.|
|[CListBox::SelItemRange](#selitemrange)|Wählt einen Zeichenfolgenbereich in einem Listenfeld mit mehreren Auswahlen aus oder untergibt diese.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Legt den Anker in einem Listenfeld mit mehreren Auswahlen fest, um eine erweiterte Auswahl zu beginnen.|
|[CListBox::SetCaretIndex](#setcaretindex)|Legt das Fokusrechteck auf das Element am angegebenen Index in einem Listenfeld mit mehreren Auswahlen fest.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Legt die Spaltenbreite eines mehrspaltigen Listenfelds fest.|
|[CListBox::SetCurSel](#setcursel)|Wählt eine Listenfeldzeichenfolge aus.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Legt die Breite in Pixel fest, in der ein Listenfeld horizontal gescrollt werden kann.|
|[CListBox::SetItemData](#setitemdata)|Legt einen Wert fest, der dem Listenfeldelement zugeordnet ist.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Legt einen Zeiger auf das Listenfeldelement fest.|
|[CListBox::SetItemHeight](#setitemheight)|Legt die Höhe von Elementen in einem Listenfeld fest.|
|[CListBox::SetLocale](#setlocale)|Legt den Gebietsschemabezeichner für ein Listenfeld fest.|
|[CListBox::SetSel](#setsel)|Wählt ein Listenfeldelement in einem Listenfeld mit mehreren Auswahlen aus oder wird die Auswahl.|
|[CListBox::SetTabStops](#settabstops)|Legt die Tabstopppositionen in einem Listenfeld fest.|
|[CListBox::SetTopIndex](#settopindex)|Legt den nullbasierten Index der ersten sichtbaren Zeichenfolge in einem Listenfeld fest.|
|[CListBox::VKeyToItem](#vkeytoitem)|Überschreiben, um benutzerdefinierte WM_KEYDOWN Für Listenfelder mit dem Stilsatz LBS_WANTKEYBOARDINPUT bereitzustellen.|

## <a name="remarks"></a>Bemerkungen

In einem Listenfeld wird eine Liste von Elementen angezeigt, z. B. Dateinamen, die der Benutzer anzeigen und auswählen kann.

In einem Listenfeld mit einer Auswahl kann der Benutzer nur ein Element auswählen. In einem Listenfeld mit mehreren Auswahlmöglichkeiten kann ein Bereich von Elementen ausgewählt werden. Wenn der Benutzer ein Element auswählt, wird es hervorgehoben, und das Listenfeld sendet eine Benachrichtigung an das übergeordnete Fenster.

Sie können ein Listenfeld entweder aus einer Dialogfeldvorlage oder direkt im Code erstellen. Um es direkt zu `CListBox` erstellen, erstellen Sie das Objekt, und rufen Sie dann `CListBox` die Memberfunktion [Erstellen](#create) auf, um das Windows-Listenfeldsteuerelement zu erstellen und es an das Objekt anzufügen. Um ein Listenfeld in einer Dialogfeldvorlage zu verwenden, deklarieren `DDX_Control` Sie eine Listenfeldvariable `DoDataExchange` in der Dialogfeldklasse, und verwenden Sie dann in der Funktion der Dialogfeldklasse die Membervariable mit dem Steuerelement. (Dies geschieht automatisch für Sie, wenn Sie Ihrer Dialogfeldklasse eine Steuerelementvariable hinzufügen.)

Die Konstruktion kann ein einstufiger Prozess `CListBox`in einer Klasse sein, die von abgeleitet ist. Schreiben Sie einen Konstruktor für `Create` die abgeleitete Klasse und rufen Sie aus dem Konstruktor heraus.

Wenn Sie Windows-Benachrichtigungen verarbeiten möchten, die von einem Listenfeld an das übergeordnete Element gesendet werden (normalerweise eine von [CDialog](../../mfc/reference/cdialog-class.md)abgeleitete Klasse), fügen Sie der übergeordneten Klasse für jede Nachricht einen Nachrichtenzuordnungseintrag und eine Message-Handler-Memberfunktion hinzu.

Jeder Nachrichtenzuordnungseintrag hat die folgende Form:

`ON_Notification( id, memberFxn )`

wobei `id` die untergeordnete Fenster-ID des Listenfeldsteuerelements `memberFxn` angegeben wird, das die Benachrichtigung sendet, und der Name der übergeordneten Memberfunktion ist, die Sie geschrieben haben, um die Benachrichtigung zu behandeln.

Der Funktionsprototyp des Übergeordneten ist wie folgt:

`afx_msg void memberFxn( );`

Im Folgenden finden Sie eine Liste der potenziellen Nachrichtenzuordnungseinträge und eine Beschreibung der Fälle, in denen sie an das übergeordnete Element gesendet werden:

- ON_LBN_DBLCLK Der Benutzer klickt in einem Listenfeld auf eine Zeichenfolge. Nur ein Listenfeld mit dem [Format LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) sendet diese Benachrichtigung.

- ON_LBN_ERRSPACE Das Listenfeld kann nicht genügend Arbeitsspeicher zuweisen, um die Anforderung zu erfüllen.

- ON_LBN_KILLFOCUS Das Listenfeld verliert den Eingabefokus.

- ON_LBN_SELCANCEL Die aktuelle Listenfeldauswahl wird abgebrochen. Diese Nachricht wird nur gesendet, wenn ein Listenfeld den LBS_NOTIFY-Stil hat.

- ON_LBN_SELCHANGE Die Auswahl im Listenfeld hat sich geändert. Diese Benachrichtigung wird nicht gesendet, wenn die Auswahl durch die [Memberfunktion CListBox::SetCurSel](#setcursel) geändert wird. Diese Benachrichtigung gilt nur für ein Listenfeld mit dem Stil LBS_NOTIFY. Die LBN_SELCHANGE Benachrichtigungwirdwirdbenachrichtigung wird für ein Listenfeld mit mehreren Auswahlen gesendet, wenn der Benutzer eine Pfeiltaste drückt, auch wenn sich die Auswahl nicht ändert.

- ON_LBN_SETFOCUS Das Listenfeld empfängt den Eingabefokus.

- ON_WM_CHARTOITEM Ein Listenfeld für die Besitzerzeichnung ohne Zeichenfolgen erhält eine WM_CHAR Nachricht.

- ON_WM_VKEYTOITEM Ein Listenfeld mit dem Stil LBS_WANTKEYBOARDINPUT erhält eine WM_KEYDOWN Nachricht.

Wenn Sie `CListBox` ein Objekt in einem Dialogfeld (über eine Dialogfeldressource) erstellen, wird das `CListBox` Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie `CListBox` ein Objekt in einem Fenster erstellen, müssen Sie das `CListBox` Objekt möglicherweise zerstören. Wenn Sie `CListBox` das Objekt auf dem Stapel erstellen, wird es automatisch zerstört. Wenn Sie `CListBox` das Objekt auf dem Heap mithilfe der **neuen** Funktion erstellen, müssen Sie **das Objekt** löschen aufrufen, um es zu zerstören, wenn der Benutzer das übergeordnete Fenster schließt.

Wenn Sie Speicher im `CListBox` Objekt zuweisen, `CListBox` überschreiben Sie den Destruktor, um die Zuordnung zu entsorgen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="clistboxaddstring"></a><a name="addstring"></a>CListBox::AddString

Fügt einem Listenfeld eine Zeichenfolge hinzu.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parameter

*lpszItem*<br/>
Zeigt auf die null-terminierte Zeichenfolge, die hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index für die Zeichenfolge im Listenfeld. Der Rückgabewert ist LB_ERR, wenn ein Fehler auftritt. Der Rückgabewert ist LB_ERRSPACE, wenn nicht genügend Speicherplatz zum Speichern der neuen Zeichenfolge verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Wenn das Listenfeld nicht mit dem [Stil LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) erstellt wurde, wird die Zeichenfolge am Ende der Liste hinzugefügt. Andernfalls wird die Zeichenfolge in die Liste eingefügt, und die Liste wird sortiert. Wenn das Listenfeld mit dem Stil LBS_SORT, nicht aber mit dem [LBS_HASSTRINGS-Stil](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) `CompareItem` erstellt wurde, sortiert das Framework die Liste nach einem oder mehreren Aufrufen der Memberfunktion.

Verwenden Sie [InsertString,](#insertstring) um eine Zeichenfolge an einer bestimmten Position im Listenfeld einzufügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

## <a name="clistboxchartoitem"></a><a name="chartoitem"></a>CListBox::CharToItem

Wird vom Framework aufgerufen, wenn das übergeordnete Fenster des Listenfelds eine WM_CHARTOITEM Nachricht aus dem Listenfeld empfängt.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parameter

*nKey*<br/>
Der ANSI-Code des Zeichens, das der Benutzer eingegeben hat.

*nIndex*<br/>
Die aktuelle Position der Listenbox-Pflege.

### <a name="return-value"></a>Rückgabewert

Gibt - 1 oder - 2 für keine weitere Aktion oder eine nicht negative Zahl zurück, um einen Index eines Listenfeldelements anzugeben, auf dem die Standardaktion für den Tastenanschlag ausgeführt werden soll. Die Standardimplementierung gibt zurück - 1.

### <a name="remarks"></a>Bemerkungen

Die WM_CHARTOITEM Nachricht wird vom Listenfeld gesendet, wenn eine WM_CHAR Nachricht empfangen wird, jedoch nur, wenn das Listenfeld alle folgenden Kriterien erfüllt:

- Ist ein Listenfeld für die Besitzerzeichnung.

- Der [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil ist nicht festgelegt.

- Hat mindestens ein Element.

Sie sollten diese Funktion niemals selbst aufrufen. Überschreiben Sie diese Funktion, um Ihre eigene benutzerdefinierte Behandlung von Tastaturnachrichten bereitzustellen.

In der Außerkraftsetzung müssen Sie einen Wert zurückgeben, um dem Framework mitzuteilen, welche Aktion Sie ausgeführt haben. Ein Rückgabewert von - 1 oder - 2 gibt an, dass Sie alle Aspekte der Auswahl des Elements behandelt haben und keine weiteren Aktionen durch das Listenfeld erfordern. Vor der Rückkehr - 1 oder - 2, können Sie die Auswahl einstellen oder die Einseroder verschieben. Um die Auswahl festzulegen, verwenden Sie [SetCurSel](#setcursel) oder [SetSel](#setsel). Um die Einserwart zu verschieben, verwenden Sie [SetCaretIndex](#setcaretindex).

Ein Rückgabewert von 0 oder höher gibt den Index eines Elements im Listenfeld an und gibt an, dass das Listenfeld die Standardaktion für den Tastenanschlag für das angegebene Element ausführen soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

## <a name="clistboxclistbox"></a><a name="clistbox"></a>CListBox::CListBox

Erstellt ein `CListBox`-Objekt.

```
CListBox();
```

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CListBox` ein Objekt in zwei Schritten. Rufen Sie zunächst `ClistBox` den Konstruktor auf, und rufen Sie dann `Create`auf, `CListBox`das Windows-Listenfeld initialisiert und an die anfügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

## <a name="clistboxcompareitem"></a><a name="compareitem"></a>CListBox::CompareItem

Wird vom Framework aufgerufen, um die relative Position eines neuen Elements in einem sortierten Listenfeld für die Besitzerzeichnung zu bestimmen.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parameter

*lpCompareItemStruct*<br/>
Ein langer Zeiger `COMPAREITEMSTRUCT` auf eine Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt die relative Position der beiden elemente an, die in der [COMPAREITEMSTRUCT-Struktur](/windows/win32/api/winuser/ns-winuser-compareitemstruct) beschrieben werden. Dabei kann es sich um einen der folgenden Werte erfreuen:

|Wert|Bedeutung|
|-----------|-------------|
|-1|Artikel 1 sortiert vor Artikel 2.|
|0|Artikel 1 und Artikel 2 sortieren die gleiche.|
|1|Artikel 1 sortiert nach Artikel 2.|

Eine Beschreibung der `COMPAREITEMSTRUCT` Struktur finden Sie unter [CWnd::OnCompareItem.](../../mfc/reference/cwnd-class.md#oncompareitem)

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Memberfunktion nichts aus. Wenn Sie ein Listenfeld für die Besitzerzeichnung mit dem Format LBS_SORT erstellen, müssen Sie diese Memberfunktion überschreiben, um das Framework beim Sortieren neuer Elemente zu unterstützen, die dem Listenfeld hinzugefügt wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

## <a name="clistboxcreate"></a><a name="create"></a>CListBox::Erstellen

Erstellt das Windows-Listenfeld und `CListBox` fügt es an das Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Listenfelds an. Wenden Sie eine beliebige Kombination von [Listenfeldstilen](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) auf das Feld an.

*Rect*<br/>
Gibt die Größe und Position des Listenfelds an. Kann entweder `CRect` ein Objekt `RECT` oder eine Struktur sein.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Listenfelds (in der Regel ein Objekt) `CDialog` an. Es darf nicht NULL sein.

*nID*<br/>
Gibt die Steuerelement-ID des Listenfelds an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CListBox` ein Objekt in zwei Schritten. Rufen Sie zunächst den Konstruktor auf, und rufen Sie dann `Create`auf, `CListBox` das Windows-Listenfeld initialisiert und an das Objekt anfügt.

Bei `Create` der Ausführung sendet Windows die [Nachrichten WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate) [, WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)und [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) Nachrichten an das Listenfeldsteuerelement.

Diese Nachrichten werden standardmäßig von den Memberfunktionen [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)und `CWnd` [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) in der Basisklasse verarbeitet. Um die Standardnachrichtenbehandlung zu erweitern, `CListBox`leiten Sie eine Klasse von ab , fügen Sie der neuen Klasse eine Nachrichtenzuordnung hinzu, und überschreiben Sie die vorherigen Message-Handler-Memberfunktionen. Überschreiben `OnCreate`Sie z. B., um die erforderliche Initialisierung für eine neue Klasse durchzuführen.

Wenden Sie die folgenden [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein Listenfeldsteuerelement an.

- WS_CHILD Immer

- WS_VISIBLE In der Regel

- WS_DISABLED Selten

- WS_VSCROLL So fügen Sie eine vertikale Bildlaufleiste hinzu

- WS_HSCROLL So fügen Sie eine horizontale Bildlaufleiste hinzu

- WS_GROUP Zu Gruppensteuerelementen

- WS_TABSTOP So lassen Sie das Tabing auf dieses Steuerelement zu

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

## <a name="clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox::DeleteItem

Wird vom Framework aufgerufen, wenn der Benutzer ein `CListBox` Element aus einem Besitzerzeichnungsobjekt löscht oder das Listenfeld zerstört.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDeleteItemStruct*<br/>
Ein langer Zeiger auf eine Windows [DELETEITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) die Informationen zum gelöschten Element enthält.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um bei Bedarf ein Listenfeld für besitzerzeichnen neu zu zeichnen.

Eine Beschreibung der `DELETEITEMSTRUCT` Struktur finden Sie unter [CWnd::OnDeleteItem.](../../mfc/reference/cwnd-class.md#ondeleteitem)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

## <a name="clistboxdeletestring"></a><a name="deletestring"></a>CListBox::DeleteString

Löscht das Element in Position *nIndex* aus dem Listenfeld.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index der zu löschenden Zeichenfolge an.

### <a name="return-value"></a>Rückgabewert

Eine Anzahl der Inseiten, die in der Liste verbleiben. Der Rückgabewert ist LB_ERR, wenn *nIndex* einen Index angibt, der größer als die Anzahl der Elemente in der Liste ist.

### <a name="remarks"></a>Bemerkungen

Alle Elemente, die *nach nIndex* folgen, bewegen sich nun um eine Position nach unten. Wenn z. B. ein Listenfeld zwei Elemente enthält, führt das Löschen des ersten Elements dazu, dass sich das verbleibende Element jetzt an der ersten Position befindet. *nIndex*=0 für das Element an der ersten Position.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

## <a name="clistboxdir"></a><a name="dir"></a>CListBox::Dir

Fügt eine Liste von Dateinamen, Laufwerken oder beides zu einem Listenfeld hinzu.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parameter

*Attr*<br/>
Kann eine beliebige Kombination der unter `CFile::GetStatu` [s](../../mfc/reference/cfile-class.md#getstatus)beschriebenen **Enumerumwerte** oder eine beliebige Kombination der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|0x0000|Die Datei kann aus gelesen oder in die Datei geschrieben werden.|
|0x0001|Die Datei kann gelesen, aber nicht geschrieben werden.|
|0x0002|Die Datei ist ausgeblendet und wird nicht in einer Verzeichnisliste angezeigt.|
|0x0004|Datei ist eine Systemdatei.|
|0x0010|Der von *lpszWildCard* angegebene Name gibt ein Verzeichnis an.|
|0x0020|Die Datei wurde archiviert.|
|0x4000|Schließen Sie alle Laufwerke ein, die dem von *lpszWildCard*angegebenen Namen entsprechen.|
|0x8000|Exklusive Flagge. Wenn das exklusive Flag festgelegt ist, werden nur Dateien des angegebenen Typs aufgelistet. Andernfalls werden Dateien des angegebenen Typs zusätzlich zu "normalen" Dateien aufgelistet.|

*lpszWildCard*<br/>
Zeigt auf eine Dateispezifikationszeichenfolge. Die Zeichenfolge kann Platzhalter enthalten (z. B. *.\*).

### <a name="return-value"></a>Rückgabewert

Der Null-basierte Index des letzten Dateinamens, der der Liste hinzugefügt wurde. Der Rückgabewert ist LB_ERR, wenn ein Fehler auftritt. Der Rückgabewert ist LB_ERRSPACE, wenn nicht genügend Speicherplatz zum Speichern der neuen Zeichenfolgen verfügbar ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

## <a name="clistboxdrawitem"></a><a name="drawitem"></a>CListBox::DrawItem

Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines Listenfelds für die Besitzerzeichnung ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein langer Zeiger auf eine [DRAWITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) die Informationen über den erforderlichen Zeichnungstyp enthält.

### <a name="remarks"></a>Bemerkungen

Die `itemAction` `itemState` und die `DRAWITEMSTRUCT` Elemente der Struktur definieren die Zeichnungsaktion, die ausgeführt werden soll.

Standardmäßig führt diese Memberfunktion nichts aus. Überschreiben Sie diese Memberfunktion, um `CListBox` die Zeichnung für ein Besitzerzeichnungsobjekt zu implementieren. Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den in *lpDrawItemStruct* bereitgestellten Anzeigekontext ausgewählt wurden, bevor diese Memberfunktion beendet wird.

Eine Beschreibung der `DRAWITEMSTRUCT` Struktur finden Sie unter [CWnd::OnDrawItem.](../../mfc/reference/cwnd-class.md#ondrawitem)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

## <a name="clistboxfindstring"></a><a name="findstring"></a>CListBox::FindString

Sucht die erste Zeichenfolge in einem Listenfeld, das das angegebene Präfix enthält, ohne die Listenfeldauswahl zu ändern.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parameter

*nStartAfter*<br/>
Enthält den nullbasierten Index des Elements vor dem ersten zu durchsuchenden Element. Wenn die Suche am Ende des Listenfelds angelangt ist, wird sie vom oberen Rand des Listenfelds zurück zu dem von *nStartAfter*angegebenen Element fortgesetzt. Wenn *nStartAfter* -1 ist, wird das gesamte Listenfeld von Anfang an durchsucht.

*lpszItem*<br/>
Verweist auf die null-terminierte Zeichenfolge, die das Präfix enthält, nach dem gesucht werden soll. Die Suche ist großfliegt, daher kann diese Zeichenfolge eine beliebige Kombination aus Groß- und Kleinbuchstaben enthalten.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des übereinstimmenden Elements oder LB_ERR, wenn die Suche nicht erfolgreich war.

### <a name="remarks"></a>Bemerkungen

Verwenden [SelectString](#selectstring) Sie die SelectString-Memberfunktion, um eine Zeichenfolge zu suchen und auszuwählen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

## <a name="clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox::FindStringExact

Sucht die erste List-Box-Zeichenfolge, die mit der in *lpszFind*angegebenen Zeichenfolge übereinstimmt.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parameter

*nIndexStart*<br/>
Gibt den nullbasierten Index des Elements vor dem ersten zu durchsuchenden Element an. Wenn die Suche am Ende des Listenfelds angelangt ist, wird sie vom oberen Rand des Listenfelds zurück zu dem von *nIndexStart*angegebenen Element fortgesetzt. Wenn *nIndexStart* -1 ist, wird das gesamte Listenfeld von Anfang an durchsucht.

*lpszFind*<br/>
Zeigt auf die null-terminierte Zeichenfolge, nach der gesucht werden soll. Diese Zeichenfolge kann einen vollständigen Dateinamen enthalten, einschließlich der Erweiterung. Bei der Suche wird die Groß-/Kleinschreibung nicht beachtet, sodass die Zeichenfolge eine beliebige Kombination aus Groß- und Kleinbuchstaben enthalten kann.

### <a name="return-value"></a>Rückgabewert

Der Index des übereinstimmenden Elements oder LB_ERR, wenn die Suche nicht erfolgreich war.

### <a name="remarks"></a>Bemerkungen

Wenn das Listenfeld mit einem Besitzerzeichnungsstil, jedoch `FindStringExact` ohne [LBS_HASSTRINGS-Stil](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) erstellt wurde, versucht die Memberfunktion, den Doppelwortwert mit dem Wert von *lpszFind*abzugleichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

## <a name="clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox::GetAnchorIndex

Ruft den nullbasierten Index des aktuellen Ankerelements im Listenfeld ab.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der Index des aktuellen Ankerelements, falls erfolgreich; ansonsten LB_ERR.

### <a name="remarks"></a>Bemerkungen

In einem Listenfeld mit mehreren Auswahlen ist das Ankerelement das erste oder letzte Element in einem Block zusammenhängender ausgewählter Elemente.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CListBox::SetAnchorIndex](#setanchorindex).

## <a name="clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox::GetCaretIndex

Bestimmt den Index des Elements mit dem Fokusrechteck in einem Listenfeld mit mehreren Auswahlen.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des Elements, das das Fokusrechteck in einem Listenfeld enthält. Wenn es sich bei dem Listenfeld um ein Listenfeld mit einer Auswahl handelt, ist der Rückgabewert der Index des ausgewählten Elements, falls vorhanden.

### <a name="remarks"></a>Bemerkungen

Das Element kann ausgewählt werden oder nicht.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CListBox::SetCaretIndex](#setcaretindex).

## <a name="clistboxgetcount"></a><a name="getcount"></a>CListBox::GetCount

Ruft die Anzahl der Elemente in einem Listenfeld ab.

```
int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Listenfeld oder LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Die zurückgegebene Anzahl ist größer als der Indexwert des letzten Elements (der Index ist nullbasiert).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

## <a name="clistboxgetcursel"></a><a name="getcursel"></a>CListBox::GetCurSel

Ruft den nullbasierten Index des aktuell ausgewählten Elements (falls vorhanden) in einem Listenfeld mit einer Auswahl ab.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des aktuell ausgewählten Elements, wenn es sich um ein Listenfeld mit einer Auswahl handelt. Es ist LB_ERR, wenn derzeit kein Element ausgewählt ist.

In einem Listenfeld mit mehreren Auswahlen wird der Index des Elements mit dem Fokus angezeigt.

### <a name="remarks"></a>Bemerkungen

Rufen `GetCurSel` Sie kein Listenfeld mit mehreren Auswahlen an. Verwenden Sie stattdessen [CListBox::GetSelItems.](#getselitems)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

## <a name="clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent

Ruft aus dem Listenfeld die Breite in Pixel ab, um die sie horizontal gescrollt werden kann.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Rückgabewert

Die scrollbare Breite des Listenfelds in Pixel.

### <a name="remarks"></a>Bemerkungen

Dies gilt nur, wenn das Listenfeld über eine horizontale Bildlaufleiste verfügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

## <a name="clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox::GetItemData

Ruft den von der Anwendung bereitgestellten Doppelwortwert ab, der dem angegebenen Listenfeldelement zugeordnet ist.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Elements im Listenfeld an.

### <a name="return-value"></a>Rückgabewert

Der dem Element zugeordnete Wert oder LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Der Doubleword-Wert war der *dwItemData-Parameter* eines [SetItemData-Aufrufs.](#setitemdata)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

## <a name="clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox::GetItemDataPtr

Ruft den von der Anwendung bereitgestellten 32-Bit-Wert ab, der dem angegebenen Listenfeldelement als Zeiger zugeordnet ist (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Elements im Listenfeld an.

### <a name="return-value"></a>Rückgabewert

Ruft einen Zeiger oder -1 ab, wenn ein Fehler auftritt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

## <a name="clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox::GetItemHeight

Bestimmt die Höhe von Elementen in einem Listenfeld.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Elements im Listenfeld an. Dieser Parameter wird nur verwendet, wenn das Listenfeld den Stil LBS_OWNERDRAWVARIABLE. Andernfalls sollte sie auf 0 gesetzt werden.

### <a name="return-value"></a>Rückgabewert

Die Höhe der Elemente im Listenfeld in Pixel. Wenn das Listenfeld den [LBS_OWNERDRAWVARIABLE-Format](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) hat, ist der Rückgabewert die Höhe des von *nIndex*angegebenen Elements . Wenn ein Fehler auftritt, wird der Rückgabewert LB_ERR.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

## <a name="clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox::GetItemRect

Ruft die Dimensionen des Rechtecks ab, das ein Listenfeldelement angrenzt, wie es derzeit im Listenfeldfenster angezeigt wird.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Elements an.

*lpRect*<br/>
Gibt einen langen Zeiger auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) an, die die Listenfeldclientkoordinaten des Elements empfängt.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

## <a name="clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox::GetListBoxInfo

Ruft die Anzahl der Elemente pro Spalte ab.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Rückgabewert

Anzahl der Elemente pro `CListBox` Spalte des Objekts.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der [LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo) Nachricht, wie im Windows SDK beschrieben.

## <a name="clistboxgetlocale"></a><a name="getlocale"></a>CListBox::GetLocale

Ruft das gebietsschema ab, das vom Listenfeld verwendet wird.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Rückgabewert

Der Gebietsschemabezeichner (LCID) für die Zeichenfolgen im Listenfeld.

### <a name="remarks"></a>Bemerkungen

Das Gebietsschema wird z. B. verwendet, um die Sortierreihenfolge der Zeichenfolgen in einem sortierten Listenfeld zu bestimmen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CListBox::SetLocale](#setlocale).

## <a name="clistboxgetsel"></a><a name="getsel"></a>CListBox::GetSel

Ruft den Auswahlstatus eines Elements ab.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Elements an.

### <a name="return-value"></a>Rückgabewert

Eine positive Zahl, wenn das angegebene Element ausgewählt ist; Andernfalls ist es 0. Der Rückgabewert ist LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion funktioniert sowohl mit Einzel- als auch mit Mehrfachauswahllistenfeldern.

Um den Index des aktuell ausgewählten Listenfeldelements abzurufen, verwenden Sie [CListBox::GetCurSel](#getcursel).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

## <a name="clistboxgetselcount"></a><a name="getselcount"></a>CListBox::GetSelCount

Ruft die Gesamtzahl der ausgewählten Elemente in einem Listenfeld mit mehreren Auswahlen ab.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der ausgewählten Elemente in einem Listenfeld. Wenn es sich bei dem Listenfeld um ein Listenfeld mit einer Auswahl handelt, wird der Rückgabewert LB_ERR.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CListBox::GetSelItems](#getselitems).

## <a name="clistboxgetselitems"></a><a name="getselitems"></a>CListBox::GetSelItems

Füllt einen Puffer mit einem Array von ganzzahlen, das die Elementnummern ausgewählter Elemente in einem Listenfeld mit mehreren Auswahlen angibt.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parameter

*nMaxItems*<br/>
Gibt die maximale Anzahl ausgewählter Artikel an, deren Artikelnummern im Puffer platziert werden sollen.

*rgIndex*<br/>
Gibt einen Zeiger auf einen Puffer an, der groß genug für die Anzahl der von *nMaxItems*angegebenen Ganzzahlen ist.

### <a name="return-value"></a>Rückgabewert

Die tatsächliche Anzahl der im Puffer platzierten Elemente. Wenn das Listenfeld ein Listenfeld mit einer `LB_ERR`Auswahl ist, lautet der Rückgabewert .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

## <a name="clistboxgettext"></a><a name="gettext"></a>CListBox::GetText

Ruft eine Zeichenfolge aus einem Listenfeld ab.

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index der abrufbaren Zeichenfolge an.

*lpszBuffer*<br/>
Zeigt auf den Puffer, der die Zeichenfolge empfängt. Der Puffer muss über ausreichend Speicherplatz für die Zeichenfolge und ein beendendes NULL-Zeichen verfügen. Die Größe der Zeichenfolge kann im Voraus `GetTextLen` durch Aufrufen der Memberfunktion bestimmt werden.

*rString*<br/>
Ein Verweis auf ein `CString`-Objekt.

### <a name="return-value"></a>Rückgabewert

Die Länge (in Bytes) der Zeichenfolge, ohne das beendende Nullzeichen. Wenn *nIndex* keinen gültigen Index angibt, wird der Rückgabewert LB_ERR.

### <a name="remarks"></a>Bemerkungen

Die zweite Form dieser Memberfunktion `CString` füllt ein Objekt mit dem Zeichenfolgentext.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

## <a name="clistboxgettextlen"></a><a name="gettextlen"></a>CListBox::GetTextLen

Ruft die Länge einer Zeichenfolge in einem Listenfeldelement ab.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index der Zeichenfolge an.

### <a name="return-value"></a>Rückgabewert

Die Länge der Zeichenfolge in Zeichen, mit Ausnahme des beendenden Nullzeichens. Wenn *nIndex* keinen gültigen Index angibt, wird der Rückgabewert LB_ERR.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CListBox::GetText](#gettext).

## <a name="clistboxgettopindex"></a><a name="gettopindex"></a>CListBox::GetTopIndex

Ruft den nullbasierten Index des ersten sichtbaren Elements in einem Listenfeld ab.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der Null-basierte Index des ersten sichtbaren Elements in einem Listenfeld, wenn erfolgreich, LB_ERR andernfalls.

### <a name="remarks"></a>Bemerkungen

Zunächst befindet sich Element 0 oben im Listenfeld, aber wenn das Listenfeld gescrollt wird, befindet sich möglicherweise ein anderes Element oben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

## <a name="clistboxinitstorage"></a><a name="initstorage"></a>CListBox::InitStorage

Reserviert Speicher zum Speichern von Listenfeldelementen.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parameter

*nItems*<br/>
Gibt die Anzahl der hinzuzufügenden Elemente an.

*nBytes*<br/>
Gibt die Speichermenge in Bytes an, die für Elementzeichenfolgen reserviert werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, ist die maximale Anzahl von Elementen, die das Listenfeld speichern kann, bevor eine Speicherumverteilung erforderlich ist, andernfalls LB_ERRSPACE, d. h., es ist nicht genügend Arbeitsspeicher verfügbar.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, bevor `CListBox`Sie eine große Anzahl von Elementen zu einer hinzufügen.

Diese Funktion beschleunigt die Initialisierung von Listenfeldern mit einer großen Anzahl von Elementen (mehr als 100). Es ordnet die angegebene Speichermenge vor, so dass nachfolgende [AddString](#addstring)-, [InsertString-](#insertstring)und [Dir-Funktionen](#dir) die kürzest mögliche Zeit in Anspruch nehmen. Sie können Schätzungen für die Parameter verwenden. Wenn Sie überschätzen, wird etwas zusätzlicher Speicher zugewiesen. Wenn Sie unterschätzen, wird die normale Zuordnung für Artikel verwendet, die den vorab zugewiesenen Betrag überschreiten.

Nur Windows 95/98: Der *nItems-Parameter* ist auf 16-Bit-Werte beschränkt. Dies bedeutet, dass Listenfelder nicht mehr als 32.767 Elemente enthalten dürfen. Obwohl die Anzahl der Elemente eingeschränkt ist, ist die Gesamtgröße der Elemente in einem Listenfeld nur durch den verfügbaren Speicher begrenzt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

## <a name="clistboxinsertstring"></a><a name="insertstring"></a>CListBox::InsertString

Fügt eine Zeichenfolge in das Listenfeld ein.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index der Position an, um die Zeichenfolge einzufügen. Wenn dieser Parameter -1 ist, wird die Zeichenfolge am Ende der Liste hinzugefügt.

*lpszItem*<br/>
Zeigt auf die einzufügende nullterminierte Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index der Position, an der die Zeichenfolge eingefügt wurde. Der Rückgabewert ist LB_ERR, wenn ein Fehler auftritt. Der Rückgabewert ist LB_ERRSPACE, wenn nicht genügend Speicherplatz zum Speichern der neuen Zeichenfolge verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Im Gegensatz zur [AddString-Memberfunktion](#addstring) `InsertString` wird keine Liste mit der LBS_SORT-Formatsortiert. [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

## <a name="clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox::ItemFromPoint

Bestimmt das Listenfeldelement, das dem in *pt*angegebenen Punkt am nächsten liegt.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Punkt, für den das nächste Element gefunden werden soll, angegeben relativ zur oberen linken Ecke des Clientbereichs des Listenfelds.

*bOutside*<br/>
Verweis auf eine BOOL-Variable, die auf TRUE gesetzt wird, wenn *pt* außerhalb des Clientbereichs des Listenfelds ist, FALSE, wenn *pt* sich innerhalb des Clientbereichs des Listenfelds befindet.

### <a name="return-value"></a>Rückgabewert

Der Index des nächstgelegenen Elements an den punktgemäß in *pt*angegebenen Punkt .

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion können Sie bestimmen, über welches Listenfeldelement der Mauszeiger bewegt wird.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CListBox::SetAnchorIndex](#setanchorindex).

## <a name="clistboxmeasureitem"></a><a name="measureitem"></a>CListBox::MeasureItem

Wird vom Framework aufgerufen, wenn ein Listenfeld mit einem Besitzerzeichnungsstil erstellt wird.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parameter

*lpMeasureItemStruct*<br/>
Ein langer Zeiger auf eine [MEASUREITEMSTRUCT-Struktur.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Memberfunktion nichts aus. Überschreiben Sie diese Memberfunktion, und füllen Sie die `MEASUREITEMSTRUCT` Struktur aus, um Windows über die Listenfelddimensionen zu informieren. Wenn das Listenfeld mit dem [Stil LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) erstellt wird, ruft das Framework diese Memberfunktion für jedes Element im Listenfeld auf. Andernfalls wird dieses Element nur einmal aufgerufen.

Weitere Informationen zur Verwendung des [LBS_OWNERDRAWFIXED-Stils](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) in einem `SubclassDlgItem` Mit `CWnd`der Memberfunktion von erstellten Listenfeld für besitzerzeichnen. Siehe die Diskussion in Technical Note [14](../../mfc/tn014-custom-controls.md).

Eine Beschreibung der `MEASUREITEMSTRUCT` Struktur finden Sie unter [CWnd::OnMeasureItem.](../../mfc/reference/cwnd-class.md#onmeasureitem)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

## <a name="clistboxresetcontent"></a><a name="resetcontent"></a>CListBox::ResetContent

Entfernt alle Elemente aus einem Listenfeld.

```
void ResetContent();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

## <a name="clistboxselectstring"></a><a name="selectstring"></a>CListBox::SelectString

Sucht nach einem Listenfeldelement, das mit der angegebenen Zeichenfolge übereinstimmt, und wenn ein übereinstimmendes Element gefunden wird, wird das Element ausgewählt.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parameter

*nStartAfter*<br/>
Enthält den nullbasierten Index des Elements vor dem ersten zu durchsuchenden Element. Wenn die Suche am Ende des Listenfelds angelangt ist, wird sie vom oberen Rand des Listenfelds zurück zu dem von *nStartAfter*angegebenen Element fortgesetzt. Wenn *nStartAfter* -1 ist, wird das gesamte Listenfeld von Anfang an durchsucht.

*lpszItem*<br/>
Verweist auf die null-terminierte Zeichenfolge, die das Präfix enthält, nach dem gesucht werden soll. Die Suche ist großfliegt, daher kann diese Zeichenfolge eine beliebige Kombination aus Groß- und Kleinbuchstaben enthalten.

### <a name="return-value"></a>Rückgabewert

Der Index des ausgewählten Elements, wenn die Suche erfolgreich war. Wenn die Suche nicht erfolgreich war, wird der Rückgabewert LB_ERR und die aktuelle Auswahl wird nicht geändert.

### <a name="remarks"></a>Bemerkungen

Das Listenfeld wird ggf. gescrollt, um das ausgewählte Element anzuzeigen.

Diese Memberfunktion kann nicht mit einem Listenfeld mit dem [Format LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) verwendet werden.

Ein Element wird nur ausgewählt, wenn seine Anfangszeichen (vom Startpunkt) mit den Zeichen in der von *lpszItem*angegebenen Zeichenfolge übereinstimmen.

Verwenden `FindString` Sie die Memberfunktion, um eine Zeichenfolge zu finden, ohne das Element auszuwählen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

## <a name="clistboxselitemrange"></a><a name="selitemrange"></a>CListBox::SelItemRange

Wählt mehrere aufeinander folgende Elemente in einem Listenfeld mit mehreren Auswahlen aus.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parameter

*bSelect*<br/>
Gibt an, wie die Auswahl festgelegt werden soll. Wenn *bSelect* TRUE ist, wird die Zeichenfolge ausgewählt und hervorgehoben. Wenn FALSE, wird die Hervorhebung entfernt, und die Zeichenfolge ist nicht mehr ausgewählt.

*nFirstItem*<br/>
Gibt den nullbasierten Index des ersten festzulegenden Elements an.

*nLastItem*<br/>
Gibt den nullbasierten Index des letzten festzulegenden Elements an.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion nur mit Listenfeldern mit mehreren Auswahlen. Wenn Sie nur ein Element in einem Listenfeld mit mehreren Auswahlen auswählen müssen, d. h., wenn *nFirstItem* *nLastItem* gleich ist, rufen Sie stattdessen die [SetSel-Memberfunktion](#setsel) auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

## <a name="clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox::SetAnchorIndex

Legt den Anker in einem Listenfeld mit mehreren Auswahlen fest, um eine erweiterte Auswahl zu beginnen.

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Listenfeldelements an, das der Anker sein wird.

### <a name="remarks"></a>Bemerkungen

In einem Listenfeld mit mehreren Auswahlen ist das Ankerelement das erste oder letzte Element in einem Block zusammenhängender ausgewählter Elemente.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

## <a name="clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox::SetCaretIndex

Legt das Fokusrechteck auf das Element am angegebenen Index in einem Listenfeld mit mehreren Auswahlen fest.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Elements an, das das Fokusrechteck im Listenfeld erhalten soll.

*bScroll*<br/>
Wenn dieser Wert 0 ist, wird das Element gescrollt, bis es vollständig sichtbar ist. Wenn dieser Wert nicht 0 ist, wird das Element gescrollt, bis es zumindest teilweise sichtbar ist.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Wenn das Element nicht sichtbar ist, wird es in die Ansicht gescrollt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

## <a name="clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListBox::SetColumnWidth

Legt die Breite in Pixeln aller Spalten in einem Listenfeld mit mehreren Spalten fest (erstellt mit dem [Stil LBS_MULTICOLUMN).](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parameter

*cxWidth*<br/>
Gibt die Breite in Pixelaller Spalten an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

## <a name="clistboxsetcursel"></a><a name="setcursel"></a>CListBox::SetCurSel

Wählt eine Zeichenfolge aus und scrollt bei Bedarf in die Ansicht.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parameter

*nWählen*<br/>
Gibt den nullbasierten Index der ausgewählten Zeichenfolge an. Wenn *nSelect* -1 ist, ist das Listenfeld so eingestellt, dass es keine Auswahl hat.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Wenn die neue Zeichenfolge ausgewählt ist, entfernt das Listenfeld die Hervorhebung aus der zuvor ausgewählten Zeichenfolge.

Verwenden Sie diese Memberfunktion nur mit Listenfeldern mit einer Auswahl.

Um eine Auswahl in einem Listenfeld mit mehreren Auswahlen festzulegen oder zu entfernen, verwenden Sie [CListBox::SetSel](#setsel).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

## <a name="clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent

Legt die Breite in Pixel fest, durch die ein Listenfeld horizontal gescrollt werden kann.

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parameter

*cxExtent*<br/>
Gibt die Anzahl der Pixel an, nach denen das Listenfeld horizontal gescrollt werden kann.

### <a name="remarks"></a>Bemerkungen

Wenn die Größe des Listenfelds kleiner als dieser Wert ist, scrollt die horizontale Bildlaufleiste horizontal Elemente im Listenfeld. Wenn das Listenfeld so groß oder größer als dieser Wert ist, wird die horizontale Bildlaufleiste ausgeblendet.

Um auf einen `SetHorizontalExtent`Aufruf von zu reagieren, muss das Listenfeld mit dem [Stil WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) definiert worden sein.

Diese Memberfunktion ist für mehrspaltige Listenfelder nicht nützlich. Rufen Sie für mehrspaltige Listenfelder die `SetColumnWidth` Memberfunktion auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

## <a name="clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox::SetItemData

Legt einen Wert fest, der dem angegebenen Element in einem Listenfeld zugeordnet ist.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Elements an.

*dwItemData*<br/>
Gibt den Wert an, der dem Element zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

## <a name="clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox::SetItemDataPtr

Legt den 32-Bit-Wert, der dem angegebenen Element zugeordnet ist, in einem Listenfeld als den angegebenen Zeiger fest ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Elements an.

*pData*<br/>
Gibt den Zeiger an, der dem Element zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Dieser Zeiger bleibt für die Lebensdauer des Listenfelds gültig, auch wenn sich die relative Position des Elements innerhalb des Listenfelds ändern kann, wenn Elemente hinzugefügt oder entfernt werden. Daher kann sich der Index des Elements innerhalb des Felds ändern, aber der Zeiger bleibt zuverlässig.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

## <a name="clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox::SetItemHeight

Legt die Höhe von Elementen in einem Listenfeld fest.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Elements im Listenfeld an. Dieser Parameter wird nur verwendet, wenn das Listenfeld den Stil LBS_OWNERDRAWVARIABLE. Andernfalls sollte sie auf 0 gesetzt werden.

*cyItemHeight*<br/>
Gibt die Höhe des Elements in Pixel an.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn der Index oder die Höhe ungültig ist.

### <a name="remarks"></a>Bemerkungen

Wenn das Listenfeld den [Stil LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) hat, legt diese Funktion die Höhe des von *nIndex*angegebenen Elements fest. Andernfalls legt diese Funktion die Höhe aller Elemente im Listenfeld fest.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

## <a name="clistboxsetlocale"></a><a name="setlocale"></a>CListBox::SetLocale

Legt den Gebietsschemabezeichner für dieses Listenfeld fest.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parameter

*nNewLocale*<br/>
Der neue Gebietsschemabezeichner (LCID), der für das Listenfeld festgelegt werden soll.

### <a name="return-value"></a>Rückgabewert

Der vorherige Gebietsschemabezeichner (LCID) für dieses Listenfeld.

### <a name="remarks"></a>Bemerkungen

Wenn `SetLocale` nicht aufgerufen wird, wird das Standardgebietsschema vom System abgerufen. Dieses Systemstandardgebietsschema kann mithilfe der regionalen (oder internationalen) Anwendung der Systemsteuerung geändert werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

## <a name="clistboxsetsel"></a><a name="setsel"></a>CListBox::SetSel

Wählt eine Zeichenfolge in einem Listenfeld mit mehreren Auswahlen aus.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält den nullbasierten Index der festzulegenden Zeichenfolge. Wenn -1, wird die Auswahl allen Zeichenfolgen hinzugefügt oder aus ihnen entfernt, abhängig vom Wert von *bSelect*.

*bSelect*<br/>
Gibt an, wie die Auswahl festgelegt werden soll. Wenn *bSelect* TRUE ist, wird die Zeichenfolge ausgewählt und hervorgehoben. Wenn FALSE, wird die Hervorhebung entfernt, und die Zeichenfolge ist nicht mehr ausgewählt. Die angegebene Zeichenfolge wird standardmäßig ausgewählt und hervorgehoben.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion nur mit Listenfeldern mit mehreren Auswahlen.

Um ein Element aus einem Listenfeld mit einer Auswahl auszuwählen, verwenden Sie [CListBox::SetCurSel](#setcursel).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

## <a name="clistboxsettabstops"></a><a name="settabstops"></a>CListBox::SetTabStops

Legt die Tabstopppositionen in einem Listenfeld fest.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parameter

*cxEachStop*<br/>
Tabstopps werden an allen *cxEachStop-Dialogeinheiten* festgelegt. Eine Beschreibung einer Dialogeinheit finden Sie unter *rgTabStops.*

*nTabStops*<br/>
Gibt die Anzahl der Tabstopps an, die im Listenfeld enthalten sein sollen.

*rgTabStops*<br/>
Zeigt auf das erste Element eines Arrays von Ganzzahlen, die die Tabstopppositionen in Dialogeinheiten enthalten. Eine Dialogeinheit ist ein horizontaler oder vertikaler Abstand. Eine horizontale Dialogeinheit entspricht einem Viertel der aktuellen Dialogbasisbreiteneinheit, und eine vertikale Dialogeinheit entspricht einem Achtel der aktuellen Dialogbasishöheneinheit. Die Dialogbasiseinheiten werden basierend auf der Höhe und Breite der aktuellen Systemschriftart berechnet. Die `GetDialogBaseUnits` Windows-Funktion gibt die aktuellen Dialogbasiseinheiten in Pixel zurück. Die Tabstopps müssen in zunehmender Reihenfolge sortiert werden. zurück-Registerkarten sind nicht zulässig.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn alle Registerkarten festgelegt wurden; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Um Tabstopps auf die Standardgröße von 2 Dialogeinheiten festzulegen, rufen Sie die parameterlose Version dieser Memberfunktion auf. Um Tabstopps auf eine andere Größe als 2 festzulegen, rufen Sie die Version mit dem Argument *cxEachStop* auf.

Um Tabstopps auf ein Array von Größen festzulegen, verwenden Sie die Version mit den Argumenten *rgTabStops* und *nTabStops.* Für jeden Wert in *rgTabStops*wird ein Tabstopp festgelegt, bis zu der von *nTabStops*angegebenen Zahl .

Um auf einen Aufruf `SetTabStops` der Memberfunktion zu reagieren, muss das Listenfeld mit dem [Stil LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) erstellt worden sein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

## <a name="clistboxsettopindex"></a><a name="settopindex"></a>CListBox::SetTopIndex

Stellt sicher, dass ein bestimmtes Listenfeldelement sichtbar ist.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Listenfeldelements an.

### <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, oder LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Das System scrollt das Listenfeld, bis entweder das von *nIndex* angegebene Element oben im Listenfeld angezeigt wird oder der maximale Bildlaufbereich erreicht wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

## <a name="clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox::VKeyToItem

Wird vom Framework aufgerufen, wenn das übergeordnete Fenster des Listenfelds eine WM_VKEYTOITEM Nachricht aus dem Listenfeld empfängt.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parameter

*nKey*<br/>
Der virtuelle Schlüsselcode der Taste, die der Benutzer gedrückt hat. Eine Liste der standardmäßigen virtuellen Schlüsselcodes finden Sie unter Winuser.h

*nIndex*<br/>
Die aktuelle Position der Listenbox-Pflege.

### <a name="return-value"></a>Rückgabewert

Gibt - 2 für keine weitere Aktion, - 1 für Standardaktion oder eine nicht negative Zahl zurück, um einen Index eines Listenfeldelements anzugeben, auf dem die Standardaktion für den Tastenanschlag ausgeführt werden soll.

### <a name="remarks"></a>Bemerkungen

Die WM_VKEYTOITEM Nachricht wird vom Listenfeld gesendet, wenn eine WM_KEYDOWN Nachricht empfangen wird, jedoch nur, wenn das Listenfeld die beiden folgenden Punkte erfüllt:

- Hat den [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil festgelegt.

- Hat mindestens ein Element.

Sie sollten diese Funktion niemals selbst aufrufen. Überschreiben Sie diese Funktion, um Ihre eigene benutzerdefinierte Behandlung von Tastaturnachrichten bereitzustellen.

Sie müssen einen Wert zurückgeben, um dem Framework mitzuteilen, welche Aktion Ihre Außerkraftsetzung ausgeführt hat. Der Rückgabewert von - 2 gibt an, dass die Anwendung alle Aspekte der Auswahl des Elements behandelt hat und keine weitere Aktion durch das Listenfeld erfordert. Vor der Rückkehr - 2, können Sie die Auswahl oder bewegen Sie die Einser oder beides. Um die Auswahl festzulegen, verwenden Sie [SetCurSel](#setcursel) oder [SetSel](#setsel). Um die Einserwart zu verschieben, verwenden Sie [SetCaretIndex](#setcaretindex).

Der Rückgabewert 1 gibt an, dass das Listenfeld die Standardaktion als Reaktion auf den Tastenanschlag ausführen soll. Die Standardimplementierung gibt zurück - 1.

Ein Rückgabewert von 0 oder höher gibt den Index eines Elements im Listenfeld an und gibt an, dass das Listenfeld die Standardaktion für den Tastenanschlag für das angegebene Element ausführen soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar-Klasse](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic-Klasse](../../mfc/reference/cstatic-class.md)
