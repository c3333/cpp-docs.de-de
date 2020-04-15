---
title: CFindReplaceDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
ms.openlocfilehash: 7a12d0520d070d74afd9fa91e828970d14c82700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373864"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog-Klasse

Ermöglicht das Implementieren von Standardzeichenfolgen-Dialogfeldern Suchen/Ersetzen in Ihrer Anwendung.

## <a name="syntax"></a>Syntax

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Rufen Sie diese `CFindReplaceDialog` Funktion auf, um ein Objekt zu erstellen.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFindReplaceDialog::Erstellen](#create)|Erstellt und `CFindReplaceDialog` zeigt ein Dialogfeld an.|
|[CFindReplaceDialog::FindNext](#findnext)|Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer das nächste Vorkommen der Find-Zeichenfolge finden möchte.|
|[CFindReplaceDialog::GetFindString](#getfindstring)|Rufen Sie diese Funktion auf, um die aktuelle Find-Zeichenfolge abzurufen.|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Rufen Sie diese `FINDREPLACE` Funktion auf, um die Struktur in Ihrem registrierten Nachrichtenhandler abzurufen.|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Rufen Sie diese Funktion auf, um die aktuelle Ersatzzeichenfolge abzurufen.|
|[CFindReplaceDialog::IsTerminating](#isterminating)|Rufen Sie diese Funktion auf, um zu bestimmen, ob das Dialogfeld beendet wird.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer der Groß-/Kleinschreibung der Find-Zeichenfolge genau entsprechen möchte.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer nur ganze Wörter übereinstimmen möchte.|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer alle Vorkommen der Zeichenfolge ersetzen soll.|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer das aktuelle Wort ersetzen soll.|
|[CFindReplaceDialog::SearchDown](#searchdown)|Rufen Sie diese Funktion auf, um zu bestimmen, ob die Suche nach unten verlaufen soll.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Eine Struktur, die `CFindReplaceDialog` zum Anpassen eines Objekts verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Im Gegensatz zu den `CFindReplaceDialog` anderen allgemeinen Windows-Dialogfeldern sind Objekte moduslos, sodass Benutzer mit anderen Fenstern interagieren können, während sie sich auf dem Bildschirm befinden. Es gibt zwei `CFindReplaceDialog` Arten von Objekten: Dialogfelder suchen und Dialogfelder suchen/ersetzen. Obwohl die Dialogfelder es dem Benutzer ermöglichen, Such- und Suchzeichenfolgen einzugeben, führen sie keine der Such- oder Ersetzungsfunktionen aus. Sie müssen diese der Anwendung hinzufügen.

Um ein `CFindReplaceDialog` Objekt zu erstellen, verwenden Sie den bereitgestellten Konstruktor (der keine Argumente enthält). Da es sich um ein modusloses Dialogfeld handelt, weisen Sie das Objekt auf dem Heap mit dem **neuen** Operator und nicht auf dem Stapel zu.

Nachdem `CFindReplaceDialog` ein Objekt erstellt wurde, müssen Sie die Funktion Member [erstellen](#create) aufrufen, um das Dialogfeld zu erstellen und anzuzeigen.

Verwenden Sie die [m_fr](#m_fr) Struktur, um `Create`das Dialogfeld vor dem Aufruf zu initialisieren. Die `m_fr` Struktur ist vom Typ [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Weitere Informationen zu dieser Struktur finden Sie im Windows SDK.

Damit das übergeordnete Fenster über Such-/Ersetzungsanforderungen benachrichtigt wird, müssen Sie die [Windows-RegisterWindowMessage-Funktion](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) verwenden und das [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) Message-Map-Makro in Ihrem Framefenster verwenden, das diese registrierte Nachricht verarbeitet.

Sie können bestimmen, ob der Benutzer beschlossen `IsTerminating` hat, das Dialogfeld mit der Memberfunktion zu beenden.

`CFindReplaceDialog`sich auf das COMMDLG verlässt. DLL-Datei, die mit Windows-Versionen 3.1 und höher ausgeliefert wird.

Um das Dialogfeld anzupassen, leiten `CFindReplaceDialog`Sie eine Klasse von ab, stellen Sie eine benutzerdefinierte Dialogfeldvorlage bereit, und fügen Sie eine Meldungszuordnung hinzu, um die Benachrichtigungen aus den erweiterten Steuerelementen zu verarbeiten. Alle nicht verarbeiteten Nachrichten sollten an die Basisklasse übergeben werden.

Das Anpassen der Hook-Funktion ist nicht erforderlich.

Weitere Informationen zur `CFindReplaceDialog`Verwendung finden Sie unter [Allgemeine Dialogklassen](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdlgs.h

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>CFindReplaceDialog::CFindReplaceDialog

Erstellt ein `CFindReplaceDialog`-Objekt.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Bemerkungen

Da `CFindReplaceDialog` es sich bei dem Objekt um ein modusloses Dialogfeld handelt, müssen Sie es mithilfe des **neuen** Operators auf dem Heap erstellen.

Während der Zerstörung versucht das Framework, dies im Zeiger auf das Dialogfeld zu **löschen.** Wenn Sie das Dialogfeld auf dem Stapel erstellt haben, ist der **Zeiger** nicht vorhanden, und es kann zu einem nicht definierten Verhalten kommen.

Weitere Informationen zur Konstruktion `CFindReplaceDialog` von Objekten finden Sie in der [CFindReplaceDialog-Übersicht.](../../mfc/reference/cfindreplacedialog-class.md) Verwenden Sie die Mitgliedsfunktion [CFindReplaceDialog::Create,](#create) um das Dialogfeld anzuzeigen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a>CFindReplaceDialog::Erstellen

Erstellt und zeigt je nach Wert von `bFindDialogOnly`entweder ein Dialogfeldobjekt suchen oder suchen/Ersetzen an.

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*bFindDialogOnly*<br/>
Legen Sie diesen Parameter auf TRUE fest, um ein Dialogfeld **Suchen** anzuzeigen. Legen Sie false fest, um ein Dialogfeld **Suchen/Ersetzen** anzuzeigen.

*lpszFindWhat*<br/>
Zeigen Sie auf die Standardsuchzeichenfolge, wenn das Dialogfeld angezeigt wird. Wenn NULL, enthält das Dialogfeld keine Standardsuchzeichenfolge.

*lpszReplaceWith*<br/>
Zeigen Sie auf die Standard-Ersatzzeichenfolge, wenn das Dialogfeld angezeigt wird. Wenn NULL, enthält das Dialogfeld keine Standardersatzzeichenfolge.

*dwFlags*<br/>
Ein oder mehrere Flags können Sie verwenden, um die Einstellungen des Dialogfelds anzupassen, kombiniert mit dem bitweisen ODER-Operator. Der Standardwert ist FR_DOWN, was angibt, dass die Suche in eine Abwärtsrichtung fortgesetzt werden soll. Weitere Informationen zu diesen Flags finden Sie in der [FINDREPLACE-Struktur](/windows/win32/api/commdlg/ns-commdlg-findreplacew) im Windows SDK.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete oder Besitzerfenster des Dialogfelds. Dies ist das Fenster, das die spezielle Meldung erhält, die angibt, dass eine Find/Replace-Aktion angefordert wird. Wenn NULL, wird das Hauptfenster der Anwendung verwendet.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dialogfeldobjekt erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Damit das übergeordnete Fenster über Find/Replace-Anforderungen benachrichtigt wird, müssen Sie die Windows [RegisterWindowMessage-Funktion](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) verwenden, deren Rückgabewert eine Nachrichtennummer ist, die für die Instanz der Anwendung eindeutig ist. Das Rahmenfenster sollte über einen Meldungszuordnungseintrag `OnFindReplace` verfügen, der die Rückruffunktion (im folgenden Beispiel) deklariert, die diese registrierte Nachricht verarbeitet. Das folgende Codefragment ist ein Beispiel dafür, wie `CMyRichEditView`Sie dies für eine Framefensterklasse mit dem Namen tun können:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

Innerhalb `OnFindReplace` Ihrer Funktion interpretieren Sie die Absichten des Benutzers mithilfe der Methoden [CFindReplaceDialog::FindNext](#findnext) und [CFindReplaceDialog::IsTerminating](#isterminating) und erstellen den Code für die Such-/Ersetzungsvorgänge.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a>CFindReplaceDialog::FindNext

Rufen Sie diese Funktion über Ihre Rückruffunktion auf, um zu bestimmen, ob der Benutzer das nächste Vorkommen der Suchzeichenfolge finden möchte.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer das nächste Vorkommen der Suchzeichenfolge finden möchte. andernfalls 0.

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>CFindReplaceDialog::GetFindString

Rufen Sie diese Funktion von Ihrer Rückruffunktion auf, um die zu ermittelnde Standardzeichenfolge abzurufen.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Rückgabewert

Die zu findende Standardzeichenfolge.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>CFindReplaceDialog::GetNotifier

Rufen Sie diese Funktion auf, um einen Zeiger auf das aktuelle Dialogfeld Ersetzen suchen abzurufen.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*lParam*<br/>
Der *lparam-Wert,* der an `OnFindReplace` die Memberfunktion des Rahmenfensters übergeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das aktuelle Dialogfeld.

### <a name="remarks"></a>Bemerkungen

Es sollte innerhalb Ihrer Rückruffunktion verwendet werden, um auf das aktuelle `m_fr` Dialogfeld zuzugreifen, seine Memberfunktionen aufzurufen und auf die Struktur zuzugreifen.

### <a name="example"></a>Beispiel

Unter [CFindReplaceDialog::Erstellen](#create) sie ein Beispiel für das Registrieren des OnFindReplace-Handlers zum Empfangen von Benachrichtigungen aus dem Dialogfeld Ersetzen suchen.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString

Rufen Sie diese Funktion auf, um die aktuelle Ersatzzeichenfolge abzurufen.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Rückgabewert

Die Standardzeichenfolge, mit der gefundene Zeichenfolgen ersetzt werden sollen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFindReplaceDialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a>CFindReplaceDialog::IsTerminating

Rufen Sie diese Funktion innerhalb Ihrer Rückruffunktion auf, um zu bestimmen, ob der Benutzer das Dialogfeld beenden möchte.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer das Dialogfeld beenden möchte. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn diese Funktion einen Wert ungleich Null zurückgibt, sollten Sie die `DestroyWindow` Memberfunktion des aktuellen Dialogfelds aufrufen und eine beliebige Dialogfeld-Zeigervariable auf NULL setzen. Optional können Sie auch den zuletzt eingegebenen Such-/Ersetzungstext speichern und ihn verwenden, um das nächste Dialogfeld suchen/ersetzen zu initialisieren.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFindReplaceDialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a>CFindReplaceDialog::m_fr

Wird zum `CFindReplaceDialog` Anpassen eines Objekts verwendet.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Bemerkungen

`m_fr`ist eine Struktur vom Typ [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Seine Member speichern die Eigenschaften des Dialogfeldobjekts. Nach dem `CFindReplaceDialog` Erstellen eines `m_fr` Objekts können Sie verschiedene Werte im Dialogfeld ändern.

Weitere Informationen zu dieser Struktur `FINDREPLACE` finden Sie in der Struktur im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a>CFindReplaceDialog::MatchCase

Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer der Groß-/Kleinschreibung der Find-Zeichenfolge genau entsprechen möchte.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer Vorkommen der Suchzeichenfolge finden möchte, die genau mit der Groß-/Kleinschreibung der Suchzeichenfolge übereinstimmen. andernfalls 0.

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord

Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer nur ganze Wörter übereinstimmen möchte.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer nur die gesamten Wörter der Suchzeichenfolge übereinstimmen möchte. andernfalls 0.

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a>CFindReplaceDialog::ReplaceAll

Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer alle Vorkommen der Zeichenfolge ersetzen soll.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer angefordert hat, dass alle Zeichenfolgen, die der Ersatzzeichenfolge entsprechen, ersetzt werden. andernfalls 0.

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent

Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer das aktuelle Wort ersetzen soll.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer angefordert hat, dass die aktuell ausgewählte Zeichenfolge durch die Ersatzzeichenfolge ersetzt werden soll. andernfalls 0.

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a>CFindReplaceDialog::SearchDown

Rufen Sie diese Funktion auf, um zu bestimmen, ob die Suche nach unten verlaufen soll.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer möchte, dass die Suche in eine Abwärtsrichtung verläuft. 0, wenn der Benutzer möchte, dass die Suche in eine Nachwärtsrichtung geht.

## <a name="see-also"></a>Siehe auch

[CCommonDialog-Klasse](../../mfc/reference/ccommondialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
