---
title: SyncLockWithStatusT-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 77bcb8336e4650de7ed01a067fa1bdd7ec0ba3e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374262"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parameter

*SyncTraits*<br/>
Ein Typ, der exklusiven oder freigegebenen Besitz einer Ressource übernehmen kann.

## <a name="remarks"></a>Bemerkungen

Stellt einen Typ dar, der exklusiven oder freigegebenen Besitz einer Ressource übernehmen kann.

Die `SyncLockWithStatusT` Klasse wird verwendet, um die [Mutex-](mutex-class.md) und [Semaphore-Klassen](semaphore-class.md) zu implementieren.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                             | BESCHREIBUNG
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Initialisiert eine neue Instanz der Klasse `SyncLockWithStatusT`.

### <a name="protected-constructors"></a>Geschützte Konstruktoren

Name                                                             | BESCHREIBUNG
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Initialisiert eine neue Instanz der Klasse `SyncLockWithStatusT`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                         | BESCHREIBUNG
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::GetStatus](#getstatus) | Ruft den Wartestatus des `SyncLockWithStatusT` aktuellen Objekts ab.
[SyncLockWithStatusT::IsLocked](#islocked)   | Gibt an, `SyncLockWithStatusT` ob das aktuelle Objekt eigentümer eine Ressource ist. das heißt, `SyncLockWithStatusT` das Objekt ist *gesperrt*.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                                    | BESCHREIBUNG
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | Hält das Ergebnis des zugrunde liegenden Wartevorgangs nach einem `SyncLockWithStatusT` Sperrvorgang für ein Objekt basierend auf dem aktuellen Objekt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>SyncLockWithStatusT::GetStatus

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis eines Wartevorgangs für das `SyncLockWithStatusT` Objekt, das auf der Klasse basiert, z. B. [mutex](mutex-class.md) oder [Semaphore](semaphore-class.md). Null (0) gibt an, dass der Wartevorgang den signalisierten Zustand zurückgegeben hat. Andernfalls ist ein anderer Zustand aufgetreten, z. B. der Timeoutwert verstrichen.

### <a name="remarks"></a>Bemerkungen

Ruft den Wartestatus des `SyncLockWithStatusT` aktuellen Objekts ab.

Die GetStatus()-Funktion ruft den Wert des zugrunde liegenden [status_](#status) Datenmembers ab. Wenn ein Objekt, `SyncLockWithStatusT` das auf der Klasse basiert, einen Sperrvorgang ausführt, wartet das Objekt zuerst darauf, dass das Objekt verfügbar wird. Das Ergebnis dieses Wartevorgangs `status_` wird im Datenmember gespeichert. Die möglichen Werte `status_` des Datenelements sind die Rückgabewerte des Wartevorgangs. Weitere Informationen finden Sie unter `WaitForSingleObjectEx()` den Rückgabewerten der Funktion in der MSDN-Bibliothek.

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>SyncLockWithStatusT::IsLocked

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt an, `SyncLockWithStatusT` ob das aktuelle Objekt eigentümer eine Ressource ist. das heißt, `SyncLockWithStatusT` das Objekt ist *gesperrt*.

### <a name="return-value"></a>Rückgabewert

**true,** `SyncLockWithStatusT` wenn das Objekt gesperrt ist; andernfalls **false**.

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>SyncLockWithStatusT::status_

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Bemerkungen

Hält das Ergebnis des zugrunde liegenden Wartevorgangs nach einem `SyncLockWithStatusT` Sperrvorgang für ein Objekt basierend auf dem aktuellen Objekt.

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Ein rvalue-Verweis `SyncLockWithStatusT` auf ein anderes Objekt.

*Sync*<br/>
Ein Verweis `SyncLockWithStatusT` auf ein anderes Objekt.

*Status*<br/>
Der Wert des [status_](#status) Datenmember des *anderen* Parameters oder des *Synchronisierungsparameters.*

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der Klasse `SyncLockWithStatusT`.

Der erste Konstruktor initialisiert `SyncLockWithStatusT` das `SyncLockWithStatusT` aktuelle Objekt aus einem anderen, durch `SyncLockWithStatusT` den Parameter *anderen*angegebenen , und macht dann das andere Objekt ungültig. Der zweite Konstruktor ist `protected`, und `SyncLockWithStatusT` initialisiert das aktuelle Objekt in einen ungültigen Zustand.
