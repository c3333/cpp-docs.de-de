---
title: '&lt;atomic&gt;-Funktionen'
ms.date: 07/11/2018
f1_keywords:
- atomic/std::atomic_compare_exchange_strong
- atomic/std::atomic_compare_exchange_strong_explicit
- atomic/std::atomic_compare_exchange_weak
- atomic/std::atomic_compare_exchange_weak_explicit
- atomic/std::atomic_exchange
- atomic/std::atomic_exchange_explicit
- atomic/std::atomic_fetch_add
- atomic/std::atomic_fetch_add_explicit
- atomic/std::atomic_fetch_and
- atomic/std::atomic_fetch_and_explicit
- atomic/std::atomic_fetch_or
- atomic/std::atomic_fetch_or_explicit
- atomic/std::atomic_fetch_sub
- atomic/std::atomic_fetch_sub_explicit
- atomic/std::atomic_fetch_xor
- atomic/std::atomic_fetch_xor_explicit
- atomic/std::atomic_flag_clear
- atomic/std::atomic_flag_clear_explicit
- atomic/std::atomic_flag_test_and_set
- atomic/std::atomic_flag_test_and_set_explicit
- atomic/std::atomic_init
- atomic/std::atomic_is_lock_free
- atomic/std::atomic_load
- atomic/std::atomic_load_explicit
- atomic/std::atomic_signal_fence
- atomic/std::atomic_store
- atomic/std::atomic_store_explicit
- atomic/std::atomic_thread_fence
- atomic/std::kill_dependency
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
helpviewer_keywords:
- std::atomic_compare_exchange_strong [C++]
- std::atomic_compare_exchange_strong_explicit [C++]
- std::atomic_compare_exchange_weak [C++]
- std::atomic_compare_exchange_weak_explicit [C++]
- std::atomic_exchange [C++]
- std::atomic_exchange_explicit [C++]
- std::atomic_fetch_add [C++]
- std::atomic_fetch_add_explicit [C++]
- std::atomic_fetch_and [C++]
- std::atomic_fetch_and_explicit [C++]
- std::atomic_fetch_or [C++]
- std::atomic_fetch_or_explicit [C++]
- std::atomic_fetch_sub [C++]
- std::atomic_fetch_sub_explicit [C++]
- std::atomic_fetch_xor [C++]
- std::atomic_fetch_xor_explicit [C++]
- std::atomic_flag_clear [C++]
- std::atomic_flag_clear_explicit [C++]
- std::atomic_flag_test_and_set [C++]
- std::atomic_flag_test_and_set_explicit [C++]
- std::atomic_init [C++]
- std::atomic_is_lock_free [C++]
- std::atomic_load [C++]
- std::atomic_load_explicit [C++]
- std::atomic_signal_fence [C++]
- std::atomic_store [C++]
- std::atomic_store_explicit [C++]
- std::atomic_thread_fence [C++]
- std::kill_dependency [C++]
ms.openlocfilehash: b6d03da446e4a3bae02f662e5b106bd5de534d0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376899"
---
# <a name="ltatomicgt-functions"></a>&lt;atomic&gt;-Funktionen

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

Führt einen atomischen Vergleichs- und Austausch-Vorgang aus.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein *atomares* Objekt, das einen Wert vom Typ `Ty`speichert.

*Exp*\
Ein Zeiger auf einen Wert des Typs `Ty`.

*Wert*\
Ein Wert vom Typ `Ty`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Werte gleich sind, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode wird ein atomischer Vergleichs- und Austauschvorgang ausgeführt, indem implizite `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)-Argumente verwendet werden. Weitere Informationen finden Sie unter [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

Führt einen *atomaren Vergleichs- und Austauschvorgang* aus.

```cpp
template <class T>
inline bool atomic_compare_exchange_strong_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Exp*\
Ein Zeiger auf einen Wert des Typs `Ty`.

*Wert*\
Ein Wert vom Typ `Ty`.

