---
title: Übersicht über die Concurrency Runtime
ms.date: 11/19/2018
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
ms.openlocfilehash: 11035f9e202d964ae91378560b9244cde6d1828b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194614"
---
# <a name="overview-of-the-concurrency-runtime"></a>Übersicht über die Concurrency Runtime

Dieses Dokument enthält eine Übersicht über die Concurrency Runtime. Es beschreibt die Vorteile der Concurrency Runtime, wann sie verwendet wird und wie ihre Komponenten miteinander und mit dem Betriebssystem und den Anwendungen interagieren.

## <a name="sections"></a><a name="top"></a>Strecken

Dieses Dokument enthält folgende Abschnitte:

- [Concurrency Runtime Implementierungs Verlauf](#dlls)

- [Warum eine Laufzeit für die Parallelität wichtig ist](#runtime)

- [Aufbau](#architecture)

- [C++-Lambdaausdrücke](#lambda)

- [Anforderungen](#requirements)

## <a name="concurrency-runtime-implementation-history"></a><a name="dlls"></a>Concurrency Runtime Implementierungs Verlauf

In Visual Studio 2010 bis 2013 war der Concurrency Runtime in msvcr100.dll über msvcr120.dll integriert.  Als das ucrt-Refactoring in Visual Studio 2015 aufgetreten ist, wurde diese DLL in drei Teile umgestaltet:

- ucrtbase.dll – C-API, ausgeliefert in Windows 10 und Serviced kompatible via Windows Update:

- vcruntime140.dll – Compiler-Unterstützungsfunktionen und eh-Laufzeit, ausgeliefert über Visual Studio

- concrt140.dll – Concurrency Runtime, ausgeliefert über Visual Studio. Erforderlich für parallele Container und Algorithmen wie z `concurrency::parallel_for` . b.. Außerdem erfordert die STL, dass diese dll unter Windows XP die Synchronisierungs primitiven unterstützt, da Windows XP nicht über Bedingungs Variablen verfügt.

In Visual Studio 2015 und höher ist der Concurrency Runtime-Taskplaner nicht mehr der Planer für die Aufgabenklasse und verwandte Typen in „ppltasks.h“. Diese Typen verwenden jetzt den Windows-Threadpool für eine bessere Leistung und Interoperabilität mit Windows-Synchronisierungsprimitiven.

## <a name="why-a-runtime-for-concurrency-is-important"></a><a name="runtime"></a>Warum eine Laufzeit für Parallelität wichtig ist

Eine Laufzeit für die Parallelität bietet die Einheitlichkeit und Vorhersagbarkeit für Anwendungen und Anwendungskomponenten, die gleichzeitig ausgeführt werden. Zwei Beispiele für die Vorteile der Concurrency Runtime sind *kooperative Aufgaben Planung* und *kooperative Blockierung*.

Die Concurrency Runtime verwendet einen kooperativen Aufgabenplaner, der einen Arbeitsübernahme-Algorithmus implementiert, um die Arbeit effizient auf die Computerressourcen zu verteilen. Betrachten Sie beispielsweise eine Anwendung mit zwei Threads, die beide von der gleichen Laufzeit verwaltet werden. Wenn ein Thread die geplante Aufgabe abgeschlossen hat, kann dieser die Arbeit des anderen Threads auslagern. Dieser Mechanismus gleicht die gesamte Arbeitsauslastung der Anwendung aus.

Die Concurrency Runtime stellt außerdem Synchronisierungsprimitiven zur Verfügung, die die kooperative Blockierung zum Synchronisieren des Zugriffs auf die Ressourcen nutzen. Betrachten Sie z. B. eine Aufgabe, bei der der exklusive Zugriff auf eine freigegebene Ressource gewährleistet sein muss. Durch die kooperative Blockierung kann die Laufzeit das verbleibende Quantum verwenden, um eine andere Aufgabe ausführen, während die erste Aufgabe auf die Ressource wartet. Durch diesen Mechanismus wird die maximale Auslastung der Computerressourcen hochgestuft.

[Nach[oben](#top)]

## <a name="architecture"></a><a name="architecture"></a> Architektur

Die Concurrency Runtime ist in vier Komponenten unterteilt: die Parallel Patterns Library (PPL), die Asynchronous Agents Library, der Taskplaner und der Ressourcen-Manager. Diese Komponenten befinden sich zwischen dem Betriebssystem und den Anwendungen. Die folgende Abbildung zeigt, wie die Concurrency Runtime-Komponenten zwischen dem Betriebssystem und den Anwendungen interagieren:

**Architektur von Concurrency Runtime**

![Die Architektur von Concurrency Runtime](../../parallel/concrt/media/concurrencyrun.png "Die Architektur von Concurrency Runtime")

> [!IMPORTANT]
> Die Taskplaner-und Ressourcen-Manager Komponenten sind nicht in einer universelle Windows-Plattform-app (UWP) verfügbar, oder wenn Sie die Aufgaben Klasse oder andere Typen in "ppltasks. h" verwenden.

Der Concurrency Runtime ist hochgradig *zusammensetzbar*, d. h., Sie können vorhandene Funktionen kombinieren, um mehr zu tun. Die Concurrency Runtime kombiniert viele Funktionen aus Komponenten auf niedrigerer Ebene, wie z. B. parallele Algorithmen.

Die Concurrency Runtime stellt außerdem Synchronisierungsprimitiven zur Verfügung, die die kooperative Blockierung zum Synchronisieren des Zugriffs auf die Ressourcen nutzen. Weitere Informationen zu diesen Synchronisierungs primitiven finden Sie unter [Synchronisierungs Datenstrukturen](../../parallel/concrt/synchronization-data-structures.md).

Die folgenden Abschnitte bieten einen kurzen Überblick über die jeweilige Komponente und deren Verwendung.

### <a name="parallel-patterns-library"></a>Parallel Patterns Library

Die Parallel Patterns Library (PPL) bietet allgemeine Container und Algorithmen zum Ausführen der differenzierten Parallelität. Die PPL ermöglicht eine *imperative Daten Parallelität* durch Bereitstellung paralleler Algorithmen, mit denen Berechnungen für Sammlungen oder Datensätze über die gesamten computingressourcen verteilt werden. Außerdem wird die *Aufgaben Parallelität* durch Bereitstellen von Task Objekten ermöglicht, die mehrere unabhängige Vorgänge über die Computerressourcen verteilen.

Verwenden Sie die Parallel Patterns Library bei lokalen Berechnungen, die von der parallelen Ausführung profitieren können. Sie können z. b. den Algorithmus "Parallelität [::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) " verwenden, um eine vorhandene **`for`** Schleife zu transformieren und parallel zu agieren.

Weitere Informationen zur Parallel Patterns Library finden Sie unter [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

### <a name="asynchronous-agents-library"></a>Asynchronous Agents Library

Die Asynchronous Agents Library (oder nur die *Agents Library*) stellt ein Actor-basiertes Programmiermodell und Nachrichten Übergabe Schnittstellen für grob abgestimmte Datenfluss-und Pipeline Aufgaben bereit. Asynchrone Agents ermöglichen es Ihnen, die Latenz produktiv zu nutzen, indem Sie Arbeiten ausführen, während andere Komponenten auf die Daten warten.

Verwenden Sie die Agents Library, wenn Sie über mehrere Entitäten verfügen, die miteinander asynchron kommunizieren. Beispielsweise können Sie einen Agent erstellen, der die Daten aus einer Datei oder einer Netzwerkverbindung liest und anschließend die Schnittstellen der Meldungsübergabe verwendet, um diese Daten an einen anderen Agent zu senden.

Weitere Informationen zur Agents Library finden Sie unter [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md).

### <a name="task-scheduler"></a>Aufgabenplanung

Der Taskplaner plant und koordiniert die Aufgaben zur Laufzeit. Der Taskplaner ist kooperativ und verwendet einen Arbeitsübernahme-Algorithmus, um die maximale Auslastung der Verarbeitungsressourcen zu erreichen.

Die Concurrency Runtime stellt einen Standardplaner bereit, sodass Sie keine Infrastrukturdetails verwalten müssen. Um die Qualitätsanforderungen Ihrer Anwendung zu erfüllen, können Sie jedoch auch Ihre eigene Planungsrichtlinie zur Verfügung stellen oder bestimmten Planern bestimmte Aufgaben zuordnen.

Weitere Informationen zum Taskplaner finden Sie unter [Taskplaner](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

### <a name="resource-manager"></a>Ressourcen-Manager

Die Aufgabe des Ressourcen-Managers besteht darin, die Computerressourcen, wie beispielsweise Prozessoren und Arbeitsspeicher, zu verwalten. Der Ressourcen-Manager reagiert auf Arbeitslasten, die sich zur Laufzeit ändern, indem die Ressourcen dorthin zugewiesen werden, wo sie am effektivsten sind.

Der Ressourcen-Manager stellt eine Abstraktionsebene für die Computerressourcen dar und interagiert in erster Linie mit dem Aufgabenplaner. Obwohl Sie den Ressourcen-Manager zur Optimierung der Leistung Ihrer Bibliotheken und Anwendungen verwenden können, verwenden Sie in der Regel die Funktionalität, die von der Parallel Patterns Library, der Agents Library und dem Aufgabenplaner bereitgestellt wird. Diese Bibliotheken verwenden den Ressourcen-Manager, um die Ressourcen dynamisch neu zu verteilen, wenn sich die Arbeitslasten ändern.

[Nach[oben](#top)]

## <a name="c-lambda-expressions"></a><a name="lambda"></a>C++ Lambda-Ausdrücke

Viele der Typen und Algorithmen, die von der Concurrency Runtime definiert werden, werden als C++-Vorlagen implementiert. Einige dieser Typen und Algorithmen nehmen als Parameter eine Routine an, die die Arbeit ausführt. Dieser Parameter kann eine Lambda-Funktion, ein Funktionsobjekt oder ein Funktionszeiger sein. Diese Entitäten werden auch als *Arbeitsfunktionen* oder *Arbeits Routinen*bezeichnet.

Die Lambda-Ausdrücke sind eine wichtige neue Sprachfunktion in Visual C++, da sie eine kompakte Art und Weise zum Definieren von Arbeitsfunktionen für die Parallelverarbeitung bieten. Funktionsobjekte und Funktionszeiger ermöglichen Ihnen die Verwendung der Concurrency Runtime mit dem vorhandenen Code. Microsoft empfiehlt jedoch, Lambdaausdrücke beim Schreiben von neuem Code zu verwenden, da diese bezüglich der Sicherheit und Produktivität viele Vorteile bieten.

Im folgenden Beispiel wird die Syntax von Lambda-Funktionen, Funktions Objekten und Funktions Zeigern in mehreren Aufrufen des Algorithmus " [parallelcurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) " verglichen. Jeder-Befehl `parallel_for_each` verwendet eine andere Technik, um das Quadrat der einzelnen Elemente in einem [Std:: Array](../../standard-library/array-class-stl.md) -Objekt zu berechnen.

[!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]

**Ausgabe**

```Output
1
256
6561
65536
390625
```

Weitere Informationen zu Lambda-Funktionen in C++ finden Sie unter [Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md).

[Nach[oben](#top)]

## <a name="requirements"></a><a name="requirements"></a> Anforderungen

Die folgende Tabelle zeigt die Headerdateien, die jeder einzelnen Komponente der Concurrency Runtime zugeordnet sind:

|Komponente|Headerdateien|
|---------------|------------------|
|Parallel Patterns Library (PPL)|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector.h|
|Asynchronous Agents Library|agents.h|
|Aufgabenplanung|concrt.h|
|Ressourcen-Manager|concrtrm.h|

Der Concurrency Runtime wird im Parallelitäts [Namespace](../../parallel/concrt/reference/concurrency-namespace.md) deklariert. (Sie können auch die Parallelität verwenden, bei der [es sich um](../../parallel/concrt/reference/concurrency-namespace.md)einen Alias für diesen Namespace handelt.) Der `concurrency::details` -Namespace unterstützt das Concurrency Runtime Framework und ist nicht für die direkte Verwendung im Code vorgesehen.

Die Concurrency Runtime wird als Teil der C-Laufzeitbibliothek (CRT) bereitgestellt. Weitere Informationen zum Erstellen einer Anwendung, die die CRT verwendet, finden Sie unter [Funktionen der CRT-Bibliothek](../../c-runtime-library/crt-library-features.md).

[Nach[oben](#top)]
