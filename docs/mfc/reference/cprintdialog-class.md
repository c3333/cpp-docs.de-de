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
ms.openlocfilehash: 6490e5488c5ab3b808a02e3608b75541e4063d8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364069"
---
# <a name="cprintdialog-class"></a>CPrintDialog-Klasse

Kapselt die Dienste, die vom allgemeinen Windows-Dialogfeld für das Drucken bereitgestellt werden.

## <a name="syntax"></a>Syntax

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|Erstellt ein `CPrintDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Erstellt einen Druckergerätekontext, ohne das Dialogfeld Drucken anzuzeigen.|
|[CPrintDialog::DoModal](#domodal)|Zeigt das Dialogfeld an und ermöglicht es dem Benutzer, eine Auswahl zu treffen.|
|[CPrintDialog::GetCopies](#getcopies)|Ruft die Anzahl der angeforderten Kopien ab.|
|[CPrintDialog::GetDefaults](#getdefaults)|Ruft Gerätestandards ab, ohne ein Dialogfeld anzuzeigen.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Ruft den Namen des aktuell ausgewählten Druckergeräts ab.|
|[CPrintDialog::GetDevMode](#getdevmode)|Ruft die `DEVMODE` Struktur ab.|
|[CPrintDialog::GetDriverName](#getdrivername)|Ruft den Namen des aktuell ausgewählten Druckertreibers ab.|
|[CPrintDialog::GetFromPage](#getfrompage)|Ruft die Startseite des Druckbereichs ab.|
|[CPrintDialog::GetPortName](#getportname)|Ruft den Namen des aktuell ausgewählten Druckeranschlusses ab.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Ruft ein Handle für den Druckergerätekontext ab.|
|[CPrintDialog::GetToPage](#gettopage)|Ruft die Endseite des Druckbereichs ab.|
|[CPrintDialog::PrintAll](#printall)|Legt fest, ob alle Seiten des Dokuments gedruckt werden sollen.|
|[CPrintDialog::PrintCollate](#printcollate)|Bestimmt, ob gesammelte Kopien angefordert werden.|
|[CPrintDialog::PrintRange](#printrange)|Legt fest, ob nur ein bestimmter Seitenbereich gedruckt werden soll.|
|[CPrintDialog::PrintAuswahl](#printselection)|Legt fest, ob nur die aktuell ausgewählten Elemente gedruckt werden sollen.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Eine Struktur, die `CPrintDialog` zum Anpassen eines Objekts verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Gemeinsame Druckdialogfelder bieten eine einfache Möglichkeit, Druck- und Druckinstallationsdialogfelder in einer Weise zu implementieren, die mit den Windows-Standards übereinstimmt.

> [!NOTE]
> Die `CPrintDialogEx` Klasse kapselt die Dienste, die vom Windows Print-Eigenschaftenblatt bereitgestellt werden. Weitere Informationen finden Sie in der [CPrintDialogEx-Übersicht.](../../mfc/reference/cprintdialogex-class.md)

`CPrintDialog`Die Funktionalität von wird durch die von [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)ersetzt, die Ihnen ein gemeinsames Dialogfeld für die Druckeinrichtung und die Seiteneinrichtung bietet.

Sie können sich auf das Framework verlassen, um viele Aspekte des Druckprozesses für Ihre Anwendung zu behandeln. In diesem Fall zeigt das Framework automatisch das allgemeine Windows-Dialogfeld zum Drucken an. Sie können das Framework auch für Ihre Anwendung drucken lassen, aber das allgemeine Dialogfeld Drucken mit Ihrem eigenen Druckdialogfeld überschreiben. Weitere Informationen zur Verwendung des Frameworks für Druckaufgaben finden Sie im Artikel [Drucken](../../mfc/printing.md).

Wenn Sie möchten, dass Ihre Anwendung den Druck ohne `CPrintDialog` die Beteiligung des Frameworks verarbeitet, können Sie die Klasse "wie besehen" mit dem bereitgestellten Konstruktor verwenden, oder Sie können Ihre eigene Dialogklasse ableiten `CPrintDialog` und einen Konstruktor entsprechend Ihren Anforderungen schreiben. In beiden Fällen verhalten sich diese Dialogfelder wie Standard-MFC-Dialogfelder, da sie von der Klasse `CCommonDialog`abgeleitet sind.

Um ein `CPrintDialog` Objekt zu verwenden, `CPrintDialog` erstellen Sie das Objekt zuerst mit dem Konstruktor. Nachdem das Dialogfeld erstellt wurde, können Sie beliebige Werte in der [m_pd](#m_pd) Struktur festlegen oder ändern, um die Werte der Steuerelemente des Dialogfelds zu initialisieren. Die `m_pd` Struktur ist vom Typ [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga). Weitere Informationen zu dieser Struktur finden Sie im Windows SDK.

Wenn Sie keine eigenen Handles `m_pd` für `hDevMode` `hDevNames` die und-Elemente angeben, `GlobalFree` rufen Sie die Windows-Funktion für diese Handles auf, wenn Sie mit dem Dialogfeld fertig sind. Wenn Sie die von `CWinApp::OnFilePrintSetup`bereitgestellte Print Setup-Implementierung des Frameworks verwenden, müssen Sie diese Handles nicht freizugeben. Die Griffe werden `CWinApp` von `CWinApp`dem Destruktor von beibehalten und im Destruktor freigegeben. Es ist nur notwendig, diese `CPrintDialog` Griffe freizugeben, wenn Sie Stand-Alone verwenden.

Rufen Sie nach dem Initialisieren `DoModal` der Dialogfeldsteuerelemente die Memberfunktion auf, um das Dialogfeld anzuzeigen, und ermöglichen Sie dem Benutzer, Druckoptionen auszuwählen. `DoModal`gibt an, ob der Benutzer die Schaltfläche OK (IDOK) oder Abbrechen (IDCANCEL) ausgewählt hat.

Wenn `DoModal` IDOK zurückgegeben wird, `CPrintDialog`können Sie eine der Memberfunktionen von verwenden, um die vom Benutzer eingegebenen Informationen abzurufen.

Die `CPrintDialog::GetDefaults` Memberfunktion ist nützlich, um die aktuellen Druckerstandards abzurufen, ohne ein Dialogfeld anzuzeigen. Diese Memberfunktion erfordert keine Benutzerinteraktion.

Sie können die `CommDlgExtendedError` Windows-Funktion verwenden, um zu ermitteln, ob während der Initialisierung des Dialogfelds ein Fehler aufgetreten ist, und um mehr über den Fehler zu erfahren. Weitere Informationen zu dieser Funktion finden Sie im Windows SDK.

`CPrintDialog`sich auf das COMMDLG verlässt. DLL-Datei, die mit Windows-Versionen 3.1 und höher ausgeliefert wird.

Um das Dialogfeld anzupassen, leiten `CPrintDialog`Sie eine Klasse von ab, stellen Sie eine benutzerdefinierte Dialogfeldvorlage bereit, und fügen Sie eine Meldungszuordnung hinzu, um die Benachrichtigungen aus den erweiterten Steuerelementen zu verarbeiten. Alle nicht verarbeiteten Nachrichten sollten an die Basisklasse weitergegeben werden. Das Anpassen der Hook-Funktion ist nicht erforderlich.

Um dieselbe Nachricht unterschiedlich zu verarbeiten, je nachdem, ob das Dialogfeld Druck oder Druckeinrichtung ist, müssen Sie für jedes Dialogfeld eine Klasse ableiten. Sie müssen auch die `AttachOnSetup` Windows-Funktion überschreiben, die die Erstellung eines neuen Dialogfelds verarbeitet, wenn die Schaltfläche Setup drucken in einem Dialogfeld Drucken ausgewählt ist.

Weitere Informationen zur `CPrintDialog`Verwendung finden Sie unter [Allgemeine Dialogklassen](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdlgs.h

## <a name="cprintdialogcprintdialog"></a><a name="cprintdialog"></a>CPrintDialog::CPrintDialog

Erstellt entweder ein Windows Print- oder Print Setup-Dialogobjekt.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*bPrintSetupOnly*<br/>
Gibt an, ob das standardmäßige Windows Print-Dialogfeld oder das Dialogfeld Druckeinrichtung angezeigt wird. Legen Sie diesen Parameter auf TRUE fest, um das standardmäßige Windows-Druckinstallationsdialogfeld anzuzeigen. Legen Sie false fest, um das Dialogfeld Windows Print anzuzeigen. Wenn *bPrintSetupOnly* FALSE ist, wird im Dialogfeld Drucken weiterhin eine Schaltfläche für die Druckeinrichtung angezeigt.

*dwFlags*<br/>
Ein oder mehrere Flags können Sie verwenden, um die Einstellungen des Dialogfelds anzupassen, kombiniert mit dem bitweisen ODER-Operator. Das PD_ALLPAGES-Flag legt z. B. den Standarddruckbereich auf alle Seiten des Dokuments fest. Weitere Informationen zu diesen Flags finden Sie in der [PRINTDLG-Struktur](/windows/win32/api/commdlg/ns-commdlg-printdlga) im Windows SDK.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete oder Besitzerfenster des Dialogfelds.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion erstellt nur das Objekt. Verwenden `DoModal` Sie die Memberfunktion, um das Dialogfeld anzuzeigen.

Beachten Sie, dass beim Aufrufen des Konstruktors mit *bPrintSetupOnly,* das auf FALSE festgelegt ist, das PD_RETURNDC-Flag automatisch verwendet wird. Nach `DoModal`dem `GetDefaults`Aufruf `GetPrinterDC`von , oder wird `m_pd.hDC`ein Drucker-DC in zurückgegeben. Dieser Domänencontroller muss mit einem Aufruf von [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) durch den Aufruf von `CPrintDialog`freigegeben werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

## <a name="cprintdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC

Erstellt einen Druckergerätekontext (DC) aus den Strukturen [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) und [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Rückgabewert

Behandeln Sie den neu erstellten Druckergerätekontext.

### <a name="remarks"></a>Bemerkungen

Dieser Domänencontroller wird als aktueller Drucker-DC angenommen, und alle anderen zuvor erhaltenen Drucker-DCs müssen vom Benutzer gelöscht werden. Diese Funktion kann aufgerufen und der resultierende Domänencontroller verwendet werden, ohne jemals das Dialogfeld Drucken anzuzeigen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

## <a name="cprintdialogdomodal"></a><a name="domodal"></a>CPrintDialog::DoModal

Zeigt das allgemeine Windows-Druckdialogfeld an und ermöglicht es dem Benutzer, verschiedene Druckoptionen auszuwählen, z. B. die Anzahl der Kopien, den Seitenbereich und die Frage, ob Kopien sortiert werden sollen.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

IDOK oder IDCANCEL. Wenn IDCANCEL zurückgegeben wird, rufen Sie die Windows [CommDlgExtendedError-Funktion](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) auf, um zu ermitteln, ob ein Fehler aufgetreten ist.

IDOK und IDCANCEL sind Konstanten, die angeben, ob der Benutzer die Schaltfläche OK oder Abbrechen ausgewählt hat.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Druckdialogoptionen initialisieren möchten, indem Sie Elemente `m_pd` `DoModal`der Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

Nach `DoModal`dem Aufruf können Sie andere Memberfunktionen aufrufen, um die Einstellungen oder Informationen, die der Benutzer in das Dialogfeld eingibt, abzurufen.

Beachten Sie, dass beim Aufrufen des Konstruktors mit *bPrintSetupOnly,* das auf FALSE festgelegt ist, das PD_RETURNDC-Flag automatisch verwendet wird. Nach `DoModal`dem `GetDefaults`Aufruf `GetPrinterDC`von , oder wird `m_pd.hDC`ein Drucker-DC in zurückgegeben. Dieser Domänencontroller muss mit einem Aufruf von [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) durch den Aufruf von `CPrintDialog`freigegeben werden.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::CreatePrinterDC](#createprinterdc).

## <a name="cprintdialoggetcopies"></a><a name="getcopies"></a>CPrintDialog::GetCopies

Ruft die Anzahl der angeforderten Kopien ab.

```
int GetCopies() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der angeforderten Kopien.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um die Anzahl der angeforderten Kopien abzurufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdefaults"></a><a name="getdefaults"></a>CPrintDialog::GetDefaults

