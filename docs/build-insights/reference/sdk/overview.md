---
title: C++Build Insights-SDK
description: Eine Übersicht über das Visual Studio C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5aafcc65bc30de77131d1945c9f4e78361db14ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334031"
---
# <a name="c-build-insights-sdk"></a>C++Build Insights-SDK

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Das C++ Build Insights SDK ist eine Sammlung von APIs, die es Ihnen ermöglichen, personalisierte Tools auf der C++ Plattform "Build Insights" zu erstellen. Auf dieser Seite finden Sie eine allgemeine Übersicht über den Einstieg.

## <a name="obtaining-the-sdk"></a>Erwerben des SDK

Sie können das Build C++ Insights SDK als nuget-Paket herunterladen, indem Sie die folgenden Schritte ausführen:

1. Erstellen Sie in Visual Studio 2017 und höher ein neues C++ Projekt.
1. Klicken Sie im **Projektmappen-Explorer** Bereich mit der rechten Maustaste auf das Projekt.
1. Wählen Sie **nuget-Pakete verwalten** aus dem Kontextmenü aus.
1. Wählen Sie oben rechts die Paketquelle **nuget.org** aus.
1. Suchen Sie nach der neuesten Version des Pakets "Microsoft. cpp. buildinsight".
1. Wählen Sie **Installieren**aus.
1. Akzeptieren Sie die Lizenz.

