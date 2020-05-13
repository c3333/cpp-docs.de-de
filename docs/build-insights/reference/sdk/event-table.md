---
title: 'C++ Build Insights SDK: Ereignistabelle'
description: Ereignisreferenz für das Visual Studio C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 932b78347e05d313e7962da2fdff8c3454dec963
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324138"
---
# <a name="c-build-insights-sdk-event-table"></a>C++ Build Insights SDK: Ereignistabelle

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Compilerereignisse

[Compiler](#compiler)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>Compiler-Front-End-Ereignisse

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>Compiler-Back-End-Ereignisse

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[Thread](#thread)\
[Funktion](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Linker-Ereignisse

[Linker](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>Ereignistabelle

| Ereignis | Eigenschaft | BESCHREIBUNG |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [Compiler](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Eigenschaften | - Absoluter Pfad zur Eingabequelldatei<br/>- Absoluter Pfad zur Ausgabeobjektdatei |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | BESCHREIBUNG | Tritt beim Start und Stopp des Compiler-Back-End-Passes auf. Dieser Durchlauf ist für die Optimierung des analysierten C/C++-Quellcodes und deren Konvertierung in Maschinencode verantwortlich. |
| <a name="bottom-up"></a>BOTTOM_UP | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Stopp des Bottom-up-Passes der gesamten Programmanalyse auf. |
| <a name="c1-dll"></a>C1_DLL | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | BESCHREIBUNG | Tritt beim Start und Stopp eines *c1.dll-* oder *c1xx.dll-Aufrufs* auf. Diese DLLs sind das C- und C++-Front-End des Compilers. Sie werden ausschließlich vom Compilertreiber (*cl.exe*) aufgerufen. |
| <a name="c2-dll"></a>C2_DLL | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | BESCHREIBUNG | Tritt beim Start und Stopp eines *c2.dll-Aufrufs* auf. Diese DLL ist das Back-End des Compilers. Es wird vom Compilertreiber aufgerufen (*cl.exe*). Es wird auch vom Linker (*link.exe*) aufgerufen, wenn link-time Codegenerierung verwendet wird. |
| <a name="code-generation"></a>CODE_GENERATION | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C2_DLL](#c2-dll) |
|  | Children | [Funktion](#function)<br/>[Thread](#thread) |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[CodeGeneration](cpp-event-data-types/code-generation.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Stopp der Codegenerierungsphase des Back-Ends auf. |
| <a name="command-line"></a>COMMAND_LINE | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Compiler](#compiler)<br/>[Linker](#linker) |
|  | Children | Keine |
|  | Eigenschaften | - Die Befehlszeile, die zum Aufrufen von *cl.exe* oder *link.exe* verwendet wurde |
|  | Capture-Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Commandline](cpp-event-data-types/command-line.md) |
|  | BESCHREIBUNG | Tritt auf, wenn der Compiler und der Linker die Auswertung der Befehlszeile abgeschlossen haben. Die ausgewertete Befehlszeile enthält alle *parameter cl.exe* und *link.exe,* die über eine Antwortdatei übergeben werden. Es enthält auch Parameter zu *cl.exe* und *link.exe* \_über\_Umgebungsvariablen \_\_wie CL, CL, LINK und LINK übergeben. |
| <a name="compiler"></a>Compiler | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | Keine |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Eigenschaften | - Compiler-Version<br/>- Arbeitsverzeichnis<br/>- Absoluter Pfad zum aufgerufenen *cl.exe* |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Aufruf](cpp-event-data-types/invocation.md)<br/>[Compiler](cpp-event-data-types/compiler.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Stopp eines *cl.exe-Aufrufs* auf. |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Compiler](#compiler)<br/>[Linker](#linker) |
|  | Children | Keine |
|  | Eigenschaften | - Der Name der Umgebungsvariablen<br/>- Der Wert der Umgebungsvariablen. |
|  | Capture-Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | BESCHREIBUNG | Tritt einmal für jede vorhandene Umgebungsvariable zum Zeitpunkt auf, zu dem *cl.exe* oder *link.exe* aufgerufen wird. |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Linker](#linker) |
|  | Children | Keine |
|  | Eigenschaften | - Der absolute Pfad zu einer DLL- oder ausführbaren Ausgabedatei. |
|  | Capture-Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | BESCHREIBUNG | Tritt auf, wenn eine der Linker-Eingaben eine DLL oder eine ausführbare Bilddatei ist. |
| <a name="exp-output"></a>EXP_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Linker](#linker) |
|  | Children | Keine |
|  | Eigenschaften | - Der absolute Pfad zu einer *.exp* Ausgabedatei. |
|  | Capture-Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | BESCHREIBUNG | Tritt auf, wenn eine der Linker-Ausgaben eine *.exp-Datei* ist. |
| <a name="file-input"></a>FILE_INPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Compiler](#compiler)<br/>[Linker](#linker) |
|  | Children | Keine |
|  | Eigenschaften | - Der absolute Pfad zur Eingabedatei<br/>- Der Typ der Eingabedatei |
|  | Capture-Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | BESCHREIBUNG | Tritt ein, um eine *cl.exe-* oder *link.exe-Eingabe* anzukündigen. |
| <a name="force-inlinee"></a>FORCE_INLINEE | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Funktion](#function) |
|  | Children | Keine |
|  | Eigenschaften | - Der Name der force-inlined-Funktion.<br/>- Die Größe der kraftinlinen Funktion, dargestellt als Zwischenanweisungsanzahl. |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | BESCHREIBUNG | Tritt auf, wenn eine Funktion durch die Verwendung des `__forceinline` Schlüsselworts in eine andere Funktion eingebunden wird. |
| <a name="front-end-file"></a>FRONT_END_FILE | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Eigenschaften | - Absoluter Pfad zur Datei. |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | BESCHREIBUNG | Tritt auf, wenn das Compiler-Front-End gestartet wird und die Verarbeitung einer Datei beendet. Dieses Ereignis ist rekursiv. Rekursion tritt auf, wenn das Front-End eingeschlossene Dateien analysiert. |
| <a name="front-end-pass"></a>FRONT_END_PASS | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [Compiler](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | Eigenschaften | - Absoluter Pfad zur Eingabequelldatei<br/>- Absoluter Pfad zur Ausgabeobjektdatei |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | BESCHREIBUNG | Tritt beim Start und Stopp des Compiler-Front-End-Passes auf. Dieser Pass ist für die Analyse des C/C++-Quellcodes und deren Konvertierung in eine Zwischensprache verantwortlich. |
| <a name="function"></a>Funktion | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [CODE_GENERATION](#code-generation)<br/>[Thread](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | Eigenschaften | - Name der Funktion |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Funktion](cpp-event-data-types/function.md) |
|  | BESCHREIBUNG | Tritt beim Starten und Beenden der Generierung des Codes für eine Funktion auf. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Linker](#linker) |
|  | Children | Keine |
|  | Eigenschaften | - Der absolute Pfad zu einer Importbibliotheksausgabedatei. |
|  | Capture-Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | BESCHREIBUNG | Tritt auf, wenn eine der Ausgaben des Linkers eine Importbibliothek ist. |
| <a name="lib-output"></a>LIB_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Linker](#linker) |
|  | Children | Keine |
|  | Eigenschaften | - Der absolute Pfad zu einer statischen Bibliotheksausgabedatei. |
|  | Capture-Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | BESCHREIBUNG | Tritt auf, wenn eine der Ausgaben des Linkers eine statische Bibliothek ist. |
| <a name="linker"></a>Linker | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | Keine |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | Eigenschaften | - Linker Version<br/>- Arbeitsverzeichnis<br/>- Absoluter Pfad zum aufgerufenen *link.exe* |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Aufruf](cpp-event-data-types/invocation.md)<br/>[Linker](cpp-event-data-types/linker.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Stopp eines *aufruferen Aufrufs von link.exe* auf. |
| <a name="ltcg"></a>LTCG | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Stopp der Linkzeitcodegenerierung auf. |
| <a name="obj-output"></a>OBJ_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Compiler](#compiler) |
|  | Children | Keine |
|  | Eigenschaften | - Der absolute Pfad zur *.obj-Ausgabedatei* |
|  | Capture-Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | BESCHREIBUNG | Tritt einmal für jede *.obj* Ausgabe auf, die von *cl.exe*produziert wird. |
| <a name="opt-icf"></a>OPT_ICF | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | BESCHREIBUNG | Tritt beim Start und Stopp der identischen COMDAT-Faltung (/OPT:ICF) Linker-Optimierung auf. |
| <a name="opt-lbr"></a>OPT_LBR | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | BESCHREIBUNG | Tritt beim Start und Stopp der langen Verzweigungsoptimierung (/OPT:LBR) auf. |
| <a name="opt-ref"></a>OPT_REF | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | BESCHREIBUNG | Tritt beim Start und Stoppen der nicht referenzierten Funktionen und datenelimination (/OPT:REF) Linker-Optimierung auf. |
| <a name="pass1"></a>PASS1 | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [Linker](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Stopp des Linkspasses 1 auf. |
| <a name="pass2"></a>PASS2 | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [Linker](#linker) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Stopp des Durchgangs 2 des Linkers auf. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | BESCHREIBUNG | Tritt beim Start und Stopp des Linker-Optimierungsdurchlaufs auf, der nicht referenzierte Funktionen und Daten eliminiert (/OPT:REF). Dies geschieht vor der Generierung von Link-Time-Code. |
| <a name="symbol-name"></a>SYMBOL_NAME | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [C1_DLL](#c1-dll) |
|  | Children | Keine |
|  | Eigenschaften | - Ein Typschlüssel<br/> - Der Name des Typs |
|  | Capture-Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Symbolname](cpp-event-data-types/symbol-name.md) |
|  | BESCHREIBUNG | Tritt am Ende des Front-End-Passes auf: einmal für jeden Typ, der an Vorlageninstanziierungen beteiligt ist. Der Schlüssel ist ein numerischer Bezeichner für den Typ, während der Name seine Textdarstellung ist. Typschlüssel sind innerhalb der zu analysierenden Ablaufverfolgung eindeutig. Verschiedene Schlüssel, die aus verschiedenen Compiler-Front-End-Pässen stammen, können jedoch auf denselben Typ verweisen. Zum Vergleichen von Typen zwischen verschiedenen Compiler-Front-End-Pässen müssen ihre Namen verwendet werden. SYMBOL_NAME Ereignisse werden am Ende eines Compiler-Front-End-Passes angezeigt, nachdem alle Vorlageninstanziierungen stattgefunden haben. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Eigenschaften | - Der Schlüssel für den spezialisierten Typ<br/>- Der Schlüssel für den Typ der primären Vorlage<br/>- Die Art der Vorlage, die instanziiert wurde |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Ende einer Vorlageninstanziierung auf. Ein primärer Vorlagentyp `vector`(z. B. ) wird instanziiert, was zu einem spezialisierten Typ führt (z. `std::vector<int>`B. ). Für beide Typen wird ein Schlüssel angegeben. Verwenden [SYMBOL_NAME](#symbol-name) Sie das SYMBOL_NAME-Ereignis, um einen Schlüssel in den Namen des Typs zu konvertieren. Typschlüssel sind innerhalb der zu analysierenden Ablaufverfolgung eindeutig. Verschiedene Schlüssel, die aus verschiedenen Compiler-Front-End-Pässen stammen, können jedoch auf denselben Typ verweisen. Zum Vergleichen von Typen zwischen verschiedenen Compiler-Front-End-Pässen müssen Symbolnamen verwendet werden. Dieses Ereignis ist rekursiv. Rekursion tritt in einigen Fällen auf, wenn das Front-End verschachtelte Vorlagen instanziiert. |
| <a name="thread"></a>Thread | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [Funktion](#function) |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Thread](cpp-event-data-types/thread.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Ende einer Compiler-Back-End-Threadausführung auf. Ein Thread, der angehalten wird, gilt als beendet. Ein Thread, der geweckt wird, gilt als gestartet. |
| <a name="top-down"></a>TOP_DOWN | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [Funktion](#function)<br/>[Thread](#thread) |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Topdown](cpp-event-data-types/top-down.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Stopp des Top-Down-Passes der gesamten Programmanalyse auf. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Eigenschaften | Keine |
|  | Capture-Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Stopp der Gesamtprogrammanalysephase der Linkzeitcodegenerierung auf. |

::: moniker-end
