---
title: IsSame-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
ms.openlocfilehash: 8c209d5a8d2a35f2643e90e5595d86f41519f30b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216556"
---
# <a name="issame-structure"></a>IsSame-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>Parameter

*T1*<br/>
Ein Typ.

*T2*<br/>
Ein anderer Typ.

## <a name="remarks"></a>Bemerkungen

Testet, ob ein angegebener Typ mit einem anderen angegebenen Typ identisch ist.

## <a name="members"></a>Member

### <a name="public-constants"></a>Öffentliche Konstanten

Name                    | BESCHREIBUNG
----------------------- | --------------------------------------------------
[IsSame:: Value](#value) | Gibt an, ob ein Typ mit einem anderen identisch ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IsSame`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** intern. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="issamevalue"></a><a name="value"></a>IsSame:: Value

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

### <a name="remarks"></a>Bemerkungen

Gibt an, ob ein Typ mit einem anderen identisch ist.

`value`Gibt an **`true`** , ob die Vorlagen Parameter identisch sind und **`false`** ob die Vorlagen Parameter unterschiedlich sind.
