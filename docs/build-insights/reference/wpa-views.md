---
title: 'Referenz: Windows Performance Analyzer-Ansichten'
description: Referenz zu den C++ Build Insights-Ansichten in Windows Performance Analyzer.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8bbcc43ef19adfd85a3679a2136d471333a74a10
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224096"
---
# <a name="reference-windows-performance-analyzer-views"></a>Referenz: Windows Performance Analyzer-Ansichten

::: moniker range="<=vs-2017"

Die C++ Build Insights-Tools sind in Visual Studio 2019 verfügbar. Wenn die Dokumentation für diese Version angezeigt werden soll, legen Sie das Steuerelement zur Auswahl der **Version** für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range="vs-2019"

Dieser Artikel enthält Details zu den einzelnen C++ Build Insights-Ansichten, die in Windows Performance Analyzer (WPA) verfügbar sind. Auf dieser Seite finden Sie:

- Datenspaltenbeschreibungen
- verfügbare Voreinstellungen für die Ansichten sowie den beabsichtigten Einsatzzweck und den bevorzugten Anzeigemodus

Wenn Sie WPA noch nicht lange einsetzen, sollten Sie sich zunächst mit den [WPA-Grundlagen für C++ Build Insights](/cpp/build-insights/tutorials/wpa-basics) vertraut machen.

## <a name="build-explorer"></a>Build-Explorer

Die Ansicht „Build-Explorer“ wird für Folgendes verwendet:

- zur Diagnose von Parallelitätsproblemen
- zur Feststellung, ob die Verarbeitung, Codegenerierung oder der Linker zur Buildzeit dominiert
- zur Ermittlung von Engpässen oder ungewöhnlich langen Buildaktivitäten

### <a name="build-explorer-view-data-columns"></a>Datenspalten der Ansicht „Build-Explorer“

| Spaltenname | Beschreibung |
|-|-|
| BuildTimelineDescription | Eine Textbeschreibung der Zeitachse, in der die aktuelle Aktivität oder Eigenschaft auftritt |
| BuildTimelineId          | Eine nullbasierter Bezeichner für die Zeitachse, in der die aktuelle Aktivität oder Eigenschaft auftritt |
| Komponente                | Die Komponente, die kompiliert oder verknüpft wird, wenn das aktuelle Ereignis ausgelöst wurde – der Wert dieser Spalte entspricht *\<Invocation X Info\>* , wenn diesem Ereignis keine Komponente zugeordnet ist. X ist ein eindeutiger numerischer Bezeichner für den Aufruf, der zum Zeitpunkt der Ereignisauslösung ausgeführt wird. Dieser Bezeichner ist mit dem Wert in der InvocationId-Spalte für dieses Ereignis identisch. |
| Anzahl                    | Die Anzahl der Aktivitäten oder Eigenschaften, die durch diese Datenzeile dargestellt werden – der Wert ist immer 1 und nur in Aggregationsszenarios nützlich, in denen mehrere Zeilen gruppiert werden. |
| ExclusiveCPUTime         | Die CPU-Zeit in Millisekunden, die für diese Aktivität aufgewendet wird, dabei wird die Zeit für untergeordnete Aktivitäten nicht berücksichtigt. |
| ExclusiveDuration        | Die Dauer dieser Aktivität in Millisekunden, dabei wird die Dauer untergeordneter Aktivitäten nicht berücksichtigt. |
| InclusiveCPUTime         | Die CPU-Zeit in Millisekunden, die für diese Aktivität und alle untergeordneten Aktivitäten aufgewendet wird. |
| InclusiveDuration        | Die Dauer dieser Aktivität und aller untergeordneten Aktivitäten in Millisekunden. |
| InvocationDescription    | Eine Textbeschreibung des Aufrufs, bei dem dieses Ereignis aufgetreten ist – aus dieser geht hervor, ob *cl.exe* oder *link.exe* beteiligt war, und ein eindeutiger numerischer Aufrufbezeichner ist enthalten. Falls zutreffend, enthält dieser den vollständigen Pfad zu der Komponente, die beim Aufruf kompiliert oder verknüpft wurde. Bei Aufrufen, die keine oder mehrere Komponenten kompilieren, ist der Pfad leer. Dieser Aufrufbezeichner ist mit dem Wert in der InvocationId-Spalte identisch. |
| InvocationId             | Ein eindeutiger numerischer Bezeichner für den Aufruf, in dem dieses Ereignis aufgetreten ist |
| name                     | Der Name der Aktivität oder Eigenschaft, die durch dieses Ereignis dargestellt wird |
| zeit                     | Ein Zeitstempel, der angibt, wann das Ereignis aufgetreten ist |
| Tool                     | Das Tool, das beim Auftreten dieses Ereignisses ausgeführt wurde – der Wert dieser Spalte ist CL oder LINK. |
| Typ                     | Der Typ des aktuellen Ereignisses – dieser Wert ist entweder Activity oder Property. |
| Wert                    | Wenn das aktuelle Ereignis eine Eigenschaft ist, enthält diese Spalte deren Wert. Wenn das aktuelle Ereignis eine Aktivität ist, bleibt diese Spalte leer. |

