---
title: CVSListBox-Klasse
ms.date: 11/19/2018
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
ms.openlocfilehash: 4ea48a263a01133419067979ee5fa3e62105c7f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373190"
---
# <a name="cvslistbox-class"></a>CVSListBox-Klasse

Die `CVSListBox` Klasse unterstützt ein bearbeitbares Listensteuerelement.

## <a name="syntax"></a>Syntax

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CVSListBox::CVSListBox](#cvslistbox)|Erstellt ein `CVSListBox`-Objekt.|
|`CVSListBox::~CVSListBox`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CVSListBox::AddItem](#additem)|Fügt einem Listensteuerelement eine Zeichenfolge hinzu. (Überschreibt `CVSListBoxBase::AddItem`.)|
|[CVSListBox::EditItem](#edititem)|Startet einen Bearbeitungsvorgang für den Text eines Listensteuerelements. (Überschreibt `CVSListBoxBase::EditItem`.)|
|[CVSListBox::GetCount](#getcount)|Ruft die Anzahl der Zeichenfolgen in einem bearbeitbaren Listensteuerelement ab. (Überschreibt `CVSListBoxBase::GetCount`.)|
|[CVSListBox::GetItemData](#getitemdata)|Ruft einen anwendungsspezifischen 32-Bit-Wert ab, der einem bearbeitbaren Listensteuerelement zugeordnet ist. (Überschreibt `CVSListBoxBase::GetItemData`.)|
|[CVSListBox::GetItemText](#getitemtext)|Ruft den Text eines bearbeitbaren Listensteuerelements ab. (Überschreibt `CVSListBoxBase::GetItemText`.)|
|[CVSListBox::GetSelItem](#getselitem)|Ruft den nullbasierten Index des aktuell ausgewählten Elements in einem bearbeitbaren Listensteuerelement ab. (Überschreibt `CVSListBoxBase::GetSelItem`.)|
|`CVSListBox::PreTranslateMessage`|Übersetzt Fensternachrichten, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. Weitere Informationen und Methodensyntax finden Sie unter [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Überschreibt `CVSListBoxBase::PreTranslateMessage`.)|
|[CVSListBox::RemoveItem](#removeitem)|Entfernt ein Element aus einem bearbeitbaren Listensteuerelement. (Überschreibt `CVSListBoxBase::RemoveItem`.)|
|[CVSListBox::SelectItem](#selectitem)|Wählt eine bearbeitbare Listensteuerelementzeichenfolge aus. (Überschreibt `CVSListBoxBase::SelectItem`.)|
|[CVSListBox::SetItemData](#setitemdata)|Ordnet einem bearbeitbaren Listensteuerelement einen anwendungsspezifischen 32-Bit-Wert zu. (Überschreibt `CVSListBoxBase::SetItemData`.)|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|Gibt das Handle an das aktuelle eingebettete Listenansichtssteuerelement zurück.|

## <a name="remarks"></a>Bemerkungen

Die `CVSListBox` Klasse stellt eine Reihe von Bearbeitungsschaltflächen bereit, mit denen der Benutzer die Elemente in einem Listensteuerelement erstellen, ändern, löschen oder neu anordnen kann.

Im Folgenden finden Sie ein Bild des bearbeitbaren Listensteuerelements. Der zweite Listeneintrag mit dem Titel "Item2" wird zur Bearbeitung ausgewählt.

![CVSListBox-Steuerelement](../../mfc/reference/media/cvslistbox.png "CVSListBox-Steuerelement")

Wenn Sie den Ressourcen-Editor verwenden, um ein bearbeitbares Listensteuerelement hinzuzufügen, beachten Sie, dass der **Toolbox-Bereich** des Editors kein vordefiniertes bearbeitbares Listensteuerelement bereitstellt. Fügen Sie stattdessen ein statisches Steuerelement wie das **Group Box-Steuerelement** hinzu. Das Framework verwendet das statische Steuerelement als Platzhalter, um die Größe und Position des bearbeitbaren Listensteuerelements anzugeben.

Um ein bearbeitbares Listensteuerelement in einer `CVSListBox` Dialogfeldvorlage zu verwenden, deklarieren Sie eine Variable in der Dialogfeldklasse. Um den Datenaustausch zwischen der Variablen `DDX_Control` und dem `DoDataExchange` Steuerelement zu unterstützen, definieren Sie einen Makroeintrag in der Methode des Dialogfelds. Standardmäßig wird das bearbeitbare Listensteuerelement ohne Bearbeitungsschaltflächen erstellt. Verwenden Sie die geerbte CVSListBoxBase::SetStandardButtons-Methode, um die Bearbeitungsschaltflächen zu aktivieren.

Weitere Informationen finden Sie im `New Controls` Beispielverzeichnis, im Beispiel, in den Dateien Page3.cpp und Page3.h.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxvslistbox.h

## <a name="cvslistboxadditem"></a><a name="additem"></a>CVSListBox::AddItem

Fügt einem Listensteuerelement eine Zeichenfolge hinzu.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>Parameter

*strIext*<br/>
[in] Ein Verweis auf eine Zeichenfolge.

*dwData*<br/>
[in] Ein anwendungsspezifischer 32-Bit-Wert, der der Zeichenfolge zugeordnet ist. Der Standardwert ist 0.

*iIndex*<br/>
[in] Der nullbasierte Index der Position, die die Zeichenfolge enthält. Wenn der *iIndex-Parameter* -1 ist, wird die Zeichenfolge am Ende der Liste hinzugefügt. Der Standardwert ist -1.

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index der Position der Zeichenfolge im Listensteuerelement.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CVSListBox::GetItemData-Methode,](#getitemdata) um den wert abzurufen, der durch den *Parameter dwData* angegeben wird. Dieser Wert kann eine anwendungsspezifische ganzzahlige Datei oder ein Zeiger auf andere Daten sein.

## <a name="cvslistboxcvslistbox"></a><a name="cvslistbox"></a>CVSListBox::CVSListBox

Erstellt ein `CVSListBox`-Objekt.

```
CVSListBox();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cvslistboxedititem"></a><a name="edititem"></a>CVSListBox::EditItem

Startet einen Bearbeitungsvorgang für den Text eines Listensteuerelements.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Nullbasierter Index eines Listensteuerelements.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bearbeitungsvorgang erfolgreich gestartet wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Der Benutzer startet einen Bearbeitungsvorgang entweder durch Doppelklicken auf die Beschriftung eines Elements oder durch Drücken der **Taste F2** oder **SPACEBAR,** wenn ein Element den Fokus hat.

## <a name="cvslistboxgetcount"></a><a name="getcount"></a>CVSListBox::GetCount

Ruft die Anzahl der Zeichenfolgen in einem bearbeitbaren Listensteuerelement ab.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Listensteuerelement.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass die Anzahl größer als der Indexwert des letzten Elements ist, da der Index nullbasiert ist.

## <a name="cvslistboxgetitemdata"></a><a name="getitemdata"></a>CVSListBox::GetItemData

Ruft einen anwendungsspezifischen 32-Bit-Wert ab, der einem bearbeitbaren Listensteuerelement zugeordnet ist.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index eines bearbeitbaren Listensteuerelements.

### <a name="return-value"></a>Rückgabewert

Der 32-Bit-Wert, der dem angegebenen Element zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CVSListBox::SetItemData](#setitemdata) oder [CVSListBox::AddItem-Methode,](#additem) um den 32-Bit-Wert dem Listensteuerelement zuzuordnen. Dieser Wert kann eine anwendungsspezifische ganzzahlige Datei oder ein Zeiger auf andere Daten sein.

## <a name="cvslistboxgetitemtext"></a><a name="getitemtext"></a>CVSListBox::GetItemText

Ruft den Text eines bearbeitbaren Listensteuerelements ab.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index eines bearbeitbaren Listensteuerelements.

### <a name="return-value"></a>Rückgabewert

Ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das den Text des angegebenen Elements enthält.

### <a name="remarks"></a>Bemerkungen

## <a name="cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a>CVSListBox::GetListHwnd

Gibt das Handle an das aktuelle eingebettete Listenansichtssteuerelement zurück.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für das eingebettete Listenansichtssteuerelement.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um ein Handle in `CVSListBox` das eingebettete Listenansichtssteuerelement abzurufen, das die Klasse unterstützt.

## <a name="cvslistboxgetselitem"></a><a name="getselitem"></a>CVSListBox::GetSelItem

Ruft den nullbasierten Index des aktuell ausgewählten Elements in einem bearbeitbaren Listensteuerelement ab.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn diese Methode erfolgreich ist, wird der nullbasierte Index des aktuell ausgewählten Elements verwendet. andernfalls -1.

### <a name="remarks"></a>Bemerkungen

## <a name="cvslistboxremoveitem"></a><a name="removeitem"></a>CVSListBox::RemoveItem

Entfernt ein Element aus einem bearbeitbaren Listensteuerelement.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index eines bearbeitbaren Listensteuerelements.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das angegebene Element entfernt wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cvslistboxselectitem"></a><a name="selectitem"></a>CVSListBox::SelectItem

Wählt eine bearbeitbare Listensteuerelementzeichenfolge aus.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>Parameter

*iItem*<br/>
[in] Der nullbasierte Index eines bearbeitbaren Listensteuerelements.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode wählt das angegebene Element aus, und wenn es erforderlich ist, wird das Element in die Ansicht eingerollt.

## <a name="cvslistboxsetitemdata"></a><a name="setitemdata"></a>CVSListBox::SetItemData

Ordnet einem bearbeitbaren Listensteuerelement einen anwendungsspezifischen 32-Bit-Wert zu.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
[in] Der nullbasierte Index eines bearbeitbaren Listensteuerelements.

*dwData*<br/>
[in] Ein 32-Bit-Wert. Dieser Wert kann eine anwendungsspezifische ganzzahlige Datei oder ein Zeiger auf andere Daten sein.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
