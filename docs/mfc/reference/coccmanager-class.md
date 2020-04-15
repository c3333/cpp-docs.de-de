---
title: COccManager-Klasse
ms.date: 11/04/2016
f1_keywords:
- COccManager
- AFXOCC/COccManager
- AFXOCC/COccManager::CreateContainer
- AFXOCC/COccManager::CreateDlgControls
- AFXOCC/COccManager::CreateSite
- AFXOCC/COccManager::GetDefBtnCode
- AFXOCC/COccManager::IsDialogMessage
- AFXOCC/COccManager::IsLabelControl
- AFXOCC/COccManager::IsMatchingMnemonic
- AFXOCC/COccManager::OnEvent
- AFXOCC/COccManager::PostCreateDialog
- AFXOCC/COccManager::PreCreateDialog
- AFXOCC/COccManager::SetDefaultButton
- AFXOCC/COccManager::SplitDialogTemplate
helpviewer_keywords:
- COccManager [MFC], CreateContainer
- COccManager [MFC], CreateDlgControls
- COccManager [MFC], CreateSite
- COccManager [MFC], GetDefBtnCode
- COccManager [MFC], IsDialogMessage
- COccManager [MFC], IsLabelControl
- COccManager [MFC], IsMatchingMnemonic
- COccManager [MFC], OnEvent
- COccManager [MFC], PostCreateDialog
- COccManager [MFC], PreCreateDialog
- COccManager [MFC], SetDefaultButton
- COccManager [MFC], SplitDialogTemplate
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
ms.openlocfilehash: 5637a4709e90bb14caff3fe4e396487e62e213e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360361"
---
# <a name="coccmanager-class"></a>COccManager-Klasse

Verwaltet unterschiedliche benutzerdefinierte ControlSites. Wird von `COleControlContainer` - und `COleControlSite` -Objekten implementiert.

