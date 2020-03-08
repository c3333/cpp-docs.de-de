---
title: CListBox-Klasse
description: Eine Beschreibung der MFC CListBox-Klasse und ihrer Member-Funktionen.
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
ms.openlocfilehash: 5c3337641dcfc720a5f9fbccf5bb0614e97c3b54
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865521"
---
# <a name="clistbox-class"></a>CListBox-Klasse

Stellt die Funktionalität eines Windows-Listenfelds bereit.

## <a name="syntax"></a>Syntax

```
class CListBox : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|-Name|Beschreibung|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Erstellt ein `CListBox`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|-Name|Beschreibung|
|----------|-----------------|
|[CListBox::AddString](#addstring)|Fügt einem Listenfeld eine Zeichenfolge hinzu.|
|[CListBox::CharToItem](#chartoitem)|Überschreiben Sie, um benutzerdefinierte WM_CHAR Behandlung für Listenfelder, die keine Zeichen folgen sind, bereitzustellen.|
|[CListBox::CompareItem](#compareitem)|Wird von Framework aufgerufen, um die Position eines neuen Elements in einem sortierten Besitzer-zeichnen-Listenfeld zu bestimmen.|
|[CListBox::Create](#create)|Erstellt das Windows-Listenfeld und fügt es an das `CListBox` Objekt an.|
|[CListBox::DeleteItem](#deleteitem)|Wird von Framework aufgerufen, wenn der Benutzer ein Element aus einem Listenfeld für den Besitzer zeichnen löscht.|
|[CListBox::DeleteString](#deletestring)|Löscht eine Zeichenfolge aus einem Listenfeld.|
|[CListBox::Dir](#dir)|Fügt Dateinamen, Laufwerke oder beides aus dem aktuellen Verzeichnis einem Listenfeld hinzu.|
|[CListBox::DrawItem](#drawitem)|Wird von Framework aufgerufen, wenn sich ein visueller Aspekt eines Listen Felds für das Besitzer Zeichen ändert.|
|[CListBox::FindString](#findstring)|Sucht in einem Listenfeld nach einer Zeichenfolge.|
|[CListBox::FindStringExact](#findstringexact)|Sucht die erste Listenfeld Zeichenfolge, die mit einer angegebenen Zeichenfolge übereinstimmt.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Ruft den NULL basierten Index des aktuellen Anker Elements in einem Listenfeld ab.|
|[CListBox::GetCaretIndex](#getcaretindex)|Bestimmt den Index des Elements, das über das Fokus Rechteck in einem Listenfeld für Mehrfachauswahl verfügt.|
|[CListBox::GetCount](#getcount)|Gibt die Anzahl der Zeichen folgen in einem Listenfeld zurück.|
|[CListBox::GetCurSel](#getcursel)|Gibt den NULL basierten Index der aktuell ausgewählten Zeichenfolge in einem Listenfeld zurück.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Gibt die Breite in Pixel zurück, in der ein Listenfeld horizontal gescrollt werden kann.|
|[CListBox::GetItemData](#getitemdata)|Gibt einen Wert zurück, der dem Listenfeld Element zugeordnet ist.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Gibt einen Zeiger auf ein Listenfeld Element zurück.|
|[CListBox::GetItemHeight](#getitemheight)|Bestimmt die Höhe der Elemente in einem Listenfeld.|
|[CListBox::GetItemRect](#getitemrect)|Gibt das umgebende Rechteck des Listenfeld Elements zurück, das aktuell angezeigt wird.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Ruft die Anzahl der Elemente pro Spalte ab.|
|[CListBox::GetLocale](#getlocale)|Ruft den Gebiets Schema Bezeichner für ein Listenfeld ab.|
|[CListBox::GetSel](#getsel)|Gibt den Auswahl Zustand eines Listenfeld Elements zurück.|
|[CListBox::GetSelCount](#getselcount)|Gibt die Anzahl der Zeichen folgen zurück, die derzeit in einem Listenfeld für Mehrfachauswahl ausgewählt sind.|
|[CListBox::GetSelItems](#getselitems)|Gibt die Indizes der Zeichen folgen zurück, die derzeit in einem Listenfeld ausgewählt sind.|
|[CListBox::GetText](#gettext)|Kopiert ein Listenfeld Element in einen Puffer.|
|[CListBox::GetTextLen](#gettextlen)|Gibt die Länge eines Listenfeld Elements in Byte zurück.|
|[CListBox::GetTopIndex](#gettopindex)|Gibt den Index der ersten sichtbaren Zeichenfolge in einem Listenfeld zurück.|
|[CListBox::InitStorage](#initstorage)|Ordnet Speicherblöcke für Listenfeld Elemente und Zeichen folgen vorab zu.|
|[CListBox::InsertString](#insertstring)|Fügt eine Zeichenfolge an einer bestimmten Position in einem Listenfeld ein.|
|[CListBox::ItemFromPoint](#itemfrompoint)|Gibt den Index des Listenfeld Elements an nächster Stelle zurück.|
|[CListBox::MeasureItem](#measureitem)|Wird von Framework aufgerufen, wenn ein Listenfeld zum Erstellen von Besitzern zum Bestimmen von Listenfeld Dimensionen erstellt wird.|
|[CListBox::ResetContent](#resetcontent)|Löscht alle Einträge aus einem Listenfeld.|
|[CListBox::SelectString](#selectstring)|Sucht nach einer Zeichenfolge in einem Listenfeld mit einer einzelnen Auswahl und wählt diese aus.|
|[CListBox::SelItemRange](#selitemrange)|Aktiviert oder deaktiviert einen Bereich von Zeichen folgen in einem Listenfeld mit Mehrfachauswahl.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Legt den Anker in einem Listenfeld Mehrfachauswahl fest, um eine erweiterte Auswahl zu beginnen.|
|[CListBox::SetCaretIndex](#setcaretindex)|Legt das Fokus Rechteck auf das Element am angegebenen Index in einem Mehrfachauswahl-Listenfeld fest.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Legt die Spaltenbreite eines mehrspaltigen Listen Felds fest.|
|[CListBox::SetCurSel](#setcursel)|Wählt eine Listenfeld Zeichenfolge aus.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Legt die Breite in Pixel fest, in der ein Listenfeld horizontal gescrollt werden kann.|
|[CListBox::SetItemData](#setitemdata)|Legt einen Wert fest, der dem Listenfeld Element zugeordnet ist.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Legt einen Zeiger auf das Listenfeld Element fest.|
|[CListBox::SetItemHeight](#setitemheight)|Legt die Höhe von Elementen in einem Listenfeld fest.|
|[CListBox::SetLocale](#setlocale)|Legt den Gebiets Schema Bezeichner für ein Listenfeld fest.|
|[CListBox::SetSel](#setsel)|Aktiviert oder deaktiviert ein Listenfeld Element in einem Listenfeld mit Mehrfachauswahl.|
|[CListBox::SetTabStops](#settabstops)|Legt die Position der Tabstopps in einem Listenfeld fest.|
|[CListBox::SetTopIndex](#settopindex)|Legt den NULL basierten Index der ersten sichtbaren Zeichenfolge in einem Listenfeld fest.|
|[CListBox::VKeyToItem](#vkeytoitem)|Überschreiben Sie, um benutzerdefinierte WM_KEYDOWN Behandlung für Listenfelder mit der LBS_WANTKEYBOARDINPUT Formatvorlage bereitzustellen.|

## <a name="remarks"></a>Hinweise

Ein Listenfeld zeigt eine Liste von Elementen (z. b. Dateinamen) an, die der Benutzer anzeigen und auswählen kann.

In einem Listenfeld mit einfacher Auswahl kann der Benutzer nur ein Element auswählen. In einem Listenfeld mit mehreren Auswahlmöglichkeiten kann ein Bereich von Elementen ausgewählt werden. Wenn der Benutzer ein Element auswählt, wird es hervorgehoben, und das Listenfeld sendet eine Benachrichtigungs Meldung an das übergeordnete Fenster.

Sie können ein Listenfeld entweder aus einer Dialogfeld Vorlage oder direkt im Code erstellen. Um es direkt zu erstellen, erstellen Sie das `CListBox`-Objekt, und rufen Sie dann die [Create](#create) Member-Funktion auf, um das Windows-Listenfeld-Steuerelement zu erstellen und es an das `CListBox` Objekt anzufügen Um ein Listenfeld in einer Dialogfeld Vorlage zu verwenden, deklarieren Sie eine Listenfeld Variable in der Dialogfeld Klasse, und verwenden Sie dann `DDX_Control` in der `DoDataExchange`-Funktion der Dialogfeld Klasse, um die Member-Variable mit dem-Steuerelement zu verbinden. (Dies erfolgt automatisch, wenn Sie Ihrer Dialogfeld Klasse eine Steuerelement Variable hinzufügen.)

Die Konstruktion kann ein einstufiger Prozess in einer Klasse sein, die von `CListBox`abgeleitet ist. Schreiben Sie einen Konstruktor für die abgeleitete Klasse, und nennen Sie `Create` aus dem Konstruktor.

Wenn Sie die von einem Listenfeld gesendeten Windows-Benachrichtigungs Meldungen an das übergeordnete Element (in der Regel eine von [CDialog](../../mfc/reference/cdialog-class.md)abgeleitete Klasse) verarbeiten möchten, fügen Sie der übergeordneten Klasse für jede Nachricht einen Nachrichten Zuordnungs Eintrag und eine nachrichtenhandlermember-Funktion hinzu.

Jeder Nachrichten Zuordnungs Eintrag hat die folgende Form:

`ON_Notification( id, memberFxn )`

Dabei gibt `id` die ID des untergeordneten Fensters des Listenfeld-Steuer Elements an, das die Benachrichtigung sendet, und `memberFxn` der Name der übergeordneten Element Funktion ist, die Sie zum Verarbeiten der Benachrichtigung geschrieben haben.

Der Prototyp der übergeordneten Funktion ist wie folgt:

`afx_msg void memberFxn( );`

Im folgenden finden Sie eine Liste potenzieller Nachrichten Zuordnungs Einträge und eine Beschreibung der Fälle, in denen Sie an das übergeordnete Element gesendet werden:

- ON_LBN_DBLCLK der Benutzer auf eine Zeichenfolge in einem Listenfeld doppelklickt. Diese Benachrichtigungs Meldung wird nur von einem Listenfeld mit dem [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) -Format gesendet.

- ON_LBN_ERRSPACE das Listenfeld kann nicht genügend Arbeitsspeicher zuordnen, um die Anforderung zu erfüllen.

- ON_LBN_KILLFOCUS das Listenfeld den Eingabefokus verliert.

- ON_LBN_SELCANCEL die aktuelle Listenfeld Auswahl abgebrochen wird. Diese Meldung wird nur gesendet, wenn ein Listenfeld den LBS_NOTIFY Stil hat.

- ON_LBN_SELCHANGE die Auswahl im Listenfeld geändert wurde. Diese Benachrichtigung wird nicht gesendet, wenn die Auswahl von der [CListBox:: setcurrsel](#setcursel) -Member-Funktion geändert wird. Diese Benachrichtigung gilt nur für ein Listenfeld, das den LBS_NOTIFY Stil hat. Wenn der Benutzer eine Pfeiltaste drückt, wird die LBN_SELCHANGE Benachrichtigungs Meldung gesendet, wenn der Benutzer eine Pfeiltaste drückt, auch wenn sich die Auswahl nicht ändert.

- ON_LBN_SETFOCUS das Listenfeld den Eingabefokus erhält.

- ON_WM_CHARTOITEM ein Listenfeld zum Zeichnen von Besitzern, das keine Zeichen folgen enthält, eine WM_CHAR Meldung empfängt.

- ON_WM_VKEYTOITEM ein Listenfeld mit dem LBS_WANTKEYBOARDINPUT Format eine WM_KEYDOWN Meldung empfängt.

Wenn Sie ein `CListBox` Objekt in einem Dialogfeld (über eine Dialogfeld Ressource) erstellen, wird das `CListBox` Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie ein `CListBox` Objekt innerhalb eines Fensters erstellen, müssen Sie möglicherweise das `CListBox` Objekt zerstören. Wenn Sie das `CListBox`-Objekt auf dem Stapel erstellen, wird es automatisch zerstört. Wenn Sie das `CListBox`-Objekt auf dem Heap mithilfe der **New** -Funktion erstellen, müssen Sie **Delete** für das-Objekt verwenden, um es zu zerstören, wenn der Benutzer das übergeordnete Fenster schließt.

Wenn Sie im `CListBox` Objekt Arbeitsspeicher zuordnen, überschreiben Sie den `CListBox`-Dekonstruktor, um die Zuordnung zu verwerfen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>-Anforderungen

**Header:** afxwin.h

##  <a name="addstring"></a>CListBox:: AddString

Fügt einem Listenfeld eine Zeichenfolge hinzu.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parameters

*lpszItem*<br/>
Verweist auf die mit NULL endende Zeichenfolge, die hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Der null basierte Index der Zeichenfolge im Listenfeld. Der Rückgabewert ist LB_ERR, wenn ein Fehler auftritt. der Rückgabewert ist LB_ERRSPACE, wenn nicht genügend Speicherplatz zum Speichern der neuen Zeichenfolge zur Verfügung steht.

### <a name="remarks"></a>Hinweise

Wenn das Listenfeld nicht mit dem [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil erstellt wurde, wird die Zeichenfolge am Ende der Liste hinzugefügt. Andernfalls wird die Zeichenfolge in die Liste eingefügt, und die Liste wird sortiert. Wenn das Listenfeld mit dem LBS_SORT-Stil, jedoch nicht mit dem [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Format erstellt wurde, sortiert das Framework die Liste nach einem oder mehreren Aufrufen der `CompareItem` Member-Funktion.

Verwenden Sie [InsertString](#insertstring) , um eine Zeichenfolge in eine bestimmte Position im Listenfeld einzufügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>CListBox:: chartoitem

Wird von Framework aufgerufen, wenn das übergeordnete Fenster des Listen Felds eine WM_CHARTOITEM Meldung aus dem Listenfeld empfängt.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parameters

*nKey*<br/>
Der ANSI-Code des Zeichens, das der Benutzer eingegeben hat.

*nIndex*<br/>
Die aktuelle Position der Listenfeld Einfügemarke.

### <a name="return-value"></a>Rückgabewert

Gibt-1 oder-2 für keine weitere Aktion oder eine nicht negative Zahl zurück, um einen Index eines Listenfeld Elements anzugeben, für das die Standardaktion für den Tastatur Strich ausgeführt werden soll. Die Standard Implementierung gibt-1 zurück.

### <a name="remarks"></a>Hinweise

Die WM_CHARTOITEM Meldung wird vom Listenfeld gesendet, wenn eine WM_CHAR Meldung empfangen wird. Dies ist jedoch nur möglich, wenn das Listenfeld alle folgenden Kriterien erfüllt:

- Ist ein Listenfeld zum Zeichnen von Besitzern.

- Hat nicht den [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil festgelegt.

- Weist mindestens ein Element auf.

Sie sollten diese Funktion niemals selbst aufzurufen. Überschreiben Sie diese Funktion, um eine eigene benutzerdefinierte Behandlung von Tastatur Meldungen bereitzustellen.

In ihrer außer Kraft Setzung müssen Sie einen Wert zurückgeben, um das Framework darüber zu informieren, welche Aktion Sie ausgeführt haben. Der Rückgabewert-1 oder-2 gibt an, dass Sie alle Aspekte der Elementauswahl behandelt haben und keine weitere Aktion im Listenfeld ausführen müssen. Vor dem Zurückgeben von-1 oder-2 konnten Sie die Auswahl festlegen oder die Einfügemarke oder beides verschieben. Verwenden Sie [setcurrsel](#setcursel) oder [SetSel](#setsel), um die Auswahl festzulegen. Verwenden Sie [setcaretindex](#setcaretindex), um die Einfügemarke zu verschieben.

Ein Rückgabewert von 0 (null) oder größer gibt den Index eines Elements im Listenfeld an und gibt an, dass im Listenfeld die Standardaktion für den Tastatur Strich für das angegebene Element ausgeführt werden soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>CListBox:: CListBox

Erstellt ein `CListBox`-Objekt.

```
CListBox();
```

### <a name="remarks"></a>Hinweise

Sie erstellen ein `CListBox`-Objekt in zwei Schritten. Zuerst wird der Konstruktor aufgerufen `ClistBox` und dann `Create`aufgerufen, der das Windows-Listenfeld initialisiert und an den `CListBox`anfügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>CListBox:: compareitem

Wird von Framework aufgerufen, um die relative Position eines neuen Elements in einem sortierten Besitzer-zeichnen-Listenfeld zu bestimmen.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parameters

*lpCompareItemStruct*<br/>
Ein Long-Zeiger auf eine `COMPAREITEMSTRUCT`-Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt die relative Position der beiden Elemente an, die in der [compareitemstruct](/windows/win32/api/winuser/ns-winuser-compareitemstruct) -Struktur beschrieben werden. Es kann sich um einen der folgenden Werte handeln:

|{2&gt;Wert&lt;2}|Bedeutung|
|-----------|-------------|
|-1|Element 1 wird vor Element 2 sortiert.|
|0|Element 1 und Element 2 Sortieren dasselbe.|
|1|Element 1 sortiert nach Element 2.|

Eine Beschreibung der `COMPAREITEMSTRUCT` Struktur finden Sie unter [CWnd:: oncompareitem](../../mfc/reference/cwnd-class.md#oncompareitem) .

### <a name="remarks"></a>Hinweise

Standardmäßig führt diese Member-Funktion keine Aktion aus. Wenn Sie ein Listenfeld zum Zeichnen von Besitzern mit dem LBS_SORT Stil erstellen, müssen Sie diese Element Funktion überschreiben, damit das Framework beim Sortieren neuer Elemente, die dem Listenfeld hinzugefügt werden, behilflich ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>CListBox:: Create

Erstellt das Windows-Listenfeld und fügt es an das `CListBox` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameters

*dwStyle*<br/>
Gibt den Stil des Listen Felds an. Wenden Sie eine beliebige Kombination von [Listenfeld Stilen](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) auf das Feld an.

*Rect*<br/>
Gibt die Größe und Position des Listen Felds an. Kann entweder ein `CRect` Objekt oder eine `RECT` Struktur sein.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Listen Felds an (normalerweise ein `CDialog` Objekt). Er darf nicht NULL sein.

*nID*<br/>
Gibt die Steuerelement-ID des Listen Felds an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Sie erstellen ein `CListBox`-Objekt in zwei Schritten. Zuerst wird der-Konstruktor aufgerufen und dann `Create`aufgerufen, der das Windows-Listenfeld initialisiert und an das `CListBox`-Objekt anfügt.

Wenn `Create` ausgeführt wird, sendet Windows die [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)-, [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)-, [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)-und [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) Meldungen an das Listenfeld-Steuerelement.

Diese Nachrichten werden standardmäßig von den Funktionen " [onnccreate](../../mfc/reference/cwnd-class.md#onnccreate)", " [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)", " [onnccalcsize](../../mfc/reference/cwnd-class.md#onnccalcsize)" und " [ongetminmaxinfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) " in der `CWnd`-Basisklasse verarbeitet. Um die standardmäßige Meldungs Behandlung zu erweitern, leiten Sie eine Klasse von `CListBox`ab, fügen Sie der neuen Klasse eine Meldungs Zuordnung hinzu, und überschreiben Sie die zuvor genannten nachrichtenhandlermember-Funktionen. Überschreiben Sie `OnCreate`z. b., um die erforderliche Initialisierung für eine neue Klasse auszuführen.

Wenden Sie die folgenden [Fenster Stile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein Listenfeld-Steuerelement an.

- Immer WS_CHILD

- WS_VISIBLE in der Regel

- WS_DISABLED selten

- WS_VSCROLL, um eine vertikale Schiebe Leiste hinzuzufügen

- WS_HSCROLL, um eine horizontale Schiebe Leiste hinzuzufügen

- WS_GROUP zum Gruppieren von Steuerelementen

- WS_TABSTOP, um die Tabstopps für dieses Steuerelement zuzulassen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>CListBox::D eleteitem

Wird von Framework aufgerufen, wenn der Benutzer ein Element aus einem Besitzer löscht `CListBox` Objekt erstellt oder das Listenfeld zerstört.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parameters

*lpDeleteItemStruct*<br/>
Ein langer Zeiger auf eine Windows [deleteitemstruct](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) -Struktur, die Informationen über das gelöschte Element enthält.

### <a name="remarks"></a>Hinweise

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um bei Bedarf ein Listenfeld für den Besitzer der Erstellung neu zu zeichnen.

Eine Beschreibung der `DELETEITEMSTRUCT` Struktur finden Sie unter [CWnd:: ondeleteitem](../../mfc/reference/cwnd-class.md#ondeleteitem) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>CListBox::D eletestring

Löscht das Element in Position *nIndex* aus dem Listenfeld.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index der zu löschenden Zeichenfolge an.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen folgen, die in der Liste verbleiben. Der Rückgabewert ist LB_ERR, wenn *nIndex* einen Index angibt, der größer als die Anzahl der Elemente in der Liste ist.

### <a name="remarks"></a>Hinweise

Alle Elemente nach *nIndex* werden nun um eine Position nach unten verschoben. Wenn ein Listenfeld z. b. zwei Elemente enthält, führt das Löschen des ersten Elements dazu, dass das restliche Element jetzt an der ersten Position liegt. *nIndex*= 0 für das Element an der ersten Position.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>CListBox::D IR

Fügt einem Listenfeld eine Liste von Dateinamen, Laufwerken oder beidem hinzu.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parameters

*attr*<br/>
Kann eine beliebige Kombi **Nation der in** `CFile::GetStatu`[s](../../mfc/reference/cfile-class.md#getstatus)beschriebenen Enumerationswerte oder eine beliebige Kombination der folgenden Werte sein:

|{2&gt;Wert&lt;2}|Bedeutung|
|-----------|-------------|
|0x0000|Die Datei kann aus gelesen oder geschrieben werden.|
|0x0001|Die Datei kann aus gelesen werden, aber nicht in geschrieben.|
|0x0002|Die Datei ist ausgeblendet und wird nicht in einer Verzeichnis Auflistung angezeigt.|
|0x0004|Die Datei ist eine Systemdatei.|
|0x0010|Der von *lpszwildcard* angegebene Name gibt ein Verzeichnis an.|
|0x0020|Die Datei wurde archiviert.|
|0x4000|Schließen Sie alle Laufwerke ein, die dem von *lpszwildcard*angegebenen Namen entsprechen.|
|0x8000|Exklusives Flag. Wenn das exklusive Flag festgelegt ist, werden nur Dateien des angegebenen Typs aufgelistet. Andernfalls werden Dateien des angegebenen Typs zusätzlich zu "normalen" Dateien aufgelistet.|

*lpszWildCard*<br/>
Verweist auf eine Datei Spezifikations Zeichenfolge. Die Zeichenfolge kann Platzhalter enthalten (z. b. *.\*).

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des letzten Datei namens, der der Liste hinzugefügt wurde. Der Rückgabewert ist LB_ERR, wenn ein Fehler auftritt. der Rückgabewert ist LB_ERRSPACE, wenn nicht genügend Speicherplatz zum Speichern der neuen Zeichen folgen verfügbar ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>CListBox::D rawitem

Wird von Framework aufgerufen, wenn sich ein visueller Aspekt eines Listen Felds für das Besitzer Zeichen ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameters

*lpDrawItemStruct*<br/>
Ein langer Zeiger auf eine [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) -Struktur, die Informationen über den erforderlichen Zeichentyp enthält.

### <a name="remarks"></a>Hinweise

Die `itemAction` und `itemState` Member der `DRAWITEMSTRUCT` Struktur definieren die auszuführende Zeichnungs Aktion.

Standardmäßig führt diese Member-Funktion keine Aktion aus. Überschreiben Sie diese Member-Funktion, um das Zeichnen für einen Besitzer `CListBox` Objekt zu implementieren. Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface), die für den in *lpdrawitemstruct* angegebenen Anzeige Kontext ausgewählt sind, wiederherstellen, bevor diese Element Funktion beendet wird.

Eine Beschreibung der `DRAWITEMSTRUCT` Struktur finden Sie unter [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>CListBox:: FindString

Sucht die erste Zeichenfolge in einem Listenfeld, das das angegebene Präfix enthält, ohne die Listenfeld Auswahl zu ändern.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parameters

*nStartAfter*<br/>
Enthält den NULL basierten Index des Elements vor dem ersten zu durchsuchenden Element. Wenn die Suche das Ende des Listen Felds erreicht, wird Sie vom oberen Rand des Listen Felds zurück zu dem durch *nstartafter*angegebenen Element. Wenn *nstartafter* den Wert-1 hat, wird das gesamte Listenfeld von Anfang an durchsucht.

*lpszItem*<br/>
Verweist auf die auf NULL endenden Zeichenfolge, die das Präfix enthält, nach dem gesucht werden soll. Die Suche erfolgt unabhängig von der Groß-/Kleinschreibung, sodass diese Zeichenfolge eine beliebige Kombination von Groß-und Kleinbuchstaben enthalten kann.

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des übereinstimmenden Elements oder LB_ERR, wenn die Suche nicht erfolgreich war.

### <a name="remarks"></a>Hinweise

Verwenden Sie die Member-Funktion von [SelectString](#selectstring) , um eine Zeichenfolge zu suchen und auszuwählen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>CListBox:: FindStringExact

Sucht die erste Listenfeld Zeichenfolge, die mit der in *lpszfind*angegebenen Zeichenfolge übereinstimmt.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parameters

*nIndexStart*<br/>
Gibt den NULL basierten Index des Elements vor dem ersten zu durchsuchenden Element an. Wenn die Suche das Ende des Listen Felds erreicht, wird Sie vom oberen Rand des Listen Felds zurück zu dem durch *nindexstart*angegebenen Element. Wenn *nindexstart* den Wert-1 aufweist, wird das gesamte Listenfeld von Anfang an durchsucht.

*lpszFind*<br/>
Zeigt auf die zu suchende NULL-terminierte Zeichenfolge. Diese Zeichenfolge kann einen kompletten Dateinamen enthalten, einschließlich der Erweiterung. Bei der Suche wird die Groß-/Kleinschreibung nicht beachtet, sodass die Zeichenfolge eine beliebige Kombination aus Groß-und Kleinbuchstaben enthalten kann.

### <a name="return-value"></a>Rückgabewert

Der Index des übereinstimmenden Elements oder LB_ERR, wenn die Suche nicht erfolgreich war.

### <a name="remarks"></a>Hinweise

Wenn das Listenfeld mit einem Besitzer Zeichnungs Stil, aber ohne den [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil erstellt wurde, versucht die `FindStringExact` Member-Funktion, den Double Word-Wert mit dem Wert von *lpszfind*abzugleichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>CListBox:: getanchorindex

Ruft den NULL basierten Index des aktuellen Anker Elements im Listenfeld ab.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der Index des aktuellen Anker Elements, wenn erfolgreich. Andernfalls LB_ERR.

### <a name="remarks"></a>Hinweise

Im Listenfeld Mehrfachauswahl ist das Anker Element das erste oder letzte Element in einem Block zusammenhängender ausgewählter Elemente.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CListBox::](#setanchorindex)"".

##  <a name="getcaretindex"></a>CListBox:: getcaretindex

Bestimmt den Index des Elements, das über das Fokus Rechteck in einem Listenfeld für Mehrfachauswahl verfügt.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des Elements, das über das Fokus Rechteck in einem Listenfeld verfügt. Wenn das Listenfeld ein Listenfeld für die einfache Auswahl ist, ist der Rückgabewert der Index des ausgewählten Elements, sofern vorhanden.

### <a name="remarks"></a>Hinweise

Das Element ist möglicherweise nicht ausgewählt.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CListBox:: setcaretindex](#setcaretindex).

##  <a name="getcount"></a>CListBox:: GetCount

Ruft die Anzahl der Elemente in einem Listenfeld ab.

```
int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Listenfeld oder LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Die zurückgegebene Anzahl ist ein Wert größer als der Indexwert des letzten Elements (der Index ist NULL basiert).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>CListBox:: getcurrsel

