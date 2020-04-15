---
title: CMFCRibbonComboBox-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
ms.openlocfilehash: 5846b1c5590a756f0a0820583af3d0b159968ea2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375227"
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox-Klasse

Die `CMFCRibbonComboBox` Klasse implementiert ein Kombinationsfeldsteuerelement, das Sie einer Multifunktionsleistenleiste, einem Menübandbereich oder einem Menümitband-Popupmenü hinzufügen können.

## <a name="syntax"></a>Syntax

```cpp
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Erstellt ein CMFCRibbonComboBox-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonComboBox::AddItem](#additem)|Fügt ein eindeutiges Element an das Listenfeld an.|
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Löscht ein angegebenes Element aus dem Listenfeld.|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Gibt an, ob das Listenfeld die Größe ändern kann, wenn es herunterfällt.|
|[CMFCRibbonComboBox::FindItem](#finditem)|Gibt den Index des ersten Elements im Listenfeld zurück, das einer angegebenen Zeichenfolge entspricht.|
|[CMFCRibbonComboBox::GetCount](#getcount)|Gibt die Anzahl der Elemente im Listenfeld zurück.|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Ruft den Index des aktuell ausgewählten Elements im Listenfeld ab.|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Ruft die Höhe des Listenfelds ab, wenn das Listenfeld heruntergelassen wird.|
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Gibt die Größe des Kombinationsfelds zurück, wie es im Zwischenmodus angezeigt wird.|
|[CMFCRibbonComboBox::GetItem](#getitem)|Gibt die Zeichenfolge zurück, die einem Element in einem angegebenen Index im Listenfeld zugeordnet ist.|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Gibt die Daten zurück, die einem Element in einem angegebenen Index im Listenfeld zugeordnet sind.|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Gibt an, ob das Steuerelement ein Bearbeitungsfeld enthält.|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Gibt an, ob die Größe des Listenfelds geändert werden kann.|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Wird vom Framework aufgerufen, wenn der Benutzer ein Element im Listenfeld auswählt.|
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Löscht alle Elemente aus dem Listenfeld und löscht das Bearbeitungsfeld.|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Wählt ein Element im Listenfeld aus.|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Legt die Höhe des Listenfelds fest, wenn es heruntergelassen wird.|

## <a name="remarks"></a>Bemerkungen

Das Menüband-Kombinationsfeld besteht aus einem Listenfeld, das entweder mit einer statischen Beschriftung oder einer Beschriftung kombiniert wird, die vom Benutzer bearbeitet werden kann. Sie müssen angeben, welcher Typ beim Erstellen des Menüband-Kombinationsfelds angezeigt werden soll.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCRibbonComboBox` wie Sie ein Objekt der Klasse erstellen, dem Kombinationsfeld ein Element hinzufügen, ein Element im Kombinationsfeld auswählen und einem Bedienfeld ein Kombinationsfeld hinzufügen.

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxribboncombobox.h

## <a name="cmfcribboncomboboxadditem"></a><a name="additem"></a>CMFCRibbonComboBox::AddItem

Fügt ein eindeutiges Element an das Listenfeld an.

```cpp
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parameter

*lpszItem*<br/>
[in] Die Zeichenfolge des hinzuzufügenden Elements.

*dwData*<br/>
[in] Die Daten, die dem hinzuzufügenden Element zugeordnet sind.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des angehängten Elements.

## <a name="cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a>CMFCRibbonComboBox::CMFCRibbonComboBox

Erstellt ein `CMFCRibbonComboBox`-Objekt.

```cpp
public:
CMFCRibbonComboBox(
    UINT nID,
    BOOL bHasEditBox=TRUE,
    Int nWidth=-1,
    LPCTSTR lpszLabel=NULL,
    Int nImage=-1);

protected:
CMFCRibbonComboBox();
```

### <a name="parameters"></a>Parameter

*nID*<br/>
[in] Die ID des Kombinationsfelds.

*bHasEditBox*<br/>
[in] TRUE, wenn Sie ein Bearbeitungsfeld innerhalb des Steuerelements verwenden möchten; FALSE sonst.

*nWidth*<br/>
[in] Breite des Kombinationsfelds in Pixel; oder -1 für die Standardbreite.

*lpszLabel*<br/>
[in] Die Anzeigebeschriftung des Kombinationsfelds.

*nImage*<br/>
[in] Der kleine Bildindex des Kombinationsfelds.

### <a name="remarks"></a>Bemerkungen

Die Standardbreite beträgt 108 Pixel.

## <a name="cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a>CMFCRibbonComboBox::DeleteItem

Löscht ein angegebenes Element aus dem Listenfeld.

```cpp
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index des zu löschenden Elements.

*dwData*<br/>
[in] Die Daten, die dem zu löschenden Element zugeordnet sind.

*lpszText*<br/>
[in] Die Zeichenfolge des zu löschenden Elements. Wenn mehrere Elemente mit derselben Zeichenfolge vorhanden sind, wird das erste Element gelöscht.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das angegebene Element gelöscht wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a>CMFCRibbonComboBox::EnableDropDownListResize

