---
title: Cmficimagepaintarea-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
ms.openlocfilehash: ee960b27651489ac1c196789d41a6c5ee396b260
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831150"
---
# <a name="cmfcimagepaintarea-class"></a>Cmficimagepaintarea-Klasse

Stellt den Bildbereich bereit, mit dem Sie ein Bild in einem Bild-Editor-Dialogfeld ändern können.

## <a name="syntax"></a>Syntax

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|[Cmficimagepaintarea:: cmficimagepaintarea](#cmfcimagepaintarea)|Erstellt ein `CMFCImagePaintArea`-Objekt.|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[Cmscimagepaintarea:: getMode](#getmode)|Ruft den aktuellen Zeichnungsmodus ab.|
|[Cmficimagepaintarea:: SetBitmap](#setbitmap)|Legt das Bitmap-Bild für den Bildbereich fest.|
|[Cmficimagepaintarea:: setColor](#setcolor)|Legt die aktuelle Zeichnungs Farbe fest.|
|[Cmscimagepaintarea:: setmode](#setmode)|Legt den aktuellen Zeichnungsmodus fest.|

### <a name="remarks"></a>Bemerkungen

Diese Klasse ist nicht für die direkte Verwendung im Code vorgesehen.

Das Framework verwendet diese Klasse, um den Bildbereich in einem Bild-Editor-Dialogfeld anzuzeigen. Weitere Informationen zum Dialogfeld Bildbearbeitung finden Sie unter [cmfcimageeditordialog-Klasse](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein Objekt der- `CMFCImagePaintArea` Klasse erstellt, die aktuelle Zeichnungs Farbe festgelegt, der aktuelle Zeichnungsmodus festgelegt und das Bitmap-Bild für den Bildbereich festgelegt wird.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afximagepaintarea. h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a> Cmficimagepaintarea:: cmficimagepaintarea

Erstellt ein `CMFCImagePaintArea`-Objekt.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Parameter

*pparameentdlg*\
in Ein Zeiger auf das Dialogfeld, das das übergeordnete Element des Bild-Editors ist.

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a> Cmscimagepaintarea:: getMode

Ruft den aktuellen Zeichnungsmodus ab.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) -Wert, der den aktuellen Zeichnungsmodus angibt.

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a> Cmficimagepaintarea:: SetBitmap

Legt das Bitmap-Bild für den Bildbereich fest.

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parameter

*pbitmap*\
in Das neue Bitmapbild, das angezeigt werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn *pbitmap* auf NULL festgelegt ist, legt diese Methode die Größe des änderbaren Zeichnungs Bereichs auf NULL fest. Andernfalls wird die Größe des änderbaren Zeichnungs Bereichs auf die Größe des bereitgestellten Bitmapbilds festgelegt.

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a> Cmficimagepaintarea:: setColor

Legt die aktuelle Zeichnungs Farbe fest.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*\
in Die neue Zeichnungs Farbe.

### <a name="remarks"></a>Bemerkungen

Wenn Sie eine Farbe aus der Bildbearbeitung-palettenleiste oder Farbauswahl auswählen, ruft das Framework diese Methode auf, um die aktuelle Zeichnungs Farbe zu aktualisieren. Die ursprüngliche Zeichnungs Farbe ist schwarz (ein COLORREF-Wert von 0).

Die Zeichnungs Farbe wird vom Dialogfeld Bildbearbeitung für alle Zeichnungs Modi mit Ausnahme von IMAGE_EDIT_MODE_COLOR verwendet. Weitere Informationen zu Zeichnungs Modi finden Sie unter [cmficimagepaintarea:: IMAGE_EDIT_MODE Enumeration](cmfcimagepaintarea-image-edit-mode-enumeration.md).

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a> Cmscimagepaintarea:: setmode

Legt den aktuellen Zeichnungsmodus fest.

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Parameter

*Spar*\
in Ein [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) -Wert, der den aktuellen Zeichnungsmodus angibt.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cmficimageeditordialog-Klasse](../../mfc/reference/cmfcimageeditordialog-class.md)