Ruft ggf. den NULL basierten Index des aktuell ausgewählten Elements in einem Listenfeld mit einer einzelnen Auswahl ab.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des derzeit ausgewählten Elements, wenn es sich um ein Listenfeld mit einfacher Auswahl handelt. Es ist LB_ERR, wenn derzeit kein Element ausgewählt ist.

Der Index des Elements in einem Listenfeld mit Mehrfachauswahl, das den Fokus besitzt.

### <a name="remarks"></a>Hinweise

`GetCurSel` für ein Listenfeld mit Mehrfachauswahl nicht aufzurufen. Verwenden Sie stattdessen [CListBox:: getselitems](#getselitems) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>CListBox:: gethorizontalblock

Ruft die Breite in Pixel ab, um die ein horizontaler Bildlauf durchgeführt werden kann.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Rückgabewert

Die scrollbare Breite des Listen Felds in Pixel.

### <a name="remarks"></a>Hinweise

Dies gilt nur, wenn das Listenfeld eine horizontale Schiebe Leiste aufweist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>CListBox:: GetItemData

Ruft den von der Anwendung bereitgestellten Double Word-Wert ab, der dem angegebenen Listenfeld Element zugeordnet ist.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Elements im Listenfeld an.

### <a name="return-value"></a>Rückgabewert

Der Wert, der dem Element zugeordnet ist, oder LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Der Double Word-Wert war der *dwitemdata* -Parameter [eines-Aufrufes](#setitemdata) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>CListBox:: getitemdataptr

Ruft den von der Anwendung bereitgestellten 32-Bit-Wert ab, der dem angegebenen Listenfeld Element als Zeiger zugeordnet ist (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Elements im Listenfeld an.

### <a name="return-value"></a>Rückgabewert

Ruft einen Zeiger ab, oder-1, wenn ein Fehler auftritt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>CListBox:: GetItemHeight

Bestimmt die Höhe der Elemente in einem Listenfeld.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Elements im Listenfeld an. Dieser Parameter wird nur verwendet, wenn das Listenfeld den LBS_OWNERDRAWVARIABLE Stil hat. Andernfalls sollte der Wert auf 0 festgelegt werden.

### <a name="return-value"></a>Rückgabewert

Die Höhe der Elemente im Listenfeld in Pixel. Wenn das Listenfeld den [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil hat, ist der Rückgabewert die Höhe des durch *nIndex*angegebenen Elements. Wenn ein Fehler auftritt, wird der Rückgabewert LB_ERR.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>CListBox:: GetItemRect

Ruft die Abmessungen des Rechtecks ab, das ein Listenfeld Element umschließt, das gerade im Listenfeld Fenster angezeigt wird.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Elements an.

*lpRect*<br/>
Gibt einen Long-Zeiger auf eine [Rect-Struktur](/windows/win32/api/windef/ns-windef-rect) an, die die Listenfeld-Client Koordinaten des Elements empfängt.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>CListBox:: getlistboxinfo

Ruft die Anzahl der Elemente pro Spalte ab.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Rückgabewert

Anzahl von Elementen pro Spalte des `CListBox` Objekts.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion emuliert die Funktionalität der [LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo) Nachricht, wie in der Windows SDK beschrieben.

##  <a name="getlocale"></a>CListBox:: getLocale

Ruft das vom Listenfeld verwendete Gebiets Schema ab.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Rückgabewert

Der LCID-Wert (Locale Identifier) für die Zeichen folgen im Listenfeld.

### <a name="remarks"></a>Hinweise

Das Gebiets Schema wird z. b. verwendet, um die Sortierreihenfolge der Zeichen folgen in einem sortierten Listenfeld zu bestimmen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CListBox:: setlocale](#setlocale).

##  <a name="getsel"></a>CListBox:: GetSEL

Ruft den Auswahl Zustand eines Elements ab.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Elements an.

### <a name="return-value"></a>Rückgabewert

Eine positive Zahl, wenn das angegebene Element ausgewählt ist. Andernfalls ist der Wert 0. Der Rückgabewert ist LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion kann sowohl mit einzelnen als auch mit Mehrfachauswahl-Listenfeldern verwendet werden.

Verwenden Sie [CListBox:: getcurrsel](#getcursel), um den Index des aktuell ausgewählten Listenfeld Elements abzurufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>CListBox:: getselcount

Ruft die Gesamtanzahl der ausgewählten Elemente in einem Listenfeld mit Mehrfachauswahl ab.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl ausgewählter Elemente in einem Listenfeld. Wenn das Listenfeld ein Listenfeld für die einfache Auswahl ist, wird der Rückgabewert LB_ERR.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CListBox:: getselitems](#getselitems).

##  <a name="getselitems"></a>CListBox:: getselitems

Füllt einen Puffer mit einem Array von ganzen Zahlen, das die Element Nummern ausgewählter Elemente in einem Listenfeld mit Mehrfachauswahl angibt.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parameters

*nMaxItems*<br/>
Gibt die maximale Anzahl ausgewählter Elemente an, deren Element Nummer in den Puffer eingefügt werden soll.

*rgIndex*<br/>
Gibt einen Zeiger auf einen Puffer an, der groß genug für die Anzahl der von *nmaxitems*angegebenen ganzzahligen Elemente ist.

### <a name="return-value"></a>Rückgabewert

Die tatsächliche Anzahl der Elemente, die im Puffer abgelegt werden. Wenn das Listenfeld ein Listenfeld für die einfache Auswahl ist, wird der Rückgabewert `LB_ERR`.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>CListBox:: gettext

Ruft eine Zeichenfolge aus einem Listenfeld ab.

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index der abzurufenden Zeichenfolge an.

*lpszBuffer*<br/>
Verweist auf den Puffer, der die Zeichenfolge empfängt. Der Puffer muss über ausreichend Speicherplatz für die Zeichenfolge und ein abschließendes NULL-Zeichen verfügen. Die Größe der Zeichenfolge kann im Voraus durch Aufrufen der `GetTextLen` Member-Funktion bestimmt werden.

*rString*<br/>
Ein Verweis auf ein `CString`-Objekt.

### <a name="return-value"></a>Rückgabewert

Die Länge (in Byte) der Zeichenfolge ohne das abschließende Null Zeichen. Wenn *nIndex* keinen gültigen Index angibt, wird der Rückgabewert LB_ERR.

### <a name="remarks"></a>Hinweise

Die zweite Form dieser Member-Funktion füllt ein `CString`-Objekt mit dem Zeichen folgen Text.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>CListBox:: gettextlen

Ruft die Länge einer Zeichenfolge in einem Listenfeld Element ab.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index der Zeichenfolge an.

### <a name="return-value"></a>Rückgabewert

Die Länge der Zeichenfolge in Zeichen, ohne das abschließende Null Zeichen. Wenn *nIndex* keinen gültigen Index angibt, wird der Rückgabewert LB_ERR.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CListBox:: gettext](#gettext).

##  <a name="gettopindex"></a>CListBox:: gettopindex

Ruft den NULL basierten Index des ersten sichtbaren Elements in einem Listenfeld ab.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der null basierte Index des ersten sichtbaren Elements in einem Listenfeld, wenn erfolgreich, LB_ERR andernfalls.

### <a name="remarks"></a>Hinweise

Zuerst befindet sich Element 0 am oberen Rand des Listen Felds, aber wenn im Listenfeld ein Bildlauf durchgeführt wird, befindet sich möglicherweise ein anderes Element im oberen Bereich.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>CListBox:: InitStorage

Ordnet Speicher zum Speichern von Listenfeld Elementen zu.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parameters

*nItems*<br/>
Gibt die Anzahl der hinzu zufügenden Elemente an.

*nBytes*<br/>
Gibt die Größe des Arbeitsspeichers in Bytes an, der für Element Zeichenfolgen belegt werden soll.

### <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung ist die maximale Anzahl von Elementen, die im Listenfeld gespeichert werden können, bevor eine Speicher Belegungs Zuordnung erforderlich ist, andernfalls LB_ERRSPACE, was bedeutet, dass nicht genügend Arbeitsspeicher verfügbar ist.

### <a name="remarks"></a>Hinweise

Diese Funktion wird aufgerufen, bevor einer `CListBox`eine große Anzahl von Elementen hinzugefügt wird.

Diese Funktion beschleunigt die Initialisierung von Listenfeldern, die über eine große Anzahl von Elementen verfügen (mehr als 100). Dadurch wird die angegebene Arbeitsspeicher Menge vorab zugeordnet, sodass nachfolgende [AddString](#addstring)-, [InsertString](#insertstring)-und [dir](#dir) -Funktionen die kürzeste mögliche Zeit beanspruchen. Sie können Schätzwerte für die Parameter verwenden. Wenn Sie den Wert überschätzen, wird ein zusätzlicher Arbeitsspeicher zugewiesen. Wenn Sie unterschätzen, wird die normale Zuordnung für Elemente verwendet, die den vorab zugeordneten Betrag überschreiten.

Nur Windows 95/98: Der *nitems* -Parameter ist auf 16-Bit-Werte beschränkt. Dies bedeutet, dass Listenfelder nicht mehr als 32.767 Elemente enthalten dürfen. Obwohl die Anzahl der Elemente eingeschränkt ist, wird die Gesamtgröße der Elemente in einem Listenfeld nur durch den verfügbaren Arbeitsspeicher beschränkt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>CListBox:: InsertString

Fügt eine Zeichenfolge in das Listenfeld ein.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index der Position an, an der die Zeichenfolge eingefügt werden soll. Wenn dieser Parameter-1 ist, wird die Zeichenfolge am Ende der Liste hinzugefügt.

*lpszItem*<br/>
Zeigt auf die einzufügende nullterminierte Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index der Position, an der die Zeichenfolge eingefügt wurde. Der Rückgabewert ist LB_ERR, wenn ein Fehler auftritt. der Rückgabewert ist LB_ERRSPACE, wenn nicht genügend Speicherplatz zum Speichern der neuen Zeichenfolge zur Verfügung steht.

### <a name="remarks"></a>Hinweise

Anders als bei der Member-Funktion von [AddString](#addstring) bewirkt `InsertString` nicht, dass eine Liste mit dem [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Format sortiert wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>CListBox:: itemfrompoint

Bestimmt das Listenfeld Element, das dem in *PT*angegebenen Punkt am nächsten liegt.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parameters

*pt*<br/>
Der Punkt, an dem das nächste Element gesucht werden soll, das relativ zur oberen linken Ecke des Client Bereichs des Listen Felds angegeben wird.

*bOutside*<br/>
Verweis auf eine boolesche Variable, die auf true festgelegt wird, wenn *PT* außerhalb des Client Bereichs des Listen Felds liegt, false, wenn *PT* im Client Bereich des Listen Felds liegt.

### <a name="return-value"></a>Rückgabewert

Der Index des nächstgelegenen Elements bis zu dem in *PT*angegebenen Punkt.

### <a name="remarks"></a>Hinweise

Sie können diese Funktion verwenden, um zu bestimmen, welches Listenfeld Element der Mauszeiger bewegt.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CListBox::](#setanchorindex)"".

##  <a name="measureitem"></a>CListBox:: MeasureItem

Wird von Framework aufgerufen, wenn ein Listenfeld mit einer Art von Besitzer Zeichenfolge erstellt wird.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parameters

*lpMeasureItemStruct*<br/>
Ein langer Zeiger auf eine [measureitemstruct](/windows/win32/api/winuser/ns-winuser-measureitemstruct) -Struktur.

### <a name="remarks"></a>Hinweise

Standardmäßig führt diese Member-Funktion keine Aktion aus. Überschreiben Sie diese Member-Funktion, und füllen Sie die `MEASUREITEMSTRUCT`-Struktur aus, um Fenster über die Listenfeld Dimensionen zu informieren. Wenn das Listenfeld mit dem [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) -Format erstellt wird, ruft das Framework diese Member-Funktion für jedes Element im Listenfeld auf. Andernfalls wird dieser Member nur einmal aufgerufen.

Weitere Informationen zur Verwendung des [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Formats in einem mit der `SubclassDlgItem` Member-Funktion von `CWnd`erstellten -Stil finden Sie in der [technischen Notiz 14](../../mfc/tn014-custom-controls.md).

Eine Beschreibung der `MEASUREITEMSTRUCT` Struktur finden Sie unter [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>CListBox:: resetcontent

Entfernt alle Elemente aus einem Listenfeld.

```
void ResetContent();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>CListBox:: SelectString

Sucht nach einem Listenfeld Element, das mit der angegebenen Zeichenfolge übereinstimmt, und wenn ein übereinstimmendes Element gefunden wird, wird das Element ausgewählt.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parameters

*nStartAfter*<br/>
Enthält den NULL basierten Index des Elements vor dem ersten zu durchsuchenden Element. Wenn die Suche das Ende des Listen Felds erreicht, wird Sie vom oberen Rand des Listen Felds zurück zu dem durch *nstartafter*angegebenen Element. Wenn *nstartafter* den Wert-1 hat, wird das gesamte Listenfeld von Anfang an durchsucht.

*lpszItem*<br/>
Verweist auf die auf NULL endenden Zeichenfolge, die das Präfix enthält, nach dem gesucht werden soll. Die Suche erfolgt unabhängig von der Groß-/Kleinschreibung, sodass diese Zeichenfolge eine beliebige Kombination von Groß-und Kleinbuchstaben enthalten kann.

### <a name="return-value"></a>Rückgabewert

Der Index des ausgewählten Elements, wenn die Suche erfolgreich war. Wenn die Suche nicht erfolgreich war, wird der Rückgabewert LB_ERR, und die aktuelle Auswahl wird nicht geändert.

### <a name="remarks"></a>Hinweise

Das Listenfeld wird ggf. mit einem Bildlauf ausgeführt, um das ausgewählte Element in der Ansicht anzuzeigen.

Diese Member-Funktion kann nicht mit einem Listenfeld verwendet werden, das den [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil aufweist.

Ein Element wird nur ausgewählt, wenn die Anfangs Zeichen (vom Startpunkt) mit den Zeichen in der durch *lpszitem*angegebenen Zeichenfolge verglichen werden.

Verwenden Sie die `FindString` Member-Funktion, um eine Zeichenfolge zu suchen, ohne das Element auszuwählen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>CListBox:: selitemrange

Wählt mehrere aufeinander folgende Elemente in einem Listenfeld mit Mehrfachauswahl aus.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parameters

*bSelect*<br/>
Gibt an, wie die Auswahl festgelegt wird. Wenn *bSelect* den Wert true hat, wird die Zeichenfolge ausgewählt und hervorgehoben. Wenn der Wert false ist, wird die Hervorhebung entfernt, und die Zeichenfolge ist nicht mehr ausgewählt.

*nFirstItem*<br/>
Gibt den NULL basierten Index des ersten festzulegenden Elements an.

*nLastItem*<br/>
Gibt den NULL basierten Index des letzten festzulegenden Elements an.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Verwenden Sie diese Member-Funktion nur für Listenfelder mit Mehrfachauswahl. Wenn Sie nur ein Element in einem Listenfeld mit Mehrfachauswahl auswählen müssen – d. h., wenn *nfirstitem* gleich *nlastitem* ist – wird stattdessen die Member-Funktion [SetSel](#setsel) aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>CListBox:: "Ziel Index Index"

Legt den Anker in einem Listenfeld Mehrfachauswahl fest, um eine erweiterte Auswahl zu beginnen.

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Listenfeld Elements an, das als Anker verwendet werden soll.

### <a name="remarks"></a>Hinweise

Im Listenfeld Mehrfachauswahl ist das Anker Element das erste oder letzte Element in einem Block zusammenhängender ausgewählter Elemente.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>CListBox:: setcaretindex

Legt das Fokus Rechteck auf das Element am angegebenen Index in einem Mehrfachauswahl-Listenfeld fest.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Elements an, das das Fokus Rechteck im Listenfeld erhalten soll.

*bScroll*<br/>
Wenn dieser Wert 0 ist, wird das Element gescrollt, bis es vollständig sichtbar ist. Wenn dieser Wert nicht 0 ist, wird das Element gescrollt, bis es mindestens teilweise sichtbar ist.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Wenn das Element nicht sichtbar ist, wird es in die Ansicht gescrollt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>CListBox:: setcolumnwidth

Legt die Breite aller Spalten in einem mehrspaltigen Listenfeld (erstellt mit dem [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil) in Pixel fest.

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parameters

*cxWidth*<br/>
Gibt die Breite aller Spalten in Pixel an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>CListBox:: setcurrsel

Wählt eine Zeichenfolge aus und führt ggf. einen Bildlauf in die Ansicht aus.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parameters

*nWählen*<br/>
Gibt den NULL basierten Index der auszuwählenden Zeichenfolge an. Wenn *nselect* den Wert-1 hat, ist das Listenfeld auf keine Auswahl festgelegt.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Wenn die neue Zeichenfolge ausgewählt ist, wird die Hervorhebung im Listenfeld aus der zuvor ausgewählten Zeichenfolge entfernt.

Verwenden Sie diese Member-Funktion nur für Listenfelder mit einfacher Auswahl.

Verwenden Sie [CListBox:: SetSel](#setsel), um eine Auswahl in einem Listenfeld Mehrfachauswahl festzulegen oder zu entfernen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>CListBox:: Abbild-Bereich

Legt die Breite (in Pixel) fest, um die ein Listenfeld horizontal gescrollt werden kann.

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parameters

*cxblock*<br/>
Gibt die Anzahl der Pixel an, um die das Listenfeld horizontal gescrollt werden kann.

### <a name="remarks"></a>Hinweise

Wenn die Größe des Listen Felds kleiner ist als dieser Wert, führt die horizontale Schiebe Leiste im Listenfeld einen horizontalen Bildlauf durch. Wenn das Listenfeld groß oder größer als dieser Wert ist, wird die horizontale Schiebe Leiste ausgeblendet.

Um auf einen `SetHorizontalExtent`aufzurufen, muss das Listenfeld mit der [WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) Formatvorlage definiert worden sein.

Diese Member-Funktion ist für Listenfelder mit mehreren Spalten nicht nützlich. Bei mehrspaltigen Listenfeldern wird die `SetColumnWidth` Member-Funktion aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>CListBox:: Daten

Legt einen Wert fest, der dem angegebenen Element in einem Listenfeld zugeordnet ist.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Elements an.

*dwItemData*<br/>
Gibt den Wert an, der dem Element zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>CListBox:: Ziel-DataPtr

Legt den 32-Bit-Wert, der dem angegebenen Element in einem Listenfeld zugeordnet ist, als den angegebenen Zeiger fest ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Elements an.

*pData*<br/>
Gibt den Zeiger an, der dem Element zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Dieser Zeiger bleibt für die Lebensdauer des Listen Felds gültig, auch wenn die relative Position des Elements im Listenfeld geändert werden kann, wenn Elemente hinzugefügt oder entfernt werden. Daher kann der Index des Elements innerhalb des Felds geändert werden, aber der Zeiger bleibt zuverlässig.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>CListBox:: Sekunden-Höhe

Legt die Höhe von Elementen in einem Listenfeld fest.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Elements im Listenfeld an. Dieser Parameter wird nur verwendet, wenn das Listenfeld den LBS_OWNERDRAWVARIABLE Stil hat. Andernfalls sollte der Wert auf 0 festgelegt werden.

*cyItemHeight*<br/>
Gibt die Höhe des Elements in Pixel an.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn der Index oder die Höhe ungültig ist.

### <a name="remarks"></a>Hinweise

Wenn das Listenfeld den [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil hat, legt diese Funktion die Höhe des durch *nIndex*angegebenen Elements fest. Andernfalls legt diese Funktion die Höhe aller Elemente im Listenfeld fest.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>CListBox:: setlocale

Legt den Gebiets Schema Bezeichner für dieses Listenfeld fest.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parameters

*nNewLocale*<br/>
Der neue LCID-Wert (Locale Identifier), der für das Listenfeld festgelegt werden soll.

### <a name="return-value"></a>Rückgabewert

Der vorherige LCID-Wert (Locale Identifier) für dieses Listenfeld.

### <a name="remarks"></a>Hinweise

Wenn `SetLocale` nicht aufgerufen wird, wird das Standard Gebiets Schema vom System abgerufen. Dieses Standard Gebiets Schema für das System kann mithilfe der regionalen (oder internationalen) Anwendung der Systemsteuerung geändert werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>CListBox:: Sekunden

Wählt eine Zeichenfolge in einem Listenfeld mit Mehrfachauswahl aus.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Enthält den NULL basierten Index der festzulegenden Zeichenfolge. Wenn-1, wird die Auswahl in Abhängigkeit vom Wert von *bSelect*zu allen Zeichen folgen hinzugefügt bzw. aus ihr entfernt.

*bSelect*<br/>
Gibt an, wie die Auswahl festgelegt wird. Wenn *bSelect* den Wert true hat, wird die Zeichenfolge ausgewählt und hervorgehoben. Wenn der Wert false ist, wird die Hervorhebung entfernt, und die Zeichenfolge ist nicht mehr ausgewählt. Die angegebene Zeichenfolge wird standardmäßig ausgewählt und hervorgehoben.

### <a name="return-value"></a>Rückgabewert

LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Verwenden Sie diese Member-Funktion nur für Listenfelder mit Mehrfachauswahl.

Verwenden Sie [CListBox:: setcurrsel](#setcursel), um ein Element aus einem Listenfeld mit einer einzelnen Auswahl auszuwählen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>CListBox:: settabstopps

Legt die Position der Tabstopps in einem Listenfeld fest.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parameters

*cxeachstopps*<br/>
Tabstopps werden bei jeder *cxeachstopp* -Dialog Einheit festgelegt. Unter *rgtabstopps* finden Sie eine Beschreibung einer Dialogfeld Einheit.

*nTabStops*<br/>
Gibt die Anzahl von Tabstopps an, die im Listenfeld enthalten sein sollen.

*rgTabStops*<br/>
Verweist auf das erste Element eines Arrays von ganzen Zahlen, das die Position der Tabstopps in Dialogfeld Einheiten enthält. Eine Dialog Einheit ist ein horizontaler oder vertikaler Abstand. Eine horizontale Dialog Einheit ist gleich 1-vierte der aktuellen Dialogfeld Basis-breiten Einheit, und eine vertikale Dialog Einheit ist gleich einem Achtel der aktuellen Dialogfeld-Basis Höheneinheit. Die Dialog Basiseinheiten werden basierend auf der Höhe und der Breite der aktuellen System Schriftart berechnet. Die `GetDialogBaseUnits` Windows-Funktion gibt die aktuellen Dialog Basiseinheiten des Dialog Felds in Pixel zurück. Die Tabstopps müssen in steigender Reihenfolge sortiert werden. zurück-Registerkarten sind nicht zulässig.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn alle Registerkarten festgelegt wurden. andernfalls 0.

### <a name="remarks"></a>Hinweise

Um Tabstopps auf die Standardgröße von 2 Dialog Einheiten festzulegen, nennen Sie die Parameter lose Version dieser Member-Funktion. Um Tabstopps auf eine andere Größe als 2 festzulegen, müssen Sie die Version mit dem *cxeachstopp* -Argument aufzurufen.

Um Tabstopps auf ein Array von Größen festzulegen, verwenden Sie die-Version mit den Argumenten *rgtabstopps* und *ntabstopps* . Ein Tabstopp wird für jeden Wert in *rgtabstopps*festgelegt, bis zu der Anzahl, die von *ntabstopps*angegeben wird.

Um auf einen aufzurufenden `SetTabStops` Member-Funktion zu reagieren, muss das Listenfeld mit der [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Formatvorlage erstellt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>CListBox:: settopindex

Stellt sicher, dass ein bestimmtes Listenfeld Element sichtbar ist.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Gibt den NULL basierten Index des Listenfeld Elements an.

### <a name="return-value"></a>Rückgabewert

NULL, wenn erfolgreich, oder LB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Das System führt einen Bildlauf durch das Listenfeld durch, bis entweder das von *nIndex* angegebene Element oben im Listenfeld angezeigt wird oder der maximale scrollbereich erreicht wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>CListBox:: vkeytoitem

Wird von Framework aufgerufen, wenn das übergeordnete Fenster des Listen Felds eine WM_VKEYTOITEM Meldung aus dem Listenfeld empfängt.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parameters

*nKey*<br/>
Der Code des virtuellen Schlüssels der vom Benutzer gedrückten Taste. Eine Liste der virtuellen Standardschlüssel Codes finden Sie unter Winuser. h.

*nIndex*<br/>
Die aktuelle Position der Listenfeld Einfügemarke.

### <a name="return-value"></a>Rückgabewert

Gibt-2 für keine weitere Aktion,-1 für die Standardaktion oder eine nicht negative Zahl zurück, um einen Index eines Listenfeld Elements anzugeben, für das die Standardaktion für den Tastatur Strich ausgeführt werden soll.

### <a name="remarks"></a>Hinweise

Die WM_VKEYTOITEM Meldung wird vom Listenfeld gesendet, wenn eine WM_KEYDOWN Meldung empfangen wird. Dies ist jedoch nur möglich, wenn das Listenfeld beide der folgenden Punkte erfüllt:

- Hat den [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) Stil festgelegt.

- Weist mindestens ein Element auf.

Sie sollten diese Funktion niemals selbst aufzurufen. Überschreiben Sie diese Funktion, um eine eigene benutzerdefinierte Behandlung von Tastatur Meldungen bereitzustellen.

Sie müssen einen Wert zurückgeben, um das Framework darüber zu informieren, welche Aktion Sie durchgeführt haben. Der Rückgabewert-2 gibt an, dass die Anwendung alle Aspekte der Elementauswahl behandelt hat und keine weitere Aktion im Listenfeld erfordert. Vor der Rückgabe von-2 konnten Sie die Auswahl festlegen oder die Einfügemarke oder beides verschieben. Verwenden Sie [setcurrsel](#setcursel) oder [SetSel](#setsel), um die Auswahl festzulegen. Verwenden Sie [setcaretindex](#setcaretindex), um die Einfügemarke zu verschieben.

Der Rückgabewert-1 gibt an, dass das Listenfeld die Standardaktion als Reaktion auf den Tastatur Strich ausführen soll. Die Standard Implementierung gibt-1 zurück.

Ein Rückgabewert von 0 (null) oder größer gibt den Index eines Elements im Listenfeld an und gibt an, dass im Listenfeld die Standardaktion für den Tastatur Strich für das angegebene Element ausgeführt werden soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit-Klasse](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar-Klasse](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic-Klasse](../../mfc/reference/cstatic-class.md)
