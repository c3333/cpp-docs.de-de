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
ms.openlocfilehash: 4b7dbe8ae1648e4185a9eb1e1142df4a3869aa2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216543"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parameter

*Syncmerkmalen*<br/>
Ein Typ, der einen exklusiven oder freigegebenen Besitz einer Ressource annehmen kann.

## <a name="remarks"></a>Bemerkungen

Stellt einen Typ dar, der einen exklusiven oder freigegebenen Besitz einer Ressource annehmen kann.

Die `SyncLockWithStatusT` -Klasse wird verwendet, um die [Mutex](mutex-class.md) -und [Semaphore](semaphore-class.md) -Klassen zu implementieren.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                             | BESCHREIBUNG
---------------------------------------------------------------- | --------------------------------------------------------------
[Synclockwithstatust:: synclockwithstatust](#synclockwithstatust) | Initialisiert eine neue Instanz der `SyncLockWithStatusT`-Klasse.

### <a name="protected-constructors"></a>Geschützte Konstruktoren

Name                                                             | BESCHREIBUNG
---------------------------------------------------------------- | --------------------------------------------------------------
[Synclockwithstatust:: synclockwithstatust](#synclockwithstatust) | Initialisiert eine neue Instanz der `SyncLockWithStatusT`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

name                                         | BESCHREIBUNG
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[Synclockwithstatust:: GetStatus](#getstatus) | Ruft den Wartestatus des aktuellen- `SyncLockWithStatusT` Objekts ab.
[Synclockwithstatust:: IsLocked](#islocked)   | Gibt an, ob das aktuelle- `SyncLockWithStatusT` Objekt eine Ressource besitzt, d `SyncLockWithStatusT` . h., das Objekt ist *gesperrt*.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                                    | BESCHREIBUNG
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[Synclockwithstatust:: status_](#status) | Enthält das Ergebnis des zugrunde liegenden warte Vorgangs nach einem Sperr Vorgang für ein-Objekt, das auf dem aktuellen- `SyncLockWithStatusT` Objekt basiert.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrappers::D etails

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>Synclockwithstatust:: GetStatus

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis eines warte Vorgangs auf dem-Objekt, das auf der- `SyncLockWithStatusT` Klasse basiert, z. b. ein [Mutex](mutex-class.md) oder [Semaphore](semaphore-class.md). NULL (0) gibt an, dass der Warte Vorgang den signalisierten Zustand zurückgegeben hat. Andernfalls ist ein anderer Zustand aufgetreten, z. b. der verstrichene Timeout Wert.

### <a name="remarks"></a>Bemerkungen

Ruft den Wartestatus des aktuellen- `SyncLockWithStatusT` Objekts ab.

Die GetStatus ()-Funktion Ruft den Wert des zugrunde liegenden [status_](#status) Datenmembers ab. Wenn ein-Objekt, das auf der- `SyncLockWithStatusT` Klasse basiert, einen Sperr Vorgang ausführt, wartet das-Objekt zunächst, bis das-Objekt verfügbar wird. Das Ergebnis dieses Warte Vorgangs wird im `status_` Datenmember gespeichert. Mögliche Werte für den `status_` Datenmember sind die Rückgabewerte des warte Vorgangs. Weitere Informationen finden Sie in den Rückgabe Werten der [`WaitForSingleObjectEx`](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobjectex) Funktion.

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>Synclockwithstatust:: IsLocked

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt an, ob das aktuelle- `SyncLockWithStatusT` Objekt eine Ressource besitzt, d `SyncLockWithStatusT` . h., das Objekt ist *gesperrt*.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das `SyncLockWithStatusT` Objekt gesperrt ist, andernfalls **`false`** .

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>Synclockwithstatust:: status_

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Bemerkungen

Enthält das Ergebnis des zugrunde liegenden warte Vorgangs nach einem Sperr Vorgang für ein-Objekt, das auf dem aktuellen- `SyncLockWithStatusT` Objekt basiert.

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>Synclockwithstatust:: synclockwithstatust

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

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

*außer*<br/>
Ein rvalue-Verweis auf ein anderes `SyncLockWithStatusT` Objekt.

*PPEN*<br/>
Ein Verweis auf ein anderes `SyncLockWithStatusT` Objekt.

*status*<br/>
Der Wert des [status_](#status) Datenmembers des *anderen* Parameters oder des *Sync* -Parameters.

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der `SyncLockWithStatusT`-Klasse.

Der erste Konstruktor initialisiert das aktuelle- `SyncLockWithStatusT` Objekt von einem anderen `SyncLockWithStatusT` , das durch einen *anderen*Parameter angegeben wird, und erklärt dann das andere-Objekt für ungültig `SyncLockWithStatusT` . Der zweite Konstruktor ist **`protected`** , und initialisiert das aktuelle- `SyncLockWithStatusT` Objekt in einen ungültigen Zustand.
