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
ms.openlocfilehash: ccd82b5c5112bc322717f2b58d79d4c8f34f5bbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368177"
---
# <a name="ischeduler-structure"></a>IScheduler-Struktur

Eine Schnittstelle zu der Abstraktion eines Arbeitsplaners. Der Ressourcen-Manager der Concurrency Runtime kommuniziert mithilfe dieser Schnittstelle mit Arbeitsplanern.

## <a name="syntax"></a>Syntax

```cpp
struct IScheduler;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IScheduler::AddVirtualProcessors](#addvirtualprocessors)|Stellt einen Planer mit einer Reihe virtueller Prozessorwurzeln für seine Verwendung bereit. Jede `IVirtualProcessorRoot` Schnittstelle stellt das Recht dar, einen einzelnen Thread auszuführen, der Arbeiten im Auftrag des Planers ausführen kann.|
|[IScheduler::GetId](#getid)|Gibt einen eindeutigen Bezeichner für den Planer zurück.|
|[IScheduler::GetPolicy](#getpolicy)|Gibt eine Kopie der Richtlinie des Planers zurück. Weitere Informationen zu Planerrichtlinien finden Sie unter [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Benachrichtigt diesen Planer, dass die Hardwarethreads, die durch den `ppVirtualProcessorRoots` Satz virtueller Prozessorwurzeln im Array dargestellt werden, jetzt von anderen Planern verwendet werden.|
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Benachrichtigt diesen Planer, dass die Hardwarethreads, die durch den `ppVirtualProcessorRoots` Satz virtueller Prozessorwurzeln im Array dargestellt werden, nicht von anderen Planern verwendet werden.|
|[IScheduler::RemoveVirtualProcessors](#removevirtualprocessors)|Initiiert das Entfernen von virtuellen Prozessorwurzeln, die zuvor diesem Planer zugewiesen wurden.|
|[IScheduler::Statistik](#statistics)|Enthält Informationen zu den Ankunfts- und Abschlussraten von Aufgaben und zur Änderung der Warteschlangenlänge für einen Planer.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie einen benutzerdefinierten Planer implementieren, der mit dem Ressourcen-Manager `IScheduler` kommuniziert, sollten Sie eine Implementierung der Schnittstelle bereitstellen. Diese Schnittstelle ist ein Ende eines zweiseitigen Kommunikationskanals zwischen einem Planer und dem Ressourcen-Manager. Das andere Ende wird `IResourceManager` `ISchedulerProxy` durch die und Schnittstellen dargestellt, die vom Ressourcen-Manager implementiert werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IScheduler`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="ischeduleraddvirtualprocessors-method"></a><a name="addvirtualprocessors"></a>IScheduler::AddVirtualProcessors-Methode

Stellt einen Planer mit einer Reihe virtueller Prozessorwurzeln für seine Verwendung bereit. Jede `IVirtualProcessorRoot` Schnittstelle stellt das Recht dar, einen einzelnen Thread auszuführen, der Arbeiten im Auftrag des Planers ausführen kann.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parameter

*ppVirtualProcessorRoots*<br/>
Ein Array `IVirtualProcessorRoot` von Schnittstellen, die die virtuellen Prozessorwurzeln darstellen, die dem Planer hinzugefügt werden.

*count*<br/>
Die Anzahl `IVirtualProcessorRoot` der Schnittstellen im Array.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager `AddVirtualProcessor` ruft die Methode auf, um einem Planer einen anfänglichen Satz virtueller Prozessorwurzeln zu gewähren. Es könnte auch die Methode aufrufen, um dem Planer virtuelle Prozessorwurzeln hinzuzufügen, wenn Ressourcen zwischen Planern neu ausbalanciert werden.

## <a name="ischedulergetid-method"></a><a name="getid"></a>IScheduler::GetId-Methode

Gibt einen eindeutigen Bezeichner für den Planer zurück.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Ganzzahlbezeichner.

### <a name="remarks"></a>Bemerkungen

Sie sollten die [GetSchedulerId-Funktion](concurrency-namespace-functions.md) verwenden, um einen eindeutigen Bezeichner für das Objekt zu erhalten, das die `IScheduler` Schnittstelle implementiert, bevor Sie die Schnittstelle als Parameter für Methoden verwenden, die vom Ressourcen-Manager bereitgestellt werden. Es wird erwartet, dass Sie `GetId` denselben Bezeichner zurückgeben, wenn die Funktion aufgerufen wird.

Ein Bezeichner, der aus einer anderen Quelle abgerufen wird, kann zu einem undefinierten Verhalten führen.

## <a name="ischedulergetpolicy-method"></a><a name="getpolicy"></a>IScheduler::GetPolicy-Methode

