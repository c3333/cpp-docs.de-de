---
title: Cdatarecoveryhandler-Klasse
ms.date: 03/27/2019
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
helpviewer_keywords:
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
ms.openlocfilehash: c796f24ad37b3bae11314e2885bf25e25f85aba6
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561972"
---
# <a name="cdatarecoveryhandler-class"></a>Cdatarecoveryhandler-Klasse

`CDataRecoveryHandler`Speichert Dokumente automatisch und stellt Sie wieder her, wenn eine Anwendung unerwartet beendet wird.

## <a name="syntax"></a>Syntax

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[Cdatarecoveryhandler:: cdatarecoveryhandler](#cdatarecoveryhandler)|Erstellt ein `CDataRecoveryHandler`-Objekt.|

### <a name="methods"></a>Methoden

|||
|-|-|
|[Cdatarecoveryhandler:: autosavealldocumentinfo](#autosavealldocumentinfo)|Speichert automatisch alle Dateien, die bei der-Klasse registriert sind `CDataRecoveryHandler` .|
|[Cdatarecoveryhandler:: autosavedocumentinfo](#autosavedocumentinfo)|Speichert das angegebene Dokument automatisch.|
|[Cdatarecoveryhandler:: kreatedocumentinfo](#createdocumentinfo)|Fügt der Liste der geöffneten Dokumente ein Dokument hinzu.|
|[Cdatarecoveryhandler::D eleteallautosavedfiles](#deleteallautosavedfiles)|Löscht alle aktuellen automatisch gespeicherten Dateien.|
|[Cdatarecoveryhandler::D eleteautosavedfile](#deleteautosavedfile)|Löscht die angegebene automatisch gespeicherte Datei.|
|[Cdatarecoveryhandler:: generateautosavefilename](#generateautosavefilename)|Generiert den Namen für eine Auto Speichern-Datei, die dem angegebenen Dokument Dateinamen zugeordnet ist.|
|[Cdatarecoveryhandler:: getautosaveinterval](#getautosaveinterval)|Gibt das Intervall zwischen den Auto speichern-versuchen zurück.|
|[Cdatarecoveryhandler:: getautosavepath](#getautosavepath)|Gibt den Pfad der automatisch gespeicherten Dateien zurück.|
|[Cdatarecoveryhandler:: getdocumentlistname](#getdocumentlistname)|Ruft den Dokumentnamen aus einem- `CDocument` Objekt ab.|
|[Cdatarecoveryhandler:: getnormaldocumenttitle](#getnormaldocumenttitle)|Ruft den normalen Titel für das angegebene Dokument ab.|
|[Cdatarecoveryhandler:: getrecovereddocumenttitle](#getrecovereddocumenttitle)|Erstellt den Titel für das wiederhergestellte Dokument und gibt diesen zurück.|
|[Cdatarecoveryhandler:: getrestartidentifier](#getrestartidentifier)|Ruft den eindeutigen Neustart Bezeichner für die Anwendung ab.|
|[Cdatarecoveryhandler:: getsavedocumentinfoonidle](#getsavedocumentinfoonidle)|Gibt an, ob der `CDataRecoveryHandler` eine automatische Speicherung in der aktuellen Leerlauf Schleife ausführt.|
|[Cdatarecoveryhandler:: getshutdownbyrestartmanager](#getshutdownbyrestartmanager)|Gibt an, ob der Neustart-Manager das Beenden der Anwendung bewirkt hat.|
|[Cdatarecoveryhandler:: Initialize](#initialize)|Initialisiert das `CDataRecoveryHandler`.|
|[Cdatarecoveryhandler:: queryrestoreautosaveddocuments](#queryrestoreautosaveddocuments)|Zeigt dem Benutzer ein Dialogfeld für jedes Dokument an, das `CDataRecoveryHandler` automatisch gespeichert wurde. Das Dialogfeld bestimmt, ob der Benutzer das automatisch gespeicherte Dokument wiederherstellen möchte.|
|[Cdatarecoveryhandler:: Read opendocumentlist](#readopendocumentlist)|Lädt die Liste der geöffneten Dokumente aus der Registrierung.|
|[Cdatarecoveryhandler:: removedocumentinfo](#removedocumentinfo)|Entfernt das angegebene Dokument aus der Liste der geöffneten Dokumente.|
|[Cdatarecoveryhandler:: reopenpreviousdocuments](#reopenpreviousdocuments)|Öffnet die zuvor geöffneten Dokumente.|
|[Cdatarecoveryhandler:: restoreautosaveddocuments](#restoreautosaveddocuments)|Stellt die automatisch gespeicherten Dokumente auf der Grundlage von Benutzereingaben wieder her.|
|[Cdatarecoveryhandler:: saveopendocumentlist](#saveopendocumentlist)|Speichert die aktuelle Liste der geöffneten Dokumente in der Windows-Registrierung.|
|[Cdatarecoveryhandler:: s.](#setautosaveinterval)|Legt die Zeit zwischen den Auto Speichern-Zyklen in Millisekunden fest.|
|[Cdatarecoveryhandler:: stautosavepath](#setautosavepath)|Legt das Verzeichnis fest, in dem automatisch gespeicherte Dateien gespeichert werden.|
|[Cdatarecoveryhandler:: abtrestartidentifier](#setrestartidentifier)|Legt den eindeutigen Neustart Bezeichner für diese Instanz von fest `CDataRecoveryHandler` .|
|[Cdatarecoveryhandler:: setsavedocumentinfoonidle](#setsavedocumentinfoonidle)|Legt fest, ob die `CDataRecoveryHandler` geöffneten Dokument Informationen während des aktuellen Leerlauf Zyklen in der Windows-Registrierung speichert.|
|[Cdatarecoveryhandler:: setshutdownbyrestartmanager](#setshutdownbyrestartmanager)|Legt fest, ob das vorherige Beenden der Anwendung durch den Neustart-Manager verursacht wurde.|
|[Cdatarecoveryhandler:: updatedocumentinfo](#updatedocumentinfo)|Aktualisiert die Informationen für ein Dokument, da der Benutzer es gespeichert hat.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|m_bRestoringPreviousOpenDocs|Gibt an, ob der Datenwiederherstellungs-Handler bereits geöffnete Dokumente erneut öffnet.|
|m_bSaveDocumentInfoOnIdle|Gibt an, ob der Datenwiederherstellungs-Handler Dokumente automatisch in der nächsten Leerlauf Schleife speichert.|
|m_bShutdownByRestartManager|Gibt an, ob der Neustart-Manager bewirkt, dass die Anwendung beendet wird.|
|m_dwRestartManagerSupportFlags|Flags, die angeben, welche Unterstützung der Neustart-Manager für die Anwendung bietet.|
|m_lstAutosavesToDelete|Eine Liste automatisch gespeicherter Dateien, die nicht gelöscht wurden, als die ursprünglichen Dokumente geschlossen wurden. Wenn die Anwendung beendet wird, versucht der Neustart-Manager erneut, die Dateien zu löschen.|
|m_mapDocNameToAutosaveName|Eine Zuordnung der Dokumentnamen zu den automatisch gespeicherten Dateinamen.|
|m_mapDocNameToDocumentPtr|Eine Zuordnung der Dokumentnamen zu den [CDocument](../../mfc/reference/cdocument-class.md) -Zeigern.|
|m_mapDocNameToRestoreBool|Eine Zuordnung der Dokumentnamen zu einem booleschen Parameter, der angibt, ob das automatisch gespeicherte Dokument wieder hergestellt werden soll.|
|m_mapDocumentPtrToDocName|Eine Zuordnung der `CDocument` Zeiger auf die Dokumentnamen.|
|m_mapDocumentPtrToDocTitle|Eine Zuordnung der `CDocument` Zeiger auf die Titel des Dokuments. Diese Titel werden zum Speichern von Dateien verwendet.|
|m_nAutosaveInterval|Zeit in Millisekunden zwischen den autospart.|
|m_nTimerID|Der Bezeichner für den Auto Speichern-Timer.|
|m_strAutosavePath|Der Speicherort, an dem die automatisch gespeicherten Dokumente gespeichert werden.|
|m_strRestartIdentifier|Die Zeichen folgen Darstellung einer GUID für den Neustart-Manager.|

## <a name="remarks"></a>Bemerkungen

Der Neustart-Manager verwendet die `CDataRecoveryHandler` -Klasse, um alle geöffneten Dokumente nachzuverfolgen und Sie nach Bedarf automatisch zu speichern. Verwenden Sie die [cdatarecoveryhandler:: setsavedocumentinfoonidle](#setsavedocumentinfoonidle) -Methode, um die automatische Speicherung zu aktivieren. Diese Methode weist das `CDataRecoveryHandler` an, eine automatische Speicherung in der nächsten Leerlauf Schleife auszuführen. Der Neustart-Manager ruft auf, `SetSaveDocumentInfoOnIdle` Wenn der `CDataRecoveryHandler` eine automatische Speicherung durchführen soll.

Alle Methoden der- `CDataRecoveryHandler` Klasse sind virtuell. Überschreiben Sie die Methoden in dieser Klasse, um einen eigenen benutzerdefinierten Datenwiederherstellungs Handler zu erstellen. Instanziieren Sie keinen cdatarecoveryhandler, es sei denn, Sie erstellen einen eigenen Datenwiederherstellungs Handler oder einen Neustart-Manager. Die [CWinApp-Klasse](../../mfc/reference/cwinapp-class.md) erstellt ein- `CDataRecoveryHandler` Objekt, wie es erforderlich ist.

Bevor Sie ein-Objekt verwenden können `CDataRecoveryHandler` , muss [cdatarecoveryhandler:: Initialize](#initialize)aufgerufen werden.

Da die- `CDataRecoveryHandler` Klasse eng mit dem Neustart-Manager verbunden ist, `CDataRecoveryHandler` hängt vom globalen Parameter ab `m_dwRestartManagerSupportFlags` . Dieser Parameter bestimmt, welche Berechtigungen der Neustart-Manager hat und wie er mit der Anwendung interagiert. Wenn Sie den Neustart-Manager in eine vorhandene Anwendung integrieren möchten, müssen Sie `m_dwRestartManagerSupportFlags` den entsprechenden Wert im Konstruktor Ihrer Hauptanwendung zuweisen. Weitere Informationen zur Verwendung des Neustart-Managers finden [Sie unter Gewusst wie: Hinzufügen der Unterstützung](../../mfc/how-to-add-restart-manager-support.md)für den Neustart-Manager.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdatarecovery. h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a> Cdatarecoveryhandler:: autosavealldocumentinfo

Speichert automatisch alle Dateien, die bei der-Klasse registriert sind `CDataRecoveryHandler` .

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn `CDataRecoveryHandler` alle Dokumente gespeichert wurden. FALSE, wenn ein Dokument nicht gespeichert wurde.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt true zurück, wenn keine Dokumente gespeichert werden müssen, die gespeichert werden müssen. Es wird auch true zurückgegeben, ohne dass Dokumente gespeichert werden, wenn das Abrufen `CWinApp` `CDocManager` von oder für die Anwendung einen Fehler generiert.

Um diese Methode zu verwenden, muss entweder AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART oder AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL in festgelegt werden `m_dwRestartManagerSupportFlags` . Weitere Informationen finden [Sie unter Gewusst wie: Hinzufügen der Unterstützung für den Neustart-Manager](../../mfc/how-to-add-restart-manager-support.md).

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a> Cdatarecoveryhandler:: autosavedocumentinfo

Speichert das angegebene Dokument automatisch.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Parameter

*pdocument*\
in Ein Zeiger auf den `CDocument` , der gespeichert werden soll.

*bresetmodifiedflag*\
in TRUE gibt an, dass das `CDataRecoveryHandler` zu ändernde *pdocument* von berücksichtigt wird. FALSE gibt an, dass das Framework *pdocument* als nicht geändert ansieht. Weitere Informationen zu den Auswirkungen dieses Flags finden Sie im Abschnitt "Hinweise".

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die entsprechenden Flags festgelegt sind und *pdocument* ein gültiges `CDocument` Objekt ist.

### <a name="remarks"></a>Bemerkungen

Jedes- `CDocument` Objekt verfügt über ein Flag, das angibt, ob es seit der letzten Speicherung geändert wurde. Verwenden Sie [CDocument:: IsModified](../../mfc/reference/cdocument-class.md#ismodified) , um den Status dieses Flags zu ermitteln. Wenn ein `CDocument` seit dem letzten Speichern nicht geändert wurde, werden `AutosaveDocumentInfo` alle automatisch gespeicherten Dateien für dieses Dokument von gelöscht. Wenn sich das Dokument seit der letzten Speicherung geändert hat, wird der Benutzer vor dem Schließen aufgefordert, das Dokument zu speichern.

> [!NOTE]
> Die Verwendung von *bresetmodifiedflag* zum Ändern des Status des Dokuments in "unverändert" kann dazu führen, dass der Benutzer nicht gespeicherte Daten verliert. Wenn das Framework ein Dokument als nicht geändert betrachtet, wird der Benutzer beim Schließen nicht zum Speichern aufgefordert.

Diese Methode löst eine Ausnahme mit dem [Assert](diagnostic-services.md#assert) -Makro aus, wenn *pdocument* kein gültiges `CDocument` Objekt ist.

Um diese Methode zu verwenden, muss entweder AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART oder AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL in *m_dwRestartManagerSupportFlags*festgelegt werden.

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a> Cdatarecoveryhandler:: cdatarecoveryhandler

Erstellt ein `CDataRecoveryHandler`-Objekt.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>Parameter

*dwrestartmanagersupportflags*\
in Gibt an, welche Optionen für den Neustart-Manager unterstützt werden.

*nautosaveingeterval*\
in Die Zeit zwischen den autospeicherungen. Dieser Parameter ist in Millisekunden angegeben.

### <a name="remarks"></a>Bemerkungen

Das MFC-Framework erstellt automatisch ein- `CDataRecoveryHandler` Objekt für die Anwendung, wenn Sie den Assistenten für **neue Projekte** verwenden. Sie sollten kein-Objekt erstellen, es sei denn, Sie passen das Daten Wiederherstellungs Verhalten oder den Neustart-Manager an `CDataRecoveryHandler` .

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a> Cdatarecoveryhandler:: kreatedocumentinfo

Fügt der Liste der geöffneten Dokumente ein Dokument hinzu.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parameter

*pdocument*\
in Ein Zeiger auf einen `CDocument` . Diese Methode erstellt die Dokument Informationen für dieses `CDocument` .

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt true zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode überprüft, ob *pdocument* bereits in der Liste der Dokumente vorhanden ist, bevor das Dokument hinzugefügt wird. Wenn sich *pdocument* bereits in der Liste befindet, löscht diese Methode die automatisch gespeicherte Datei, die *pdocument*zugeordnet ist.

Um diese Methode zu verwenden, muss entweder AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART oder AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL in *m_dwRestartManagerSupportFlags*festgelegt werden.

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a> Cdatarecoveryhandler::D eleteallautosavedfiles

Löscht alle aktuellen automatisch gespeicherten Dateien.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt immer true zurück.

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a> Cdatarecoveryhandler::D eleteautosavedfile

Löscht die angegebene automatisch gespeicherte Datei.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Parameter

*"strauautosavedfile"*\
in Eine Zeichenfolge, die den automatisch gespeicherten Dateinamen enthält.

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt immer true zurück.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode die automatisch gespeicherte Datei nicht löschen kann, speichert Sie den Namen der Datei in einer Liste. Der Dekonstruktor für den `CDataRecoveryHandler` versucht, jede automatisch gespeicherte Datei zu löschen, die in der Liste angegeben ist.

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a> Cdatarecoveryhandler:: generateautosavefilename

Generiert den Namen für eine Auto Speichern-Datei, die dem angegebenen Dokument Dateinamen zugeordnet ist.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Parameter

*"Name"*<br/>
in Eine Zeichenfolge, die den Dokumentnamen enthält. `GenerateAutosaveFileName` verwendet diesen Dokumentnamen, um einen entsprechenden Auto Speichern-Dateinamen zu generieren.

### <a name="return-value"></a>Rückgabewert

Der Name der Auto Speichern-Datei, *der aus dem Namen "*" von "

### <a name="remarks"></a>Bemerkungen

Jeder Dokument Name hat eine eins-zu-Eins-Zuordnung mit einem Auto Speichern-Dateinamen.

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a> Cdatarecoveryhandler:: getautosaveinterval

Gibt das Intervall zwischen den Auto speichern-versuchen zurück.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Millisekunden zwischen den Auto speichern-versuchen.

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a> Cdatarecoveryhandler:: getautosavepath

Gibt den Pfad der automatisch gespeicherten Dateien zurück.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Rückgabewert

Der Speicherort, an dem die automatisch gespeicherten Dokumente gespeichert werden.

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a> Cdatarecoveryhandler:: getdocumentlistname

Ruft den Dokumentnamen aus einem- `CDocument` Objekt ab.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Parameter

*pdocument*\
in Ein Zeiger auf einen `CDocument` . `GetDocumentListName` Ruft den Dokumentnamen aus diesem ab `CDocument` .

### <a name="return-value"></a>Rückgabewert

Der Dokument Name aus *pdocument*.

### <a name="remarks"></a>Bemerkungen

Der `CDataRecoveryHandler` verwendet den Dokumentnamen als Schlüssel in *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*und *m_mapDocNameToRestoreBool*. Dieser Parameter ermöglicht das `CDataRecoveryHandler` Überwachen von `CDocument` Objekten, den Namen der Auto Speichern-Datei und die Einstellungen für die automatische Speicherung.

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a> Cdatarecoveryhandler:: getnormaldocumenttitle

Ruft den normalen Titel für das angegebene Dokument ab.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Parameter

*pdocument*\
in Ein Zeiger auf einen `CDocument` .

### <a name="return-value"></a>Rückgabewert

Der normale Titel für das angegebene Dokument.

### <a name="remarks"></a>Bemerkungen

Der normale Titel eines Dokuments ist normalerweise der Dateiname des Dokuments ohne den Pfad. Dies ist der Titel im Feld **Dateiname** des Dialog Felds **Speichern** unter.

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a> Cdatarecoveryhandler:: getrecovereddocumenttitle

Erstellt den Titel für das wiederhergestellte Dokument und gibt diesen zurück.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Parameter

*"Strauch Titel"*<br/>
in Der normale Titel des Dokuments.

### <a name="return-value"></a>Rückgabewert

Der wiederhergestellte Dokumenttitel.

### <a name="remarks"></a>Bemerkungen

Standardmäßig ist der wiederhergestellte Titel eines Dokuments der normale Titel, an den **[wieder hergestellt]** angehängt ist. Der wiederhergestellte Titel wird dem Benutzer angezeigt, wenn der den `CDataRecoveryHandler` Benutzer abfragt, um automatisch gespeicherte Dokumente wiederherzustellen.

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a> Cdatarecoveryhandler:: getrestartidentifier

Ruft den eindeutigen Neustart Bezeichner für die Anwendung ab.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Rückgabewert

Der eindeutige Neustart Bezeichner.

### <a name="remarks"></a>Bemerkungen

Der Neustart Bezeichner ist für jede Ausführung der Anwendung eindeutig.

`CDataRecoveryHandler`Speichert Informationen zu den derzeit geöffneten Dokumenten in der Registrierung. Wenn der Neustart-Manager eine Anwendung beendet und neu startet, wird der Neustart Bezeichner für die bereitgestellt `CDataRecoveryHandler` . `CDataRecoveryHandler`Verwendet den Neustart Bezeichner, um die Liste der zuvor geöffneten Dokumente abzurufen. Dadurch kann der `CDataRecoveryHandler` versuchen, automatisch gespeicherte Dateien zu suchen und wiederherzustellen.

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a> Cdatarecoveryhandler:: getsavedocumentinfoonidle

Gibt an, ob der `CDataRecoveryHandler` eine automatische Speicherung in der aktuellen Leerlauf Schleife ausführt.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt `CDataRecoveryHandler` an, dass die automatische Speicherung der aktuellen Leerlauf Schleife ist. FALSE gibt an, dass dies nicht möglich ist.

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a> Cdatarecoveryhandler:: getshutdownbyrestartmanager

Gibt an, ob der Neustart-Manager das Beenden der Anwendung bewirkt hat.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager das Beenden der Anwendung bewirkt hat. FALSE gibt an, dass dies nicht möglich war.

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a> Cdatarecoveryhandler:: Initialize

Initialisiert das `CDataRecoveryHandler`.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Initialisierung erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Der Initialisierungs Prozess lädt den Pfad zum Speichern von Dateien für das automatische Speichern aus der Registrierung. Wenn die `Initialize` Methode dieses Verzeichnis nicht finden kann oder der Pfad NULL ist, `Initialize` schlägt fehl und gibt zurück `FALSE` .

Verwenden Sie [cdatarecoveryhandler:: setautosavepath](#setautosavepath) , um den Pfad für die automatische Speicherung zu ändern, nachdem die Anwendung die initialisiert hat `CDataRecoveryHandler` .

Die- `Initialize` Methode startet außerdem einen Timer, um zu überwachen, wann die nächste automatische Speicherung auftritt. Verwenden Sie [cdatarecoveryhandler:: setautosaveinterval](#setautosaveinterval) , um das Intervall für die automatische Speicherung zu ändern, nachdem die Anwendung die initialisiert hat `CDataRecoveryHandler` .

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a> Cdatarecoveryhandler:: queryrestoreautosaveddocuments

Zeigt dem Benutzer ein Dialogfeld für jedes Dokument an, das `CDataRecoveryHandler` automatisch gespeichert wurde. Das Dialogfeld bestimmt, ob der Benutzer das automatisch gespeicherte Dokument wiederherstellen möchte.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Anwendung Unicode ist, zeigt diese Methode einen [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) für den Benutzer an. Andernfalls verwendet das Framework [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) , um den Benutzer abzufragen.

Nachdem `QueryRestoreAutosavedDocuments` alle Antworten vom Benutzer erfasst wurden, werden die Informationen in der Element Variablen *m_mapDocNameToRestoreBool*gespeichert. Diese Methode stellt die automatisch gespeicherten Dokumente nicht wieder her.

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a> Cdatarecoveryhandler:: Read opendocumentlist

Lädt die Liste der geöffneten Dokumente aus der Registrierung.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass `ReadOpenDocumentList` die Informationen für mindestens ein Dokument aus der Registrierung geladen hat. FALSE gibt an, dass keine Dokument Informationen geladen wurden.

### <a name="remarks"></a>Bemerkungen

Diese Funktion lädt die geöffneten Dokument Informationen aus der Registrierung und speichert Sie in der Element Variablen *m_mapDocNameToAutosaveName*.

Nachdem `ReadOpenDocumentList` alle Daten geladen wurden, werden die Dokument Informationen aus der Registrierung gelöscht.

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a> Cdatarecoveryhandler:: removedocumentinfo

Entfernt das angegebene Dokument aus der Liste der geöffneten Dokumente.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parameter

*pdocument*\
in Ein Zeiger auf das Dokument, das entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

"True", wenn " *pdocument* " aus der Liste entfernt wurde. FALSE, wenn ein Fehler aufgetreten ist.

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer ein Dokument schließt, verwendet das Framework diese Methode, um es aus der Liste der geöffneten Dokumente zu entfernen.

Wenn `RemoveDocumentInfo` *pdocument* nicht in der Liste der geöffneten Dokumente gefunden werden kann, wird keine Aktion durchführt, und es wird true zurückgegeben.

Um diese Methode verwenden zu können, müssen AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES in *m_dwRestartManagerSupportFlags*festgelegt werden.

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a> Cdatarecoveryhandler:: reopenpreviousdocuments

Öffnet die zuvor geöffneten Dokumente.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn mindestens ein Dokument geöffnet wurde. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode öffnet das aktuellste Speichern der zuvor geöffneten Dokumente. Wenn ein Dokument nicht gespeichert oder automatisch gespeichert wurde, `ReopenPreviousDocuments` öffnet ein leeres Dokument auf der Grundlage der Vorlage für diesen Dateityp.

Um diese Methode verwenden zu können, müssen AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES in *m_dwRestartManagerSupportFlags*festgelegt werden. Wenn dieser Parameter nicht festgelegt ist, `ReopenPreviousDocuments` führt keine Aktion aus und gibt false zurück.

Wenn in der Liste der zuvor geöffneten Dokumente keine Dokumente gespeichert sind, führt keine Aktion aus `ReopenPreviousDocuments` und gibt false zurück.

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a> Cdatarecoveryhandler:: restoreautosaveddocuments

Stellt die automatisch gespeicherten Dokumente auf der Grundlage von Benutzereingaben wieder her.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode die Dokumente erfolgreich wiederherstellt.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode wird [cdatarecoveryhandler:: queryrestoreautosaveddocuments](#queryrestoreautosaveddocuments) aufgerufen, um zu bestimmen, welche Dokumente der Benutzer wiederherstellen möchte. Wenn ein Benutzer entscheidet, ein automatisch gespeichertes Dokument nicht wiederherzustellen, `RestoreAutosavedDocuments` Löscht die Datei automatisch speichern. Andernfalls `RestoreAutosavedDocuments` ersetzt das geöffnete Dokument durch die automatisch gespeicherte Version.

Um diese Methode zu verwenden, muss entweder AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES oder AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES in festgelegt werden `m_dwRestartManagerSupportFlags` .

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a> Cdatarecoveryhandler:: saveopendocumentlist

Speichert die aktuelle Liste der geöffneten Dokumente in der Windows-Registrierung.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn keine geöffneten Dokumente zum Speichern vorhanden sind oder wenn Sie erfolgreich gespeichert wurden. FALSE, wenn in der Registrierung Dokumente gespeichert werden sollen, die jedoch nicht gespeichert wurden, weil ein Fehler aufgetreten ist.

### <a name="remarks"></a>Bemerkungen

Der Neustart-Manager ruft `SaveOpenDocumentList` auf, wenn die Anwendung unerwartet beendet wird oder wenn Sie für ein Upgrade beendet wird. Wenn die Anwendung neu gestartet wird, wird [cdatarecoveryhandler:: Read opendocumentlist](#readopendocumentlist) verwendet, um die Liste der geöffneten Dokumente abzurufen.

Diese Methode speichert nur die Liste der geöffneten Dokumente. Die Methode [cdatarecoveryhandler:: autosavedocumentinfo](#autosavedocumentinfo) ist für das Speichern der Dokumente selbst verantwortlich.

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a> Cdatarecoveryhandler:: s.

Legt die Zeit zwischen den Auto Speichern-Zyklen in Millisekunden fest.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Parameter

*nautosaveingeterval*<br/>
in Das neue automatische Speicher Intervall in Millisekunden.

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a> Cdatarecoveryhandler:: stautosavepath

Legt das Verzeichnis fest, in dem automatisch gespeicherte Dateien gespeichert werden.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Parameter

*"stranautosavepath"*\
in Der Pfad, in dem Auto Speichern-Dateien gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Wenn Sie das Verzeichnis "Auto Speichern" ändern, werden die derzeit automatisch gespeicherten Dateien nicht verschoben.

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a> Cdatarecoveryhandler:: abtrestartidentifier

Legt den eindeutigen Neustart Bezeichner für diese Instanz von fest `CDataRecoveryHandler` .

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Parameter

*"ertifizierer"*\
in Der eindeutige Bezeichner für den Neustart-Manager.

### <a name="remarks"></a>Bemerkungen

Der Neustart-Manager zeichnet Informationen zu den geöffneten Dokumenten in der Registrierung auf. Diese Informationen werden mit dem eindeutigen Neustart Bezeichner als Schlüssel gespeichert. Da der Neustart Bezeichner für jede Instanz einer Anwendung eindeutig ist, können mehrere Instanzen einer Anwendung unerwartet beendet werden, und der Neustart-Manager kann die einzelnen Instanzen einer Anwendung wiederherstellen.

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a> Cdatarecoveryhandler:: setsavedocumentinfoonidle

Legt fest, ob die `CDataRecoveryHandler` geöffneten Dokument Informationen während des aktuellen Leerlauf Zyklen in der Windows-Registrierung speichert.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Parameter

*bsaveonidle*\
in "True", um Dokument Informationen während des aktuellen Leerlauf Zyklen zu speichern. FALSE, um keine Speicherung auszuführen.

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a> Cdatarecoveryhandler:: setshutdownbyrestartmanager

Legt fest, ob das vorherige Beenden der Anwendung durch den Neustart-Manager verursacht wurde.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Parameter

*bshutdownbyrestartmanager*\
in TRUE, um anzugeben, dass der Neustart-Manager das Beenden der Anwendung bewirkt hat. FALSE gibt an, dass die Anwendung aus einem anderen Grund beendet wurde.

### <a name="remarks"></a>Bemerkungen

Das Framework verhält sich unterschiedlich, je nachdem, ob der vorherige Exit-Vorgang unerwartet war oder ob er vom Neustart-Manager initiiert wurde.

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a> Cdatarecoveryhandler:: updatedocumentinfo

Aktualisiert die Informationen für ein Dokument, da der Benutzer es gespeichert hat.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parameter

*pdocument*\
in Ein Zeiger auf das gespeicherte Dokument.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode das automatisch gespeicherte Dokument gelöscht und die Dokument Informationen aktualisiert hat. FALSE, wenn ein Fehler aufgetreten ist.

### <a name="remarks"></a>Bemerkungen

Wenn ein Benutzer ein Dokument speichert, wird die automatisch gespeicherte Datei von der Anwendung entfernt, da Sie nicht mehr benötigt wird. `UpdateDocumentInfo` Löscht die automatisch gespeicherte Datei durch Aufrufen von [cdatarecoveryhandler:: removedocumentinfo](#removedocumentinfo). `UpdateDocumentInfo` fügt dann die Informationen aus *pdocument* der Liste der derzeit geöffneten Dokumente hinzu `RemoveDocumentInfo` , da diese Informationen von gelöscht werden, das gespeicherte Dokument jedoch weiterhin geöffnet ist.

Um diese Methode verwenden zu können, müssen AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES in *m_dwRestartManagerSupportFlags*festgelegt werden.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Vorgehensweise: Hinzufügen der Unterstützung für Neustart-Manager](../../mfc/how-to-add-restart-manager-support.md)
