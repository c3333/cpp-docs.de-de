---
title: COleInsertDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
ms.openlocfilehash: b5de4ff5daa80e1d8727444a4cfd275597e18c08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374975"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog-Klasse

Wird für das OLE-Dialogfeld "Objekt einfügen" verwendet.

## <a name="syntax"></a>Syntax

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Erstellt ein `COleInsertDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|Erstellt das im Dialogfeld ausgewählte Element.|
|[COleInsertDialog::DoModal](#domodal)|Zeigt das Dialogfeld OLE Insert Object an.|
|[COleInsertDialog::GetClassID](#getclassid)|Ruft die CLSID ab, die dem ausgewählten Element zugeordnet ist.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Gibt an, ob das Element als Symbol gezeichnet werden soll.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Ruft ein Handle für die Metadatei ab, die der ikonischen Form dieses Elements zugeordnet ist.|
|[COleInsertDialog::GetPathName](#getpathname)|Ruft den vollständigen Pfad zu der im Dialogfeld ausgewählten Datei ab.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Ruft den ausgewählten Objekttyp ab.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Eine Struktur vom Typ OLEUIINSERTOBJECT, die das Verhalten des Dialogfelds steuert.|

## <a name="remarks"></a>Bemerkungen

Erstellen Sie ein `COleInsertDialog` Klassenobjekt, wenn Sie dieses Dialogfeld aufrufen möchten. Nachdem `COleInsertDialog` ein Objekt erstellt wurde, können Sie die [m_io](#m_io) Struktur verwenden, um die Werte oder Zustände von Steuerelementen im Dialogfeld zu initialisieren. Die `m_io` Struktur ist vom Typ OLEUIINSERTOBJECT. Weitere Informationen zur Verwendung dieser Dialogklasse finden Sie in der [DoModal-Memberfunktion.](#domodal)

> [!NOTE]
> Anwendungs-Wizard-generierter Containercode verwendet diese Klasse.

Weitere Informationen finden Sie in der [OLEUIINSERTOBJECT-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) im Windows SDK.

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="coleinsertdialogcoleinsertdialog"></a><a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog

Diese Funktion erstellt `COleInsertDialog` nur ein Objekt.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Erstellungsflag, das eine beliebige Anzahl der folgenden Werte enthält, die mit dem Bitwise-OR-Operator kombiniert werden sollen:

- IOF_SHOWHELP Gibt an, dass die Hilfeschaltfläche angezeigt wird, wenn das Dialogfeld aufgerufen wird.

- IOF_SELECTCREATENEW Gibt an, dass das Optionsfeld "Neue" erstellen zunächst ausgewählt wird, wenn das Dialogfeld aufgerufen wird. Dies ist die Standardeinstellung und kann nicht mit IOF_SELECTCREATEFROMFILE verwendet werden.

- IOF_SELECTCREATEFROMFILE Gibt an, dass das Optionsfeld Datei erstellen zunächst ausgewählt wird, wenn das Dialogfeld aufgerufen wird. Kann nicht mit IOF_SELECTCREATENEW verwendet werden.

- IOF_CHECKLINK Gibt an, dass das Kontrollkästchen Verknüpfung zunächst aktiviert wird, wenn das Dialogfeld aufgerufen wird.

- IOF_DISABLELINK Gibt an, dass das Kontrollkästchen Verknüpfung deaktiviert wird, wenn das Dialogfeld aufgerufen wird.

- IOF_CHECKDISPLAYASICON Gibt an, dass das Kontrollkästchen Als Symbol anzeigen anfänglich aktiviert wird, das aktuelle Symbol angezeigt wird und die Schaltfläche Symbol ändern aktiviert wird, wenn das Dialogfeld aufgerufen wird.

- IOF_VERIFYSERVERSEXIST Gibt an, dass das Dialogfeld die Klassen überprüfen soll, die es dem Listenfeld hinzufügt, indem sichergestellt wird, dass die in der Registrierungsdatenbank angegebenen Server vorhanden sind, bevor das Dialogfeld angezeigt wird. Das Festlegen dieses Flags kann die Leistung erheblich beeinträchtigen.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ `CWnd`), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogobjekts auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Um das Dialogfeld anzuzeigen, rufen Sie die [DoModal-Funktion](#domodal) auf.

## <a name="coleinsertdialogcreateitem"></a><a name="createitem"></a>COleInsertDialog::CreateItem

Rufen Sie diese Funktion auf, um ein Objekt vom Typ [COleClientItem](../../mfc/reference/coleclientitem-class.md) nur zu erstellen, wenn [DoModal](#domodal) IDOK zurückgibt.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeigt auf das zu erstellende Element.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn ein Element erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie müssen `COleClientItem` das Objekt zuweisen, bevor Sie diese Funktion aufrufen können.

## <a name="coleinsertdialogdomodal"></a><a name="domodal"></a>COleInsertDialog::DoModal

Rufen Sie diese Funktion auf, um das Dialogfeld OLE Insert Object anzuzeigen.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Einer der folgenden Werte:

`COleInsertDialog::DocObjectsOnly`fügt nur DocObjects ein.

`COleInsertDialog::ControlsOnly`fügt nur ActiveX-Steuerelemente ein.

Zero fügt weder ein DocObject- noch ein ActiveX-Steuerelement ein. Dieser Wert führt zu derselben Implementierung wie der erste oben aufgeführte Prototyp.

### <a name="return-value"></a>Rückgabewert

Abschlussstatus für das Dialogfeld. Einer der folgenden Werte:

- IDOK, wenn das Dialogfeld erfolgreich angezeigt wurde.

- IDCANCEL, wenn der Benutzer das Dialogfeld abgebrochen hat.

- IDABORT, wenn ein Fehler aufgetreten ist. Wenn IDABORT zurückgegeben wird, rufen Sie die [Memberfunktion COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) auf, um weitere Informationen über den Fehlertyp zu erhalten. Eine Liste möglicher Fehler finden Sie in der [OleUIInsertObject-Funktion](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Dialogfeldsteuerelemente initialisieren [m_io](#m_io) möchten, indem Sie Elemente `DoModal`der m_io Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

Wenn `DoModal` IDOK zurückgegeben wird, können Sie andere Memberfunktionen aufrufen, um die Einstellungen oder Informationen, die vom Benutzer in das Dialogfeld eingegeben wurden, abzurufen.

## <a name="coleinsertdialoggetclassid"></a><a name="getclassid"></a>COleInsertDialog::GetClassID

Rufen Sie diese Funktion auf, um die CLSID nur dann abzurufen, `COleInsertDialog::createNewItem`wenn [DoModal](#domodal) IDOK zurückgibt und der Auswahltyp ist.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die CLSID zurück, die dem ausgewählten Element zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm) im Windows SDK.

## <a name="coleinsertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect

Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer das ausgewählte Element als Symbol anzeigen möchte.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Rückgabewert

Die Methode, die zum Rendern des Objekts erforderlich ist.

- DVASPECT_CONTENT zurückgegeben, wenn das Kontrollkästchen Als Symbol anzeigen nicht aktiviert war.

- DVASPECT_ICON zurückgegeben, wenn das Kontrollkästchen Als Symbol anzeigen aktiviert war.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion nur auf, wenn [DoModal](#domodal) IDOK zurückgibt.

Weitere Informationen zum Zeichnungsaspekt finden Sie unter [FORMATETC-Datenstruktur](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

## <a name="coleinsertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile

Rufen Sie diese Funktion auf, um ein Handle für die Metadatei abzurufen, das den ikonischen Aspekt des ausgewählten Elements enthält.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Rückgabewert

Das Handle für die Metadatei, das den ikonischen Aspekt des ausgewählten Elements enthält, wenn das Kontrollkästchen Als Symbol anzeigen aktiviert wurde, als das Dialogfeld durch Auswahl von **OK**verworfen wurde; andernfalls NULL.

## <a name="coleinsertdialoggetpathname"></a><a name="getpathname"></a>COleInsertDialog::GetPathName

Rufen Sie diese Funktion auf, um den vollständigen Pfad der ausgewählten Datei `COleInsertDialog::createNewItem`nur dann abzurufen, wenn [DoModal](#domodal) IDOK zurückgibt und der Auswahltyp nicht ist.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Rückgabewert

Der vollständige Pfad zur im Dialogfeld ausgewählten Datei. Wenn der Auswahltyp ist `createNewItem`, gibt `CString` diese Funktion im Veröffentlichungsmodus einen bedeutungslosen Wert zurück oder verursacht eine Assertion im Debugmodus.

## <a name="coleinsertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleInsertDialog::GetSelectionType

Rufen Sie diese Funktion auf, um den Auswahltyp abzurufen, der ausgewählt wurde, wenn das Dialogfeld Objekt einfügen verworfen wurde, indem Sie **OK**auswählen.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Rückgabewert

Art der getroffenen Auswahl.

### <a name="remarks"></a>Bemerkungen

Die Rückgabetypwerte werden `Selection` durch den in der `COleInsertDialog` Klasse deklarierten Enumerationstyp angegeben.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Kurze Beschreibungen dieser Werte folgen:

- `COleInsertDialog::createNewItem`Das Optionsfeld Neu erstellen wurde ausgewählt.

- `COleInsertDialog::insertFromFile`Das Optionsfeld Datei erstellen wurde aktiviert, und das Kontrollkästchen Verknüpfung wurde nicht aktiviert.

- `COleInsertDialog::linkToFile`Das Optionsfeld Datei erstellen wurde aktiviert, und das Kontrollkästchen Verknüpfung wurde aktiviert.

## <a name="coleinsertdialogm_io"></a><a name="m_io"></a>COleInsertDialog::m_io

Struktur vom Typ OLEUIINSERTOBJECT, die zum Steuern des Verhaltens des Dialogfelds Objekt einfügen verwendet wird.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Bemerkungen

Member dieser Struktur können entweder direkt oder über Memberfunktionen geändert werden.

Weitere Informationen finden Sie in der [OLEUIINSERTOBJECT-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)
