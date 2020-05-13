---
title: task-Klasse (Concurrency Runtime)
ms.date: 07/30/2019
f1_keywords:
- task
- PPLTASKS/concurrency::task
- PPLTASKS/concurrency::task::task
- PPLTASKS/concurrency::task::get
- PPLTASKS/concurrency::task::is_apartment_aware
- PPLTASKS/concurrency::task::is_done
- PPLTASKS/concurrency::task::scheduler
- PPLTASKS/concurrency::task::then
- PPLTASKS/concurrency::task::wait
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
ms.openlocfilehash: d42c7fbd3e065fc295027b7c56e207b2a49221bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358732"
---
# <a name="task-class-concurrency-runtime"></a>task-Klasse (Concurrency Runtime)

Die Parallel Patterns Library (PPL) `task`-Klasse. Ein `task` Objekt stellt Arbeit dar, die asynchron und gleichzeitig mit anderen Aufgaben und parallelen Arbeiten ausgeführt werden kann, die von parallelen Algorithmen in der Concurrency Runtime erzeugt werden. Es enthält bei erfolgreichem Abschluss ein Ergebnis vom Typ `_ResultType`. Tasks des Typs `task<void>` führen zu keinem Ergebnis. Eine Aufgabe kann erwartet und unabhängig von anderen Aufgaben abgebrochen werden. Es kann auch mit anderen Aufgaben `then`mit Fortsetzungen `when_all`( ) `when_any`und Join( ) und Choice( ) Mustern zusammengesetzt werden. Wenn ein Taskobjekt einer neuen Variablen zugewiesen wird, ist das Verhalten das von `std::shared_ptr`; Mit anderen Worten, beide Objekte stellen dieselbe zugrunde liegende Aufgabe dar.

## <a name="syntax"></a>Syntax

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>Parameter

