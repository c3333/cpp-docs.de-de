---
title: Semaphore-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
ms.openlocfilehash: e017b1b6316c4b6d49563d9a543950ab28961d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359355"
---
# <a name="semaphore-class"></a>Semaphore-Klasse

Stellt ein Synchronisierungsobjekt dar, das eine freigegebene Ressource steuert, die eine begrenzte Anzahl von Benutzern unterstützen kann.

## <a name="syntax"></a>Syntax

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name       | BESCHREIBUNG
---------- | ------------------------------------------------------
`SyncLock` | Ein Synonym für eine Klasse, die synchrone Sperren unterstützt.

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                               | BESCHREIBUNG
---------------------------------- | ----------------------------------------------------
[Semaphore::Semaphore](#semaphore) | Initialisiert eine neue Instanz der Klasse `Semaphore`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                     | BESCHREIBUNG
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semaphore::Lock](#lock) | Wartet, bis sich das aktuelle Objekt oder das dem angegebenen Handle zugeordnete Objekt im signalisierten Zustand befindet oder das angegebene Timeoutintervall abgelaufen ist.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                     | BESCHREIBUNG
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semaphore::operator=](#operator-assign) | Verschiebt das angegebene `Semaphore` Handle von `Semaphore` einem Objekt in das aktuelle Objekt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Semaphore`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="semaphorelock"></a><a name="lock"></a>Semaphore::Lock

Wartet, bis sich das `Semaphore` aktuelle Objekt oder das dem angegebenen Handle zugeordnete Objekt im signalisierten Zustand befindet oder das angegebene Timeoutintervall abgelaufen ist.

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>Parameter

*Millisekunden*<br/>
Das Timeoutintervall in Millisekunden. Der Standardwert ist INFINITE, der auf unbestimmte Zeit wartet.

*H*<br/>
Ein Handle `Semaphore` für ein Objekt.

### <a name="return-value"></a>Rückgabewert

A `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="semaphoreoperator"></a><a name="operator-assign"></a>Semaphore::operator=

Verschiebt das angegebene `Semaphore` Handle von `Semaphore` einem Objekt in das aktuelle Objekt.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Rvalue-Verweis auf `Semaphore` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf `Semaphore` das aktuelle Objekt.

## <a name="semaphoresemaphore"></a><a name="semaphore"></a>Semaphore::Semaphore

Initialisiert eine neue Instanz der Klasse `Semaphore`.

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Ein Handle oder ein rvalue-Verweis auf ein `Semaphore` Objekt.
