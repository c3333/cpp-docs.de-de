---
title: CurrentScheduler-Klasse
ms.date: 11/04/2016
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
ms.openlocfilehash: 6bf61af9ff55722553353a045c87501dbd27fad9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427410"
---
# <a name="currentscheduler-class"></a>CurrentScheduler-Klasse

Stellt eine Abstraktion für den aktuellen Planer dar, der dem aufrufenden Kontext zugeordnet ist.

## <a name="syntax"></a>Syntax

```cpp
class CurrentScheduler;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[Erstellen](#create)|Erstellt einen neuen Scheduler, dessen Verhalten durch den `_Policy`-Parameter beschrieben und an den aufrufenden Kontext angefügt wird. Der neu erstellte Scheduler wird zum aktuellen Planer für den aufrufenden Kontext.|
|[CreateScheduleGroup](#createschedulegroup)|Ist überladen. Erstellt eine neue Zeit Plan Gruppe innerhalb des Planers, der dem aufrufenden Kontext zugeordnet ist. Die Version, die den-Parameter annimmt `_Placement` bewirkt, dass Tasks innerhalb der neu erstellten Zeit Plan Gruppe für die Ausführung an der durch diesen Parameter angegebenen Position verzerrt werden.|
|[Trennen](#detach)|Trennt den aktuellen Scheduler vom aufrufenden Kontext und stellt den zuvor angefügten Planer als aktuellen Scheduler wieder her, falls vorhanden. Nachdem diese Methode zurückgegeben wurde, wird der aufrufenden Kontext vom Scheduler verwaltet, der zuvor mit der `CurrentScheduler::Create`-oder `Scheduler::Attach`-Methode an den Kontext angefügt wurde.|
|[Get](#get)|Gibt einen Zeiger auf den Scheduler zurück, der dem aufrufenden Kontext zugeordnet ist, auch als aktueller Planer bezeichnet.|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Gibt die aktuelle Anzahl virtueller Prozessoren für den Scheduler zurück, der dem aufrufenden Kontext zugeordnet ist.|
|[GetPolicy](#getpolicy)|Gibt eine Kopie der Richtlinie zurück, mit der der aktuelle Scheduler erstellt wurde.|
|[Id](#id)|Gibt einen eindeutigen Bezeichner für den aktuellen Scheduler zurück.|
|[IsAvailableLocation](#isavailablelocation)|Bestimmt, ob ein angegebener Speicherort im aktuellen Scheduler verfügbar ist.|
|[RegisterShutdownEvent](#registershutdownevent)|Bewirkt, dass das an den `_ShutdownEvent`-Parameter übergebenen Windows-Ereignis Handle signalisiert wird, wenn der dem aktuellen Kontext zugeordnete Scheduler heruntergefahren und selbst zerstört wird. Zum Zeitpunkt der Signalisierung des Ereignisses ist die gesamte Arbeit, die für den Scheduler geplant war, abgeschlossen. Mehrere Shutdown-Ereignisse können über diese Methode registriert werden.|
|[ScheduleTask](#scheduletask)|Ist überladen. Plant eine leichte Aufgabe innerhalb des Planers, der dem aufrufenden Kontext zugeordnet ist. Die leichte Aufgabe wird in einer Zeit Plan Gruppe platziert, die von der Laufzeit bestimmt wird. Die Version, die den-Parameter annimmt `_Placement` bewirkt, dass die Aufgabe an der angegebenen Position für die Ausführung verzerrt wird.|

## <a name="remarks"></a>Hinweise

Wenn kein Planer (siehe [Scheduler](scheduler-class.md)) vorhanden ist, der dem aufrufenden Kontext zugeordnet ist, führen viele Methoden in der `CurrentScheduler` Klasse zu einer Anlage des Standard Planers des Prozesses. Dies kann auch bedeuten, dass der Standard Planer des Prozesses während eines solchen Aufrufes erstellt wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CurrentScheduler`

## <a name="requirements"></a>Voraussetzungen

**Header:** ConcRT. h

**Namespace:** Parallelität

## <a name="create"></a> Create

Erstellt einen neuen Scheduler, dessen Verhalten durch den `_Policy`-Parameter beschrieben und an den aufrufenden Kontext angefügt wird. Der neu erstellte Scheduler wird zum aktuellen Planer für den aufrufenden Kontext.

