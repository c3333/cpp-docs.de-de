---
title: SemaphoreTraits-Struktur
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: 11719576c9fc7b23f4cd318ee1b3ed9ca3f5edaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360738"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits-Struktur

Definiert allgemeine Merkmale `Semaphore` eines Objekts.

## <a name="syntax"></a>Syntax

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

Name                               | BESCHREIBUNG
---------------------------------- | --------------------------------------
[SemaphoreTraits::Entsperren](#unlock) | Gibt die Steuerung einer freigegebenen Ressource frei.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="semaphoretraitsunlock"></a><a name="unlock"></a>SemaphoreTraits::Entsperren

Gibt die Steuerung einer freigegebenen Ressource frei.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Handle für `Semaphore` ein Objekt.

### <a name="remarks"></a>Bemerkungen

Wenn der Entsperrvorgang `Unlock()` fehlschlägt, wird ein Fehler ausgesendet, der auf die Ursache des Fehlers hinweist.
