---
title: CComboBox-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
ms.openlocfilehash: df935bb924c7d8908b1166852dc553a73fc71ff3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369514"
---
# <a name="ccombobox-class"></a>CComboBox-Klasse

Stellt die Funktionalität eines Windows-Kombinationsfelds bereit.

## <a name="syntax"></a>Syntax

```
class CComboBox : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComboBox::CComboBox](#ccombobox)|Erstellt ein `CComboBox`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComboBox:: AddString](#addstring)|Fügt eine Zeichenfolge am Ende der Liste im Listenfeld eines Kombinationsfelds oder an der sortierten Position für Listenfelder mit dem Stil CBS_SORT hinzu.|
|[CComboBox::Löschen](#clear)|Löscht (löscht) die aktuelle Auswahl, falls vorhanden, im Bearbeitungssteuerelement.|
|[CComboBox::CompareItem](#compareitem)|Wird vom Framework aufgerufen, um die relative Position eines neuen Listenelements in einem sortierten, vom Besitzer gezeichneten Kombinationsfeld zu bestimmen.|
|[CComboBox::Kopieren](#copy)|Kopiert die aktuelle Auswahl,, falls vorhanden, in die Zwischenablage im CF_TEXT Format.|
|[CComboBox::Erstellen](#create)|Erstellt das Kombinationsfeld und `CComboBox` fügt es an das Objekt an.|
|[CComboBox::Schnitt](#cut)|Löscht (schneidet) die aktuelle Auswahl,, falls vorhanden, im Bearbeitungssteuerelement und kopiert den gelöschten Text in der Zwischenablage im CF_TEXT Format.|
|[CComboBox::DeleteItem](#deleteitem)|Wird vom Framework aufgerufen, wenn ein Listenelement aus einem vom Besitzer gezeichneten Kombinationsfeld gelöscht wird.|
|[CComboBox::DeleteString](#deletestring)|Löscht eine Zeichenfolge aus dem Listenfeld eines Kombinationsfelds.|
|[CComboBox::Dir](#dir)|Fügt dem Listenfeld eines Kombinationsfelds eine Liste mit Dateinamen hinzu.|
|[CComboBox::DrawItem](#drawitem)|Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines vom Besitzer gezeichneten Kombinationsfelds ändert.|
|[CComboBox::FindString](#findstring)|Sucht die erste Zeichenfolge, die das angegebene Präfix im Listenfeld eines Kombinationsfelds enthält.|
|[CComboBox::FindStringExact](#findstringexact)|Sucht die erste Listenfeldzeichenfolge (in einem Kombinationsfeld), die mit der angegebenen Zeichenfolge übereinstimmt.|
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Ruft Informationen zum `CComboBox` Objekt ab.|
|[CComboBox::GetCount](#getcount)|Ruft die Anzahl der Elemente im Listenfeld eines Kombinationsfelds ab.|
|[CComboBox::GetCueBanner](#getcuebanner)|Ruft den Cue-Text ab, der für ein Kombinationsfeldsteuerelement angezeigt wird.|
|[CComboBox::GetCurSel](#getcursel)|Ruft den Index des aktuell ausgewählten Elements (falls vorhanden) im Listenfeld eines Kombinationsfelds ab.|
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Ruft die Bildschirmkoordinaten des sichtbaren (nach unten fallengelassenen) Listenfelds eines Dropdown-Kombinationsfelds ab.|
|[CComboBox::GetDroppedState](#getdroppedstate)|Bestimmt, ob das Listenfeld eines Dropdown-Kombinationsfelds sichtbar ist (nach unten fallen gelassen).|
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Ruft die minimale zulässige Breite für den Dropdown-Listenfeldteil eines Kombinationsfelds ab.|
|[CComboBox::GetEditSel](#geteditsel)|Ruft die Anfangs- und Endzeichenpositionen der aktuellen Auswahl im Bearbeitungssteuerelement eines Kombinationsfelds ab.|
|[CComboBox::GetExtendedUI](#getextendedui)|Bestimmt, ob ein Kombinationsfeld über die Standardbenutzeroberfläche oder die erweiterte Benutzeroberfläche verfügt.|
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Gibt die Breite in Pixel zurück, in der der Listenfeldteil des Kombinationsfelds horizontal gescrollt werden kann.|
|[CComboBox::GetItemData](#getitemdata)|Ruft den von der Anwendung bereitgestellten 32-Bit-Wert ab, der dem angegebenen Kombinationsfeldelement zugeordnet ist.|
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Ruft den von der Anwendung bereitgestellten 32-Bit-Zeiger ab, der dem angegebenen Kombinationsfeldelement zugeordnet ist.|
|[CComboBox::GetItemHeight](#getitemheight)|Ruft die Höhe von Listenelementen in einem Kombinationsfeld ab.|
|[CComboBox::GetLBText](#getlbtext)|Ruft eine Zeichenfolge aus dem Listenfeld eines Kombinationsfelds ab.|
|[CComboBox::GetLBTextLen](#getlbtextlen)|Ruft die Länge einer Zeichenfolge im Listenfeld eines Kombinationsfelds ab.|
|[CComboBox::GetLocale](#getlocale)|Ruft den Gebietsschemabezeichner für ein Kombinationsfeld ab.|
|[CComboBox::GetMinVisible](#getminvisible)|Ruft die minimale Anzahl sichtbarer Elemente in der Dropdownliste des aktuellen Kombinationsfelds ab.|
|[CComboBox::GetTopIndex](#gettopindex)|Gibt den Index des ersten sichtbaren Elements im Listenfeldteil des Kombinationsfelds zurück.|
|[CComboBox::InitStorage](#initstorage)|Ordnet Speicherblöcke für Elemente und Zeichenfolgen im Listenfeldteil des Kombinationsfelds vorab zu.|
|[CComboBox::InsertString](#insertstring)|Fügt eine Zeichenfolge in das Listenfeld eines Kombinationsfelds ein.|
|[CComboBox::LimitText](#limittext)|Beschränkt die Länge des Textes, den der Benutzer in das Bearbeitungssteuerelement eines Kombinationsfelds eingeben kann.|
|[CComboBox::MeasureItem](#measureitem)|Wird vom Framework aufgerufen, um Kombinationsfelddimensionen zu bestimmen, wenn ein vom Besitzer gezeichnetes Kombinationsfeld erstellt wird.|
|[CComboBox::Paste](#paste)|Fügt die Daten aus der Zwischenablage in das Bearbeitungssteuerelement an der aktuellen Cursorposition ein. Daten werden nur eingefügt, wenn die Zwischenablage Daten im CF_TEXT-Format enthält.|
|[CComboBox::ResetContent](#resetcontent)|Entfernt alle Elemente aus dem Listenfeld und bearbeitet die Steuerung eines Kombinationsfelds.|
|[CComboBox::SelectString](#selectstring)|Sucht im Listenfeld eines Kombinationsfelds nach einer Zeichenfolge, und wenn die Zeichenfolge gefunden wird, wählt sie die Zeichenfolge im Listenfeld aus und kopiert die Zeichenfolge in das Bearbeitungssteuerelement.|
|[CComboBox::SetCueBanner](#setcuebanner)|Legt den Cue-Text fest, der für ein Kombinationsfeldsteuerelement angezeigt wird.|
|[CComboBox::SetCurSel](#setcursel)|Wählt eine Zeichenfolge im Listenfeld eines Kombinationsfelds aus.|
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Legt die minimale zulässige Breite für den Dropdown-Listenfeldteil eines Kombinationsfelds fest.|
|[CComboBox::SetEditSel](#seteditsel)|Wählt Zeichen im Bearbeitungssteuerelement eines Kombinationsfelds aus.|
|[CComboBox::SetExtendedUI](#setextendedui)|Wählt entweder die Standardbenutzeroberfläche oder die erweiterte Benutzeroberfläche für ein Kombinationsfeld mit dem CBS_DROPDOWN oder CBS_DROPDOWNLIST Stil aus.|
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Legt die Breite in Pixel fest, mit der der Listenfeldteil des Kombinationsfelds horizontal gescrollt werden kann.|
|[CComboBox::SetItemData](#setitemdata)|Legt den 32-Bit-Wert fest, der dem angegebenen Element in einem Kombinationsfeld zugeordnet ist.|
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Legt den 32-Bit-Zeiger fest, der dem angegebenen Element in einem Kombinationsfeld zugeordnet ist.|
|[CComboBox::SetItemHeight](#setitemheight)|Legt die Höhe von Listenelementen in einem Kombinationsfeld oder die Höhe des Abschnitts "Bearbeiten-Steuerelement" (oder statischen Text) eines Kombinationsfelds fest.|
|[CComboBox::SetLocale](#setlocale)|Legt den Gebietsschemabezeichner für ein Kombinationsfeld fest.|
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Legt die minimale Anzahl sichtbarer Elemente in der Dropdownliste des aktuellen Kombinationsfelds fest.|
|[CComboBox::SetTopIndex](#settopindex)|Weist den Listenfeldteil des Kombinationsfelds an, das Element mit dem angegebenen Index oben anzuzeigen.|
|[CComboBox::ShowDropDown](#showdropdown)|Zeigt das Listenfeld eines Kombinationsfelds mit dem Format CBS_DROPDOWN oder CBS_DROPDOWNLIST ein oder blendet es aus.|

## <a name="remarks"></a>Bemerkungen

Ein Kombinationsfeld besteht aus einem Listenfeld, das entweder mit einem statischen Steuerelement oder einem Bearbeitungssteuerelement kombiniert wird. Der Listenfeldteil des Steuerelements kann jederzeit angezeigt werden oder nur dann herunterfallen, wenn der Benutzer den Dropdownpfeil neben dem Steuerelement auswählt.

Das aktuell ausgewählte Element (falls vorhanden) im Listenfeld wird im statischen oder Bearbeitungssteuerelement angezeigt. Wenn das Kombinationsfeld den Dropdownlistenstil hat, kann der Benutzer außerdem das Anfangszeichen eines der Elemente in der Liste eingeben, und das Listenfeld wird, falls sichtbar, das nächste Element mit diesem Anfangszeichen hervorgehoben.

In der folgenden Tabelle werden [styles](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)die drei Kombinationsfeldstile verglichen.

|Stil|Wann ist das Listenfeld sichtbar?|Statisches oder Bearbeitungssteuerelement|
|-----------|-------------------------------|-----------------------------|
|Einfach|Always|Edit (Bearbeiten)|
|Drop-down|Wenn sie heruntergelassen werden|Edit (Bearbeiten)|
|Dropdownliste|Wenn sie heruntergelassen werden|statischen|

Sie können `CComboBox` ein Objekt entweder aus einer Dialogfeldvorlage oder direkt im Code erstellen. Rufen Sie in beiden Fällen `CComboBox` zuerst `CComboBox` den Konstruktor auf, um das Objekt zu erstellen. rufen Sie dann die [Memberfunktion Erstellen](#create) auf, `CComboBox` um das Steuerelement zu erstellen und es an das Objekt anzufügen.

Wenn Sie Windows-Benachrichtigungen verarbeiten möchten, die von einem Kombinationsfeld an das übergeordnete Element gesendet werden (in der Regel eine von `CDialog`abgeleitete Klasse), fügen Sie der übergeordneten Klasse für jede Nachricht einen Nachrichtenzuordnungseintrag und eine Message-Handler-Memberfunktion hinzu.

Jeder Nachrichtenzuordnungseintrag hat die folgende Form:

**\_ON-Benachrichtigung**_Notification_ **(** _id_, _memberFxn_ **)**

wobei `id` die untergeordnete Fenster-ID des Kombinationsfeldsteuerelements `memberFxn` angegeben wird, das die Benachrichtigung sendet, und der Name der übergeordneten Memberfunktion ist, die Sie geschrieben haben, um die Benachrichtigung zu behandeln.

Der Funktionsprototyp des Übergeordneten ist wie folgt:

**afx_msg** `void` afx_msg `memberFxn` **( );**

Die Reihenfolge, in der bestimmte Benachrichtigungen gesendet werden, kann nicht vorhergesagt werden. Insbesondere kann eine CBN_SELCHANGE Benachrichtigung entweder vor oder nach einer CBN_CLOSEUP Benachrichtigung erfolgen.

Potenzielle Nachrichtenzuordnungseinträge sind die folgenden:

- ON_CBN_CLOSEUP (Windows 3.1 und höher)) Das Listenfeld eines Kombinationsfelds wurde geschlossen. Diese Benachrichtigung wird nicht für ein Kombinationsfeld mit dem [Stil CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) gesendet.

- ON_CBN_DBLCLK Der Benutzer doppelklickt im Listenfeld eines Kombinationsfelds auf eine Zeichenfolge. Diese Benachrichtigung wird nur für ein Kombinationsfeld mit dem Stil CBS_SIMPLE gesendet. Bei einem Kombinationsfeld mit dem [Format stil CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) oder [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) kann kein Doppelklick ausgeführt werden, da mit einem einzigen Klick das Listenfeld ausgeblendet wird.

- ON_CBN_DROPDOWN Das Listenfeld eines Kombinationsfelds wird heruntergelassen (sichtbar gemacht). Diese Benachrichtigung kann nur für ein Kombinationsfeld mit dem Stil CBS_DROPDOWN oder CBS_DROPDOWNLIST auftreten.

- ON_CBN_EDITCHANGE Der Benutzer hat eine Aktion ausgeführt, die den Text im Abschnitt "Bearbeiten- und Steuerelement" eines Kombinationsfelds geändert haben könnte. Im Gegensatz zur CBN_EDITUPDATE Nachricht wird diese Nachricht gesendet, nachdem Windows den Bildschirm aktualisiert hat. Es wird nicht gesendet, wenn das Kombinationsfeld den CBS_DROPDOWNLIST Stil hat.

- ON_CBN_EDITUPDATE Der Bearbeitungssteuerungsteil eines Kombinationsfelds wird geänderten Text anzeigen. Diese Benachrichtigung wird gesendet, nachdem das Steuerelement den Text formatiert hat, aber bevor der Text angezeigt wird. Es wird nicht gesendet, wenn das Kombinationsfeld den CBS_DROPDOWNLIST Stil hat.

- ON_CBN_ERRSPACE Das Kombinationsfeld kann nicht genügend Arbeitsspeicher zuweisen, um eine bestimmte Anforderung zu erfüllen.

- ON_CBN_SELENDCANCEL (Windows 3.1 und höher) Gibt an, dass die Auswahl des Benutzers abgebrochen werden soll. Der Benutzer klickt auf ein Element und dann auf ein anderes Fenster oder Steuerelement, um das Listenfeld eines Kombinationsfelds auszublenden. Diese Benachrichtigung wird vor dem CBN_CLOSEUP Benachrichtigung gesendet, um anzugeben, dass die Auswahl des Benutzers ignoriert werden soll. Die CBN_SELENDCANCEL oder CBN_SELENDOK Benachrichtigungwirdwird, auch wenn die CBN_CLOSEUP Benachrichtigung s/ nicht gesendet wird (wie im Fall eines Kombinationsfelds mit dem Format CBS_SIMPLE).

- ON_CBN_SELENDOK Der Benutzer wählt ein Element aus und drückt dann entweder die ENTER-Taste oder klickt auf die DOWN ARROW-Taste, um das Listenfeld eines Kombinationsfelds auszublenden. Diese Benachrichtigung wird vor der CBN_CLOSEUP Nachricht gesendet, um anzugeben, dass die Auswahl des Benutzers als gültig betrachtet werden soll. Die CBN_SELENDCANCEL oder CBN_SELENDOK Benachrichtigungwirdwird, auch wenn die CBN_CLOSEUP Benachrichtigung s/ nicht gesendet wird (wie im Fall eines Kombinationsfelds mit dem Format CBS_SIMPLE).

- ON_CBN_KILLFOCUS Das Kombinationsfeld verliert den Eingabefokus.

- ON_CBN_SELCHANGE Die Auswahl im Listenfeld eines Kombinationsfelds wird geändert, da der Benutzer entweder in das Listenfeld klickt oder die Auswahl mithilfe der Pfeiltasten ändert. Bei der Verarbeitung dieser Nachricht kann der Text im Bearbeitungssteuerelement `GetLBText` des Kombinationsfelds nur über oder eine andere ähnliche Funktion abgerufen werden. `GetWindowText`kann nicht verwendet werden.

- ON_CBN_SETFOCUS Das Kombinationsfeld empfängt den Eingabefokus.

Wenn Sie `CComboBox` ein Objekt in einem Dialogfeld (über eine Dialogfeldressource) erstellen, wird das `CComboBox` Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie ein `CComboBox` Objekt in ein anderes Fensterobjekt einbetten, müssen Sie es nicht zerstören. Wenn Sie `CComboBox` das Objekt auf dem Stapel erstellen, wird es automatisch zerstört. Wenn Sie `CComboBox` das Objekt auf dem Heap mithilfe der **neuen** Funktion erstellen, müssen Sie **das Objekt** löschen aufrufen, um es zu zerstören, wenn das Windows-Kombinationsfeld zerstört wird.

**Hinweis** Wenn Sie WM_KEYDOWN- und WM_CHAR-Nachrichten verarbeiten möchten, müssen Sie die Bearbeitungs- und Listenfeldsteuerelemente des Kombinationsfelds unterklassieren, Klassen von `CEdit` und `CListBox`ableiten und Handler für diese Nachrichten zu den abgeleiteten Klassen hinzufügen. Weitere Informationen finden Sie unter [CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a>CComboBox::AddString

Fügt dem Listenfeld eines Kombinationsfelds eine Zeichenfolge hinzu.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parameter

*lpszString*<br/>
Zeigt auf die null-terminierte Zeichenfolge, die hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn der Rückgabewert größer oder gleich 0 ist, ist er der nullbasierte Index für die Zeichenfolge im Listenfeld. Der Rückgabewert ist CB_ERR wenn ein Fehler auftritt. Der Rückgabewert ist CB_ERRSPACE, wenn nicht genügend Speicherplatz zum Speichern der neuen Zeichenfolge verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Wenn das Listenfeld nicht mit dem [Stil CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) erstellt wurde, wird die Zeichenfolge am Ende der Liste hinzugefügt. Andernfalls wird die Zeichenfolge in die Liste eingefügt, und die Liste wird sortiert.

> [!NOTE]
> Diese Funktion wird vom `ComboBoxEx` Windows-Steuerelement nicht unterstützt. Weitere Informationen zu diesem Steuerelement finden Sie unter [ComboBoxEx-Steuerelemente](/windows/win32/Controls/comboboxex-controls) im Windows SDK.

Um eine Zeichenfolge an einer bestimmten Position [InsertString](#insertstring) in der Liste einzufügen, verwenden Sie die InsertString-Memberfunktion.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a>CComboBox::CComboBox

Erstellt ein `CComboBox`-Objekt.

```
CComboBox();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a>CComboBox::Löschen

