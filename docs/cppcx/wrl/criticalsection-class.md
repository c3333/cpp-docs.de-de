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
ms.openlocfilehash: 5deb89e795d1886ca316886ae1ea260ce1f36fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372589"
---
# <a name="criticalsection-class"></a>CriticalSection-Klasse

Stellt ein kritisches Abschnittsobjekt dar.

## <a name="syntax"></a>Syntax

```cpp
class CriticalSection;
```

## <a name="members"></a>Member

### <a name="constructor"></a>Konstruktor

Name                                                        | BESCHREIBUNG
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::CriticalSection](#criticalsection)        | Initialisiert ein Synchronisierungsobjekt, das einem Mutex-Objekt ähnelt, aber nur von den Threads eines einzelnen Prozesses verwendet werden kann.
[CriticalSection::-CriticalSection](#tilde-criticalsection) | Deinitialisiert und zerstört das `CriticalSection` aktuelle Objekt.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                 | BESCHREIBUNG
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::IsValid](#isvalid) | Gibt an, ob der aktuelle kritische Abschnitt gültig ist.
[CriticalSection::Lock](#lock)       | Wartet auf den Besitz des angegebenen kritischen Abschnittsobjekts. Die Funktion wird zurückgegeben, wenn dem aufrufenden Thread der Besitz gewährt wird.
[CriticalSection::TryLock](#trylock) | Versucht, einen kritischen Abschnitt ohne Blockierung einzugeben. Wenn der Aufruf erfolgreich ist, übernimmt der aufrufende Thread den Besitz des kritischen Abschnitts.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                        | BESCHREIBUNG
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | Deklariert ein kritisches Abschnittsdatenelement.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CriticalSection`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>CriticalSection::-CriticalSection

Deinitialisiert und zerstört das `CriticalSection` aktuelle Objekt.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>CriticalSection::CriticalSection

Initialisiert ein Synchronisierungsobjekt, das einem Mutex-Objekt ähnelt, aber nur von den Threads eines einzelnen Prozesses verwendet werden kann.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parameter

*Spincount*<br/>
Die Spinanzahl für das kritische Abschnittsobjekt. Der Standardwert ist 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu kritischen Abschnitten und `InitializeCriticalSectionAndSpinCount` Spincounts `Synchronization` finden Sie in der Funktion im Abschnitt der Windows-API-Dokumentation.

## <a name="criticalsectioncs_"></a><a name="cs"></a>CriticalSection::cs_

Deklariert ein kritisches Abschnittsdatenelement.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Bemerkungen

Dieses Datenelement ist geschützt.

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>CriticalSection::IsValid

Gibt an, ob der aktuelle kritische Abschnitt gültig ist.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

Standardmäßig wird immer **true**zurückgegeben.

## <a name="criticalsectionlock"></a><a name="lock"></a>CriticalSection::Lock

Wartet auf den Besitz des angegebenen kritischen Abschnittsobjekts. Die Funktion wird zurückgegeben, wenn dem aufrufenden Thread der Besitz gewährt wird.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parameter

*Cs*<br/>
Ein vom Benutzer angegebenes kritisches Abschnittsobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Sperrobjekt, das zum Entsperren des aktuellen kritischen Abschnitts verwendet werden kann.

### <a name="remarks"></a>Bemerkungen

Die `Lock` erste Funktion wirkt sich auf das aktuelle kritische Abschnittsobjekt aus. Die `Lock` zweite Funktion betrifft einen vom Benutzer angegebenen kritischen Abschnitt.

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>CriticalSection::TryLock

Versucht, einen kritischen Abschnitt ohne Blockierung einzugeben. Wenn der Aufruf erfolgreich ist, übernimmt der aufrufende Thread den Besitz des kritischen Abschnitts.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parameter

*Cs*<br/>
Ein vom Benutzer angegebenes kritisches Abschnittsobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der kritische Abschnitt erfolgreich eingegeben wurde oder der aktuelle Thread bereits Eigentümer des kritischen Abschnitts ist. Null, wenn ein anderer Thread bereits den kritischen Abschnitt besitzt.

### <a name="remarks"></a>Bemerkungen

Die `TryLock` erste Funktion wirkt sich auf das aktuelle kritische Abschnittsobjekt aus. Die `TryLock` zweite Funktion betrifft einen vom Benutzer angegebenen kritischen Abschnitt.