Gibt an, ob das Listenfeld die Größe ändern kann, wenn es herunterfällt.

```cpp
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um die Größenänderung zu aktivieren; FALSE, um die Größenänderung zu deaktivieren.

### <a name="remarks"></a>Bemerkungen

Wenn die Größenänderung aktiviert ist, ändert sich die Größe des Listenfelds an die angezeigten Elemente.

## <a name="cmfcribboncomboboxfinditem"></a><a name="finditem"></a>CMFCRibbonComboBox::FindItem

Gibt den Index des ersten Elements im Listenfeld zurück, das einer angegebenen Zeichenfolge entspricht.

```cpp
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
[in] Die Zeichenfolge eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des Elements; oder -1, wenn das Element nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncomboboxgetcount"></a><a name="getcount"></a>CMFCRibbonComboBox::GetCount

Gibt die Anzahl der Elemente im Listenfeld zurück.

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Listenfeld oder 0, wenn das Listenfeld keine Elemente enthält.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a>CMFCRibbonComboBox::GetCurSel

Ruft den Index des aktuell ausgewählten Elements im Listenfeld ab.

```cpp
int GetCurSel() const;
```

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index des aktuell ausgewählten Elements im Listenfeld; oder -1, wenn kein Element ausgewählt ist.

## <a name="cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a>CMFCRibbonComboBox::GetDropDownHeight

Ruft die Höhe des Listenfelds ab, wenn das Listenfeld heruntergelassen wird.

```cpp
int GetDropDownHeight();
```

### <a name="return-value"></a>Rückgabewert

Die Höhe des Listenfelds in Pixel.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonComboBox::GetIntermediateSize

Gibt die Größe des Kombinationsfelds zurück, wie es im Zwischenmodus angezeigt wird.

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext für das Kombinationsfeld.

### <a name="return-value"></a>Rückgabewert

Die Größe des Kombinationsfelds.

### <a name="remarks"></a>Bemerkungen

Die zurückgegebene Größe basiert auf der Größe des Kombinationsfelds, wenn kleine Bilder angezeigt werden.

## <a name="cmfcribboncomboboxgetitem"></a><a name="getitem"></a>CMFCRibbonComboBox::GetItem

Gibt die Zeichenfolge zurück, die einem Element in einem angegebenen Index im Listenfeld zugeordnet ist.

```cpp
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Zeichenfolge, die dem Element zugeordnet ist; Andernfalls NULL, wenn der Indexparameter ungültig ist oder wenn der Indexparameter -1 ist und im Kombinationsfeld kein Element ausgewählt ist.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a>CMFCRibbonComboBox::GetItemData

Gibt die Daten zurück, die einem Element in einem angegebenen Index im Listenfeld zugeordnet sind.

```cpp
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

Die dem Element zugeordneten Daten; oder 0, wenn das Element nicht vorhanden ist oder wenn der Indexparameter -1 ist und kein ausgewähltes Element im Listenfeld vorhanden ist.

## <a name="cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a>CMFCRibbonComboBox::HasEditBox

Gibt an, ob das Steuerelement ein Bearbeitungsfeld enthält.

```cpp
BOOL HasEditBox() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Steuerelement ein Bearbeitungsfeld enthält; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a>CMFCRibbonComboBox::IsResizeDropDownList

Gibt an, ob die Größe des Listenfelds geändert werden kann.

```cpp
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Größe des Listenfelds geändert werden kann; andernfalls FALSE. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>Bemerkungen

Sie können die Größenänderung des Listenfelds mithilfe der [CMFCRibbonComboBox::EnableDropDownListResize-Methode](#enabledropdownlistresize) aktivieren.

## <a name="cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a>CMFCRibbonComboBox::OnSelectItem

Wird vom Framework aufgerufen, wenn ein Benutzer ein Element im Listenfeld auswählt.

```cpp
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
[in] Der Index des ausgewählten Elements.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, wenn Sie eine Benutzereingabeauswahl verarbeiten möchten.

## <a name="cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a>CMFCRibbonComboBox::RemoveAllItems

Löscht alle Elemente aus dem Listenfeld und löscht das Bearbeitungsfeld.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncomboboxselectitem"></a><a name="selectitem"></a>CMFCRibbonComboBox::SelectItem

Wählt ein Element im Listenfeld aus.

```cpp
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index eines Elements im Listenfeld.

*dwData*<br/>
[in] Die Daten, die einem Element im Listenfeld zugeordnet sind.

*lpszText*<br/>
[in] Die Zeichenfolge eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCRibbonComboBox::SetDropDownHeight

Legt die Höhe des Listenfelds fest, wenn es heruntergelassen wird.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parameter

*nHeight*<br/>
[in] Die Höhe des Listenfelds in Pixel.

### <a name="remarks"></a>Bemerkungen

Die Standardhöhe beträgt 150 Pixel.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonEdit-Klasse](../../mfc/reference/cmfcribbonedit-class.md)
