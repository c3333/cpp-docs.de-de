---
title: Concurrency Runtime im Vergleich zu anderen Parallelitätsmodellen
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
ms.openlocfilehash: 5bc6691f6d0b166bb3084091ee6af70474937568
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855401"
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Concurrency Runtime im Vergleich zu anderen Parallelitätsmodellen

Dieses Dokument beschreibt die Unterschiede zwischen den Funktionen und Programmiermodellen der Concurrency Runtime und anderen Technologien. Wenn Sie verstehen, welche Vorteile die Concurrency Runtime gegenüber anderen Programmiermodellen hat, können Sie die Technologie auswählen, die die Anforderungen der jeweiligen Anwendung am besten erfüllt.

Wenn Sie derzeit ein anderes Programmiermodell verwenden, zum Beispiel Windows Threadpool oder OpenMP, gibt es Situationen, in denen es angebracht sein kann, zu Concurrency Runtime zu migrieren. Das Thema [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) beschreibt zum Beispiel, wann es angebracht sein kann, von OpenMP zu Concurrency Runtime zu migrieren. Wenn Sie die mit der Anwendungsleistung und der aktuellen Debugunterstützung zufrieden sind, ist eine Migration nicht erforderlich.

Sie können die Funktionen und Produktivitätsvorteile der Concurrency Runtime auch als Ergänzung in vorhandenen Anwendungen verwenden, die ein anderes Parallelitätsmodell verwenden. Die Concurrency Runtime garantiert nicht einen Lastenausgleich, wenn mehrere Aufgabenplaner um die gleichen Ressourcen konkurrieren. Wenn sich Arbeitslasten nicht überlappen, ist dieser Effekt minimal.

## <a name="top"></a> Abschnitte

