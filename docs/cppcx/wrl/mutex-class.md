---
title: Mutex-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
ms.openlocfilehash: 36466bd00c5b100f20ee87173e68fdef4131ec23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371241"
---
# <a name="mutex-class"></a>Mutex-Klasse

Stellt ein Synchronisierungsobjekt dar, das ausschließlich eine freigegebene Ressource steuert.

## <a name="syntax"></a>Syntax

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name       | BESCHREIBUNG
---------- | ------------------------------------------------------
`SyncLock` | Ein Synonym für eine Klasse, die synchrone Sperren unterstützt.

### <a name="public-constructor"></a>Öffentlicher Konstrukteur

Name                   | BESCHREIBUNG
---------------------- | ------------------------------------------------
[Mutex::Mutex](#mutex) | Initialisiert eine neue Instanz der Klasse `Mutex`.

### <a name="public-members"></a>Öffentliche Mitglieder

Name                 | BESCHREIBUNG
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::Sperre](#lock) | Wartet, bis das aktuelle `Mutex` Objekt oder das dem angegebenen Handle zugeordnete Objekt den Mutex freigibt oder das angegebene Timeoutintervall abgelaufen ist.

### <a name="public-operator"></a>Öffentlicher Betreiber

Name                                 | BESCHREIBUNG
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::operator=](#operator-assign) | Weist das angegebene `Mutex` Objekt dem aktuellen `Mutex` Objekt zu.( verschiebt) es dem aktuellen Objekt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Mutex`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="mutexlock"></a><a name="lock"></a>Mutex::Sperre

Wartet, bis das aktuelle `Mutex` Objekt oder das dem angegebenen Handle zugeordnete Objekt den Mutex freigibt oder das angegebene Timeoutintervall abgelaufen ist.

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
Das Handle `Mutex` eines Objekts.

### <a name="return-value"></a>Rückgabewert

## <a name="mutexmutex"></a><a name="mutex"></a>Mutex::Mutex

Initialisiert eine neue Instanz der Klasse `Mutex`.

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Ein Handle oder ein rvalue-Verweis auf `Mutex` ein Handle auf ein Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert ein `Mutex` Objekt aus dem angegebenen Handle. Der zweite Konstruktor initialisiert ein `Mutex` Objekt aus dem angegebenen Handle und verschiebt dann den Besitz des Mutex auf das aktuelle `Mutex` Objekt.

## <a name="mutexoperator"></a><a name="operator-assign"></a>Mutex::operator=

Weist das angegebene `Mutex` Objekt dem aktuellen `Mutex` Objekt zu.( verschiebt) es dem aktuellen Objekt.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Ein rvalue-Verweis `Mutex` auf ein Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf `Mutex` das aktuelle Objekt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Abschnitt **Move Semantics** von [Rvalue Reference Declarator: &&](../../cpp/rvalue-reference-declarator-amp-amp.md).
