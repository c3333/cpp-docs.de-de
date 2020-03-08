---
title: IScheduler-Struktur
ms.date: 11/04/2016
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
ms.openlocfilehash: cd7b04b0dc5ca1bc496ce87a6459d00ed5813bf7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854157"
---
# <a name="ischeduler-structure"></a>IScheduler-Struktur

Eine Schnittstelle zu der Abstraktion eines Arbeitsplaners. Der Ressourcen-Manager der Concurrency Runtime kommuniziert mithilfe dieser Schnittstelle mit Arbeitsplanern.

## <a name="syntax"></a>Syntax

```cpp
struct IScheduler;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IScheduler:: addvirtualprocessor](#addvirtualprocessors)|Stellt einen Planer mit einem Satz virtueller Prozessor Stämme für seine Verwendung bereit. Jede `IVirtualProcessorRoot`-Schnittstelle stellt das Recht dar, einen einzelnen Thread auszuführen, der im Auftrag des Planers Arbeit ausführen kann.|
|[IScheduler:: GetId](#getid)|Gibt einen eindeutigen Bezeichner für den Scheduler zurück.|
|[IScheduler:: GetPolicy](#getpolicy)|Gibt eine Kopie der Richtlinie des Schedulers zurück. Weitere Informationen zu Scheduler-Richtlinien finden Sie unter [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler:: NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Benachrichtigt diesen Planer, dass die Hardwarethreads, die durch die Gruppe der virtuellen Prozessor Stämme im Array `ppVirtualProcessorRoots` dargestellt werden, nun von anderen Zeit Planungs Modulen verwendet werden.|
|[IScheduler:: notifyresourcesexternallyidle](#notifyresourcesexternallyidle)|Benachrichtigt diesen Planer, dass die Hardwarethreads, die durch den Satz virtueller Prozessor Stämme im Array `ppVirtualProcessorRoots` dargestellt werden, von anderen Zeit Planungs Modulen nicht verwendet werden.|
|[IScheduler:: removevirtualprocessor](#removevirtualprocessors)|Initiiert das Entfernen virtueller Prozessor Stämme, die zuvor diesem Scheduler zugeordnet wurden.|
|[IScheduler:: Statistics](#statistics)|Stellt Informationen im Zusammenhang mit den Eingangs-und Abschluss Raten der Aufgabe sowie eine Änderung der Warteschlangen Länge für einen Scheduler bereit.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie einen benutzerdefinierten Planer implementieren, der mit dem Ressourcen-Manager kommuniziert, sollten Sie eine Implementierung der `IScheduler`-Schnittstelle bereitstellen. Diese Schnittstelle ist ein Ende eines bidirektionalen Kommunikationskanals zwischen einem Scheduler und dem Ressourcen-Manager. Das andere Ende wird durch die `IResourceManager`-und `ISchedulerProxy`-Schnittstellen dargestellt, die vom Ressourcen-Manager implementiert werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IScheduler`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concrtrm. h

**Namespace:** Parallelität

## <a name="addvirtualprocessors"></a>IScheduler:: addvirtualprocessor-Methode

Stellt einen Planer mit einem Satz virtueller Prozessor Stämme für seine Verwendung bereit. Jede `IVirtualProcessorRoot`-Schnittstelle stellt das Recht dar, einen einzelnen Thread auszuführen, der im Auftrag des Planers Arbeit ausführen kann.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parameter

*ppvirtualprocessorroots*<br/>
Ein Array von `IVirtualProcessorRoot` Schnittstellen, die die dem Scheduler hinzugefügten virtuellen Prozessor Stämme darstellen.

*count*<br/>
Die Anzahl der `IVirtualProcessorRoot` Schnittstellen im Array.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager ruft die `AddVirtualProcessor`-Methode auf, um einem Planer einen anfänglichen Satz virtueller Prozessor Stämme zu gewähren. Sie kann auch die-Methode aufrufen, um dem Scheduler virtuelle Prozessor Stämme hinzuzufügen, wenn er Ressourcen Zwischenzeit Planungs Modulen umgleicht.

## <a name="getid"></a>IScheduler:: GetId-Methode

Gibt einen eindeutigen Bezeichner für den Scheduler zurück.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine eindeutige ganzzahlige Kennung.

### <a name="remarks"></a>Bemerkungen

Sie sollten die [GetSchedulerId-](concurrency-namespace-functions.md) Funktion verwenden, um einen eindeutigen Bezeichner für das Objekt zu erhalten, das die `IScheduler`-Schnittstelle implementiert, bevor Sie die-Schnittstelle als Parameter für Methoden verwenden, die vom Ressourcen-Manager bereitgestellt werden. Es wird erwartet, dass Sie denselben Bezeichner zurückgeben, wenn die `GetId`-Funktion aufgerufen wird.

Ein Bezeichner aus einer anderen Quelle kann zu undefiniertem Verhalten führen.

## <a name="getpolicy"></a>IScheduler:: GetPolicy-Methode

