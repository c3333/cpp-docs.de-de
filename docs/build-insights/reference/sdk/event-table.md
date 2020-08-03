---
title: 'C++ Build Insights SDK: Ereignistabelle'
description: Ereignisreferenz für das C++ Build Insights SDK in Visual Studio
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b1cf6871329fcce3166495e173360a88ac38ee0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224213"
---
# <a name="c-build-insights-sdk-event-table"></a>C++ Build Insights SDK: Ereignistabelle

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Compilerereignisse

[COMPILER](#compiler)\
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
[THREAD](#thread)\
[FUNCTION](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Linkerereignisse

[LINKER](#linker)\
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

| event | Eigenschaft | Beschreibung |
|--|--|--|
| <a name="back-end-pass"></a> BACK_END_PASS | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [COMPILER](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Eigenschaften | – Absoluter Pfad zur Eingabequelldatei<br/>– Absoluter Pfad zur Ausgabeobjektdatei |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Compiler-Back-End-Übergabe auf, die für die Optimierung des verarbeiteten C- oder C++-Quellcodes und die Konvertierung in Computercode zuständig ist |
| <a name="bottom-up"></a> BOTTOM_UP | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Bottom-up-Übergabe bei der Analyse des gesamten Programms auf |
| <a name="c1-dll"></a> C1_DLL | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Beschreibung | Tritt am Anfang und am Ende eines Aufrufs der DLL-Dateien *c1.dll* oder *c1xx.dll* auf, die das C- und C++-Front-End des Computers darstellen und nur über den Compilertreiber (*cl.exe*) aufgerufen werden |
| <a name="c2-dll"></a> C2_DLL | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Beschreibung | Tritt am Anfang und am Ende eines Aufrufs der DLL-Datei *c2.dll* auf, die das Back-End des Compilers darstellt und über den Compilertreiber (*cl.exe*) oder den Linker (*link.exe*) aufgerufen wird, wenn die Codegenerierung zur Verknüpfungszeit erfolgt |
| <a name="code-generation"></a> CODE_GENERATION | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C2_DLL](#c2-dll) |
|  | Children | [FUNCTION](#function)<br/>[THREAD](#thread) |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[CodeGeneration](cpp-event-data-types/code-generation.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Codegenerierungsphase im Back-End auf |
| <a name="command-line"></a> COMMAND_LINE | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [COMPILER](#compiler)<br/>[LINKER](#linker) |
|  | Children | Keine |
|  | Eigenschaften | – Befehlszeile, die zum Aufrufen von *cl.exe* oder *link.exe* verwendet wurde |
|  | Erfassungsklassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[CommandLine](cpp-event-data-types/command-line.md) |
|  | Beschreibung | Tritt auf, wenn der Compiler und Linker die Auswertung der Befehlszeile abgeschlossen haben: Die ausgewertete Befehlszeile enthält alle *cl.exe*- und *link.exe*-Parameter, die über eine Antwortdatei übergeben wurden. Sie enthält zudem Parameter für *cl.exe* und *link.exe*, die über Umgebungsvariablen wie CL, \_CL\_, LINK und \_LINK\_ übergeben wurden. |
| <a name="compiler"></a> COMPILER | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | Keine |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Eigenschaften | – Compilerversion<br/>– Arbeitsverzeichnis<br/>– Absoluter Pfad zur aufgerufenen Datei *cl.exe* |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Aufruf](cpp-event-data-types/invocation.md)<br/>[Compiler](cpp-event-data-types/compiler.md) |
|  | Beschreibung | Tritt am Anfang und am Ende eines Aufrufs der Datei *cl.exe* auf |
| <a name="environment-variable"></a> ENVIRONMENT_VARIABLE | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [COMPILER](#compiler)<br/>[LINKER](#linker) |
|  | Children | Keine |
|  | Eigenschaften | – Name der Umgebungsvariablen<br/>– Wert der Umgebungsvariablen |
|  | Erfassungsklassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | Beschreibung | Tritt einmal für jede vorhandene Umgebungsvariable auf, wenn *cl.exe* oder *link.exe* aufgerufen wird |
| <a name="executable-image-output"></a> EXECUTABLE_IMAGE_OUTPUT | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [LINKER](#linker) |
|  | Children | Keine |
|  | Eigenschaften | – Absoluter Pfad zu einer DLL-Ausgabedatei oder einer ausführbaren Ausgabedatei |
|  | Erfassungsklassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Beschreibung | Tritt auf, wenn eine der Linkerausgaben eine DLL-Datei oder eine ausführbare Imagedatei ist |
| <a name="exp-output"></a> EXP_OUTPUT | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [LINKER](#linker) |
|  | Children | Keine |
|  | Eigenschaften | – Absoluter Pfad zu einer *EXP*-Ausgabedatei |
|  | Erfassungsklassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | Beschreibung | Tritt auf, wenn eine der Linkerausgaben eine *EXP*-Datei ist |
| <a name="file-input"></a> FILE_INPUT | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [COMPILER](#compiler)<br/>[LINKER](#linker) |
|  | Children | Keine |
|  | Eigenschaften | – Absoluter Pfad zur Eingabedatei<br/>– Eingabedateityp |
|  | Erfassungsklassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | Beschreibung | Tritt auf, um eine *cl.exe*- oder *link.exe*-Eingabe anzukündigen |
| <a name="force-inlinee"></a> FORCE_INLINEE | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [FUNCTION](#function) |
|  | Children | Keine |
|  | Eigenschaften | – Name der erzwungenen Inlinefunktion<br/>– Größe der erzwungenen Inlinefunktion in Form der Anzahl von Zwischenanweisungen |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | Beschreibung | Tritt auf, wenn eine Inlinefunktion in einer anderen Funktion über das Schlüsselwort **`__forceinline`** erzwungen wird |
| <a name="front-end-file"></a> FRONT_END_FILE | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Eigenschaften | – Absoluter Dateipfad |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | Beschreibung | Tritt auf, wenn das Compiler-Front-End mit der Verarbeitung einer Datei beginnt oder diese beendet: Dieses Ereignis ist rekursiv. Eine Rekursion tritt auf, wenn das Front-End enthaltene Dateien verarbeitet. |
| <a name="front-end-pass"></a> FRONT_END_PASS | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [COMPILER](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | Eigenschaften | – Absoluter Pfad zur Eingabequelldatei<br/>– Absoluter Pfad zur Ausgabeobjektdatei |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Compiler-Front-End-Übergabe auf, die für die Verarbeitung des C- oder C++-Quellcodes und die Konvertierung in Zwischensprache zuständig ist |
| <a name="function"></a> FUNCTION | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [CODE_GENERATION](#code-generation)<br/>[THREAD](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | Eigenschaften | – Name der Funktion |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Function](cpp-event-data-types/function.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Codegenerierung für eine Funktion auf |
| <a name="imp-lib-output"></a> IMP_LIB_OUTPUT | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [LINKER](#linker) |
|  | Children | Keine |
|  | Eigenschaften | – Absoluter Pfad zur Ausgabedatei einer Importbibliothek |
|  | Erfassungsklassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | Beschreibung | Tritt auf, wenn eine der Linkerausgaben eine Importbibliothek ist |
| <a name="lib-output"></a> LIB_OUTPUT | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [LINKER](#linker) |
|  | Children | Keine |
|  | Eigenschaften | – Absoluter Pfad zur Ausgabedatei einer statischen Bibliothek |
|  | Erfassungsklassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | Beschreibung | Tritt auf, wenn eine der Linkerausgaben eine statische Bibliothek ist |
| <a name="linker"></a> LINKER | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | Keine |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | Eigenschaften | – Linkerversion<br/>– Arbeitsverzeichnis<br/>– Absoluter Pfad zur aufgerufenen Datei *link.exe* |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Aufruf](cpp-event-data-types/invocation.md)<br/>[Linker](cpp-event-data-types/linker.md) |
|  | Beschreibung | Tritt am Anfang und am Ende eines Aufrufs der Datei *link.exe* auf |
| <a name="ltcg"></a> LTCG | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | Beschreibung | Tritt am Anfang und am Ende der Codegenerierung zur Verknüpfungszeit auf |
| <a name="obj-output"></a> OBJ_OUTPUT | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [COMPILER](#compiler) |
|  | Children | Keine |
|  | Eigenschaften | – Absoluter Pfad zu einer *OBJ*-Ausgabedatei |
|  | Erfassungsklassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | Beschreibung | Tritt einmal für jede von *cl.exe* generierte *OBJ*-Ausgabedatei auf |
| <a name="opt-icf"></a> OPT_ICF | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | Beschreibung | Tritt am Anfang und Ende der identischen Linkeroptimierung /OPT:ICF (COMDAT-Folding) auf |
| <a name="opt-lbr"></a> OPT_LBR | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Linkeroptimierung /OPT:LBR (langer Branch) auf |
| <a name="opt-ref"></a> OPT_REF | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Linkeroptimierung /OPT:REF (Löschung verweisloser Funktionen und Daten) auf |
| <a name="pass1"></a> PASS1 | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [LINKER](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | Beschreibung | Tritt am Anfang und am Ende der Pass1-Linkerübergabe auf |
| <a name="pass2"></a> PASS2 | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [LINKER](#linker) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | Beschreibung | Tritt am Anfang und am Ende der Pass2-Linkerübergabe auf |
| <a name="pre-ltcg-opt-ref"></a> PRE_LTCG_OPT_REF | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Linkeroptimierung /OPT:REF (Löschung verweisloser Funktionen und Daten) und vor der Codegenerierung zur Verknüpfungszeit auf |
| <a name="symbol-name"></a> SYMBOL_NAME | Typ | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [C1_DLL](#c1-dll) |
|  | Children | Keine |
|  | Eigenschaften | – Typschlüssel<br/> – Typname |
|  | Erfassungsklassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName](cpp-event-data-types/symbol-name.md) |
|  | Beschreibung | Tritt am Ende der Front-End-Übergabe einmal für jeden Typ auf, der an Vorlageninstanziierungen beteiligt war, dabei ist der Schlüssel ein numerischer Typbezeichner und der Name dessen Textdarstellung. Typschlüssel sind innerhalb der Stapelüberwachung eindeutig, die analysiert wird. Allerdings können verschiedene Schlüssel, die von unterschiedlichen Compiler-Front-End-Übergaben stammen, auf denselben Typ verweisen. Für den Vergleich von Typen aus unterschiedlichen Compiler-Front-End-Übergaben sind deren Namen erforderlich. SYMBOL_NAME-Ereignisse werden am Ende einer Compiler-Front-End-Übergabe ausgegeben, nachdem alle Vorlageninstanziierungen durchgeführt wurden. |
| <a name="template-instantiation"></a> TEMPLATE_INSTANTIATION | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Eigenschaften | – Schlüssel für den spezialisierten Typ<br/>– Schlüssel für den primären Vorlagentyp<br/>– Instanziierte Vorlage |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | Beschreibung | Tritt am Anfang und Ende einer Vorlageninstanziierung auf: Ein primärer Vorlagentyp (wie `vector`) wird instanziiert, und das Ergebnis ist ein spezialisierter Typ (wie `std::vector<int>`). Für beide Typen wird ein Schlüssel angegeben. Verwenden Sie das [SYMBOL_NAME](#symbol-name)-Ereignis, um einen Schlüssel in einen Typnamen zu konvertieren. Typschlüssel sind innerhalb der Stapelüberwachung eindeutig, die analysiert wird. Allerdings können verschiedene Schlüssel, die von unterschiedlichen Compiler-Front-End-Übergaben stammen, auf denselben Typ verweisen. Für den Vergleich von Typen aus unterschiedlichen Compiler-Front-End-Übergaben sind deren Symbolnamen erforderlich. Dieses Ereignis ist rekursiv. Wenn das Front-End geschachtelte Vorlagen instanziiert, tritt manchmal eine Rekursion auf. |
| <a name="thread"></a> THREAD | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FUNCTION](#function) |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Thread](cpp-event-data-types/thread.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Ausführung eines Compiler-Back-End-Threads auf, dabei gilt ein angehaltener Thread als beendet, und ein reaktivierter Thread gilt als gestartet. |
| <a name="top-down"></a> TOP_DOWN | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [FUNCTION](#function)<br/>[THREAD](#thread) |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Top-down-Übergabe bei der Analyse des gesamten Programms auf |
| <a name="whole-program-analysis"></a> WHOLE_PROGRAM_ANALYSIS | Typ | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Eigenschaften | Keine |
|  | Erfassungsklassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | Beschreibung | Tritt am Anfang und Ende der Analysephase des gesamten Programms bei der Codegenerierung zur Verknüpfungszeit auf |

::: moniker-end
