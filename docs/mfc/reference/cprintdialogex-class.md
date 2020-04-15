---
title: CPrintDialogEx-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPrintDialogEx
- AFXDLGS/CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CreatePrinterDC
- AFXDLGS/CPrintDialogEx::DoModal
- AFXDLGS/CPrintDialogEx::GetCopies
- AFXDLGS/CPrintDialogEx::GetDefaults
- AFXDLGS/CPrintDialogEx::GetDeviceName
- AFXDLGS/CPrintDialogEx::GetDevMode
- AFXDLGS/CPrintDialogEx::GetDriverName
- AFXDLGS/CPrintDialogEx::GetPortName
- AFXDLGS/CPrintDialogEx::GetPrinterDC
- AFXDLGS/CPrintDialogEx::PrintAll
- AFXDLGS/CPrintDialogEx::PrintCollate
- AFXDLGS/CPrintDialogEx::PrintCurrentPage
- AFXDLGS/CPrintDialogEx::PrintRange
- AFXDLGS/CPrintDialogEx::PrintSelection
- AFXDLGS/CPrintDialogEx::m_pdex
helpviewer_keywords:
- CPrintDialogEx [MFC], CPrintDialogEx
- CPrintDialogEx [MFC], CreatePrinterDC
- CPrintDialogEx [MFC], DoModal
- CPrintDialogEx [MFC], GetCopies
- CPrintDialogEx [MFC], GetDefaults
- CPrintDialogEx [MFC], GetDeviceName
- CPrintDialogEx [MFC], GetDevMode
- CPrintDialogEx [MFC], GetDriverName
- CPrintDialogEx [MFC], GetPortName
- CPrintDialogEx [MFC], GetPrinterDC
- CPrintDialogEx [MFC], PrintAll
- CPrintDialogEx [MFC], PrintCollate
- CPrintDialogEx [MFC], PrintCurrentPage
- CPrintDialogEx [MFC], PrintRange
- CPrintDialogEx [MFC], PrintSelection
- CPrintDialogEx [MFC], m_pdex
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
ms.openlocfilehash: 52e992cf021a592198daeddf0a4321fcea487f72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364041"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx-Klasse

Kapselt die Vom Windows Print-Eigenschaftenblatt bereitgestellten Dienste.

