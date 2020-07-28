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
ms.openlocfilehash: 3573cad21734a97629cbc12b76d73b99024cbc2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220508"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits-Struktur

Spezialisiert ein- `CriticalSection` Objekt, um entweder einen ungültigen kritischen Abschnitt oder eine Funktion zum Freigeben eines kritischen Abschnitts zu unterstützen.

## <a name="syntax"></a>Syntax

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name   | BESCHREIBUNG
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | Ein **`typedef`** , der einen Zeiger auf einen kritischen Abschnitt definiert. `Type` ist als `typedef CRITICAL_SECTION* Type;` definiert.

### <a name="public-methods"></a>Öffentliche Methoden

name                                                       | BESCHREIBUNG
---------------------------------------------------------- | -----------------
[Criticalsectiontrait:: getinvalidvalue](#getinvalidvalue) | Spezialisiert eine `CriticalSection` Vorlage, sodass die Vorlage immer ungültig ist.
[Criticalsectiontrait:: Unlock](#unlock)                   | Spezialisiert eine `CriticalSection` Vorlage, sodass Sie die Freigabe des angegebenen kritischen Abschnitts Objekts unterstützt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CriticalSectionTraits`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrappers:: Lenker Merkmale

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>Criticalsectiontrait:: getinvalidvalue

Spezialisiert eine `CriticalSection` Vorlage, sodass die Vorlage immer ungültig ist.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer einen Zeiger auf einen ungültigen kritischen Abschnitt zurück.

### <a name="remarks"></a>Bemerkungen

Der- `Type` Modifizierer ist als definiert `typedef CRITICAL_SECTION* Type;` .

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>Criticalsectiontrait:: Unlock

Spezialisiert eine `CriticalSection` Vorlage, sodass Sie die Freigabe des angegebenen kritischen Abschnitts Objekts unterstützt.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parameter

*CS*<br/>
Ein Zeiger auf ein kritisches Abschnitts Objekt.

### <a name="remarks"></a>Bemerkungen

Der- `Type` Modifizierer ist als definiert `typedef CRITICAL_SECTION* Type;` .

Weitere Informationen finden Sie unter **Funktion "LeaveCriticalSection** " im Abschnitt **Synchronisierungs Funktionen** der Windows-API-Dokumentation.
