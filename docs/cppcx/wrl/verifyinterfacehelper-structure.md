---
title: VerifyInterfaceHelper-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: 09c2cc7e08e2dc0e8df42c64d285c37627c5925a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374246"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper-Struktur

Unterstützt die Windows Runtime C++-Vorlagenbibliotheksinfrastruktur und ist nicht für die direkte Verwendung aus Ihrem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Parameter

*Ⅰ*<br/>
Eine Schnittstelle zum Überprüfen.

*isWinRTInterface*

## <a name="remarks"></a>Bemerkungen

Überprüft, ob die vom Vorlagenparameter angegebene Schnittstelle bestimmte Anforderungen erfüllt.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

Name                                            | BESCHREIBUNG
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify-Methode](#verify) | Überprüft, ob die vom aktuellen Vorlagenparameter angegebene Schnittstelle bestimmte Anforderungen erfüllt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`VerifyInterfaceHelper`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="verifyinterfacehelperverify"></a><a name="verify"></a>VerifyInterfaceHelper::Verify

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
static void Verify();
```

### <a name="remarks"></a>Bemerkungen

Überprüft, ob die vom aktuellen Vorlagenparameter angegebene Schnittstelle bestimmte Anforderungen erfüllt.