Gibt eine Kopie der Richtlinie des Schedulers zurück. Weitere Informationen zu Scheduler-Richtlinien finden Sie unter [SchedulerPolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine Kopie der Richtlinie des Schedulers.

## <a name="notifyresourcesexternallybusy"></a>IScheduler:: NotifyResourcesExternallyBusy-Methode

Benachrichtigt diesen Planer, dass die Hardwarethreads, die durch die Gruppe der virtuellen Prozessor Stämme im Array `ppVirtualProcessorRoots` dargestellt werden, nun von anderen Zeit Planungs Modulen verwendet werden.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parameter

*ppvirtualprocessorroots*<br/>
Ein Array von `IVirtualProcessorRoot` Schnittstellen, die den Hardwarethreads zugeordnet sind, auf denen andere Planer ausgelastet sind.

*count*<br/>
Die Anzahl der `IVirtualProcessorRoot` Schnittstellen im Array.

### <a name="remarks"></a>Bemerkungen

Es ist möglich, dass ein bestimmter Hardware Thread gleichzeitig mehreren Zeit Planungs Modulen zugewiesen wird. Ein Grund hierfür könnte sein, dass auf dem System nicht genügend Hardwarethreads vorhanden sind, um die minimale Parallelität für alle Planer zu erfüllen, ohne Ressourcen gemeinsam zu nutzen. Eine weitere Möglichkeit besteht darin, dass Ressourcen temporär anderen Zeit Planungs Modulen zugewiesen werden, wenn Sie vom besitzenden Planer nicht verwendet werden, und zwar über alle virtuellen Prozessor Stämme auf dem deaktivierten Hardware Thread.

Die Abonnement Ebene eines Hardware Threads wird durch die Anzahl der abonnierten und aktivierten virtuellen Prozessor Stämme gekennzeichnet, die mit diesem Hardware Thread verknüpft sind. Aus Sicht eines bestimmten Zeit Planungs Moduls ist die externe Abonnement Ebene eines Hardware Threads der Teil des Abonnements, zu dem andere Planer beitragen. Benachrichtigungen, dass Ressourcen extern ausgelastet sind, werden an einen Planer gesendet, wenn die externe Abonnement Stufe für einen Hardware Thread von NULL in positives Gebiet verschoben wird.

Benachrichtigungen über diese Methode werden nur an Planer gesendet, die über eine Richtlinie verfügen, bei der der Wert für den `MinConcurrency` Richtlinien Schlüssel gleich dem Wert für den `MaxConcurrency` Richtlinien Schlüssel ist. Weitere Informationen zu Scheduler-Richtlinien finden Sie unter [SchedulerPolicy](schedulerpolicy-class.md).

Ein Scheduler, der für Benachrichtigungen qualifiziert ist, erhält bei der Erstellung eine Reihe von anfänglichen Benachrichtigungen, die darauf hingewiesen werden, ob die soeben zugewiesenen Ressourcen extern ausgelastet sind oder sich im Leerlauf befinden.

## <a name="notifyresourcesexternallyidle"></a>IScheduler:: notifyresourcesexternallyidle-Methode

Benachrichtigt diesen Planer, dass die Hardwarethreads, die durch den Satz virtueller Prozessor Stämme im Array `ppVirtualProcessorRoots` dargestellt werden, von anderen Zeit Planungs Modulen nicht verwendet werden.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parameter

*ppvirtualprocessorroots*<br/>
Ein Array von `IVirtualProcessorRoot` Schnittstellen, die Hardwarethreads zugeordnet sind, auf denen andere Zeit Planungs Module sich im Leerlauf befinden.

*count*<br/>
Die Anzahl der `IVirtualProcessorRoot` Schnittstellen im Array.

### <a name="remarks"></a>Bemerkungen

Es ist möglich, dass ein bestimmter Hardware Thread gleichzeitig mehreren Zeit Planungs Modulen zugewiesen wird. Ein Grund hierfür könnte sein, dass auf dem System nicht genügend Hardwarethreads vorhanden sind, um die minimale Parallelität für alle Planer zu erfüllen, ohne Ressourcen gemeinsam zu nutzen. Eine weitere Möglichkeit besteht darin, dass Ressourcen temporär anderen Zeit Planungs Modulen zugewiesen werden, wenn Sie vom besitzenden Planer nicht verwendet werden, und zwar über alle virtuellen Prozessor Stämme auf dem deaktivierten Hardware Thread.

Die Abonnement Ebene eines Hardware Threads wird durch die Anzahl der abonnierten und aktivierten virtuellen Prozessor Stämme gekennzeichnet, die mit diesem Hardware Thread verknüpft sind. Aus Sicht eines bestimmten Zeit Planungs Moduls ist die externe Abonnement Ebene eines Hardware Threads der Teil des Abonnements, zu dem andere Planer beitragen. Benachrichtigungen, dass Ressourcen extern ausgelastet sind, werden an einen Planer gesendet, wenn die externe Abonnement Ebene für einen Hardware Thread von einem vorherigen positiven Wert auf 0 (null) fällt.

Benachrichtigungen über diese Methode werden nur an Planer gesendet, die über eine Richtlinie verfügen, bei der der Wert für den `MinConcurrency` Richtlinien Schlüssel gleich dem Wert für den `MaxConcurrency` Richtlinien Schlüssel ist. Weitere Informationen zu Scheduler-Richtlinien finden Sie unter [SchedulerPolicy](schedulerpolicy-class.md).

Ein Scheduler, der für Benachrichtigungen qualifiziert ist, erhält bei der Erstellung eine Reihe von anfänglichen Benachrichtigungen, die darauf hingewiesen werden, ob die soeben zugewiesenen Ressourcen extern ausgelastet sind oder sich im Leerlauf befinden.

## <a name="removevirtualprocessors"></a>IScheduler:: removevirtualprocessor-Methode

Initiiert das Entfernen virtueller Prozessor Stämme, die zuvor diesem Scheduler zugeordnet wurden.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parameter

*ppvirtualprocessorroots*<br/>
Ein Array von `IVirtualProcessorRoot`-Schnittstellen, die die zu entfernenden virtuellen Prozessor Stämme darstellen.

*count*<br/>
Die Anzahl der `IVirtualProcessorRoot` Schnittstellen im Array.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager ruft die `RemoveVirtualProcessors`-Methode auf, um einen Satz virtueller Prozessor Stämme von einem Planer zurück zu nehmen. Der Planer muss die [Remove](iexecutionresource-structure.md#remove) -Methode für jede Schnittstelle aufrufen, wenn dies mit den virtuellen Prozessor Stämmen erfolgt. Verwenden Sie keine `IVirtualProcessorRoot`-Schnittstelle, nachdem Sie die `Remove`-Methode dafür aufgerufen haben.

Der-Parameter `ppVirtualProcessorRoots` verweist auf ein Array von-Schnittstellen. Unter dem Satz der zu entfernenden virtuellen Prozessor Stämme können die Stämme nicht sofort mit der `Remove`-Methode zurückgegeben werden. Die Stamm Elemente, die aktiviert wurden und entweder Arbeiten ausführen oder deaktiviert wurden und auf das Eintreffen der Arbeit warten, sollten asynchron zurückgegeben werden. Der Planer muss jeden Versuch durchführen, den virtuellen Prozessor Stamm so schnell wie möglich zu entfernen. Das Verzögern der Entfernung der virtuellen Prozessor Stämme kann zu unbeabsichtigtem Überschreiben innerhalb des Planers führen.

## <a name="statistics"></a>IScheduler:: Statistics-Methode

Stellt Informationen im Zusammenhang mit den Eingangs-und Abschluss Raten der Aufgabe sowie eine Änderung der Warteschlangen Länge für einen Scheduler bereit.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parameter

*ptaskcompletionrate*<br/>
Die Anzahl der Aufgaben, die seit dem letzten aufrufungsvorgang durch den Scheduler abgeschlossen wurden.

*ptaskarrivalrate*<br/>
Die Anzahl der Aufgaben, die seit dem letzten aufrufenen aufrufungsmethode im Scheduler eingetroffen sind.

*pnumoftasksenqueued*<br/>
Die Gesamtanzahl der Aufgaben in allen Scheduler-Warteschlangen.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Ressourcen-Manager aufgerufen, um Statistiken für einen Planer zu erfassen. Die hier gesammelten Statistiken werden verwendet, um dynamische Feedback Algorithmen zu erstellen, um zu bestimmen, wann es sinnvoll ist, dem Scheduler mehr Ressourcen zuzuweisen, und wann Ressourcen entfernt werden sollen. Die vom Scheduler bereitgestellten Werte können optimistisch sein und müssen nicht unbedingt die aktuelle Anzahl genau widerspiegeln.

Sie sollten diese Methode implementieren, wenn Sie möchten, dass das Ressourcen-Manager Feedback zu solchen Dingen wie z. b. die Aufgaben Ankunft verwendet, um zu bestimmen, wie die Ressourcen zwischen Ihrem Planer und anderen Zeit Planungs Modulen, die beim Ressourcen-Manager registriert sind, ausgeglichen Wenn Sie keine Statistiken sammeln möchten, können Sie den Richtlinien Schlüssel `DynamicProgressFeedback` auf den Wert festlegen, der in der Richtlinie des Planers `DynamicProgressFeedbackDisabled` ist, und die Ressourcen-Manager ruft diese Methode nicht für Ihren Scheduler auf.

Wenn keine statistischen Informationen vorhanden sind, werden die Ressourcen-Manager Hardware-Thread Abonnement Ebenen verwenden, um die Ressourcen Zuordnung und die Migrationsentscheidungen zu treffen. Weitere Informationen zu Abonnement Ebenen finden Sie unter [IExecutionResource:: currentabonneptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy-Klasse](schedulerpolicy-class.md)<br/>
[IExecutionContext-Struktur](iexecutioncontext-structure.md)<br/>
[IThreadProxy-Struktur](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot-Struktur](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager-Struktur](iresourcemanager-structure.md)
