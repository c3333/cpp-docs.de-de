---
title: Scheduler-Klasse
ms.date: 11/04/2016
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
ms.openlocfilehash: 77ad876b8352ab1ae86fde622b05712ec5f2cea9
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274718"
---
# <a name="scheduler-class"></a>Scheduler-Klasse

Stellt eine Abstraktion für einen Concurrency Runtime-Planer dar.

## <a name="syntax"></a>Syntax

```cpp
class Scheduler;
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Scheduler](#ctor)|Ein Objekt der- `Scheduler` Klasse kann nur mit Factorymethoden oder implizit erstellt werden.|
|[~ Scheduler-Dekonstruktor](#dtor)|Ein Objekt der `Scheduler` Klasse wird implizit zerstört, wenn alle externen Verweise darauf nicht mehr vorhanden sind.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Anfügen](#attach)|Fügt den Scheduler an den aufrufenden Kontext an. Nachdem diese Methode zurückgegeben wurde, wird der aufrufenden Kontext vom Scheduler verwaltet, und der Scheduler wird zum aktuellen Scheduler.|
|[Erstellen](#create)|Erstellt einen neuen Scheduler, dessen Verhalten durch den- `_Policy` Parameter beschrieben wird, einen anfänglichen Verweis auf den Scheduler platziert und einen Zeiger darauf zurückgibt.|
|[CreateScheduleGroup](#createschedulegroup)|Überladen. Erstellt eine neue Zeit Plan Gruppe im Scheduler. Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass Tasks innerhalb der neu erstellten Zeit Plan Gruppe an dem durch diesen Parameter angegebenen Speicherort ausgeführt werden.|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Gibt die aktuelle Anzahl von virtuellen Prozessoren für den Planer zurück.|
|[GetPolicy](#getpolicy)|Gibt eine Kopie der Richtlinie zurück, mit der der Scheduler erstellt wurde.|
|[Id](#id)|Gibt einen eindeutigen Bezeichner für den Scheduler zurück.|
|[IsAvailableLocation](#isavailablelocation)|Bestimmt, ob ein angegebener Speicherort im Scheduler verfügbar ist.|
|[Referenz](#reference)|Erhöht den Verweis Zähler für den Scheduler.|
|[RegisterShutdownEvent](#registershutdownevent)|Bewirkt, dass das Windows-Ereignis handle, das im- `_Event` Parameter übergeben wird, signalisiert wird, wenn der Scheduler heruntergefahren und selbst zerstört wird. Zum Zeitpunkt der Signalisierung des Ereignisses ist die gesamte Arbeit, die für den Scheduler geplant war, abgeschlossen. Mehrere Shutdown-Ereignisse können über diese Methode registriert werden.|
|[Release](#release)|Dekremente den Verweis Zähler für den Planer.|
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|Setzt die standardmäßige Scheduler-Richtlinie auf den Standardwert der Laufzeit zurück. Wenn ein Standard Planer das nächste Mal erstellt wird, werden die Standardrichtlinien Einstellungen der Laufzeit verwendet.|
|[ScheduleTask](#scheduletask)|Überladen. Plant eine leichte Aufgabe innerhalb des Zeit Planungs Moduls. Die leichte Aufgabe wird in einer Zeit Plan Gruppe platziert, die von der Laufzeit bestimmt wird. Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass die Aufgabe an der angegebenen Position für die Ausführung verzerrt wird.|
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|Ermöglicht die Verwendung einer benutzerdefinierten Richtlinie zum Erstellen des Standard Planers. Diese Methode kann nur aufgerufen werden, wenn innerhalb des Prozesses kein Standard Planer vorhanden ist. Nachdem eine Standard Richtlinie festgelegt wurde, bleibt Sie bis zum nächsten gültigen Aufrufen der `SetDefaultSchedulerPolicy` Methode oder der Methode [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) wirksam.|

## <a name="remarks"></a>Bemerkungen

Der Concurrency Runtime Scheduler verwendet Ausführungs Kontexte, die den Ausführungs Kontexten des Betriebssystems (z. b. einem Thread) zugeordnet sind, um die von der Anwendung in die Warteschlange eingereihte Arbeit auszuführen. Die Parallelitäts Stufe eines Zeit Planungs Moduls ist gleich der Anzahl der virtuellen Prozessoren, die ihm von der Ressourcen-Manager gewährt wurden. Ein virtueller Prozessor ist eine Abstraktion für eine Verarbeitungsressource und wird einem Hardwarethread des zugrunde liegenden Systems zugeordnet. Nur ein einzelner Planerkontext kann jeweils auf einem virtuellen Prozessor ausgeführt werden.

Mit dem Concurrency Runtime wird ein Standard Planer pro Prozess erstellt, um parallele Arbeiten auszuführen. Außerdem können Sie Ihre eigenen Scheduler-Instanzen erstellen und mit dieser Klasse bearbeiten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Scheduler`

