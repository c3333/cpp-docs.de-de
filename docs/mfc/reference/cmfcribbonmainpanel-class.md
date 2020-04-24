---
title: CMFCRibbonMainPanel-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
ms.openlocfilehash: 0fd1cd2fec31f9da0c2bec36d08586780f4f95c3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753568"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel-Klasse

Implementiert ein Menübandbedienfeld, das angezeigt wird, wenn Sie auf [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)klicken.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Der Standardkonstruktor.|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonMainPanel::Hinzufügen](#add)|Fügt dem linken Bereich des Anwendungsschaltflächenbereichs ein Multifunktionsleistenelement hinzu. (Überschreibt [CMFCRibbonPanel::Hinzufügen](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Fügt dem Listenmenü der letzten Dateien eine Textzeichenfolge hinzu.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Fügt dem unteren Bereich des Menübandbedienfelds ein Multifunktionsleistenelement hinzu.|
|[CMFCRibbonMainPanel::Addtoright](#addtoright)|Fügt dem rechten Bereich des Anwendungsschaltflächenbereichs ein Multifunktionsleistenelement hinzu.|
|`CMFCRibbonMainPanel::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Gibt ein Rechteck zurück, das den Bereich des Menüband-Hauptfensters darstellt.|
|`CMFCRibbonMainPanel::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

Das Framework `CMFCRibbonMainPanel` zeigt die anzeige, wenn Sie das Anwendungsfeld öffnen. Es enthält drei Bereiche:

- Der linke Bereich enthält Befehle, die Dateien zugeordnet sind, z. B. **Öffnen**, **Speichern**, **Drucken**und **Schließen**. Um diesem Bereich einen Befehl hinzuzufügen, rufen Sie [CMFCRibbonMainPanel::Add](#add)auf.

- Der rechte Bereich enthält Optionen, die den Befehl ändern, auf den Sie im linken Bereich klicken. Wenn Sie beispielsweise im linken Bereich auf **Speichern unter** klicken, können im rechten Bereich verfügbare Dateitypen angezeigt werden. Um diesem Bereich ein Element hinzuzufügen, rufen Sie [CMFCRibbonMainPanel::AddToRight](#addtoright)auf.

- Der untere Bereich enthält Schaltflächen, mit denen Sie die Einstellungen der Anwendung ändern und das Programm beenden können. Um diesem Bereich ein Element hinzuzufügen, rufen Sie [CMFCRibbonMainPanel::AddToBottom](#addtobottom)auf.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxRibbonMainPanel.h

## <a name="cmfcribbonmainpaneladd"></a><a name="add"></a>CMFCRibbonMainPanel::Hinzufügen

Fügt dem linken Bereich des Anwendungsschaltflächenbereichs ein Multifunktionsleistenelement hinzu.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Parameter

*pElem*<br/>
[in, out] Ein Zeiger auf das Menübandelement, das dem Hauptfenster hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Fügt dem Bedienfeld ein Multifunktionsleistenelement hinzu. Elemente, die mit dieser Methode hinzugefügt werden, befinden sich in der linken Spalte des Hauptfensters.

## <a name="cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList

Fügt dem Listenmenü der letzten Dateien eine Textzeichenfolge hinzu.

```cpp
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Parameter

*lpszLabel*<br/>
Gibt die Zeichenfolge an, die der Liste der letzten Dateien hinzugefügt werden soll.

*nWidth*<br/>
Gibt die Breite des Listenbereichs der letzten Dateien in Pixel an.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom

Fügt dem unteren Bereich des Menübandbedienfelds ein Multifunktionsleistenelement hinzu.

```cpp
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Parameter

*pElem*<br/>
[in, out] Ein Zeiger auf das Menübandelement, das am unteren Rand des Hauptfensters hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a>CMFCRibbonMainPanel::Addtoright

Fügt dem rechten Bereich des Anwendungsschaltflächenbereichs ein Multifunktionsleistenelement hinzu.

```cpp
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Parameter

*pElem*<br/>
Ein Zeiger auf ein Menübandelement, das auf der rechten Seite des Hauptfensters hinzugefügt werden soll.

*nWidth*<br/>
Gibt die Breite des rechten Bedienfelds in Pixel an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um dem rechten Bereich ein Multifunktionsleistenelement hinzuzufügen. Im rechten Bereich wird in der Regel die Liste der letzten Dateien angezeigt, Sie können jedoch hier ein beliebiges weiteres Multifunktionsleistenelement hinzufügen.

## <a name="cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame

Gibt ein Rechteck zurück, das den Bereich des Menüband-Hauptfensters darstellt.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Rechteck, das den Bereich des Menüband-Hauptfensters darstellt.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel-Klasse](../../mfc/reference/cmfcribbonpanel-class.md)
