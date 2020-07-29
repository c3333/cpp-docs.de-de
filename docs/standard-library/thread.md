---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 251a423829a048e3d67b0bcf83107f52c3fdafca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232845"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

Schließen Sie den Standard Header ein \<thread> , um die `thread` -Klasse und verschiedene unterstützende Funktionen zu definieren.

## <a name="syntax"></a>Syntax

```cpp
#include <thread>
```

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> In Code, der mit **/CLR**kompiliert wird, wird dieser Header blockiert.

Das- `__STDCPP_THREADS__` Makro wird als Wert ungleich 0 (null) definiert, um anzugeben, dass Threads von diesem Header unterstützt werden.

## <a name="members"></a>Member

### <a name="public-classes"></a>Öffentliche Klassen

|Name|Beschreibung|
|----------|-----------------|
|[Thread-Klasse](../standard-library/thread-class.md)|Definiert ein Objekt, das verwendet wird, um einen Ausführungs Thread in einer Anwendung zu beobachten und zu verwalten.|

### <a name="public-structures"></a>Öffentliche Strukturen

|Name|Beschreibung|
|----------|-----------------|
|[Hash-Struktur (C++-Standardbibliothek)](../standard-library/hash-structure-stl.md)|Definiert eine Member-Funktion, die einen Wert zurückgibt, der von einem eindeutig bestimmt wird `thread::id` . Die Member-Funktion definiert eine [Hash](../standard-library/hash-class.md) Funktion, die für die Zuordnung von Werten vom Typ `thread::id` zu einer Verteilung von Indexwerten geeignet ist.|

### <a name="public-functions"></a>Öffentliche Funktionen

|Name|Beschreibung|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Weist den aktuellen Ausführungsthread eindeutig aus.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Blockiert den aufrufenden Thread.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Blockiert den aufrufenden Thread mindestens bis zum angegebenen Zeitpunkt.|
|[swap](../standard-library/thread-functions.md#swap)|Tauscht die Zustände von zwei- `thread` Objekten aus.|
|[yield](../standard-library/thread-functions.md#yield)|Signalisiert dem Betriebssystem, andere Threads auszuführen, auch wenn der aktuelle Thread normalerweise weiterhin ausgeführt werden würde.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Operator>=-Operator](../standard-library/thread-operators.md#op_gt_eq)|Bestimmt, ob ein `thread::id`-Objekt größer als oder gleich einem anderen Objekt ist.|
|[Operator>-Operator](../standard-library/thread-operators.md#op_gt)|Bestimmt, ob ein `thread::id`-Objekt größer als ein anderes Objekt ist.|
|[Operator<=-Operator](../standard-library/thread-operators.md#op_lt_eq)|Bestimmt, ob ein `thread::id`-Objekt kleiner als oder gleich einem anderen Objekt ist.|
|[Operator<-Operator](../standard-library/thread-operators.md#op_lt)|Bestimmt, ob ein `thread::id`-Objekt kleiner als ein anderes Objekt ist.|
|[Operator! =-Operator](../standard-library/thread-operators.md#op_neq)|Überprüft zwei `thread::id`-Objekte auf Ungleichheit.|
|[Operator = =-Operator](../standard-library/thread-operators.md#op_eq_eq)|Überprüft zwei `thread::id`-Objekte auf Gleichheit.|
|[Operator<< -Operator](../standard-library/thread-operators.md#op_lt_lt)|Fügt eine Textdarstellung eines `thread::id`-Objekts in einen Stream ein.|

## <a name="see-also"></a>Siehe auch

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
