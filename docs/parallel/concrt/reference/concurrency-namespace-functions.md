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
ms.openlocfilehash: 25cd74e20102bbc1a75e4b4efe1bf234845f7fcb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840179"
---
# <a name="concurrency-namespace-functions"></a>concurrency-Namespace-Funktionen

:::row:::
   :::column span="":::
      [`Alloc`](#alloc)\
      [`asend`](#asend)\
      [`cancel_current_task`](#cancel_current_task)\
      [`clear`](#clear)\
      [`create_async`](#create_async)\
      [`create_task`](#create_task)\
      [`CreateResourceManager`](#createresourcemanager)\
      [`DisableTracing`](#disabletracing)\
      [`EnableTracing`](#enabletracing)\
      [`Free`](#free)\
      [`get_ambient_scheduler`](#get_ambient_scheduler)\
      [`GetExecutionContextId`](#getexecutioncontextid)\
      [`GetOSVersion`](#getosversion)\
      [`GetProcessorCount`](#getprocessorcount)\
      [`GetProcessorNodeCount`](#getprocessornodecount)
   :::column-end:::
   :::column span="":::
      [`GetSchedulerId`](#getschedulerid)\
      [`internal_assign_iterators`](#internal_assign_iterators)\
      [`interruption_point`](#interruption_point)\
      [`is_current_task_group_canceling`](#is_current_task_group_canceling)\
      [`make_choice`](#make_choice)\
      [`make_greedy_join`](#make_greedy_join)\
      [`make_join`](#make_join)\
      [`make_task`](#make_task)\
      [`parallel_buffered_sort`](#parallel_buffered_sort)\
      [`parallel_for_each`](#parallel_for_each)\
      [`parallel_for`](#parallel_for)\
      [`parallel_invoke`](#parallel_invoke)\
      [`parallel_radixsort`](#parallel_radixsort)\
      [`parallel_reduce`](#parallel_reduce)\
      [`parallel_sort`](#parallel_sort)
   :::column-end:::
   :::column span="":::
      [`parallel_transform`](#parallel_transform)\
      [`receive`](#receive)\
      [`run_with_cancellation_token`](#run_with_cancellation_token)\
      [`send`](#send)\
      [`set_ambient_scheduler`](#set_ambient_scheduler)\
      [`set_task_execution_resources`](#set_task_execution_resources)\
      [`swap`](#swap)\
      [`task_from_exception`](#task_from_exception)\
      [`task_from_result`](#task_from_result)\
      [`Trace_agents_register_name`](#trace_agents_register_name)\
      [`try_receive`](#try_receive)\
      [`wait`](#wait)\
      [`when_all`](#when_all)\
      [`when_any`](#when_any)
   :::column-end:::
:::row-end:::

## <a name="alloc"></a><a name="alloc"></a> Zuordnungseinheits

Reserviert einen Speicherblock mit der in der Unterbelegungsfunktion für die Zwischenspeicherung der Concurrency Runtime angegebenen Größe.

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Parameter

*_NumBytes*<br/>
Die Anzahl der zuzuordnenden Arbeitsspeicher bytes.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den neu belegten Arbeitsspeicher.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen darüber, welche Szenarien in Ihrer Anwendung von der Verwendung der cachesubzuweisung profitieren können, finden Sie unter [Taskplaner](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="asend"></a><a name="asend"></a> ASend

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

**`true`** , wenn die Nachricht vor der Rückgabe der Methode akzeptiert wurde, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Nachrichten Übergabe Funktionen](../../../parallel/concrt/message-passing-functions.md).

## <a name="cancel_current_task"></a><a name="cancel_current_task"></a> cancel_current_task

Bricht die gerade ausgeführte Aufgabe ab. Diese Funktion kann aus dem Text einer Aufgabe aufgerufen werden, um die Ausführung der Aufgabe abzubrechen und ihn dabei in den `canceled` Zustand übergehen zu lassen.

Der Aufruf dieser Funktion, wenn Sie sich nicht innerhalb des Texts von einem `task` befinden, ist kein unterstütztes Szenario. Dies führt zu undefiniertem Verhalten, wie z. b. einem Absturz oder einer nicht Reaktionsfähigkeit in Ihrer Anwendung.

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a><a name="clear"></a> Klartext

Löscht die gleichzeitige Warteschlange und zerstört alle Elemente, die in die Warteschlange eingereiht sind Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Parameter

*T*<br/>

*_Ax*<br/>

## <a name="create_async"></a><a name="create_async"></a> create_async

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

Ein asynchrones Konstrukt, dargestellt durch iasyncaction ^, iasyncactionwithprogress \<TProgress> ^, iasyncoperation \<TResult> ^ oder iasyncoperationwithprogress \<TResult, TProgress> ^. Die Schnittstelle, die zurückgegeben wird, hängt von der Signatur des Lambda-Ausdrucks ab, der an die Funktion übergeben wird.

### <a name="remarks"></a>Bemerkungen

Der Rückgabetyp des Lambdaausdrucks bestimmt, ob das Konstrukt eine Aktion oder ein Vorgang ist.

Lambda-Ausdrücke, die "void" zurückgeben, führen zur Erstellung von Aktionen. Lambda-Ausdrücke, die ein Ergebnis vom Typ `TResult` zurückgeben, führen zur Erstellung von TResult-Vorgängen.

Der Lambda-Ausdruck kann auch `task<TResult>` zurückgeben, was die asynchronen Abläufe kapselt, oder die Fortsetzung einer Kette von Aufgaben ist, die die asynchronen Abläufe darstellen. In diesem Fall wird der Lambda-Ausdruck selbst inline ausgeführt, da die Aufgaben asynchron ausgeführt werden, und der Rückgabetyp des Lambda-Ausdrucks wird entpackt, um das von `create_async` zurückgegebene asynchrone Konstrukt zu erstellen. Dies impliziert, dass ein Lambda-Ausdruck, der eine Aufgabe zurückgibt \<void> , die Erstellung von Aktionen verursacht, und ein Lambda-Ausdruck, der eine Aufgabe zurückgibt, bewirkt, dass \<TResult> TResult-Vorgänge erstellt werden.

Der Lambda-Ausdruck akzeptiert null, ein oder zwei Argumente. Die gültigen Argumente sind `progress_reporter<TProgress>` und `cancellation_token` in dieser Reihenfolge, wenn beide verwendet werden. Ein Lambda-Ausdruck ohne Argumente bewirkt die Erstellung eines asynchronen Konstrukts ohne die Möglichkeit der Statusberichterstellung. Ein Lambda, das eine progress_reporter annimmt, \<TProgress> bewirkt `create_async` , dass ein asynchrones Konstrukt zurückgibt, das jedes Mal, wenn die- `report` Methode des progress_reporter Objekts aufgerufen wird, den Status des Typs tprogress meldet. Ein Lambda-Ausdruck, der ein „cancellation_token“ verwendet, kann dieses Token verwenden, um auf einen Abbruch zu prüfen, oder es an Aufgaben übergeben, die er erstellt, sodass ein Abbruch des asynchronen Konstrukts den Abbruch dieser Aufgaben verursacht.

Wenn der Text des Lambda-oder Funktions Objekts ein Ergebnis (und nicht eine Aufgabe) zurückgibt \<TResult> , wird der Lambda asynchron im Prozess-MTA im Kontext einer Aufgabe ausgeführt, die die Laufzeit implizit dafür erstellt. Die `IAsyncInfo::Cancel`-Methode verursacht den Abbruch der impliziten Aufgabe.

Wenn der Text des Lambda-Ausdrucks eine Aufgabe zurückgibt, wird der Lambda-Ausdruck inline ausgeführt. Durch Deklarieren des Lambda-Ausdrucks zur Verwendung eines Arguments des Typs `cancellation_token` können Sie den Abbruch aller Aufgaben auslösen, die Sie innerhalb des Lambda-Ausdrucks erstellen, indem Sie dieses Token bei ihrer Erstellung übergeben. Sie können auch die `register_callback`-Methode im Token verwenden, um die Laufzeit zu veranlassen, einen Rückruf aufzurufen, wenn Sie `IAsyncInfo::Cancel` für den asynchronen Vorgang oder die verursachte Aktion aufrufen.

Diese Funktion ist nur für Windows-Runtime-apps verfügbar.

## <a name="createresourcemanager"></a><a name="createresourcemanager"></a> CreateResourceManager

Gibt eine Schnittstelle zurück, die die Singletoninstanz des Ressourcen-Managers der Concurrency Runtime darstellt. Der Ressourcen-Manager ist für das Zuweisen von Ressourcen für Planer, die miteinander kooperieren möchten, zuständig.

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Rückgabewert

Eine `IResourceManager`-Schnittstelle.

### <a name="remarks"></a>Bemerkungen

Mehrere nachfolgende Aufrufe dieser Methode geben die gleiche Instanz des Ressourcen-Managers zurück. Jeder aufrufsvorgang erhöht den Verweis Zähler für den Ressourcen-Manager und muss mit einem Rückruf der Methode " [IResourceManager:: Release](iresourcemanager-structure.md) " abgeglichen werden, wenn der Planer die Kommunikation mit dem Ressourcen-Manager abgeschlossen hat.

[Unsupported_os](unsupported-os-class.md) wird ausgelöst, wenn das Betriebssystem vom Concurrency Runtime nicht unterstützt wird.

## <a name="create_task"></a><a name="create_task"></a> create_task

Erstellt ein ppl- [Aufgaben](task-class.md) Objekt. Das Element `create_task` kann überall dort verwendet werden, wo Sie einen Aufgabenkonstruktor verwendet hätten. Es wird hauptsächlich aus Gründen der praktische bereitgestellt, da es die Verwendung des- **`auto`** Schlüssel Worts beim Erstellen von Aufgaben ermöglicht.

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
Der Parameter, von dem der Task erstellt werden soll. Dies kann ein Lambda-oder Funktions Objekt, ein- `task_completion_event` Objekt, ein anderes- `task` Objekt oder eine Windows:: Foundation:: iasyncinfo-Schnittstelle sein, wenn Sie Aufgaben in der UWP-App verwenden.

*_TaskOptions*<br/>
Die Aufgaben Optionen.

*_Task*<br/>
Der zu erstellende Task.

### <a name="return-value"></a>Rückgabewert

Eine neue Aufgabe des Typs `T`, der von `_Param` abgeleitet wird.

### <a name="remarks"></a>Bemerkungen

Die erste Überladung verhält sich wie ein Aufgabenkonstruktor, der einen einzelnen Parameter akzeptiert.

Die zweite Überladung weist das Abbruchtoken, das der neu erstellten Aufgabe bereitgestellt wird, zu. Wenn Sie diese Überladung verwenden, ist die Übergabe eines anderen `task`-Objekts als erster Parameter nicht zulässig.

Der Typ des zurückgegebenen Tasks wird vom ersten Parameter zur Funktion abgeleitet. Wenn `_Param` ein `task_completion_event<T>`, ein `task<T>` oder ein Funktionselement ist, das entweder den Typ `T` oder `task<T>` zurückgibt, ist der Typ des erstellten Tasks `task<T>`.

Wenn in einer UWP-APP `_Param` vom Typ Windows:: Foundation:: iasyncoperation \<T> ^ oder Windows:: Foundation:: iasyncoperationwithprogress ^ oder ein Funktionselement ist, \<T,P> das einen dieser Typen zurückgibt, ist die erstellte Aufgabe vom Typ `task<T>` . Wenn `_Param` vom Typ Windows:: Foundation:: iasyncaction ^ oder Windows:: Foundation:: iasyncactionwithprogress \<P> ^ ist, oder ein Funktionselement, das einen dieser Typen zurückgibt, hat die erstellte Aufgabe den Typ `task<void>` .

## <a name="disabletracing"></a><a name="disabletracing"></a> DisableTracing

Deaktiviert die Ablaufverfolgung in der Concurrency Runtime. Diese Funktion ist veraltet, da die Registrierung der ETW-Ablaufverfolgung standardmäßig aufgehoben wird.

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Ablauf Verfolgung ordnungsgemäß deaktiviert wurde, `S_OK` wird zurückgegeben. Wenn die Ablauf Verfolgung zuvor nicht initiiert wurde, `E_NOT_STARTED` wird zurückgegeben.

## <a name="enabletracing"></a><a name="enabletracing"></a> EnableTracing

Aktiviert die Ablaufverfolgung in der Concurrency Runtime. Diese Funktion ist veraltet, da die Registrierung der ETW-Ablaufverfolgung jetzt standardmäßig erfolgt.

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Ablauf Verfolgung ordnungsgemäß initiiert wurde, `S_OK` wird zurückgegeben; andernfalls `E_NOT_STARTED` wird zurückgegeben.

## <a name="free"></a><a name="free"></a> Kosten

Gibt einen Speicherblock frei, der zuvor mit der `Alloc`-Methode der Unterbelegungsfunktion für die Zwischenspeicherung der Concurrency Runtime reserviert wurde.

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Parameter

*_PAllocation*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor mit der `Alloc`-Methode reserviert wurde und jetzt freigegeben werden soll. Wenn der `_PAllocation`-Parameter auf den Wert `NULL` festgelegt wurde, ignoriert diese Methode den Parameter und kehrt sofort zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen darüber, welche Szenarien in Ihrer Anwendung von der Verwendung der cachesubzuweisung profitieren können, finden Sie unter [Taskplaner](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="get_ambient_scheduler"></a><a name="get_ambient_scheduler"></a> get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Rückgabewert

## <a name="getexecutioncontextid"></a><a name="getexecutioncontextid"></a> GetExecutionContextId

Gibt einen eindeutigen Bezeichner zurück, der einem Ausführungskontext zugewiesen werden kann, der die `IExecutionContext`-Schnittstelle implementiert.

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Bezeichner für einen Ausführungs Kontext.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um einen Bezeichner für den Ausführungs Kontext abzurufen, bevor Sie eine `IExecutionContext` Schnittstelle als Parameter an eine der Methoden übergeben, die vom Ressourcen-Manager angeboten werden.

## <a name="getosversion"></a><a name="getosversion"></a> GetOSVersion

Gibt die Betriebssystemversion zurück.

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Rückgabewert

Ein Enumerationswert, der das Betriebssystem darstellt.

### <a name="remarks"></a>Bemerkungen

[Unsupported_os](unsupported-os-class.md) wird ausgelöst, wenn das Betriebssystem vom Concurrency Runtime nicht unterstützt wird.

## <a name="getprocessorcount"></a><a name="getprocessorcount"></a> GetProcessorCount

Gibt die Anzahl von Hardwarethreads des zugrunde liegenden Systems zurück.

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Hardwarethreads.

### <a name="remarks"></a>Bemerkungen

[Unsupported_os](unsupported-os-class.md) wird ausgelöst, wenn das Betriebssystem vom Concurrency Runtime nicht unterstützt wird.

## <a name="getprocessornodecount"></a><a name="getprocessornodecount"></a> GetProcessorNodeCount

Gibt die Anzahl von NUMA-Knoten oder Prozessorpaketen des zugrunde liegenden Systems zurück.

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von NUMA-Knoten oder Prozessorpaketen.

### <a name="remarks"></a>Bemerkungen

Wenn das System mehr NUMA-Knoten als Prozessorpakete enthält, wird die Anzahl der NUMA-Knoten zurückgegeben. Andernfalls wird die Anzahl der Prozessorpakete zurückgegeben.

[Unsupported_os](unsupported-os-class.md) wird ausgelöst, wenn das Betriebssystem vom Concurrency Runtime nicht unterstützt wird.

## <a name="getschedulerid"></a><a name="getschedulerid"></a> GetSchedulerId

Gibt einen eindeutigen Bezeichner zurück, der einem Planer zugewiesen werden kann, der die `IScheduler`-Schnittstelle implementiert.

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Bezeichner für einen Scheduler.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um einen Bezeichner für den Scheduler abzurufen, bevor Sie eine `IScheduler` Schnittstelle als Parameter an eine der Methoden übergeben, die vom Ressourcen-Manager angeboten werden.

## <a name="internal_assign_iterators"></a><a name="internal_assign_iterators"></a> internal_assign_iterators

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

## <a name="interruption_point"></a><a name="interruption_point"></a> interruption_point

Erstellt einen Unterbrechungspunkt für den Abbruch. Wenn ein Abbruch im Kontext, in dem diese Funktion aufgerufen wird, ausgeführt wird, löst diese eine interne Ausnahme aus, mit der die Ausführung der aktuell ausgeführten parallelen Verarbeitung abgebrochen wird. Wenn kein Abbruch ausgeführt wird, bleibt die Funktion untätig.

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>Bemerkungen

Die von der Funktion ausgelöste interne Abbruch Ausnahme sollte nicht abgefangen werden `interruption_point()` . Die Ausnahme wird von der Laufzeit abgefangen und behandelt, und das abfangen kann dazu führen, dass sich das Programm nicht ordnungsgemäß verhält.

## <a name="is_current_task_group_canceling"></a><a name="is_current_task_group_canceling"></a> is_current_task_group_canceling

Gibt zurück, ob die Aufgabengruppe, die gerade inline auf dem aktuellen Kontext ausgeführt wird, in diesem Moment (oder in Kürze) einen Abbruch durchführt. Beachten Sie, dass zurückgegeben wird, wenn derzeit keine Aufgaben Gruppe im aktuellen Kontext Inline ausgeführt wird **`false`** .

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die derzeit ausgeführte Aufgaben Gruppe abgebrochen wird, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Abbruch](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="make_choice"></a><a name="make_choice"></a> make_choice

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

## <a name="make_greedy_join"></a><a name="make_greedy_join"></a> make_greedy_join

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

## <a name="make_join"></a><a name="make_join"></a> make_join

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

## <a name="make_task"></a><a name="make_task"></a> make_task

Eine Factorymethode zum Erstellen eines `task_handle`-Objekts.

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktions Objekts, das aufgerufen wird, um die durch das-Objekt dargestellte Arbeit auszuführen `task_handle` .

*_Func*<br/>
Die Funktion, die aufgerufen wird, um die durch das-Objekt dargestellte Arbeit auszuführen `task_handle` . Hierbei kann es sich um einen Lambda-Funktor, einen Zeiger auf eine Funktion oder ein beliebiges Objekt handeln, das eine Version des Funktions aufrufoperators mit der Signatur unterstützt `void operator()()` .

### <a name="return-value"></a>Rückgabewert

Ein `task_handle`-Objekt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nützlich, wenn Sie ein- `task_handle` Objekt mit einem Lambda-Ausdruck erstellen müssen, da es Ihnen ermöglicht, das-Objekt zu erstellen, ohne den tatsächlichen Typ des Lambda-funktors zu kennen.

## <a name="parallel_buffered_sort"></a><a name="parallel_buffered_sort"></a> parallel_buffered_sort

Ordnet die Elemente in einem angegebenen Bereich in einer nicht absteigenden Reihenfolge oder entsprechend einem Sortierkriterium an, das von einem binären Prädikat gleichzeitig angegeben wird. Diese Funktion entspricht `std::sort` semantisch darin, dass sie eine vergleichsbasierte, instabile, direkte Sortierung ist, abgesehen von den zusätzlich erforderlichen `O(n)`-Leerzeichen und er notwendigen Standardinitialisierung für die sortierten Elemente.

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
Der iteratortyp des Eingabe Bereichs.

*_Allocator*<br/>
Der Typ einer C++-Standard Bibliothek kompatiblen Speicherzuweisung.

*_Function*<br/>
Der Typ des binären Vergleichs Operators.

*_Begin*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*_End*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der sortiert werden soll.

*_Alloc*<br/>
Eine Instanz einer C++-Standard Bibliothek kompatiblen Speicherzuweisung.

*_Func*<br/>
Ein benutzerdefiniertes Prädikat Funktions Objekt, das das Vergleichskriterium definiert, das von aufeinander folgenden Elementen in der Reihenfolge erfüllt werden soll. Ein binäres Prädikat übernimmt zwei Argumente und gibt **`true`** bei Erfüllung und **`false`** bei Nichterfüllung zurück. Diese Vergleichoperatorfunktion muss eine strikte schwache Sortierung auf Elementenpaare der Sequenz anwenden.

*_Chunk_size*<br/>
Die imitige Größe eines Blocks, der für die parallele Ausführung in zwei Spalten aufgeteilt wird.

### <a name="remarks"></a>Bemerkungen

Alle über Ladungen erfordern `n * sizeof(T)` zusätzlichen Speicherplatz, wobei `n` die Anzahl der zu sortierenden Elemente und `T` der Elementtyp ist. In den meisten Fällen wird parallel_buffered_sort eine Verbesserung der Leistung gegenüber [parallel_sort](concurrency-namespace-functions.md)anzeigen, und Sie sollten Sie über parallel_sort verwenden, wenn Sie über den verfügbaren Arbeitsspeicher verfügen.

Wenn Sie kein binäres Vergleichs `std::less` Element angeben, wird als Standardwert verwendet, der erfordert, dass der-Elementtyp den-Operator bereitstellt `operator<()` .

Wenn Sie keinen zuordnertyp oder keine Instanz angeben, wird die Speicherzuweisung der C++-Standard Bibliothek `std::allocator<T>` verwendet, um den Puffer zuzuordnen.

Der Algorithmus dividiert den Eingabebereich in zwei Blöcke und dividiert jeden Block nacheinander in zwei unter Segmente für die parallele Ausführung. Das optionale-Argument `_Chunk_size` kann verwendet werden, um für den Algorithmus anzugeben, dass er Blöcke der Größe < `_Chunk_size` seriell verarbeiten soll.

## <a name="parallel_for"></a><a name="parallel_for"></a> parallel_for

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
Der Typ des Indexes, der für die Iterationen verwendet wird.

*_Function*<br/>
Der Typ der Funktion, die bei jeder Iterationen ausgeführt wird.

*_Partitioner*<br/>
Der Typ des Partitionierers, der verwendet wird, um den angegebenen Bereich zu partitionieren.

*first*<br/>
Der erste Index, der in die Iterations eingefügt werden soll.

*last*<br/>
Der Index eins hinter dem letzten Index, der in die Iterations-eingeschlossen werden soll.

*_Step*<br/>
Der Wert, um den bei der Iteration von nach ein Schritt durchlaufen werden soll `first` `last` . Der Schritt muss positiv sein. [Invalid_argument](../../../standard-library/invalid-argument-class.md) wird ausgelöst, wenn der Schritt kleiner als 1 ist.

*_Func*<br/>
Die Funktion, die bei jeder Iterationen ausgeführt werden soll. Dabei kann es sich um einen Lambda-Ausdruck, einen Funktionszeiger oder ein beliebiges Objekt handeln, das eine Version des Funktions aufrufoperators mit der Signatur unterstützt `void operator()(_Index_type)` .

*_Part*<br/>
Ein Verweis auf das Partitionierer-Objekt. Bei dem Argument kann es sich um einen **`const`** [auto_partitioner](auto-partitioner-class.md) `&` , **`const`** [static_partitioner](static-partitioner-class.md) `&` **`const`** [simple_partitioner](simple-partitioner-class.md) `&` oder um [affinity_partitioner](affinity-partitioner-class.md) `&` Wenn ein [affinity_partitioner](affinity-partitioner-class.md) Objekt verwendet wird, muss es sich bei dem Verweis um einen nicht konstanten l-Wert-Verweis handeln, damit der Algorithmus den Zustand für zukünftige Schleifen speichern kann.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [parallele Algorithmen](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_for_each"></a><a name="parallel_for_each"></a> parallel_for_each

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
Der Typ des Iterators, der verwendet wird, um den Container zu durchlaufen.

*_Function*<br/>
Der Typ der Funktion, die auf jedes Element im Bereich angewendet wird.

*_Partitioner*<br/>
*first*<br/>
Ein Iterator, der die Position des ersten Elements adressiert, das in die parallele Iterationen eingeschlossen werden soll.

*last*<br/>
Ein Iterator, der die Position hinter dem letzten Element adressiert, das in die parallele Iterationen eingeschlossen werden soll.

*_Func*<br/>
Ein benutzerdefiniertes Funktions Objekt, das auf jedes Element im Bereich angewendet wird.

*_Part*<br/>
Ein Verweis auf das Partitionierer-Objekt. Bei dem Argument kann es sich um einen **`const`** [auto_partitioner](auto-partitioner-class.md) `&` , **`const`** [static_partitioner](static-partitioner-class.md) `&` **`const`** [simple_partitioner](simple-partitioner-class.md) `&` oder um [affinity_partitioner](affinity-partitioner-class.md) `&` Wenn ein [affinity_partitioner](affinity-partitioner-class.md) Objekt verwendet wird, muss es sich bei dem Verweis um einen nicht konstanten l-Wert-Verweis handeln, damit der Algorithmus den Zustand für zukünftige Schleifen speichern kann.

### <a name="remarks"></a>Bemerkungen

[auto_partitioner](auto-partitioner-class.md) wird für die Überladung ohne einen expliziten Partitionierer verwendet.

Für Iteratoren, die keinen zufälligen Zugriff unterstützen, wird nur [auto_partitioner](auto-partitioner-class.md) unterstützt.

Weitere Informationen finden Sie unter [parallele Algorithmen](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_invoke"></a><a name="parallel_invoke"></a> parallel_invoke

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
Der Typ des ersten Funktions Objekts, das parallel ausgeführt werden soll.

*_Function2*<br/>
Der Typ des zweiten Funktions Objekts, das parallel ausgeführt werden soll.

*_Function3*<br/>
Der Typ des dritten Funktions Objekts, das parallel ausgeführt werden soll.

*_Function4*<br/>
Der Typ des vierten Funktions Objekts, das parallel ausgeführt werden soll.

*_Function5*<br/>
Der Typ des fünften Funktions Objekts, das parallel ausgeführt werden soll.

*_Function6*<br/>
Der Typ des sechsten Funktions Objekts, das parallel ausgeführt werden soll.

*_Function7*<br/>
Der Typ des siebten Funktions Objekts, das parallel ausgeführt werden soll.

*_Function8*<br/>
Der Typ des achten Funktions Objekts, das parallel ausgeführt werden soll.

*_Function9*<br/>
Der Typ des neunten Funktions Objekts, das parallel ausgeführt werden soll.

*_Function10*<br/>
Der Typ des zehnten Funktions Objekts, das parallel ausgeführt werden soll.

*_Func1*<br/>
Das erste Funktions Objekt, das parallel ausgeführt werden soll.

*_Func2*<br/>
Das zweite Funktions Objekt, das parallel ausgeführt werden soll.

*_Func3*<br/>
Das dritte Funktions Objekt, das parallel ausgeführt werden soll.

*_Func4*<br/>
Das vierte Funktions Objekt, das parallel ausgeführt werden soll.

*_Func5*<br/>
Das fünfte Funktions Objekt, das parallel ausgeführt werden soll.

*_Func6*<br/>
Das sechste Funktions Objekt, das parallel ausgeführt werden soll.

*_Func7*<br/>
Das siebte Funktions Objekt, das parallel ausgeführt werden soll.

*_Func8*<br/>
Das achte Funktions Objekt, das parallel ausgeführt werden soll.

*_Func9*<br/>
Das neunte Funktions Objekt, das parallel ausgeführt werden soll.

*_Func10*<br/>
Das zehnte Funktions Objekt, das parallel ausgeführt werden soll.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass mindestens ein Funktions Objekt, das als Parameter angegeben wird, Inline im aufrufenden Kontext ausgeführt werden kann.

Wenn mindestens eines der Funktions Objekte, das als Parameter an diese Funktion weitergegeben wird, eine Ausnahme auslöst, wählt die Laufzeit eine solche Ausnahme aus, die von ihr ausgewählt wird, und gibt Sie aus dem aufzurufenden an `parallel_invoke` .

Weitere Informationen finden Sie unter [parallele Algorithmen](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_radixsort"></a><a name="parallel_radixsort"></a> parallel_radixsort

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
Der iteratortyp des Eingabe Bereichs.

*_Allocator*<br/>
Der Typ einer C++-Standard Bibliothek kompatiblen Speicherzuweisung.

*_Function*<br/>
Der Typ der Projektions Funktion.

*_Begin*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*_End*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der sortiert werden soll.

*_Alloc*<br/>
Eine Instanz einer C++-Standard Bibliothek kompatiblen Speicherzuweisung.

*_Proj_func*<br/>
Ein benutzerdefiniertes Projektions Funktions Objekt, das ein Element in einen ganzzahligen Wert konvertiert.

*_Chunk_size*<br/>
Die imitige Größe eines Blocks, der für die parallele Ausführung in zwei Spalten aufgeteilt wird.

### <a name="remarks"></a>Bemerkungen

Alle über Ladungen erfordern `n * sizeof(T)` zusätzlichen Speicherplatz, wobei `n` die Anzahl der zu sortierenden Elemente und `T` der Elementtyp ist. Ein unäres Projektions Funktor mit der Signatur `I _Proj_func(T)` ist erforderlich, um einen Schlüssel zurückzugeben, wenn ein Element angegeben wird, wobei `T` der Elementtyp und `I` ein ganzzahliger ganzzahliger Typ ohne Vorzeichen ist.

Wenn Sie keine Projektions Funktion bereitstellen, wird eine Standard Projektions Funktion, die einfach das-Element zurückgibt, für ganzzahlige Typen verwendet. Die Funktion kann nicht kompiliert werden, wenn das Element kein ganzzahliger Typ ist, wenn eine Projektions Funktion fehlt.

Wenn Sie keinen zuordnertyp oder keine Instanz angeben, wird die Speicherzuweisung der C++-Standard Bibliothek `std::allocator<T>` verwendet, um den Puffer zuzuordnen.

Der Algorithmus dividiert den Eingabebereich in zwei Blöcke und dividiert jeden Block nacheinander in zwei unter Segmente für die parallele Ausführung. Das optionale-Argument `_Chunk_size` kann verwendet werden, um für den Algorithmus anzugeben, dass er Blöcke der Größe < `_Chunk_size` seriell verarbeiten soll.

## <a name="parallel_reduce"></a><a name="parallel_reduce"></a> parallel_reduce

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
Der iteratortyp des Eingabe Bereichs.

*_Sym_reduce_fun*<br/>
Der Typ der symmetrischen Reduzierungs Funktion. Dabei muss es sich um einen Funktionstyp mit der Signatur handeln `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)` , bei dem _Reduce_type identisch mit dem Identitätstyp und dem Ergebnistyp der Reduzierung ist. Für die dritte Überladung muss dies mit dem Ausgabetyp von konsistent sein `_Range_reduce_fun` .

*_Reduce_type*<br/>
Der Typ, auf den die Eingabe reduziert wird, der sich vom Eingabe Elementtyp unterscheiden kann. Der Rückgabewert und der Identitäts Wert weisen diesen Typ auf.

*_Range_reduce_fun*<br/>
Der Typ der Bereichs Reduzierungs Funktion. Dabei muss es sich um einen Funktionstyp mit Signatur handeln `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)` , _Reduce_type identisch mit dem Identitätstyp und dem Ergebnistyp der Reduzierung ist.

*_Begin*<br/>
Ein eingabeiterator, der das erste Element im zu redugenden Bereich adressiert.

*_End*<br/>
Ein eingabeiterator, der das Element adressiert, das eine Position hinter dem letzten Element im zu redugenden Bereich ist.

*_Identity*<br/>
Der Identitäts Wert `_Identity` ist vom selben Typ wie der Ergebnistyp der Reduzierung und auch der `value_type` des Iterators für die erste und die zweite Überladung. Für die dritte Überladung muss der Identitäts Wert denselben Typ wie der Ergebnistyp der Reduzierung aufweisen, er kann sich aber vom `value_type` des Iterators unterscheiden. Er muss über einen geeigneten Wert verfügen, damit der Bereichs Reduzierungs Operator `_Range_fun` , wenn er auf einen Bereich eines einzelnen Elements vom Typ `value_type` und den Identitäts Wert angewendet wird, wie eine Typumwandlung des Werts vom Typ `value_type` in den Identitätstyp verhält.

*_Sym_fun*<br/>
Die symmetrische Funktion, die in der zweiten der Reduzierung verwendet wird. Weitere Informationen finden Sie in den hinweisen.

*_Range_fun*<br/>
Die Funktion, die in der ersten Phase der Reduzierung verwendet wird. Weitere Informationen finden Sie in den hinweisen.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Reduzierung.

### <a name="remarks"></a>Bemerkungen

Um eine parallele Reduzierung auszuführen, dividiert die Funktion den Bereich auf der Grundlage der Anzahl der Worker, die für den zugrunde liegenden Scheduler verfügbar sind. Die Reduzierung erfolgt in zwei Phasen, in der ersten Phase wird in jedem Segment eine Reduzierung durchgeführt, und in der zweiten Phase wird eine Reduzierung der partiellen Ergebnisse aus jedem Block durchgeführt.

Die erste Überladung erfordert, dass der Iterator `value_type` , `T` , identisch mit dem Identitäts Werttyp und dem reduzierungergebnistyp ist. Der Elementtyp T muss den Operator bereitstellen `T T::operator + (T)` , um Elemente in jedem Segment zu reduzieren. Der gleiche Operator wird auch in der zweiten Phase verwendet.

Die zweite Überladung erfordert auch, dass der Iterator mit dem `value_type` Identitäts Werttyp und dem reduzierungergebnistyp identisch ist. Der angegebene binäre Operator `_Sym_fun` wird in beiden Reduzierungs Phasen verwendet, wobei der Identitäts Wert als Anfangswert für die erste Phase verwendet wird.

Für die dritte Überladung muss der Identitäts Werttyp mit dem reduzierungstyp identisch sein, aber die Iteratoren `value_type` können sich von beiden unterscheiden. Die Bereichs Reduzierungs Funktion `_Range_fun` wird in der ersten Phase mit dem Identitäts Wert als Anfangswert verwendet, und die binäre Funktion `_Sym_reduce_fun` wird in der zweiten Phase auf Sub-Ergebnisse angewendet.

## <a name="parallel_sort"></a><a name="parallel_sort"></a> parallel_sort

Ordnet die Elemente in einem angegebenen Bereich in einer nicht absteigenden Reihenfolge oder entsprechend einem Sortierkriterium an, das von einem binären Prädikat gleichzeitig angegeben wird. Diese Funktion entspricht `std::sort` semantisch insofern, dass sie eine vergleichsbasierte, instabile, direkte Sortierung ist.

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
Der iteratortyp des Eingabe Bereichs.

*_Function*<br/>
Der Typ des funktors für binäre Vergleiche.

*_Begin*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*_End*<br/>
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der sortiert werden soll.

*_Func*<br/>
Ein benutzerdefiniertes Prädikat Funktions Objekt, das das Vergleichskriterium definiert, das von aufeinander folgenden Elementen in der Reihenfolge erfüllt werden soll. Ein binäres Prädikat übernimmt zwei Argumente und gibt **`true`** bei Erfüllung und **`false`** bei Nichterfüllung zurück. Diese Vergleichoperatorfunktion muss eine strikte schwache Sortierung auf Elementenpaare der Sequenz anwenden.

*_Chunk_size*<br/>
Die minimale Größe eines Blocks, der für die parallele Ausführung in zwei Spalten aufgeteilt wird.

### <a name="remarks"></a>Bemerkungen

Die erste Überladung verwendet den binären Vergleichs Operator `std::less` .

Der zweite überladene verwendet den bereitgestellten binären Vergleichs Operator, der über die Signatur verfügen soll, `bool _Func(T, T)` wobei `T` der Typ der Elemente im Eingabebereich ist.

Der Algorithmus dividiert den Eingabebereich in zwei Blöcke und dividiert jeden Block nacheinander in zwei unter Segmente für die parallele Ausführung. Das optionale-Argument `_Chunk_size` kann verwendet werden, um für den Algorithmus anzugeben, dass er Blöcke der Größe < `_Chunk_size` seriell verarbeiten soll.

## <a name="parallel_transform"></a><a name="parallel_transform"></a> parallel_transform

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
Der Typ des ersten oder einzigen eingabeiterators.

*_Output_iterator*<br/>
Der Typ des Ausgabeiterators.

*_Unary_operator*<br/>
Der Typ des unären funktors, der für jedes Element im Eingabebereich ausgeführt werden soll.

*_Input_iterator2*<br/>
Der Typ des zweiten eingabeiterators.

*_Binary_operator*<br/>
Der Typ des binären funktors, der paarweise für Elemente aus den beiden Quell Bereichen ausgeführt wird.

*_Partitioner*<br/>
*First1*<br/>
Ein eingabeiterator, der die Position des ersten Elements im ersten oder einzigen Quellbereich adressiert, der verarbeitet werden soll.

*Last1*<br/>
Ein eingabeiterator, der die Position hinter dem letzten Element im ersten oder einzigen Quellbereich adressiert, der verarbeitet werden soll.

*_Result*<br/>
Ein Ausgabeiterator, der die Position des ersten Elements im Zielbereich adressiert.

*_Unary_op*<br/>
Ein benutzerdefiniertes unäres Funktions Objekt, das auf jedes Element im Quellbereich angewendet wird.

*_Part*<br/>
Ein Verweis auf das Partitionierer-Objekt. Bei dem Argument kann es sich um einen **`const`** [auto_partitioner](auto-partitioner-class.md) `&` , **`const`** [static_partitioner](static-partitioner-class.md) `&` **`const`** [simple_partitioner](simple-partitioner-class.md) `&` oder um [affinity_partitioner](affinity-partitioner-class.md) `&` Wenn ein [affinity_partitioner](affinity-partitioner-class.md) Objekt verwendet wird, muss es sich bei dem Verweis um einen nicht konstanten l-Wert-Verweis handeln, damit der Algorithmus den Zustand für zukünftige Schleifen speichern kann.

*First2*<br/>
Ein Eingabeiterator, der die Position des ersten Elements im zweiten Quellbereich adressiert.

*_Binary_op*<br/>
Ein benutzerdefiniertes binäres Funktions Objekt, das paarweise in einer vorwärts Reihenfolge auf die beiden Quellbereiche angewendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position direkt hinter dem letzten Element im Zielbereich adressiert, der die vom Funktionsobjekt umgewandelten Ausgabeelemente erhält.

### <a name="remarks"></a>Bemerkungen

[auto_partitioner](auto-partitioner-class.md) werden für die über Ladungen ohne ein explizites partiierer-Argument verwendet.

Für Iteratoren, die keinen zufälligen Zugriff unterstützen, wird nur [auto_partitioner](auto-partitioner-class.md) unterstützt.

Die über Ladungen, die das-Argument akzeptieren, `_Unary_op` transformieren den Eingabebereich in den Ausgabebereich, indem Sie den unären Funktor auf jedes Element im Eingabebereich anwenden. `_Unary_op` muss den Funktions Aufrufoperator mit der Signatur unterstützen `operator()(T)` `T` , wobei der Werttyp des Bereichs ist, der durchlaufen wird.

Die über Ladungen, die das-Argument akzeptieren, `_Binary_op` transformieren zwei Eingabe Bereiche in den Ausgabebereich, indem Sie das binäre Funktor auf ein Element vom ersten Eingabebereich und ein Element aus dem zweiten Eingabebereich anwenden. `_Binary_op` muss den Funktions Aufrufoperator mit der Signatur unterstützen `operator()(T, U)` , wobei die `T` Werttypen der beiden eingabeiteratoren `U` sind.

Weitere Informationen finden Sie unter [parallele Algorithmen](../../../parallel/concrt/parallel-algorithms.md).

## <a name="receive"></a><a name="receive"></a> medizinisch

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
Der Nutz Lasttyp.

*_Src*<br/>
Ein Zeiger oder Verweis auf die Quelle, aus der Daten erwartet werden.

*_Timeout*<br/>
Die maximale Zeit, für die die Methode für die Daten in Millisekunden angegeben werden soll.

*_Filter_proc*<br/>
Eine Filterfunktion, die bestimmt, ob Nachrichten akzeptiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Wert aus der Quelle des Nutz Last Typs.

### <a name="remarks"></a>Bemerkungen

Wenn der-Parameter `_Timeout` einen anderen Wert als die-Konstante aufweist `COOPERATIVE_TIMEOUT_INFINITE` , wird die Ausnahme [Operation_timed_out](operation-timed-out-class.md) ausgelöst, wenn die angegebene Zeitspanne abläuft, bevor eine Nachricht empfangen wird. Wenn Sie ein Timeout der Länge 0 (null) benötigen, sollten Sie die [Try_receive](concurrency-namespace-functions.md) -Funktion verwenden, anstatt `receive` mit einem Timeout von `0` (null) aufrufen zu müssen, da Sie effizienter ist und keine Ausnahmen für Timeouts auslöst.

Weitere Informationen finden Sie unter [Nachrichten Übergabe Funktionen](../../../parallel/concrt/message-passing-functions.md).

## <a name="run_with_cancellation_token"></a><a name="run_with_cancellation_token"></a> run_with_cancellation_token

Führt sofort synchron ein Funktionsobjekt im Kontext eines angegebenen Abbruchtokens aus.

```cpp
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktions Objekts, das aufgerufen wird.

*_Func*<br/>
Das Funktions Objekt, das ausgeführt wird. Dieses Objekt muss den Funktions Aufrufoperator mit der Signatur void (void) unterstützen.

*_Ct*<br/>
Das Abbruch Token, das den impliziten Abbruch des Funktions Objekts steuert. Verwenden `cancellation_token::none()` Sie, wenn die Funktion ausgeführt werden soll, ohne dass die Möglichkeit besteht, dass eine übergeordnete Aufgaben Gruppe abgebrochen wird.

### <a name="remarks"></a>Bemerkungen

Alle Unterbrechungs Punkte im Funktions Objekt werden ausgelöst, wenn der `cancellation_token` abgebrochen wird. Das explizite Token `_Ct` isoliert dies `_Func` von einem übergeordneten Abbruch, wenn das übergeordnete Element über ein anderes Token oder kein Token verfügt.

## <a name="send"></a><a name="send"></a> Senden

Ein synchroner Sendevorgang, der wartet, bis das Ziel die Meldung akzeptiert oder ablehnt.

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Nutz Lasttyp.

*_Trg*<br/>
Ein Zeiger oder Verweis auf das Ziel, an das Daten gesendet werden.

*_Data*<br/>
Ein Verweis auf die zu sendenden Daten.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die Nachricht akzeptiert wurde, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Nachrichten Übergabe Funktionen](../../../parallel/concrt/message-passing-functions.md).

## <a name="set_ambient_scheduler"></a><a name="set_ambient_scheduler"></a> set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Parameter

*_Scheduler*<br/>
Der zu fest Legende Ambient-Scheduler.

## <a name="set_task_execution_resources"></a><a name="set_task_execution_resources"></a> set_task_execution_resources

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
Die Affinitäts Maske, auf die die Concurrency Runtime Arbeitsthreads beschränkt werden soll. Verwenden Sie diese Methode nur auf einem System mit mehr als 64 Hardwarethreads, wenn Sie die Concurrency Runtime auf eine Teilmenge der aktuellen Prozessor Gruppe begrenzen möchten. Im Allgemeinen sollten Sie die Version der-Methode verwenden, die ein Array von Gruppen Affinitäten als Parameter annimmt, um die Affinität auf Computern mit mehr als 64 Hardwarethreads einzuschränken.

*count*<br/>
Die Anzahl der `GROUP_AFFINITY` Einträge im Array, die durch den-Parameter angegeben werden `_PGroupAffinity` .

*_PGroupAffinity*<br/>
Ein Array von `GROUP_AFFINITY` Einträgen.

### <a name="remarks"></a>Bemerkungen

Die Methode löst eine [Invalid_operation](invalid-operation-class.md) Ausnahme aus, wenn ein Ressourcen-Manager zum Zeitpunkt des aufgerufenen vorhanden ist, und eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme, wenn die angegebene Affinität einen leeren Satz von Ressourcen ergibt.

Die Version der-Methode, die ein Array von Gruppen Affinitäten als Parameter annimmt, sollte nur auf Betriebssystemen mit Version Windows 7 oder höher verwendet werden. Andernfalls wird eine [Invalid_operation](invalid-operation-class.md) Ausnahme ausgelöst.

Die programmgesteuerte Änderung der Prozess Affinität, nachdem diese Methode aufgerufen wurde, bewirkt nicht, dass die Ressourcen-Manager die Affinität, auf die Sie beschränkt ist, neu auswerten. Daher sollten alle Änderungen an der Prozess Affinität vorgenommen werden, bevor diese Methode aufgerufen wird.

## <a name="swap"></a><a name="swap"></a> Wechsel

Tauscht die Elemente zweier `concurrent_vector`-Objekte.

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Elemente, die in den gleichzeitigen Vektoren gespeichert werden.

*_Ax*<br/>
Der zuordnertyp der gleichzeitigen Vektoren.

*_A*<br/>
Der gleichzeitige Vektor, dessen Elemente mit denen des gleichzeitigen Vektors ausgetauscht werden sollen `_B` .

*_B*<br/>
Der gleichzeitige Vektor, der die auszutauschenden Elemente bereitstellt, oder der Vektor, dessen Elemente mit denen des gleichzeitigen Vektors ausgetauscht werden sollen `_A` .

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion ist ein Algorithmus, der auf die Container Klasse spezialisiert ist `concurrent_vector` , um die Member-Funktion auszuführen `_A` . [concurrent_vector:: Swap](concurrent-vector-class.md#swap)( `_B` ). Hierbei handelt es sich um Instanzen der partiellen Sortierung von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die spezialisierteste Version der Vorlagenfunktion aus. Die allgemeine Version der Vorlagen Funktion `template <class T> void swap(T&, T&)` in der Algorithmusklasse funktioniert durch Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse genutzt werden kann.

Diese Methode ist nicht nebenläufigkeitssicher. Wenn Sie diese Methode aufgerufen haben, müssen Sie sicherstellen, dass keine anderen Threads Vorgänge für einen der gleichzeitigen Vektoren durchführen.

## <a name="task_from_exception"></a><a name="task_from_exception"></a> task_from_exception

```cpp
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parameter

*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Rückgabewert

## <a name="task_from_result"></a><a name="task_from_result"></a> task_from_result

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

## <a name="trace_agents_register_name"></a><a name="trace_agents_register_name"></a> Trace_agents_register_name

Ordnet den angegebenen Namen dem Nachrichtenblock oder dem Agent in der ETW-Ablaufverfolgung zu.

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Objekts. Dabei handelt es sich in der Regel um einen Nachrichtenblock oder einen Agent.

*_PObject*<br/>
Ein Zeiger auf den Nachrichtenblock oder den Agent, der in der Ablauf Verfolgung benannt wird.

*_Name*<br/>
Der Name für das angegebene Objekt.

## <a name="try_receive"></a><a name="try_receive"></a> try_receive

Eine allgemeine try-receive-Implementierung, mit der ein Kontext Daten von genau einer Quelle suchen und die akzeptierten Werte filtern kann. Wenn die Daten nicht bereit sind, gibt die Methode zurück **`false`** .

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
Der Nutz Lasttyp.

*_Src*<br/>
Ein Zeiger oder Verweis auf die Quelle, aus der Daten erwartet werden.

*_value*<br/>
Ein Verweis auf einen Speicherort, an dem das Ergebnis platziert wird.

*_Filter_proc*<br/>
Eine Filterfunktion, die bestimmt, ob Nachrichten akzeptiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein **`bool`** Wert, der angibt, ob eine Nutzlast in eingefügt wurde `_value` .

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Nachrichten Übergabe Funktionen](../../../parallel/concrt/message-passing-functions.md).

## <a name="wait"></a><a name="wait"></a> Warte

Hält den aktuellen Kontext für eine bestimmte Zeit an.

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Parameter

*_Milliseconds*<br/>
Die Anzahl von Millisekunden, für die der aktuelle Kontext angehalten werden soll. Wenn der- `_Milliseconds` Parameter auf den-Wert festgelegt ist `0` , sollte der aktuelle Kontext die Ausführung in anderen ausführbaren Kontexten erzielen, bevor Sie fortfahren.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode für einen Concurrency Runtime Scheduler-Kontext aufgerufen wird, findet der Planer einen anderen Kontext, der für die zugrunde liegende Ressource ausgeführt werden kann. Da der Scheduler in der Natur kooperativ ist, kann dieser Kontext nicht genau nach der angegebenen Anzahl von Millisekunden wieder aufgenommen werden. Wenn das Zeit Planungs Modul mit dem Ausführen anderer Aufgaben beschäftigt ist, die nicht kooperativ an den Scheduler übergeben werden, kann die Wartezeit unbegrenzt sein.

## <a name="when_all"></a><a name="when_all"></a> when_all

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

Eine Aufgabe, die erfolgreich abgeschlossen wird, wenn alle Eingabe Aufgaben erfolgreich abgeschlossen wurden. Wenn die Eingabeaufgaben vom Typ `T` sind, wird die Ausgabe dieser Funktion `task<std::vector<T>>` sein. Wenn die Eingabe Aufgaben vom Typ sind, ist **`void`** die Ausgabe Aufgabe ebenfalls ein `task<void>` .

### <a name="remarks"></a>Bemerkungen

`when_all` ist eine nicht blockierende Funktion, die `task` als Ergebnis erzeugt. Anders als bei [Task:: Wait](task-class.md#wait)ist es sicher, diese Funktion in einer UWP-App auf dem AStA-Thread (Application STA) aufzurufen.

Wenn eine der Aufgaben abgebrochen wird oder eine Ausnahme auslöst, wird die zurückgegebene Aufgabe früh im abgebrochenen Zustand ausgeführt, und die Ausnahme wird ausgelöst, wenn Sie [Task:: Get](task-class.md#get) oder `task::wait` für diese Aufgabe aufruft.

Weitere Informationen finden Sie unter [Aufgaben Parallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="when_any"></a><a name="when_any"></a> when_any

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

Eine Aufgabe, die erfolgreich abgeschlossen ist, wenn eine der Eingabeaufgaben erfolgreich abgeschlossen wurde. Wenn die Eingabeaufgaben vom Typ `T` sind, ist die Ausgabe dieser Funktion `task<std::pair<T, size_t>>>`, wobei das erste Element des Paares das Ergebnis der letzten Aufgabe ist, und das zweite Element der Index der beendeten Aufgabe. Wenn die Eingabe Aufgaben vom Typ sind **`void`** , ist die Ausgabe eine `task<size_t>` , bei der es sich bei dem Ergebnis um den Index der abgeschlossenen Aufgabe handelt.

### <a name="remarks"></a>Bemerkungen

`when_any` ist eine nicht blockierende Funktion, die `task` als Ergebnis erzeugt. Anders als bei [Task:: Wait](task-class.md#wait)ist es sicher, diese Funktion in einer UWP-App auf dem AStA-Thread (Application STA) aufzurufen.

Weitere Informationen finden Sie unter [Aufgaben Parallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)
