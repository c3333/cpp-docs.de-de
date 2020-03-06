---
title: 'Referenz: Windows Performance Analyzer-Ansichten'
description: Referenz zu C++ den in Windows Performance Analyzer verfügbaren Build Insights-Ansichten.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eb3e20ed3ca4231b10efaf36310f6fbc0f5980bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333893"
---
# <a name="reference-windows-performance-analyzer-views"></a>Referenz: Windows Performance Analyzer-Ansichten

::: moniker range="<=vs-2017"

Die C++ Build Insights-Tools sind in Visual Studio 2019 verfügbar. Um die Dokumentation für diese Version anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2019 fest.

::: moniker-end
::: moniker range="vs-2019"

Dieser Artikel enthält Details zu den C++ einzelnen in Windows Performance Analyzer (WPA) verfügbaren Build Insights-Ansichten. Verwenden Sie diese Seite, um Folgendes zu finden:

- Datenspalten Beschreibungen; immer
- Verfügbare Voreinstellungen für jede Ansicht, einschließlich der vorgesehenen Verwendung und des bevorzugten Anzeigemodus.

Wenn Sie noch nicht mit WPA vertraut sind, sollten Sie sich zunächst mit den [Grundlagen von WPA für C++ Einblicke](/cpp/build-insights/tutorials/wpa-basics)in die Erstellung vertraut machen.

## <a name="build-explorer"></a>Build Explorer

Die Ansicht "Build Explorer" wird für Folgendes verwendet:

- Diagnostizieren von Parallelitäts Problemen
- Stellen Sie fest, ob die Buildzeit durch die Generierung, die Codegenerierung oder die Verknüpfung dominiert wird.
- Identifizieren Sie Engpässe und ungewöhnlich lange buildaktivitäten.

### <a name="build-explorer-view-data-columns"></a>Anzeigen von Datenspalten im Build-Explorer

| Spaltenname | BESCHREIBUNG |
|-|-|
| Buildtimelinedescription | Eine Textbeschreibung der Zeitachse, in der die aktuelle Aktivität oder Eigenschaft auftritt. |
| Buildtimelineid          | Ein NULL basierter Bezeichner für die Zeitachse, in der die aktuelle Aktivität oder Eigenschaft auftritt. |
| Komponente                | Die Komponente, die kompiliert oder verknüpft wird, wenn das aktuelle Ereignis ausgegeben wurde. Der Wert dieser Spalte ist *\<Aufruf X Info\>* , wenn diesem Ereignis keine Komponente zugeordnet ist. X ist ein eindeutiger numerischer Bezeichner für den Aufruf, der zum Zeitpunkt der Ausgabe des Ereignisses ausgeführt wird. Dieser Bezeichner ist mit dem Wert in der invocationID-Spalte für dieses Ereignis identisch. |
| Anzahl                    | Die Anzahl der Aktivitäten oder Eigenschaften, die durch diese Daten Zeile dargestellt werden. Dieser Wert ist immer 1 und nur in Aggregations Szenarios nützlich, wenn mehrere Zeilen gruppiert sind. |
| Exclusivecputime         | Die CPU-Zeit in Millisekunden, die von dieser Aktivität verwendet wird. Die Zeit, die für untergeordnete Aktivitäten aufgewendet wird, ist in diesem Betrag nicht enthalten. |
| Exclusiveduration        | Die millisekundendauer der Aktivität. Die Dauer von untergeordneten Aktivitäten ist in diesem Betrag nicht enthalten. |
| Inclusivecputime         | Die CPU-Zeit (in Millisekunden), die von dieser Aktivität und allen untergeordneten Aktivitäten verwendet wird. |
| Inclusiveduration        | Die millisekundendauer dieser Aktivität, einschließlich aller untergeordneten Aktivitäten. |
| Invocationdescription    | Eine Textbeschreibung des aufereignisses, in dem dieses Ereignis aufgetreten ist. Die Beschreibung enthält, ob es sich um *cl. exe* oder *Link. exe*handelt, und einen eindeutigen numerischen Aufruf Bezeichner. Falls zutreffend, enthält Sie den vollständigen Pfad zu der Komponente, die beim Aufruf kompiliert oder verknüpft wurde. Für Aufrufe, bei denen keine Komponenten erstellt werden, oder für diejenigen, die mehrere Komponenten erstellen, ist der Pfad leer. Der Aufruf Bezeichner ist derselbe wie der in der Spalte invocationID. |
| InvocationId             | Ein eindeutiger numerischer Bezeichner für den Aufruf, in dem dieses Ereignis aufgetreten ist. |
| Name                     | Der Name der Aktivität oder Eigenschaft, die durch dieses Ereignis dargestellt wird. |
| Time                     | Ein Zeitstempel, der angibt, wann das Ereignis aufgetreten ist. |
| Tool                     | Das Tool, das beim Eintreten dieses Ereignisses ausgeführt wird. Der Wert dieser Spalte ist entweder CL oder Link. |
| type                     | Der Typ des aktuellen Ereignisses. Dieser Wert ist entweder Aktivität oder Eigenschaft. |
| value                    | Wenn das aktuelle Ereignis eine Eigenschaft ist, enthält diese Spalte ihren Wert. Wenn das aktuelle Ereignis eine Aktivität ist, wird diese Spalte leer gelassen. |

