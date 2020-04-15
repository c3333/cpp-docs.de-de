---
title: COleLinksDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
ms.openlocfilehash: f120678c822749c8f27c3c56c95fcdd54647aca3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374934"
---
# <a name="colelinksdialog-class"></a>COleLinksDialog-Klasse

Wird für das OLE-Dialogfeld "Verknüpfungen bearbeiten" verwendet.

## <a name="syntax"></a>Syntax

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|Erstellt ein `COleLinksDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleLinksDialog::DoModal](#domodal)|Zeigt das Dialogfeld OLE-Bearbeitungslinks an.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|Eine Struktur vom Typ OLEUIEDITLINKS, die das Verhalten des Dialogfelds steuert.|

## <a name="remarks"></a>Bemerkungen

Erstellen Sie ein `COleLinksDialog` Klassenobjekt, wenn Sie dieses Dialogfeld aufrufen möchten. Nachdem `COleLinksDialog` ein Objekt erstellt wurde, können Sie die [m_el](#m_el) Struktur verwenden, um die Werte oder Zustände von Steuerelementen im Dialogfeld zu initialisieren. Die `m_el` Struktur ist vom Typ OLEUIEDITLINKS. Weitere Informationen zur Verwendung dieser Dialogklasse finden Sie in der [DoModal-Memberfunktion.](#domodal)

> [!NOTE]
> Anwendungs-Wizard-generierter Containercode verwendet diese Klasse.

Weitere Informationen finden Sie in der [OLEUIEDITLINKS-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) im Windows SDK.

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="colelinksdialogdomodal"></a><a name="domodal"></a>COleLinksDialog::DoModal

Zeigt das Dialogfeld OLE-Bearbeitungslinks an.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Abschlussstatus für das Dialogfeld. Einer der folgenden Werte:

- IDOK, wenn das Dialogfeld erfolgreich angezeigt wurde.

- IDCANCEL, wenn der Benutzer das Dialogfeld abgebrochen hat.

- IDABORT, wenn ein Fehler aufgetreten ist. Wenn IDABORT zurückgegeben wird, rufen Sie die `COleDialog::GetLastError` Memberfunktion auf, um weitere Informationen über den Fehlertyp zu erhalten, der aufgetreten ist. Eine Liste möglicher Fehler finden Sie in der [OleUIEditLinks-Funktion](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Dialogfeldsteuerelemente initialisieren [m_el](#m_el) möchten, indem Sie Elemente `DoModal`der m_el Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

## <a name="colelinksdialogcolelinksdialog"></a><a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

Erstellt ein `COleLinksDialog`-Objekt.

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*pDoc*<br/>
Verweist auf das OLE-Dokument, das die zu bearbeitenden Verknüpfungen enthält.

*Pview*<br/>
Zeigt auf die aktuelle Ansicht auf *pDoc*.

*dwFlags*<br/>
Erstellungsflag, das entweder 0 oder ELF_SHOWHELP enthält, um anzugeben, ob die Hilfeschaltfläche angezeigt wird, wenn das Dialogfeld angezeigt wird.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ `CWnd`), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogfelds auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion erstellt `COleLinksDialog` nur ein Objekt. Um das Dialogfeld anzuzeigen, rufen Sie die [DoModal-Funktion](#domodal) auf.

## <a name="colelinksdialogm_el"></a><a name="m_el"></a>COleLinksDialog::m_el

Struktur des Typs OLEUIEDITLINKS, die verwendet wird, um das Verhalten des Dialogfelds Links bearbeiten zu steuern.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Bemerkungen

Member dieser Struktur können entweder direkt oder über Memberfunktionen geändert werden.

Weitere Informationen finden Sie in der [OLEUIEDITLINKS-Struktur](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)
