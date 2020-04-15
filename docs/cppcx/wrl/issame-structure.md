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
ms.openlocfilehash: fcaf33309521b44163022e0ffa9b1e03e53e2551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371344"
---
# <a name="issame-structure"></a>IsSame-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

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
[IsSame::Wert](#value) | Gibt an, ob ein Typ mit einem anderen identisch ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IsSame`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="issamevalue"></a><a name="value"></a>IsSame::Wert

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

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

`value`ist **true,** wenn die Vorlagenparameter identisch sind, und **false,** wenn die Vorlagenparameter unterschiedlich sind.
