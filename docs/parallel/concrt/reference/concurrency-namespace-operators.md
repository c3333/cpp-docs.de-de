---
title: concurrency-Namespace-Operatoren
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 676e1936af317a6ab19959f8fd09b1de06dfaf69
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427374"
---
# <a name="concurrency-namespace-operators"></a>concurrency-Namespace-Operatoren

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[operator||](#operator_lor)| |

## <a name="operator_lor"></a>Operator&#124; &#124; Operator

Erstellt eine Aufgabe, die erfolgreich abgeschlossen wird, wenn eine der als Argumente angegeben Aufgaben erfolgreich abgeschlossen wird.

```cpp
template<typename ReturnType>
task<ReturnType> operator||(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void> operator||(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>Parameter

*ReturnType*<br/>
Der Typ der zurückgegebenen Aufgabe.

*LHS*<br/>
Die erste Aufgabe, die mit der resultierenden Aufgabe kombiniert werden soll.

*rhs*<br/>
Die zweite Aufgabe, die mit der resultierenden Aufgabe kombiniert werden soll.

### <a name="return-value"></a>Rückgabewert

Eine Aufgabe, die erfolgreich abgeschlossen wird, wenn eine der Eingabe Aufgaben erfolgreich abgeschlossen wurde. Wenn die Eingabeaufgaben vom Typ `T` sind, wird die Ausgabe dieser Funktion `task<std::vector<T>` sein. Wenn die Eingabeaufgaben vom Typ `void` sind, ist die Ausgabeaufgabe auch `task<void>`.

### <a name="remarks"></a>Hinweise

Wenn beide Tasks abgebrochen oder Ausnahmen ausgelöst werden, wird die zurückgegebene Aufgabe im Zustand "abgebrochen" vervollständigt, und eine der Ausnahmen, falls vorhanden, wird ausgelöst, wenn Sie `get()` oder `wait()` für diese Aufgabe ausführen.

## <a name="operator_amp_amp"></a>Operator&amp;&amp;-Operator

Erstellt eine Aufgabe, die erfolgreich abgeschlossen wird, wenn beide Aufgaben, die als Argumente bereitgestellt werden, erfolgreich abgeschlossen werden.

```cpp
template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void>  operator&&(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>Parameter

*ReturnType*<br/>
Der Typ der zurückgegebenen Aufgabe.

*LHS*<br/>
Die erste Aufgabe, die mit der resultierenden Aufgabe kombiniert werden soll.

*rhs*<br/>
Die zweite Aufgabe, die mit der resultierenden Aufgabe kombiniert werden soll.

### <a name="return-value"></a>Rückgabewert

Eine Aufgabe, die erfolgreich abgeschlossen ist, wenn beide Eingabeaufgaben erfolgreich abgeschlossen wurden. Wenn die Eingabeaufgaben vom Typ `T` sind, wird die Ausgabe dieser Funktion `task<std::vector<T>>` sein. Wenn die Eingabeaufgaben vom Typ `void` sind, ist die Ausgabeaufgabe auch `task<void>`.

### <a name="remarks"></a>Hinweise

Wenn eine der Aufgaben abgebrochen wird oder eine Ausnahme auslöst, wird die zurückgegebene Aufgabe früh im abgebrochenen Zustand ausgeführt, und die Ausnahme wird ausgelöst, wenn Sie `get()` oder `wait()` für diese Aufgabe aufruft.

## <a name="operator_eq_eq"></a>Operator = =-Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator gleich dem `concurrent_vector`-Objekt rechts vom Operator ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Elemente, die in den gleichzeitigen Vektoren gespeichert werden.

*A1*<br/>
Der zuordnertyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der zuordnertyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn der gleichzeitige Vektor Links vom Operator gleich dem gleichzeitigen Vektor auf der rechten Seite des Operators ist. andernfalls **false**.

### <a name="remarks"></a>Hinweise

Zwei gleichzeitige Vektoren sind gleich, wenn Sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

Diese Methode ist in Bezug auf andere Methoden, die einen der gleichzeitigen Vektoren `_A` oder `_B`ändern können, nicht Parallelitäts sicher.

## <a name="operator_neq"></a>Operator! =-Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator ungleich dem `concurrent_vector`-Objekt rechts vom Operator ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Elemente, die in den gleichzeitigen Vektoren gespeichert werden.

*A1*<br/>
Der zuordnertyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der zuordnertyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die gleichzeitigen Vektoren nicht gleich sind. **false** , wenn die gleichzeitigen Vektoren gleich sind.

### <a name="remarks"></a>Hinweise

Zwei gleichzeitige Vektoren sind gleich, wenn Sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

Diese Methode ist in Bezug auf andere Methoden, die einen der gleichzeitigen Vektoren `_A` oder `_B`ändern können, nicht Parallelitäts sicher.

## <a name="operator_lt"></a>Operator&lt;-Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator kleiner als das `concurrent_vector`-Objekt auf der rechten Seite ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Elemente, die in den gleichzeitigen Vektoren gespeichert werden.

*A1*<br/>
Der zuordnertyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der zuordnertyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn der gleichzeitige Vektor Links vom Operator kleiner als der gleichzeitige Vektor auf der rechten Seite des Operators ist. andernfalls **false**.

### <a name="remarks"></a>Hinweise

Das Verhalten dieses Operators ist mit dem äquivalenten Operator für die `vector`-Klasse im `std`-Namespace identisch.

Diese Methode ist in Bezug auf andere Methoden, die einen der gleichzeitigen Vektoren `_A` oder `_B`ändern können, nicht Parallelitäts sicher.

## <a name="operator_lt_eq"></a>Operator&lt;=-Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator kleiner oder gleich dem `concurrent_vector`-Objekt auf der rechten Seite ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Elemente, die in den gleichzeitigen Vektoren gespeichert werden.

*A1*<br/>
Der zuordnertyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der zuordnertyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn der gleichzeitige Vektor Links vom Operator kleiner als oder gleich dem gleichzeitigen Vektor auf der rechten Seite des Operators ist. andernfalls **false**.

### <a name="remarks"></a>Hinweise

Das Verhalten dieses Operators ist mit dem äquivalenten Operator für die `vector`-Klasse im `std`-Namespace identisch.

Diese Methode ist in Bezug auf andere Methoden, die einen der gleichzeitigen Vektoren `_A` oder `_B`ändern können, nicht Parallelitäts sicher.

## <a name="operator_gt"></a>Operator&gt;-Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator größer als das `concurrent_vector`-Objekt auf der rechten Seite ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Elemente, die in den gleichzeitigen Vektoren gespeichert werden.

*A1*<br/>
Der zuordnertyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der zuordnertyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn der gleichzeitige Vektor Links vom Operator größer als der gleichzeitige Vektor auf der rechten Seite des Operators ist. andernfalls **false**.

### <a name="remarks"></a>Hinweise

Das Verhalten dieses Operators ist mit dem äquivalenten Operator für die `vector`-Klasse im `std`-Namespace identisch.

Diese Methode ist in Bezug auf andere Methoden, die einen der gleichzeitigen Vektoren `_A` oder `_B`ändern können, nicht Parallelitäts sicher.

## <a name="operator_gt_eq"></a>Operator&gt;=-Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator größer oder gleich dem `concurrent_vector`-Objekt auf der rechten Seite ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Elemente, die in den gleichzeitigen Vektoren gespeichert werden.

*A1*<br/>
Der zuordnertyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der zuordnertyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn der gleichzeitige Vektor Links vom Operator größer als oder gleich dem gleichzeitigen Vektor auf der rechten Seite des Operators ist. andernfalls **false**.

### <a name="remarks"></a>Hinweise

Das Verhalten dieses Operators ist mit dem äquivalenten Operator für die `vector`-Klasse im `std`-Namespace identisch.

Diese Methode ist in Bezug auf andere Methoden, die einen der gleichzeitigen Vektoren `_A` oder `_B`ändern können, nicht Parallelitäts sicher.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