*Bestellung1*\
Erstes [memory_order](../standard-library/atomic-enums.md#memory_order_enum)-Argument.

*Bestellung2*\
Zweites `memory_order`-Argument. Der Wert von *Order2* kann nicht oder `memory_order_release` `memory_order_acq_rel`sein, er darf nicht stärker als der Wert von *Order1*sein.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Werte gleich sind, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Ein *atomarer Vergleichs- und Austauschvorgang* vergleicht den Wert, der in dem Objekt gespeichert ist, auf das von *Atom* verwiesen wird, mit dem Wert, auf den *Exp*zeigt. Wenn die Werte gleich sind, wird der Wert, der in dem Objekt gespeichert `read-modify-write` ist, auf das durch *Atom* verwiesen wird, durch *Wert* ersetzt, indem ein Vorgang verwendet wird und die Inanspruchlungseinschränkungen angewendet werden, die in *Order1*angegeben sind. Wenn die Werte nicht gleich sind, ersetzt der Vorgang den Wert, auf den von *Exp* verwiesen wird, durch den Wert, der in dem Objekt gespeichert ist, auf das von *Atom* verwiesen wird, und wendet die Speicherreihenfolgeeinschränkungen an, die in *Order2*angegeben sind.

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

Führt einen *schwachen atomischen Vergleichs- und Austauschvorgang* aus.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Exp*\
Ein Zeiger auf einen Wert des Typs `Ty`.

*Wert*\
Ein Wert vom Typ `Ty`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Werte gleich sind, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode wird ein *schwacher atomischer Vergleichs- und Austauschvorgang* ausgeführt, der über implizite `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)-Argumente verfügt. Weitere Informationen finden Sie unter [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

Führt einen *schwachen atomischen Vergleichs- und Austauschvorgang* aus.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Exp*\
Ein Zeiger auf einen Wert des Typs `Ty`.

*Wert*\
Ein Wert vom Typ `Ty`.

*Bestellung1*\
Erstes [memory_order](../standard-library/atomic-enums.md#memory_order_enum)-Argument.

*Bestellung2*\
Zweites `memory_order`-Argument. Der Wert von *Order2* kann nicht oder `memory_order_release` `memory_order_acq_rel`sein, noch kann er stärker als der Wert von *Order1*sein.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Werte gleich sind, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Sowohl die starken als auch die schwachen Geschmacksrichtungen eines *atomaren Vergleichs- und Austauschvorgangs* garantieren, dass sie den neuen Wert nicht speichern, wenn die erwarteten und aktuellen Werte nicht gleich sind. Der starke Geschmack garantiert, dass der neue Wert gespeichert wird, wenn die erwarteten und aktuellen Werte gleich sind. Der schwache Geschmack kann manchmal **false** zurückgeben und den neuen Wert nicht speichern, selbst wenn die aktuellen und erwarteten Werte gleich sind. Mit anderen Worten, die Funktion gibt **false**zurück, aber eine spätere Untersuchung des erwarteten Wertes könnte zeigen, dass sie sich nicht geändert hat und daher als gleich verglichen werden sollte.

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

Verwendet *Wert,* um den gespeicherten Wert von *Atom*zu ersetzen.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Wert*\
Ein Wert vom Typ `Ty`.

### <a name="return-value"></a>Rückgabewert

Der gespeicherte Wert von *Atom* vor dem Austausch.

### <a name="remarks"></a>Bemerkungen

Die `atomic_exchange` Funktion `read-modify-write` führt einen Vorgang aus, um den in *Atom* gespeicherten Wert mit *Wert*zu tauschen, indem `memory_order_seq_cst` [die memory_order](../standard-library/atomic-enums.md#memory_order_enum)verwendet wird.

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

Ersetzt den gespeicherten Wert von *Atom* durch *Value*.

```cpp
template <class Ty>
inline Ty atomic_exchange_explicit(
    volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_exchange_explicit(
    atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Wert*\
Ein Wert vom Typ `Ty`.

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der gespeicherte Wert von *Atom* vor dem Austausch.

### <a name="remarks"></a>Bemerkungen

Die `atomic_exchange_explicit` Funktion `read-modify-write` führt einen Vorgang aus, um den in *Atom* gespeicherten Wert *innerhalb*der Speichereinschränkungen, die durch *Order*angegeben sind, auszutauschen.

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

Fügt einem vorhandenen Wert einen in einem `atomic`-Objekt gespeicherten Wert hinzu.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Zeiger auf den Typ `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `ptrdiff_t`.

### <a name="return-value"></a>Rückgabewert

Der Wert des unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthaltenen Zeigers.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_add` Funktion `read-modify-write` führt einen Vorgang aus, um den gespeicherten `memory_order_seq_cst`Wert in *Atom*atomar *zu* erhöhen, indem die [Einschränkung memory_order](../standard-library/atomic-enums.md#memory_order_enum) verwendet wird.

Wenn der atomare `atomic_address`Typ ist , *hat Wert* den Typ, `ptrdiff_t` und der Vorgang behandelt den gespeicherten Zeiger als . `char *`

Dieser Vorgang wird auch bei Integraltypen überladen:

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a><a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

Fügt einem vorhandenen Wert einen in einem `atomic`-Objekt gespeicherten Wert hinzu.

```cpp
template <class T>
T* atomic_fetch_add_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_add_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Zeiger auf den Typ `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `ptrdiff_t`.

### <a name="return-value"></a>Rückgabewert

Der Wert des unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthaltenen Zeigers.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_add_explicit` Funktion `read-modify-write` führt einen Vorgang aus, um dem gespeicherten Wert in *Atom* `Order`atomar Einen *Wert* hinzuzufügen, innerhalb der [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen, die von angegeben werden.

Wenn der atomische Typ `atomic_address` ist, dann ist `Value` vom Typ `ptrdiff_t`, und der Vorgang behandelt den gespeicherten Zeiger als `char *`.

Dieser Vorgang wird auch bei Integraltypen überladen:

```cpp
integral atomic_fetch_add_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_add_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_and"></a><a name="atomic_fetch_and"></a>atomic_fetch_and

Führt ein bitweises `and` auf einem Wert und einem vorhandenen in einem `atomic`-Objekt gespeicherten Wert aus.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_and` Funktion `read-modify-write` führt einen Vorgang aus, um den `and` gespeicherten Wert von *Atom* durch einen `memory_order_seq_cst`bitweisen *Wert* und den aktuellen Wert, der in *Atom*gespeichert ist, mithilfe der [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkung zu ersetzen.

## <a name="atomic_fetch_and_explicit"></a><a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

Führt ein bitweises `and` eines Werts und einen vorhandenen in einem `atomic`-Objekt gespeicherten Wert aus.

```cpp
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_and_explicit` Funktion `read-modify-write` führt einen Vorgang aus, um den `and` gespeicherten Wert von *Atom* durch einen bitweisen *Wert* und den aktuellen Wert, der in *Atom*gespeichert ist, innerhalb der Speichereinschränkungen zu ersetzen, die durch *Order*angegeben werden.

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

Führt ein bitweises `or` auf einem Wert und einem vorhandenen in einem `atomic`-Objekt gespeicherten Wert aus.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_or` Funktion `read-modify-write` führt einen Vorgang aus, um den `or` gespeicherten Wert von *Atom* durch einen `memory_order_seq_cst`bitweisen *Wert* und den aktuellen Wert, der in *Atom*gespeichert ist, mit dem [memory_order](../standard-library/atomic-enums.md#memory_order_enum)zu ersetzen.

## <a name="atomic_fetch_or_explicit"></a><a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

Führt ein bitweises `or` auf einem Wert und einem vorhandenen in einem `atomic`-Objekt gespeicherten Wert aus.

```cpp
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_or_explicit` Funktion `read-modify-write` führt einen Vorgang aus, um den `or` gespeicherten Wert von *Atom* durch einen bitweisen *Wert* und den aktuellen Wert zu ersetzen, der in *Atom*gespeichert ist, innerhalb der [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen, die durch *Order*angegeben werden.

## <a name="atomic_fetch_sub"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub

Subtrahiert einen Wert von einem in einem `atomic`-Objekt vorhandenen Wert.

```cpp
template <class T>
T* atomic_fetch_sub(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;

template <class T>
T* atomic_fetch_sub(
    atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Zeiger auf den Typ `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `ptrdiff_t`.

### <a name="return-value"></a>Rückgabewert

Der Wert des unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthaltenen Zeigers.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_sub` Funktion `read-modify-write` führt einen Vorgang aus, um *den Wert* atomar vom gespeicherten Wert in *Atom*zu subtrahieren, indem `memory_order_seq_cst` [die memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkung verwendet wird.

Wenn der atomare `atomic_address`Typ ist , *hat Wert* den Typ, `ptrdiff_t` und der Vorgang behandelt den gespeicherten Zeiger als . `char *`

Dieser Vorgang wird auch bei Integraltypen überladen:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a><a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

Subtrahiert einen Wert von einem in einem `atomic`-Objekt vorhandenen Wert.

```cpp
template <class T>
T* atomic_fetch_sub_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_sub_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Zeiger auf den Typ `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `ptrdiff_t`.

### <a name="return-value"></a>Rückgabewert

Der Wert des unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthaltenen Zeigers.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_sub_explicit` Funktion `read-modify-write` führt einen Vorgang aus, um *den Wert* in *Atom*atomar vom `Order`gespeicherten Wert zu subtrahieren, innerhalb der [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen, die von angegeben werden.

Wenn der atomare `atomic_address`Typ ist , *hat Wert* den Typ, `ptrdiff_t` und der Vorgang behandelt den gespeicherten Zeiger als . `char *`

Dieser Vorgang wird auch bei Integraltypen überladen:

```cpp
integral atomic_fetch_sub_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_sub_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_xor"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor

Führt ein bitweises `exclusive or` auf einem Wert und einem vorhandenen in einem `atomic`-Objekt gespeicherten Wert aus.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_xor` Funktion `read-modify-write` führt einen Vorgang aus, um den `exclusive or` gespeicherten Wert von *Atom* durch einen `memory_order_seq_cst`bitweisen *Wert* und den aktuellen Wert, der in *Atom*gespeichert ist, mit dem [memory_order](../standard-library/atomic-enums.md#memory_order_enum)zu ersetzen.

## <a name="atomic_fetch_xor_explicit"></a><a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

Führt ein bitweises `exclusive or` auf einem Wert und einem vorhandenen in einem `atomic`-Objekt gespeicherten Wert aus.

```cpp
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die `atomic_fetch_xor_explicit` Funktion `read-modify-write` führt einen Vorgang aus, um den `exclusive or` gespeicherten Wert von *Atom* durch einen bitweisen *Wert* und den aktuellen Wert zu ersetzen, der in *Atom*gespeichert ist, innerhalb der [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen, die durch *Order*angegeben werden.

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

Legt das **bool-Flag** in einem [atomic_flag-Objekt](../standard-library/atomic-flag-structure.md) auf **false**fest, innerhalb der `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parameter

*Flag*\
Ein Zeiger auf ein `atomic_flag` -Objekt.

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

Legt das **bool-Flag** in einem [atomic_flag-Objekt](../standard-library/atomic-flag-structure.md) s-wert auf **false**fest, innerhalb der angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Flag*\
Ein Zeiger auf ein `atomic_flag` -Objekt.

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

Legt das **bool-Flag** in einem [atomic_flag-Objekt](../standard-library/atomic-flag-structure.md) innerhalb `memory_order_seq_cst`der Einschränkungen der [memory_order](../standard-library/atomic-enums.md#memory_order_enum)auf **true**fest.

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parameter

*Flag*\
Ein Zeiger auf ein `atomic_flag` -Objekt.

### <a name="return-value"></a>Rückgabewert

Der Anfangswert von *Flag*.

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

Legt das **bool-Flag** in einem [atomic_flag-Objekt](../standard-library/atomic-flag-structure.md) innerhalb der angegebenen memory_order Einschränkungen auf **true** [fest.](../standard-library/atomic-enums.md#memory_order_enum)

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Flag*\
Ein Zeiger auf ein `atomic_flag` -Objekt.

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Anfangswert von *Flag*.

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

Legt den gespeicherten Wert in einem `atomic`-Objekt fest.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Wert*\
Ein Wert vom Typ `Ty`.

### <a name="remarks"></a>Bemerkungen

`atomic_init` ist kein atomischer Vorgang. Ist nicht threadsicher.

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a>atomic_is_lock_free

Gibt an, ob die atomischen Vorgänge auf ein `atomic`-Objekt *sperrfrei* sind.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

### <a name="return-value"></a>Rückgabewert

**true,** wenn atomare Operationen auf *Atom* sperrfrei sind; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Ein atomischer Typ ist sperrfrei, wenn für keine der atomischen Vorgänge auf diesem Typ Sperren verwendet werden. Wenn diese Funktion TRUE zurückgibt, ist der Typ sicher und kann in Signalhandlern verwendet werden.

## <a name="atomic_load"></a><a name="atomic_load"></a>atomic_load

Ruft den gespeicherten Wert in einem `atomic`-Objekt ab.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` enthalten ist.

### <a name="return-value"></a>Rückgabewert

Der abgerufene Wert, der in *Atom*gespeichert ist.

### <a name="remarks"></a>Bemerkungen

`atomic_load` verwendet implizit `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a>atomic_load_explicit

Ruft den gespeicherten Wert in einem `atomic`-Objekt in einer angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ab.

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` enthalten ist.

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Verwenden Sie nicht `memory_order_release` oder `memory_order_acq_rel`.

### <a name="return-value"></a>Rückgabewert

Der abgerufene Wert, der in *Atom*gespeichert ist.

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

Fungiert als *Umgrenzung* (das ist eine Arbeitsspeicher-Synchronisierungsprimitive, mit der die Reihenfolge zwischen Lade- bzw. Speichervorgängen erzwungen wird) zwischen anderen Umgrenzungen in einem aufrufenden Thread, die über im gleichen Thread ausgeführte Signalhandler verfügen.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Bestellung*\
Eine den Umgrenzungstyp bestimmende Speicheranordnungseinschränkung.

### <a name="remarks"></a>Bemerkungen

Das *Argument "Auftrag"* bestimmt den Zauntyp.

|||
|-|-|
|`memory_order_relaxed`|Die Umgrenzung hat keine Auswirkung.|
|`memory_order_consume`|Die Umgrenzung ist eine Abrufumgrenzung.|
|`memory_order_acquire`|Die Umgrenzung ist eine Abrufumgrenzung.|
|`memory_order_release`|Die Umgrenzung ist eine Releaseumgrenzung.|
|`memory_order_acq_rel`|Die Umgrenzung ist eine Abrufumgrenzung und eine Releaseumgrenzung.|
|`memory_order_seq_cst`|Die Umgrenzung ist eine Abrufumgrenzung und eine Releaseumgrenzung, und sie ist sequenziell konsistent.|

## <a name="atomic_store"></a><a name="atomic_store"></a>atomic_store

Speichert einen Wert atomisch in einem atomischen Objekt.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein atomisches Objekt, das einen Wert vom Typ `Ty` enthält.

*Wert*\
Ein Wert vom Typ `Ty`.

### <a name="remarks"></a>Bemerkungen

`atomic_store`speichert *Value* in dem Objekt, auf das `memory_order_seq_cst`von *Atom*verwiesen wird, innerhalb der [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkung.

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a>atomic_store_explicit

Speichert einen Wert atomisch in einem atomischen Objekt.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(
    const volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_store_explicit(
    const atomic<Ty>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Atom*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` enthalten ist.

*Wert*\
Ein Wert vom Typ `Ty`.

*Bestellung*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Verwenden Sie nicht `memory_order_consume`, `memory_order_acquire`, oder `memory_order_acq_rel`.

### <a name="remarks"></a>Bemerkungen

`atomic_store`speichert *Value* in dem Objekt, auf das `memory_order` von *Atom*verwiesen wird, innerhalb der, die durch *Order*angegeben ist.

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

Fungiert als *Umgrenzung*. Dabei handelt es sich um eine Arbeitsspeichersynchronisierungs-Primitive, mit der die Reihenfolge zwischen Lade- bzw. Speichervorgängen ohne einen zugeordneten atomischen Vorgang erzwungen wird.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Bestellung*\
Eine den Umgrenzungstyp bestimmende Speicheranordnungseinschränkung.

### <a name="remarks"></a>Bemerkungen

Das *Argument "Auftrag"* bestimmt den Zauntyp.

|||
|-|-|
|`memory_order_relaxed`|Die Umgrenzung hat keine Auswirkung.|
|`memory_order_consume`|Die Umgrenzung ist eine Abrufumgrenzung.|
|`memory_order_acquire`|Die Umgrenzung ist eine Abrufumgrenzung.|
|`memory_order_release`|Die Umgrenzung ist eine Releaseumgrenzung.|
|`memory_order_acq_rel`|Die Umgrenzung ist eine Abrufumgrenzung und eine Releaseumgrenzung.|
|`memory_order_seq_cst`|Die Umgrenzung ist eine Abrufumgrenzung und eine Releaseumgrenzung, und sie ist sequenziell konsistent.|

## <a name="kill_dependency"></a><a name="kill_dependency"></a>kill_dependency

Entfernt eine Abhängigkeit.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parameter

*Arg*\
Ein Wert vom Typ `Ty`.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist *Arg*. Die Auswertung von *Arg* ist nicht vom Funktionsaufruf abhängig. Durch Unterbrechen einer möglichen Abhängigkeitskette könnte die Funktion zulassen, dass der Compiler effizienteren Code generiert.

## <a name="see-also"></a>Siehe auch

[\<atomare>](../standard-library/atomic.md)
