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
ms.openlocfilehash: b07190c70fb11950b25aff45fb10e850c0e81b24
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424476"
---
# <a name="cdialog-class"></a>CDialog-Klasse

Die Basisklasse, die zum Anzeigen von Dialogfeldern auf dem Bildschirm verwendet wird.

## <a name="syntax"></a>Syntax

```
class CDialog : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CDialog:: CDialog](#cdialog)|Erstellt ein `CDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CDialog:: Create](#create)|Initialisiert das `CDialog`-Objekt. Erstellt ein nicht modalem Dialogfeld und fügt es an das `CDialog` Objekt an.|
|[CDialog:: kreatandirect](#createindirect)|Erstellt ein nicht modalem Dialogfeld aus einer Dialogfeld Vorlage im Speicher (nicht Ressourcen basiert).|
|[CDialog::D omodal](#domodal)|Ruft ein modales Dialogfeld auf und gibt nach Abschluss des Vorgangs zurück.|
|[CDialog:: EndDialog](#enddialog)|Schließt ein modales Dialogfeld.|
|[CDialog:: getdefid](#getdefid)|Ruft die ID des Standard-PUSHBUTTON-Steuer Elements für ein Dialogfeld ab.|
|[CDialog:: godedlgctrl](#gotodlgctrl)|Verschiebt den Fokus auf ein angegebenes Dialogfeld-Steuerelement im Dialogfeld.|
|[CDialog:: initmodalindirekte](#initmodalindirect)|Erstellt ein modales Dialogfeld aus einer Dialogfeld Vorlage im Speicher (nicht Ressourcen basiert). Die Parameter werden so lange gespeichert, bis die Funktion `DoModal` aufgerufen wird.|
|[CDialog:: mapdialogrect](#mapdialogrect)|Konvertiert die Dialogfeld Einheiten eines Rechtecks in Bildschirm Einheiten.|
|[CDialog:: nextdlgctrl](#nextdlgctrl)|Verschiebt den Fokus auf das nächste Dialogfeld-Steuerelement im Dialogfeld.|
|[CDialog:: OnInitDialog](#oninitdialog)|Überschreiben, um die Dialogfeld Initialisierung zu vergrößern.|
|[CDialog:: onsetfont](#onsetfont)|Überschreiben Sie, um die Schriftart anzugeben, die ein Dialogfeld-Steuerelement beim Zeichnen von Text verwenden soll.|
|[CDialog::P revdlgctrl](#prevdlgctrl)|Verschiebt den Fokus auf das vorherige Dialogfeld-Steuerelement im Dialogfeld.|
|[CDialog:: setdefid](#setdefid)|Ändert das standardmäßige PUSHBUTTON-Steuerelement für ein Dialogfeld in eine angegebene pushschaltfläche.|
|[CDialog:: ablokpid](#sethelpid)|Legt eine kontextabhängige Hilfe-ID für das Dialogfeld fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CDialog:: OnCancel](#oncancel)|Überschreiben, um die Schaltfläche Abbrechen oder ESC-Taste auszuführen. Standardmäßig wird das Dialogfeld geschlossen, und `DoModal` gibt IDCANCEL zurück.|
|[CDialog:: OnOK](#onok)|Überschreiben, um die Schaltflächen Aktion OK in einem modalen Dialogfeld auszuführen. Standardmäßig wird das Dialogfeld geschlossen, und `DoModal` gibt IDOK zurück.|

## <a name="remarks"></a>Hinweise

Dialog Felder haben zwei Typen: Modal und nicht modale. Ein modales Dialogfeld muss vom Benutzer geschlossen werden, bevor die Anwendung fortgesetzt wird. Mit einem nicht modalem Dialogfeld kann der Benutzer das Dialogfeld anzeigen und zu einer anderen Aufgabe zurückkehren, ohne das Dialogfeld zu abbrechen oder zu entfernen.

Ein `CDialog`-Objekt ist eine Kombination aus einer Dialogfeld Vorlage und einer `CDialog`abgeleiteten Klasse. Verwenden Sie den Dialog-Editor, um die Dialog Vorlage zu erstellen und in einer Ressource zu speichern. verwenden Sie dann den Assistenten zum Hinzufügen von Klassen, um eine von `CDialog`abgeleitete Klasse zu erstellen

Ein Dialogfeld empfängt, wie ein beliebiges anderes Fenster, Meldungen von Windows. In einem Dialogfeld sind Sie besonders an der Verarbeitung von Benachrichtigungs Meldungen aus den Steuerelementen des Dialog Felds interessiert, da der Benutzer mit dem Dialogfeld interagiert. Verwenden Sie den [Klassen-Assistenten](mfc-class-wizard.md) , um auszuwählen, welche Nachrichten Sie behandeln möchten, und fügt der Klasse die entsprechenden Meldungs Zuordnungs Einträge und nachrichtenhandlermember-Funktionen hinzu. Sie müssen nur anwendungsspezifischen Code in den handlermember-Funktionen schreiben.

Wenn Sie möchten, können Sie Nachrichten Zuordnungs Einträge und Element Funktionen immer manuell schreiben.

In allen außer dem trivialen Dialogfeld fügen Sie ihrer abgeleiteten Dialogfeld Klasse Element Variablen hinzu, um Daten zu speichern, die vom Benutzer in den Steuerelementen des Dialog Felds eingegeben werden, oder um Daten für den Benutzer anzuzeigen. Sie können den Assistenten zum Hinzufügen von Variablen verwenden, um Element Variablen zu erstellen und Sie Steuerelementen zuzuordnen. Gleichzeitig wählen Sie einen Variablentyp und einen zulässigen Wertebereich für jede Variable aus. Der Code-Assistent fügt die Element Variablen ihrer abgeleiteten Dialogfeld Klasse hinzu.

Eine Datenzuordnung wird generiert, um den Datenaustausch zwischen den Element Variablen und den Steuerelementen des Dialog Felds automatisch zu verarbeiten. Die Datenzuordnung enthält Funktionen, die die Steuerelemente im Dialogfeld mit den richtigen Werten initialisieren, die Daten abrufen und die Daten überprüfen.

Um ein modales Dialogfeld zu erstellen, erstellen Sie ein Objekt im Stapel mithilfe des Konstruktors für die abgeleitete Dialogfeld Klasse, und rufen Sie dann `DoModal` auf, um das Dialogfenster und seine Steuerelemente zu erstellen. Wenn Sie ein nicht modalem Dialogfeld erstellen möchten, rufen Sie `Create` im Konstruktor der Dialogfeld Klasse auf.

Sie können auch eine Vorlage im Speicher erstellen, indem Sie eine [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) -Datenstruktur verwenden, wie im Windows SDK beschrieben. Nachdem Sie ein `CDialog` Objekt erstellt haben, rufen Sie " [kreateindirect](#createindirect) " auf, um ein nicht modales Dialogfeld zu erstellen, oder rufen Sie [initmodalindirekte](#initmodalindirect) und [DoModal](#domodal) auf, um ein modales Dialogfeld zu erstellen

Die Exchange-und Validierungsdaten Zuordnung wird in eine außer Kraft setzung der `CWnd::DoDataExchange` geschrieben, die der neuen Dialogfeld Klasse hinzugefügt wird. Weitere Informationen zu den Exchange-und Validierungs Funktionen finden Sie unter der [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) -Member-Funktion in `CWnd`.

Sowohl der Programmierer als auch der Framework-Rückruf `DoDataExchange` indirekt durch einen [CWnd:: UpdateData](../../mfc/reference/cwnd-class.md#updatedata)-Befehl.

Das Framework ruft `UpdateData` auf, wenn der Benutzer auf die Schaltfläche OK klickt, um ein modales Dialogfeld zu schließen. (Die Daten werden nicht abgerufen, wenn auf die Schaltfläche Abbrechen geklickt wird.) Die Standard Implementierung von [OnInitDialog](#oninitdialog) ruft auch `UpdateData` auf, um die Anfangswerte der Steuerelemente festzulegen. In der Regel überschreiben Sie `OnInitDialog`, um Steuerelemente weiter zu initialisieren `OnInitDialog` wird aufgerufen, nachdem alle Dialogfeld Steuerelemente erstellt wurden und kurz bevor das Dialogfeld angezeigt wird.

Sie können `CWnd::UpdateData` jederzeit während der Ausführung eines modalen oder nicht modalen Dialog Felds aufgerufen werden.

Wenn Sie ein Dialogfeld manuell entwickeln, fügen Sie die erforderlichen Element Variablen der abgeleiteten Dialogfeld Klasse hinzu, und Sie fügen Element Funktionen hinzu, um diese Werte festzulegen oder zu erhalten.

Ein modales Dialogfeld wird automatisch geschlossen, wenn der Benutzer die Schaltflächen OK oder Abbrechen drückt, oder wenn der Code die `EndDialog` Member-Funktion aufruft.

Wenn Sie ein nicht modalem Dialogfeld implementieren, überschreiben Sie immer die `OnCancel` Member-Funktion, und nennen Sie `DestroyWindow` darin. Rufen Sie nicht die Basisklasse `CDialog::OnCancel`auf, da Sie `EndDialog`aufruft, wodurch das Dialogfeld unsichtbar wird, aber nicht zerstört wird. Sie sollten auch `PostNcDestroy` für nicht modlose Dialogfelder überschreiben, um **Dies**zu löschen, da die Dialogfelder ohne Modus in der Regel mit **New**zugeordnet werden. Modale Dialogfelder werden in der Regel auf dem Frame erstellt und benötigen keine `PostNcDestroy` Bereinigung.

Weitere Informationen zu `CDialog`finden Sie unter [Dialog Felder](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxwin.h

##  <a name="cdialog"></a>CDialog:: CDialog

Um ein Ressourcen basiertes modales Dialogfeld zu erstellen, müssen Sie entweder die öffentliche Form des Konstruktors aufzurufen.

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

*lpsztemplatename*<br/>
Enthält eine NULL-terminierte Zeichenfolge, die den Namen einer Dialogfeld Vorlagen Ressource ist.

*nidtemplate*<br/>
Enthält die ID-Nummer einer Dialogfeld Vorlagen-Ressource.

*pparser*<br/>
Verweist auf das übergeordnete oder Besitzer Fenster Objekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialog Objekt gehört. Wenn der Wert NULL ist, wird das übergeordnete Fenster des Dialog Objekts auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Hinweise

Eine Form des Konstruktors ermöglicht den Zugriff auf die Dialog Ressource über den Vorlagen Namen. Der andere Konstruktor ermöglicht den Zugriff über die Vorlagen-ID-Nummer, in der Regel mit einem **IDD_** Präfix (z. b. IDD_DIALOG1).

Um ein modales Dialogfeld aus einer Vorlage im Arbeitsspeicher zu erstellen, rufen Sie zunächst den Parameter losen, geschützten Konstruktor auf, und rufen Sie dann `InitModalIndirect`auf.

Wenn Sie ein modales Dialogfeld mit einer der oben genannten Methoden erstellt haben, wenden Sie `DoModal`an.

Um ein nicht Modaldialogfeld zu erstellen, verwenden Sie das geschützte Formular des `CDialog` Konstruktors. Der Konstruktor ist geschützt, da Sie eine eigene Dialogfeld Klasse ableiten müssen, um ein nicht modalem Dialogfeld zu implementieren. Die Erstellung eines nicht modalen Dialog Felds ist ein zweistufiger Prozess. Ruft zuerst den Konstruktor auf. Rufen Sie dann die `Create` Member-Funktion auf, um ein Ressourcen basiertes Dialogfeld zu erstellen, oder rufen Sie `CreateIndirect` auf, um das Dialogfeld aus einer Vorlage im Arbeitsspeicher zu erstellen.

##  <a name="create"></a>CDialog:: Create

Rufen Sie `Create` auf, um ein nicht modalem Dialogfeld mithilfe einer Dialogfeld Vorlage aus einer Ressource zu erstellen.

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*lpsztemplatename*<br/>
Enthält eine NULL-terminierte Zeichenfolge, die den Namen einer Dialogfeld Vorlagen Ressource ist.

*pparser*<br/>
Zeigt auf das übergeordnete Fenster Objekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialog Objekt gehört. Wenn der Wert NULL ist, wird das übergeordnete Fenster des Dialog Objekts auf das Hauptanwendungsfenster festgelegt.

*nidtemplate*<br/>
Enthält die ID-Nummer einer Dialogfeld Vorlagen-Ressource.

### <a name="return-value"></a>Rückgabewert

Beide Formulare geben einen Wert ungleich 0 (null) zurück, wenn die Dialogfeld Erstellung und Initialisierung erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Hinweise

Sie können den Aufruf `Create` innerhalb des Konstruktors platzieren oder ihn aufrufen, nachdem der Konstruktor aufgerufen wurde.

Zwei Formen der `Create` Member-Funktion werden für den Zugriff auf die Vorlagen Ressource des Dialog Felds über den Vorlagen Namen oder die Vorlagen-ID-Nummer (z. b. IDD_DIALOG1) bereitgestellt.

Übergeben Sie für beide Formulare einen Zeiger auf das übergeordnete Fenster Objekt. Wenn *pparser* auf NULL festgelegt ist, wird das Dialogfeld erstellt, dessen übergeordnetes Element oder Besitzer Fenster auf das Hauptanwendungsfenster festgelegt ist.

Die `Create` Member-Funktion gibt sofort zurück, nachdem das Dialogfeld erstellt wurde.

Verwenden Sie das WS_VISIBLE Format in der Dialogfeld Vorlage, wenn das Dialogfeld angezeigt werden soll, wenn das übergeordnete Fenster erstellt wird. Andernfalls müssen Sie `ShowWindow`abrufen. Weitere Dialogfeld Stile und deren Anwendung finden Sie in der [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) -Struktur in den Windows SDK-und [Fenster Stilen](../../mfc/reference/styles-used-by-mfc.md#window-styles) in der *MFC-Referenz*.

Verwenden Sie die `CWnd::DestroyWindow`-Funktion, um ein von der `Create`-Funktion erstelltes Dialogfeld zu zerstören.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>CDialog:: kreatandirect

Rufen Sie diese Member-Funktion auf, um ein nicht modalem Dialogfeld aus einer Dialogfeld Vorlage im Arbeitsspeicher zu erstellen.

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

*lpdialogtemplate*<br/>
Zeigt auf den Arbeitsspeicher, der eine Dialogfeld Vorlage enthält, die zum Erstellen des Dialog Felds verwendet wird. Diese Vorlage ist in Form einer [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) -Struktur und von Steuerungsinformationen, wie im Windows SDK beschrieben.

*pparser*<br/>
Zeigt auf das übergeordnete Fenster Objekt des Dialog Objekts (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)). Wenn der Wert NULL ist, wird das übergeordnete Fenster des Dialog Objekts auf das Hauptanwendungsfenster festgelegt.

*lpdialoginit*<br/>
Verweist auf eine dlginit-Ressource.

*hdialogtemplate*<br/>
Enthält ein Handle für den globalen Speicher, der eine Dialogfeld Vorlage enthält. Diese Vorlage befindet sich in Form einer `DLGTEMPLATE` Struktur und Daten für jedes Steuerelement im Dialogfeld.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Dialogfeld erfolgreich erstellt und initialisiert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die `CreateIndirect` Member-Funktion gibt sofort zurück, nachdem das Dialogfeld erstellt wurde.

Verwenden Sie das WS_VISIBLE Format in der Dialogfeld Vorlage, wenn das Dialogfeld angezeigt werden soll, wenn das übergeordnete Fenster erstellt wird. Andernfalls müssen Sie `ShowWindow` aufzurufen, damit Sie angezeigt wird. Weitere Informationen zum Angeben anderer Dialogfeld Stile in der Vorlage finden Sie in der [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) -Struktur in der Windows SDK.

Verwenden Sie die `CWnd::DestroyWindow`-Funktion, um ein von der `CreateIndirect`-Funktion erstelltes Dialogfeld zu zerstören.

Für Dialog Felder, die ActiveX-Steuerelemente enthalten, sind zusätzliche Informationen in einer dlginit-Ressource erforderlich.

##  <a name="domodal"></a>CDialog::D omodal

Rufen Sie diese Member-Funktion auf, um das modale Dialogfeld aufzurufen, und geben Sie anschließend das Dialogfeld Ergebnis zurück.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Ein **int** -Wert, der den Wert des *nResult* -Parameters angibt, der an die Member-Funktion [CDialog:: EndDialog](#enddialog) übergeben wurde, die verwendet wird, um das Dialogfeld zu schließen. Der Rückgabewert ist-1, wenn die Funktion das Dialogfeld nicht erstellen konnte, oder idabort, wenn ein anderer Fehler aufgetreten ist. in diesem Fall enthält das Ausgabefenster Fehlerinformationen von [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Hinweise

Diese Member-Funktion verarbeitet die gesamte Interaktion mit dem Benutzer, während das Dialogfeld aktiv ist. Dadurch wird das Dialogfeld modal. Das heißt, der Benutzer kann erst dann mit anderen Fenstern interagieren, wenn das Dialogfeld geschlossen ist.

Wenn der Benutzer auf eine der Schaltflächen im Dialogfeld klickt, z. b. OK oder Abbrechen, wird eine nachrichtenhandlermember-Funktion, wie z. b. [OnOK](#onok) oder [OnCancel](#oncancel), aufgerufen, um zu versuchen, das Dialogfeld zu schließen. Die standardmäßige `OnOK` Member-Funktion überprüft und aktualisiert die Dialogfeld Daten und schließt das Dialogfeld mit dem Ergebnis IDOK, und die standardmäßige `OnCancel` Member-Funktion schließt das Dialogfeld mit dem Ergebnis IDCANCEL, ohne die Dialogfeld Daten zu überprüfen oder zu aktualisieren. Sie können diese nachrichtenhandlerfunktionen überschreiben, um Ihr Verhalten zu ändern.

> [!NOTE]
> `PreTranslateMessage` wird jetzt für die Nachrichtenverarbeitung im modalen Dialogfeld aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>CDialog:: EndDialog

Diese Member-Funktion wird aufgerufen, um ein modales Dialogfeld zu beenden.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parameter

*nergebnis*<br/>
Enthält den Wert, der vom Dialogfeld an den Aufrufer von `DoModal`zurückgegeben werden soll.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion gibt *nResult* als Rückgabewert `DoModal`zurück. Wenn ein modales Dialogfeld erstellt wird, müssen Sie die `EndDialog`-Funktion verwenden, um die Verarbeitung abzuschließen.

Sie können `EndDialog` jederzeit in [OnInitDialog](#oninitdialog)aufzurufen. in diesem Fall sollten Sie das Dialogfeld schließen, bevor es angezeigt wird, oder bevor der Eingabefokus festgelegt wird.

`EndDialog` schließt das Dialogfeld nicht sofort. Stattdessen wird ein Flag festgelegt, das das Dialogfeld zum Schließen anweist, sobald der aktuelle Nachrichten Handler zurückkehrt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>CDialog:: getdefid

Ruft die `GetDefID` Member-Funktion auf, um die ID des Standard-PUSHBUTTON-Steuer Elements für ein Dialogfeld zu erhalten.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Rückgabewert

Ein 32-Bit-Wert (`DWORD`). Wenn der Standardwert für PUSHBUTTON einen ID-Wert aufweist, enthält das hochwertige Wort DC_HASDEFID, und das nieder wertige Wort enthält den ID-Wert. Wenn der Standardwert für PUSHBUTTON keinen ID-Wert hat, ist der Rückgabewert 0.

### <a name="remarks"></a>Hinweise

Dies ist in der Regel eine Schaltfläche OK.

##  <a name="gotodlgctrl"></a>CDialog:: godedlgctrl

Verschiebt den Fokus auf das angegebene Steuerelement im Dialogfeld.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parameter

*pwndctrl*<br/>
Identifiziert das Fenster (Steuerelement), das den Fokus erhalten soll.

### <a name="remarks"></a>Hinweise

Um einen Zeiger auf das Steuerelement (untergeordnetes Fenster) zu erhalten, das als *pwndctrl*übergeben werden soll, nennen Sie die `CWnd::GetDlgItem` Member-Funktion, die einen Zeiger auf ein [CWnd](../../mfc/reference/cwnd-class.md) -Objekt zurückgibt.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CWnd:: GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

##  <a name="initmodalindirect"></a>CDialog:: initmodalindirekte

Diese Member-Funktion wird aufgerufen, um ein modales Dialogfeld Objekt mithilfe einer Dialogfeld Vorlage zu initialisieren, die Sie im Arbeitsspeicher erstellen.

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

*lpdialogtemplate*<br/>
Zeigt auf den Arbeitsspeicher, der eine Dialogfeld Vorlage enthält, die zum Erstellen des Dialog Felds verwendet wird. Diese Vorlage ist in Form einer [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) -Struktur und von Steuerungsinformationen, wie im Windows SDK beschrieben.

*hdialogtemplate*<br/>
Enthält ein Handle für den globalen Speicher, der eine Dialogfeld Vorlage enthält. Diese Vorlage befindet sich in Form einer `DLGTEMPLATE` Struktur und Daten für jedes Steuerelement im Dialogfeld.

*pparser*<br/>
Verweist auf das übergeordnete oder Besitzer Fenster Objekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialog Objekt gehört. Wenn der Wert NULL ist, wird das übergeordnete Fenster des Dialog Objekts auf das Hauptanwendungsfenster festgelegt.

*lpdialoginit*<br/>
Verweist auf eine dlginit-Ressource.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Dialog Objekt erfolgreich erstellt und initialisiert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Wenn Sie ein modales Dialogfeld indirekt erstellen möchten, müssen Sie zunächst einen globalen Speicherblock zuordnen und ihn mit der Dialogfeld Vorlage auffüllen. Anschließend können Sie den leeren `CDialog`-Konstruktor zum Erstellen des Dialogfeld Objekts aufzurufen. Als nächstes wird `InitModalIndirect` aufgerufen, um das Handle in der in-Memory-Dialogfeld Vorlage zu speichern. Das Dialogfeld Windows wird erstellt und später angezeigt, wenn die [DoModal](#domodal) -Member-Funktion aufgerufen wird.

Für Dialog Felder, die ActiveX-Steuerelemente enthalten, sind zusätzliche Informationen in einer dlginit-Ressource erforderlich.

##  <a name="mapdialogrect"></a>CDialog:: mapdialogrect

Wird aufgerufen, um die Dialogfeld Einheiten eines Rechtecks in Bildschirm Einheiten zu konvertieren.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt, das die zu konvertierenden Dialogfeld Koordinaten enthält.

### <a name="remarks"></a>Hinweise

Dialog Feld Einheiten werden in Bezug auf die aktuelle Dialogfeld-Basiseinheit angegeben, die von der durchschnittlichen Breite und Höhe der Zeichen in der Schriftart abgeleitet ist, die für Text im Dialogfeld verwendet wird. Eine horizontale Einheit ist ein vierte der Dialogfeld-Basis breiten Einheit, und eine vertikale Einheit ist ein Achtel der Dialogfeld-Basis Höheneinheit.

Die `GetDialogBaseUnits` Windows-Funktion gibt Größen Informationen für die System Schriftart zurück, Sie können jedoch für jedes Dialogfeld eine andere Schriftart angeben, wenn Sie den DS_SETFONT Stil in der Ressourcen Definitionsdatei verwenden. Die `MapDialogRect` Windows-Funktion verwendet die entsprechende Schriftart für dieses Dialogfeld.

Die `MapDialogRect` Member-Funktion ersetzt die Dialogfeld Einheiten in *lprect* durch Bildschirm Einheiten (Pixel), sodass das Rechteck verwendet werden kann, um ein Dialogfeld zu erstellen oder ein Steuerelement in einem Feld zu positionieren.

##  <a name="nextdlgctrl"></a>CDialog:: nextdlgctrl

Verschiebt den Fokus auf das nächste Steuerelement im Dialogfeld.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Hinweise

Wenn sich der Fokus auf dem letzten Steuerelement im Dialogfeld befindet, wechselt er zum ersten Steuerelement.

##  <a name="oncancel"></a>CDialog:: OnCancel

Das Framework ruft diese Methode auf, wenn der Benutzer in einem modalen oder nicht modalen Dialogfeld auf **Abbrechen** klickt oder die ESC-Taste drückt.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Methode, um Aktionen (z. b. das Wiederherstellen alter Daten) auszuführen, wenn ein Benutzer das Dialogfeld schließt, indem Sie auf **Abbrechen** klicken oder die ESC-Taste Standardmäßig wird ein modales Dialogfeld durch Aufrufen von [EndDialog](#enddialog) geschlossen und bewirkt, dass [DoModal](#domodal) IDCANCEL zurückgibt.

Wenn Sie die Schaltfläche **Abbrechen** in einem nicht modalem Dialogfeld implementieren, müssen Sie die `OnCancel`-Methode überschreiben und [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) darin aufzurufen. Rufen Sie die Basisklassen Methode nicht auf, da Sie `EndDialog`aufruft. Dadurch wird das Dialogfeld unsichtbar, aber nicht zerstört.

> [!NOTE]
>  Diese Methode kann nicht überschrieben werden, wenn Sie ein `CFileDialog` Objekt in einem Programm verwenden, das unter Windows XP kompiliert wird. Weitere Informationen zu `CFileDialog`finden Sie unter [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>CDialog:: OnInitDialog

Diese Methode wird als Reaktion auf die `WM_INITDIALOG` Nachricht aufgerufen.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Gibt an, ob die Anwendung den Eingabefokus auf eines der Steuerelemente im Dialogfeld festgelegt hat. Wenn `OnInitDialog` einen Wert ungleich 0 (null) zurückgibt, legt Windows den Eingabefokus auf den Standard Speicherort fest, das erste Steuerelement im Dialogfeld. Die Anwendung kann 0 nur zurückgeben, wenn Sie den Eingabefokus explizit auf eines der Steuerelemente im Dialogfeld festgelegt hat.

### <a name="remarks"></a>Hinweise

Windows sendet die `WM_INITDIALOG` Meldung während der Aufrufe [Create,](#create) [anateindirect](#createindirect)oder [DoModal](#domodal) an das Dialogfeld, die unmittelbar vor dem Anzeigen des Dialog Felds auftreten.

Überschreiben Sie diese Methode, wenn Sie eine besondere Verarbeitung durchführen möchten, wenn das Dialogfeld initialisiert wird. In der überschriebenen Version wird zuerst die Basisklasse aufgerufen `OnInitDialog`, aber der Rückgabewert wird ignoriert. Sie geben in der Regel `TRUE` von der überschriebenen-Methode zurück.

Windows Ruft die `OnInitDialog`-Funktion mit der standardmäßigen globalen Dialogfeld Prozedur auf, die für alle Microsoft Foundation Class-Bibliothek Dialogfelder verwendet wird. Diese Funktion wird nicht über die Meldungs Zuordnung aufgerufen. Daher benötigen Sie keinen Nachrichten Zuordnungs Eintrag für diese Methode.

> [!NOTE]
> Sie können diese Methode nicht außer Kraft setzen, wenn Sie ein `CFileDialog` Objekt in einem Programm verwenden, das unter Windows Vista oder höher kompiliert wird. Weitere Informationen zu Änderungen an `CFileDialog` unter Windows Vista und höher finden Sie unter [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>CDialog:: OnOK

Wird aufgerufen, wenn der Benutzer auf die Schaltfläche " **OK** " klickt (die Schaltfläche mit der ID IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Methode, um Aktionen auszuführen, wenn die Schaltfläche **OK** aktiviert ist. Wenn das Dialogfeld die automatische Datenvalidierung und den Austausch von Daten enthält, werden die Dialogfeld Daten von der Standard Implementierung dieser Methode überprüft und die entsprechenden Variablen in der Anwendung aktualisiert.

Wenn Sie die Schaltfläche **OK** in einem nicht modalem Dialogfeld implementieren, müssen Sie die `OnOK`-Methode überschreiben und [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) darin aufzurufen. Rufen Sie die Basisklassen Methode nicht auf, da Sie [EndDialog](#enddialog) aufruft. Dadurch wird das Dialogfeld unsichtbar, aber nicht zerstört.

> [!NOTE]
>  Diese Methode kann nicht überschrieben werden, wenn Sie ein `CFileDialog` Objekt in einem Programm verwenden, das unter Windows XP kompiliert wird. Weitere Informationen zu `CFileDialog`finden Sie unter [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>CDialog:: onsetfont

Gibt die Schriftart an, die ein Dialogfeld-Steuerelement beim Zeichnen von Text verwendet.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parameter

*pfont*<br/>
in Gibt einen Zeiger auf die Schriftart an, die als Standard Schriftart für alle Steuerelemente in diesem Dialogfeld verwendet wird.

### <a name="remarks"></a>Hinweise

Im Dialogfeld wird die angegebene Schriftart als Standardwert für alle Steuerelemente verwendet.

Der Dialogfeld-Editor legt die Dialogfeld Schriftart in der Regel als Teil der Dialogfeld Vorlagen Ressource fest.

> [!NOTE]
> Sie können diese Methode nicht außer Kraft setzen, wenn Sie ein `CFileDialog` Objekt in einem Programm verwenden, das unter Windows Vista oder höher kompiliert wird. Weitere Informationen zu Änderungen an `CFileDialog` unter Windows Vista und höher finden Sie unter [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md).

##  <a name="prevdlgctrl"></a>CDialog::P revdlgctrl

Legt den Fokus auf das vorherige Steuerelement im Dialogfeld fest.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Hinweise

Wenn sich der Fokus auf dem ersten Steuerelement im Dialogfeld befindet, wechselt er zum letzten Steuerelement im Feld.

##  <a name="setdefid"></a>CDialog:: setdefid

Ändert das standardmäßige PUSHBUTTON-Steuerelement für ein Dialogfeld.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parameter

*NID*<br/>
Gibt die ID des PUSHBUTTON-Steuer Elements an, das zum Standard wird.

##  <a name="sethelpid"></a>CDialog:: ablokpid

Legt eine kontextabhängige Hilfe-ID für das Dialogfeld fest.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parameter

*nidr*<br/>
Gibt die kontextabhängige Hilfe-ID an.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