Ruft die Gerätestandards des Standarddruckers ab, ohne ein Dialogfeld anzuzeigen.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die abgerufenen Werte `m_pd` werden in der Struktur platziert.

In einigen Fällen ruft ein Aufruf dieser Funktion `CPrintDialog` den [Konstruktor](#cprintdialog) für auf, wobei *bPrintSetupOnly* auf FALSE festgelegt ist. In diesen Fällen werden `hDevNames` automatisch `hDevMode` ein Drucker-DC `m_pd` und und (zwei Handles im Datenmember) zugeordnet.

Wenn der Konstruktor `CPrintDialog` für aufgerufen wurde, wobei *bPrintSetupOnly* auf `hDevNames` `hDevMode` FALSE `m_pd.hDevNames` gesetzt `m_pd.hDevMode`ist, gibt diese Funktion nicht nur `m_pd.hDC`den Aufrufer zurück und ) sondern gibt auch einen Drucker-DC in zurück. Es liegt in der Verantwortung des Aufrufers, den Drucker-DC zu löschen und die `CPrintDialog` Windows [GlobalFree-Funktion](/windows/win32/api/winbase/nf-winbase-globalfree) auf den Handles aufzurufen, wenn Sie mit dem Objekt fertig sind.

### <a name="example"></a>Beispiel

