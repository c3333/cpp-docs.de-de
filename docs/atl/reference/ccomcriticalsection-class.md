---
title: Ccomcriticalsection-Klasse
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
ms.openlocfilehash: 8cf590052dee9d0303ccfb102296fc66038aec57
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224304"
---
# <a name="ccomcriticalsection-class"></a>Ccomcriticalsection-Klasse

Diese Klasse stellt Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnitts Objekts bereit.

## <a name="syntax"></a>Syntax

```
class CComCriticalSection
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Ccomcriticalsection:: ccomcriticalsection](#ccomcriticalsection)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Ccomcriticalsection:: init](#init)|Erstellt und initialisiert ein kritisches Abschnitts Objekt.|
|[Ccomcriticalsection:: Lock](#lock)|Ruft den Besitz des kritischen Abschnitts Objekts ab.|
|[Ccomcriticalsection:: Term](#term)|Gibt Systemressourcen frei, die vom Objekt des kritischen Abschnitts verwendet werden.|
|[Ccomcriticalsection:: Unlock](#unlock)|Gibt den Besitz des kritischen Abschnitts Objekts frei.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[Ccomcriticalsection:: m_sec](#m_sec)|Ein CRITICAL_SECTION-Objekt.|

## <a name="remarks"></a>Bemerkungen

`CComCriticalSection`ähnelt der Klasse [ccomautocriticalsection](../../atl/reference/ccomautocriticalsection-class.md), mit dem Unterschied, dass Sie den kritischen Abschnitt explizit initialisieren und freigeben müssen.

In der Regel verwenden Sie `CComCriticalSection` den **`typedef`** Namen [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Dieser Name verweist auf den Fall `CComCriticalSection` , dass [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) verwendet wird.

Unter [ccomcritcclock Class](../../atl/reference/ccomcritseclock-class.md) finden Sie eine sicherere Möglichkeit, diese Klasse zu verwenden, als `Lock` `Unlock` direkt aufrufen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcore. h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a>Ccomcriticalsection:: ccomcriticalsection

Der Konstruktor.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Bemerkungen

Legt den [m_sec](#m_sec) Datenmember auf NULL fest.

## <a name="ccomcriticalsectioninit"></a><a name="init"></a>Ccomcriticalsection:: init

Ruft die Win32-Funktion [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)auf, die das im [m_sec](#m_sec) -Datenmember enthaltene kritische Abschnitts Objekt initialisiert.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg, E_OUTOFMEMORY oder E_FAIL bei einem Fehler zurück.

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a>Ccomcriticalsection:: Lock

Ruft die Win32-Funktion " [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)" auf, die wartet, bis der Thread den Besitz des kritischen Abschnitts Objekts übernimmt, das im [m_sec](#m_sec) Datenmember enthalten ist.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg, E_OUTOFMEMORY oder E_FAIL bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das Critical Section-Objekt muss zuerst mit einem Rückruf der [Init](#init) -Methode initialisiert werden. Wenn die Ausführung des geschützten Codes abgeschlossen ist, muss der Thread [Unlock](#unlock) aufgerufen werden, um den Besitz des kritischen Abschnitts freizugeben.

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a>Ccomcriticalsection:: m_sec

Enthält ein kritisches Abschnitts Objekt, das von allen- `CComCriticalSection` Methoden verwendet wird.

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a>Ccomcriticalsection:: Term

Ruft die Win32-Funktion [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)auf, die alle Ressourcen freigibt, die vom kritischen Abschnitts Objekt verwendet werden, das im [m_sec](#m_sec) Datenmember enthalten ist.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Nachdem `Term` aufgerufen wurde, kann der kritische Abschnitt nicht mehr für die Synchronisierung verwendet werden.

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a>Ccomcriticalsection:: Unlock

Ruft die Win32-Funktion " [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)" auf, die den Besitz des kritischen Abschnitts Objekts freigibt, das im [m_sec](#m_sec) Datenmember enthalten ist.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Um zuerst den Besitz zu erhalten, muss der Thread die [Lock](#lock) -Methode aufzurufen. Jeder-Befehl `Lock` erfordert einen entsprechenden-Befehl, `Unlock` um den Besitz des kritischen Abschnitts freizugeben.

## <a name="see-also"></a>Weitere Informationen

[Ccomfakecriticalsection-Klasse](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Ccomcritcclock-Klasse](../../atl/reference/ccomcritseclock-class.md)
