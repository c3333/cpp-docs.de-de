---
title: SRWLockSharedTraits-Struktur
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
ms.openlocfilehash: 0dc43d4b9c16145ed7a5abe03cddb598c59b1e94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374300"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits-Struktur

Beschreibt die gemeinsamen `SRWLock` Merkmale der Klasse im Modus der gemeinsamen Sperre.

## <a name="syntax"></a>Syntax

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name   | BESCHREIBUNG
------ | --------------------------------------------------------------------------
`Type` | Synonym für einen Zeiger auf die [SRWLOCK-Klasse.](srwlock-class.md)

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                     | BESCHREIBUNG
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | Ruft ein `SRWLockSharedTraits` Objekt ab, das immer ungültig ist.
[SRWLockSharedTraits::Entsperren](#unlock)                   | Gibt die exklusive `SRWLock` Steuerung des angegebenen Objekts frei.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SRWLockSharedTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="srwlocksharedtraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

Ruft ein `SRWLockSharedTraits` Objekt ab, das immer ungültig ist.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle `SRWLockSharedTraits` für ein Objekt.

## <a name="srwlocksharedtraitsunlock"></a><a name="unlock"></a>SRWLockSharedTraits::Entsperren

Gibt die exklusive `SRWLock` Steuerung des angegebenen Objekts frei.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parameter

*srwlock*<br/>
Ein Handle `SRWLock` für ein Objekt.
