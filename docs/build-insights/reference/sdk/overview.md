---
title: C++ Build Insights SDK
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
ms.openlocfilehash: 126abb0d039227eb269500966d46ef0a729763ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323266"
---
# <a name="c-build-insights-sdk"></a>C++ Build Insights SDK

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Das C++ Build Insights SDK ist eine Sammlung von APIs, mit denen Sie personalisierte Tools auf der C++Build Insights-Plattform erstellen können. Diese Seite bietet eine Übersicht auf hoher Ebene, die Ihnen den Einstieg erleichtern.

## <a name="obtaining-the-sdk"></a>Abrufen des SDK

Sie können das C++ Build Insights SDK als NuGet-Paket herunterladen, indem Sie die folgenden Schritte ausführen:

1. Erstellen Sie in Visual Studio 2017 und höher ein neues C++-Projekt.
1. Klicken Sie im Bereich **Projektmappen-Explorer** mit der rechten Maustaste auf Ihr Projekt.
1. Wählen Sie **NuGet-Pakete** verwalten aus dem Kontextmenü aus.
1. Wählen Sie oben rechts die **nuget.org** Paketquelle aus.
1. Suchen Sie nach der neuesten Version des Microsoft.Cpp.BuildInsights-Pakets.
1. Wählen Sie **Installieren**.
1. Akzeptieren Sie die Lizenz.

