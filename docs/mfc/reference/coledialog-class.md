---
title: COleDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: 6a1983d426e97dd8063aee2857dc36557aa20677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366091"
---
# <a name="coledialog-class"></a>COleDialog-Klasse

Stellt die Funktionalität allgemeiner Dialogfelder für OLE bereit.

## <a name="syntax"></a>Syntax

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ColeDialog::GetLastError](#getlasterror)|Ruft den vom Dialogfeld zurückgegebenen Fehlercode ab.|

## <a name="remarks"></a>Bemerkungen

Die Microsoft Foundation-Klassenbibliothek bietet `COleDialog`mehrere Klassen, die von folgenden Klassen abgeleitet sind:

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

Weitere Informationen zu OLE-spezifischen Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="coledialoggetlasterror"></a><a name="getlasterror"></a>ColeDialog::GetLastError

Rufen `GetLastError` Sie die Memberfunktion auf, um zusätzliche Fehlerinformationen zu erhalten, wenn `DoModal` IDABORT zurückgegeben wird.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Rückgabewert

Die von zurückgegebenen `GetLastError` Fehlercodes hängen vom angezeigten Dialogfeld ab.

### <a name="remarks"></a>Bemerkungen

Informationen `DoModal` zu bestimmten Fehlermeldungen finden Sie in der Memberfunktion in den abgeleiteten Klassen.

## <a name="see-also"></a>Siehe auch

[CCommonDialog-Klasse](../../mfc/reference/ccommondialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
