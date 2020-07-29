---
title: Module::ReleaseNotifier-Klasse
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
ms.openlocfilehash: 25fbb23ee7ecb7e55377aed74effe8bfa43a1597
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218363"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier-Klasse

Ruft einen Ereignishandler auf, wenn das letzte-Objekt in einem Modul freigegeben wird.

## <a name="syntax"></a>Syntax

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                                                | BESCHREIBUNG
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module:: releasenotifier:: ~ releasenotifier](#releasenotifier-tilde-releasenotifier) | Deinitialisiert die aktuelle Instanz der- `Module::ReleaseNotifier` Klasse.
[Module:: releasenotifier:: releasenotifier](#releasenotifier-releasenotifier)        | Initialisiert eine neue Instanz der `Module::ReleaseNotifier`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

name                                                         | BESCHREIBUNG
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module:: releasenotifier:: aufrufen](#releasenotifier-invoke)   | Bei Implementierung wird ein Ereignishandler aufgerufen, wenn das letzte-Objekt in einem Modul freigegeben wird.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Löscht das aktuelle- `Module::ReleaseNotifier` Objekt, wenn das-Objekt mit einem Parameter von erstellt wurde **`true`** .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ReleaseNotifier`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a>Module:: releasenotifier:: ~ releasenotifier

Deinitialisiert die aktuelle Instanz der- `Module::ReleaseNotifier` Klasse.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a>Module:: releasenotifier:: aufrufen

Bei Implementierung wird ein Ereignishandler aufgerufen, wenn das letzte-Objekt in einem Modul freigegeben wird.

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a>Module:: releasenotifier:: Release

Löscht das aktuelle- `Module::ReleaseNotifier` Objekt, wenn das-Objekt mit einem Parameter von erstellt wurde **`true`** .

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a>Module:: releasenotifier:: releasenotifier

Initialisiert eine neue Instanz der `Module::ReleaseNotifier`-Klasse.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parameter

*Abgabe*<br/>
**`true`**, um diese Instanz zu löschen, wenn die- `Release` Methode aufgerufen wird,, **`false`** um diese Instanz nicht zu löschen.
