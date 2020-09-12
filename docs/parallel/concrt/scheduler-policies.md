---
title: Planerrichtlinien
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: a962c00d23c41d97087e705d395b601afc7b1910
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042042"
---
# <a name="scheduler-policies"></a>Planerrichtlinien

In diesem Dokument wird die Rolle der Scheduler-Richtlinien in der Concurrency Runtime beschrieben. Eine *Scheduler-Richtlinie* steuert die Strategie, die der Scheduler beim Verwalten von Aufgaben verwendet. Betrachten Sie z. b. eine Anwendung, für die einige Aufgaben ausgeführt werden müssen, `THREAD_PRIORITY_NORMAL` und andere Tasks, die bei ausgeführt werden müssen `THREAD_PRIORITY_HIGHEST` .  Sie können zwei Scheduler-Instanzen erstellen: einen, der die `ContextPriority` Richtlinie angibt, `THREAD_PRIORITY_NORMAL` und einen anderen, der die gleiche Richtlinie angibt `THREAD_PRIORITY_HIGHEST` .

Mithilfe von Scheduler-Richtlinien können Sie die verfügbaren Verarbeitungs Ressourcen aufteilen und jedem Scheduler einen festgelegten Satz von Ressourcen zuweisen. Stellen Sie sich beispielsweise einen parallelen Algorithmus vor, der nicht über vier Prozessoren skaliert werden kann. Sie können eine Scheduler-Richtlinie erstellen, die die Aufgaben einschränkt, sodass nicht mehr als vier Prozessoren gleichzeitig verwendet werden.

> [!TIP]
> Der Concurrency Runtime stellt einen Standard Planer bereit. Daher müssen Sie keinen in Ihrer Anwendung erstellen. Da der Taskplaner Sie bei der Feinabstimmung der Leistung Ihrer Anwendungen unterstützt, empfehlen wir Ihnen, mit der [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) oder der [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md) zu beginnen, wenn Sie mit der Concurrency Runtime noch nicht vertraut sind.

Bei Verwendung der Parallelität [:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create), [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create)oder [Concurrency:: Scheduler:: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) -Methode zum Erstellen einer planerinstanz geben Sie ein [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) -Objekt an, das eine Auflistung von Schlüssel-Wert-Paaren enthält, die das Verhalten des Schedulers angeben. Der `SchedulerPolicy` Konstruktor nimmt eine Variable Anzahl von Argumenten an. Das erste Argument ist die Anzahl der Richtlinien Elemente, die Sie angeben. Die übrigen Argumente sind Schlüssel-Wert-Paare für jedes Policy-Element. Im folgenden Beispiel wird ein- `SchedulerPolicy` Objekt erstellt, das drei Richtlinien Elemente angibt. Die Laufzeit verwendet Standardwerte für die nicht angegebenen Richtlinien Schlüssel.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

Die Enumeration " [parallelcurrency::P olicyelementkey](reference/concurrency-namespace-enums.md#policyelementkey) " definiert die dem Taskplaner zugeordneten Richtlinien Schlüssel. In der folgenden Tabelle werden die Richtlinien Schlüssel und der Standardwert beschrieben, der von der Common Language Runtime für diese verwendet wird.

