---
title: CMFCRibbonCheckBox-Klasse
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
ms.openlocfilehash: 089c8056afebef31ff98a435bf145566ae64fe1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375254"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox-Klasse

Die `CMFCRibbonCheckBox`-Klasse implementiert ein Kontrollkästchen, das einem Menübandbereich, einer Symbolleiste für den Schnellzugriff oder einem Popupmenü hinzugefügt werden kann.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Überschreibt [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Überschreibt [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Überschreibt [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Überschreibt `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Überschreibt [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Überschreibt [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Überschreibt `CMFCRibbonButton::OnDrawOnList`.)|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Überschreibt [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Bemerkungen

Fügen Sie zum Verwenden von `CMFCRibbonCheckBox` in Ihrer Anwendung Ihrem Code den folgenden Konstruktor hinzu:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

wobei *nID* das Kontrollkästchen Befehls-ID und *lpszText* die Textbeschriftung des Kontrollkästchens ist.

Sie können ein Kontrollkästchen zu einem Multifunktionsleistenbedienfeld hinzufügen, indem Sie [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)verwenden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxribboncheckbox.h

## <a name="cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

Konstruktor eines Menüband-Kontrollkästchenobjekts

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
[in] Gibt die Befehls-ID an.

*lpszText*<br/>
[in] Gibt die Textbeschriftung an.

### <a name="return-value"></a>Rückgabewert

Erstellt ein Menüband-Kontrollkästchenobjekt.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCRibbonCheckBox` wie ein Objekt der Klasse erstellt wird.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

## <a name="cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize

Wenn sie überschrieben wird, wird die kompakte Größe des Kontrollkästchens angezeigt.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeigen Sie mit dem Hinweis auf das CDC, das dem Kontrollkästchen zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Gibt `CSize` ein Objekt zurück, das die kompakte Größe des Kontrollkästchens enthält.

### <a name="remarks"></a>Bemerkungen

Wenn nicht überschrieben, gibt die Zwischengröße des Kontrollkästchens zurück.

## <a name="cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize

Ruft die Zwischengröße des Kontrollkästchens ab.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeigen Sie mit dem mit diesem Kontrollkästchen verknüpften CDC.

### <a name="return-value"></a>Rückgabewert

Ein `CSize` Objekt, das die Zwischengröße des Kontrollkästchens enthält.

### <a name="remarks"></a>Bemerkungen

Wenn nicht überschrieben, berechnet die Zwischengröße als `AFX_CHECK_BOX_DEFAULT_SIZE`Standard-Kontrollkästchengröße ( ) plus Textgröße plus Ränder.

## <a name="cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize

Ruft die normale Größe des Kontrollkästchens ab.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeigen Sie mit dem Zeiger auf das CDC-Objekt, das diesem Kontrollkästchen zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Gibt `CSize` ein Objekt zurück, das die normale Größe des Kontrollkästchens enthält.

### <a name="remarks"></a>Bemerkungen

Wenn nicht überschrieben, gibt die Zwischengröße des Kontrollkästchens zurück.

## <a name="cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

Gibt an, ob dem Kontrollkästchen ein QuickInfo-Bild zugeordnet ist.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn dem Kontrollkästchen ein QuickInfo-Bild zugeordnet ist, oder FALSE, falls nicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncheckboxondraw"></a><a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw

Wird vom Framework aufgerufen, um das Kontrollkästchen mithilfe eines angegebenen Gerätekontexts zu zeichnen.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeigen Sie auf das CDC, in dem das Kontrollkästchen gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage

Wird vom Framework aufgerufen, um ein Menübild für das Kontrollkästchen zu zeichnen.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parameter

[in] *CDC&#42;*<br/>
Zeigen Sie mit dem Hinweis auf das CDC, das dem Kontrollkästchen zugeordnet ist.

*CRect*<br/>
[in] Ein `CRect` Objekt, das das Rechteck angibt, in dem das Menübild gezeichnet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das Bild gezeichnet wurde, oder FALSE, wenn nicht.

### <a name="remarks"></a>Bemerkungen

Wenn nicht überschrieben, gibt FALSE zurück.

## <a name="cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawonList

Wird vom Framework aufgerufen, um das Kontrollkästchen in einem Befehlslistenfeld zu zeichnen.

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
[in] Zeigen Sie auf den Gerätekontext, in dem das Kontrollkästchen gezeichnet werden soll.

*strText*<br/>
[in] Der Anzeigetext.

*nTextOffset*<br/>
[in] Der Abstand (in Pixel) von der linken Seite des Listenfelds zum Anzeigetext.

*Rect*<br/>
[in] Das Anzeigerechteck für das Kontrollkästchen.

*bIsSelected*<br/>
[in] TRUE, wenn das Kontrollkästchen aktiviert ist, oder FALSE, wenn nicht.

*bHervorgehoben*<br/>
[in] TRUE, wenn das Kontrollkästchen hervorgehoben ist, oder FALSE, wenn nicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData

Legt die Eingabehilfendaten für das Kontrollkästchen fest.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parameter

*pParent*<br/>
Das übergeordnete Fenster des Kontrollkästchens.

*Daten*<br/>
Die Eingabehilfendaten für das Kontrollkästchen.

### <a name="return-value"></a>Rückgabewert

Gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Standardmäßig legt diese Methode die Eingabehilfendaten für das Kontrollkästchen fest und gibt immer TRUE zurück. Setzen Sie diese Methode außer Kraft, um die Barrierefreiheitsdaten festzulegen und einen Wert zurückzugeben, der den Erfolg oder einen Fehler angibt.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel-Klasse](../../mfc/reference/cmfcribbonpanel-class.md)