### <a name="build-explorer-view-presets"></a>Voreinstellungen für den Build-Explorer

| Voreingestellter Name           | Bevorzugter Ansichtsmodus | Verwendung |
|-----------------------|---------------------|------------|
| Aktivitäts Statistik   | Diagramm/Tabelle       | Verwenden Sie diese Voreinstellung, um aggregierte Statistiken für alle Build Explorer-Aktivitäten anzuzeigen. Legen Sie im Tabellen Modus auf einen Blick fest, ob der Build durch die Generierung, die Codegenerierung oder den Linker dominiert wird. Die aggregierten Dauer für jede Aktivität wird in absteigender Reihenfolge sortiert. Führen Sie einen Drilldown durch, indem Sie den obersten Knoten erweitern, um leicht herauszufinden, welche Aufrufe für diese wichtigsten Aktivitäten die meiste Zeit beanspruchen. Wenn Sie möchten, können Sie die WPA-Einstellungen anpassen, um Durchschnittswerte oder andere Typen von Aggregationen anzuzeigen. Lesen Sie im Graph-Modus, wann jede Aktivität während des Builds aktiv ist. |
| Aufrufe           | Graph               | Scrollen Sie nach unten durch eine Liste der Aufrufe in der Diagramm Ansicht nach Startzeit sortiert. Sie können Sie in Verbindung mit der CPU-Ansicht (Sampling) verwenden, um Aufrufe zu suchen, die mit niedrigen CPU-Auslastungs Zonen übereinstimmen. Erkennen von Parallelitäts Problemen |
| Aufruf Eigenschaften | Tabelle               | Suchen Sie schnell Schlüsselinformationen zu einem bestimmten Compiler oder Linker-Aufruf. Bestimmen Sie die Version, das Arbeitsverzeichnis oder die vollständige Befehlszeile, die zum Aufrufen verwendet wird. |
| Zeitpläne             | Graph               | Sehen Sie sich ein Balkendiagramm an, wie der Build parallelisiert wurde. Erkennen Sie Parallelitäts Probleme und Engpässe auf einen Blick. Konfigurieren Sie WPA so, dass den Balken entsprechend Ihren Anforderungen unterschiedliche Bedeutungen zugewiesen werden. Wählen Sie Aufruf Beschreibungen als letzte gruppierte Spalte aus, um ein Farb codiertes Balkendiagramm für alle Ihre Aufrufe anzuzeigen. Damit können Sie schnell zeitaufwändige Täter identifizieren. Vergrößern Sie anschließend den Aktivitäts Namen, und wählen Sie den Aktivitäts Namen als letzte gruppierte Spalte aus, um die längsten Teile anzuzeigen. |

## <a name="files"></a>Dateien

Die Ansicht Dateien wird für folgende Aktionen verwendet:

- Legen Sie fest, welche Header am häufigsten eingeschlossen werden sollen.
- helfen Sie Ihnen bei der Entscheidung, was Sie in einen vorkompilierten Header (PCH) einschließen möchten.

### <a name="files-view-data-columns"></a>Dateien Ansicht (Datenspalten)

