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
ms.openlocfilehash: 52c4404fa28f680a9a7a4592d03f535e8406d1a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374286"
---
# <a name="synclockt-class"></a>SyncLockT-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Parameter

*SyncTraits*<br/>
Der Typ, der den Besitz einer Ressource übernehmen kann.

## <a name="remarks"></a>Bemerkungen

Stellt einen Typ dar, der exklusiven oder freigegebenen Besitz einer Ressource übernehmen kann.

Die `SyncLockT` Klasse wird z. B. zum Implementieren der [SRWLock-Klasse](srwlock-class.md) verwendet.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                      | BESCHREIBUNG
----------------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt)        | Initialisiert eine neue Instanz der Klasse `SyncLockT`.
[SyncLockT::-SyncLockt](#tilde-synclockt) | Deinitialisiert eine Instanz `SyncLockT` der Klasse.

### <a name="protected-constructors"></a>Geschützte Konstruktoren

Name                               | BESCHREIBUNG
---------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt) | Initialisiert eine neue Instanz der Klasse `SyncLockT`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                             | BESCHREIBUNG
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::IsLocked](#islocked) | Gibt an, `SyncLockT` ob das aktuelle Objekt eigentümer eine Ressource ist. das heißt, `SyncLockT` das Objekt ist *gesperrt*.
[SyncLockT::Entsperren](#unlock)     | Gibt die Steuerung der Ressource `SyncLockT` frei, die sich im Besitz des aktuellen Objekts befindet.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                      | BESCHREIBUNG
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | Enthält die zugrunde liegende `SyncLockT` Ressource, die von der Klasse dargestellt wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SyncLockT`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>SyncLockT::-SyncLockt

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Bemerkungen

Deinitialisiert eine Instanz `SyncLockT` der Klasse.

Dieser Destruktor entsperrt auch die aktuelle `SyncLockT` Instanz.

## <a name="synclocktislocked"></a><a name="islocked"></a>SyncLockT::IsLocked

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Rückgabewert

**true,** `SyncLockT` wenn das Objekt gesperrt ist; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Gibt an, `SyncLockT` ob das aktuelle Objekt eigentümer eine Ressource ist. das heißt, `SyncLockT` das Objekt ist *gesperrt*.

## <a name="synclocktsync_"></a><a name="sync"></a>SyncLockT::sync_

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Bemerkungen

Enthält die zugrunde liegende `SyncLockT` Ressource, die von der Klasse dargestellt wird.

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>SyncLockT::SyncLockT

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein rvalue-Verweis `SyncLockT` auf ein anderes Objekt.

*Sync*<br/>
Ein Verweis `SyncLockWithStatusT` auf ein anderes Objekt.

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der Klasse `SyncLockT`.

Der erste Konstruktor initialisiert `SyncLockT` das `SyncLockT` aktuelle Objekt aus einem anderen Objekt, `SyncLockT` das durch den Parameter *andere*angegeben wird, und macht dann das andere Objekt ungültig. Der zweite Konstruktor ist `protected`, und `SyncLockT` initialisiert das aktuelle Objekt in einen ungültigen Zustand.

## <a name="synclocktunlock"></a><a name="unlock"></a>SyncLockT::Entsperren

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
void Unlock();
```

### <a name="remarks"></a>Bemerkungen

Gibt die Steuerung der Ressource `SyncLockT` frei, die sich im Besitz des aktuellen Objekts befindet.
