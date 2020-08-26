---
title: Cmfcstandardcolorspropertypage-Klasse
ms.date: 11/04/2016
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
ms.openlocfilehash: c57715171816e83cd1e04872d88b452b51b39388
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843949"
---
# <a name="cmfcstandardcolorspropertypage-class"></a>Cmfcstandardcolorspropertypage-Klasse

Stellt eine Eigenschaften Seite dar, die Benutzer verwenden, um Standardfarben in einem Farb Dialogfeld auszuwählen.

## <a name="syntax"></a>Syntax

```
class CMFCStandardColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Standardkonstruktor|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|`CMFCStandardColorsPropertyPage::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCStandardColorsPropertyPage::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Objekt abzurufen, das diesem Klassentyp zugeordnet ist.|

### <a name="remarks"></a>Bemerkungen

Die- `CMFCColorDialog` Klasse verwendet diese Klasse, um die standardmäßige Farbeigenschaften Seite anzuzeigen. Weitere Informationen zu `CMFCColorDialog` finden Sie unter [cmfccolordialog-Klasse](../../mfc/reference/cmfccolordialog-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[Cmfcstandardcolorspropertypage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxstandardcolorspropertypage. h

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cmfccolordialog-Klasse](../../mfc/reference/cmfccolordialog-class.md)<br/>
[Cmfccustomcolorspropertypage-Klasse](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