*_ResultType*<br/>
Der Typ des Ergebnisses, das die Aufgabe erzeugt.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`result_type`|Der Typ des von einem Objekt dieser Klasse erstellten Ergebnisses.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Aufgabe](#ctor)|Ist überladen. Erstellt ein `task`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[get](#get)|Ist überladen. Gibt das von diesem Task erstellte Ergebnis zurück. Wenn sich die Aufgabe nicht in einem abschließenden Zustand befindet, wird mit dem `get`-Aufruf gewartet, bis die Aufgabe fertig gestellt wurde. Diese Methode gibt bei dem Aufruf einer Aufgabe mit einem `result_type` von `void` keinen Wert zurück.|
|[is_apartment_aware](#is_apartment_aware)|Bestimmt, ob der Task eine `IAsyncInfo`-Schnittstelle der Windows Runtime entpackt oder von einem solchen Task abgeleitet wurde.|
|[is_done](#is_done)|Bestimmt, ob die Aufgabe abgeschlossen wurde.|
|[Scheduler](#scheduler)|Gibt den Planer für diesen Task zurück.|
|[Dann](#then)|Ist überladen. Fügt diesem Task einen Fortsetzungstask hinzu.|
|[Warte](#wait)|Erwartet, dass dieser Task einen Terminalzustand erreicht. Es ist möglich, dass das `wait`-Element den Task inline ausführt, wenn alle Taskabhängigkeiten erfüllt sind und er nicht bereits zur Ausführung durch einen Hintergrundworker aufgehoben wurde.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator!=](#operator_neq)|Ist überladen. Bestimmt, ob zwei `task`-Objekte unterschiedliche interne Aufgaben darstellen.|
|[Operator=](#operator_eq)|Ist überladen. Ersetzt den Inhalt eines `task`-Objekts durch einen anderen.|
|[Betreiber== Einzelnachweise ==](#operator_eq_eq)|Ist überladen. Bestimmt, ob zwei `task`-Objekte die gleiche interne Aufgabe darstellen.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Vorgangsparallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`task`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** ppltasks.h

**Namespace:** Parallelität

## <a name="get"></a><a name="get"></a>Erhalten

Gibt das von diesem Task erstellte Ergebnis zurück. Wenn sich die Aufgabe nicht in einem abschließenden Zustand befindet, wird mit dem `get`-Aufruf gewartet, bis die Aufgabe fertig gestellt wurde. Diese Methode gibt bei dem Aufruf einer Aufgabe mit einem `result_type` von `void` keinen Wert zurück.

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Aufgabe.

### <a name="remarks"></a>Bemerkungen

Wenn die Aufgabe abgebrochen wird, `get` löst ein Aufruf an eine [task_canceled](task-canceled-class.md) Ausnahme aus. Wenn die Aufgabe eine Ausnahme während der Ausführung feststellt oder an sie eine Ausnahme aus einer vorherigen Aufgabe weitergegeben wurde, löst ein Aufruf von `get` diese Ausnahme aus.

> [!IMPORTANT]
> Rufen Sie in einer UWP-App (Universelle Windows-Plattform) [concurrency::task::wait](#wait) oder `get` ( `wait` calls `get`) nicht in Code auf, der im Benutzeroberflächenthread ausgeführt wird. Andernfalls löst die Laufzeit [concurrency::invalid_operation](invalid-operation-class.md) aus, da diese Methoden den aktuellen Thread blockieren und dazu führen können, dass die App nicht mehr reagiert. Sie können jedoch die `get`-Methode aufrufen, um das Ergebnis der vorangegangenen Aufgabe in einer aufgabenbasierten Fortsetzung zu erhalten, da das Ergebnis sofort verfügbar ist.

## <a name="is_apartment_aware"></a><a name="is_apartment_aware"></a>is_apartment_aware

Bestimmt, ob der Task eine `IAsyncInfo`-Schnittstelle der Windows Runtime entpackt oder von einem solchen Task abgeleitet wurde.

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Aufgabe `IAsyncInfo` eine Schnittstelle auspackt oder von einer solchen Aufgabe abstammt, **andernfalls false.**

## <a name="taskis_done-method-concurrency-runtime"></a><a name="is_done"></a>Task::is_done-Methode (Concurrency Runtime)

Bestimmt, ob die Aufgabe abgeschlossen wurde.

```cpp
bool is_done() const;
```

### <a name="return-value"></a>Rückgabewert

"True", wenn die Aufgabe abgeschlossen wurde, andernfalls "false".

### <a name="remarks"></a>Bemerkungen

Die Funktion gibt "true" zurück, wenn die Aufgabe abgeschlossen oder abgebrochen wurde (mit oder ohne Benutzerausnahme).

## <a name="operator"></a><a name="operator_neq"></a>Operator!=

Bestimmt, ob zwei `task`-Objekte unterschiedliche interne Aufgaben darstellen.

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die zu vergleichende Aufgabe.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Objekte auf verschiedene zugrunde liegende Aufgaben verweisen, und andernfalls **false.**

## <a name="operator"></a><a name="operator_eq"></a>Operator=

Ersetzt den Inhalt eines `task`-Objekts durch einen anderen.

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das `task`-Quellobjekt.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Da sich `task` wie ein intelligenter Zeiger verhält, stellt dieses `task`-Objekt nach einer Kopierzuweisung die gleiche Aufgabe dar wie `_Other`.

## <a name="operator"></a><a name="operator_eq_eq"></a>Betreiber== Einzelnachweise ==

Bestimmt, ob zwei `task`-Objekte die gleiche interne Aufgabe darstellen.

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die zu vergleichende Aufgabe.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Objekte auf dieselbe zugrunde liegende Aufgabe verweisen, und andernfalls **false.**

## <a name="taskscheduler-method-concurrency-runtime"></a><a name="scheduler"></a>task::scheduler-Methode (Concurrency Runtime)

Gibt den Planer für diesen Task zurück.

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Planer.

## <a name="task"></a><a name="ctor"></a>-Aufgabe

Erstellt ein `task`-Objekt.

```cpp
task();

template<typename T>
__declspec(
    noinline) explicit task(T _Param);

template<typename T>
__declspec(
    noinline) explicit task(T _Param, const task_options& _TaskOptions);

task(
    const task& _Other);

task(
    task&& _Other);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Parameters, von dem die Aufgabe erstellt werden soll.

*_Param*<br/>
Der Parameter, von dem der Task erstellt werden soll. Dies kann ein Lambda, ein `task_completion_event<result_type>` Funktionsobjekt, ein Objekt oder ein Windows::Foundation::IAsyncInfo sein, wenn Sie Aufgaben in Ihrer Windows-Runtime-App verwenden. Das Lambda- oder Funktionsobjekt sollte `std::function<X(void)>`ein Typ sein, der `result_type` `task<result_type>`einem entspricht, wobei X eine Variable vom Typ , oder eine Windows::Foundation::IAsyncInfo in Windows-Runtime-Apps sein kann.

*_TaskOptions*<br/>
Die Aufgabenoptionen enthalten Abbruchtoken, Planer usw.

*_Other*<br/>
Das `task`-Quellobjekt.

### <a name="remarks"></a>Bemerkungen

Der Standardkonstruktor für `task` ist nur vorhanden, damit Aufgaben in Containern verwendet werden können. Eine erstellte Standardaufgabe kann nicht verwendet werden, bis Sie ihr eine gültige Aufgabe zuweisen. Methoden wie `get` `wait` , `then` oder löst eine [invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn sie für eine standardmäßig konstruierte Aufgabe aufgerufen wird.

Eine Aufgabe, die aus einem `task_completion_event` erstellt wird, wird abgeschlossen (und danach werden ihre Fortsetzungen geplant), wenn das Aufgabenabschlussereignis festgelegt ist.

Die Version des Konstruktors, die ein Abbruchtoken verwendet, erstellt eine Aufgabe, die mithilfe der `cancellation_token_source`, aus der das Token abgerufen wurde, abgebrochen werden kann. Die Aufgaben, die ohne ein Abbruchtoken erstellt werden, können nicht abgebrochen werden.

Die Aufgaben, die aus einer `Windows::Foundation::IAsyncInfo`-Schnittstelle oder einem Lambda-Ausdruck erstellt werden, der eine `IAsyncInfo`-Schnittstelle zurückgibt, erreichen den abgeschlossenen Zustand, wenn der enthaltene asynchrone Windows-Runtime-Vorgang oder die enthaltene Aktion abgeschlossen wurde. Ebenso werden Aufgaben, die aus `task<result_type>` einem Lambda erstellt werden, der einen Terminalzustand zurückgibt, wenn die innere Aufgabe ihren Terminalstatus erreicht, und nicht, wenn der Lambda zurückkehrt.

`task` verhält sich wie ein intelligenter Zeiger und kann mehrmals als Wert übergeben werden. Ein Zugriff ist durch mehrere Threads ohne Sperren möglich.

Die Konstruktorüberladungen, die eine Windows::Foundation::IAsyncInfo-Schnittstelle oder einen Lambda verwenden, der eine solche Schnittstelle zurückgibt, sind nur für Windows-Runtime-Apps verfügbar.

Weitere Informationen finden Sie unter [Vorgangsparallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="then"></a><a name="then"></a>Dann

Fügt diesem Task einen Fortsetzungstask hinzu.

```cpp
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions = task_options()) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktionsobjekts, das von dieser Aufgabe aufgerufen wird.

*_Func*<br/>
Die Fortsetzungsfunktion, die ausgeführt werden soll, wenn diese Aufgabe abgeschlossen ist. Diese Fortsetzungsfunktion muss als Eingabe die Variable `result_type` oder `task<result_type>` verwenden, wobei `result_type` der Ergebnistyp ist, den diese Aufgabe erzeugt.

*_TaskOptions*<br/>
Die Aufgabenoptionen umfassen das Abbruchtoken, den Planer und den Fortsetzungskontext. Standardmäßig werden die vorherigen drei Optionen von der Vorgängeraufgabe geerbt.

*_CancellationToken*<br/>
Das Abbruchtoken, das der Fortsetzungsaufgabe zugeordnet werden soll. Eine Fortsetzungsaufgabe, die ohne ein Abbruchtoken erstellt wird, erbt das Token von der Vorgängeraufgabe.

*_ContinuationContext*<br/>
Eine Variable, die angibt, wo die Fortsetzung ausgeführt werden soll. Diese Variable ist nur nützlich, wenn sie in einer UWP-App verwendet wird. Weitere Informationen finden Sie [unter task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>Rückgabewert

Die neu erstellte Fortsetzungsaufgabe. Der Ergebnistyp der zurückgegebenen Aufgabe wird von dem bestimmt, was `_Func` zurückgibt.

### <a name="remarks"></a>Bemerkungen

Die Überladungen, `then` die einen Lambda oder Functor verwenden, der eine Windows::Foundation::IAsyncInfo-Schnittstelle zurückgibt, sind nur für Windows-Runtime-Apps verfügbar.

Weitere Informationen zur Verwendung von Aufgabenfortsetzungen zum Komponieren asynchroner Arbeit finden Sie unter [Vorgangsparallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="wait"></a><a name="wait"></a>Warte

Erwartet, dass dieser Task einen Terminalzustand erreicht. Es ist möglich, dass das `wait`-Element den Task inline ausführt, wenn alle Taskabhängigkeiten erfüllt sind und er nicht bereits zur Ausführung durch einen Hintergrundworker aufgehoben wurde.

```cpp
task_status wait() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `task_status`-Wert, der entweder `completed` oder `canceled` ist. Wenn die Aufgabe eine Ausnahme während der Ausführung feststellt oder an sie eine Ausnahme aus einer vorherigen Aufgabe weitergegeben wurde, löst `wait` diese Ausnahme aus.

### <a name="remarks"></a>Bemerkungen

> [!IMPORTANT]
> Rufen Sie in einer UWP-App (Universelle Windows-Plattform) keinen Code auf, `wait` der auf dem Benutzeroberflächenthread ausgeführt wird. Andernfalls löst die Laufzeit [concurrency::invalid_operation](invalid-operation-class.md) aus, da diese Methode den aktuellen Thread blockiert und die App dadurch möglicherweise nicht mehr reagiert. Sie können jedoch die [concurrency::task::get](#get) -Methode aufrufen, um das Ergebnis der Vorgängeraufgabe in einer aufgabenbasierten Fortsetzung zu erhalten.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
