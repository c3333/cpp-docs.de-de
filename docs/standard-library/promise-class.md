---
title: promise-Klasse
ms.date: 10/18/2018
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.openlocfilehash: a6541fefb2423853f8e59a662e1c8a37777dc14c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323040"
---
# <a name="promise-class"></a>promise-Klasse

Beschreibt einen *asynchronen Anbieter*.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Versprechen](#promise)|Erstellt ein `promise`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[get_future](#get_future)|Gibt eine dieser Zusage zugeordnete [Zukunft](../standard-library/future-class.md) zurück.|
|[set_exception](#set_exception)|Legt das Ergebnis dieser Zusage atomisch zum Angeben einer Ausnahme fest.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Legt das Ergebnis dieser Zusage zum Angeben einer Ausnahme atomisch fest, und stellt die Benachrichtigung nur zu, nachdem alle Objekte eines lokalen Threads im aktuellen Thread zerstört wurden (normalerweise zur Threadbeendigung).|
|[set_value](#set_value)|Legt das Ergebnis dieser Zusage zum Angeben eines Werts atomisch fest.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Legt das Ergebnis dieser Zusage zum Angeben eines Werts atomisch fest, und stellt die Benachrichtigung nur zu, nachdem alle Objekte eines lokalen Threads im aktuellen Thread zerstört wurden (normalerweise zur Threadbeendigung).|
|[swap](#swap)|Tauscht den *zugeordneten asynchronen Zustand* dieser Zusage mit dem eines angegebenen Zusageobjekts aus.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Versprechen::operator=](#op_eq)|Zuweisung des Freigabestatus dieses Zusageobjekts.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

*Versprechen*

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<zukünftige>

**Namespace:** std

## <a name="promiseget_future"></a><a name="get_future"></a>Verheißung::get_future

Gibt ein [Zukunft](../standard-library/future-class.md)-Objekt zurück, das über den gleichen *zugeordneten asynchronen Zustand* wie die Zusage verfügt.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Zusageobjekt leer ist, löst diese Methode [future_error](../standard-library/future-error-class.md) mit einem [error_code](../standard-library/error-code-class.md) von `no_state` aus.

Wenn diese Methode bereits für ein Zusageobjekt mit dem gleichen zugeordneten asynchronen Zustand aufgerufen wurde, löst die Methode `future_error` mit `error_code` von `future_already_retrieved` aus.

## <a name="promiseoperator"></a><a name="op_eq"></a>Versprechen::operator=

Überträgt den *zugeordneten asynchronen Zustand* aus einem angegebenen `promise`-Objekt.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parameter

*Andere*\
Ein `promise` -Objekt.

### <a name="return-value"></a>Rückgabewert

`*this`

### <a name="remarks"></a>Bemerkungen

Dieser Operator überträgt den zugeordneten asynchronen Zustand von *Andere*. Nach der Übertragung ist *Andere* *leer.*

## <a name="promisepromise-constructor"></a><a name="promise"></a>versprechen::promise Konstruktor

Erstellt ein `promise`-Objekt.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parameter

*Al*\
Eine Speicherbelegung. Weitere Informationen finden Sie [ \<unter allocators>.](../standard-library/allocators-header.md)

*Andere*\
Ein `promise` -Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt ein *leeres* `promise`-Objekt.

Der zweite Konstruktor erstellt `promise` ein leeres Objekt und verwendet *Al* für die Speicherzuweisung.

Der dritte Konstruktor `promise` erstellt ein Objekt und überträgt den zugeordneten asynchronen Zustand aus *Anderen*und lässt *Andere* leer.

## <a name="promiseset_exception"></a><a name="set_exception"></a>Verheißung::set_exception

Es wird atomisch eine Ausnahme als Ergebnis dieses `promise`-Objekts gespeichert, und der *entsprechende asynchrone Zustand* wird auf *fertig* festgelegt.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Parameter

*Ohne*\
Ein [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr), der von dieser Methode als Ausnahmeergebnis gespeichert ist.

### <a name="remarks"></a>Bemerkungen

Wenn das `promise`-Objekt über keinen zugeordneten asynchronen Zustand verfügt, löst diese Methode [future_error](../standard-library/future-error-class.md) mit einem Fehlercode von `no_state` aus.

Wenn `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) oder [set_value_at_thread_exit](#set_value_at_thread_exit) bereits für ein `promise`-Objekt mit demselben zugeordneten asynchronen Zustand aufgerufen wurde, löst diese Methode `future_error` mit einem Fehlercode von `promise_already_satisfied` aus.

Aufgrund dieser Methode wird die Blockierung aller Threads, die auf dem zugeordneten asynchronen Zustand blockiert werden, aufgehoben.

## <a name="promiseset_exception_at_thread_exit"></a><a name="set_exception_at_thread_exit"></a>Verheißung::set_exception_at_thread_exit

Legt das Ergebnis von `promise` zum Angeben einer Ausnahme atomisch fest, und stellt die Benachrichtigung nur zu, nachdem alle Objekte eines lokalen Threads im aktuellen Thread zerstört wurden (normalerweise zur Threadbeendigung).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Parameter

*Ohne*\
Ein [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr), der von dieser Methode als Ausnahmeergebnis gespeichert ist.

### <a name="remarks"></a>Bemerkungen

Wenn das Zusageobjekt über keinen *zugeordneten asynchronen Zustand* verfügt, löst diese Methode [future_error](../standard-library/future-error-class.md) mit einem Fehlercode von `no_state` aus.

Wenn [set_exception](#set_exception)set_exception `set_exception_at_thread_exit`, [set_value](#set_value)oder [set_value_at_thread_exit](#set_value_at_thread_exit) bereits `promise` für ein Objekt mit demselben zugeordneten asynchronen Zustand aufgerufen wurde, löst diese Methode eine `future_error` mit einem Fehlercode von `promise_already_satisfied`aus.

Im Gegensatz zu [set_exception](#set_exception) wird der asynchrone zugeordnete Zustand von dieser Methode nicht auf „fertig“ festgelegt, bis alle Objekte eines lokalen Threads im aktuellen Thread zerstört wurden. Normalerweise kann die Blockierung von Threads, die auf dem zugeordneten asynchronen Zustand blockiert werden, nicht aufgehoben werden, bis der aktuelle Thread beendet wird.

## <a name="promiseset_value"></a><a name="set_value"></a>Verheißung::set_value

Es wird atomisch ein Wert als Ergebnis dieses `promise`-Objekts gespeichert, und der *entsprechende asynchrone Zustand* wird auf *fertig* festgelegt.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Parameter

*Val*\
Der als Ergebnis zu speichernde Wert.

### <a name="remarks"></a>Bemerkungen

Wenn das `promise`-Objekt über keinen zugeordneten asynchronen Zustand verfügt, löst diese Methode [future_error](../standard-library/future-error-class.md) mit einem Fehlercode von `no_state` aus.

Wenn [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value` oder [set_value_at_thread_exit](#set_value_at_thread_exit) bereits für ein `promise`-Objekt mit demselben zugeordneten asynchronen Zustand aufgerufen wurde, löst diese Methode `future_error` mit einem Fehlercode von `promise_already_satisfied` aus.

Aufgrund dieser Methode wird die Blockierung aller Threads, die auf dem zugeordneten asynchronen Zustand blockiert werden, aufgehoben.

Die erste Methode löst auch alle Ausnahmen aus, die ausgelöst werden, wenn *Val* in den zugeordneten asynchronen Zustand kopiert wird. In dieser Situation wird der zugeordnete asynchrone Zustand nicht auf "vorbereitet" festgelegt.

Die zweite Methode löst auch alle Ausnahmen aus, die ausgelöst werden, wenn *Val* in den zugeordneten asynchronen Zustand verschoben wird. In dieser Situation wird der zugeordnete asynchrone Zustand nicht auf "vorbereitet" festgelegt.

Für die Teilspezialisierung `promise<Ty&>`ist der gespeicherte Wert faktisch ein Verweis auf *Val*.

Für die Spezialisierung `promise<void>` ist kein gespeicherter Wert vorhanden.

## <a name="promiseset_value_at_thread_exit"></a><a name="set_value_at_thread_exit"></a>Verheißung::set_value_at_thread_exit

Speichert einen Wert atomisch als Ergebnis dieses `promise`-Objekts.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Parameter

*Val*\
Der als Ergebnis zu speichernde Wert.

### <a name="remarks"></a>Bemerkungen

Wenn das Zusageobjekt über keinen *zugeordneten asynchronen Zustand* verfügt, löst diese Methode [future_error](../standard-library/future-error-class.md) mit einem Fehlercode von `no_state` aus.

Wenn [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) oder `set_value_at_thread_exit` bereits für ein `promise`-Objekt mit demselben zugeordneten asynchronen Zustand aufgerufen wurde, löst diese Methode `future_error` mit einem Fehlercode von `promise_already_satisfied` aus.

Im Gegensatz zu `set_value`, wird der zugeordnete asynchrone Zustand erst auf "vorbereitet" festgelegt, nachdem alle Objekte eines lokalen Threads im aktuellen Thread zerstört wurden. Normalerweise kann die Blockierung von Threads, die auf dem zugeordneten asynchronen Zustand blockiert werden, nicht aufgehoben werden, bis der aktuelle Thread beendet wird.

Die erste Methode löst auch alle Ausnahmen aus, die ausgelöst werden, wenn *Val* in den zugeordneten asynchronen Zustand kopiert wird.

Die zweite Methode löst auch alle Ausnahmen aus, die ausgelöst werden, wenn *Val* in den zugeordneten asynchronen Zustand verschoben wird.

Für die Teilspezialisierung `promise<Ty&>`ist der gespeicherte Wert effektiv ein Verweis auf *Val*.

Für die Spezialisierung `promise<void>` ist kein gespeicherter Wert vorhanden.

## <a name="promiseswap"></a><a name="swap"></a>Versprechen::swap

Tauscht den *zugeordneten asynchronen Zustand* dieses Zusageobjekts mit dem eines angegebenen Objekts aus.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Parameter

*Andere*\
Ein `promise` -Objekt.

## <a name="see-also"></a>Siehe auch

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
