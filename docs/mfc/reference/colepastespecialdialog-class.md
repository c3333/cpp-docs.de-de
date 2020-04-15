---
title: COlePasteSpecialDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
ms.openlocfilehash: 5e67a81f48b8cdf0dae6dc90fc2ded8dc44a73ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376990"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog-Klasse

Wird für das OLE-Dialogfeld "Inhalte einfügen" verwendet.

## <a name="syntax"></a>Syntax

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Erstellt ein `COlePasteSpecialDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|Fügt der Liste der Formate, die Ihre Anwendung einfügen kann, benutzerdefinierte Formate hinzu.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Fügt der Liste der unterstützten Zwischenablageformate einen neuen Eintrag hinzu.|
|[COlePasteSpecialDialog::Standardformate hinzufügen](#addstandardformats)|Fügt der Liste der Formate, die Ihre Anwendung einfügen kann, CF_BITMAP, CF_DIB, CF_METAFILEPICT und optional CF_LINKSOURCE hinzu.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Erstellt das Element im Containerdokument im angegebenen Format.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Zeigt das Dialogfeld OLE Paste Special an.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Gibt an, ob ein Element als Symbol gezeichnet werden soll oder nicht.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Ruft ein Handle für die Metadatei ab, die der ikonischen Form dieses Elements zugeordnet ist.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Ruft den Index der verfügbaren Einfügeoptionen ab, der vom Benutzer ausgewählt wurde.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Ruft den ausgewählten Auswahltyp ab.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Eine Struktur vom Typ OLEUIPASTESPECIAL, die die Funktion des Dialogfelds steuert.|

## <a name="remarks"></a>Bemerkungen

Erstellen Sie ein `COlePasteSpecialDialog` Klassenobjekt, wenn Sie dieses Dialogfeld aufrufen möchten. Nachdem `COlePasteSpecialDialog` ein Objekt erstellt wurde, können Sie die Memberfunktionen [AddFormat](#addformat) und [AddStandardFormats](#addstandardformats) verwenden, um dem Dialogfeld Zwischenablageformate hinzuzufügen. Sie können auch die [m_ps](#m_ps) Struktur verwenden, um die Werte oder Zustände von Steuerelementen im Dialogfeld zu initialisieren. Die `m_ps` Struktur ist vom Typ OLEUIPASTESPECIAL.

Weitere Informationen finden Sie in der [OLEUIPASTESPECIAL-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) im Windows SDK.

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="colepastespecialdialogaddformat"></a><a name="addformat"></a>COlePasteSpecialDialog::AddFormat

Rufen Sie diese Funktion auf, um der Liste der Formate, die Ihre Anwendung in einem Vorgang "Einfügen" unterstützen kann, neue Formate hinzuzufügen.

```
void AddFormat(
    const FORMATETC& formatEtc,
    LPTSTR lpszFormat,
    LPTSTR lpszResult,
    DWORD flags);

void AddFormat(
    UINT cf,
    DWORD tymed,
    UINT nFormatID,
    BOOL bEnableIcon,
    BOOL bLink);
