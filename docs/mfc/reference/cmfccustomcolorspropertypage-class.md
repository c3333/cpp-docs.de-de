---
title: CMFCCustomColorsPropertyPage-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: 468d947947fc89f9ebc832cda722d854bb8b4be2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752464"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage-Klasse

Stellt eine Eigenschaftenseite dar, die benutzerdefinierte Farben in einem Farbdialogfeld auswählen kann.

## <a name="syntax"></a>Syntax

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|`CMFCCustomColorsPropertyPage::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Legt die Farbkomponenten der Eigenschaftenseite fest.|

### <a name="remarks"></a>Bemerkungen

Die `CMFCColorDialog` Klasse verwendet diese Klasse, um die benutzerdefinierte Farbeigenschaftsseite anzuzeigen. Weitere Informationen `CMFCColorDialog`zu finden Sie unter [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCCustomColorsPropertyPage` veranschaulicht, wie ein Objekt erstellt und die Farbkomponenten der Eigenschaftenseite festgelegt werden.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxcustomcolorspropertypage.h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a>CMFCCustomColorsPropertyPage::Setup

Legt die Farbkomponenten der Eigenschaftenseite fest.

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*R*|[in] Die rote Komponente des RGB-Werts.|
|*G*|[in] Die grüne Komponente des RGB-Werts.|
|*B*|[in] Die blaue Komponente des RGB-Werts.|

### <a name="remarks"></a>Bemerkungen

Diese Methode aktualisiert die aktuellen RGB- und die zugehörigen HLS-Farbwerte (Farbton, Leichtigkeit und Sättigung) der Eigenschaftenseite. Die [CMFCColorDialog::SetPageTwo-Methode](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) ruft diese Methode auf, wenn das Framework das Farbdialogfeld initialisiert oder der Benutzer die linke Maustaste drückt. Weitere Informationen `CMFCColorDialog`zu finden Sie unter [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog-Klasse](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage-Klasse](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
