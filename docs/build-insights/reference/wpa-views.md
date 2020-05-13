---
title: 'Referenz: Windows Performance Analyzer-Ansichten'
description: Referenz für C++-Build-Insights-Ansichten, die in Windows Performance Analyzer verfügbar sind.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b54b1b76d83b77ec7b8d8d3309d81ed9eb2db2d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323233"
---
# <a name="reference-windows-performance-analyzer-views"></a>Referenz: Windows Performance Analyzer-Ansichten

::: moniker range="<=vs-2017"

Die C++-Build-Insights-Tools sind in Visual Studio 2019 verfügbar. Um die Dokumentation für diese Version **Version** anzuzeigen, legen Sie das Visual Studio Version-Selektor-Steuerelement für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range="vs-2019"

Dieser Artikel enthält Details zu den einzelnen C++-Build-Insights-Ansichten, die in Windows Performance Analyzer (WPA) verfügbar sind. Verwenden Sie diese Seite, um zu finden:

- Beschreibungen der Datenspalte; Und
- verfügbaren Voreinstellungen für jede Ansicht, einschließlich ihrer beabsichtigten Verwendung und des bevorzugten Anzeigemodus.

Wenn Sie WPA noch nicht kennen, empfehlen wir Ihnen, sich zunächst mit den [Grundlagen von WPA for C++ Build Insights](/cpp/build-insights/tutorials/wpa-basics)vertraut zu machen.

## <a name="build-explorer"></a>Build Explorer

Die Build-Explorer-Ansicht wird verwendet, um:

- Parallelitätsprobleme zu diagnostizieren,
- bestimmen, ob Ihre Buildzeit durch Analysieren, Codegenerierung oder Verknüpfung dominiert wird, und
- Engpässe und ungewöhnlich lange Bauaktivitäten zu identifizieren.

### <a name="build-explorer-view-data-columns"></a>Erstellen von Explorer-Ansichtsdatenspalten

| Spaltenname | BESCHREIBUNG |
|-|-|
| BuildTimelineDescription | Eine Textbeschreibung der Zeitachse, auf der die aktuelle Aktivität oder Eigenschaft auftritt. |
| BuildTimelineId          | Ein nullbasierter Bezeichner für die Zeitachse, auf der die aktuelle Aktivität oder Eigenschaft auftritt. |
| Komponente                | Die Komponente, die beim Aussenden des aktuellen Ereignisses kompiliert oder verknüpft wurde. Der Wert dieser Spalte ist * \<\> Invocation X Info,* wenn diesem Ereignis keine Komponente zugeordnet ist. X ist ein eindeutiger numerischer Bezeichner für den Aufruf, der zum Zeitpunkt der Ausekommnisausführung des Ereignisses ausgeführt wird. Dieser Bezeichner ist derselbe wie der bezeichner in der InvocationId-Spalte für dieses Ereignis. |
| Anzahl                    | Die Anzahl der Aktivitäten oder Eigenschaften, die durch diese Datenzeile dargestellt werden. Dieser Wert ist immer 1 und nur in Aggregationsszenarien nützlich, wenn mehrere Zeilen gruppiert werden. |
| ExclusiveCPUTime         | Die CPU-Zeit in Millisekunden, die von dieser Aktivität verwendet wird. Die zeit, die für untergeordnete Aktivitäten aufgewendet wird, ist in diesem Betrag nicht enthalten. |
| ExclusiveDuration        | Die Millisekundendauer der Aktivität. Die Dauer der untergeordneten Aktivitäten ist in diesem Betrag nicht enthalten. |
| InklusiveCPUTime         | Die CPU-Zeit in Millisekunden, die von dieser Aktivität und allen untergeordneten Aktivitäten verwendet wird. |
| InklusiveDauer        | Die Millisekundendauer dieser Aktivität, einschließlich aller untergeordneten Aktivitäten. |
| InvocationDescription    | Eine Textbeschreibung des Aufrufs, in dem dieses Ereignis aufgetreten ist. Die Beschreibung enthält, ob es *sich um cl.exe* oder *link.exe*handelte, und einen eindeutigen numerischen Aufrufbezeichner. Gegebenenfalls enthält sie den vollständigen Pfad zu der Komponente, die während des Aufrufs kompiliert oder verknüpft wurde. Bei Aufrufen, die keine Komponente erstellen, oder bei Aufrufen, die mehrere Komponenten erstellen, ist der Pfad leer. Der Aufrufbezeichner ist derselbe wie in der Spalte InvocationId. |
| InvocationId             | Ein eindeutiger numerischer Bezeichner für den Aufruf dieses Ereignisses ist aufgetreten. |
| Name                     | Der Name der Aktivität oder Eigenschaft, die durch dieses Ereignis dargestellt wird. |
| Time                     | Ein Zeitstempel, der angibt, wann das Ereignis aufgetreten ist. |
| Tool                     | Das Tool, das ausgeführt wurde, als dieses Ereignis aufgetreten ist. Der Wert dieser Spalte ist entweder CL oder Link. |
| type                     | Der Typ des aktuellen Ereignisses. Dieser Wert ist entweder Aktivität oder Eigenschaft. |
| Wert                    | Wenn das aktuelle Ereignis eine Eigenschaft ist, enthält diese Spalte ihren Wert. Diese Spalte bleibt leer, wenn es sich bei dem aktuellen Ereignis um eine Aktivität handelt. |

