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
ms.openlocfilehash: 5fc1b8965bf8bf2f86dd30f2195fa825f85f6d7e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865586"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier-Klasse

Ruft einen Ereignishandler auf, wenn das letzte-Objekt in einem Modul freigegeben wird.

## <a name="syntax"></a>Syntax

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                                                | BESCHREIBUNG
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module:: releasenotifier:: ~ releasenotifier](#releasenotifier-tilde-releasenotifier) | Deinitialisiert die aktuelle Instanz der `Module::ReleaseNotifier`-Klasse.
[Module:: releasenotifier:: releasenotifier](#releasenotifier-releasenotifier)        | Initialisiert eine neue Instanz der Klasse `Module::ReleaseNotifier`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                         | BESCHREIBUNG
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module:: releasenotifier:: aufrufen](#releasenotifier-invoke)   | Bei Implementierung wird ein Ereignishandler aufgerufen, wenn das letzte-Objekt in einem Modul freigegeben wird.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Löscht das aktuelle `Module::ReleaseNotifier` Objekt, wenn das Objekt mit dem Parameter " **true**" erstellt wurde.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ReleaseNotifier`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module:: releasenotifier:: ~ releasenotifier

Deinitialisiert die aktuelle Instanz der `Module::ReleaseNotifier`-Klasse.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module:: releasenotifier:: aufrufen

Bei Implementierung wird ein Ereignishandler aufgerufen, wenn das letzte-Objekt in einem Modul freigegeben wird.

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module:: releasenotifier:: Release

Löscht das aktuelle `Module::ReleaseNotifier` Objekt, wenn das Objekt mit dem Parameter " **true**" erstellt wurde.

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module:: releasenotifier:: releasenotifier

Initialisiert eine neue Instanz der Klasse `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parameter

*release*<br/>
`true`, um diese Instanz zu löschen, wenn die `Release`-Methode aufgerufen wird. `false`, diese Instanz nicht zu löschen.
