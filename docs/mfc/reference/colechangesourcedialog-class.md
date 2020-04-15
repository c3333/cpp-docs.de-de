---
title: COleChangeSourceDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
ms.openlocfilehash: 78da0a495de6ea951deab984550756a2d6f3e2bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321876"
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog-Klasse

Wird für das OLE-Dialogfeld "Quelle ändern" verwendet.

## <a name="syntax"></a>Syntax

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Erstellt ein `COleChangeSourceDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|Zeigt das Dialogfeld OLE-Änderungsquelle an.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Ruft den vollständigen Quellanzeigenamen ab.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Ruft den Dateinamen aus dem Quellnamen ab.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Ruft das Präfix der vorherigen Quelle ab.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Ruft den Elementnamen aus dem Quellnamen ab.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Ruft das Präfix der neuen Quelle ab|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Gibt an, ob die Quelle gültig ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Eine Struktur, die das Verhalten des Dialogfelds steuert.|

## <a name="remarks"></a>Bemerkungen

Erstellen Sie ein `COleChangeSourceDialog` Klassenobjekt, wenn Sie dieses Dialogfeld aufrufen möchten. Nachdem `COleChangeSourceDialog` ein Objekt erstellt wurde, können Sie die [m_cs](#m_cs) Struktur verwenden, um die Werte oder Zustände von Steuerelementen im Dialogfeld zu initialisieren. Die `m_cs` Struktur ist vom Typ [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew). Weitere Informationen zur Verwendung dieser Dialogklasse finden Sie in der [DoModal-Memberfunktion.](#domodal)

Weitere Informationen finden Sie in der [OLEUICHANGESOURCE-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) in Windows SDK.

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="colechangesourcedialogcolechangesourcedialog"></a><a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog

Diese Funktion erstellt `COleChangeSourceDialog` ein Objekt.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeiger auf das verknüpfte [COleClientItem,](../../mfc/reference/coleclientitem-class.md) dessen Quelle aktualisiert werden soll.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ `CWnd`), zu dem das Dialogobjekt gehört. Wenn es NULL ist, wird das übergeordnete Fenster des Dialogfelds auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Um das Dialogfeld anzuzeigen, rufen Sie die [DoModal-Funktion](#domodal) auf.

Weitere Informationen finden Sie in der [OLEUICHANGESOURCE-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) und der [OleUIChangeSource-Funktion](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) in Windows SDK.

## <a name="colechangesourcedialogdomodal"></a><a name="domodal"></a>COleChangeSourceDialog::DoModal

Rufen Sie diese Funktion auf, um das Dialogfeld OLE-Änderungsquelle anzuzeigen.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Abschlussstatus für das Dialogfeld. Einer der folgenden Werte:

- IDOK, wenn das Dialogfeld erfolgreich angezeigt wurde.

- IDCANCEL, wenn der Benutzer das Dialogfeld abgebrochen hat.

- IDABORT, wenn ein Fehler aufgetreten ist. Wenn IDABORT zurückgegeben wird, rufen Sie die [Memberfunktion COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) auf, um weitere Informationen über den Fehlertyp zu erhalten. Eine Liste möglicher Fehler finden Sie in der [OleUIChangeSource-Funktion](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) in Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Dialogfeldsteuerelemente initialisieren [m_cs](#m_cs) möchten, indem Sie Elemente `DoModal`der m_cs Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

Wenn `DoModal` IDOK zurückgegeben wird, können Sie Memberfunktionen aufrufen, um vom Benutzer eingegebene Einstellungen oder Informationen aus dem Dialogfeld abzurufen. Die folgende Liste benennt typische Abfragefunktionen:

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

## <a name="colechangesourcedialoggetdisplayname"></a><a name="getdisplayname"></a>COleChangeSourceDialog::GetDisplayName

Rufen Sie diese Funktion auf, um den vollständigen Anzeigenamen für das verknüpfte Clientelement abzurufen.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Rückgabewert

Der vollständige Quellanzeigename (Moniker) für das im Konstruktor angegebene [COleClientItem.](../../mfc/reference/coleclientitem-class.md)

## <a name="colechangesourcedialoggetfilename"></a><a name="getfilename"></a>COleChangeSourceDialog::GetFileName

Rufen Sie diese Funktion auf, um den Dateimoniker-Teil des Anzeigenamens für das verknüpfte Clientelement abzurufen.

```
CString GetFileName();
```

### <a name="return-value"></a>Rückgabewert

Der Dateimonikerteil des Quellanzeigenamens für das im Konstruktor angegebene [COleClientItem.](../../mfc/reference/coleclientitem-class.md)

### <a name="remarks"></a>Bemerkungen

Der Dateimoniker gibt zusammen mit dem Elementmoniker den vollständigen Anzeigenamen an.

## <a name="colechangesourcedialoggetfromprefix"></a><a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix

Rufen Sie diese Funktion auf, um die vorherige Präfixzeichenfolge für die Quelle abzurufen.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Rückgabewert

Die vorherige Präfixzeichenfolge der Quelle.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion erst auf, nachdem [DoModal](#domodal) IDOK zurückgegeben hat.

Dieser Wert stammt `lpszFrom` direkt vom Member der [OLEUICHANGESOURCE-Struktur.](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)

Weitere Informationen finden Sie in der [OLEUICHANGESOURCE-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) in Windows SDK.

## <a name="colechangesourcedialoggetitemname"></a><a name="getitemname"></a>COleChangeSourceDialog::GetItemName

Rufen Sie diese Funktion auf, um den Elementmonikerteil des Anzeigenamens für das verknüpfte Clientelement abzurufen.

```
CString GetItemName();
```

### <a name="return-value"></a>Rückgabewert

Der Elementmonikerteil des Quellanzeigenamens für das im Konstruktor angegebene [COleClientItem.](../../mfc/reference/coleclientitem-class.md)

### <a name="remarks"></a>Bemerkungen

Der Dateimoniker gibt zusammen mit dem Elementmoniker den vollständigen Anzeigenamen an.

## <a name="colechangesourcedialoggettoprefix"></a><a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix

Rufen Sie diese Funktion auf, um die neue Präfixzeichenfolge für die Quelle abzurufen.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Rückgabewert

Die neue Präfixzeichenfolge der Quelle.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion erst auf, nachdem [DoModal](#domodal) IDOK zurückgegeben hat.

Dieser Wert stammt `lpszTo` direkt vom Member der [OLEUICHANGESOURCE-Struktur.](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)

Weitere Informationen finden Sie in der [OLEUICHANGESOURCE-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) in Windows SDK.

## <a name="colechangesourcedialogm_cs"></a><a name="m_cs"></a>COleChangeSourceDialog::m_cs

Dieser Datenmember ist eine Struktur des Typs [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Bemerkungen

`OLEUICHANGESOURCE`wird verwendet, um das Verhalten des Dialogfelds OLE Change Source zu steuern. Mitglieder dieser Struktur können direkt geändert werden.

Weitere Informationen finden Sie in der [OLEUICHANGESOURCE-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) in Windows SDK.

## <a name="colechangesourcedialogisvalidsource"></a><a name="isvalidsource"></a>COleChangeSourceDialog::IsValidSource

Rufen Sie diese Funktion auf, um festzustellen, ob die neue Quelle gültig ist.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die neue Quelle gültig ist, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion erst auf, nachdem [DoModal](#domodal) IDOK zurückgegeben hat.

Weitere Informationen finden Sie in der [OLEUICHANGESOURCE-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) in Windows SDK.

## <a name="see-also"></a>Siehe auch

[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)
