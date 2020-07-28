---
title: CriticalSection-Klasse
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
ms.openlocfilehash: b95e512f89ee1ff32ca9f1bea51bce643d185a2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220521"
---
# <a name="criticalsection-class"></a>CriticalSection-Klasse

Stellt ein kritisches Abschnitts Objekt dar.

## <a name="syntax"></a>Syntax

```cpp
class CriticalSection;
```

## <a name="members"></a>Member

### <a name="constructor"></a>Konstruktor

Name                                                        | BESCHREIBUNG
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection:: CriticalSection](#criticalsection)        | Initialisiert ein Synchronisierungs Objekt, das einem Mutex-Objekt ähnelt, aber nur von den Threads eines einzelnen Prozesses verwendet werden kann.
[CriticalSection:: ~ CriticalSection](#tilde-criticalsection) | Deinitialisiert und zerstört das aktuelle- `CriticalSection` Objekt.

### <a name="public-methods"></a>Öffentliche Methoden

name                                 | BESCHREIBUNG
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection:: IsValid](#isvalid) | Gibt an, ob der aktuelle kritische Abschnitt gültig ist.
[CriticalSection:: Lock](#lock)       | Wartet auf den Besitz des angegebenen kritischen Abschnitts Objekts. Die Funktion gibt zurück, wenn dem aufrufenden Thread der Besitz erteilt wird.
[CriticalSection:: TryLock](#trylock) | Versucht, einen kritischen Abschnitt einzugeben, ohne zu blockieren. Wenn der Aufruf erfolgreich ist, übernimmt der aufrufende Thread den Besitz des kritischen Abschnitts.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                        | BESCHREIBUNG
--------------------------- | ----------------------------------------
[CriticalSection:: cs_](#cs) | Deklariert einen kritischen Abschnitts Datenmember.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CriticalSection`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrapper

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>CriticalSection:: ~ CriticalSection

Deinitialisiert und zerstört das aktuelle- `CriticalSection` Objekt.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>CriticalSection:: CriticalSection

Initialisiert ein Synchronisierungs Objekt, das einem Mutex-Objekt ähnelt, aber nur von den Threads eines einzelnen Prozesses verwendet werden kann.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parameter

*spincount*<br/>
Die drehanzahl für das kritische Abschnitts Objekt. Der Standardwert ist 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu kritischen Abschnitten und spincounts finden Sie unter der- `InitializeCriticalSectionAndSpinCount` Funktion im `Synchronization` Abschnitt der Windows-API-Dokumentation.

## <a name="criticalsectioncs_"></a><a name="cs"></a>CriticalSection:: cs_

Deklariert einen kritischen Abschnitts Datenmember.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Bemerkungen

Dieser Datenmember ist geschützt.

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>CriticalSection:: IsValid

Gibt an, ob der aktuelle kritische Abschnitt gültig ist.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

Standardmäßig gibt immer zurück **`true`** .

## <a name="criticalsectionlock"></a><a name="lock"></a>CriticalSection:: Lock

Wartet auf den Besitz des angegebenen kritischen Abschnitts Objekts. Die Funktion gibt zurück, wenn dem aufrufenden Thread der Besitz erteilt wird.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parameter

*CS*<br/>
Ein vom Benutzer angegebenes kritisches Abschnitts Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Sperr Objekt, das zum Entsperren des aktuellen kritischen Abschnitts verwendet werden kann.

### <a name="remarks"></a>Bemerkungen

Die erste `Lock` Funktion wirkt sich auf das aktuelle kritische Abschnitts Objekt aus. Die zweite `Lock` Funktion wirkt sich auf einen vom Benutzer angegebenen kritischen Abschnitt aus.

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>CriticalSection:: TryLock

Versucht, einen kritischen Abschnitt einzugeben, ohne zu blockieren. Wenn der Aufruf erfolgreich ist, übernimmt der aufrufende Thread den Besitz des kritischen Abschnitts.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parameter

*CS*<br/>
Ein vom Benutzer angegebenes kritisches Abschnitts Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn der kritische Abschnitt erfolgreich eingegeben wurde oder der aktuelle Thread bereits den kritischen Abschnitt besitzt. 0 (null), wenn ein anderer Thread bereits den kritischen Abschnitt besitzt.

### <a name="remarks"></a>Bemerkungen

Die erste `TryLock` Funktion wirkt sich auf das aktuelle kritische Abschnitts Objekt aus. Die zweite `TryLock` Funktion wirkt sich auf einen vom Benutzer angegebenen kritischen Abschnitt aus.
