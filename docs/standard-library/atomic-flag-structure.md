---
title: atomic_flag-Struktur
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ad4b6dcaf6db1a8abe5b81b4d630e84b54fbaa63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376871"
---
# <a name="atomic_flag-structure"></a>atomic_flag-Struktur

Beschreibt ein Objekt, das atomar ein **bool-Flag** festlegt und löscht. Vorgänge auf atomischen Flags sind immer sperrenfrei.

## <a name="syntax"></a>Syntax

```cpp
struct atomic_flag;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Klar](#clear)|Legt das gespeicherte Flag auf **false**fest.|
|[test_and_set](#test_and_set)|Legt das gespeicherte Flag auf **true** fest und gibt den ursprünglichen Flagwert zurück.|

## <a name="remarks"></a>Bemerkungen

`atomic_flag`-Objekte können den Nicht-Member-Funktionen [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) und [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit) übergeben werden. Sie können mithilfe des `ATOMIC_FLAG_INIT`-Werts initialisiert werden.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<atomic>

**Namespace:** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag::klar

Legt das **bool-Flag** `*this` fest, das innerhalb der angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen in **false**gespeichert ist.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parameter

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag::test_and_set

Legt das **bool-Flag** `*this` fest, das innerhalb der angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen in **true**gespeichert ist.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parameter

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Anfangswert des im `*this` gespeicherten Flags.

## <a name="see-also"></a>Siehe auch

[\<atomare>](../standard-library/atomic.md)
