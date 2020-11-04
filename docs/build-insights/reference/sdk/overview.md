---
title: C++ Build Insights SDK
description: Eine Übersicht zum C++ Build Insights SDK in Visual Studio.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a6ecff81a9f3d2b22107a8fa7fc26fad85d4f579
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919513"
---
# <a name="c-build-insights-sdk"></a>C++ Build Insights SDK

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Das C++ Build Insights SDK ist eine Sammlung von APIs, die Ihnen ermöglichen, personalisierte Tools auf der C++ Build Insights-Plattform zu erstellen. Auf dieser Seite finden Sie eine allgemeine Übersicht, die Ihnen den Einstieg erleichtern soll.

## <a name="obtaining-the-sdk"></a>Abrufen des SDK

Sie können das C++ Build Insights SDK mit folgenden Schritten als NuGet-Paket herunterladen:

1. Erstellen Sie in Visual Studio 2017 und höher ein neues C++-Projekt.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf Ihr Projekt.
1. Wählen Sie im Kontextmenü **NuGet-Pakete verwalten** aus.
1. Wählen Sie oben rechts die **nuget.org** -Paketquelle aus.
1. Suchen Sie nach der neuesten Version des Pakets Microsoft.Cpp.BuildInsights.
1. Wählen Sie **Installieren** aus.
1. Akzeptieren Sie die Lizenzbedingungen.

Lesen Sie die weiteren Informationen zu den allgemeinen Konzepten im Zusammenhang mit dem SDK. Sie können auch auf das offizielle [GitHub-Repository mit C++ Build Insights-Beispielen](https://github.com/microsoft/cpp-build-insights-samples) zugreifen, um Beispiele echter C++-Anwendungen anzuzeigen, die das SDK verwenden.

## <a name="collecting-a-trace"></a>Erfassen einer Ablaufverfolgung

Wenn Sie mit dem C++ Build Insights SDK Ereignisse aus der MSVC-Toolkette analysieren, müssen Sie zuerst eine Ablaufverfolgung erfassen. Das SDK nutzt die Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW) als grundlegende Ablaufverfolgungstechnologie. Das Erfassen einer Ablaufverfolgung kann auf zwei Arten erfolgen:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Methode 1: Verwenden von vcperf in Visual Studio 2019 und höher