| Spaltenname              | BESCHREIBUNG |
|--------------------------|-------------|
| ActivityName             | Die Aktivität, die während der Ausgabe dieses Datei Ereignisses ausgeführt wird. Derzeit wird dieser *Wert immer verarbeitet*. |
| Buildtimelinedescription | * |
| Buildtimelineid          | * |
| Komponente                | * |
| Anzahl                    | * |
| Tiefe                    | Die null basierte Position in der Include-Struktur, in der diese Datei gefunden wird. Die Zählung beginnt am Stamm der Include-Struktur. Der Wert 0 entspricht in der Regel einer c/. cpp-Datei. |
| Exclusiveduration        | * |
| Includby               | Der vollständige Pfad der Datei, die die aktuelle Datei enthielt. |
| Includecodpath             | Der vollständige Pfad der aktuellen Datei. |
| Inclusiveduration        | * |
| InvocationId             | * |
| StartTime                | Ein Zeitstempel, der die Uhrzeit darstellt, zu der das aktuelle Datei Ereignis ausgegeben wurde. |
| Tool                     | * |

\* der Wert dieser Spalte mit dem Wert in der Ansicht " [Build Explorer](#build-explorer-view-data-columns) " identisch ist.

### <a name="files-view-presets"></a>Voreinstellungen der Dateiansicht

| Voreingestellter Name | Bevorzugter Ansichtsmodus | Verwendung |
|-------------|---------------------|------------|
| Statistik  | Tabelle               | Sehen Sie, welche Dateien die höchste aggregierte Verarbeitungszeit hatten, indem Sie die Liste in absteigender Reihenfolge betrachten. Verwenden Sie diese Informationen, um die Neustrukturierung ihrer Header zu unterstützen oder zu entscheiden, was in Ihrem PCH enthalten sein soll. |

## <a name="functions"></a>Functions

Die Funktions Ansicht wird verwendet, um Funktionen mit übermäßig langer Code Generierungs Zeit zu identifizieren.

### <a name="functions-view-data-columns"></a>Funktions Anzeige von Datenspalten

| Spaltenname              | BESCHREIBUNG |
|--------------------------|-------------|
| ActivityName             | Die Aktivität, die ausgeführt wird, als dieses Funktions Ereignis ausgegeben wurde. Derzeit ist dieser Wert immer *Codegenerierung*. |
| Buildtimelinedescription | * |
| Buildtimelineid          | * |
| Komponente                | * |
| Anzahl                    | * |
| Duration                 | Die Dauer der Code Generierungs Aktivität für diese Funktion. |
| FunctionName             | Der Name der Funktion, die die Codegenerierung durchläuft. |
| InvocationId             | * |
| StartTime                | Ein Zeitstempel, der angibt, wann das aktuelle Funktions Ereignis ausgegeben wurde. |
| Tool                     | * |

\* der Wert dieser Spalte mit dem Wert in der Ansicht " [Build Explorer](#build-explorer-view-data-columns) " identisch ist.

### <a name="functions-view-presets"></a>Funktions Anzeigeeinstellungen

| Voreingestellter Name | Bevorzugter Ansichtsmodus | Verwendung |
|-------------|---------------------|------------|
| Statistik  | Tabelle               | Sehen Sie sich an, welche Funktionen die höchste aggregierte Code Generierungs Zeit haben, indem Sie die Liste in absteigender Reihenfolge betrachten. Sie können darauf hinweisen, wo Ihr Code das **__forceinline** Schlüsselwort überschreitet, oder dass einige Funktionen zu groß sind. |
| Zeitpläne   | Graph               | Sehen Sie sich dieses Balkendiagramm an, um den Speicherort und die Dauer von Funktionen zu erlernen, die die meiste Zeit für die Generierung benötigen. Überprüfen Sie, ob Sie in der Ansicht des Build-Explorers mit Engpässen übereinstimmen. Wenn dies der Fall ist, führen Sie die entsprechende Aktion aus, um die Code Generierungs Zeit zu verkürzen und die Buildzeiten zu |

## <a name="see-also"></a>Weitere Informationen

[Machen Sie sich C++ mit den Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights) -\
[Referenz: vcperf-Befehle](vcperf-commands.md)\
[Tutorial: Grundlagen zu Windows Performance Analyzer](/cpp/build-insights/tutorials/wpa-basics)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
