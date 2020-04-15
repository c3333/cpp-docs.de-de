---
title: CPageSetupDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPageSetupDialog
- AFXDLGS/CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CreatePrinterDC
- AFXDLGS/CPageSetupDialog::DoModal
- AFXDLGS/CPageSetupDialog::GetDeviceName
- AFXDLGS/CPageSetupDialog::GetDevMode
- AFXDLGS/CPageSetupDialog::GetDriverName
- AFXDLGS/CPageSetupDialog::GetMargins
- AFXDLGS/CPageSetupDialog::GetPaperSize
- AFXDLGS/CPageSetupDialog::GetPortName
- AFXDLGS/CPageSetupDialog::OnDrawPage
- AFXDLGS/CPageSetupDialog::PreDrawPage
- AFXDLGS/CPageSetupDialog::m_psd
helpviewer_keywords:
- CPageSetupDialog [MFC], CPageSetupDialog
- CPageSetupDialog [MFC], CreatePrinterDC
- CPageSetupDialog [MFC], DoModal
- CPageSetupDialog [MFC], GetDeviceName
- CPageSetupDialog [MFC], GetDevMode
- CPageSetupDialog [MFC], GetDriverName
- CPageSetupDialog [MFC], GetMargins
- CPageSetupDialog [MFC], GetPaperSize
- CPageSetupDialog [MFC], GetPortName
- CPageSetupDialog [MFC], OnDrawPage
- CPageSetupDialog [MFC], PreDrawPage
- CPageSetupDialog [MFC], m_psd
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
ms.openlocfilehash: 218ed24ccf56854622e20936299fcc2e8a3d0fa9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374791"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog-Klasse

Kapselt die Dienste, die durch das allgemeine Windows-OLE-Dialogfeld "Seiteneinrichtung" bereitgestellt werden, zusammen mit zusätzlicher Unterstützung für das Festlegen und Ändern von Druckrändern.

