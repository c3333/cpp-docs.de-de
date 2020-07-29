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
ms.openlocfilehash: 15a2d86fcaf83c470f52c879ab6fe7525f80aec8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203948"
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

*DAT*\
Ein Zeiger auf ein *atomisches* Objekt, das einen Wert vom Typ speichert `Ty` .

*Exp*\
Ein Zeiger auf einen Wert des Typs `Ty`.

*Wert*\
Ein Wert vom Typ `Ty`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Werte gleich sind, andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode wird ein atomischer Vergleichs- und Austauschvorgang ausgeführt, indem implizite `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)-Argumente verwendet werden. Weitere Informationen finden Sie unter [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

Führt einen *atomischen Vergleichs-und Austausch* Vorgang aus.

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Exp*\
Ein Zeiger auf einen Wert des Typs `Ty`.

*Wert*\
Ein Wert vom Typ `Ty`.

*Order1*\
Erstes [memory_order](../standard-library/atomic-enums.md#memory_order_enum)-Argument.

*Order2*\
Zweites `memory_order`-Argument. Der Wert von *Order2* kann nicht `memory_order_release` oder sein `memory_order_acq_rel` , er kann nicht stärker als der Wert von *order1*sein.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Werte gleich sind, andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Ein *atomarischer Vergleichs-und Austausch Vorgang* vergleicht den Wert, der in dem Objekt gespeichert wird, auf das von *Atom* mit dem Wert gezeigt wird, auf den von *Exp*verwiesen wird. Wenn die Werte gleich sind, wird der Wert, der in dem Objekt gespeichert wird, auf das von *Atom* verwiesen wird *, durch einen* `read-modify-write` -Vorgang und durch Anwenden der durch *order1*angegebenen Einschränkungen für die Speicher Reihenfolge ersetzt. Wenn die Werte nicht gleich sind, ersetzt der Vorgang den Wert, auf den durch *Exp* verwiesen wird, mit dem Wert, der in dem Objekt gespeichert ist, auf das von *Atom* verwiesen wird, und wendet die von *Order2*angegebenen Einschränkungen für die Speicher Reihenfolge an.

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Exp*\
Ein Zeiger auf einen Wert des Typs `Ty`.

*Wert*\
Ein Wert vom Typ `Ty`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Werte gleich sind, andernfalls **`false`** .

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Exp*\
Ein Zeiger auf einen Wert des Typs `Ty`.

*Wert*\
Ein Wert vom Typ `Ty`.

*Order1*\
Erstes [memory_order](../standard-library/atomic-enums.md#memory_order_enum)-Argument.

*Order2*\
Zweites `memory_order`-Argument. Der Wert von *Order2* kann weder `memory_order_release` oder sein `memory_order_acq_rel` , noch kann er stärker als der Wert von *order1*sein.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Werte gleich sind, andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Sowohl die starke als auch die schwache Leistung eines *atomaren Vergleichs-und Exchange-Vorgangs* garantieren, dass der neue Wert nicht gespeichert wird, wenn die erwarteten und aktuellen Werte nicht gleich sind. Die starke Konfiguration gewährleistet, dass der neue Wert gespeichert wird, wenn die erwarteten und aktuellen Werte gleich sind. Die schwache Geschmacksrichtung kann manchmal **`false`** den neuen Wert zurückgeben und nicht speichern, auch wenn die aktuellen und erwarteten Werte gleich sind. Anders ausgedrückt, gibt die Funktion zurück **`false`** , aber eine spätere Untersuchung des erwarteten Werts zeigt möglicherweise, dass Sie sich nicht geändert hat, und sollte daher als gleich verglichen werden.

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

Verwendet den *Wert* , um den gespeicherten Wert von *Atom*zu ersetzen.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parameter

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Wert*\
Ein Wert vom Typ `Ty`.

### <a name="return-value"></a>Rückgabewert

Der gespeicherte Wert von *Atom* vor dem Austausch.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_exchange` Funktion führt einen- `read-modify-write` Vorgang aus, um den in *Atom* gespeicherten Wert *Value*mit dem- `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)auszutauschen.

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

Ersetzt den gespeicherten Wert von *Atom* durch *value*.

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` gespeichert wird.