- [Vergleich von präemptiver Planung mit kooperativer Planung](#models)

- [Vergleich der Concurrency Runtime mit der Windows-API](#winapi)

- [Vergleich der Concurrency Runtime mit OpenMP](#openmp)

## <a name="models"></a> Vergleich von präemptiver Planung mit kooperativer Planung

Das präemptive Modell und kooperative Planungsmodelle sind zwei allgemeine Verfahren zum Aktivieren mehrerer Aufgaben zum Freigeben von Ressourcen, z.B. Prozessoren oder Hardwarethreads.

### <a name="preemptive-and-cooperative-scheduling"></a>Präemptive und kooperative Planung

*Präemptive Planung* ist ein prioritätsbasierter Roundrobin-Mechanismus, bei dem Aufgaben nacheinander jeweils für einen bestimmten Zeitraum exklusiven Zugriff auf eine Computerressource erhalten. Präemptive Planung wird häufig in Multitasking-Betriebssystemen wie Windows verwendet. *Kooperative Planung* ist ein Mechanismus, der jeder Aufgabe exklusiven Zugriff auf eine Computer Ressource gibt, bis die Aufgabe abgeschlossen ist oder die Aufgabe den Zugriff auf die Ressource gewährt. Concurrency Runtime verwendet die kooperative Planung zusammen mit dem präemptiven Planer des Betriebssystems, um eine maximale Nutzung der Verarbeitungsressourcen zu erreichen.

### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Unterschiede zwischen präemptiven und kooperativen Planern

Präemptive Planer versuchen, mehreren Threads gleichen Zugriff auf Computerressourcen zu geben, um sicherzustellen, dass jeder Thread ausgeführt wird. Einen fairen Zugriff sicherzustellen ist auf Computern mit vielen Computerressourcen weniger problematisch. Die effiziente Nutzung der Ressourcen sicherzustellen wird jedoch problematisch.

Bei einem präemptiven Kernel-Modus-Planer muss sich die Anwendung bei Planungsentscheidungen auf das Betriebssystem verlassen. Umgekehrt ermöglicht ein kooperativer Benutzermodusplaner dem Anwendungscode, eigene Planungsentscheidungen zu treffen. Da bei kooperativer Planung viele Planungsentscheidungen durch die Anwendung erfolgen können, entfällt ein Großteil des Aufwands der Kernelmodus-Synchronisierung. Ein kooperativer Planer schiebt Planungsentscheidungen in der Regel an den Betriebssystem-Kernel, wenn dieser keine anderen Aufgaben zu planen hat. Ein kooperativer Planer schiebt auch an den Betriebssystem-Planer, wenn ein Blockierungsvorgang vorliegt, der an den Kernel kommuniziert wird, dieser Vorgang aber nicht an den Benutzermodusplaner kommuniziert wird.

### <a name="cooperative-scheduling-and-efficiency"></a>Kooperative Planung und Effizienz

Für einen präemptiven Planer sind Aufgaben mit selber Prioritätsstufe gleich. Ein präemptiver Planer plant Threads gewöhnlich in der Reihenfolge, in der sie erstellt werden. Darüber hinaus gewährt ein präemptiver Planer jedem Thread eine Zeitscheibe in Roundrobin-Weise auf Grundlage der Priorität des Threads. Obwohl dieser Mechanismus Ausgewogenheit bietet (jeder Thread macht Fortschritt), erfolgt dies auf Kosten der Effizienz. Viele rechenintensive Algorithmen erfordern beispielsweise keine Ausgewogenheit. Stattdessen ist es wichtig, dass verwandte Aufgaben in der geringsten Gesamtzeit beendet werden. Durch kooperative Planung kann eine Anwendung Arbeit effizienter planen. Betrachten Sie beispielsweise eine Anwendung mit vielen Threads. Das Planen von Threads, die keine gleichzeitig auszuführenden Ressourcen gemeinsam nutzen, kann den Synchronisierungsaufwand reduzieren und somit die Effizienz steigern. Eine andere effiziente Möglichkeit zum Planen von Aufgaben ist die Ausführung von Pipelines mit Aufgaben (wo jede Aufgabe die Ausgabe der vorherigen Aufgabe bearbeitet) auf dem gleichen Prozessor, sodass die Eingabe jeder Stufe der Pipeline bereits in den Speichercache geladen ist.

### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Verwenden von präemptiver und kooperativer Planung

Kooperative Planung löst nicht alle Planungsprobleme. Beispielsweise können Aufgaben, die nicht genügend an andere Aufgaben abgeben, alle verfügbaren Computerressourcen nutzen und verhindern, dass andere Aufgaben ausgeführt werden. Die Concurrency Runtime verwendet die Effizienzvorteile der kooperativen Planung, um die Ausgewogenheitsgarantien der präemptiven Planung zu ergänzen. Concurrency Runtime bietet standardmäßig einen kooperativen Planer, der einen Arbeitsübernahme-Algorithmus verwendet, um die Arbeit effizient auf die Computerressourcen zu verteilen. Der Concurrency Runtime-Planer hängt jedoch auch von dem präemptiven Planer des Betriebssystems ab, der die Ressourcen zwischen den Anwendungen verteilt. Sie können auch benutzerdefinierte Planer und Planerrichtlinien in den Anwendungen erstellen, um eine präzisere Kontrolle über die Ausführung von Threads zu ermöglichen.

[[Nach oben](#top)]

## <a name="winapi"></a> Vergleich der Concurrency Runtime mit der Windows-API

Die Microsoft Windows Anwendungsprogrammierschnittstelle (API), die in der Regel als Windows-API (und früher als Win32) bezeichnet wird, bietet ein Programmiermodell, das Parallelität in der Anwendung ermöglicht. Die Concurrency Runtime basiert auf der Windows-API und stellt zusätzliche Programmiermodelle bereit, die nicht über das zugrunde liegende Betriebssystem verfügbar sind.

Die Concurrency Runtime basiert auf dem Windows-API-Threadmodell zur Ausführung paralleler Arbeiten. Sie verwendet auch die Windows-API-Speicherverwaltung und lokale Threadspeicher-Mechanismen. Unter Windows 7 und Windows Server 2008 R2 verwendet sie Windows-API-Unterstützung für durch den Benutzer planbare Threads und Computer, die mehr als 64 Hardwarethreads aufweisen. Die Concurrency Runtime erweitert das Windows-API-Modell um einen kooperativen Taskplaner und einen Arbeitsübernahme-Algorithmus, um die Verwendung von Computerressourcen zu maximieren und mehrere gleichzeitige Planerinstanzen zu aktivieren.

### <a name="programming-languages"></a>Programmiersprachen

Die Windows-API verwendet die Programmiersprache C, um das Programmiermodell verfügbar machen. Die Concurrency Runtime stellt eine C++-Programmierschnittstelle bereit, die die neuesten Funktionen der Programmiersprache C++ nutzt. Lambda-Funktionen bieten beispielsweise einen knappen, typsicheren Mechanismus zum Definieren von parallelen Arbeitsfunktionen. Weitere Informationen zu den neuesten C++-Funktionen, die von der Concurrency Runtime verwendet werden, finden Sie unter [Übersicht](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="threads-and-thread-pools"></a>Threads und Threadpools

Der zentrale Parallelitätsmechanismus in der Windows-API ist der Thread. In der Regel verwenden Sie die [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) -Funktion zum Erstellen von Threads. Obwohl Threads relativ einfach zu erstellen sind, weist das Betriebssystem viel Zeit und Ressourcen für deren Verwaltung zu. Obwohl jeder Thread garantiert die gleiche Ausführungszeit wie alle anderen Threads auf gleicher Prioritätsebene erhält, erfordert der zugeordnete Mehraufwand, dass Sie ausreichend große Aufgaben erstellen. Für kleinere oder differenziertere Aufgaben kann der Aufwand, der mit der Parallelität verbunden ist, den Vorteil, dass die Aufgaben parallel ausgeführt werden zunichte machen.

Threadpools sind eine Möglichkeit, die Kosten der Threadverwaltung zu reduzieren. Benutzerdefinierte Threadpools und die Threadpoolimplementierung, die von der Windows-API bereitgestellt wird, ermöglichen kleine Arbeitselemente effizient parallel auszuführen. Der Windows-Threadpool verwaltet die Arbeitselemente in einer FIFO-Warteschlange (First in, First Out). Jedes Arbeitselement wird in der Reihenfolge gestartet, in der es dem Pool hinzugefügt wurde.

Die Concurrency Runtime implementiert einen Arbeitsübernahme-Algorithmus, um den FIFO-Planungsmechanismus zu erweitern. Der Algorithmus verschiebt Aufgaben, die noch nicht gestartet wurden, in Threads, die keine Arbeitselemente mehr haben. Obwohl der Arbeitsübernahme-Algorithmus Arbeitslasten ausgleichen kann, kann er auch dazu führen, dass Arbeitselemente neu angeordnet werden. Diese Neuordnung kann dazu führen, dass ein Arbeitselement in einer anderen Reihenfolge gestartet wird, als es übermittelt wurde. Dies ist hilfreich bei rekursiven Algorithmen, wenn eine bessere Möglichkeit besteht, dass Daten eher von neuen Aufgaben als von alten gemeinsam verwendet werden. Die neuen Elemente zuerst auszuführen bedeutet weniger Cachefehler und möglicherweise weniger Seitenfehler.

Aus der Perspektive des Betriebssystems ist die Arbeitsübernahme unausgewogen. Wenn jedoch eine Anwendung einen Algorithmus oder eine Aufgabe zur parallelen Ausführung implementiert, spielt Ausgewogenheit zwischen untergeordneten Aufgaben nicht immer eine Rolle. Welche Rolle spielt ist, wie schnell die gesamte Aufgabe abgeschlossen wird. Für andere Algorithmen ist FIFO die geeignete Planungsstrategie.

### <a name="behavior-on-various-operating-systems"></a>Verhalten unter verschiedenen Betriebssystemen

Unter Windows XP und Windows Vista verhalten sich Anwendungen, die die Concurrency Runtime verwenden, ähnlich, außer dass die Heap-Leistung unter Windows Vista verbessert wird.

Unter Windows 7 und Windows Server 2008 R2 unterstützt das Betriebssystem Parallelität und Skalierbarkeit. Diese Betriebssysteme unterstützen beispielsweise Computer, die mehr als 64 Hardwarethreads aufweisen. Eine vorhandene Anwendung, die die Windows-API verwendet, muss geändert werden, um diese neuen Funktionen nutzen zu können. Allerdings wird eine Anwendung, die Concurrency Runtime verwendet, automatisch diese Funktionen verwenden und keine Änderungen erfordern.

[base.user-mode_scheduling](/windows/win32/procthread/user-mode-scheduling)

[[Nach oben](#top)]

## <a name="openmp"></a> Vergleich der Concurrency Runtime mit OpenMP

Concurrency Runtime ermöglicht eine Vielzahl von Programmiermodellen. Diese Modelle überlappen oder ergänzen die Modelle von anderen Bibliotheken. In diesem Abschnitt wird die Concurrency Runtime mit [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) verglichen.

Das OpenMP-Programmiermodell wird durch einen offenen Standard definiert und verfügt über klar definierte Bindungen zu den Programmiersprachen Fortran und C/C++. Version 2.0 und 2.5 von OpenMP sind hervorragend für parallele Algorithmen geeignet, die iterativ sind. Sie führen eine parallele Iteration über einem Array von Daten durch. OpenMP ist am effizientesten, wenn der Grad an Parallelität vorgegeben ist und mit den verfügbaren Ressourcen auf dem System übereinstimmt. Das OpenMP-Modell eignet sich besonders gut für High Performance Computing, wo sehr große Berechnungsprobleme auf die Verarbeitungsressourcen eines einzelnen Computers verteilt werden. In diesem Szenario ist die Hardwareumgebung bekannt und der Entwickler kann davon ausgehen, exklusiven Zugriff auf Computerressourcen zu haben, wenn der Algorithmus ausgeführt wird.

Andere, weniger eingeschränkte Computerumgebungen können dagegen weniger gut für OpenMP geeignet sein. Rekursive Probleme (wie z.B. der Quicksort-Algorithmus oder die Suche in einer Datenbaumstruktur) sind mit OpenMP schwieriger zu implementieren. Die Concurrency Runtime ergänzt die Funktionen von OpenMP durch die Bereitstellung der [Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) und [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md). Die Concurrency Runtime bietet im Gegensatz zu OpenMP einen dynamische Planer, der sich den verfügbaren Ressourcen anpasst und den Grad der Parallelität bei wechselnder Arbeitslast ändert.

Viele der Funktionen in der Concurrency Runtime können erweitert werden. Sie können auch vorhandene Funktionen zu neuen Funktionen kombinieren. Da OpenMP Compilerdirektiven benötigt, kann es nicht problemlos erweitert werden.

Weitere Informationen zum Vergleich von Concurrency Runtime und OpenMP und wie vorhandener OpenMP-Code für die Verwendung der Concurrency Runtime migriert wird finden Sie unter [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).

[[Nach oben](#top)]

## <a name="see-also"></a>Weitere Informationen

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[Übersicht](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Asynchrone Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
