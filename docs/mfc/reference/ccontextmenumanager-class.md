---
title: CContextMenuManager-Klasse
ms.date: 11/04/2016
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
ms.openlocfilehash: f322f40beabeb9a837dda01c95e9f950a07585d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369420"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager-Klasse

Das `CContextMenuManager` Objekt verwaltet Kontextmenüs, die auch als Kontextmenüs bezeichnet werden.

## <a name="syntax"></a>Syntax

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Erstellt ein `CContextMenuManager`-Objekt.|
|`CContextMenuManager::~CContextMenuManager`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CContextMenuManager::AddMenu](#addmenu)|Fügt ein neues Kontextmenü hinzu.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Gibt ein Handle an das Menü zurück, das der bereitgestellten Ressourcen-ID zugeordnet ist.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Gibt ein Handle an das Menü zurück, das mit dem angegebenen Menünamen übereinstimmt.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Gibt eine Liste mit Menünamen zurück.|
|[CContextMenuManager::LoadState](#loadstate)|Lädt In der Windows-Registrierung gespeicherte Kontextmenüs.|
|[CContextMenuManager::ResetState](#resetstate)|Löscht die Kontextmenüs aus dem Kontextmenü-Manager.|
|[CContextMenuManager::SaveState](#savestate)|Speichert Kontextmenüs in der Windows-Registrierung.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Steuert, `CContextMenuManager` ob das aktive Kontextmenü geschlossen wird, wenn ein neues Kontextmenü angezeigt wird.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Zeigt das angegebene Kontextmenü an.|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Zeigt das angegebene Kontextmenü an. Gibt den Index des ausgewählten Menübefehls zurück.|

## <a name="remarks"></a>Bemerkungen

`CContextMenuManager`verwaltet Kontextmenüs und stellt sicher, dass sie ein einheitliches Erscheinungsbild haben.

Sie sollten ein `CContextMenuManager` Objekt nicht manuell erstellen. Das Framework Ihrer Anwendung `CContextMenuManager` erstellt das Objekt. Sie sollten jedoch [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) aufrufen, wenn Ihre Anwendung initialisiert wird. Nachdem Sie den Kontext-Manager initialisiert haben, verwenden Sie die Methode [CWinAppEx::GetContextMenuManager,](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) um einen Zeiger auf den Kontext-Manager für Ihre Anwendung zu erhalten.

Sie können Zur Laufzeit Kontextmenüs `AddMenu`erstellen, indem Sie aufrufen. Wenn Sie das Menü anzeigen möchten, ohne `ShowPopupMenu`vorher Benutzereingaben zu erhalten, rufen Sie an. `TrackPopupMenu`wird verwendet, wenn Sie ein Menü erstellen und auf Benutzereingaben warten möchten. `TrackPopupMenu`gibt den Index des ausgewählten Befehls oder 0 zurück, wenn der Benutzer beendet wurde, ohne etwas auszuwählen.

Der `CContextMenuManager` kann auch speichern und seinen Status in die Windows-Registrierung laden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CContextMenuManager` wie einem Objekt ein Menü hinzugefügt wird und `CContextMenuManager` wie das aktive Popupmenü nicht geschlossen wird, wenn das Objekt ein neues Popupmenü anzeigt. Dieser Codeausschnitt ist Teil des [Beispiels für benutzerdefinierte Seiten](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxcontextmenumanager.h

## <a name="ccontextmenumanageraddmenu"></a><a name="addmenu"></a>CContextMenuManager::AddMenu

Fügt dem [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)ein neues Kontextmenü hinzu.

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>Parameter

*uiMenuNameResId*<br/>
[in] Eine Ressourcen-ID für eine Zeichenfolge, die den Namen für das neue Menü enthält.

*uiMenuResId*<br/>
[in] Die Menüressourcen-ID.

*lpszName*<br/>
[in] Eine Zeichenfolge, die den Namen für das neue Menü enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode erfolgreich war; 0, wenn die Methode fehlschlägt.

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt fehl, wenn *uiMenuResId* ungültig ist oder wenn `CContextMenuManager`sich bereits ein anderes Menü mit demselben Namen im befindet.

## <a name="ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager

Erstellt ein [CContextMenuManager-Objekt.](../../mfc/reference/ccontextmenumanager-class.md)

```
CContextMenuManager();
```

### <a name="remarks"></a>Bemerkungen

In den meisten Fällen sollten `CContextMenuManager` Sie keine manuell erstellen. Das Framework Ihrer Anwendung `CContextMenuManager` erstellt das Objekt. Sie sollten [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) während der Initialisierung Ihrer Anwendung aufrufen. Um einen Zeiger auf den Kontext-Manager zu erhalten, rufen Sie [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)auf.

## <a name="ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a>CContextMenuManager::GetMenuById

Gibt ein Handle an das Menü zurück, das einer bestimmten Ressourcen-ID zugeordnet ist.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parameter

*nMenuResId*<br/>
[in] Die Ressourcen-ID für das Menü.

### <a name="return-value"></a>Rückgabewert

Ein Handle zum zugeordneten Menü oder `NULL` wenn das Menü nicht gefunden wird.

## <a name="ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a>CContextMenuManager::GetMenuByName

Gibt ein Handle an ein bestimmtes Menü zurück.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
[in] Eine Zeichenfolge, die den Namen des abzurufenden Menüs enthält.

*puiOrigResID*<br/>
[out] Ein Zeiger auf ein UINT. Dieser Parameter enthält die Ressourcen-ID des angegebenen Menüs, falls gefunden.

### <a name="return-value"></a>Rückgabewert

Ein Handle für das Menü, das mit dem Namen übereinstimmt, der von *lpszName*angegeben wurde. NULL, wenn kein Menü namens *lpszName*vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode ein Menü findet, `GetMenuByName` das *mit lpszName*übereinstimmt, speichert die Menüressourcen-ID im Parameter *puiOrigResID*.

## <a name="ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a>CContextMenuManager::GetMenuNames

Gibt die Liste der Menünamen zurück, die dem [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)hinzugefügt wurden.

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parameter

*listOfNames*<br/>
[out] Ein Verweis auf einen [CStringList-Parameter.](../../mfc/reference/cstringlist-class.md) Diese Methode schreibt die Liste der Menünamen in diesen Parameter.

## <a name="ccontextmenumanagerloadstate"></a><a name="loadstate"></a>CContextMenuManager::LoadState

Lädt Informationen, die der [CContextMenuManager-Klasse](../../mfc/reference/ccontextmenumanager-class.md) zugeordnet sind, aus der Windows-Registrierung.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Eine Zeichenfolge, die den relativen Pfad eines Registrierungsschlüssels enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Parameter *lpszProfileName* ist nicht der absolute Pfad für einen Registrierungseintrag. Es handelt sich um einen relativen Pfad, der am Ende des Standardregistrierungsschlüssels für Ihre Anwendung hinzugefügt wird. Um den Standardregistrierungsschlüssel abzudateien oder festzulegen, verwenden Sie die Methoden [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) bzw. [CWinAppEx::SetRegistryBase.](../../mfc/reference/cwinappex-class.md#setregistrybase)

Verwenden Sie die Methode [CContextMenuManager::SaveState,](#savestate) um die Verknüpfungsmenüs in der Registrierung zu speichern.

## <a name="ccontextmenumanagerresetstate"></a><a name="resetstate"></a>CContextMenuManager::ResetState

Löscht alle Elemente aus den Kontextmenüs, die der [CContextMenuManager-Klasse](../../mfc/reference/ccontextmenumanager-class.md)zugeordnet sind.

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist; FALSE, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Diese Methode löscht die Popupmenüs und entfernt `CContextMenuManager`sie aus der .

## <a name="ccontextmenumanagersavestate"></a><a name="savestate"></a>CContextMenuManager::SaveState

Speichert Informationen, die der [CContextMenuManager-Klasse](../../mfc/reference/ccontextmenumanager-class.md) zugeordnet sind, in der Windows-Registrierung.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Eine Zeichenfolge, die den relativen Pfad eines Registrierungsschlüssels enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Parameter *lpszProfileName* ist nicht der absolute Pfad für einen Registrierungseintrag. Es handelt sich um einen relativen Pfad, der am Ende des Standardregistrierungsschlüssels für Ihre Anwendung hinzugefügt wird. Um den Standardregistrierungsschlüssel abzudateien oder festzulegen, verwenden Sie die Methoden [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) bzw. [CWinAppEx::SetRegistryBase.](../../mfc/reference/cwinappex-class.md#setregistrybase)

Verwenden Sie die Methode [CContextMenuManager::LoadState,](#loadstate) um die Kontextmenüs aus der Registrierung zu laden.

## <a name="ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu

Steuert, ob der [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) das aktive Popupmenü schließt, wenn ein neues Popupmenü angezeigt wird.

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parameter

*bSet*<br/>
[in] Ein boolescher Parameter, der steuert, ob das aktive Popupmenü geschlossen werden soll. Der Wert TRUE gibt an, dass das aktive Popupmenü nicht geschlossen ist. FALSE gibt an, dass das aktive Popupmenü geschlossen ist.

### <a name="remarks"></a>Bemerkungen

Standardmäßig schließt `CContextMenuManager` der das aktive Popupmenü.

## <a name="ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu

Zeigt das angegebene Kontextmenü an.

```
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bRightAlign = FALSE);

virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bAutoDestroy = TRUE,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Parameter

*uiMenuResId*<br/>
[in] Die Ressourcen-ID des Menüs, das von dieser Methode angezeigt wird.

*X*<br/>
[in] Der horizontale Versatz für das Kontextmenü in Clientkoordinaten.

*y*<br/>
[in] Der vertikale Versatz für das Kontextmenü in Clientkoordinaten

*pWndOwner*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster des Kontextmenüs.

*bOwnMessage*<br/>
[in] Ein boolescher Parameter, der angibt, wie Nachrichten weitergeleitet werden. Wenn *bOwnMessage* FALSE ist, wird standard-MFC-Routing verwendet. Andernfalls empfängt *pWndOwner* die Nachrichten.

*hmenuPopup*<br/>
[in] Das Handle des Menüs, das von dieser Methode angezeigt wird.

*bAutoDestroy*<br/>
[in] Ein boolescher Parameter, der angibt, ob das Menü automatisch zerstört wird.

*bRightAlign*<br/>
[in] Ein boolescher Parameter, der angibt, wie die Menüelemente ausgerichtet sind. Wenn *bRightAlign* TRUE ist, ist das Menü für die Lesereihenfolge von rechts nach links rechts-nach-links ausgerichtet.

### <a name="return-value"></a>Rückgabewert

Die erste Methodenüberladung gibt einen Wert ungleich Null zurück, wenn die Methode das Menü erfolgreich anzeigt. andernfalls 0. Die zweite Methodenüberladung gibt einen Zeiger auf [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) zurück, wenn das Kontextmenü korrekt angezeigt wird. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Diese Methode ähnelt der Methode [CContextMenuManager::TrackPopupMenu,](#trackpopupmenu) da beide Methoden ein Kontextmenü anzeigen. `TrackPopupMenu` Gibt jedoch den Index des ausgewählten Menübefehls zurück.

Wenn der Parameter *bAutoDestroy* FALSE ist, müssen `DestroyMenu` Sie die geerbte Methode manuell aufrufen, um Speicherressourcen freizugeben. Die Standardimplementierung `ShowPopupMenu` von verwendet nicht den Parameter *bAutoDestroy*. Sie wird für die zukünftige Verwendung oder `CContextMenuManager` für benutzerdefinierte Klassen bereitgestellt, die von der Klasse abgeleitet sind.

## <a name="ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu

Zeigt das angegebene Kontextmenü an und gibt den Index des ausgewählten Kontextmenübefehls zurück.

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Parameter

*hmenuPopup*<br/>
[in] Das Handle des Kontextmenüs, das diese Methode anzeigt.

*X*<br/>
[in] Der horizontale Versatz für das Kontextmenü in Clientkoordinaten.

*y*<br/>
[in] Der vertikale Versatz für das Kontextmenü in den Clientkoordinaten.

*pWndOwner*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster des Kontextmenüs.

*bRightAlign*<br/>
[in] Ein boolescher Parameter, der angibt, wie Menüelemente ausgerichtet sind. Wenn *bRightAlign* TRUE ist, ist das Menü für die Lesereihenfolge von rechts nach links rechts-nach-links ausgerichtet. Wenn *bRightAlign* FALSE ist, ist das Menü für die Lesereihenfolge von links nach rechts links ausgerichtet.

### <a name="return-value"></a>Rückgabewert

Die Menübefehls-ID des Befehls, den der Benutzer auswählt; 0, wenn der Benutzer das Kontextmenü schließt, ohne einen Menübefehl auszuwählen.

### <a name="remarks"></a>Bemerkungen

Diese Methode fungiert als modaler Aufruf, um ein Kontextmenü anzuzeigen. Die Anwendung fährt erst in der folgenden Zeile im Code fort, wenn der Benutzer entweder das Kontextmenü schließt oder einen Befehl auswählt. Eine alternative Methode, die Sie zum Anzeigen eines Kontextmenüs verwenden können, ist [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Diese Methode ist kein modaler Aufruf und gibt die ID des ausgewählten Befehls nicht zurück.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)
