---
title: CMFCTasksPaneTaskGroup-Klasse
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
helpviewer_keywords:
- CMFCTasksPaneTaskGroup [MFC], CMFCTasksPaneTaskGroup
- CMFCTasksPaneTaskGroup [MFC], SetACCData
- CMFCTasksPaneTaskGroup [MFC], m_bIsBottom
- CMFCTasksPaneTaskGroup [MFC], m_bIsCollapsed
- CMFCTasksPaneTaskGroup [MFC], m_bIsSpecial
- CMFCTasksPaneTaskGroup [MFC], m_lstTasks
- CMFCTasksPaneTaskGroup [MFC], m_rect
- CMFCTasksPaneTaskGroup [MFC], m_rectGroup
- CMFCTasksPaneTaskGroup [MFC], m_strName
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
ms.openlocfilehash: 4c24eba646bede462a5f3cfb85715278cfa7daee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366257"
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup-Klasse

Die `CMFCTasksPaneTaskGroup` Klasse ist eine Hilfsklasse, die vom [CMFCTasksPane-Steuerelement](../../mfc/reference/cmfctaskspane-class.md) verwendet wird. Objekte des Typs `CMFCTasksPaneTaskGroup` stellen eine *Aufgabengruppe*dar. Die Aufgabengruppe ist eine Liste von Elementen, die vom Framework in einem separaten Feld angezeigt wird, das eine Schaltfläche zum Reduzieren enthält. Das Feld kann über eine optionale Beschriftung (Gruppennamen) verfügen. Wenn eine Gruppe reduziert ist, ist die Liste der Aufgaben nicht sichtbar.

## <a name="syntax"></a>Syntax

```
class CMFCTasksPaneTaskGroup : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|Erstellt ein `CMFCTasksPaneTaskGroup`-Objekt.|
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|Bestimmt die Eingabehilfendaten für die aktuelle Aufgabengruppe.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Bestimmt, ob die Aufgabengruppe am unteren Rand des Aufgabenbereichssteuerelements ausgerichtet ist.|
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Bestimmt, ob die Aufgabengruppe reduziert ist.|
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Bestimmt, ob die Aufgabengruppe *speziell ist.* Das Framework zeigt spezielle Beschriftungen in einer anderen Farbe an.|
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Enthält die interne Liste der Vorgänge.|
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Gibt das umgrenzende Rechteck der Gruppenbeschriftung an.|
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Gibt das umgrenzende Rechteck der Gruppe an.|
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Gibt den Namen der Gruppe an.|

## <a name="remarks"></a>Bemerkungen

Die folgende Abbildung zeigt eine erweiterte Aufgabengruppe:

![Aufgabengruppe, erweitert](../../mfc/reference/media/nexttaskgrpexpand.png "Aufgabengruppe, erweitert")

Die folgende Abbildung zeigt eine zusammengebrochene Aufgabengruppe:

![Reduzierte Aufgabengruppe](../../mfc/reference/media/nexttaskgrpcollapse.png "Reduzierte Aufgabengruppe")

Die folgende Abbildung zeigt eine Aufgabengruppe ohne Beschriftung:

![Aufgabengruppe ohne Beschriftung](../../mfc/reference/media/nexttaskgrpnocapt.png "Aufgabengruppe ohne Beschriftung")

Die folgende Abbildung zeigt zwei Aufgabengruppen. Die erste Aufgabengruppe wird als `m_bIsSpecial` speziell markiert, indem das Flag auf TRUE gesetzt wird, während die zweite Aufgabengruppe nicht speziell ist. Beachten Sie, dass die Beschriftung für die erste Aufgabengruppe dunkler ist als die zweite Aufgabengruppe:

![Spezielle Aufgabengruppe](../../mfc/reference/media/nexttaskgrpspecial.png "Spezielle Aufgabengruppe")

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxTasksPane.h

## <a name="cmfctaskspanetaskgroupcmfctaskspanetaskgroup"></a><a name="cmfctaskspanetaskgroup"></a>CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup

Erstellt ein `CMFCTasksPaneTaskGroup`-Objekt.

```
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,
    BOOL bIsBottom,
    BOOL bIsSpecial=FALSE,
    BOOL bIsCollapsed=FALSE,
    CMFCTasksPanePropertyPage* pPage=NULL,
    HICON hIcon=NULL);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Gibt den Namen der Gruppe in der Gruppenbeschriftung an.

*bIsBottom*<br/>
Gibt an, ob die Gruppe am unteren Rand des Aufgabenbereichssteuerelements ausgerichtet ist.

