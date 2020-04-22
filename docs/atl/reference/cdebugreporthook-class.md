---
title: CDebugReportHook-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
ms.openlocfilehash: 8380556bbe007326156bf0ec0eefc23052e8e056
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747720"
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook-Klasse

Verwenden Sie diese Klasse, um Debugberichte an eine Named Pipe zu senden.

## <a name="syntax"></a>Syntax

```
class CDebugReportHook
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Ruft [SetPipeName](#setpipename), [SetTimeout](#settimeout)und [SetHook](#sethook)auf.|
|[CDebugReportHook::'CDebugReportHook](#dtor)|Ruft [CDebugReportHook::RemoveHook](#removehook)auf.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Statisch) Die benutzerdefinierte Berichtsfunktion, die in den C-Laufzeitdebug-Berichtsprozess eingebunden ist.|
|[CDebugReportHook::RemoveHook](#removehook)|Rufen Sie diese Methode auf, um das Senden von Debugberichten an die named pipe zu beenden und den vorherigen Berichtshook wiederherzustellen.|
|[CDebugReportHook::SetHook](#sethook)|Rufen Sie diese Methode auf, um mit dem Senden von Debugberichten an die named pipe zu beginnen.|
|[CDebugReportHook::SetPipeName](#setpipename)|Rufen Sie diese Methode auf, um den Computer und den Namen der Pipe festzulegen, an die die Debugberichte gesendet werden.|
|[CDebugReportHook::SetTimeout](#settimeout)|Rufen Sie diese Methode auf, um die Zeit in Millisekunden festzulegen, die diese Klasse wartet, bis die benannte Pipe verfügbar wird.|

## <a name="remarks"></a>Bemerkungen

Erstellen Sie eine Instanz dieser Klasse in Debugbuilds Ihrer Dienste oder Anwendungen, um Debugberichte an eine Named Pipe zu senden. Debugberichte werden generiert, indem [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) oder ein Wrapper für diese Funktion wie die [Makros ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) und [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) verwendet werden.

Mithilfe dieser Klasse können Sie Komponenten, die in nicht interaktiven [Fensterstationen](/windows/win32/winstation/window-stations)ausgeführt werden, interaktiv debuggen.

Beachten Sie, dass Debugberichte mithilfe des zugrunde liegenden Sicherheitskontexts des Threads gesendet werden. Der Identitätswechsel ist vorübergehend deaktiviert, sodass Debugberichte in Situationen angezeigt werden können, in denen der Identitätswechsel von Benutzern mit niedrigen Berechtigungen stattfindet, z. B. in Webanwendungen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlutil.h

## <a name="cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook

Ruft [SetPipeName](#setpipename), [SetTimeout](#settimeout)und [SetHook](#sethook)auf.

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Parameter

*szMachineName*<br/>
Der Name des Computers, an den die Debugausgabe gesendet werden soll. Standardwerte für den lokalen Computer.

*szPipeName*<br/>
Der Name der benannten Pipe, an die die Debugausgabe gesendet werden soll.

*dwTimeout*<br/>
Die Zeit in Millisekunden, die diese Klasse wartet, bis die benannte Pipe verfügbar ist.

## <a name="cdebugreporthookcdebugreporthook"></a><a name="dtor"></a>CDebugReportHook::'CDebugReportHook

Ruft [CDebugReportHook::RemoveHook](#removehook)auf.

```
~CDebugReportHook() throw();
```

## <a name="cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc

Die benutzerdefinierte Berichtsfunktion, die in den C-Laufzeitdebug-Berichtsprozess eingebunden ist.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>Parameter

*reportType*<br/>
Der Typ des Berichts (_CRT_WARN, _CRT_ERROR oder _CRT_ASSERT).

*Nachricht*<br/>
Die Meldungszeichenfolge.

*Returnvalue*<br/>
Der Wert, der von [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt FALSE zurück, wenn der Hook die betreffende Nachricht vollständig verarbeitet, sodass keine weitere Meldung erforderlich ist. Gibt TRUE `_CrtDbgReport` zurück, wenn die Nachricht auf die normale Weise gemeldet werden soll.

### <a name="remarks"></a>Bemerkungen

Die Berichtsfunktion versucht, die Named Pipe zu öffnen und mit dem Prozess am anderen Ende zu kommunizieren. Wenn die Pipe ausgelastet ist, wartet die Berichtsfunktion, bis die Pipe frei ist oder das Timeout abläuft. Das Timeout kann vom Konstruktor oder einem Aufruf von [CDebugReportHook::SetTimeout](#settimeout)festgelegt werden.

Der Code in dieser Funktion wird im zugrunde liegenden Sicherheitskontext des aufrufenden Threads ausgeführt, d. h. der Identitätswechsel ist für die Dauer dieser Funktion deaktiviert.

## <a name="cdebugreporthookremovehook"></a><a name="removehook"></a>CDebugReportHook::RemoveHook

Rufen Sie diese Methode auf, um das Senden von Debugberichten an die named pipe zu beenden und den vorherigen Berichtshook wiederherzustellen.

```cpp
void RemoveHook() throw();
```

### <a name="remarks"></a>Bemerkungen

Ruft [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) auf, um den vorherigen Berichtshaken wiederherzustellen.

## <a name="cdebugreporthooksethook"></a><a name="sethook"></a>CDebugReportHook::SetHook

Rufen Sie diese Methode auf, um mit dem Senden von Debugberichten an die named pipe zu beginnen.

```cpp
void SetHook() throw();
```

### <a name="remarks"></a>Bemerkungen

Ruft [_CrtSetReportHook2,](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) dass Debugberichte über [CDebugReportHookProc](#cdebugreporthookproc) an die Named Pipe weitergeleitet werden. Diese Klasse verfolgt den vorherigen Berichtshaken, sodass er wiederhergestellt werden kann, wenn [RemoveHook](#removehook) aufgerufen wird.

## <a name="cdebugreporthooksetpipename"></a><a name="setpipename"></a>CDebugReportHook::SetPipeName

Rufen Sie diese Methode auf, um den Computer und den Namen der Pipe festzulegen, an die die Debugberichte gesendet werden.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Parameter

*szMachineName*<br/>
Der Name des Computers, an den die Debugausgabe gesendet werden soll.

*szPipeName*<br/>
Der Name der benannten Pipe, an die die Debugausgabe gesendet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="cdebugreporthooksettimeout"></a><a name="settimeout"></a>CDebugReportHook::SetTimeout

Rufen Sie diese Methode auf, um die Zeit in Millisekunden festzulegen, die diese Klasse wartet, bis die benannte Pipe verfügbar wird.

```cpp
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parameter

*dwTimeout*<br/>
Die Zeit in Millisekunden, die diese Klasse wartet, bis die benannte Pipe verfügbar ist.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../atl/reference/atl-classes.md)
