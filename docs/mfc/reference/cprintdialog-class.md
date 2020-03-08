---
title: CPrintDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: ccc673d665d6d5beb92f398b21e6ffd313a58fc9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855571"
---
# <a name="cprintdialog-class"></a>CPrintDialog-Klasse

Kapselt die Dienste, die vom allgemeinen Windows-Dialogfeld für das Drucken bereitgestellt werden.

## <a name="syntax"></a>Syntax

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintDialog:: CPrintDialog](#cprintdialog)|Erstellt ein `CPrintDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintDialog:: kreateprinterdc](#createprinterdc)|Erstellt einen Drucker Gerätekontext, ohne das Dialogfeld Drucken anzuzeigen.|
|[CPrintDialog::D omodal](#domodal)|Zeigt das Dialogfeld an und ermöglicht es dem Benutzer, eine Auswahl vorzunehmen.|
|[CPrintDialog:: getkopien](#getcopies)|Ruft die Anzahl der angeforderten Kopien ab.|
|[CPrintDialog:: getdefaults](#getdefaults)|Ruft Geräte Standardwerte ab, ohne ein Dialogfeld anzuzeigen.|
|[CPrintDialog:: GetDeviceName](#getdevicename)|Ruft den Namen des aktuell ausgewählten Drucker Geräts ab.|
|[CPrintDialog:: getdevmode](#getdevmode)|Ruft die `DEVMODE` Struktur ab.|
|[CPrintDialog:: getDriverName](#getdrivername)|Ruft den Namen des aktuell ausgewählten Druckertreibers ab.|
|[CPrintDialog:: GetFromPage](#getfrompage)|Ruft die Startseite des Druck Bereichs ab.|
|[CPrintDialog:: getportname](#getportname)|Ruft den Namen des aktuell ausgewählten Drucker Ports ab.|
|[CPrintDialog:: getPrinterDC](#getprinterdc)|Ruft ein Handle für den Drucker Gerätekontext ab.|
|[CPrintDialog:: GetToPage](#gettopage)|Ruft die Endseite des Druck Bereichs ab.|
|[CPrintDialog::P rintall](#printall)|Bestimmt, ob alle Seiten des Dokuments gedruckt werden.|
|[CPrintDialog::P rintcollate](#printcollate)|Bestimmt, ob sortierte Kopien angefordert werden.|
|[CPrintDialog::P rintrange](#printrange)|Bestimmt, ob nur ein angegebener Seitenbereich gedruckt werden soll.|
|[CPrintDialog::P rintselection](#printselection)|Bestimmt, ob nur die aktuell ausgewählten Elemente gedruckt werden.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintDialog:: m_pd](#m_pd)|Eine-Struktur, die verwendet wird, um ein `CPrintDialog` Objekt anzupassen.|

## <a name="remarks"></a>Bemerkungen

Allgemeine Druck Dialogfelder bieten eine einfache Möglichkeit, Druck-und Druck Setup Dialogfelder auf eine Weise zu implementieren, die mit Windows-Standards konsistent ist.

> [!NOTE]
>  Die `CPrintDialogEx`-Klasse kapselt die Dienste, die vom Windows-Druckeigenschaften Blatt bereitgestellt werden. Weitere Informationen finden Sie in der Übersicht über [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) .

die Funktionalität von `CPrintDialog`wird durch die von [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)ersetzt, die so konzipiert ist, dass Sie ein gemeinsames Dialogfeld für die Druck Einrichtung und das Einrichten der Seite bereitstellen.

Sie können sich auf das Framework verlassen, um viele Aspekte des Druckprozesses für Ihre Anwendung zu bewältigen. In diesem Fall zeigt das Framework automatisch das Windows-Dialogfeld "Allgemein" für den Druck an. Sie können auch das Framework-Handle für die Anwendung drucken lassen, aber das Dialogfeld "allgemeiner Druck" mit dem Dialogfeld "Drucken" außer Kraft setzen. Weitere Informationen zum Verwenden des Frameworks zum Verarbeiten von Druckaufgaben finden Sie im Artikel [Drucken](../../mfc/printing.md).

Wenn Sie möchten, dass Ihre Anwendung den Druck ohne die Einbindung des Frameworks behandelt, können Sie die `CPrintDialog`-Klasse mit dem bereitgestellten Konstruktor "unverändert" verwenden, oder Sie können eine eigene Dialog Klasse von `CPrintDialog` ableiten und einen Konstruktor für Ihre Bedürfnisse schreiben. In beiden Fällen verhalten sich diese Dialogfelder wie Standard-MFC-Dialogfelder, da Sie von Klassen `CCommonDialog`abgeleitet werden.

Um ein `CPrintDialog` Objekt zu verwenden, erstellen Sie zunächst das-Objekt mithilfe des `CPrintDialog`-Konstruktors. Nachdem das Dialogfeld erstellt wurde, können Sie alle Werte in der [m_pd](#m_pd) -Struktur festlegen oder ändern, um die Werte der Steuerelemente des Dialog Felds zu initialisieren. Die `m_pd` Struktur ist vom Typ [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga). Weitere Informationen zu dieser Struktur finden Sie in der Windows SDK.

Wenn Sie in `m_pd` keine eigenen Handles für die `hDevMode` und `hDevNames` Member bereitstellen, stellen Sie sicher, dass Sie die Windows-Funktion `GlobalFree` für diese Handles aufzurufen, wenn Sie das Dialogfeld verwenden. Wenn Sie die Druck Setup Implementierung des Frameworks verwenden, die von `CWinApp::OnFilePrintSetup`bereitgestellt wird, müssen Sie diese Handles nicht freigeben. Die Handles werden von `CWinApp` verwaltet und im Dekonstruktor `CWinApp`freigegeben. Es ist nur erforderlich, diese Handles freizugeben, wenn Sie `CPrintDialog` eigenständige verwenden.

Nachdem Sie die Dialogfeld Steuerelemente initialisiert haben, können Sie die `DoModal` Member-Funktion aufrufen, um das Dialogfeld anzuzeigen und dem Benutzer die Auswahl von Druckoptionen zu ermöglichen. `DoModal` gibt zurück, ob der Benutzer die Schaltfläche OK (IDOK) oder Abbrechen (IDCANCEL) ausgewählt hat.

Wenn `DoModal` IDOK zurückgibt, können Sie eine der Member-Funktionen von `CPrintDialog`verwenden, um die vom Benutzer eingegebenen Informationen abzurufen.

Die `CPrintDialog::GetDefaults` Member-Funktion ist nützlich, um die aktuellen Drucker Standardwerte abzurufen, ohne ein Dialogfeld anzuzeigen. Diese Member-Funktion erfordert keine Benutzerinteraktion.

Sie können die Windows `CommDlgExtendedError`-Funktion verwenden, um zu bestimmen, ob ein Fehler während der Initialisierung des Dialog Felds aufgetreten ist, und um weitere Informationen zum Fehler zu erhalten. Weitere Informationen zu dieser Funktion finden Sie in der Windows SDK.

`CPrintDialog` auf der Kommas basiert. DLL-Datei, die in der Windows-Version 3,1 und höher enthalten ist.

Zum Anpassen des Dialog Felds leiten Sie eine Klasse von `CPrintDialog`ab, geben eine benutzerdefinierte Dialogfeld Vorlage an und fügen eine Meldungs Zuordnung hinzu, um die Benachrichtigungs Meldungen der erweiterten Steuerelemente zu verarbeiten. Alle nicht verarbeiteten Nachrichten sollten an die Basisklasse weitergegeben werden. Das Anpassen der Hook-Funktion ist nicht erforderlich.

Sie müssen für jedes Dialogfeld eine Klasse ableiten, um die gleiche Nachricht in Abhängigkeit davon zu unterscheiden, ob es sich bei dem Dialogfeld um eine Druck-oder Druck Installation handelt. Sie müssen auch die Windows-`AttachOnSetup`-Funktion überschreiben, die die Erstellung eines neuen Dialog Felds behandelt, wenn die Schaltfläche Druck Setup innerhalb eines Druck Dialogfelds ausgewählt wird.

Weitere Informationen zur Verwendung von `CPrintDialog`finden Sie unter [Allgemeine Dialog Klassen](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Ccommondialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdlgs. h

##  <a name="cprintdialog"></a>CPrintDialog:: CPrintDialog

Erstellt entweder ein Windows-Druck-oder Druck Setup Dialogfeld Objekt.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*bprintsetuponly*<br/>
Gibt an, ob das Dialogfeld Windows-Standarddruck oder Druck Setup angezeigt wird. Legen Sie diesen Parameter auf "true" fest, um das Standard Dialogfeld Windows-Druck Setup anzuzeigen. Legen Sie diese Einstellung auf false fest, um das Dialogfeld Windows-Druck anzuzeigen. Wenn *bprintsetuponly* auf false festgelegt ist, wird im Dialogfeld Drucken weiterhin das Optionsfeld Druck Setup angezeigt.

*dwFlags*<br/>
Ein oder mehrere Flags, die Sie verwenden können, um die Einstellungen des Dialog Felds mithilfe des bitweisen OR-Operators zu ändern. Beispielsweise legt das Flag PD_ALLPAGES den Standarddruck Bereich auf alle Seiten des Dokuments fest. Weitere Informationen zu diesen Flags finden Sie in der [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) -Struktur im Windows SDK.

*pparser*<br/>
Ein Zeiger auf das übergeordnete oder Besitzer Fenster des Dialog Felds.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion erstellt nur das-Objekt. Verwenden Sie die `DoModal` Member-Funktion, um das Dialogfeld anzuzeigen.

Beachten Sie Folgendes: Wenn Sie den Konstruktor aufrufen, bei dem *bprintsetuponly* auf false festgelegt ist, wird das PD_RETURNDC-Flag automatisch verwendet. Nachdem Sie `DoModal`, `GetDefaults`oder `GetPrinterDC`aufgerufen haben, wird ein Drucker-DC in `m_pd.hDC`zurückgegeben. Dieser Domänen Controller muss durch einen Aufruf von [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) vom Aufrufer von `CPrintDialog`freigegeben werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>CPrintDialog:: kreateprinterdc

Erstellt einen Drucker Gerätekontext (DC) aus den [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) -und [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) -Strukturen.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Rückgabewert

Handle für den neu erstellten Drucker Gerätekontext.

### <a name="remarks"></a>Bemerkungen

Es wird davon ausgegangen, dass es sich bei diesem DC um den aktuellen Drucker-DC handelt, und alle anderen zuvor erhaltenen Drucker-DCS müssen vom Benutzer gelöscht werden. Diese Funktion kann aufgerufen werden, und der resultierende DC wird verwendet, ohne dass das Dialogfeld "Drucken" angezeigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>CPrintDialog::D omodal

Zeigt das Dialogfeld "allgemeiner Windows-Druck" an und ermöglicht dem Benutzer die Auswahl verschiedener Druckoptionen, wie z. b. die Anzahl von Kopien, den Seitenbereich und ob Kopien sortiert werden sollen.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

IDOK oder IDCANCEL. Wenn IDCANCEL zurückgegeben wird, rufen Sie die Windows-Funktion [commdlgextendederror](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) auf, um zu bestimmen, ob ein Fehler aufgetreten ist.

IDOK und IDCANCEL sind Konstanten, die angeben, ob der Benutzer die Schaltfläche OK oder Abbrechen ausgewählt hat.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Druck Dialogfeld Optionen durch Festlegen der Elemente der `m_pd` Struktur initialisieren möchten, sollten Sie dies vor dem Aufrufen von `DoModal`tun, nachdem das Dialogfeld Objekt erstellt wurde.

Nachdem Sie `DoModal`aufgerufen haben, können Sie andere Element Funktionen aufrufen, um die Einstellungen oder die Eingabeinformationen vom Benutzer in das Dialogfeld abzurufen.

Beachten Sie Folgendes: Wenn Sie den Konstruktor aufrufen, bei dem *bprintsetuponly* auf false festgelegt ist, wird das PD_RETURNDC-Flag automatisch verwendet. Nachdem Sie `DoModal`, `GetDefaults`oder `GetPrinterDC`aufgerufen haben, wird ein Drucker-DC in `m_pd.hDC`zurückgegeben. Dieser Domänen Controller muss durch einen Aufruf von [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) vom Aufrufer von `CPrintDialog`freigegeben werden.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog:: kreateprinterdc](#createprinterdc).

##  <a name="getcopies"></a>CPrintDialog:: getkopien

Ruft die Anzahl der angeforderten Kopien ab.

```
int GetCopies() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der angeforderten Kopien.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, nachdem Sie `DoModal` aufgerufen haben, um die Anzahl der angeforderten Kopien abzurufen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdefaults"></a>CPrintDialog:: getdefaults

Ruft die Geräte Standardwerte des Standard Druckers ab, ohne ein Dialogfeld anzuzeigen.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Funktion erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die abgerufenen Werte werden in der `m_pd` Struktur abgelegt.

In einigen Fällen ruft ein Aufrufen dieser Funktion den [Konstruktor](#cprintdialog) für `CPrintDialog` auf, wobei *bprintsetuponly* auf false festgelegt ist. In diesen Fällen werden ein Drucker-DC und `hDevNames` und `hDevMode` (zwei Handles, die sich im `m_pd` Datenmember befinden) automatisch zugeordnet.

Wenn der Konstruktor für `CPrintDialog` mit *bprintsetuponly* auf false festgelegt wurde, gibt diese Funktion nicht nur `hDevNames` und `hDevMode` in `m_pd.hDevNames` und `m_pd.hDevMode`) dem Aufrufer zurück, sondern gibt auch einen Drucker-DC in `m_pd.hDC`zurück. Es liegt in der Verantwortung des Aufrufers, den Drucker-DC zu löschen und die Windows [Global Free](/windows/win32/api/winbase/nf-winbase-globalfree) -Funktion für die Handles aufzurufen, wenn Sie mit dem `CPrintDialog` Objekt fertig sind.

### <a name="example"></a>Beispiel

Dieses Code Fragment Ruft den Gerätekontext des Standard Druckers ab und meldet dem Benutzer die Auflösung des Druckers in dpi (Punkte pro Zoll). (Dieses Attribut der Funktionen des Druckers wird häufig als dpi bezeichnet.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>CPrintDialog:: GetDeviceName

Ruft den Namen des aktuell ausgewählten Drucker Geräts ab.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des aktuell ausgewählten Druckers.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion nach dem Aufrufen von [DoModal](#domodal) auf, um den Namen des aktuell ausgewählten Druckers abzurufen, oder nachdem Sie [getdefaults](#getdefaults) aufgerufen haben, um die aktuellen Geräte Standardwerte des Standard Druckers abzurufen. Verwenden Sie einen Zeiger auf das `CString` Objekt, das von `GetDeviceName` als Wert von `lpszDeviceName` in einem Aufrufen von [CDC:: | atedc](../../mfc/reference/cdc-class.md#createdc)zurückgegeben wurde.

### <a name="example"></a>Beispiel

Dieses Code Fragment zeigt den Standarddrucker Namen des Benutzers und den Port an, mit dem er verbunden ist, zusammen mit dem spoolernamen, den der Drucker verwendet. Im Code wird möglicherweise ein Meldungs Feld mit dem Hinweis angezeigt, dass der Standarddrucker HP LaserJet IIIP auf \\\server\freigabe mithilfe von winspool ist, z. b.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>CPrintDialog:: getdevmode

Ruft die `DEVMODE` Struktur ab.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Rückgabewert

Die [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) -Datenstruktur, die Informationen über die Geräte Initialisierung und die Umgebung eines Druck Treibers enthält. Sie müssen den von dieser Struktur erstellten Arbeitsspeicher mit der Funktion Windows [globalunlock](/windows/win32/api/winbase/nf-winbase-globalunlock) entsperren, die im Windows SDK beschrieben wird.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion nach dem Aufrufen von " [DoModal](#domodal) " oder " [getdefaults](#getdefaults) " auf, um Informationen zum Druck Gerät abzurufen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdrivername"></a>CPrintDialog:: getDriverName

Ruft den Namen des aktuell ausgewählten Druckertreibers ab.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `CString` der den Namen des System definierten Treibers angibt.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion nach dem Aufrufen von " [DoModal](#domodal) " oder " [getdefaults](#getdefaults) " auf, um den Namen des System definierten Drucker-Gerätetreibers abzurufen. Verwenden Sie einen Zeiger auf das `CString` Objekt, das von `GetDriverName` als Wert von `lpszDriverName` in einem Aufrufen von [CDC:: | atedc](../../mfc/reference/cdc-class.md#createdc)zurückgegeben wurde.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog:: GetDeviceName](#getdevicename).

##  <a name="getfrompage"></a>CPrintDialog:: GetFromPage

Ruft die Startseite des Druck Bereichs ab.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Rückgabewert

Die Nummer der Startseite im Bereich der zu druckenden Seiten.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, nachdem Sie `DoModal` aufgerufen haben, um die Anfangs Seitenzahl im Bereich der zu druckenden Seiten abzurufen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog:: m_pd](#m_pd).

##  <a name="getportname"></a>CPrintDialog:: getportname

Ruft den Namen des aktuell ausgewählten Drucker Ports ab.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des aktuell ausgewählten Drucker Anschlusses.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion nach dem Aufrufen von " [DoModal](#domodal) " oder " [getdefaults](#getdefaults) " auf, um den Namen des aktuell ausgewählten Drucker Ports abzurufen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog:: GetDeviceName](#getdevicename).

##  <a name="getprinterdc"></a>CPrintDialog:: getPrinterDC

Ruft ein Handle für den Drucker Gerätekontext ab.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für den Drucker Gerätekontext, wenn der Vorgang erfolgreich war. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn der *bprintsetuponly* -Parameter des `CPrintDialog` Konstruktors false war (was anzeigt, dass das Dialogfeld "Drucken" angezeigt wird), gibt `GetPrinterDC` ein Handle für den Drucker Gerätekontext zurück. Sie müssen die Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) -Funktion aufrufen, um den Gerätekontext zu löschen, wenn Sie ihn nicht mehr benötigen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>CPrintDialog:: GetToPage

Ruft die Endseite des Druck Bereichs ab.

```
int GetToPage() const;
```

### <a name="return-value"></a>Rückgabewert

Die Endseiten Zahl im Seitenbereich, der gedruckt werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, nachdem Sie `DoModal` aufgerufen haben, um die Endseiten Zahl im Bereich der zu druckenden Seiten abzurufen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog:: m_pd](#m_pd).

##  <a name="m_pd"></a>CPrintDialog:: m_pd

Eine-Struktur, deren Elemente die Merkmale des Dialog Objekts speichern.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Bemerkungen

Nachdem Sie ein `CPrintDialog` Objekt erstellt haben, können Sie mit `m_pd` verschiedene Aspekte des Dialog Felds festlegen, bevor Sie die [DoModal](#domodal) -Member-Funktion aufrufen. Weitere Informationen zur `m_pd` Struktur finden Sie unter [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) in der Windows SDK.

Wenn Sie die `m_pd` Datenmember direkt ändern, überschreiben Sie jedes Standardverhalten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>CPrintDialog::P rintall

Bestimmt, ob alle Seiten des Dokuments gedruckt werden.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn alle Seiten im Dokument gedruckt werden sollen. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion nach dem Aufrufen von `DoModal` auf, um zu bestimmen, ob alle Seiten im Dokument gedruckt werden sollen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog:: m_pd](#m_pd).

##  <a name="printcollate"></a>CPrintDialog::P rintcollate

Bestimmt, ob sortierte Kopien angefordert werden.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn der Benutzer im Dialogfeld das Kontrollkästchen COLLATE auswählt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion nach dem Aufrufen von `DoModal` auf, um zu bestimmen, ob der Drucker alle gedruckten Kopien des Dokuments anordnen soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>CPrintDialog::P rintrange

Bestimmt, ob nur ein angegebener Seitenbereich gedruckt werden soll.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn nur ein Seitenbereich im Dokument gedruckt werden soll. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, nachdem Sie `DoModal` aufgerufen haben, um zu bestimmen, ob nur ein Bereich von Seiten im Dokument gedruckt werden soll.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog:: m_pd](#m_pd).

##  <a name="printselection"></a>CPrintDialog::P rintselection

Bestimmt, ob nur die aktuell ausgewählten Elemente gedruckt werden.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn nur die ausgewählten Elemente gedruckt werden sollen. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion nach dem Aufrufen von `DoModal` auf, um zu bestimmen, ob nur die aktuell ausgewählten Elemente gedruckt werden sollen

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPrintDialog:: m_pd](#m_pd).

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog-Klasse](../../mfc/reference/ccommondialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo-Struktur](../../mfc/reference/cprintinfo-structure.md)
