---
title: CMFCTasksPaneTask-Klasse
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTask::m_bAutoDestroyWindow
- AFXTASKSPANE/CMFCTasksPaneTask::m_bIsBold
- AFXTASKSPANE/CMFCTasksPaneTask::m_dwUserData
- AFXTASKSPANE/CMFCTasksPaneTask::m_hwndTask
- AFXTASKSPANE/CMFCTasksPaneTask::m_nIcon
- AFXTASKSPANE/CMFCTasksPaneTask::m_nWindowHeight
- AFXTASKSPANE/CMFCTasksPaneTask::m_pGroup
- AFXTASKSPANE/CMFCTasksPaneTask::m_rect
- AFXTASKSPANE/CMFCTasksPaneTask::m_strName
- AFXTASKSPANE/CMFCTasksPaneTask::m_uiCommandID
helpviewer_keywords:
- CMFCTasksPaneTask [MFC], CMFCTasksPaneTask
- CMFCTasksPaneTask [MFC], SetACCData
- CMFCTasksPaneTask [MFC], m_bAutoDestroyWindow
- CMFCTasksPaneTask [MFC], m_bIsBold
- CMFCTasksPaneTask [MFC], m_dwUserData
- CMFCTasksPaneTask [MFC], m_hwndTask
- CMFCTasksPaneTask [MFC], m_nIcon
- CMFCTasksPaneTask [MFC], m_nWindowHeight
- CMFCTasksPaneTask [MFC], m_pGroup
- CMFCTasksPaneTask [MFC], m_rect
- CMFCTasksPaneTask [MFC], m_strName
- CMFCTasksPaneTask [MFC], m_uiCommandID
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
ms.openlocfilehash: 49fccdf161da7deb1fd88a12a107df40bafdae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375867"
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask-Klasse

Die `CMFCTasksPaneTask` Klasse ist eine Hilfsklasse, die Aufgaben für das Aufgabenbereichssteuerelement ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)) darstellt. Das Aufgabenobjekt stellt ein Element in der Aufgabengruppe ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)) dar. Jede Aufgabe kann über einen Befehl verfügen, den das Framework ausführt, wenn ein Benutzer auf die Aufgabe klickt, und über ein Symbol, das auf der linken Seite des Aufgabennamens angezeigt wird.