## <a name="requirements"></a>Anforderungen

**Header:** ConcRT. h

**Namespace:** Parallelität

## <a name="attach"></a><a name="attach"></a> An

Fügt den Scheduler an den aufrufenden Kontext an. Nachdem diese Methode zurückgegeben wurde, wird der aufrufenden Kontext vom Scheduler verwaltet, und der Scheduler wird zum aktuellen Scheduler.

```cpp
virtual void Attach() = 0;
```

### <a name="remarks"></a>Bemerkungen

Durch das Anfügen eines Zeit Planungs Moduls wird implizit ein Verweis auf den Scheduler platziert.

Zu einem späteren Zeitpunkt müssen Sie die [CurrentScheduler::D Etach](currentscheduler-class.md#detach) -Methode abrufen, damit das Scheduler heruntergefahren werden kann.

Wenn diese Methode von einem Kontext aufgerufen wird, der bereits an einen anderen Planer angefügt ist, wird der vorhandene Planer als vorheriger Planer gespeichert, und der neu erstellte Scheduler wird zum aktuellen Scheduler. Wenn Sie die- `CurrentScheduler::Detach` Methode zu einem späteren Zeitpunkt aufzurufen, wird der vorherige Scheduler als aktueller Planer wieder hergestellt.

Diese Methode löst eine [Improper_scheduler_attach](improper-scheduler-attach-class.md) Ausnahme aus, wenn dieser Scheduler der aktuelle Planer des aufrufenden Kontexts ist.

## <a name="create"></a><a name="create"></a> Erstellen

Erstellt einen neuen Scheduler, dessen Verhalten durch den- `_Policy` Parameter beschrieben wird, einen anfänglichen Verweis auf den Scheduler platziert und einen Zeiger darauf zurückgibt.

```cpp
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parameter

*_Policy*<br/>
Die Scheduler-Richtlinie, die das Verhalten des neu erstellten Zeit Planungs Moduls beschreibt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf einen neu erstellten Scheduler. `Scheduler`Für dieses Objekt wurde ein anfänglicher Verweis Zähler eingefügt.

### <a name="remarks"></a>Bemerkungen

Nachdem ein Scheduler mit der- `Create` Methode erstellt wurde, müssen Sie die- `Release` Methode zu einem bestimmten Zeitpunkt in der Zukunft abrufen, um den anfänglichen Verweis Zähler zu entfernen und das Herunterfahren des Schedulers zuzulassen.

Ein mit dieser Methode erstellter Scheduler ist nicht an den aufrufenden Kontext angefügt. Sie kann mithilfe der [Attach](#attach) -Methode an einen Kontext angefügt werden.

Diese Methode kann eine Vielzahl von Ausnahmen auslösen, einschließlich [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) und [Invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a><a name="createschedulegroup"></a> CreateScheduleGroup

Erstellt eine neue Zeit Plan Gruppe im Scheduler. Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass Tasks innerhalb der neu erstellten Zeit Plan Gruppe an dem durch diesen Parameter angegebenen Speicherort ausgeführt werden.

```cpp
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>Parameter

*_Placement*<br/>
Ein Verweis auf einen Speicherort, an dem die Tasks innerhalb der Zeit Plan Gruppe für die Ausführung bei unberücksichtigt werden.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die neu erstellte Zeit Plan Gruppe. `ScheduleGroup`Für dieses Objekt wurde ein anfänglicher Verweis Zähler eingefügt.

### <a name="remarks"></a>Bemerkungen

Sie müssen die [releasemethode](schedulegroup-class.md#release) in einer Zeit Plan Gruppe aufrufen, wenn Sie mit der Planung der Arbeit daran gearbeitet haben. Der Scheduler zerstört die Zeit Plan Gruppe, wenn alle Arbeiten in der Warteschlange abgeschlossen wurden.

Beachten Sie, dass Sie, wenn Sie diesen Planer explizit erstellt haben, alle Verweise auf Zeit Plan Gruppen freigeben müssen, bevor Sie die Verweise auf den Scheduler freigeben.

## <a name="getnumberofvirtualprocessors"></a><a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors

Gibt die aktuelle Anzahl von virtuellen Prozessoren für den Planer zurück.

```cpp
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Anzahl der virtuellen Prozessoren für den Scheduler.

## <a name="getpolicy"></a><a name="getpolicy"></a> GetPolicy

Gibt eine Kopie der Richtlinie zurück, mit der der Scheduler erstellt wurde.

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine Kopie der Richtlinie, mit der der Scheduler erstellt wurde.

## <a name="id"></a><a name="id"></a> Name

Gibt einen eindeutigen Bezeichner für den Scheduler zurück.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Bezeichner für den Scheduler.

## <a name="isavailablelocation"></a><a name="isavailablelocation"></a> IsAvailableLocation

Bestimmt, ob ein angegebener Speicherort im Scheduler verfügbar ist.

```cpp
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>Parameter

*_Placement*<br/>
Ein Verweis auf den Speicherort, zu dem der Scheduler abgefragt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Hinweis darauf, ob der durch das-Argument angegebene Speicherort `_Placement` im Scheduler verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass der Rückgabewert eine sofortige Stichprobe dafür ist, ob der angegebene Speicherort verfügbar ist. Wenn mehrere Planer vorhanden sind, kann die dynamische Ressourcenverwaltung Ressourcen von Zeit Planungs Modulen jederzeit hinzufügen oder entfernen. Wenn dies der Fall ist, kann die Verfügbarkeit des angegebenen Standorts geändert werden.

## <a name="reference"></a><a name="reference"></a> Angabe

Erhöht den Verweis Zähler für den Scheduler.

```cpp
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>Rückgabewert

Der neu inkrementierte Verweis Zähler.

### <a name="remarks"></a>Bemerkungen

Dies wird normalerweise verwendet, um die Lebensdauer des Zeit Planungs Moduls für die Komposition zu verwalten. Wenn der Verweis Zähler eines Zeit Planungs Moduls auf 0 (null) fällt, wird der Scheduler nach Abschluss der gesamten Arbeit im Zeit Planungs Modul heruntergefahren und die Struktur selbst zerlegt.

Die-Methode löst eine [Improper_scheduler_reference](improper-scheduler-reference-class.md) Ausnahme aus, wenn der Verweis Zähler vor dem Aufrufen der `Reference` -Methode 0 (null) war und der Aufruf von einem Kontext erfolgt, der nicht im Besitz des Zeit Planungs Moduls ist.

## <a name="registershutdownevent"></a><a name="registershutdownevent"></a> RegisterShutdownEvent

Bewirkt, dass das Windows-Ereignis handle, das im- `_Event` Parameter übergeben wird, signalisiert wird, wenn der Scheduler heruntergefahren und selbst zerstört wird. Zum Zeitpunkt der Signalisierung des Ereignisses ist die gesamte Arbeit, die für den Scheduler geplant war, abgeschlossen. Mehrere Shutdown-Ereignisse können über diese Methode registriert werden.

```cpp
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>Parameter

*_Event*<br/>
Ein Handle für ein Windows-Ereignis Objekt, das von der Laufzeit signalisiert wird, wenn der Scheduler heruntergefahren und selbst zerstört wird.

## <a name="release"></a><a name="release"></a> Abgabe

Dekremente den Verweis Zähler für den Planer.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Rückgabewert

Der neu dekrementierte Verweis Zähler.

### <a name="remarks"></a>Bemerkungen

Dies wird normalerweise verwendet, um die Lebensdauer des Zeit Planungs Moduls für die Komposition zu verwalten. Wenn der Verweis Zähler eines Zeit Planungs Moduls auf 0 (null) fällt, wird der Scheduler nach Abschluss der gesamten Arbeit im Zeit Planungs Modul heruntergefahren und die Struktur selbst zerlegt.

## <a name="resetdefaultschedulerpolicy"></a><a name="resetdefaultschedulerpolicy"></a> ResetDefaultSchedulerPolicy

Setzt die standardmäßige Scheduler-Richtlinie auf den Standardwert der Laufzeit zurück. Wenn ein Standard Planer das nächste Mal erstellt wird, werden die Standardrichtlinien Einstellungen der Laufzeit verwendet.

```cpp
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode kann aufgerufen werden, während ein Standard Planer innerhalb des Prozesses vorhanden ist. Dies wirkt sich nicht auf die Richtlinie des vorhandenen Standard Planers aus. Wenn der Standard Planer jedoch heruntergefahren wird und ein neuer Standardwert zu einem späteren Zeitpunkt erstellt werden soll, verwendet der neue Scheduler die Standardrichtlinien Einstellungen der Laufzeit.

## <a name="scheduler"></a><a name="ctor"></a> Scheduler

Ein Objekt der- `Scheduler` Klasse kann nur mit Factorymethoden oder implizit erstellt werden.

```cpp
Scheduler();
```

### <a name="remarks"></a>Bemerkungen

Der Standard Planer des Prozesses wird implizit erstellt, wenn Sie viele der Lauf Zeitfunktionen verwenden, die erfordern, dass ein Scheduler an den aufrufenden Kontext angefügt wird. Methoden in der- `CurrentScheduler` Klasse und Funktionen der ppl-und Agents-Schichten führen in der Regel eine implizite Anlage aus.

Sie können einen Scheduler auch explizit über die- `CurrentScheduler::Create` Methode oder die- `Scheduler::Create` Methode erstellen.

## <a name="scheduler"></a><a name="dtor"></a> ~ Scheduler

Ein Objekt der `Scheduler` Klasse wird implizit zerstört, wenn alle externen Verweise darauf nicht mehr vorhanden sind.

```cpp
virtual ~Scheduler();
```

## <a name="scheduletask"></a><a name="scheduletask"></a> ScheduleTask

Plant eine leichte Aufgabe innerhalb des Zeit Planungs Moduls. Die leichte Aufgabe wird in einer Zeit Plan Gruppe platziert, die von der Laufzeit bestimmt wird. Die Version, die den-Parameter annimmt, `_Placement` bewirkt, dass die Aufgabe an der angegebenen Position für die Ausführung verzerrt wird.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```

### <a name="parameters"></a>Parameter

*_Proc*<br/>
Ein Zeiger auf die Funktion, die ausgeführt wird, um den Text der einfachen Aufgabe auszuführen.

*_Data*<br/>
Ein void-Zeiger auf die Daten, die als Parameter an den Textkörper der Aufgabe übergeben werden.

*_Placement*<br/>
Ein Verweis auf einen Speicherort, an dem die leichte Aufgabe für die Ausführung bei unberücksichtigt wird.

## <a name="setdefaultschedulerpolicy"></a><a name="setdefaultschedulerpolicy"></a> SetDefaultSchedulerPolicy

Ermöglicht die Verwendung einer benutzerdefinierten Richtlinie zum Erstellen des Standard Planers. Diese Methode kann nur aufgerufen werden, wenn innerhalb des Prozesses kein Standard Planer vorhanden ist. Nachdem eine Standard Richtlinie festgelegt wurde, bleibt Sie bis zum nächsten gültigen Aufrufen der `SetDefaultSchedulerPolicy` Methode oder der Methode [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) wirksam.

```cpp
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parameter

*_Policy*<br/>
Die Richtlinie, die als standardmäßige Scheduler-Richtlinie festgelegt werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn die- `SetDefaultSchedulerPolicy` Methode aufgerufen wird, wenn bereits ein Standard Planer innerhalb des Prozesses vorhanden ist, löst die Laufzeit eine [default_scheduler_exists](default-scheduler-exists-class.md) Ausnahme aus.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[Scheduler-Klasse](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[Aufgabenplanung](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
