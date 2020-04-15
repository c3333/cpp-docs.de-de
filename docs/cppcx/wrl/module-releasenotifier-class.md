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
ms.openlocfilehash: f314d09c443d0d284e3a821b5c879bfb74baf812
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371276"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier-Klasse

Ruft einen Ereignishandler auf, wenn das letzte Objekt in einem Modul freigegeben wird.

## <a name="syntax"></a>Syntax

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                                                | BESCHREIBUNG
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Modul::ReleaseNotifier::'ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Deinitialisiert die aktuelle Instanz `Module::ReleaseNotifier` der Klasse.
[Modul::ReleaseNotifier::ReleaseNotifier](#releasenotifier-releasenotifier)        | Initialisiert eine neue Instanz der Klasse `Module::ReleaseNotifier`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                         | BESCHREIBUNG
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Modul::ReleaseNotifier::Invoke](#releasenotifier-invoke)   | Ruft bei implementierung einen Ereignishandler auf, wenn das letzte Objekt in einem Modul freigegeben wird.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Löscht das `Module::ReleaseNotifier` aktuelle Objekt, wenn das Objekt mit dem Parameter **true**erstellt wurde.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ReleaseNotifier`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a>Modul::ReleaseNotifier::'ReleaseNotifier

Deinitialisiert die aktuelle Instanz `Module::ReleaseNotifier` der Klasse.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a>Modul::ReleaseNotifier::Invoke

Ruft bei implementierung einen Ereignishandler auf, wenn das letzte Objekt in einem Modul freigegeben wird.

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a>Modul::ReleaseNotifier::Release

Löscht das `Module::ReleaseNotifier` aktuelle Objekt, wenn das Objekt mit dem Parameter **true**erstellt wurde.

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a>Modul::ReleaseNotifier::ReleaseNotifier

Initialisiert eine neue Instanz der Klasse `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parameter

*Release*<br/>
`true`, um diese `Release` Instanz zu löschen, wenn die Methode aufgerufen wird; `false` , um diese Instanz nicht zu löschen.
