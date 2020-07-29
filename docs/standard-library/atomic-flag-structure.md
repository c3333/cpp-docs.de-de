---
title: atomic_flag-Struktur
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ff60e05c7d14104e164e8251a9146f8b0d0dcde3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203922"
---
# <a name="atomic_flag-structure"></a>atomic_flag-Struktur

Beschreibt ein Objekt, das ein Flag atomisch festlegt und löscht **`bool`** . Vorgänge auf atomischen Flags sind immer sperrenfrei.

## <a name="syntax"></a>Syntax

```cpp
struct atomic_flag;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Löschen](#clear)|Legt das gespeicherte Flag auf fest **`false`** .|
|[test_and_set](#test_and_set)|Legt das gespeicherte Flag auf fest **`true`** und gibt den ursprünglichen Flagwert zurück.|

## <a name="remarks"></a>Bemerkungen

`atomic_flag`-Objekte können den Nicht-Member-Funktionen [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) und [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit) übergeben werden. Sie können mithilfe des `ATOMIC_FLAG_INIT`-Werts initialisiert werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<atomic>

**Namespace:** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag:: Clear

Legt das **`bool`** in gespeicherte-Flag **`*this`** **`false`** innerhalb der angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen auf fest.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parameter

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag:: test_and_set

Legt das **`bool`** in gespeicherte-Flag **`*this`** **`true`** innerhalb der angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen auf fest.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parameter

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Anfangswert des Flags, das in gespeichert wird **`*this`** .

## <a name="see-also"></a>Weitere Informationen

[\<atomic>](../standard-library/atomic.md)