### <a name="build-explorer-view-presets"></a>Build Explorer-Ansichtsvoreinstellungen

| Voreingestellter Name           | Bevorzugter Ansichtsmodus | Verwendung |
|-----------------------|---------------------|------------|
| Aktivitätsstatistik   | Grafik / Tabelle       | Verwenden Sie diese Voreinstellung, um aggregierte Statistiken für alle Build Explorer-Aktivitäten anzuzeigen. Im Tabellenmodus können Sie auf einen Blick feststellen, ob Ihr Build von Deranalyse, Codegenerierung oder dem Linker dominiert wird. Die aggregierten Dauern für jede Aktivität werden in absteigender Reihenfolge sortiert. Führen Sie drillin, indem Sie den obersten Knoten erweitern, um leicht zu finden, welche Aufrufe für diese Top-Aktivitäten die meiste Zeit in Anspruch nehmen. Wenn Sie möchten, können Sie die WPA-Einstellungen anpassen, um Durchschnittswerte oder andere Arten von Aggregationen anzuzeigen. Sehen Sie im Diagrammmodus, wann jede Aktivität während des Builds aktiv ist. |
| Aufrufe           | Graph               | Scrollen Sie nach unten durch eine Liste von Aufrufen in der Diagrammansicht sortiert nach Startzeit. Sie können es zusammen mit der CPU-Ansicht (Sampled) verwenden, um Aufrufe zu finden, die an Zonen mit geringer CPU-Auslastung ausgerichtet sind. Erkennen Sie Parallelitätsprobleme. |
| Aufrufeigenschaften | Tabelle               | Finden Sie schnell wichtige Informationen zu einem bestimmten Compiler- oder Linkeraufruf. Bestimmen Sie die Version, das Arbeitsverzeichnis oder die vollständige Befehlszeile, die zum Aufrufen verwendet wird. |
| Zeitpläne             | Graph               | Sehen Sie sich ein Balkendiagramm an, wie Ihr Build parallelisiert wurde. Identifizieren Sie Parallelitätsprobleme und Engpässe auf einen Blick. Konfigurieren Sie WPA so, dass den Balken je nach Ihren Anforderungen unterschiedliche Bedeutungen zugewiesen werden. Wählen Sie Aufrufbeschreibungen als letzte gruppierte Spalte aus, um ein farbcodiertes Balkendiagramm aller Aufrufe anzuzeigen. Es hilft Ihnen, zeitaufwändige Täter schnell zu identifizieren. Zoomen Sie dann hinein, und wählen Sie den Aktivitätsnamen als letzte gruppierte Spalte aus, um die längsten Teile anzuzeigen. |

## <a name="files"></a>Dateien

Die Dateiansicht wird verwendet, um:

- bestimmen, welche Header am häufigsten enthalten sind, und
- helfen Sie bei der Entscheidung, was in einen vorkompilierten Header (PCH) aufgenommen werden soll.

### <a name="files-view-data-columns"></a>Dateien anzeigen Datenspalten

