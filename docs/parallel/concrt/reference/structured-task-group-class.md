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
ms.openlocfilehash: 44fd2a42f4c98a569e985449f0c55102a9cbc3a6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231675"
---
# <a name="structured_task_group-class"></a>structured_task_group-Klasse

Die `structured_task_group`-Klasse stellt eine stark strukturierte Auflistung paralleler Arbeit dar. Sie können einzelne parallele Aufgaben mithilfe von `structured_task_group`-Objekten in eine `task_handle` stellen und warten, bis sie abgeschlossen werden, oder Sie können die Aufgabengruppe abbrechen, bevor deren Ausführung beendet wird, wodurch auch alle Aufgaben abgebrochen werden, deren Ausführung nicht gestartet wurde.

## <a name="syntax"></a>Syntax

```cpp
class structured_task_group;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[structured_task_group](#ctor)|Ist überladen. Erstellt ein neues `structured_task_group`-Objekt.|
|[~ structured_task_group-Dekonstruktor](#dtor)|Zerstört ein `structured_task_group` -Objekt. Es wird erwartet `wait` `run_and_wait` , dass Sie vor dem Ausführen des Dekonstruktors entweder die-oder-Methode für das-Objekt aufruft, es sei denn, der Dekonstruktor wird aufgrund einer Ausnahme als Ergebnis der Stapel Auflösung ausgeführt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[cancel](#cancel)|Versucht, die Unterstruktur der Arbeit abzubrechen, die an dieser Aufgaben Gruppe verankert ist. Alle Aufgaben, die für die Aufgaben Gruppe geplant werden, werden, wenn möglich, vorübergehend abgebrochen.|
|[is_canceling](#is_canceling)|Informiert den Aufrufer darüber, ob die Aufgaben Gruppe derzeit in der Mitte eines Abbruchs liegt. Dies weist nicht unbedingt darauf hin, dass die- `cancel` Methode für das-Objekt aufgerufen wurde `structured_task_group` (obwohl diese Methode sicherlich für die Rückgabe qualifiziert ist **`true`** ). Dies kann der Fall sein, wenn das `structured_task_group` Objekt Inline ausgeführt wird und eine Aufgaben Gruppe weiter oben in der Arbeitsstruktur abgebrochen wurde. In Fällen, in denen die Common Language Runtime feststellen kann, dass der Abbruch durch dieses `structured_task_group` Objekt fließt, **`true`** wird ebenfalls zurückgegeben.|
|[Lauf](#run)|Ist überladen. Plant eine Aufgabe für das- `structured_task_group` Objekt. Der Aufrufer verwaltet die Lebensdauer des-Objekts, das `task_handle` im-Parameter übergeben wird `_Task_handle` . Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass die Aufgabe an der durch den-Parameter angegebenen Position für die Ausführung verzerrt wird.|
|[run_and_wait](#run_and_wait)|Ist überladen. Plant eine Aufgabe, die Inline im aufrufenden Kontext ausgeführt werden soll, und unterstützt das- `structured_task_group` Objekt für die vollständige Abbruch Unterstützung. Wenn ein- `task_handle` Objekt als Parameter an übergeben wird `run_and_wait` , ist der Aufrufer für die Verwaltung der Lebensdauer des- `task_handle` Objekts verantwortlich. Die Funktion wartet dann, bis die gesamte Arbeit an dem `structured_task_group` Objekt entweder abgeschlossen oder abgebrochen wurde.|
|[Warte](#wait)|Wartet, bis die gesamte Arbeit an `structured_task_group` abgeschlossen ist oder abgebrochen wurde.|

## <a name="remarks"></a>Bemerkungen

Die Verwendung eines-Objekts hat eine Reihe schwerwiegender Einschränkungen `structured_task_group` , um die Leistung zu steigern:

- Ein einzelnes- `structured_task_group` Objekt kann nicht von mehreren Threads verwendet werden. Alle Vorgänge für ein- `structured_task_group` Objekt müssen von dem Thread ausgeführt werden, der das-Objekt erstellt hat. Die zwei Ausnahmen für diese Regel sind die-Member `cancel` -Funktionen und `is_canceling` . Das Objekt ist möglicherweise nicht in der Erfassungs Liste eines Lambda-Ausdrucks enthalten und wird innerhalb einer Aufgabe verwendet, es sei denn, die Aufgabe verwendet einen der Abbruch Vorgänge.

- Alle Tasks, die für ein- `structured_task_group` Objekt geplant sind, werden durch die Verwendung von- `task_handle` Objekten geplant, die die Lebensdauer von explizit verwalten müssen.

- Mehrere Gruppen dürfen nur in einer absolut in der Reihenfolge verwendeten Reihenfolge verwendet werden. Wenn zwei- `structured_task_group` Objekte deklariert werden, muss der zweite, der deklariert wird (der innere), vor jeder Methode Zerstörung werden, außer `cancel` oder `is_canceling` wird für den ersten aufgerufen (der äußere). Diese Bedingung gilt sowohl für das einfache Deklarieren mehrerer `structured_task_group` Objekte innerhalb derselben oder funktionell geschachtelter Bereiche als auch für eine Aufgabe, die `structured_task_group` über die-Methode oder die-Methode in die Warteschlange eingereiht wurde `run` `run_and_wait` .

- Anders als bei der allgemeinen `task_group` Klasse sind alle Zustände in der `structured_task_group` Klasse endgültig. Nachdem Sie der Gruppe Aufgaben in der Warteschlange hinzugefügt und darauf gewartet haben, dass Sie fertiggestellt werden, verwenden Sie die gleiche Gruppe möglicherweise nicht mehr.

Weitere Informationen finden Sie unter [Aufgaben Parallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`structured_task_group`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ppl. h

**Namespace:** Parallelität

## <a name="cancel"></a><a name="cancel"></a>Abbrechen

Versucht, die Unterstruktur der Arbeit abzubrechen, die an dieser Aufgaben Gruppe verankert ist. Alle Aufgaben, die für die Aufgaben Gruppe geplant werden, werden, wenn möglich, vorübergehend abgebrochen.

```cpp
void cancel();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Abbruch](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="is_canceling"></a><a name="is_canceling"></a>is_canceling

Informiert den Aufrufer darüber, ob die Aufgaben Gruppe derzeit in der Mitte eines Abbruchs liegt. Dies weist nicht unbedingt darauf hin, dass die- `cancel` Methode für das-Objekt aufgerufen wurde `structured_task_group` (obwohl diese Methode sicherlich für die Rückgabe qualifiziert ist **`true`** ). Dies kann der Fall sein, wenn das `structured_task_group` Objekt Inline ausgeführt wird und eine Aufgaben Gruppe weiter oben in der Arbeitsstruktur abgebrochen wurde. In Fällen, in denen die Common Language Runtime feststellen kann, dass der Abbruch durch dieses `structured_task_group` Objekt fließt, **`true`** wird ebenfalls zurückgegeben.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Rückgabewert

Ein Hinweis darauf, ob `structured_task_group` sich das Objekt in der Mitte eines Abbruchs befindet (oder in Kürze).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Abbruch](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="run"></a><a name="run"></a>Lauf

Plant eine Aufgabe für das- `structured_task_group` Objekt. Der Aufrufer verwaltet die Lebensdauer des-Objekts, das `task_handle` im-Parameter übergeben wird `_Task_handle` . Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass die Aufgabe an der durch den-Parameter angegebenen Position für die Ausführung verzerrt wird.

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
Ein Handle für die geplante Arbeit. Beachten Sie, dass der Aufrufer für die Lebensdauer dieses Objekts zuständig ist. Die Laufzeit erwartet weiterhin, bis die-Methode oder die- `wait` `run_and_wait` Methode für dieses Objekt aufgerufen wurde `structured_task_group` .

*_Placement*<br/>
Ein Verweis auf den Speicherort, an dem die durch den-Parameter dargestellte Aufgabe `_Task_handle` ausgeführt werden soll.

### <a name="remarks"></a>Bemerkungen

Die Laufzeit erstellt eine Kopie der Arbeitsfunktion, die Sie an diese Methode übergeben. Alle Zustandsänderungen, die in einem Funktions Objekt auftreten, das Sie an diese Methode übergeben, werden nicht in Ihrer Kopie des Funktions Objekts angezeigt.

Wenn `structured_task_group` als Ergebnis der Stapel Entsicherung von einer Ausnahme zerstört wird, müssen Sie nicht sicherstellen, dass ein-oder-Methode aufgerufen wurde `wait` `run_and_wait` . In diesem Fall wird der Dekonstruktor entsprechend abbrechen und darauf warten, dass die vom-Parameter dargestellte Aufgabe `_Task_handle` beendet wird.

Löst eine [Invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) Ausnahme aus, wenn das vom-Parameter angegebene Aufgaben Handle `_Task_handle` bereits über die-Methode für ein Aufgaben Gruppen Objekt geplant wurde und kein zwischengeschalteter `run` Aufrufversuch der- `wait` oder- `run_and_wait` Methode für diese Aufgaben Gruppe aufgetreten ist.

## <a name="run_and_wait"></a><a name="run_and_wait"></a>run_and_wait

Plant eine Aufgabe, die Inline im aufrufenden Kontext ausgeführt werden soll, und unterstützt das- `structured_task_group` Objekt für die vollständige Abbruch Unterstützung. Wenn ein- `task_handle` Objekt als Parameter an übergeben wird `run_and_wait` , ist der Aufrufer für die Verwaltung der Lebensdauer des- `task_handle` Objekts verantwortlich. Die Funktion wartet dann, bis die gesamte Arbeit an dem `structured_task_group` Objekt entweder abgeschlossen oder abgebrochen wurde.

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
Ein Handle für die Aufgabe, die Inline im aufrufenden Kontext ausgeführt wird. Beachten Sie, dass der Aufrufer für die Lebensdauer dieses Objekts zuständig ist. Die Laufzeit wird fortgesetzt, bis die `run_and_wait` Ausführung der Methode abgeschlossen ist.

*_Func*<br/>
Eine Funktion, die aufgerufen wird, um den Hauptteil der Arbeit aufzurufen. Hierbei kann es sich um einen Lambda-oder ein anderes Objekt handeln, das eine Version des Funktions aufrufoperators mit der Signatur unterstützt `void operator()()` .

### <a name="return-value"></a>Rückgabewert

Gibt an, ob der Warte Vorgang durch einen expliziten Abbruch Vorgang oder durch Auslösen einer Ausnahme von einer seiner Aufgaben abgebrochen wurde oder ob die Aufgaben Gruppe abgebrochen wurde. Weitere Informationen finden Sie unter [Task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass mindestens eine der Aufgaben, die für dieses Objekt geplant sind, `structured_task_group` Inline im aufrufenden Kontext ausgeführt werden kann.

Wenn eine oder mehrere der Aufgaben, die für dieses `structured_task_group` Objekt geplant sind, eine Ausnahme auslösen, wählt die Common Language Runtime eine solche Ausnahme aus und gibt Sie aus dem Aufrufen der- `run_and_wait` Methode weiter.

Nachdem diese Funktion zurückgegeben wurde, `structured_task_group` wird das-Objekt in einem Endzustand behandelt und sollte nicht verwendet werden. Beachten Sie, dass die Auslastung nach der `run_and_wait` Rückgabe der Methode zu einem nicht definierten Verhalten führt.

Im nicht außergewöhnlichen Ausführungs Pfad haben Sie die Möglichkeit, entweder diese Methode oder die-Methode aufzurufen, `wait` bevor der Dekonstruktor von `structured_task_group` ausgeführt wird.

## <a name="structured_task_group"></a><a name="ctor"></a>structured_task_group

Erstellt ein neues `structured_task_group`-Objekt.

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Parameter

*_CancellationToken*<br/>
Ein Abbruch Token, das dieser strukturierten Aufgaben Gruppe zugeordnet werden soll. Die strukturierte Aufgaben Gruppe wird abgebrochen, wenn das Token abgebrochen wird.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor, der ein Abbruch Token annimmt, erstellt eine `structured_task_group` , die abgebrochen wird, wenn die dem Token zugeordnete Quelle abgebrochen wird. Das Bereitstellen eines expliziten Abbruch Tokens isoliert diese strukturierte Aufgaben Gruppe auch von der Teilnahme an einem impliziten Abbruch von einer übergeordneten Gruppe mit einem anderen Token oder ohne Token.

## <a name="structured_task_group"></a><a name="dtor"></a>~ structured_task_group

Zerstört ein `structured_task_group` -Objekt. Es wird erwartet `wait` `run_and_wait` , dass Sie vor dem Ausführen des Dekonstruktors entweder die-oder-Methode für das-Objekt aufruft, es sei denn, der Dekonstruktor wird aufgrund einer Ausnahme als Ergebnis der Stapel Auflösung ausgeführt.

```cpp
~structured_task_group();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Dekonstruktor als Ergebnis der normalen Ausführung ausgeführt wird (z. b. aufgrund einer Ausnahme kein Stapel entwickeln) und weder die-noch die- `wait` `run_and_wait` Methode aufgerufen wurde, kann der Dekonstruktor eine [Missing_wait](missing-wait-class.md) Ausnahme auslösen.

## <a name="wait"></a><a name="wait"></a>Warte

Wartet, bis die gesamte Arbeit an `structured_task_group` abgeschlossen ist oder abgebrochen wurde.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Rückgabewert

Gibt an, ob der Warte Vorgang durch einen expliziten Abbruch Vorgang oder durch Auslösen einer Ausnahme von einer seiner Aufgaben abgebrochen wurde oder ob die Aufgaben Gruppe abgebrochen wurde. Weitere Informationen finden Sie unter [Task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass mindestens eine der Aufgaben, die für dieses Objekt geplant sind, `structured_task_group` Inline im aufrufenden Kontext ausgeführt werden kann.

Wenn eine oder mehrere der Aufgaben, die für dieses `structured_task_group` Objekt geplant sind, eine Ausnahme auslösen, wählt die Common Language Runtime eine solche Ausnahme aus und gibt Sie aus dem Aufrufen der- `wait` Methode weiter.

Nachdem diese Funktion zurückgegeben wurde, `structured_task_group` wird das-Objekt in einem Endzustand behandelt und sollte nicht verwendet werden. Beachten Sie, dass die Auslastung nach der `wait` Rückgabe der Methode zu einem nicht definierten Verhalten führt.

Im nicht außergewöhnlichen Ausführungs Pfad haben Sie die Möglichkeit, entweder diese Methode oder die-Methode aufzurufen, `run_and_wait` bevor der Dekonstruktor von `structured_task_group` ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[Task_group-Klasse](task-group-class.md)<br/>
[task_handle-Klasse](task-handle-class.md)
