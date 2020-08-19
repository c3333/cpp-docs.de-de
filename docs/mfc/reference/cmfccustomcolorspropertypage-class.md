---
title: Cmfccustomcolorspropertypage-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: d4bdd1524f71bfba33e9090058fce26763a862bf
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561127"
---
# <a name="cmfccustomcolorspropertypage-class"></a>Cmfccustomcolorspropertypage-Klasse

Stellt eine Eigenschaften Seite dar, mit der benutzerdefinierte Farben in einem Farb Dialogfeld ausgewählt werden können.

## <a name="syntax"></a>Syntax

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|name|BESCHREIBUNG|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|name|BESCHREIBUNG|
|`CMFCCustomColorsPropertyPage::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Objekt abzurufen, das diesem Klassentyp zugeordnet ist.|
|[Cmfccustomcolorspropertypage:: Setup](#setup)|Legt die Farbkomponenten der Eigenschaften Seite fest.|

### <a name="remarks"></a>Bemerkungen

Die- `CMFCColorDialog` Klasse verwendet diese Klasse, um die Eigenschaften Seite für benutzerdefinierte Farben anzuzeigen. Weitere Informationen zu `CMFCColorDialog` finden Sie unter [cmfccolordialog-Klasse](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein `CMFCCustomColorsPropertyPage` -Objekt erstellt und die Farbkomponenten der Eigenschaften Seite festgelegt werden.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[Cmfccustomcolorspropertypage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcustomcolorspropertypage. h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a> Cmfccustomcolorspropertypage:: Setup

Legt die Farbkomponenten der Eigenschaften Seite fest.

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parameter

*R*\
in Die rote Komponente des RGB-Werts.

*Selbst*\
in Die grüne Komponente des RGB-Werts.

*B*\
in Die blaue Komponente des RGB-Werts.

### <a name="remarks"></a>Bemerkungen

Diese Methode aktualisiert die aktuellen RGB-Farbwerte (Hue, Helligkeit und Sättigung) der Eigenschaften Seite. Die [cmfccolordialog:: setpagetwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) -Methode ruft diese Methode auf, wenn das Framework das Farb Dialogfeld initialisiert oder der Benutzer die linke Maustaste drückt. Weitere Informationen zu `CMFCColorDialog` finden Sie unter [cmfccolordialog-Klasse](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cmfccolordialog-Klasse](../../mfc/reference/cmfccolordialog-class.md)<br/>
[Cmfcstandardcolorspropertypage-Klasse](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