Gibt eine Kopie der Richtlinie des Planers zurück. Weitere Informationen zu Planerrichtlinien finden Sie unter [SchedulerPolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine Kopie der Richtlinie des Planers.

## <a name="ischedulernotifyresourcesexternallybusy-method"></a><a name="notifyresourcesexternallybusy"></a>IScheduler::NotifyResourcesExternallyBusy-Methode

Benachrichtigt diesen Planer, dass die Hardwarethreads, die durch den `ppVirtualProcessorRoots` Satz virtueller Prozessorwurzeln im Array dargestellt werden, jetzt von anderen Planern verwendet werden.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parameter

*ppVirtualProcessorRoots*<br/>
Ein Array `IVirtualProcessorRoot` von Schnittstellen, die den Hardwarethreads zugeordnet sind, auf denen andere Planer beschäftigt sind.

*count*<br/>
Die Anzahl `IVirtualProcessorRoot` der Schnittstellen im Array.

### <a name="remarks"></a>Bemerkungen

Es ist möglich, dass ein bestimmter Hardwarethread mehreren Planern gleichzeitig zugewiesen wird. Ein Grund dafür könnte sein, dass nicht genügend Hardwarethreads auf dem System vorhanden sind, um die Mindestparallelität für alle Planer zu erfüllen, ohne Ressourcen gemeinsam zu nutzen. Eine weitere Möglichkeit besteht darin, dass Ressourcen vorübergehend anderen Planern zugewiesen werden, wenn der besitzende Planer sie nicht verwendet, und alle virtuellen Prozessorwurzeln auf diesem Hardwarethread deaktiviert werden.

Die Abonnementebene eines Hardwarethreads wird durch die Anzahl der abonnierten Threads und aktivierten virtuellen Prozessorwurzeln bezeichnet, die diesem Hardwarethread zugeordnet sind. Aus der Sicht eines bestimmten Planers ist die externe Abonnementebene eines Hardwarethreads der Teil des Abonnements, zu dem andere Planer beitragen. Benachrichtigungen, dass Ressourcen extern ausgelastet sind, werden an einen Planer gesendet, wenn die externe Abonnementebene für einen Hardwarethread von Null in den positiven Bereich verschoben wird.

Benachrichtigungen über diese Methode werden nur an Planer gesendet, `MinConcurrency` die über eine Richtlinie verfügen, bei der der Wert für den Richtlinienschlüssel dem Wert für den `MaxConcurrency` Richtlinienschlüssel entspricht. Weitere Informationen zu Planerrichtlinien finden Sie unter [SchedulerPolicy](schedulerpolicy-class.md).

Ein Planer, der für Benachrichtigungen qualifiziert ist, ruft beim Erstellen eine Reihe von Anfangsbenachrichtigungen ab und informiert ihn darüber, ob die Ressourcen, die er gerade zugewiesen wurde, extern ausgelastet oder im Leerlauf sind.

## <a name="ischedulernotifyresourcesexternallyidle-method"></a><a name="notifyresourcesexternallyidle"></a>IScheduler::NotifyResourcesExternallyIdle-Methode

Benachrichtigt diesen Planer, dass die Hardwarethreads, die durch den `ppVirtualProcessorRoots` Satz virtueller Prozessorwurzeln im Array dargestellt werden, nicht von anderen Planern verwendet werden.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parameter

*ppVirtualProcessorRoots*<br/>
Ein Array `IVirtualProcessorRoot` von Schnittstellen, die Mithardwarethreads zugeordnet sind, bei denen andere Planer im Leerlauf sind.

*count*<br/>
Die Anzahl `IVirtualProcessorRoot` der Schnittstellen im Array.

### <a name="remarks"></a>Bemerkungen

Es ist möglich, dass ein bestimmter Hardwarethread mehreren Planern gleichzeitig zugewiesen wird. Ein Grund dafür könnte sein, dass nicht genügend Hardwarethreads auf dem System vorhanden sind, um die Mindestparallelität für alle Planer zu erfüllen, ohne Ressourcen gemeinsam zu nutzen. Eine weitere Möglichkeit besteht darin, dass Ressourcen vorübergehend anderen Planern zugewiesen werden, wenn der besitzende Planer sie nicht verwendet, und alle virtuellen Prozessorwurzeln auf diesem Hardwarethread deaktiviert werden.

Die Abonnementebene eines Hardwarethreads wird durch die Anzahl der abonnierten Threads und aktivierten virtuellen Prozessorwurzeln bezeichnet, die diesem Hardwarethread zugeordnet sind. Aus der Sicht eines bestimmten Planers ist die externe Abonnementebene eines Hardwarethreads der Teil des Abonnements, zu dem andere Planer beitragen. Benachrichtigungen, dass Ressourcen extern ausgelastet sind, werden an einen Planer gesendet, wenn die externe Abonnementebene für einen Hardwarethread von einem vorherigen positiven Wert auf Null fällt.

Benachrichtigungen über diese Methode werden nur an Planer gesendet, `MinConcurrency` die über eine Richtlinie verfügen, bei der der Wert für den Richtlinienschlüssel dem Wert für den `MaxConcurrency` Richtlinienschlüssel entspricht. Weitere Informationen zu Planerrichtlinien finden Sie unter [SchedulerPolicy](schedulerpolicy-class.md).

Ein Planer, der für Benachrichtigungen qualifiziert ist, ruft beim Erstellen eine Reihe von Anfangsbenachrichtigungen ab und informiert ihn darüber, ob die Ressourcen, die er gerade zugewiesen wurde, extern ausgelastet oder im Leerlauf sind.

## <a name="ischedulerremovevirtualprocessors-method"></a><a name="removevirtualprocessors"></a>IScheduler::RemoveVirtualProcessors-Methode

Initiiert das Entfernen von virtuellen Prozessorwurzeln, die zuvor diesem Planer zugewiesen wurden.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parameter

*ppVirtualProcessorRoots*<br/>
Ein Array `IVirtualProcessorRoot` von Schnittstellen, die die zu entfernenden virtuellen Prozessorwurzeln darstellen.

*count*<br/>
Die Anzahl `IVirtualProcessorRoot` der Schnittstellen im Array.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager `RemoveVirtualProcessors` ruft die Methode auf, um einen Satz virtueller Prozessorwurzeln von einem Planer zurückzunehmen. Es wird erwartet, dass der Planer die [Remove-Methode](iexecutionresource-structure.md#remove) auf jeder Schnittstelle aufruft, wenn dies mit den Stammverzeichnissen des virtuellen Prozessors erfolgt. Verwenden Sie `IVirtualProcessorRoot` keine Schnittstelle, nachdem `Remove` Sie die Methode darauf aufgerufen haben.

Der `ppVirtualProcessorRoots` Parameter verweist auf ein Array von Schnittstellen. Unter den zu entfernenden virtuellen Prozessorwurzeln können die Roots nie aktiviert `Remove` werden, um sofort mit der Methode zurückgegeben zu werden. Die Wurzeln, die aktiviert wurden und entweder Arbeit ausführen oder deaktiviert wurden und auf das Eintreffen der Arbeit warten, sollten asynchron zurückgegeben werden. Der Planer muss jeden Versuch unternehmen, den Stamm des virtuellen Prozessors so schnell wie möglich zu entfernen. Das Verzögern des Entfernens der virtuellen Prozessorwurzeln kann zu einer unbeabsichtigten Überzeichnung innerhalb des Planers führen.

## <a name="ischedulerstatistics-method"></a><a name="statistics"></a>IScheduler::Statistikmethode

Enthält Informationen zu den Ankunfts- und Abschlussraten von Aufgaben und zur Änderung der Warteschlangenlänge für einen Planer.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parameter

*pTaskCompletionRate*<br/>
Die Anzahl der Vorgänge, die vom Planer seit dem letzten Aufruf dieser Methode abgeschlossen wurden.

*pTaskArrivalRate*<br/>
Die Anzahl der Vorgänge, die seit dem letzten Aufruf dieser Methode im Planer angekommen sind.

*pNumberOfTasksEnqueued*<br/>
Die Gesamtanzahl der Vorgänge in allen Planerwarteschlangen.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Ressourcen-Manager aufgerufen, um Statistiken für einen Planer zu sammeln. Die hier gesammelten Statistiken werden verwendet, um dynamische Feedbackalgorithmen zu entwickeln, um zu bestimmen, wann es sinnvoll ist, dem Planer weitere Ressourcen zuzuweisen und wann Ressourcen entfernt werden. Die vom Planer bereitgestellten Werte können optimistisch sein und müssen nicht unbedingt die aktuelle Anzahl genau widerspiegeln.

Sie sollten diese Methode implementieren, wenn der Ressourcen-Manager Feedback zu z. B. beim Eintreffen von Aufgaben verwenden soll, um zu bestimmen, wie Die Ressource zwischen Dem Planer und anderen beim Ressourcen-Manager registrierten Planern ausgeglichen werden kann. Wenn Sie keine Statistiken sammeln möchten, können `DynamicProgressFeedback` Sie `DynamicProgressFeedbackDisabled` den Richtlinienschlüssel auf den Wert in der Richtlinie des Planers festlegen, und der Ressourcen-Manager ruft diese Methode nicht auf dem Planer auf.

In Ermangelung statistischer Informationen verwendet der Ressourcen-Manager Hardwarethreadabonnementebenen, um Ressourcenzuweisungs- und Migrationsentscheidungen zu treffen. Weitere Informationen zu Abonnementebenen finden Sie unter [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy-Klasse](schedulerpolicy-class.md)<br/>
[IExecutionContext-Struktur](iexecutioncontext-structure.md)<br/>
[IThreadProxy-Struktur](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot-Struktur](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager-Struktur](iresourcemanager-structure.md)