| Spaltenname              | BESCHREIBUNG |
|--------------------------|-------------|
| ActivityName             | Die Aktivität, die ausgeführt wurde, als dieses Dateiereignis ausgesendet wurde. Derzeit ist dieser Wert immer *Parsing*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Komponente                | * |
| Anzahl                    | * |
| Tiefe                    | Die Null-basierte Position in der Include-Struktur, in der diese Datei gefunden wird. Die Zählung beginnt am Stamm des Include-Baums. Der Wert 0 entspricht in der Regel einer .c/.cpp-Datei. |
| ExclusiveDuration        | * |
| InklusiveBy               | Der vollständige Pfad der Datei, die die aktuelle Datei enthält. |
| IncludedPath             | Der vollständige Pfad der aktuellen Datei. |
| InklusiveDauer        | * |
| InvocationId             | * |
| StartTime                | Ein Zeitstempel, der den Zeitpunkt darstellt, zu dem das aktuelle Dateiereignis ausgesendet wurde. |
| Tool                     | * |

\*Der Wert dieser Spalte ist derselbe wie in der [Build-Explorer-Ansicht.](#build-explorer-view-data-columns)

### <a name="files-view-presets"></a>Dateiansicht summieren Voreinstellungen

| Voreingestellter Name | Bevorzugter Ansichtsmodus | Verwendung |
|-------------|---------------------|------------|
| Statistik  | Tabelle               | Sehen Sie, welche Dateien die höchste aggregierte Analysezeit hatten, indem Sie sich die Liste in absteigender Reihenfolge ansehen. Verwenden Sie diese Informationen, um Ihre Header neu zu strukturieren oder zu entscheiden, was in Ihre PCH aufgenommen werden soll. |

## <a name="functions"></a>Functions

Die Functions-Ansicht wird verwendet, um Funktionen mit einer zu langen Codegenerierungszeit zu identifizieren.

### <a name="functions-view-data-columns"></a>Funktionen anzeigen Datenspalten

| Spaltenname              | BESCHREIBUNG |
|--------------------------|-------------|
| ActivityName             | Die Aktivität, die ausgeführt wurde, als dieses Funktionsereignis emittiert wurde. Derzeit ist dieser Wert immer *CodeGeneration*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Komponente                | * |
| Anzahl                    | * |
| Duration                 | Die Dauer der Codegenerierungsaktivität für diese Funktion. |
| FunctionName             | Der Name der Funktion, die eine Codegenerierung durchläuft. |
| InvocationId             | * |
| StartTime                | Ein Zeitstempel, der angibt, wann das aktuelle Funktionsereignis emittiert wurde. |
| Tool                     | * |

\*Der Wert dieser Spalte ist derselbe wie in der [Build-Explorer-Ansicht.](#build-explorer-view-data-columns)

### <a name="functions-view-presets"></a>Funktionen Ansicht summat

| Voreingestellter Name | Bevorzugter Ansichtsmodus | Verwendung |
|-------------|---------------------|------------|
| Statistik  | Tabelle               | Sehen Sie, welche Funktionen die höchste aggregierte Codegenerierungszeit hatten, indem Sie sich die Liste in absteigender Reihenfolge ansehen. Sie können darauf hinweisen, wo Ihr Code das **__forceinline** Schlüsselwort überverwendet, oder dass einige Funktionen zu groß sind. |
| Zeitpläne   | Graph               | Sehen Sie sich dieses Balkendiagramm an, um den Speicherort und die Dauer von Funktionen zu erfahren, deren Generierung am meisten Inanspruchnimmt. Prüfen Sie, ob sie in der Build-Explorer-Ansicht mit Engpässen ausgerichtet sind. Wenn dies der Zeitpunkt ist, ergreifen Sie geeignete Maßnahmen, um die Codegenerierungszeit zu verkürzen und Ihre Buildzeiten zu nutzen. |

## <a name="see-also"></a>Siehe auch

[Erste Schritte mit C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Referenz: vcperf-Befehle](vcperf-commands.md)\
[Tutorial: Grundlagen des Windows-Leistungsanalyseprogramms](/cpp/build-insights/tutorials/wpa-basics)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