### <a name="build-explorer-view-presets"></a>Voreinstellungen für die Ansicht „Build-Explorer“

| Name der Voreinstellung           | Bevorzugter Anzeigemodus | Verwendung |
|-----------------------|---------------------|------------|
| Aktivitätsstatistik   | Diagramm/Tabelle       | Verwenden Sie diese Voreinstellung, um aggregierte Statistiken für alle Build-Explorer-Aktivitäten anzuzeigen. Im Tabellenmodus sehen Sie auf einen Blick, ob die Verarbeitung, die Codegenerierung oder der Linker bei Ihrem Build dominiert. Die aggregierte Dauer für jede Aktivität wird in absteigender Reihenfolge sortiert. Sehen Sie sich diese genauer an, indem Sie den obersten Knoten aufklappen, um herauszufinden, welche Aufrufe für die obersten Aktivitäten die meiste Zeit beanspruchen. Sie können die WPA-Einstellungen so anpassen, dass Durchschnittswerte oder andere Aggregationen angezeigt werden. Im Diagrammmodus können Sie nachprüfen, wann welche Aktivität während des Builds ausgeführt wurde. |
| Aufrufe           | Graph               | Scrollen Sie durch eine Liste der Aufrufe in der Diagrammansicht, die nach Startzeit sortiert ist. Sie können sie in Verbindung mit der CPU-Ansicht (stichprobenartig) verwenden, um Aufrufe zu suchen, die mit niedrigen CPU-Auslastungszonen übereinstimmen. Zudem können Parallelitätsprobleme ermittelt werden. |
| Aufrufeigenschaften | Tabelle               | Hier finden Sie schnell wichtige Informationen zu einem bestimmten Compiler- oder Linkeraufruf. Bestimmen Sie die Version, das Arbeitsverzeichnis oder die vollständige Befehlszeile, die für den Aufruf verwendet wurde. |
| Zeitpläne             | Graph               | Hier wird ein Balkendiagramm für die Parallelisierung Ihres Builds angezeigt. So können Sie Parallelitätsprobleme und Engpässe auf einen Blick erkennen. Sie können WPA so konfigurieren, dass den Balken nach Bedarf unterschiedliche Bedeutungen zugewiesen werden. Legen Sie die Aufrufbeschreibungen als letzte gruppierte Spalte fest, um ein farbcodiertes Balkendiagramm für alle Aufrufe anzuzeigen. So können Sie zeitaufwändige Aktivitäten schnell ermitteln. Vergrößern Sie das Diagramm anschließend, und legen Sie den Aktivitätsnamen als letzte gruppierte Spalte fest, um die längsten Aktivitäten anzuzeigen. |

## <a name="files"></a>Dateien

Die Ansicht „Dateien“ wird für Folgendes verwendet:

- zur Ermittlung, welche Header am häufigsten eingeschlossen werden
- zur Entscheidung, welche Komponenten in einen vorkompilierten Header eingeschlossen werden sollen

### <a name="files-view-data-columns"></a>Datenspalten der Ansicht „Dateien“

