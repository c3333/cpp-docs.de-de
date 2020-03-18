---
title: Ccontextmenumanager-Klasse
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
ms.openlocfilehash: c8a51a33c69b09d0ecd61520b5f1c9ff18c290a0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425982"
---
# <a name="ccontextmenumanager-class"></a>Ccontextmenumanager-Klasse

Das `CContextMenuManager` Objekt verwaltet Kontextmenüs, auch als Kontextmenüs bezeichnet.

## <a name="syntax"></a>Syntax

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Ccontextmenumanager:: ccontextmenumanager](#ccontextmenumanager)|Erstellt ein `CContextMenuManager`-Objekt.|
|`CContextMenuManager::~CContextMenuManager`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[Ccontextmenumanager:: AddMenu](#addmenu)|Fügt ein neues Kontextmenü hinzu.|
|[Ccontextmenumanager:: getmenubyid](#getmenubyid)|Gibt ein Handle für das Menü zurück, das der angegebenen Ressourcen-ID zugeordnet ist.|
|[Ccontextmenumanager:: getmenubyname](#getmenubyname)|Gibt ein Handle für das Menü zurück, das mit dem angegebenen Menünamen übereinstimmt.|
|[Ccontextmenumanager:: getmenunames](#getmenunames)|Gibt eine Liste von Menü Namen zurück.|
|[Ccontextmenumanager:: LoadState](#loadstate)|Lädt Kontextmenüs, die in der Windows-Registrierung gespeichert sind.|
|[Ccontextmenumanager:: ResetState](#resetstate)|Löscht die Kontextmenüs aus dem Kontextmenü-Manager.|
|[Ccontextmenumanager:: SaveState](#savestate)|Speichert Kontextmenüs in der Windows-Registrierung.|
|[Ccontextmenumanager:: setdontcloseactivemenu](#setdontcloseactivemenu)|Steuert, ob das `CContextMenuManager` das aktive Kontextmenü schließt, wenn ein neues Kontextmenü angezeigt wird.|
|[Ccontextmenumanager:: showPopupMenu](#showpopupmenu)|Zeigt das angegebene Kontextmenü an.|
|[Ccontextmenumanager:: TrackPopupMenu](#trackpopupmenu)|Zeigt das angegebene Kontextmenü an. Gibt den Index des ausgewählten Menübefehls zurück.|

## <a name="remarks"></a>Hinweise

`CContextMenuManager` verwaltet Kontextmenüs und stellt sicher, dass Sie über ein konsistentes Erscheinungsbild verfügen.

Sie sollten kein `CContextMenuManager` Objekt manuell erstellen. Das Framework der Anwendung erstellt das `CContextMenuManager` Objekt. Sie sollten jedoch [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) aufrufen, wenn Ihre Anwendung initialisiert wird. Verwenden Sie nach dem Initialisieren des Kontext-Managers die Methode [CWinAppEx:: getcontextmenumanager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) , um einen Zeiger auf den Kontext-Manager für Ihre Anwendung zu erhalten.

Sie können zur Laufzeit Kontextmenüs erstellen, indem Sie `AddMenu`aufrufen. Wenn Sie das Menü anzeigen möchten, ohne zuerst Benutzereingaben zu empfangen, wenden Sie `ShowPopupMenu`an. `TrackPopupMenu` wird verwendet, wenn Sie ein Menü Erstellen und auf Benutzereingaben warten möchten. `TrackPopupMenu` gibt den Index des ausgewählten Befehls oder "0" zurück, wenn der Benutzer beendet wurde, ohne etwas auszuwählen.

Der `CContextMenuManager` kann auch seinen Status speichern und in die Windows-Registrierung laden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie einem `CContextMenuManager` Objekt ein Menü hinzugefügt wird und wie das aktive Popup Menü nicht geschlossen wird, wenn das `CContextMenuManager`-Objekt ein neues Popup Menü anzeigt. Dieser Code Ausschnitt ist Teil des Beispiels für [benutzerdefinierte Seiten](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxcontextmenumanager. h

##  <a name="addmenu"></a>Ccontextmenumanager:: AddMenu

Fügt dem [ccontextmenumanager](../../mfc/reference/ccontextmenumanager-class.md)ein neues Kontextmenü hinzu.

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>Parameter

*uimerunameresid*<br/>
in Eine Ressourcen-ID für eine Zeichenfolge, die den Namen für das neue Menü enthält.

*uimaufuresid*<br/>
in Die Menü Ressourcen-ID.

*lpszname*<br/>
in Eine Zeichenfolge, die den Namen für das neue Menü enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Methode erfolgreich war. 0, wenn die Methode fehlschlägt.

### <a name="remarks"></a>Hinweise

Diese Methode schlägt fehl, wenn *uimenuresid* ungültig ist oder ein anderes Menü mit dem gleichen Namen bereits im `CContextMenuManager`vorhanden ist.

##  <a name="ccontextmenumanager"></a>Ccontextmenumanager:: ccontextmenumanager

Erstellt ein [ccontextmenumanager](../../mfc/reference/ccontextmenumanager-class.md) -Objekt.

```
CContextMenuManager();
```

### <a name="remarks"></a>Hinweise

In den meisten Fällen sollten Sie keine `CContextMenuManager` manuell erstellen. Das Framework der Anwendung erstellt das `CContextMenuManager` Objekt. Sie sollten [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) während der Initialisierung der Anwendung aufrufen. Rufen Sie [CWinAppEx:: getcontextmenumanager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)auf, um einen Zeiger auf den Kontext-Manager zu erhalten.

##  <a name="getmenubyid"></a>Ccontextmenumanager:: getmenubyid

Gibt ein Handle für das Menü zurück, das einer bestimmten Ressourcen-ID zugeordnet ist.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parameter

*nmenuresid*<br/>
in Die Ressourcen-ID für das Menü.

### <a name="return-value"></a>Rückgabewert

Ein Handle für das zugeordnete Menü oder `NULL`, wenn das Menü nicht gefunden wurde.

##  <a name="getmenubyname"></a>Ccontextmenumanager:: getmenubyname

Gibt ein Handle für ein bestimmtes Menü zurück.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
in Eine Zeichenfolge, die den Namen des abzurufenden Menüs enthält.

*puiorigresid*<br/>
vorgenommen Ein Zeiger auf einen uint. Dieser Parameter enthält die Ressourcen-ID des angegebenen Menüs, sofern gefunden.

### <a name="return-value"></a>Rückgabewert

Ein Handle für das Menü, das mit dem Namen übereinstimmt, der von *lpszname*angegeben wurde. NULL, wenn kein Menü namens *lpszname*vorhanden ist.

### <a name="remarks"></a>Hinweise

Wenn diese Methode ein Menü findet, das *lpszname*entspricht, speichert `GetMenuByName` die Menü Ressourcen-ID im Parameter *puiorigresid*.

##  <a name="getmenunames"></a>Ccontextmenumanager:: getmenunames

Gibt die Liste der dem [ccontextmenumanager](../../mfc/reference/ccontextmenumanager-class.md)hinzugefügten Menü Namen zurück.

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parameter

*listobnames*<br/>
vorgenommen Ein Verweis auf einen [CStringList](../../mfc/reference/cstringlist-class.md) -Parameter. Diese Methode schreibt die Liste der Menü Namen in diesen Parameter.

##  <a name="loadstate"></a>Ccontextmenumanager:: LoadState

Lädt Informationen, die der [ccontextmenumanager-Klasse](../../mfc/reference/ccontextmenumanager-class.md) zugeordnet sind, aus der Windows-Registrierung.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszprofilename*<br/>
in Eine Zeichenfolge, die den relativen Pfad eines Registrierungsschlüssels enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Methode erfolgreich ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

Der *lpszprofilename* -Parameter ist nicht der absolute Pfad für einen Registrierungs Eintrag. Dabei handelt es sich um einen relativen Pfad, der am Ende des Standard Registrierungsschlüssels für Ihre Anwendung hinzugefügt wird. Um den Standard Registrierungsschlüssel zu erhalten oder festzulegen, verwenden Sie die Methoden [CWinAppEx:: getregistrybase](../../mfc/reference/cwinappex-class.md#getregistrybase) bzw. [CWinAppEx:: setregistrybase](../../mfc/reference/cwinappex-class.md#setregistrybase) .

Verwenden Sie die-Methode [ccontextmenumanager:: SaveState](#savestate) , um die Kontextmenüs in der Registrierung zu speichern.

##  <a name="resetstate"></a>Ccontextmenumanager:: ResetState

Löscht alle Elemente aus den Kontextmenüs, die der [ccontextmenumanager-Klasse](../../mfc/reference/ccontextmenumanager-class.md)zugeordnet sind.

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist. FALSE, wenn ein Fehler auftritt.

### <a name="remarks"></a>Hinweise

Diese Methode löscht die Popup Menüs und entfernt Sie aus der `CContextMenuManager`.

##  <a name="savestate"></a>Ccontextmenumanager:: SaveState

Speichert die der [ccontextmenumanager-Klasse](../../mfc/reference/ccontextmenumanager-class.md) zugeordneten Informationen in der Windows-Registrierung.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszprofilename*<br/>
in Eine Zeichenfolge, die den relativen Pfad eines Registrierungsschlüssels enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Methode erfolgreich ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

Der *lpszprofilename* -Parameter ist nicht der absolute Pfad für einen Registrierungs Eintrag. Dabei handelt es sich um einen relativen Pfad, der am Ende des Standard Registrierungsschlüssels für Ihre Anwendung hinzugefügt wird. Um den Standard Registrierungsschlüssel zu erhalten oder festzulegen, verwenden Sie die Methoden [CWinAppEx:: getregistrybase](../../mfc/reference/cwinappex-class.md#getregistrybase) bzw. [CWinAppEx:: setregistrybase](../../mfc/reference/cwinappex-class.md#setregistrybase) .

Verwenden Sie die-Methode [ccontextmenumanager:: LoadState](#loadstate) , um die Kontextmenüs aus der Registrierung zu laden.

##  <a name="setdontcloseactivemenu"></a>Ccontextmenumanager:: setdontcloseactivemenu

Steuert, ob [ccontextmenumanager](../../mfc/reference/ccontextmenumanager-class.md) das aktive Popup Menü beim Anzeigen eines neuen Popup Menüs schließt.

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parameter

*BSET*<br/>
in Ein boolescher Parameter, der steuert, ob das aktive Popup Menü geschlossen werden soll. Der Wert true gibt an, dass das aktive Popup Menü nicht geschlossen ist. FALSE gibt an, dass das aktive Popup Menü geschlossen wird.

### <a name="remarks"></a>Hinweise

Standardmäßig schließt das `CContextMenuManager` das aktive Popupmenü.

##  <a name="showpopupmenu"></a>Ccontextmenumanager:: showPopupMenu

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

*uimaufuresid*<br/>
in Die Ressourcen-ID des Menüs, das von dieser Methode angezeigt wird.

*x*<br/>
in Der horizontale Offset für das Kontextmenü in Client Koordinaten.

*y*<br/>
in Der vertikale Offset für das Kontextmenü in Client Koordinaten.

*pwndowner*<br/>
in Ein Zeiger auf das übergeordnete Fenster des Kontextmenüs.

*bownmessage*<br/>
in Ein boolescher Parameter, der angibt, wie Nachrichten weitergeleitet werden. Wenn *bownmessage* den Wert false hat, wird das MFC-Standard Routing verwendet. Andernfalls empfängt *pwndowner* die Nachrichten.

*hmenupopup*<br/>
in Das Handle des Menüs, das von dieser Methode angezeigt wird.

*Bauto zerstören*<br/>
in Ein boolescher Parameter, der angibt, ob das Menü automatisch gelöscht wird.

*brightalign*<br/>
in Ein boolescher Parameter, der angibt, wie die Menü Elemente ausgerichtet werden. Wenn *brightalign* den Wert true hat, wird das Menü rechts-nach-Links-Lesefolge rechtsbündig ausgerichtet.

### <a name="return-value"></a>Rückgabewert

Die erste Methoden Überladung gibt einen Wert ungleich 0 zurück, wenn die-Methode das Menü erfolgreich anzeigt. andernfalls 0. Die zweite Methoden Überladung gibt einen Zeiger auf [cmfcpopupmenu](../../mfc/reference/cmfcpopupmenu-class.md) zurück, wenn das Kontextmenü ordnungsgemäß angezeigt wird. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Diese Methode ähnelt der-Methode [ccontextmenumanager:: TrackPopupMenu](#trackpopupmenu) darin, dass beide Methoden ein Kontextmenü anzeigen. `TrackPopupMenu` gibt jedoch den Index des ausgewählten Menübefehls zurück.

Wenn der Parameter *baudedestroy* den Wert false hat, müssen Sie die geerbte `DestroyMenu` Methode manuell aufrufen, um Speicherressourcen freizugeben. Die Standard Implementierung von `ShowPopupMenu` verwendet nicht den Parameter " *bauy}* ". Sie wird für die zukünftige Verwendung oder für benutzerdefinierte Klassen bereitgestellt, die von der `CContextMenuManager`-Klasse abgeleitet werden.

##  <a name="trackpopupmenu"></a>Ccontextmenumanager:: TrackPopupMenu

Zeigt das angegebene Kontextmenü an und gibt den Index des ausgewählten Kontextmenü Befehls zurück.

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Parameter

*hmenupopup*<br/>
in Das Handle des Kontextmenüs, das von dieser Methode angezeigt wird.

*x*<br/>
in Der horizontale Offset für das Kontextmenü in Client Koordinaten.

*y*<br/>
in Der vertikale Offset für das Kontextmenü in Client Koordinaten.

*pwndowner*<br/>
in Ein Zeiger auf das übergeordnete Fenster des Kontextmenüs.

*brightalign*<br/>
in Ein boolescher Parameter, der angibt, wie Menü Elemente ausgerichtet werden. Wenn *brightalign* den Wert true hat, wird das Menü rechts-nach-Links-Lesefolge rechtsbündig ausgerichtet. Wenn *brightalign* den Wert false hat, wird das Menü für die Lesefolge von links nach rechts ausgerichtet.

### <a name="return-value"></a>Rückgabewert

Die Menübefehls-ID des Befehls, den der Benutzer auswählt. 0, wenn der Benutzer das Kontextmenü schließt, ohne einen Menübefehl auszuwählen.

### <a name="remarks"></a>Hinweise

Diese Methode fungiert als modaler-Befehl, um ein Kontextmenü anzuzeigen. Die Anwendung wird nicht mit der folgenden Zeile im Code fortgesetzt, bis der Benutzer das Kontextmenü schließt oder einen Befehl auswählt. Eine alternative Methode, mit der Sie ein Kontextmenü anzeigen können, ist [ccontextmenumanager:: showPopupMenu](#showpopupmenu). Bei dieser Methode handelt es sich nicht um einen modalen-Befehl, und die ID des ausgewählten Befehls wird nicht zurückgegeben.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)
