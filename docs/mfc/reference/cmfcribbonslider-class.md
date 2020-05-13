---
title: CMFCRibbonSlider-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
ms.openlocfilehash: 304581371c68817c6031153c3cec227137771c5d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754064"
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider-Klasse

Die `CMFCRibbonSlider` Klasse implementiert ein Schiebereglersteuerelement, das Sie einer Multifunktionsleisten- oder Multifunktionsleisten-Statusleiste hinzufügen können. Das Schieberegler-Steuerelement im Menüband ähnelt den Zoomschiebereglern, die in Office 2007-Anwendungen verwendet werden.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Erstellt und initialisiert ein Multifunktionsleisten-Schieberegler-Steuerelement.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|Gibt die aktuelle Position des Schiebereglersteuerelements zurück.|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Gibt den Maximalwert des Schiebereglers zurück.|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Gibt den Mindestwert des Schiebereglers zurück.|
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Gibt die reguläre Größe des Menübandelements zurück. (Überschreibt [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Gibt die Größe des Zoom-Inkrements für das Schieberegler-Steuerelement zurück.|
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Gibt an, ob der Schieberegler über Zoomschaltflächen verfügt.|
|[CMFCRibbonSlider::OnDraw](#ondraw)|Wird vom Framework aufgerufen, um das Menübandelement zu zeichnen. (Überschreibt [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonSlider::SetPos](#setpos)|Legt die aktuelle Position des Schiebereglersteuerelements fest.|
|[CMFCRibbonSlider::SetRange](#setrange)|Gibt den Bereich des Schiebereglersteuerelements an, indem die minimalen und maximalen Werte festgelegt werden.|
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Zeigt die Zoomschaltflächen an oder blendet sie aus.|
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Legt die Größe des Zoom-Inkrements für das Schieberegler-Steuerelement fest.|

## <a name="remarks"></a>Bemerkungen

Sie können `SetRange` die Methode verwenden, um den Bereich der Zoomschritte für den Schieberegler zu konfigurieren. Sie können die aktuelle Position des `SetPos` Schiebereglers mit der Methode festlegen.

Sie können kreisförmige Zoomschaltflächen auf der linken und rechten `SetZoomButtons` Seite des Schiebereglersteuerelements anzeigen, indem Sie die Methode verwenden. Standardmäßig ist der Schieberegler horizontal, die linke Zoom-Schaltfläche zeigt ein Minuszeichen und die rechte Zoom-Schaltfläche ein Pluszeichen an.

Die `SetZoomIncrement` Methode definiert das Inkrement, das der aktuellen Position hinzugefügt oder von ihr subtrahiert werden soll, wenn ein Benutzer auf die Zoomschaltflächen klickt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCRibbonSlider` wie verschiedene Methoden in der Klasse verwendet werden, um die Eigenschaften des Schiebereglers festzulegen. Das Beispiel zeigt, `CMFCRibbonSlider` wie Sie ein Objekt erstellen, Zoomschaltflächen anzeigen, die aktuelle Position des Schiebereglersteuerelements festlegen und den Wertebereich für das Schiebereglersteuerelement festlegen.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxribbonslider.h

## <a name="cmfcribbonslidercmfcribbonslider"></a><a name="cmfcribbonslider"></a>CMFCRibbonSlider::CMFCRibbonSlider

Erstellen Sie einen Multifunktionsleisten-Schieberegler.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
[in] Slider-ID.

[in] *nWidth* Schiebereglerbreite in Pixel.

### <a name="remarks"></a>Bemerkungen

Erstellt einen Multifunktionsleisten-Schieberegler, der *nWidth-Pixel* breit ist in der Bedienfeldkategorie, in der der Schieberegler hinzugefügt wird. Standardmäßig ist der Schieberegler horizontal.

## <a name="cmfcribbonslidergetpos"></a><a name="getpos"></a>CMFCRibbonSlider::GetPos

Gibt die aktuelle Position des Schiebereglersteuerelements zurück.

```
int GetPos() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Position des Schiebereglers, bei der es sich um eine Position relativ zum Anfang des Schiebereglers handelt.

## <a name="cmfcribbonslidergetrangemax"></a><a name="getrangemax"></a>CMFCRibbonSlider::GetRangeMax

Ruft das maximale Inkrement des Schiebereglers ab, den der Schieberegler auf dem Schieberegler-Steuerelement bewegen kann.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Rückgabewert

Das maximale Inkrement des Schiebereglers, den der Schieberegler auf dem Schieberegler-Steuerelement bewegen kann.

## <a name="cmfcribbonslidergetrangemin"></a><a name="getrangemin"></a>CMFCRibbonSlider::GetRangeMin

Gibt das minimale Inkrement zurück, das der Schieberegler auf dem Schieberegler-Steuerelement bewegen kann.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Rückgabewert

Das minimale Inkrement, das der Schieberegler auf dem Schieberegler-Steuerelement bewegen kann.

## <a name="cmfcribbonslidergetregularsize"></a><a name="getregularsize"></a>CMFCRibbonSlider::GetRegularSize

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonslidergetzoomincrement"></a><a name="getzoomincrement"></a>CMFCRibbonSlider::GetZoomIncrement

Rufen Sie das Zoom-Inkrement für das Schieberegler-Steuerelement ab.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>Rückgabewert

Das Zoom-Inkrement für das Schieberegler-Steuerelement.

## <a name="cmfcribbonsliderhaszoombuttons"></a><a name="haszoombuttons"></a>CMFCRibbonSlider::HasZoomButtons

Gibt an, ob der Schieberegler über Zoomschaltflächen verfügt.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Schieberegler über Zoomtasten verfügt; FALSE sonst.

## <a name="cmfcribbonsliderondraw"></a><a name="ondraw"></a>CMFCRibbonSlider::OnDraw

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonslidersetpos"></a><a name="setpos"></a>CMFCRibbonSlider::SetPos

Legen Sie die aktuelle Position des Schiebereglers fest.

```cpp
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
[in] Gibt die Position an, die für den Schieberegler festgelegt werden soll. Die Position ist relativ zum Anfang des Schiebereglers.

*bZeichnung*<br/>
[in] Wenn TRUE, wird der Schieberegler neu gezeichnet.

## <a name="cmfcribbonslidersetrange"></a><a name="setrange"></a>CMFCRibbonSlider::SetRange

Legen Sie den Wertebereich für das Schiebereglersteuerelement fest.

```cpp
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parameter

*Nmin*<br/>
[in] Gibt den Mindestwert des Schiebereglersteuerelements an.

*nMax*<br/>
[in] Gibt den Maximalwert des Schiebereglersteuerelements an.

### <a name="remarks"></a>Bemerkungen

Gibt den Wertebereich für das Schiebereglersteuerelement an, indem die minimalen und maximalen Werte festgelegt werden.

## <a name="cmfcribbonslidersetzoombuttons"></a><a name="setzoombuttons"></a>CMFCRibbonSlider::SetZoomButtons

Zoomtasten anzeigen oder ausblenden.

```cpp
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>Parameter

[in] *bSet* TRUE, um Zoomtasten anzuzeigen; FALSE, um sie zu verbergen.

## <a name="cmfcribbonslidersetzoomincrement"></a><a name="setzoomincrement"></a>CMFCRibbonSlider::SetZoomIncrement

Legen Sie das Zoom-Inkrement für das Schieberegler-Steuerelement fest.

```cpp
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>Parameter

*nZoomIncrement*<br/>
[in] Gibt das Zoom-Inkrement des Schiebereglersteuerelements an.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement-Klasse](../../mfc/reference/cmfcribbonbaseelement-class.md)
