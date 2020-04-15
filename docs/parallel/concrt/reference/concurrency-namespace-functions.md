---
title: concurrency-Namespace-Funktionen
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
ms.openlocfilehash: 15b265744640628425502706d69fd98a1c64bda2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374374"
---
# <a name="concurrency-namespace-functions"></a>concurrency-Namespace-Funktionen

||||
|-|-|-|
|[Alloc](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|
|[EnableTracing](#enabletracing)|[Kostenlos](#free)|[GetExecutionContextId](#getexecutioncontextid)|
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[Klar](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[Parallel_for](#parallel_for)|[Parallel_for_each](#parallel_for_each)|
|[Parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[Erhalten](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[send](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[Warte](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

## <a name="alloc"></a><a name="alloc"></a>Alloc

Reserviert einen Speicherblock mit der in der Unterbelegungsfunktion für die Zwischenspeicherung der Concurrency Runtime angegebenen Größe.

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Parameter

*_NumBytes*<br/>
Die Anzahl der zuzuweisenden Bytes an Arbeitsspeicher.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf neu zugewiesenen Speicher.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen darüber, welche Szenarien in Ihrer Anwendung von der Verwendung des Caching Suballocator profitieren könnten, finden Sie unter [Taskplaner](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="asend"></a><a name="asend"></a>asend

Ein asynchroner Sendevorgang, der eine Aufgabe zum Weitergeben der Daten an den Zielblock plant.

```cpp
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der zu sendenden Daten.

*_Trg*<br/>
Ein Zeiger oder Verweis auf das Ziel, an das Daten gesendet werden.

*_Data*<br/>
Ein Verweis auf die zu sendenden Daten.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Nachricht akzeptiert wurde, bevor die Methode zurückgegeben wurde, **andernfalls false.**

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).

## <a name="cancel_current_task"></a><a name="cancel_current_task"></a>cancel_current_task

Bricht die gerade ausgeführte Aufgabe ab. Diese Funktion kann aus dem Text einer Aufgabe aufgerufen werden, um die Ausführung der Aufgabe abzubrechen und ihn dabei in den `canceled` Zustand übergehen zu lassen.

Der Aufruf dieser Funktion, wenn Sie sich nicht innerhalb des Texts von einem `task` befinden, ist kein unterstütztes Szenario. Dies würde zu nicht definiertem Verhalten, wie einem Absturz oder einem Hänger in der Anwendung, führen.

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a><a name="clear"></a>Klar

Löscht die gleichzeitige Warteschlange und zerstört alle derzeit in die Warteschlange eingebundenen Elemente. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Parameter

*T*<br/>

*_Ax*<br/>

## <a name="create_async"></a><a name="create_async"></a>create_async

Erstellt ein asynchrones Konstrukt der Windows Runtime auf einem vom Benutzer angegebenes Lambda oder Funktionsobjekt. Der Rückgabetyp von `create_async` ist entweder `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` oder `IAsyncOperationWithProgress<TResult, TProgress>^` auf Grundlage der Signatur des Lambda-Ausdrucks, der an die Methode übergeben wurde.

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Type (Typ).

*_Func*<br/>
Der Lambda-Ausdruck oder das Funktionsobjekt, aus dem ein asynchrones Windows-Runtime-Konstrukt erstellt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein asynchrones Konstrukt, das durch eine IAsyncAction,\<IAsyncActionWithProgress TProgress>, IAsyncOperation\<TResult\<>, oder ein IAsyncOperationWithProgress TResult, TProgress>. Die Schnittstelle, die zurückgegeben wird, hängt von der Signatur des Lambda-Ausdrucks ab, der an die Funktion übergeben wird.

### <a name="remarks"></a>Bemerkungen

Der Rückgabetyp des Lambdaausdrucks bestimmt, ob das Konstrukt eine Aktion oder ein Vorgang ist.

Lambda-Ausdrücke, die "void" zurückgeben, führen zur Erstellung von Aktionen. Lambda-Ausdrücke, die ein Ergebnis vom Typ `TResult` zurückgeben, führen zur Erstellung von TResult-Vorgängen.

Der Lambda-Ausdruck kann auch `task<TResult>` zurückgeben, was die asynchronen Abläufe kapselt, oder die Fortsetzung einer Kette von Aufgaben ist, die die asynchronen Abläufe darstellen. In diesem Fall wird der Lambda-Ausdruck selbst inline ausgeführt, da die Aufgaben asynchron ausgeführt werden, und der Rückgabetyp des Lambda-Ausdrucks wird entpackt, um das von `create_async` zurückgegebene asynchrone Konstrukt zu erstellen. Dies bedeutet, dass ein\<Lambda, der eine Aufgabenlücke> zurückgibt,\<die Erstellung von Aktionen verursacht, und ein Lambda, der eine Aufgabe TResult> zurückgibt, die Erstellung von Vorgängen von TResult verursacht.

Der Lambda-Ausdruck akzeptiert null, ein oder zwei Argumente. Die gültigen Argumente sind `progress_reporter<TProgress>` und `cancellation_token` in dieser Reihenfolge, wenn beide verwendet werden. Ein Lambda-Ausdruck ohne Argumente bewirkt die Erstellung eines asynchronen Konstrukts ohne die Möglichkeit der Statusberichterstellung. Ein Lambda, der\<einen progress_reporter `create_async` TProgress> verwendet, führt dazu, dass ein `report` asynchrones Konstrukt zurückgegeben wird, das den Fortschritt vom Typ TProgress jedes Mal meldet, wenn die Methode des progress_reporter Objekts aufgerufen wird. Ein Lambda-Ausdruck, der ein „cancellation_token“ verwendet, kann dieses Token verwenden, um auf einen Abbruch zu prüfen, oder es an Aufgaben übergeben, die er erstellt, sodass ein Abbruch des asynchronen Konstrukts den Abbruch dieser Aufgaben verursacht.

Wenn der Text des Lambda- oder Funktionsobjekts\<ein Ergebnis zurückgibt (und nicht eine Aufgabe, die TResult>), wird die Lamdba asynchron innerhalb des Prozess-MTA im Kontext einer Aufgabe ausgeführt, die die Runtime implizit für sie erstellt. Die `IAsyncInfo::Cancel`-Methode verursacht den Abbruch der impliziten Aufgabe.

Wenn der Text des Lambda-Ausdrucks eine Aufgabe zurückgibt, wird der Lambda-Ausdruck inline ausgeführt. Durch Deklarieren des Lambda-Ausdrucks zur Verwendung eines Arguments des Typs `cancellation_token` können Sie den Abbruch aller Aufgaben auslösen, die Sie innerhalb des Lambda-Ausdrucks erstellen, indem Sie dieses Token bei ihrer Erstellung übergeben. Sie können auch die `register_callback`-Methode im Token verwenden, um die Laufzeit zu veranlassen, einen Rückruf aufzurufen, wenn Sie `IAsyncInfo::Cancel` für den asynchronen Vorgang oder die verursachte Aktion aufrufen.

Diese Funktion ist nur für Windows-Runtime-Apps verfügbar.

## <a name="createresourcemanager"></a><a name="createresourcemanager"></a>CreateResourceManager

Gibt eine Schnittstelle zurück, die die Singletoninstanz des Ressourcen-Managers der Concurrency Runtime darstellt. Der Ressourcen-Manager ist für das Zuweisen von Ressourcen für Planer, die miteinander kooperieren möchten, zuständig.

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Rückgabewert

Eine `IResourceManager`-Schnittstelle.

### <a name="remarks"></a>Bemerkungen

Mehrere nachfolgende Aufrufe dieser Methode geben die gleiche Instanz des Ressourcen-Managers zurück. Jeder Aufruf der Methode erhöht eine Referenzanzahl für den Ressourcen-Manager und muss mit einem Aufruf der [IResourceManager::Release-Methode](iresourcemanager-structure.md) abgeglichen werden, wenn der Planer mit dem Ressourcen-Manager kommuniziert.

[unsupported_os](unsupported-os-class.md) wird ausgelöst, wenn das Betriebssystem von der Concurrency Runtime nicht unterstützt wird.

## <a name="create_task"></a><a name="create_task"></a>create_task

Erstellt ein [PPL-Taskobjekt.](task-class.md) Das Element `create_task` kann überall dort verwendet werden, wo Sie einen Aufgabenkonstruktor verwendet hätten. Es wird hauptsächlich der Einfachheit halber bereitgestellt, da es beim Erstellen eines Tasks die Verwendung des `auto`-Schlüsselwort ermöglicht.

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Parameters, von dem die Aufgabe erstellt werden soll.

*_ReturnType*<br/>
Type (Typ).

*_Param*<br/>
Der Parameter, von dem der Task erstellt werden soll. Dies kann ein Lambda- `task_completion_event` oder Funktionsobjekt, ein Objekt, ein anderes `task` Objekt oder eine Windows::Foundation::IAsyncInfo-Schnittstelle sein, wenn Sie Aufgaben in Ihrer UWP-App verwenden.

*_TaskOptions*<br/>
Die Aufgabenoptionen.

*_Task*<br/>
Der zu erstellende Task.

### <a name="return-value"></a>Rückgabewert

Eine neue Aufgabe des Typs `T`, der von `_Param` abgeleitet wird.

### <a name="remarks"></a>Bemerkungen

Die erste Überladung verhält sich wie ein Aufgabenkonstruktor, der einen einzelnen Parameter akzeptiert.

Die zweite Überladung weist das Abbruchtoken, das der neu erstellten Aufgabe bereitgestellt wird, zu. Wenn Sie diese Überladung verwenden, ist die Übergabe eines anderen `task`-Objekts als erster Parameter nicht zulässig.

Der Typ des zurückgegebenen Tasks wird vom ersten Parameter zur Funktion abgeleitet. Wenn `_Param` ein `task_completion_event<T>`, ein `task<T>` oder ein Funktionselement ist, das entweder den Typ `T` oder `task<T>` zurückgibt, ist der Typ des erstellten Tasks `task<T>`.

In `_Param` einer UWP-App, wenn es sich um windows::Foundation::IAsyncOperation\<T>oder Windows::Foundation::IAsyncOperationWithProgress\<T,P>oder einen Functor `task<T>`handelt, der einen dieser Typen zurückgibt, ist die erstellte Aufgabe vom Typ . Wenn `_Param` es sich um Windows::Foundation::IAsyncAction oder Windows::Foundation::IAsyncActionWithProgress\<P>oder einen Functor handelt, der `task<void>`einen dieser Typen zurückgibt, hat die erstellte Aufgabe den Typ .

## <a name="disabletracing"></a><a name="disabletracing"></a>DisableTracing

Deaktiviert die Ablaufverfolgung in der Concurrency Runtime. Diese Funktion ist veraltet, da die Registrierung der ETW-Ablaufverfolgung standardmäßig aufgehoben wird.

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Ablaufverfolgung ordnungsgemäß `S_OK` deaktiviert wurde, wird zurückgegeben. Wenn die Ablaufverfolgung zuvor `E_NOT_STARTED` nicht initiiert wurde, wird

## <a name="enabletracing"></a><a name="enabletracing"></a>EnableTracing

Aktiviert die Ablaufverfolgung in der Concurrency Runtime. Diese Funktion ist veraltet, da die Registrierung der ETW-Ablaufverfolgung jetzt standardmäßig erfolgt.

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Ablaufverfolgung korrekt `S_OK` initiiert wurde, wird zurückgegeben. `E_NOT_STARTED` andernfalls zurückgegeben.

## <a name="free"></a><a name="free"></a>kostenlos

Gibt einen Speicherblock frei, der zuvor mit der `Alloc`-Methode der Unterbelegungsfunktion für die Zwischenspeicherung der Concurrency Runtime reserviert wurde.

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Parameter

*_PAllocation*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor mit der `Alloc`-Methode reserviert wurde und jetzt freigegeben werden soll. Wenn der `_PAllocation`-Parameter auf den Wert `NULL` festgelegt wurde, ignoriert diese Methode den Parameter und kehrt sofort zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen darüber, welche Szenarien in Ihrer Anwendung von der Verwendung des Caching Suballocator profitieren könnten, finden Sie unter [Taskplaner](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="get_ambient_scheduler"></a><a name="get_ambient_scheduler"></a>get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Rückgabewert

## <a name="getexecutioncontextid"></a><a name="getexecutioncontextid"></a>GetExecutionContextId

Gibt einen eindeutigen Bezeichner zurück, der einem Ausführungskontext zugewiesen werden kann, der die `IExecutionContext`-Schnittstelle implementiert.

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Bezeichner für einen Ausführungskontext.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um einen Bezeichner für ihren Ausführungskontext abzusuchen, bevor Sie eine `IExecutionContext` Schnittstelle als Parameter an eine der vom Ressourcen-Manager angebotenen Methoden übergeben.

## <a name="getosversion"></a><a name="getosversion"></a>GetOSVersion

Gibt die Betriebssystemversion zurück.

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Rückgabewert

Ein Enumerationswert, der das Betriebssystem darstellt.

### <a name="remarks"></a>Bemerkungen

[unsupported_os](unsupported-os-class.md) wird ausgelöst, wenn das Betriebssystem von der Concurrency Runtime nicht unterstützt wird.

## <a name="getprocessorcount"></a><a name="getprocessorcount"></a>GetProcessorCount

Gibt die Anzahl von Hardwarethreads des zugrunde liegenden Systems zurück.

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Hardwarethreads.

### <a name="remarks"></a>Bemerkungen

[unsupported_os](unsupported-os-class.md) wird ausgelöst, wenn das Betriebssystem von der Concurrency Runtime nicht unterstützt wird.

## <a name="getprocessornodecount"></a><a name="getprocessornodecount"></a>GetProcessorNodeCount

Gibt die Anzahl von NUMA-Knoten oder Prozessorpaketen des zugrunde liegenden Systems zurück.

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von NUMA-Knoten oder Prozessorpaketen.

### <a name="remarks"></a>Bemerkungen

Wenn das System mehr NUMA-Knoten als Prozessorpakete enthält, wird die Anzahl der NUMA-Knoten zurückgegeben. Andernfalls wird die Anzahl der Prozessorpakete zurückgegeben.

[unsupported_os](unsupported-os-class.md) wird ausgelöst, wenn das Betriebssystem von der Concurrency Runtime nicht unterstützt wird.

## <a name="getschedulerid"></a><a name="getschedulerid"></a>GetSchedulerId

Gibt einen eindeutigen Bezeichner zurück, der einem Planer zugewiesen werden kann, der die `IScheduler`-Schnittstelle implementiert.

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Bezeichner für einen Planer.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um einen Bezeichner für ihren Planer abzusuchen, bevor Sie eine `IScheduler` Schnittstelle als Parameter an eine der vom Ressourcen-Manager angebotenen Methoden übergeben.

## <a name="internal_assign_iterators"></a><a name="internal_assign_iterators"></a>internal_assign_iterators

```cpp
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>Parameter

*T*<br/>

*_Ax*<br/>

*_I*<br/>

*first*<br/>

*last*<br/>

## <a name="interruption_point"></a><a name="interruption_point"></a>interruption_point

Erstellt einen Unterbrechungspunkt für den Abbruch. Wenn ein Abbruch im Kontext, in dem diese Funktion aufgerufen wird, ausgeführt wird, löst diese eine interne Ausnahme aus, mit der die Ausführung der aktuell ausgeführten parallelen Verarbeitung abgebrochen wird. Wenn kein Abbruch ausgeführt wird, bleibt die Funktion untätig.

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>Bemerkungen

Sie sollten die interne Abbruchausnahme, `interruption_point()` die von der Funktion ausgelöst wird, nicht abfangen. Die Ausnahme wird von der Laufzeit abgefangen und behandelt, und das Abfangen kann dazu führen, dass sich Ihr Programm ungewöhnlich verhält.

## <a name="is_current_task_group_canceling"></a><a name="is_current_task_group_canceling"></a>is_current_task_group_canceling

Gibt zurück, ob die Aufgabengruppe, die gerade inline auf dem aktuellen Kontext ausgeführt wird, in diesem Moment (oder in Kürze) einen Abbruch durchführt. Beachten Sie, dass `false` zurückgegeben wird, wenn auf dem aktuellen Kontext zurzeit inline keine Aufgabengruppe ausgeführt wird.

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Taskgruppe, die gerade ausgeführt wird, andernfalls **abgebrochen** wird.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Stornierung](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="make_choice"></a><a name="make_choice"></a>make_choice

Erstellt einen `choice`-Meldungsblock aus einem optionalen `Scheduler` oder einer `ScheduleGroup` und mindestens zwei Eingabequellen.

```cpp
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parameter

*T1*<br/>
Der Meldungsblocktyp der ersten Quelle.

*T2*<br/>
Der Meldungsblocktyp der zweiten Quelle.

*_PScheduler*<br/>
Das `Scheduler` -Objekt, in dem die Weiterleitungsaufgabe für den `choice` -Meldungsblock geplant ist.

*_Item1*<br/>
Die erste Quelle.

*_Item2*<br/>
Die zweite Quelle.

*_Items*<br/>
Zusätzliche Quellen.

*_PScheduleGroup*<br/>
Das `ScheduleGroup` -Objekt, in dem die Weiterleitungsaufgabe für den `choice` -Meldungsblock geplant ist. Das verwendete `Scheduler` -Objekt wird von der Planungsgruppe impliziert.

### <a name="return-value"></a>Rückgabewert

Ein `choice`-Nachrichtenblock mit zwei oder mehr Eingabequellen.

## <a name="make_greedy_join"></a><a name="make_greedy_join"></a>make_greedy_join

Erstellt einen `greedy multitype_join`-Meldungsblock aus einem optionalen `Scheduler` oder einer `ScheduleGroup` und mindestens zwei Eingabequellen.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```

### <a name="parameters"></a>Parameter

*T1*<br/>
Der Meldungsblocktyp der ersten Quelle.

*T2*<br/>
Der Meldungsblocktyp der zweiten Quelle.

*_PScheduler*<br/>
Das `Scheduler` -Objekt, in dem die Weiterleitungsaufgabe für den `multitype_join` -Meldungsblock geplant ist.

*_Item1*<br/>
Die erste Quelle.

*_Item2*<br/>
Die zweite Quelle.

*_Items*<br/>
Zusätzliche Quellen.

*_PScheduleGroup*<br/>
Das `ScheduleGroup` -Objekt, in dem die Weiterleitungsaufgabe für den `multitype_join` -Meldungsblock geplant ist. Das verwendete `Scheduler` -Objekt wird von der Planungsgruppe impliziert.

### <a name="return-value"></a>Rückgabewert

Ein `greedy multitype_join`-Nachrichtenblock mit zwei oder mehr Eingabequellen.

## <a name="make_join"></a><a name="make_join"></a>make_join

Erstellt einen `non_greedy multitype_join`-Meldungsblock aus einem optionalen `Scheduler` oder einer `ScheduleGroup` und mindestens zwei Eingabequellen.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>>
    make_join(
Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parameter

*T1*<br/>
Der Meldungsblocktyp der ersten Quelle.

*T2*<br/>
Der Meldungsblocktyp der zweiten Quelle.

*_PScheduler*<br/>
Das `Scheduler` -Objekt, in dem die Weiterleitungsaufgabe für den `multitype_join` -Meldungsblock geplant ist.

*_Item1*<br/>
Die erste Quelle.

*_Item2*<br/>
Die zweite Quelle.

*_Items*<br/>
Zusätzliche Quellen.

*_PScheduleGroup*<br/>
Das `ScheduleGroup` -Objekt, in dem die Weiterleitungsaufgabe für den `multitype_join` -Meldungsblock geplant ist. Das verwendete `Scheduler` -Objekt wird von der Planungsgruppe impliziert.

### <a name="return-value"></a>Rückgabewert

Ein `non_greedy multitype_join`-Nachrichtenblock mit zwei oder mehr Eingabequellen.

## <a name="make_task"></a><a name="make_task"></a>make_task

Eine Factorymethode zum Erstellen eines `task_handle`-Objekts.

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktionsobjekts, das aufgerufen wird, `task_handle` um die vom Objekt dargestellte Arbeit auszuführen.

*_Func*<br/>
Die Funktion, die aufgerufen wird, um `task_handle` die vom Objekt dargestellte Arbeit auszuführen. Dies kann ein Lambda-Functor, ein Zeiger auf eine Funktion oder ein beliebiges `void operator()()`Objekt sein, das eine Version des Funktionsaufrufoperators mit der Signatur unterstützt.

### <a name="return-value"></a>Rückgabewert

Ein `task_handle` -Objekt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nützlich, wenn `task_handle` Sie ein Objekt mit einem Lambda-Ausdruck erstellen müssen, da Sie das Objekt erstellen können, ohne den wahren Typ des Lambda-Functors zu kennen.

## <a name="parallel_buffered_sort"></a><a name="parallel_buffered_sort"></a>parallel_buffered_sort

Ordnet die Elemente in einem angegebenen Bereich in einer nicht absteigenden Reihenfolge oder nach einem Durchordnungskriterium an, das durch ein binäres Prädikat parallel angegeben wird. Diese Funktion entspricht `std::sort` semantisch darin, dass sie eine vergleichsbasierte, instabile, direkte Sortierung ist, abgesehen von den zusätzlich erforderlichen `O(n)`-Leerzeichen und er notwendigen Standardinitialisierung für die sortierten Elemente.

```cpp
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parameter

*_Random_iterator*<br/>
Der Iteratortyp des Eingangsbereichs.

*_Allocator*<br/>
Der Typ eines C++-Standardbibliothekskompatiblen Speicherzuweisungs.

*_Function*<br/>
Der Typ des binären Komparators.

*_Begin*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*_End*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der sortiert werden soll.

*_Alloc*<br/>
Eine Instanz eines C++-Standardbibliothekskompatiblen Speicherzuweisungs.

*_Func*<br/>
Ein benutzerdefiniertes Prädikatfunktionsobjekt, das das Vergleichskriterium definiert, das durch aufeinander folgende Elemente in der Reihenfolge erfüllt werden soll. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück. Diese Vergleichoperatorfunktion muss eine strikte schwache Sortierung auf Elementenpaare der Sequenz anwenden.

*_Chunk_size*<br/>
Die Mimimumgröße eines Chunks, der für die parallele Ausführung in zwei Teile aufgeteilt wird.

### <a name="remarks"></a>Bemerkungen

Alle Überladungen erfordern `n * sizeof(T)` `n` zusätzlichen Speicherplatz, wobei die Anzahl `T` der zu sortierenden Elemente und der Elementtyp ist. In den meisten Fällen zeigt parallel_buffered_sort eine Leistungsverbesserung gegenüber [parallel_sort](concurrency-namespace-functions.md), und Sie sollten sie über parallel_sort verwenden, wenn Sie über den verfügbaren Arbeitsspeicher verfügen.

Wenn Sie keinen binären Komparator `std::less` angeben, wird als Standard verwendet, `operator<()`der den Elementtyp benötigt, um den Operator bereitzustellen.

Wenn Sie keinen Zuweisungstyp oder keine Instanz angeben, wird der Speicherzuweisungsbefehl `std::allocator<T>` für die C++-Standardbibliothek verwendet, um den Puffer zuzuweisen.

Der Algorithmus teilt den Eingabebereich in zwei Blöcke und teilt nacheinander jeden Chunk in zwei Unterblöcke für die parallele Ausführung. Das optionale Argument `_Chunk_size` kann verwendet werden, um dem Algorithmus anzuzeigen, dass er Teile der Größe < `_Chunk_size` seriell verarbeiten soll.

## <a name="parallel_for"></a><a name="parallel_for"></a>Parallel_for

`parallel_for` durchläuft einen Bereich von Indizes und führt bei jeder Iteration parallel eine vom Benutzer bereitgestellte Funktion aus.

```cpp
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```

### <a name="parameters"></a>Parameter

*_Index_type*<br/>
Der Typ des Indexes, der für die Iteration verwendet wird.

*_Function*<br/>
Der Typ der Funktion, die bei jeder Iteration ausgeführt wird.

*_Partitioner*<br/>
Der Typ des Partitionierers, der zum Partitionieren des angegebenen Bereichs verwendet wird.

*first*<br/>
Der erste Index, der in die Iteration aufgenommen wurde.

*last*<br/>
Der Index nach dem letzten Index, der in die Iteration einbezogen werden soll.

*_Step*<br/>
Der Wert, um den schritt `first` werden `last`soll, wenn von nach iterieren deiner . Der Schritt muss positiv sein. [invalid_argument](../../../standard-library/invalid-argument-class.md) wird ausgelöst, wenn der Schritt kleiner als 1 ist.

*_Func*<br/>
Die Funktion, die bei jeder Iteration ausgeführt werden soll. Dabei kann es sich um einen Lambda-Ausdruck, einen Funktionszeiger oder ein beliebiges Objekt erachten, das eine Version des Funktionsaufrufoperators mit der Signatur `void operator()(_Index_type)`unterstützt.

*_Part*<br/>
Ein Verweis auf das Partitionerobjekt. Das Argument kann `const`ein [auto_partitioner](auto-partitioner-class.md)`&` `const` `const`, [static_partitioner](static-partitioner-class.md)`&`, [simple_partitioner](simple-partitioner-class.md) `&` oder [affinity_partitioner](affinity-partitioner-class.md) `&` Wenn ein [affinity_partitioner](affinity-partitioner-class.md) Objekt verwendet wird, muss der Verweis ein Verweis ohne const-l-Wert-Verweis sein, damit der Algorithmus den Status für zukünftige Schleifen speichern kann, die wiederverwendet werden können.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Parallelalgorithmen](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_for_each"></a><a name="parallel_for_each"></a>Parallel_for_each

`parallel_for_each` wendet eine angegebene Funktion parallel auf jedes Element innerhalb eines Bereichs an. Sie entspricht semantisch der `for_each`-Funktion im `std`-Namespace, außer dass die Iteration über die Elemente parallel ausgeführt wird und die Reihenfolge der Iteration nicht angegeben ist. Das Argument `_Func` muss einen Funktionsaufrufoperator in der Form `operator()(T)` unterstützen, wobei der Parameter `T` der Elementtyp des durchlaufenen Containers ist.

```cpp
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```

### <a name="parameters"></a>Parameter

*_Iterator*<br/>
Der Typ des Iterators, der zum Iterieren über den Container verwendet wird.

*_Function*<br/>
Der Typ der Funktion, die auf jedes Element innerhalb des Bereichs angewendet wird.

*_Partitioner*<br/>
*first*<br/>
Ein Iterator, der die Position des ersten Elements adressiert, das in die parallele Iteration einbezogen werden soll.

*last*<br/>
Ein Iterator, der die Position eins hinter dem letzten Element anspricht, das in die parallele Iteration einbezogen werden soll.

*_Func*<br/>
Ein benutzerdefiniertes Funktionsobjekt, das auf jedes Element im Bereich angewendet wird.

*_Part*<br/>
Ein Verweis auf das Partitionerobjekt. Das Argument kann `const`ein [auto_partitioner](auto-partitioner-class.md)`&` `const` `const`, [static_partitioner](static-partitioner-class.md)`&`, [simple_partitioner](simple-partitioner-class.md) `&` oder [affinity_partitioner](affinity-partitioner-class.md) `&` Wenn ein [affinity_partitioner](affinity-partitioner-class.md) Objekt verwendet wird, muss der Verweis ein Verweis ohne const-l-Wert-Verweis sein, damit der Algorithmus den Status für zukünftige Schleifen speichern kann, die wiederverwendet werden können.

### <a name="remarks"></a>Bemerkungen

[auto_partitioner](auto-partitioner-class.md) wird für die Überladung ohne expliziten Partitionierer verwendet.

Für Iteratoren, die keinen zufälligen Zugriff unterstützen, wird nur [auto_partitioner](auto-partitioner-class.md) unterstützt.

Weitere Informationen finden Sie unter [Parallelalgorithmen](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_invoke"></a><a name="parallel_invoke"></a>Parallel_invoke

Führt die als Parameter angegebenen Funktionsobjekte parallel aus, und blockiert, bis die Ausführung beendet ist. Jedes Funktionsobjekt kann ein Lambdaausdruck, ein Zeiger auf eine Funktion oder ein anderes Objekt sein, das den Funktionsaufrufoperator mit der Signatur `void operator()()` unterstützt.

```cpp
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```

### <a name="parameters"></a>Parameter

*_Function1*<br/>
Der Typ des ersten Funktionsobjekts, das parallel ausgeführt werden soll.

*_Function2*<br/>
Der Typ des zweiten Funktionsobjekts, das parallel ausgeführt werden soll.

*_Function3*<br/>
Der Typ des dritten Funktionsobjekts, das parallel ausgeführt werden soll.

*_Function4*<br/>
Der Typ des vierten Funktionsobjekts, das parallel ausgeführt werden soll.

*_Function5*<br/>
Der Typ des fünften Funktionsobjekts, das parallel ausgeführt werden soll.

*_Function6*<br/>
Der Typ des sechsten Funktionsobjekts, das parallel ausgeführt werden soll.

*_Function7*<br/>
Der Typ des siebten Funktionsobjekts, das parallel ausgeführt werden soll.

*_Function8*<br/>
Der Typ des achten Funktionsobjekts, das parallel ausgeführt werden soll.

*_Function9*<br/>
Der Typ des neunten Funktionsobjekts, das parallel ausgeführt werden soll.

*_Function10*<br/>
Der Typ des zehnten Funktionsobjekts, das parallel ausgeführt werden soll.

*_Func1*<br/>
Das erste Funktionsobjekt, das parallel ausgeführt werden soll.

*_Func2*<br/>
Das zweite Funktionsobjekt, das parallel ausgeführt werden soll.

*_Func3*<br/>
Das dritte Funktionsobjekt, das parallel ausgeführt werden soll.

*_Func4*<br/>
Das vierte Funktionsobjekt, das parallel ausgeführt werden soll.

*_Func5*<br/>
Das fünfte Funktionsobjekt, das parallel ausgeführt werden soll.

*_Func6*<br/>
Das sechste Funktionsobjekt, das parallel ausgeführt werden soll.

*_Func7*<br/>
Das siebte Funktionsobjekt, das parallel ausgeführt werden soll.

*_Func8*<br/>
Das achte Funktionsobjekt, das parallel ausgeführt werden soll.

*_Func9*<br/>
Das neunte Funktionsobjekt, das parallel ausgeführt werden soll.

*_Func10*<br/>
Das zehnte Funktionsobjekt, das parallel ausgeführt werden soll.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass eines oder mehrere der als Parameter bereitgestellten Funktionsobjekte inline für den aufrufenden Kontext ausgeführt werden können.

Wenn eines oder mehrere der Funktionsobjekte, die als Parameter an diese Funktion übergeben werden, eine Ausnahme auslösen, wählt `parallel_invoke`die Laufzeit eine solche Ausnahme aus und gibt sie aus dem Aufruf an weiter.

Weitere Informationen finden Sie unter [Parallelalgorithmen](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_radixsort"></a><a name="parallel_radixsort"></a>parallel_radixsort

Ordnet Elemente in einem angegebenen Bereich mithilfe eines Basis-Sortieralgorithmus in einer absteigenden Reihenfolge an. Dies ist eine stabile Sortierfunktion, die eine Projektionsfunktion erfordert, mit der Elemente zur Sortierung in Schlüssel, die ganzen Zahlen ohne Vorzeichen ähneln, projiziert werden können. Standardinitialisierung ist für die zu sortierenden Elemente erforderlich.

```cpp
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```

### <a name="parameters"></a>Parameter

*_Random_iterator*<br/>
Der Iteratortyp des Eingangsbereichs.

*_Allocator*<br/>
Der Typ eines C++-Standardbibliothekskompatiblen Speicherzuweisungs.

*_Function*<br/>
Der Typ der Projektionsfunktion.

*_Begin*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*_End*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der sortiert werden soll.

*_Alloc*<br/>
Eine Instanz eines C++-Standardbibliothekskompatiblen Speicherzuweisungs.

*_Proj_func*<br/>
Ein benutzerdefiniertes Projektionsfunktionsobjekt, das ein Element in einen integralen Wert konvertiert.

*_Chunk_size*<br/>
Die Mimimumgröße eines Chunks, der für die parallele Ausführung in zwei Teile aufgeteilt wird.

### <a name="remarks"></a>Bemerkungen

Alle Überladungen erfordern `n * sizeof(T)` `n` zusätzlichen Speicherplatz, wobei die Anzahl `T` der zu sortierenden Elemente und der Elementtyp ist. Ein unärer Projektionsfunctor mit der Signatur `I _Proj_func(T)` ist erforderlich, `T` um einen `I` Schlüssel zurückzugeben, wenn ein Element angegeben wird, wobei der Elementtyp und ein ganzzahliger Typ ohne Vorzeichen ist.

Wenn Sie keine Projektionsfunktion angeben, wird eine Standardprojektionsfunktion verwendet, die das Element einfach zurückgibt. Die Funktion kann nicht kompiliert werden, wenn das Element kein integraler Typ ist, wenn keine Projektionsfunktion besteht.

Wenn Sie keinen Zuweisungstyp oder keine Instanz angeben, wird der Speicherzuweisungsbefehl `std::allocator<T>` für die C++-Standardbibliothek verwendet, um den Puffer zuzuweisen.

Der Algorithmus teilt den Eingabebereich in zwei Blöcke und teilt nacheinander jeden Chunk in zwei Unterblöcke für die parallele Ausführung. Das optionale Argument `_Chunk_size` kann verwendet werden, um dem Algorithmus anzuzeigen, dass er Teile der Größe < `_Chunk_size` seriell verarbeiten soll.

## <a name="parallel_reduce"></a><a name="parallel_reduce"></a>parallel_reduce

Berechnet die Summe aller Elemente in einem angegebenen Bereich, indem aufeinander folgende Teilsummen berechnet werden, oder berechnet das Ergebnis der aufeinander folgenden Teilergebnisse, die auf ähnliche Weise mithilfe eines angegebenen binären Vorgangs (außer Summe) abgerufen werden parallel. `parallel_reduce` entspricht `std::accumulate` semantisch, außer dass der binäre Vorgang assoziativ sein muss und ein Identitätswert anstelle eines Anfangswerts erforderlich ist.

```cpp
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```

### <a name="parameters"></a>Parameter

*_Forward_iterator*<br/>
Der Iteratortyp des Eingangsbereichs.

*_Sym_reduce_fun*<br/>
Der Typ der symmetrischen Reduktionsfunktion. Dies muss ein Funktionstyp mit Signatur `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`sein, wobei _Reduce_type mit dem Identitätstyp und dem Ergebnistyp der Reduktion identisch ist. Bei der dritten Überladung sollte dies mit `_Range_reduce_fun`dem Ausgabetyp von übereinstimmen.

*_Reduce_type*<br/>
Der Typ, auf den die Eingabe reduziert wird, der sich vom Eingabeelementtyp unterscheiden kann. Der Rückgabewert und der Identitätswert haben diesen Typ.

*_Range_reduce_fun*<br/>
Der Typ der Bereichsreduktionsfunktion. Dies muss ein Funktionstyp mit Signatur `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`sein, _Reduce_type mit dem Identitätstyp und dem Ergebnistyp der Reduktion identisch ist.

*_Begin*<br/>
Ein Eingabe-Iterator, der das erste Zuspiel im zu reduzierenden Bereich adressiert.

*_End*<br/>
Ein Eingabe-Iterator, der das Element adressiert, das eine Position über das endgültige Element im zu reduzierenden Bereich hinaus ist.

*_Identity*<br/>
Der Identitätswert `_Identity` ist vom gleichen Typ wie der `value_type` Ergebnistyp der Reduktion und auch der des Iterators für die erste und zweite Überladung. Für die dritte Überladung muss der Identitätswert denselben Typ wie der Ergebnistyp `value_type` der Reduktion aufweisen, kann sich jedoch vom des Iterators unterscheiden. Er muss einen geeigneten Wert haben, `_Range_fun`sodass sich der Bereichsreduktionsoperator, wenn er auf einen Bereich eines einzelnen Typs `value_type` und des Identitätswerts angewendet wird, wie eine Typumwandlung des Werts vom Typ `value_type` zum Identitätstyp verhält.

*_Sym_fun*<br/>
Die symmetrische Funktion, die in der zweiten der Reduktion verwendet wird. Weitere Informationen finden Sie unter Hinweise.

*_Range_fun*<br/>
Die Funktion, die in der ersten Phase der Reduktion verwendet wird. Weitere Informationen finden Sie unter Hinweise.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Reduzierung.

### <a name="remarks"></a>Bemerkungen

Um eine parallele Reduzierung durchzuführen, teilt die Funktion den Bereich in Blöcke auf der Grundlage der Anzahl der Arbeitskräfte, die dem zugrunde liegenden Planer zur Verfügung stehen. Die Reduktion erfolgt in zwei Phasen, die erste Phase führt eine Reduktion innerhalb jedes Chunks durch, und die zweite Phase führt eine Reduktion zwischen den Teilergebnissen aus jedem Chunk durch.

Die erste Überladung erfordert, dass der `value_type` `T`Iterator , mit dem Identitätswerttyp sowie dem Reduktionsergebnistyp identisch ist. Der Elementtyp T muss `T T::operator + (T)` den Operator bereitstellen, um Elemente in jedem Chunk zu reduzieren. Derselbe Operator wird auch in der zweiten Phase verwendet.

Die zweite Überladung erfordert auch, dass `value_type` der Iterator mit dem Identitätswerttyp sowie dem Reduktionsergebnistyp identisch ist. Der angegebene `_Sym_fun` binäre Operator wird in beiden Reduktionsphasen verwendet, wobei der Identitätswert als Anfangswert für die erste Phase verwendet wird.

Für die dritte Überladung muss der Identitätswerttyp mit dem Reduktionsergebnistyp `value_type` identisch sein, der Iterator kann jedoch von beiden abweichen. Die Bereichsreduktionsfunktion `_Range_fun` wird in der ersten Phase mit dem Identitätswert als Anfangswert verwendet, und die binäre Funktion `_Sym_reduce_fun` wird in der zweiten Phase auf Subergebnisse angewendet.

## <a name="parallel_sort"></a><a name="parallel_sort"></a>parallel_sort

Ordnet die Elemente in einem angegebenen Bereich in einer nicht absteigenden Reihenfolge oder nach einem Durchordnungskriterium an, das durch ein binäres Prädikat parallel angegeben wird. Diese Funktion entspricht `std::sort` semantisch insofern, dass sie eine vergleichsbasierte, instabile, direkte Sortierung ist.

```cpp
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parameter

*_Random_iterator*<br/>
Der Iteratortyp des Eingangsbereichs.

*_Function*<br/>
Der Typ des binären Vergleichsfunctors.

*_Begin*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*_End*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der sortiert werden soll.

*_Func*<br/>
Ein benutzerdefiniertes Prädikatfunktionsobjekt, das das Vergleichskriterium definiert, das durch aufeinander folgende Elemente in der Reihenfolge erfüllt werden soll. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück. Diese Vergleichoperatorfunktion muss eine strikte schwache Sortierung auf Elementenpaare der Sequenz anwenden.

*_Chunk_size*<br/>
Die Mindestgröße eines Blocks, der für die parallele Ausführung in zwei Teile aufgeteilt wird.

### <a name="remarks"></a>Bemerkungen

Die erste Überladung verwendet den `std::less`binären Komparator .

Der zweite überladene verwendet den mitgelieferten `bool _Func(T, T)` binären Komparator, der die Signatur haben sollte, wobei `T` der Typ der Elemente im Eingabebereich ist.

Der Algorithmus teilt den Eingabebereich in zwei Blöcke und teilt nacheinander jeden Chunk in zwei Unterblöcke für die parallele Ausführung. Das optionale Argument `_Chunk_size` kann verwendet werden, um dem Algorithmus anzuzeigen, dass er Teile der Größe < `_Chunk_size` seriell verarbeiten soll.

## <a name="parallel_transform"></a><a name="parallel_transform"></a>parallel_transform

Wendet ein angegebenes Funktionsobjekt auf jedes Element in einem Quellbereich oder auf ein Elementpaar aus zwei Quellbereichen an und kopiert die Rückgabewerte des Funktionsobjekts parallel in einen Zielbereich. Diese Funktion entspricht semantisch `std::transform`.

```cpp
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```

### <a name="parameters"></a>Parameter

*_Input_iterator1*<br/>
Der Typ des ersten oder einzigen Eingabeiterators.

*_Output_iterator*<br/>
Der Typ des Ausgabeiterators.

*_Unary_operator*<br/>
Der Typ des unären Functors, der für jedes Element im Eingabebereich ausgeführt werden soll.

*_Input_iterator2*<br/>
Der Typ des zweiten Eingabeiterators.

*_Binary_operator*<br/>
Der Typ des binären Functors, der paarweise auf Elementen aus den beiden Quellbereichen ausgeführt wird.

*_Partitioner*<br/>
*first1*<br/>
Ein Eingabe-Iterator, der die Position des ersten Elements im ersten oder einzigen zu bedienenden Quellbereich adressiert.

*zuletzt1*<br/>
Ein Eingabe-Iterator, der die Position eins hinter dem letzten Element im ersten oder einzigen zu bedienenden Quellbereich anspricht.

*_Result*<br/>
Ein Ausgabeiterator, der die Position des ersten Elements im Zielbereich adressiert.

*_Unary_op*<br/>
Ein benutzerdefiniertes unäres Funktionsobjekt, das auf jedes Element im Quellbereich angewendet wird.

*_Part*<br/>
Ein Verweis auf das Partitionerobjekt. Das Argument kann `const`ein [auto_partitioner](auto-partitioner-class.md)`&` `const` `const`, [static_partitioner](static-partitioner-class.md)`&`, [simple_partitioner](simple-partitioner-class.md) `&` oder [affinity_partitioner](affinity-partitioner-class.md) `&` Wenn ein [affinity_partitioner](affinity-partitioner-class.md) Objekt verwendet wird, muss der Verweis ein Verweis ohne const-l-Wert-Verweis sein, damit der Algorithmus den Status für zukünftige Schleifen speichern kann, die wiederverwendet werden können.

*first2*<br/>
Ein Eingabeiterator, der die Position des ersten Elements im zweiten Quellbereich adressiert.

*_Binary_op*<br/>
Ein benutzerdefiniertes binäres Funktionsobjekt, das paarweise in einer Vorwärtsreihenfolge auf die beiden Quellbereiche angewendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position direkt hinter dem letzten Element im Zielbereich adressiert, der die vom Funktionsobjekt umgewandelten Ausgabeelemente erhält.

### <a name="remarks"></a>Bemerkungen

[auto_partitioner](auto-partitioner-class.md) werden für die Überladungen ohne explizites Partitionerargument verwendet.

Für Iteratoren, die keinen zufälligen Zugriff unterstützen, wird nur [auto_partitioner](auto-partitioner-class.md) unterstützt.

Die Überladungen, `_Unary_op` die das Argument übernehmen, wandeln den Eingabebereich in den Ausgabebereich um, indem sie den unären Functor auf jedes Element im Eingabebereich anwenden. `_Unary_op`muss den Funktionsaufrufoperator `operator()(T)` mit `T` signatur unterstützen, wobei der Werttyp des zu übertragenden Bereichs liegt.

Die Überladungen, `_Binary_op` die das Argument verwenden, transformieren zwei Eingabebereiche in den Ausgabebereich, indem sie den binären Functor auf ein Element aus dem ersten Eingabebereich und ein Element aus dem zweiten Eingabebereich anwenden. `_Binary_op`muss den Funktionsaufrufoperator `operator()(T, U)` mit `T` `U` der Signatur where unterstützen, wobei Wertetypen der beiden Eingabeiteratoren sind.

Weitere Informationen finden Sie unter [Parallelalgorithmen](../../../parallel/concrt/parallel-algorithms.md).

## <a name="receive"></a><a name="receive"></a>Erhalten

Eine allgemeine Empfangsimplementierung, mit der ein Kontext auf Daten von genau einer Quelle warten und die akzeptierten Werte filtern kann.

```cpp
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Nutzlasttyp.

*_Src*<br/>
Ein Zeiger oder Verweis auf die Quelle, von der Daten erwartet werden.

*_Timeout*<br/>
Die maximale Zeit, für die die Methode für die Daten in Millisekunden verwendet werden soll.

*_Filter_proc*<br/>
Eine Filterfunktion, die bestimmt, ob Nachrichten akzeptiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Wert aus der Quelle des Nutzlasttyps.

### <a name="remarks"></a>Bemerkungen

Wenn der `_Timeout` Parameter einen anderen `COOPERATIVE_TIMEOUT_INFINITE`Wert als die Konstante hat, wird die Ausnahme [operation_timed_out](operation-timed-out-class.md) ausgelöst, wenn die angegebene Zeit vor dem Empfangen einer Nachricht abläuft. Wenn Sie ein Timeout mit einer Länge von Null wünschen, sollten Sie `0` die [try_receive-Funktion](concurrency-namespace-functions.md) verwenden, im Gegensatz zum Aufruf `receive` mit einem Timeout von (Null), da es effizienter ist und keine Ausnahmen bei Timeouts auslöst.

Weitere Informationen finden Sie unter [Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).

## <a name="run_with_cancellation_token"></a><a name="run_with_cancellation_token"></a>run_with_cancellation_token

Führt sofort synchron ein Funktionsobjekt im Kontext eines angegebenen Abbruchtokens aus.

```cpp
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktionsobjekts, das aufgerufen wird.

*_Func*<br/>
Das Funktionsobjekt, das ausgeführt wird. Dieses Objekt muss den Funktionsaufrufoperator mit einer Signatur von void(void) unterstützen.

*_Ct*<br/>
Das Abbruchtoken, das den impliziten Abbruch des Funktionsobjekts steuert. Verwenden `cancellation_token::none()` Sie diese Verwendung, wenn die Funktion ausgeführt werden soll, ohne dass die Möglichkeit besteht, dass ein impliziter Abbruch aus einer übergeordneten Aufgabengruppe abgebrochen wird.

### <a name="remarks"></a>Bemerkungen

Alle Unterbrechungspunkte im Funktionsobjekt werden `cancellation_token` ausgelöst, wenn der abgebrochen wird. Das explizite Token `_Func` isoliert dies vom übergeordneten Abbruch, wenn das übergeordnete Element `_Ct` über ein anderes oder kein Token verfügt.

## <a name="send"></a><a name="send"></a>Senden

Ein synchroner Sendevorgang, der wartet, bis das Ziel die Meldung akzeptiert oder ablehnt.

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Nutzlasttyp.

*_Trg*<br/>
Ein Zeiger oder Verweis auf das Ziel, an das Daten gesendet werden.

*_Data*<br/>
Ein Verweis auf die zu sendenden Daten.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Nachricht akzeptiert wurde, **andernfalls falsch.**

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).

## <a name="set_ambient_scheduler"></a><a name="set_ambient_scheduler"></a>set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Parameter

*_Scheduler*<br/>
Der festzulegende Umgebungsplaner.

## <a name="set_task_execution_resources"></a><a name="set_task_execution_resources"></a>set_task_execution_resources

Schränkt die Ausführungsressourcen, die von den internen Arbeitsthreads der Concurrency Runtime verwendet werden, auf den angegebenen Affinitätssatz ein.

Es ist nur gültig, diese Methode vor Erstellung des Ressourcen-Managers oder zwischen der Lebensdauer zweier Ressourcen-Manager aufzurufen. Sie kann mehrmals aufgerufen werden, solange der Ressourcen-Manager zum Zeitpunkt des Aufrufs nicht vorhanden ist. Nachdem eine Affinitätsgrenze eingerichtet wurde, bleibt diese bis zum nächsten gültigen Aufruf der `set_task_execution_resources`-Methode bestehen.

Die bereitgestellte Affinitätsmaske muss keine Teilmenge der Prozessaffinitätsmaske sein. Die Prozessaffinität wird bei Bedarf aktualisiert.

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Parameter

*_ProcessAffinityMask*<br/>
Die Affinitätsmaske, auf die die Concurrency Runtime-Arbeitsthreads beschränkt werden sollen. Verwenden Sie diese Methode nur auf einem System mit mehr als 64 Hardwarethreads, wenn Sie die Concurrency Runtime auf eine Teilmenge der aktuellen Prozessorgruppe beschränken möchten. Im Allgemeinen sollten Sie die Version der Methode verwenden, die ein Array von Gruppenaffinitäten als Parameter akzeptiert, um die Affinität auf Computern mit mehr als 64 Hardwarethreads einzuschränken.

*count*<br/>
Die Anzahl `GROUP_AFFINITY` der Einträge im Array, die durch den Parameter `_PGroupAffinity`angegeben werden.

*_PGroupAffinity*<br/>
Ein Array `GROUP_AFFINITY` von Einträgen.

### <a name="remarks"></a>Bemerkungen

Die Methode löst eine [invalid_operation](invalid-operation-class.md) Ausnahme aus, wenn ein Ressourcen-Manager zum Zeitpunkt des Aufrufs vorhanden ist, und eine [invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme, wenn die angegebene Affinität zu einem leeren Satz von Ressourcen führt.

Die Version der Methode, die ein Array von Gruppenaffinitäten als Parameter verwendet, sollte nur auf Betriebssystemen mit der Version Windows 7 oder höher verwendet werden. Andernfalls wird eine [invalid_operation](invalid-operation-class.md) Ausnahme ausgelöst.

Das programmgesteuerte Ändern der Prozessaffinität nach dem Aufruf dieser Methode führt nicht dazu, dass der Ressourcen-Manager die Affinität, auf die er beschränkt ist, erneut auswertet. Daher sollten alle Änderungen an der Prozessaffinität vor dem Aufruf dieser Methode vorgenommen werden.

## <a name="swap"></a><a name="swap"></a>Swap

Tauscht die Elemente zweier `concurrent_vector`-Objekte.

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der in den gleichzeitigen Vektoren gespeicherten Elemente.

*_Ax*<br/>
Der Zuweisungstyp der gleichzeitigen Vektoren.

*_A*<br/>
Der gleichzeitige Vektor, dessen Elemente mit denen des `_B`gleichzeitigen Vektors ausgetauscht werden sollen.

*_B*<br/>
Der gleichzeitige Vektor, der die zu tauschenden Elemente bereitstellt, oder der Vektor, `_A`dessen Elemente mit denen des gleichzeitigen Vektors ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion ist ein Algorithmus, `concurrent_vector` der auf `_A`die Containerklasse zum Ausführen der Memberfunktion spezialisiert ist. [concurrent_vector::swap](concurrent-vector-class.md#swap) `_B`( ). Hierbei handelt es sich um Instanzen der partiellen Sortierung von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die spezialisierteste Version der Vorlagenfunktion aus. Die allgemeine Version der `template <class T> void swap(T&, T&)`Vorlagenfunktion , in der Algorithmusklasse funktioniert nach Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse genutzt werden kann.

Diese Methode ist nicht nebenläufigkeitssicher. Sie müssen sicherstellen, dass beim Aufrufen dieser Methode keine anderen Threads Vorgänge für einen der gleichzeitigen Vektoren ausführen.

## <a name="task_from_exception"></a><a name="task_from_exception"></a>task_from_exception

```cpp
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parameter

*_TaskType*<br/>

*_ExType*<br/>

*_exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Rückgabewert

## <a name="task_from_result"></a><a name="task_from_result"></a>task_from_result

```cpp
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parameter

*T*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Rückgabewert

## <a name="trace_agents_register_name"></a><a name="trace_agents_register_name"></a>Trace_agents_register_name

Ordnet den angegebenen Namen dem Nachrichtenblock oder dem Agent in der ETW-Ablaufverfolgung zu.

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Objekts. Dies ist in der Regel ein Nachrichtenblock oder ein Agent.

*_PObject*<br/>
Ein Zeiger auf den Nachrichtenblock oder Agenten, der in der Ablaufverfolgung benannt wird.

*_Name*<br/>
Der Name für das angegebene Objekt.

## <a name="try_receive"></a><a name="try_receive"></a>try_receive

Eine allgemeine try-receive-Implementierung, mit der ein Kontext Daten von genau einer Quelle suchen und die akzeptierten Werte filtern kann. Wenn die Daten nicht bereit sind, gibt die Methode **false**zurück.

```cpp
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Nutzlasttyp

*_Src*<br/>
Ein Zeiger oder Verweis auf die Quelle, von der Daten erwartet werden.

*_value*<br/>
Ein Verweis auf einen Speicherort, an dem das Ergebnis platziert wird.

*_Filter_proc*<br/>
Eine Filterfunktion, die bestimmt, ob Nachrichten akzeptiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein `bool` Wert, der angibt, ob `_value`eine Nutzlast in platziert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).

## <a name="wait"></a><a name="wait"></a>Warte

Hält den aktuellen Kontext für eine bestimmte Zeit an.

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Parameter

*_Milliseconds*<br/>
Die Anzahl der Millisekunden, für die der aktuelle Kontext angehalten werden soll. Wenn `_Milliseconds` der Parameter auf `0`den Wert festgelegt ist, sollte der aktuelle Kontext die Ausführung in andere ausfetzbare Kontexte liefern, bevor der Fortbestand fortgesetzt wird.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode in einem Concurrency Runtime-Schedulerkontext aufgerufen wird, findet der Planer einen anderen Kontext, der für die zugrunde liegende Ressource ausgeführt werden soll. Da der Planer kooperativ ist, kann dieser Kontext nicht genau nach der angegebenen Anzahl von Millisekunden fortgesetzt werden. Wenn der Planer damit beschäftigt ist, andere Aufgaben auszuführen, die dem Planer nicht kooperativ nachgeben, kann die Wartezeit unbegrenzt sein.

## <a name="when_all"></a><a name="when_all"></a>when_all

Erstellt eine Aufgabe, die erfolgreich abgeschlossen wird, wenn alle als Argumente angegeben Aufgaben erfolgreich abgeschlossen werden.

```cpp
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) ->
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```

### <a name="parameters"></a>Parameter

*_Iterator*<br/>
Der Typ des Eingabeiterators.

*_Begin*<br/>
Die Position des ersten Elements in dem Bereich von Elementen, die mit der resultierenden Aufgabe kombiniert werden sollen.

*_End*<br/>
Die Position des ersten Elements hinter dem Bereich von Elementen, die mit der resultierenden Aufgabe kombiniert werden sollen.

*_TaskOptions*<br/>
Das `task_options`-Objekt.

### <a name="return-value"></a>Rückgabewert

Eine Aufgabe, die erfolgreich abgeschlossen wird, wenn alle Eingabeaufgaben erfolgreich abgeschlossen wurden. Wenn die Eingabeaufgaben vom Typ `T` sind, wird die Ausgabe dieser Funktion `task<std::vector<T>>` sein. Wenn die Eingabeaufgaben vom Typ `void` sind, ist die Ausgabeaufgabe auch `task<void>`.

### <a name="remarks"></a>Bemerkungen

`when_all` ist eine nicht blockierende Funktion, die `task` als Ergebnis erzeugt. Im Gegensatz zu [task::wait](task-class.md#wait)ist es sicher, diese Funktion in einer UWP-App im ASTA-Thread (Application STA) aufzurufen.

Wenn eine der Aufgaben abgebrochen wird oder eine Ausnahme auslöst, wird die zurückgegebene Aufgabe vorzeitig im abgebrochenen Zustand abgeschlossen, `task::wait` und die Ausnahme, falls eine ausgeführt wird, wird ausgelöst, wenn Sie [task::get](task-class.md#get) oder bei dieser Aufgabe aufrufen.

Weitere Informationen finden Sie unter [Vorgangsparallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="when_any"></a><a name="when_any"></a>when_any

Erstellt eine Aufgabe, die erfolgreich abgeschlossen wird, wenn eine der als Argumente angegeben Aufgaben erfolgreich abgeschlossen wird.

```cpp
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options())
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken)
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```

### <a name="parameters"></a>Parameter

*_Iterator*<br/>
Der Typ des Eingabeiterators.

*_Begin*<br/>
Die Position des ersten Elements in dem Bereich von Elementen, die mit der resultierenden Aufgabe kombiniert werden sollen.

*_End*<br/>
Die Position des ersten Elements hinter dem Bereich von Elementen, die mit der resultierenden Aufgabe kombiniert werden sollen.

*_TaskOptions*<br/>
*_CancellationToken*<br/>
Das Abbruchtoken, das den Abbruch der zurückgegebenen Aufgabe steuert. Wenn Sie kein Abbruchtoken bereitstellen, erhält die resultierende Aufgabe das Abbruchtoken der Aufgabe, die ihren Abschluss verursacht.

### <a name="return-value"></a>Rückgabewert

Eine Aufgabe, die erfolgreich abgeschlossen ist, wenn eine der Eingabeaufgaben erfolgreich abgeschlossen wurde. Wenn die Eingabeaufgaben vom Typ `T` sind, ist die Ausgabe dieser Funktion `task<std::pair<T, size_t>>>`, wobei das erste Element des Paares das Ergebnis der letzten Aufgabe ist, und das zweite Element der Index der beendeten Aufgabe. Wenn die Eingabeaufgaben vom Typ `void` sind, ist die Ausgabe `task<size_t>`, wobei das Ergebnis der Index der abgeschlossenen Aufgabe ist.

### <a name="remarks"></a>Bemerkungen

`when_any` ist eine nicht blockierende Funktion, die `task` als Ergebnis erzeugt. Im Gegensatz zu [task::wait](task-class.md#wait)ist es sicher, diese Funktion in einer UWP-App im ASTA-Thread (Application STA) aufzurufen.

Weitere Informationen finden Sie unter [Vorgangsparallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
