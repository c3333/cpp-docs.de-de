---
title: CUserTool-Klasse
ms.date: 11/04/2016
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
ms.openlocfilehash: 183b30961e4a7d3079fa0d035a4ddc38bc2eebac
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752027"
---
# <a name="cusertool-class"></a>CUserTool-Klasse

Ein Benutzertool ist ein Menüelement, das eine externe Anwendung ausführt. Auf der Registerkarte **Extras** des Dialogfelds **Anpassen** ( [CMFCToolBarsCustomizeDialog-Klasse](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) kann der Benutzer Benutzertools hinzufügen und den Namen, den Befehl, die Argumente und das Anfangsverzeichnis für jedes Benutzertool angeben.

## <a name="syntax"></a>Syntax

```
class CUserTool : public CObject
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|Zeichnet das Benutzerwerkzeugsymbol in einem angegebenen Rechteck.|
|[CUserTool::GetCommand](#getcommand)|Gibt eine Zeichenfolge zurück, die den Text des Befehls enthält, der dem Benutzertool zugeordnet ist.|
|[CUserTool::GetCommandId](#getcommandid)|Gibt die Befehls-ID des Menüelements des Benutzertools zurück.|
|[CUserTool::Aufrufen](#invoke)|Führt den dem Benutzertool zugeordneten Befehl aus.|
|[CUserTool::Serialisieren](#serialize)|Liest oder schreibt dieses Objekt aus einem oder in ein Archiv. (Überschreibt [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CUserTool::SetCommand](#setcommand)|Legt den Befehl fest, der dem Benutzertool zugeordnet ist.|
|[CUserTool::SetToolIcon](#settoolicon)|Lädt das Symbol für das Benutzerwerkzeug aus der dem Werkzeug zugeordneten Anwendung.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Lädt das Standardsymbol für ein Benutzertool.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Die Befehlszeilenargumente für das Benutzertool.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Das Anfangsverzeichnis für das Benutzertool.|
|[CUserTool::m_strLabel](#m_strlabel)|Der Werkzeugname, der im Menüelement für das Werkzeug angezeigt wird.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Aktivieren von Benutzertools in Ihrer Anwendung finden Sie unter [CUserToolsManager-Klasse](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CUserToolsManager` wie Sie `m_strLabel` ein Werkzeug aus einem Objekt erstellen, die Membervariable festlegen und die Anwendung festlegen, die das Benutzertool ausführt. Dieser Codeausschnitt ist Teil des [Visual Studio Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxusertool.h

## <a name="cusertoolcopyicontoclipboard"></a><a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cusertooldrawtoolicon"></a><a name="drawtoolicon"></a>CUserTool::DrawToolIcon

Zeichnet das Benutzerwerkzeugsymbol in der Mitte eines angegebenen Rechtecks.

```cpp
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*rectImage*<br/>
[in] Gibt die Koordinaten des Bereichs an, der das Symbol anzeigen soll.

## <a name="cusertoolgetcommand"></a><a name="getcommand"></a>CUserTool::GetCommand

Gibt eine Zeichenfolge zurück, die den Text des Befehls enthält, der dem Benutzertool zugeordnet ist.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis `CString` auf ein Objekt, das den Text des Befehls enthält, der dem Benutzertool zugeordnet ist.

## <a name="cusertoolgetcommandid"></a><a name="getcommandid"></a>CUserTool::GetCommandId

Gibt die Befehls-ID des Benutzertools zurück.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Rückgabewert

Die Befehls-ID dieses Benutzertools.

## <a name="cusertoolinvoke"></a><a name="invoke"></a>CUserTool::Aufrufen

Führt den dem Benutzertool zugeordneten Befehl aus.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Befehl erfolgreich ausgeführt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ruft [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) auf, um einen Befehl auszuführen, der dem Benutzertool zugeordnet ist. Die Funktion schlägt fehl, wenn der Befehl leer ist oder [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) fehlschlägt.

## <a name="cusertoolloaddefaulticon"></a><a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon

Lädt das Standardsymbol für ein Benutzertool.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für das geladene Symbol ( HICON) oder NULL, wenn das Standardsymbol nicht geladen werden kann.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn es nicht in der Lage ist, ein Symbol für ein benutzerdefiniertes Tool aus der ausführbaren Datei des Tools zu laden.

Überschreiben Sie diese Methode, um ein eigenes Standardsymbol für das Werkzeug einzuschließen.

## <a name="cusertoolm_strarguments"></a><a name="m_strarguments"></a>CUserTool::m_strArguments

Die Befehlszeilenargumente für das Benutzertool.

```
CString m_strArguments;
```

### <a name="remarks"></a>Bemerkungen

Diese Zeichenfolge wird an das Tool übergeben, wenn Sie [CUserTool::Invoke](#invoke) aufrufen oder wenn ein Benutzer auf den diesem Tool zugeordneten Befehl klickt.

## <a name="cusertoolm_strinitialdirectory"></a><a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory

Gibt das Anfangsverzeichnis für das Benutzertool an.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Bemerkungen

Diese Variable gibt das Anfangsverzeichnis an, in dem das Tool ausgeführt wird, wenn Sie [CUserTool::Invoke](#invoke) aufrufen oder wenn ein Benutzer auf den diesem Tool zugeordneten Befehl klickt.

## <a name="cusertoolm_strlabel"></a><a name="m_strlabel"></a>CUserTool::m_strLabel

Die Beschriftung, die im Menüelement für das Werkzeug angezeigt wird.

```
CString m_strLabel;
```

## <a name="cusertoolserialize"></a><a name="serialize"></a>CUserTool::Serialisieren

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

[in] *ar*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cusertoolsetcommand"></a><a name="setcommand"></a>CUserTool::SetCommand

Legt die Anwendung fest, die das Benutzertool ausführt.

```cpp
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Parameter

*lpszCmd*<br/>
[in] Gibt die neue Anwendung an, die dem Benutzertool zugeordnet werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um eine neue Anwendung festzulegen, die vom Benutzertool ausgeführt wird. Die Methode zerstört das alte Symbol und lädt ein neues Symbol aus der angegebenen Anwendung. Wenn ein Symbol nicht aus der Anwendung geladen werden kann, wird das Standardsymbol für ein Benutzertool geladen, indem [CUserTool::LoadDefaultIcon](#loaddefaulticon)aufgerufen wird.

## <a name="cusertoolsettoolicon"></a><a name="settoolicon"></a>CUserTool::SetToolIcon

Lädt das Symbol für das Benutzerwerkzeug aus der Anwendung, die das Tool verwendet.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle zum geladenen Symbol.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um das Symbol zu laden, das im Menüpunkt angezeigt werden soll. Diese Methode sucht nach dem Symbol in der ausführbaren Datei, die das Tool verwendet. Wenn es kein Standardsymbol hat, wird stattdessen das von [CUserTool::LoadDefaultIcon](#loaddefaulticon) bereitgestellte Symbol verwendet.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager-Klasse](../../mfc/reference/cusertoolsmanager-class.md)
