---
title: SyncLockT-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
ms.openlocfilehash: 6a6e176020624f02e778ba5684a374abfbafa9e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184669"
---
# <a name="synclockt-class"></a>SyncLockT-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Parameter

*Syncmerkmalen*<br/>
Der Typ, der den Besitz einer Ressource übernehmen kann.

## <a name="remarks"></a>Bemerkungen

Stellt einen Typ dar, der einen exklusiven oder freigegebenen Besitz einer Ressource annehmen kann.

Die- `SyncLockT` Klasse wird z. b. verwendet, um die Implementierung der [SRWLOCK](srwlock-class.md) -Klasse zu unterstützen.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                      | BESCHREIBUNG
----------------------------------------- | ----------------------------------------------------
[Synclockt:: synclockt](#synclockt)        | Initialisiert eine neue Instanz der `SyncLockT`-Klasse.
[Synclockt:: ~ synclockt](#tilde-synclockt) | Deinitialisiert eine Instanz der- `SyncLockT` Klasse.

### <a name="protected-constructors"></a>Geschützte Konstruktoren

Name                               | BESCHREIBUNG
---------------------------------- | ----------------------------------------------------
[Synclockt:: synclockt](#synclockt) | Initialisiert eine neue Instanz der `SyncLockT`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

name                             | BESCHREIBUNG
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[Synclockt:: IsLocked](#islocked) | Gibt an, ob das aktuelle- `SyncLockT` Objekt eine Ressource besitzt, d `SyncLockT` . h., das Objekt ist *gesperrt*.
[Synclockt:: Unlock](#unlock)     | Gibt die Steuerung der Ressource frei, die vom aktuellen- `SyncLockT` Objekt gehalten wird (sofern vorhanden).

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                      | BESCHREIBUNG
------------------------- | -------------------------------------------------------------------
[Synclockt:: sync_](#sync) | Enthält die zugrunde liegende Ressource, die von der-Klasse dargestellt wird `SyncLockT` .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SyncLockT`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrappers::D etails

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>Synclockt:: ~ synclockt

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Bemerkungen

Deinitialisiert eine Instanz der- `SyncLockT` Klasse.

Dieser Dekonstruktor entsperrt auch die aktuelle `SyncLockT` Instanz.

## <a name="synclocktislocked"></a><a name="islocked"></a>Synclockt:: IsLocked

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das `SyncLockT` Objekt gesperrt ist, andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Gibt an, ob das aktuelle- `SyncLockT` Objekt eine Ressource besitzt, d `SyncLockT` . h., das Objekt ist *gesperrt*.

## <a name="synclocktsync_"></a><a name="sync"></a>Synclockt:: sync_

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Bemerkungen

Enthält die zugrunde liegende Ressource, die von der-Klasse dargestellt wird `SyncLockT` .

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>Synclockt:: synclockt

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Ein rvalue-Verweis auf ein anderes `SyncLockT` Objekt.

*PPEN*<br/>
Ein Verweis auf ein anderes `SyncLockWithStatusT` Objekt.

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der `SyncLockT`-Klasse.

Der erste Konstruktor initialisiert das aktuelle- `SyncLockT` Objekt aus einem anderen `SyncLockT` Objekt, das durch einen *anderen*Parameter angegeben wird, und erklärt dann das andere-Objekt für ungültig `SyncLockT` . Der zweite Konstruktor ist **`protected`** , und initialisiert das aktuelle- `SyncLockT` Objekt in einen ungültigen Zustand.

## <a name="synclocktunlock"></a><a name="unlock"></a>Synclockt:: Unlock

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
void Unlock();
```

### <a name="remarks"></a>Bemerkungen

Gibt die Steuerung der Ressource frei, die vom aktuellen- `SyncLockT` Objekt gehalten wird (sofern vorhanden).
