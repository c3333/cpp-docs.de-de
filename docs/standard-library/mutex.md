---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: d5ff6f2a81a5caa564792e2c0cb43b7722c3e1dd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838549"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

Schließen Sie den-Standard Header ein, \<mutex> um die Klassen `mutex` , `recursive_mutex` , `timed_mutex` und, `recursive_timed_mutex` die Vorlagen `lock_guard` und `unique_lock` sowie unterstützende Typen und Funktionen, die Code Bereiche für den gegenseitigen Ausschluss definieren, zu definieren.

> [!WARNING]
> Ab Visual Studio 2015 basieren die Synchronisierungs Typen der C++-Standard Bibliothek auf Windows-Synchronisierungs primitiven und verwenden ConcRT nicht mehr (außer wenn die Zielplattform Windows XP ist). Die in definierten Typen \<mutex> dürfen nicht mit ConcRT-Typen oder-Funktionen verwendet werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<mutex>

**Namespace:** std

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> In Code, der mit **/CLR**kompiliert wird, wird dieser Header blockiert.

Die Klassen `mutex` und `recursive_mutex` sind *mutex-Typen*. Ein mutex-Typ verfügt über einen Standardkonstruktor und einen Destruktor, der keine Ausnahmen auslöst. Diese Objekte weisen Methoden auf, die gegenseitigen Ausschluss bereitstellen, wenn mehrere Threads versuchen, das gleiche Objekt zu sperren. Ein mutex-Typ enthält genauer gesagt die `lock`- `try_lock`- und `unlock`-Methoden:

- Die `lock`-Methode blockiert den aufrufenden Thread, bis der Thread in den Besitz von mutex gelangt. Der Rückgabewert wird ignoriert.

- Die `try_lock`-Methode versucht, ohne Blockierung in den Besitz von mutex zu gelangen. Der Rückgabetyp ist in konvertierbar **`bool`** und ist **`true`** , wenn die Methode den Besitz erhält, andernfalls **`false`** .

- Die `unlock`-Methode gibt den Besitz von mutex von dem aufrufenden Thread frei.

Sie können mutex-Typen als Typargumente verwenden, um die Vorlagen `lock_guard` und `unique_lock` zu instanziieren. Sie können Objekte dieser Typen als das `Lock`-Argument für die wait-Memberfunktionen in der Vorlage [condition_variable_any](../standard-library/condition-variable-any-class.md) verwenden.

Ein *timed_mutex-Typ* erfüllt die Anforderungen eines mutex-Typs. Außerdem verfügt sie über die `try_lock_for` -Methode und die- `try_lock_until` Methode, die mit einem Argument aufgerufen werden müssen, und muss einen Typ zurückgeben, der in konvertierbar ist **`bool`** . Ein zeitgesteuerter mutex-Typ kann diese Funktionen mit zusätzlichen Argumenten definieren, vorausgesetzt, dass diese zusätzlichen Argumente über Standardwerte verfügen.

- Die `try_lock_for`-Methode muss mit einem Argument (`Rel_time`) aufgerufen werden können, dessen Typ eine Instanziierung von [chrono::duration](../standard-library/duration-class.md) ist. Die Methode versucht, in den Besitz von mutex zu gelangen, gibt jedoch unabhängig vom Erfolg innerhalb der in `Rel_time` festgelegten Zeit einen Wert zurück. Der Rückgabewert wird in konvertiert, **`true`** Wenn die Methode den Besitz erhält; andernfalls wird der Rückgabewert in konvertiert **`false`** .

- Die `try_lock_until`-Methode muss mit einem Argument (`Abs_time`) aufgerufen werden können, dessen Typ eine Instanziierung von [chrono:: time_point](../standard-library/time-point-class.md) ist. Die Methode versucht, in den Besitz von mutex zu gelangen, gibt jedoch unabhängig vom Erfolg nicht später als innerhalb der in `Abs_time` festgelegten Zeit einen Wert zurück. Der Rückgabewert wird in konvertiert, **`true`** Wenn die Methode den Besitz erhält; andernfalls wird der Rückgabewert in konvertiert **`false`** .

