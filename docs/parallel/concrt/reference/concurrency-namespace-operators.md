---
title: concurrency-Namespace-Operatoren
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: aac43a15b09bd792118fbfe7ea51493b73b8ac9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374385"
---
# <a name="concurrency-namespace-operators"></a>concurrency-Namespace-Operatoren

||||
|-|-|-|
|[Operator!=](#operator_neq)|[Operator&amp;&amp;](#operator_amp_amp)|[Operator&gt;](#operator_gt)|
|[Operator&gt;=](#operator_gt_eq)|[Operator&lt;](#operator_lt)|[Operator&lt;=](#operator_lt_eq)|
|[Betreiber== Einzelnachweise ==](#operator_eq_eq)|[operator||](#operator_lor)| |

## <a name="operator124124-operator"></a><a name="operator_lor"></a>Betreiber&#124;&#124; Operator

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

*Lhs*<br/>
Die erste Aufgabe, die mit der resultierenden Aufgabe kombiniert werden soll.

*rhs*<br/>
Die zweite Aufgabe, die mit der resultierenden Aufgabe kombiniert werden soll.

### <a name="return-value"></a>Rückgabewert

Eine Aufgabe, die erfolgreich abgeschlossen wird, wenn eine der Eingabeaufgaben erfolgreich abgeschlossen wurde. Wenn die Eingabeaufgaben vom Typ `T` sind, wird die Ausgabe dieser Funktion `task<std::vector<T>` sein. Wenn die Eingabeaufgaben vom Typ `void` sind, ist die Ausgabeaufgabe auch `task<void>`.

### <a name="remarks"></a>Bemerkungen

Wenn beide Vorgänge abgebrochen oder Ausnahmen ausgelöst werden, wird die zurückgegebene Aufgabe im stornierten Zustand abgeschlossen, und eine `get()` `wait()` der Ausnahmen, falls vorhanden, wird beim Aufruf oder bei dieser Aufgabe ausgelöst.

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>Operator&amp; &amp; Operator

Erstellt eine Aufgabe, die erfolgreich abgeschlossen wird, wenn beide als Argumente bereitgestellten Aufgaben erfolgreich abgeschlossen werden.

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

*Lhs*<br/>
Die erste Aufgabe, die mit der resultierenden Aufgabe kombiniert werden soll.

*rhs*<br/>
Die zweite Aufgabe, die mit der resultierenden Aufgabe kombiniert werden soll.

### <a name="return-value"></a>Rückgabewert

Eine Aufgabe, die erfolgreich abgeschlossen ist, wenn beide Eingabeaufgaben erfolgreich abgeschlossen wurden. Wenn die Eingabeaufgaben vom Typ `T` sind, wird die Ausgabe dieser Funktion `task<std::vector<T>>` sein. Wenn die Eingabeaufgaben vom Typ `void` sind, ist die Ausgabeaufgabe auch `task<void>`.

### <a name="remarks"></a>Bemerkungen

Wenn eine der Aufgaben abgebrochen wird oder eine Ausnahme auslöst, wird die zurückgegebene Aufgabe vorzeitig im stornierten `get()` `wait()` Zustand abgeschlossen, und die Ausnahme, falls eine aufgabe, wird ausgelöst, wenn Sie diese Aufgabe aufrufen oder für diese Aufgabe.

## <a name="operator-operator"></a><a name="operator_eq_eq"></a>Operator == Betreiber

Testet, ob das `concurrent_vector`-Objekt links vom Operator gleich dem `concurrent_vector`-Objekt rechts vom Operator ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der in den gleichzeitigen Vektoren gespeicherten Elemente.

*A1*<br/>
Der Zuweisungstyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der Zuweisungstyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der gleichzeitige Vektor auf der linken Seite des Operators dem gleichzeitigen Vektor auf der rechten Seite des Operators entspricht; andernfalls **falsch**.

### <a name="remarks"></a>Bemerkungen

Zwei gleichzeitige Vektoren sind gleich, wenn sie die gleiche Anzahl von Elementen haben und ihre jeweiligen Elemente die gleichen Werte haben. Andernfalls sind sie ungleich.

Diese Methode ist in Bezug auf andere Methoden, die entweder die `_A` gleichzeitigen Vektoren oder `_B`ändern könnten, nicht parallelitätssicher.

## <a name="operator-operator"></a><a name="operator_neq"></a>Operator!= Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator ungleich dem `concurrent_vector`-Objekt rechts vom Operator ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der in den gleichzeitigen Vektoren gespeicherten Elemente.

*A1*<br/>
Der Zuweisungstyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der Zuweisungstyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die gleichzeitigen Vektoren nicht gleich sind; **false,** wenn die gleichzeitigen Vektoren gleich sind.

### <a name="remarks"></a>Bemerkungen

Zwei gleichzeitige Vektoren sind gleich, wenn sie die gleiche Anzahl von Elementen haben und ihre jeweiligen Elemente die gleichen Werte haben. Andernfalls sind sie ungleich.

Diese Methode ist in Bezug auf andere Methoden, die entweder die `_A` gleichzeitigen Vektoren oder `_B`ändern könnten, nicht parallelitätssicher.

## <a name="operatorlt-operator"></a><a name="operator_lt"></a>Operator&lt; Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator kleiner als das `concurrent_vector`-Objekt auf der rechten Seite ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der in den gleichzeitigen Vektoren gespeicherten Elemente.

*A1*<br/>
Der Zuweisungstyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der Zuweisungstyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der gleichzeitige Vektor auf der linken Seite des Operators kleiner als der gleichzeitige Vektor auf der rechten Seite des Operators ist; andernfalls **falsch**.

### <a name="remarks"></a>Bemerkungen

Das Verhalten dieses Operators ist identisch mit `vector` dem `std` entsprechenden Operator für die Klasse im Namespace.

Diese Methode ist in Bezug auf andere Methoden, die entweder die `_A` gleichzeitigen Vektoren oder `_B`ändern könnten, nicht parallelitätssicher.

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a>Operator&lt;= Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator kleiner oder gleich dem `concurrent_vector`-Objekt auf der rechten Seite ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der in den gleichzeitigen Vektoren gespeicherten Elemente.

*A1*<br/>
Der Zuweisungstyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der Zuweisungstyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der gleichzeitige Vektor auf der linken Seite des Operators kleiner oder gleich dem gleichzeitigen Vektor auf der rechten Seite des Operators ist; andernfalls **falsch**.

### <a name="remarks"></a>Bemerkungen

Das Verhalten dieses Operators ist identisch mit `vector` dem `std` entsprechenden Operator für die Klasse im Namespace.

Diese Methode ist in Bezug auf andere Methoden, die entweder die `_A` gleichzeitigen Vektoren oder `_B`ändern könnten, nicht parallelitätssicher.

## <a name="operatorgt-operator"></a><a name="operator_gt"></a>Operator&gt; Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator größer als das `concurrent_vector`-Objekt auf der rechten Seite ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der in den gleichzeitigen Vektoren gespeicherten Elemente.

*A1*<br/>
Der Zuweisungstyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der Zuweisungstyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der gleichzeitige Vektor auf der linken Seite des Operators größer ist als der gleichzeitige Vektor auf der rechten Seite des Operators; andernfalls **falsch**.

### <a name="remarks"></a>Bemerkungen

Das Verhalten dieses Operators ist identisch mit `vector` dem `std` entsprechenden Operator für die Klasse im Namespace.

Diese Methode ist in Bezug auf andere Methoden, die entweder die `_A` gleichzeitigen Vektoren oder `_B`ändern könnten, nicht parallelitätssicher.

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a>Operator&gt;= Operator

Testet, ob das `concurrent_vector`-Objekt links vom Operator größer oder gleich dem `concurrent_vector`-Objekt auf der rechten Seite ist.

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der in den gleichzeitigen Vektoren gespeicherten Elemente.

*A1*<br/>
Der Zuweisungstyp des ersten `concurrent_vector` Objekts.

*A2*<br/>
Der Zuweisungstyp des zweiten `concurrent_vector` Objekts.

*_A*<br/>
Ein Objekt des Typs `concurrent_vector`.

*_B*<br/>
Ein Objekt des Typs `concurrent_vector`.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der gleichzeitige Vektor auf der linken Seite des Operators größer oder gleich dem gleichzeitigen Vektor auf der rechten Seite des Operators ist; andernfalls **falsch**.

### <a name="remarks"></a>Bemerkungen

Das Verhalten dieses Operators ist identisch mit `vector` dem `std` entsprechenden Operator für die Klasse im Namespace.

Diese Methode ist in Bezug auf andere Methoden, die entweder die `_A` gleichzeitigen Vektoren oder `_B`ändern könnten, nicht parallelitätssicher.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
