---
title: RuntimeClassFlags-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 9fed5bb31b077288495a78aefcbd8401b3520bb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367228"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags-Struktur

Enthält den Typ für eine Instanz einer [RuntimeClass](runtimeclass-class.md).

## <a name="syntax"></a>Syntax

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parameter

*Flaggen*<br/>
Ein [RuntimeClassType-Enumerationswert.](runtimeclasstype-enumeration.md)

## <a name="members"></a>Member

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[RuntimeClassFlags::value-Konstante](#value-constant)|Enthält einen [RuntimeClassType-Enumerationswert.](runtimeclasstype-enumeration.md)|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`RuntimeClassFlags`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL

## <a name="runtimeclassflagsvalue-constant"></a><a name="value-constant"></a>RuntimeClassFlags::value Konstante

Ein Feld, das einen [RuntimeClassType-Enumerationswert](runtimeclasstype-enumeration.md) enthält.

```cpp
static const unsigned int value = flags;
```
