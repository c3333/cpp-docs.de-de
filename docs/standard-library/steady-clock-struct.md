---
title: steady_clock-Struktur
ms.date: 05/22/2018
f1_keywords:
- chrono/std::chrono::steady_clock
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
ms.openlocfilehash: d21d5c2ed7ed667333007f3bd12d13f47b868380
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217401"
---
# <a name="steady_clock-struct"></a>steady_clock-Struktur

Stellt eine *Konstante* Uhr dar.

## <a name="syntax"></a>Syntax

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Bemerkungen

Unter Windows umschließt `steady_clock` die- `QueryPerformanceCounter` Funktion.

Eine Uhr ist *monoton*, wenn der von einem ersten Aufruf von `now` zurückgegebene Wert immer kleiner oder gleich dem Wert ist, der über einen nachfolgenden Aufruf von `now` zurückgegeben wird. Eine Uhr ist *gleichmäßig*, wenn sie *monoton* und die Zeit zwischen den Teilstrichen konstant ist.

`high_resolution_clock`ist eine typedef für `steady_clock` .

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`steady_clock::duration`|Ein Synonym für `nanoseconds` , das in definiert ist \<chrono> .|
|`steady_clock::period`|Ein Synonym für `nano` , das in definiert ist \<ratio> .|
|`steady_clock::rep`|Ein Synonym für **`long long`** , der Typ, der zum Darstellen der Anzahl von Takt Ticks in der enthaltenen Instanziierung von verwendet wird `duration` .|
|`steady_clock::time_point`|Ein Synonym für `chrono::time_point<steady_clock>`.|

## <a name="public-functions"></a>Öffentliche Funktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|`now`|Gibt die aktuelle Uhrzeit als- `time_point` Wert zurück.|

## <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|`steady_clock::is_steady`|Enthält **`true`** . Eine `steady_clock` ist *gleichmäßig*.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<chrono>

**Namespace:** std::chrono

## <a name="see-also"></a>Weitere Informationen

- [Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock-Struktur](../standard-library/system-clock-structure.md)
