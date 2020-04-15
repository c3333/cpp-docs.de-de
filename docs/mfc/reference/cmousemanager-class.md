---
title: CMouseManager-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
ms.openlocfilehash: d05a2e186f001a69310e99cec013193a4d1bff3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319724"
---
# <a name="cmousemanager-class"></a>CMouseManager-Klasse

Ermöglicht es einem Benutzer, einem bestimmten [CView-Objekt](../../mfc/reference/cview-class.md) verschiedene Befehle zuzuordnen, wenn der Benutzer in dieser Ansicht doppelklickt.

## <a name="syntax"></a>Syntax

```
class CMouseManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|Fügt `CView` dem Dialogfeld **Anpassung** ein Objekt hinzu. Im Dialogfeld **Anpassung** kann der Benutzer einen Doppelklick mit einem Befehl für jede der aufgelisteten Ansichten zuordnen.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Gibt den Befehl zurück, der ausgeführt wird, wenn der Benutzer in der bereitgestellten Ansicht doppelklickt.|
|[CMouseManager::GetViewIconId](#getviewiconid)|Gibt das Symbol zurück, das der bereitgestellten Ansichts-ID zugeordnet ist.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Gibt die Ansichts-ID zurück, die dem angegebenen Ansichtsnamen zugeordnet ist.|
|[CMouseManager::GetViewNames](#getviewnames)|Ruft eine Liste aller hinzugefügten Ansichtsnamen ab.|
|[CMouseManager::LoadState](#loadstate)|Lädt `CMouseManager` den Status aus der Windows-Registrierung.|
|[CMouseManager::SaveState](#savestate)|Schreibt `CMouseManager` den Status in die Windows-Registrierung.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Verknüpft den bereitgestellten Befehl und die bereitgestellte Ansicht.|

## <a name="remarks"></a>Bemerkungen

Die `CMouseManager` Klasse verwaltet `CView` eine Auflistung von Objekten. Jede Ansicht wird durch einen Namen und eine ID gekennzeichnet. Diese Ansichten werden im Dialogfeld **Anpassung** angezeigt. Der Benutzer kann den Befehl, der einer Ansicht zugeordnet ist, über das Dialogfeld **Anpassung** ändern. Der zugeordnete Befehl wird ausgeführt, wenn der Benutzer in dieser Ansicht doppelklickt. Um dies aus Dercodierungsperspektive zu unterstützen, müssen Sie die WM_LBUTTONDBLCLK-Nachricht verarbeiten und die `CView` [CWinAppEx::OnViewDoubleClick-Funktion](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) im Code für dieses Objekt aufrufen.

Sie sollten ein `CMouseManager` Objekt nicht manuell erstellen. Sie wird durch das Framework Ihrer Anwendung erstellt. Es wird auch automatisch zerstört, wenn der Benutzer die Anwendung verlässt. Um einen Zeiger auf den Maus-Manager für Ihre Anwendung zu erhalten, rufen Sie [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager)an.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmousemanager.h

## <a name="cmousemanageraddview"></a><a name="addview"></a>CMouseManager::AddView

Registriert ein [CView-Objekt](../../mfc/reference/cview-class.md) bei der [CMouseManager-Klasse,](../../mfc/reference/cmousemanager-class.md) um das benutzerdefinierte Mausverhalten zu unterstützen.

```
BOOL AddView(
    int iViewId,
    UINT uiViewNameResId,
    UINT uiIconId = 0);

BOOL AddView(
    int iId,
    LPCTSTR lpszViewName,
    UINT uiIconId = 0);
