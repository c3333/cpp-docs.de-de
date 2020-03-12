---
title: Klasse von "-Klasse"
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
ms.openlocfilehash: 2854d0902700b268383eca094bed35843ea73272
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864995"
---
# <a name="catlservicemodulet-class"></a>Klasse von "-Klasse"

Diese Klasse implementiert einen Dienst.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die von `CAtlServiceModuleT`abgeleitete Klasse.

*nServiceNameID*<br/>
Der Ressourcen Bezeichner des Dienstanbieter.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|-Name|Beschreibung|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|-Name|Beschreibung|
|----------|-----------------|
|["-Klasse": Handler](#handler)|Die Handlerroutine für den Dienst.|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Stellt die Standard Sicherheitseinstellungen für den-Dienst bereit.|
|["-Installations Dienst Module":](#install)|Installiert und erstellt den-Dienst.|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Bestätigt, dass der Dienst installiert wurde.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Schreibt in das Ereignisprotokoll.|
|["": OnContinue](#oncontinue)|Überschreiben Sie diese Methode, um den Dienst fortzusetzen.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Überschreiben Sie diese Methode, um den Dienst abzuhören.|
|[CAtlServiceModuleT::OnPause](#onpause)|Überschreiben Sie diese Methode, um den Dienst anzuhalten.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Überschreiben Sie diese Methode, um den Dienst zu beenden.|
|[CAtlServiceModuleT::OnStop](#onstop)|Überschreiben Sie diese Methode, um den Dienst zu verhindern.|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Überschreiben Sie diese Methode, um unbekannte Anforderungen an den Dienst zu verarbeiten.|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analysiert die Befehlszeile und führt ggf. eine Registrierung durch.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Diese Methode wird unmittelbar vor der Eingabe der Nachrichten Schleife aufgerufen.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Registriert den Dienst in der Registrierung.|
|["": Run](#run)|Führt den Dienst aus.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Die vom Dienststeuerungs-Manager aufgerufene Methode.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Aktualisiert den Dienststatus.|
|[CAtlServiceModuleT::Start](#start)|Wird von `CAtlServiceModuleT::WinMain` aufgerufen, wenn der Dienst gestartet wird.|
|[CAtlServiceModuleT::Uninstall](#uninstall)|Beendet den Dienst und entfernt ihn.|
|[CAtlServiceModuleT::Unlock](#unlock)|Verringert die Sperrenanzahl des dienstanschlusses.|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Entfernt den Dienst aus der Registrierung.|
|[CAtlServiceModuleT::WinMain](#winmain)|Diese Methode implementiert den Code, der zum Ausführen des Dienstanbieter erforderlich ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Flag, das angibt, dass das Programm als Dienst ausgeführt wird.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Die Element Variable, die den Thread Bezeichner speichert.|
|["": M_hServiceStatus](#m_hservicestatus)|Member-Variable, die ein Handle für die Status Informationsstruktur für den aktuellen Dienst speichert.|
|["": M_status](#m_status)|Member-Variable, die die Status Informationsstruktur für den aktuellen Dienst speichert.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Der Name des Dienstanbieter, der registriert wird.|

## <a name="remarks"></a>Hinweise

`CAtlServiceModuleT`, abgeleitet von [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementiert ein ATL Service-Modul. `CAtlServiceModuleT` stellt Methoden für die Befehlszeilen Verarbeitung,-Installation,-Registrierung und-Entfernung bereit. Wenn zusätzliche Funktionen erforderlich sind, können diese und andere Methoden überschrieben werden.

Diese Klasse ersetzt die veraltete [CComModule-Klasse](../../atl/reference/ccommodule-class.md) , die in früheren Versionen von ATL verwendet wurde. Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

##  <a name="catlservicemodulet"></a>"" "" "" "" "".

Der Konstruktor.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Hinweise

Initialisiert die Datenmember und legt den anfänglichen Dienststatus fest.

##  <a name="handler"></a>"-Klasse": Handler

Die Handlerroutine für den Dienst.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parameter

*dwOpcode*<br/>
Ein Schalter, der den handlervorgang definiert. Weitere Informationen finden Sie in den hinweisen.

### <a name="remarks"></a>Hinweise

Dies ist der Code, der vom Dienststeuerungs-Manager (Service Control Manager, SCM) aufgerufen wird, um den Status des diensdienstanbieter abzurufen und Anweisungen wie z. b Der SCM übergibt einen Vorgangs Code, der unten dargestellt ist, an `Handler`, um anzugeben, was der Dienst tun soll.

|Vorgangs Code|Bedeutung|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Beendet den Dienst. Überschreiben Sie die [CAtlServiceModuleT::OnStop](#onstop)-Methode in atlbase.h, um das Verhalten zu ändern.|
|SERVICE_CONTROL_PAUSE|Der Benutzer wurde implementiert. Überschreiben Sie die leere Methode [CAtlServiceModuleT::OnPause](#onpause) in atlbase.h, um den Dienst anzuhalten.|
|SERVICE_CONTROL_CONTINUE|Der Benutzer wurde implementiert. Überschreiben Sie die leere Methode [CAtlServiceModuleT::OnContinue](#oncontinue) in atlbase.h, um den Dienst wieder zu starten.|
|SERVICE_CONTROL_INTERROGATE|Der Benutzer wurde implementiert. Überschreiben Sie die leere Methode [CAtlServiceModuleT::OnInterrogate](#oninterrogate) in atlbase. h, um den Dienst abzufragen.|
|SERVICE_CONTROL_SHUTDOWN|Der Benutzer wurde implementiert. Überschreiben Sie die leere Methode [CAtlServiceModuleT::OnShutdown](#onshutdown) in atlbase.h, um den Dienst herunterzufahren.|

Wenn der Vorgangscode nicht erkannt wird, wird die Methode [CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest) aufgerufen.

Ein von ATL generierter Standard Dienst verarbeitet nur die Anweisung zum Abbrechen. Wenn der SCM die Anweisung zum Abbrechen übergibt, teilt der Dienst dem SCM mit, dass das Programm beendet werden soll. Der Dienst ruft dann `PostThreadMessage` auf, um eine Nachricht zum Beenden an sich selbst zu senden. Dadurch wird die Nachrichten Schleife beendet, und der Dienst wird letztendlich geschlossen.

##  <a name="initializesecurity"></a>"Gatlservicemodulet:: InitializeSecurity"

Stellt die Standard Sicherheitseinstellungen für den-Dienst bereit.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Jede Klasse, die von `CAtlServiceModuleT` abgeleitet ist, muss diese Methode in der abgeleiteten Klasse implementieren.

Verwenden Sie die Authentifizierung auf Pkt-Ebene, die Identitätswechsel Ebene RPC_C_IMP_LEVEL_IDENTIFY und eine entsprechende Sicherheits Beschreibung, die nicht NULL ist, im `CoInitializeSecurity`aufgerufen wird.

Bei von Assistenten generierten nicht attributierten Dienstprojekten ist dies in

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

Bei attributierten Dienstprojekten ist dies Folgendes:

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>"-Installations Dienst Module":

Installiert und erstellt den-Dienst.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Hinweise

Installiert den-Dienst in der Dienststeuerungs-Manager-Datenbank (SCM) und erstellt dann das Dienst Objekt. Wenn der Dienst nicht erstellt werden konnte, wird ein Meldungs Feld angezeigt, und die Methode gibt false zurück.

##  <a name="isinstalled"></a>"Sinlservicemodulet:: isinstemamp;"

Bestätigt, dass der Dienst installiert wurde.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Dienst installiert ist, und andernfalls false.

##  <a name="logevent"></a>"": LogEvent ""

Schreibt in das Ereignisprotokoll.

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parameter

*pszFormat*<br/>
Die in das Ereignisprotokoll zu schreibende Zeichenfolge.

*...*<br/>
Optionale zusätzliche Zeichen folgen, die in das Ereignisprotokoll geschrieben werden sollen.

### <a name="remarks"></a>Hinweise

Diese Methode schreibt Details mithilfe der Report [Event](/windows/win32/api/winbase/nf-winbase-reporteventw)-Funktion in ein Ereignisprotokoll. Wenn kein Dienst ausgeführt wird, wird die Zeichenfolge an die Konsole gesendet.

##  <a name="m_bservice"></a>"": M_bService

Flag, das angibt, dass das Programm als Dienst ausgeführt wird.

```
BOOL m_bService;
```

### <a name="remarks"></a>Hinweise

Wird verwendet, um eine Dienst-exe von einer Anwendungs-exe unterscheiden.

##  <a name="m_dwthreadid"></a>"": M_dwThreadID

Element Variable, die den Thread Bezeichner des Dienstanbieter speichert.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Hinweise

Diese Variable speichert den Thread Bezeichner des aktuellen Threads.

##  <a name="m_hservicestatus"></a>"": M_hServiceStatus

Member-Variable, die ein Handle für die Status Informationsstruktur für den aktuellen Dienst speichert.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Hinweise

Die [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) -Struktur enthält Informationen zu einem Dienst.

##  <a name="m_status"></a>"": M_status

Member-Variable, die die Status Informationsstruktur für den aktuellen Dienst speichert.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Hinweise

Die [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) -Struktur enthält Informationen zu einem Dienst.

##  <a name="m_szservicename"></a>"": M_szServiceName

Der Name des Dienstanbieter, der registriert wird.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Hinweise

Eine auf NULL endenden Zeichenfolge, in der der Name des Dienstanbieter gespeichert wird.

##  <a name="oncontinue"></a>"": OnContinue

Überschreiben Sie diese Methode, um den Dienst fortzusetzen.

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>"Gatlservicemodulet:: oninterrogate"

Überschreiben Sie diese Methode, um den Dienst abzuhören.

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>"": OnPause

Überschreiben Sie diese Methode, um den Dienst anzuhalten.

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>"": OnShutdown

Überschreiben Sie diese Methode, um den Dienst zu beenden.

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>"": ""

Überschreiben Sie diese Methode, um den Dienst zu verhindern.

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>"": Onunknownrequest

Überschreiben Sie diese Methode, um unbekannte Anforderungen an den Dienst zu verarbeiten.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parameter

*dwOpcode*<br/>
Reserviert.

##  <a name="parsecommandline"></a>"Cmdlet"::P arccommandline

Analysiert die Befehlszeile und führt ggf. eine Registrierung durch.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parameter

*lpCmdLine*<br/>
Die Befehlszeile.

*pnRetCode*<br/>
Das HRESULT, das der Registrierung entspricht (sofern vorhanden).

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, oder false, wenn die in der Befehlszeile angegebene RGS-Datei nicht registriert werden konnte.

### <a name="remarks"></a>Hinweise

Analysiert die Befehlszeile und registriert oder hebt die Registrierung der angegebenen RGS-Datei bei Bedarf auf. Diese Methode [:P](../../atl/reference/catlexemodulet-class.md#parsecommandline) ruft "" "" mit "" "" "" "" "", um nach **/RegServer** und **/unregserver**zu suchen. Durch das Hinzufügen des Arguments **/Service** wird der Dienst registriert.

##  <a name="premessageloop"></a>"" ("") "", ":P remessageloop"

Diese Methode wird unmittelbar vor der Eingabe der Nachrichten Schleife aufgerufen.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Dieser Parameter wird [:P](../../atl/reference/catlexemodulet-class.md#premessageloop)an "" "" "" ".

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Methode, um benutzerdefinierten Initialisierungs Code für den Dienst hinzuzufügen.

##  <a name="registerappid"></a>"Sinlservicemodulet:: registerappid"

Registriert den Dienst in der Registrierung.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parameter

*bService*<br/>
Muss "true" sein, um als Dienst registriert werden zu können.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

##  <a name="run"></a>"": Run

Führt den Dienst aus.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der Werte sein, die im Abschnitt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) erläutert werden. Der Standardwert ist SW_HIDE.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Nachdem `Run` aufgerufen wurde, werden [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop) und [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop) aufgerufen.

##  <a name="servicemain"></a>"", "": ServiceMain

Diese Methode wird vom Dienststeuerungs-Manager aufgerufen.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parameter

*dwArgc*<br/>
Das argc-Argument.

*lpszArgv*<br/>
Das argv-Argument.

### <a name="remarks"></a>Hinweise

Wenn Sie in der Systemsteuerung die Dienst Anwendung öffnen, werden vom Dienststeuerungs-Manager (Service Control Manager, SCM) `ServiceMain` aufgerufen, der Dienst ausgewählt und auf Start.

Nachdem der SCM `ServiceMain`aufgerufen hat, muss ein Dienst dem SCM eine Handlerfunktion einräumen. Mit dieser Funktion kann der SCM den Dienststatus abrufen und bestimmte Anweisungen (z. b. anhalten oder beenden) übergeben. Anschließend wird [CAtlServiceModuleT::Run](#run) aufgerufen, um die Hauptarbeit des Dienstanbieter auszuführen. `Run` wird weiter ausgeführt, bis der Dienst beendet wird.

##  <a name="setservicestatus"></a>"Pelservicemodulet:: SetServiceStatus"

Diese Methode aktualisiert den Dienststatus.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parameter

*dwState*<br/>
Der neue Status. Mögliche Werte finden Sie unter [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) .

### <a name="remarks"></a>Hinweise

Aktualisiert die Statusinformationen des Dienststeuerungs-Managers für den-Dienst. Sie wird von [CAtlServiceModuleT::Run](#run), [CAtlServiceModuleT::ServiceMain](#servicemain) und weiteren Handlermethoden aufgerufen. Der Status wird auch in der Membervariable [CAtlServiceModuleT::m_status](#m_status) gespeichert.

##  <a name="start"></a>"": Start

Wird von `CAtlServiceModuleT::WinMain` aufgerufen, wenn der Dienst gestartet wird.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der Werte sein, die im Abschnitt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) erläutert werden.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Die Methode [CAtlServiceModuleT::WinMain](#winmain) verarbeitet jeweils die Registrierung und Installation sowie Aufgaben, die bei der Entfernung von Registrierungseinträgen und der Deinstallation des Moduls involviert sind. Wenn der Dienst ausgeführt wird, ruft `WinMain` `Start`auf.

##  <a name="uninstall"></a>"": Deinstallieren von "".

Beendet den Dienst und entfernt ihn.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Hinweise

Beendet die Ausführung des Dienstanbieter und entfernt ihn aus der Dienststeuerungs-Manager-Datenbank.

##  <a name="unlock"></a>"": Unlock

Verringert die Sperrenanzahl des dienstanschlusses.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Sperrenanzahl zurück, die für die Diagnose und das Debuggen nützlich sein kann.

##  <a name="unregisterappid"></a>"Sinlservicemodulet:: unregisterappid"

Entfernt den Dienst aus der Registrierung.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

##  <a name="winmain"></a>"": WinMain

Diese Methode implementiert den Code, der zum Starten des Dienstanbieter erforderlich ist.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der Werte sein, die im Abschnitt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) erläutert werden.

### <a name="return-value"></a>Rückgabewert

Gibt den Rückgabewert des dienstaners zurück.

### <a name="remarks"></a>Hinweise

Diese Methode verarbeitet die Befehlszeile (mit [CAtlServiceModuleT::ParseCommandLine](#parsecommandline)) und startet den Dienst (mithilfe von [CAtlServiceModuleT::Start](#start)).

## <a name="see-also"></a>Siehe auch

[CAtlExeModuleT-Klasse](../../atl/reference/catlexemodulet-class.md)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)