*Wert*\
Ein Wert vom Typ `Ty`.

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der gespeicherte Wert von *Atom* vor dem Austausch.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_exchange_explicit` Funktion führt einen- `read-modify-write` Vorgang aus, um den Wert, der in *Atom* gespeichert ist, mit einem *Wert*innerhalb der durch die *Reihenfolge*angegebenen Speicher Einschränkungen auszutauschen.

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

Fügt einem vorhandenen Wert einen in einem `atomic`-Objekt gespeicherten Wert hinzu.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parameter

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Zeiger auf den Typ `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `ptrdiff_t`.

### <a name="return-value"></a>Rückgabewert

Der Wert des unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthaltenen Zeigers.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_add` Funktion führt einen- `read-modify-write` Vorgang aus, um dem gespeicherten Wert in *Atom*mithilfe der memory_order-Einschränkung atomisch *Werte* hinzuzufügen `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

Wenn der atomische Typ ist `atomic_address` , hat *value* den Typ, `ptrdiff_t` und der Vorgang behandelt den gespeicherten Zeiger als `char *` .

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Zeiger auf den Typ `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `ptrdiff_t`.

### <a name="return-value"></a>Rückgabewert

Der Wert des unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthaltenen Zeigers.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_add_explicit` Funktion führt einen- `read-modify-write` Vorgang aus, um dem gespeicherten Wert in *Atom*atomisch *Werte* hinzuzufügen, und zwar innerhalb der von angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen `Order` .

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_and` Funktion führt einen `read-modify-write` -Vorgang aus, um den gespeicherten Wert von *Atom* durch einen bitweisen `and` *Wert* und den aktuellen Wert, der in *Atom*gespeichert wird, mithilfe der- `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkung zu ersetzen.

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_and_explicit` Funktion führt `read-modify-write` einen-Vorgang aus, um den gespeicherten Wert von *Atom* durch einen bitweisen `and` *Wert* und den aktuellen Wert, der in *Atom*gespeichert ist, innerhalb der durch die *Reihenfolge*angegebenen Speicher Einschränkungen zu ersetzen.

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

Führt ein bitweises `or` auf einem Wert und einem vorhandenen in einem `atomic`-Objekt gespeicherten Wert aus.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parameter

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_or` Funktion führt einen `read-modify-write` -Vorgang aus, um den gespeicherten Wert von *Atom* durch einen bitweisen `or` *Wert* und den aktuellen Wert, der in *Atom*gespeichert wird, mithilfe des- `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)zu ersetzen.

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_or_explicit` Funktion führt einen `read-modify-write` -Vorgang aus, um den gespeicherten Wert von *Atom* durch einen bitweisen `or` *Wert* und den aktuellen Wert, der in *Atom*gespeichert ist, innerhalb der von *Order*angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen zu ersetzen.

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Zeiger auf den Typ `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `ptrdiff_t`.

### <a name="return-value"></a>Rückgabewert

Der Wert des unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthaltenen Zeigers.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_sub` Funktion führt einen- `read-modify-write` Vorgang aus, um den *Wert* mithilfe der-memory_order Einschränkung atomisch aus dem gespeicherten Wert in *Atom*zu subtrahieren `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

Wenn der atomische Typ ist `atomic_address` , hat *value* den Typ, `ptrdiff_t` und der Vorgang behandelt den gespeicherten Zeiger als `char *` .

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Zeiger auf den Typ `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `ptrdiff_t`.

### <a name="return-value"></a>Rückgabewert

Der Wert des unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthaltenen Zeigers.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_sub_explicit` Funktion führt einen- `read-modify-write` Vorgang aus, um den *Wert* aus dem gespeicherten Wert in *Atom*in den von angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen atomisch zu subtrahieren `Order` .

Wenn der atomische Typ ist `atomic_address` , hat *value* den Typ, `ptrdiff_t` und der Vorgang behandelt den gespeicherten Zeiger als `char *` .

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_xor` Funktion führt einen `read-modify-write` -Vorgang aus, um den gespeicherten Wert von *Atom* durch einen bitweisen `exclusive or` *Wert* und den aktuellen Wert, der in *Atom*gespeichert wird, mithilfe des- `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)zu ersetzen.

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

*Wert*\
Ein Wert vom Typ `T`.

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Wert, der unmittelbar vor dem Ausführen des Vorgangs im atomischen Objekt enthalten war.

### <a name="remarks"></a>Bemerkungen

Die- `atomic_fetch_xor_explicit` Funktion führt einen `read-modify-write` -Vorgang aus, um den gespeicherten Wert von *Atom* durch einen bitweisen `exclusive or` *Wert* und den aktuellen Wert, der in *Atom*gespeichert ist, innerhalb der durch die *Reihenfolge*angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen zu ersetzen.

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

Legt das- **`bool`** Flag in einem [atomic_flag](../standard-library/atomic-flag-structure.md) -Objekt **`false`** innerhalb der `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)auf fest.

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parameter

