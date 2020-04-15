---
title: CDataRecoveryHandler-Klasse
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
ms.openlocfilehash: bdfcbea6c345235358384691388afcdbbd2d0a42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321929"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler-Klasse

Die `CDataRecoveryHandler` automatische Spart Dokumente und stellt sie wieder her, wenn eine Anwendung unerwartet beendet wird.

## <a name="syntax"></a>Syntax

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|Erstellt ein `CDataRecoveryHandler`-Objekt.|

### <a name="methods"></a>Methoden

|||
|-|-|
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Speichert automatisch jede Datei, die bei der `CDataRecoveryHandler` Klasse registriert ist.|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Speichert das angegebene Dokument automatisch.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Fügt der Liste der geöffneten Dokumente ein Dokument hinzu.|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Löscht alle aktuellen automatisch gespeicherten Dateien.|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Löscht die angegebene automatisch gespeicherte Datei.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Generiert den Namen für eine AutoSave-Datei, die dem angegebenen Dokumentdateinamen zugeordnet ist.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Gibt das Intervall zwischen autosave-Versuchen zurück.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Gibt den Pfad der automatisch gespeicherten Dateien zurück.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Ruft den Dokumentnamen `CDocument` aus einem Objekt ab.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Ruft den normalen Titel für das angegebene Dokument ab.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Erstellt und gibt den Titel für das wiederhergestellte Dokument zurück.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Ruft den eindeutigen Neustartbezeichner für die Anwendung ab.|
|[CDataRecoveryHandler::GetSaveDocumentInfoonIdle](#getsavedocumentinfoonidle)|Gibt an, ob der `CDataRecoveryHandler` eine automatische Speicherung auf der aktuellen Leerlaufschleife durchführt.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Gibt an, ob der Neustart-Manager den Beenden der Anwendung verursacht hat.|
|[CDataRecoveryHandler::Initialisieren](#initialize)|Initialisiert das `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Zeigt dem Benutzer für jedes Dokument, `CDataRecoveryHandler` das der autogespeicherte Dokument gespeichert hat, ein Dialogfeld an. Das Dialogfeld bestimmt, ob der Benutzer das automatisch gespeicherte Dokument wiederherstellen möchte.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Lädt die Liste der geöffneten Dokumente aus der Registrierung.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Entfernt das angegebene Dokument aus der Liste der geöffneten Dokumente.|
|[CDataRecoveryHandler::PreviousDocuments erneut öffnen](#reopenpreviousdocuments)|Öffnet die zuvor geöffneten Dokumente.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Stellt die automatisch gespeicherten Dokumente basierend auf Benutzereingaben wieder her.|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Speichert die aktuelle Liste der geöffneten Dokumente in der Windows-Registrierung.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Legt die Zeit zwischen den automatischen Speicherzyklen in Millisekunden fest.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Legt das Verzeichnis fest, in dem automatisch gespeicherte Dateien gespeichert werden.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Legt den eindeutigen Neustartbezeichner für diese Instanz der `CDataRecoveryHandler`fest.|
|[CDataRecoveryHandler::SetSaveDocumentInfoonidle](#setsavedocumentinfoonidle)|Legt fest, ob die `CDataRecoveryHandler` geöffneten Dokumentinformationen während des aktuellen Leerlaufzyklus in der Windows-Registrierung speichert werden.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Legt fest, ob der vorherige Exit der Anwendung vom Neustart-Manager verursacht wurde.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Aktualisiert die Informationen für ein Dokument, da der Benutzer sie gespeichert hat.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|m_bRestoringPreviousOpenDocs|Gibt an, ob der Datenwiederherstellungshandler zuvor geöffnete Dokumente erneut öffnet.|
|m_bSaveDocumentInfoOnIdle|Gibt an, ob der Datenwiederherstellungshandler Dokumente in der nächsten Leerlaufschleife automatisch speichert.|
|m_bShutdownByRestartManager|Gibt an, ob der Neustart-Manager bewirkt, dass die Anwendung beendet wird.|
|m_dwRestartManagerSupportFlags|Flags, die angeben, welche Unterstützung der Neustart-Manager für die Anwendung bereitstellt.|
|m_lstAutosavesToDelete|Eine Liste der automatisch gespeicherten Dateien, die beim Schließen der Originaldokumente nicht gelöscht wurden. Wenn die Anwendung beendet wird, versucht der Neustart-Manager erneut, die Dateien zu löschen.|
|m_mapDocNameToAutosaveName|Eine Zuordnung der Dokumentnamen zu den automatisch gespeicherten Dateinamen.|
|m_mapDocNameToDocumentPtr|Eine Zuordnung der Dokumentnamen [CDocument](../../mfc/reference/cdocument-class.md) zu den CDocument-Zeigern.|
|m_mapDocNameToRestoreBool|Eine Zuordnung der Dokumentnamen zu einem booleschen Parameter, der angibt, ob das automatisch gespeicherte Dokument wiederhergestellt werden soll.|
|m_mapDocumentPtrToDocName|Eine Zuordnung `CDocument` der Zeiger auf die Dokumentnamen.|
|m_mapDocumentPtrToDocTitle|Eine Karte `CDocument` der Zeiger auf die Dokumenttitel. Diese Titel werden zum Speichern von Dateien verwendet.|
|m_nAutosaveInterval|Zeit in Millisekunden zwischen Autosaves.|
|m_nTimerID|Der Bezeichner für den Autosave-Timer.|
|m_strAutosavePath|Der Speicherort, an dem die automatisch gespeicherten Dokumente gespeichert werden.|
|m_strRestartIdentifier|Die Zeichenfolgendarstellung einer GUID für den Neustart-Manager.|

## <a name="remarks"></a>Bemerkungen

Der Neustart-Manager `CDataRecoveryHandler` verwendet die Klasse, um alle geöffneten Dokumente nachzuverfolgen und bei Bedarf automatisch zu speichern. Um das automatische Speichern zu aktivieren, verwenden Sie die [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle-Methode.](#setsavedocumentinfoonidle) Diese Methode weist `CDataRecoveryHandler` die an, eine automatische Speicherung auf der nächsten Leerlaufschleife durchzuführen. Der Neustart-Manager ruft auf, `SetSaveDocumentInfoOnIdle` wenn der `CDataRecoveryHandler` eine automatische Speicherung durchführen soll.

Alle Methoden der `CDataRecoveryHandler` Klasse sind virtuell. Überschreiben Sie die Methoden in dieser Klasse, um einen eigenen benutzerdefinierten Datenwiederherstellungshandler zu erstellen. Wenn Sie keinen eigenen Datenwiederherstellungshandler oder Neustart-Manager erstellen, instanziieren Sie keinen CDataRecoveryHandler. Die [CWinApp-Klasse](../../mfc/reference/cwinapp-class.md) erstellt ein `CDataRecoveryHandler` Objekt nach Bedarf.

Bevor Sie ein `CDataRecoveryHandler` Objekt verwenden können, müssen Sie [CDataRecoveryHandler::Initialize](#initialize)aufrufen.

Da `CDataRecoveryHandler` die Klasse eng mit dem `CDataRecoveryHandler` Neustart-Manager `m_dwRestartManagerSupportFlags`verbunden ist, hängt der globale Parameter ab. Dieser Parameter bestimmt, über welche Berechtigungen der Neustart-Manager verfügt und wie er mit Ihrer Anwendung interagiert. Um den Neustart-Manager in eine vorhandene `m_dwRestartManagerSupportFlags` Anwendung zu integrieren, müssen Sie den entsprechenden Wert im Konstruktor der Hauptanwendung zuweisen. Weitere Informationen zur Verwendung des Neustart-Managers finden Sie unter [Gewusst wie: Hinzufügen des Neustart-Managers-Supports](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdatarecovery.h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo

Speichert automatisch jede Datei, die bei der `CDataRecoveryHandler` Klasse registriert ist.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Rückgabewert

TRUE, `CDataRecoveryHandler` wenn alle Dokumente gespeichert sind; FALSE, wenn kein Dokument gespeichert wurde.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt TRUE zurück, wenn keine Dokumente gespeichert werden müssen. Außerdem wird TRUE zurückgegeben, ohne Dokumente `CWinApp` `CDocManager` zu speichern, wenn das Abrufen der oder für die Anwendung einen Fehler generiert.

Um diese Methode verwenden zu können, `m_dwRestartManagerSupportFlags`müssen entweder AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART oder AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL in festgelegt werden. Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen des Neustart-Managers-Supports](../../mfc/how-to-add-restart-manager-support.md).

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo

Speichert das angegebene Dokument automatisch.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pDocument*|[in] Ein Zeiger auf `CDocument` den zu speichern.|
|*bResetModifiedFlag*|[in] TRUE gibt `CDataRecoveryHandler` an, dass das *pDocument* geändert werden soll. FALSE gibt an, dass pDocument im Rahmen *pDocument* als unverändert betrachtet wird. Weitere Informationen zu den Auswirkungen dieses Flags finden Sie im Abschnitt "Bemerkungen".|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die entsprechenden Flags gesetzt `CDocument` sind und *pDocument* ein gültiges Objekt ist.

### <a name="remarks"></a>Bemerkungen

Jedes `CDocument` Objekt verfügt über ein Flag, das angibt, ob es sich seit dem letzten Speichern geändert hat. Verwenden Sie [CDocument::IsModified,](../../mfc/reference/cdocument-class.md#ismodified) um den Status dieses Flags zu bestimmen. Wenn `CDocument` sich seit dem letzten `AutosaveDocumentInfo` Speichern keine Änderung geändert hat, werden alle automatisch gespeicherten Dateien für dieses Dokument gelöscht. Wenn sich ein Dokument seit dem letzten Speichern geändert hat, wird der Benutzer beim Schließen aufgefordert, das Dokument vor dem Schließen zu speichern.

> [!NOTE]
> Die Verwendung von *bResetModifiedFlag* zum Ändern des Status des Dokuments in unveränderte Daten kann dazu führen, dass der Benutzer nicht gespeicherte Daten verliert. Wenn das Framework ein Dokument für unverändert hält, wird der Benutzer beim Schließen nicht zum Speichern aufgefordert.

Diese Methode löst eine Ausnahme mit dem [ASSERT-Makro](diagnostic-services.md#assert) aus, wenn *pDocument* kein gültiges `CDocument` Objekt ist.

Um diese Methode verwenden zu können, müssen entweder AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART oder AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL in *m_dwRestartManagerSupportFlags*festgelegt werden.

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler

Erstellt ein `CDataRecoveryHandler`-Objekt.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*dwRestartManagerSupportFlags*|[in] Gibt an, welche Optionen des Neustart-Managers unterstützt werden.|
|*nAutosaveInterval*|[in] Die Zeit zwischen autosaves. Dieser Parameter ist in Millisekunden angegeben.|

### <a name="remarks"></a>Bemerkungen

Das MFC-Framework `CDataRecoveryHandler` erstellt automatisch ein Objekt für Ihre Anwendung, wenn Sie den Assistenten für **neues Projekt** verwenden. Wenn Sie das Datenwiederherstellungsverhalten oder den Neustart-Manager `CDataRecoveryHandler` nicht anpassen, sollten Sie kein Objekt erstellen.

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo

Fügt der Liste der geöffneten Dokumente ein Dokument hinzu.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pDocument*|[in] Ein Zeiger auf `CDocument`eine . Diese Methode erstellt die `CDocument`Dokumentinformationen für diese .|

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode überprüft, ob *pDocument* bereits in der Liste der Dokumente enthalten ist, bevor das Dokument hinzugefügt wird. Wenn *pDocument* bereits in der Liste enthalten ist, löscht diese Methode die automatisch gespeicherte Datei, die *pDocument*zugeordnet ist.

Um diese Methode verwenden zu können, müssen entweder AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART oder AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL in *m_dwRestartManagerSupportFlags*festgelegt werden.

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles

Löscht alle aktuellen automatisch gespeicherten Dateien.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt immer TRUE zurück.

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile

Löscht die angegebene automatisch gespeicherte Datei.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*strAutosavedFile*|[in] Eine Zeichenfolge, die den automatisch gespeicherten Dateinamen enthält.|

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode die automatisch gespeicherte Datei nicht löschen kann, wird der Name der Datei in einer Liste gespeichert. Der Destruktor `CDataRecoveryHandler` für den versucht, jede in dieser Liste angegebene automatisch gespeicherte Datei zu löschen.

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName

Generiert den Namen für eine AutoSave-Datei, die dem angegebenen Dokumentdateinamen zugeordnet ist.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Parameter

*strDocumentName*<br/>
[in] Eine Zeichenfolge, die den Dokumentnamen enthält. `GenerateAutosaveFileName`verwendet diesen Dokumentnamen, um einen entsprechenden AutoSave-Dateinamen zu generieren.

### <a name="return-value"></a>Rückgabewert

Der aus *strDocumentName*generierte Dateiname zum automatischen Speichern.

### <a name="remarks"></a>Bemerkungen

Jeder Dokumentname verfügt über eine 1:1-Zuordnung mit einem Autosave-Dateinamen.

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval

Gibt das Intervall zwischen autosave-Versuchen zurück.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Millisekunden zwischen den automatischen Wiedereinsparversuchen.

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath

Gibt den Pfad der automatisch gespeicherten Dateien zurück.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Rückgabewert

Der Speicherort, an dem die automatisch gespeicherten Dokumente gespeichert werden.

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName

Ruft den Dokumentnamen `CDocument` aus einem Objekt ab.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pDocument*|[in] Ein Zeiger auf `CDocument`eine . `GetDocumentListName`ruft den Dokumentnamen `CDocument`von dieser ab.|

### <a name="return-value"></a>Rückgabewert

Der Dokumentname aus *pDocument*.

### <a name="remarks"></a>Bemerkungen

Der `CDataRecoveryHandler` verwendet den Dokumentnamen als Schlüssel in *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*und *m_mapDocNameToRestoreBool*. Mit diesen `CDataRecoveryHandler` Parametern `CDocument` können Objekte, der Dateiname automatisch gespeichert und die Einstellungen für das automatische Speichern überwacht werden.

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle

Ruft den normalen Titel für das angegebene Dokument ab.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pDocument*|[in] Ein Zeiger auf `CDocument`eine .|

### <a name="return-value"></a>Rückgabewert

Der normale Titel für das angegebene Dokument.

### <a name="remarks"></a>Bemerkungen

Der normale Titel eines Dokuments ist in der Regel der Dateiname des Dokuments ohne Pfad. Dies ist der Titel im Feld **Dateiname** des Dialogfelds **Speichern** unter.

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle

Erstellt und gibt den Titel für das wiederhergestellte Dokument zurück.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Parameter

*strDocumentTitle*<br/>
[in] Der normale Titel für das Dokument.

### <a name="return-value"></a>Rückgabewert

Der wiederhergestellte Dokumenttitel.

### <a name="remarks"></a>Bemerkungen

Standardmäßig ist der wiederhergestellte Titel eines Dokuments der normale Titel, an den **[wiederhergestellt]** angehängt ist. Der wiederhergestellte Titel wird dem `CDataRecoveryHandler` Benutzer angezeigt, wenn der Benutzer die wiederhergestellten Dokumente wiederherstellt.

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier

Ruft den eindeutigen Neustartbezeichner für die Anwendung ab.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Rückgabewert

Der eindeutige Neustartbezeichner.

### <a name="remarks"></a>Bemerkungen

Der Neustartbezeichner ist für jede Ausführung der Anwendung eindeutig.

Der `CDataRecoveryHandler` speichert Informationen in der Registrierung zu den aktuell geöffneten Dokumenten. Wenn der Neustart-Manager eine Anwendung beendet und neu startet, `CDataRecoveryHandler`wird der Neustartbezeichner an die . Der `CDataRecoveryHandler` verwendet den Neustartbezeichner, um die Liste der zuvor geöffneten Dokumente abzurufen. Auf diese `CDataRecoveryHandler` Weise können Sie versuchen, automatisch gespeicherte Dateien zu finden und wiederherzustellen.

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoonIdle

Gibt an, ob der `CDataRecoveryHandler` eine automatische Speicherung auf der aktuellen Leerlaufschleife durchführt.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt `CDataRecoveryHandler` die Autosaves auf der aktuellen Leerlaufschleife an. FALSE gibt an, dass dies nicht der Fall ist.

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager

Gibt an, ob der Neustart-Manager den Beenden der Anwendung verursacht hat.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt an, dass der Neustart-Manager die Anwendung beendet hat. FALSE gibt an, dass dies nicht der Fall war.

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a>CDataRecoveryHandler::Initialisieren

Initialisiert das `CDataRecoveryHandler`.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Initialisierung erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Der Initialisierungsprozess lädt den Pfad zum Speichern von Autosave-Dateien aus der Registrierung. Wenn `Initialize` die Methode dieses Verzeichnis nicht finden `Initialize` kann oder `FALSE`wenn der Pfad NULL ist, schlägt sie fehl und gibt zurück.

Verwenden Sie [CDataRecoveryHandler::SetAutosavePath,](#setautosavepath) um den Autosave-Pfad `CDataRecoveryHandler`zu ändern, nachdem Ihre Anwendung die initialisiert hat.

Die `Initialize` Methode startet auch einen Timer, um zu überwachen, wenn die nächste automatische Speicherung erfolgt. Verwenden Sie [CDataRecoveryHandler::SetAutosaveInterval,](#setautosaveinterval) um das automatische Speicherintervall `CDataRecoveryHandler`zu ändern, nachdem Ihre Anwendung die initialisiert hat.

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Zeigt dem Benutzer für jedes Dokument, `CDataRecoveryHandler` das der autogespeicherte Dokument gespeichert hat, ein Dialogfeld an. Das Dialogfeld bestimmt, ob der Benutzer das automatisch gespeicherte Dokument wiederherstellen möchte.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Anwendung Unicode ist, zeigt diese Methode dem Benutzer einen [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) an. Andernfalls verwendet das Framework [AfxMessageBox,](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) um den Benutzer abzufragen.

Nachdem `QueryRestoreAutosavedDocuments` alle Antworten des Benutzers gesammelt wurden, werden die Informationen in der Membervariablen *m_mapDocNameToRestoreBool*gespeichert. Diese Methode stellt die automatisch gespeicherten Dokumente nicht wieder her.

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList

Lädt die Liste der geöffneten Dokumente aus der Registrierung.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Rückgabewert

TRUE gibt `ReadOpenDocumentList` an, dass die Informationen für mindestens ein Dokument aus der Registrierung geladen wurden. FALSE gibt an, dass keine Dokumentinformationen geladen wurden.

### <a name="remarks"></a>Bemerkungen

Diese Funktion lädt die geöffneten Dokumentinformationen aus der Registrierung und speichert sie in der Membervariablen *m_mapDocNameToAutosaveName*.

Nachdem `ReadOpenDocumentList` alle Daten geladen wurden, werden die Dokumentinformationen aus der Registrierung gelöscht.

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo

Entfernt das angegebene Dokument aus der Liste der geöffneten Dokumente.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pDocument*|[in] Ein Zeiger auf das zu entfernende Dokument.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn *pDocument* aus der Liste entfernt wurde; FALSE, wenn ein Fehler aufgetreten ist.

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer ein Dokument schließt, verwendet das Framework diese Methode, um es aus der Liste der geöffneten Dokumente zu entfernen.

Wenn `RemoveDocumentInfo` *pDocument* in der Liste der geöffneten Dokumente nicht gefunden werden kann, wird nichts unternommen und TRUE zurückgegeben.

Um diese Methode verwenden zu können, müssen AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES in *m_dwRestartManagerSupportFlags*festgelegt werden.

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::PreviousDocuments erneut öffnen

Öffnet die zuvor geöffneten Dokumente.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn mindestens ein Dokument geöffnet wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode öffnet die letzte Speicherung der zuvor geöffneten Dokumente. Wenn ein Dokument nicht gespeichert `ReopenPreviousDocuments` oder automatisch gespeichert wurde, wird ein leeres Dokument geöffnet, das auf der Vorlage für diesen Dateityp basiert.

Um diese Methode verwenden zu können, müssen AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES in *m_dwRestartManagerSupportFlags*festgelegt werden. Wenn dieser Parameter nicht `ReopenPreviousDocuments` festgelegt ist, tut nichts und gibt FALSE zurück.

Wenn in der Liste der zuvor geöffneten `ReopenPreviousDocuments` Dokumente keine Dokumente gespeichert sind, wird nichts unternommen und FALSE zurückgegeben.

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments

Stellt die automatisch gespeicherten Dokumente basierend auf Benutzereingaben wieder her.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode die Dokumente erfolgreich wiederherstellt.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) auf, um zu bestimmen, welche Dokumente der Benutzer wiederherstellen möchte. Wenn ein Benutzer beschließt, ein automatisch `RestoreAutosavedDocuments` gespeichertes Dokument nicht wiederherzustellen, löscht die autoSave-Datei. Ersetzt `RestoreAutosavedDocuments` andernfalls das geöffnete Dokument durch die automatisch gespeicherte Version.

Um diese Methode verwenden zu können, `m_dwRestartManagerSupportFlags`müssen entweder AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES oder AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES in festgelegt werden.

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList

Speichert die aktuelle Liste der geöffneten Dokumente in der Windows-Registrierung.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn keine geöffneten Dokumente zu speichern sind oder wenn sie erfolgreich gespeichert wurden. FALSE, wenn Dokumente in der Registrierung gespeichert werden sollen, die jedoch nicht gespeichert wurden, weil ein Fehler aufgetreten ist.

### <a name="remarks"></a>Bemerkungen

Der Neustart-Manager ruft auf, `SaveOpenDocumentList` wenn die Anwendung unerwartet beendet wird oder wenn sie für ein Upgrade beendet wird. Wenn die Anwendung neu gestartet wird, verwendet sie [CDataRecoveryHandler::ReadOpenDocumentList,](#readopendocumentlist) um die Liste der geöffneten Dokumente abzurufen.

Bei dieser Methode wird nur die Liste der geöffneten Dokumente speichert. Die Methode [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) ist für das Speichern der Dokumente selbst verantwortlich.

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval

Legt die Zeit zwischen den automatischen Speicherzyklen in Millisekunden fest.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Parameter

*nAutosaveInterval*<br/>
[in] Das neue autosave-Intervall in Millisekunden.

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath

Legt das Verzeichnis fest, in dem automatisch gespeicherte Dateien gespeichert werden.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*strAutosavePath*|[in] Der Pfad, in dem autosave-Dateien gespeichert werden.|

### <a name="remarks"></a>Bemerkungen

Durch das Ändern des Verzeichnisses zum automatischen Speichern werden derzeit nicht automatisch gespeicherte Dateien verschoben.

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier

Legt den eindeutigen Neustartbezeichner für diese Instanz der `CDataRecoveryHandler`fest.

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*strRestartIdentifier*|[in] Der eindeutige Bezeichner für den Neustart-Manager.|

### <a name="remarks"></a>Bemerkungen

Der Neustart-Manager zeichnet Informationen zu den geöffneten Dokumenten in der Registrierung auf. Diese Informationen werden mit dem eindeutigen Neustartbezeichner als Schlüssel gespeichert. Da der Neustartbezeichner für jede Instanz einer Anwendung eindeutig ist, können mehrere Instanzen einer Anwendung unerwartet beendet werden, und der Neustart-Manager kann jede dieser Instanzen wiederherstellen.

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoonidle

Legt fest, ob die `CDataRecoveryHandler` geöffneten Dokumentinformationen während des aktuellen Leerlaufzyklus in der Windows-Registrierung speichert werden.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*bSaveOnIdle*|[in] TRUE, um Dokumentinformationen während des aktuellen Leerlaufzyklus zu speichern; FALSE, um keine Speicherung durchzuführen.|

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager

Legt fest, ob der vorherige Exit der Anwendung vom Neustart-Manager verursacht wurde.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*bShutdownByRestartManager*|[in] TRUE, um anzugeben, dass der Neustart-Manager die Anwendung beendet hat. FALSE, um anzugeben, dass die Anwendung aus einem anderen Grund beendet wurde.|

### <a name="remarks"></a>Bemerkungen

Das Framework verhält sich unterschiedlich, je nach unerwartetem Unerwarteten oder vom Neustart-Manager initiiert wurde.

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo

Aktualisiert die Informationen für ein Dokument, da der Benutzer sie gespeichert hat.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pDocument*|[in] Ein Zeiger auf das gespeicherte Dokument.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode das automatisch gespeicherte Dokument gelöscht und die Dokumentinformationen aktualisiert hat. FALSE, wenn ein Fehler aufgetreten ist.

### <a name="remarks"></a>Bemerkungen

Wenn ein Benutzer ein Dokument speichert, entfernt die Anwendung die automatisch gespeicherte Datei, da sie nicht mehr benötigt wird. `UpdateDocumentInfo`löscht die automatisch gespeicherte Datei, indem [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)aufgerufen wird. `UpdateDocumentInfo`fügt dann die Informationen aus *pDocument* zur `RemoveDocumentInfo` Liste der aktuell geöffneten Dokumente hinzu, da diese Informationen gelöscht werden, das gespeicherte Dokument jedoch noch geöffnet ist.

Um diese Methode verwenden zu können, müssen AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES in *m_dwRestartManagerSupportFlags*festgelegt werden.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Vorgehensweise: Hinzufügen von Unterstützung für den Neustart-Manager](../../mfc/how-to-add-restart-manager-support.md)
