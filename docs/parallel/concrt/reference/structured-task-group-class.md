---
title: structured_task_group-Klasse
ms.date: 11/04/2016
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
ms.openlocfilehash: 93dd79b755f79dcb4857c1b1c4856362b0bd45dd
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427362"
---
# <a name="structured_task_group-class"></a>structured_task_group-Klasse

Die `structured_task_group`-Klasse stellt eine stark strukturierte Auflistung paralleler Arbeit dar. Sie können einzelne parallele Aufgaben mithilfe von `structured_task_group`-Objekten in eine `task_handle` stellen und warten, bis sie abgeschlossen werden, oder Sie können die Aufgabengruppe abbrechen, bevor deren Ausführung beendet wird, wodurch auch alle Aufgaben abgebrochen werden, deren Ausführung nicht gestartet wurde.

## <a name="syntax"></a>Syntax

```cpp
class structured_task_group;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[structured_task_group](#ctor)|Ist überladen. Erstellt ein neues `structured_task_group`-Objekt.|
|[~ structured_task_group-Dekonstruktor](#dtor)|Zerstört ein `structured_task_group`-Objekt. Es wird erwartet, dass Sie vor dem Ausführen des Dekonstruktors entweder die `wait`-oder `run_and_wait`-Methode für das-Objekt aufruft, es sei denn, der Dekonstruktor wird aufgrund einer Ausnahme aufgrund der Stapel Auflösung ausgeführt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[cancel](#cancel)|Versucht, die Unterstruktur der Arbeit abzubrechen, die an dieser Aufgaben Gruppe verankert ist. Alle Aufgaben, die für die Aufgaben Gruppe geplant werden, werden, wenn möglich, vorübergehend abgebrochen.|
|[is_canceling](#is_canceling)|Informiert den Aufrufer darüber, ob die Aufgaben Gruppe derzeit in der Mitte eines Abbruchs liegt. Dies weist nicht unbedingt darauf hin, dass die `cancel`-Methode für das `structured_task_group` Objekt aufgerufen wurde (obwohl diese Methode sicherlich für die Rückgabe von **true**qualifiziert ist). Dies kann der Fall sein, wenn das `structured_task_group` Objekt Inline ausgeführt wird und eine Aufgaben Gruppe weiter oben in der Arbeitsstruktur abgebrochen wurde. In Fällen, in denen die Common Language Runtime feststellen kann, dass der Abbruch durch dieses `structured_task_group` Objekt fließt, wird auch **true** zurückgegeben.|
|[run](#run)|Ist überladen. Plant eine Aufgabe für das `structured_task_group` Objekt. Der Aufrufer verwaltet die Lebensdauer des `task_handle` Objekts, das im `_Task_handle`-Parameter übergeben wird. Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass die Aufgabe an der durch den-Parameter angegebenen Position vorangeht.|
|[run_and_wait](#run_and_wait)|Ist überladen. Plant, dass eine Aufgabe Inline im aufrufenden Kontext ausgeführt wird, wobei die Unterstützung des `structured_task_group` Objekts für vollständige Abbruch Unterstützung unterstützt wird. Wenn ein `task_handle` Objekt als Parameter an `run_and_wait`übergeben wird, ist der Aufrufer für die Verwaltung der Lebensdauer des `task_handle` Objekts verantwortlich. Die Funktion wartet dann, bis alle Aufgaben am `structured_task_group` Objekt entweder abgeschlossen oder abgebrochen wurden.|
|[Warte](#wait)|Wartet, bis alle Arbeiten am `structured_task_group` abgeschlossen oder abgebrochen wurden.|

## <a name="remarks"></a>Hinweise

Es gibt eine Reihe schwerwiegender Einschränkungen bei der Verwendung eines `structured_task_group` Objekts, um die Leistung zu steigern:

- Ein einzelnes `structured_task_group` Objekt kann nicht von mehreren Threads verwendet werden. Alle Vorgänge für ein `structured_task_group` Objekt müssen von dem Thread ausgeführt werden, der das Objekt erstellt hat. Die beiden Ausnahmen dieser Regel sind die `cancel`-und `is_canceling`Element Funktionen. Das Objekt ist möglicherweise nicht in der Erfassungs Liste eines Lambda-Ausdrucks enthalten und wird innerhalb einer Aufgabe verwendet, es sei denn, die Aufgabe verwendet einen der Abbruch Vorgänge.

- Alle Tasks, die für ein `structured_task_group` Objekt geplant sind, werden durch die Verwendung von `task_handle` Objekten geplant, bei denen Sie die Lebensdauer von explizit verwalten müssen.

- Mehrere Gruppen dürfen nur in einer absolut in der Reihenfolge verwendeten Reihenfolge verwendet werden. Wenn zwei `structured_task_group`-Objekte deklariert werden, muss das zweite, das deklariert wird (das innere eins), vor jeder Methode Zerstörung werden, außer `cancel` oder `is_canceling` auf dem ersten aufgerufen wird (der äußere). Diese Bedingung gilt sowohl für das einfache Deklarieren mehrerer `structured_task_group` Objekte innerhalb der gleichen oder funktionell geschachtelten Bereiche als auch für einen Task, der über die `run`-oder `run_and_wait` Methoden in `structured_task_group` die Warteschlange eingereiht wurde.

- Anders als bei der allgemeinen `task_group` Klasse sind alle Zustände in der `structured_task_group`-Klasse endgültig. Nachdem Sie der Gruppe Aufgaben in der Warteschlange hinzugefügt und darauf gewartet haben, dass Sie fertiggestellt werden, verwenden Sie die gleiche Gruppe möglicherweise nicht mehr.

Weitere Informationen finden Sie unter [Aufgaben Parallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`structured_task_group`

## <a name="requirements"></a>Voraussetzungen

**Header:** ppl. h

**Namespace:** Parallelität

## <a name="cancel"></a>Abbrechen

Versucht, die Unterstruktur der Arbeit abzubrechen, die an dieser Aufgaben Gruppe verankert ist. Alle Aufgaben, die für die Aufgaben Gruppe geplant werden, werden, wenn möglich, vorübergehend abgebrochen.

```cpp
void cancel();
```

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [Abbruch](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="is_canceling"></a>is_canceling

Informiert den Aufrufer darüber, ob die Aufgaben Gruppe derzeit in der Mitte eines Abbruchs liegt. Dies weist nicht unbedingt darauf hin, dass die `cancel`-Methode für das `structured_task_group` Objekt aufgerufen wurde (obwohl diese Methode sicherlich für die Rückgabe von **true**qualifiziert ist). Dies kann der Fall sein, wenn das `structured_task_group` Objekt Inline ausgeführt wird und eine Aufgaben Gruppe weiter oben in der Arbeitsstruktur abgebrochen wurde. In Fällen, in denen die Common Language Runtime feststellen kann, dass der Abbruch durch dieses `structured_task_group` Objekt fließt, wird auch **true** zurückgegeben.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Rückgabewert

Ein Hinweis darauf, ob sich das `structured_task_group` Objekt mitten in einem Abbruch befindet (oder sicher ist, dass es in Kürze ist).

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [Abbruch](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="run"></a>Lauf

Plant eine Aufgabe für das `structured_task_group` Objekt. Der Aufrufer verwaltet die Lebensdauer des `task_handle` Objekts, das im `_Task_handle`-Parameter übergeben wird. Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass die Aufgabe an der durch den-Parameter angegebenen Position vorangeht.

```cpp
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktions Objekts, das aufgerufen wird, um den Text des Task Handles auszuführen.