| Richtlinien Schlüssel | BESCHREIBUNG | Standardwert |
|--|--|--|
| `SchedulerKind` | Ein [parallelcurrency:: SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) -Wert, der den Typ der Threads angibt, die zum Planen von Tasks verwendet werden sollen. | `ThreadScheduler` (verwenden Sie normale Threads). Dies ist der einzige gültige Wert für diesen Schlüssel. |
| `MaxConcurrency` | Ein- **`unsigned int`** Wert, der die maximale Anzahl von Parallelitäts Ressourcen angibt, die vom Scheduler verwendet werden. | [Parallelität:: MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources) |
| `MinConcurrency` | Ein- **`unsigned int`** Wert, der die Mindestanzahl von Parallelitäts Ressourcen angibt, die vom Scheduler verwendet werden. | `1` |
| `TargetOversubscriptionFactor` | Ein- **`unsigned int`** Wert, der angibt, wie viele Threads den einzelnen Verarbeitungs Ressourcen zuzuordnen sind. | `1` |
| `LocalContextCacheSize` | Ein- **`unsigned int`** Wert, der die maximale Anzahl von Kontexten angibt, die in der lokalen Warteschlange jedes virtuellen Prozessors zwischengespeichert werden können. | `8` |
| `ContextStackSize` | Ein- **`unsigned int`** Wert, der die Größe des Stapels in Kilobyte angibt, die für jeden Kontext reserviert werden soll. | `0` (Standard Stapelgröße verwenden) |
| `ContextPriority` | Ein- **`int`** Wert, der die Thread Priorität jedes Kontexts angibt. Dies kann ein beliebiger Wert sein, den Sie an [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) oder übergeben können `INHERIT_THREAD_PRIORITY` . | `THREAD_PRIORITY_NORMAL` |
| `SchedulingProtocol` | Ein " [parallelcurrency:: SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) "-Wert, der den zu verwendenden Planungs Algorithmus angibt. | `EnhanceScheduleGroupLocality` |
| `DynamicProgressFeedback` | Ein [parallelcurrency::D ynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) -Wert, der angibt, ob Ressourcen entsprechend den Statistik basierten Statusinformationen ausgeglichen werden sollen.<br /><br /> **Hinweis** Legen Sie diese Richtlinie nicht auf fest, `ProgressFeedbackDisabled` da Sie für die Verwendung durch die Laufzeit reserviert ist. | `ProgressFeedbackEnabled` |

Jeder Planer verwendet seine eigene Richtlinie, wenn er Tasks plant. Die Richtlinien, die einem Scheduler zugeordnet sind, wirken sich nicht auf das Verhalten anderer Planer aus. Außerdem können Sie die Scheduler-Richtlinie nicht ändern, nachdem Sie das-Objekt erstellt haben `Scheduler` .

> [!IMPORTANT]
> Verwenden Sie nur Scheduler-Richtlinien, um die Attribute für die von der Laufzeit erstellten Threads zu steuern. Ändern Sie nicht die Thread Affinität oder Priorität der Threads, die von der Laufzeit erstellt werden, da dies zu undefiniertem Verhalten führen kann.

Die Laufzeit erstellt einen Standard Planer für Sie, wenn Sie nicht explizit eine erstellen. Wenn Sie den Standard Planer in Ihrer Anwendung verwenden möchten, aber eine Richtlinie angeben möchten, die dieser Planer verwenden soll, müssen Sie die Methode " [parallelcurrency:: Scheduler:: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) " aufrufen, bevor Sie parallele Arbeiten planen. Wenn Sie die-Methode nicht aufzurufen `Scheduler::SetDefaultSchedulerPolicy` , verwendet die Common Language Runtime die Standardrichtlinien Werte aus der-Tabelle.

Verwenden Sie die [Concurrency:: CurrentScheduler:: GetPolicy](reference/currentscheduler-class.md#getpolicy) -Methode und die [Concurrency:: Scheduler:: GetPolicy](reference/scheduler-class.md#getpolicy) -Methode, um eine Kopie der Scheduler-Richtlinie abzurufen. Die Richtlinien Werte, die Sie von diesen Methoden erhalten, können sich von den Richtlinien Werten unterscheiden, die Sie beim Erstellen des Planers angeben.

## <a name="example"></a>Beispiel

Beispiele, in denen bestimmte Scheduler-Richtlinien zum Steuern des Verhaltens des Zeit Planungs Moduls verwendet werden, finden Sie unter Gewusst [wie: Angeben spezifischer Scheduler-Richtlinien](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) und Gewusst [wie: Erstellen von Agents, die bestimmte planerrichtlinien verwenden](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>Weitere Informationen

[Aufgabenplanung](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Vorgehensweise: Angeben spezifischer Scheduler-Richtlinien](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Gewusst wie: Erstellen von Agents, die bestimmte planerrichtlinien verwenden](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
