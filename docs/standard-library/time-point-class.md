---
title: time_point-Klasse
ms.date: 03/27/2019
f1_keywords:
- chrono/std::chrono::time_point
- chrono/std::chrono::time_point::time_point
- chrono/std::chrono::time_point::max
- chrono/std::chrono::time_point::min
- chrono/std::chrono::time_point::time_since_epoch
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
helpviewer_keywords:
- std::chrono [C++], time_point
ms.openlocfilehash: e1de674d4a13ba465100923bffe6cba76e61ab4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368033"
---
# <a name="time_point-class"></a>time_point-Klasse

Mit `time_point` wird ein Typ beschrieben, der einen bestimmten Zeitpunkt darstellt. Er enthält ein Objekt des Typs [duration](../standard-library/duration-class.md), in dem die verstrichene Zeit seit dem vom Vorlagenargument `Clock` dargestellten Zeitraum gespeichert ist.

## <a name="syntax"></a>Syntax

```cpp
template <class Clock,
    class Duration = typename Clock::duration>
class time_point;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`time_point::clock`|Synonym für den Vorlagenparameter `Clock`.|
|`time_point::duration`|Synonym für den Vorlagenparameter `Duration`.|
|`time_point::period`|Synonym für den Namen `duration::period` des geschachtelten Typ.|
|`time_point::rep`|Synonym für den Namen `duration::rep` des geschachtelten Typ.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[time_point](#time_point)|Erstellt ein `time_point`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[max](#max)|Gibt die Obergrenze für `time_point::ref` an.|
|[min](#min)|Gibt die Untergrenze für `time_point::ref` an.|
|[time_since_epoch](#time_since_epoch)|Gibt den gespeicherten `duration`-Wert zurück.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[time_point::operator+=](#op_add_eq)|Fügt der gespeicherten Dauer einen angegebenen Wert hinzu.|
|[time_point::operator-=](#operator-_eq)|Subtrahiert einen angegebenen Wert von der gespeicherten Dauer.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<chrono>

**Namespace:** std::chrono

## <a name="time_pointmax"></a><a name="max"></a>time_point::max

Statische Methode, von der die Obergrenze für Werte vom Typ `time_point::ref` zurückgegeben wird.

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>Rückgabewert

Tatsächlich wird `time_point(duration::max())` zurückgegeben.

## <a name="time_pointmin"></a><a name="min"></a>time_point::min

Statische Methode, von der die Untergrenze für Werte vom Typ `time_point::ref` zurückgegeben wird.

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>Rückgabewert

Tatsächlich wird `time_point(duration::min())` zurückgegeben.

## <a name="time_pointoperator"></a><a name="op_add_eq"></a>time_point::operator+=

Fügt dem gespeicherten [duration](../standard-library/duration-class.md)-Wert einen angegebenen Wert hinzu.

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parameter

*Dur*\
Ein `duration` -Objekt.

### <a name="return-value"></a>Rückgabewert

Das `time_point`-Objekt nach Ausführung der Addition.

## <a name="time_pointoperator-"></a><a name="operator-_eq"></a>time_point::operator-=

Subtrahiert einen angegebenen Wert vom gespeicherten [duration](../standard-library/duration-class.md)-Wert.

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parameter

*Dur*\
Ein `duration` -Objekt.

### <a name="return-value"></a>Rückgabewert

Das `time_point`-Objekt nach Ausführung der Subtraktion.

## <a name="time_pointtime_point-constructor"></a><a name="time_point"></a>time_point::time_point Konstrukteur

Erstellt ein `time_point`-Objekt.

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>Parameter

*Dur*\
Ein [duration](../standard-library/duration-class.md)-Objekt.

*Tp*\
Ein `time_point` -Objekt.

### <a name="remarks"></a>Bemerkungen

Mit dem ersten Konstruktor wird ein Objekt erstellt, dessen gespeicherter `duration`-Wert [duration::zero](../standard-library/duration-class.md#zero) entspricht.

Der zweite Konstruktor erstellt ein Objekt, dessen gespeicherter Dauerwert gleich *Dur*ist. Sofern `is_convertible<Duration2, duration>` dies nicht zutrifft, nimmt der zweite Konstruktor nicht an der Überladungsauflösung teil. Weitere Informationen finden Sie unter [<type_traits>](../standard-library/type-traits.md).

Mit dem dritten Konstruktor wird der `duration`-Wert initialisiert, indem `Tp.time_since_epoch()` verwendet wird.

## <a name="time_pointtime_since_epoch"></a><a name="time_since_epoch"></a>time_point::time_since_epoch

Ruft den gespeicherten [duration](../standard-library/duration-class.md)-Wert ab.

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>Siehe auch

[Header-Dateien-Referenz](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
