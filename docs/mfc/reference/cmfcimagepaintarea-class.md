---
title: CMFCImagePaintArea-Klasse
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
ms.openlocfilehash: cd74d2418bb874553fbbafa637f527a7b84b73bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754276"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea-Klasse

Stellt den Bildbereich bereit, den Sie zum Ändern eines Bildes in einem Bildeditor-Dialogfeld verwenden.

## <a name="syntax"></a>Syntax

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Erstellt ein `CMFCImagePaintArea`-Objekt.|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCImagePaintArea::GetMode](#getmode)|Ruft den aktuellen Zeichnungsmodus ab.|
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Legt das Bitmapbild für den Bildbereich fest.|
|[CMFCImagePaintArea::SetColor](#setcolor)|Legt die aktuelle Zeichnungsfarbe fest.|
|[CMFCImagePaintArea::SetMode](#setmode)|Legt den aktuellen Zeichnungsmodus fest.|

### <a name="remarks"></a>Bemerkungen

Diese Klasse ist nicht für die direkte Verwendung im Code vorgesehen.

Das Framework verwendet diese Klasse, um den Bildbereich in einem Bildeditor-Dialogfeld anzuzeigen. Weitere Informationen zum Dialogfeld Bildeditor finden Sie unter [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCImagePaintArea` wie Sie ein Objekt der Klasse erstellen, die aktuelle Zeichnungsfarbe festlegen, den aktuellen Zeichnungsmodus festlegen und das Bitmapbild für den Bildbereich festlegen.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afximagepaintarea.h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a>CMFCImagePaintArea::CMFCImagePaintArea

Erstellt ein `CMFCImagePaintArea`-Objekt.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*pParentDlg*|[in] Ein Zeiger auf das Dialogfeld, das das übergeordnete Element des Bildeditors ist.|

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a>CMFCImagePaintArea::GetMode

Ruft den aktuellen Zeichnungsmodus ab.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) Wert, der den aktuellen Zeichnungsmodus angibt.

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a>CMFCImagePaintArea::SetBitmap

Legt das Bitmapbild für den Bildbereich fest.

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*pBitmap*|[in] Das neue Bitmapbild, das angezeigt werden soll.|

### <a name="remarks"></a>Bemerkungen

Wenn *pBitmap* NULL ist, legt diese Methode die Größe des veränderbaren Farbbereichs auf Null fest. Andernfalls wird die Größe des veränderbaren Farbbereichs auf die Größe des bereitgestellten Bitmapbilds festgelegt.

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a>CMFCImagePaintArea::SetColor

Legt die aktuelle Zeichnungsfarbe fest.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*color*|[in] Die neue Zeichnungsfarbe.|

### <a name="remarks"></a>Bemerkungen

Wenn Sie eine Farbe aus der Bildeditor-Palettenleiste oder Farbauswahl auswählen, ruft das Framework diese Methode auf, um die aktuelle Zeichnungsfarbe zu aktualisieren. Die ursprüngliche Zeichnungsfarbe ist schwarz (ein COLORREF-Wert von 0).

Die Zeichenfarbe wird vom Dialogfeld Bildeditor für alle Zeichnungsmodi mit Ausnahme IMAGE_EDIT_MODE_COLOR verwendet. Weitere Informationen zu Zeichnungsmodi finden Sie unter [CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration](cmfcimagepaintarea-image-edit-mode-enumeration.md).

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a>CMFCImagePaintArea::SetMode

Legt den aktuellen Zeichnungsmodus fest.

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*Modus*|[in] Ein [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) Wert, der den aktuellen Zeichnungsmodus angibt.|

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog-Klasse](../../mfc/reference/cmfcimageeditordialog-class.md)
