---
title: CUserToolsManager-Klasse
ms.date: 11/04/2016
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
helpviewer_keywords:
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
ms.openlocfilehash: 1e9be5d7cb81f2769b98d9baeae786873f5fa73d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751986"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager-Klasse

Behält die Auflistung von [CUserTool-Klassenobjekten](../../mfc/reference/cusertool-class.md) in einer Anwendung bei. Ein Benutzertool ist ein Menüelement, das eine externe Anwendung ausführt. Mithilfe des Objekts `CUserToolsManager` können Benutzer oder Entwickler der Anwendung neue Benutzertools hinzuzufügen. Es unterstützt die Ausführung der Befehle, die Benutzertools zugeordnet sind, und speichert außerdem Informationen über Benutzertools in der Windows-Registrierung.

## <a name="syntax"></a>Syntax

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|Erstellt ein Objekt vom Typ `CUserToolsManager`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CUserToolsManager::CreateNewTool](#createnewtool)|Erstellt ein neues Benutzertool.|
|[CUserToolsManager::FindTool](#findtool)|Gibt den Zeiger `CMFCUserTool` auf das Objekt zurück, das einer angegebenen Befehls-ID zugeordnet ist.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Gibt die Ressourcen-ID zurück, die dem Menü **Argumente** auf der Registerkarte **Extras** im Dialogfeld **Anpassen** zugeordnet ist.|
|[CUserToolsManager::GetDefExt](#getdefext)|Gibt die Standarderweiterung zurück, die das Dialogfeld **Dateigeöffnet** ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) im **Feld Befehl** auf der Registerkarte **Werkzeuge** im Dialogfeld **Anpassen** verwendet.|
|[CUserToolsManager::GetFilter](#getfilter)|Gibt den Dateifilter zurück, den das Dialogfeld **Dateigeöffnet** ( [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md)) im **Feld Befehl** auf der Registerkarte **Werkzeuge** im Dialogfeld **Anpassen** verwendet.|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Gibt die Ressourcen-ID zurück, die dem Menü **"Anfangsverzeichnis"** auf der Registerkarte **Extras** im Dialogfeld **Anpassen** zugeordnet ist.|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Gibt die maximale Anzahl von Benutzertools zurück, die in der Anwendung zugewiesen werden können.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Gibt die Befehls-ID des Menüelementplatzhalters für Benutzertools zurück.|
|[CUserToolsManager::GetUserTools](#getusertools)|Gibt einen Verweis auf die Liste der Benutzertools zurück.|
|[CUserToolsManager::InvokeTool](#invoketool)|Führt eine Anwendung aus, die dem Benutzertool zugeordnet ist, das über eine angegebene Befehls-ID verfügt.|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Bestimmt, ob eine Befehls-ID einem Benutzertool zugeordnet ist.|
|[CUserToolsManager::LoadState](#loadstate)|Lädt Informationen zu Benutzertools aus der Windows-Registrierung.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|Verschiebt das angegebene Benutzertool in der Liste der Benutzertools nach unten.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|Verschiebt das angegebene Benutzertool in der Liste der Benutzertools nach oben.|
|[CUserToolsManager::RemoveTool](#removetool)|Entfernt das angegebene Benutzertool aus der Anwendung.|
|[CUserToolsManager::SaveState](#savestate)|Speichert Informationen zu Benutzertools in der Windows-Registrierung.|
|[CUserToolsManager::SetDefExt](#setdefext)|Gibt die Standarderweiterung an, die das Dialogfeld **Dateiöffnen** ( [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md)) im **Befehlsfeld** auf der Registerkarte **Werkzeuge** im Dialogfeld **Anpassen** verwendet.|
|[CUserToolsManager::SetFilter](#setfilter)|Gibt den Dateifilter an, den das Dialogfeld **Dateiöffnen** ( [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md)) im **Befehlsfeld** auf der Registerkarte **Werkzeuge** im Dialogfeld **Anpassen** verwendet.|

## <a name="remarks"></a>Bemerkungen

Um Benutzertools in Ihre Anwendung zu integrieren, müssen Sie:

1. Reservieren Sie ein Menüelement und eine zugehörige Befehls-ID für einen Menüeintrag des Benutzertools.

2. Reservieren Sie eine sequenzielle Befehls-ID für jedes Benutzertool, das ein Benutzer in Ihrer Anwendung definieren kann.

3. Rufen Sie die [CWinAppEx::EnableUserTools-Methode](../../mfc/reference/cwinappex-class.md#enableusertools) auf und geben Sie die folgenden Parameter an: Menübefehls-ID, erste Benutzertool-Befehls-ID und letzte Benutzerwerkzeugbefehls-ID.

Es sollte nur `CUserToolsManager` ein globales Objekt pro Anwendung vorhanden sein.

Ein Beispiel für Benutzertools finden Sie im VisualStudioDemo-Beispielprojekt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CUserToolsManager` wie Sie einen Verweis auf ein Objekt abrufen und neue Benutzertools erstellen. Dieser Codeausschnitt ist Teil des [Visual Studio Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxusertoolsmanager.h

## <a name="cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a>CUserToolsManager::CreateNewTool

Erstellt ein neues Benutzertool.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Benutzertool oder NULL, wenn die Anzahl der Benutzertools das Maximum überschritten hat. Der zurückgegebene Typ entspricht dem Typ, `CWinAppEx::EnableUserTools` an den als *pToolRTC-Parameter* übergeben wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode findet die erste verfügbare Menübefehls-ID in dem Bereich, der im Aufruf von [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) angegeben wird, und weist dem Benutzertool diese ID zu.

Die Methode schlägt fehl, wenn die Anzahl der Werkzeuge das Maximum erreicht hat. Dies tritt auf, wenn alle Befehls-IDs innerhalb des Bereichs Benutzertools zugewiesen werden. Sie können die maximale Anzahl von Tools abrufen, indem Sie [CUserToolsManager::GetMaxTools](#getmaxtools)aufrufen. Sie können auf die Toolsliste zugreifen, indem Sie die [CUserToolsManager::GetUserTools-Methode](#getusertools) aufrufen.

## <a name="cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a>CUserToolsManager::CUserToolsManager

Erstellt ein Objekt vom Typ `CUserToolsManager`. Jede Anwendung muss über höchstens einen Benutzertools-Manager verfügen.

```
CUserToolsManager();

CUserToolsManager(
    const UINT uiCmdToolsDummy,
    const UINT uiCmdFirst,
    const UINT uiCmdLast,
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),
    UINT uArgMenuID=0,
    UINT uInitDirMenuID=0);
```

### <a name="parameters"></a>Parameter

*uiCmdToolsDummy*<br/>
[in] Eine ganzzahlige Datei ohne Vorzeichen, die das Framework als Platzhalter für die Befehls-ID des Menüs "Benutzertools" verwendet.

*uiCmdFirst*<br/>
[in] Die Befehls-ID für den ersten Benutzertoolbefehl.

*uiCmdLast*<br/>
[in] Die Befehls-ID für den letzten Benutzertoolbefehl.

*pToolRTC*<br/>
[in] Die Klasse, die [CUserToolsManager::CreateNewTool](#createnewtool) erstellt. Mithilfe dieser Klasse können Sie anstelle der Standardimplementierung einen abgeleiteten Typ der [CUserTool-Klasse](../../mfc/reference/cusertool-class.md) verwenden.

*uArgMenuID*<br/>
[in] Die Menüressourcen-ID des Argument-Popupmenüs.

*uInitDirMenuID*<br/>
[in] Die Menüressourcen-ID des ersten Verzeichnis-Popupmenüs.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diesen Konstruktor nicht auf. Rufen Sie stattdessen [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) auf, um Benutzertools zu aktivieren, und rufen Sie [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) auf, um einen Zeiger auf die `CUserToolsManager`zu erhalten. Weitere Informationen finden Sie unter [Benutzerdefinierte Tools](../../mfc/user-defined-tools.md).

## <a name="cusertoolsmanagerfindtool"></a><a name="findtool"></a>CUserToolsManager::FindTool

Gibt den Zeiger auf das [CUserTool-Klassenobjekt](../../mfc/reference/cusertool-class.md) zurück, das einer angegebenen Befehls-ID zugeordnet ist.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parameter

*uiCmdId*<br/>
[in] Ein Menübefehlsbezeichner.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine [CUserTool-Klasse](../../mfc/reference/cusertool-class.md) oder `CUserTool`ein -derived-Objekt bei Erfolg; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn `FindTool` erfolgreich, ist der zurückgegebene Typ der gleiche wie der Typ des *pToolRTC-Parameters* [in CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a>CUserToolsManager::GetArgumentsMenuID

Gibt die Ressourcen-ID zurück, die dem Menü **Argumente** auf der Registerkarte **Extras** im Dialogfeld **Anpassen** zugeordnet ist.

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>Rückgabewert

Der Bezeichner einer Menüressource.

### <a name="remarks"></a>Bemerkungen

Der *uArgMenuID-Parameter* von [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) gibt die ID der Ressource an.

## <a name="cusertoolsmanagergetdefext"></a><a name="getdefext"></a>CUserToolsManager::GetDefExt

Gibt die Standarderweiterung zurück, die das Dialogfeld **Dateigeöffnet** ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) im **Feld Befehl** auf der Registerkarte **Werkzeuge** im Dialogfeld **Anpassen** verwendet.

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis `CString` auf das Objekt, das die Erweiterung enthält.

## <a name="cusertoolsmanagergetfilter"></a><a name="getfilter"></a>CUserToolsManager::GetFilter

Gibt den Dateifilter zurück, den das Dialogfeld **Dateigeöffnet** ( [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md)) im **Feld Befehl** auf der Registerkarte **Werkzeuge** im Dialogfeld **Anpassen** verwendet.

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis `CString` auf das Objekt, das den Filter enthält.

## <a name="cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a>CUserToolsManager::GetInitialDirMenuID

Gibt die Ressourcen-ID zurück, die dem Menü **"Anfangsverzeichnis"** auf der Registerkarte **Extras** im Dialogfeld **Anpassen** zugeordnet ist.

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Menüressourcenbezeichner.

### <a name="remarks"></a>Bemerkungen

Die zurückgegebene ID wird im *UInitDirMenuID-Parameter* von [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)angegeben.

## <a name="cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a>CUserToolsManager::GetMaxTools

Gibt die maximale Anzahl von Benutzertools zurück, die in der Anwendung zugewiesen werden können.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Benutzertools, die zugewiesen werden können.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die maximale Anzahl von Tools abzurufen, die in der Anwendung zugewiesen werden können. Diese Zahl ist die Anzahl der IDs im Bereich von *uiCmdFirst* bis zu den *uiCmdLast-Parametern,* die Sie an [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)übergeben.

## <a name="cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a>CUserToolsManager::GetToolsEntryCmd

Gibt die Befehls-ID des Menüelementplatzhalters für Benutzertools zurück.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>Rückgabewert

Die Befehls-ID des Platzhalters.

### <a name="remarks"></a>Bemerkungen

Um Benutzertools zu aktivieren, rufen Sie [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)auf. Der Parameter *uiCmdToolsDummy* gibt die Befehls-ID des Befehls tools entry an. Diese Methode gibt die Befehls-ID für den Werkzeugeintrag zurück. Überall dort, wo diese ID in einem Menü verwendet wird, wird sie durch die Liste der Benutzertools ersetzt, wenn das Menü angezeigt wird.

## <a name="cusertoolsmanagergetusertools"></a><a name="getusertools"></a>CUserToolsManager::GetUserTools

Gibt einen Verweis auf die Liste der Benutzertools zurück.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>Rückgabewert

Ein const-Verweis auf ein [CObList-Klassenobjekt,](../../mfc/reference/coblist-class.md) das eine Liste von Benutzertools enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um eine Liste von Benutzertools abzurufen, die vom [CUserToolsManager-Objekt](../../mfc/reference/cusertoolsmanager-class.md) verwaltet werden. Jedes Benutzertool wird durch ein Objekt vom Typ [CUserTool Class](../../mfc/reference/cusertool-class.md) oder einen von `CUserTool`abgeleiteten Typ dargestellt. Der Typ wird durch den Parameter *pToolRTC* angegeben, wenn Sie [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) aufrufen, um Benutzertools zu aktivieren.

## <a name="cusertoolsmanagerinvoketool"></a><a name="invoketool"></a>CUserToolsManager::InvokeTool

Führt eine Anwendung aus, die dem Benutzertool zugeordnet ist, das über eine angegebene Befehls-ID verfügt.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>Parameter

*uiCmdId*<br/>
[in] Die Menübefehls-ID, die dem Benutzertool zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der dem Benutzertool zugeordnete Befehl erfolgreich ausgeführt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um eine Anwendung auszuführen, die dem Benutzertool zugeordnet ist, das die von *uiCmdId*angegebene Befehls-ID enthält.

## <a name="cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a>CUserToolsManager::IsUserToolCmd

Bestimmt, ob eine Befehls-ID einem Benutzertool zugeordnet ist.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parameter

*uiCmdId*<br/>
[in] Eine Befehls-ID des Menüelements.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn eine bestimmte Befehls-ID einem Benutzertool zugeordnet ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode überprüft, ob sich die angegebene Befehls-ID im Befehls-ID-Bereich befindet. Sie geben den Bereich an, wenn Sie [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) aufrufen, um Benutzertools zu aktivieren.

## <a name="cusertoolsmanagerloadstate"></a><a name="loadstate"></a>CUserToolsManager::LoadState

Lädt Informationen zu Benutzertools aus der Windows-Registrierung.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Der Pfad des Windows-Registrierungsschlüssels.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Status erfolgreich geladen wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode lädt den `CUserToolsManager` Status des Objekts aus der Windows-Registrierung.

Normalerweise rufen Sie diese Methode nicht direkt auf. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) ruft es als Teil des Workspace-Initialisierungsprozesses auf.

## <a name="cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a>CUserToolsManager::MoveToolDown

Verschiebt das angegebene Benutzertool in der Liste der Benutzertools nach unten.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>Parameter

*pTool*<br/>
[in] Gibt das zu verschiebende Benutzerwerkzeug an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Benutzertool erfolgreich nach unten verschoben wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Methode schlägt fehl, wenn das vom *pTool* angibte Werkzeug nicht in der internen Liste enthalten ist oder wenn das Werkzeug zuletzt in der Liste enthalten ist.

## <a name="cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a>CUserToolsManager::MoveToolUp

Verschiebt das angegebene Benutzertool in der Liste der Benutzertools nach oben.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>Parameter

*pTool*<br/>
[in] Gibt das zu verschiebende Benutzerwerkzeug an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Benutzertool erfolgreich nach oben verschoben wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Methode schlägt fehl, wenn das Werkzeug, das der *pTool-Parameter* angibt, nicht in der internen Liste enthalten ist oder wenn das Werkzeug das erste Werkzeugelement in der Liste ist.

## <a name="cusertoolsmanagerremovetool"></a><a name="removetool"></a>CUserToolsManager::RemoveTool

Entfernt das angegebene Benutzertool aus der Anwendung.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>Parameter

*pTool*<br/>
[in, out] Ein Zeiger auf ein Benutzertool, das entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Werkzeug erfolgreich entfernt wurde. Andernfalls lautet der Wert FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn das Tool erfolgreich entfernt wurde, löscht diese Methode *pTool*.

## <a name="cusertoolsmanagersavestate"></a><a name="savestate"></a>CUserToolsManager::SaveState

Speichert Informationen zu Benutzertools in der Windows-Registrierung.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Ein Pfad zum Windows-Registrierungsschlüssel.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Status erfolgreich gespeichert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Methode speichert den `CUserToolsManager` aktuellen Status des Objekts in der Windows-Registrierung.

Normalerweise müssen Sie diese Methode nicht direkt aufrufen, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) ruft sie automatisch als Teil des Workspace-Serialisierungsprozesses der Anwendung auf.

## <a name="cusertoolsmanagersetdefext"></a><a name="setdefext"></a>CUserToolsManager::SetDefExt

Gibt die Standarderweiterung an, die das Dialogfeld **Dateiöffnen** ( [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md)) im **Befehlsfeld** auf der Registerkarte **Werkzeuge** im Dialogfeld **Anpassen** verwendet.

```cpp
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>Parameter

*strDefExt*<br/>
[in] Eine Textzeichenfolge, die die Standarderweiterung des Dateinamens enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um eine Standarddateinamenerweiterung im Dialogfeld **Dateiöffnen** anzugeben, die angezeigt wird, wenn der Benutzer eine Anwendung auswählt, die dem Benutzertool zugeordnet werden soll. Der Standardwert ist "exe".

## <a name="cusertoolsmanagersetfilter"></a><a name="setfilter"></a>CUserToolsManager::SetFilter

Gibt den Dateifilter an, den das Dialogfeld **Dateiöffnen** ( [CFileDialog-Klasse](../../mfc/reference/cfiledialog-class.md)) im **Befehlsfeld** auf der Registerkarte **Werkzeuge** im Dialogfeld **Anpassen** verwendet.

```cpp
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>Parameter

*strFilter*<br/>
[in] Gibt den Filter an.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool-Klasse](../../mfc/reference/cusertool-class.md)