Ein mutex-Typ wird auch als *sperrbarer Typ* bezeichnet. Wenn er die Memberfunktion `try_lock` nicht bereitstellt, handelt es sich um einen *sperrbaren Basistyp*. Ein timed_mutex-Typ wird auch als *zeitgesteuerter sperrbarer Typ* bezeichnet.

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[lock_guard-Klasse](../standard-library/lock-guard-class.md)|Stellt eine Vorlage dar, die zum Erstellen eines Objekts instanziiert werden kann, dessen Destruktor ein `mutex`-Objekt entsperrt.|
|[Mutex-Klasse (C++-Standard Bibliothek)](../standard-library/mutex-class-stl.md)|Stellt einen mutex-Typ dar. Verwenden Sie Objekte dieses Typs dazu, den gegenseitigen Ausschluss innerhalb eines Programms zu erzwingen.|
|[recursive_mutex-Klasse](../standard-library/recursive-mutex-class.md)|Stellt einen mutex-Typ dar. Das Verhalten von aufrufenden Sperrmethoden für Objekte, die bereits gesperrt sind, ist im Gegensatz zur `mutex`-Klasse klar definiert.|
|[recursive_timed_mutex-Klasse](../standard-library/recursive-timed-mutex-class.md)|Stellt einen zeitgesteuerten mutex-Typ dar. Verwenden Sie Objekte dieses Typs dazu, den gegenseitigen Ausschluss mit zeitbegrenzter Blockierung innerhalb eines Programms zu erzwingen. Im Gegensatz zu Objekten des `timed_mutex`-Typs sind die Auswirkungen von aufrufenden Sperrmethoden für `recursive_timed_mutex`-Objekte klar definiert.|
|[scoped_lock-Klasse](../standard-library/scoped-lock-class.md)||
|[timed_mutex-Klasse](../standard-library/timed-mutex-class.md)|Stellt einen zeitgesteuerten mutex-Typ dar. Verwenden Sie Objekte dieses Typs dazu, den gegenseitigen Ausschluss mit zeitbegrenzter Blockierung innerhalb eines Programms zu erzwingen.|
|[unique_lock-Klasse](../standard-library/unique-lock-class.md)|Stellt eine Vorlage dar, die zum Erstellen von Objekten instanziiert werden kann, die das Sperren und Entsperren von `mutex` verwalten.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[call_once](../standard-library/mutex-functions.md#call_once)|Stellt einen Mechanismus zum Aufrufen eines angegebenen aufrufbaren Objekts genau einmal während der Ausführung bereit.|
|[lock](../standard-library/mutex-functions.md#lock)|Versucht, alle Argumente ohne Deadlock zu sperren.|
|[swap](../standard-library/mutex-functions.md#swap)||
|[try_lock](../standard-library/mutex-functions.md#try_lock)||

### <a name="structs"></a>Strukturen

|Name|Beschreibung|
|-|-|
|[adopt_lock_t-Struktur](../standard-library/adopt-lock-t-structure.md)|Stellt einen Typ dar, der zum Definieren eines `adopt_lock`-Elements verwendet wird.|
|[defer_lock_t-Struktur](../standard-library/defer-lock-t-structure.md)|Stellt einen Typ dar, der ein `defer_lock`-Objekt definiert, das zum Auswählen eines überladenen Konstruktors von `unique_lock` verwendet wird.|
|[once_flag-Struktur](../standard-library/once-flag-structure.md)|Stellt eine dar **`struct`** , die mit der Vorlagen Funktion verwendet wird, `call_once` um sicherzustellen, dass der Initialisierungs Code nur einmal aufgerufen wird, auch wenn mehrere Ausführungs Threads vorhanden sind.|
|[try_to_lock_t-Struktur](../standard-library/try-to-lock-t-structure.md)|Stellt eine dar **`struct`** , die ein `try_to_lock` -Objekt definiert und verwendet wird, um einen der überladenen Konstruktoren von auszuwählen `unique_lock` .|

### <a name="variables"></a>Variables

|Name|Beschreibung|
|-|-|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Stellt ein Objekt dar, das an die Konstruktoren von `lock_guard` und `unique_lock` übergeben werden kann, um anzugeben, dass das auch an den Konstruktor übergebene mutex-Objekt gesperrt ist.|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|Stellt ein Objekt dar, das an den Konstruktor für `unique_lock` übergeben werden kann, um anzugeben, dass der Konstruktor das an diesen übergebene mutex-Objekt nicht sperren soll.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Stellt ein Objekt dar, das an den Konstruktor für `unique_lock` übergeben werden kann, um anzugeben, dass der Konstruktor das an diesen übergebene `mutex`-Objekt ohne Blockierung entsperren soll.|

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
