---
title: '&lt;chrono&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 398e2429c38cffb454c7b510aa5ab44fbe4cfef6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427206"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt;-Operatoren

## <a name="operator-"></a>KOM

Operator für die Subtraktion oder Negation von [duration](../standard-library/duration-class.md)- und [time_point](../standard-library/time-point-class.md)-Objekten.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator-(
       const duration<Rep1, Period1>& Left,
       cconst duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type
   operator-(
       const time_point<Clock, Duration1>& Time,
       const duration<Rep2, Period2>& Dur);

template <class Clock, class Duration1, class Duration2>
constexpr typename common_type<Duration1, Duration2>::type
   operator-(
       const time_point<Clock, Duration1>& Left,
       const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `duration` oder `time_point`-Objekt.

*Rechte*\
Das rechte `duration` oder `time_point`-Objekt.

*Zeit*\
Ein `time_point`-Objekt.

*Dur* -\
Ein `duration`-Objekt.

### <a name="return-value"></a>Rückgabewert

Von der ersten Funktion wird ein `duration`-Objekt zurückgegeben, dessen Intervalllänge der Unterschied zwischen den Zeitintervallen zweier Argumente ist.

Die zweite Funktion gibt ein `time_point` Objekt zurück, das einen Zeitpunkt darstellt, der durch die Negation des Zeitintervalls, das durch " *Dur*" dargestellt wird, von dem Zeitpunkt, der durch " *time*" angegeben wird, zurückgegeben wird.

Die dritte Funktion gibt ein `duration` Objekt zurück, das das Zeitintervall zwischen *Links* und *Rechts*darstellt.

## <a name="op_neq"></a>Operator! =

Ungleichheitsoperator für [duration](../standard-library/duration-class.md)- oder [time_point](../standard-library/time-point-class.md)-Objekte.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `duration` oder `time_point`-Objekt.

*Rechte*\
Das rechte `duration` oder `time_point`-Objekt.

### <a name="return-value"></a>Rückgabewert

Jede Funktion gibt `!(Left == Right)` zurück.

## <a name="op_star"></a>KOM

Multiplikationsoperator für [duration](../standard-library/chrono-operators.md#op_star)-Objekte.

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator*(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Mult);

template <class Rep1, class Rep2, class Period2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2>
   operator*(
       const Rep1& Mult,
       const duration<Rep2,
       Period2>& Dur);
```

### <a name="parameters"></a>Parameter

*Dur* -\
Ein `duration`-Objekt.

*Mult* -\
Ein Integralwert.

### <a name="return-value"></a>Rückgabewert

Jede Funktion gibt ein `duration` Objekt zurück, dessen Intervall *Länge mit der*Länge von " *mult* " multipliziert ist.

Sofern `is_convertible<Rep2, common_type<Rep1, Rep2>>` *nicht wahr ist*, wird die erste Funktion nicht an der Überladungsauflösung beteiligt. Weitere Informationen finden Sie unter [<type_traits>](../standard-library/type-traits.md).

Sofern `is_convertible<Rep1, common_type<Rep1, Rep2>>` *nicht wahr ist*, wird die zweite Funktion nicht an der Überladungsauflösung beteiligt. Weitere Informationen finden Sie unter [<type_traits>](../standard-library/type-traits.md).

## <a name="op_div"></a>KOM

Divisionsoperator für [duration](../standard-library/chrono-operators.md#op_star)-Objekte.

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator/(
     const duration<Rep1, Period1>& Dur,
     const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<Rep1, Rep2>::type
   operator/(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Parameter

*Dur* -\
Ein `duration`-Objekt.

*Div* -\
Ein Integralwert.

*Linker*\
Das linke `duration`-Objekt.

*Rechte*\
Das rechte `duration`-Objekt.

### <a name="return-value"></a>Rückgabewert

Der erste Operator gibt ein Duration-Objekt zurück, dessen Intervalllänge die Länge von *Dur* dividiert durch den Wert *div*ist.

Der zweite Operator gibt das Verhältnis der Intervall Längen von *Links* und *Rechts*zurück.

Sofern `is_convertible<Rep2, common_type<Rep1, Rep2>>` *nicht wahr ist* und `Rep2` keine Instanziierung von `duration` ist, wird der erste Operator nicht an der Überladungsauflösung beteiligt. Weitere Informationen finden Sie unter [<type_traits>](../standard-library/type-traits.md).

## <a name="op_add"></a>Operator +

Fügt [duration](../standard-library/duration-class.md)- und [time_point](../standard-library/time-point-class.md)-Objekte hinzu.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator+(
      const duration<Rep1, Period1>& Left,
      const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,
      const duration<Rep2, Period2>& Dur);

template <class Rep1, class Period1, class Clock, class Duration2>
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,
      const time_point<Clock, Duration2>& Time);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `duration` oder `time_point`-Objekt.

*Rechte*\
Das rechte `duration` oder `time_point`-Objekt.

*Zeit*\
Ein `time_point`-Objekt.

*Dur* -\
Ein `duration`-Objekt.

### <a name="return-value"></a>Rückgabewert

Die erste Funktion gibt ein `duration` Objekt zurück, das über ein Zeitintervall verfügt, das gleich der Summe der Intervalle von *Links* und *Rechts*ist.

Die zweite und dritte Funktion geben ein `time_point` Objekt zurück, das einen Zeitpunkt darstellt, der von *der Zeitspanne*bis zum Zeitpunkt des Intervalls von dem *Zeitpunkt, an*dem Sie sich befinden, von der Zeitspanne

## <a name="op_lt"></a>-Operator&lt;

Bestimmt, ob ein [duration](../standard-library/duration-class.md)- oder [time_point](../standard-library/time-point-class.md)-Objekt kleiner als ein anderes `duration`- oder `time_point`-Objekt ist.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `duration` oder `time_point`-Objekt.

*Rechte*\
Das rechte `duration` oder `time_point`-Objekt.

### <a name="return-value"></a>Rückgabewert

Die erste Funktion gibt **true** zurück, wenn die Intervalllänge von *left* kleiner als die Intervalllänge von *right*ist. Andernfalls gibt die Funktion **false**zurück.

Die zweite Funktion gibt " **true** " zurück, wenn " *left* " in der *rechten* Andernfalls gibt die Funktion **false**zurück.

## <a name="op_lt_eq"></a>Operator&lt;=

Bestimmt, ob ein [duration](../standard-library/duration-class.md)- oder [time_point](../standard-library/time-point-class.md)-Objekt kleiner oder gleich einem anderen `duration`- oder `time_point`-Objekt ist.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `duration` oder `time_point`-Objekt.

*Rechte*\
Das rechte `duration` oder `time_point`-Objekt.

### <a name="return-value"></a>Rückgabewert

Jede Funktion gibt `!(Right < Left)` zurück.

## <a name="op_eq_eq"></a>Operator = =

Bestimmt, ob zwei `duration`-Objekte Zeitintervalle mit derselben Länge darstellen, oder ob zwei `time_point`-Objekte den gleichen Zeitpunkt darstellen.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `duration` oder `time_point`-Objekt.

*Rechte*\
Das rechte `duration` oder `time_point`-Objekt.

### <a name="return-value"></a>Rückgabewert

Die erste Funktion gibt **true** zurück, wenn *left* und *right* Zeitintervalle mit derselben Länge darstellen. Andernfalls gibt die Funktion **false**zurück.

Die zweite Funktion gibt **true** zurück, wenn *left* und *right* denselben Zeitpunkt darstellen. Andernfalls gibt die Funktion **false**zurück.

## <a name="op_gt"></a>-Operator&gt;

Bestimmt, ob ein [duration](../standard-library/duration-class.md)- oder [time_point](../standard-library/time-point-class.md)-Objekt größer als ein anderes `duration`- oder `time_point`-Objekt ist.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `duration` oder `time_point`-Objekt.

*Rechte*\
Das rechte `duration` oder `time_point`-Objekt.

### <a name="return-value"></a>Rückgabewert

Jede Funktion gibt `Right < Left` zurück.

## <a name="op_gt_eq"></a>Operator&gt;=

Bestimmt, ob ein [duration](../standard-library/duration-class.md)- oder [time_point](../standard-library/time-point-class.md)-Objekt größer oder gleich einem anderen `duration`- oder `time_point`-Objekt ist.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `duration` oder `time_point`-Objekt.

*Rechte*\
Das rechte `duration` oder `time_point`-Objekt.

### <a name="return-value"></a>Rückgabewert

Jede Funktion gibt `!(Left < Right)` zurück.

## <a name="op_modulo"></a>Operator Modulo

Operator für Modulo-Vorgänge für [duration](../standard-library/duration-class.md)-Objekte.

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<Rep1, Period1, Rep2>::type
   operator%(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Parameter

*Dur* -\
Ein `duration`-Objekt.

*Div* -\
Ein Integralwert.

*Linker*\
Das linke `duration`-Objekt.

*Rechte*\
Das rechte `duration`-Objekt.

### <a name="return-value"></a>Rückgabewert

Die erste Funktion gibt ein `duration` Objekt zurück, dessen Intervalllänge den Wert " *Dur* Modulo *div*" hat.

Die zweite Funktion gibt einen Wert zurück, der *left* Modulo *right*darstellt.
