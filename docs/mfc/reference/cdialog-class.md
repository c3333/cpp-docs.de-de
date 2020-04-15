---
title: CDialog-Klasse
ms.date: 09/07/2019
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
ms.openlocfilehash: cad762f426012d9d1931b96d54d8a53c9bab465d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375647"
---
# <a name="cdialog-class"></a>CDialog-Klasse

Die Basisklasse, die zum Anzeigen von Dialogfeldern auf dem Bildschirm verwendet wird.

## <a name="syntax"></a>Syntax

```
class CDialog : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|Erstellt ein `CDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDialog::Erstellen](#create)|Initialisiert das `CDialog`-Objekt. Erstellt ein modusloses Dialogfeld und `CDialog` fügt es an das Objekt an.|
|[CDialog::CreateIndirect](#createindirect)|Erstellt ein modusloses Dialogfeld aus einer Dialogfeldvorlage im Speicher (nicht ressourcenbasiert).|
|[CDialog::DoModal](#domodal)|Ruft ein modales Dialogfeld auf und gibt zurück, wenn dies erledigt ist.|
|[CDialog::EndDialog](#enddialog)|Schließt ein modales Dialogfeld.|
|[CDialog::GetDefID](#getdefid)|Ruft die ID des Standard-Tastensteuerelements für ein Dialogfeld ab.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Verschiebt den Fokus auf ein angegebenes Dialogfeldsteuerelement im Dialogfeld.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Erstellt ein modales Dialogfeld aus einer Dialogfeldvorlage im Arbeitsspeicher (nicht ressourcenbasiert). Die Parameter werden gespeichert, bis die Funktion `DoModal` aufgerufen wird.|
|[CDialog::MapDialogRect](#mapdialogrect)|Konvertiert die Dialogfeldeinheiten eines Rechtecks in Bildschirmeinheiten.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Verschiebt den Fokus auf das nächste Dialogfeldsteuerelement im Dialogfeld.|
|[CDialog::OnInitDialog](#oninitdialog)|Überschreiben, um die Dialogfeldinitialisierung zu erweitern.|
|[CDialog::OnSetFont](#onsetfont)|Überschreiben Sie, um die Schriftart anzugeben, die ein Dialogfeldsteuerelement beim Gezeichnet von Text verwenden soll.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Verschiebt den Fokus auf das vorherige Dialogfeldsteuerelement im Dialogfeld.|
|[CDialog::SetDefID](#setdefid)|Ändert das Standard-Tastensteuerelement für ein Dialogfeld in eine angegebene Taste.|
|[CDialog::SetHelpID](#sethelpid)|Legt eine kontextsensitive Hilfe-ID für das Dialogfeld fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Überschreiben, um die Schaltfläche Abbrechen oder esC-Schlüsselaktion auszuführen. Die Standardeinstellung schließt das `DoModal` Dialogfeld und gibt IDCANCEL zurück.|
|[CDialog::OnOK](#onok)|Überschreiben Sie, um die OK-Schaltflächenaktion in einem modalen Dialogfeld auszuführen. Die Standardeinstellung schließt das `DoModal` Dialogfeld und gibt IDOK zurück.|

## <a name="remarks"></a>Bemerkungen

Dialogfelder sind von zwei Typen: modal und moduslos. Ein modales Dialogfeld muss vom Benutzer geschlossen werden, bevor die Anwendung fortgesetzt wird. Ein modusloses Dialogfeld ermöglicht es dem Benutzer, das Dialogfeld anzuzeigen und zu einer anderen Aufgabe zurückzukehren, ohne das Dialogfeld abzubrechen oder zu entfernen.

Ein `CDialog` Objekt ist eine Kombination aus `CDialog`einer Dialogvorlage und einer -derived-Klasse. Verwenden Sie den Dialog-Editor, um die Dialogvorlage zu erstellen und in einer `CDialog`Ressource zu speichern, und verwenden Sie dann den Assistenten zum Hinzufügen von Klassen, um eine von abgeleitete Klasse zu erstellen.

Ein Dialogfeld empfängt wie jedes andere Fenster Nachrichten von Windows. In einem Dialogfeld sind Sie besonders an der Behandlung von Benachrichtigungen aus den Steuerelementen des Dialogfelds interessiert, da der Benutzer so mit dem Dialogfeld interagiert. Verwenden Sie den [Klassen-Assistenten,](mfc-class-wizard.md) um auszuwählen, welche Nachrichten Sie behandeln möchten, und fügen Sie der Klasse die entsprechenden Nachrichtenzuordnungseinträge und Message-Handler-Memberfunktionen hinzu. Sie müssen nur anwendungsspezifischen Code in die Handlermemberfunktionen schreiben.

Wenn Sie möchten, können Sie Nachrichtenmapeinträge und Memberfunktionen immer manuell schreiben.

In allen bis auf das trivialste Dialogfeld fügen Sie der abgeleiteten Dialogklasse Membervariablen hinzu, um daten zu speichern, die vom Benutzer in die Steuerelemente des Dialogfelds eingegeben wurden, oder um Daten für den Benutzer anzuzeigen. Sie können den Assistenten zum Hinzufügen von Variablen verwenden, um Membervariablen zu erstellen und sie Steuerelementen zuzuordnen. Gleichzeitig wählen Sie einen Variablentyp und einen zulässigen Wertebereich für jede Variable aus. Der Code-Assistent fügt die Membervariablen der abgeleiteten Dialogklasse hinzu.

Eine Datenzuordnung wird generiert, um den Datenaustausch zwischen den Membervariablen und den Steuerelementen des Dialogfelds automatisch zu verarbeiten. Die Datenzuordnung bietet Funktionen, die die Steuerelemente im Dialogfeld mit den richtigen Werten initialisieren, die Daten abrufen und die Daten überprüfen.

Um ein modales Dialogfeld zu erstellen, erstellen Sie ein Objekt auf `DoModal` dem Stapel mithilfe des Konstruktors für die abgeleitete Dialogfeldklasse, und rufen Sie dann das Dialogfenster und seine Steuerelemente auf. Wenn Sie ein modusloses Dialogfeld `Create` erstellen möchten, rufen Sie den Konstruktor Ihrer Dialogklasse auf.

Sie können auch eine Vorlage im Arbeitsspeicher erstellen, indem Sie eine [DLGTEMPLATE-Datenstruktur](/windows/win32/api/winuser/ns-winuser-dlgtemplate) verwenden, wie im Windows SDK beschrieben. Rufen Sie `CDialog` nach dem Erstellen eines Objekts [CreateIndirect](#createindirect) auf, um ein modusloses Dialogfeld zu erstellen, oder rufen Sie [InitModalIndirect](#initmodalindirect) und [DoModal](#domodal) auf, um ein modales Dialogfeld zu erstellen.

Die Exchange- und Validierungsdatenzuordnung wird `CWnd::DoDataExchange` in einer Außerkraftsetzung geschrieben, die der neuen Dialogklasse hinzugefügt wird. Weitere Informationen zur Austausch- `CWnd` und Validierungsfunktionalität finden Sie in der [DoDataExchange-Memberfunktion.](../../mfc/reference/cwnd-class.md#dodataexchange)

Sowohl der Programmierer als `DoDataExchange` auch das Framework rufen indirekt über einen Aufruf von [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)auf.

Das Framework `UpdateData` ruft auf, wenn der Benutzer auf die Schaltfläche OK klickt, um ein modales Dialogfeld zu schließen. (Die Daten werden nicht abgerufen, wenn auf die Schaltfläche Abbrechen geklickt wird.) Die Standardimplementierung von [OnInitDialog](#oninitdialog) ruft auch auf, `UpdateData` um die Anfangswerte der Steuerelemente festzulegen. In der `OnInitDialog` Regel überschreiben Sie, um Steuerelemente weiter zu initialisieren. `OnInitDialog`wird aufgerufen, nachdem alle Dialogsteuerelemente erstellt wurden und kurz bevor das Dialogfeld angezeigt wird.

Sie können `CWnd::UpdateData` jederzeit während der Ausführung eines modalen oder moduslosen Dialogfelds aufrufen.

Wenn Sie ein Dialogfeld von Hand entwickeln, fügen Sie die erforderlichen Membervariablen selbst zur abgeleiteten Dialogfeldklasse hinzu und fügen Memberfunktionen hinzu, um diese Werte festzulegen oder abzurufen.

Ein modales Dialogfeld wird automatisch geschlossen, wenn der Benutzer die `EndDialog` Schaltflächen OK oder Abbrechen drückt oder wenn der Code die Memberfunktion aufruft.

Wenn Sie ein modusloses Dialogfeld implementieren, überschreiben Sie immer die `OnCancel` Memberfunktion und rufen Sie daraus auf. `DestroyWindow` Rufen Sie nicht die `CDialog::OnCancel`Basisklasse `EndDialog`auf, da sie aufruft, was das Dialogfeld unsichtbar macht, es aber nicht zerstört. Sie sollten auch `PostNcDestroy` für moduslose Dialogfelder überschreiben, um **diese**zu löschen, da moduslose Dialogfelder in der Regel mit **neuen**zugeordnet werden. Modale Dialogfelder werden in der Regel `PostNcDestroy` auf dem Rahmen erstellt und müssen nicht bereinigen.

Weitere Informationen `CDialog`zu finden Sie unter [Dialogfelder](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cdialogcdialog"></a><a name="cdialog"></a>CDialog::CDialog

Um ein ressourcenbasiertes modales Dialogfeld zu erstellen, rufen Sie eine der beiden öffentlichen Formen des Konstruktors auf.

```
explicit CDialog(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

explicit CDialog(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);

CDialog();
```

### <a name="parameters"></a>Parameter

*lpszTemplateName*<br/>
Enthält eine null-terminierte Zeichenfolge, die der Name einer Dialogfeldvorlagenressource ist.

*nIDTemplate*<br/>
Enthält die ID-Nummer einer Dialogfeldvorlagenressource.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogobjekts auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Eine Form des Konstruktors ermöglicht den Zugriff auf die Dialogressource nach Vorlagenname. Der andere Konstruktor gewährt den Zugriff über die Vorlagen-ID-Nummer, in der Regel mit einem **IDD_** Präfix (z. B. IDD_DIALOG1).

Um ein modales Dialogfeld aus einer Vorlage im Speicher zu erstellen, `InitModalIndirect`rufen Sie zuerst den parameterlosen, geschützten Konstruktor auf und rufen Sie dann auf.

Nachdem Sie ein modales Dialogfeld mit einer `DoModal`der oben genannten Methoden erstellt haben, rufen Sie auf.

Um ein modusloses Dialogfeld zu erstellen, `CDialog` verwenden Sie die geschützte Form des Konstruktors. Der Konstruktor ist geschützt, da Sie eine eigene Dialogfeldklasse ableiten müssen, um ein modusloses Dialogfeld zu implementieren. Die Erstellung eines moduslosen Dialogfelds ist ein zweistufiger Prozess. Rufen Sie zuerst den Konstruktor auf; rufen Sie `Create` dann die Memberfunktion auf, um `CreateIndirect` ein ressourcenbasiertes Dialogfeld zu erstellen, oder rufen Sie das Dialogfeld aus einer Vorlage im Arbeitsspeicher auf.

## <a name="cdialogcreate"></a><a name="create"></a>CDialog::Erstellen

Rufen `Create` Sie an, um ein modusloses Dialogfeld mithilfe einer Dialogfeldvorlage aus einer Ressource zu erstellen.

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*lpszTemplateName*<br/>
Enthält eine null-terminierte Zeichenfolge, die der Name einer Dialogfeldvorlagenressource ist.

*pParentWnd*<br/>
Zeigt auf das übergeordnete Fensterobjekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogobjekts auf das Hauptanwendungsfenster festgelegt.

*nIDTemplate*<br/>
Enthält die ID-Nummer einer Dialogfeldvorlagenressource.

### <a name="return-value"></a>Rückgabewert

Beide Formulare geben einen Wert ungleich Null zurück, wenn die Erstellung und Initialisierung des Dialogfelds erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie können den `Create` Aufruf innerhalb des Konstruktors setzen oder aufrufen, nachdem der Konstruktor aufgerufen wurde.

Für den `Create` Zugriff auf die Dialogfeldvorlagenressource werden zwei Formen der Memberfunktion entweder über vorlagenname oder vorlagen-ID-Nummer bereitgestellt (z. B. IDD_DIALOG1).

Übergeben Sie für beide Formen einen Zeiger auf das übergeordnete Fensterobjekt. Wenn *pParentWnd* NULL ist, wird das Dialogfeld erstellt, wenn das übergeordnete oder Besitzerfenster auf das Hauptanwendungsfenster festgelegt ist.

Die `Create` Memberfunktion kehrt unmittelbar nach dem Erstellen des Dialogfelds zurück.

Verwenden Sie den Stil WS_VISIBLE in der Dialogfeldvorlage, wenn das Dialogfeld beim Erstellen des übergeordneten Fensters angezeigt werden soll. Andernfalls müssen Sie `ShowWindow`anrufen . Weitere Dialogfeldstile und deren Anwendung finden Sie in der [DLGTEMPLATE-Struktur](/windows/win32/api/winuser/ns-winuser-dlgtemplate) im Windows SDK und in den [Fensterstilen](../../mfc/reference/styles-used-by-mfc.md#window-styles) in der *MFC-Referenz*.

Verwenden `CWnd::DestroyWindow` Sie die Funktion, um `Create` ein von der Funktion erstelltes Dialogfeld zu zerstören.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

## <a name="cdialogcreateindirect"></a><a name="createindirect"></a>CDialog::CreateIndirect

Rufen Sie diese Memberfunktion auf, um ein modusloses Dialogfeld aus einer Dialogfeldvorlage im Speicher zu erstellen.

```
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*lpDialogTemplate*<br/>
Punkte in den Arbeitsspeicher, der eine Dialogfeldvorlage enthält, die zum Erstellen des Dialogfelds verwendet wird. Diese Vorlage hat eine [DLGTEMPLATE-Struktur](/windows/win32/api/winuser/ns-winuser-dlgtemplate) und Steuerelementinformationen, wie im Windows SDK beschrieben.

*pParentWnd*<br/>
Zeigt auf das übergeordnete Fensterobjekt des Dialogobjekts (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)). Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogobjekts auf das Hauptanwendungsfenster festgelegt.

*lpDialogInit*<br/>
Zeigt auf eine DLGINIT-Ressource.

*hDialogTemplate*<br/>
Enthält ein Handle für den globalen Speicher, der eine Dialogfeldvorlage enthält. Diese Vorlage besteht aus `DLGTEMPLATE` einer Struktur und Daten für jedes Steuerelement im Dialogfeld.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dialogfeld erfolgreich erstellt und initialisiert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `CreateIndirect` Memberfunktion kehrt unmittelbar nach dem Erstellen des Dialogfelds zurück.

Verwenden Sie den Stil WS_VISIBLE in der Dialogfeldvorlage, wenn das Dialogfeld beim Erstellen des übergeordneten Fensters angezeigt werden soll. Andernfalls müssen Sie `ShowWindow` anrufen, damit es angezeigt wird. Weitere Informationen dazu, wie Sie andere Dialogfeldstile in der Vorlage angeben können, finden Sie in der [DLGTEMPLATE-Struktur](/windows/win32/api/winuser/ns-winuser-dlgtemplate) im Windows SDK.

Verwenden `CWnd::DestroyWindow` Sie die Funktion, um `CreateIndirect` ein von der Funktion erstelltes Dialogfeld zu zerstören.

Dialogfelder, die ActiveX-Steuerelemente enthalten, erfordern zusätzliche Informationen, die in einer DLGINIT-Ressource bereitgestellt werden.

## <a name="cdialogdomodal"></a><a name="domodal"></a>CDialog::DoModal

Rufen Sie diese Memberfunktion auf, um das modale Dialogfeld aufzurufen und das Dialogfeldergebnis zurückzugeben, wenn Dies geschieht.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Ein **int-Wert,** der den Wert des *nResult-Parameters* angibt, der an die [CDialog::EndDialog-Memberfunktion](#enddialog) übergeben wurde, die zum Schließen des Dialogfelds verwendet wird. Der Rückgabewert ist -1, wenn die Funktion das Dialogfeld nicht erstellen konnte, oder IDABORT, wenn ein anderer Fehler aufgetreten ist, in diesem Fall enthält das Ausgabefenster Fehlerinformationen aus [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion verarbeitet die gesamte Interaktion mit dem Benutzer, während das Dialogfeld aktiv ist. Dies ist es, was das Dialogfeld modal macht; Das heißt, der Benutzer kann erst dann mit anderen Fenstern interagieren, wenn das Dialogfeld geschlossen ist.

Wenn der Benutzer auf eine der Drucktasten im Dialogfeld klickt, z. B. OK oder Abbrechen, wird eine Nachrichtenhandlermemberfunktion wie [OnOK](#onok) oder [OnCancel](#oncancel)aufgerufen, um zu versuchen, das Dialogfeld zu schließen. Die `OnOK` Standardmemberfunktion überprüft und aktualisiert die Dialogfelddaten und schließt das Dialogfeld `OnCancel` mit Ergebnis-IDOK, und die Standardmemberfunktion schließt das Dialogfeld mit result IDCANCEL, ohne die Dialogfelddaten zu überprüfen oder zu aktualisieren. Sie können diese Nachrichtenhandlerfunktionen überschreiben, um ihr Verhalten zu ändern.

> [!NOTE]
> `PreTranslateMessage`wird nun für die Verarbeitung des modalen Dialogfelds aufgefordert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

## <a name="cdialogenddialog"></a><a name="enddialog"></a>CDialog::EndDialog

Rufen Sie diese Memberfunktion auf, um ein modales Dialogfeld zu beenden.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parameter

*nResult*<br/>
Enthält den Wert, der aus dem Dialogfeld `DoModal`an den Aufrufer von zurückgegeben werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion gibt *nResult* als `DoModal`Rückgabewert von zurück. Sie müssen `EndDialog` die Funktion verwenden, um die Verarbeitung abzuschließen, wenn ein modales Dialogfeld erstellt wird.

Sie können `EndDialog` jederzeit aufrufen, auch in [OnInitDialog](#oninitdialog), in diesem Fall sollten Sie das Dialogfeld schließen, bevor es angezeigt wird oder bevor der Eingabefokus festgelegt wird.

`EndDialog`schließt das Dialogfeld nicht sofort. Stattdessen wird ein Flag festgelegt, das das Dialogfeld zum Schließen angibt, sobald der aktuelle Nachrichtenhandler zurückkehrt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

## <a name="cdialoggetdefid"></a><a name="getdefid"></a>CDialog::GetDefID

Rufen `GetDefID` Sie die Memberfunktion auf, um die ID des Standard-Drucktastensteuerelements für ein Dialogfeld abzurufen.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Rückgabewert

Ein 32-Bit-Wert ( `DWORD`). Wenn die Standardtaste einen ID-Wert hat, enthält das Wort mit hoher Ordnung DC_HASDEFID und das Wort niedriger Ordnung den ID-Wert. Wenn die Standardtaste keinen ID-Wert hat, ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Dies ist in der Regel eine OK-Schaltfläche.

## <a name="cdialoggotodlgctrl"></a><a name="gotodlgctrl"></a>CDialog::GotoDlgCtrl

Verschiebt den Fokus auf das angegebene Steuerelement im Dialogfeld.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parameter

*pWndCtrl*<br/>
Identifiziert das Fenster (Steuerelement), das den Fokus empfangen soll.

### <a name="remarks"></a>Bemerkungen

Um einen Zeiger auf das Steuerelement (untergeordnetes Fenster) zu erhalten, `CWnd::GetDlgItem` das als *pWndCtrl*übergeben werden soll, rufen Sie die Memberfunktion auf, die einen Zeiger auf ein [CWnd-Objekt](../../mfc/reference/cwnd-class.md) zurückgibt.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

## <a name="cdialoginitmodalindirect"></a><a name="initmodalindirect"></a>CDialog::InitModalIndirect

Rufen Sie diese Memberfunktion auf, um ein modales Dialogfeldobjekt mithilfe einer Dialogfeldvorlage zu initialisieren, die Sie im Arbeitsspeicher erstellen.

```
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*lpDialogTemplate*<br/>
Punkte in den Arbeitsspeicher, der eine Dialogfeldvorlage enthält, die zum Erstellen des Dialogfelds verwendet wird. Diese Vorlage hat eine [DLGTEMPLATE-Struktur](/windows/win32/api/winuser/ns-winuser-dlgtemplate) und Steuerelementinformationen, wie im Windows SDK beschrieben.

*hDialogTemplate*<br/>
Enthält ein Handle für den globalen Speicher, der eine Dialogfeldvorlage enthält. Diese Vorlage besteht aus `DLGTEMPLATE` einer Struktur und Daten für jedes Steuerelement im Dialogfeld.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogobjekts auf das Hauptanwendungsfenster festgelegt.

*lpDialogInit*<br/>
Zeigt auf eine DLGINIT-Ressource.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dialogobjekt erfolgreich erstellt und initialisiert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Um ein modales Dialogfeld indirekt zu erstellen, weisen Sie zunächst einen globalen Speicherblock zu und füllen ihn mit der Dialogfeldvorlage aus. Rufen Sie `CDialog` dann den leeren Konstruktor auf, um das Dialogfeldobjekt zu erstellen. Rufen Sie `InitModalIndirect` als Nächstes an, um Ihr Handle in der Vorlage für das Dialogfeld im Arbeitsspeicher zu speichern. Das Windows-Dialogfeld wird erstellt und später angezeigt, wenn die [DoModal-Memberfunktion](#domodal) aufgerufen wird.

Dialogfelder, die ActiveX-Steuerelemente enthalten, erfordern zusätzliche Informationen, die in einer DLGINIT-Ressource bereitgestellt werden.

## <a name="cdialogmapdialogrect"></a><a name="mapdialogrect"></a>CDialog::MapDialogRect

Rufen Sie an, um die Dialogfeldeinheiten eines Rechtecks in Bildschirmeinheiten zu konvertieren.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das die zu konvertierenden Dialogfeldkoordinaten enthält.

### <a name="remarks"></a>Bemerkungen

Dialogfeldeinheiten werden in Bezug auf die aktuelle Dialogfeld-Basiseinheit angegeben, die von der durchschnittlichen Breite und Höhe der Zeichen in der Schriftart abgeleitet ist, die für Dialogfeldtext verwendet wird. Eine horizontale Einheit ist ein Viertel der Dialogfeld-Basisbreiteneinheit, und eine vertikale Einheit ist ein Achtel der Dialogfeld-Basishöheneinheit.

Die `GetDialogBaseUnits` Windows-Funktion gibt Größeninformationen für die Systemschriftart zurück, Sie können jedoch für jedes Dialogfeld eine andere Schriftart angeben, wenn Sie den Stil DS_SETFONT in der Ressourcendefinitionsdatei verwenden. Die `MapDialogRect` Windows-Funktion verwendet die entsprechende Schriftart für dieses Dialogfeld.

Die `MapDialogRect` Memberfunktion ersetzt die Dialogfeldeinheiten in *lpRect* durch Bildschirmeinheiten (Pixel), sodass das Rechteck verwendet werden kann, um ein Dialogfeld zu erstellen oder ein Steuerelement innerhalb eines Feldes zu positionieren.

## <a name="cdialognextdlgctrl"></a><a name="nextdlgctrl"></a>CDialog::NextDlgCtrl

Verschiebt den Fokus auf das nächste Steuerelement im Dialogfeld.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Bemerkungen

Wenn sich der Fokus am letzten Steuerelement im Dialogfeld befindet, wird er zum ersten Steuerelement verschoben.

## <a name="cdialogoncancel"></a><a name="oncancel"></a>CDialog::OnCancel

Das Framework ruft diese Methode auf, wenn der Benutzer auf **Abbrechen** klickt oder die ESC-Taste in einem modalen oder moduslosen Dialogfeld drückt.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um Aktionen auszuführen (z. B. das Wiederherstellen alter Daten), wenn ein Benutzer das Dialogfeld schließt, indem er auf **Abbrechen** oder die ESC-Taste klickt. Die Standardeinstellung schließt ein modales Dialogfeld, indem [EndDialog](#enddialog) aufgerufen wird und [DoModal](#domodal) IDCANCEL zurückgibt.

Wenn Sie die **Schaltfläche Abbrechen** in einem moduslosen Dialogfeld implementieren, müssen Sie die `OnCancel` Methode überschreiben und [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) darin aufrufen. Rufen Sie die Basisklassenmethode nicht `EndDialog`auf, da sie aufruft, wodurch das Dialogfeld unsichtbar wird, aber nicht zerstört wird.

> [!NOTE]
> Sie können diese Methode nicht `CFileDialog` überschreiben, wenn Sie ein Objekt in einem Programm verwenden, das unter Windows XP kompiliert wird. Weitere Informationen `CFileDialog`zu finden Sie unter [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

## <a name="cdialogoninitdialog"></a><a name="oninitdialog"></a>CDialog::OnInitDialog

Diese Methode wird als `WM_INITDIALOG` Reaktion auf die Nachricht aufgerufen.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Gibt an, ob die Anwendung den Eingabefokus auf eines der Steuerelemente im Dialogfeld festgelegt hat. Wenn `OnInitDialog` der Eingabefokus ungleich Null zurückgegeben wird, legt windows den Eingabefokus auf die Standardposition, das erste Steuerelement im Dialogfeld, fest. Die Anwendung kann 0 nur zurückgeben, wenn sie den Eingabefokus explizit auf eines der Steuerelemente im Dialogfeld festgelegt hat.

### <a name="remarks"></a>Bemerkungen

Windows sendet `WM_INITDIALOG` die Nachricht während der [Aufrufe Create](#create), [CreateIndirect](#createindirect)oder [DoModal](#domodal) an das Dialogfeld, die unmittelbar vor der Anzeige des Dialogfelds auftreten.

Überschreiben Sie diese Methode, wenn Sie eine spezielle Verarbeitung durchführen möchten, wenn das Dialogfeld initialisiert wird. Rufen Sie in der überschriebenen `OnInitDialog` Version zuerst die Basisklasse auf, ignorieren jedoch deren Rückgabewert. In der `TRUE` Regel kehren Sie von der überschriebenen Methode zurück.

Windows ruft `OnInitDialog` die Funktion mithilfe der standardmäßigen globalen Dialogfeldprozedur auf, die allen Dialogfeldern der Microsoft Foundation-Klassenbibliothek gemeinsam ist. Diese Funktion wird nicht über Ihre Nachrichtenzuordnung aufrufen, und Daher benötigen Sie keinen Nachrichtenzuordnungseintrag für diese Methode.

> [!NOTE]
> Sie können diese Methode nicht `CFileDialog` überschreiben, wenn Sie ein Objekt in einem Programm verwenden, das unter Windows Vista oder neueren Betriebssystemen kompiliert wird. Weitere Informationen zu `CFileDialog` Änderungen an unter Windows Vista und höher finden Sie unter [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

## <a name="cdialogonok"></a><a name="onok"></a>CDialog::OnOK

Wird aufgerufen, wenn der Benutzer auf die **Schaltfläche OK** klickt (die Schaltfläche mit der IDOK-ID).

```
virtual void OnOK();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um Aktionen auszuführen, wenn die **Schaltfläche OK** aktiviert ist. Wenn das Dialogfeld die automatische Datenüberprüfung und den automatischen Austausch enthält, überprüft die Standardimplementierung dieser Methode die Dialogfelddaten und aktualisiert die entsprechenden Variablen in der Anwendung.

Wenn Sie die **Schaltfläche OK** in einem moduslosen Dialogfeld implementieren, müssen Sie die `OnOK` Methode überschreiben und [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) darin aufrufen. Rufen Sie die Basisklassenmethode nicht auf, da sie [EndDialog](#enddialog) aufruft, wodurch das Dialogfeld unsichtbar wird, es jedoch nicht zerstört wird.

> [!NOTE]
> Sie können diese Methode nicht `CFileDialog` überschreiben, wenn Sie ein Objekt in einem Programm verwenden, das unter Windows XP kompiliert wird. Weitere Informationen `CFileDialog`zu finden Sie unter [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

## <a name="cdialogonsetfont"></a><a name="onsetfont"></a>CDialog::OnSetFont

Gibt die Schriftart an, die ein Dialogfeldsteuerelement beim Zeichnen von Text verwendet.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parameter

*pFont*<br/>
[in] Gibt einen Zeiger auf die Schriftart an, der als Standardschriftart für alle Steuerelemente in diesem Dialogfeld verwendet wird.

### <a name="remarks"></a>Bemerkungen

Das Dialogfeld verwendet die angegebene Schriftart als Standard für alle Steuerelemente.

Der Dialogdialog-Editor legt in der Regel die Dialogfeldschriftart als Teil der Dialogfeldvorlagenressource fest.

> [!NOTE]
> Sie können diese Methode nicht `CFileDialog` überschreiben, wenn Sie ein Objekt in einem Programm verwenden, das unter Windows Vista oder neueren Betriebssystemen kompiliert wird. Weitere Informationen zu `CFileDialog` Änderungen an unter Windows Vista und höher finden Sie unter [CFileDialog Class](../../mfc/reference/cfiledialog-class.md).

## <a name="cdialogprevdlgctrl"></a><a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl

Legt den Fokus auf das vorherige Steuerelement im Dialogfeld fest.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Bemerkungen

Wenn sich der Fokus beim ersten Steuerelement im Dialogfeld befindet, wird er zum letzten Steuerelement im Feld verschoben.

## <a name="cdialogsetdefid"></a><a name="setdefid"></a>CDialog::SetDefID

Ändert das Standard-Tastensteuerelement für ein Dialogfeld.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Gibt die ID des Drucktastensteuerelements an, das zum Standardsteuerelement wird.

## <a name="cdialogsethelpid"></a><a name="sethelpid"></a>CDialog::SetHelpID

Legt eine kontextsensitive Hilfe-ID für das Dialogfeld fest.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parameter

*nIDR*<br/>
Gibt die kontextsensitive Hilfe-ID an.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