*_Task_handle*<br/>
Ein Handle für die geplante Arbeit. Beachten Sie, dass der Aufrufer für die Lebensdauer dieses Objekts zuständig ist. Die Laufzeit erwartet, dass Sie aktiv bleibt, bis entweder die `wait` oder `run_and_wait` Methode für dieses `structured_task_group` Objekt aufgerufen wurde.

*_Placement*<br/>
Ein Verweis auf den Speicherort, an dem die durch den `_Task_handle`-Parameter dargestellte Aufgabe ausgeführt werden soll.

### <a name="remarks"></a>Hinweise

Die Laufzeit erstellt eine Kopie der Arbeitsfunktion, die Sie an diese Methode übergeben. Alle Zustandsänderungen, die in einem Funktions Objekt auftreten, das Sie an diese Methode übergeben, werden nicht in Ihrer Kopie des Funktions Objekts angezeigt.

Wenn die `structured_task_group` als Ergebnis der Stapel Auflösung von einer Ausnahme zerstört wird, müssen Sie nicht garantieren, dass ein-oder `run_and_wait`-Methode `wait` aufgerufen wurde. In diesem Fall wird der Dekonstruktor entsprechend abbrechen und darauf warten, dass die durch den `_Task_handle`-Parameter dargestellte Aufgabe beendet wird.

Löst eine [Invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) Ausnahme aus, wenn das vom `_Task_handle`-Parameter angegebene Aufgaben handle bereits über die `run`-Methode für ein Aufgaben Gruppen Objekt geplant wurde und kein zwischengeschalteter Versuch der `wait`-oder `run_and_wait`-Methode für diese Aufgaben Gruppe aufgetreten ist.

## <a name="run_and_wait"></a>run_and_wait

Plant, dass eine Aufgabe Inline im aufrufenden Kontext ausgeführt wird, wobei die Unterstützung des `structured_task_group` Objekts für vollständige Abbruch Unterstützung unterstützt wird. Wenn ein `task_handle` Objekt als Parameter an `run_and_wait`übergeben wird, ist der Aufrufer für die Verwaltung der Lebensdauer des `task_handle` Objekts verantwortlich. Die Funktion wartet dann, bis alle Aufgaben am `structured_task_group` Objekt entweder abgeschlossen oder abgebrochen wurden.

