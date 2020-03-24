---
title: Microsoft::WRL::Wrappers::HandleTraits-Namespace
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: b19cc426fc7c1b4fc6ec0638730d59998f8c108a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213732"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits-Namespace

Beschreibt Merkmale allgemeiner handle-basierter Ressourcentypen.

## <a name="syntax"></a>Syntax

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Members

### <a name="structures"></a>Strukturen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CriticalSectionTraits-Struktur](criticalsectiontraits-structure.md)|Spezialisiert ein `CriticalSection` Objekt, um entweder einen ungültigen kritischen Abschnitt oder eine Funktion zum Freigeben eines kritischen Abschnitts zu unterstützen.|
|[EventTraits-Struktur](eventtraits-structure.md)|Definiert Merkmale eines `Event` Class-Handles.|
|[FileHandleTraits-Struktur](filehandletraits-structure.md)|Definiert die Merkmale eines Datei Handles.|
|[HANDLENullTraits-Struktur](handlenulltraits-structure.md)|Definiert allgemeine Merkmale eines nicht initialisierten Handles.|
|[HANDLETraits-Struktur](handletraits-structure.md)|Definiert allgemeine Merkmale eines Handles.|
|[MutexTraits-Struktur](mutextraits-structure.md)|Definiert allgemeine Merkmale der [Mutex](mutex-class.md) -Klasse.|
|[SemaphoreTraits-Struktur](semaphoretraits-structure.md)|Definiert allgemeine Merkmale eines Semaphore-Objekts.|
|[SRWLockExclusiveTraits-Struktur](srwlockexclusivetraits-structure.md)|Beschreibt allgemeine Merkmale der `SRWLock`-Klasse im exklusiven Sperrmodus.|
|[SRWLockSharedTraits-Struktur](srwlocksharedtraits-structure.md)|Beschreibt allgemeine Merkmale der `SRWLock`-Klasse im Modus für freigegebene Sperren.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrapper

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Wrappers-Namespace](microsoft-wrl-wrappers-namespace.md)