## <a name="syntax"></a>Syntax

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|Erstellt und initialisiert ein `CMFCTasksPaneTask`-Objekt.|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Bestimmt die Eingabehilfendaten für die aktuelle Aufgabe.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|Bestimmt, ob das Aufgabenfenster automatisch zerstört wird.|
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|Bestimmt, ob das Framework eine Aufgabenbeschriftung in fett formatiertem Text zeichnet.|
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|Enthält benutzerdefinierte Daten, die das Framework der Aufgabe zuordnet. Wird auf Null gesetzt, wenn der Task keine daten zugeordnet ist.|
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|Ein Handle für das Aufgabenfenster.|
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|Der Index in der Bildliste des Bildes, das das Framework neben der Aufgabe anzeigt.|
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|Die Höhe des Aufgabenfensters. Wenn der Vorgang kein Vorgangsfenster hat, ist dieser Wert Null.|
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|Ein Zeiger auf `CMFCTasksPaneTaskGroup` die Aufgabe, zu der diese Aufgabe gehört.|
|[CMFCTasksPaneTask::m_rect](#m_rect)|Gibt das umgrenzende Rechteck der Aufgabe an.|
|[CMFCTasksPaneTask::m_strName](#m_strname)|Der Name des Tasks.|
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|Gibt die Befehls-ID des Befehls an, den das Framework ausführt, wenn der Benutzer auf die Aufgabe klickt. Wenn dieser Wert keine gültige Befehls-ID ist, wird die Aufgabe als einfache Bezeichnung behandelt.|

## <a name="remarks"></a>Bemerkungen

Die folgende Abbildung zeigt eine Aufgabengruppe, die drei Aufgaben enthält:

![Aufgabengruppe, erweitert](../../mfc/reference/media/nexttaskgrpexpand.png "Aufgabengruppe, erweitert")

> [!NOTE]
> Wenn eine Aufgabe nicht über eine gültige Befehls-ID verfügt, wird sie als einfache Bezeichnung behandelt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxTasksPane.h

## <a name="cmfctaskspanetaskcmfctaskspanetask"></a><a name="cmfctaskspanetask"></a>CMFCTasksPaneTask::CMFCTasksPaneTask

Erstellt und initialisiert ein `CMFCTasksPaneTask`-Objekt.

```
CMFCTasksPaneTask(
    CMFCTasksPaneTaskGroup* pGroup,
    LPCTSTR lpszName,
    int nIcon,
    UINT uiCommandID,
    DWORD dwUserData = 0,
    HWND hwndTask = NULL,
    BOOL bAutoDestroyWindow = FALSE,
    int nWindowHeight = 0);
```

### <a name="parameters"></a>Parameter

*pGruppe*<br/>
Gibt die [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) an, zu der die Aufgabe gehört.

*lpszName*<br/>
Gibt den Namen des Tasks an.

*nIcon*<br/>
Gibt den Index des Bildes der Aufgabe in der Bildliste an.

*uiCommandID*<br/>
Gibt die Befehls-ID des Befehls an, der ausgeführt wird, wenn auf die Aufgabe geklickt wird.

*dwUserData*<br/>
Benutzerdefinierte Daten.

*hwndTask*<br/>
Gibt das Handle für das Aufgabenfenster an.

*bAutoDestroyWindow*<br/>
Wenn TRUE, wird das Aufgabenfenster automatisch zerstört.

*nWindowHeight*<br/>
Gibt die Höhe des Aufgabenfensters an.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctaskspanetaskm_bautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFCTasksPaneTask::m_bAutoDestroyWindow

Bestimmt, ob das Aufgabenfenster automatisch zerstört wird.

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie TRUE fest, um anzugeben, dass das Aufgabenfenster ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) automatisch zerstört werden soll. andernfalls FALSE.

## <a name="cmfctaskspanetaskm_bisbold"></a><a name="m_bisbold"></a>CMFCTasksPaneTask::m_bIsBold

Bestimmt, ob eine Aufgabenbeschriftung in fett formatiertem Text gezeichnet wird.

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Member auf TRUE fest, um fett formatierten Text für die Aufgabenbeschriftung anzuzeigen.

## <a name="cmfctaskspanetaskm_dwuserdata"></a><a name="m_dwuserdata"></a>CMFCTasksPaneTask::m_dwUserData

Enthält benutzerdefinierte Daten, die der Aufgabe zugeordnet sind. Legen Sie null fest, wenn der Aufgabe keine Daten zugeordnet sind.

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctaskspanetaskm_hwndtask"></a><a name="m_hwndtask"></a>CMFCTasksPaneTask::m_hwndTask

Ein Handle für das Aufgabenfenster.

```
HWND m_hwndTask;
```

### <a name="remarks"></a>Bemerkungen

Um ein Aufgabenfenster hinzuzufügen, rufen Sie [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow)auf.

## <a name="cmfctaskspanetaskm_nicon"></a><a name="m_nicon"></a>CMFCTasksPaneTask::m_nIcon

Die Indexposition in einer Bildliste, die ein Bild identifiziert, das neben der angegebenen Aufgabe angezeigt wird.

```
int m_nIcon;
```

### <a name="remarks"></a>Bemerkungen

Die Bildliste wird von [CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist)festgelegt.

Legen `m_nIcon` Sie -1 fest, wenn Sie die Aufgabe ohne Bild anzeigen möchten.

## <a name="cmfctaskspanetaskm_nwindowheight"></a><a name="m_nwindowheight"></a>CMFCTasksPaneTask::m_nWindowHeight

Die Höhe des Aufgabenfensters. Wenn der Vorgang kein Vorgangsfenster hat, ist dieser Wert Null.

```
int m_nWindowHeight;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctaskspanetaskm_pgroup"></a><a name="m_pgroup"></a>CMFCTasksPaneTask::m_pGroup

Zeiger auf die [CMFCTasksPaneTaskGroup,](../../mfc/reference/cmfctaskspanetaskgroup-class.md) zu der diese Aufgabe gehört.

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>Bemerkungen

Jede Aufgabe muss über eine übergeordnete Gruppe verfügen. Sie fügen Einem Aufgabenbereich Gruppen hinzu, indem Sie [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)aufrufen.

## <a name="cmfctaskspanetaskm_rect"></a><a name="m_rect"></a>CMFCTasksPaneTask::m_rect

Gibt das umgrenzende Rechteck der Aufgabe an.

```
CRect m_rect;
```

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird vom Framework berechnet, wenn der Vorgang gezeichnet wird.

## <a name="cmfctaskspanetaskm_strname"></a><a name="m_strname"></a>CMFCTasksPaneTask::m_strName

Der Name des Tasks.

```
CString m_strName;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctaskspanetaskm_uicommandid"></a><a name="m_uicommandid"></a>CMFCTasksPaneTask::m_uiCommandID

Gibt die Befehls-ID des Befehls an, der ausgeführt wird, wenn der Benutzer auf die Aufgabe klickt. Wenn dieser Wert keine gültige Befehls-ID ist, wird die Aufgabe als einfache Bezeichnung behandelt.

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctaskspanetasksetaccdata"></a><a name="setaccdata"></a>CMFCTasksPaneTask::SetACCData

Bestimmt die Eingabehilfendaten für die aktuelle Aufgabe.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parameter

*pParent*<br/>
[in] Stellt das übergeordnete Fenster der aktuellen Aufgabe dar.

*Daten*<br/>
[out] Ein Objekt `CAccessibilityData` des Typs, das mit den Eingabehilfendaten der aktuellen Aufgabe aufgefüllt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der *Datenparameter* erfolgreich mit den Eingabehilfendaten der aktuellen Aufgabe aufgefüllt wurde; andernfalls FALSE.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)
