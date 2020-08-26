---
title: Concurrency-Namespace-Funktionen (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::all_memory_fence
- amp/Concurrency::atomic_compare_exchange
- amp/Concurrency::atomic_fetch_dec
- amp/Concurrency::atomic_fetch_max
- amp/Concurrency::atomic_fetch_min
- amp/Concurrency::copy
- amp/Concurrency::direct3d_abort
- amp/Concurrency::direct3d_printf
- amp/Concurrency::global_memory_fence
- amp/Concurrency::tile_static_memory_fence
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
ms.openlocfilehash: b03a6189d2205dff62d94f07bc597ca2e1013a28
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840205"
---
# <a name="concurrency-namespace-functions-amp"></a>Concurrency-Namespace-Funktionen (AMP)

:::row:::
   :::column span="":::
      [`all_memory_fence`](#all_memory_fence)\
      [`amp_uninitialize`](#amp_uninitialize)\
      [`atomic_compare_exchange`](#atomic_compare_exchange)\
      [`atomic_exchange`](#atomic_exchange)\
      [`atomic_fetch_add`](#atomic_fetch_add)\
      [`atomic_fetch_and`](#atomic_fetch_and)
   :::column-end:::
   :::column span="":::
      [`atomic_fetch_dec`](#atomic_fetch_dec)\
      [`atomic_fetch_inc`](#atomic_fetch_inc)\
      [`atomic_fetch_max`](#atomic_fetch_max)\
      [`atomic_fetch_min`](#atomic_fetch_min)\
      [`atomic_fetch_or`](#atomic_fetch_or)
   :::column-end:::
   :::column span="":::
      [`atomic_fetch_sub`](#atomic_fetch_sub)\
      [`atomic_fetch_xor`](#atomic_fetch_xor)\
      [`copy`](#copy)\
      [`copy_async`](#copy_async)\
      [`direct3d_abort`](#direct3d_abort)
   :::column-end:::
   :::column span="":::
      [`direct3d_errorf`](#direct3d_errorf)\
      [`direct3d_printf`](#direct3d_printf)\
      [`global_memory_fence`](#global_memory_fence)\
      [`parallel_for_each`](#parallel_for_each)\
      [`tile_static_memory_fence`](#tile_static_memory_fence)
   :::column-end:::
:::row-end:::

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a> all_memory_fence

Blockiert die Ausführung aller Threads in einer Kachel, bis alle Speicherzugriffe abgeschlossen sind. Dadurch wird sichergestellt, dass alle Speicherzugriffe für andere Threads in der Threadkachel sichtbar sind und in der Programmreihenfolge ausgeführt werden.

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Barrier*<br/>
Ein `tile_barrier`-Objekt.

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a> amp_uninitialize

Hebt die Initialisierung der C++ AMP-Laufzeit auf. Es ist zulässig, diese Funktion während der Lebensdauer einer Anwendung mehrmals aufzurufen. Wenn Sie eine C++ amp-API aufrufen, nachdem diese Funktion aufgerufen wurde, wird die C++ amp-Laufzeit erneut initialisiert. Beachten Sie, dass C++ AMP-Objekte nicht für Aufrufe dieser Funktion verwendet werden dürfen, da dies zu nicht definiertem Verhalten führen kann. Außerdem ist das gleichzeitige Aufrufen dieser Funktion und beliebiger anderer AMP-APIs unzulässig und kann zu nicht definiertem Verhalten führen.

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a> atomic_compare_exchange

Vergleicht atomisch den Wert, der an einer Speicheradresse gespeichert wird, die im ersten Argument für Gleichheit mit dem Wert des zweiten angegebenen Arguments festgelegt ist. Wenn die Werte identisch sind, wird der Wert an der Speicheradresse in den Wert des dritten angegebenen Arguments geändert.

```cpp
inline bool atomic_compare_exchange(
    _Inout_ int* _Dest,
    _Inout_ int* _Expected_value,
    int value
    ) restrict(amp)

inline bool atomic_compare_exchange(
    _Inout_ unsigned int* _Dest,
    _Inout_ unsigned int* _Expected_value,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Der Speicherort, aus dem einer der zu vergleichenden Werte gelesen wird und an dem der neue Wert ggf. abgelegt werden soll.

*_Expected_value*<br/>
Der Speicherort, aus dem der zweite zu vergleichende Wert gelesen wird.

*value*<br/>
Der Wert, der an dem von `_Dest` angegebenen Speicherort abgelegt werden soll, wenn `_Dest` gleich `_Expected_value` ist.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn der Vorgang erfolgreich ist. andernfalls **`false`** .

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a> atomic_exchange-Funktion (C++ amp)

Legt den Wert des Zielspeicher Orts als atomarischen Vorgang fest.

```cpp
inline int atomic_exchange(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_exchange(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)

inline float atomic_exchange(
    _Inout_ float* _Dest,
    float value
    ) restrict(amp)
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Zeiger auf den Ziel Speicherort.

*value*<br/>
Der neue Wert.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert des Zielspeicher Orts.

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a> atomic_fetch_add-Funktion (C++ amp)

Fügen Sie dem Wert eines Speicher Orts atomarisch einen Wert hinzu.

```cpp
inline int atomic_fetch_add(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_add(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Zeiger auf den Speicherort des Speichers.

*value*<br/>
Der hinzuzufügende Wert.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert des Speicher Orts.

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a> atomic_fetch_and-Funktion (C++ amp)

Führt eine bitweise AND-Operation eines-Werts und des-Werts einer Speicheradresse atomarisch aus.

```cpp
inline int atomic_fetch_and(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_and(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Zeiger auf den Speicherort des Speichers.

*value*<br/>
Der Wert, der in der bitweisen and-Berechnung verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert des Speicher Orts.

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a> atomic_fetch_dec

Dekrementiert den Wert atomisch, der an der angegebenen Speicheradresse gespeichert ist.

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Die Adresse im Speicher des zu dekrementierenden Werts.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert, der an der Speicheradresse abgelegt ist.

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a> atomic_fetch_inc

Inkrementiert den Wert atomisch, der an der angegebenen Speicheradresse gespeichert ist.

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Die Adresse im Speicher des zu inkrementierenden Werts.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert, der an der Speicheradresse abgelegt ist.

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a> atomic_fetch_max

Berechnet atomisch den Maximalwert aus dem Wert, der an der im ersten Argument angegebenen Speicheradresse abgelegt wurde, und dem im zweiten Argument angegebenen Wert und speichert ihn an derselben Speicheradresse.

```cpp
inline int atomic_fetch_max(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_max(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Der Speicherort, aus dem einer der zu vergleichenden Werte gelesen wird und an dem das Maximum der beiden Werte gespeichert werden soll.

*value*<br/>
Der Wert, der mit dem Wert an der angegebenen Position verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert wird an der angegebenen Position gespeichert.

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a> atomic_fetch_min

Berechnet atomisch den Minimalwert aus dem Wert, der an der im ersten Argument angegebenen Speicheradresse abgelegt wurde, und dem im zweiten Argument angegebenen Wert und speichert ihn an derselben Speicheradresse.

```cpp
inline int atomic_fetch_min(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_min(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Der Speicherort, aus dem einer der zu vergleichenden Werte gelesen wird und an dem das Minimum der beiden Werte gespeichert werden soll.

*value*<br/>
Der Wert, der mit dem Wert an der angegebenen Position verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert wird an der angegebenen Position gespeichert.

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a> atomic_fetch_or-Funktion (C++ amp)

Führt atomisch eine bitweise OR-Operation mit einem Wert und dem Wert einer Speicheradresse aus.

```cpp
inline int atomic_fetch_or(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_or(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Zeiger auf den Speicherort des Speichers.

*value*<br/>
Der Wert, der in der bitweisen OR-Berechnung verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert des Speicher Orts.

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a> atomic_fetch_sub-Funktion (C++ amp)

Subtrahiert einen Wert atomisch von einem Speicher Speicherort.

```cpp
inline int atomic_fetch_sub(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_sub(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Zeiger auf den Ziel Speicherort.

*value*<br/>
Der Wert, der subtrahiert werden soll.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert des Speicher Orts.

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a> atomic_fetch_xor-Funktion (C++ amp)

Führt eine bitweise XOR-Operation eines-Werts und eines-Speicherort atomarisch aus.

```cpp
inline int atomic_fetch_xor(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_xor(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Zeiger auf den Speicherort des Speichers.

*value*<br/>
Der Wert, der in der XOR-Berechnung verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Der ursprüngliche Wert des Speicher Orts.

## <a name="copy"></a><a name="copy"></a> skopie

Kopiert ein C++ AMP-Objekt. Alle Anforderungen der synchronen Datenübertragung werden erfüllt. Sie können keine Daten kopieren, wenn Code auf einem Beschleuniger ausgeführt wird. Das allgemeine Format dieser Funktion ist `copy(src, dest)`.

```cpp
template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
   OutputIterator _DestIter);

template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    OutputIterator _DestIter);
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Das Objekt, in das kopiert wird.

*_DestIter*<br/>
Ein Ausgabeiterator zur Anfangsposition am Ziel.

*InputIterator*<br/>
Der Typ des Eingabeiterators.

*OutputIterator*<br/>
Der Typ des Ausgabeiterators.

*_Rank*<br/>
Der Rang des Objekts, aus dem bzw. in das kopiert werden soll.

*_Src*<br/>
Das zu kopierende Objekt.

*_SrcFirst*<br/>
Ein Anfangsiterator in den Quellcontainer.

*_SrcLast*<br/>
Ein Endeiterator in den Quellcontainer.

*value_type*<br/>
Der Datentyp der Elemente, die kopiert werden.

## <a name="copy_async"></a><a name="copy_async"></a> copy_async

Kopiert ein C++ amp Objekt und gibt ein [completion_future](completion-future-class.md) Objekt zurück, auf das gewartet werden kann. Sie können keine Daten kopieren, wenn Code auf einem Beschleuniger ausgeführt wird.  Das allgemeine Format dieser Funktion ist `copy(src, dest)`.

```cpp
template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src, OutputIterator _DestIter);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src, OutputIterator _DestIter);
```

### <a name="parameters"></a>Parameter

*_Dest*<br/>
Das Objekt, in das kopiert wird.

*_DestIter*<br/>
Ein Ausgabeiterator zur Anfangsposition am Ziel.

*InputIterator*<br/>
Der Typ des Eingabeiterators.

*OutputIterator*<br/>
Der Typ des Ausgabeiterators.

*_Rank*<br/>
Der Rang des Objekts, aus dem bzw. in das kopiert werden soll.

*_Src*<br/>
Das zu kopierende Objekt.

*_SrcFirst*<br/>
Ein Anfangsiterator in den Quellcontainer.

*_SrcLast*<br/>
Ein Endeiterator in den Quellcontainer.

*value_type*<br/>
Der Datentyp der Elemente, die kopiert werden.

### <a name="return-value"></a>Rückgabewert

Ein `future<void>`-Objekt, auf das gewartet werden kann.

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a> direct3d_abort

Bricht die Ausführung einer Funktion mit der Einschränkungsklausel `restrict(amp)` ab. Wenn die AMP-Laufzeit den Aufruf erkennt, löst sie eine [runtime_exception](runtime-exception-class.md) -Ausnahme mit der Fehlermeldung „Referenzrasterprogramm: Anweisung zum Abbrechen von Shader ermittelt“ aus.

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a> direct3d_errorf

Gibt eine formatierte Zeichenfolge im Visual Studio-Ausgabefenster aus. Sie wird von einer Funktion mit der Einschränkungsklausel `restrict(amp)` aufgerufen. Wenn die amp-Laufzeit den-Befehl erkennt, löst Sie eine [runtime_exception](runtime-exception-class.md) -Ausnahme mit derselben Formatierungs Zeichenfolge aus.

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a> direct3d_printf

Gibt eine formatierte Zeichenfolge im Visual Studio-Ausgabefenster aus. Sie wird von einer Funktion mit der Einschränkungsklausel `restrict(amp)` aufgerufen.

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a> global_memory_fence

Blockiert die Ausführung aller Threads in einer Kachel, bis alle globalen Speicherzugriffe abgeschlossen sind. Dadurch wird sichergestellt, dass globale Speicherzugriffe für andere Threads in der Threadkachel sichtbar sind und in der Programmreihenfolge ausgeführt werden.

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Barrier*<br/>
Ein tile_barrier-Objekt

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a> Parallel_for_each-Funktion (C++ amp)

Führt eine Funktion übergreifend über die "compute"-Domäne aus. Weitere Informationen finden Sie unter [C++ amp Übersicht](../../../parallel/amp/cpp-amp-overview.md).

```cpp
template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
   const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);
```

### <a name="parameters"></a>Parameter

*_Accl_view*<br/>
Das `accelerator_view`-Objekt, auf dem die parallele Berechnung ausgeführt werden soll.

*_Compute_domain*<br/>
Ein `extent`-Objekt, das die Daten für die Berechnung enthält.

*_Dim0*<br/>
Die Dimension des `tiled_extent`-Objekts.

*_Dim1*<br/>
Die Dimension des `tiled_extent`-Objekts.

*_Dim2*<br/>
Die Dimension des `tiled_extent`-Objekts.

*_Kernel*<br/>
Ein Lambda-oder Funktions Objekt, das ein Argument vom Typ "Index \<_Rank> " annimmt und die parallele Berechnung ausführt.

*_Kernel_type*<br/>
Ein Lambda- oder Funktionselement.

*_Rank*<br/>
Der Rang des Wertebereichs.

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a> tile_static_memory_fence

Blockiert die Ausführung aller Threads in einer Kachel, bis alle ausstehenden `tile_static`-Speicherzugriffe abgeschlossen sind. Dadurch wird sichergestellt, dass `tile_static`-Speicherzugriffe für andere Threads in der Threadkachel sichtbar sind und in der Programmreihenfolge ausgeführt werden.

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Barrier*<br/>
Ein tile_barrier-Objekt.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace (C++ amp)](concurrency-namespace-cpp-amp.md)
