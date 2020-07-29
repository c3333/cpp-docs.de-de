---
title: shared_future-Klasse
ms.date: 11/04/2016
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.openlocfilehash: dcc1f4bf1ce25890945f1d9e207f2363122c0ad2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217492"
---
# <a name="shared_future-class"></a>shared_future-Klasse

Beschreibt ein *asynchrones Rückgabeobjekt*. Im Gegensatz zu einem [zukünftigen](../standard-library/future-class.md) Objekt, kann ein *asynchroner Anbieter* beliebig vielen `shared_future`-Objekten zugeordnet werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Bemerkungen

Rufen Sie keine anderen Methoden als `valid`, `operator=` und den Destruktor eines `shared_future`-Objekts auf, das *leer* ist.

`shared_future`-Objekte werden nicht synchronisiert. Aufrufen von Methoden für das gleiche Objekt von mehreren Threads führt zu einem Datenrace mit unvorhersehbaren Ergebnissen.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[shared_future](#shared_future)|Erstellt ein `shared_future`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[get](#get)|Ruft das Ergebnis ab, das im *zugeordneten asynchronen Zustand* gespeichert ist.|
|[gültigen](#valid)|Gibt an, ob das Objekt nicht leer ist.|
|[Warte](#wait)|Blockiert den aktuellen Thread, bis der zugeordnete asynchrone Zustand bereit ist.|
|[wait_for](#wait_for)|Blockiert, bis der zugeordnete asynchrone Zustand bereit ist, oder bis die angegebene Zeit verstrichen ist.|
|[wait_until](#wait_until)|Blockiert, bis der zugeordnete asynchrone Zustand bereit ist, oder bis ein angegebener Zeitpunkt erreicht ist.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[shared_future:: Operator =](#op_eq)|Weist einen neuen zugeordneten asynchronen Zustand zu.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<future>

**Namespace:** std

## <a name="shared_futureget"></a><a name="get"></a>shared_future:: Get

Ruft das Ergebnis ab, das im *zugeordneten asynchronen Zustand* gespeichert ist.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Bemerkungen

Wenn das Ergebnis eine Ausnahme ist, wird es erneut von der Methode ausgelöst. Andernfalls wird das Ergebnis zurückgegeben.

Bevor es das Ergebnis abruf, blockiert diese Methode den aktuellen Thread, bis der zugeordnete asynchrone Zustand bereit ist.

Bei der partiellen Spezialisierung `shared_future<Ty&>` ist der gespeicherte Wert tatsächlich ein Verweis auf das Objekt, das an den *asynchronen Anbieter* als Rückgabewert übermittelt wurde.

Da für die Spezialisierung kein gespeicherter Wert vorhanden `shared_future<void>` ist, gibt die Methode zurück **`void`** .

## <a name="shared_futureoperator"></a><a name="op_eq"></a>shared_future:: Operator =

Überträgt einen *zugeordneten asynchronen Zustand* aus einem angegebenen-Objekt.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `shared_future`-Objekt.

### <a name="return-value"></a>Rückgabewert

`*this`

### <a name="remarks"></a>Bemerkungen

Für den ersten Operator verfügt *right* nach dem Vorgang nicht mehr über einen zugeordneten asynchronen Zustand.

Bei der zweiten Methode behält *right* den zugeordneten asynchronen Zustand bei.

## <a name="shared_futureshared_future-constructor"></a><a name="shared_future"></a>shared_future:: shared_future-Konstruktor

Erstellt ein `shared_future`-Objekt.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein [zukünftiges](../standard-library/future-class.md) oder `shared_future`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt ein- `shared_future` Objekt, das über keinen *zugeordneten asynchronen Zustand*verfügt.

Mit dem zweiten und dritten Konstruktoren wird ein `shared_future` -Objekt erstellt und der zugehörige asynchrone Zustand von *Rechts*übertragen. *Right* weist keinen zugeordneten asynchronen Zustand mehr auf.

Der vierte Konstruktor erstellt ein- `shared_future` Objekt, das denselben zugeordneten asynchronen Zustand aufweist wie *Rechts*.

## <a name="shared_futurevalid"></a><a name="valid"></a>shared_future:: valid

Gibt an, ob das Objekt über einen *zugeordneten asynchronen Zustand*verfügt.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Objekt über einen zugeordneten asynchronen Zustand verfügt. andernfalls **`false`** .

## <a name="shared_futurewait"></a><a name="wait"></a>shared_future:: Wait

Blockiert den aktuellen Thread, bis der zugeordnete *asynchrone Zustand* *bereit*ist.

```cpp
void wait() const;
```

### <a name="remarks"></a>Bemerkungen

Ein zugeordneter asynchroner Zustand ist nur dann bereit, wenn sein asynchroner Anbieter einen Rückgabewert oder eine Ausnahme gespeichert hat.

## <a name="shared_futurewait_for"></a><a name="wait_for"></a>shared_future:: wait_for

Blockiert den aktuellen Thread, bis der zugeordnete asynchrone Zustand *bereit* oder eine angegebene Zeit verstrichen ist.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parameter

*Rel_time*\
Ein [chrono::duration](../standard-library/duration-class.md)-Objekt, das ein maximales Zeitintervall angibt, das der Thread blockiert.

### <a name="return-value"></a>Rückgabewert

Ein [future_status](../standard-library/future-enums.md#future_status), das den Grund für die Rückgabe angibt.

### <a name="remarks"></a>Bemerkungen

Ein zugeordneter asynchroner Zustand ist nur dann *bereit* , wenn sein asynchroner Anbieter einen Rückgabewert gespeichert oder eine Ausnahme gespeichert hat.

## <a name="shared_futurewait_until"></a><a name="wait_until"></a>shared_future:: wait_until

Blockiert den aktuelle Thread, bis der zugeordnete asynchrone Zustand *bereit* ist, oder bis ein angegebener Zeitpunkt verstrichen ist.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parameter

*Abs_time*\
Ein [chrono::time_point](../standard-library/time-point-class.md)-Objekt, das eine Zeit angibt, nach der der Thread die Blockierung aufheben kann.

### <a name="return-value"></a>Rückgabewert

Ein [future_status](../standard-library/future-enums.md#future_status), das den Grund für die Rückgabe angibt.

### <a name="remarks"></a>Bemerkungen

Ein zugeordneter asynchroner Zustand ist nur dann bereit, wenn sein asynchroner Anbieter einen Rückgabewert oder eine Ausnahme gespeichert hat.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
