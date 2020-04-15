---
title: CRTThreadTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
ms.openlocfilehash: a7cfddc64e8c1b4e192e718d05812e385fbe08ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331021"
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits-Klasse

Diese Klasse stellt die Erstellungsfunktion für einen CRT-Thread bereit. Verwenden Sie diese Klasse, wenn der Thread CRT-Funktionen verwendet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CRTThreadTraits
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRTThreadTraits::CreateThread](#createthread)|(Statisch) Rufen Sie diese Funktion auf, um einen Thread zu erstellen, der CRT-Funktionen verwenden kann.|

## <a name="remarks"></a>Bemerkungen

Threadeigenschaften sind Klassen, die eine Erstellungsfunktion für einen bestimmten Threadtyp bereitstellen. Die Erstellungsfunktion hat die gleiche Signatur und Semantik wie die Windows [CreateThread-Funktion.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)

Threadeigenschaften werden von den folgenden Klassen verwendet:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Wenn der Thread keine CRT-Funktionen verwendet, verwenden Sie stattdessen [Win32ThreadTraits.](../../atl/reference/win32threadtraits-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="crtthreadtraitscreatethread"></a><a name="createthread"></a>CRTThreadTraits::CreateThread

Rufen Sie diese Funktion auf, um einen Thread zu erstellen, der CRT-Funktionen verwenden kann.

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

Diese Funktion ruft [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) auf, um den Thread zu erstellen.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
