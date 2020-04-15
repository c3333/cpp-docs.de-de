---
title: CMFCRibbonCustomizeDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: a66c0a19c04e0a900b91c0c28c45bb9c766d25c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375208"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog-Klasse

Zeigt die Seite **"Menüband Anpassen"** an.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Erstellt ein `CMFCRibbonCustomizeDialog`-Objekt.|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

MFC instanziiert diese Klasse automatisch, wenn Sie die AFX_WM_ON_RIBBON_CUSTOMIZE Nachricht nicht verarbeiten oder wenn Sie 0 vom Nachrichtenhandler zurückgeben.

Wenn Sie diese Klasse in Ihrer Anwendung verwenden möchten, um das Dialogfeld **"Anpassen** anpassen" anzuzeigen, instanziieren Sie sie einfach, und rufen Sie die `DoModal` Methode auf.

Da diese Klasse von der [CMFCPropertySheet-Klasse](../../mfc/reference/cmfcpropertysheet-class.md)abgeleitet ist, können Sie mithilfe der `CMFCPropertySheet` API benutzerdefinierte Seiten hinzufügen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizedialogcmfcribboncustomizedialog"></a><a name="cmfcribboncustomizedialog"></a>CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

Erstellt ein `CMFCRibbonCustomizeDialog`-Objekt.

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster (in der Regel der Hauptrahmen).

*pRibbon*<br/>
[in] Ein Zeiger `CMFCRibbonBar` darauf, dass angepasst werden soll.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCRibbonCustomizeDialog` veranschaulicht, wie ein Objekt erstellt wird.

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>Bemerkungen

Der Konstruktor instanziiert ein [CMFCRibbonCustomizePropertyPage-Klassenobjekt](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) und fügt es der Auflistung von Eigenschaftenblattseiten hinzu.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
