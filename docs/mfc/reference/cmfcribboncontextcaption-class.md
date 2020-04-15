---
title: CMFCRibbonContextCaption-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
ms.openlocfilehash: 7aacbe23684914c91129d9962ae847d442cc411b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375221"
---
# <a name="cmfcribboncontextcaption-class"></a>CMFCRibbonContextCaption-Klasse

Implementiert eine farbige Beschriftung, die über einer Menübandkategorie oder einer Kontextkategorie angezeigt wird.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|[CMFCRibbonContextCaption::GetColor](#getcolor)|Gibt die Farbe der Beschriftung zurück.|
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse kann nicht direkt instanziiert werden. Die [CMFCRibbonBar-Klassenklasse](../../mfc/reference/cmfcribbonbar-class.md) verwendet diese Klasse intern, um Bandgruppenkategorien Farbe hinzuzufügen.

Um die Farbe für Multifunktionsleistenkategorien festzulegen, rufen Sie [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)auf. Um die Farbe für Kontextkategorien festzulegen, rufen Sie [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)auf.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxRibbonBar.h

## <a name="cmfcribboncontextcaptiongetcolor"></a><a name="getcolor"></a>CMFCRibbonContextCaption::GetColor

Gibt die Hintergrundfarbe der Beschriftung zurück.

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Der zurückgegebene Wert kann einer der folgenden aufgezählten Werte sein:

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>Bemerkungen

Die Farbe der Beschriftung kann durch Aufrufen von [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) oder [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)festgelegt werden.

## <a name="cmfcribboncontextcaptiongetrighttabx"></a><a name="getrighttabx"></a>CMFCRibbonContextCaption::GetrightTabX

Ruft die Position des rechten Rands der Menüband-Registerkarte der Kategorie ab.

```
int GetRightTabX() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den rechten X-Wert des einschließenden `CMFCRibbonCategory` Rechtecks der Multifunktionsleisten-Registerkarte des Objekts oder einen Wert von -1 zurück, wenn die Registerkarte abgeschnitten ist.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton-Klasse](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonCategory-Klasse](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[CMFCRibbonBar-Klasse](../../mfc/reference/cmfcribbonbar-class.md)