## <a name="syntax"></a>Syntax

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CoccManager::CreateContainer](#createcontainer)|Erstellt ein `COleContainer` -Objekt.|
|[CoccManager::CreateDlgControls](#createdlgcontrols)|Erstellt ActiveX-Steuerelemente, `COleContainer` die vom zugeordneten Objekt gehostet werden.|
|[CoccManager::CreateSite](#createsite)|Erstellt ein `COleClientSite` -Objekt.|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Ruft den Code der Standardschaltfläche ab.|
|[CoccManager::IsDialogMessage](#isdialogmessage)|Bestimmt das Ziel einer Dialogfeldnachricht.|
|[CoccManager::IsLabelControl](#islabelcontrol)|Bestimmt, ob es sich bei dem angegebenen Steuerelement um ein Beschriftungssteuerelement handelt.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Bestimmt, ob die aktuelle mnemonic mit der mnemonic des angegebenen Steuerelements übereinstimmt.|
|[CoccManager::OnEvent](#onevent)|Versucht, das angegebene Ereignis zu behandeln.|
|[COccManager::PostCreateDialog](#postcreatedialog)|Gibt Ressourcen frei, die während der Dialogerstellung zugewiesen wurden.|
|[COccManager::PreCreateDialog](#precreatedialog)|Verarbeitet eine Dialogfeldvorlage für ActiveX-Steuerelemente.|
|[CoccManager::SetDefaultButton](#setdefaultbutton)|Schaltet den Standardstatus des angegebenen Steuerelements um.|
|[CoccManager::SplitDialogTemplate](#splitdialogtemplate)|Trennt alle vorhandenen ActiveX-Steuerelemente von allgemeinen Steuerelementen in der angegebenen Dialogfeldvorlage.|

## <a name="remarks"></a>Bemerkungen

Die Basisklasse `CNoTrackObject`, ist eine nicht dokumentierte Basisklasse (in AFXTLS). H). Klassen, die von der `CNoTrackObject` Klasse abgeleitet wurden, sind für die Verwendung durch das MFC-Framework von der Erkennung von Speicherlecks ausgenommen. Es wird nicht empfohlen, dass `CNoTrackObject`Sie direkt von ableiten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxocc.h

## <a name="coccmanagercreatecontainer"></a><a name="createcontainer"></a>CoccManager::CreateContainer

Wird vom Framework aufgerufen, um einen Steuerelementcontainer zu erstellen.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf das Fensterobjekt, das dem benutzerdefinierten Websitecontainer zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den neu erstellten Container; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Erstellen benutzerdefinierter Websites finden Sie unter [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

## <a name="coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a>CoccManager::CreateDlgControls

Rufen Sie diese Funktion auf, um ActiveX-Steuerelemente zu erstellen, die durch den Parameter *pOccDialogInfo* angegeben werden.

```
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    LPCTSTR lpszResourceName,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);

virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    void* lpResource,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
Ein Zeiger auf das übergeordnete Element des Dialogobjekts.

*lpszResourceName*<br/>
Der Name der zu erstellenden Ressource.

*pOccDialogInfo*<br/>
Ein Zeiger auf die Dialogvorlage, die zum Erstellen des Dialogobjekts verwendet wird.

*lpResource*<br/>
Ein Zeiger auf eine Ressource.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Steuerelement erfolgreich erstellt wurde; andernfalls Null.

## <a name="coccmanagercreatesite"></a><a name="createsite"></a>CoccManager::CreateSite

Wird vom Framework aufgerufen, um eine Kontrollsite zu erstellen, die vom Container gehostet wird, auf den *pCtrlCont*zeigt.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parameter

*pCtrlCont*<br/>
Ein Zeiger auf den Steuerelementcontainer, der die neue Kontrollsite hostet.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die neu erstellte Kontrollsite.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um eine benutzerdefinierte Steuerungssite mit Ihrer [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-derived-Klasse zu erstellen.

Jeder Steuerelementcontainer kann mehrere Standorte hosten. Erstellen Sie zusätzliche Websites `CreateSite`mit mehreren Aufrufen von .

## <a name="coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a>COccManager::GetDefBtnCode

Rufen Sie diese Funktion auf, um zu bestimmen, ob es sich bei dem Steuerelement um eine Standard-Push-Taste handelt.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Das Fensterobjekt, das das Schaltflächensteuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Einer der folgenden Werte:

- DLGC_DEFPUSHBUTTON Control ist die Standardschaltfläche im Dialogfeld.

- DLGC_UNDEFPUSHBUTTON Control ist nicht die Standardschaltfläche im Dialogfeld.

- **0** Die Steuerung ist keine Schaltfläche.

## <a name="coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a>CoccManager::IsDialogMessage

Wird vom Framework aufgerufen, um zu bestimmen, ob eine Nachricht für das angegebene Dialogfeld vorgesehen ist, und verarbeitet die Nachricht, falls dies der Fall ist.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*pWndDlg*<br/>
Ein Zeiger auf das beabsichtigte Zieldialogfeld der Nachricht.

*lpMsg*<br/>
Ein Zeiger auf `MSG` eine Struktur, die die zu überprüfende Nachricht enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Nachricht verarbeitet wird; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Das Standardverhalten `IsDialogMessage` von besteht darin, nach Tastaturmeldungen zu suchen und sie in Auswahlen für das entsprechende Dialogfeld umzuwandeln. Wenn Sie beispielsweise gedrückt werden, wird die nächste Steuerelemente oder Steuerungsgruppe ausgewählt, wenn Sie gedrückt werden.

Überschreiben Sie diese Funktion, um benutzerdefiniertes Verhalten für Nachrichten bereitzustellen, die an das angegebene Dialogfeld gesendet werden.

## <a name="coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a>CoccManager::IsLabelControl

Rufen Sie diese Funktion auf, um zu bestimmen, ob es sich bei dem angegebenen Steuerelement um ein Beschriftungssteuerelement handelt.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf das Fenster, das das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn es sich bei dem Steuerelement um eine Bezeichnung handelt; sonst Null

### <a name="remarks"></a>Bemerkungen

Ein Etikettensteuerelement ist ein Etikett, das wie ein Etikett für die nächste Steuerung in der Bestellung wirkt.

## <a name="coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic

Rufen Sie diese Funktion auf, um zu bestimmen, ob die aktuelle mnemonic mit der vom Steuerelement dargestellten übereinstimmt.

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf das Fenster, das das Steuerelement enthält.

*lpMsg*<br/>
Ein Zeiger auf die Nachricht, die die zu übereinstimmende mnemonic enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der mnemonic mit dem Steuerelement übereinstimmt; sonst Null

### <a name="remarks"></a>Bemerkungen

## <a name="coccmanageronevent"></a><a name="onevent"></a>CoccManager::OnEvent

Wird vom Framework aufgerufen, um das angegebene Ereignis zu behandeln.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parameter

*pCmdTarget*<br/>
Ein Zeiger auf `CCmdTarget` das Objekt, das versucht, das Ereignis zu behandeln

*idCtrl*<br/>
Die Ressourcen-ID des Steuerelements.

*pEvent*<br/>
Das behandelte Ereignis.

*pHandlerInfo*<br/>
Wenn nicht `OnEvent` NULL, füllt `pTarget` `pmf` die und `AFX_CMDHANDLERINFO` Member der Struktur, anstatt den Befehl zu senden. In der Regel sollte dieser Parameter NULL sein.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Ereignis behandelt wurde, andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um den standardmäßigen Ereignisbehandlungsprozess anzupassen.

## <a name="coccmanagerprecreatedialog"></a><a name="precreatedialog"></a>COccManager::PreCreateDialog

Wird vom Framework aufgerufen, um eine Dialogvorlage für ActiveX-Steuerelemente zu verarbeiten, bevor das eigentliche Dialogfeld erstellt wird.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parameter

*pOccDialogInfo*<br/>
Eine `_AFX_OCC_DIALOG_INFO` Struktur, die Informationen zur Dialogvorlage und alle ActiveX-Steuerelemente enthält, die vom Dialogfeld gehostet werden.

*pOrigTemplate*<br/>
Ein Zeiger auf die Dialogvorlage, die beim Erstellen des Dialogfelds verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Dialogfeldvorlagenstruktur, die zum Erstellen des Dialogfelds verwendet wird.

### <a name="remarks"></a>Bemerkungen

Das Standardverhalten ruft `SplitDialogTemplate`einen Aufruf von aus, um festzustellen, ob ActiveX-Steuerelemente vorhanden sind, und gibt dann die resultierende Dialogfeldvorlage zurück.

Überschreiben Sie diese Funktion, um den Prozess des Erstellens eines Dialogfelds anzupassen, in dem ActiveX-Steuerelemente gehostet werden.

## <a name="coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a>COccManager::PostCreateDialog

Wird vom Framework aufgerufen, um den für die Dialogvorlage reservierten Speicher freizugeben.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parameter

*pOccDialogInfo*<br/>
Eine `_AFX_OCC_DIALOG_INFO` Struktur, die Informationen zur Dialogvorlage und alle ActiveX-Steuerelemente enthält, die vom Dialogfeld gehostet werden.

### <a name="remarks"></a>Bemerkungen

Dieser Speicher wurde durch `SplitDialogTemplate`einen Aufruf von zugewiesen und für alle gehosteten ActiveX-Steuerelemente im Dialogfeld verwendet.

Überschreiben Sie diese Funktion, um den Vorgang zum Bereinigen aller Ressourcen anzupassen, die vom Dialogfeldobjekt verwendet werden.

## <a name="coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a>CoccManager::SetDefaultButton

Rufen Sie diese Funktion auf, um das Steuerelement als Standardschaltfläche festzulegen.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf das Fenster, das das Steuerelement enthält.

*bDefault*<br/>
Ein Wert ungleich Null, wenn das Steuerelement zur Standardschaltfläche werden soll; andernfalls Null.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Das Steuerelement muss die OLEMISC_ACTSLIKEBUTTON Statusbit festgelegt haben. Weitere Informationen zu OLEMISC-Flags finden Sie im [OLEMISC-Thema](/windows/win32/api/oleidl/ne-oleidl-olemisc) im Windows SDK.

## <a name="coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a>CoccManager::SplitDialogTemplate

Wird vom Framework aufgerufen, um die ActiveX-Steuerelemente von allgemeinen Dialogsteuerelementen aufzuteilen.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Parameter

*pTemplate*<br/>
Ein Zeiger auf die zu untersuchende Dialogvorlage.

*ppOleDlgItems*<br/>
Eine Liste von Zeigern auf Dialogfeldelemente, die ActiveX-Steuerelemente sind.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Dialogvorlagenstruktur, die nur Nicht-ActiveX-Steuerelemente enthält. Wenn keine ActiveX-Steuerelemente vorhanden sind, wird NULL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn ActiveX-Steuerelemente gefunden werden, wird die Vorlage analysiert, und es wird eine neue Vorlage erstellt, die nur Nicht-ActiveX-Steuerelemente enthält. Alle ActiveX-Steuerelemente, die während dieses Prozesses gefunden wurden, werden *ppOleDlgItems*hinzugefügt.

Wenn die Vorlage keine ActiveX-Steuerelemente enthält, wird NULL *zurückgegeben.*

> [!NOTE]
> Der für die neue Vorlage `PostCreateDialog` reservierte Speicher wird in der Funktion freigegeben.

Überschreiben Sie diese Funktion, um diesen Prozess anzupassen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite-Klasse](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer-Klasse](../../mfc/reference/colecontrolcontainer-class.md)