*Ssen*\
Ein Zeiger auf ein `atomic_flag` -Objekt.

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

Legt das- **`bool`** Flag in einem [atomic_flag](../standard-library/atomic-flag-structure.md) -Objekt **`false`** innerhalb der angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen auf fest.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Ssen*\
Ein Zeiger auf ein `atomic_flag` -Objekt.

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

Legt das- **`bool`** Flag in einem [atomic_flag](../standard-library/atomic-flag-structure.md) -Objekt **`true`** innerhalb der Einschränkungen des `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)auf fest.

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parameter

*Ssen*\
Ein Zeiger auf ein `atomic_flag` -Objekt.

### <a name="return-value"></a>Rückgabewert

Der Anfangswert des *Flags*.

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

Legt das- **`bool`** Flag in einem [atomic_flag](../standard-library/atomic-flag-structure.md) -Objekt **`true`** innerhalb der angegebenen [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkungen auf fest.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Ssen*\
Ein Zeiger auf ein `atomic_flag` -Objekt.

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Rückgabewert

Der Anfangswert des *Flags*.

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

Legt den gespeicherten Wert in einem `atomic`-Objekt fest.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parameter

*DAT*\
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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `T` gespeichert wird.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn atomarische Operationen für *Atom* sperrfrei sind. andernfalls **`false`** .

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` enthalten ist.

### <a name="return-value"></a>Rückgabewert

Der abgerufene Wert, der in *Atom*gespeichert wird.

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` enthalten ist.

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Verwenden Sie nicht `memory_order_release` oder `memory_order_acq_rel`.

### <a name="return-value"></a>Rückgabewert

Der abgerufene Wert, der in *Atom*gespeichert wird.

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

Fungiert als *Umgrenzung* (das ist eine Arbeitsspeicher-Synchronisierungsprimitive, mit der die Reihenfolge zwischen Lade- bzw. Speichervorgängen erzwungen wird) zwischen anderen Umgrenzungen in einem aufrufenden Thread, die über im gleichen Thread ausgeführte Signalhandler verfügen.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Reihenfolge*\
Eine den Umgrenzungstyp bestimmende Speicheranordnungseinschränkung.

### <a name="remarks"></a>Bemerkungen

Das *Order* -Argument bestimmt den umgrenzungstyp.

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

*DAT*\
Ein Zeiger auf ein atomisches Objekt, das einen Wert vom Typ `Ty` enthält.

*Wert*\
Ein Wert vom Typ `Ty`.

### <a name="remarks"></a>Bemerkungen

`atomic_store`speichert den *Wert* in dem Objekt, auf das von *Atom*in der `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) Einschränkung verwiesen wird.

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

*DAT*\
Ein Zeiger auf ein `atomic`-Objekt, in dem ein Wert des Typs `Ty` enthalten ist.

*Wert*\
Ein Wert vom Typ `Ty`.

*Reihenfolge*\
Ein [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Verwenden Sie nicht `memory_order_consume`, `memory_order_acquire`, oder `memory_order_acq_rel`.

### <a name="remarks"></a>Bemerkungen

`atomic_store`speichert den *Wert* in dem Objekt, auf das von *Atom*verwiesen wird, in der, die in der `memory_order` *Reihenfolge*angegeben ist.

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

Fungiert als *Umgrenzung*. Dabei handelt es sich um eine Arbeitsspeichersynchronisierungs-Primitive, mit der die Reihenfolge zwischen Lade- bzw. Speichervorgängen ohne einen zugeordneten atomischen Vorgang erzwungen wird.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parameter

*Reihenfolge*\
Eine den Umgrenzungstyp bestimmende Speicheranordnungseinschränkung.

### <a name="remarks"></a>Bemerkungen

Das *Order* -Argument bestimmt den umgrenzungstyp.

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

*Gebeut*\
Ein Wert vom Typ `Ty`.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist *arg*. Die Auswertung von *arg* enthält keine Abhängigkeit vom Funktions Aufruf. Durch Unterbrechen einer möglichen Abhängigkeitskette könnte die Funktion zulassen, dass der Compiler effizienteren Code generiert.

## <a name="see-also"></a>Weitere Informationen

[\<atomic>](../standard-library/atomic.md)