Löscht (löscht) die aktuelle Auswahl, falls vorhanden, im Bearbeitungssteuerelement des Kombinationsfelds.

```
void Clear();
```

### <a name="remarks"></a>Bemerkungen

Um die aktuelle Auswahl zu löschen und den gelöschten Inhalt in der Zwischenablage zu platzieren, verwenden Sie die Funktion [Member ausschneiden.](#cut)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a>CComboBox::CompareItem

Wird vom Framework aufgerufen, um die relative Position eines neuen Elements im Listenfeldteil eines sortierten Kombinationsfelds für besitzerzeichnen zu bestimmen.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parameter

*lpCompareItemStruct*<br/>
Ein langer Zeiger auf eine [COMPAREITEMSTRUCT-Struktur.](/windows/win32/api/winuser/ns-winuser-compareitemstruct)

### <a name="return-value"></a>Rückgabewert

Gibt die relative Position der beiden `COMPAREITEMSTRUCT` in der Struktur beschriebenen Elemente an. Dabei kann es sich um einen der folgenden Werte handeln:

|Wert|Bedeutung|
|-----------|-------------|
|- 1|Artikel 1 sortiert vor Artikel 2.|
|0|Artikel 1 und Artikel 2 sortieren die gleiche.|
|1|Artikel 1 sortiert nach Artikel 2.|

Eine Beschreibung von `COMPAREITEMSTRUCT`finden Sie unter [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) .

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Memberfunktion nichts aus. Wenn Sie ein Kombinationsfeld zum Zeichnen von Besitzern mit dem Stil LBS_SORT erstellen, müssen Sie diese Memberfunktion überschreiben, um das Framework beim Sortieren neuer Elemente zu unterstützen, die dem Listenfeld hinzugefügt wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a>CComboBox::Kopieren

Kopiert die aktuelle Auswahl(en) im Bearbeitungssteuerelement des Kombinationsfelds im CF_TEXT Format in die Zwischenablage.

```
void Copy();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a>CComboBox::Erstellen

Erstellt das Kombinationsfeld und `CComboBox` fügt es an das Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Kombinationsfelds an. Wenden Sie eine beliebige Kombination von [Kombinationsbox-Stilen](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) auf das Feld an.

*Rect*<br/>
Zeigt auf die Position und Größe des Kombinationsfelds. Kann eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder ein `CRect` Objekt sein.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Kombinationsfelds (in der Regel a `CDialog`) an. Es darf nicht NULL sein.

*nID*<br/>
Gibt die Steuer-ID des Kombinationsfelds an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CComboBox` ein Objekt in zwei Schritten. Rufen Sie zunächst den Konstruktor auf, und rufen Sie dann `Create` `CComboBox` auf, das Windows-Kombinationsfeld erstellt und an das Objekt anfügt.

Bei `Create` der Ausführung sendet Windows die [Nachrichten WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)und [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) Nachrichten an das Kombinationsfeld.

Diese Nachrichten werden standardmäßig von den Memberfunktionen [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)und `CWnd` [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) in der Basisklasse verarbeitet. Um die Standardnachrichtenbehandlung zu erweitern, `CComboBox`leiten Sie eine Klasse von ab , fügen Sie der neuen Klasse eine Nachrichtenzuordnung hinzu, und überschreiben Sie die vorherigen Message-Handler-Memberfunktionen. Überschreiben `OnCreate`Sie z. B., um die erforderliche Initialisierung für eine neue Klasse durchzuführen.

Wenden Sie die folgenden [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein Kombinationsfeldsteuerelement an. :

- WS_CHILD Immer

- WS_VISIBLE In der Regel

- WS_DISABLED Selten

- WS_VSCROLL So fügen Sie vertikales Scrollen für das Listenfeld im Kombinationsfeld hinzu

- WS_HSCROLL So fügen Sie horizontales Scrollen für das Listenfeld im Kombinationsfeld hinzu

- WS_GROUP Zu Gruppensteuerelementen

- WS_TABSTOP So schließen Sie das Kombinationsfeld in die Tabstoppreihenfolge ein

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a>CComboBox::Schnitt

Löscht (schneidet) die aktuelle Auswahl, falls vorhanden, im Kombinationsfeld-Bearbeitungssteuerelement und kopiert den gelöschten Text in der Zwischenablage im CF_TEXT Format.

```
void Cut();
```

### <a name="remarks"></a>Bemerkungen

Um die aktuelle Auswahl zu löschen, ohne den gelöschten Text in der Zwischenablage zu platzieren, rufen Sie die Funktion [Member löschen](#clear) auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a>CComboBox::DeleteItem

Wird vom Framework aufgerufen, wenn der Benutzer ein `CComboBox` Element aus einem Besitzerzeichnungsobjekt löscht oder das Kombinationsfeld zerstört.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDeleteItemStruct*<br/>
Ein langer Zeiger auf eine Windows [DELETEITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) die Informationen zum gelöschten Element enthält. Eine Beschreibung dieser Struktur finden Sie unter [CWnd::OnDeleteItem.](../../mfc/reference/cwnd-class.md#ondeleteitem)

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um das Kombinationsfeld nach Bedarf neu zu zeichnen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a>CComboBox::DeleteString

Löscht das Element in Position *nIndex* aus dem Kombinationsfeld.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den Index für die Zeichenfolge an, die gelöscht werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn der Rückgabewert größer oder gleich 0 ist, handelt es sich um eine Anzahl der Zeichenfolgen, die in der Liste verbleiben. Der Rückgabewert ist CB_ERR, wenn *nIndex* einen Index angibt, der größer als die Anzahl der Elemente in der Liste ist.

### <a name="remarks"></a>Bemerkungen

Alle Elemente, die *nach nIndex* folgen, bewegen sich nun um eine Position nach unten. Wenn z. B. ein Kombinationsfeld zwei Elemente enthält, führt das Löschen des ersten Elements dazu, dass sich das verbleibende Element jetzt an der ersten Position befindet. *nIndex*=0 für das Element an der ersten Position.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a>CComboBox::Dir

Fügt dem Listenfeld eines Kombinationsfelds eine Liste mit Dateinamen oder Laufwerken hinzu.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parameter

*Attr*<br/>
Kann eine beliebige Kombination der in [CFile::GetStatus](../../mfc/reference/cfile-class.md#getstatus) beschriebenen **Enumerumwerte** oder eine beliebige Kombination der folgenden Werte sein:

- DDL_READWRITE Datei kann aus gelesen oder geschrieben werden.

- DDL_READONLY Datei kann gelesen, aber nicht geschrieben werden.

- DDL_HIDDEN Datei ist ausgeblendet und wird nicht in einer Verzeichnisliste angezeigt.

- DDL_SYSTEM Datei ist eine Systemdatei.

- DDL_DIRECTORY Der von *lpszWildCard* angegebene Name gibt ein Verzeichnis an.

- DDL_ARCHIVE Datei wurde archiviert.

- DDL_DRIVES Alle Laufwerke einschließen, die dem von *lpszWildCard*angegebenen Namen entsprechen.

- DDL_EXCLUSIVE Exklusive Flagge. Wenn das exklusive Flag festgelegt ist, werden nur Dateien des angegebenen Typs aufgelistet. Andernfalls werden Dateien des angegebenen Typs zusätzlich zu "normalen" Dateien aufgelistet.

*lpszWildCard*<br/>
Zeigt auf eine Dateispezifikationszeichenfolge. Die Zeichenfolge kann Platzhalter enthalten (z. B. *.\*).

### <a name="return-value"></a>Rückgabewert

Wenn der Rückgabewert größer oder gleich 0 ist, ist er der Null-basierte Index des letzten Dateinamens, der der Liste hinzugefügt wurde. Der Rückgabewert ist CB_ERR wenn ein Fehler auftritt. Der Rückgabewert ist CB_ERRSPACE, wenn nicht genügend Speicherplatz zum Speichern der neuen Zeichenfolgen verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird vom `ComboBoxEx` Windows-Steuerelement nicht unterstützt. Weitere Informationen zu diesem Steuerelement finden Sie unter [ComboBoxEx-Steuerelemente](/windows/win32/Controls/comboboxex-controls) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a>CComboBox::DrawItem

Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines Besitzer-Zeichnungs-Kombinationsfelds ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein Zeiger auf eine [DRAWITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) die Informationen über den erforderlichen Zeichnungstyp enthält.

### <a name="remarks"></a>Bemerkungen

Das `itemAction` Element `DRAWITEMSTRUCT` der Struktur definiert die Zeichnungsaktion, die ausgeführt werden soll. Eine Beschreibung dieser Struktur finden Sie unter [CWnd::OnDrawItem.](../../mfc/reference/cwnd-class.md#ondrawitem)

Standardmäßig führt diese Memberfunktion nichts aus. Überschreiben Sie diese Memberfunktion, um `CComboBox` die Zeichnung für ein Besitzerzeichnungsobjekt zu implementieren. Bevor diese Memberfunktion beendet wird, sollte die Anwendung alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den in *lpDrawItemStruct*bereitgestellten Anzeigekontext ausgewählt wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a>CComboBox::FindString

Sucht die erste Zeichenfolge, die das angegebene Präfix im Listenfeld eines Kombinationsfelds enthält, wählt aber nicht aus.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>Parameter

*nStartAfter*<br/>
Enthält den nullbasierten Index des Elements vor dem ersten zu durchsuchenden Element. Wenn die Suche am Ende des Listenfelds angelangt ist, wird sie vom oberen Rand des Listenfelds zurück zu dem von *nStartAfter*angegebenen Element fortgesetzt. Wenn -1, wird das gesamte Listenfeld von Anfang an durchsucht.

*lpszString*<br/>
Verweist auf die null-terminierte Zeichenfolge, die das Präfix enthält, nach dem gesucht werden soll. Die Suche ist großfliegt, daher kann diese Zeichenfolge eine beliebige Kombination aus Groß- und Kleinbuchstaben enthalten.

### <a name="return-value"></a>Rückgabewert

Wenn der Rückgabewert größer oder gleich 0 ist, ist er der nullbasierte Index des übereinstimmenden Elements. Es ist CB_ERR, ob die Suche erfolglos war.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird vom `ComboBoxEx` Windows-Steuerelement nicht unterstützt. Weitere Informationen zu diesem Steuerelement finden Sie unter [ComboBoxEx-Steuerelemente](/windows/win32/Controls/comboboxex-controls) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a>CComboBox::FindStringExact

Rufen `FindStringExact` Sie die Memberfunktion auf, um die erste Listenfeldzeichenfolge (in einem Kombinationsfeld) zu finden, die mit der in *lpszFind*angegebenen Zeichenfolge übereinstimmt.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parameter

*nIndexStart*<br/>
Gibt den nullbasierten Index des Elements vor dem ersten zu durchsuchenden Element an. Wenn die Suche am Ende des Listenfelds angelangt ist, wird sie vom oberen Rand des Listenfelds zurück zu dem von *nIndexStart*angegebenen Element fortgesetzt. Wenn *nIndexStart* -1 ist, wird das gesamte Listenfeld von Anfang an durchsucht.

*lpszFind*<br/>
Zeigt auf die null-terminierte Zeichenfolge, nach der gesucht werden soll. Diese Zeichenfolge kann einen vollständigen Dateinamen enthalten, einschließlich der Erweiterung. Bei der Suche wird die Groß-/Kleinschreibung nicht beachtet, sodass diese Zeichenfolge eine beliebige Kombination aus Groß- und Kleinbuchstaben enthalten kann.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des übereinstimmenden Elements oder CB_ERR, wenn die Suche nicht erfolgreich war.

### <a name="remarks"></a>Bemerkungen

Wenn das Kombinationsfeld mit einem Besitzerzeichnungsstil, `FindStringExact` jedoch ohne [den CBS_HASSTRINGS-Stil](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) erstellt wurde, wird versucht, den Doppelwortwert mit dem Wert von *lpszFind*abzugleichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo

Ruft Informationen für `CComboBox` das Objekt ab.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>Parameter

*pcbi*<br/>
Ein Zeiger auf die [COMBOBOXINFO-Struktur.](/windows/win32/api/winuser/ns-winuser-comboboxinfo)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der [CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo) Nachricht, wie im Windows SDK beschrieben.

## <a name="ccomboboxgetcount"></a><a name="getcount"></a>CComboBox::GetCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der Elemente im Listenfeldteil eines Kombinationsfelds abzurufen.

```
int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente. Die zurückgegebene Anzahl ist größer als der Indexwert des letzten Elements (der Index ist nullbasiert). Es ist CB_ERR, wenn ein Fehler auftritt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a>CComboBox::GetCueBanner

Ruft den Cue-Text ab, der für ein Kombinationsfeldsteuerelement angezeigt wird.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*lpszText*|[out] Zeiger auf einen Puffer, der den Cue-Bannertext empfängt.|
|*cchText*|[in] Größe des Puffers, auf den der Parameter *lpszText* verweist.|

### <a name="return-value"></a>Rückgabewert

In der ersten Überladung ein [CString-Objekt,](../../atl-mfc-shared/using-cstring.md) das den Cue-Banner-Text enthält, falls vorhanden; Andernfalls ein `CString` Objekt mit einer Länge von null.

- oder -

In der zweiten Überladung TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Cue-Text ist eine Eingabeaufforderung, die im Eingabebereich des Kombinationsfeldsteuerelements angezeigt wird. Der Cue-Text wird angezeigt, bis der Benutzer Eingaben bereitstellt.

Diese Methode sendet die [CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner) Nachricht, die im Windows SDK beschrieben wird.

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a>CComboBox::GetCurSel

Rufen Sie diese Memberfunktion auf, um zu bestimmen, welches Element im Kombinationsfeld ausgewählt ist.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des aktuell ausgewählten Elements im Listenfeld eines Kombinationsfelds oder CB_ERR, wenn kein Element ausgewählt ist.

### <a name="remarks"></a>Bemerkungen

`GetCurSel`gibt einen Index in die Liste zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect

Rufen `GetDroppedControlRect` Sie die Memberfunktion auf, um die Bildschirmkoordinaten des sichtbaren (Dropdown-)Listenfelds eines Dropdown-Kombinationsfelds abzurufen.

```
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>Parameter

*lprect*<br/>
Zeigt auf die [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Koordinaten empfangen soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a>CComboBox::GetDroppedState

Rufen `GetDroppedState` Sie die Memberfunktion auf, um zu bestimmen, ob das Listenfeld eines Dropdown-Kombinationsfelds sichtbar ist (nach unten fallen gelassen).

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Listenfeld sichtbar ist; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth

Rufen Sie diese Funktion auf, um die minimal zulässige Breite (in Pixel) des Listenfelds eines Kombinationsfelds abzurufen.

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, die minimal zulässige Breite, in Pixel; andernfalls CB_ERR.

### <a name="remarks"></a>Bemerkungen

Diese Funktion gilt nur für Kombinationsfelder mit dem [CBS_DROPDOWN-](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) oder [CBS_DROPDOWNLIST-Stil.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

Standardmäßig ist die zulässige Mindestbreite des Dropdown-Listenfelds 0. Die minimal zulässige Breite kann durch Aufrufen von [SetDroppedWidth](#setdroppedwidth)festgelegt werden. Wenn der Listenfeldteil des Kombinationsfelds angezeigt wird, ist seine Breite größer als die minimale zulässige Breite oder die Breite des Kombinationsfelds.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [SetDroppedWidth](#setdroppedwidth).

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a>CComboBox::GetEditSel

Ruft die Anfangs- und Endzeichenpositionen der aktuellen Auswahl im Bearbeitungssteuerelement eines Kombinationsfelds ab.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>Rückgabewert

Ein 32-Bit-Wert, der die Startposition im Wort niedriger Ordnung und die Position des ersten nicht ausgewählten Zeichens nach dem Ende der Auswahl im Wort hoher Ordnung enthält. Wenn diese Funktion in einem Kombinationsfeld ohne Bearbeitungssteuerelement verwendet wird, wird CB_ERR zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a>CComboBox::GetExtendedUI

Rufen `GetExtendedUI` Sie die Memberfunktion auf, um zu bestimmen, ob ein Kombinationsfeld über die Standardbenutzeroberfläche oder die erweiterte Benutzeroberfläche verfügt.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Kombinationsfeld über die erweiterte Benutzeroberfläche verfügt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die erweiterte Benutzeroberfläche kann wie folgt identifiziert werden:

- Wenn Sie auf das statische Steuerelement klicken, wird das Listenfeld nur für Kombinationsfelder mit dem [Stil CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) angezeigt.

- Wenn Sie die TASTE DOWN ARROW drücken, wird das Listenfeld angezeigt (F4 ist deaktiviert).

Das Scrollen im statischen Steuerelement ist deaktiviert, wenn die Elementliste nicht sichtbar ist (Pfeiltasten sind deaktiviert).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent

Ruft aus dem Kombinationsfeld die Breite in Pixel ab, mit der der Listenfeldteil des Kombinationsfelds horizontal gescrollt werden kann.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>Rückgabewert

Die scrollbare Breite des Listenfeldteils des Kombinationsfelds in Pixel.

### <a name="remarks"></a>Bemerkungen

Dies gilt nur, wenn der Listenfeldteil des Kombinationsfelds über eine horizontale Bildlaufleiste verfügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a>CComboBox::GetItemData

Ruft den von der Anwendung bereitgestellten 32-Bit-Wert ab, der dem angegebenen Kombinationsfeldelement zugeordnet ist.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält den nullbasierten Index eines Elements im Listenfeld des Kombinationsfelds.

### <a name="return-value"></a>Rückgabewert

Der dem Element zugeordnete 32-Bit-Wert oder CB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Der 32-Bit-Wert kann mit dem *dwItemData-Parameter* eines [SetItemData-Memberfunktionsaufrufs](#setitemdata) festgelegt werden. Verwenden `GetItemDataPtr` Sie die Memberfunktion, wenn der abzuholende 32-Bit-Wert ein Zeiger (**void )** <strong>\*</strong>ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a>CComboBox::GetItemDataPtr

Ruft den von der Anwendung bereitgestellten 32-Bit-Wert ab, der dem angegebenen Kombinationsfeldelement als Zeiger zugeordnet ist (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält den nullbasierten Index eines Elements im Listenfeld des Kombinationsfelds.

### <a name="return-value"></a>Rückgabewert

Ruft einen Zeiger oder -1 ab, wenn ein Fehler auftritt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a>CComboBox::GetItemHeight

Rufen `GetItemHeight` Sie die Memberfunktion auf, um die Höhe von Listenelementen in einem Kombinationsfeld abzurufen.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt die Komponente des Kombinationsfelds an, dessen Höhe abgerufen werden soll. Wenn der *nIndex-Parameter* -1 ist, wird die Höhe des Abschnitts "Edit-Control" (oder statischer Text) des Kombinationsfelds abgerufen. Wenn das Kombinationsfeld den [Stil CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) hat, gibt *nIndex* den nullbasierten Index des Listenelements an, dessen Höhe abgerufen werden soll. Andernfalls sollte *nIndex* auf 0 gesetzt werden.

### <a name="return-value"></a>Rückgabewert

Die Höhe des angegebenen Elements in einem Kombinationsfeld in Pixel. Der Rückgabewert beim Auftreten eines Fehlers ist CB_ERR.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a>CComboBox::GetLBText

Ruft eine Zeichenfolge aus dem Listenfeld eines Kombinationsfelds ab.

```
int GetLBText(
    int nIndex,
    LPTSTR lpszText) const;

void GetLBText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält den nullbasierten Index der zu kopierenden Listenfeldzeichenfolge.

*lpszText*<br/>
Zeigt auf einen Puffer, der die Zeichenfolge empfangen soll. Der Puffer muss über ausreichend Speicherplatz für die Zeichenfolge und ein beendendes NULL-Zeichen verfügen.

*rString*<br/>
Ein Verweis auf eine `CString`.

### <a name="return-value"></a>Rückgabewert

Die Länge (in Bytes) der Zeichenfolge, ohne das beendende Nullzeichen. Wenn *nIndex* keinen gültigen Index angibt, wird der Rückgabewert CB_ERR.

### <a name="remarks"></a>Bemerkungen

Die zweite Form dieser Memberfunktion `CString` füllt ein Objekt mit dem Text des Elements.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a>CComboBox::GetLBTextLen

Ruft die Länge einer Zeichenfolge im Listenfeld eines Kombinationsfelds ab.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält den nullbasierten Index der Listenfeldzeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die Länge der Zeichenfolge in Bytes, mit Ausnahme des beendenden Nullzeichens. Wenn *nIndex* keinen gültigen Index angibt, wird der Rückgabewert CB_ERR.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CComboBox::GetLBText](#getlbtext).

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a>CComboBox::GetLocale

Ruft das Gebietsschema ab, das vom Kombinationsfeld verwendet wird.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Rückgabewert

Der LCID-Wert (Locale Identifier) für die Zeichenfolgen im Kombinationsfeld.

### <a name="remarks"></a>Bemerkungen

Das Gebietsschema wird z. B. verwendet, um die Sortierreihenfolge der Zeichenfolgen in einem sortierten Kombinationsfeld zu bestimmen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CComboBox::SetLocale](#setlocale).

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a>CComboBox::GetMinVisible

Ruft die minimale Anzahl sichtbarer Elemente in der Dropdownliste des aktuellen Kombinationsfeldsteuerelements ab.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>Rückgabewert

Die minimale Anzahl sichtbarer Elemente in der aktuellen Dropdownliste.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) Nachricht, die im Windows SDK beschrieben wird.

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a>CComboBox::GetTopIndex

Ruft den nullbasierten Index des ersten sichtbaren Elements im Listenfeldteil des Kombinationsfelds ab.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der Null-basierte Index des ersten sichtbaren Elements im Listenfeldteil des Kombinationsfelds, wenn erfolgreich, CB_ERR andernfalls.

### <a name="remarks"></a>Bemerkungen

Zunächst befindet sich Element 0 oben im Listenfeld, aber wenn das Listenfeld gescrollt wird, befindet sich möglicherweise ein anderes Element oben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a>CComboBox::InitStorage

Reserviert Speicher zum Speichern von Listenfeldelementen im Listenfeldteil des Kombinationsfelds.

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

Wenn dies erfolgreich ist, kann die maximale Anzahl von Elementen, die der Listenfeldteil des Kombinationsfelds speichern kann, bevor eine Speicherumverteilung erforderlich ist, andernfalls CB_ERRSPACE, d. h. nicht genügend Arbeitsspeicher verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, bevor Sie dem Listenfeldteil des `CComboBox`eine große Anzahl von Elementen hinzufügen.

Nur Windows 95/98: Der *parameter wParam* ist auf 16-Bit-Werte beschränkt. Dies bedeutet, dass Listenfelder nicht mehr als 32.767 Elemente enthalten dürfen. Obwohl die Anzahl der Elemente eingeschränkt ist, ist die Gesamtgröße der Elemente in einem Listenfeld nur durch den verfügbaren Speicher begrenzt.

Diese Funktion beschleunigt die Initialisierung von Listenfeldern mit einer großen Anzahl von Elementen (mehr als 100). Es ordnet die angegebene Speichermenge vor, so dass nachfolgende [AddString](#addstring)-, [InsertString-](#insertstring)und [Dir-Funktionen](#dir) die kürzest mögliche Zeit in Anspruch nehmen. Sie können Schätzungen für die Parameter verwenden. Wenn Sie überschätzen, wird etwas zusätzlicher Speicher zugewiesen. Wenn Sie unterschätzen, wird die normale Zuordnung für Artikel verwendet, die den vorab zugewiesenen Betrag überschreiten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a>CComboBox::InsertString

Fügt eine Zeichenfolge in das Listenfeld eines Kombinationsfelds ein.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält den nullbasierten Index der Position im Listenfeld, die die Zeichenfolge aufnehmen soll. Wenn dieser Parameter -1 ist, wird die Zeichenfolge am Ende der Liste hinzugefügt.

*lpszString*<br/>
Zeigt auf die einzufügende nullterminierte Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index der Position, an der die Zeichenfolge eingefügt wurde. Der Rückgabewert beim Auftreten eines Fehlers ist CB_ERR. Der Rückgabewert ist CB_ERRSPACE, wenn zum Speichern der neuen Zeichenfolge nicht genügend Platz vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Im Gegensatz zur Memberfunktion [AddString](#addstring) bewirkt die `InsertString` -Memberfunktion nicht die Sortierung einer Liste mit der Formatvorlage [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

> [!NOTE]
> Diese Funktion wird vom `ComboBoxEx` Windows-Steuerelement nicht unterstützt. Weitere Informationen zu diesem Steuerelement finden Sie unter [ComboBoxEx-Steuerelemente](/windows/win32/Controls/comboboxex-controls) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a>CComboBox::LimitText

Beschränkt die Länge des Textes in Bytes, den der Benutzer in das Bearbeitungssteuerelement eines Kombinationsfelds eingeben kann.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>Parameter

*nMaxChars*<br/>
Gibt die Länge (in Bytes) des Textes an, den der Benutzer eingeben kann. Wenn dieser Parameter 0 ist, wird die Textlänge auf 65.535 Bytes festgelegt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich. Wenn ein Kombinationsfeld mit dem Stil [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) oder für ein Kombinationsfeld ohne Bearbeitungssteuerelement aufgerufen wird, wird der Rückgabewert CB_ERR.

### <a name="remarks"></a>Bemerkungen

Wenn das Kombinationsfeld nicht über den Stil [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)verfügt, hat das Festlegen des Textlimits auf die Größe des Bearbeitungssteuerelements keine Auswirkungen.

`LimitText`beschränkt nur den Text, den der Benutzer eingeben kann. Sie hat keine Auswirkungen auf Text, der sich bereits im Bearbeitungssteuerelement befindet, wenn die Nachricht gesendet wird, und auch nicht die Länge des Textes, der in das Bearbeitungssteuerelement kopiert wird, wenn eine Zeichenfolge im Listenfeld ausgewählt ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a>CComboBox::MeasureItem

Wird vom Framework aufgerufen, wenn ein Kombinationsfeld mit einem Besitzerzeichnungsstil erstellt wird.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parameter

*lpMeasureItemStruct*<br/>
Ein langer Zeiger auf eine [MEASUREITEMSTRUCT-Struktur.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Memberfunktion nichts aus. Überschreiben Sie diese Memberfunktion, und füllen Sie die `MEASUREITEMSTRUCT` Struktur aus, um Windows über die Dimensionen des Listenfelds im Kombinationsfeld zu informieren. Wenn das Kombinationsfeld mit dem [Stil CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) erstellt wird, ruft das Framework diese Memberfunktion für jedes Element im Listenfeld auf. Andernfalls wird dieses Element nur einmal aufgerufen.

Die Verwendung des CBS_OWNERDRAWFIXED-Stils in einem Mit-Besitzer-Zeichnungs-Kombinationsfeld, das mit der [SubclassDlgItem-Memberfunktion](../../mfc/reference/cwnd-class.md#subclassdlgitem) erstellt wurde, `CWnd` beinhaltet weitere Programmierüberlegungen. Siehe die Diskussion in [Technical Note 14](../../mfc/tn014-custom-controls.md).

Eine Beschreibung der `MEASUREITEMSTRUCT` Struktur finden Sie unter [CWnd::OnMeasureItem.](../../mfc/reference/cwnd-class.md#onmeasureitem)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a>CComboBox::Paste

Fügt die Daten aus der Zwischenablage in das Bearbeitungssteuerelement des Kombinationsfelds an der aktuellen Cursorposition ein.

```
void Paste();
```

### <a name="remarks"></a>Bemerkungen

Daten werden nur eingefügt, wenn die Zwischenablage Daten im CF_TEXT-Format enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a>CComboBox::ResetContent

Entfernt alle Elemente aus dem Listenfeld und bearbeitet die Steuerung eines Kombinationsfelds.

```
void ResetContent();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a>CComboBox::SelectString

Sucht im Listenfeld eines Kombinationsfelds nach einer Zeichenfolge, und wenn die Zeichenfolge gefunden wird, wählt sie die Zeichenfolge im Listenfeld aus und kopiert sie in das Bearbeitungssteuerelement.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parameter

*nStartAfter*<br/>
Enthält den nullbasierten Index des Elements vor dem ersten zu durchsuchenden Element. Wenn die Suche am Ende des Listenfelds angelangt ist, wird sie vom oberen Rand des Listenfelds zurück zu dem von *nStartAfter*angegebenen Element fortgesetzt. Wenn -1, wird das gesamte Listenfeld von Anfang an durchsucht.

*lpszString*<br/>
Verweist auf die null-terminierte Zeichenfolge, die das Präfix enthält, nach dem gesucht werden soll. Die Suche ist großfliegt, daher kann diese Zeichenfolge eine beliebige Kombination aus Groß- und Kleinbuchstaben enthalten.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des ausgewählten Elements, wenn die Zeichenfolge gefunden wurde. Wenn die Suche nicht erfolgreich war, wird der Rückgabewert CB_ERR und die aktuelle Auswahl wird nicht geändert.

### <a name="remarks"></a>Bemerkungen

Eine Zeichenfolge wird nur ausgewählt, wenn ihre Anfangszeichen (vom Startpunkt) mit den Zeichen in der Präfixzeichenfolge übereinstimmen.

Beachten Sie, dass die `SelectString` und `FindString` Memberfunktionen `SelectString` beide eine Zeichenfolge finden, aber die Memberfunktion wählt auch die Zeichenfolge aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a>CComboBox::SetCueBanner

Legt den Cue-Text fest, der für ein Kombinationsfeldsteuerelement angezeigt wird.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*lpszText*|[in] Zeiger auf einen null-terminierten Puffer, der den Cue-Text enthält.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Cue-Text ist eine Eingabeaufforderung, die im Eingabebereich des Kombinationsfeldsteuerelements angezeigt wird. Der Cue-Text wird angezeigt, bis der Benutzer Eingaben bereitstellt.

Diese Methode sendet die [CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Variable *m_combobox*definiert, die für den programmgesteuerten Zugriff auf das Kombinationsfeldsteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das Cue-Banner für das Kombinationsfeldsteuerelement festgelegt.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a>CComboBox::SetCurSel

Wählt eine Zeichenfolge im Listenfeld eines Kombinationsfelds aus.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parameter

*nWählen*<br/>
Gibt den nullbasierten Index der auszuwählenden Zeichenfolge an. Wenn -1, wird jede aktuelle Auswahl im Listenfeld entfernt, und das Bearbeitungssteuerelement wird gelöscht.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des ausgewählten Elements, wenn die Nachricht erfolgreich ist. Der Rückgabewert ist CB_ERR, wenn *nSelect* größer als die Anzahl der Elemente in der Liste ist oder wenn *nSelect* auf -1 gesetzt ist, wodurch die Auswahl entfernt wird.

### <a name="remarks"></a>Bemerkungen

Bei Bedarf wird im Listenfeld ein Bildlauf der Zeichenfolge in die Ansicht durchgeführt (wenn das Listenfeld sichtbar ist). Der Text im Bearbeitungssteuerelement des Kombinationsfelds wird geändert, um die neue Auswahl widerzuspiegeln. Jede vorherige Auswahl im Listenfeld wird entfernt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth

Rufen Sie diese Funktion auf, um die zulässige Mindestbreite (in Pixel) des Listenfelds eines Kombinationsfelds festzulegen.

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>Parameter

*nWidth*<br/>
Die minimal zulässige Breite des Listenfeldteils des Kombinationsfelds in Pixel.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird die neue Breite des Listenfelds andernfalls CB_ERR.

### <a name="remarks"></a>Bemerkungen

Diese Funktion gilt nur für Kombinationsfelder mit dem [CBS_DROPDOWN-](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) oder [CBS_DROPDOWNLIST-Stil.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

Standardmäßig ist die zulässige Mindestbreite des Dropdown-Listenfelds 0. Wenn der Listenfeldteil des Kombinationsfelds angezeigt wird, ist seine Breite größer als die minimale zulässige Breite oder die Breite des Kombinationsfelds.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a>CComboBox::SetEditSel

Wählt Zeichen im Bearbeitungssteuerelement eines Kombinationsfelds aus.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>Parameter

*nStartChar*<br/>
Gibt die Startposition an. Wenn die Startposition auf -1 festgelegt ist, wird jede vorhandene Auswahl entfernt.

*nEndChar*<br/>
Gibt die Endposition an. Wenn die Endposition auf -1 festgelegt ist, wird der gesamte Text von der Startposition bis zum letzten Zeichen im Bearbeitungssteuerelement ausgewählt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Memberfunktion erfolgreich ist; andernfalls 0. Es ist `CComboBox` CB_ERR, ob [der CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) Stil oder kein Listenfeld vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Die Positionen sind nullbasiert. Um das erste Zeichen des Bearbeitungssteuerelements auszuwählen, geben Sie eine Startposition von 0 an. Die Endposition ist für das Zeichen direkt nach dem letzten Zeichen auszuwählen. Um beispielsweise die ersten vier Zeichen des Bearbeitungssteuerelements auszuwählen, verwenden Sie eine Startposition von 0 und eine Endposition von 4.

> [!NOTE]
> Diese Funktion wird vom `ComboBoxEx` Windows-Steuerelement nicht unterstützt. Weitere Informationen zu diesem Steuerelement finden Sie unter [ComboBoxEx-Steuerelemente](/windows/win32/Controls/comboboxex-controls) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CComboBox::GetEditSel](#geteditsel).

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a>CComboBox::SetExtendedUI

Rufen `SetExtendedUI` Sie die Memberfunktion auf, um entweder die Standardbenutzeroberfläche oder die erweiterte Benutzeroberfläche für ein Kombinationsfeld mit dem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) oder [CBS_DROPDOWNLIST-Stil](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) auszuwählen.

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>Parameter

*bErweitert*<br/>
Gibt an, ob das Kombinationsfeld die erweiterte Benutzeroberfläche oder die Standardbenutzeroberfläche verwenden soll. Der Wert TRUE wählt die erweiterte Benutzeroberfläche aus. der Wert FALSE wählt die Standardbenutzeroberfläche aus.

### <a name="return-value"></a>Rückgabewert

CB_OKAY, wenn der Vorgang erfolgreich ist, oder CB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Die erweiterte Benutzeroberfläche kann wie folgt identifiziert werden:

- Wenn Sie auf das statische Steuerelement klicken, wird das Listenfeld nur für Kombinationsfelder mit dem Stil CBS_DROPDOWNLIST angezeigt.

- Wenn Sie die TASTE DOWN ARROW drücken, wird das Listenfeld angezeigt (F4 ist deaktiviert).

Das Scrollen im statischen Steuerelement ist deaktiviert, wenn die Elementliste nicht sichtbar ist (die Pfeiltasten sind deaktiviert).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CComboBox::GetExtendedUI](#getextendedui).

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent

Legt die Breite in Pixel fest, mit der der Listenfeldteil des Kombinationsfelds horizontal gescrollt werden kann.

```
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>Parameter

*nExtent*<br/>
Gibt die Anzahl der Pixel an, mit der der Listenfeldteil des Kombinationsfelds horizontal gescrollt werden kann.

### <a name="remarks"></a>Bemerkungen

Wenn die Breite des Listenfelds kleiner als dieser Wert ist, scrollt die horizontale Bildlaufleiste horizontal Elemente im Listenfeld. Wenn die Breite des Listenfelds gleich oder größer als dieser Wert ist, wird die horizontale Bildlaufleiste ausgeblendet oder, wenn das Kombinationsfeld den [Stil CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) hat, deaktiviert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a>CComboBox::SetItemData

Legt den 32-Bit-Wert fest, der dem angegebenen Element in einem Kombinationsfeld zugeordnet ist.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält einen nullbasierten Index für das festzulegende Element.

*dwItemData*<br/>
Enthält den neuen Wert, der dem Artikel zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

CB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Verwenden `SetItemDataPtr` Sie die Memberfunktion, wenn das 32-Bit-Element ein Zeiger sein soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a>CComboBox::SetItemDataPtr

Legt den 32-Bit-Wert, der dem angegebenen Element zugeordnet ist, in einem Kombinationsfeld als den angegebenen Zeiger (**void** <strong>\*</strong>) fest.

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält einen nullbasierten Index für das Element.

*pData*<br/>
Enthält den Zeiger, der dem Artikel zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

CB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Dieser Zeiger bleibt für die Lebensdauer des Kombinationsfelds gültig, auch wenn sich die relative Position des Elements innerhalb des Kombinationsfelds ändern kann, wenn Elemente hinzugefügt oder entfernt werden. Daher kann sich der Index des Elements innerhalb des Felds ändern, aber der Zeiger bleibt zuverlässig.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a>CComboBox::SetItemHeight

Rufen `SetItemHeight` Sie die Memberfunktion auf, um die Höhe von Listenelementen in einem Kombinationsfeld oder die Höhe des Abschnitts "Bearbeiten-Steuerelement" (oder statischen Text) eines Kombinationsfelds festzulegen.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt an, ob die Höhe von Listenelementen oder die Höhe des Abschnitts "Bearbeiten-Steuerelement" (oder "statischer Text" des Kombinationsfelds festgelegt ist.

Wenn das Kombinationsfeld den [CBS_OWNERDRAWVARIABLE-Stil](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) hat, gibt *nIndex* den nullbasierten Index des Listenelements an, dessen Höhe festgelegt werden soll. Andernfalls muss *nIndex* 0 sein, und die Höhe aller Listenelemente wird festgelegt.

Wenn *nIndex* -1 ist, ist die Höhe des Abschnitts "Edit-Control" oder "Static-Text" des Kombinationsfelds festzulegen.

*cyItemHeight*<br/>
Gibt die Höhe der Kombinationsboxkomponente, die durch *nIndex*identifiziert wird, in Pixel an.

### <a name="return-value"></a>Rückgabewert

CB_ERR, wenn der Index oder die Höhe ungültig ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Höhe des Abschnitts "Bearbeiten-Steuerelement" (oder statisches Text) des Kombinationsfelds wird unabhängig von der Höhe der Listenelemente festgelegt. Eine Anwendung muss sicherstellen, dass die Höhe des Abschnitts "Bearbeiten-Steuerelement" (oder "statischer Text" nicht kleiner als die Höhe eines bestimmten Listenfeldelements ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a>CComboBox::SetLocale

Legt den Gebietsschemabezeichner für dieses Kombinationsfeld fest.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parameter

*nNewLocale*<br/>
Der neue Gebietsschemabezeichner (LCID), der für das Kombinationsfeld festgelegt werden soll.

### <a name="return-value"></a>Rückgabewert

Der vorherige Gebietsschemabezeichner (LCID) für dieses Kombinationsfeld.

### <a name="remarks"></a>Bemerkungen

Wenn `SetLocale` nicht aufgerufen wird, wird das Standardgebietsschema vom System abgerufen. Dieses Systemstandardgebietsschema kann mithilfe der regionalen (oder internationalen) Anwendung der Systemsteuerung geändert werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems

Legt die minimale Anzahl sichtbarer Elemente in der Dropdownliste des aktuellen Kombinationsfeldsteuerelements fest.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*iMinVisible*|[in] Gibt die minimale Anzahl sichtbarer Elemente an.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Variable *m_combobox*definiert, die für den programmgesteuerten Zugriff auf das Kombinationsfeldsteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel werden 20 Elemente in die Dropdownliste eines Kombinationsfeldsteuerelements eingefügt. Anschließend wird angegeben, dass mindestens 10 Elemente angezeigt werden, wenn ein Benutzer den Dropdown-Pfeil drückt.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a>CComboBox::SetTopIndex

Stellt sicher, dass ein bestimmtes Element im Listenfeldteil des Kombinationsfelds sichtbar ist.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den nullbasierten Index des Listenfeldelements an.

### <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, oder CB_ERR, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Das System scrollt das Listenfeld, bis entweder das von *nIndex* angegebene Element oben im Listenfeld angezeigt wird oder der maximale Bildlaufbereich erreicht wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a>CComboBox::ShowDropDown

Zeigt das Listenfeld eines Kombinationsfelds mit dem [Stil CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) oder CBS_DROPDOWNLIST ein oder blendet [es](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) aus.

```
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>Parameter

*bShowIt*<br/>
Gibt an, ob das Dropdown-Listenfeld angezeigt oder ausgeblendet werden soll. Der Wert TRUE zeigt das Listenfeld an. Mit dem Wert FALSE wird das Listenfeld ausgeblendet.

### <a name="remarks"></a>Bemerkungen

Standardmäßig wird in einem Kombinationsfeld dieses Stils das Listenfeld angezeigt.

Diese Memberfunktion hat keine Auswirkungen auf ein Kombinationsfeld, das mit dem [Stil CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) erstellt wurde.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CComboBox::GetDroppedState](#getdroppedstate).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel STRGBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar-Klasse](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic-Klasse](../../mfc/reference/cstatic-class.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
