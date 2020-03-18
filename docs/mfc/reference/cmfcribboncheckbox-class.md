---
title: Cmscribboncheckbox-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: a8048f860a2cce75c37a065cfdd2751141054f1b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446240"
---
# <a name="cmfcribboncheckbox-class"></a>Cmscribboncheckbox-Klasse

Die `CMFCRibbonCheckBox`-Klasse implementiert ein Kontrollkästchen, das einem Menübandbereich, einer Symbolleiste für den Schnellzugriff oder einem Popupmenü hinzugefügt werden kann.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMF cribboncheckbox:: CMF cribboncheckbox](#cmfcribboncheckbox)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMF cribboncheckbox:: getcompactsize](#getcompactsize)|(Überschreibt [cmfcribbonbutton:: getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMF cribboncheckbox:: getintermediatesize](#getintermediatesize)|(Überschreibt [cmfcribbonbutton:: getintermediatesize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMF cribboncheckbox:: getregularsize](#getregularsize)|(Überschreibt [cmfcribbonbutton:: getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMF cribboncheckbox:: isdrawtooltipimage](#isdrawtooltipimage)|(Überschreibt `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMF cribboncheckbox:: OnDraw](#ondraw)|(Überschreibt [cmfcribbonbutton:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMF cribboncheckbox:: ondrawmenuimage](#ondrawmenuimage)|(Überschreibt [CMF cribbonbaseelement:: ondrawmenuimage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMF cribboncheckbox:: ondrawonlist](#ondrawonlist)|(Überschreibt `CMFCRibbonButton::OnDrawOnList`.)|
|[CMF cribboncheckbox:: setaccdata](#setaccdata)|(Überschreibt [cmfcribbonbutton:: setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Bemerkungen

Fügen Sie zum Verwenden von `CMFCRibbonCheckBox` in Ihrer Anwendung Ihrem Code den folgenden Konstruktor hinzu:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

Dabei ist *NID* die Befehls-ID des Kontrollkästchens, und *lpszText* ist die Text Bezeichnung des Kontrollkästchens.

Sie können einem Menü Band Bereich mithilfe von [CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)ein Kontrollkästchen hinzufügen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[Cmocribboncheckbox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxribboncheckbox. h

##  <a name="cmfcribboncheckbox"></a>CMF cribboncheckbox:: CMF cribboncheckbox

Konstruktor eines Menüband-Kontrollkästchen Objekts

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*NID*<br/>
in Gibt die Befehls-ID an.

*lpszText*<br/>
in Gibt die Text Bezeichnung an.

### <a name="return-value"></a>Rückgabewert

Erstellt ein Menüband-Kontrollkästchen-Objekt.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein Objekt der `CMFCRibbonCheckBox`-Klasse erstellt wird.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>CMF cribboncheckbox:: getcompactsize

Ruft beim Überschreiben die kompakte Größe des Kontrollkästchens ab.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
in Zeiger auf den CDC, der dem Kontrollkästchen zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Gibt ein `CSize` Objekt zurück, das die kompakte Größe des Kontrollkästchens enthält.

### <a name="remarks"></a>Bemerkungen

Wenn Sie nicht überschrieben wird, wird die zwischen Größe des Kontrollkästchens zurückgegeben.

##  <a name="getintermediatesize"></a>CMF cribboncheckbox:: getintermediatesize

Ruft die zwischen Größe des Kontrollkästchens ab.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
in Zeiger auf den CDC, der diesem Kontrollkästchen zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ein `CSize`-Objekt, das die zwischen Größe des Kontrollkästchens enthält.

### <a name="remarks"></a>Bemerkungen

Wenn Sie nicht überschrieben wird, berechnet die zwischen Größe als Standardgröße des Kontrollkästchens (`AFX_CHECK_BOX_DEFAULT_SIZE`) zuzüglich der Textgröße Plus Ränder.

##  <a name="getregularsize"></a>CMF cribboncheckbox:: getregularsize

Ruft die reguläre Größe des Kontrollkästchens ab.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
in Zeiger auf das CDC-Objekt, das diesem Kontrollkästchen zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Gibt ein `CSize` Objekt zurück, das die reguläre Größe des Kontrollkästchens enthält.

### <a name="remarks"></a>Bemerkungen

Wenn Sie nicht überschrieben wird, wird die zwischen Größe des Kontrollkästchens zurückgegeben.

##  <a name="isdrawtooltipimage"></a>CMF cribboncheckbox:: isdrawtooltipimage

Gibt an, ob dem Kontrollkästchen ein QuickInfo-Bild zugeordnet ist.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn dem Kontrollkästchen ein QuickInfo-Bild zugeordnet ist, andernfalls false.

### <a name="remarks"></a>Bemerkungen

##  <a name="ondraw"></a>CMF cribboncheckbox:: OnDraw

Wird von Framework aufgerufen, um das Kontrollkästchen mit einem angegebenen Gerätekontext zu zeichnen.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
in Zeiger auf den CDC, in dem das Kontrollkästchen gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

##  <a name="ondrawmenuimage"></a>CMF cribboncheckbox:: ondrawmenuimage

Wird von Framework aufgerufen, um ein Menübild für das Kontrollkästchen zu zeichnen.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parameter

in *CDC&#42;*<br/>
Zeiger auf den CDC, der dem Kontrollkästchen zugeordnet ist.

*CRect*<br/>
in Ein `CRect`-Objekt, das das Rechteck angibt, in dem das Menübild gezeichnet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn das Bild gezeichnet wurde, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn Sie nicht überschrieben wird, wird false zurückgegeben.

##  <a name="ondrawonlist"></a>CMF cribboncheckbox:: ondrawonlist

Wird von Framework aufgerufen, um das Kontrollkästchen in einem Befehle-Listenfeld zu zeichnen.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
in Zeiger auf den Gerätekontext, in dem das Kontrollkästchen gezeichnet werden soll.

*Text*<br/>
[in] Der Anzeigetext.

*ntexumffset*<br/>
in Der Abstand von der linken Seite des Listen Felds zum Anzeige Text in Pixel.

*Rect*<br/>
in Das Anzeige Rechteck für das Kontrollkästchen.

*bissgewählt*<br/>
in TRUE, wenn das Kontrollkästchen aktiviert ist, andernfalls false.

*bhervor gehoben*<br/>
in TRUE, wenn das Kontrollkästchen markiert ist, andernfalls false.

### <a name="remarks"></a>Bemerkungen

##  <a name="setaccdata"></a>CMF cribboncheckbox:: setaccdata

Legt die Barrierefreiheits Daten für das Kontrollkästchen fest.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parameter

*pparent*<br/>
Das übergeordnete Fenster des Kontrollkästchens.

*data*<br/>
Die Barrierefreiheits Daten für das Kontrollkästchen.

### <a name="return-value"></a>Rückgabewert

Gibt immer true zurück.

### <a name="remarks"></a>Bemerkungen

Standardmäßig legt diese Methode die Barrierefreiheits Daten für das Kontrollkästchen fest und gibt immer true zurück. Setzen Sie diese Methode außer Kraft, um die Barrierefreiheitsdaten festzulegen und einen Wert zurückzugeben, der den Erfolg oder einen Fehler angibt.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel-Klasse](../../mfc/reference/cmfcribbonpanel-class.md)
