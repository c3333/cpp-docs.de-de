---
title: CEdit Class
ms.date: 09/12/2018
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
ms.openlocfilehash: 3ca2fe4486ae0751f37d046ef28ed11e60e776ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373987"
---
# <a name="cedit-class"></a>CEdit Class

Stellt die Funktionalität eines Windows-Bearbeitungssteuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CEdit : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEdit::CEdit](#cedit)|Erstellt ein `CEdit` Steuerobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|Bestimmt, ob ein Bearbeitungssteuerungsvorgang rückgängig gemacht werden kann.|
|[CEdit::CharFromPos](#charfrompos)|Ruft die Linien- und Zeichenindizes für das Zeichen ab, das einer angegebenen Position am nächsten liegt.|
|[CEdit::Klar](#clear)|Löscht (löscht) die aktuelle Auswahl (falls vorhanden) im Bearbeitungssteuerelement.|
|[CEdit::Kopieren](#copy)|Kopiert die aktuelle Auswahl (falls vorhanden) im Bearbeitungssteuerelement in die Zwischenablage im CF_TEXT Format.|
|[CEdit::Erstellen](#create)|Erstellt das Windows-Bearbeitungssteuerelement und `CEdit` fügt es an das Objekt an.|
|[CEdit::Schnitt](#cut)|Löscht (schneidet) die aktuelle Auswahl (falls vorhanden) im Bearbeitungssteuerelement und kopiert den gelöschten Text im CF_TEXT Format in die Zwischenablage.|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Setzt das Rückgängig-Flag eines Bearbeitungssteuerelements zurück ( löscht).|
|[CEdit::FmtLines](#fmtlines)|Legt die Einschlussung weicher Zeilenumbruchzeichen in oder aus einem mehrzeiligen Bearbeitungssteuerelement fest.|
|[CEdit::GetCueBanner](#getcuebanner)|Ruft den Text ab, der als Text-Cue oder Tipp in einem Bearbeitungssteuerelement angezeigt wird, wenn das Steuerelement leer ist und keinen Fokus hat.|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Bestimmt die oberste sichtbare Zeile in einem Bearbeitungssteuerelement.|
|[CEdit::GetHandle](#gethandle)|Ruft ein Handle für den Speicher ab, der derzeit für ein mehrzeiliges Bearbeitungssteuerelement reserviert ist.|
|[CEdit::GetHighlight](#gethighlight)|Ruft die Indizes der Anfangs- und Endzeichen in einem Textbereich ab, der im aktuellen Bearbeitungssteuerelement hervorgehoben ist.|
|[CEdit::GetLimitText](#getlimittext)|Ruft die maximale Textmenge ab, die darin enthalten `CEdit` sein kann.|
|[CEdit::GetLine](#getline)|Ruft eine Textzeile aus einem Bearbeitungssteuerelement ab.|
|[CEdit::GetLineCount](#getlinecount)|Ruft die Anzahl der Zeilen in einem mehrzeiligen Bearbeitungssteuerelement ab.|
|[CEdit::GetMargins](#getmargins)|Ruft den linken und `CEdit`rechten Rand für diese ab.|
|[CEdit::GetModify](#getmodify)|Bestimmt, ob der Inhalt eines Bearbeitungssteuerelements geändert wurde.|
|[CEdit::GetPasswordChar](#getpasswordchar)|Ruft das Kennwortzeichen ab, das in einem Bearbeitungssteuerelement angezeigt wird, wenn der Benutzer Text eingibt.|
|[CEdit::GetRect](#getrect)|Ruft das Formatierungsrechteck eines Bearbeitungssteuerelements ab.|
|[CEdit::GetSel](#getsel)|Ruft die ersten und letzten Zeichenpositionen der aktuellen Auswahl in einem Bearbeitungssteuerelement ab.|
|[CEdit::HideBalloonTip](#hideballoontip)|Blendet alle Sprechblasenspitzen aus, die dem aktuellen Bearbeitungssteuerelement zugeordnet sind.|
|[CEdit::LimitText](#limittext)|Beschränkt die Länge des Textes, den der Benutzer in ein Bearbeitungssteuerelement eingeben kann.|
|[CEdit::LineFromChar](#linefromchar)|Ruft die Zeilennummer der Zeile ab, die den angegebenen Zeichenindex enthält.|
|[CEdit::LineIndex](#lineindex)|Ruft den Zeichenindex einer Linie innerhalb eines mehrzeiligen Bearbeitungssteuerelements ab.|
|[CEdit::LineLength](#linelength)|Ruft die Länge einer Linie in einem Bearbeitungssteuerelement ab.|
|[CEdit::LineScroll](#linescroll)|Scrollt den Text eines mehrzeiligen Bearbeitungssteuerelements.|
|[CEdit::Paste](#paste)|Fügt die Daten aus der Zwischenablage in das Bearbeitungssteuerelement an der aktuellen Cursorposition ein. Daten werden nur eingefügt, wenn die Zwischenablage Daten im CF_TEXT-Format enthält.|
|[CEdit::PosVonChar](#posfromchar)|Ruft die Koordinaten der oberen linken Ecke eines angegebenen Zeichenindexes ab.|
|[CEdit::ReplaceSel](#replacesel)|Ersetzt die aktuelle Auswahl in einem Bearbeitungssteuerelement durch den angegebenen Text.|
|[CEdit::SetCueBanner](#setcuebanner)|Legt den Text fest, der als Text-Cue oder Tipp in einem Bearbeitungssteuerelement angezeigt wird, wenn das Steuerelement leer ist und keinen Fokus hat.|
|[CEdit::SetHandle](#sethandle)|Legt das Handle auf den lokalen Speicher fest, der von einem mehrzeiligen Bearbeitungssteuerelement verwendet wird.|
|[CEdit::SetHighlight](#sethighlight)|Hebt einen Textbereich hervor, der im aktuellen Bearbeitungssteuerelement angezeigt wird.|
|[CEdit::SetLimitText](#setlimittext)|Legt die maximale Textmenge fest, `CEdit` die darin enthalten sein kann.|
|[CEdit::SetMargins](#setmargins)|Legt den linken und `CEdit`rechten Rand für diese fest.|
|[CEdit::SetModify](#setmodify)|Legt das Änderungsflag für ein Bearbeitungssteuerelement fest oder löscht es.|
|[CEdit::SetPasswordChar](#setpasswordchar)|Legt ein Kennwortzeichen fest, das in einem Bearbeitungssteuerelement angezeigt wird, wenn der Benutzer Text eingibt, oder entfernt es.|
|[CEdit::SetReadOnly](#setreadonly)|Legt den schreibgeschützten Status eines Bearbeitungssteuerelements fest.|
|[CEdit::SetRect](#setrect)|Legt das Formatierungsrechteck eines mehrzeiligen Bearbeitungssteuerelements fest und aktualisiert das Steuerelement.|
|[CEdit::SetRectNP](#setrectnp)|Legt das Formatierungsrechteck eines mehrzeiligen Bearbeitungssteuerelements fest, ohne das Steuerelementfenster neu zu zeichnen.|
|[CEdit::SetSel](#setsel)|Wählt einen Zeichenbereich in einem Bearbeitungssteuerelement aus.|
|[CEdit::SetTabStops](#settabstops)|Legt die Tabstopps in einem mehrzeiligen Bearbeitungssteuerelement fest.|
|[CEdit::ShowBalloonTip](#showballoontip)|Zeigt eine Sprechblasenspitze an, die dem aktuellen Bearbeitungssteuerelement zugeordnet ist.|
|[CEdit::Rückgängig](#undo)|Kehrt den letzten Bearbeitungssteuerungsvorgang um.|

## <a name="remarks"></a>Bemerkungen

Ein Bearbeitungssteuerelement ist ein rechteckiges untergeordnetes Fenster, in das der Benutzer Text eingeben kann.

Sie können ein Bearbeitungssteuerelement entweder aus einer Dialogfeldvorlage oder direkt im Code erstellen. Rufen Sie in beiden Fällen `CEdit` zuerst `CEdit` den Konstruktor auf, um das Objekt zu erstellen, `CEdit` und rufen Sie dann die [Memberfunktion Erstellen](#create) auf, um das Windows-Bearbeitungssteuerelement zu erstellen und es an das Objekt anzufügen.

Die Konstruktion kann ein einstufiger Prozess `CEdit`in einer Klasse sein, die von abgeleitet ist. Schreiben Sie einen Konstruktor für `Create` die abgeleitete Klasse und rufen Sie aus dem Konstruktor heraus.

`CEdit`erbt wesentliche Funktionen `CWnd`von . Um Text aus einem `CEdit` Objekt festzulegen `CWnd` und abzurufen, verwenden Sie die Memberfunktionen [SetWindowText](cwnd-class.md#setwindowtext) und [GetWindowText](cwnd-class.md#getwindowtext), die den gesamten Inhalt eines Bearbeitungssteuerelements festlegen oder abrufen, auch wenn es sich um ein mehrzeiliges Steuerelement handelt. Textzeilen in einem mehrzeiligen Steuerelement werden durch Zeichensequenzen getrennt. Wenn ein Bearbeitungssteuerelement mehrseitlos ist, rufen Sie einen Teil des `CEdit` Texts des Steuerelements ab und legen Sie ihn fest, indem Sie die Memberfunktionen [GetLine](#getline), [SetSel](#setsel), [GetSel](#getsel)und [ReplaceSel](#replacesel)aufrufen.

Wenn Sie Windows-Benachrichtigungen verarbeiten möchten, die von einem Bearbeitungssteuerelement `CDialog`an das übergeordnete Steuerelement gesendet werden (in der Regel eine von abgeleitete Klasse), fügen Sie der übergeordneten Klasse für jede Nachricht einen Nachrichtenzuordnungseintrag und eine Message-Handler-Memberfunktion hinzu.

Jeder Nachrichtenzuordnungseintrag hat die folgende Form:

  **ON_**_NOTIFICATION_**(** _id_**,** _memberFxn_ **)**

wobei `id` die untergeordnete Fenster-ID des Bearbeitungssteuerelements `memberFxn` angegeben wird, das die Benachrichtigung sendet, und der Name der übergeordneten Memberfunktion ist, die Sie geschrieben haben, um die Benachrichtigung zu behandeln.

Der Funktionsprototyp des Übergeordneten ist wie folgt:

**afx_msg** void MemberFxn **( );**

Im Folgenden finden Sie eine Liste der potenziellen Nachrichtenzuordnungseinträge und eine Beschreibung der Fälle, in denen sie an das übergeordnete Element gesendet werden:

- ON_EN_CHANGE Der Benutzer hat eine Aktion ausgeführt, die möglicherweise Text in einem Bearbeitungssteuerelement geändert hat. Im Gegensatz zur EN_UPDATE Benachrichtigung wird diese Benachrichtigung gesendet, nachdem Windows die Anzeige aktualisiert hat.

- ON_EN_ERRSPACE Das Bearbeitungssteuerelement kann nicht genügend Arbeitsspeicher zuweisen, um eine bestimmte Anforderung zu erfüllen.

- ON_EN_HSCROLL Der Benutzer klickt auf die horizontale Bildlaufleiste eines Bearbeitungssteuerelements. Das übergeordnete Fenster wird benachrichtigt, bevor der Bildschirm aktualisiert wird.

- ON_EN_KILLFOCUS Das Bearbeitungssteuerelement verliert den Eingabefokus.

- ON_EN_MAXTEXT Die aktuelle Einfügung hat die angegebene Anzahl von Zeichen für das Bearbeitungssteuerelement überschritten und wurde abgeschnitten. Wird auch gesendet, wenn ein Bearbeitungssteuerelement nicht über die ES_AUTOHSCROLL-Formatvorlage verfügt und die Anzahl der einzufügenden Zeichen die Breite des Bearbeitungssteuerelements überschreiten würde. Wird auch gesendet, wenn ein Bearbeitungssteuerelement nicht über den ES_AUTOVSCROLL Stil verfügt und die Gesamtzahl der Zeilen, die sich aus einer Texteinfügung ergeben, die Höhe des Bearbeitungssteuerelements überschreitet.

- ON_EN_SETFOCUS Gesendet, wenn ein Bearbeitungssteuerelement den Eingabefokus empfängt.

- ON_EN_UPDATE Das Bearbeitungssteuerelement wird geänderten Text anzeigen. Gesendet, nachdem das Steuerelement den Text formatiert hat, aber bevor er den Text so überprüft, dass die Fenstergröße bei Bedarf geändert werden kann.

- ON_EN_VSCROLL Der Benutzer klickt auf die vertikale Bildlaufleiste eines Bearbeitungssteuerelements. Das übergeordnete Fenster wird benachrichtigt, bevor der Bildschirm aktualisiert wird.

Wenn Sie `CEdit` ein Objekt in einem `CEdit` Dialogfeld erstellen, wird das Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie `CEdit` ein Objekt aus einer Dialogfeldressource `CEdit` mithilfe des Dialogfeld-Editors erstellen, wird das Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie `CEdit` ein Objekt in einem Fenster erstellen, müssen Sie es möglicherweise auch zerstören. Wenn Sie `CEdit` das Objekt auf dem Stapel erstellen, wird es automatisch zerstört. Wenn Sie `CEdit` das Objekt auf dem Heap mithilfe der **neuen** Funktion erstellen, müssen Sie **löschen** für das Objekt aufrufen, um es zu zerstören, wenn der Benutzer das Windows-Bearbeitungssteuerelement beendet. Wenn Sie Speicher im `CEdit` Objekt zuweisen, `CEdit` überschreiben Sie den Destruktor, um die Zuordnungen zu entsorgen.

Um bestimmte Formatvorlagen in einem Bearbeitungssteuerelement (z. B. ES_READONLY) zu ändern, müssen Sie bestimmte Nachrichten an das Steuerelement senden, anstatt [ModifyStyle](cwnd-class.md#modifystyle)zu verwenden. Weitere Informationen finden Sie unter Bearbeiten von [Steuerelementstilen](/windows/win32/Controls/edit-control-styles) im Windows SDK.

Weitere Informationen `CEdit`zu finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a>CEdit::CanUndo

Rufen Sie diese Funktion auf, um zu bestimmen, ob der letzte Bearbeitungsvorgang rückgängig gemacht werden kann.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der letzte `Undo` Bearbeitungsvorgang durch einen Aufruf der Memberfunktion rückgängig gemacht werden kann. 0, wenn sie nicht rückgängig gemacht werden kann.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EM_CANUNDO](/windows/win32/Controls/em-canundo) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEdit::Undo](#undo).

## <a name="ceditcedit"></a><a name="cedit"></a>CEdit::CEdit

Erstellt ein `CEdit`-Objekt.

```
CEdit();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [Erstellen,](#create) um das Windows-Bearbeitungssteuerelement zu erstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a>CEdit::CharFromPos

Rufen Sie diese Funktion auf, um die Null-basierten Linien- und `CEdit` Zeichenindizes des Zeichens abzurufen, das dem angegebenen Punkt in diesem Steuerelement am nächsten liegt.

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Die Koordinaten eines Punktes im `CEdit` Clientbereich dieses Objekts.

### <a name="return-value"></a>Rückgabewert

Der Zeichenindex im WORD niedriger Ordnung und der Linienindex im WORD mit hoher Ordnung.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Memberfunktion ist ab Windows 95 und Windows NT 4.0 verfügbar.

Weitere Informationen finden Sie unter [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a>CEdit::Klar

Rufen Sie diese Funktion auf, um die aktuelle Auswahl (falls vorhanden) im Bearbeitungssteuerelement zu löschen (löschen).

```
void Clear();
```

### <a name="remarks"></a>Bemerkungen

Die von `Clear` ausgeführte Löschung kann rückgängig gemacht werden, indem die [Rückgängig-Memberfunktion](#undo) aufgerufen wird.

Um die aktuelle Auswahl zu löschen und den gelöschten Inhalt in der Zwischenablage zu platzieren, rufen Sie die [Funktion "Member ausschneiden"](#cut) auf.

Weitere Informationen finden Sie unter [WM_CLEAR](/windows/win32/dataxchg/wm-clear) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a>CEdit::Kopieren

Rufen Sie diese Funktion auf, um die aktuelle Auswahl (falls vorhanden) im Bearbeitungssteuerelement in der Zwischenablage im format CF_TEXT zu ändern.

```
void Copy();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [WM_COPY](/windows/win32/dataxchg/wm-copy) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a>CEdit::Erstellen

Erstellt das Windows-Bearbeitungssteuerelement und `CEdit` fügt es an das Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Bearbeitungssteuerelements an. Wenden Sie eine beliebige Kombination von [Bearbeitungsstilen](styles-used-by-mfc.md#edit-styles) auf das Steuerelement an.

*Rect*<br/>
Gibt die Größe und Position des Bearbeitungssteuerelements an. Kann ein `CRect` Objekt `RECT` oder eine Struktur sein.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Bearbeitungssteuerelements (in der Regel a `CDialog`) an. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Bearbeitungssteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CEdit` ein Objekt in zwei Schritten. Rufen Sie `CEdit` zunächst den Konstruktor auf, und rufen Sie dann `Create` `CEdit` auf, das das Windows-Bearbeitungssteuerelement erstellt und an das Objekt anfügt.

Bei `Create` der Ausführung sendet Windows die [Nachrichten WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create)und [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) an das Bearbeitungssteuerelement.

Diese Nachrichten werden standardmäßig von den Memberfunktionen [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate)und `CWnd` [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) in der Basisklasse verarbeitet. Um die Standardnachrichtenbehandlung zu erweitern, `CEdit`leiten Sie eine Klasse von ab , fügen Sie der neuen Klasse eine Nachrichtenzuordnung hinzu, und überschreiben Sie die oben genannten Message-Handler-Memberfunktionen. Überschreiben `OnCreate`Sie z. B., um die erforderliche Initialisierung für die neue Klasse durchzuführen.

Wenden Sie die folgenden [Fensterstile](styles-used-by-mfc.md#window-styles) auf ein Bearbeitungssteuerelement an.

- WS_CHILD Immer

- WS_VISIBLE In der Regel

- WS_DISABLED Selten

- WS_GROUP Zu Gruppensteuerelementen

- WS_TABSTOP So wird das Bearbeitungssteuerelement in die Tabstoppreihenfolge eingeschlossen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a>CEdit::Schnitt

Rufen Sie diese Funktion auf, um die aktuelle Auswahl (falls vorhanden) im Bearbeitungssteuerelement zu löschen (auszuschneiden) und den gelöschten Text in die Zwischenablage im CF_TEXT Format zu kopieren.

```
void Cut();
```

### <a name="remarks"></a>Bemerkungen

Die von `Cut` ausgeführte Löschung kann rückgängig gemacht werden, indem die [Rückgängig-Memberfunktion](#undo) aufgerufen wird.

Um die aktuelle Auswahl zu löschen, ohne den gelöschten Text in die Zwischenablage zu legen, rufen Sie die Funktion [Member löschen](#clear) auf.

Weitere Informationen finden Sie unter [WM_CUT](/windows/win32/dataxchg/wm-cut) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer

Rufen Sie diese Funktion auf, um das Rückgängig-Flag eines Bearbeitungssteuerelements zurückzusetzen (löschen).

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Bemerkungen

Das Bearbeitungssteuerelement kann nun den letzten Vorgang nicht mehr rückgängig machen. Das Rückgängig-Flag wird immer dann festgelegt, wenn ein Vorgang innerhalb des Bearbeitungssteuerelements rückgängig gemacht werden kann.

Das Rückgängig-Flag wird automatisch gelöscht, wenn die [SetWindowText-](../../mfc/reference/cwnd-class.md#setwindowtext) oder [SetHandle-Memberfunktionen](#sethandle) `CWnd` aufgerufen werden.

Weitere Informationen finden Sie unter [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a>CEdit::FmtLines

Rufen Sie diese Funktion auf, um die Einschlussung weicher Zeilenumbruchzeichen in ein mehrzeiliger Bearbeitungssteuerelement oder -aus in ein oder aus.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parameter

*bAddEOL*<br/>
Gibt an, ob weiche Zeilenumbruchzeichen eingefügt werden sollen. Der Wert TRUE fügt die Zeichen ein. ein Wert von FALSE entfernt sie.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn eine Formatierung auftritt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein weicher Zeilenumbruch besteht aus zwei Wagenrückläufen und einem Zeilenvorschub, der am Ende einer Zeile eingefügt wird, die aufgrund von Wortumbruch unterbrochen wird. Ein harter Zeilenumbruch besteht aus einem Wagenrücklauf und einem Zeilenvorschub. Zeilen, die mit einem harten Zeilenumbruch enden, sind von `FmtLines`nicht betroffen.

Windows reagiert nur, `CEdit` wenn es sich bei dem Objekt um ein mehrzeiliges Bearbeitungssteuerelement handelt.

`FmtLines`wirkt sich nur auf den von [GetHandle](#gethandle) zurückgegebenen Puffer und den von [WM_GETTEXT](/windows/win32/winmsg/wm-gettext)zurückgegebenen Text aus. Es hat keine Auswirkungen auf die Anzeige des Textes innerhalb des Bearbeitungssteuerelements.

Weitere Informationen finden Sie unter [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a>CEdit::GetCueBanner

Ruft den Text ab, der als Text-Cue oder Tipp in einem Bearbeitungssteuerelement angezeigt wird, wenn das Steuerelement leer ist.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
[out] Ein Zeiger auf eine Zeichenfolge, die den Cue-Text enthält.

*cchText*<br/>
[in] Die Anzahl der Zeichen, die empfangen werden können. Diese Zahl enthält das beendende NULL-Zeichen.

### <a name="return-value"></a>Rückgabewert

Für die erste Überladung TRUE, wenn die Methode erfolgreich ist; andernfalls FALSE.

Für die zweite Überladung eine [CString,](../../atl-mfc-shared/using-cstring.md) die den Cue-Text enthält, wenn die Methode erfolgreich ist; andernfalls die leere Zeichenfolge ("").

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner) Nachricht, die im Windows SDK beschrieben wird. Weitere Informationen finden [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) Sie im Edit_GetCueBannerText-Makro.

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine

Rufen Sie diese Funktion auf, um die oberste sichtbare Zeile in einem Bearbeitungssteuerelement zu bestimmen.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index der obersten sichtbaren Linie. Bei einzeiligen Bearbeitungssteuerelementen ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a>CEdit::GetHandle

Rufen Sie diese Funktion auf, um ein Handle in den Speicher abzurufen, der derzeit für ein mehrzeiliges Bearbeitungssteuerelement reserviert ist.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Rückgabewert

Ein lokales Speicherhandle, das den Puffer identifiziert, der den Inhalt des Bearbeitungssteuerelements enthält. Wenn ein Fehler auftritt, z. B. das Senden der Nachricht an ein einzeiliges Bearbeitungssteuerelement, ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Das Handle ist ein lokales Speicherhandle und kann von allen **lokalen** Windows-Speicherfunktionen verwendet werden, die ein lokales Speicherhandle als Parameter verwenden.

`GetHandle`wird nur von mehrzeiligen Bearbeitungssteuerelementen verarbeitet.

Rufen `GetHandle` Sie ein mehrzeiliges Bearbeitungssteuerelement in einem Dialogfeld nur an, wenn das Dialogfeld mit dem DS_LOCALEDIT Stilflagsatz erstellt wurde. Wenn der DS_LOCALEDIT Stil nicht festgelegt ist, erhalten Sie weiterhin einen Rückgabewert ungleich Null, aber Sie können den zurückgegebenen Wert nicht verwenden.

> [!NOTE]
> `GetHandle`funktioniert nicht mit Windows 95/98. Wenn Sie `GetHandle` in Windows 95/98 aufrufen, wird NULL zurückgegeben. `GetHandle`funktioniert wie unter Windows NT, Version 3.51 und höher dokumentiert.

Weitere Informationen finden Sie unter [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a>CEdit::GetHighlight

Ruft die Indizes des ersten und letzten Zeichens in einem Textbereich ab, der im aktuellen Bearbeitungssteuerelement hervorgehoben ist.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pichStart*|[out] Nullbasierter Index des ersten Zeichens im hervorgehobenen Textbereich.|
|*pichEnd*|[out] Nullbasierter Index des letzten Zeichens im hervorgehobenen Textbereich.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [EM_GETHILITE](/windows/win32/Controls/em-gethilite) Nachricht, die im Windows SDK beschrieben wird. Beide `SetHighlight` `GetHighlight` und sind derzeit nur für UNICODE-Builds aktiviert.

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a>CEdit::GetLimitText

Rufen Sie diese Memberfunktion auf, `CEdit` um das Textlimit für dieses Objekt abzurufen.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Textgrenze in TCHARs `CEdit` für dieses Objekt.

### <a name="remarks"></a>Bemerkungen

Die Textgrenze ist die maximale Textmenge in TCHARs, die das Bearbeitungssteuerelement akzeptieren kann.

> [!NOTE]
> Diese Memberfunktion ist ab Windows 95 und Windows NT 4.0 verfügbar.

Weitere Informationen finden Sie unter [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a>CEdit::GetLine

Rufen Sie diese Funktion auf, um eine Textzeile aus einem Bearbeitungssteuerelement abzurufen, und platziert sie in *lpszBuffer*.

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt die Zeilennummer an, die von einem mehrzeiligen Bearbeitungssteuerelement abgerufen werden soll. Zeilennummern sind nullbasiert. ein Wert von 0 gibt die erste Zeile an. Dieser Parameter wird von einem einzeiligen Bearbeitungssteuerelement ignoriert.

*lpszBuffer*<br/>
Zeigt auf den Puffer, der eine Kopie der Zeile empfängt. Das erste Wort des Puffers muss die maximale Anzahl von TCHARs angeben, die in den Puffer kopiert werden können.

*nMaxLength*<br/>
Gibt die maximale Anzahl von TCHAR-Zeichen an, die in den Puffer kopiert werden können. `GetLine`platziert diesen Wert im ersten Wort von *lpszBuffer,* bevor der Aufruf von Windows gemacht wird.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der tatsächlich kopierten Zeichen. Der Rückgabewert ist 0, wenn die von *nIndex* angegebene Zeilennummer größer als die Anzahl der Zeilen im Bearbeitungssteuerelement ist.

### <a name="remarks"></a>Bemerkungen

Die kopierte Zeile enthält kein Null-Beendigungszeichen.

Weitere Informationen finden Sie unter [EM_GETLINE](/windows/win32/Controls/em-getline) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CEdit::GetLineCount](#getlinecount).

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a>CEdit::GetLineCount

Rufen Sie diese Funktion auf, um die Anzahl der Zeilen in einem mehrzeiligen Bearbeitungssteuerelement abzurufen.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die die Anzahl der Zeilen im mehrzeiligen Bearbeitungssteuerelement enthält. Wenn kein Text in das Bearbeitungssteuerelement eingegeben wurde, ist der Rückgabewert 1.

### <a name="remarks"></a>Bemerkungen

`GetLineCount`wird nur von mehrzeiligen Bearbeitungssteuerelementen verarbeitet.

Weitere Informationen finden Sie unter [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a>CEdit::GetMargins

Rufen Sie diese Memberfunktion auf, um den linken und rechten Rand dieses Bearbeitungssteuerelements abzurufen.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite des linken Rands im WORD niedriger Ordnung und die Breite des rechten Rands im WORD mit hoher Ordnung.

### <a name="remarks"></a>Bemerkungen

Die Ränder werden in Pixeln gemessen.

> [!NOTE]
> Diese Memberfunktion ist ab Windows 95 und Windows NT 4.0 verfügbar.

Weitere Informationen finden Sie unter [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditgetmodify"></a><a name="getmodify"></a>CEdit::GetModify

Rufen Sie diese Funktion auf, um zu bestimmen, ob der Inhalt eines Bearbeitungssteuerelements geändert wurde.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Inhalt der Bearbeitungssteuerung geändert wurde; 0 wenn sie unverändert geblieben sind.

### <a name="remarks"></a>Bemerkungen

Windows verwaltet ein internes Flag, das angibt, ob der Inhalt des Bearbeitungssteuerelements geändert wurde. Dieses Flag wird gelöscht, wenn das Bearbeitungssteuerelement zum ersten Mal erstellt wird, und kann auch durch Aufrufen der [SetModify-Memberfunktion](#setmodify) gelöscht werden.

Weitere Informationen finden Sie unter [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a>CEdit::GetPasswordChar

Rufen Sie diese Funktion auf, um das Kennwortzeichen abzurufen, das in einem Bearbeitungssteuerelement angezeigt wird, wenn der Benutzer Text eingibt.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Zeichen an, das angezeigt werden soll, anstelle des Zeichens, das der Benutzer eingegeben hat. Der Rückgabewert ist NULL, wenn kein Kennwortzeichen vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Bearbeitungssteuerelement mit dem ES_PASSWORD-Stil erstellen, bestimmt die DLL, die das Steuerelement unterstützt, das Standardkennwortzeichen. Das Manifest oder die [InitCommonControlsEx-Methode](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) bestimmt, welche DLL das Bearbeitungssteuerelement unterstützt. Wenn user32.dll das Bearbeitungssteuerelement unterstützt, lautet das Standardkennwortzeichen ASTERISK ('*', U+002A). Wenn comctl32.dll Version 6 das Bearbeitungssteuerelement unterstützt, ist das Standardzeichen BLACK CIRCLE ('', U+25CF). Weitere Informationen dazu, welche DLL und Version die allgemeinen Steuerelemente unterstützt, finden Sie unter [Shell- und Common Controls-Versionen](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\)).

Diese Methode sendet die [EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a>CEdit::GetRect

Rufen Sie diese Funktion auf, um das Formatierungsrechteck eines Bearbeitungssteuerelements abzurufen.

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf `RECT` die Struktur, die das Formatierungsrechteck empfängt.

### <a name="remarks"></a>Bemerkungen

Das Formatierungsrechteck ist das einschränkende Rechteck des Textes, das unabhängig von der Größe des Bearbeitungssteuerungsfensters ist.

Das Formatierungsrechteck eines mehrzeiligen Bearbeitungssteuerelements kann durch die Memberfunktionen [SetRect](#setrect) und [SetRectNP](#setrectnp) geändert werden.

Weitere Informationen finden Sie unter [EM_GETRECT](/windows/win32/Controls/em-getrect) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEdit::LimitText](#limittext).

## <a name="ceditgetsel"></a><a name="getsel"></a>CEdit::GetSel

Rufen Sie diese Funktion auf, um die Start- und Endzeichenpositionen der aktuellen Auswahl (falls vorhanden) in einem Bearbeitungssteuerelement mithilfe des Rückgabewerts oder der Parameter abzurufen.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Parameter

*nStartChar*<br/>
Verweis auf eine ganze Zahl, die die Position des ersten Zeichens in der aktuellen Auswahl empfängt.

*nEndChar*<br/>
Verweis auf eine ganze Zahl, die die Position des ersten nicht ausgewählten Zeichens über das Ende der aktuellen Auswahl hinaus empfängt.

### <a name="return-value"></a>Rückgabewert

Die Version, die ein DWORD zurückgibt, gibt einen Wert zurück, der die Startposition im Wort niedriger Ordnung und die Position des ersten nicht ausgewählten Zeichens nach dem Ende der Auswahl im Wort hoher Ordnung enthält.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EM_GETSEL](/windows/win32/Controls/em-getsel) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a>CEdit::HideBalloonTip

Blendet alle Sprechblasenspitzen aus, die dem aktuellen Bearbeitungssteuerelement zugeordnet sind.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sendet die [EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip) Nachricht, die im Windows SDK beschrieben wird.

## <a name="ceditlimittext"></a><a name="limittext"></a>CEdit::LimitText

Rufen Sie diese Funktion auf, um die Länge des Textes zu begrenzen, den der Benutzer in ein Bearbeitungssteuerelement eingeben kann.

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parameter

*nChars*<br/>
Gibt die Länge (in TCHARs) des Textes an, den der Benutzer eingeben kann. Wenn dieser Parameter 0 ist, wird die Textlänge auf UINT_MAX Bytes festgelegt. Dies ist das Standardverhalten.

### <a name="remarks"></a>Bemerkungen

Durch ändern des Textlimits wird nur der Text eingeschränkt, den der Benutzer eingeben kann. It has no effect on any text already in the edit control, nor does it affect the length of the text copied to the edit control by the [SetWindowText](cwnd-class.md#setwindowtext) member function in `CWnd`. Wenn eine Anwendung `SetWindowText` die Funktion verwendet, um mehr Text in `LimitText`ein Bearbeitungssteuerelement zu platzieren, als im Aufruf von angegeben ist, kann der Benutzer den Text innerhalb des Bearbeitungssteuerelements löschen. Die Textbeschränkung verhindert jedoch, dass der Benutzer den vorhandenen Text durch neuen Text ersetzt, es sei denn, das Löschen der aktuellen Auswahl führt dazu, dass der Text unter die Textgrenze fällt.

> [!NOTE]
> In Win32 (Windows NT und Windows 95/98) ersetzt [SetLimitText](#setlimittext) diese Funktion.

Weitere Informationen finden Sie unter [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a>CEdit::LineFromChar

Rufen Sie diese Funktion auf, um die Zeilennummer der Zeile abzurufen, die den angegebenen Zeichenindex enthält.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält den nullbasierten Indexwert für das gewünschte Zeichen im Text des Bearbeitungssteuerelements oder enthält -1. Wenn *nIndex* -1 ist, gibt es die aktuelle Zeile an, d. h. die Zeile, die die Einstellte enthält.

### <a name="return-value"></a>Rückgabewert

Die nullbasierte Zeilennummer der Zeile, die den von *nIndex*angegebenen Zeichenindex enthält. Wenn *nIndex* -1 ist, wird die Nummer der Zeile zurückgegeben, die das erste Zeichen der Auswahl enthält. Wenn keine Auswahl vorhanden ist, wird die aktuelle Zeilennummer zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Ein Zeichenindex ist die Anzahl der Zeichen vom Anfang des Bearbeitungssteuerelements.

Diese Memberfunktion wird nur von mehrzeiligen Bearbeitungssteuerelementen verwendet.

Weitere Informationen finden Sie unter [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a>CEdit::LineIndex

Rufen Sie diese Funktion auf, um den Zeichenindex einer Linie innerhalb eines mehrzeiligen Bearbeitungssteuerelements abzurufen.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parameter

*nLine*<br/>
Enthält den Indexwert für die gewünschte Zeile im Text des Bearbeitungssteuerelements oder enthält -1. Wenn *nLine* -1 ist, gibt es die aktuelle Zeile an, d. h. die Zeile, die die Einstellte enthält.

### <a name="return-value"></a>Rückgabewert

Der Zeichenindex der in *nLine* oder -1 angegebenen Linie, wenn die angegebene Zeilennummer größer als die Anzahl der Zeilen im Bearbeitungssteuerelement ist.

### <a name="remarks"></a>Bemerkungen

Der Zeichenindex ist die Anzahl der Zeichen vom Anfang des Bearbeitungssteuerelements bis zur angegebenen Zeile.

Diese Memberfunktion wird nur von mehrzeiligen Bearbeitungssteuerelementen verarbeitet.

Weitere Informationen finden Sie unter [EM_LINEINDEX](/windows/win32/controls/em-lineindex) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a>CEdit::LineLength

Ruft die Länge einer Linie in einem Bearbeitungssteuerelement ab.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parameter

*nLine*<br/>
Der nullbasierte Index eines Zeichens in der Zeile, dessen Länge abgerufen werden soll. Der Standardwert ist -1.

### <a name="return-value"></a>Rückgabewert

Bei einzeiligen Bearbeitungssteuerelementen ist der Rückgabewert die Länge des Texts im Bearbeitungssteuerelement in TCHARs.

Bei mehrzeiligen Bearbeitungssteuerelementen ist der Rückgabewert die Länge der durch den Parameter *nLine* angegebenen Zeile in TCHARs. Bei ANSI-Text ist die Länge die Anzahl der Bytes in der Zeile. Bei Unicode-Text ist die Länge die Anzahl der Zeichen in der Zeile. Die Länge enthält nicht das Wagen-Rücklaufzeichen am Ende der Zeile.

Wenn der *nLine-Parameter* mehr als die Anzahl der Zeichen im Steuerelement ist, ist der Rückgabewert Null.

Wenn der *nLine-Parameter* -1 ist, ist der Rückgabewert die Anzahl der nicht ausgewählten Zeichen in den Zeilen, die ausgewählte Zeichen enthalten. Wenn sich die Auswahl beispielsweise vom vierten Zeichen einer Zeile bis zum achten Zeichen vom Ende der nächsten Zeile erstreckt, beträgt der Rückgabewert 10. Das heißt, drei Zeichen in der ersten Zeile und sieben in der nächsten.

Weitere Informationen zum TCHAR-Typ finden Sie in der TCHAR-Zeile in der Tabelle unter [Windows-Datentypen](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von der [EM_LINELENGTH-Meldung](/windows/win32/Controls/em-linelength) unterstützt, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEdit::LineIndex](#lineindex).

## <a name="ceditlinescroll"></a><a name="linescroll"></a>CEdit::LineScroll

Rufen Sie diese Funktion auf, um den Text eines mehrzeiligen Bearbeitungssteuerelements zu scrollen.

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parameter

*nLines*<br/>
Gibt die Anzahl der Linien an, die vertikal gescrollt werden sollen.

*nChars*<br/>
Gibt die Anzahl der Zeichenpositionen an, die horizontal gescrollt werden sollen. Dieser Wert wird ignoriert, wenn das Bearbeitungssteuerelement entweder den ES_RIGHT- oder ES_CENTER-Stil hat.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird nur von mehrzeiligen Bearbeitungssteuerelementen verarbeitet.

Das Bearbeitungssteuerelement führt keinen vertikalen Bildlauf über die letzte Textzeile im Bearbeitungssteuerelement. Wenn die aktuelle Zeile plus die anzahl der von *nLines* angegebenen Zeilen die Gesamtzahl der Zeilen im Bearbeitungssteuerelement überschreitet, wird der Wert so angepasst, dass die letzte Zeile des Bearbeitungssteuerelements an den Anfang des Bearbeitungssteuerungsfensters gescrollt wird.

`LineScroll`kann verwendet werden, um horizontal über das letzte Zeichen einer beliebigen Zeile zu scrollen.

Weitere Informationen finden Sie unter [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CEdit::GetFirstVisibleLine](#getfirstvisibleline).

## <a name="ceditpaste"></a><a name="paste"></a>CEdit::Paste

Rufen Sie diese Funktion auf, um `CEdit` die Daten aus der Zwischenablage in die einfüge-Einfügemarke einzufügen.

```
void Paste();
```

### <a name="remarks"></a>Bemerkungen

Daten werden nur eingefügt, wenn die Zwischenablage Daten im CF_TEXT-Format enthält.

Weitere Informationen finden Sie unter [WM_PASTE](/windows/win32/dataxchg/wm-paste) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a>CEdit::PosVonChar

Rufen Sie diese Funktion auf, um die Position (obere `CEdit` linke Ecke) eines bestimmten Zeichens innerhalb dieses Objekts abzurufen.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parameter

*Nchar*<br/>
Der nullbasierte Index des angegebenen Zeichens.

### <a name="return-value"></a>Rückgabewert

Die Koordinaten der oberen linken Ecke des durch *nChar*angegebenen Zeichens .

### <a name="remarks"></a>Bemerkungen

Das Zeichen wird angegeben, indem der nullbasierte Indexwert angegeben wird. Wenn *nChar* größer als der Index des `CEdit` letzten Zeichens in diesem Objekt ist, gibt der Rückgabewert die Koordinaten der Zeichenposition direkt hinter dem letzten Zeichen in diesem `CEdit` Objekt an.

> [!NOTE]
> Diese Memberfunktion ist ab Windows 95 und Windows NT 4.0 verfügbar.

Weitere Informationen finden Sie unter [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CEdit::LineFromChar](#linefromchar).

## <a name="ceditreplacesel"></a><a name="replacesel"></a>CEdit::ReplaceSel

Rufen Sie diese Funktion auf, um die aktuelle Auswahl in einem Bearbeitungssteuerelement durch den von *lpszNewText*angegebenen Text zu ersetzen.

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parameter

*lpszNewText*<br/>
Zeigt auf eine null-beendete Zeichenfolge, die den Ersatztext enthält.

*bCanUndo*<br/>
Um anzugeben, dass diese Funktion rückgängig gemacht werden kann, legen Sie den Wert dieses Parameters auf TRUE fest. Der Standardwert ist FALSE.

### <a name="remarks"></a>Bemerkungen

Ersetzt nur einen Teil des Textes in einem Bearbeitungssteuerelement. Wenn Sie den gesamten Text ersetzen möchten, verwenden Sie die Memberfunktion [CWnd::SetWindowText.](cwnd-class.md#setwindowtext)

Wenn keine aktuelle Auswahl vorhanden ist, wird der Ersatztext an der aktuellen Cursorposition eingefügt.

Weitere Informationen finden Sie unter [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEdit::LineIndex](#lineindex).

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a>CEdit::SetCueBanner

Legt den Text fest, der als Text-Cue oder Tipp in einem Bearbeitungssteuerelement angezeigt wird, wenn das Steuerelement leer ist.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
[in] Zeiger auf eine Zeichenfolge, die den Cue enthält, der im Bearbeitungssteuerelement angezeigt werden soll.

*fDrawWhenFocused*<br/>
[in] Wenn FALSE, wird das Cue-Banner nicht gezeichnet, wenn der Benutzer auf das Bearbeitungssteuerelement klickt und dem Steuerelement den Fokus gibt.

Wenn TRUE, wird das Cue-Banner auch dann gezeichnet, wenn das Steuerelement den Fokus hat. Das Cue-Banner verschwindet, wenn der Benutzer mit der Eingabe des Steuerelements beginnt.

Der Standardwert ist FALSE.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner) Nachricht, die im Windows SDK beschrieben wird. Weitere Informationen finden [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) Sie im Edit_SetCueBannerTextFocused-Makro.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CEdit::SetCueBanner-Methode](#setcuebanner) veranschaulicht.

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a>CEdit::SetHandle

Rufen Sie diese Funktion auf, um das Handle auf den lokalen Speicher festzulegen, der von einem mehrzeiligen Bearbeitungssteuerelement verwendet wird.

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parameter

*hBuffer*<br/>
Enthält ein Handle für den lokalen Speicher. Dieses Handle muss durch einen vorherigen Aufruf der [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows-Funktion mit dem LMEM_MOVEABLE-Flag erstellt worden sein. Es wird davon ausgegangen, dass der Speicher eine null-terminierte Zeichenfolge enthält. Ist dies nicht der Fall, sollte das erste Byte des zugewiesenen Speichers auf 0 gesetzt werden.

### <a name="remarks"></a>Bemerkungen

Das Bearbeitungssteuerelement verwendet dann diesen Puffer, um den aktuell angezeigten Text zu speichern, anstatt einen eigenen Puffer zuzuweisen.

Diese Memberfunktion wird nur von mehrzeiligen Bearbeitungssteuerelementen verarbeitet.

Bevor eine Anwendung ein neues Speicherhandle festlegt, sollte sie die [GetHandle-Memberfunktion](#gethandle) verwenden, um `LocalFree` das Handle in den aktuellen Speicherpuffer zu bringen und diesen Speicher mithilfe der Windows-Funktion freizugeben.

`SetHandle`löscht den Rückgängig-Puffer (die [CanUndo-Memberfunktion](#canundo) gibt dann 0 zurück) und das interne Änderungsflag (die [GetModify-Memberfunktion](#getmodify) gibt dann 0 zurück). Das Bearbeitungssteuerungsfenster wird neu gezeichnet.

Sie können diese Memberfunktion in einem mehrzeiligen Bearbeitungssteuerelement in einem Dialogfeld nur verwenden, wenn Sie das Dialogfeld mit dem DS_LOCALEDIT Stilflagsatz erstellt haben.

> [!NOTE]
> `GetHandle`funktioniert nicht mit Windows 95/98. Wenn Sie `GetHandle` in Windows 95/98 aufrufen, wird NULL zurückgegeben. `GetHandle`funktioniert wie unter Windows NT, Version 3.51 und höher dokumentiert.

Weitere Informationen finden Sie unter [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)und [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a>CEdit::SetHighlight

Hebt einen Textbereich hervor, der im aktuellen Bearbeitungssteuerelement angezeigt wird.

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*ichStart*|[in] Nullbasierter Index des ersten Zeichens im zu markierenden Textbereich.|
|*ichEnd*|[in] Nullbasierter Index des letzten Zeichens im zu markierenden Textbereich.|

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [EM_SETHILITE](/windows/win32/Controls/em-sethilite) Nachricht, die im Windows SDK beschrieben wird.  Diese Methode sendet die [EM_SETHILITE](/windows/win32/Controls/em-sethilite) Nachricht, die im Windows SDK beschrieben wird. Beide `SetHighlight` `GetHighlight` und sind nur für UNICODE-Builds aktiviert.

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a>CEdit::SetLimitText

Rufen Sie diese Memberfunktion auf, `CEdit` um die Textgrenze für dieses Objekt festzulegen.

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parameter

*nMax*<br/>
Die neue Textbeschränkung in Zeichen.

### <a name="remarks"></a>Bemerkungen

Die Textgrenze ist die maximale Textmenge in Zeichen, die das Bearbeitungssteuerelement akzeptieren kann.

Durch ändern des Textlimits wird nur der Text eingeschränkt, den der Benutzer eingeben kann. It has no effect on any text already in the edit control, nor does it affect the length of the text copied to the edit control by the [SetWindowText](cwnd-class.md#setwindowtext) member function in `CWnd`. Wenn eine Anwendung `SetWindowText` die Funktion verwendet, um mehr Text in `LimitText`ein Bearbeitungssteuerelement zu platzieren, als im Aufruf von angegeben ist, kann der Benutzer den Text innerhalb des Bearbeitungssteuerelements löschen. Die Textbeschränkung verhindert jedoch, dass der Benutzer den vorhandenen Text durch neuen Text ersetzt, es sei denn, das Löschen der aktuellen Auswahl führt dazu, dass der Text unter die Textgrenze fällt.

Diese Funktion ersetzt [LimitText](#limittext) in Win32.

Weitere Informationen finden Sie unter [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmargins"></a><a name="setmargins"></a>CEdit::SetMargins

Rufen Sie diese Methode auf, um den linken und rechten Rand dieses Bearbeitungssteuerelements festzulegen.

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parameter

*nLeft*<br/>
Die Breite des neuen linken Rands in Pixel.

*nRight*<br/>
Die Breite des neuen rechten Rands in Pixel.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Memberfunktion ist ab Windows 95 und Windows NT 4.0 verfügbar.

Weitere Informationen finden Sie unter [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmodify"></a><a name="setmodify"></a>CEdit::SetModify

Rufen Sie diese Funktion auf, um das geänderte Flag für ein Bearbeitungssteuerelement festzulegen oder zu löschen.

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parameter

*bModified*<br/>
Der Wert TRUE gibt an, dass der Text geändert wurde, und ein Wert von FALSE gibt an, dass er unverändert ist. Standardmäßig wird das geänderte Flag gesetzt.

### <a name="remarks"></a>Bemerkungen

Das geänderte Flag gibt an, ob der Text im Bearbeitungssteuerelement geändert wurde. Sie wird automatisch festgelegt, wenn der Benutzer den Text ändert. Sein Wert kann mit der [GetModify-Memberfunktion](#getmodify) abgerufen werden.

Weitere Informationen finden Sie unter [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEdit::GetModify](#getmodify).

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a>CEdit::SetPasswordChar

Rufen Sie diese Funktion auf, um ein Kennwortzeichen festzulegen oder zu entfernen, das in einem Bearbeitungssteuerelement angezeigt wird, wenn der Benutzer Text eingibt.

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parameter

*Ch*<br/>
Gibt das Zeichen an, das anstelle des vom Benutzer eingegebenen Zeichens angezeigt werden soll. Wenn *ch* 0 ist, werden die tatsächlichen Zeichen angezeigt, die vom Benutzer eingegeben werden.

### <a name="remarks"></a>Bemerkungen

Wenn ein Kennwortzeichen festgelegt wird, wird dieses Zeichen für jedes Zeichen angezeigt, das der Benutzer eingibt.

Diese Memberfunktion hat keine Auswirkungen auf ein mehrzeiliges Bearbeitungssteuerelement.

Wenn `SetPasswordChar` die Memberfunktion `CEdit` aufgerufen wird, werden alle sichtbaren Zeichen mit dem von *ch*angegebenen Zeichen neu gezeichnet.

Wenn das Bearbeitungssteuerelement mit dem [Formatformat ES_PASSWORD](styles-used-by-mfc.md#edit-styles) erstellt wird, wird <strong>\*</strong>das Standardkennwortzeichen auf ein Sternchen ( ) festgelegt. Dieser Stil wird `SetPasswordChar` entfernt, wenn *ch* auf 0 gesetzt aufgerufen wird.

Weitere Informationen finden Sie unter [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a>CEdit::SetReadOnly

Ruft diese Funktion auf, um den schreibgeschützten Status eines Bearbeitungssteuerelements festzulegen.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parameter

*bReadOnly*<br/>
Gibt an, ob der schreibgeschützte Status des Bearbeitungssteuerelements festgelegt oder entfernt werden soll. Der Wert TRUE legt den Status auf schreibgeschützt fest. ein Wert von FALSE legt den Status auf Lesen/Schreiben fest.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich ist, oder 0, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Die aktuelle Einstellung kann gefunden werden, indem Sie das [ES_READONLY-Flag](styles-used-by-mfc.md#edit-styles) im Rückgabewert von [CWnd::GetStyle](cwnd-class.md#getstyle)testen.

Weitere Informationen finden Sie unter [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a>CEdit::SetRect

Rufen Sie diese Funktion auf, um die Bemaßungen eines Rechtecks mithilfe der angegebenen Koordinaten festzulegen.

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf `RECT` die `CRect` Struktur oder das Objekt, das die neuen Dimensionen des Formatierungsrechtecks angibt.

### <a name="remarks"></a>Bemerkungen

Dieses Element wird nur von mehrzeiligen Bearbeitungssteuerelementen verarbeitet.

Verwenden `SetRect` Sie diese Datei, um das Formatierungsrechteck eines mehrzeiligen Bearbeitungssteuerelements festzulegen. Das Formatierungsrechteck ist das einschränkende Rechteck des Textes, das unabhängig von der Größe des Bearbeitungssteuerungsfensters ist. Wenn das Bearbeitungssteuerelement zum ersten Mal erstellt wird, entspricht das Formatierungsrechteck dem Clientbereich des Bearbeitungssteuerungsfensters. Mithilfe der `SetRect` Memberfunktion kann eine Anwendung das Formatierungsrechteck größer oder kleiner als das Fenster für die Bearbeitungssteuerung machen.

Wenn das Bearbeitungssteuerelement über keine Bildlaufleiste verfügt, wird Text abgeschnitten und nicht umbrochen, wenn das Formatierungsrechteck größer als das Fenster ist. Wenn das Bearbeitungssteuerelement einen Rahmen enthält, wird das Formatierungsrechteck um die Größe des Rahmens verringert. Wenn Sie das von `GetRect` der Memberfunktion zurückgegebene Rechteck anpassen, müssen Sie `SetRect`die Größe des Rahmens entfernen, bevor Sie das Rechteck an übergeben.

Wenn `SetRect` aufgerufen wird, wird auch der Text des Bearbeitungssteuerelements neu formatiert und erneut angezeigt.

Weitere Informationen finden Sie unter [EM_SETRECT](/windows/win32/Controls/em-setrect) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a>CEdit::SetRectNP

Rufen Sie diese Funktion auf, um das Formatierungsrechteck eines mehrzeiligen Bearbeitungssteuerelements festzulegen.

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf `RECT` eine `CRect` Struktur oder ein Objekt, das die neuen Bemaßungen des Rechtecks angibt.

### <a name="remarks"></a>Bemerkungen

Das Formatierungsrechteck ist das einschränkende Rechteck des Textes, das unabhängig von der Größe des Bearbeitungssteuerungsfensters ist.

`SetRectNP`ist mit `SetRect` der Memberfunktion identisch, mit der Ausnahme, dass das Bearbeitungssteuerungsfenster nicht neu gezeichnet wird.

Wenn das Bearbeitungssteuerelement zum ersten Mal erstellt wird, entspricht das Formatierungsrechteck dem Clientbereich des Bearbeitungssteuerungsfensters. Durch Aufrufen `SetRectNP` der Memberfunktion kann eine Anwendung das Formatierungsrechteck größer oder kleiner als das Fenster für die Bearbeitungssteuerung machen.

Wenn das Bearbeitungssteuerelement über keine Bildlaufleiste verfügt, wird Text abgeschnitten und nicht umbrochen, wenn das Formatierungsrechteck größer als das Fenster ist.

Dieses Element wird nur von mehrzeiligen Bearbeitungssteuerelementen verarbeitet.

Weitere Informationen finden Sie unter [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEdit::SetRect](#setrect).

## <a name="ceditsetsel"></a><a name="setsel"></a>CEdit::SetSel

Rufen Sie diese Funktion auf, um einen Zeichenbereich in einem Bearbeitungssteuerelement auszuwählen.

```
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>Parameter

*dwSelection*<br/>
Gibt die Startposition im Wort niedriger Ordnung und die Endposition im Wort hoher Ordnung an. Wenn das Wort niedriger Ordnung 0 und das Wort mit hoher Ordnung -1 ist, wird der gesamte Text im Bearbeitungssteuerelement ausgewählt. Wenn das Wort niedriger Ordnung -1 ist, wird jede aktuelle Auswahl entfernt.

*bNoScroll*<br/>
Gibt an, ob die Einstellte in die Ansicht gescrollt werden soll. Wenn FALSE, wird die Einstellte in die Ansicht gescrollt. Wenn TRUE, wird die Einstellte nicht in die Ansicht gescrollt.

*nStartChar*<br/>
Gibt die Startposition an. Wenn *nStartChar* 0 und *nEndChar* -1 ist, wird der gesamte Text im Bearbeitungssteuerelement ausgewählt. Wenn *nStartChar* -1 ist, wird jede aktuelle Auswahl entfernt.

*nEndChar*<br/>
Gibt die Endposition an.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EM_SETSEL](/windows/win32/Controls/em-setsel) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CEdit::GetSel](#getsel).

## <a name="ceditsettabstops"></a><a name="settabstops"></a>CEdit::SetTabStops

Rufen Sie diese Funktion auf, um die Tabstopps in einem mehrzeiligen Bearbeitungssteuerelement festzulegen.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parameter

*cxEachStop*<br/>
Gibt an, dass Tabstopps an allen *cxEachStop-Dialogeinheiten* festgelegt werden sollen.

*nTabStops*<br/>
Gibt die Anzahl der Tabstopps an, die in *rgTabStops*enthalten sind. Diese Zahl muss größer als 1 sein.

*rgTabStops*<br/>
Zeigt auf ein Array von nicht signierten Ganzzahlen, die die Tabstopps in Dialogeinheiten angeben. Eine Dialogeinheit ist ein horizontaler oder vertikaler Abstand. Eine horizontale Dialogeinheit entspricht einem Viertel der aktuellen Dialogbasisbreiteneinheit, und eine vertikale Dialogeinheit entspricht einem Achtel der aktuellen Dialogbasishöheneinheit. Die Dialogbasiseinheiten werden basierend auf der Höhe und Breite der aktuellen Systemschriftart berechnet. Die `GetDialogBaseUnits` Windows-Funktion gibt die aktuellen Dialogbasiseinheiten in Pixel zurück.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Registerkarten festgelegt wurden; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Text in ein mehrzeiliges Bearbeitungssteuerelement kopiert wird, führt jedes Registerkartenzeichen im Text dazu, dass bis zum nächsten Tabstopp Speicherplatz generiert wird.

Um Tabstopps auf die Standardgröße von 32 Dialogeinheiten festzulegen, rufen Sie die parameterlose Version dieser Memberfunktion auf. Um Tabstopps auf eine andere Größe als 32 festzulegen, rufen Sie die Version mit dem Parameter *cxEachStop* auf. Um Tabstopps auf ein Array von Größen festzulegen, verwenden Sie die Version mit zwei Parametern.

Diese Memberfunktion wird nur von mehrzeiligen Bearbeitungssteuerelementen verarbeitet.

`SetTabStops`zeichnet das Bearbeitungsfenster nicht automatisch neu. Wenn Sie die Registerkartenstopps für Text ändern, der sich bereits im Bearbeitungssteuerelement befindet, rufen Sie [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) auf, um das Bearbeitungsfenster neu zu zeichnen.

Weitere Informationen finden Sie unter [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) und [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CEditView::SetTabStops](ceditview-class.md#settabstops).

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a>CEdit::ShowBalloonTip

Zeigt eine Sprechblasenspitze an, die dem aktuellen Bearbeitungssteuerelement zugeordnet ist.

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pEditBalloonTip*|[in] Zeiger auf eine [EDITBALLOONTIP-Struktur,](/windows/win32/api/commctrl/ns-commctrl-editballoontip) die die Ballonspitze beschreibt.|
|*lpszTitle*|[in] Zeiger auf eine Unicode-Zeichenfolge, die den Titel der Sprechblasenspitze enthält.|
|*lpszText*|[in] Zeiger auf eine Unicode-Zeichenfolge, die den Text der Sprechblasenspitze enthält.|
|*ttiIcon*|[in] Ein **INT,** das den Symboltyp angibt, der der Sprechblasenspitze zugeordnet werden soll. Der Standardwert ist TTI_NONE. Weitere Informationen finden `ttiIcon` Sie im Member der [EDITBALLOONTIP-Struktur.](/windows/win32/api/commctrl/ns-commctrl-editballoontip)|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sendet die [EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip) Nachricht, die im Windows SDK beschrieben wird. Weitere Informationen finden [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) Sie im Edit_ShowBalloonTip-Makro.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_cedit`eine Variable definiert, , die für den Zugriff auf das aktuelle Bearbeitungssteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird eine Sprechblasenspitze für ein Bearbeitungssteuerelement angezeigt. Die [CEdit::ShowBalloonTip-Methode](#showballoontip) gibt einen Titel- und Sprechblasentipptext an.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a>CEdit::Rückgängig

Rufen Sie diese Funktion auf, um den letzten Bearbeitungssteuerungsvorgang rückgängig zu machen.

```
BOOL Undo();
```

### <a name="return-value"></a>Rückgabewert

Bei einem einzeiligen Bearbeitungssteuerelement ist der Rückgabewert immer ungleich Null. Bei einem mehrzeiligen Bearbeitungssteuerelement ist der Rückgabewert ungleich Null, wenn der Rückgängig-Vorgang erfolgreich ist, oder 0, wenn der Rückgängig-Vorgang fehlschlägt.

### <a name="remarks"></a>Bemerkungen

Ein Rückgängig-Vorgang kann auch rückgängig gemacht werden. Sie können z. B. gelöschten `Undo`Text mit dem ersten Aufruf von wiederherstellen. Solange kein Zwischenvorgang für die Bearbeitung vorhanden ist, können Sie den `Undo`Text mit einem zweiten Aufruf von erneut entfernen.

Weitere Informationen finden Sie unter [EM_UNDO](/windows/win32/Controls/em-undo) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](cwnd-class.md)<br/>
[CButton-Klasse](cbutton-class.md)<br/>
[CComboBox-Klasse](ccombobox-class.md)<br/>
[CListBox-Klasse](clistbox-class.md)<br/>
[CScrollBar-Klasse](cscrollbar-class.md)<br/>
[CStatic-Klasse](cstatic-class.md)<br/>
[CDialog-Klasse](cdialog-class.md)
