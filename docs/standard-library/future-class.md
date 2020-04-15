---
title: future-Klasse
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: e71c750ddeb198faa3ae9c5960b2668c376241ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370707"
---
# <a name="future-class"></a>future-Klasse

Beschreibt ein *asynchrones Rückgabeobjekt*.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Bemerkungen

Jeder standardmäßige *asynchrone Anbieter* gibt ein Objekt zurück, dessen Typ eine Instanziierung dieser Vorlage ist. Ein `future`-Objekt liefert den Einzigen Zugriff auf einen asynchronen Anbieter, dem es zugeordnet ist. Wenn Sie mehrere asynchrone Rückgabeobjekte benötigen, die dem gleichen asynchronen Anbieter zugeordnet sind,, kopieren Sie das `future`-Objekt in das [shared_future](../standard-library/shared-future-class.md)-Objekt.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Zukunft](#future)|Erstellt ein `future`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[get](#get)|Ruft das Ergebnis ab, das im zugeordneten asynchronen Zustand gespeichert ist.|
|[Freigeben](#share)|Konvertiert das Objekt in ein `shared_future`.|
|[Gültig](#valid)|Gibt an, ob das Objekt nicht leer ist.|
|[Warte](#wait)|Blockiert den aktuellen Thread, bis der zugeordnete asynchrone Zustand bereit ist.|
|[wait_for](#wait_for)|Blockiert, bis der zugeordnete asynchrone Zustand bereit ist, oder bis die angegebene Zeit verstrichen ist.|
|[wait_until](#wait_until)|Blockiert, bis der zugeordnete asynchrone Zustand bereit ist, oder bis ein angegebener Zeitpunkt erreicht ist.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[future::operator=](#op_eq)|Überträgt den zugeordneten asynchronen Zustand aus einem angegebenen Objekt.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<zukünftige>

**Namespace:** std

## <a name="futurefuture-constructor"></a><a name="future"></a>Zukunft::zukünftiger Konstrukteur

Erstellt ein `future`-Objekt.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parameter

*Andere*\
Ein `future` -Objekt.

### <a name="remarks"></a>Bemerkungen

Mit dem ersten Konstruktor wird ein `future`-Objekt erstellt, das über keinen zugeordneten asynchronen Zustand verfügt.

Der zweite Konstruktor `future` erstellt ein Objekt und überträgt den zugeordneten asynchronen Zustand aus *Anderen*. *Andere* haben keinen asynchronen Zustand mehr.

## <a name="futureget"></a><a name="get"></a>Zukunft::get

Ruft das Ergebnis ab, das im zugeordneten asynchronen Zustand gespeichert ist.

```cpp
Ty get();
```

### <a name="return-value"></a>Rückgabewert

Wenn das Ergebnis eine Ausnahme ist, wird es erneut von der Methode ausgelöst. Andernfalls wird das Ergebnis zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Bevor es das Ergebnis abruf, blockiert diese Methode den aktuellen Thread, bis der zugeordnete asynchrone Zustand bereit ist.

Für die Teilspezialisierung `future<Ty&>` ist der gespeicherte Wert praktisch ein Verweis auf das Objekt, das dem asynchronen Anbieter als Rückgabewert übergeben wurde.

Da für die Spezialisierung `future<void>`kein gespeicherter Wert vorhanden ist, gibt die Methode **void**zurück.

In anderen Spezialisierung verschiebt die Methode ihren Rückgabewert aus dem gespeicherten Wert. Deshalb sollten Sie diese Methode nur einmal aufrufen.

## <a name="futureoperator"></a><a name="op_eq"></a>zukunft::operator=

Überträgt einen zugeordneten asynchronen Zustand aus einem angegebenen Objekt.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `future` -Objekt.

### <a name="return-value"></a>Rückgabewert

`*this`

### <a name="remarks"></a>Bemerkungen

Nach der Übertragung verfügt *Right* nicht mehr über einen zugeordneten asynchronen Zustand.

## <a name="futureshare"></a><a name="share"></a>Zukunft::teilen

Konvertiert das Objekt in ein [shared_future](../standard-library/shared-future-class.md)-Objekt.

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Rückgabewert

`shared_future(move(*this))`

## <a name="futurevalid"></a><a name="valid"></a>Zukunft::gültig

Legt fest, ob das Objekt einen zugeordneten asynchronen Zustand hat.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn dem Objekt ein asynchroner Zustand zugeordnet ist; andernfalls **false**.

## <a name="futurewait"></a><a name="wait"></a>Zukunft::warten

Blockiert den aktuellen Thread, bis der zugeordnete asynchrone Zustand *bereit* ist.

```cpp
void wait() const;
```

### <a name="remarks"></a>Bemerkungen

Ein zugeordneter asynchroner Zustand ist nur *bereit,* wenn sein asynchroner Anbieter einen Rückgabewert oder eine Ausnahme gespeichert hat.

## <a name="futurewait_for"></a><a name="wait_for"></a>Zukunft::wait_for

Blockiert dem aktuelle Thread, bis der zugeordnete asynchrone Zustand *bereit* ist, oder bis ein angegebenes Zeitintervall verstrichen ist.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parameter

*Rel_time*\
Ein [chrono::duration](../standard-library/duration-class.md)-Objekt, das ein maximales Zeitintervall angibt, das der Thread blockiert.

### <a name="return-value"></a>Rückgabewert

Ein [future_status](../standard-library/future-enums.md#future_status), das den Grund für die Rückgabe angibt.

### <a name="remarks"></a>Bemerkungen

Ein zugeordneter asynchroner Zustand ist nur dann bereit, wenn sein asynchroner Anbieter einen Rückgabewert oder eine Ausnahme gespeichert hat.

## <a name="futurewait_until"></a><a name="wait_until"></a>Zukunft::wait_until

Blockiert den aktuelle Thread, bis der zugeordnete asynchrone Zustand *bereit* ist, oder bis ein angegebener Zeitpunkt verstrichen ist.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parameter

*Abs_time*\
Ein [chrono::time_point](../standard-library/time-point-class.md)-Objekt, das eine Zeit angibt, nach der der Thread die Blockierung aufheben kann.

### <a name="return-value"></a>Rückgabewert

Ein [future_status](../standard-library/future-enums.md#future_status), das den Grund für die Rückgabe angibt.

### <a name="remarks"></a>Bemerkungen

Ein zugeordneter asynchroner Zustand ist nur *bereit,* wenn sein asynchroner Anbieter einen Rückgabewert oder eine Ausnahme gespeichert hat.

## <a name="see-also"></a>Siehe auch

[Header-Dateien-Referenz](../standard-library/cpp-standard-library-header-files.md)\
[\<zukünftige>](../standard-library/future.md)
