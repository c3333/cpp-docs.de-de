---
title: SRWLock-Klasse
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock_
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::~SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
helpviewer_keywords:
- Microsoft::WRL::Wrappers::SRWLock class
- Microsoft::WRL::Wrappers::SRWLock::LockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::LockShared method
- Microsoft::WRL::Wrappers::SRWLock::SRWLock, constructor
- Microsoft::WRL::Wrappers::SRWLock::SRWLock_ data member
- Microsoft::WRL::Wrappers::SRWLock::~SRWLock, destructor
- Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::TryLockShared method
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
ms.openlocfilehash: e305ad54e30455ce7c25f356c454791da0783591
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377265"
---
# <a name="srwlock-class"></a>SRWLock-Klasse

Stellt eine schlanke Lese-/Schreibsperre dar.

## <a name="syntax"></a>Syntax

```cpp
class SRWLock;
```

## <a name="remarks"></a>Bemerkungen

Eine schlanke Lese-/Schreibsperre wird verwendet, um den Zugriff über Threads hinweg auf ein Objekt oder eine Ressource zu synchronisieren. Weitere Informationen finden Sie unter [Synchronisierungsfunktionen](/windows/win32/Sync/synchronization-functions).

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name                | BESCHREIBUNG
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Synonym für `SRWLock` ein Objekt, das im exklusiven Modus erworben wird.
`SyncLockShared`    | Synonym für `SRWLock` ein Objekt, das im freigegebenen Modus erworben wird.

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                     | BESCHREIBUNG
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Initialisiert eine neue Instanz der Klasse `SRWLock`.
[SRWLock::sRWLock](#tilde-srwlock)      | Deinitialisiert eine Instanz `SRWLock` der Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                           | BESCHREIBUNG
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Erwirbt `SRWLock` ein Objekt im exklusiven Modus.
[SRWLock::LockShared](#lockshared)             | Erwirbt `SRWLock` ein Objekt im freigegebenen Modus.
[SRWLock::TryLockExklusiv](#trylockexclusive) | Versucht, ein `SRWLock` Objekt im exklusiven Modus `SRWLock` für das aktuelle oder angegebene Objekt zu erwerben.
[SRWLock::TryLockShared](#trylockshared)       | Versucht, ein `SRWLock` Objekt im freigegebenen Modus `SRWLock` für das aktuelle oder angegebene Objekt zu erwerben.

### <a name="protected-data-member"></a>Protected Data Member

Name                                      | BESCHREIBUNG
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Enthält die zugrunde liegende `SRWLock` Sperrvariable für das aktuelle Objekt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SRWLock`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="srwlocksrwlock"></a><a name="tilde-srwlock"></a>SRWLock::sRWLock

Deinitialisiert eine Instanz `SRWLock` der Klasse.

```cpp
~SRWLock();
```

## <a name="srwlocklockexclusive"></a><a name="lockexclusive"></a>SRWLock::LockExclusive

Erwirbt `SRWLock` ein Objekt im exklusiven Modus.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Zeiger auf `SRWLock` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Ein `SRWLock` Objekt im exklusiven Modus.

## <a name="srwlocklockshared"></a><a name="lockshared"></a>SRWLock::LockShared

Erwirbt `SRWLock` ein Objekt im freigegebenen Modus.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Zeiger auf `SRWLock` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Ein `SRWLock` Objekt im freigegebenen Modus.

## <a name="srwlocksrwlock"></a><a name="srwlock-constructor"></a>SRWLock::SRWLock

Initialisiert eine neue Instanz der Klasse `SRWLock`.

```cpp
SRWLock();
```

## <a name="srwlocksrwlock_"></a><a name="srwlock-data-member"></a>SRWLock::SRWLock_

Enthält die zugrunde liegende `SRWLock` Sperrvariable für das aktuelle Objekt.

```cpp
SRWLOCK SRWLock_;
```

## <a name="srwlocktrylockexclusive"></a><a name="trylockexclusive"></a>SRWLock::TryLockExklusiv

Versucht, ein `SRWLock` Objekt im exklusiven Modus `SRWLock` für das aktuelle oder angegebene Objekt zu erwerben. Wenn der Aufruf erfolgreich ist, übernimmt der aufrufende Thread den Besitz der Sperre.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Zeiger auf `SRWLock` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Bei Erfolg `SRWLock` übernimmt ein Objekt im exklusiven Modus und der aufrufende Thread den Besitz der Sperre. Andernfalls ein `SRWLock` Objekt, dessen Status ungültig ist.

## <a name="srwlocktrylockshared"></a><a name="trylockshared"></a>SRWLock::TryLockShared

Versucht, ein `SRWLock` Objekt im freigegebenen Modus `SRWLock` für das aktuelle oder angegebene Objekt zu erwerben.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Zeiger auf `SRWLock` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Bei Erfolg `SRWLock` übernimmt ein Objekt im freigegebenen Modus und der aufrufende Thread den Besitz der Sperre. Andernfalls ein `SRWLock` Objekt, dessen Status ungültig ist.