Lesen Sie weiter, um Informationen zu den allgemeinen Konzepten rund um das SDK zu erhalten. Sie können auch auf das offizielle [C++-Build-Insights-Beispiel-GitHub-Repository](https://github.com/microsoft/cpp-build-insights-samples) zugreifen, um Beispiele für echte C++-Anwendungen zu sehen, die das SDK verwenden.

## <a name="collecting-a-trace"></a>Sammeln einer Spur

Wenn Sie das C++ Build Insights SDK verwenden, um Ereignisse zu analysieren, die aus der MSVC-Toolchain stammen, müssen Sie zuerst eine Ablaufverfolgung sammeln. Das SDK verwendet Event Tracing for Windows (ETW) als zugrunde liegende Ablaufverfolgungstechnologie. Das Sammeln einer Ablaufverfolgung kann auf zwei Arten erfolgen:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Methode 1: Verwenden von vcperf in Visual Studio 2019 und höher

1. Öffnen Sie eine erhöhte x64 Native Tools-Eingabeaufforderung für VS 2019.
1. Führen Sie den folgenden Befehl aus: `vcperf /start MySessionName`
1. Erstellen Sie Ihr Projekt.
1. Führen Sie den folgenden Befehl aus: `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Verwenden `/stopnoanalyze` Sie den Befehl, wenn Sie die Ablaufverfolgung mit vcperf beenden. Sie können das C++Build Insights SDK nicht verwenden, `/stop` um Ablaufverfolgungen zu analysieren, die mit dem regulären Befehl angehalten wurden.

### <a name="method-2-programmatically"></a>Methode 2: programmgesteuert

Verwenden Sie eine dieser C++ Build Insights SDK-Ablaufverfolgungsauflistungsfunktionen, um Ablaufverfolgungen programmgesteuert zu starten und zu beenden. **Das Programm, das diese Funktionsaufrufe ausführt, muss über Administratorrechte verfügen.** Nur die Start- und Stoppprotokollierungsfunktionen erfordern Administratorrechte. Alle anderen Funktionen im C++ Build Insights SDK können ohne sie ausgeführt werden.

### <a name="sdk-functions-related-to-trace-collection"></a>SDK-Funktionen im Zusammenhang mit der Ablaufverfolgungsauflistung

| Funktionalität | C++-API | C-API |
|--|--|--|
| Starten einer Ablaufverfolgung | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Beenden einer Ablaufverfolgung | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| Stoppen einer Spur und<br />sofort das Ergebnis analysieren | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| Stoppen einer Spur und<br />sofort das Ergebnis erneut protokollieren | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

In den folgenden Abschnitten erfahren Sie, wie Sie eine Analyse oder eine Relogging-Sitzung konfigurieren. Es ist für die kombinierten Funktionsfunktionen erforderlich, z. B. [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Verwenden einer Spur

Sobald Sie über eine ETW-Ablaufverfolgung verfügen, verwenden Sie das C++ Build Insights SDK, um sie zu entpacken. Das SDK bietet Ihnen die Ereignisse in einem Format, mit dem Sie Ihre Tools schnell entwickeln können. Es wird nicht empfohlen, die unformatierte ETW-Ablaufverfolgung zu verwenden, ohne das SDK zu verwenden. Das von MSVC verwendete Ereignisformat ist nicht dokumentiert, für die Skalierung auf riesige Builds optimiert und schwer sinnvoll. Darüber hinaus ist die C++ Build Insights SDK-API stabil, während sich das unformatierte ETW-Ablaufverfolgungsformat ohne vorherige Ankündigung ändern kann.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>SDK-Typen und -Funktionen im Zusammenhang mit dem Ablaufverfolgungsverbrauch

| Funktionalität | C++-API | C-API | Notizen |
|--|--|--|--|
| Einrichten von Ereignisrückrufen | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | Das C++ Build Insights SDK stellt Ereignisse über Rückruffunktionen bereit. Implementieren Sie in C++ die Rückruffunktionen, indem Sie eine Analyzer- oder Reloggerklasse erstellen, die die IAnalyzer- oder IRelogger-Schnittstelle erbt. Implementieren Sie in C die Rückrufe in globalen Funktionen und stellen Sie Hinweise darauf in der ANALYSIS_CALLBACKS- oder RELOG_CALLBACKS-Struktur bereit. |
| Aufbau von Gruppen | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | Die C++-API bietet Hilfsfunktionen und -typen zum Gruppieren mehrerer Analysaor- und Reloggerobjekte. Gruppen sind eine saubere Möglichkeit, eine komplexe Analyse in einfachere Schritte aufzuteilen. [vcperf](https://github.com/microsoft/vcperf) ist auf diese Weise organisiert. |
| Analysieren oder Relogging | [Analysieren](functions/analyze.md)<br />[Relog](functions/relog.md) | [AnalyzeA](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analysieren und Relogging

Das Verwenden einer Ablaufverfolgung erfolgt entweder über eine Analysesitzung oder eine Relogging-Sitzung.

Die Verwendung einer regelmäßigen Analyse eignet sich für die meisten Szenarien. Diese Methode gibt Ihnen die Flexibilität, `printf` Ihr Ausgabeformat auszuwählen: Text, XML, JSON, Datenbank, REST-Aufrufe usw.

Relogging dient für spezielle Analysen, die eine ETW-Ausgabedatei erzeugen müssen. Mithilfe des Reloggings können Sie die C++Build Insights-Ereignisse in Ihr eigenes ETW-Ereignisformat übersetzen. Eine geeignete Verwendung von Relogging wäre, C++ Build Insights-Daten an Ihre vorhandenen ETW-Tools und -Infrastrukturen anzubinden. [Vcperf](https://github.com/microsoft/vcperf) nutzt beispielsweise die Relogging-Schnittstellen. Das liegt daran, dass daten erzeugt werden müssen, die windows Performance Analyzer, ein ETW-Tool, verstehen kann. Wenn Sie die Relogging-Schnittstellen verwenden möchten, sind einige Vorkenntnisse über die Funktionsweise von ETW erforderlich.

### <a name="creating-analyzer-groups"></a>Erstellen von Analysegruppen

Es ist wichtig zu wissen, wie man Gruppen erstellt. Hier ist ein Beispiel, das zeigt, wie man eine Analyzer-Gruppe erstellt, die *Hello, world!* für jedes Aktivitätsstartereignis, das es empfängt.

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

| Funktionalität | C++-API | C-API | Notizen |
|--|--|--|--|
| Abgleichen und Filtern von Ereignissen | [MatcheventStackInMemberFunktion](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatcheventInMemberFunktion](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | Die C++-API bietet Funktionen, die es Ihnen leicht machen, die Ereignisse, die Ihnen wichtig sind, aus Ihren Ablaufverfolgungen zu extrahieren. Mit der C-API muss diese Filterung von Hand erfolgen. |
| Ereignisdatentypen | [Aktivität](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration](cpp-event-data-types/code-generation.md)<br />[Commandline](cpp-event-data-types/command-line.md)<br />[Compiler](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[Event](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Funktion](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[Aufruf](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[Linker](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[Symbolname](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[Thread](cpp-event-data-types/thread.md)<br />[Topdown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Aktivitäten und einfache Veranstaltungen

Die Veranstaltungen sind in zwei Kategorien unterteilt: *Aktivitäten* und *einfache Veranstaltungen*. Aktivitäten sind laufende Prozesse in der Zeit, die einen Anfang und ein Ende haben. Einfache Ereignisse sind pünktliche Ereignisse und haben keine Dauer. Wenn Sie MSVC-Ablaufverfolgungen mit dem C++ Build Insights SDK analysieren, erhalten Sie separate Ereignisse, wenn eine Aktivität gestartet und beendet wird. Sie erhalten nur ein Ereignis, wenn ein einfaches Ereignis eintritt.

### <a name="parent-child-relationships"></a>Eltern-Kind-Beziehungen

Aktivitäten und einfache Ereignisse stehen über Eltern-Kind-Beziehungen miteinander in Verbindung. Das übergeordnete Element einer Aktivität oder eines einfachen Ereignisses ist die umfassende Aktivität, in der sie auftreten. Wenn der Compiler beispielsweise eine Quelldatei kompiliert, muss er die Datei analysieren und dann den Code generieren. Die Analyse- und Codegenerierungsaktivitäten sind beide untergeordnete Elemente der Compileraktivität.

Einfache Ereignisse haben keine Dauer, so dass nichts anderes in ihnen passieren kann. Als solche haben sie nie Kinder.

Die Eltern-Kind-Beziehungen jeder Aktivität und jedes einfachen Ereignisses werden in der [Ereignistabelle](event-table.md)angezeigt. Das Wissen um diese Beziehungen ist wichtig, wenn C++ Build Insights-Ereignisse verwendet werden. Sie müssen sich oft darauf verlassen, dass sie den vollständigen Kontext eines Ereignisses verstehen.

### <a name="properties"></a>Eigenschaften

Alle Ereignisse haben die folgenden Eigenschaften:

| Eigenschaft | Beschreibung |
|--|--|
| Typbezeichner | Eine Zahl, die den Ereignistyp eindeutig identifiziert. |
| Instanzbezeichner | Eine Zahl, die das Ereignis innerhalb der Ablaufverfolgung eindeutig identifiziert. Wenn zwei Ereignisse desselben Typs in einer Ablaufverfolgung auftreten, erhalten beide einen eindeutigen Instanzbezeichner. |
| Startzeit | Der Zeitpunkt, zu dem eine Aktivität gestartet wurde, oder der Zeitpunkt, zu dem ein einfaches Ereignis aufgetreten ist. |
| Prozessbezeichner | Eine Zahl, die den Prozess identifiziert, in dem das Ereignis aufgetreten ist. |
| Thread-Bezeichner | Eine Zahl, die den Thread identifiziert, in dem das Ereignis aufgetreten ist. |
| Prozessorindex | Ein nullbasierter Index, der angibt, von welchem logischen Prozessor das Ereignis ausgesendet wurde. |
| Ereignisname | Eine Zeichenfolge, die den Ereignistyp beschreibt. |

Alle Aktivitäten außer einfachen Ereignissen haben auch folgende Eigenschaften:

| Eigenschaft | Beschreibung |
|--|--|
| Endzeit | Der Zeitpunkt, zu dem die Aktivität beendet wurde. |
| Exklusive Dauer | Die in einer Aktivität verbrachte Zeit, mit Ausnahme der zeit, die in den untergeordneten Aktivitäten verbracht wird. |
| CPU-Zeit | Die Zeit, die die CPU für die Ausführung von Code im Thread aufgewendet hat, der an die Aktivität angefügt ist. Es enthält keine Zeit, wann der Thread, der an die Aktivität angeschlossen ist, schlief. |
| Exklusive CPU-Zeit | Genauso wie CPU-Zeit, jedoch ohne die CPU-Zeit, die von untergeordneten Aktivitäten verbracht wird. |
| Wand-Uhr-Zeitverantwortung | Der Beitrag der Aktivität zur Gesamtzeit von Wanduhr. Die Wand-Uhr-Zeitverantwortung berücksichtigt die Parallelität zwischen den Aktivitäten. Angenommen, zwei nicht verknüpfte Aktivitäten verlaufen parallel. Beide haben eine Dauer von 10 Sekunden und genau die gleiche Start- und Stoppzeit. In diesem Fall weist Build Insights sowohl eine Wand-Uhr-Zeitverantwortung von 5 Sekunden zu. Im Gegensatz dazu wird diesen Aktivitäten eine nach der anderen ohne Überlappung zugewiesen, beiden wird eine Wand-Uhr-Zeitverantwortung von 10 Sekunden zugewiesen. |
| Exklusive Wand-Uhr-Zeitverantwortung | Ebenso wie die Zeitverantwortung für die Wanduhrzeit, schließt jedoch die Wand-Uhr-Zeitverantwortung für untergeordnete Aktivitäten aus. |

Einige Ereignisse haben ihre eigenen Eigenschaften über die genannten hinaus. In diesem Fall werden diese zusätzlichen Eigenschaften in der [Ereignistabelle](event-table.md)aufgeführt.

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Verwenden von Ereignissen, die vom C++ Build Insights SDK bereitgestellt werden

#### <a name="the-event-stack"></a>Der Ereignisstapel

Immer wenn das C++ Build Insights SDK Ihnen ein Ereignis bietet, wird es in Form eines Stacks angezeigt. Der letzte Eintrag im Stapel ist das aktuelle Ereignis, und die Einträge, bevor er die übergeordnete Hierarchie ist. Beispielsweise treten [LTCG-Start-](event-table.md#ltcg) und Stoppereignisse während Despasses 1 des Linkers auf. In diesem Fall enthält der Stapel, \[den Sie erhalten würden,: [LINKER](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. Die übergeordnete Hierarchie ist praktisch, da Sie ein Ereignis auf seinen Stamm zurückverfolgen können. Wenn die oben erwähnte LTCG-Aktivität langsam ist, können Sie sofort erfahren, um welchen Linkeraufruf es sich handelte.

#### <a name="matching-events-and-event-stacks"></a>Passende Ereignisse und Ereignisstapel

Das C++ Build Insights SDK gibt Ihnen jedes Ereignis in einer Ablaufverfolgung, aber meistens kümmern Sie sich nur um eine Teilmenge davon. In einigen Fällen ist Ihnen möglicherweise nur eine Teilmenge von *Ereignisstapeln*wichtig. Das SDK bietet Funktionen, mit denen Sie die benötigten Ereignisse oder Ereignisse schnell extrahieren und die Ereignisse ablehnen können, die Sie nicht benötigen. Dies geschieht über diese Abgleichsfunktionen:

|  |  |
|--|--|
| [MatchEvent](functions/match-event.md) | Behalten Sie ein Ereignis bei, wenn es mit einem der angegebenen Typen übereinstimmt. Leiten Sie übereinstimmende Ereignisse an einen Lambda- oder einen anderen aufrufbaren Typ weiter. Die übergeordnete Hierarchie des Ereignisses wird von dieser Funktion nicht berücksichtigt. |
| [MatcheventInMemberFunktion](functions/match-event-in-member-function.md) | Behalten Sie ein Ereignis bei, wenn es mit dem im Parameter einer Memberfunktion angegebenen Typ übereinstimmt. Leiten Sie übereinstimmende Ereignisse an die Memberfunktion weiter. Die übergeordnete Hierarchie des Ereignisses wird von dieser Funktion nicht berücksichtigt. |
| [MatchEventStack](functions/match-event-stack.md) | Behalten Sie ein Ereignis bei, wenn sowohl das Ereignis als auch die übergeordnete Hierarchie mit den angegebenen Typen übereinstimmen. Leiten Sie das Ereignis und die übereinstimmenden übergeordneten Hierarchieereignisse an einen Lambda- oder einen anderen aufrufbaren Typ weiter. |
| [MatcheventStackInMemberFunktion](functions/match-event-stack-in-member-function.md) | Behalten Sie ein Ereignis bei, wenn sowohl das Ereignis als auch seine übergeordnete Hierarchie mit den in der Parameterliste einer Memberfunktion angegebenen Typen übereinstimmen. Leiten Sie das Ereignis und die übereinstimmenden übergeordneten Hierarchieereignisse an die Memberfunktion weiter. |

Die Ereignisstapelabgleichsfunktionen wie `MatchEventStack` Zulassen von Lücken beim Beschreiben der übergeordneten Hierarchie. Sie können beispielsweise sagen, dass Sie \[am [LINKER](event-table.md#linker), [LTCG-Stack](event-table.md#ltcg) \] interessiert sind. Es würde auch \[mit dem LINKER,\] [PASS1](event-table.md#pass1), LTCG-Stack übereinstimmen. Der zuletzt angegebene Typ muss der zu vergleichende Ereignistyp sein und ist nicht Teil der übergeordneten Hierarchie.

#### <a name="capture-classes"></a>Capture-Klassen

Die `Match*` Verwendung der Funktionen erfordert, dass Sie die Typen angeben, die Sie abgleichen möchten. Diese Typen werden aus einer Liste von *Erfassungsklassen*ausgewählt. Capture-Klassen werden in mehreren Kategorien angezeigt, die unten beschrieben werden.

| Category | BESCHREIBUNG |
|--|--|
| Exact | Diese Erfassungsklassen werden verwendet, um einen bestimmten Ereignistyp und keine andere zu entsprechen. Ein Beispiel ist die [Compilerklasse,](cpp-event-data-types/compiler.md) die mit dem [COMPILER-Ereignis](event-table.md#compiler) übereinstimmt. |
| Platzhalter | Diese Erfassungsklassen können verwendet werden, um jedes Ereignis aus der Liste der von ihnen unterstützten Ereignisse abzugleichen. Der Platzhalter [Aktivität](cpp-event-data-types/activity.md) entspricht z. B. jedem Aktivitätsereignis. Ein weiteres Beispiel ist der [CompilerPass-Platzhalter,](cpp-event-data-types/compiler-pass.md) der entweder mit dem [FRONT_END_PASS](event-table.md#front-end-pass) oder dem [BACK_END_PASS-Ereignis](event-table.md#back-end-pass) übereinstimmen kann. |
| Group | Die Namen von Gruppenerfassungsklassen enden in *Gruppe*. Sie werden verwendet, um mehrere Ereignisse desselben Typs in einer Zeile abzugleichen und Lücken zu ignorieren. Sie sind nur sinnvoll, wenn rekursive Ereignisse übereinstimmen, da Sie nicht wissen, wie viele im Ereignisstapel vorhanden sind. Die [FRONT_END_FILE-Aktivität](event-table.md#front-end-file) findet z. B. jedes Mal statt, wenn der Compiler eine Datei analysiert. Diese Aktivität ist rekursiv, da der Compiler möglicherweise eine Include-Direktive findet, während er die Datei analysiert. Die [FrontEndFile-Klasse](cpp-event-data-types/front-end-file.md) entspricht nur einem FRONT_END_FILE Ereignis im Stapel. Verwenden Sie die [FrontEndFileGroup-Klasse,](cpp-event-data-types/front-end-file-group.md) um die gesamte Includehierarchie abzugleichen. |
| Wildcard-Gruppe | Eine Platzhaltergruppe kombiniert die Eigenschaften von Platzhaltern und Gruppen. Die einzige Klasse dieser Kategorie ist [InvocationGroup](cpp-event-data-types/invocation-group.md), die alle [LINKER-](event-table.md#linker) und [COMPILER-Ereignisse](event-table.md#compiler) in einem einzelnen Ereignisstapel abgleichen und erfassen. |

Informationen zu den Erfassungsklassen, die für die einzelnen Ereignisse verwendet werden können, finden Sie in der [Ereignistabelle.](event-table.md)

#### <a name="after-matching-using-captured-events"></a>Nach dem Abgleichen: Verwenden von erfassten Ereignissen

Sobald eine Übereinstimmung erfolgreich `Match*` abgeschlossen wurde, erstellen die Funktionen die Capture-Klassenobjekte und leiten sie an die angegebene Funktion weiter. Verwenden Sie diese Capture-Klassenobjekte, um auf die Eigenschaften der Ereignisse zuzugreifen.

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
