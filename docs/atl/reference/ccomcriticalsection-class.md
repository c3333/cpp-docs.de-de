---
title: CComCriticalSection-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: f3991d217fbc201bd428ed2522a5c4c25e074928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327969"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection-Klasse

Diese Klasse stellt Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnittsobjekts bereit.

## <a name="syntax"></a>Syntax

```
class CComCriticalSection
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCriticalSection::Init](#init)|Erstellt und initialisiert ein kritisches Schnittobjekt.|
|[CComCriticalSection::Lock](#lock)|Ruft den Besitz des kritischen Abschnittsobjekts ab.|
|[CComCriticalSection::Term](#term)|Gibt Systemressourcen frei, die vom kritischen Abschnittsobjekt verwendet werden.|
|[CComCriticalSection::Entsperren](#unlock)|Gibt den Besitz des kritischen Abschnittsobjekts frei.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|Ein CRITICAL_SECTION Objekt.|

## <a name="remarks"></a>Bemerkungen

`CComCriticalSection`ist der Klasse [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)ähnlich, mit der Ausnahme, dass Sie den kritischen Abschnitt explizit initialisieren und freigeben müssen.

In der `CComCriticalSection` Regel verwenden Sie über den **typedef-Namen** [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Dieser Name `CComCriticalSection` verweist auf die Verwendung von [CComMultiThreadModel.](../../atl/reference/ccommultithreadmodel-class.md)

Eine sicherere Möglichkeit, diese Klasse als Aufruf `Lock` und `Unlock` direkt zu verwenden, finden Sie unter [CComCritSecLock-Klasse.](../../atl/reference/ccomcritseclock-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcore.h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection

Der Konstruktor.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Bemerkungen

Legt den [m_sec](#m_sec) Datenmember auf NULL fest.

## <a name="ccomcriticalsectioninit"></a><a name="init"></a>CComCriticalSection::Init

Ruft die Win32-Funktion [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)auf, die das im [m_sec-Datenmember](#m_sec) enthaltene kritische Abschnittsobjekt initialisiert.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg, E_OUTOFMEMORY oder E_FAIL bei Einem Fehler zurück.

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a>CComCriticalSection::Lock

Ruft die Win32-Funktion [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)auf, die wartet, bis der Thread den Besitz des kritischen Abschnittsobjekts übernehmen kann, das im [m_sec-Datenmember](#m_sec) enthalten ist.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg, E_OUTOFMEMORY oder E_FAIL bei Einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das kritische Abschnittsobjekt muss zuerst mit einem Aufruf der [Init-Methode](#init) initialisiert werden. Wenn die Ausführung des geschützten Codes abgeschlossen ist, muss der Thread [Unlock](#unlock) aufrufen, um den Besitz des kritischen Abschnitts freizugeben.

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a>CComCriticalSection::m_sec

Enthält ein kritisches Abschnittsobjekt, das von allen `CComCriticalSection` Methoden verwendet wird.

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a>CComCriticalSection::Term

Ruft die Win32-Funktion [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)auf, die alle Ressourcen freigibt, die vom kritischen Abschnittsobjekt im [m_sec](#m_sec) Datenmember verwendet werden.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Nach `Term` dem Aufruf kann der kritische Abschnitt nicht mehr für die Synchronisierung verwendet werden.

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a>CComCriticalSection::Entsperren

Ruft die Win32-Funktion [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)auf, die den Besitz des kritischen Abschnittsobjekts freigibt, das im [m_sec](#m_sec) Datenmember enthalten ist.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Um zuerst den Besitz zu erhalten, muss der Thread die [Lock-Methode](#lock) aufrufen. Jeder Aufruf `Lock` erfordert einen `Unlock` entsprechenden Aufruf, um den Besitz des kritischen Abschnitts freizugeben.

## <a name="see-also"></a>Siehe auch

[CComFakeCriticalSection-Klasse](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock-Klasse](../../atl/reference/ccomcritseclock-class.md)