```cpp
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktions Objekts, das aufgerufen wird, um die Aufgabe auszuführen.

*_Task_handle*<br/>
Ein Handle für die Aufgabe, die Inline im aufrufenden Kontext ausgeführt wird. Beachten Sie, dass der Aufrufer für die Lebensdauer dieses Objekts zuständig ist. Die Laufzeit wird fortgesetzt, bis die Ausführung der `run_and_wait`-Methode abgeschlossen ist.

*_Func*<br/>
Eine Funktion, die aufgerufen wird, um den Hauptteil der Arbeit aufzurufen. Hierbei kann es sich um einen Lambda-oder ein anderes Objekt handeln, das eine Version des Funktions aufrufoperators mit der Signatur `void operator()()`unterstützt.

### <a name="return-value"></a>Rückgabewert

Gibt an, ob der Warte Vorgang durch einen expliziten Abbruch Vorgang oder durch Auslösen einer Ausnahme von einer seiner Aufgaben abgebrochen wurde oder ob die Aufgaben Gruppe abgebrochen wurde. Weitere Informationen finden Sie unter [Task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Hinweise

Beachten Sie, dass mindestens eine der Aufgaben, die für dieses `structured_task_group` Objekt geplant sind, im aufrufenden Kontext Inline ausgeführt werden kann.

Wenn mindestens eine der Aufgaben, die für dieses `structured_task_group` Objekt geplant sind, eine Ausnahme auslöst, wählt die Common Language Runtime eine Ausnahme von Ihrer Wahl aus und gibt Sie aus dem Aufrufen der `run_and_wait`-Methode weiter.

Nachdem diese Funktion zurückgegeben wurde, wird das `structured_task_group` Objekt in einem Endzustand behandelt und sollte nicht verwendet werden. Beachten Sie, dass die Verwendung nach der Rückgabe der `run_and_wait`-Methode zu einem nicht definierten Verhalten führt.

Im nicht außergewöhnlichen Ausführungs Pfad haben Sie die Möglichkeit, entweder diese Methode oder die `wait` Methode aufzurufen, bevor der Dekonstruktor des `structured_task_group` ausgeführt wird.

## <a name="ctor"></a>structured_task_group

Erstellt ein neues `structured_task_group`-Objekt.

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Parameter

*_CancellationToken*<br/>
Ein Abbruch Token, das dieser strukturierten Aufgaben Gruppe zugeordnet werden soll. Die strukturierte Aufgaben Gruppe wird abgebrochen, wenn das Token abgebrochen wird.

### <a name="remarks"></a>Hinweise

Der Konstruktor, der ein Abbruch Token annimmt, erstellt eine `structured_task_group`, die abgebrochen wird, wenn die dem Token zugeordnete Quelle abgebrochen wird. Das Bereitstellen eines expliziten Abbruch Tokens isoliert diese strukturierte Aufgaben Gruppe auch von der Teilnahme an einem impliziten Abbruch von einer übergeordneten Gruppe mit einem anderen Token oder ohne Token.

## <a name="dtor"></a>~ structured_task_group

Zerstört ein `structured_task_group`-Objekt. Es wird erwartet, dass Sie vor dem Ausführen des Dekonstruktors entweder die `wait`-oder `run_and_wait`-Methode für das-Objekt aufruft, es sei denn, der Dekonstruktor wird aufgrund einer Ausnahme aufgrund der Stapel Auflösung ausgeführt.

```cpp
~structured_task_group();
```

### <a name="remarks"></a>Hinweise

Wenn der Dekonstruktor als Ergebnis der normalen Ausführung ausgeführt wird (z. b. aufgrund einer Ausnahme keine Stapel entruppe) und weder die `wait` noch `run_and_wait` Methoden aufgerufen wurden, kann der Dekonstruktor eine [Missing_wait](missing-wait-class.md) Ausnahme auslösen.

## <a name="wait"></a>Warte

Wartet, bis alle Arbeiten am `structured_task_group` abgeschlossen oder abgebrochen wurden.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Rückgabewert

Gibt an, ob der Warte Vorgang durch einen expliziten Abbruch Vorgang oder durch Auslösen einer Ausnahme von einer seiner Aufgaben abgebrochen wurde oder ob die Aufgaben Gruppe abgebrochen wurde. Weitere Informationen finden Sie unter [Task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Hinweise

Beachten Sie, dass mindestens eine der Aufgaben, die für dieses `structured_task_group` Objekt geplant sind, im aufrufenden Kontext Inline ausgeführt werden kann.

Wenn mindestens eine der Aufgaben, die für dieses `structured_task_group` Objekt geplant sind, eine Ausnahme auslöst, wählt die Common Language Runtime eine Ausnahme von Ihrer Wahl aus und gibt Sie aus dem Aufrufen der `wait`-Methode weiter.

Nachdem diese Funktion zurückgegeben wurde, wird das `structured_task_group` Objekt in einem Endzustand behandelt und sollte nicht verwendet werden. Beachten Sie, dass die Verwendung nach der Rückgabe der `wait`-Methode zu einem nicht definierten Verhalten führt.

Im nicht außergewöhnlichen Ausführungs Pfad haben Sie die Möglichkeit, entweder diese Methode oder die `run_and_wait` Methode aufzurufen, bevor der Dekonstruktor des `structured_task_group` ausgeführt wird.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[task_group-Klasse](task-group-class.md)<br/>
[task_handle-Klasse](task-handle-class.md)
