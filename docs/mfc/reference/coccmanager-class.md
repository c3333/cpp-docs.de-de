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
ms.openlocfilehash: c2a49e3396879e5f1e0864ab5342b57541c6b36c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423936"
---
# <a name="coccmanager-class"></a>COccManager-Klasse

Verwaltet unterschiedliche benutzerdefinierte ControlSites. Wird von `COleControlContainer` - und `COleControlSite` -Objekten implementiert.

## <a name="syntax"></a>Syntax

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COccManager:: kreatecontainer](#createcontainer)|Erstellt ein `COleContainer`-Objekt.|
|[COccManager:: kreatedlgcontrols](#createdlgcontrols)|Erstellt ActiveX-Steuerelemente, die vom zugeordneten `COleContainer`-Objekt gehostet werden.|
|[COccManager:: up Site](#createsite)|Erstellt ein `COleClientSite`-Objekt.|
|[COccManager:: getdefbtncode](#getdefbtncode)|Ruft den Code der Standard Schaltfläche ab.|
|[COccManager:: IsDialogMessage](#isdialogmessage)|Bestimmt das Ziel einer Dialog Meldung.|
|[COccManager:: islabelcontrol](#islabelcontrol)|Bestimmt, ob das angegebene Steuerelement ein Label-Steuerelement ist.|
|[COccManager:: ismatchingmnetmonic](#ismatchingmnemonic)|Bestimmt, ob das aktuelle mnetmonisches-Element mit dem mnetmonischen des angegebenen Steuer Elements übereinstimmt.|
|[COccManager:: OnEvent](#onevent)|Versucht, das angegebene Ereignis zu behandeln.|
|[COccManager::P ostkreatedialog](#postcreatedialog)|Gibt während der Erstellung des Dialog Felds zugeordnete Ressourcen frei.|
|[COccManager::P neu erstellen Dialog](#precreatedialog)|Verarbeitet eine Dialogfeld Vorlage für ActiveX-Steuerelemente.|
|[COccManager:: setDefaultButton](#setdefaultbutton)|Schaltet den Standardzustand des angegebenen Steuer Elements um.|
|[COccManager:: splitdialogtemplate](#splitdialogtemplate)|Trennt alle vorhandenen ActiveX-Steuerelemente von allgemeinen Steuerelementen in der angegebenen Dialogfeld Vorlage.|

## <a name="remarks"></a>Hinweise

Die Basisklasse, `CNoTrackObject`, ist eine nicht dokumentierte Basisklasse (befindet sich in afxtls). H). Die von der `CNoTrackObject`-Klasse abgeleiteten Klassen sind von der Speicher Speicher-Erkennung ausgenommen, wenn Sie vom MFC-Framework verwendet werden sollen. Es wird nicht empfohlen, die Ableitung direkt von `CNoTrackObject`durchzuführen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxocc. h

##  <a name="createcontainer"></a>COccManager:: kreatecontainer

Wird von Framework aufgerufen, um einen Steuerelement Container zu erstellen.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Ein Zeiger auf das Fenster Objekt, das dem benutzerdefinierten Site Container zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den neu erstellten Container. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Weitere Informationen zum Erstellen von benutzerdefinierten Websites finden Sie unter [COleControlContainer:: attachcontrolsite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

##  <a name="createdlgcontrols"></a>COccManager:: kreatedlgcontrols

Mit dieser Funktion können Sie ActiveX-Steuerelemente erstellen, die durch den *poccdialoginfo* -Parameter angegeben werden.

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

*pwndparent*<br/>
Ein Zeiger auf das übergeordnete Element des Dialog Objekts.

*lpszresourcename*<br/>
Der Name der Ressource, die erstellt wird.

*poccdialoginfo*<br/>
Ein Zeiger auf die Dialogfeld Vorlage, die zum Erstellen des Dialog Objekts verwendet wird.

*lpresource*<br/>
Ein Zeiger auf eine Ressource.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Steuerelement erfolgreich erstellt wurde. andernfalls NULL.

##  <a name="createsite"></a>COccManager:: up Site

Wird von Framework aufgerufen, um eine Steuerelement Website zu erstellen, die von dem Container gehostet wird, auf den von *pctrlact*verwiesen wird.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parameter

*pctrlact*<br/>
Ein Zeiger auf den Steuerelement Container, der die neue Steuerelement Website gehostet.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die neu erstellte Steuerelement Website.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Funktion, um mithilfe der von [COleControlSite](../../mfc/reference/colecontrolsite-class.md)abgeleiteten Klasse eine benutzerdefinierte Steuerelement Website zu erstellen.

Jeder Steuerelement Container kann mehrere-Standorte hosten. Erstellen Sie zusätzliche Standorte mit mehreren Aufrufen an `CreateSite`.

##  <a name="getdefbtncode"></a>COccManager:: getdefbtncode

Mit dieser Funktion können Sie bestimmen, ob das Steuerelement eine standardmäßige pushschaltfläche ist.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Das Fenster Objekt, das das Schaltflächen Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Einer der folgenden Werte:

- DLGC_DEFPUSHBUTTON-Steuerelement ist die Standard Schaltfläche im Dialogfeld.

- DLGC_UNDEFPUSHBUTTON Steuerelement ist nicht die Standard Schaltfläche im Dialogfeld.

- **0** -Steuerelement ist keine Schaltfläche.

##  <a name="isdialogmessage"></a>COccManager:: IsDialogMessage

Wird von Framework aufgerufen, um zu bestimmen, ob eine Meldung für das angegebene Dialogfeld vorgesehen ist, und verarbeitet die Meldung, wenn dies der Fall ist.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*pwnddlg*<br/>
Ein Zeiger auf das beabsichtigte Ziel Dialogfeld der Nachricht.

*lpmsg*<br/>
Ein Zeiger auf eine `MSG`-Struktur, die die zu überprüfende Nachricht enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Nachricht verarbeitet wird. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Das Standardverhalten von `IsDialogMessage` besteht darin, Tastatur Meldungen zu überprüfen und Sie in eine Auswahl für das entsprechende Dialogfeld zu konvertieren. Wenn z. b. die Tab-Taste gedrückt wird, wird das nächste Steuerelement oder die nächste Gruppe von Steuerelementen ausgewählt.

Überschreiben Sie diese Funktion, um benutzerdefiniertes Verhalten für Nachrichten bereitzustellen, die an den angegebenen Dialog

##  <a name="islabelcontrol"></a>COccManager:: islabelcontrol

Mit dieser Funktion wird bestimmt, ob das angegebene Steuerelement ein Label-Steuerelement ist.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Ein Zeiger auf das Fenster, das das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Steuerelement eine Bezeichnung ist. andernfalls NULL

### <a name="remarks"></a>Hinweise

Ein Label-Steuerelement ist ein Steuerelement, das sich wie eine Bezeichnung für das nächste Steuerelement in der Reihenfolge verhält.

##  <a name="ismatchingmnemonic"></a>COccManager:: ismatchingmnetmonic

Mit dieser Funktion wird bestimmt, ob die aktuelle mnetmonische Übereinstimmung mit der vom Steuerelement dargestellten übereinstimmt.

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Ein Zeiger auf das Fenster, das das Steuerelement enthält.

*lpmsg*<br/>
Ein Zeiger auf die Nachricht, die das zu abgleichtende mnetmonische enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der mnetmonic dem Steuerelement entspricht. andernfalls NULL

### <a name="remarks"></a>Hinweise

##  <a name="onevent"></a>COccManager:: OnEvent

Wird von Framework aufgerufen, um das angegebene Ereignis zu behandeln.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parameter

*pcmdtarget*<br/>
Ein Zeiger auf das `CCmdTarget` Objekt, das versucht, das Ereignis zu behandeln.

*idctrl*<br/>
Die Ressourcen-ID des Steuer Elements.

*Peer Event*<br/>
Das Ereignis, das behandelt wird.

*phandlerinfo*<br/>
Wenn nicht NULL, füllt `OnEvent` die `pTarget` und `pmf` Member der `AFX_CMDHANDLERINFO` Struktur aus, statt den Befehl zu verteilen. In der Regel sollte dieser Parameter NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Ereignis behandelt wurde, andernfalls NULL.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Funktion, um den standardmäßigen Ereignis Behandlungsprozess anzupassen.

##  <a name="precreatedialog"></a>COccManager::P neu erstellen Dialog

Wird von Framework aufgerufen, um eine Dialogfeld Vorlage für ActiveX-Steuerelemente zu verarbeiten, bevor das eigentliche Dialogfeld erstellt wird.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parameter

*poccdialoginfo*<br/>
Eine `_AFX_OCC_DIALOG_INFO` Struktur, die Informationen über die Dialogfeld Vorlage und alle vom Dialogfeld gehosteten ActiveX-Steuerelemente enthält.

*porigtemplate*<br/>
Ein Zeiger auf die Dialogfeld Vorlage, die zum Erstellen des Dialog Felds verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Dialogfeld Vorlagen Struktur, die zum Erstellen des Dialog Felds verwendet wird.

### <a name="remarks"></a>Hinweise

Das Standardverhalten führt einen aufzurufenden `SplitDialogTemplate`aus und bestimmt, ob ActiveX-Steuerelemente vorhanden sind, und gibt dann die resultierende Dialogfeld Vorlage zurück.

Überschreiben Sie diese Funktion, um das Erstellen eines Dialog Felds, das ActiveX-Steuerelemente hostet, anzupassen.

##  <a name="postcreatedialog"></a>COccManager::P ostkreatedialog

Wird von Framework aufgerufen, um für die Dialogfeld Vorlage zugeordnete Arbeitsspeicher freizugeben.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parameter

*poccdialoginfo*<br/>
Eine `_AFX_OCC_DIALOG_INFO` Struktur, die Informationen über die Dialogfeld Vorlage und alle vom Dialogfeld gehosteten ActiveX-Steuerelemente enthält.

### <a name="remarks"></a>Hinweise

Dieser Arbeitsspeicher wurde durch einen aufzurufenden `SplitDialogTemplate`zugeordnet und für alle gehosteten ActiveX-Steuerelemente im Dialogfeld verwendet.

Überschreiben Sie diese Funktion, um den Prozess der Bereinigung von Ressourcen anzupassen, die vom Dialogfeld Objekt verwendet werden.

##  <a name="setdefaultbutton"></a>COccManager:: setDefaultButton

Mit dieser Funktion können Sie das Steuerelement als Standard Schaltfläche festlegen.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Ein Zeiger auf das Fenster, das das Steuerelement enthält.

*bdefault*<br/>
Ungleich NULL, wenn das Steuerelement die Standard Schaltfläche werden soll. andernfalls NULL.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

> [!NOTE]
>  Für das-Steuerelement muss das OLEMISC_ACTSLIKEBUTTON Statusbit festgelegt sein. Weitere Informationen zu OLEMISC-Flags finden Sie im Thema zu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) in der Windows SDK.

##  <a name="splitdialogtemplate"></a>COccManager:: splitdialogtemplate

Wird von Framework aufgerufen, um die ActiveX-Steuerelemente von allgemeinen Dialogfeld Steuerelementen aufzuteilen.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Parameter

*pTemplate*<br/>
Ein Zeiger auf die Dialogfeld Vorlage, die überprüft werden soll.

*ppoledlgitems*<br/>
Eine Liste von Zeigern auf Dialogfeld Elemente, die ActiveX-Steuerelemente sind.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Dialogfeld Vorlagen Struktur, die nur nicht-ActiveX-Steuerelemente enthält. Wenn keine ActiveX-Steuerelemente vorhanden sind, wird NULL zurückgegeben.

### <a name="remarks"></a>Hinweise

Wenn ActiveX-Steuerelemente gefunden werden, wird die Vorlage analysiert, und es wird eine neue Vorlage erstellt, die nur nicht-ActiveX-Steuerelemente enthält. Alle ActiveX-Steuerelemente, die während dieses Vorgangs gefunden werden, werden *ppoledlgitems*hinzugefügt.

Wenn in der Vorlage keine ActiveX-Steuerelemente vorhanden sind, wird NULL zurückgegeben *.*

> [!NOTE]
>  Der für die neue Vorlage zugewiesene Arbeitsspeicher wird in der `PostCreateDialog`-Funktion freigegeben.

Überschreiben Sie diese Funktion, um diesen Prozess anzupassen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite-Klasse](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer-Klasse](../../mfc/reference/colecontrolcontainer-class.md)
