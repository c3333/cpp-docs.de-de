---
title: Win32ThreadTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
ms.openlocfilehash: 64f02293508894a70f36c29d5032c9ba8f250c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325798"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits-Klasse

Diese Klasse stellt die Erstellungsfunktion für einen Windows-Thread bereit. Verwenden Sie diese Klasse, wenn der Thread keine CRT-Funktionen verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class Win32ThreadTraits
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|(Statisch) Rufen Sie diese Funktion auf, um einen Thread zu erstellen, der keine CRT-Funktionen verwenden sollte.|

## <a name="remarks"></a>Bemerkungen

Threadeigenschaften sind Klassen, die eine Erstellungsfunktion für einen bestimmten Threadtyp bereitstellen. Die Erstellungsfunktion hat die gleiche Signatur und Semantik wie die Windows [CreateThread-Funktion.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)

Threadeigenschaften werden von den folgenden Klassen verwendet:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Wenn der Thread CRT-Funktionen verwendet, verwenden Sie stattdessen [CRTThreadTraits.](../../atl/reference/crtthreadtraits-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="win32threadtraitscreatethread"></a><a name="createthread"></a>Win32ThreadTraits::CreateThread

Rufen Sie diese Funktion auf, um einen Thread zu erstellen, der keine CRT-Funktionen verwenden sollte.

```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```

### <a name="parameters"></a>Parameter

*lpsa*<br/>
Die Sicherheitsattribute für den neuen Thread.

*dwStackSize*<br/>
Die Stapelgröße für den neuen Thread.

*pfnThreadProc*<br/>
Die Threadprozedur des neuen Threads.

*pvParam*<br/>
Der Parameter, der an die Threadprozedur übergeben werden soll.

*dwCreationFlags*<br/>
Die Erstellungsflags (0 oder CREATE_SUSPENDED).

*pdwThreadId*<br/>
[out] Adresse der DWORD-Variablen, die bei Erfolg die Thread-ID des neu erstellten Threads empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt das Handle an den neu erstellten Thread oder NULL bei einem Fehler zurück. Rufen Sie [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf, um erweiterte Fehlerinformationen zu erhalten.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu den Parametern für diese Funktion finden Sie unter [CreateThread.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)

Diese Funktion `CreateThread` ruft auf, um den Thread zu erstellen.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
