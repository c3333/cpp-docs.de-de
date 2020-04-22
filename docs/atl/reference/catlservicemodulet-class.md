---
title: CAtlServiceModuleT-Klasse
ms.date: 05/06/2019
f1_keywords:
- CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::Handler
- ATLBASE/ATL::CAtlServiceModuleT::InitializeSecurity
- ATLBASE/ATL::CAtlServiceModuleT::Install
- ATLBASE/ATL::CAtlServiceModuleT::IsInstalled
- ATLBASE/ATL::CAtlServiceModuleT::LogEvent
- ATLBASE/ATL::CAtlServiceModuleT::OnContinue
- ATLBASE/ATL::CAtlServiceModuleT::OnInterrogate
- ATLBASE/ATL::CAtlServiceModuleT::OnPause
- ATLBASE/ATL::CAtlServiceModuleT::OnShutdown
- ATLBASE/ATL::CAtlServiceModuleT::OnStop
- ATLBASE/ATL::CAtlServiceModuleT::OnUnknownRequest
- ATLBASE/ATL::CAtlServiceModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlServiceModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlServiceModuleT::RegisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::Run
- ATLBASE/ATL::CAtlServiceModuleT::ServiceMain
- ATLBASE/ATL::CAtlServiceModuleT::SetServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::Start
- ATLBASE/ATL::CAtlServiceModuleT::Uninstall
- ATLBASE/ATL::CAtlServiceModuleT::Unlock
- ATLBASE/ATL::CAtlServiceModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::WinMain
- ATLBASE/ATL::CAtlServiceModuleT::m_bService
- ATLBASE/ATL::CAtlServiceModuleT::m_dwThreadID
- ATLBASE/ATL::CAtlServiceModuleT::m_hServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::m_status
- ATLBASE/ATL::CAtlServiceModuleT::m_szServiceName
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
ms.openlocfilehash: 6d1985384c2d9a324abac548f27be6be5f0cacf5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748590"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT-Klasse

Diese Klasse implementiert einen Dienst.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse `CAtlServiceModuleT`abgeleitet von .

