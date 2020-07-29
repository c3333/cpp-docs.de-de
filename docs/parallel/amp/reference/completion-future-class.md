---
title: completion_future-Klasse
ms.date: 11/04/2016
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
ms.openlocfilehash: 1863f0908753fb05abb01cf1bd2e34dc6649e0a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228491"
---
# <a name="completion_future-class"></a>completion_future-Klasse

Stellt ein "future"-Objekt dar, das einer asynchronen C++ AMP-Operation entspricht.

## <a name="syntax"></a>Syntax

```cpp
class completion_future;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[completion_future-Konstruktor](#ctor)|Initialisiert eine neue Instanz der `completion_future`-Klasse.|
|[~ completion_future-Dekonstruktor](#dtor)|Zerstört das `completion_future`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[get](#get)|Wartet, bis der zugeordnete asynchrone Vorgang beendet ist.|
|[Seitdem](#then)|Verkettet ein Rückruffunktionsobjekt mit dem `completion_future`-Objekt, das ausgeführt werden soll, wenn der zugeordnete asynchrone Vorgang beendet wird.|
|[to_task](#to_task)|Gibt ein `task`-Objekt zurück, das dem zugeordneten asynchronen Vorgang entspricht.|
|[gültigen](#valid)|Ruft einen booleschen Wert ab, der angibt, ob das Objekt einem asynchronen Vorgang zugeordnet ist.|
|[Warte](#wait)|Blockiert, bis der zugeordnete asynchrone Vorgang beendet ist.|
|[wait_for](#wait_for)|Blockiert, bis der zugeordnete asynchrone Vorgang beendet oder die Zeit, die von `_Rel_time` angegeben wird, abgelaufen ist.|
|[wait_until](#wait_until)|Blockiert, bis der zugeordnete asynchrone Vorgang beendet ist oder die aktuelle Uhrzeit den von `_Abs_time` angegebenen Wert überschreitet.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Operator Std:: shared_future\<void>](#operator_shared_future)|Konvertiert implizit das `completion_future`-Objekt zu einem `std::shared_future`-Objekt.|
|[Operator =](#operator_eq)|Kopiert den Inhalt des angegebenen `completion_future`-Objekts in dieses Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`completion_future`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** amprt. h

**Namespace:** Parallelität

## <a name="completion_future"></a><a name="ctor"></a>completion_future

Initialisiert eine neue Instanz der `completion_future`-Klasse.

### <a name="syntax"></a>Syntax

```cpp
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das `completion_future` Objekt, das kopiert oder verschoben werden soll.

### <a name="overloads-list"></a>Überladungsliste

|Name|Beschreibung|
|----------|-----------------|
|`completion_future();`|Initialisiert eine neue Instanz der- `completion_future` Klasse.|
|`completion_future(const completion_future& _Other);`|Initialisiert eine neue Instanz der- `completion_future` Klasse durch Kopieren eines Konstruktors.|
|`completion_future(completion_future&& _Other);`|Initialisiert eine neue Instanz der- `completion_future` Klasse durch Verschieben eines Konstruktors.|

## <a name="get"></a><a name="get"></a>Erhalten

Wartet, bis der zugeordnete asynchrone Vorgang beendet ist. Löst die gespeicherte Ausnahme aus, wenn während des asynchronen Vorgangs ein Fehler aufgetreten ist.

### <a name="syntax"></a>Syntax

```cpp
void get() const;
```

## <a name="operator-stdshared_futurevoid"></a><a name="operator_shared_future"></a>Operator Std:: shared_future\<void>

Konvertiert implizit das `completion_future`-Objekt zu einem `std::shared_future`-Objekt.

### <a name="syntax"></a>Syntax

```cpp
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `std::shared_future`-Objekt.

## <a name="operator"></a><a name="operator_eq"></a>Operator =

Kopiert den Inhalt des angegebenen `completion_future`-Objekts in dieses Objekt.

### <a name="syntax"></a>Syntax

```cpp
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das Objekt, aus dem kopiert wird.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `completion_future`-Objekt.

## <a name="overloads-list"></a>Überladungsliste

