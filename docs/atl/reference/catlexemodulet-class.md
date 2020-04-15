---
title: CAtlExeModuleT-Klasse
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
ms.openlocfilehash: a20a02a467d74a89e3cda176a6a15961be4ffd61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318988"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT-Klasse

Diese Klasse stellt das Modul für eine Anwendung dar.

## <a name="syntax"></a>Syntax

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse `CAtlExeModuleT`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Der Konstruktor.|
|[CAtlExeModuleT::-CAtlExeModuleT](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|Initialisiert COM.|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analysiert die Befehlszeile und führt bei Bedarf eine Registrierung durch.|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Diese Methode wird unmittelbar nach dem Beenden der Nachrichtenschleife aufgerufen.|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Diese Methode wird unmittelbar vor dem Eingeben der Nachrichtenschleife aufgerufen.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Registriert das Klassenobjekt.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Das Klassenobjekt wird widerrufen.|
|[CAtlExeModuleT::Ausführen](#run)|Diese Methode führt Code im EXE-Modul aus, um die Nachrichtenschleife zu initialisieren, auszuführen und zu bereinigen.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Diese Methode führt die Nachrichtenschleife aus.|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Nicht initialisiert COM.|
|[CAtlExeModuleT::Entsperren](#unlock)|Dekrementiert die Sperranzahl des Moduls.|
|[CAtlExeModuleT::WinMain](#winmain)|Diese Methode implementiert den Code, der zum Ausführen einer EXE erforderlich ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Ein Flag, das angibt, dass das Modul verzögert werden soll.|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Ein Pausenwert, der verwendet wird, um sicherzustellen, dass alle Objekte vor dem Herunterfahren freigegeben werden.|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Ein Timeoutwert, der verwendet wird, um das Entladen des Moduls zu verzögern.|

## <a name="remarks"></a>Bemerkungen

`CAtlExeModuleT`stellt das Modul für eine Anwendung (EXE) dar und enthält Code, der das Erstellen einer EXE, die Verarbeitung der Befehlszeile, das Registrieren von Klassenobjekten, das Ausführen der Nachrichtenschleife und das Bereinigen beim Beenden unterstützt.

Diese Klasse wurde entwickelt, um die Leistung zu verbessern, wenn COM-Objekte im EXE-Server kontinuierlich erstellt und zerstört werden. Nachdem das letzte COM-Objekt freigegeben wurde, wartet die EXE auf eine vom [CAtlExeModuleT::m_dwTimeOut-Datenmember](#m_dwtimeout) angegebene Dauer. Wenn während dieses Zeitraums keine Aktivität vorhanden ist (d. h., es werden keine COM-Objekte erstellt), wird der Herunterfahrvorgang initiiert.

Das [CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) Datenmember ist ein Flag, das verwendet wird, um zu bestimmen, ob die EXE den oben definierten Mechanismus verwenden soll. Wenn es auf false gesetzt ist, wird das Modul sofort beendet.

Weitere Informationen zu Modulen in ATL finden Sie unter [ATL-Modulklassen](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>CAtlExeModuleT::CAtlExeModuleT

Der Konstruktor.

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn das EXE-Modul nicht initialisiert werden konnte, wird WinMain sofort ohne weitere Verarbeitung zurückgegeben.

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>CAtlExeModuleT::-CAtlExeModuleT

Der Destruktor.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>CAtlExeModuleT::InitializeCom

Initialisiert COM.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Konstruktor aufgerufen und kann überschrieben werden, um COM auf eine andere Weise als die Standardimplementierung zu initialisieren. Die Standardimplementierung `CoInitializeEx(NULL, COINIT_MULTITHREADED)` ruft `CoInitialize(NULL)` entweder auf oder abhängig von der Projektkonfiguration.

Das Überschreiben dieser Methode erfordert normalerweise das Überschreiben von [CAtlExeModuleT::UninitializeCom](#uninitializecom).

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>CAtlExeModuleT::m_bDelayShutdown

Ein Flag, das angibt, dass das Modul verzögert werden soll.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie in der [CAtlExeModuleT-Übersicht.](../../atl/reference/catlexemodulet-class.md)

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>CAtlExeModuleT::m_dwPause

Ein Pausenwert, der verwendet wird, um sicherzustellen, dass alle Objekte vor dem Herunterfahren verschwunden sind.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Bemerkungen

Ändern Sie diesen Wert nach dem Aufruf von [CAtlExeModuleT::InitializeCom,](#initializecom) um die Anzahl der Millisekunden festzulegen, die als Pausenwert zum Herunterfahren des Servers verwendet werden. Der Standardwert ist 1000 Millisekunden.

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>CAtlExeModuleT::m_dwTimeOut

Ein Timeoutwert, der verwendet wird, um das Entladen des Moduls zu verzögern.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Bemerkungen

Ändern Sie diesen Wert nach dem Aufruf von [CAtlExeModuleT::InitializeCom,](#initializecom) um die Anzahl der Millisekunden zu definieren, die als Timeoutwert zum Herunterfahren des Servers verwendet werden. Der Standardwert ist 5000 Millisekunden. Weitere Informationen finden Sie in der [CAtlExeModuleT-Übersicht.](../../atl/reference/catlexemodulet-class.md)

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlExeModuleT::ParseCommandLine

Analysiert die Befehlszeile und führt bei Bedarf eine Registrierung durch.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parameter

*lpCmdLine*<br/>
Die Befehlszeile, die an die Anwendung übergeben wurde.

*pnRetCode*<br/>
Das der Registrierung entsprechende HRESULT (falls dies der Ort in Kraft war).

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Anwendung weiterhin ausgeführt werden soll, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von [CAtlExeModuleT::WinMain](#winmain) aufgerufen und kann überschrieben werden, um Befehlszeilen-Switches zu verarbeiten. Die Standardimplementierung überprüft **/RegServer-** und **/UnRegServer-Befehlszeilenargumente** und führt die Registrierung oder Deregistrierung durch.

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>CAtlExeModuleT::PostMessageLoop

Diese Methode wird unmittelbar nach dem Beenden der Nachrichtenschleife aufgerufen.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um eine benutzerdefinierte Anwendungsbereinigung durchzuführen. Die Standardimplementierung ruft [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)auf.

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlExeModuleT::PreMessageLoop

Diese Methode wird unmittelbar vor dem Eingeben der Nachrichtenschleife aufgerufen.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Der Wert, der als *nShowCmd-Parameter* in WinMain übergeben wurde.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um benutzerdefinierten Initialisierungscode für die Anwendung hinzuzufügen. Die Standardimplementierung registriert die Klassenobjekte.

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>CAtlExeModuleT::RegisterClassObjects

Registriert das Klassenobjekt bei OLE, damit andere Anwendungen eine Verbindung herstellen können.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parameter

*dwClsContext*<br/>
Gibt den Kontext an, in dem das Klassenobjekt ausgeführt werden soll. Mögliche Werte sind CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER oder CLSCTX_LOCAL_SERVER.

*dwFlags*<br/>
Bestimmt die Verbindungstypen zum Klassenobjekt. Mögliche Werte sind REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE oder REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK auf Erfolg zurück, S_FALSE, wenn keine Klassen registriert werden konnten, oder einen Fehler HRESULT bei einem Fehler.

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>CAtlExeModuleT::RevokeClassObjects

Entfernt das Klassenobjekt.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK auf Erfolg zurück, S_FALSE, wenn keine Klassen registriert werden konnten, oder einen Fehler HRESULT bei einem Fehler.

## <a name="catlexemoduletrun"></a><a name="run"></a>CAtlExeModuleT::Ausführen

Diese Methode führt Code im EXE-Modul aus, um die Nachrichtenschleife zu initialisieren, auszuführen und zu bereinigen.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der im [WinMain-Abschnitt](/windows/win32/api/winbase/nf-winbase-winmain) beschriebenen Werte sein. Standardmäßig SW_HIDE.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann überschrieben werden. In der Praxis ist es jedoch besser, [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop)oder [CAtlExeModuleT::PostMessageLoop](#postmessageloop) zu überschreiben.

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>CAtlExeModuleT::RunMessageLoop

Diese Methode führt die Nachrichtenschleife aus.

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode kann überschrieben werden, um das Verhalten der Nachrichtenschleife zu ändern.

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>CAtlExeModuleT::UninitializeCom

Nicht initialisiert COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig ruft diese Methode einfach [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) auf und wird vom Destruktor aufgerufen. Überschreiben Sie diese Methode, wenn Sie [CAtlExeModuleT::InitializeCom](#initializecom)überschreiben.

## <a name="catlexemoduletunlock"></a><a name="unlock"></a>CAtlExeModuleT::Entsperren

Dekrementiert die Sperranzahl des Moduls.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert zurück, der für Diagnosen oder Tests nützlich sein kann.

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a>CAtlExeModuleT::WinMain

Diese Methode implementiert den Code, der zum Ausführen einer EXE erforderlich ist.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parameter

*nShowCmd*<br/>
Gibt an, wie das Fenster angezeigt werden soll. Dieser Parameter kann einer der im [WinMain-Abschnitt](/windows/win32/api/winbase/nf-winbase-winmain) beschriebenen Werte sein.

### <a name="return-value"></a>Rückgabewert

Gibt den Rückgabewert der ausführbaren Datei zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann überschrieben werden. Wenn das Überschreiben von [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop)oder [CAtlExeModuleT::RunMessageLoop](#runmessageloop) nicht genügend Flexibilität `WinMain` bietet, ist es möglich, die Funktion mit dieser Methode zu überschreiben.

## <a name="see-also"></a>Siehe auch

[ATLDuck-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT-Klasse](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT-Klasse](../../atl/reference/catldllmodulet-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