```

### <a name="parameters"></a>Parameter

*Fmt*<br/>
Verweis auf den hinzuzufügenden Datentyp.

*lpszFormat*<br/>
Zeichenfolge, die dem Benutzer das Format beschreibt.

*lpszErgebnis*<br/>
Zeichenfolge, die das Ergebnis beschreibt, wenn dieses Format im Dialogfeld ausgewählt ist.

*Flaggen*<br/>
Die verschiedenen Verknüpfungs- und Einbettungsoptionen für dieses Format. Dieses Flag ist eine bitweise Kombination eines oder mehrerer der verschiedenen Werte im aufgezählten OLEUIPASTEFLAG-Typ.

*Cf*<br/>
Das hinzuzufügende Zwischenablageformat.

*Tymed*<br/>
Die in diesem Format verfügbaren Medientypen. Dies ist eine bitweise Kombination eines oder mehrerer Werte im aufgezählten TYMED-Typ.

*nFormatID*<br/>
Die ID der Zeichenfolge, die dieses Format identifiziert. Das Format dieser Zeichenfolge besteht aus zwei separaten Zeichenfolgen, die durch ein Zeichen 'n' getrennt sind. Die erste Zeichenfolge ist die gleiche, die im *lpstrFormat-Parameter* übergeben würde, und die zweite ist die gleiche wie der *lpstrResult-Parameter.*

*bEnableIcon*<br/>
Flag, das bestimmt, ob das Kontrollkästchen Als Symbol anzeigen aktiviert ist, wenn dieses Format im Listenfeld ausgewählt wird.

*Blinken*<br/>
Flag, das bestimmt, ob das Optionsfeld Link einfügen aktiviert ist, wenn dieses Format im Listenfeld ausgewählt wird.

### <a name="remarks"></a>Bemerkungen

Diese Funktion kann aufgerufen werden, um entweder Standardformate wie CF_TEXT oder CF_TIFF oder benutzerdefinierte Formate hinzuzufügen, die Ihre Anwendung beim System registriert hat. Weitere Informationen zum Einfügen von Datenobjekten in Ihre Anwendung finden Sie im Artikel [Datenobjekte und Datenquellen: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Weitere Informationen finden [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) Sie im TYMED-Enumerationstyp und in der [FORMATETC-Struktur](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

Weitere Informationen finden Sie im aufgezählten [OLEUIPASTEFLAG-Typ](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) im Windows SDK.

## <a name="colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry

Fügt der Liste der unterstützten Zwischenablageformate einen neuen Eintrag hinzu.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parameter

*Cf*<br/>
Das hinzuzufügende Zwischenablageformat.

### <a name="return-value"></a>Rückgabewert

Eine [OLEUIPASTEFLAG-Struktur,](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) die die Informationen für den neuen Linkeintrag enthält.

## <a name="colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a>COlePasteSpecialDialog::Standardformate hinzufügen

Rufen Sie diese Funktion auf, um die folgenden Zwischenablageformate zur Liste der Formate hinzuzufügen, die Ihre Anwendung in einem Vorgang "Einfügen" unterstützen kann:

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnableLink*<br/>
Flag, das bestimmt, ob der Liste der Formate, die Die Anwendung eingefügt werden kann, CF_LINKSOURCE hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Eingebettetes Objekt"**

- (optional) **"Link-Quelle"**

Diese Formate werden verwendet, um das Einbetten und Verknüpfen zu unterstützen.

## <a name="colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog

Erstellt ein `COlePasteSpecialDialog`-Objekt.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Erstellungsflag enthält eine beliebige Anzahl der folgenden Flags, die mit dem bitwise-OR-Operator kombiniert werden:

- PSF_SELECTPASTE Gibt an, dass das Optionsfeld Einfügen zunächst aktiviert wird, wenn das Dialogfeld aufgerufen wird. Kann nicht in Kombination mit PSF_SELECTPASTELINK verwendet werden. Dies ist die Standardoption.

- PSF_SELECTPASTELINK Gibt an, dass das Optionsfeld Verknüpfung einfügen zunächst aktiviert wird, wenn das Dialogfeld aufgerufen wird. Kann nicht in Kombination mit PSF_SELECTPASTE verwendet werden.

- PSF_CHECKDISPLAYASICON Gibt an, dass das Kontrollkästchen Als Symbol anzeigen wird, wird anfänglich aktiviert, wenn das Dialogfeld aufgerufen wird.

- PSF_SHOWHELP Gibt an, dass die Hilfeschaltfläche angezeigt wird, wenn das Dialogfeld aufgerufen wird.

*pDataObject*<br/>
Zeigt auf das [COleDataObject](../../mfc/reference/coledataobject-class.md) zum Einfügen. Wenn dieser Wert NULL ist, ruft er die `COleDataObject` aus der Zwischenablage ab.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ `CWnd`), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogfelds auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion erstellt `COlePasteSpecialDialog` nur ein Objekt. Um das Dialogfeld anzuzeigen, rufen Sie die [DoModal-Funktion](#domodal) auf.

Weitere Informationen finden Sie im aufgezählten [OLEUIPASTEFLAG-Typ](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) im Windows SDK.

## <a name="colepastespecialdialogcreateitem"></a><a name="createitem"></a>COlePasteSpecialDialog::CreateItem

Erstellt das neue Element, das im Dialogfeld Spezial einfügen ausgewählt wurde.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parameter

*pNewItem*<br/>
Zeigt auf `COleClientItem` eine Instanz. Lässt keine NULL-Werte zu.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Element erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte nur aufgerufen werden, nachdem [DoModal](#domodal) IDOK zurückgegeben hat.

## <a name="colepastespecialdialogdomodal"></a><a name="domodal"></a>COlePasteSpecialDialog::DoModal

Zeigt das Dialogfeld OLE Paste Special an.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Abschlussstatus für das Dialogfeld. Einer der folgenden Werte:

- IDOK, wenn das Dialogfeld erfolgreich angezeigt wurde.

- IDCANCEL, wenn der Benutzer das Dialogfeld abgebrochen hat.

- IDABORT, wenn ein Fehler aufgetreten ist. Wenn IDABORT zurückgegeben wird, rufen Sie die `COleDialog::GetLastError` Memberfunktion auf, um weitere Informationen über den Fehlertyp zu erhalten, der aufgetreten ist. Eine Liste möglicher Fehler finden Sie unter Die [OleUIPasteSpecial-Funktion](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Dialogfeldsteuerelemente initialisieren [m_ps](#m_ps) möchten, indem Sie Elemente `DoModal`der m_ps Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

Wenn `DoModal` IDOK zurückgegeben wird, können Sie andere Memberfunktionen aufrufen, um die Einstellungen oder Informationen, die der Benutzer eingibt, in das Dialogfeld abzurufen.

## <a name="colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect

Legt fest, ob der Benutzer das ausgewählte Element als Symbol anzeigen möchte.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Rückgabewert

Die Methode, die zum Rendern des Objekts erforderlich ist.

- DVASPECT_CONTENT zurückgegeben, wenn das Kontrollkästchen Als Symbol anzeigen nicht aktiviert wurde, wenn das Dialogfeld verworfen wurde.

- DVASPECT_ICON zurückgegeben, wenn das Kontrollkästchen Als Symbol anzeigen aktiviert wurde, wenn das Dialogfeld deaktiviert wurde.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion nur auf, nachdem [DoModal](#domodal) IDOK zurückgegeben hat.

Weitere Informationen zum Zeichnungsaspekt finden Sie in der [FORMATETC-Struktur](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

## <a name="colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile

Ruft die Metadatei ab, die dem vom Benutzer ausgewählten Element zugeordnet ist.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Rückgabewert

Das Handle für die Metadatei, das den ikonischen Aspekt des ausgewählten Elements enthält, wenn das Kontrollkästchen Als Symbol anzeigen aktiviert wurde, als das Dialogfeld durch Auswahl **von OK**verworfen wurde; andernfalls NULL.

## <a name="colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex

Ruft den Indexwert ab, der dem vom Benutzer ausgewählten Eintrag zugeordnet ist.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der Index in `OLEUIPASTEENTRY` das Array von Strukturen, das vom Benutzer ausgewählt wurde. Das Format, das dem ausgewählten Index entspricht, sollte beim Ausführen des Einfügevorgangs verwendet werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie in der [OLEUIPASTEENTRY-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) im Windows SDK.

## <a name="colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType

Bestimmt den Auswahltyp, den der Benutzer getroffen hat.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den Typ der getroffenen Auswahl zurück.

### <a name="remarks"></a>Bemerkungen

Die Rückgabetypwerte werden `Selection` durch den in der `COlePasteSpecialDialog` Klasse deklarierten Enumerationstyp angegeben.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Kurze Beschreibungen dieser Werte folgen:

- `COlePasteSpecialDialog::pasteLink`Das Menülink-Optionsfeld wurde überprüft, und das gewählte Format war ein Standard-OLE-Format.

- `COlePasteSpecialDialog::pasteNormal`Die Schaltfläche "Einfügen" wurde aktiviert und das gewählte Format war ein Standard-OLE-Format.

- `COlePasteSpecialDialog::pasteOther`Das ausgewählte Format ist kein Standard-OLE-Format.

- `COlePasteSpecialDialog::pasteStatic`Das gewählte Format war eine Metadatei.

## <a name="colepastespecialdialogm_ps"></a><a name="m_ps"></a>COlePasteSpecialDialog::m_ps

Struktur vom Typ OLEUIPASTESPECIAL, die verwendet wird, um das Verhalten des Dialogfelds "Spezial einfügen" zu steuern.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Bemerkungen

Member dieser Struktur können direkt oder über Memberfunktionen geändert werden.

Weitere Informationen finden Sie in der [OLEUIPASTESPECIAL-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)
