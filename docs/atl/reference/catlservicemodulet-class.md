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
ms.openlocfilehash: 0985fba4e534b6e2f6efb58ed2a8685c390dd3bd
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167796"
---
# <a name="catlservicemodulet-class"></a>Klasse von "-Klasse"

Diese Klasse implementiert einen Dienst.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von `CAtlServiceModuleT`abgeleitete Klasse.

*nservicenameid*<br/>
Der Ressourcen Bezeichner des Dienstanbieter.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["" "" "" "" "".](#catlservicemodulet)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|["-Klasse": Handler](#handler)|Die Handlerroutine für den Dienst.|
|["Gatlservicemodulet:: InitializeSecurity"](#initializesecurity)|Stellt die Standard Sicherheitseinstellungen für den-Dienst bereit.|
|["-Installations Dienst Module":](#install)|Installiert und erstellt den-Dienst.|
|["Sinlservicemodulet:: isinstemamp;"](#isinstalled)|Bestätigt, dass der Dienst installiert wurde.|
|["": LogEvent ""](#logevent)|Schreibt in das Ereignisprotokoll.|
|["": OnContinue](#oncontinue)|Überschreiben Sie diese Methode, um den Dienst fortzusetzen.|
|["Gatlservicemodulet:: oninterrogate"](#oninterrogate)|Überschreiben Sie diese Methode, um den Dienst abzuhören.|
|["": OnPause](#onpause)|Überschreiben Sie diese Methode, um den Dienst anzuhalten.|
|["": OnShutdown](#onshutdown)|Überschreiben Sie diese Methode, um den Dienst zu beenden.|
|["": ""](#onstop)|Überschreiben Sie diese Methode, um den Dienst zu verhindern.|
|["": Onunknownrequest](#onunknownrequest)|Überschreiben Sie diese Methode, um unbekannte Anforderungen an den Dienst zu verarbeiten.|
|["Cmdlet"::P arccommandline](#parsecommandline)|Analysiert die Befehlszeile und führt ggf. eine Registrierung durch.|
|["" ("") "", ":P remessageloop"](#premessageloop)|Diese Methode wird unmittelbar vor der Eingabe der Nachrichten Schleife aufgerufen.|
|["Sinlservicemodulet:: registerappid"](#registerappid)|Registriert den Dienst in der Registrierung.|
|["": Run](#run)|Führt den Dienst aus.|
|["", "": ServiceMain](#servicemain)|Die vom Dienststeuerungs-Manager aufgerufene Methode.|
|["Pelservicemodulet:: SetServiceStatus"](#setservicestatus)|Aktualisiert den Dienststatus.|
|["": Start](#start)|Wird von `CAtlServiceModuleT::WinMain` aufgerufen, wenn der Dienst gestartet wird.|
|["": Deinstallieren von "".](#uninstall)|Beendet den Dienst und entfernt ihn.|
|["": Unlock](#unlock)|Verringert die Sperrenanzahl des dienstanschlusses.|
|["Sinlservicemodulet:: unregisterappid"](#unregisterappid)|Entfernt den Dienst aus der Registrierung.|
|["": WinMain](#winmain)|Diese Methode implementiert den Code, der zum Ausführen des Dienstanbieter erforderlich ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|["": M_bService](#m_bservice)|Flag, das angibt, dass das Programm als Dienst ausgeführt wird.|
|["": M_dwThreadID](#m_dwthreadid)|Die Element Variable, die den Thread Bezeichner speichert.|
|["": M_hServiceStatus](#m_hservicestatus)|Member-Variable, die ein Handle für die Status Informationsstruktur für den aktuellen Dienst speichert.|
|["": M_status](#m_status)|Member-Variable, die die Status Informationsstruktur für den aktuellen Dienst speichert.|
|["": M_szServiceName](#m_szservicename)|Der Name des Dienstanbieter, der registriert wird.|

## <a name="remarks"></a>Bemerkungen

`CAtlServiceModuleT`, abgeleitet von "" mit " [", wird](../../atl/reference/catlexemodulet-class.md)ein ATL-Dienst Modul implementiert. `CAtlServiceModuleT`stellt Methoden für die Befehlszeilen Verarbeitung,-Installation,-Registrierung und-Entfernung bereit. Wenn zusätzliche Funktionen erforderlich sind, können diese und andere Methoden überschrieben werden.

Diese Klasse ersetzt die veraltete [CComModule-Klasse](../../atl/reference/ccommodule-class.md) , die in früheren Versionen von ATL verwendet wurde. Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

["-Module"](../../atl/reference/catlmodule-class.md)

["-Modulet"](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT dient](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a>"" "" "" "" "".

Der Konstruktor.

```cpp
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert die Datenmember und legt den anfänglichen Dienststatus fest.

## <a name="catlservicemodulethandler"></a><a name="handler"></a>"-Klasse": Handler

Die Handlerroutine für den Dienst.

```cpp
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parameter

*dwopcode*<br/>
Ein Schalter, der den handlervorgang definiert. Weitere Informationen finden Sie in den hinweisen.

### <a name="remarks"></a>Bemerkungen

Dies ist der Code, der vom Dienststeuerungs-Manager (Service Control Manager, SCM) aufgerufen wird, um den Status des diensdienstanbieter abzurufen und Anweisungen wie z. b Der SCM übergibt einen Vorgangs Code, der unten dargestellt ist `Handler` , an, um anzugeben, was der Dienst tun soll.

|Vorgangs Code|Bedeutung|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Beendet den Dienst. Überschreiben Sie [die Methode "](#onstop) " in "atlbase. h", um das Verhalten zu ändern.|
|SERVICE_CONTROL_PAUSE|Der Benutzer wurde implementiert. Überschreiben Sie die [leere Methode "](#onpause) ", "", um den Dienst anzuhalten.|
|SERVICE_CONTROL_CONTINUE|Der Benutzer wurde implementiert. Überschreiben Sie die [leere Methode "](#oncontinue) " "" "" "".|
|SERVICE_CONTROL_INTERROGATE|Der Benutzer wurde implementiert. Überschreiben Sie die [leere Methode "](#oninterrogate) " in "atlbase. h", um den Dienst abzuhören.|
|SERVICE_CONTROL_SHUTDOWN|Der Benutzer wurde implementiert. Überschreiben Sie die [leere Methode "](#onshutdown) ", um den Dienst herunterzufahren, in "atlbase. h".|

Wenn der Vorgangs Code nicht erkannt wird, wird [die Methode "](#onunknownrequest) " mit dem Namen "".

Ein von ATL generierter Standard Dienst verarbeitet nur die Anweisung zum Abbrechen. Wenn der SCM die Anweisung zum Abbrechen übergibt, teilt der Dienst dem SCM mit, dass das Programm beendet werden soll. Der Dienst ruft `PostThreadMessage` dann auf, um eine beendenmeldung an sich selbst zu senden. Dadurch wird die Nachrichten Schleife beendet, und der Dienst wird letztendlich geschlossen.

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a>"Gatlservicemodulet:: InitializeSecurity"

Stellt die Standard Sicherheitseinstellungen für den-Dienst bereit.

```cpp
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Jede Klasse, die von `CAtlServiceModuleT` abgeleitet wird, muss diese Methode in der abgeleiteten Klasse implementieren.

Verwenden Sie die Authentifizierung auf `CoInitializeSecurity`Pkt-Ebene, die Identitätswechsel Ebene RPC_C_IMP_LEVEL_IDENTIFY und eine entsprechende Sicherheits Beschreibung, die nicht NULL ist, im-Befehl.

Bei von Assistenten generierten nicht attributierten Dienstprojekten ist dies in

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

Bei attributierten Dienstprojekten ist dies Folgendes:

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a>"-Installations Dienst Module":

Installiert und erstellt den-Dienst.

```cpp
BOOL Install() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Installiert den-Dienst in der Dienststeuerungs-Manager-Datenbank (SCM) und erstellt dann das Dienst Objekt. Wenn der Dienst nicht erstellt werden konnte, wird ein Meldungs Feld angezeigt, und die Methode gibt false zurück.

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a>"Sinlservicemodulet:: isinstemamp;"

Bestätigt, dass der Dienst installiert wurde.

```cpp
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Dienst installiert ist, und andernfalls false.

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a>"": LogEvent ""

Schreibt in das Ereignisprotokoll.

```cpp
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parameter

*pszformat*<br/>
Die in das Ereignisprotokoll zu schreibende Zeichenfolge.

*...*<br/>
Optionale zusätzliche Zeichen folgen, die in das Ereignisprotokoll geschrieben werden sollen.

### <a name="remarks"></a>Bemerkungen

Diese Methode schreibt Details mithilfe der Report [Event](/windows/win32/api/winbase/nf-winbase-reporteventw)-Funktion in ein Ereignisprotokoll. Wenn kein Dienst ausgeführt wird, wird die Zeichenfolge an die Konsole gesendet.

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a>"": M_bService

Flag, das angibt, dass das Programm als Dienst ausgeführt wird.

```cpp
BOOL m_bService;
```

### <a name="remarks"></a>Bemerkungen

Wird verwendet, um eine Dienst-exe von einer Anwendungs-exe unterscheiden.

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a>"": M_dwThreadID

Element Variable, die den Thread Bezeichner des Dienstanbieter speichert.

```cpp
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Bemerkungen

Diese Variable speichert den Thread Bezeichner des aktuellen Threads.

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a>"": M_hServiceStatus

Member-Variable, die ein Handle für die Status Informationsstruktur für den aktuellen Dienst speichert.

```cpp
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Bemerkungen

Die [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) -Struktur enthält Informationen zu einem Dienst.

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a>"": M_status

Member-Variable, die die Status Informationsstruktur für den aktuellen Dienst speichert.

```cpp
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Bemerkungen

Die [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) -Struktur enthält Informationen zu einem Dienst.

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a>"": M_szServiceName

Der Name des Dienstanbieter, der registriert wird.

```cpp
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Bemerkungen

Eine auf NULL endenden Zeichenfolge, in der der Name des Dienstanbieter gespeichert wird.

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a>"": OnContinue

Überschreiben Sie diese Methode, um den Dienst fortzusetzen.

```cpp
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a>"Gatlservicemodulet:: oninterrogate"

Überschreiben Sie diese Methode, um den Dienst abzuhören.

```cpp
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a>"": OnPause

Überschreiben Sie diese Methode, um den Dienst anzuhalten.

```cpp
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a>"": OnShutdown

Überschreiben Sie diese Methode, um den Dienst zu beenden.

```cpp
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a>"": ""

Überschreiben Sie diese Methode, um den Dienst zu verhindern.

```cpp
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a>"": Onunknownrequest

Überschreiben Sie diese Methode, um unbekannte Anforderungen an den Dienst zu verarbeiten.

```cpp
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parameter

*dwopcode*<br/>
Reserviert.

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a>"Cmdlet"::P arccommandline

Analysiert die Befehlszeile und führt ggf. eine Registrierung durch.

```cpp
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parameter

*lpCmdLine*<br/>
Die Befehlszeile.

*pnretcode*<br/>
Das HRESULT, das der Registrierung entspricht (sofern vorhanden).

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, oder false, wenn die in der Befehlszeile angegebene RGS-Datei nicht registriert werden konnte.

### <a name="remarks"></a>Bemerkungen

Analysiert die Befehlszeile und registriert oder hebt die Registrierung der angegebenen RGS-Datei bei Bedarf auf. Diese Methode [:P](../../atl/reference/catlexemodulet-class.md#parsecommandline) ruft "" "" mit "" "" "" "" "", um nach **/RegServer** und **/unregserver**zu suchen. Durch das Hinzufügen des Arguments **/Service** wird der Dienst registriert.

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a>"" ("") "", ":P remessageloop"

Diese Methode wird unmittelbar vor der Eingabe der Nachrichten Schleife aufgerufen.

```cpp
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nshowcmd*<br/>
Dieser Parameter wird [:P](../../atl/reference/catlexemodulet-class.md#premessageloop)an "" "" "" ".

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um benutzerdefinierten Initialisierungs Code für den Dienst hinzuzufügen.

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a>"Sinlservicemodulet:: registerappid"

Registriert den Dienst in der Registrierung.

```cpp
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parameter

*bService*<br/>
Muss "true" sein, um als Dienst registriert werden zu können.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="catlservicemoduletrun"></a><a name="run"></a>"": Run

Führt den Dienst aus.

```cpp
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parameter

*nshowcmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der Werte sein, die im Abschnitt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) erläutert werden. Der Standardwert ist SW_HIDE.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Nachdem der Aufruf erfolgt `Run` ist, ruft die Datei "" auf [::P remessageloop](#premessageloop), "" [:P](../../atl/reference/catlexemodulet-class.md#postmessageloop), ["",](../../atl/reference/catlexemodulet-class.md#runmessageloop)"", "", "", "".

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a>"", "": ServiceMain

Diese Methode wird vom Dienststeuerungs-Manager aufgerufen.

```cpp
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parameter

*dwargc*<br/>
Das argc-Argument.

*lpszargv*<br/>
Das argv-Argument.

### <a name="remarks"></a>Bemerkungen

Der Dienststeuerungs-Manager (SCM) `ServiceMain` Ruft auf, wenn Sie die Anwendung Dienste in der Systemsteuerung öffnen, wählen Sie den Dienst aus, und klicken Sie auf starten.

Nachdem der SCM aufgerufen `ServiceMain`hat, muss ein Dienst dem SCM eine Handlerfunktion einräumen. Mit dieser Funktion kann der SCM den Dienststatus abrufen und bestimmte Anweisungen (z. b. anhalten oder beenden) übergeben. Anschließend wird ["](#run) " "" "" "", "", um die Hauptarbeit des Dienstanbieter auszuführen. `Run`wird weiter ausgeführt, bis der Dienst beendet wird.

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a>"Pelservicemodulet:: SetServiceStatus"

Diese Methode aktualisiert den Dienststatus.

```cpp
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parameter

*dwstate*<br/>
Der neue Status. Mögliche Werte finden Sie unter [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) .

### <a name="remarks"></a>Bemerkungen

Aktualisiert die Statusinformationen des Dienststeuerungs-Managers für den-Dienst. Sie wird von "" von "" für " [", "](#servicemain) ", "", "", "" und anderen [Handlermethoden](#run)aufgerufen. Der Status wird auch in der Element [m_status](#m_status)Variablen "",

## <a name="catlservicemoduletstart"></a><a name="start"></a>"": Start

Wird von `CAtlServiceModuleT::WinMain` aufgerufen, wenn der Dienst gestartet wird.

```cpp
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nshowcmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der Werte sein, die im Abschnitt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) erläutert werden.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Die Methode "-Methode" (Methode) übernimmt sowohl die Registrierung als [auch die Installation](#winmain) sowie die Aufgaben, die beim Entfernen von Registrierungs Einträgen und Deinstallieren des Moduls beteiligt sind. Wenn der Dienst ausgeführt wird, `WinMain` ruft `Start`auf.

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a>"": Deinstallieren von "".

Beendet den Dienst und entfernt ihn.

```cpp
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Beendet die Ausführung des Dienstanbieter und entfernt ihn aus der Dienststeuerungs-Manager-Datenbank.

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a>"": Unlock

Verringert die Sperrenanzahl des dienstanschlusses.

```cpp
LONG Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Sperrenanzahl zurück, die für die Diagnose und das Debuggen nützlich sein kann.

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a>"Sinlservicemodulet:: unregisterappid"

Entfernt den Dienst aus der Registrierung.

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a>"": WinMain

Diese Methode implementiert den Code, der zum Starten des Dienstanbieter erforderlich ist.

```cpp
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nshowcmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der Werte sein, die im Abschnitt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) erläutert werden.

### <a name="return-value"></a>Rückgabewert

Gibt den Rückgabewert des dienstaners zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode verarbeitet die Befehlszeile ( [:P](#parsecommandline)mit "" "" "" "" "" mit "" "" "" " [CAtlServiceModuleT::Start](#start).

## <a name="see-also"></a>Weitere Informationen:

[Klasse von "-Klasse"](../../atl/reference/catlexemodulet-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