1. Öffnen einer x64 Native Tools-Eingabeaufforderung mit erhöhten Rechten für VS 2019.
1. Führen Sie den folgenden Befehl aus: `vcperf /start MySessionName`
1. Erstellen Sie Ihr Projekt.
1. Führen Sie den folgenden Befehl aus: `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Beenden Sie die Ablaufverfolgung mit vcperf mit dem `/stopnoanalyze`-Befehl. Sie können mit dem C++ Build Insights SDK keine Ablaufverfolgungen analysieren, die mit dem regulären `/stop`-Befehl beendet wurden.

### <a name="method-2-programmatically"></a>Methode 2: programmgesteuert

Verwenden Sie eine dieser C++ Build Insights SDK-Funktionen zum Erfassen von Ablaufverfolgungen, um Ablaufverfolgungen programmgesteuert zu starten und zu beenden. **Das Programm, das diese Funktionsaufrufe ausführt, muss über Administratorrechte verfügen.** Nur die Funktionen zum Starten und Beenden von Ablaufverfolgungsfunktionen erfordern Administratorrechte. Alle anderen Funktionen im C++ Build Insights SDK können ohne sie ausgeführt werden.

### <a name="sdk-functions-related-to-trace-collection"></a>SDK-Funktionen zum Erfassen von Ablaufverfolgungen

| Funktionalität | C++-API | C-API |
|--|--|--|
| Starten einer Ablaufverfolgung | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Beenden einer Ablaufverfolgung | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| Beenden einer Ablaufverfolgung und<br />sofortiges Analysieren des Ergebnisses | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| Beenden einer Ablaufverfolgung und<br />sofortige Neuprotokollierung des Ergebnisses | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

In den folgenden Abschnitten wird gezeigt, wie Sie eine Analyse- oder eine Neuprotokollierungssitzung konfigurieren. Dies ist für die Funktionen mit kombinierter Funktionalität wie [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) erforderlich.

## <a name="consuming-a-trace"></a>Nutzen einer Ablaufverfolgung

Wenn Sie über eine ETW-Ablaufverfolgung verfügen, entpacken Sie sie mit dem C++ Build Insights SDK. Das SDK stellt Ihnen die Ereignisse in einem Format bereit, mit dem Sie Ihre Tools schnell entwickeln können. Sie sollten die ETW-Ablaufverfolgung nicht ohne das SDK verwenden. Das von MSVC verwendete Ereignisformat ist undokumentiert, zur Skalierung für umfangreiche Builds optimiert und schwer zu verstehen. Außerdem ist die C++ Build Insights SDK-API beständig, während das reine ETW-Format ohne vorherige Ankündigung geändert werden kann.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>SDK-Typen und -Funktionen im Zusammenhang mit der Nutzung der Ablaufverfolgung

| Funktionalität | C++-API | C-API | Hinweise |
|--|--|--|--|
| Einrichten von Ereignisrückrufen | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | Das C++ Build Insights SDK stellt Ereignisse mithilfe von Rückruffunktionen bereit. Implementieren Sie in C++ die Rückruffunktionen, indem Sie eine Analysetool- oder Reloggerklasse erstellen, die die IAnalyzer- oder IRelogger-Schnittstelle erbt. Implementieren Sie in C die Rückrufe in globalen Funktionen, und stellen Sie in der ANALYSIS_CALLBACKS- oder RELOG_CALLBACKS-Struktur Zeiger darauf bereit. |
| Erstellen von Gruppen | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | Die C++-API stellt Hilfsfunktionen und -typen bereit, um mehrere Analysetool- und Reloggerobjekte zu gruppieren. Gruppen sind eine gute Möglichkeit, eine komplexe Analyse in einfachere Schritte aufzuteilen. [vcperf](https://github.com/microsoft/vcperf) ist auf diese Weise organisiert. |
| Analysieren oder erneut protokollieren | [Analysieren](functions/analyze.md)<br />[Relog](functions/relog.md) | [AnalyzeA](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analysieren und erneut protokollieren

Die Nutzung einer Ablaufverfolgung erfolgt entweder über eine Analyse- oder eine Neuprotokollierungssitzung.

Die Verwendung einer regulären Analyse ist für die meisten Szenarien geeignet. Diese Methode bietet Ihnen die Flexibilität, das Ausgabeformat auszuwählen: `printf`-Text, XML, JSON, Datenbank, REST-Aufrufe usw.

Die Neuprotokollierung ist für zweckgebundene Analysen vorgesehen, die eine ETW-Ausgabedatei produzieren müssen. Mithilfe der Neuprotokollierung können Sie die C++ Build Insights-Ereignisse in Ihr eigenes ETW-Ereignisformat übersetzen. Eine geeignete Verwendung der Neuprotokollierung wäre, die C++ Build Insights-Daten in Ihre vorhandenen ETW-Tools und Ihre Infrastruktur einzubinden. Beispielsweise verwendet [vcperf](https://github.com/microsoft/vcperf) die Schnittstellen der Neuprotokollierung. Das liegt daran, dass Daten erzeugt werden müssen, die der Windows Performance Analyzer – ein ETW-Tool – versteht. Wenn Sie die Schnittstellen der Neuprotokollierung verwenden möchten, benötigen Sie Vorkenntnisse der Funktionsweise von ETW.

### <a name="creating-analyzer-groups"></a>Erstellen von Analysetoolgruppen

Sie müssen wissen, wie Gruppen erstellt werden. Das folgende Beispiel zeigt, wie eine Analysetoolgruppe erstellt wird, die *Hello, World!* für jedes Aktivitätsstartereignis ausgibt, das sie empfängt.

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

### <a name="sdk-types-and-functions-related-to-events"></a>SDK-Typen und -Funktionen im Zusammenhang mit Ereignissen

| Funktionalität | C++-API | C-API | Hinweise |
|--|--|--|--|
| Abgleichen und Filtern von Ereignissen | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | Die C++-API bietet Funktionen, die Ihnen erleichtern, die Ereignisse aus Ihren Ablaufverfolgungen zu extrahieren, die Sie interessieren. Bei der C-API muss diese Filterung manuell erfolgen. |
| Ereignisdatentypen | [Aktivität](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration](cpp-event-data-types/code-generation.md)<br />[CommandLine](cpp-event-data-types/command-line.md)<br />[Compiler](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[Event](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Function](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[Aufruf](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[Linker](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[Thread](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Aktivitäten und einfache Ereignisse

Ereignisse lassen sich in zwei Kategorien einteilen: *Aktivitäten* und *einfache Ereignisse*. Aktivitäten sind in einem Zeitraum ablaufende Prozesse mit Anfang und Ende. Einfache Ereignisse sind punktuelle Vorkommnisse ohne Dauer. Beim Analysieren von MSVC-Ablaufverfolgungen mit dem C++ Build Insights SDK erhalten Sie separate Ereignisse, wenn eine Aktivität startet und endet. Sie erhalten nur ein Ereignis, wenn ein einfaches Ereignis auftritt.

### <a name="parent-child-relationships"></a>Beziehungen zwischen übergeordneten und untergeordneten Elementen

Aktivitäten und einfache Ereignisse sind über Beziehungen zwischen übergeordneten und untergeordneten Elementen miteinander verknüpft. Das übergeordnete Element von Aktivitäten oder einfachen Ereignissen ist die umfassende Aktivität, in der sie auftreten. Wenn Sie z. B. eine Quelldatei kompilieren, muss der Compiler die Datei analysieren und dann den Code generieren. Die Aktivitäten für Analyse und Codegenerierung sind beide untergeordnete Elemente der Compileraktivität.

Da einfache Ereignisse keine Dauer haben, kann innerhalb einfacher Ereignisse nichts anderes geschehen. Folglich haben sie niemals untergeordnete Elemente.

Die Beziehungen zwischen übergeordneten und untergeordneten Elementen der einzelnen Aktivitäten und einfachen Ereignisse werden in der [Ereignistabelle](event-table.md) angegeben. Wenn Sie C++ Build Insights-Ereignisse nutzen, müssen Sie diese Beziehungen kennen. Häufig müssen Sie sich auf sie verlassen, um den vollständigen Kontext eines Ereignisses zu verstehen.

### <a name="properties"></a>Eigenschaften

Alle Ereignisse verfügen über folgende Eigenschaften:

| Eigenschaft | BESCHREIBUNG |
|--|--|
| Typbezeichner | Eine Zahl, die den Ereignistyp eindeutig identifiziert. |
| Instanzbezeichner | Eine Zahl, die das Ereignis innerhalb der Ablaufverfolgung eindeutig identifiziert. Wenn zwei Ereignisse desselben Typs in einer Ablaufverfolgung auftreten, erhalten beide einen eindeutigen Instanzbezeichner. |
| Startzeit | Der Zeitpunkt, zu dem eine Aktivität gestartet wurde, oder der Zeitpunkt, zu dem ein einfaches Ereignis auftrat. |
| Prozessbezeichner | Eine Zahl, die den Prozess identifiziert, in dem das Ereignis auftrat. |
| Threadbezeichner | Eine Zahl, die den Thread identifiziert, in dem das Ereignis auftrat. |
| Prozessorindex | Ein auf 0 (null) basierender Index, der den logischen Prozessor angibt, von dem das Ereignis ausgegeben wurde. |
| Ereignisname | Eine Zeichenfolge, die den Ereignistyp beschreibt. |

Alle Aktivitäten, die keine einfachen Ereignisse sind, haben auch folgende Eigenschaften:

| Eigenschaft | BESCHREIBUNG |
|--|--|
| Endzeit | Der Zeitpunkt, zu dem die Aktivität beendet wurde. |
| Exklusive Dauer | Die für eine Aktivität aufgewendete Zeit mit Ausnahme der in den untergeordneten Aktivitäten aufgewendeten Zeit. |
| CPU-Zeit | Die Zeit, die die CPU für das Ausführen von Code in dem der Aktivität angefügten Thread aufgewendet hat. Die Zeit, für die der der Aktivität angefügte Thread sich im Ruhezustand befand, ist darin nicht enthalten. |
| Exklusive CPU-Zeit | CPU-Zeit ohne die für untergeordnete Aktivitäten aufgewendete CPU-Zeit. |
| Gesamtbetrachtungszeit-Verantwortung | Der Beitrag der Aktivität zur Gesamtbetrachtungszeit. Die Gesamtbetrachtungszeit berücksichtigt die Parallelität zwischen Aktivitäten. Nehmen wir beispielsweise an, dass zwei nicht verknüpfte Aktivitäten parallel ausgeführt werden. Beide haben eine Dauer von 10 Sekunden und genau dieselbe Start- und Endzeit. In diesem Fall weist Build Insights beiden eine Gesamtbetrachtungszeit-Verantwortung von 5 Sekunden zu. Wenn diese Aktivitäten dagegen nacheinander und ohne Überlappung ausgeführt werden, wird ihnen jeweils eine Gesamtbetrachtungszeit-Verantwortung von 10 Sekunden zugewiesen. |
| Exklusive Gesamtbetrachtungszeit-Verantwortung | Gesamtbetrachtungszeit-Verantwortung mit Ausnahme der Gesamtbetrachtungszeit-Verantwortung untergeordneter Aktivitäten. |

Einige Ereignisse haben neben den erwähnten Eigenschaften eigene Eigenschaften. In diesem Fall werden diese zusätzlichen Eigenschaften in der [Ereignistabelle](event-table.md) aufgelistet.

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Nutzen von Ereignissen, die vom C++ Build Insights SDK bereitgestellt werden

#### <a name="the-event-stack"></a>Der Ereignisstapel

Immer dann, wenn das C++ Build Insights SDK ein Ereignis meldet, wird es in Form eines Stapels bereitgestellt. Der letzte Eintrag im Stapel ist das aktuelle Ereignis, und die Einträge davor sind ihm übergeordnet. Beispielsweise treten das [LTCG](event-table.md#ltcg)-Start- und Endeereignis während des ersten Linkerdurchlaufs auf. In diesem Fall enthält der Stapel, den Sie erhalten, Folgendes: \[[LINKER](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. Die übergeordnete Hierarchie ist praktisch, da Sie so ein Ereignis auf seine Ursache zurückverfolgen können. Wenn die oben genannte LTCG-Aktivität langsam ist, können Sie sofort ermitteln, welcher Linkeraufruf beteiligt war.

#### <a name="matching-events-and-event-stacks"></a>Abgleichen von Ereignissen und Ereignisstapeln

Das C++ Build Insights SDK stellt Ihnen jedes Ereignis in einer Ablaufverfolgung bereit, aber in den meisten Fällen ist nur eine Teilmenge davon wichtig. In einigen Fällen ist möglicherweise nur eine Teilmenge der *Ereignisstapel* für Sie interessant. Mithilfe des SDK können Sie schnell die benötigten Ereignisse oder Ereignisstapel extrahieren und diejenigen ablehnen, die Sie nicht benötigen. Dies erfolgt über diese Abgleichsfunktionen:

| Funktion | BESCHREIBUNG |
|--|--|
| [MatchEvent](functions/match-event.md) | Beibehalten eines Ereignisses, wenn es mit einem der angegebenen Typen übereinstimmt. Weiterleiten übereinstimmender Ereignisse an eine Lambdafunktion oder einen anderen aufrufbaren Typ. Die übergeordnete Hierarchie des Ereignisses wird von dieser Funktion nicht berücksichtigt. |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | Beibehalten eines Ereignisses, wenn es mit dem in einem Parameter der Memberfunktion angegebenen Typen übereinstimmt. Weiterleiten übereinstimmender Ereignisse an eine Memberfunktion. Die übergeordnete Hierarchie des Ereignisses wird von dieser Funktion nicht berücksichtigt. |
| [MatchEventStack](functions/match-event-stack.md) | Beibehalten eines Ereignisses, wenn sowohl das Ereignis als auch seine übergeordnete Hierarchie den angegebenen Typen entspricht. Weiterleiten des Ereignisses und der übereinstimmenden Ereignisse der übergeordneten Hierarchie an eine Lambdafunktion oder einen anderen aufrufbaren Typen. |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | Beibehalten eines Ereignisses, wenn sowohl das Ereignis als auch seine übergeordnete Hierarchie den in der Parameterliste einer Memberfunktion angegebenen Typen entspricht. Weiterleiten des Ereignisses und der übereinstimmenden Ereignisse der übergeordneten Hierarchie an die Memberfunktion. |

Die Ereignisstapel-Abgleichsfunktionen wie `MatchEventStack` lassen Lücken bei der Beschreibung der abzugleichenden übergeordneten Hierarchie zu. Sie interessieren sich z. B. für den Stapel \[[Linker](event-table.md#linker), [LTCG](event-table.md#ltcg)\]. Dies würde auch dem Stapel \[LINKER, [PASS1](event-table.md#pass1), LTCG\] entsprechen. Der letzte angegebene Typ muss dem Ereignistyp entsprechen, der abgeglichen werden soll, und ist nicht Teil der übergeordneten Hierarchie.

#### <a name="capture-classes"></a>Erfassungsklassen

Die Verwendung der `Match*`-Funktionen erfordert, dass Sie die Typen angeben, die Sie abgleichen möchten. Diese Typen werden aus einer Liste von *Erfassungsklassen* ausgewählt. Erfassungsklassen sind in verschiedenen Kategorien enthalten, die unten beschrieben werden.

| Category | BESCHREIBUNG |
|--|--|
| Exact | Diese Erfassungsklassen werden verwendet, um einen bestimmten Ereignistyp und keinen anderen abzugleichen. Ein Beispiel hierfür ist die [Compiler](cpp-event-data-types/compiler.md)-Klasse zum Abgleich des [COMPILER](event-table.md#compiler)-Ereignisses. |
| Platzhalter | Diese Erfassungsklassen können verwendet werden, um beliebige Ereignisse aus der Liste der von Ihnen unterstützten Ereignisse abzugleichen. Beispielsweise entspricht der [Activity](cpp-event-data-types/activity.md)-Platzhalter jedem Aktivitätsereignis. Ein weiteres Beispiel ist der [CompilerPass](cpp-event-data-types/compiler-pass.md)-Platzhalter, der entweder dem [FRONT_END_PASS](event-table.md#front-end-pass)- oder dem [BACK_END_PASS](event-table.md#back-end-pass)-Ereignis entsprechen kann. |
| Group | Die Namen der Gruppenerfassungsklassen enden mit *Group*. Sie werden verwendet, um mehrere Ereignisse desselben Typs in einer Zeile abzugleichen, wobei Lücken ignoriert werden. Sie sind nur sinnvoll, wenn rekursive Ereignisse abgeglichen werden, da Sie nicht wissen, wie viele im Ereignisstapel vorhanden sind. Beispielsweise erfolgt die [FRONT_END_FILE](event-table.md#front-end-file)-Aktivität jedes Mal, wenn der Compiler eine Datei analysiert. Diese Aktivität ist rekursiv, da der Compiler möglicherweise bei der Analyse der Datei eine Include-Direktive findet. Die [FrontEndFile](cpp-event-data-types/front-end-file.md)-Klasse stimmt nur mit einem FRONT_END_FILE-Ereignis im Stapel überein. Verwenden Sie die Klasse [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md), um die gesamte Include-Hierarchie abzugleichen. |
| Platzhaltergruppe | Eine Platzhaltergruppe vereinigt in sich die Eigenschaften von Platzhaltern und Gruppen. Die einzige Klasse dieser Kategorie ist [InvocationGroup](cpp-event-data-types/invocation-group.md), die alle [LINKER](event-table.md#linker)- und [COMPILER](event-table.md#compiler)-Ereignisse in einem einzelnen Ereignisstapel abgleicht und erfasst. |

Informationen zu den Erfassungsklassen, die verwendet werden können, um die einzelnen Ereignisse abzugleichen, finden Sie in der [Ereignistabelle](event-table.md).

#### <a name="after-matching-using-captured-events"></a>Nach dem Abgleich: Verwenden von aufgezeichneten Ereignissen

Nach erfolgreichem Abschluss eines Abgleichs erstellen die `Match*`-Funktionen die Erfassungsklassenobjekte und leiten sie an die angegebene Funktion weiter. Verwenden Sie diese Objekte der Erfassungsklasse zum Zugriff auf die Eigenschaften der Ereignisse.

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