```cpp
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parameter

*_Policy*<br/>
Die Scheduler-Richtlinie, die das Verhalten des neu erstellten Schedulers beschreibt.

### <a name="remarks"></a>Hinweise

Die Anlage des Schedulers an den aufrufenden Kontext fügt implizit einen Verweis Zähler für den Planer ein.

Nachdem ein Scheduler mit der `Create`-Methode erstellt wurde, müssen Sie zu einem beliebigen Zeitpunkt in der Zukunft die [CurrentScheduler::D Etach](#detach) -Methode abrufen, damit das Scheduler heruntergefahren werden kann.

Wenn diese Methode von einem Kontext aufgerufen wird, der bereits an einen anderen Planer angefügt ist, wird der vorhandene Planer als vorheriger Planer gespeichert, und der neu erstellte Scheduler wird zum aktuellen Scheduler. Wenn Sie die `CurrentScheduler::Detach`-Methode zu einem späteren Zeitpunkt aufzurufen, wird der vorherige Scheduler als aktueller Planer wieder hergestellt.

Diese Methode kann eine Vielzahl von Ausnahmen auslösen, einschließlich [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) und [Invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a>CreateScheduleGroup

Erstellt eine neue Zeit Plan Gruppe innerhalb des Planers, der dem aufrufenden Kontext zugeordnet ist. Die Version, die den-Parameter annimmt `_Placement` bewirkt, dass Tasks innerhalb der neu erstellten Zeit Plan Gruppe für die Ausführung an der durch diesen Parameter angegebenen Position verzerrt werden.

```cpp
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>Parameter

*_Placement*<br/>
Ein Verweis auf einen Speicherort, an dem die Tasks innerhalb der Zeit Plan Gruppe für die Ausführung bei unberücksichtigt werden.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die neu erstellte Zeit Plan Gruppe. Für dieses `ScheduleGroup` Objekt wurde ein anfänglicher Verweis Zähler eingefügt.

### <a name="remarks"></a>Hinweise

Diese Methode führt dazu, dass der Standardplaner des Prozesses erstellt und/oder an den aufrufenden Kontext angefügt wird, wenn derzeit dem aufrufenden Kontext kein Planer zugeordnet ist.

