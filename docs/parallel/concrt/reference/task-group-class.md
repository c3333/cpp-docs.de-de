---
title: task_group-Klasse
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 4d11a7fc25d95884418a3062721df75cc11be520
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224954"
---
# <a name="task_group-class"></a>task_group-Klasse

Die `task_group`-Klasse stellt eine Auflistung der parallelen Arbeit dar, auf die gewartet oder die abgebrochen werden kann.

## <a name="syntax"></a>Syntax

```cpp
class task_group;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[task_group](#ctor)|Ist überladen. Erstellt ein neues `task_group`-Objekt.|
|[~ Task_group-Dekonstruktor](#dtor)|Zerstört ein `task_group` -Objekt. Es wird erwartet, dass Sie die- `wait` Methode oder die- `run_and_wait` Methode für das-Objekt vor dem Ausführen des Dekonstruktors aufruft, es sei denn, der Dekonstruktor wird aufgrund einer Ausnahme als Ergebnis der Stapel Auflösung ausgeführt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[cancel](#cancel)|Versucht, die Unterstruktur der Arbeit abzubrechen, die an dieser Aufgaben Gruppe verankert ist. Alle Aufgaben, die für die Aufgaben Gruppe geplant werden, werden, wenn möglich, vorübergehend abgebrochen.|
|[is_canceling](#is_canceling)|Informiert den Aufrufer darüber, ob die Aufgaben Gruppe derzeit in der Mitte eines Abbruchs liegt. Dies weist nicht unbedingt darauf hin, dass die- `cancel` Methode für das-Objekt aufgerufen wurde `task_group` (obwohl diese Methode sicherlich für die Rückgabe qualifiziert ist **`true`** ). Dies kann der Fall sein, wenn das `task_group` Objekt Inline ausgeführt wird und eine Aufgaben Gruppe weiter oben in der Arbeitsstruktur abgebrochen wurde. In Fällen, in denen die Common Language Runtime feststellen kann, dass der Abbruch durch dieses `task_group` Objekt fließt, **`true`** wird ebenfalls zurückgegeben.|
|[Lauf](#run)|Ist überladen. Plant eine Aufgabe für das- `task_group` Objekt. Wenn ein- `task_handle` Objekt als Parameter an übergeben wird `run` , ist der Aufrufer für die Verwaltung der Lebensdauer des- `task_handle` Objekts verantwortlich. Die Version der-Methode, die einen Verweis auf ein Funktions Objekt als Parameter annimmt, umfasst die Heap Zuordnung innerhalb der Laufzeit, die weniger gut ausgeführt werden kann als die Verwendung der-Version, die einen Verweis auf ein- `task_handle` Objekt annimmt. Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass die Aufgabe an der durch den-Parameter angegebenen Position für die Ausführung verzerrt wird.|
|[run_and_wait](#run_and_wait)|Ist überladen. Plant eine Aufgabe, die Inline im aufrufenden Kontext ausgeführt werden soll, und unterstützt das- `task_group` Objekt für die vollständige Abbruch Unterstützung. Die Funktion wartet dann, bis die gesamte Arbeit an dem `task_group` Objekt entweder abgeschlossen oder abgebrochen wurde. Wenn ein- `task_handle` Objekt als Parameter an übergeben wird `run_and_wait` , ist der Aufrufer für die Verwaltung der Lebensdauer des- `task_handle` Objekts verantwortlich.|
|[Warte](#wait)|Wartet, bis die gesamte Arbeit an dem `task_group` Objekt entweder abgeschlossen oder abgebrochen wurde.|

## <a name="remarks"></a>Bemerkungen

Anders als bei der stark eingeschränkten `structured_task_group` Klasse `task_group` ist die Klasse viel allgemeineres Konstrukt. Sie verfügt nicht über die Einschränkungen, die durch [structured_task_group](structured-task-group-class.md)beschrieben werden. `task_group`Objekte können problemlos Thread übergreifend verwendet und in frei Form Weise genutzt werden. Der Nachteil des- `task_group` Konstrukts besteht darin, dass es möglicherweise nicht und das- `structured_task_group` Konstrukt für Aufgaben, die eine kleine Menge an Arbeit ausführen, nicht ausgeführt wird.

Weitere Informationen finden Sie unter [Aufgaben Parallelität](../task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`task_group`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ppl. h

**Namespace:** Parallelität

## <a name="cancel"></a><a name="cancel"></a>Abbrechen

Versucht, die Unterstruktur der Arbeit abzubrechen, die an dieser Aufgaben Gruppe verankert ist. Alle Aufgaben, die für die Aufgaben Gruppe geplant werden, werden, wenn möglich, vorübergehend abgebrochen.

```cpp
void cancel();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Abbruch](../cancellation-in-the-ppl.md).

## <a name="is_canceling"></a><a name="is_canceling"></a>is_canceling