## <a name="syntax"></a>Syntax

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|Erstellt ein `CPageSetupDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Erstellt einen Gerätekontext für den Druck.|
|[CPageSetupDialog::DoModal](#domodal)|Zeigt das Dialogfeld an und ermöglicht es dem Benutzer, eine Auswahl zu treffen.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Gibt den Gerätenamen des Druckers zurück.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Gibt den aktuellen DEVMODE des Druckers zurück.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Gibt den vom Drucker verwendeten Treiber zurück.|
|[CPageSetupDialog::GetMargins](#getmargins)|Gibt die aktuellen Randeinstellungen des Druckers zurück.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Gibt das Papierformat des Druckers zurück.|
|[CPageSetupDialog::GetPortName](#getportname)|Gibt den Namen des Ausgabeports zurück.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Wird vom Framework aufgerufen, um ein Bildschirmbild einer gedruckten Seite zu rendern.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Wird vom Framework aufgerufen, bevor ein Bildschirmbild einer gedruckten Seite gerendert wird.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Eine Struktur, die `CPageSetupDialog` zum Anpassen eines Objekts verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse ist so konzipiert, dass sie an die Stelle des Dialogfelds Druckeinrichtung treten kann.

Um ein `CPageSetupDialog` Objekt zu verwenden, `CPageSetupDialog` erstellen Sie das Objekt zuerst mit dem Konstruktor. Nachdem das Dialogfeld erstellt wurde, können Sie beliebige `m_psd` Werte im Datenelement festlegen oder ändern, um die Werte der Steuerelemente des Dialogfelds zu initialisieren. Die [m_psd](#m_psd) Struktur vom Typ PAGESETUPDLG.

Rufen Sie nach dem Initialisieren `DoModal` der Dialogfeldsteuerelemente die Memberfunktion auf, um das Dialogfeld anzuzeigen, und ermöglichen Sie dem Benutzer, Druckoptionen auszuwählen. `DoModal`gibt an, ob der Benutzer die Schaltfläche OK (IDOK) oder Abbrechen (IDCANCEL) ausgewählt hat.

Wenn `DoModal` IDOK zurückgegeben wird, `CPageSetupDialog`können Sie mehrere Memberfunktionen `m_psd` von verwenden oder auf das Datenelement zugreifen, um Informationen vom Benutzer abzurufen.

> [!NOTE]
> Nachdem das allgemeine Dialogfeld OLE-Seiteneinrichtung verworfen wurde, werden alle vom Benutzer vorgenommenen Änderungen nicht vom Framework gespeichert. Es liegt an der Anwendung selbst, werteaus diesem Dialogfeld an einem permanenten Speicherort zu speichern, z. B. Member des Dokuments oder der Anwendungsklasse der Anwendung.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdlgs.h

## <a name="cpagesetupdialogcpagesetupdialog"></a><a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog

Rufen Sie diese `CPageSetupDialog` Funktion auf, um ein Objekt zu erstellen.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Ein oder mehrere Flags können Sie verwenden, um die Einstellungen des Dialogfelds anzupassen. Die Werte können mit dem bitwise-OR-Operator kombiniert werden. Diese Werte haben die folgenden Bedeutungen:

- PSD_DEFAULTMINMARGINS Legt die zulässigen Mindestbreiten für die Seitenränder so fest wie die Mindestbreiten des Druckers. Dieses Flag wird ignoriert, wenn die flags PSD_MARGINS und PSD_MINMARGINS ebenfalls angegeben werden.

- PSD_INWININIINTLMEASURE Nicht implementiert.

- PSD_MINMARGINS Bewirkt, dass das System `rtMinMargin` die im Element angegebenen Werte als zulässige Mindestbreiten für den linken, oberen, rechten und unteren Rand verwendet. Das System verhindert, dass der Benutzer eine Breite eingibt, die kleiner als das angegebene Minimum ist. Wenn PSD_MINMARGINS nicht angegeben ist, legt das System die zulässigen Mindestbreiten auf die vom Drucker zulässigen Breiten fest.

- PSD_MARGINS Aktiviert den Randkontrollbereich.

- PSD_INTHOUSANDTHSOFINCHES Bewirkt, dass die Einheiten des Dialogfelds in 1/1000 Zoll gemessen werden.

- PSD_INHUNDREDTHSOFMILLIMETERS Bewirkt, dass die Einheiten des Dialogfelds in 1/100 Millimeter gemessen werden.

- PSD_DISABLEMARGINS Deaktiviert die Steuerelemente des Randdialogfelds.

- PSD_DISABLEPRINTER Deaktiviert die Druckerschaltfläche.

- PSD_NOWARNING Verhindert, dass die Warnmeldung angezeigt wird, wenn kein Standarddrucker vorhanden ist.

- PSD_DISABLEORIENTATION Deaktiviert das Dialogfeldsteuerelement für die Seitenausrichtung.

- PSD_RETURNDEFAULT `CPageSetupDialog` verursacht die Rückgabe von [DEVMODE-](/windows/win32/api/wingdi/ns-wingdi-devmodea) und [DEVNAMES-Strukturen,](/windows/win32/api/commdlg/ns-commdlg-devnames) die für den Standarddrucker des Systems initialisiert werden, ohne ein Dialogfeld anzuzeigen. Es wird davon `hDevNames` `hDevMode` ausgegangen, dass beide und NULL sind; Andernfalls gibt die Funktion einen Fehler zurück. Wenn der Standarddrucker des Systems von einem alten Druckertreiber (früher `hDevNames` als Windows Version 3.0) unterstützt wird, wird nur zurückgegeben. `hDevMode` ist NULL.

- PSD_DISABLEPAPER Deaktiviert die Papierauswahlsteuerung.

- PSD_SHOWHELP Bewirkt, dass im Dialogfeld die Hilfeschaltfläche angezeigt wird. Der `hwndOwner` Member darf nicht NULL sein, wenn dieses Flag angegeben ist.

- PSD_ENABLEPAGESETUPHOOK Aktiviert die in `lpfnSetupHook`angegebene Hook-Funktion.

- PSD_ENABLEPAGESETUPTEMPLATE Veranlasst das Betriebssystem, das Dialogfeld mithilfe des `hInstance` Dialogfelds zu erstellen, das von und `lpSetupTemplateName`identifiziert wurde.

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE Gibt `hInstance` an, dass ein Datenblock identifiziert wird, der eine vorinstallierte Dialogfeldvorlage enthält. Das System `lpSetupTemplateName` ignoriert, wenn dieses Flag angegeben ist.

- PSD_ENABLEPAGEPAINTHOOK Aktiviert die in `lpfnPagePaintHook`angegebene Hook-Funktion.

- PSD_DISABLEPAGEPAINTING Deaktiviert den Zeichnungsbereich des Dialogfelds.

*pParentWnd*<br/>
Zeigen Sie mit dem Zeiger auf das übergeordnete elementge oder den Besitzer des Dialogfelds.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [DoModal-Funktion,](../../mfc/reference/cdialog-class.md#domodal) um das Dialogfeld anzuzeigen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

## <a name="cpagesetupdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPageSetupDialog::CreatePrinterDC

Erstellt einen Druckergerätekontext aus den Strukturen [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) und [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Rückgabewert

Behandeln Sie den neu erstellten Druckergerätekontext (DC).

## <a name="cpagesetupdialogdomodal"></a><a name="domodal"></a>CPageSetupDialog::DoModal

Rufen Sie diese Funktion auf, um das allgemeine Dialogfeld OLE-Seiteneinrichtung von Windows anzuzeigen, und ermöglichen Sie dem Benutzer, verschiedene Druckeinrichtungsoptionen auszuwählen, z. B. Druckränder, Größe und Ausrichtung des Papiers und Zieldrucker.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

IDOK oder IDCANCEL. Wenn IDCANCEL zurückgegeben wird, rufen Sie die Windows [CommDlgExtendedError-Funktion](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) auf, um zu ermitteln, ob ein Fehler aufgetreten ist.

IDOK und IDCANCEL sind Konstanten, die angeben, ob der Benutzer die Schaltfläche OK oder Abbrechen ausgewählt hat.

### <a name="remarks"></a>Bemerkungen

Darüber hinaus kann der Benutzer auf die Druckereinrichtungsoptionen zugreifen, z. B. den Netzwerkspeicherort und die für den ausgewählten Drucker spezifischen Eigenschaften.

Wenn Sie die verschiedenen Dialogdialogoptionen für das Seiteneinrichten initialisieren möchten, indem Sie Member der Struktur festlegen, sollten Sie dies `m_psd` vor dem Aufruf und nach dem Erstellen `DoModal`des Dialogobjekts tun. Rufen `DoModal`Sie nach dem Aufruf andere Memberfunktionen auf, um die Einstellungen oder Informationen, die der Benutzer in das Dialogfeld eingibt, abzurufen.

Wenn Sie die aktuellen Einstellungen des Benutzers weitergeben möchten, rufen Sie [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter)an. Diese Funktion nimmt die `CPageSetupDialog` Informationen aus dem Objekt und initialisiert und wählt einen neuen Drucker-DC mit den richtigen Attributen aus.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialoggetdevicename"></a><a name="getdevicename"></a>CPageSetupDialog::GetDeviceName

Rufen Sie `DoModal` diese Funktion nach, um den Namen des aktuell ausgewählten Druckers abzurufen.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Rückgabewert

Der vom `CPageSetupDialog` Objekt verwendete Gerätename.

## <a name="cpagesetupdialoggetdevmode"></a><a name="getdevmode"></a>CPageSetupDialog::GetDevMode

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um Informationen über den Druckergerätekontext des `CPageSetupDialog` Objekts abzurufen.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Rückgabewert

Die [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) DEVMODE-Datenstruktur, die Informationen zur Geräteinitialisierung und Umgebung eines Druckertreibers enthält. Sie müssen den von dieser Struktur entnommenen Speicher mit der Windows [GlobalUnlock-Funktion](/windows/win32/api/winbase/nf-winbase-globalunlock) entsperren, die im Windows SDK beschrieben wird.

## <a name="cpagesetupdialoggetdrivername"></a><a name="getdrivername"></a>CPageSetupDialog::GetDriverName

Rufen Sie diese Funktion auf, nachdem Sie [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) aufgerufen haben, um den Namen des systemdefinierten Druckergerätetreibers abzurufen.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine `CString` Angabe des systemdefinierten Treibernamens.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie einen `CString` Zeiger auf `GetDriverName` das Objekt, das als Wert von `lpszDriverName` in einem Aufruf von [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)zurückgegeben wird.

## <a name="cpagesetupdialoggetmargins"></a><a name="getmargins"></a>CPageSetupDialog::GetMargins

Rufen Sie diese Funktion `DoModal` nach einem Aufruf auf, um die Ränder des Druckergerätetreibers abzurufen.

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Parameter

*lpRectMargins*<br/>
Zeiger auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das (in 1/1000 Zoll oder 1/100 mm) die Druckränder für den aktuell ausgewählten Drucker beschreibt. Übergeben Sie NULL für diesen Parameter, wenn Sie nicht an diesem Rechteck interessiert sind.

*lpRectMinMargins*<br/>
Zeiger auf `RECT` eine `CRect` Struktur oder ein Objekt, das (in 1/1000 Zoll oder 1/100 mm) die minimalen Druckränder für den aktuell ausgewählten Drucker beschreibt. Übergeben Sie NULL für diesen Parameter, wenn Sie nicht an diesem Rechteck interessiert sind.

## <a name="cpagesetupdialoggetpapersize"></a><a name="getpapersize"></a>CPageSetupDialog::GetPaperSize

Rufen Sie diese Funktion auf, um die Größe des für den Drucken ausgewählten Papiers abzurufen.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [CSize-Objekt,](../../atl-mfc-shared/reference/csize-class.md) das die Größe des Papiers (in 1/1000 Zoll oder 1/100 mm) enthält, das für den Druck ausgewählt wurde.

## <a name="cpagesetupdialoggetportname"></a><a name="getportname"></a>CPageSetupDialog::GetPortName

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um den Namen des aktuell ausgewählten Druckeranschlusses abzurufen.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des aktuell ausgewählten Druckeranschlusses.

## <a name="cpagesetupdialogm_psd"></a><a name="m_psd"></a>CPageSetupDialog::m_psd

Eine Struktur vom Typ PAGESETUPDLG, deren Member die Eigenschaften des Dialogobjekts speichern.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Bemerkungen

Nach dem `CPageSetupDialog` Erstellen eines `m_psd` Objekts können Sie verschiedene Aspekte `DoModal` des Dialogfelds festlegen, bevor Sie die Memberfunktion aufrufen.

Wenn Sie `m_psd` das Datenelement direkt ändern, überschreiben Sie jedes Standardverhalten.

Weitere Informationen zur [PAGESETUPDLG-Struktur](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw) finden Sie im Windows SDK.

Siehe Beispiel für [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialogondrawpage"></a><a name="ondrawpage"></a>CPageSetupDialog::OnDrawPage

Wird vom Framework aufgerufen, um ein Bildschirmbild einer gedruckten Seite zu zeichnen.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf den Druckergerätekontext.

*nMessage*<br/>
Gibt eine Meldung an, die den Bereich der Seite angibt, die gerade gezeichnet wird. Dabei kann es sich um eine der folgenden Methoden handeln:

- WM_PSD_FULLPAGERECT Der gesamte Seitenbereich.

- WM_PSD_MINMARGINRECT Aktuelle Mindestmargen.

- WM_PSD_MARGINRECT Aktuelle Margen.

- WM_PSD_GREEKTEXTRECT Inhalt der Seite.

- WM_PSD_ENVSTAMPRECT Bereich, der für eine Briefmarkendarstellung reserviert ist.

- WM_PSD_YAFULLPAGERECT Bereich für eine Rückgabeadressendarstellung. Dieser Bereich erstreckt sich bis zu den Rändern des Beispielseitenbereichs.

*lpRect*<br/>
Zeiger auf ein [CRect-](../../atl-mfc-shared/reference/crect-class.md) oder [RECT-Objekt,](/windows/win32/api/windef/ns-windef-rect) das die Koordinaten des Zeichenbereichs enthält.

### <a name="return-value"></a>Rückgabewert

Wert ungleich Null, wenn behandelt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dieses Bild wird dann als Teil des allgemeinen Dialogfelds OLE Seiteneinrichtung angezeigt. Die Standardimplementierung zeichnet ein Bild einer Textseite.

Überschreiben Sie diese Funktion, um die Zeichnung eines bestimmten Bereichs des Bildes oder des gesamten Bildes anzupassen. Sie können dies tun, indem Sie eine **switch-Anweisung** mit **Fallanweisungen** verwenden, die den Wert von *nMessage*überprüfen. Um beispielsweise das Rendern des Inhalts des Seitenbilds anzupassen, können Sie den folgenden Beispielcode verwenden:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Beachten Sie, dass Sie nicht jeden Fall von *nMessage*behandeln müssen. Sie können eine Komponente des Bildes, mehrere Komponenten des Bildes oder den gesamten Bereich behandeln.

## <a name="cpagesetupdialogpredrawpage"></a><a name="predrawpage"></a>CPageSetupDialog::PreDrawPage

Wird vom Framework aufgerufen, bevor das Bildschirmbild einer gedruckten Seite gezeichnet wird.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Parameter

*wPaper*<br/>
Gibt einen Wert an, der das Papierformat angibt. Dieser Wert kann einer der **DMPAPER_** Werte sein, die in der Beschreibung der [DEVMODE-Struktur](/windows/win32/api/wingdi/ns-wingdi-devmodea) aufgeführt sind.

*wFlags*<br/>
Gibt die Ausrichtung des Papiers oder Umschlags an und gibt an, ob es sich bei dem Drucker um ein Dot-Matrix- oder HPPCL-Gerät (Hewlett Packard Printer Control Language) handelt. Dieser Parameter kann einen der folgenden Werte aufweisen:

- 0x001 Papier im Querformat (Punktmatrix)

- 0x003 Papier im Querformat (HPPCL)

- 0x005 Papier im Hochformat (Punktmatrix)

- 0x007 Papier im Hochformat (HPPCL)

- 0x00b Umschlag im Querformat (HPPCL)

- 0x00d Umschlag im Hochformat (Punktmatrix)

- 0x019 Umschlag im Querformat (Punktmatrix)

- 0x01f Umschlag im Hochformat (Punktmatrix)

*pPSD*<br/>
Zeiger auf eine `PAGESETUPDLG`-Struktur. Weitere Informationen [zu PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)finden Sie im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Wert ungleich Null, wenn behandelt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Zeichnung des Bildes anzupassen. Wenn Sie diese Funktion überschreiben und TRUE zurückgeben, müssen Sie das gesamte Bild zeichnen. Wenn Sie diese Funktion überschreiben und FALSE zurückgeben, wird das gesamte Standardbild vom Framework gezeichnet.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog-Klasse](../../mfc/reference/ccommondialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
