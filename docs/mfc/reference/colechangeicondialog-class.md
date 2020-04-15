---
title: COleChangeIconDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 6cdc0ed6bfa4765817de8b7628f339db5e7e5bf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369621"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog-Klasse

Wird für das OLE-Dialogfeld "Symbol ändern" verwendet.

## <a name="syntax"></a>Syntax

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Erstellt ein `COleChangeIconDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Führt die im Dialogfeld angegebene Änderung aus.|
|[COleChangeIconDialog::DoModal](#domodal)|Zeigt das Dialogfeld OLE 2 Symbol ändern an.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Ruft ein Handle für die Metadatei ab, die der ikonischen Form dieses Elements zugeordnet ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Eine Struktur, die das Verhalten des Dialogfelds steuert.|

## <a name="remarks"></a>Bemerkungen

Erstellen Sie ein `COleChangeIconDialog` Klassenobjekt, wenn Sie dieses Dialogfeld aufrufen möchten. Nachdem `COleChangeIconDialog` ein Objekt erstellt wurde, können Sie die [m_ci](#m_ci) Struktur verwenden, um die Werte oder Zustände von Steuerelementen im Dialogfeld zu initialisieren. Die `m_ci` Struktur ist vom Typ OLEUICHANGEICON. Weitere Informationen zur Verwendung dieser Dialogklasse finden Sie in der [DoModal-Memberfunktion.](#domodal)

Weitere Informationen finden Sie in der [OLEUICHANGEICON-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) im Windows SDK.

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog

Diese Funktion erstellt `COleChangeIconDialog` nur ein Objekt.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeigt auf das zu konvertierende Element.

*dwFlags*<br/>
Erstellungsflag, das eine beliebige Anzahl der folgenden Werte enthält, die mit dem Bit-oder-Operator kombiniert werden:

- CIF_SELECTCURRENT Gibt an, dass das aktuelle Optionsfeld zunächst ausgewählt wird, wenn das Dialogfeld aufgerufen wird. Dies ist die Standardoption.

- CIF_SELECTDEFAULT Gibt an, dass das Standard-Optionsfeld zunächst ausgewählt wird, wenn das Dialogfeld aufgerufen wird.

- CIF_SELECTFROMFILE Gibt an, dass das Optionsfeld Von Datei zunächst ausgewählt wird, wenn das Dialogfeld aufgerufen wird.

- CIF_SHOWHELP Gibt an, dass die Hilfeschaltfläche angezeigt wird, wenn das Dialogfeld aufgerufen wird.

- CIF_USEICONEXE Gibt an, dass das Symbol aus der `szIconExe` ausführbaren Datei extrahiert werden soll, die im Feld [m_ci](#m_ci) angegeben ist, anstatt aus dem Typ abgerufen zu werden. Dies ist nützlich zum Einbetten oder Verknüpfen mit Nicht-OLE-Dateien.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ `CWnd`), zu dem das Dialogobjekt gehört. Wenn es NULL ist, wird das übergeordnete Fenster des Dialogfelds auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Um das Dialogfeld anzuzeigen, rufen Sie die [DoModal-Funktion](#domodal) auf.

Weitere Informationen finden Sie in der [OLEUICHANGEICON-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) im Windows SDK.

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a>COleChangeIconDialog::DoChangeIcon

Rufen Sie diese Funktion auf, um das Symbol, das das Element darstellt, in das im Dialogfeld ausgewählte Element zu ändern, nachdem [DoModal](#domodal) IDOK zurückgegeben hat.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeigt auf das Element, dessen Symbol sich ändert.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Änderung erfolgreich ist; andernfalls 0.

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a>COleChangeIconDialog::DoModal

Rufen Sie diese Funktion auf, um das Dialogfeld OLE Change Icon anzuzeigen.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Abschlussstatus für das Dialogfeld. Einer der folgenden Werte:

- IDOK, wenn das Dialogfeld erfolgreich angezeigt wurde.

- IDCANCEL, wenn der Benutzer das Dialogfeld abgebrochen hat.

- IDABORT, wenn ein Fehler aufgetreten ist. Wenn IDABORT zurückgegeben wird, rufen Sie die `COleDialog::GetLastError` Memberfunktion auf, um weitere Informationen über den Fehlertyp zu erhalten, der aufgetreten ist. Eine Liste möglicher Fehler finden Sie in der [OleUIChangeIcon-Funktion](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Dialogfeldsteuerelemente initialisieren [m_ci](#m_ci) möchten, indem Sie Elemente `DoModal`der m_ci Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

Wenn `DoModal` IDOK zurückgegeben wird, können Sie andere Memberfunktionen aufrufen, um die Einstellungen oder Informationen abzurufen, die vom Benutzer in das Dialogfeld eingegeben wurden.

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

Rufen Sie diese Funktion auf, um ein Handle für die Metadatei abzurufen, das den ikonischen Aspekt des ausgewählten Elements enthält.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Rückgabewert

Das Handle für die Metadatei, das den ikonischen Aspekt des neuen Symbols enthält, wenn das Dialogfeld durch Auswahl **von OK**verworfen wurde; Andernfalls wird das Symbol wie vor dem Dialog angezeigt.

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a>COleChangeIconDialog::m_ci

Struktur des Typs OLEUICHANGEICON, die verwendet wird, um das Verhalten des Dialogfelds Symbol ändern zu steuern.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Bemerkungen

Member dieser Struktur können entweder direkt oder über Memberfunktionen geändert werden.

Weitere Informationen finden Sie in der [OLEUICHANGEICON-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)