Dieses Codefragment ruft den Gerätekontext des Standarddruckers ab und meldet dem Benutzer die Auflösung des Druckers in Punkten pro Zoll. (Dieses Attribut der Druckerfunktionen wird häufig als DPI bezeichnet.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

## <a name="cprintdialoggetdevicename"></a><a name="getdevicename"></a>CPrintDialog::GetDeviceName

Ruft den Namen des aktuell ausgewählten Druckergeräts ab.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des aktuell ausgewählten Druckers.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, nachdem Sie [DoModal](#domodal) aufgerufen haben, um den Namen des aktuell ausgewählten Druckers abzurufen, oder nachdem Sie [GetDefaults](#getdefaults) aufgerufen haben, um die aktuellen Gerätestandards des Standarddruckers abzurufen. Verwenden Sie einen `CString` Zeiger auf `GetDeviceName` das Objekt, das als Wert von `lpszDeviceName` in einem Aufruf von [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)zurückgegeben wird.

### <a name="example"></a>Beispiel

Dieses Codefragment zeigt den Standarddruckernamen des Benutzers und den Anschluss, mit dem er verbunden ist, sowie den vom Drucker verwendeten Spoolernamen an. Der Code zeigt möglicherweise ein Meldungsfeld mit der Meldung "Ihr Standarddrucker ist HP LaserJet IIIP auf \\der Website "Server" mit winspool."

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

## <a name="cprintdialoggetdevmode"></a><a name="getdevmode"></a>CPrintDialog::GetDevMode

Ruft die `DEVMODE` Struktur ab.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Rückgabewert

Die [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) DEVMODE-Datenstruktur, die Informationen zur Geräteinitialisierung und Umgebung eines Druckertreibers enthält. Sie müssen den von dieser Struktur entnommenen Speicher mit der Windows [GlobalUnlock-Funktion](/windows/win32/api/winbase/nf-winbase-globalunlock) entsperren, die im Windows SDK beschrieben wird.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, nachdem Sie [DoModal](#domodal) oder [GetDefaults](#getdefaults) aufgerufen haben, um Informationen über das Druckgerät abzurufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdrivername"></a><a name="getdrivername"></a>CPrintDialog::GetDriverName

Ruft den Namen des aktuell ausgewählten Druckertreibers ab.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine `CString` Angabe des systemdefinierten Treibernamens.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, nachdem Sie [DoModal](#domodal) oder [GetDefaults](#getdefaults) aufgerufen haben, um den Namen des systemdefinierten Druckergerätetreibers abzurufen. Verwenden Sie einen `CString` Zeiger auf `GetDriverName` das Objekt, das als Wert von `lpszDriverName` in einem Aufruf von [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)zurückgegeben wird.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::GetDeviceName](#getdevicename).

## <a name="cprintdialoggetfrompage"></a><a name="getfrompage"></a>CPrintDialog::GetFromPage

Ruft die Startseite des Druckbereichs ab.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Rückgabewert

Die Startseitenzahl im Bereich der zu druckenden Seiten.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um die Startseitenzahl im Bereich der zu druckenden Seiten abzurufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialoggetportname"></a><a name="getportname"></a>CPrintDialog::GetPortName

Ruft den Namen des aktuell ausgewählten Druckeranschlusses ab.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des aktuell ausgewählten Druckeranschlusses.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, nachdem Sie [DoModal](#domodal) oder [GetDefaults](#getdefaults) aufgerufen haben, um den Namen des aktuell ausgewählten Druckeranschlusses abzurufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::GetDeviceName](#getdevicename).

## <a name="cprintdialoggetprinterdc"></a><a name="getprinterdc"></a>CPrintDialog::GetPrinterDC

Ruft ein Handle für den Druckergerätekontext ab.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für den Druckergerätekontext, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn der Parameter *bPrintSetupOnly* des `CPrintDialog` Konstruktors FALSE war (was darauf `GetPrinterDC` hinweist, dass das Dialogfeld Drucken angezeigt wird), gibt er einen Handle an den Druckergerätekontext zurück. Sie müssen die Windows [DeleteDC-Funktion](/windows/win32/api/wingdi/nf-wingdi-deletedc) aufrufen, um den Gerätekontext zu löschen, wenn Sie damit fertig sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

## <a name="cprintdialoggettopage"></a><a name="gettopage"></a>CPrintDialog::GetToPage

Ruft die Endseite des Druckbereichs ab.

```
int GetToPage() const;
```

### <a name="return-value"></a>Rückgabewert

Die Endseitenzahl im Bereich der zu druckenden Seiten.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um die Endseitennummer im Bereich der zu druckenden Seiten abzurufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialogm_pd"></a><a name="m_pd"></a>CPrintDialog::m_pd

Eine Struktur, deren Member die Eigenschaften des Dialogobjekts speichern.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Bemerkungen

Nach dem `CPrintDialog` Erstellen eines `m_pd` Objekts können Sie verschiedene Aspekte des Dialogfelds festlegen, bevor Sie die [DoModal-Memberfunktion](#domodal) aufrufen. Weitere Informationen zur `m_pd` Struktur finden Sie unter [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) im Windows SDK.

Wenn Sie `m_pd` das Datenelement direkt ändern, überschreiben Sie jedes Standardverhalten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

## <a name="cprintdialogprintall"></a><a name="printall"></a>CPrintDialog::PrintAll

Legt fest, ob alle Seiten des Dokuments gedruckt werden sollen.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn alle Seiten im Dokument gedruckt werden sollen; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um zu bestimmen, ob alle Seiten im Dokument gedruckt werden sollen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialogprintcollate"></a><a name="printcollate"></a>CPrintDialog::PrintCollate

Bestimmt, ob gesammelte Kopien angefordert werden.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn der Benutzer das Kontrollkästchen Collate im Dialogfeld aktiviert. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um zu bestimmen, ob der Drucker alle gedruckten Kopien des Dokuments zusammenstellen soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

## <a name="cprintdialogprintrange"></a><a name="printrange"></a>CPrintDialog::PrintRange

Legt fest, ob nur ein bestimmter Seitenbereich gedruckt werden soll.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn nur ein Seitenbereich im Dokument gedruckt werden soll; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um zu bestimmen, ob nur ein Bereich von Seiten im Dokument gedruckt werden soll.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialogprintselection"></a><a name="printselection"></a>CPrintDialog::PrintAuswahl

Legt fest, ob nur die aktuell ausgewählten Elemente gedruckt werden sollen.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn nur die ausgewählten Artikel gedruckt werden sollen; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um zu bestimmen, ob nur die aktuell ausgewählten Elemente gedruckt werden sollen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPrintDialog::m_pd](#m_pd).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog-Klasse](../../mfc/reference/ccommondialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo-Struktur](../../mfc/reference/cprintinfo-structure.md)
