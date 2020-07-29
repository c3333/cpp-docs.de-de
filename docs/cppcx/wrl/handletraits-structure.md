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
ms.openlocfilehash: c04e53789fd737b12ca10ef2c279a05fb43f5925
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212994"
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
`Type` | Ein Synonym für handle.

### <a name="public-methods"></a>Öffentliche Methoden

name                                              | BESCHREIBUNG
------------------------------------------------- | -----------------------------
[Lenker:: Close](#close)                     | Schließt das angegebene Handle.
[Lenker Merkmale:: getinvalidvalue](#getinvalidvalue) | Stellt ein ungültiges Handle dar.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HANDLETraits`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrappers:: Lenker Merkmale

## <a name="handletraitsclose"></a><a name="close"></a>Lenker:: Close

Schließt das angegebene Handle.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Parameter

*h*<br/>
Das Handle, das geschlossen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Handle *h* erfolgreich geschlossen wurde. andernfalls **`false`** .

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>Lenker Merkmale:: getinvalidvalue

Stellt ein ungültiges Handle dar.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer INVALID_HANDLE_VALUE zurück. (INVALID_HANDLE_VALUE wird von Windows definiert.)
