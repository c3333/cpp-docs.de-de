---
title: CriticalSectionTraits-Struktur
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: 05c93bf6a2765bd11489075067c627ab3c3ab691
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372581"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits-Struktur

Spezialisiert auf `CriticalSection` ein Objekt, um entweder einen ungültigen kritischen Abschnitt oder eine Funktion zum Freigeben eines kritischen Abschnitts zu unterstützen.

## <a name="syntax"></a>Syntax

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name   | BESCHREIBUNG
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | Eine, `typedef` die einen Zeiger auf einen kritischen Abschnitt definiert. `Type` ist als `typedef CRITICAL_SECTION* Type;` definiert.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                       | BESCHREIBUNG
---------------------------------------------------------- | -----------------
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | Speziell ist `CriticalSection` eine Vorlage so, dass die Vorlage immer ungültig ist.
[CriticalSectionTraits::Entsperren](#unlock)                   | Spezialisiert auf `CriticalSection` eine Vorlage, sodass sie das Freigeben des Besitzes des angegebenen kritischen Abschnittsobjekts unterstützt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CriticalSectionTraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

Speziell ist `CriticalSection` eine Vorlage so, dass die Vorlage immer ungültig ist.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer einen Zeiger auf einen ungültigen kritischen Abschnitt zurück.

### <a name="remarks"></a>Bemerkungen

Der `Type` Modifikator `typedef CRITICAL_SECTION* Type;`ist definiert als .

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>CriticalSectionTraits::Entsperren

Spezialisiert auf `CriticalSection` eine Vorlage, sodass sie das Freigeben des Besitzes des angegebenen kritischen Abschnittsobjekts unterstützt.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parameter

*Cs*<br/>
Ein Zeiger auf ein kritisches Abschnittsobjekt.

### <a name="remarks"></a>Bemerkungen

Der `Type` Modifikator `typedef CRITICAL_SECTION* Type;`ist definiert als .

Weitere Informationen finden Sie unter **LeaveCriticalSection-Funktion** im Abschnitt **Synchronisierungsfunktionen** in der Windows-API-Dokumentation.