## <a name="syntax"></a>Syntax

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|Erstellt ein `CPrintDialogEx`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Erstellt einen Druckergerätekontext, ohne das Dialogfeld Drucken anzuzeigen.|
|[CPrintDialogEx::DoModal](#domodal)|Zeigt das Dialogfeld an und ermöglicht es dem Benutzer, eine Auswahl zu treffen.|
|[CPrintDialogEx::GetCopies](#getcopies)|Ruft die Anzahl der angeforderten Kopien ab.|
|[CPrintDialogEx::GetDefaults](#getdefaults)|Ruft Gerätestandards ab, ohne ein Dialogfeld anzuzeigen.|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Ruft den Namen des aktuell ausgewählten Druckergeräts ab.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|Ruft die `DEVMODE` Struktur ab.|
|[CPrintDialogEx::GetDriverName](#getdrivername)|Ruft den Namen des systemdefinierten Druckergerätetreibers ab.|
|[CprintDialogEx::GetPortName](#getportname)|Ruft den Namen des aktuell ausgewählten Druckeranschlusses ab.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Ruft ein Handle für den Druckergerätekontext ab.|
|[CPrintDialogEx::PrintAll](#printall)|Legt fest, ob alle Seiten des Dokuments gedruckt werden sollen.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Bestimmt, ob gesammelte Kopien angefordert werden.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Legt fest, ob die aktuelle Seite des Dokuments gedruckt werden soll.|
|[CPrintDialogEx::PrintRange](#printrange)|Legt fest, ob nur ein bestimmter Seitenbereich gedruckt werden soll.|
|[CPrintDialogEx::PrintAuswahl](#printselection)|Legt fest, ob nur die aktuell ausgewählten Elemente gedruckt werden sollen.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|Eine Struktur, die `CPrintDialogEx` zum Anpassen eines Objekts verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Sie können sich auf das Framework verlassen, um viele Aspekte des Druckprozesses für Ihre Anwendung zu behandeln. Weitere Informationen zur Verwendung des Frameworks für Druckaufgaben finden Sie im Artikel [Drucken](../../mfc/printing.md).

Wenn Sie möchten, dass Ihre Anwendung den Druck ohne `CPrintDialogEx` die Beteiligung des Frameworks verarbeitet, können Sie die Klasse "wie besehen" mit dem bereitgestellten Konstruktor verwenden, oder Sie können Ihre eigene Dialogklasse ableiten `CPrintDialogEx` und einen Konstruktor entsprechend Ihren Anforderungen schreiben. In beiden Fällen verhalten sich diese Dialogfelder wie Standard-MFC-Dialogfelder, da sie von der Klasse `CCommonDialog`abgeleitet sind.

Um ein `CPrintDialogEx` Objekt zu verwenden, `CPrintDialogEx` erstellen Sie das Objekt zuerst mit dem Konstruktor. Nachdem das Dialogfeld erstellt wurde, können Sie beliebige Werte in der [m_pdex](#m_pdex) Struktur festlegen oder ändern, um die Werte der Steuerelemente des Dialogfelds zu initialisieren. Die `m_pdex` Struktur ist vom Typ [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw). Weitere Informationen zu dieser Struktur finden Sie im Windows SDK.

Wenn Sie keine eigenen Handles `m_pdex` für `hDevMode` `hDevNames` die und-Elemente angeben, `GlobalFree` rufen Sie die Windows-Funktion für diese Handles auf, wenn Sie mit dem Dialogfeld fertig sind.

Rufen Sie nach dem Initialisieren `DoModal` der Dialogfeldsteuerelemente die Memberfunktion auf, um das Dialogfeld anzuzeigen, und ermöglichen Sie dem Benutzer, Druckoptionen auszuwählen. Bei `DoModal` Rückgaben können Sie bestimmen, ob der Benutzer die Schaltfläche OK, Anwenden oder Abbrechen ausgewählt hat.

Wenn der Benutzer OK gedrückt `CPrintDialogEx`hat, können Sie die Memberfunktionen von verwenden, um die vom Benutzer eingegebenen Informationen abzurufen.

Die `CPrintDialogEx::GetDefaults` Memberfunktion ist nützlich, um die aktuellen Druckerstandards abzurufen, ohne ein Dialogfeld anzuzeigen. Diese Methode erfordert keine Benutzerinteraktion.

Sie können die `CommDlgExtendedError` Windows-Funktion verwenden, um zu ermitteln, ob während der Initialisierung des Dialogfelds ein Fehler aufgetreten ist, und um mehr über den Fehler zu erfahren. Weitere Informationen zu dieser Funktion finden Sie im Windows SDK.

Weitere Informationen zur `CPrintDialogEx`Verwendung finden Sie unter [Allgemeine Dialogklassen](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdlgs.h

## <a name="cprintdialogexcprintdialogex"></a><a name="cprintdialogex"></a>CPrintDialogEx::CPrintDialogEx

Erstellt ein Windows Print-Eigenschaftenblatt.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Ein oder mehrere Flags können Sie verwenden, um die Einstellungen des Dialogfelds anzupassen, kombiniert mit dem bitweisen ODER-Operator. Das PD_ALLPAGES-Flag legt z. B. den Standarddruckbereich auf alle Seiten des Dokuments fest. Weitere Informationen zu diesen Flags finden Sie in der [PRINTDLGEX-Struktur](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) im Windows SDK.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete oder Besitzerfenster des Dialogfelds.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion erstellt nur das Objekt. Verwenden `DoModal` Sie die Memberfunktion, um das Dialogfeld anzuzeigen.

## <a name="cprintdialogexcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialogEx::CreatePrinterDC

Erstellt einen Druckergerätekontext (DC) aus den Strukturen [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) und [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Rückgabewert

Behandeln Sie den neu erstellten Druckergerätekontext.

### <a name="remarks"></a>Bemerkungen

Der zurückgegebene Dc wird `hDC` auch im Member von [m_pdex](#m_pdex)gespeichert.

Es wird davon ausgegangen, dass dieser Domänencontroller der aktuelle Drucker-DC ist, und alle anderen zuvor erhaltenen Drucker-DCs müssen gelöscht werden. Diese Funktion kann aufgerufen und der resultierende Domänencontroller verwendet werden, ohne jemals das Dialogfeld Drucken anzuzeigen.

## <a name="cprintdialogexdomodal"></a><a name="domodal"></a>CPrintDialogEx::DoModal

Rufen Sie diese Funktion auf, um das Windows Print-Eigenschaftenblatt anzuzeigen, und ermöglichen Sie dem Benutzer, verschiedene Druckoptionen auszuwählen, z. B. die Anzahl der Kopien, den Seitenbereich und die Frage, ob Kopien sortiert werden sollen.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Der INT_PTR Rückgabewert ist eigentlich ein HRESULT. Weitere Informationen finden Sie im Abschnitt Rückgabewerte in [PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\)) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Druckdialogoptionen initialisieren möchten, indem Sie Elemente `m_pdex` `DoModal`der Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

Nach `DoModal`dem Aufruf können Sie andere Memberfunktionen aufrufen, um die Einstellungen oder Informationen, die der Benutzer in das Dialogfeld eingibt, abzurufen.

Wenn das PD_RETURNDC-Flag `DoModal`beim Aufrufen verwendet wird, `hDC` wird ein Drucker-DC im Mitglied [von m_pdex](#m_pdex)zurückgegeben. Dieser Domänencontroller muss mit einem Aufruf von [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) durch den Aufruf von `CPrintDialogEx`freigegeben werden.

## <a name="cprintdialogexgetcopies"></a><a name="getcopies"></a>CPrintDialogEx::GetCopies

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um die Anzahl der angeforderten Kopien abzurufen.

```
int GetCopies() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der angeforderten Kopien.

## <a name="cprintdialogexgetdefaults"></a><a name="getdefaults"></a>CPrintDialogEx::GetDefaults

Rufen Sie diese Funktion auf, um die Gerätestandards des Standarddruckers abzurufen, ohne ein Dialogfeld anzuzeigen.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Erstellt einen Druckergerätekontext (DC) aus den Strukturen [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) und [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

`GetDefaults`zeigt das Eigenschaftenblatt Drucken nicht an. Stattdessen werden die `hDevNames` `hDevMode` und Die Member von [m_pdex](#m_pdex) auf die [DEVMODE-](/windows/win32/api/wingdi/ns-wingdi-devmodea) und [DEVNAMES-Strukturen](/windows/win32/api/commdlg/ns-commdlg-devnames) festgelegt, die für den Systemstandarddrucker initialisiert werden. Beide `hDevNames` `hDevMode` müssen NULL sein `GetDefaults` oder fehlschlägt.

Wenn das PD_RETURNDC-Flag gesetzt ist, `hDevNames` wird `hDevMode` diese `m_pdex.hDevNames` Funktion `m_pdex.hDevMode`nicht nur an den Aufrufer zurückgegeben `m_pdex.hDC`und (in und ) gefunden, sondern auch einen Drucker-DC in zurückgegeben. Es liegt in der Verantwortung des Aufrufers, den Drucker-DC zu löschen und die `CPrintDialogEx` Windows [GlobalFree-Funktion](/windows/win32/api/winbase/nf-winbase-globalfree) auf den Handles aufzurufen, wenn Sie mit dem Objekt fertig sind.

## <a name="cprintdialogexgetdevicename"></a><a name="getdevicename"></a>CPrintDialogEx::GetDeviceName

Rufen Sie diese Funktion auf, nachdem Sie [DoModal](#domodal) aufgerufen haben, um den Namen des aktuell ausgewählten Druckers abzurufen, oder nachdem Sie [GetDefaults](#getdefaults) aufgerufen haben, um den Namen des Standarddruckers abzurufen.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des aktuell ausgewählten Druckers.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie einen `CString` Zeiger auf `GetDeviceName` das Objekt, das als Wert von `lpszDeviceName` in einem Aufruf von [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)zurückgegeben wird.

## <a name="cprintdialogexgetdevmode"></a><a name="getdevmode"></a>CPrintDialogEx::GetDevMode

Rufen Sie diese Funktion auf, nachdem Sie [DoModal](#domodal) oder [GetDefaults](#getdefaults) aufgerufen haben, um Informationen über das Druckgerät abzurufen.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Rückgabewert

Die [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) DEVMODE-Datenstruktur, die Informationen zur Geräteinitialisierung und Umgebung eines Druckertreibers enthält. Sie müssen den von dieser Struktur entnommenen Speicher mit der Windows [GlobalUnlock-Funktion](/windows/win32/api/winbase/nf-winbase-globalunlock) entsperren, die im Windows SDK beschrieben wird.

## <a name="cprintdialogexgetdrivername"></a><a name="getdrivername"></a>CPrintDialogEx::GetDriverName

Rufen Sie diese Funktion auf, nachdem Sie [DoModal](#domodal) oder [GetDefaults](#getdefaults) aufgerufen haben, um den Namen des systemdefinierten Druckergerätetreibers abzurufen.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine `CString` Angabe des systemdefinierten Treibernamens.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie einen `CString` Zeiger auf `GetDriverName` das Objekt, das als Wert von *lpszDriverName* in einem Aufruf von [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)zurückgegeben wird.

## <a name="cprintdialogexgetportname"></a><a name="getportname"></a>CprintDialogEx::GetPortName

Rufen Sie diese Funktion auf, nachdem Sie [DoModal](#domodal) oder [GetDefaults](#getdefaults) aufgerufen haben, um den Namen des aktuell ausgewählten Druckeranschlusses abzurufen.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des aktuell ausgewählten Druckeranschlusses.

## <a name="cprintdialogexgetprinterdc"></a><a name="getprinterdc"></a>CPrintDialogEx::GetPrinterDC

Gibt ein Handle an den Druckergerätekontext zurück.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für den Druckergerätekontext.

### <a name="remarks"></a>Bemerkungen

Sie müssen die Windows [DeleteDC-Funktion](/windows/win32/api/wingdi/nf-wingdi-deletedc) aufrufen, um den Gerätekontext zu löschen, wenn Sie damit fertig sind.

## <a name="cprintdialogexm_pdex"></a><a name="m_pdex"></a>CPrintDialogEx::m_pdex

Eine PRINTDLGEX-Struktur, deren Member die Eigenschaften des Dialogobjekts speichern.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Bemerkungen

Nach dem `CPrintDialogEx` Erstellen eines `m_pdex` Objekts können Sie verschiedene Aspekte des Dialogfelds festlegen, bevor Sie die [DoModal-Memberfunktion](#domodal) aufrufen. Weitere Informationen zur `m_pdex` Struktur finden Sie unter [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) im Windows SDK.

Wenn Sie `m_pdex` das Datenelement direkt ändern, überschreiben Sie jedes Standardverhalten.

## <a name="cprintdialogexprintall"></a><a name="printall"></a>CPrintDialogEx::PrintAll

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um zu bestimmen, ob alle Seiten im Dokument gedruckt werden sollen.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn alle Seiten im Dokument gedruckt werden sollen; andernfalls FALSE.

## <a name="cprintdialogexprintcollate"></a><a name="printcollate"></a>CPrintDialogEx::PrintCollate

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um zu bestimmen, ob der Drucker alle gedruckten Kopien des Dokuments zusammenstellen soll.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Benutzer das Kontrollkästchen Collate im Dialogfeld aktiviert; andernfalls FALSE.

## <a name="cprintdialogexprintcurrentpage"></a><a name="printcurrentpage"></a>CPrintDialogEx::PrintCurrentPage

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um zu bestimmen, ob die aktuelle Seite im Dokument gedruckt werden soll.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn **Aktuelle Seite drucken** im Druckdialog ausgewählt ist; andernfalls FALSE.

## <a name="cprintdialogexprintrange"></a><a name="printrange"></a>CPrintDialogEx::PrintRange

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um zu bestimmen, ob nur ein Bereich von Seiten im Dokument gedruckt werden soll.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn nur ein Seitenbereich im Dokument gedruckt werden soll; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Die angegebenen Seitenbereiche können [m_pdex](#m_pdex) aus `nPageRanges`m_pdex `nMaxPageRanges`(siehe , und `lpPageRanges` in der [PRINTDLGEX-Struktur](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) im Windows SDK) bestimmt werden.

## <a name="cprintdialogexprintselection"></a><a name="printselection"></a>CPrintDialogEx::PrintAuswahl

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um zu bestimmen, ob nur die aktuell ausgewählten Elemente gedruckt werden sollen.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn nur die ausgewählten Elemente gedruckt werden sollen; andernfalls FALSE.

## <a name="see-also"></a>Siehe auch

[CCommonDialog-Klasse](../../mfc/reference/ccommondialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo-Struktur](../../mfc/reference/cprintinfo-structure.md)
