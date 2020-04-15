---
title: HANDLETraits-Struktur
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
ms.openlocfilehash: 604098cd3289722767117910d6e44e272dcb8b77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371444"
---
# <a name="handletraits-structure"></a>HANDLETraits-Struktur

Definiert allgemeine Merkmale eines Handles.

## <a name="syntax"></a>Syntax

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name   | BESCHREIBUNG
------ | ---------------------
`Type` | Ein Synonym für HANDLE.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                              | BESCHREIBUNG
------------------------------------------------- | -----------------------------
[HANDLETraits::Schließen](#close)                     | Schließt das angegebene Handle.
[HANDLETraits::GetInvalidValue](#getinvalidvalue) | Stellt ein ungültiges Handle dar.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HANDLETraits`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="handletraitsclose"></a><a name="close"></a>HANDLETraits::Schließen

Schließt das angegebene Handle.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Das zu schließende Handle.

### <a name="return-value"></a>Rückgabewert

**true,** wenn Handle *h* erfolgreich geschlossen wurde; andernfalls **false**.

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLETraits::GetInvalidValue

Stellt ein ungültiges Handle dar.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer INVALID_HANDLE_VALUE zurück. (INVALID_HANDLE_VALUE wird durch Windows definiert.)