Informiert den Aufrufer darüber, ob die Aufgaben Gruppe derzeit in der Mitte eines Abbruchs liegt. Dies weist nicht unbedingt darauf hin, dass die- `cancel` Methode für das-Objekt aufgerufen wurde `task_group` (obwohl diese Methode sicherlich für die Rückgabe qualifiziert ist **`true`** ). Dies kann der Fall sein, wenn das `task_group` Objekt Inline ausgeführt wird und eine Aufgaben Gruppe weiter oben in der Arbeitsstruktur abgebrochen wurde. In Fällen, in denen die Common Language Runtime feststellen kann, dass der Abbruch durch dieses `task_group` Objekt fließt, **`true`** wird ebenfalls zurückgegeben.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Rückgabewert

Ein Hinweis darauf, ob `task_group` sich das Objekt in der Mitte eines Abbruchs befindet (oder in Kürze).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Abbruch](../cancellation-in-the-ppl.md).

## <a name="run"></a><a name="run"></a>Lauf

Plant eine Aufgabe für das- `task_group` Objekt. Wenn ein- `task_handle` Objekt als Parameter an übergeben wird `run` , ist der Aufrufer für die Verwaltung der Lebensdauer des- `task_handle` Objekts verantwortlich. Die Version der-Methode, die einen Verweis auf ein Funktions Objekt als Parameter annimmt, umfasst die Heap Zuordnung innerhalb der Laufzeit, die weniger gut ausgeführt werden kann als die Verwendung der-Version, die einen Verweis auf ein- `task_handle` Objekt annimmt. Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass die Aufgabe an der durch den-Parameter angegebenen Position für die Ausführung verzerrt wird.

```cpp
template<
   typename _Function
>
void run(
   const _Function& _Func
);

template<
   typename _Function
>
void run(
   const _Function& _Func,
   location& _Placement
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle,
   location& _Placement
);
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktions Objekts, das aufgerufen wird, um den Text des Task Handles auszuführen.

*_Func*<br/>
Eine Funktion, die aufgerufen wird, um den Textkörper der Aufgabe aufzurufen. Hierbei kann es sich um einen Lambda-Ausdruck oder ein anderes Objekt handeln, das eine Version des Funktions aufrufoperators mit der Signatur unterstützt `void operator()()` .

*_Placement*<br/>
Ein Verweis auf den Speicherort, an dem die durch den-Parameter dargestellte Aufgabe `_Func` ausgeführt werden soll.

*_Task_handle*<br/>
Ein Handle für die geplante Arbeit. Beachten Sie, dass der Aufrufer für die Lebensdauer dieses Objekts zuständig ist. Die Laufzeit erwartet weiterhin, bis die-Methode oder die- `wait` `run_and_wait` Methode für dieses Objekt aufgerufen wurde `task_group` .

### <a name="remarks"></a>Bemerkungen

Die Laufzeit plant, dass die bereitgestellte Arbeitsfunktion zu einem späteren Zeitpunkt ausgeführt wird. Dies kann nach der Rückgabe der aufrufenden Funktion erfolgen. Diese Methode verwendet ein [task_handle](task-handle-class.md) Objekt, um eine Kopie der bereitgestellten Arbeitsfunktion zu speichern. Daher werden alle Zustandsänderungen, die in einem Funktions Objekt auftreten, das Sie an diese Methode übergeben, nicht in Ihrer Kopie des Funktions Objekts angezeigt. Stellen Sie außerdem sicher, dass die Lebensdauer von Objekten, die Sie als Zeiger oder als Verweis an die Arbeitsfunktion übergeben, gültig bleibt, bis die Arbeitsfunktion zurückgibt.

Wenn `task_group` als Ergebnis der Stapel Entsicherung von einer Ausnahme zerstört wird, müssen Sie nicht sicherstellen, dass ein-oder-Methode aufgerufen wurde `wait` `run_and_wait` . In diesem Fall wird der Dekonstruktor entsprechend abbrechen und darauf warten, dass die vom-Parameter dargestellte Aufgabe `_Task_handle` beendet wird.

Die-Methode löst eine [Invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) Ausnahme aus, wenn das vom-Parameter angegebene Aufgaben Handle `_Task_handle` bereits über die-Methode für ein Aufgaben Gruppen Objekt geplant wurde `run` und kein zwischenzeitlichen Aufrufen der- `wait` oder- `run_and_wait` Methode für diese Aufgaben Gruppe aufgetreten ist.

## <a name="run_and_wait"></a><a name="run_and_wait"></a>run_and_wait

Plant eine Aufgabe, die Inline im aufrufenden Kontext ausgeführt werden soll, und unterstützt das- `task_group` Objekt für die vollständige Abbruch Unterstützung. Die Funktion wartet dann, bis die gesamte Arbeit an dem `task_group` Objekt entweder abgeschlossen oder abgebrochen wurde. Wenn ein- `task_handle` Objekt als Parameter an übergeben wird `run_and_wait` , ist der Aufrufer für die Verwaltung der Lebensdauer des- `task_handle` Objekts verantwortlich.

```cpp
template<
   class _Function
>
task_group_status run_and_wait(
   task_handle<_Function>& _Task_handle
);

template<
   class _Function
>
task_group_status run_and_wait(
   const _Function& _Func
);
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktions Objekts, das aufgerufen wird, um den Hauptteil der Aufgabe auszuführen.

