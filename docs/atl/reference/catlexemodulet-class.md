---
title: Klasse von "-Klasse"
ms.date: 11/04/2016
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: d37cc8e97d29cbedfeb4ba79502d44529485399f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423429"
---
# <a name="catlexemodulet-class"></a>Klasse von "-Klasse"

Diese Klasse stellt das Modul für eine Anwendung dar.

## <a name="syntax"></a>Syntax

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die von `CAtlExeModuleT`abgeleitete Klasse.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|-Name|Beschreibung|
|----------|-----------------|
|["-" "" ""](#catlexemodulet)|Der Konstruktor.|
|["" ("") ":](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|-Name|Beschreibung|
|----------|-----------------|
|["Gatlexemodulet:: InitializeCom"](#initializecom)|Initialisiert com.|
|["-Cmdlet"::P arccommandline](#parsecommandline)|Analysiert die Befehlszeile und führt ggf. eine Registrierung durch.|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Diese Methode wird unmittelbar nach Beendigung der Nachrichten Schleife aufgerufen.|
|["-":P remessageloop](#premessageloop)|Diese Methode wird unmittelbar vor der Eingabe der Nachrichten Schleife aufgerufen.|
|[' ' ' ' ' ' ' "](#registerclassobjects)|Registriert das Klassenobjekt.|
|[' ' ' ' ' "](#revokeclassobjects)|Widerruft das Klassenobjekt.|
|["": Run](#run)|Diese Methode führt Code im exe-Modul aus, um die Initialisierung auszuführen, die Nachrichten Schleife auszuführen und die Bereinigung auszuführen.|
|["": Runmessageloop](#runmessageloop)|Diese Methode führt die Nachrichten Schleife aus.|
|["Gatlexemodulet:: uninitializecom"](#uninitializecom)|Hebt die Initialisierung von com auf.|
|["": Unlock](#unlock)|Verringert die Sperrenanzahl des Moduls.|
|["": WinMain](#winmain)|Diese Methode implementiert den Code, der zum Ausführen einer exe-Datei erforderlich ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Ein Flag, das angibt, dass das Modul verzögert heruntergefahren werden muss.|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Ein Pausen Wert, mit dem sichergestellt wird, dass alle Objekte vor dem Herunterfahren freigegeben|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Ein Timeout Wert, mit dem das Entladen des Moduls verzögert wird.|

## <a name="remarks"></a>Hinweise

`CAtlExeModuleT` stellt das Modul für eine Anwendung (exe) dar und enthält Code, der das Erstellen einer exe-Datei, die Verarbeitung der Befehlszeile, das Registrieren von Klassen Objekten, das Ausführen der Nachrichten Schleife und das Bereinigen beim Beenden unterstützt.

Diese Klasse wurde entwickelt, um die Leistung zu verbessern, wenn com-Objekte auf dem exe-Server ständig erstellt und zerstört werden. Nachdem das letzte com-Objekt freigegeben wurde, wartet die exe-Datei auf eine Dauer, die durch das DataSet "-Datenelement von" [m_dwTimeOut::](#m_dwtimeout) "angegeben wird. Wenn während dieses Zeitraums keine Aktivitäten vorhanden sind (d. h., es werden keine COM-Objekte erstellt), wird der Vorgang zum Herunterfahren initiiert.

Das DataSet "-Datenelement von" " [m_bDelayShutdown](#m_bdelayshutdown) " (Daten) ist ein Flag, mit dem bestimmt wird, ob die exe den oben definierten Mechanismus verwenden soll. Wenn der Wert auf false festgelegt ist, wird das Modul sofort beendet.

Weitere Informationen zu Modulen in ATL finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

##  <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>"-" "" ""

Der Konstruktor.

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Hinweise

Wenn das exe-Modul nicht initialisiert werden konnte, wird WinMain sofort ohne weitere Verarbeitung zurückgegeben.

##  <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>"" ("") ":

Der Destruktor.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Hinweise

Gibt alle zugeordneten Ressourcen frei.

##  <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>"Gatlexemodulet:: InitializeCom"

Initialisiert com.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Diese Methode wird vom-Konstruktor aufgerufen und kann überschrieben werden, um com auf eine Weise zu initialisieren, die von der Standard Implementierung abweicht. Die Standard Implementierung ruft entweder `CoInitializeEx(NULL, COINIT_MULTITHREADED)` oder `CoInitialize(NULL)` auf, abhängig von der Projekt Konfiguration.

Das Überschreiben dieser Methode erfordert normalerweise das Überschreiben von "" "" "" " [".](#uninitializecom)

##  <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>"": M_bDelayShutdown

Ein Flag, das angibt, dass das Modul verzögert heruntergefahren werden muss.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie in der [Übersicht](../../atl/reference/catlexemodulet-class.md) zu "" ".

##  <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>"": M_dwPause

Ein Pausen Wert, der verwendet wird, um sicherzustellen, dass alle Objekte vor dem Herunterfahren

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Hinweise

Ändern Sie diesen Wert nach dem Aufruf von [CAtlExeModuleT:: InitializeCom](#initializecom) , um die Anzahl der Millisekunden festzulegen, die als Pause-Wert zum Herunterfahren des Servers verwendet wird. Der Standardwert ist 1000 Millisekunden.

##  <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>"": M_dwTimeOut

Ein Timeout Wert, mit dem das Entladen des Moduls verzögert wird.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Hinweise

Ändern Sie diesen Wert nach dem Aufruf von [CAtlExeModuleT:: InitializeCom](#initializecom) , um die Anzahl der Millisekunden zu definieren, die als Timeout Wert für das Herunterfahren des Servers verwendet werden. Der Standardwert ist 5000 Millisekunden. Weitere Informationen finden Sie in der [Übersicht](../../atl/reference/catlexemodulet-class.md) zu "" "".

##  <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>"-Cmdlet"::P arccommandline

Analysiert die Befehlszeile und führt ggf. eine Registrierung durch.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parameter

*lpCmdLine*<br/>
Die Befehlszeile, die an die Anwendung übermittelt wird.

*pnRetCode*<br/>
Das HRESULT, das der Registrierung entspricht (sofern vorhanden).

### <a name="return-value"></a>Rückgabewert

Gibt "true" zurück, wenn die Anwendung weiterhin ausgeführt werden soll, andernfalls "false".

### <a name="remarks"></a>Hinweise

Diese Methode [wird von "](#winmain) " von "" von "" mit den Befehls zeilenschaltern aufgerufen und kann überschrieben werden. Die Standard Implementierung überprüft die Befehlszeilenargumente **/RegServer** und **/UnRegServer** und führt die Registrierung oder Aufhebung der Registrierung durch.

##  <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>"-" ""-Projekt:P

Diese Methode wird unmittelbar nach Beendigung der Nachrichten Schleife aufgerufen.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Methode, um eine benutzerdefinierte Anwendungs Bereinigung auszuführen. Die Standard [Implementierung ruft "](#revokeclassobjects)" "" ".

##  <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>"-":P remessageloop

Diese Methode wird unmittelbar vor der Eingabe der Nachrichten Schleife aufgerufen.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Der als *nshowcmd* -Parameter in WinMain übergebenen Wert.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Methode, um benutzerdefinierten Initialisierungs Code für die Anwendung hinzuzufügen. Die Standard Implementierung registriert die-Klassen Objekte.

##  <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>' ' ' ' ' ' ' "

Registriert das Klassenobjekt bei OLE, damit andere Anwendungen eine Verbindung damit herstellen können.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parameter

*dwClsContext*<br/>
Gibt den Kontext an, in dem das Klassenobjekt ausgeführt werden soll. Mögliche Werte sind CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER oder CLSCTX_LOCAL_SERVER.

*dwFlags*<br/>
Bestimmt die Verbindungstypen für das-Klassenobjekt. Mögliche Werte sind REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE oder REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK S_FALSE zurück, wenn keine zu registrierende Klassen vorhanden waren, oder ein Fehler HRESULT bei einem Fehler.

##  <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>' ' ' ' ' "

Entfernt das-Klassenobjekt.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK S_FALSE zurück, wenn keine zu registrierende Klassen vorhanden waren, oder ein Fehler HRESULT bei einem Fehler.

##  <a name="catlexemoduletrun"></a><a name="run"></a>"": Run

Diese Methode führt Code im exe-Modul aus, um die Initialisierung auszuführen, die Nachrichten Schleife auszuführen und die Bereinigung auszuführen.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der Werte sein, die im Abschnitt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) erläutert werden. Der Standardwert ist SW_HIDE.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Diese Methode kann überschrieben werden. In der Praxis ist es jedoch besser, das ""-Ereignis "" zu überschreiben [: ":P remessageloop](#premessageloop)" [:P](#postmessageloop) [, "" "",](#runmessageloop)"", "".

##  <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>"": Runmessageloop

Diese Methode führt die Nachrichten Schleife aus.

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Hinweise

Diese Methode kann überschrieben werden, um das Verhalten der Nachrichten Schleife zu ändern.

##  <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>"Gatlexemodulet:: uninitializecom"

Hebt die Initialisierung von com auf.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Hinweise

Standardmäßig ruft diese Methode einfach " [dininitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) " auf und wird vom Dekonstruktor aufgerufen. Überschreiben Sie diese Methode, wenn Sie "" "" [".](#initializecom)

##  <a name="catlexemoduletunlock"></a><a name="unlock"></a>"": Unlock

Verringert die Sperrenanzahl des Moduls.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert zurück, der möglicherweise für Diagnose-oder Testzwecke nützlich ist.

##  <a name="catlexemoduletwinmain"></a><a name="winmain"></a>"": WinMain

Diese Methode implementiert den Code, der zum Ausführen einer exe-Datei erforderlich ist.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der Werte sein, die im Abschnitt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) erläutert werden.

### <a name="return-value"></a>Rückgabewert

Gibt den Rückgabewert der ausführbaren Datei zurück.

### <a name="remarks"></a>Hinweise

Diese Methode kann überschrieben werden. Wenn das Überschreiben von [CAtlExeModuleT::PreMessageLoop](#premessageloop) [CAtlExeModuleT::PostMessageLoop](#postmessageloop) [CAtlExeModuleT::RunMessageLoop](#runmessageloop) mit dieser Methode möglich, die `WinMain` Funktion zu überschreiben.

## <a name="see-also"></a>Siehe auch

[ATLDuck-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT-Klasse](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT-Klasse](../../atl/reference/catldllmodulet-class.md)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)