```

### <a name="parameters"></a>Parameter

*iViewId*<br/>
[in] Eine Ansichts-ID.

*uiViewNameResId*<br/>
[in] Eine Ressourcenzeichenfolgen-ID, die auf den Ansichtsnamen verweist.

*uiIconId*<br/>
[in] Eine Ansichtssymbol-ID.

*Iid*<br/>
[in] Eine Ansichts-ID.

*lpszViewName*<br/>
[in] Ein Ansichtsname.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Um das benutzerdefinierte Mausverhalten zu unterstützen, `CMouseManager` muss eine Ansicht beim Objekt registriert werden. Jedes von der `CView` Klasse abgeleitete Objekt kann beim Maus-Manager registriert werden. Die Zeichenfolge und das Symbol, die einer Ansicht zugeordnet sind, werden auf der Registerkarte **Maus** im Dialogfeld **Anpassen** angezeigt.

Es liegt in der Verantwortung des Programmierers, Ansichts-IDs wie *iViewId* und *iId*zu erstellen und zu verwalten.

Weitere Informationen zum Bereitstellen des benutzerdefinierten Mausverhaltens finden Sie unter [Tastatur- und Mausanpassung](../../mfc/keyboard-and-mouse-customization.md).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie `CMouseManager` ein Zeiger `CWinAppEx::GetMouseManager` auf `AddView` ein Objekt `CMouseManager` mithilfe der Methode und der Methode in der Klasse abgerufen wird. Dieser Codeausschnitt ist Teil des [Beispiels für](../../overview/visual-cpp-samples.md)die State Collection .

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

## <a name="cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand

Gibt den Befehl zurück, der ausgeführt wird, wenn der Benutzer in der bereitgestellten Ansicht doppelklickt.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die Ansichts-ID.

### <a name="return-value"></a>Rückgabewert

Der Befehlsbezeichner, wenn die Ansicht einem Befehl zugeordnet ist; andernfalls 0.

## <a name="cmousemanagergetviewiconid"></a><a name="getviewiconid"></a>CMouseManager::GetViewIconId

Ruft das Symbol ab, das einer Ansichts-ID zugeordnet ist.

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>Parameter

*iViewId*<br/>
[in] Die Ansichts-ID.

### <a name="return-value"></a>Rückgabewert

Ein Icon-Ressourcenbezeichner, wenn erfolgreich; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt fehl, wenn die Ansicht nicht zuerst mit [CMouseManager::AddView](#addview)registriert wird.

## <a name="cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a>CMouseManager::GetViewIdByName

Ruft die Ansichts-ID ab, die einem Ansichtsnamen zugeordnet ist.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
[in] Der Ansichtsname.

### <a name="return-value"></a>Rückgabewert

Eine Ansichts-ID, wenn erfolgreich; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode durchsucht Ansichten, die mit [CMouseManager::AddView](#addview)registriert wurden.

## <a name="cmousemanagergetviewnames"></a><a name="getviewnames"></a>CMouseManager::GetViewNames

Ruft eine Liste aller registrierten Ansichtsnamen ab.

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parameter

*listOfNames*<br/>
[out] Ein Verweis `CStringList` auf das Objekt.

### <a name="remarks"></a>Bemerkungen

Diese Methode füllt `listOfNames` den Parameter mit den Namen aller Ansichten, die mit [CMouseManager::AddView](#addview)registriert wurden.

## <a name="cmousemanagerloadstate"></a><a name="loadstate"></a>CMouseManager::LoadState

Lädt den Status der [CMouseManager-Klasse](../../mfc/reference/cmousemanager-class.md) aus der Registrierung.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Ein Pfad eines Registrierungsschlüssels.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die aus der Registrierung geladenen Statusinformationen umfassen die registrierten Ansichten, Ansichtsbezeichner und die zugehörigen Befehle. Wenn der Parameter *lpszProfileName* NULL ist, lädt diese Funktion die `CMouseManager` Daten vom Standardregistrierungsspeicherort, der von der [CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)gesteuert wird.

In den meisten Fällen müssen Sie diese Funktion nicht direkt aufrufen. Sie wird als Teil des Workspace-Initialisierungsprozesses aufgerufen. Weitere Informationen zum Workspace-Initialisierungsprozess finden Sie unter [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).

## <a name="cmousemanagersavestate"></a><a name="savestate"></a>CMouseManager::SaveState

Schreibt den Status der [CMouseManager-Klasse](../../mfc/reference/cmousemanager-class.md) in die Registrierung.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Ein Pfad eines Registrierungsschlüssels.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die in die Registrierung geschriebenen Statusinformationen umfassen alle registrierten Ansichten, Ansichtsbezeichner und die zugehörigen Befehle. Wenn der Parameter *lpszProfileName* NULL ist, schreibt diese Funktion die `CMouseManager` Daten in den Standardregistrierungsspeicherort, der von der [CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)gesteuert wird.

In den meisten Fällen müssen Sie diese Funktion nicht direkt aufrufen. Sie wird als Teil des Workspace-Serialisierungsprozesses aufgerufen. Weitere Informationen zum Prozess der Workspaceserialisierung finden Sie unter [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

## <a name="cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk

Ordnet einen benutzerdefinierten Befehl einer Ansicht zu, die zuerst beim Maus-Manager registriert ist.

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>Parameter

*iViewId*<br/>
[in] Der Ansichtsbezeichner.

*uiCmd*<br/>
[in] Der Befehlsbezeichner.

### <a name="remarks"></a>Bemerkungen

Um einen benutzerdefinierten Befehl einer Ansicht zuzuordnen, müssen Sie die Ansicht zuerst mit [CMouseManager::AddView](#addview)registrieren. Die `AddView` Methode erfordert einen Ansichtsbezeichner als Eingabeparameter. Nachdem Sie eine Ansicht registriert `CMouseManager::SetCommandForDblClk` haben, können Sie denselben Eingabeparameter für Ansichtskennungen aufrufen, den Sie an `AddView`angegeben haben. Wenn der Benutzer anschließend in der registrierten Ansicht mit der Maus doppelklickt, führt die Anwendung den von *uiCmd* angegebenen Befehl aus. Um das benutzerdefinierte Mausverhalten zu unterstützen, müssen Sie auch die Ansicht anpassen, die beim Maus-Manager registriert ist. Weitere Informationen zum benutzerdefinierten Mausverhalten finden Sie unter [Tastatur- und Mausanpassung](../keyboard-and-mouse-customization.md).

Wenn *uiCmd* auf 0 gesetzt ist, ist die angegebene Ansicht keinem Befehl mehr zugeordnet.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)<br/>
[Tastatur- und Mausanpassung](../../mfc/keyboard-and-mouse-customization.md)
