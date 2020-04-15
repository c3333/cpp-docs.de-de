---
title: COleConvertDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
ms.openlocfilehash: 6d6690b8d06df29ce9fcd323eb8724009ee3cca9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366165"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog-Klasse

Weitere Informationen finden Sie in der [OLEUICONVERT-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) im Windows SDK.

## <a name="syntax"></a>Syntax

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ColeConvertDialog::COleConvertDialog](#coleconvertdialog)|Erstellt ein `COleConvertDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleConvertDialog::DoConvert](#doconvert)|Führt die im Dialogfeld angegebene Konvertierung aus.|
|[COleConvertDialog::DoModal](#domodal)|Zeigt das Dialogfeld OLE-Änderungselement an.|
|[COleConvertDialog::GetClassID](#getclassid)|Ruft die CLSID ab, die dem ausgewählten Element zugeordnet ist.|
|[ColeConvertDialog::GetDrawAspect](#getdrawaspect)|Gibt an, ob ein Element als Symbol gezeichnet werden soll.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Ruft ein Handle für die Metadatei ab, die der ikonischen Form dieses Elements zugeordnet ist.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Ruft den ausgewählten Auswahltyp ab.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Eine Struktur, die das Verhalten des Dialogfelds steuert.|

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Anwendungs-Wizard-generierter Containercode verwendet diese Klasse.

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>ColeConvertDialog::COleConvertDialog

Erstellt nur `COleConvertDialog` ein Objekt.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeigt auf das Element, das konvertiert oder aktiviert werden soll.

*dwFlags*<br/>
Erstellungsflag, das eine beliebige Anzahl der folgenden Werte enthält, die mit dem Bit-oder-Operator kombiniert werden:

- CF_SELECTCONVERTTO Gibt an, dass das Optionsfeld "In konvertieren" zunächst ausgewählt wird, wenn das Dialogfeld aufgerufen wird. Dies ist die Standardoption.

- CF_SELECTACTIVATEAS Gibt an, dass das Optionsfeld Aktivieren als zunächst ausgewählt wird, wenn das Dialogfeld aufgerufen wird.

- CF_SETCONVERTDEFAULT Gibt an, dass die Klasse, `clsidConvertDefault` deren `m_cv` CLSID vom Member der Struktur angegeben wird, als Standardauswahl im Klassenlistenfeld verwendet wird, wenn das Optionsfeld "In konvertieren" ausgewählt ist.

- CF_SETACTIVATEDEFAULT Gibt an, dass die Klasse, `clsidActivateDefault` deren `m_cv` CLSID vom Member der Struktur angegeben wird, als Standardauswahl im Klassenlistenfeld verwendet wird, wenn das Optionsfeld Aktivieren als ausgewählt ist.

- CF_SHOWHELPBUTTON Gibt an, dass die Hilfeschaltfläche angezeigt wird, wenn das Dialogfeld aufgerufen wird.

*pClassID*<br/>
Zeigt auf die CLSID des zu konvertierenden oder zu aktivierenden Elements. Wenn NULL, wird die clSID verwendet, die *pItem* zugeordnet ist.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ `CWnd`), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogfelds auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Um das Dialogfeld anzuzeigen, rufen Sie die [DoModal-Funktion](#domodal) auf.

Weitere Informationen finden Sie unter [CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm) und die [OLEUICONVERT-Struktur.](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)

## <a name="coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvertDialog::DoConvert

Rufen Sie diese Funktion auf, nachdem Sie erfolgreich von [DoModal](#domodal)zurückgegeben wurden, um ein Objekt vom Typ [COleClientItem](../../mfc/reference/coleclientitem-class.md)zu konvertieren oder zu aktivieren.

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeigt auf das Element, das konvertiert oder aktiviert werden soll. Lässt keine NULL-Werte zu.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das Element wird entsprechend den vom Benutzer im Dialogfeld Konvertieren ausgewählten Informationen konvertiert oder aktiviert.

## <a name="coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvertDialog::DoModal

Rufen Sie diese Funktion auf, um das Dialogfeld OLE Konvertieren anzuzeigen.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Abschlussstatus für das Dialogfeld. Einer der folgenden Werte:

- IDOK, wenn das Dialogfeld erfolgreich angezeigt wurde.

- IDCANCEL, wenn der Benutzer das Dialogfeld abgebrochen hat.

- IDABORT, wenn ein Fehler aufgetreten ist. Wenn IDABORT zurückgegeben wird, rufen Sie die [Memberfunktion COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) auf, um weitere Informationen über den Fehlertyp zu erhalten. Eine Liste möglicher Fehler finden Sie in der [OleUIConvert-Funktion](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Dialogfeldsteuerelemente initialisieren [m_cv](#m_cv) möchten, indem Sie Elemente `DoModal`der m_cv Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

Wenn `DoModal` IDOK zurückgegeben wird, können Sie andere Memberfunktionen aufrufen, um die Einstellungen oder Informationen abzurufen, die vom Benutzer in das Dialogfeld eingegeben wurden.

## <a name="coleconvertdialoggetclassid"></a><a name="getclassid"></a>COleConvertDialog::GetClassID

Rufen Sie diese Funktion auf, um die CLSID abzurufen, die dem Element zugeordnet ist, das der Benutzer im Dialogfeld Konvertieren ausgewählt hat.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Rückgabewert

Die CLSID, die dem Element zugeordnet ist, das im Dialogfeld Konvertieren ausgewählt wurde.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion erst auf, nachdem [DoModal](#domodal) IDOK zurückgegeben hat.

Weitere Informationen finden Sie unter [CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm) im Windows SDK.

## <a name="coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>ColeConvertDialog::GetDrawAspect

Rufen Sie diese Funktion auf, um zu bestimmen, ob der Benutzer das ausgewählte Element als Symbol anzeigen möchte.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Rückgabewert

Die Methode, die zum Rendern des Objekts erforderlich ist.

- DVASPECT_CONTENT zurückgegeben, wenn das Kontrollkästchen Als Symbol anzeigen nicht aktiviert war.

- DVASPECT_ICON zurückgegeben, wenn das Kontrollkästchen Als Symbol anzeigen aktiviert war.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion erst auf, nachdem [DoModal](#domodal) IDOK zurückgegeben hat.

Weitere Informationen zum Zeichnungsaspekt finden Sie in der [FORMATETC-Datenstruktur](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

## <a name="coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile

Rufen Sie diese Funktion auf, um ein Handle für die Metadatei abzurufen, das den ikonischen Aspekt des ausgewählten Elements enthält.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Rückgabewert

Das Handle für die Metadatei, das den ikonischen Aspekt des ausgewählten Elements enthält, wenn das Kontrollkästchen Als Symbol anzeigen aktiviert wurde, als das Dialogfeld durch Auswahl von OK verworfen wurde. andernfalls NULL.

## <a name="coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvertDialog::GetSelectionType

Rufen Sie diese Funktion auf, um den im Dialogfeld Konvertieren ausgewählten Konvertierungstyp zu bestimmen.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Rückgabewert

Art der getroffenen Auswahl.

### <a name="remarks"></a>Bemerkungen

Die Rückgabetypwerte werden `Selection` durch den in der `COleConvertDialog` Klasse deklarierten Enumerationstyp angegeben.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

Kurze Beschreibungen dieser Werte folgen:

- `COleConvertDialog::noConversion`Wird zurückgegeben, wenn entweder das Dialogfeld abgebrochen wurde oder der Benutzer keine Konvertierung ausgewählt hat. Bei `COleConvertDialog::DoModal` der Rückgabe von IDOK ist es möglich, dass der Benutzer ein anderes Symbol als das zuvor ausgewählte ausgewählt hat.

- `COleConvertDialog::convertItem`Wenn das Optionsfeld "In konvertieren" aktiviert wurde, hat der `DoModal` Benutzer ein anderes Element ausgewählt, in das konvertiert werden soll, und IDOK zurückgegeben.

- `COleConvertDialog::activateAs`Wenn das Optionsfeld Aktivieren aktiviert wurde, hat der Benutzer ein `DoModal` anderes zu aktivierendes Element ausgewählt und IDOK zurückgegeben.

## <a name="coleconvertdialogm_cv"></a><a name="m_cv"></a>COleConvertDialog::m_cv

Struktur des Typs OLEUICONVERT, die zum Steuern des Verhaltens des Dialogfelds Konvertieren verwendet wird.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Bemerkungen

Member dieser Struktur können entweder direkt oder über Memberfunktionen geändert werden.

Weitere Informationen finden Sie in der [OLEUICONVERT-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)