Weitere Informationen zu den allgemeinen Konzepten im Zusammenhang mit dem SDK finden Sie unter. Sie können auch auf das [ C++ GitHub-Repository](https://github.com/microsoft/cpp-build-insights-samples) mit den offiziellen Build Insights-Beispielen zugreifen C++ , um Beispiele für echte Anwendungen anzuzeigen, die das SDK verwenden.

## <a name="collecting-a-trace"></a>Erfassen einer Ablauf Verfolgung

Wenn Sie C++ das Build Insights SDK zum Analysieren von Ereignissen verwenden, die aus der MSVC-Toolkette stammen, müssen Sie zuerst eine Ablauf Verfolgung erfassen. Das SDK nutzt die Ereignis Ablauf Verfolgung für Windows (Event Tracing for Windows, etw) als zugrunde liegende Ablauf Verfolgungs Technologie. Das Erfassen einer Ablauf Verfolgung kann auf zwei Arten erfolgen:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Methode 1: Verwenden von vcperf in Visual Studio 2019 und höher

1. Öffnen Sie eine erhöhte x64 Native Tools-Eingabeaufforderung für vs 2019.
1. Führen Sie den folgenden Befehl aus: `vcperf /start MySessionName`
1. Erstellen Sie Ihr Projekt.
1. Führen Sie den folgenden Befehl aus: `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Verwenden Sie den `/stopnoanalyze` Befehl, wenn Sie die Ablauf Verfolgung mit vcperf beenden. Sie können das C++ Build Insights SDK nicht verwenden, um Ablauf Verfolgungen zu analysieren, die mit dem regulären `/stop` Befehl beendet wurden.

### <a name="method-2-programmatically"></a>Methode 2: Programm gesteuert

Verwenden Sie eine dieser C++ Funktionen zum Erstellen von Insights-SDK-Ablauf Verfolgungs Sammlungen, um Ablauf Verfolgungen Programm gesteuert zu starten und anzuhalten **Das Programm, das diese Funktionsaufrufe ausführt, muss über Administratorrechte verfügen.** Nur die Funktionen zum Starten und Abbrechen von Ablauf Verfolgung erfordern Administratorrechte. Alle anderen Funktionen im C++ Build Insights SDK können ohne sie ausgeführt werden.

### <a name="sdk-functions-related-to-trace-collection"></a>SDK-Funktionen im Zusammenhang mit Ablauf Verfolgungs Sammlungen

| Funktionalität | C++-API | C-API |
|--|--|--|
| Starten einer Ablauf Verfolgung | [Starttracingsession](functions/start-tracing-session.md) | [Starttracingsessiona](functions/start-tracing-session-a.md)<br />[Starttracingsessionw](functions/start-tracing-session-w.md) |
| Beenden einer Ablauf Verfolgung | [Stoptracingsession](functions/stop-tracing-session.md) | [Stoptracingsessiona](functions/stop-tracing-session-a.md)<br />[Stoptracingsessionw](functions/stop-tracing-session-w.md) |
| Beenden einer Ablauf Verfolgung und<br />sofortiges Analysieren des Ergebnisses | [Stopandanalyzetracingsession](functions/stop-and-analyze-tracing-session.md) | [Stopandanalyzetracingsessiona](functions/stop-and-analyze-tracing-session-a.md)<br />[Stopandanalyzetracingsession](functions/stop-and-analyze-tracing-session-w.md) |
| Beenden einer Ablauf Verfolgung und<br />Das Ergebnis wird sofort erneut protokolliert. | [Stopandrelogtracingsession](functions/stop-and-relog-tracing-session.md) | [Stopandrelogtracingsessiona](functions/stop-and-relog-tracing-session-a.md)<br />[Stopandrelogtracingsessionw](functions/stop-and-relog-tracing-session-w.md) |

In den folgenden Abschnitten wird gezeigt, wie Sie eine Analyse oder eine Sitzung für die erneute Protokollierung konfigurieren. Es ist für die kombinierten Funktions Funktionen erforderlich, z. b. [stopandanalyzetracingsession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Verwenden einer Ablauf Verfolgung

Wenn Sie über eine ETW-Ablauf Verfolgung verfügen C++ , verwenden Sie das Build Insights SDK, um es zu entpacken. Das SDK gibt Ihnen die Ereignisse in einem Format, mit dem Sie Ihre Tools schnell entwickeln können. Es wird nicht empfohlen, die RAW-etw-Ablauf Verfolgung zu verwenden, ohne das SDK zu verwenden. Das von MSVC verwendete Ereignis Format ist nicht dokumentiert, optimiert für die Skalierung auf riesige Builds und schwer zu verstehen. Außerdem ist die C++ SDK-API von Build Insights stabil, während das RAW-Format der etw-Ablauf Verfolgung ohne vorherige Ankündigung geändert werden kann.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>SDK-Typen und Funktionen im Zusammenhang mit der Ablauf Verfolgung

| Funktionalität | C++-API | C-API | Notizen |
|--|--|--|--|
| Einrichten von Ereignis Rückrufen | [Ianalyzer](other-types/ianalyzer-class.md)<br />[Irelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | Das C++ Build Insights SDK stellt Ereignisse mithilfe von Rückruf Funktionen bereit. Implementieren C++Sie in die Rückruf Funktionen, indem Sie eine Analyzer-oder der reloggersitzung-Klasse erstellen, die die ianalyzer-oder irelogger-Schnittstelle erbt. Implementieren Sie in C die Rückrufe in globalen Funktionen, und stellen Sie in der ANALYSIS_CALLBACKS-oder RELOG_CALLBACKS Struktur Zeiger darauf bereit. |
| Gruppen werden aufgebaut | [Makestaticanalyzergroup](functions/make-static-analyzer-group.md)<br />[Makestatikreloggergroup](functions/make-static-relogger-group.md)<br />[Makedynamicanalyzergroup](functions/make-dynamic-analyzer-group.md)<br />[Makedynamikreloggergroup](functions/make-dynamic-relogger-group.md) |  | Die C++ API stellt Hilfsfunktionen und-Typen bereit, um mehrere Analyzer-und der reloggersitzung-Objekte zu gruppieren. Gruppen sind eine saubere Möglichkeit, eine komplexe Analyse in einfachere Schritte aufzuteilen. [vcperf](https://github.com/microsoft/vcperf) ist auf diese Weise organisiert. |
| Analysieren oder neuprotokollieren | [Analysieren](functions/analyze.md)<br />[Erneut aufzuzeichnen](functions/relog.md) | [Analyzea](functions/analyze-a.md)<br />[Analyzew](functions/analyze-w.md)<br />[Reloga](functions/relog-a.md)<br />[Erneut protokollog](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analysieren und neuprotokollieren

Das Verarbeiten einer Ablauf Verfolgung erfolgt entweder über eine Analyse Sitzung oder eine Sitzung zum erneuten protokollieren.

Die Verwendung einer regulären Analyse ist für die meisten Szenarien geeignet. Diese Methode bietet Ihnen die Flexibilität, das Ausgabeformat auszuwählen: `printf` Text, XML, JSON, Database, Rest-Aufrufe usw.

Die erneute Protokollierung ist für zweckgebundene Analysen vorgesehen, die eine ETW-Ausgabedatei bilden müssen. Mithilfe von relogging können Sie die C++ buildinsights-Ereignisse in Ihr eigenes ETW-Ereignis Format übersetzen. Eine geeignete Verwendung der erneuten Protokollierung wäre C++ das Synchronisieren von buildinsights-Daten mit Ihren vorhandenen etw-Tools und-Infrastrukturen. [Vcperf](https://github.com/microsoft/vcperf) verwendet beispielsweise die relogging-Schnittstellen. Das liegt daran, dass die Daten von Windows Performance Analyzer, einem etw-Tool, erzeugt werden müssen. Einige vorherige Kenntnisse der Funktionsweise von etw sind erforderlich, wenn Sie die neuprotokollierungs Schnittstellen verwenden möchten.

### <a name="creating-analyzer-groups"></a>Erstellen von Analyse Gruppen

Es ist wichtig zu wissen, wie Sie Gruppen erstellen. Es folgt ein Beispiel, das zeigt, wie Sie eine Analyzer-Gruppe erstellen, die *Hello, World!* für jedes empfangene Aktivitäts Start Ereignis.

```cpp
using namespace Microsoft::Cpp::BuildInsights;

class Hello : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "Hello, " << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

class World : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "world!" << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

int main()
{
    Hello hello;
    World world;

    // Let's make Hello the first analyzer in the group
    // so that it receives events and prints "Hello, "
    // first.
    auto group = MakeStaticAnalyzerGroup(&hello, &world);

    unsigned numberOfAnalysisPasses = 1;

    // Calling this function initiates the analysis and
    // forwards all events from "inputTrace.etl" to my analyzer
    // group.
    Analyze("inputTrace.etl", numberOfAnalysisPasses, group);

    return 0;
}
```

## <a name="using-events"></a>Verwenden von Ereignissen

### <a name="sdk-types-and-functions-related-to-events"></a>SDK-Typen und-Funktionen im Zusammenhang mit Ereignissen

| Funktionalität | C++-API | C-API | Notizen |
|--|--|--|--|
| Abgleichen und Filtern von Ereignissen | [Matcheventstackinmembership-Funktion](functions/match-event-stack-in-member-function.md)<br />[Matcheventstack](functions/match-event-stack.md)<br />[Matcheventinmembership Function](functions/match-event-in-member-function.md)<br />[Matchevent](functions/match-event.md) |  | Die C++ API bietet Funktionen, die das Extrahieren der Ereignisse, die Sie interessieren, von ihren Ablauf Verfolgungen erleichtern. Bei der C-API muss diese Filterung von Hand durchgeführt werden. |
| Ereignis Datentypen | [Aktivität](cpp-event-data-types/activity.md)<br />[Backendpass](cpp-event-data-types/back-end-pass.md)<br />[Nach unten](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[Code Generation](cpp-event-data-types/code-generation.md)<br />[CommandLine](cpp-event-data-types/command-line.md)<br />[Versionen](cpp-event-data-types/compiler.md)<br />[Compilerpass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[Event](cpp-event-data-types/event.md)<br />[Event Group](cpp-event-data-types/event-group.md)<br />[Ereignis Stapel](cpp-event-data-types/event-stack.md)<br />[Executableimageoutput](cpp-event-data-types/executable-image-output.md)<br />[Expoutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[Forceingelinee](cpp-event-data-types/force-inlinee.md)<br />[Frontendfile](cpp-event-data-types/front-end-file.md)<br />[Frontendfilegroup](cpp-event-data-types/front-end-file-group.md)<br />[Frontendpass](cpp-event-data-types/front-end-pass.md)<br />[Function](cpp-event-data-types/function.md)<br />[Impliboutput](cpp-event-data-types/imp-lib-output.md)<br />[Aufruf](cpp-event-data-types/invocation.md)<br />[Invocationgroup](cpp-event-data-types/invocation-group.md)<br />[Liboutput](cpp-event-data-types/lib-output.md)<br />[Linker](cpp-event-data-types/linker.md)<br />[Linkergroup](cpp-event-data-types/linker-group.md)<br />[Linkerpass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[Objoutput](cpp-event-data-types/obj-output.md)<br />[Opticf](cpp-event-data-types/opt-icf.md)<br />[Optlbr](cpp-event-data-types/opt-lbr.md)<br />[Optref](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[Preltcgoptref](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[Symbolname](cpp-event-data-types/symbol-name.md)<br />[Templatin stantiations](cpp-event-data-types/template-instantiation.md)<br />[Templateingestantiationgroup](cpp-event-data-types/template-instantiation-group.md)<br />[Thread](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[Traceingefo](cpp-event-data-types/trace-info.md)<br />["Wholeprogramanalysis"](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Aktivitäten und einfache Ereignisse

Ereignisse sind in zwei Kategorien enthalten: *Aktivitäten* und *einfache Ereignisse*. Aktivitäten sind laufende Prozesse mit einem Anfang und einem Ende. Einfache Ereignisse sind Zeit punktende vorkommen und haben keine Dauer. Beim Analysieren von MSVC-Ablauf C++ Verfolgungen mit dem Build Insights SDK erhalten Sie separate Ereignisse, wenn eine Aktivität startet und beendet wird. Sie erhalten nur ein Ereignis, wenn ein einfaches Ereignis auftritt.

### <a name="parent-child-relationships"></a>Über-/Unterordnungsbeziehungen

Aktivitäten und einfache Ereignisse sind über Beziehungen zwischen übergeordneten und untergeordneten Elementen miteinander verknüpft. Das übergeordnete Element einer Aktivität oder eines einfachen Ereignisses ist die umfassende Aktivität, in der Sie auftreten. Wenn Sie z. b. eine Quelldatei kompilieren, muss der Compiler die Datei analysieren und dann den Code generieren. Die Aktivitäten für die Verarbeitung und die Codegenerierung sind beide untergeordnete Elemente der compileraktivität.

Einfache Ereignisse haben keine Dauer, daher kann nichts anderes vorkommen. Daher haben Sie niemals untergeordnete Elemente.

Die Beziehungen zwischen übergeordneten und untergeordneten Elementen der einzelnen Aktivitäten und einfachen Ereignisse werden in der [Ereignis Tabelle](event-table.md)angegeben. Das Wissen dieser Beziehungen ist wichtig, C++ Wenn Sie buildinsights-Ereignisse verarbeiten. Häufig müssen Sie sich darauf verlassen, dass Sie den vollständigen Kontext eines Ereignisses verstehen.

### <a name="properties"></a>Eigenschaften

Alle Ereignisse verfügen über die folgenden Eigenschaften:

| Eigenschaft | BESCHREIBUNG |
|--|--|
| Typbezeichner | Eine Zahl, die den Ereignistyp eindeutig identifiziert. |
| Instanzbezeichner | Eine Zahl, die das Ereignis innerhalb der Ablauf Verfolgung eindeutig identifiziert. Wenn zwei Ereignisse desselben Typs in einer Ablauf Verfolgung auftreten, erhalten beide einen eindeutigen Instanzbezeichner. |
| Startzeit | Der Zeitpunkt, zu dem eine Aktivität gestartet wurde, oder der Zeitpunkt, zu dem ein einfaches Ereignis aufgetreten ist. |
| Prozess-ID | Eine Zahl, die den Prozess angibt, in dem das Ereignis aufgetreten ist. |
| Thread Bezeichner | Eine Zahl, die den Thread identifiziert, in dem das Ereignis aufgetreten ist. |
| Prozessor Index | Ein NULL basierter Index, der den logischen Prozessor angibt, von dem das Ereignis ausgegeben wurde. |
| Ereignisname | Eine Zeichenfolge, die den Ereignistyp beschreibt. |

Alle Aktivitäten, die keine einfachen Ereignisse sind, haben auch folgende Eigenschaften:

| Eigenschaft | BESCHREIBUNG |
|--|--|
| Endzeit | Der Zeitpunkt, zu dem die Aktivität beendet wurde. |
| Exklusive Dauer | Die Zeit, die für eine Aktivität aufgewendet wurde, ohne die Zeit, die in den untergeordneten Aktivitäten aufgewendet wurde. |
| CPU-Zeit | Die Zeit, die die CPU für das Ausführen von Code in dem an die Aktivität angefügten Thread aufgewendet hat. Es schließt keine Zeit ein, zu der der an die Aktivität angefügte Thread in den Standbymodus |
| Exklusive CPU-Zeit | Identisch mit der CPU-Zeit, aber ohne die CPU-Zeit, die von untergeordneten Aktivitäten aufgewendet wurde. |
| Verantwortung für die Wand Uhrzeit | Der Beitrag der Aktivität zur Gesamtzeit der Gesamtzeit. Bei der Wand-/Uhrzeit-Verantwortlichkeit wird die Parallelität zwischen Aktivitäten berücksichtigt. Nehmen wir beispielsweise an, dass zwei nicht verknüpfte Aktivitäten parallel ausgeführt werden. Beide haben eine Dauer von 10 Sekunden und genau dieselbe Start-und Endzeit. In diesem Fall weist die Erstellungs Informationen sowohl eine Aufgabe für die Zeit der Computerzeit von 5 Sekunden zu. Wenn diese Aktivitäten dagegen nacheinander und ohne Überlappung ausgeführt werden, wird Ihnen jeweils die Aufgabe "Wall-Clock-Zeit" von 10 Sekunden zugewiesen. |
| Exklusive Aufgabe der Wall-Clock-Zeit | Identisch mit der Verantwortung für die Gesamtzeit, aber schließt die Zeit in Bezug auf die Zeit der untergeordneten Aktivitäten aus. |

Einige Ereignisse haben neben den erwähnten Eigenschaften ihre eigenen Eigenschaften. In diesem Fall sind diese zusätzlichen Eigenschaften in der [Ereignis Tabelle](event-table.md)aufgeführt.

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Verarbeiten von Ereignissen, die C++ vom Build Insights SDK bereitgestellt werden

#### <a name="the-event-stack"></a>Der Ereignis Stapel

Jedes Mal C++ , wenn das Build Insights SDK ein Ereignis liefert, wird es in Form eines Stapels angezeigt. Der letzte Eintrag im Stapel ist das aktuelle Ereignis und Einträge vor der übergeordneten Hierarchie. Beispielsweise treten während der Übergabe 1 des Linkers [LTCG](event-table.md#ltcg) -Ereignisse zum Starten und Abbrechen auf. In diesem Fall enthält der Stapel, den Sie erhalten, Folgendes: \[[Linker](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. Die übergeordnete Hierarchie ist praktisch, da Sie ein Ereignis auf seinen Stamm zurückverfolgen können. Wenn die oben genannte LTCG-Aktivität langsam ist, können Sie sofort ermitteln, welcher Linker Aufruf beteiligt war.

#### <a name="matching-events-and-event-stacks"></a>Übereinstimmende Ereignisse und Ereignis Stapel

Das C++ buildinsights-SDK gibt Ihnen jedes Ereignis in einer Ablauf Verfolgung, aber in den meisten Fällen ist nur eine Teilmenge davon wichtig. In einigen Fällen ist es möglicherweise nur eine Teilmenge von *Ereignis Stapeln*wichtig. Das SDK stellt Funktionen bereit, mit deren Hilfe Sie schnell die benötigten Ereignisse oder Ereignis Stapel extrahieren und diejenigen ablehnen können, die Sie nicht benötigen. Dies erfolgt über diese abgleichsfunktionen:

|  |  |
|--|--|
| [Matchevent](functions/match-event.md) | Behalten Sie ein Ereignis bei, wenn es mit einem der angegebenen Typen übereinstimmt. Leiten Sie übereinstimmende Ereignisse an einen Lambda-oder einen anderen Aufruf baren Typ weiter. Die übergeordnete Hierarchie des Ereignisses wird von dieser Funktion nicht berücksichtigt. |
| [Matcheventinmembership Function](functions/match-event-in-member-function.md) | Behalten Sie ein Ereignis bei, wenn es mit dem im-Parameter der Element Funktion angegebenen Typ übereinstimmt. Leiten Sie übereinstimmende Ereignisse an die Element Funktion weiter. Die übergeordnete Hierarchie des Ereignisses wird von dieser Funktion nicht berücksichtigt. |
| [Matcheventstack](functions/match-event-stack.md) | Behalten Sie ein Ereignis bei, wenn sowohl das Ereignis als auch seine übergeordnete Hierarchie den angegebenen Typen entsprechen. Leiten Sie das Ereignis und die übereinstimmenden übergeordneten Hierarchie Ereignisse an einen Lambda-oder einen anderen Aufruf baren Typ weiter. |
| [Matcheventstackinmembership-Funktion](functions/match-event-stack-in-member-function.md) | Behalten Sie ein Ereignis bei, wenn sowohl das Ereignis als auch seine übergeordnete Hierarchie mit den in der Parameterliste der Element Funktion angegebenen Typen identisch sind. Leiten Sie das Ereignis und die übereinstimmenden übergeordneten Hierarchie Ereignisse an die Element Funktion weiter. |

Die Ereignis Stapel abgleichsfunktionen wie `MatchEventStack` mögliche Lücken bei der Beschreibung der Übereinstimmung der übergeordneten Hierarchie zulassen. Angenommen, Sie interessieren sich für den \[[Linker](event-table.md#linker), [LTCG](event-table.md#ltcg)\] Stack. Es würde auch der \[Linker, [PASS1](event-table.md#pass1), LTCG\] Stack entsprechen. Der letzte angegebene Typ muss dem Ereignistyp entsprechen, der abgeglichen werden soll, und ist nicht Teil der übergeordneten Hierarchie.

#### <a name="capture-classes"></a>Erfassungs Klassen

Die Verwendung der `Match*` Funktionen erfordert, dass Sie die Typen angeben, die Sie vergleichen möchten. Diese Typen werden aus einer Liste von *Erfassungs Klassen*ausgewählt. Erfassungs Klassen sind in verschiedenen Kategorien enthalten, die unten beschrieben werden.

| Category | BESCHREIBUNG |
|--|--|
| Exact | Diese Erfassungs Klassen werden verwendet, um einen bestimmten Ereignistyp und keinen anderen abzugleichen. Ein Beispiel hierfür ist die [compilerklasse](cpp-event-data-types/compiler.md) , die mit dem [compilerereignis](event-table.md#compiler) übereinstimmt. |
| Platzhalter | Diese Erfassungs Klassen können verwendet werden, um beliebige Ereignisse aus der Liste der von Ihnen unterstützten Ereignisse abzugleichen. Beispielsweise entspricht der [Aktivitäts](cpp-event-data-types/activity.md) Platzhalter jedem Aktivitäts Ereignis. Ein weiteres Beispiel ist der " [compilerpass](cpp-event-data-types/compiler-pass.md) "-Platzhalter, der entweder der [FRONT_END_PASS](event-table.md#front-end-pass) oder dem [BACK_END_PASS](event-table.md#back-end-pass) -Ereignis entsprechen kann. |
| Group | Die Namen der Gruppen Erfassungs Klassen enden in der *Gruppe*. Sie werden verwendet, um mehrere Ereignisse desselben Typs in einer Zeile abzugleichen, wobei Lücken ignoriert werden. Sie sind nur sinnvoll, wenn rekursive Ereignisse abgeglichen werden, da Sie nicht wissen, wie viele im Ereignis Stapel vorhanden sind. Beispielsweise erfolgt die [FRONT_END_FILE](event-table.md#front-end-file) Aktivität jedes Mal, wenn der Compiler eine Datei analysiert. Diese Aktivität ist rekursiv, da der Compiler möglicherweise eine include-Direktive findet, während er die Datei verarbeitet. Die [frontendfile](cpp-event-data-types/front-end-file.md) -Klasse stimmt nur mit einem FRONT_END_FILE Ereignis im Stapel überein. Verwenden Sie die [frontendfilegroup](cpp-event-data-types/front-end-file-group.md) -Klasse, um die gesamte include-Hierarchie abzugleichen. |
| Platzhalter Gruppe | Eine Platzhalter Gruppe kombiniert die Eigenschaften von Platzhaltern und Gruppen. Die einzige Klasse dieser Kategorie ist [invocationgroup](cpp-event-data-types/invocation-group.md), die alle [Linker](event-table.md#linker) -und [compilerereignisse](event-table.md#compiler) in einem einzelnen Ereignis Stapel abgleichen und aufzeichnen. |

In der [Ereignis Tabelle](event-table.md) erfahren Sie, welche Aufzeichnungs Klassen verwendet werden können, um die einzelnen Ereignisse abzugleichen.

#### <a name="after-matching-using-captured-events"></a>Nach dem Abgleich: Verwenden von aufgezeichneten Ereignissen

Nachdem eine Abgleich erfolgreich abgeschlossen wurde, erstellen die `Match*` Funktionen die Erfassungs Klassen Objekte und leiten Sie an die angegebene Funktion weiter. Verwenden Sie diese Objekte der Erfassungs Klasse, um auf die Eigenschaften der Ereignisse zuzugreifen.

#### <a name="example"></a>Beispiel

```cpp
AnalysisControl MyAnalyzer::OnStartActivity(const EventStack& eventStack)
{
    // The event types to match are specified in the PrintIncludes function
    // signature.  
    MatchEventStackInMemberFunction(eventStack, this, &MyAnalyzer::PrintIncludes);
}

// We want to capture event stacks where:
// 1. The current event is a FrontEndFile activity.
// 2. The current FrontEndFile activity has at least one parent FrontEndFile activity
//    and possibly many.
void PrintIncludes(FrontEndFileGroup parentIncludes, FrontEndFile currentFile)
{
    // Once we reach this point, the event stack we are interested in has been matched.
    // The current FrontEndFile activity has been captured into 'currentFile', and
    // its entire inclusion hierarchy has been captured in 'parentIncludes'.

    cout << "The current file being parsed is: " << currentFile.Path() << endl;
    cout << "This file was reached through the following inclusions:" << endl;

    for (auto& f : parentIncludes)
    {
        cout << f.Path() << endl;
    }
}
```

::: moniker-end