*bIsSpecial*<br/>
Gibt an, ob die Gruppe als *speziell* und damit mit einer anderen Farbe gefüllt ist.

*bIsCollapsed*<br/>
Gibt an, ob die Gruppe reduziert ist.

*pPage*<br/>
Gibt die Eigenschaftenseite an, zu der diese Aufgabengruppe gehört.

*hIcon*<br/>
Gibt das Symbol an, das in der Gruppenbeschriftung angezeigt wird.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctaskspanetaskgroupm_bisbottom"></a><a name="m_bisbottom"></a>CMFCTasksPaneTaskGroup::m_bIsBottom

Bestimmt, ob die Aufgabengruppe am unteren Rand des Aufgabenbereichssteuerelements ausgerichtet ist.

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>Bemerkungen

Nur eine Gruppe kann am unteren Rand des Aufgabenbereichssteuerelements ausgerichtet werden. Diese Aufgabengruppe muss zuletzt hinzugefügt werden. Weitere Informationen finden Sie unter [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

## <a name="cmfctaskspanetaskgroupm_biscollapsed"></a><a name="m_biscollapsed"></a>CMFCTasksPaneTaskGroup::m_bIsCollapsed

Bestimmt, ob die Aufgabengruppe reduziert ist.

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>Bemerkungen

Sie können die Möglichkeit zum Reduzieren von Gruppen im Aufgabenbereich aktivieren oder deaktivieren, indem Sie [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse)aufrufen.

## <a name="cmfctaskspanetaskgroupm_bisspecial"></a><a name="m_bisspecial"></a>CMFCTasksPaneTaskGroup::m_bIsSpecial

Legt fest, ob die Aufgabengruppe *speziell* ist und ob die Beschriftung für eine spezielle Aufgabengruppe durch eine andere Farbe identifiziert werden soll.

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Anwendung das visuelle Design `m_bIsSpecial` von Windows XP `DrawThemeBackground` verwendet und FALSE ist, ruft das Framework mit dem EBP_NORMALGROUPBACKGROUND-Flag auf. Wenn `m_bIsSpecial` TRUE ist, `DrawThemeBackground` ruft das Framework mit dem EBP_SPECIALGROUPBACKGROUND-Flag auf.

## <a name="cmfctaskspanetaskgroupm_lsttasks"></a><a name="m_lsttasks"></a>CMFCTasksPaneTaskGroup::m_lstTasks

Enthält die interne Liste der Vorgänge.

```
CObList m_lstTasks;
```

### <a name="remarks"></a>Bemerkungen

Um diese Liste zu füllen, rufen Sie [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask)auf.

## <a name="cmfctaskspanetaskgroupm_rect"></a><a name="m_rect"></a>CMFCTasksPaneTaskGroup::m_rect

Gibt das umgrenzende Rechteck der Gruppenbeschriftung an.

```
CRect m_rect;
```

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird automatisch vom Framework berechnet.

## <a name="cmfctaskspanetaskgroupm_rectgroup"></a><a name="m_rectgroup"></a>CMFCTasksPaneTaskGroup::m_rectGroup

Gibt das umgrenzende Rechteck der Gruppe an.

```
CRect m_rectGroup;
```

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird automatisch vom Framework berechnet.

## <a name="cmfctaskspanetaskgroupm_strname"></a><a name="m_strname"></a>CMFCTasksPaneTaskGroup::m_strName

Gibt den Namen der Gruppe an.

```
CString m_strName;
```

### <a name="remarks"></a>Bemerkungen

Wenn dieser Wert leer ist, wird die Gruppenbeschriftung nicht angezeigt, und die Gruppe kann nicht reduziert werden.

## <a name="cmfctaskspanetaskgroupsetaccdata"></a><a name="setaccdata"></a>CMFCTasksPaneTaskGroup::SetACCData

Bestimmt die Eingabehilfendaten für die aktuelle Aufgabengruppe.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parameter

*pParent*<br/>
[in] Stellt das übergeordnete Fenster der aktuellen Aufgabengruppe dar.

*Daten*<br/>
[out] Ein Objekt `CAccessibilityData` des Typs, das mit den Eingabehilfendaten der aktuellen Aufgabengruppe aufgefüllt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der *Datenparameter* erfolgreich mit den Eingabehilfendaten der aktuellen Aufgabengruppe aufgefüllt wurde; andernfalls FALSE.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTasksPane-Klasse](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFCTasksPaneTask-Klasse](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)
