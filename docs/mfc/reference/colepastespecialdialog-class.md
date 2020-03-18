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
ms.openlocfilehash: f4174369620f14f2d1ac410aa5d756c75097ad0f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426618"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog-Klasse

Wird für das OLE-Dialogfeld "Inhalte einfügen" verwendet.

## <a name="syntax"></a>Syntax

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[COlePasteSpecialDialog:: COlePasteSpecialDialog](#colepastespecialdialog)|Erstellt ein `COlePasteSpecialDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COlePasteSpecialDialog:: addFormat](#addformat)|Fügt der Liste der Formate, die von der Anwendung eingefügt werden können, benutzerdefinierte Formate hinzu.|
|[COlePasteSpecialDialog:: addlinkentry](#addlinkentry)|Fügt der Liste der unterstützten Zwischenablage Formate einen neuen Eintrag hinzu.|
|[COlePasteSpecialDialog:: addstandardformats](#addstandardformats)|Fügt CF_BITMAP, CF_DIB, CF_METAFILEPICT und optional CF_LINKSOURCE der Liste der Formate hinzu, die von der Anwendung eingefügt werden können.|
|[COlePasteSpecialDialog:: kreateitem](#createitem)|Erstellt das Element im Container Dokument unter Verwendung des angegebenen Formats.|
|[COlePasteSpecialDialog::D omodal](#domodal)|Zeigt das OLE-Dialogfeld "speziell einfügen" an.|
|[COlePasteSpecialDialog:: getdrawaspect](#getdrawaspect)|Gibt an, ob das Element als Symbol gezeichnet werden soll oder nicht.|
|[COlePasteSpecialDialog:: getikonicmetafile](#geticonicmetafile)|Ruft ein Handle für die Metadatei ab, die der ikonischen Form dieses Elements zugeordnet ist.|
|[COlePasteSpecialDialog:: getpasteindex](#getpasteindex)|Ruft den Index der verfügbaren Einfüge Optionen ab, die vom Benutzer ausgewählt wurden.|
|[COlePasteSpecialDialog:: GetSelectionType](#getselectiontype)|Ruft den ausgewählten Typ der Auswahl ab.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[COlePasteSpecialDialog:: m_ps](#m_ps)|Eine Struktur vom Typ oleuipastespecial, mit der die Funktion des Dialog Felds gesteuert wird.|

## <a name="remarks"></a>Hinweise

Erstellen Sie ein Objekt der Klasse `COlePasteSpecialDialog`, wenn Sie dieses Dialogfeld aufzurufen. Nachdem ein `COlePasteSpecialDialog`-Objekt erstellt wurde, können Sie mit den Member-Funktionen [addFormat](#addformat) und [addstandardformats](#addstandardformats) dem Dialogfeld Zwischenablage Formate hinzufügen. Sie können auch die [m_ps](#m_ps) -Struktur verwenden, um die Werte oder Zustände von Steuerelementen im Dialogfeld zu initialisieren. Die `m_ps` Struktur ist vom Typ oleuipastespecial.

Weitere Informationen finden Sie in der [oleuipastespecial](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) -Struktur in der Windows SDK.

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie in den Artikel [Dialogfeldern in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Ccommondialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxodlgs. h

##  <a name="addformat"></a>COlePasteSpecialDialog:: addFormat

Mit dieser Funktion können Sie der Liste der Formate, die Ihre Anwendung in einem Vorgang zum Einfügen von Sonderzeichen unterstützen kann, neue Formate hinzufügen.

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

*fmt*<br/>
Verweis auf den hinzu zufügenden Datentyp.

*lpszformat*<br/>
Eine Zeichenfolge, die das Format für den Benutzer beschreibt.

*lpszresult*<br/>
Eine Zeichenfolge, die das Ergebnis beschreibt, wenn dieses Format im Dialogfeld ausgewählt wird.

*flags*<br/>
Die verschiedenen Verknüpfungs-und Einbettungs Optionen für dieses Format sind verfügbar. Dieses Flag ist eine bitweise Kombination aus einem oder mehreren der unterschiedlichen Werte im enumerierten oleuipasteflag-Typ.

*CF*<br/>
Das hinzu zufügende Zwischenablage Format.

*TYMED*<br/>
Die in diesem Format verfügbaren Medientypen. Dies ist eine bitweise Kombination aus einem oder mehreren Werten im TYMED-enumerierten Typ.

*nformatid*<br/>
Die ID der Zeichenfolge, die dieses Format identifiziert. Das Format dieser Zeichenfolge sind zwei separate Zeichen folgen, die durch ein "\n"-Zeichen getrennt sind. Die erste Zeichenfolge ist die gleiche, die im *lpstreformat* -Parameter übergeben wird, und die zweite Zeichenfolge entspricht dem *lpstrauresult* -Parameter.

*benableicon*<br/>
Flag, das bestimmt, ob das Kontrollkästchen als Symbol anzeigen aktiviert ist, wenn dieses Format im Listenfeld ausgewählt wird.

*bLink*<br/>
Flag, das bestimmt, ob das Optionsfeld Link einfügen aktiviert ist, wenn dieses Format im Listenfeld ausgewählt wird.

### <a name="remarks"></a>Hinweise

Diese Funktion kann aufgerufen werden, um entweder Standardformate (z. b. CF_TEXT oder CF_TIFF oder benutzerdefinierte Formate hinzuzufügen, die von der Anwendung beim System registriert wurden. Weitere Informationen zum Einfügen von Datenobjekten in Ihre Anwendung finden Sie im Artikel [Datenobjekte und Datenquellen: Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).

Weitere Informationen finden Sie unter dem [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) -Enumerationstyp und der [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur in der Windows SDK.

Weitere Informationen finden Sie unter dem enumerierten [oleuipasteflag](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) -Typ in der Windows SDK.

##  <a name="addlinkentry"></a>COlePasteSpecialDialog:: addlinkentry

Fügt der Liste der unterstützten Zwischenablage Formate einen neuen Eintrag hinzu.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parameter

*CF*<br/>
Das hinzu zufügende Zwischenablage Format.

### <a name="return-value"></a>Rückgabewert

Eine [oleuipasteflag](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) -Struktur, die die Informationen für den neuen Link Eintrag enthält.

##  <a name="addstandardformats"></a>COlePasteSpecialDialog:: addstandardformats

Mit dieser Funktion können Sie die folgenden Zwischenablage Formate zur Liste der Formate hinzufügen, die Ihre Anwendung in einem Vorgang zum Einfügen von Sondervorgängen unterstützen kann:

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parameter

*benablelink*<br/>
Flag, das bestimmt, ob CF_LINKSOURCE der Liste der Formate hinzugefügt werden soll, die von der Anwendung eingefügt werden können.

### <a name="remarks"></a>Hinweise

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Eingebettetes Objekt"**

- optional **"Link Quelle"**

Diese Formate werden verwendet, um Einbettungen und Verknüpfungen zu unterstützen.

##  <a name="colepastespecialdialog"></a>COlePasteSpecialDialog:: COlePasteSpecialDialog

Erstellt ein `COlePasteSpecialDialog`-Objekt.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Erstellungsflag enthält eine beliebige Anzahl der folgenden Flags, die mithilfe des bitweisen OR-Operators kombiniert werden:

- PSF_SELECTPASTE gibt an, dass beim Aufrufen des Dialog Felds zunächst das Optionsfeld einfügen aktiviert wird. Kann nicht in Kombination mit PSF_SELECTPASTELINK verwendet werden. Dies ist die Standardeinstellung.

- PSF_SELECTPASTELINK gibt an, dass das Optionsfeld Link einfügen anfänglich aktiviert wird, wenn das Dialogfeld aufgerufen wird. Kann nicht in Kombination mit PSF_SELECTPASTE verwendet werden.

- PSF_CHECKDISPLAYASICON gibt an, dass das Kontrollkästchen als Symbol anzeigen zuerst überprüft wird, wenn das Dialogfeld aufgerufen wird.

- PSF_SHOWHELP gibt an, dass die Schaltfläche Hilfe angezeigt wird, wenn das Dialogfeld aufgerufen wird.

*pDataObject*<br/>
Verweist auf das [COleDataObject-Objekt](../../mfc/reference/coledataobject-class.md) , das eingefügt werden soll. Wenn dieser Wert NULL ist, wird der `COleDataObject` aus der Zwischenablage abgerufen.

*pparser*<br/>
Zeigt auf das übergeordnete oder Besitzer Fenster Objekt (vom Typ "`CWnd`"), zu dem das Dialog Objekt gehört. Wenn er NULL ist, wird das übergeordnete Fenster des Dialog Felds auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Hinweise

Diese Funktion erstellt nur ein `COlePasteSpecialDialog` Objekt. Um das Dialogfeld anzuzeigen, müssen Sie die Funktion [DoModal](#domodal) aufrufen.

Weitere Informationen finden Sie unter dem enumerierten [oleuipasteflag](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) -Typ in der Windows SDK.

##  <a name="createitem"></a>COlePasteSpecialDialog:: kreateitem

Erstellt das neue Element, das im Dialogfeld "besonderes einfügen" ausgewählt wurde.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parameter

*pnetwitem*<br/>
Verweist auf eine `COleClientItem`-Instanz. Darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Element erfolgreich erstellt wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion sollte nur aufgerufen werden, nachdem die [Domäne](#domodal) IDOK zurückgegeben hat.

##  <a name="domodal"></a>COlePasteSpecialDialog::D omodal

Zeigt das OLE-Dialogfeld "speziell einfügen" an.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Abschluss Status für das Dialogfeld. Einer der folgenden Werte:

- IDOK, wenn das Dialogfeld erfolgreich angezeigt wurde.

- IDCANCEL, wenn der Benutzer das Dialogfeld abgebrochen hat.

- Idabort, wenn ein Fehler aufgetreten ist. Wenn idabort zurückgegeben wird, können Sie die `COleDialog::GetLastError` Member-Funktion abrufen, um weitere Informationen zum aufgetretenen Fehlertyp abzurufen. Eine Auflistung möglicher Fehler finden Sie unter der [oleuipastespecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) -Funktion in der Windows SDK.

### <a name="remarks"></a>Hinweise

Wenn Sie die verschiedenen Dialogfeld-Steuerelemente durch Festlegen der Elemente der [m_ps](#m_ps) Struktur initialisieren möchten, sollten Sie dies vor dem Aufrufen von `DoModal`tun, nachdem das Dialogfeld Objekt erstellt wurde.

Wenn `DoModal` IDOK zurückgibt, können Sie andere Element Funktionen aufrufen, um die Einstellungen oder Informationen einzugeben, die der Benutzer im Dialogfeld abruft.

##  <a name="getdrawaspect"></a>COlePasteSpecialDialog:: getdrawaspect

Bestimmt, ob der Benutzer das ausgewählte Element als Symbol anzeigt.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Rückgabewert

Die Methode, die zum Rendering des-Objekts erforderlich ist.

- DVASPECT_CONTENT zurückgegeben, wenn das Kontrollkästchen als Symbol anzeigen beim Verwerfen des Dialog Felds nicht überprüft wurde.

- DVASPECT_ICON zurückgegeben, wenn das Kontrollkästchen als Symbol anzeigen beim Verwerfen des Dialog Felds aktiviert wurde.

### <a name="remarks"></a>Hinweise

Diese Funktion nur dann aufzurufen, nachdem die [Domäne](#domodal) IDOK zurückgegeben hat.

Weitere Informationen zum Zeichnen-Aspekt finden Sie in der [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur im Windows SDK.

##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog:: getikonicmetafile

Ruft die Metadatendatei ab, die dem vom Benutzer ausgewählten Element zugeordnet ist.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Rückgabewert

Das Handle für die Metadatei, das den ikonischen Aspekt des ausgewählten Elements enthält, wenn das Kontrollkästchen als Symbol anzeigen beim Verwerfen des Dialog Felds ausgewählt wurde, indem Sie auf **OK**klicken. andernfalls NULL.

##  <a name="getpasteindex"></a>COlePasteSpecialDialog:: getpasteindex

Ruft den Indexwert ab, der dem vom Benutzer ausgewählten Eintrag zugeordnet ist.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der Index im Array der `OLEUIPASTEENTRY` Strukturen, die vom Benutzer ausgewählt wurden. Das Format, das dem ausgewählten Index entspricht, sollte beim Ausführen des Einfügevorgangs verwendet werden.

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie in der [oleuipasteentry](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) -Struktur in der Windows SDK.

##  <a name="getselectiontype"></a>COlePasteSpecialDialog:: GetSelectionType

Bestimmt den vom Benutzer vorgenommenen Auswahltyp.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den Typ der getroffenen Auswahl zurück.

### <a name="remarks"></a>Hinweise

Die Rückgabetyp Werte werden durch den `Selection` Enumerationstyp angegeben, der in der `COlePasteSpecialDialog`-Klasse deklariert ist.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Die folgenden Werte werden in kurze Form der folgenden Werte beschrieben:

- `COlePasteSpecialDialog::pasteLink` das Optionsfeld Link einfügen aktiviert wurde und das ausgewählte Format ein Standardmäßiges OLE-Format war.

- `COlePasteSpecialDialog::pasteNormal` das Optionsfeld einfügen aktiviert und das ausgewählte Format ein Standardmäßiges OLE-Format war.

- `COlePasteSpecialDialog::pasteOther` das ausgewählte Format kein standardmäßiges OLE-Format ist.

- `COlePasteSpecialDialog::pasteStatic` das ausgewählte Format eine Metadatei ist.

##  <a name="m_ps"></a>COlePasteSpecialDialog:: m_ps

Struktur des Typs oleuipastespecial, mit der das Verhalten des Dialog Felds spezielles einfügen gesteuert wird.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Hinweise

Member dieser Struktur können direkt oder über Element Funktionen geändert werden.

Weitere Informationen finden Sie in der [oleuipastespecial](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) -Struktur in der Windows SDK.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)
