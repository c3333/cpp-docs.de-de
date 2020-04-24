---
title: CMFCToolBarComboBoxButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
ms.openlocfilehash: 995d7d0db55889130e1cad9585b8fc87285ffd27
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754012"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton-Klasse

Eine Symbolleistenschaltfläche, die ein Kombinationsfeldsteuerelement ( [CComboBox Class](../../mfc/reference/ccombobox-class.md)) enthält.

## <a name="syntax"></a>Syntax

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Erstellt ein Objekt vom Typ `CMFCToolBarComboBoxButton`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Fügt ein Element am Ende der Kombinationsfeldliste hinzu.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Fügt der Liste der Kombinationsfelder ein Element hinzu. Die Reihenfolge der Elemente in `Compare`der Liste wird durch angegeben.|
|[CMFCToolBarComboBoxButton::Vergleichen](#compare)|Vergleicht zwei Elemente. Wird aufgerufen, `AddSortedItems` um Elemente zu sortieren, die der Kombinationsfeldliste hinzugefügt werden.|
|[CMFCToolBarComboBoxButton::CreateBearbeiten](#createedit)|Erstellt ein neues Bearbeitungssteuerelement für die Kombinationsfeldschaltfläche.|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Löscht ein Element aus der Kombinationsfeldliste.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Gibt den Index des Elements zurück, das eine angegebene Zeichenfolge enthält.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Gibt einen Zeiger auf die Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID zurück.|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Gibt einen Zeiger auf das Kombinationsfeldsteuerelement zurück, das in die Kombinationsfeldschaltfläche eingebettet ist.|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Gibt die Anzahl der Elemente in der Kombinationsfeldliste zurück.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Sucht die Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID. Gibt die Anzahl der Elemente in der Kombinationsfeldliste dieser Schaltfläche zurück.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Gibt den Index des ausgewählten Elements in der Kombinationsfeldliste zurück.|
|[CMFCToolBarComboBoxButton::GetCurselAll](#getcurselall)|Sucht die Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID und gibt den Index des ausgewählten Elements in der Kombinationsfeldliste dieser Schaltfläche zurück.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Gibt einen Zeiger auf das Bearbeitungssteuerelement zurück, das in die Kombinationsfeldschaltfläche eingebettet ist.|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Gibt die Zeichenfolge zurück, die einem angegebenen Index in der Kombinationsfeldliste zugeordnet ist.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Sucht die Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID und gibt die Zeichenfolge zurück, die einem Index in der Kombinationsfeldliste dieser Schaltfläche zugeordnet ist.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Gibt den 32-Bit-Wert zurück, der einem angegebenen Index in der Kombinationsfeldliste zugeordnet ist.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Sucht die Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID und gibt den 32-Bit-Wert zurück, der einem Index in der Kombinationsfeldliste dieser Schaltfläche zugeordnet ist.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Sucht die Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID. Ruft den 32-Bit-Wert ab, der einem Index in der Kombinationsfeldliste dieser Schaltfläche zugeordnet ist, und gibt den 32-Bit-Wert als Zeiger zurück.|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Gibt den Text aus dem Bearbeitungssteuerelement des Kombinationsfelds zurück.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Sucht die Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID und gibt den Text aus dem Bearbeitungssteuerelement dieser Schaltfläche zurück.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Legt fest, ob Kombinationsfeldschaltflächen in der Anwendung zentriert oder am oberen Rand der Symbolleiste ausgerichtet sind.|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Bestimmt, ob Kombinationsfeldschaltflächen in der Anwendung ein flaches Erscheinungsbild haben.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Entfernt alle Elemente aus dem Listenfeld und bearbeitet die Steuerung des Kombinationsfelds.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Wählt ein Element im Kombinationsfeld entsprechend seinem Index, 32-Bit-Wert oder String aus und benachrichtigt das Kombinationsfeldsteuerelement über die Auswahl.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Sucht die Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID. Ruft `SelectItem` ein Element im Kombinationsfeld dieser Schaltfläche entsprechend seinem Zeichenfolgen-, Index- oder 32-Bit-Wert auf.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Gibt an, ob Kombinationsfeldschaltflächen in der Anwendung vertikal zentriert oder am oberen Rand der Symbolleiste ausgerichtet sind.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Legt die Höhe des Dropdown-Listenfelds fest.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Gibt an, ob Kombinationsfeldschaltflächen in der Anwendung ein flaches Erscheinungsbild haben.|

## <a name="remarks"></a>Bemerkungen

Führen Sie die folgenden Schritte aus, um eine Kombinationsfeldschaltfläche zu einer Symbolleiste hinzuzufügen:

1. Reservieren Sie eine Platzhalterressourcen-ID für die Schaltfläche in der übergeordneten Symbolleistenressource.

2. Konstruieren Sie ein `CMFCToolBarComboBoxButton`-Objekt.

3. Ersetzen Sie im Nachrichtenhandler, der die AFX_WM_RESETTOOLBAR-Nachricht verarbeitet, die Dummy-Schaltfläche durch die neue Kombinationsfeldschaltfläche mithilfe der [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Einstecken von Steuerelementen auf Symbolleisten](../../mfc/walkthrough-putting-controls-on-toolbars.md). Ein Beispiel für eine Symbolleistenschaltfläche für Kombinationsfelder finden Sie im Beispielprojekt VisualStudioDemo.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCToolBarComboBoxButton` -Klasse. Das Beispiel zeigt, wie Sie die Bearbeitungs- und Kombinationsfelder aktivieren, die vertikale Position der Kombinationsfeldschaltflächen in der Anwendung festlegen, die Höhe des Listenfelds festlegen, wenn es heruntergelassen wird, die flache Darstellung von Kombinationsfeldschaltflächen in der Anwendung festlegen und den Text im Bearbeitungsfeld der Kombinationsfeldschaltfläche festlegen. Dieser Codeausschnitt ist Teil des [Visual Studio Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxtoolbarcomboboxbutton.h

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a>CMFCToolBarComboBoxButton::AddItem

Fügt ein eindeutiges Element an das Listenfeld an.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parameter

*lpszItem*<br/>
[in] Der Text des Elements, das dem Listenfeld hinzugefügt werden soll.

*dwData*<br/>
[in] Die Daten, die dem Element zugeordnet sind, das dem Listenfeld hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des letzten Elements im Listenfeld.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nicht, wenn der Listenfeldstil sortiert ist.

Wenn sich der Elementtext bereits im Listenfeld befindet, werden die neuen Daten mit dem vorhandenen Element gespeichert. Bei der Suche nach dem Element wird die Groß-/Kleinschreibung beachtet.

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem

Fügt dem Listenfeld in der Reihenfolge, die durch die [Compare-Methode](#compare) definiert wird, ein Element hinzu.

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parameter

*lpszItem*<br/>
[in] Der Text des Elements, das dem Listenfeld hinzugefügt werden soll.

*dwData*<br/>
[in] Die Daten, die dem Element zugeordnet sind, das dem Listenfeld hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Index des Elements, das dem Listenfeld hinzugefügt wurde.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um dem Listenfeld Elemente in einer bestimmten Reihenfolge hinzuzufügen.

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched

Gibt an, ob sich die Größe der Kombinationsbox ändern kann.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück.

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Erstellt ein [CMFCToolBarComboBoxButton-Objekt.](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Parameter

*uiID*<br/>
[in] Die Befehls-ID der neuen Schaltfläche.

*iImage*<br/>
[in] Der Bildindex des Bildes, das der neuen Schaltfläche zugeordnet ist.

*dwStyle*<br/>
[in] Der Stil der neuen Schaltfläche.

*iWidth*<br/>
[in] Die Breite der neuen Schaltfläche in Pixel.

### <a name="remarks"></a>Bemerkungen

Die Standardbreite beträgt 150 Pixel.

Eine Liste der Symbolleistenschaltflächenstile finden Sie unter [ToolBar-Steuerelementstile](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData

Löscht benutzerdefinierte Daten.

```
virtual void ClearData();
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Methode nichts aus. Überschreiben Sie diese Methode in einer abgeleiteten Klasse, wenn Sie benutzerdefinierte Daten löschen möchten.

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a>CMFCToolBarComboBoxButton::Vergleichen

Vergleicht zwei Zeichenfolgen.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Parameter

*lpszItem1*<br/>
[in] Die erste zu vergleichende Zeichenfolge.

*lpszItem2*<br/>
[in] Die zweite zu vergleichende Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Ein Wert, der die lexikographische Beziehung zwischen den Zeichenfolgen angibt, bei der die Groß-/Kleinschreibung beachtet wird. Die folgende Tabelle enthält die möglichen Werte:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|\<0|Die erste Zeichenfolge ist kleiner als die zweite.|
|0|Die erste Zeichenfolge entspricht der zweiten.|
|>0|Die erste Zeichenfolge ist größer als die zweite.|

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um zu ändern, wie Elemente im Listenfeld sortiert werden.

Bei dem Vergleich wird die Groß-/Kleinschreibung berücksichtigt.

Diese Methode wird nur von der [AddSortedItem-Methode](#addsorteditem) aufgerufen.

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarComboBoxButton::Kopieren von

Kopiert den Status `CMFCToolBarComboBoxButton` des angegebenen Objekts in das aktuelle Objekt.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
[in] Das `CMFCToolBarComboBoxButton` Quellobjekt.

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo

Erstellt ein neues Kombinationsfeld für die Kombinationsbox-Schaltfläche.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster der Schaltfläche.

*Rect*<br/>
[in] Begrenzungsrechteck des Kombinationsfelds.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neue Kombinationsfeld, wenn die Methode erfolgreich war. andernfalls NULL.

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarComboBoxButton::CreateBearbeiten

Erstellt ein neues Bearbeitungsfeld für die Kombinationsfeldschaltfläche.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster der Schaltfläche.

*Rect*<br/>
[in] Begrenzungsrechteck des neuen Bearbeitungsfelds.

*dwEditStyle*<br/>
[in] Steuern Sie den Stil des neuen Bearbeitungsfelds.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neue Bearbeitungsfeld, wenn die Methode erfolgreich war. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn ein neues Bearbeitungsfeld für eine Kombinationsfeldschaltfläche erstellt wird. Überschreiben Sie diese Methode, um zu ändern, wie [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) erstellt wird.

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem

Löscht ein angegebenes Element aus dem Listenfeld.

```
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
[in] Der Text des zu löschenden Elements. Wenn mehrere Elemente mit demselben Text vorhanden sind, wird das erste Element gelöscht.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Element gefunden und erfolgreich gelöscht wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData

Dupliziert benutzerdefinierte Daten.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Methode nichts aus. Überschreiben Sie diese Methode in einer abgeleiteten Klasse, wenn Sie benutzerdefinierte Daten kopieren möchten.

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow

Aktiviert oder deaktiviert die Bearbeitungs- und Kombinationsfelder.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um die Bearbeitungs- und Kombinationsfelder zu aktivieren; FALSE, um die Bearbeitungs- und Kombinationsfelder zu deaktivieren.

### <a name="remarks"></a>Bemerkungen

Wenn diese Option deaktiviert ist, können die Steuerelemente nicht aktiv werden und benutzereingaben nicht akzeptieren.

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton

Kopiert eine Zeichenfolge aus der Anwendungszeichenfolgentabelle mithilfe der Befehls-ID der Kombinationsbox in das angegebene Menü.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parameter

*menuButton*<br/>
[out] Verweis auf eine Menüschaltfläche.

### <a name="return-value"></a>Rückgabewert

Immer TRUE.

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem

Gibt den Index des ersten Elements im Listenfeld zurück, das eine angegebene Zeichenfolge enthält.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
[in] Der Text, nach dem im Listenfeld gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des Elements; oder CB_ERR, wenn das Element nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd

Ruft einen Zeiger auf die Kombinationsfeldschaltfläche ab, die über eine angegebene Befehls-ID verfügt.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID einer Kombinationsbox-Schaltfläche.

*bIsFocus*<br/>
[in] TRUE, um nur fokussierte Schaltflächen zu suchen; FALSE, um alle Schaltflächen zu durchsuchen.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Kombinationsfeldschaltfläche; oder NULL, wenn die Schaltfläche nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox

Gibt einen Zeiger auf das Kombinationsfeld in der Kombinationsfeldschaltfläche zurück.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das [CComboBox-Klassenobjekt,](../../mfc/reference/ccombobox-class.md) wenn die Methode erfolgreich war. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID

Ruft die Kontextmenüressourcen-ID für die Kombinationsfeldschaltfläche ab.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Rückgabewert

Die Ressourcen-ID des Kontextmenüs.

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount

Gibt die Anzahl der Elemente im Listenfeld zurück.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Listenfeld.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll

Ruft die Anzahl der Elemente im Listenfeld einer Kombinationsfeldschaltfläche ab, die über eine angegebene Befehls-ID verfügt.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID einer Kombinationsbox-Schaltfläche.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Listenfeld; Andernfalls CB_ERR, wenn die Kombinationsbox-Schaltfläche nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel

Ruft den Index des aktuell ausgewählten Elements im Listenfeld ab.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Rückgabewert

Der Index des aktuell ausgewählten Elements im Listenfeld; oder CB_ERR, wenn kein Element ausgewählt ist.

### <a name="remarks"></a>Bemerkungen

Der Listenfeldindex ist nullbasiert.

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurselAll

Gibt den Index des aktuell ausgewählten Elements im Listenfeld einer Kombinationsfeldschaltfläche zurück, die über eine angegebene Befehls-ID verfügt.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID einer Kombinationsbox-Schaltfläche.

### <a name="return-value"></a>Rückgabewert

Der Index des aktuell ausgewählten Elements im Listenfeld; Andernfalls CB_ERR, wenn kein Element ausgewählt ist oder keine Kombinationsfeldschaltfläche gefunden wird.

### <a name="remarks"></a>Bemerkungen

Der Listenfeldindex ist nullbasiert.

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl

Gibt einen Zeiger auf das Bearbeitungsfeld in der Kombinationsfeldschaltfläche zurück.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Bearbeitungsfeld, wenn die Methode erfolgreich war. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd

Gibt das Fensterhandle für das Kombinationsfeld zurück.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Rückgabewert

Das Fensterhandle oder NULL, wenn das Kombinationsfeld keinem Fensterobjekt zugeordnet ist.

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem

Gibt die Zeichenfolge zurück, die einem Element in einem angegebenen Index im Listenfeld zugeordnet ist.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Nullbasierter Index eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Zeichenfolge, die dem Element zugeordnet ist; Andernfalls NULL, wenn der Indexparameter ungültig ist oder wenn der Indexparameter -1 ist und kein ausgewähltes Element im Kombinationsfeld vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Ein Indexparameter von -1 gibt die Zeichenfolge des aktuell ausgewählten Elements zurück.

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

Gibt die Zeichenfolge zurück, die einem Element in einem angegebenen Index im Listenfeld einer Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID zugeordnet ist.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID einer Kombinationsbox-Schaltfläche.

*iIndex*<br/>
[in] Der nullbasierte Index eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Zeichenfolge des Elements, wenn die Methode erfolgreich war. Andernfalls NULL, wenn der Index ungültig ist, eine Kombinationsfeldschaltfläche nicht gefunden wird oder wenn der Index -1 ist und kein ausgewähltes Element im Kombinationsfeld vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Ein Indexwert von -1 gibt die Zeichenfolge des aktuell ausgewählten Elements zurück.

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData

Gibt die Daten zurück, die einem Element in einem bestimmten Index im Listenfeld zugeordnet sind.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

Die dem Element zugeordneten Daten; oder 0, wenn das Element nicht vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Ein Indexparameter von -1 gibt die Daten zurück, die dem aktuell ausgewählten Element zugeordnet sind.

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll

Gibt die Daten zurück, die einem Element in einem bestimmten Index im Listenfeld einer Kombinationsfeldschaltfläche mit einer bestimmten Befehls-ID zugeordnet sind.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID einer Kombinationsbox-Schaltfläche.

*iIndex*<br/>
[in] Der nullbasierte Index eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

Die Daten, die dem Element zugeordnet sind, wenn die Methode erfolgreich war. Andernfalls 0, wenn der angegebene Index ungültig ist, oder CB_ERR, wenn die Schaltfläche "Kombinationsfeld" nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

Ein Indexparameter von -1 gibt die Daten zurück, die dem aktuell ausgewählten Element zugeordnet sind.

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

Gibt die Daten zurück, die einem Element in einem bestimmten Index im Listenfeld einer Kombinationsfeldschaltfläche mit einer bestimmten Befehls-ID zugeordnet sind. Diese Daten werden als Zeiger zurückgegeben.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID der Kombinationsbox-Schaltfläche.

*iIndex*<br/>
[in] Der nullbasierte Index eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger, der dem Element zugeordnet ist, wenn die Methode erfolgreich war. Andernfalls -1, wenn ein Fehler auftritt, oder NULL, wenn die Schaltfläche "Kombinationsfeld" nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt

Gibt die Eingabeaufforderungszeichenfolge für die Kombinationsfeldschaltfläche zurück.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Rückgabewert

Die Eingabeaufforderungszeichenfolge.

### <a name="remarks"></a>Bemerkungen

Diese Methode ist derzeit nicht implementiert.

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a>CMFCToolBarComboBoxButton::GetText

Ruft den Text im Bearbeitungsfeld ab.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Rückgabewert

Der Text im Bearbeitungsfeld.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

Ruft den Text im Bearbeitungsfeld einer Kombinationsfeldschaltfläche ab, die über eine angegebene Befehls-ID verfügt.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID einer bestimmten Kombinationsfeldschaltfläche.

### <a name="return-value"></a>Rückgabewert

Der Text im Bearbeitungsfeld, wenn die Methode erfolgreich war; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus

Gibt an, ob das Kombinationsfeld derzeit den Fokus hat.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Kombinationsfeld derzeit den Fokus hat; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt auch TRUE zurück, wenn ein untergeordnetes Fenster des Kombinationsfelds derzeit den Fokus hat.

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert

Gibt die vertikale Position der Kombinationsfeldschaltflächen in der Anwendung zurück.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltflächen zentriert sind; FALSE, wenn die Schaltflächen oben ausgerichtet sind.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode

Gibt die flache Darstellung von Kombinationsfeldschaltflächen in der Anwendung zurück.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltflächen einen flachen Stil haben; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Der Standardstil für Kombinationsfeldschaltflächen ist FALSE.

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnervon

Gibt an, ob das angegebene Handle der Kombinationsfeldschaltfläche oder einem der untergeordneten Elemente zugeordnet ist.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Parameter

*Hwnd*<br/>
[in] Ein Fenstergriff.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Griff mit der Kombinationsbox-Schaltfläche oder einem seiner untergeordneten Elemente zugeordnet ist; andernfalls FALSE.

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton

Gibt an, ob sich die Kombinationsfeldschaltfläche in einem Menübandbereich befindet.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Rückgabewert

Immer FALSE

### <a name="remarks"></a>Bemerkungen

Standardmäßig gibt diese Methode immer FALSE zurück, was bedeutet, dass die Kombinationsfeldschaltfläche nie in einem Multifunktionsleistenbedienfeld angezeigt wird.

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible

Gibt den Sichtbarkeitsstatus der Kombinationsfeldschaltfläche zurück.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Rückgabewert

Der Sichtbarkeitsstatus der Kombinationsfeldschaltfläche.

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand

Gibt an, ob die Kombinationsfeldschaltfläche die Nachricht verarbeitet.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parameter

*iNotifyCode*<br/>
[in] Die dem Befehl zugeordnete Benachrichtigung.

### <a name="return-value"></a>Rückgabewert

Gibt an, ob die Kombinationsbox-Schaltfläche die Nachricht verarbeitet.

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolbarComboBoxButton::OnAddToCustomizePage

Wird vom Framework aufgerufen, wenn die Schaltfläche zum Dialogfeld **Anpassen** hinzugefügt wird.

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCToolbarComboBoxButton::OnCalculateSize

Wird vom Framework aufgerufen, um die Größe der Schaltfläche zu berechnen.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Der Gerätekontext, der die Kombinationsfeldschaltfläche anzeigt.

*sizeStandard*<br/>
[in] Die Standardgröße der Kombinationsfeldschaltfläche.

*bHorz*<br/>
[in] Der Dockstatus der übergeordneten Symbolleiste. TRUE, wenn die Symbolleiste horizontal und FALSE angedockt ist, wenn die Symbolleiste vertikal angedockt ist.

### <a name="return-value"></a>Rückgabewert

Eine `SIZE` Struktur, die die Abmessungen der Kombinationsfeldschaltfläche in Pixel enthält.

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

Wird vom Framework aufgerufen, wenn die Kombinationsfeldschaltfläche in eine neue Symbolleiste eingefügt wird.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Zeiger auf die neue übergeordnete Symbolleiste.

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick

Wird vom Framework aufgerufen, wenn der Benutzer auf die Schaltfläche "Kombinationsfeld" klickt.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
[in] Zeigen Sie mit dem Mauszeiger auf das übergeordnete Fenster der Schaltfläche "Kombinationsbox".

*bDelay*<br/>
[in] Reserviert für die Verwendung in einer abgeleiteten Klasse.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode das Ereignis behandelt; andernfalls FALSE.

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor

Wird vom Framework aufgerufen, wenn der Benutzer die Farbe der übergeordneten Symbolleiste ändert, um die Schaltflächenfarbe des Kombinationsfelds festzulegen.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Der Gerätekontext, der die Kombinationsfeldschaltfläche anzeigt.

*nCtlColor*<br/>
[in] Nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Behandeln Sie den Pinsel, den das Framework verwendet, um den Hintergrund der Kombinationsbox-Schaltfläche zu malen.

### <a name="remarks"></a>Bemerkungen

Diese Methode legt auch die Textfarbe der Kombinationsfeldschaltfläche fest.

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a>CMFCToolbarComboBoxButton::OnDraw

Wird vom Framework aufgerufen, um die Kombinationsfeldschaltfläche mithilfe der angegebenen Stile und Optionen zu zeichnen.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>Parameter

*Pdc*<br/>
[in] Der Gerätekontext, der die Schaltfläche anzeigt.

*Rect*<br/>
[in] Das umgrenzende Rechteck der Schaltfläche.

*pImages*<br/>
[in] Die Sammlung von Bildern, die der Schaltfläche zugeordnet ist.

*bHorz*<br/>
[in] Der Dockstatus der übergeordneten Symbolleiste. TRUE, wenn die Symbolleiste horizontal und FALSE angedockt ist, wenn die Symbolleiste vertikal angedockt ist.

*bCustomizeMode*<br/>
[in] Gibt an, ob sich die Anwendung im Anpassungsmodus befindet.

*bHighlight*<br/>
[in] Ob die Kombinationsbox-Schaltfläche hervorgehoben werden soll.

*bDrawBorder*<br/>
[in] Gibt an, ob die Kombinationsbox-Schaltfläche mit einem Rahmen gezeichnet werden soll.

*bGrayDisabledButtons*<br/>
[in] TRUE zum Zeichnen schattierter deaktivierter Schaltflächen; FALSE, um die Sammlung deaktivierter Bilder zu verwenden.

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCToolbarComboBoxButton::OnDrawonCustomizeList

Wird vom Framework aufgerufen, um die Kombinationsfeldschaltfläche im **Befehlsbereich** des Dialogfelds **Anpassen** zu zeichnen.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Der Gerätekontext, der die Kombinationsfeldschaltfläche anzeigt.

*Rect*<br/>
[in] Das umschließende Rechteck der Kombinationsfeldschaltfläche.

*bAusgewählt*<br/>
[in] TRUE, wenn die Kombinationsbox-Schaltfläche ausgewählt ist; andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

Die Breite (in Pixel) der Kombinationsfeldschaltfläche.

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged

Wird vom Framework aufgerufen, um die Kombinationsfeldschaltflächenschrift artiumzulegen, wenn sich die Anwendungsschriftart ändert.

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove

Wird vom Framework aufgerufen, um die Position der Kombinationsfeldschaltfläche zu ändern, wenn die übergeordnete Symbolleiste verschoben wird.

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow

Wird vom Framework aufgerufen, wenn die Kombinationsfeldschaltfläche ausgeblendet oder angezeigt wird.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
[in] Gibt an, ob die Kombinationsbox-Schaltfläche ausgeblendet oder angezeigt werden soll.

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize

Wird vom Framework aufgerufen, um die Größe der Schaltfläche "Kombinationsfeld" zu ändern, wenn die übergeordnete Symbolleiste die Größe ändert.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parameter

*iSize*<br/>
[in] Die neue Breite der Kombinationsbox-Schaltfläche.

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolbarComboBoxButton::OnUpdateToolTip

Wird vom Framework aufgerufen, wenn der Benutzer die QuickInfo für die Kombinationsbox-Schaltfläche ändert.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Zeigen Sie mit dem Mauszeiger auf das übergeordnete Fenster für die Schaltfläche "Kombinationsbox".

*iButtonIndex*<br/>
[in] ID der Combo-Box-Taste.

*wndToolTip*<br/>
[in] Die Werkzeugspitze, die mit der Kombinationsbox-Schaltfläche in Verbindung gebracht werden soll.

*Str*<br/>
[in] Der QuickInfo-Text.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode das Ereignis behandelt; andernfalls FALSE.

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems

Löscht alle Elemente aus der Liste und bearbeitet Felder.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Bemerkungen

Entfernt alle Elemente aus dem Listenfeld und bearbeitet die Steuerung eines Kombinationsfelds.

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem

Wählt ein Element im Listenfeld aus.

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index eines Elements im Listenfeld.

*bNotify*<br/>
[in] TRUE, um die Kombinationsfeldschaltfläche der Auswahl zu benachrichtigen; andernfalls FALSE.

*dwData*<br/>
[in] Die Daten, die einem Element im Listenfeld zugeordnet sind.

*lpszText*<br/>
[in] Der Text eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll

Wählt ein Element im Listenfeld einer Kombinationsfeldschaltfläche mit einer angegebenen Befehls-ID aus.

```
static BOOL SelectItemAll(
    UINT uiCmd,
    int iIndex);

static BOOL SelectItemAll(
    UINT uiCmd,
    DWORD_PTR dwData);

static BOOL SelectItemAll(
    UINT uiCmd,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID der Kombinationsfeldschaltfläche, die das Listenfeld enthält.

*iIndex*<br/>
[in] Der nullbasierte Index des Elements im Listenfeld. Der Wert -1 entfernt jede aktuelle Auswahl im Listenfeld und löscht das Bearbeitungsfeld.

*dwData*<br/>
[in] Die Daten eines Elements im Listenfeld.

*lpszText*<br/>
[in] Der Text eines Elements im Listenfeld.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a>CMFCToolBarComboBoxButton::Serialisieren

Liest dieses Objekt aus einem Archiv oder schreibt es in ein Archiv.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*ar*<br/>
[in, out] Das `CArchive` zu serialisierende Objekt.

### <a name="remarks"></a>Bemerkungen

Einstellungen im `CArchive` Objekt bestimmen, ob diese Methode in das Archiv gelesen oder schreibt.

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData

Füllt das angegebene `CAccessibilityData` Objekt mithilfe von Eingabehilfendaten aus der Kombinationsfeldschaltfläche.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parameter

*pParent*<br/>
[in] Das übergeordnete Fenster der Kombinationsfeldschaltfläche.

*Daten*<br/>
[out] Ein `CAccessibilityData` Objekt, das die Eingabehilfendaten von der Schaltfläche "Kombinationsbox" empfängt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert

Legt die vertikale Position der Kombinationsfeldschaltflächen in der Anwendung fest.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Parameter

*bCenterVert*<br/>
[in] TRUE, um die Kombinationsbox-Schaltfläche in der Symbolleiste zu zentrieren; FALSE, um die Kombinationsbox-Schaltfläche am oberen Rand der Symbolleiste auszurichten.

### <a name="remarks"></a>Bemerkungen

Standardmäßig werden Kombinationsfeldschaltflächen nach oben ausgerichtet.

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID

Legt die Ressourcen-ID des Kontextmenüs für die Kombinationsfeldschaltfläche fest.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parameter

*uiResID*<br/>
[in] Die Ressourcen-ID des Kontextmenüs.

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight

Legt die Höhe des Listenfelds fest, wenn es heruntergelassen wird.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parameter

*nHeight*<br/>
[in] Die Höhe des Listenfelds in Pixel.

### <a name="remarks"></a>Bemerkungen

Die Standardhöhe beträgt 150 Pixel.

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode

Legt die flache Darstellung von Kombinationsfeldschaltflächen in der Anwendung fest.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parameter

*bFlat*<br/>
[in] TRUE für ein flaches Aussehen; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Der Standardstil für Kombinationsfeldschaltflächen ist FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle

Legt den angegebenen Stil für die Schaltfläche "Kombinationsbox" fest und zeichnet das Steuerelement neu, wenn es nicht deaktiviert ist.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parameter

*nStyle*<br/>
[in] Eine bitweise Kombination (OR) von Symbolleistenstilen.

### <a name="remarks"></a>Bemerkungen

Eine Liste der Symbolleistenschaltflächenstile finden Sie unter [ToolBar-Steuerelementstile](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a>CMFCToolBarComboBoxButton::SetText

Legt den Text im Bearbeitungsfeld der Kombinationsfeldschaltfläche fest.

```cpp
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
[in] Zeigen Sie mit dem Zeiger auf eine Zeichenfolge, die den Text für das Bearbeitungsfeld enthält.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton-Klasse](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Exemplarische Vorgehensweise: Steuerelemente in eine Symbolleiste einfügen](../../mfc/walkthrough-putting-controls-on-toolbars.md)
