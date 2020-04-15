---
title: CMFCRibbonButtonsGroup-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
ms.openlocfilehash: af5919ff2a72fc2aa1eeeb95fc93afbe9e743582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375287"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup-Klasse

Mit `CMFCRibbonButtonsGroup` der Klasse können Sie eine Reihe von Menübandschaltflächen in einer Gruppe organisieren. Alle Schaltflächen der Gruppe liegen innerhalb eines Rahmens direkt horizontal nebeneinander.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Erstellt ein `CMFCRibbonButtonsGroup`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Fügt einer Gruppe eine Schaltfläche hinzu.|
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Fügt einer Gruppe eine Liste von Schaltflächen hinzu.|
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Gibt einen Zeiger auf die Schaltfläche zurück, die sich an einem angegebenen Index befindet.|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Gibt die Anzahl der Schaltflächen in der Gruppe zurück.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Gibt die Bildgröße der normalen Bilder in der Multifunktionsleistengruppe zurück (überschreibt [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Gibt die normale Größe des Multifunktionsleistenelements zurück (überschreibt [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Gibt an, ob das `CMFCRibbonButtonsGroup` Objekt Symbolleistenbilder enthält.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Zeichnet das entsprechende Bild für eine angegebene Schaltfläche, je nachdem, ob die Schaltfläche normal, hervorgehoben oder deaktiviert ist.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Entfernt alle Schaltflächen `CMFCRibbonButtonsGroup` aus dem Objekt.|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Weist der Gruppe Bilder zu.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Legt das `CMFCRibbonCategory` übergeordnete `CMFCRibbonButtonsGroup` Element des Objekts und alle darin enthaltenen Schaltflächen fest (überschreibt [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Bemerkungen

Die Gruppe wird von [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) abgeleitet und kann als einzelne Entität bearbeitet werden. Sie können die Gruppe in jedem Bedienfeld oder Popupmenü positionieren.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCRibbonButtonsGroup` -Klasse. Das Beispiel zeigt, `CMFCRibbonButtonsGroup` wie Sie ein Objekt erstellen, der Gruppe von Menübandschaltflächen Bilder zuweisen und der Gruppe der Menübandschaltflächen eine Schaltfläche hinzufügen. Dieser Codeausschnitt ist Teil des [Draw Client-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxribbonbuttonsgroup.h

## <a name="cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a>CMFCRibbonButtonsGroup::AddButton

Fügt einer Gruppe eine Schaltfläche hinzu.

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parameter

*pButton*<br/>
[in] Ein Zeiger auf eine schaltfläche, die hinzugefügt werden soll.

## <a name="cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a>CMFCRibbonButtonsGroup::AddButtons

Fügt einer Gruppe eine Liste von Schaltflächen hinzu.

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Parameter

*lstButtons*<br/>
[in] Eine Liste von Zeigern auf die Schaltflächen, die Sie hinzufügen möchten.

## <a name="cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a>CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

Erstellt ein `CMFCRibbonButtonsGroup`-Objekt.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parameter

*pButton*<br/>
[in] Gibt eine Schaltfläche an, die `CMFCRibbonButtonsGroup` dem neu erstellten Objekt hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a>CMFCRibbonButtonsGroup::GetButton

Gibt einen Zeiger auf die Schaltfläche zurück, die sich an einem angegebenen Index befindet.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Parameter

*Ⅰ*<br/>
[in] Ein nullbasierter Index einer Schaltfläche, die zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Schaltfläche, die sich am angegebenen Index befindet. NULL, wenn der angegebene Index anicht zulässig ist.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a>CMFCRibbonButtonsGroup::GetCount

Gibt die Anzahl der Schaltflächen in der Gruppe zurück.

```
int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Schaltflächen in der Gruppe.

## <a name="cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a>CMFCRibbonButtonsGroup::GetImageSize

Ruft die Quellbildgröße des `CMFCToolBarImages` `m_Images`geschützten Elements ab.

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Quellbildgröße der Symbolleistenbilder zurück, sofern `CSize` vorhanden, oder eine von Null, wenn nicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonButtonsGroup::GetRegularSize

Ruft die maximal mögliche Größe des Menübandgruppenelements ab.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeigen Sie auf den Gerätekontext der Menübandgruppe.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a>CMFCRibbonButtonsGroup::HasImages

Gibt an, ob das `CMFCRibbonButtonsGroup` Objekt Symbolleistenbilder enthält.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das geschützte `CMFCToolBarImages` Element `m_Images` Bilder enthält, oder FALSE, wenn nicht.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a>CMFCRibbonButtonsGroup::OnDrawImage

Zeichnet das entsprechende Bild für eine angegebene Schaltfläche, je nachdem, ob die Schaltfläche normal, hervorgehoben oder deaktiviert ist.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf den Gerätekontext `CMFCRibbonButtonsGroup` des Objekts.

*rectImage*<br/>
[in] Das Rechteck, in dem das Bild gezeichnet werden soll.

*pButton*<br/>
[in] Die Schaltfläche, für die das Bild gezeichnet werden soll.

*nImageIndex*<br/>
[in] Der Index des Bildes, das auf der Schaltfläche gezeichnet werden soll (in einem der drei Bildarrays für normale, hervorgehobene oder deaktivierte Schaltflächen).

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a>CMFCRibbonButtonsGroup::RemoveAll

Entfernt alle Schaltflächen `CMFCRibbonButtonsGroup` aus dem Objekt.

```
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a>CMFCRibbonButtonsGroup::SetImages

Weist der Gruppe der Menübandschaltflächen Bilder zu.

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Parameter

*pImages*<br/>
[in] Regelmäßige Bilder.

*pHotImages*<br/>
[in] Heiße Bilder.

*pDisabledImages*<br/>
[in] Deaktivierte Bilder.

### <a name="remarks"></a>Bemerkungen

Rufen `SetImages` Sie an, bevor Sie einer Gruppe Schaltflächen hinzufügen. Die Anzahl der Bilder muss größer oder gleich der Anzahl der Schaltflächen sein, die der Gruppe hinzugefügt werden sollen.

> [!NOTE]
> Heiße Bilder sind Bilder, die angezeigt werden, wenn der Benutzer mit der Maus über die Schaltfläche zeigt. Deaktivierte Bilder sind Bilder, die angezeigt werden, wenn die Schaltfläche deaktiviert ist.

## <a name="cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a>CMFCRibbonButtonsGroup::SetParentCategory

Legt das `CMFCRibbonCategory` übergeordnete `CMFCRibbonButtonsGroup` Element des Objekts und alle darin enthaltenen Schaltflächen fest.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Parameter

*pKategorie*<br/>
[in] Zeiger auf die festzulegende übergeordnete Kategorie (die Registerkartengruppen in Menübandsteuerelementen werden als Kategorien bezeichnet).

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