*_Task_handle*<br/>
Ein Handle für die Aufgabe, die Inline im aufrufenden Kontext ausgeführt wird. Beachten Sie, dass der Aufrufer für die Lebensdauer dieses Objekts zuständig ist. Die Laufzeit wird fortgesetzt, bis die `run_and_wait` Ausführung der Methode abgeschlossen ist.

*_Func*<br/>
Eine Funktion, die aufgerufen wird, um den Hauptteil der Arbeit aufzurufen. Hierbei kann es sich um einen Lambda-Ausdruck oder ein anderes Objekt handeln, das eine Version des Funktions aufrufoperators mit der Signatur unterstützt `void operator()()` .

### <a name="return-value"></a>Rückgabewert

Gibt an, ob der Warte Vorgang durch einen expliziten Abbruch Vorgang oder durch Auslösen einer Ausnahme von einer seiner Aufgaben abgebrochen wurde oder ob die Aufgaben Gruppe abgebrochen wurde. Weitere Informationen finden Sie unter [Task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass mindestens eine der Aufgaben, die für dieses Objekt geplant sind, `task_group` Inline im aufrufenden Kontext ausgeführt werden kann.

Wenn eine oder mehrere der Aufgaben, die für dieses `task_group` Objekt geplant sind, eine Ausnahme auslösen, wählt die Common Language Runtime eine solche Ausnahme aus und gibt Sie aus dem Aufrufen der- `run_and_wait` Methode weiter.

Wenn die- `run_and_wait` Methode für ein- `task_group` Objekt zurückgegeben wird, setzt die Laufzeit das Objekt auf einen fehlerfreien Zustand zurück, in dem es wieder verwendet werden kann. Dies gilt auch für den Fall, in dem das `task_group` Objekt abgebrochen wurde.

Im nicht außergewöhnlichen Ausführungs Pfad haben Sie die Möglichkeit, entweder diese Methode oder die-Methode aufzurufen, `wait` bevor der Dekonstruktor von `task_group` ausgeführt wird.

## <a name="task_group"></a><a name="ctor"></a>task_group

Erstellt ein neues `task_group`-Objekt.

```cpp
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>Parameter

*_CancellationToken*<br/>
Ein Abbruch Token, das dieser Aufgaben Gruppe zugeordnet werden soll. Die Aufgaben Gruppe wird abgebrochen, wenn das Token abgebrochen wird.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor, der ein Abbruch Token annimmt, erstellt eine `task_group` , die abgebrochen wird, wenn die dem Token zugeordnete Quelle abgebrochen wird. Das Bereitstellen eines expliziten Abbruch Tokens isoliert diese Aufgaben Gruppe auch von der Teilnahme an einem impliziten Abbruch von einer übergeordneten Gruppe mit einem anderen Token oder ohne Token.

## <a name="task_group"></a><a name="dtor"></a>~ Task_group

Zerstört ein `task_group` -Objekt. Es wird erwartet, dass Sie die- `wait` Methode oder die- `run_and_wait` Methode für das-Objekt vor dem Ausführen des Dekonstruktors aufruft, es sei denn, der Dekonstruktor wird aufgrund einer Ausnahme als Ergebnis der Stapel Auflösung ausgeführt.

```cpp
~task_group();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Dekonstruktor als Ergebnis der normalen Ausführung ausgeführt wird (z. b. aufgrund einer Ausnahme kein Stapel entwickeln) und weder die-noch die- `wait` `run_and_wait` Methode aufgerufen wurde, kann der Dekonstruktor eine [Missing_wait](missing-wait-class.md) Ausnahme auslösen.

## <a name="wait"></a><a name="wait"></a>Warte

Wartet, bis die gesamte Arbeit an dem `task_group` Objekt entweder abgeschlossen oder abgebrochen wurde.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Rückgabewert

Gibt an, ob der Warte Vorgang durch einen expliziten Abbruch Vorgang oder durch Auslösen einer Ausnahme von einer seiner Aufgaben abgebrochen wurde oder ob die Aufgaben Gruppe abgebrochen wurde. Weitere Informationen finden Sie unter [Task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass mindestens eine der Aufgaben, die für dieses Objekt geplant sind, `task_group` Inline im aufrufenden Kontext ausgeführt werden kann.

Wenn eine oder mehrere der Aufgaben, die für dieses `task_group` Objekt geplant sind, eine Ausnahme auslösen, wählt die Common Language Runtime eine solche Ausnahme aus und gibt Sie aus dem Aufrufen der- `wait` Methode weiter.

Durch Aufrufen `wait` von für ein- `task_group` Objekt wird der Zustand wieder hergestellt, in dem er wieder verwendet werden kann. Dies gilt auch für den Fall, in dem das `task_group` Objekt abgebrochen wurde.

Im nicht außergewöhnlichen Ausführungs Pfad haben Sie die Möglichkeit, entweder diese Methode oder die-Methode aufzurufen, `run_and_wait` bevor der Dekonstruktor von `task_group` ausgeführt wird.

## <a name="see-also"></a>Siehe auch

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[structured_task_group-Klasse](structured-task-group-class.md)<br/>
[task_handle-Klasse](task-handle-class.md)
