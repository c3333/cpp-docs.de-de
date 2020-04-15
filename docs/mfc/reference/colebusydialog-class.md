---
title: COleBusyDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
ms.openlocfilehash: 5be42463c08cacd83de84900fb4d98771774e897
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364240"
---
# <a name="colebusydialog-class"></a>COleBusyDialog-Klasse

Wird für die OLE-Dialogfelder "Server antwortet nicht" oder "Server ausgelastet" verwendet.

## <a name="syntax"></a>Syntax

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COlebusyDialog::COlebusyDialog](#colebusydialog)|Erstellt ein `COleBusyDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleBusyDialog::DoModal](#domodal)|Zeigt das Dialogfeld OLE Server Beschäftigt an.|
|[COlebusyDialog::GetSelectionType](#getselectiontype)|Bestimmt die im Dialogfeld getroffene Auswahl.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Struktur des Typs OLEUIBUSY, die das Verhalten des Dialogfelds steuert.|

## <a name="remarks"></a>Bemerkungen

Erstellen Sie ein `COleBusyDialog` Klassenobjekt, wenn Sie diese Dialogfelder aufrufen möchten. Nachdem `COleBusyDialog` ein Objekt erstellt wurde, können Sie die [m_bz-Struktur](#m_bz) verwenden, um die Werte oder Zustände von Steuerelementen im Dialogfeld zu initialisieren. Die `m_bz` Struktur ist vom Typ OLEUIBUSY. Weitere Informationen zur Verwendung dieser Dialogklasse finden Sie in der [DoModal-Memberfunktion.](#domodal)

> [!NOTE]
> Anwendungs-Wizard-generierter Containercode verwendet diese Klasse.

Weitere Informationen finden Sie in der [OLEUIBUSY-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) im Windows SDK.

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="colebusydialogcolebusydialog"></a><a name="colebusydialog"></a>COlebusyDialog::COlebusyDialog

Diese Funktion erstellt `COleBusyDialog` nur ein Objekt.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*htaskBusy*<br/>
Behandeln Sie die Serveraufgabe, die ausgelastet ist.

*bNotResponding*<br/>
Wenn TRUE, rufen Sie das Dialogfeld Nicht antworten anstelle des Dialogfelds "Server Beschäftigt" auf. Der Wortlaut im Dialogfeld Nicht antworten unterscheidet sich geringfügig von dem Wortlaut im Dialogfeld Server Beschäftigt, und die Schaltfläche Abbrechen ist deaktiviert.

*dwFlags*<br/>
Erstellungsflagge. Kann null oder mehr der folgenden Werte in Kombination mit dem bitweisen-ODER-Operator enthalten:

- BZ_DISABLECANCELBUTTON Deaktivieren Sie die Schaltfläche Abbrechen, wenn Sie das Dialogfeld aufrufen.

- BZ_DISABLESWITCHTOBUTTON Deaktivieren Sie die Schaltfläche Wechseln zu, wenn Sie das Dialogfeld aufrufen.

- BZ_DISABLERETRYBUTTON Deaktivieren Sie die Schaltfläche Wiederholen, wenn Sie das Dialogfeld aufrufen.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ `CWnd`), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogobjekts auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Um das Dialogfeld anzuzeigen, rufen Sie [DoModal](#domodal)auf.

Weitere Informationen finden Sie in der [OLEUIBUSY-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) im Windows SDK.

## <a name="colebusydialogdomodal"></a><a name="domodal"></a>COleBusyDialog::DoModal

Rufen Sie diese Funktion auf, um das Dialogfeld OLE Server Beschäftigt oder Server nicht zu aktivieren.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Abschlussstatus für das Dialogfeld. Einer der folgenden Werte:

- IDOK, wenn das Dialogfeld erfolgreich angezeigt wurde.

- IDCANCEL, wenn der Benutzer das Dialogfeld abgebrochen hat.

- IDABORT, wenn ein Fehler aufgetreten ist. Wenn IDABORT zurückgegeben wird, rufen Sie die `COleDialog::GetLastError` Memberfunktion auf, um weitere Informationen über den Fehlertyp zu erhalten, der aufgetreten ist. Eine Liste möglicher Fehler finden Sie in der [OleUIBusy-Funktion](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Dialogfeldsteuerelemente initialisieren [m_bz](#m_bz) möchten, indem Sie Elemente `DoModal`der m_bz Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

Wenn `DoModal` IDOK zurückgegeben wird, können Sie andere Memberfunktionen aufrufen, um die Einstellungen oder Informationen abzurufen, die vom Benutzer in das Dialogfeld eingegeben wurden.

## <a name="colebusydialoggetselectiontype"></a><a name="getselectiontype"></a>COlebusyDialog::GetSelectionType

Rufen Sie diese Funktion auf, um den vom Benutzer im Dialogfeld "Server Beschäftigt" ausgewählten Auswahltyp abzurufen.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Rückgabewert

Art der getroffenen Auswahl.

### <a name="remarks"></a>Bemerkungen

Die Rückgabetypwerte werden `Selection` durch den in der `COleBusyDialog` Klasse deklarierten Enumerationstyp angegeben.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

Kurze Beschreibungen dieser Werte folgen:

- `COleBusyDialog::switchTo`Schalter Auf Taste wurde gedrückt.

- `COleBusyDialog::retry`Die Wiederholungstaste wurde gedrückt.

- `COleBusyDialog::callUnblocked`Der Aufruf zum Aktivieren des Servers ist nun aufgehoben.

## <a name="colebusydialogm_bz"></a><a name="m_bz"></a>COleBusyDialog::m_bz

Struktur des Typs OLEUIBUSY, die zum Steuern des Verhaltens des Dialogfelds "Server Beschäftigt" verwendet wird.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Bemerkungen

Member dieser Struktur können direkt oder über Memberfunktionen geändert werden.

Weitere Informationen finden Sie in der [OLEUIBUSY-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)
