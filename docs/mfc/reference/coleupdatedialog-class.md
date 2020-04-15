---
title: COleUpdateDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
ms.openlocfilehash: 9e2c7a8d79ebf5e6483a06354b280e474d7b8e61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374837"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog-Klasse

Wird für einen Sonderfall des OLE-Dialogfelds "Verknüpfungen bearbeiten" verwendet, das eingesetzt werden sollte, wenn in einem Dokument nur vorhandene Links oder eingebettete Objekte aktualisiert werden müssen.

## <a name="syntax"></a>Syntax

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Erstellt ein `COleUpdateDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|Zeigt das Dialogfeld **Links bearbeiten** im Aktualisierungsmodus an.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="coleupdatedialogcoleupdatedialog"></a><a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog

Erstellt ein `COleUpdateDialog`-Objekt.

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*pDoc*<br/>
Verweist auf das Dokument, das die Links enthält, die möglicherweise aktualisiert werden müssen.

*bUpdateLinks*<br/>
Flag, das bestimmt, ob verknüpfte Objekte aktualisiert werden sollen.

*bUpdateEinbettungen*<br/>
Flag, das bestimmt, ob eingebettete Objekte aktualisiert werden sollen.

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ `CWnd`), zu dem das Dialogobjekt gehört. Wenn es NULL ist, wird das übergeordnete Fenster des Dialogfelds auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion erstellt `COleUpdateDialog` nur ein Objekt. Um das Dialogfeld anzuzeigen, rufen Sie [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)auf. Diese Klasse sollte verwendet `COleLinksDialog` werden, anstatt wenn Sie nur vorhandene verknüpfte oder eingebettete Elemente aktualisieren möchten.

## <a name="coleupdatedialogdomodal"></a><a name="domodal"></a>COleUpdateDialog::DoModal

Zeigt das Dialogfeld Links bearbeiten im Aktualisierungsmodus an.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Abschlussstatus für das Dialogfeld. Einer der folgenden Werte:

- IDOK, wenn das Dialogfeld erfolgreich zurückgegeben wurde.

- IDCANCEL, wenn keines der verknüpften oder eingebetteten Elemente im aktuellen Dokument aktualisiert werden muss.

- IDABORT, wenn ein Fehler aufgetreten ist. Wenn IDABORT zurückgegeben wird, rufen Sie die [Memberfunktion COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) auf, um weitere Informationen über den Fehlertyp zu erhalten. Eine Liste möglicher Fehler finden Sie in der [OleUIEditLinks-Funktion](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Alle Links und/oder Einbettungen werden aktualisiert, es sei denn, der Benutzer wählt die Schaltfläche Abbrechen aus.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog-Klasse](../../mfc/reference/colelinksdialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog-Klasse](../../mfc/reference/colelinksdialog-class.md)
