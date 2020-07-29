---
title: HANDLENullTraits-Struktur
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
ms.openlocfilehash: a7ce730b8d723a839c5b509c825cff84111ca613
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226918"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits-Struktur

Definiert allgemeine Merkmale eines nicht initialisierten Handles.

## <a name="syntax"></a>Syntax

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name   | Beschreibung
------ | ---------------------
`Type` | Ein Synonym für handle.

### <a name="public-methods"></a>Öffentliche Methoden

name                                                  | Beschreibung
----------------------------------------------------- | -----------------------------
[Handlenullmerkmalen:: Close](#close)                     | Schließt das angegebene Handle.
[Handlenullmerkmalen:: getinvalidvalue](#getinvalidvalue) | Stellt ein ungültiges Handle dar.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HANDLENullTraits`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrappers:: Lenker Merkmale

## <a name="handlenulltraitsclose"></a><a name="close"></a>Handlenullmerkmalen:: Close

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

## <a name="handlenulltraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>Handlenullmerkmalen:: getinvalidvalue

Stellt ein ungültiges Handle dar.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer zurück **`nullptr`** .
