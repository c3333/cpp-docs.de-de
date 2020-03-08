---
title: ScheduleGroup-Klasse
ms.date: 11/04/2016
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
ms.openlocfilehash: 8686b5ef0906e3188a1e683d1190bbe6124cd19e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867128"
---
# <a name="schedulegroup-class"></a>ScheduleGroup-Klasse

Stellt die Abstraktion für eine Planungsgruppe dar. In Planungsgruppen werden Sätze verwandter Arbeitsaufgaben organisiert, die von einer gemeinsamen Planung profitieren. Die kann entweder zeitlich durch das Ausführen einer anderen Aufgabe in der gleichen Gruppe vor dem Wechsel in eine andere Gruppe, oder räumlich durch das Ausführen mehrerer Elemente innerhalb der gleichen Gruppe auf dem gleichen NUMA-Knoten oder physischem Socket geschehen.

## <a name="syntax"></a>Syntax

```cpp
class ScheduleGroup;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[~ ScheduleGroup-Dekonstruktor](#dtor)||

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Id](#id)|Gibt einen Bezeichner für die Planungsgruppe zurück, der innerhalb des Planers eindeutig ist, zu dem die Gruppe gehört.|
|[Referenz](#reference)|Inkrementiert den Verweiszähler dieser Planergruppe.|
|[Release](#release)|Dekrementiert den Verweiszähler dieser Planergruppe.|
|[ScheduleTask](#scheduletask)|Plant eine einfache Aufgabe innerhalb der Planungsgruppe.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ScheduleGroup`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

**Namespace:** Parallelität

## <a name="id"></a>Name

Gibt einen Bezeichner für die Planungsgruppe zurück, der innerhalb des Planers eindeutig ist, zu dem die Gruppe gehört.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Bezeichner für die Zeit Plan Gruppe, der innerhalb des Planers eindeutig ist, zu dem die Gruppe gehört.

## <a name="operator_delete"></a>Operator löschen

Ein `ScheduleGroup` Objekt wird von der Laufzeit intern zerstört, wenn alle externen Verweise darauf freigegeben werden. Sie kann nicht explizit gelöscht werden.

```cpp
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
const char *,
    int);
```

### <a name="parameters"></a>Parameter

*_PObject*<br/>
Ein Zeiger auf das Objekt, das gelöscht werden soll.

## <a name="reference"></a>Angabe

Inkrementiert den Verweiszähler dieser Planergruppe.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Rückgabewert

Der neu inkrementierte Verweis Zähler.

### <a name="remarks"></a>Bemerkungen

Dies wird normalerweise verwendet, um die Lebensdauer der Zeit Plan Gruppe für die Komposition zu verwalten. Wenn der Verweis Zähler einer Zeit Plan Gruppe auf 0 (null) fällt, wird die Zeit Plan Gruppe von der Laufzeit gelöscht. Eine Zeit Plan Gruppe, die mit der [CurrentScheduler:: aufgabenschedulegroup](currentscheduler-class.md#createschedulegroup) -Methode erstellt wurde, oder die [Scheduler:: up ScheduleGroup](scheduler-class.md#createschedulegroup) -Methode beginnt mit einem Verweis Zähler von 1.

## <a name="release"></a>Abgabe

Dekrementiert den Verweiszähler dieser Planergruppe.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Rückgabewert

Der neu dekrementierte Verweis Zähler.

### <a name="remarks"></a>Bemerkungen

Dies wird normalerweise verwendet, um die Lebensdauer der Zeit Plan Gruppe für die Komposition zu verwalten. Wenn der Verweis Zähler einer Zeit Plan Gruppe auf 0 (null) fällt, wird die Zeit Plan Gruppe von der Laufzeit gelöscht. Nachdem Sie die `Release`-Methode so oft wie möglich, um den Verweis Zähler für die Erstellung und alle zusätzlichen Verweise, die mit der `Reference`-Methode platziert wurden, aufgerufen haben, können Sie die Zeit Plan Gruppe nicht weiter verwenden. Dies führt zu undefiniertem Verhalten.

Eine Zeit Plan Gruppe ist einer bestimmten Scheduler-Instanz zugeordnet. Sie müssen sicherstellen, dass alle Verweise auf die Zeit Plan Gruppe freigegeben werden, bevor alle Verweise auf den Scheduler freigegeben werden, da letztere möglicherweise dazu führt, dass der Scheduler zerstört wird. Andernfalls führt dies zu einem nicht definierten Verhalten.

## <a name="dtor"></a>~ ScheduleGroup

```cpp
virtual ~ScheduleGroup();
```

## <a name="scheduletask"></a>ScheduleTask

Plant eine einfache Aufgabe innerhalb der Planungsgruppe.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>Parameter

*_Proc*<br/>
Ein Zeiger auf die Funktion, die ausgeführt wird, um den Text der einfachen Aufgabe auszuführen.

*_Data*<br/>
Ein void-Zeiger auf die Daten, die als Parameter an den Textkörper der Aufgabe übergeben werden.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die `ScheduleTask`-Methode aufrufen, wird implizit ein Verweis Zähler für die Zeit Plan Gruppe eingefügt, der nach der Ausführung des Tasks von der Laufzeit zu einem passenden Zeitpunkt entfernt wird.

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[CurrentScheduler-Klasse](currentscheduler-class.md)<br/>
[Scheduler-Klasse](scheduler-class.md)<br/>
[Aufgabenplanung](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
