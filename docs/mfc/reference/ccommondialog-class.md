---
title: CCommonDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 853a4756df3b70f4f33deb7159b4d1aee610092c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369445"
---
# <a name="ccommondialog-class"></a>CCommonDialog-Klasse

Die Basisklasse für Klassen, die Funktionalität der allgemeinen Windows-Dialogfelder kapseln.

## <a name="syntax"></a>Syntax

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCommonDialog::CCommonDialog](#ccommondialog)|Erstellt ein `CCommonDialog`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Die folgenden Klassen kapseln die Funktionalität der allgemeinen Windows-Dialogfelder:

- [CFileDialog](../../mfc/reference/cfiledialog-class.md)

- [CFontDialog](../../mfc/reference/cfontdialog-class.md)

- [CColorDialog](../../mfc/reference/ccolordialog-class.md)

- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)

- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)

- [COleDialog](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdlgs.h

## <a name="ccommondialogccommondialog"></a><a name="ccommondialog"></a>CCommonDialog::CCommonDialog

Erstellt ein `CCommonDialog`-Objekt.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Zeigt auf das übergeordnete oder Besitzerfensterobjekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogobjekts auf das Hauptanwendungsfenster festgelegt.

### <a name="remarks"></a>Bemerkungen

Vollständige Informationen finden Sie unter [CDialog::CDialog.](../../mfc/reference/cdialog-class.md#cdialog)

## <a name="see-also"></a>Siehe auch

[CDialog-Klasse](../../mfc/reference/cdialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md)<br/>
[CFontDialog-Klasse](../../mfc/reference/cfontdialog-class.md)<br/>
[CColorDialog-Klasse](../../mfc/reference/ccolordialog-class.md)<br/>
[CPageSetupDialog-Klasse](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[CPrintDialog-Klasse](../../mfc/reference/cprintdialog-class.md)<br/>
[CFindReplaceDialog-Klasse](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)
