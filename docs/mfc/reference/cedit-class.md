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
ms.openlocfilehash: 0e15472ddaad214d575a7479680454ae6b4d3178
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561621"
---
# <a name="cedit-class"></a>CEdit Class

Stellt die Funktionalität eines Windows-Bearbeitungssteuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CEdit : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CEdit:: CEdit](#cedit)|Erstellt ein `CEdit` Steuerelement Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CEdit:: CanUndo](#canundo)|Bestimmt, ob ein Bearbeitungs Steuerungs Vorgang rückgängig gemacht werden kann.|
|[CEdit:: charfrompos](#charfrompos)|Ruft die Zeilen-und Zeichen Indizes für das Zeichen ab, das einer angegebenen Position am nächsten liegt.|
|[CEdit:: Clear](#clear)|Löscht (löscht) die aktuelle Auswahl im Bearbeitungs Steuerelement (sofern vorhanden).|
|[CEdit:: Copy](#copy)|Kopiert die aktuelle Auswahl (sofern vorhanden) im Bearbeitungs Steuerelement in CF_TEXT Format in die Zwischenablage.|
|[CEdit:: Create](#create)|Erstellt das Windows-Bearbeitungs Steuerelement und fügt es an das- `CEdit` Objekt an.|
|[CEdit:: Cut](#cut)|Löscht (wenn vorhanden) die aktuelle Auswahl im Bearbeitungs Steuerelement und kopiert den gelöschten Text in CF_TEXT Format in die Zwischenablage.|
|[CEdit:: emptyundobuffer](#emptyundobuffer)|Setzt das rückgängig-Flag eines Bearbeitungs Steuer Elements zurück (löscht dieses).|
|[CEdit:: smtlines](#fmtlines)|Legt die Einbindung weicher Zeilenumbruch Zeichen in einem mehrzeiligen Bearbeitungs Steuerelement ein bzw. aus.|
|[CEdit:: getcuebanner](#getcuebanner)|Ruft den Text ab, der als Text Hinweis oder Tipp in einem Bearbeitungs Steuerelement angezeigt wird, wenn das Steuerelement leer ist und keinen Fokus hat.|
|[CEdit:: getfirstvisibleline](#getfirstvisibleline)|Bestimmt die oberste sichtbare Zeile in einem Bearbeitungs Steuerelement.|
|[CEdit:: GetHandle](#gethandle)|Ruft ein Handle für den Arbeitsspeicher ab, der derzeit für ein mehrzeilige Bearbeitungs Steuerelement zugeordnet ist.|
|[CEdit:: gethighlight](#gethighlight)|Ruft die Indizes der Anfangs-und Endzeichen in einem Textbereich ab, der im aktuellen Bearbeitungs Steuerelement hervorgehoben ist.|
|[CEdit:: getlimittext](#getlimittext)|Ruft die maximale Menge an Text ab, der in diesem `CEdit` enthalten sein kann.|
|[CEdit:: getline](#getline)|Ruft eine Textzeile aus einem Bearbeitungs Steuerelement ab.|
|[CEdit:: getLineCount](#getlinecount)|Ruft die Anzahl der Zeilen in einem mehrzeiligen Bearbeitungs Steuerelement ab.|
|[CEdit:: getMargin](#getmargins)|Ruft den linken und rechten Rand für dieses ab `CEdit` .|
|[CEdit:: getmodify](#getmodify)|Bestimmt, ob der Inhalt eines Bearbeitungs Steuer Elements geändert wurde.|
|[CEdit:: getpasswordchar](#getpasswordchar)|Ruft das Kenn Wort Zeichen ab, das in einem Bearbeitungs Steuerelement angezeigt wird, wenn der Benutzer Text eingibt.|
|[CEdit:: GetRect](#getrect)|Ruft das Formatierungs Rechteck eines Bearbeitungs Steuer Elements ab.|
|[CEdit:: GetSEL](#getsel)|Ruft die ersten und letzten Zeichen Positionen der aktuellen Auswahl in einem Bearbeitungs Steuerelement ab.|
|[CEdit:: hideballoontip](#hideballoontip)|Blendet jede Sprechblase aus, die dem aktuellen Bearbeitungs Steuerelement zugeordnet ist.|
|[CEdit:: limittext](#limittext)|Schränkt die Länge des Texts ein, den der Benutzer in ein Bearbeitungs Steuerelement eingeben kann.|
|[CEdit:: linefromchar](#linefromchar)|Ruft die Zeilennummer der Zeile ab, die den angegebenen Zeichen Index enthält.|
|[CEdit:: lineingedex](#lineindex)|Ruft den Zeichen Index einer Zeile in einem mehrzeiligen Bearbeitungs Steuerelement ab.|
|[CEdit:: LineLength](#linelength)|Ruft die Länge einer Zeile in einem Bearbeitungs Steuerelement ab.|
|[CEdit:: linescroll](#linescroll)|Scrollt den Text eines mehrzeiligen Bearbeitungs Steuer Elements.|
|[CEdit::P Aste](#paste)|Fügt die Daten aus der Zwischenablage an der aktuellen Cursorposition in das Bearbeitungs Steuerelement ein. Daten werden nur eingefügt, wenn die Zwischenablage Daten in CF_TEXT Format enthält.|
|[CEdit::P osfromchar](#posfromchar)|Ruft die Koordinaten der oberen linken Ecke eines angegebenen Zeichen Indexes ab.|
|[CEdit:: replacesel](#replacesel)|Ersetzt die aktuelle Auswahl in einem Bearbeitungs Steuerelement durch den angegebenen Text.|
|[CEdit:: setcuebanner](#setcuebanner)|Legt den Text fest, der als Text Hinweis oder Tipp in einem Bearbeitungs Steuerelement angezeigt wird, wenn das Steuerelement leer ist und keinen Fokus hat.|
|[CEdit:: lthandle](#sethandle)|Legt das Handle auf den lokalen Arbeitsspeicher fest, der von einem mehrzeiligen Bearbeitungs Steuerelement verwendet wird.|
|[CEdit:: ab.](#sethighlight)|Markiert einen Textbereich, der im aktuellen Bearbeitungs Steuerelement angezeigt wird.|
|[CEdit:: SetLimitText](#setlimittext)|Legt die maximale Menge an Text fest, der in diesem `CEdit` enthalten sein kann.|
|[CEdit:: setMargin](#setmargins)|Legt den linken und rechten Rand für dieses fest `CEdit` .|
|[CEdit:: setmodify](#setmodify)|Legt das Änderungsflag für ein Bearbeitungs Steuerelement fest oder löscht dieses.|
|[CEdit:: setpasswordchar](#setpasswordchar)|Legt ein in einem Bearbeitungs Steuerelement angezeigtes Kennwort fest oder entfernt dieses, wenn der Benutzer Text eingibt.|
|[CEdit:: abtreadonly](#setreadonly)|Legt den schreibgeschützten Zustand eines Bearbeitungs Steuer Elements fest.|
|[CEdit:: SetRect](#setrect)|Legt das Formatierungs Rechteck eines mehrzeiligen Bearbeitungs Steuer Elements fest und aktualisiert das-Steuerelement.|
|[CEdit:: setrectnp](#setrectnp)|Legt das Formatierungs Rechteck eines mehrzeiligen Bearbeitungs Steuer Elements fest, ohne das Steuerelement Fenster neu zu zeichnen.|
|[CEdit:: abtsel](#setsel)|Wählt einen Bereich von Zeichen in einem Bearbeitungs Steuerelement aus.|
|[CEdit:: settabstopps](#settabstops)|Legt die Tabstopps in einem mehrzeiligen Bearbeitungs Steuerelement fest.|
|[CEdit:: ShowBalloonTip](#showballoontip)|Zeigt eine Sprechblasen Info an, die dem aktuellen Bearbeitungs Steuerelement zugeordnet ist.|
|[CEdit:: rückgängig](#undo)|Kehrt den letzten Bearbeitungs Steuerungs Vorgang um.|

## <a name="remarks"></a>Bemerkungen

Ein Bearbeitungs Steuerelement ist ein rechteckiges untergeordnetes Fenster, in dem der Benutzer Text eingeben kann.

Sie können ein Bearbeitungs Steuerelement entweder aus einer Dialogfeld Vorlage oder direkt im Code erstellen. Rufen Sie in beiden Fällen zuerst den-Konstruktor `CEdit` auf, um das-Objekt zu erstellen `CEdit` , und rufen Sie dann die [Create](#create) Member-Funktion auf, um das Windows-Bearbeitungs Steuerelement zu erstellen und es dem- `CEdit` Objekt

Die Konstruktion kann ein einstufiger Prozess in einer von abgeleiteten Klasse sein `CEdit` . Schreiben Sie einen Konstruktor für die abgeleitete Klasse, und geben Sie `Create` im Konstruktor ein.

`CEdit` erbt bedeutende Funktionen von `CWnd` . Um Text von einem-Objekt festzulegen und abzurufen `CEdit` , verwenden `CWnd` Sie die Member-Funktionen [SetWindowText](cwnd-class.md#setwindowtext) und [GetWindowText](cwnd-class.md#getwindowtext), die den gesamten Inhalt eines Bearbeitungs Steuer Elements festlegen oder abrufen, auch wenn es sich um ein mehrzeilige Steuerelement handelt. Text Zeilen in einem mehrzeiligen Steuerelement werden durch "\r\n"-Zeichen folgen getrennt. Wenn ein Bearbeitungs Steuerelement mehrzeilige Werte hat, können Sie den Text des Steuer Elements abrufen und festlegen, indem Sie die `CEdit` Member-Funktionen [getline](#getline), [SetSel](#setsel), [GetSEL](#getsel)und [replacesel](#replacesel)aufrufen.

Wenn Sie Windows-Benachrichtigungs Meldungen verarbeiten möchten, die von einem Bearbeitungs Steuerelement an das übergeordnete Element gesendet werden (normalerweise eine von abgeleitete Klasse `CDialog` ), fügen Sie der übergeordneten Klasse für jede Nachricht einen Meldungs Zuordnungs Eintrag und eine nachrichtenhandlerelementfunktion hinzu.

Jeder Nachrichten Zuordnungs Eintrag hat die folgende Form:

  **ON_**_Benachrichtigung_**(** _ID_**,** _mitgliedungsfxn_ **)**

Where `id` gibt die untergeordnete Fenster-ID des Bearbeitungs Steuer Elements an, das die Benachrichtigung sendet, und `memberFxn` ist der Name der übergeordneten Element Funktion, die Sie zum Verarbeiten der Benachrichtigung geschrieben haben.

Der Prototyp der übergeordneten Funktion ist wie folgt:

**afx_msg** void-mitgliedmitgliedschaft **();**

Im folgenden finden Sie eine Liste potenzieller Nachrichten Zuordnungs Einträge und eine Beschreibung der Fälle, in denen Sie an das übergeordnete Element gesendet werden:

- ON_EN_CHANGE der Benutzer eine Aktion durchgeführt hat, die möglicherweise Text in einem Bearbeitungs Steuerelement geändert hat. Im Gegensatz zur EN_UPDATE Benachrichtigungs Meldung wird diese Benachrichtigungs Meldung gesendet, nachdem Windows die Anzeige aktualisiert hat.

- ON_EN_ERRSPACE das Bearbeitungs Steuerelement kann nicht genügend Arbeitsspeicher zuordnen, um eine bestimmte Anforderung zu erfüllen.

- ON_EN_HSCROLL der Benutzer auf die horizontale Schiebe Leiste eines Bearbeitungs Steuer Elements klickt. Das übergeordnete Fenster wird benachrichtigt, bevor der Bildschirm aktualisiert wird.

- ON_EN_KILLFOCUS das Bearbeitungs Steuerelement den Eingabefokus verliert.

- , ON_EN_MAXTEXT der aktuelle Einfügewert die angegebene Anzahl von Zeichen für das Bearbeitungs Steuerelement überschritten hat und abgeschnitten wurde. Wird auch gesendet, wenn ein Bearbeitungs Steuerelement nicht den ES_AUTOHSCROLL Stil hat und die Anzahl der einzufügenden Zeichen die Breite des Bearbeitungs Steuer Elements überschreiten würde. Wird auch gesendet, wenn ein Bearbeitungs Steuerelement nicht den ES_AUTOVSCROLL Stil hat und die Gesamtanzahl der Zeilen, die sich aus einer Text Einfügung ergeben, die Höhe des Bearbeitungs Steuer Elements überschreiten würde.

- ON_EN_SETFOCUS gesendet, wenn ein Bearbeitungs Steuerelement den Eingabefokus erhält.

- ON_EN_UPDATE das Bearbeitungs Steuerelement im Begriff ist, geänderten Text anzuzeigen. Wird gesendet, nachdem das Steuerelement den Text formatiert hat, aber bevor der Text angezeigt wird, sodass die Fenstergröße geändert werden kann, falls erforderlich.

- ON_EN_VSCROLL der Benutzer auf die vertikale Schiebe Leiste eines Bearbeitungs Steuer Elements klickt. Das übergeordnete Fenster wird benachrichtigt, bevor der Bildschirm aktualisiert wird.

Wenn Sie ein- `CEdit` Objekt in einem Dialogfeld erstellen, `CEdit` wird das Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie `CEdit` über den Dialog-Editor ein-Objekt aus einer Dialogfeld Ressource erstellen, `CEdit` wird das Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie ein- `CEdit` Objekt in einem-Fenster erstellen, müssen Sie es möglicherweise auch zerstören. Wenn Sie das `CEdit` Objekt auf dem Stapel erstellen, wird es automatisch zerstört. Wenn Sie das- `CEdit` Objekt auf dem Heap mithilfe der- **`new`** Funktion erstellen, müssen Sie für das-Objekt aufzurufen, **`delete`** um es zu zerstören, wenn der Benutzer das Windows-Bearbeitungs Steuerelement beendet. Wenn Sie im Objektspeicher zuweisen `CEdit` , überschreiben Sie den `CEdit` Dekonstruktor, um die Zuweisungen zu verwerfen.

Wenn Sie bestimmte Stile in einem Bearbeitungs Steuerelement ändern möchten (z. b. ES_READONLY), müssen Sie bestimmte Nachrichten an das Steuerelement senden, anstatt [modifystyle](cwnd-class.md#modifystyle)zu verwenden. Weitere Informationen finden Sie unter [Edit Control Styles](/windows/win32/Controls/edit-control-styles) in the Windows SDK.

Weitere Informationen zu finden Sie unter Steuer `CEdit` [Elemente](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a> CEdit:: CanUndo

Mit dieser Funktion können Sie ermitteln, ob der letzte Bearbeitungsvorgang rückgängig gemacht werden kann.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der letzte Bearbeitungsvorgang durch einen Rückruf der Member-Funktion rückgängig gemacht werden kann `Undo` ; 0, wenn er nicht rückgängig gemacht werden kann.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EM_CANUNDO](/windows/win32/Controls/em-canundo) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: Undo](#undo).

## <a name="ceditcedit"></a><a name="cedit"></a> CEdit:: CEdit

Erstellt ein `CEdit`-Objekt.

```
CEdit();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [Create](#create) zum Erstellen des Windows-Bearbeitungs Steuer Elements.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a> CEdit:: charfrompos

Mit dieser Funktion können Sie die NULL basierten Zeilen-und Zeichen Indizes des Zeichens abrufen, das dem angegebenen Punkt in diesem Steuerelement am nächsten liegt. `CEdit`

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parameter

*pt*<br/>
Die Koordinaten eines Punkts im Client Bereich des- `CEdit` Objekts.

### <a name="return-value"></a>Rückgabewert

Der Zeichen Index im nieder wertigen Wort und der Zeilen Index im Wort mit hoher Reihenfolge.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Member-Funktion ist ab Windows 95 und Windows NT 4,0 verfügbar.

Weitere Informationen finden Sie unter [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a> CEdit:: Clear

Mit dieser Funktion können Sie die aktuelle Auswahl (sofern vorhanden) im Bearbeitungs Steuerelement löschen (Löschen).

```cpp
void Clear();
```

### <a name="remarks"></a>Bemerkungen

Der von ausgeführte Löschvorgang `Clear` kann [Rück](#undo) gängig gemacht werden, indem die Funktion rückgängigmember aufgerufen wird.

Um die aktuelle Auswahl zu löschen und den gelöschten Inhalt in die Zwischenablage einzufügen, müssen Sie die Funktion zum [Ausschneiden](#cut) von Membern.

Weitere Informationen finden Sie unter [WM_CLEAR](/windows/win32/dataxchg/wm-clear) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a> CEdit:: Copy

Mit dieser Funktion wird die aktuelle Auswahl (sofern vorhanden) im Bearbeitungs Steuerelement in CF_TEXT Format in die Zwischenablage kopiert.

```cpp
void Copy();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [WM_COPY](/windows/win32/dataxchg/wm-copy) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a> CEdit:: Create

Erstellt das Windows-Bearbeitungs Steuerelement und fügt es an das- `CEdit` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Gibt den Stil des Bearbeitungs Steuer Elements an. Wenden Sie eine beliebige Kombination von [Bearbeitungs Stilen](styles-used-by-mfc.md#edit-styles) auf das Steuerelement an.

*Rect*<br/>
Gibt die Größe und Position des Bearbeitungs Steuer Elements an. Kann ein- `CRect` Objekt oder eine- `RECT` Struktur sein.

*pparser*<br/>
Gibt das übergeordnete Fenster des Bearbeitungs Steuer Elements an (normalerweise ein `CDialog` ). Er darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Bearbeitungs Steuer Elements an.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Initialisierung erfolgreich ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen ein- `CEdit` Objekt in zwei Schritten. Zuerst wird der `CEdit` -Konstruktor aufgerufen und dann aufgerufen `Create` , wodurch das Windows-Bearbeitungs Steuerelement erstellt und an das-Objekt angefügt wird `CEdit` .

Wenn `Create` ausgeführt wird, sendet Windows die [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate)-, [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize)-, [WM_CREATE](/windows/win32/winmsg/wm-create)-und [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) Meldungen an das Bearbeitungs Steuerelement.

Diese Nachrichten werden standardmäßig von den Element Funktionen " [onnccreate](cwnd-class.md#onnccreate)", " [onnccalcsize](cwnd-class.md#onnccalcsize)", " [OnCreate](cwnd-class.md#oncreate)" und " [ongetminmaxinfo](cwnd-class.md#ongetminmaxinfo) " in der `CWnd` Basisklasse verarbeitet. Um die standardmäßige Nachrichten Behandlung zu erweitern, leiten Sie eine Klasse von ab `CEdit` , fügen Sie der neuen Klasse eine Meldungs Zuordnung hinzu, und überschreiben Sie die obigen nachrichtenhandlermember-Funktionen. Überschreiben `OnCreate` Sie z. b., um die erforderliche Initialisierung für die neue Klasse auszuführen.

Wenden Sie die folgenden [Fenster Stile](styles-used-by-mfc.md#window-styles) auf ein Bearbeitungs Steuerelement an.

- Immer WS_CHILD

- WS_VISIBLE in der Regel

- WS_DISABLED selten

- WS_GROUP zum Gruppieren von Steuerelementen

- WS_TABSTOP, um das Bearbeitungs Steuerelement in der Tabstopps-Reihenfolge einzubeziehen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a> CEdit:: Cut

Mit dieser Funktion können Sie die aktuelle Auswahl (sofern vorhanden) im Bearbeitungs Steuerelement löschen (Ausschneiden) und den gelöschten Text in CF_TEXT Format in die Zwischenablage kopieren.

```cpp
void Cut();
```

### <a name="remarks"></a>Bemerkungen

Der von ausgeführte Löschvorgang `Cut` kann [Rück](#undo) gängig gemacht werden, indem die Funktion rückgängigmember aufgerufen wird.

Um die aktuelle Auswahl zu löschen, ohne den gelöschten Text in der Zwischenablage zu platzieren, müssen [Sie die Funktion zum Löschen von](#clear) Membern

Weitere Informationen finden Sie unter [WM_CUT](/windows/win32/dataxchg/wm-cut) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a> CEdit:: emptyundobuffer

Mit dieser Funktion wird das rückgängigflag eines Bearbeitungs Steuer Elements zurückgesetzt (gelöscht).

```cpp
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Bemerkungen

Das Bearbeitungs Steuerelement kann jetzt den letzten Vorgang nicht rückgängig machen. Das rückgängigflag wird festgelegt, wenn ein Vorgang innerhalb des Bearbeitungs Steuer Elements rückgängig gemacht werden kann.

Das rückgängigflag wird automatisch gelöscht, wenn die Element Funktionen [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) oder [SetHandle](#sethandle) `CWnd` aufgerufen werden.

Weitere Informationen finden Sie unter [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a> CEdit:: smtlines

Mit dieser Funktion können Sie die Aufnahme von Zeichen in einem mehrzeiligen Bearbeitungs Steuerelement ein-oder ausschalten.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parameter

*baddäol*<br/>
Gibt an, ob weiche Zeilenumbruch Zeichen eingefügt werden sollen. Der Wert true fügt die Zeichen ein. bei einem Wert von false werden diese entfernt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn eine Formatierung auftritt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein weicher Zeilenumbruch besteht aus zwei Wagen Rücklauf Zeichen und einem Zeilenvorschub, der am Ende einer Zeile eingefügt wird, die aufgrund von Wort Umbrüchen unterbrochen wird. Ein harter Zeilenumbruch besteht aus einem Wagen Rücklauf und einem Zeilenvorschub. Zeilen, die mit einem hart zeiligen Umbruch enden, sind von nicht betroffen `FmtLines` .

Windows antwortet nur, wenn `CEdit` es sich bei dem Objekt um ein mehrzeilige Bearbeitungs Steuerelement handelt.

`FmtLines` wirkt sich nur auf den von [GetHandle](#gethandle) zurückgegebenen Puffer und den von [WM_GETTEXT](/windows/win32/winmsg/wm-gettext)zurückgegebenen Text aus. Dies hat keine Auswirkung auf die Anzeige des Texts innerhalb des Bearbeitungs Steuer Elements.

Weitere Informationen finden Sie unter [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a> CEdit:: getcuebanner

Ruft den Text ab, der als Text Hinweis oder Tipp in einem Bearbeitungs Steuerelement angezeigt wird, wenn das Steuerelement leer ist.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
vorgenommen Ein Zeiger auf eine Zeichenfolge, die den Hinweis Text enthält.

*cchText*<br/>
in Die Anzahl der Zeichen, die empfangen werden können. Diese Zahl schließt das abschließende Null-Zeichen ein.

### <a name="return-value"></a>Rückgabewert

Bei der ersten Überladung ist true, wenn die Methode erfolgreich ist. andernfalls false.

Bei der zweiten Überladung eine [CString](../../atl-mfc-shared/using-cstring.md) , die den Hinweis Text enthält, wenn die Methode erfolgreich ist. andernfalls die leere Zeichenfolge ("").

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner) Nachricht, die in der Windows SDK beschrieben wird. Weitere Informationen finden Sie im [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) -Makro.

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a> CEdit:: getfirstvisibleline

Mit dieser Funktion wird die oberste sichtbare Zeile in einem Bearbeitungs Steuerelement bestimmt.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Rückgabewert

Der null basierte Index der obersten sichtbaren Zeile. Für einzeilige Bearbeitungs Steuerelemente ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a> CEdit:: GetHandle

Rufen Sie diese Funktion auf, um ein Handle für den aktuell zugeordneten Arbeitsspeicher für ein mehrzeilige Bearbeitungs Steuerelement abzurufen.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Rückgabewert

Ein lokales Speicher handle, das den Puffer identifiziert, der den Inhalt des Bearbeitungs Steuer Elements enthält. Wenn ein Fehler auftritt, z. b. das Senden der Nachricht an ein einzeilige Bearbeitungs Steuerelement, ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Bei dem Handle handelt es sich um ein lokales Speicher handle, das von allen **lokalen** Windows-Speicherfunktionen verwendet werden kann, die ein lokales Speicher Handle als Parameter annehmen.

`GetHandle` wird nur von mehrzeiligen Bearbeitungs Steuerelementen verarbeitet.

Sie `GetHandle` sollten für ein mehrzeilige Bearbeitungs Steuerelement nur in einem Dialogfeld aufgerufen werden, wenn das Dialogfeld mit dem DS_LOCALEDIT Style-Flag festgelegt wurde. Wenn der DS_LOCALEDIT Stil nicht festgelegt ist, erhalten Sie weiterhin einen Rückgabewert ungleich NULL, aber Sie können den zurückgegebenen Wert nicht verwenden.

> [!NOTE]
> `GetHandle` funktioniert nicht mit Windows 95/98. Wenn Sie `GetHandle` in Windows 95/98 aufzurufen, wird NULL zurückgegeben. `GetHandle` funktioniert wie unter Windows NT, Version 3,51 und höher dokumentiert.

Weitere Informationen finden Sie unter [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a> CEdit:: gethighlight

Ruft die Indizes des ersten und des letzten Zeichens in einem Textbereich ab, der im aktuellen Bearbeitungs Steuerelement hervorgehoben ist.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parameter

*pichstart*\
vorgenommen NULL basierter Index des ersten Zeichens im Textbereich, der hervorgehoben wird.

*pichend*\
vorgenommen NULL basierter Index des letzten Zeichens im Textbereich, der hervorgehoben wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [EM_GETHILITE](/windows/win32/Controls/em-gethilite) Nachricht, die in der Windows SDK beschrieben wird. `SetHighlight`Und `GetHighlight` sind zurzeit nur für Unicode-Builds aktiviert.

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a> CEdit:: getlimittext

Diese Member-Funktion zum Abrufen des Text Limits für dieses `CEdit` Objekt aufzurufen.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Rückgabewert

Das aktuelle Text Limit für dieses Objekt in tchars `CEdit` .

### <a name="remarks"></a>Bemerkungen

Das Text Limit ist die maximale Text Menge in tchars, die das Bearbeitungs Steuerelement annehmen kann.

> [!NOTE]
> Diese Member-Funktion ist ab Windows 95 und Windows NT 4,0 verfügbar.

Weitere Informationen finden Sie unter [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a> CEdit:: getline

Rufen Sie diese Funktion auf, um eine Textzeile aus einem Bearbeitungs Steuerelement abzurufen und in *lpszbuffer*zu stellen.

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
Gibt die Zeilennummer an, die von einem mehrzeiligen Bearbeitungs Steuerelement abgerufen werden soll. Zeilennummern sind NULL basiert. der Wert 0 gibt die erste Zeile an. Dieser Parameter wird von einem einzeiligen Bearbeitungs Steuerelement ignoriert.

*lpszBuffer*<br/>
Verweist auf den Puffer, der eine Kopie der Zeile empfängt. Im ersten Wort des Puffers muss die maximale Anzahl von tchars angegeben werden, die in den Puffer kopiert werden können.

*nMaxLength*<br/>
Gibt die maximale Anzahl von TCHAR-Zeichen an, die in den Puffer kopiert werden können. `GetLine` platziert diesen Wert im ersten Wort von *lpszbuffer* , bevor Windows aufgerufen wird.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der tatsächlich kopierten Zeichen. Der Rückgabewert ist 0, wenn die durch *nIndex* angegebene Zeilennummer größer als die Anzahl der Zeilen im Bearbeitungs Steuerelement ist.

### <a name="remarks"></a>Bemerkungen

Die kopierte Zeile enthält kein NULL-Terminierungs Zeichen.

Weitere Informationen finden Sie unter [EM_GETLINE](/windows/win32/Controls/em-getline) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: getLineCount](#getlinecount).

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a> CEdit:: getLineCount

Rufen Sie diese Funktion auf, um die Anzahl von Zeilen in einem mehrzeiligen Bearbeitungs Steuerelement abzurufen.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die die Anzahl der Zeilen im mehrzeiligen Bearbeitungs Steuerelement enthält. Wenn kein Text in das Bearbeitungs Steuerelement eingegeben wurde, ist der Rückgabewert 1.

### <a name="remarks"></a>Bemerkungen

`GetLineCount` wird nur von mehrzeiligen Bearbeitungs Steuerelementen verarbeitet.

Weitere Informationen finden Sie unter [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a> CEdit:: getMargin

Rufen Sie diese Member-Funktion auf, um die linken und rechten Ränder dieses Bearbeitungs Steuer Elements abzurufen.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite des linken Rands im nieder wertigen Wort und die Breite des rechten Rands im Wort mit hoher Reihenfolge.

### <a name="remarks"></a>Bemerkungen

Ränder werden in Pixel gemessen.

> [!NOTE]
> Diese Member-Funktion ist ab Windows 95 und Windows NT 4,0 verfügbar.

Weitere Informationen finden Sie unter [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEditView:: geteditctrl](ceditview-class.md#geteditctrl).

## <a name="ceditgetmodify"></a><a name="getmodify"></a> CEdit:: getmodify

Mit dieser Funktion können Sie feststellen, ob der Inhalt eines Bearbeitungs Steuer Elements geändert wurde.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Inhalt des Bearbeitungs Steuer Elements geändert wurde. 0 (null), wenn Sie unverändert geblieben sind.

### <a name="remarks"></a>Bemerkungen

Windows behält ein internes Flag bei, das angibt, ob der Inhalt des Bearbeitungs Steuer Elements geändert wurde. Dieses Flag wird gelöscht, wenn das Bearbeitungs Steuerelement erstmalig erstellt wird, und kann auch durch Aufrufen der [setmodify](#setmodify) -Member-Funktion gelöscht werden.

Weitere Informationen finden Sie unter [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a> CEdit:: getpasswordchar

Rufen Sie diese Funktion auf, um das Kenn Wort Zeichen abzurufen, das in einem Bearbeitungs Steuerelement angezeigt wird, wenn der Benutzer Text eingibt.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Zeichen an, das anstelle des vom Benutzer eingegebenen Zeichens angezeigt werden soll. Der Rückgabewert ist NULL, wenn kein Kenn Wort Zeichen vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Bearbeitungs Steuerelement mit dem ES_PASSWORD-Stil erstellen, bestimmt die dll, die das-Steuerelement unterstützt, das Standard Kennwort-Zeichen. Das Manifest oder die [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) -Methode bestimmt, welche DLL das Bearbeitungs Steuerelement unterstützt. Wenn user32.dll das Bearbeitungs Steuerelement unterstützt, ist das Standard Kennwort ein Sternchen ("*", U + 002A). Wenn comctl32.dll Version 6 das Bearbeitungs Steuerelement unterstützt, ist das Standard Zeichen schwarz Kreis ("●", U + 25cf). Weitere Informationen dazu, welche dll und Version die allgemeinen Steuerelemente unterstützt, finden Sie unter [Shell und allgemeine](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))Steuerelement Versionen.

Diese Methode sendet die [EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a> CEdit:: GetRect

Mit dieser Funktion können Sie das Formatierungs Rechteck eines Bearbeitungs Steuer Elements abrufen.

```cpp
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*lprect*<br/>
Verweist auf die- `RECT` Struktur, die das Formatierungs Rechteck empfängt.

### <a name="remarks"></a>Bemerkungen

Das Formatierungs Rechteck ist das einschränkende Rechteck des Texts, der unabhängig von der Größe des Bearbeitungs Steuerelement Fensters ist.

Das Formatierungs Rechteck eines mehrzeiligen Bearbeitungs Steuer Elements kann durch die Member-Funktionen [SetRect](#setrect) und [setrectnp](#setrectnp) geändert werden.

Weitere Informationen finden Sie unter [EM_GETRECT](/windows/win32/Controls/em-getrect) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: limittext](#limittext).

## <a name="ceditgetsel"></a><a name="getsel"></a> CEdit:: GetSEL

Mit dieser Funktion werden die Anfangs-und Endzeichen Positionen der aktuellen Auswahl (sofern vorhanden) in einem Bearbeitungs Steuerelement mithilfe des Rückgabewerts oder der Parameter abgerufen.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Parameter

*nstartchar*<br/>
Verweis auf eine Ganzzahl, die die Position des ersten Zeichens in der aktuellen Auswahl empfängt.

*nendchar*<br/>
Verweis auf eine Ganzzahl, die die Position des ersten nicht ausgewählten Zeichens nach dem Ende der aktuellen Auswahl empfängt.

### <a name="return-value"></a>Rückgabewert

Die Version, die ein DWORD zurückgibt, gibt einen-Wert zurück, der die Anfangsposition im nieder wertigen Wort und die Position des ersten nicht ausgewählten Zeichens nach dem Ende der Auswahl im höherwertigen Wort enthält.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EM_GETSEL](/windows/win32/Controls/em-getsel) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a> CEdit:: hideballoontip

Blendet jede Sprechblase aus, die dem aktuellen Bearbeitungs Steuerelement zugeordnet ist.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sendet die [EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="ceditlimittext"></a><a name="limittext"></a> CEdit:: limittext

Diese Funktion wird aufgerufen, um die Länge des Texts einzuschränken, den der Benutzer in ein Bearbeitungs Steuerelement eingeben darf.

```cpp
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parameter

*nchars*<br/>
Gibt die Länge (in tchars) des Texts an, den der Benutzer eingeben kann. Wenn dieser Parameter 0 ist, wird die Textlänge auf UINT_MAX Bytes festgelegt. Dies ist das Standardverhalten.

### <a name="remarks"></a>Bemerkungen

Durch Ändern des Text Limits wird nur der Text eingeschränkt, den der Benutzer eingeben kann. Sie hat keine Auswirkung auf einen Text, der sich bereits im Bearbeitungs Steuerelement befindet, und wirkt sich nicht auf die Länge des Texts aus, der durch die Member-Funktion von [SetWindowText](cwnd-class.md#setwindowtext) in das Bearbeitungs Steuerelement kopiert wurde `CWnd` . Wenn eine Anwendung die- `SetWindowText` Funktion verwendet, um mehr Text in ein Bearbeitungs Steuerelement zu platzieren, als im-Befehl angegeben ist `LimitText` , kann der Benutzer jeden beliebigen Text innerhalb des Bearbeitungs Steuer Elements löschen. Das Text Limit verhindert jedoch, dass der Benutzer den vorhandenen Text durch neuen Text ersetzt, es sei denn, das Löschen der aktuellen Auswahl bewirkt, dass der Text unterhalb des Text Limits liegt.

> [!NOTE]
> In Win32 (Windows NT und Windows 95/98) ersetzt [SetLimitText](#setlimittext) diese Funktion.

Weitere Informationen finden Sie unter [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a> CEdit:: linefromchar

Rufen Sie diese Funktion auf, um die Zeilennummer der Zeile abzurufen, die den angegebenen Zeichen Index enthält.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Enthält den NULL basierten Indexwert für das gewünschte Zeichen im Text des Bearbeitungs Steuer Elements oder enthält-1. Wenn *nIndex* den Wert-1 aufweist, wird die aktuelle Zeile angegeben, d. h. die Zeile, die die Einfügemarke enthält.

### <a name="return-value"></a>Rückgabewert

Die null basierte Zeilennummer der Zeile, die den durch *nIndex*angegebenen Zeichen Index enthält. Wenn *nIndex* den Wert-1 aufweist, wird die Nummer der Zeile zurückgegeben, die das erste Zeichen der Auswahl enthält. Wenn keine Auswahl vorhanden ist, wird die aktuelle Zeilennummer zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Ein Zeichen Index ist die Anzahl der Zeichen vom Anfang des Bearbeitungs Steuer Elements.

Diese Member-Funktion wird nur von mehrzeiligen Bearbeitungs Steuerelementen verwendet.

Weitere Informationen finden Sie unter [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a> CEdit:: lineingedex

Rufen Sie diese Funktion auf, um den Zeichen Index einer Zeile innerhalb eines mehrzeiligen Bearbeitungs Steuer Elements abzurufen.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parameter

*nzeile*<br/>
Enthält den Indexwert für die gewünschte Zeile im Text des Bearbeitungs Steuer Elements oder enthält-1. Wenn *nline* den Wert-1 aufweist, wird die aktuelle Zeile angegeben, d. h. die Zeile, die die Einfügemarke enthält.

### <a name="return-value"></a>Rückgabewert

Der Zeichen Index der in *nline* angegebenen Zeile oder-1, wenn die angegebene Zeilennummer größer als die Anzahl der Zeilen im Bearbeitungs Steuerelement ist.

### <a name="remarks"></a>Bemerkungen

Der Zeichen Index entspricht der Anzahl von Zeichen vom Anfang des Bearbeitungs Steuer Elements bis zur angegebenen Zeile.

Diese Member-Funktion wird nur von mehrzeiligen Bearbeitungs Steuerelementen verarbeitet.

Weitere Informationen finden Sie unter [EM_LINEINDEX](/windows/win32/controls/em-lineindex) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a> CEdit:: LineLength

Ruft die Länge einer Zeile in einem Bearbeitungs Steuerelement ab.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parameter

*nzeile*<br/>
Der null basierte Index eines Zeichens in der Zeile, deren Länge abgerufen werden soll. Der Standardwert ist -1.

### <a name="return-value"></a>Rückgabewert

Für einzeilige Bearbeitungs Steuerelemente ist der Rückgabewert die Länge des Texts im Bearbeitungs Steuerelement in tchars.

Für mehrzeilige Bearbeitungs Steuerelemente ist der Rückgabewert die Länge in tchars der durch den *nline* -Parameter angegebenen Zeile. Bei ANSI-Text entspricht die Länge der Anzahl der Bytes in der Zeile. bei Unicode-Text entspricht die Länge der Anzahl der Zeichen in der Zeile. Die Länge schließt das Wagen Rücklauf Zeichen am Ende der Zeile nicht ein.

Wenn der *nline* -Parameter größer als die Anzahl der Zeichen im-Steuerelement ist, ist der Rückgabewert 0 (null).

Wenn der *nline* -Parameter-1 ist, ist der Rückgabewert die Anzahl der nicht ausgewählten Zeichen in den Zeilen, die die ausgewählten Zeichen enthalten. Wenn die Auswahl z. b. vom vierten Zeichen einer Zeile bis zum achten Zeichen vom Ende der nächsten Zeile reicht, ist der Rückgabewert 10. Das heißt, drei Zeichen in der ersten Zeile und sieben für das nächste.

Weitere Informationen zum TCHAR-Typ finden Sie in der TCHAR-Zeile in der-Tabelle unter [Windows-Datentypen](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von der [EM_LINELENGTH](/windows/win32/Controls/em-linelength) Meldung unterstützt, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: lineingedex](#lineindex).

## <a name="ceditlinescroll"></a><a name="linescroll"></a> CEdit:: linescroll

Mit dieser Funktion können Sie im Text eines mehrzeiligen Bearbeitungs Steuer Elements einen Bildlauf durchführen.

```cpp
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parameter

*nlines*<br/>
Gibt die Anzahl der Zeilen an, die vertikal scrollen soll.

*nchars*<br/>
Gibt die Anzahl der Zeichen Positionen an, die horizontal durchlaufen werden sollen. Dieser Wert wird ignoriert, wenn das Bearbeitungs Steuerelement entweder den ES_RIGHT oder ES_CENTER Stil hat.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird nur von mehrzeiligen Bearbeitungs Steuerelementen verarbeitet.

Das Bearbeitungs Steuerelement scrollt nicht vertikal nach der letzten Textzeile im Bearbeitungs Steuerelement. Wenn die aktuelle Zeile zuzüglich der Anzahl der durch *nlines* angegebenen Zeilen die Gesamtzahl der Zeilen im Bearbeitungs Steuerelement überschreitet, wird der Wert so angepasst, dass die letzte Zeile des Bearbeitungs Steuer Elements auf den oberen Rand des Fensters zum Bearbeiten von Steuerelementen aufgeschlult wird.

`LineScroll` kann verwendet werden, um horizontal nach dem letzten Zeichen einer beliebigen Zeile zu scrollen.

Weitere Informationen finden Sie unter [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: getfirstvisibleline](#getfirstvisibleline).

## <a name="ceditpaste"></a><a name="paste"></a> CEdit::P Aste

Mit dieser Funktion können Sie die Daten aus der Zwischenablage `CEdit` an der Einfügemarke in die einfügen.

```cpp
void Paste();
```

### <a name="remarks"></a>Bemerkungen

Daten werden nur eingefügt, wenn die Zwischenablage Daten in CF_TEXT Format enthält.

Weitere Informationen finden Sie unter [WM_PASTE](/windows/win32/dataxchg/wm-paste) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a> CEdit::P osfromchar

Mit dieser Funktion wird die Position (obere linke Ecke) eines angegebenen Zeichens innerhalb dieses `CEdit` Objekts abzurufen.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parameter

*NCHAR*<br/>
Der null basierte Index des angegebenen Zeichens.

### <a name="return-value"></a>Rückgabewert

Die Koordinaten der linken oberen Ecke des durch *NCHAR*angegebenen Zeichens.

### <a name="remarks"></a>Bemerkungen

Das Zeichen wird angegeben, indem der null basierte Indexwert angegeben wird. Wenn *NCHAR* größer ist als der Index des letzten Zeichens in diesem- `CEdit` Objekt, gibt der Rückgabewert die Koordinaten der Zeichenposition direkt hinter dem letzten Zeichen in diesem- `CEdit` Objekt an.

> [!NOTE]
> Diese Member-Funktion ist ab Windows 95 und Windows NT 4,0 verfügbar.

Weitere Informationen finden Sie unter [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: linefromchar](#linefromchar).

## <a name="ceditreplacesel"></a><a name="replacesel"></a> CEdit:: replacesel

Mit dieser Funktion wird die aktuelle Auswahl in einem Bearbeitungs Steuerelement durch den von *lpsznewtext*angegebenen Text ersetzt.

```cpp
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parameter

*lpsznewtext*<br/>
Verweist auf eine mit NULL endenden Zeichenfolge, die den Ersetzungstext enthält.

*bcanundo*<br/>
Um anzugeben, dass diese Funktion rückgängig gemacht werden kann, legen Sie den Wert dieses Parameters auf true fest. Der Standardwert ist FALSE.

### <a name="remarks"></a>Bemerkungen

Ersetzt nur einen Teil des Texts in einem Bearbeitungs Steuerelement. Wenn Sie den gesamten Text ersetzen möchten, verwenden Sie die [CWnd:: SetWindowText](cwnd-class.md#setwindowtext) -Member-Funktion.

Wenn keine aktuelle Auswahl vorhanden ist, wird der Ersetzungstext an der aktuellen Cursorposition eingefügt.

Weitere Informationen finden Sie unter [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: lineingedex](#lineindex).

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a> CEdit:: setcuebanner

Legt den Text fest, der als Text Hinweis oder Tipp in einem Bearbeitungs Steuerelement angezeigt wird, wenn das Steuerelement leer ist.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
in Ein Zeiger auf eine Zeichenfolge, die den Hinweis enthält, der im Bearbeitungs Steuerelement angezeigt werden soll.

*mit "f"-Fokus*<br/>
in Wenn der Wert false ist, wird das Hinweis Banner nicht gezeichnet, wenn der Benutzer in das Bearbeitungs Steuerelement klickt und dem Steuerelement den Fokus übergibt.

TRUE gibt an, dass das Hinweis Banner auch dann gezeichnet wird, wenn das Steuerelement den Fokus besitzt. Das Hinweis Banner verschwindet, wenn der Benutzer mit dem Eingeben des Steuer Elements beginnt.

Der Standardwert ist FALSE.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner) Nachricht, die in der Windows SDK beschrieben wird. Weitere Informationen finden Sie im [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) -Makro.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CEdit:: setcuebanner](#setcuebanner) -Methode veranschaulicht.

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a> CEdit:: lthandle

Mit dieser Funktion wird das Handle auf den lokalen Arbeitsspeicher festgelegt, der von einem mehrzeiligen Bearbeitungs Steuerelement verwendet wird.

```cpp
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parameter

*hbuffer*<br/>
Enthält ein Handle für den lokalen Arbeitsspeicher. Dieses Handle muss von einem vorherigen-Befehl der Windows-Funktion [localzuc](/windows/win32/api/winbase/nf-winbase-localalloc) mit dem LMEM_MOVEABLE-Flag erstellt worden sein. Es wird davon ausgegangen, dass der Arbeitsspeicher eine auf NULL endenden Zeichenfolge enthält. Wenn dies nicht der Fall ist, sollte das erste Byte des zugeordneten Speichers auf 0 festgelegt werden.

### <a name="remarks"></a>Bemerkungen

Das Bearbeitungs Steuerelement verwendet diesen Puffer dann, um den aktuell angezeigten Text zu speichern, anstatt seinen eigenen Puffer zuzuweisen.

Diese Member-Funktion wird nur von mehrzeiligen Bearbeitungs Steuerelementen verarbeitet.

Bevor eine Anwendung ein neues Speicher handle festlegt, sollte Sie die [GetHandle](#gethandle) -Member-Funktion verwenden, um das Handle für den aktuellen Speicherpuffer zu erhalten und diesen Speicher mithilfe der Windows-Funktion freizugeben `LocalFree` .

`SetHandle` Löscht den Rückgängig-Puffer (die [kanundo](#canundo) -Member-Funktion gibt dann 0 zurück) und das interne modifizierungsflag (die [getmodify](#getmodify) -Member-Funktion gibt dann 0 zurück). Das Fenster "Bearbeitungs Steuerelement" wird neu gezeichnet.

Sie können diese Element Funktion in einem mehrzeiligen Bearbeitungs Steuerelement nur in einem Dialogfeld verwenden, wenn Sie das Dialogfeld mit dem DS_LOCALEDIT stilflag festgelegt haben.

> [!NOTE]
> `GetHandle` funktioniert nicht mit Windows 95/98. Wenn Sie `GetHandle` in Windows 95/98 aufzurufen, wird NULL zurückgegeben. `GetHandle` funktioniert wie unter Windows NT, Version 3,51 und höher dokumentiert.

Weitere Informationen finden Sie unter [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [localzugewiesenen](/windows/win32/api/winbase/nf-winbase-localalloc)und [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a> CEdit:: ab.

Markiert einen Textbereich, der im aktuellen Bearbeitungs Steuerelement angezeigt wird.

```cpp
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parameter

*ichstart*\
in NULL basierter Index des ersten Zeichens im Textbereich, der hervorgehoben werden soll.

*ichend*\
in Der null basierte Index des letzten Zeichens im Textbereich, der hervorgehoben werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [EM_SETHILITE](/windows/win32/Controls/em-sethilite) Nachricht, die in der Windows SDK beschrieben wird.  Diese Methode sendet die [EM_SETHILITE](/windows/win32/Controls/em-sethilite) Nachricht, die in der Windows SDK beschrieben wird. Sowohl `SetHighlight` als auch `GetHighlight` sind nur für Unicode-Builds aktiviert.

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a> CEdit:: SetLimitText

Diese Member-Funktion zum Festlegen des Text Limits für dieses `CEdit` Objekt aufzurufen.

```cpp
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parameter

*nMax*<br/>
Das neue Text Limit in Zeichen.

### <a name="remarks"></a>Bemerkungen

Das Text Limit ist die maximale Text Menge in Zeichen, die das Bearbeitungs Steuerelement annehmen kann.

Durch Ändern des Text Limits wird nur der Text eingeschränkt, den der Benutzer eingeben kann. Sie hat keine Auswirkung auf einen Text, der sich bereits im Bearbeitungs Steuerelement befindet, und wirkt sich nicht auf die Länge des Texts aus, der durch die Member-Funktion von [SetWindowText](cwnd-class.md#setwindowtext) in das Bearbeitungs Steuerelement kopiert wurde `CWnd` . Wenn eine Anwendung die- `SetWindowText` Funktion verwendet, um mehr Text in ein Bearbeitungs Steuerelement zu platzieren, als im-Befehl angegeben ist `LimitText` , kann der Benutzer jeden beliebigen Text innerhalb des Bearbeitungs Steuer Elements löschen. Das Text Limit verhindert jedoch, dass der Benutzer den vorhandenen Text durch neuen Text ersetzt, es sei denn, das Löschen der aktuellen Auswahl bewirkt, dass der Text unterhalb des Text Limits liegt.

Diese Funktion ersetzt [limittext](#limittext) in Win32.

Weitere Informationen finden Sie unter [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEditView:: geteditctrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmargins"></a><a name="setmargins"></a> CEdit:: setMargin

Ruft diese Methode auf, um den linken und rechten Rand dieses Bearbeitungs Steuer Elements festzulegen.

```cpp
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parameter

*nleft*<br/>
Die Breite des neuen linken Rands in Pixel.

*nright*<br/>
Die Breite des neuen rechten Rands in Pixel.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Member-Funktion ist ab Windows 95 und Windows NT 4,0 verfügbar.

Weitere Informationen finden Sie unter [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEditView:: geteditctrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmodify"></a><a name="setmodify"></a> CEdit:: setmodify

Mit dieser Funktion können Sie das geänderte Flag für ein Bearbeitungs Steuerelement festlegen oder löschen.

```cpp
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parameter

*bmodified*<br/>
Der Wert true gibt an, dass der Text geändert wurde, und der Wert false gibt an, dass er unverändert ist. Standardmäßig ist das geänderte Flag festgelegt.

### <a name="remarks"></a>Bemerkungen

Das geänderte Flag gibt an, ob der Text im Bearbeitungs Steuerelement geändert wurde. Sie wird automatisch festgelegt, wenn der Benutzer den Text ändert. Der Wert kann mit der [getmodify](#getmodify) -Member-Funktion abgerufen werden.

Weitere Informationen finden Sie unter [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: getmodify](#getmodify).

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a> CEdit:: setpasswordchar

Mit dieser Funktion können Sie ein Kenn Wort Zeichen festlegen oder entfernen, das in einem Bearbeitungs Steuerelement angezeigt wird, wenn der Benutzer Text eingibt.

```cpp
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parameter

*ch*<br/>
Gibt das Zeichen an, das anstelle des vom Benutzer eingegebenen Zeichens angezeigt werden soll. Wenn *ch* den Wert 0 hat, werden die tatsächlich vom Benutzer eingegebenen Zeichen angezeigt.

### <a name="remarks"></a>Bemerkungen

Wenn ein Kenn Wort Zeichen festgelegt ist, wird dieses Zeichen für jedes Zeichen angezeigt, das der Benutzer eingibt.

Diese Member-Funktion hat keine Auswirkung auf ein mehrzeilige Bearbeitungs Steuerelement.

Wenn die `SetPasswordChar` Member-Funktion aufgerufen wird, `CEdit` zeichnet alle sichtbaren Zeichen mithilfe des von *ch*angegebenen Zeichens neu.

Wenn das Bearbeitungs Steuerelement mit dem [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) -Format erstellt wird, wird das standardmäßige Kenn Wort Zeichen auf ein Sternchen () festgelegt <strong>\*</strong> . Dieser Stil wird entfernt `SetPasswordChar` , wenn aufgerufen wird, wobei *ch* auf 0 festgelegt ist.

Weitere Informationen finden Sie unter [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a> CEdit:: abtreadonly

Ruft diese Funktion auf, um den schreibgeschützten Zustand eines Bearbeitungs Steuer Elements festzulegen.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parameter

*nur Bread*<br/>
Gibt an, ob der schreibgeschützte Zustand des Bearbeitungs Steuer Elements festgelegt oder entfernt werden soll. Mit dem Wert true wird der Zustand auf schreibgeschützt festgelegt. der Wert false legt den Zustand auf Lese-/Schreibzugriff fest.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Vorgang erfolgreich ist, oder 0, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Die aktuelle Einstellung kann gefunden werden, indem Sie das [ES_READONLY](styles-used-by-mfc.md#edit-styles) -Flag im Rückgabewert von [CWnd:: GetStyle](cwnd-class.md#getstyle)testen.

Weitere Informationen finden Sie unter [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a> CEdit:: SetRect

Mit dieser Funktion werden die Dimensionen eines Rechtecks mithilfe der angegebenen Koordinaten festgelegt.

```cpp
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*lprect*<br/>
Verweist auf die- `RECT` Struktur oder das- `CRect` Objekt, das die neuen Dimensionen des Formatierungs Rechtecks angibt.

### <a name="remarks"></a>Bemerkungen

Dieser Member wird nur von mehrzeiligen Bearbeitungs Steuerelementen verarbeitet.

Verwenden `SetRect` Sie, um das Formatierungs Rechteck eines mehrzeiligen Bearbeitungs Steuer Elements festzulegen. Das Formatierungs Rechteck ist das einschränkende Rechteck des Texts, der unabhängig von der Größe des Bearbeitungs Steuerelement Fensters ist. Wenn das Bearbeitungs Steuerelement erstmalig erstellt wird, entspricht das Formatierungs Rechteck dem Client Bereich des Bearbeitungs Steuer Elements. Mithilfe der `SetRect` Member-Funktion kann eine Anwendung das Formatierungs Rechteck vergrößern oder verkleinern als das Bearbeitungs Steuerelement-Fenster.

Wenn das Bearbeitungs Steuerelement keine Scrollleiste hat, wird der Text abgeschnitten und nicht umschließt, wenn das Formatierungs Rechteck größer als das Fenster ist. Wenn das Bearbeitungs Steuerelement einen Rahmen enthält, wird das Formatierungs Rechteck um die Größe des Rahmens reduziert. Wenn Sie das von der Member-Funktion zurückgegebene Rechteck anpassen `GetRect` , müssen Sie die Größe des Rahmens entfernen, bevor Sie das Rechteck an übergeben `SetRect` .

Wenn `SetRect` aufgerufen wird, wird der Text des Bearbeitungs Steuer Elements ebenfalls neu formatiert und angezeigt.

Weitere Informationen finden Sie unter [EM_SETRECT](/windows/win32/Controls/em-setrect) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a> CEdit:: setrectnp

Mit dieser Funktion wird das Formatierungs Rechteck eines mehrzeiligen Bearbeitungs Steuer Elements festgelegt.

```cpp
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*lprect*<br/>
Verweist auf eine `RECT` Struktur oder ein `CRect` Objekt, das die neuen Abmessungen des Rechtecks angibt.

### <a name="remarks"></a>Bemerkungen

Das Formatierungs Rechteck ist das einschränkende Rechteck des Texts, der unabhängig von der Größe des Bearbeitungs Steuerelement Fensters ist.

`SetRectNP` ist mit der `SetRect` Member-Funktion identisch, außer dass das Bearbeitungs Steuerelement-Fenster nicht neu gezeichnet wird.

Wenn das Bearbeitungs Steuerelement erstmalig erstellt wird, entspricht das Formatierungs Rechteck dem Client Bereich des Bearbeitungs Steuer Elements. Durch Aufrufen der `SetRectNP` Member-Funktion kann eine Anwendung das Formatierungs Rechteck vergrößern oder verkleinern als das Bearbeitungs Steuerelement-Fenster.

Wenn das Bearbeitungs Steuerelement keine Scrollleiste hat, wird der Text abgeschnitten und nicht umschließt, wenn das Formatierungs Rechteck größer als das Fenster ist.

Dieser Member wird nur von mehrzeiligen Bearbeitungs Steuerelementen verarbeitet.

Weitere Informationen finden Sie unter [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: SetRect](#setrect).

## <a name="ceditsetsel"></a><a name="setsel"></a> CEdit:: abtsel

Mit dieser Funktion können Sie einen Bereich von Zeichen in einem Bearbeitungs Steuerelement auswählen.

```cpp
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>Parameter

*dwselection*<br/>
Gibt die Anfangsposition im nieder wertigen Wort und die Endposition im höherwertigen Wort an. Wenn das nieder wertige Wort 0 und das hochwertige Wort-1 ist, wird der gesamte Text im Bearbeitungs Steuerelement ausgewählt. Wenn das nieder wertige Wort-1 ist, wird die aktuelle Auswahl entfernt.

*bnoscroll*<br/>
Gibt an, ob die Einfügemarke in die Ansicht gescrollt werden soll. Wenn false, wird die Einfügemarke in die Ansicht gescrollt. TRUE gibt an, dass die Einfügemarke nicht in die Ansicht gescrollt wird.

*nstartchar*<br/>
Gibt die Anfangsposition an. Wenn *nstartchar* den Wert 0 hat und *nendchar* den Wert-1 hat, wird der gesamte Text im Bearbeitungs Steuerelement ausgewählt. Wenn *nstartchar* den Wert-1 hat, wird die aktuelle Auswahl entfernt.

*nendchar*<br/>
Gibt die Endposition an.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EM_SETSEL](/windows/win32/Controls/em-setsel) in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CEdit:: GetSEL](#getsel).

## <a name="ceditsettabstops"></a><a name="settabstops"></a> CEdit:: settabstopps

Mit dieser Funktion können Sie die Tabstopps in einem mehrzeiligen Bearbeitungs Steuerelement festlegen.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parameter

*cxeachstopps*<br/>
Gibt an, dass Tabstopps für jede *cxeachstopp* -Dialog Einheit festgelegt werden sollen.

*ntabstopps*<br/>
Gibt die Anzahl der in *rgtabstopps*enthaltenen Tabstopps an. Diese Zahl muss größer als 1 sein.

*rgtabstopps*<br/>
Verweist auf ein Array von ganzen Zahlen ohne Vorzeichen, das die Tabstopps in Dialogfeld Einheiten angibt. Eine Dialog Einheit ist ein horizontaler oder vertikaler Abstand. Eine horizontale Dialog Einheit ist gleich 1-vierte der aktuellen Dialogfeld Basis-breiten Einheit, und eine vertikale Dialog Einheit ist gleich einem Achtel der aktuellen Dialogfeld-Basis Höheneinheit. Die Dialog Basiseinheiten werden basierend auf der Höhe und der Breite der aktuellen System Schriftart berechnet. Die `GetDialogBaseUnits` Windows-Funktion gibt die aktuellen Dialog Basiseinheiten des Dialog Felds in Pixel zurück.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Registerkarten festgelegt wurden. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Text in ein Bearbeitungs Steuerelement mit mehreren Zeilen kopiert wird, bewirkt jedes Tabulator Zeichen im Text, bis der nächste Tabstopp Bereich angezeigt wird.

Um Tabstopps auf die Standardgröße von 32-Dialog Einheiten festzulegen, nennen Sie die Parameter lose Version dieser Member-Funktion. Um Tabstopps auf eine andere Größe als 32 festzulegen, müssen Sie die Version mit dem *cxeachstopp* -Parameter aufrufen. Um Tabstopps auf ein Array von Größen festzulegen, verwenden Sie die Version mit zwei Parametern.

Diese Member-Funktion wird nur von mehrzeiligen Bearbeitungs Steuerelementen verarbeitet.

`SetTabStops` das Bearbeitungsfenster wird nicht automatisch neu gezeichnet. Wenn Sie die Tabstopps für Text, der sich bereits im Bearbeitungs Steuerelement befindet, ändern, müssen Sie [CWnd:: invalidaterierup](cwnd-class.md#invalidaterect) aufrufen, um das Bearbeitungsfenster neu zu zeichnen

Weitere Informationen finden Sie unter [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) und [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) im Windows SDK.

### <a name="example"></a>Beispiel

  Sehen Sie sich das Beispiel für [CEditView:: settabstopps](ceditview-class.md#settabstops)an.

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a> CEdit:: ShowBalloonTip

Zeigt eine Sprechblasen Info an, die dem aktuellen Bearbeitungs Steuerelement zugeordnet ist.

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>Parameter

*peditballoontip*\
in Zeiger auf eine [editballoontip](/windows/win32/api/commctrl/ns-commctrl-editballoontip) -Struktur, die die Sprechblasen Info beschreibt.

*lpsztitle*\
in Ein Zeiger auf eine Unicode-Zeichenfolge, die den Titel der Sprechblasen info enthält.

*lpszText*\
in Ein Zeiger auf eine Unicode-Zeichenfolge, die den Text der Sprechblasen info enthält.

*ttiicon*\
in Ein **int** -Wert, der den Typ des Symbols angibt, das der Sprechblasen Info zugeordnet werden soll. Der Standardwert ist TTI_NONE. Weitere Informationen finden Sie unter dem- `ttiIcon` Member der [editballoontip](/windows/win32/api/commctrl/ns-commctrl-editballoontip) -Struktur.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sendet die [EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip) Nachricht, die in der Windows SDK beschrieben wird. Weitere Informationen finden Sie im [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) -Makro.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_cedit` für den Zugriff auf das aktuelle Bearbeitungs Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt eine Sprechblasen Info für ein Bearbeitungs Steuerelement. Die [CEdit:: ShowBalloonTip](#showballoontip) -Methode gibt einen Titel und einen Sprechblasen Text an.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a> CEdit:: rückgängig

Rufen Sie diese Funktion auf, um den letzten Bearbeitungs Steuerungs Vorgang rückgängig zu machen.

```
BOOL Undo();
```

### <a name="return-value"></a>Rückgabewert

Bei einem einzeiligen Bearbeitungs Steuerelement ist der Rückgabewert immer ungleich 0 (null). Bei einem mehrzeiligen Bearbeitungs Steuerelement ist der Rückgabewert ungleich 0 (null), wenn der Rückgängig-Vorgang erfolgreich ist, oder 0, wenn der Rückgängig-Vorgang fehlschlägt.

### <a name="remarks"></a>Bemerkungen

Ein Rückgängig-Vorgang kann auch rückgängig gemacht werden. Beispielsweise können Sie gelöschten Text mit dem ersten-Befehl Wiederherstellen `Undo` . Solange es keinen dazwischen liegenden Bearbeitungsvorgang gibt, können Sie den Text mit einem zweiten-Befehl erneut entfernen `Undo` .

Weitere Informationen finden Sie unter [EM_UNDO](/windows/win32/Controls/em-undo) in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel für CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](cwnd-class.md)<br/>
[CButton-Klasse](cbutton-class.md)<br/>
[CComboBox-Klasse](ccombobox-class.md)<br/>
[CListBox-Klasse](clistbox-class.md)<br/>
[Cscrollbar-Klasse](cscrollbar-class.md)<br/>
[Cstatic-Klasse](cstatic-class.md)<br/>
[CDialog-Klasse](cdialog-class.md)