*nServiceNameID*<br/>
Der Ressourcenbezeichner des Dienstes.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlServiceModuleT::Handler](#handler)|Die Handlerroutine für den Dienst.|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Stellt die Standardsicherheitseinstellungen für den Dienst bereit.|
|[CAtlServiceModuleT::Installieren](#install)|Installiert und erstellt den Dienst.|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Bestätigt, dass der Dienst installiert wurde.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Schreibt in das Ereignisprotokoll.|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Überschreiben Sie diese Methode, um den Dienst fortzusetzen.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Überschreiben Sie diese Methode, um den Dienst abzuhören.|
|[CAtlServiceModuleT::OnPause](#onpause)|Überschreiben Sie diese Methode, um den Dienst anzuhalten.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Überschreiben Sie diese Methode, um den Dienst herunterzufahren|
|[CAtlServiceModuleT::OnStop](#onstop)|Überschreiben Sie diese Methode, um den Dienst zu beenden|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Überschreiben Sie diese Methode, um unbekannte Anforderungen an den Dienst zu behandeln|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analysiert die Befehlszeile und führt bei Bedarf eine Registrierung durch.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Diese Methode wird unmittelbar vor dem Eingeben der Nachrichtenschleife aufgerufen.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Registriert den Dienst in der Registrierung.|
|[CAtlServiceModuleT::Ausführen](#run)|Führt den Dienst aus.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Die vom Dienststeuerungs-Manager aufgerufene Methode.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Aktualisiert den Dienststatus.|
|[CAtlServiceModuleT::Start](#start)|Wird `CAtlServiceModuleT::WinMain` aufgerufen, wenn der Dienst gestartet wird.|
|[CAtlServiceModuleT::Deinstallieren](#uninstall)|Beendet und entfernt den Dienst.|
|[CAtlServiceModuleT::Entsperren](#unlock)|Dekrementiert die Anzahl der Sperren des Dienstes.|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Entfernt den Dienst aus der Registrierung.|
|[CAtlServiceModuleT::WinMain](#winmain)|Diese Methode implementiert den Code, der zum Ausführen des Dienstes erforderlich ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Flag, das angibt, dass das Programm als Dienst ausgeführt wird.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Membervariable, die den Threadbezeichner speichert.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Membervariable, die ein Handle in der Statusinformationsstruktur für den aktuellen Dienst speichert.|
|[CAtlServiceModuleT::m_status](#m_status)|Elementvariable, die die Statusinformationsstruktur für den aktuellen Dienst speichert.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Der Name des zu registrierenden Dienstes.|

## <a name="remarks"></a>Bemerkungen

`CAtlServiceModuleT`, abgeleitet von [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementiert ein ATL-Dienstmodul. `CAtlServiceModuleT`bietet Methoden für die Befehlszeilenverarbeitung, -installation, -registrierung und -entfernung. Wenn zusätzliche Funktionen erforderlich sind, können diese und andere Methoden überschrieben werden.

Diese Klasse ersetzt die veraltete [CComModule-Klasse,](../../atl/reference/ccommodule-class.md) die in früheren Versionen von ATL verwendet wurde. Weitere Informationen finden Sie unter [ATL-Modulklassen.](../../atl/atl-module-classes.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlbase.h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a>CAtlServiceModuleT::CAtlServiceModuleT

Der Konstruktor.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert die Datenmember und legt den anfänglichen Dienststatus fest.

## <a name="catlservicemodulethandler"></a><a name="handler"></a>CAtlServiceModuleT::Handler

Die Handlerroutine für den Dienst.

```cpp
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parameter

*dwOpcode*<br/>
Ein Schalter, der den Handlervorgang definiert. Weitere Informationen finden Sie in den Anmerkungen.

### <a name="remarks"></a>Bemerkungen

Dies ist der Code, den der Service Control Manager (SCM) aufruft, um den Status des Dienstes abzurufen und Anweisungen wie Beenden oder Anhalten zu geben. Der SCM übergibt einen unten `Handler` gezeigten Vorgangscode, um anzugeben, was der Dienst tun soll.

|Betriebscode|Bedeutung|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Beendet den Dienst. Überschreiben Sie die Methode [CAtlServiceModuleT::OnStop](#onstop) in atlbase.h, um das Verhalten zu ändern.|
|SERVICE_CONTROL_PAUSE|Benutzer implementiert. Überschreiben Sie die leere Methode [CAtlServiceModuleT::OnPause](#onpause) in atlbase.h, um den Dienst anzuhalten.|
|SERVICE_CONTROL_CONTINUE|Benutzer implementiert. Überschreiben Sie die leere Methode [CAtlServiceModuleT::OnContinue](#oncontinue) in atlbase.h, um den Dienst fortzusetzen.|
|SERVICE_CONTROL_INTERROGATE|Benutzer implementiert. Überschreiben Sie die leere Methode [CAtlServiceModuleT::OnInterrogate](#oninterrogate) in atlbase.h, um den Dienst abzufragen.|
|SERVICE_CONTROL_SHUTDOWN|Benutzer implementiert. Überschreiben Sie die leere Methode [CAtlServiceModuleT::OnShutdown](#onshutdown) in atlbase.h, um den Dienst herunterzufahren.|

Wenn der Vorgangscode nicht erkannt wird, wird die Methode [CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest) aufgerufen.

Ein standardmäßiger ATL-generierter Dienst verarbeitet nur die Stop-Anweisung. Wenn der SCM die Stop-Anweisung übergibt, teilt der Dienst dem SCM mit, dass das Programm beendet werden soll. Der Dienst `PostThreadMessage` ruft dann auf, eine Quittnachricht an sich selbst zu senden. Dadurch wird die Nachrichtenschleife beendet, und der Dienst wird schließlich geschlossen.

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a>CAtlServiceModuleT::InitializeSecurity

Stellt die Standardsicherheitseinstellungen für den Dienst bereit.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Jede Klasse, die `CAtlServiceModuleT` von dieser abgeleiteten Klasse abgeleitet wird, muss diese Methode in der abgeleiteten Klasse implementieren.

Verwenden Sie die Authentifizierung auf PKT-Ebene, die Identitätswechselebene von RPC_C_IMP_LEVEL_IDENTIFY `CoInitializeSecurity`und eine entsprechende Sicherheitsbeschreibung, die nicht null ist, im Aufruf von .

Bei assistentengenerierten nicht attributierten Serviceprojekten

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

Bei zugeschriebenen Serviceprojekten würde dies

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a>CAtlServiceModuleT::Installieren

Installiert und erstellt den Dienst.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Installiert den Dienst in der SCM-Datenbank (Service Control Manager) und erstellt dann das Dienstobjekt. Wenn der Dienst nicht erstellt werden konnte, wird ein Meldungsfeld angezeigt, und die Methode gibt FALSE zurück.

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a>CAtlServiceModuleT::IsInstalled

Bestätigt, dass der Dienst installiert wurde.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Dienst installiert ist, andernfalls FALSE.

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a>CAtlServiceModuleT::LogEvent

Schreibt in das Ereignisprotokoll.

```cpp
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parameter

*pszFormat*<br/>
Die in das Ereignisprotokoll zu schreibende Zeichenfolge.

*...*<br/>
Optionale zusätzliche Zeichenfolgen, die in das Ereignisprotokoll geschrieben werden sollen.

### <a name="remarks"></a>Bemerkungen

Diese Methode schreibt Details mithilfe der Funktion [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw)in ein Ereignisprotokoll. Wenn kein Dienst ausgeführt wird, wird die Zeichenfolge an die Konsole gesendet.

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a>CAtlServiceModuleT::m_bService

Flag, das angibt, dass das Programm als Dienst ausgeführt wird.

```
BOOL m_bService;
```

### <a name="remarks"></a>Bemerkungen

Wird verwendet, um eine Service EXE von einer Application EXE zu unterscheiden.

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a>CAtlServiceModuleT::m_dwThreadID

Membervariable, die den Threadbezeichner des Dienstes speichert.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Bemerkungen

Diese Variable speichert den Threadbezeichner des aktuellen Threads.

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a>CAtlServiceModuleT::m_hServiceStatus

Membervariable, die ein Handle in der Statusinformationsstruktur für den aktuellen Dienst speichert.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Bemerkungen

Die [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) Struktur enthält Informationen zu einem Dienst.

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a>CAtlServiceModuleT::m_status

Elementvariable, die die Statusinformationsstruktur für den aktuellen Dienst speichert.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Bemerkungen

Die [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) Struktur enthält Informationen zu einem Dienst.

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a>CAtlServiceModuleT::m_szServiceName

Der Name des zu registrierenden Dienstes.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Bemerkungen

Eine null-terminierte Zeichenfolge, die den Namen des Dienstes speichert.

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a>CAtlServiceModuleT::OnContinue

Überschreiben Sie diese Methode, um den Dienst fortzusetzen.

```cpp
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a>CAtlServiceModuleT::OnInterrogate

Überschreiben Sie diese Methode, um den Dienst abzuhören.

```cpp
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a>CAtlServiceModuleT::OnPause

Überschreiben Sie diese Methode, um den Dienst anzuhalten.

```cpp
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a>CAtlServiceModuleT::OnShutdown

Überschreiben Sie diese Methode, um den Dienst herunterzufahren.

```cpp
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a>CAtlServiceModuleT::OnStop

Überschreiben Sie diese Methode, um den Dienst zu beenden.

```cpp
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a>CAtlServiceModuleT::OnUnknownRequest

Überschreiben Sie diese Methode, um unbekannte Anforderungen an den Dienst zu verarbeiten.

```cpp
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parameter

*dwOpcode*<br/>
Reserviert.

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlServiceModuleT::ParseCommandLine

Analysiert die Befehlszeile und führt bei Bedarf eine Registrierung durch.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parameter

*lpCmdLine*<br/>
Die Befehlszeile.

*pnRetCode*<br/>
Das der Registrierung entsprechende HRESULT (falls dies der Ort in Kraft war).

### <a name="return-value"></a>Rückgabewert

Gibt true bei Erfolg oder false zurück, wenn die in der Befehlszeile angegebene RGS-Datei nicht registriert werden konnte.

### <a name="remarks"></a>Bemerkungen

Analysiert die Befehlszeile und registriert die mitgelieferte RGS-Datei bei Bedarf oder entfällt. Diese Methode ruft [CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline) auf, um nach **/RegServer** und **/UnregServer**zu suchen. Durch Hinzufügen des Arguments **-/Service** wird der Dienst registriert.

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlServiceModuleT::PreMessageLoop

Diese Methode wird unmittelbar vor dem Eingeben der Nachrichtenschleife aufgerufen.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Dieser Parameter wird an [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop)übergeben.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um benutzerdefinierten Initialisierungscode für den Dienst hinzuzufügen.

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a>CAtlServiceModuleT::RegisterAppId

Registriert den Dienst in der Registrierung.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parameter

*bService*<br/>
Muss wahr sein, um sich als Dienst registrieren zu können.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catlservicemoduletrun"></a><a name="run"></a>CAtlServiceModuleT::Ausführen

Führt den Dienst aus.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der im [WinMain-Abschnitt](/windows/win32/api/winbase/nf-winbase-winmain) beschriebenen Werte sein. Der Standardwert ist SW_HIDE.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Nach dem `Run` Aufruf ruft [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)und [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a>CAtlServiceModuleT::ServiceMain

Diese Methode wird vom Dienststeuerungs-Manager aufgerufen.

```cpp
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parameter

*dwArgc*<br/>
Das argc-Argument.

*lpszArgv*<br/>
Das argv-Argument.

### <a name="remarks"></a>Bemerkungen

Der Service Control Manager (SCM) ruft auf, `ServiceMain` wenn Sie die Services-Anwendung in der Systemsteuerung öffnen, den Dienst auswählen und auf Start klicken.

Nach dem SCM-Aufrufe `ServiceMain`muss ein Dienst dem SCM eine Handlerfunktion zuweisen. Mit dieser Funktion kann der SCM den Status des Dienstes abrufen und bestimmte Anweisungen (z. B. Anhalten oder Anhalten) übergeben. Anschließend wird [CAtlServiceModuleT::Run](#run) aufgerufen, um die Hauptarbeit des Dienstes auszuführen. `Run`wird ausgeführt, bis der Dienst beendet wird.

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a>CAtlServiceModuleT::SetServiceStatus

Diese Methode aktualisiert den Dienststatus.

```cpp
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parameter

*dwState*<br/>
Der neue Status. Siehe [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) für mögliche Werte.

### <a name="remarks"></a>Bemerkungen

Aktualisiert die Statusinformationen des Dienststeuerungs-Managers für den Dienst. Es wird von [CAtlServiceModuleT::Run](#run), [CAtlServiceModuleT::ServiceMain](#servicemain) und anderen Handlermethoden aufgerufen. Der Status wird auch in der Membervariablen [CAtlServiceModuleT::m_status](#m_status)gespeichert.

## <a name="catlservicemoduletstart"></a><a name="start"></a>CAtlServiceModuleT::Start

Wird `CAtlServiceModuleT::WinMain` aufgerufen, wenn der Dienst gestartet wird.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der im [WinMain-Abschnitt](/windows/win32/api/winbase/nf-winbase-winmain) beschriebenen Werte sein.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Die [CAtlServiceModuleT::WinMain-Methode](#winmain) behandelt sowohl die Registrierung als auch die Installation sowie Aufgaben, die mit dem Entfernen von Registrierungseinträgen und der Deinstallation des Moduls verbunden sind. Wenn der Dienst `WinMain` ausgeführt `Start`wird, ruft .

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a>CAtlServiceModuleT::Deinstallieren

Beendet und entfernt den Dienst.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Beendet die Ausführung des Dienstes und entfernt ihn aus der Dienststeuerungs-Manager-Datenbank.

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a>CAtlServiceModuleT::Entsperren

Dekrementiert die Anzahl der Sperren des Dienstes.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Sperranzahl zurück, die für die Diagnose und das Debuggen nützlich sein kann.

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlServiceModuleT::UnregisterAppId

Entfernt den Dienst aus der Registrierung.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a>CAtlServiceModuleT::WinMain

Diese Methode implementiert den Code, der zum Starten des Dienstes erforderlich ist.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der im [WinMain-Abschnitt](/windows/win32/api/winbase/nf-winbase-winmain) beschriebenen Werte sein.

### <a name="return-value"></a>Rückgabewert

Gibt den Rückgabewert des Dienstes zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode verarbeitet die Befehlszeile (mit [CAtlServiceModuleT::ParseCommandLine](#parsecommandline)) und startet dann den Dienst (mit [CAtlServiceModuleT::Start](#start)).

## <a name="see-also"></a>Weitere Informationen

[CAtlExeModuleT-Klasse](../../atl/reference/catlexemodulet-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