Sie müssen die [releasemethode](schedulegroup-class.md#release) in einer Zeit Plan Gruppe aufrufen, wenn Sie mit der Planung der Arbeit daran gearbeitet haben. Der Scheduler zerstört die Zeit Plan Gruppe, wenn alle Arbeiten in der Warteschlange abgeschlossen wurden.

Beachten Sie, dass Sie, wenn Sie diesen Planer explizit erstellt haben, alle Verweise auf Zeit Plan Gruppen freigeben müssen, bevor Sie den Verweis auf den Scheduler freigeben, indem Sie den aktuellen Kontext davon trennen.

## <a name="detach"></a>Trennen

Trennt den aktuellen Scheduler vom aufrufenden Kontext und stellt den zuvor angefügten Planer als aktuellen Scheduler wieder her, falls vorhanden. Nachdem diese Methode zurückgegeben wurde, wird der aufrufenden Kontext vom Scheduler verwaltet, der zuvor mit der `CurrentScheduler::Create`-oder `Scheduler::Attach`-Methode an den Kontext angefügt wurde.

```cpp
static void __cdecl Detach();
```

### <a name="remarks"></a>Hinweise

Die `Detach`-Methode entfernt implizit einen Verweis Zähler aus dem Scheduler.

Wenn kein Scheduler an den aufrufenden Kontext angefügt ist, wird beim Aufrufen dieser Methode eine [scheduler_not_attached](scheduler-not-attached-class.md) Ausnahme ausgelöst.

Wenn Sie diese Methode aus einem Kontext aufrufen, der von einem Scheduler verwendet und verwaltet wird, oder einen Kontext, der mit einer anderen Methode als der [Scheduler:: Attach](scheduler-class.md#attach) -Methode oder der [CurrentScheduler:: Create](#create) -Methode angefügt wurde, wird eine [improper_scheduler_detach](improper-scheduler-detach-class.md) Ausnahme ausgelöst.

## <a name="get"></a>Erhalten

Gibt einen Zeiger auf den Scheduler zurück, der dem aufrufenden Kontext zugeordnet ist, auch als aktueller Planer bezeichnet.

```cpp
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Scheduler, der dem aufrufenden Kontext (dem aktuellen Scheduler) zugeordnet ist.

### <a name="remarks"></a>Hinweise

Diese Methode führt dazu, dass der Standardplaner des Prozesses erstellt und/oder an den aufrufenden Kontext angefügt wird, wenn derzeit dem aufrufenden Kontext kein Planer zugeordnet ist. Auf dem `Scheduler` Objekt, das von dieser Methode zurückgegeben wird, wird kein zusätzlicher Verweis eingefügt.

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors

Gibt die aktuelle Anzahl virtueller Prozessoren für den Scheduler zurück, der dem aufrufenden Kontext zugeordnet ist.

```cpp
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>Rückgabewert

Wenn ein Planer dem aufrufenden Kontext zugeordnet ist, entspricht dies der aktuellen Anzahl von virtuellen Prozessoren für diesen Scheduler. Andernfalls wird der Wert `-1`.

### <a name="remarks"></a>Hinweise

Diese Methode führt nicht zu einer planeranlage, wenn der aufrufenden Kontext nicht bereits einem Zeit Planungs Modul zugeordnet ist.

Der Rückgabewert dieser Methode ist eine sofortige Stichprobe der Anzahl virtueller Prozessoren für den Scheduler, der dem aufrufenden Kontext zugeordnet ist. Dieser Wert kann veraltet sein, sobald er zurückgegeben wird.

## <a name="getpolicy"></a>GetPolicy

Gibt eine Kopie der Richtlinie zurück, mit der der aktuelle Scheduler erstellt wurde.

```cpp
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>Rückgabewert

Eine Kopie der Richtlinie, mit der der aktuelle Scheduler erstellt wurde.

### <a name="remarks"></a>Hinweise

Diese Methode führt dazu, dass der Standardplaner des Prozesses erstellt und/oder an den aufrufenden Kontext angefügt wird, wenn derzeit dem aufrufenden Kontext kein Planer zugeordnet ist.

## <a name="id"></a>Name

Gibt einen eindeutigen Bezeichner für den aktuellen Scheduler zurück.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Rückgabewert

Wenn ein Scheduler dem aufrufenden Kontext zugeordnet ist, ein eindeutiger Bezeichner für diesen Scheduler; Andernfalls wird der Wert `-1`.

### <a name="remarks"></a>Hinweise

Diese Methode führt nicht zu einer planeranlage, wenn der aufrufenden Kontext nicht bereits einem Zeit Planungs Modul zugeordnet ist.

## <a name="isavailablelocation"></a>IsAvailableLocation

Bestimmt, ob ein angegebener Speicherort im aktuellen Scheduler verfügbar ist.

```cpp
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>Parameter

*_Placement*<br/>
Ein Verweis auf den Speicherort, zu dem der aktuelle Scheduler abgefragt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt an, ob der durch das `_Placement`-Argument angegebene Speicherort im aktuellen Planer verfügbar ist.

### <a name="remarks"></a>Hinweise

Diese Methode führt nicht zu einer planeranlage, wenn der aufrufenden Kontext nicht bereits einem Zeit Planungs Modul zugeordnet ist.

Beachten Sie, dass der Rückgabewert eine sofortige Stichprobe dafür ist, ob der angegebene Speicherort verfügbar ist. Wenn mehrere Planer vorhanden sind, kann die dynamische Ressourcenverwaltung Ressourcen von Zeit Planungs Modulen jederzeit hinzufügen oder entfernen. Wenn dies der Fall ist, kann die Verfügbarkeit des angegebenen Standorts geändert werden.

## <a name="registershutdownevent"></a>RegisterShutdownEvent

Bewirkt, dass das an den `_ShutdownEvent`-Parameter übergebenen Windows-Ereignis Handle signalisiert wird, wenn der dem aktuellen Kontext zugeordnete Scheduler heruntergefahren und selbst zerstört wird. Zum Zeitpunkt der Signalisierung des Ereignisses ist die gesamte Arbeit, die für den Scheduler geplant war, abgeschlossen. Mehrere Shutdown-Ereignisse können über diese Methode registriert werden.

```cpp
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>Parameter

*_ShutdownEvent*<br/>
Ein Handle für ein Windows-Ereignis Objekt, das von der Laufzeit signalisiert wird, wenn der dem aktuellen Kontext zugeordnete Scheduler heruntergefahren und selbst zerstört wird.

### <a name="remarks"></a>Hinweise

Wenn kein Scheduler an den aufrufenden Kontext angefügt ist, wird beim Aufrufen dieser Methode eine [scheduler_not_attached](scheduler-not-attached-class.md) Ausnahme ausgelöst.

## <a name="scheduletask"></a>ScheduleTask

Plant eine leichte Aufgabe innerhalb des Planers, der dem aufrufenden Kontext zugeordnet ist. Die leichte Aufgabe wird in einer Zeit Plan Gruppe platziert, die von der Laufzeit bestimmt wird. Die Version, die den-Parameter annimmt `_Placement` bewirkt, dass die Aufgabe an der angegebenen Position für die Ausführung verzerrt wird.

```cpp
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```

### <a name="parameters"></a>Parameter

*_Proc*<br/>
Ein Zeiger auf die Funktion, die ausgeführt wird, um den Text der einfachen Aufgabe auszuführen.

*_Data*<br/>
Ein void-Zeiger auf die Daten, die als Parameter an den Textkörper der Aufgabe übergeben werden.

*_Placement*<br/>
Ein Verweis auf einen Speicherort, an dem die leichte Aufgabe für die Ausführung bei unberücksichtigt wird.

### <a name="remarks"></a>Hinweise

Diese Methode führt dazu, dass der Standardplaner des Prozesses erstellt und/oder an den aufrufenden Kontext angefügt wird, wenn derzeit dem aufrufenden Kontext kein Planer zugeordnet ist.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[Scheduler-Klasse](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[Aufgabenplanung](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
