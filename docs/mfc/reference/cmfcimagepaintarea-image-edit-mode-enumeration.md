---
title: CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration
ms.date: 11/04/2016
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
ms.openlocfilehash: 37c877cc8562a9479535d9c6132e49e7c9b7e82f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831137"
---
# <a name="cmfcimagepaintareaimage_edit_mode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration

Gibt einen Zeichnungsmodus an, den Sie zum Ändern eines Bilds in einem Bild-Editor-Dialogfeld verwenden.

## <a name="syntax"></a>Syntax

```
enum IMAGE_EDIT_MODE
{
    IMAGE_EDIT_MODE_PEN = 0,
    IMAGE_EDIT_MODE_FILL,
    IMAGE_EDIT_MODE_LINE,
    IMAGE_EDIT_MODE_RECT,
    IMAGE_EDIT_MODE_ELLIPSE,
    IMAGE_EDIT_MODE_COLOR
};
```

## <a name="members"></a>Member

|Name|Beschreibung|
|-|-|
|IMAGE_EDIT_MODE_PEN|Wird verwendet, um einzelne Pixel zu zeichnen.|
|IMAGE_EDIT_MODE_FILL|Wird verwendet, um alle angrenzenden Bereiche auszufüllen, die die Farbe an der aktuellen Cursorposition enthalten.|
|IMAGE_EDIT_MODE_LINE|Wird verwendet, um eine Linie zu zeichnen.|
|IMAGE_EDIT_MODE_RECT|Wird verwendet, um ein Rechteck zu zeichnen.|
|IMAGE_EDIT_MODE_ELLIPSE|Wird zum Zeichnen einer Ellipse verwendet.|
|IMAGE_EDIT_MODE_COLOR|Wird verwendet, um die aktuelle Farbe auf die Farbe an der aktuellen Cursorposition festzulegen.|

### <a name="remarks"></a>Bemerkungen

Die `CMFCImagePaintArea` - `CMFCImageEditorDialog` Klasse und die-Klasse verwenden diese Enumeration, um den aktuellen Zeichnungsmodus festzulegen. Der Zeichenmodus und die aktuelle Farbe werden verwendet, um den Bildbereich in einem Bild-Editor-Dialogfeld zu ändern. Weitere Informationen zu `CMFCImagePaintArea` und `CMFCImageEditorDialog` finden Sie unter [cmficimagepaintarea Class](../../mfc/reference/cmfcimagepaintarea-class.md) und [cmficimageeditordialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).

Wenn Sie eine Farbe aus einem Bild auswählen, indem Sie den IMAGE_EDIT_MODE_COLOR Zeichnungsmodus verwenden, legt das Framework den aktuellen Zeichnungsmodus auf IMAGE_EDIT_MODE_PEN fest.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afximagepaintarea. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cmficimagepaintarea-Klasse](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[Cmficimageeditordialog-Klasse](../../mfc/reference/cmfcimageeditordialog-class.md)