|Name|Beschreibung|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|Kopiert den Inhalt des angegebenen- `completion_future` Objekts unter Verwendung einer tiefen Kopie in diese.|
|`completion_future& operator=(completion_future&& _Other);`|Kopiert den Inhalt des angegebenen- `completion_future` Objekts unter Verwendung einer Verschiebungs Zuweisung in dieses Objekt.|

## <a name="then"></a><a name="then"></a>Seitdem

Verkettet ein Rückruffunktionsobjekt mit dem `completion_future`-Objekt, das ausgeführt werden soll, wenn der zugeordnete asynchrone Vorgang beendet wird.

### <a name="syntax"></a>Syntax

```cpp
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>Parameter

*_Functor*<br/>
Das Rückruf-Funktor.

*_Func*<br/>
Das Rückruf Funktions Objekt.

## <a name="to_task"></a><a name="to_task"></a>to_task

Gibt ein `task`-Objekt zurück, das dem zugeordneten asynchronen Vorgang entspricht.

### <a name="syntax"></a>Syntax

```cpp
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>Rückgabewert

Ein- `task` Objekt, das dem zugeordneten asynchronen Vorgang entspricht.

## <a name="valid"></a><a name="valid"></a>gültigen

Ruft einen booleschen Wert ab, der angibt, ob das Objekt einem asynchronen Vorgang zugeordnet ist.

### <a name="syntax"></a>Syntax

```cpp
bool valid() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das-Objekt einem asynchronen Vorgang zugeordnet ist. andernfalls **`false`** .

## <a name="wait"></a><a name="wait"></a>Warte

Blockiert, bis der zugeordnete asynchrone Vorgang beendet ist.

### <a name="syntax"></a>Syntax

```cpp
void wait() const;
```

## <a name="wait_for"></a><a name="wait_for"></a>wait_for

Blockiert, bis der zugeordnete asynchrone Vorgang beendet oder die Zeit, die von `_Rel_time` angegeben wird, abgelaufen ist.

### <a name="syntax"></a>Syntax

```cpp
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>Parameter

*_Rep*<br/>
Ein arithmetischer Typ, der die Anzahl von Zeiteinheiten darstellt.

*_Period*<br/>
Ein std::ratio, das die Anzahl von Sekunden darstellt, die pro Zeiteinheit verstreichen.

*_Rel_time*<br/>
Die maximale Zeitspanne, die auf den Abschluss der Operation gewartet wird.

### <a name="return-value"></a>Rückgabewert

Rückgabewerte:

- `std::future_status::deferred`, wenn der zugeordnete asynchrone Vorgang nicht ausgeführt wird.

- `std::future_status::ready`, wenn der zugeordnete asynchrone Vorgang abgeschlossen ist.

- `std::future_status::timeout`, wenn der angegebene Zeitraum verstrichen ist.

## <a name="wait_until"></a><a name="wait_until"></a>wait_until

Blockiert, bis der zugeordnete asynchrone Vorgang beendet ist oder die aktuelle Uhrzeit den von `_Abs_time` angegebenen Wert überschreitet.

### <a name="syntax"></a>Syntax

```cpp
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>Parameter

*_Clock*<br/>
Die Uhr, auf der der Zeitpunkt gemessen wird.

*_Duration*<br/>
Das Zeitintervall seit dem Beginn der Epoche von `_Clock`, nach der die Funktion durch einen Timeout beendet wird.

*_Abs_time*<br/>
Der Zeitpunkt, nach dem die Funktion durch einen Timeout beendet wird.

### <a name="return-value"></a>Rückgabewert

Rückgabewerte:

1. `std::future_status::deferred`, wenn der zugeordnete asynchrone Vorgang nicht ausgeführt wird.

1. `std::future_status::ready`, wenn der zugeordnete asynchrone Vorgang abgeschlossen ist.

1. `std::future_status::timeout`, wenn der angegebene Zeitraum verstrichen ist.

## <a name="completion_future"></a><a name="dtor"></a>~ completion_future

Zerstört das `completion_future`-Objekt.

### <a name="syntax"></a>Syntax

```cpp
~completion_future();
```

## <a name="see-also"></a>Siehe auch

[Parallelitäts Namespace (C++ amp)](concurrency-namespace-cpp-amp.md)