| Spaltenname              | Beschreibung |
|--------------------------|-------------|
| ActivityName             | Die Aktivität, die während der Auslösung dieses Dateiereignisses ausgeführt wurde Derzeit lautet dieser Wert standardmäßig *Parsing*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Komponente                | * |
| Anzahl                    | * |
| Tiefe                    | Die nullbasierte Position in der include-Struktur, in der diese Datei gefunden wird – die Zählung beginnt beim Stamm der include-Struktur. Ein Wert von 0 entspricht in der Regel einer C- oder CPP-Datei. |
| ExclusiveDuration        | * |
| IncludedBy               | Der vollständige Pfad der Datei, die das aktuelle Element enthielt |
| IncludedPath             | Der vollständige Pfad der aktuellen Datei |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | Ein Zeitstempel, der die Uhrzeit darstellt, zu der das aktuelle Dateiereignis ausgelöst wurde |
| Tool                     | * |

\* Der Wert dieser Spalte entspricht dem Wert der Ansicht [Build-Explorer](#build-explorer-view-data-columns).

### <a name="files-view-presets"></a>Voreinstellungen der Ansicht „Dateien“

| Name der Voreinstellung | Bevorzugter Anzeigemodus | Verwendung |
|-------------|---------------------|------------|
| Statistik  | Tabelle               | Wenn Sie die Liste in absteigender Reihenfolge sortieren, sehen Sie, bei welchen Dateien die aggregierte Verarbeitungsdauer am höchsten war. Anhand dieser Informationen können Sie die Header neu strukturieren oder entscheiden, welche Komponenten der vorkompilierte Header enthalten soll. |

## <a name="functions"></a>Funktionen

Die Ansicht „Funktionen“ wird verwendet, um Funktionen mit übermäßig langer Codegenerierungsdauer zu ermitteln.

### <a name="functions-view-data-columns"></a>Datenspalten der Ansicht „Funktionen“

| Spaltenname              | Beschreibung |
|--------------------------|-------------|
| ActivityName             | Die Aktivität, die während der Auslösung dieses Funktionsereignisses ausgeführt wurde Derzeit lautet dieser Wert standardmäßig *CodeGeneration*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Komponente                | * |
| Anzahl                    | * |
| Dauer                 | Die Dauer der Codegenerierungsaktivität für diese Funktion |
| FunctionName             | Der Name der Funktion, für die Code generiert wird |
| InvocationId             | * |
| StartTime                | Ein Zeitstempel, der angibt, wann das aktuelle Funktionsereignis ausgelöst wurde |
| Tool                     | * |

\* Der Wert dieser Spalte entspricht dem Wert der Ansicht [Build-Explorer](#build-explorer-view-data-columns).

### <a name="functions-view-presets"></a>Voreinstellungen der Ansicht „Funktionen“

| Name der Voreinstellung | Bevorzugter Anzeigemodus | Verwendung |
|-------------|---------------------|------------|
| Statistik  | Tabelle               | Wenn Sie die Liste in absteigender Reihenfolge sortieren, sehen Sie, bei welchen Funktionen die aggregierte Codegenerierungsdauer am höchsten war. Diese können Hinweise darauf liefern, wo Ihr Code das Schlüsselwort **`__forceinline`** übermäßig verwendet oder einige Funktionen zu groß sind. |
| Zeitpläne   | Graph               | Aus diesem Balkendiagramm gehen die Position und die Dauer der Funktionen hervor, bei denen die Generierung am längsten dauert. Überprüfen Sie, ob diese mit Engpässen in der Ansicht „Build-Explorer“ übereinstimmen. Wenn das der Fall ist, sollten Sie entsprechende Maßnahmen ergreifen, um die Codegenerierungsdauer zu verkürzen und Builds zu beschleunigen. |

## <a name="see-also"></a>Siehe auch

[Erste Schritte mit C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Referenz: vcperf-Befehle](vcperf-commands.md)\
[Tutorial: Windows Performance Analyzer-Grundlagen](/cpp/build-insights/tutorials/wpa-basics)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
