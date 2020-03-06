---
title: 'C++Build Insights-SDK: Ereignis Tabelle'
description: Ereignis Referenz für das Visual Studio C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ccc8a4ef707942963b85edc6db9e21e05610b54
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334511"
---
# <a name="c-build-insights-sdk-event-table"></a>C++Build Insights-SDK: Ereignis Tabelle

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Compilerereignisse

[Compiler\](#compiler)
[Command_line](#command-line)\
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
[Funktions](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Linker-Ereignisse

[Linker](#linker) -\
[Command_line](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg) -\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>Ereignis Tabelle

| Ereignis | Eigenschaft | BESCHREIBUNG |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [Versionen](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Eigenschaften | -Absoluter Pfad zur Eingabe Quelldatei<br/>-Absoluter Pfad zur Ausgabe Objektdatei |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Compilerpass](cpp-event-data-types/compiler-pass.md)<br/>[Backendpass](cpp-event-data-types/back-end-pass.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende des Compiler-Back-End-Pass-Ends auf. Dieser Durchlauf ist für die Optimierung von analysierten C/C++ Quellcode und das umrechnen in Computercode zuständig. |
| <a name="bottom-up"></a>BOTTOM_UP | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Nach unten](cpp-event-data-types/bottom-up.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende der gesamten Programmanalyse "Bottom-up-Durchlauf" auf. |
| <a name="c1-dll"></a>C1_DLL | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende eines Aufhörens von *C1. dll* oder *c1xx. dll* auf. Diese DLLs sind das C- C++ und das Front-End des Compilers. Sie werden ausschließlich vom Compilertreiber (*cl. exe*) aufgerufen. |
| <a name="c2-dll"></a>C2_DLL | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende eines *C2. dll* -Aufhörens auf. Diese dll ist das Back-End des Compilers. Sie wird vom Compilertreiber (*cl. exe*) aufgerufen. Sie wird auch vom Linker (*Link. exe*) aufgerufen, wenn die Link-Zeit Codegenerierung verwendet wird. |
| <a name="code-generation"></a>CODE_GENERATION | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C2_DLL](#c2-dll) |
|  | Children | [FUNCTION](#function)<br/>[Aden](#thread) |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Code Generation](cpp-event-data-types/code-generation.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende der Code Generierungs Phase für das Back-End auf. |
| <a name="command-line"></a>COMMAND_LINE | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Versionen](#compiler)<br/>[Amin](#linker) |
|  | Children | Keine |
|  | Eigenschaften | : Die Befehlszeile, die zum Aufrufen von *cl. exe* oder *Link. exe* verwendet wurde. |
|  | Erfassungs Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[CommandLine](cpp-event-data-types/command-line.md) |
|  | BESCHREIBUNG | Tritt auf, wenn der Compiler und Linker die Auswertung der Befehlszeile abgeschlossen haben. Die ausgewertete Befehlszeile enthält alle *cl. exe* -und *Link. exe* -Parameter, die über eine Antwortdatei übermittelt werden. Sie enthält auch Parameter für " *cl. exe* " und " *Link. exe* ", die über Umgebungsvariablen wie CL, \_cl\_, Link und \_Link\_übermittelt werden. |
| <a name="compiler"></a>Versionen | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | Keine |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Eigenschaften | -Compilerversion<br/>-Arbeitsverzeichnis<br/>-Absoluter Pfad zu der aufgerufenen *cl. exe* |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Aufruf](cpp-event-data-types/invocation.md)<br/>[Versionen](cpp-event-data-types/compiler.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende eines *cl. exe* -Aufhörens auf. |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Versionen](#compiler)<br/>[Amin](#linker) |
|  | Children | Keine |
|  | Eigenschaften | : Der Name der Umgebungsvariablen<br/>: Der Wert der Umgebungsvariablen. |
|  | Erfassungs Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | BESCHREIBUNG | Tritt einmal für jede vorhandene Umgebungsvariable auf, wenn " *cl. exe* " oder " *Link. exe* " aufgerufen wird. |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Amin](#linker) |
|  | Children | Keine |
|  | Eigenschaften | : Der absolute Pfad zu einer DLL-oder ausführbaren Ausgabedatei. |
|  | Erfassungs Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[Executableimageoutput](cpp-event-data-types/executable-image-output.md) |
|  | BESCHREIBUNG | Tritt auf, wenn eine der Linker-Eingaben eine DLL-Datei oder eine ausführbare Bilddatei ist. |
| <a name="exp-output"></a>EXP_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Amin](#linker) |
|  | Children | Keine |
|  | Eigenschaften | : Der absolute Pfad zu einer *Exp* -Ausgabedatei. |
|  | Erfassungs Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[Expoutput](cpp-event-data-types/exp-output.md) |
|  | BESCHREIBUNG | Tritt auf, wenn eine der Linker Ausgaben eine *Exp* -Datei ist. |
| <a name="file-input"></a>FILE_INPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Versionen](#compiler)<br/>[Amin](#linker) |
|  | Children | Keine |
|  | Eigenschaften | : Der absolute Pfad zur Eingabedatei<br/>: Der Typ der Eingabedatei |
|  | Erfassungs Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | BESCHREIBUNG | Tritt auf, um eine *cl. exe* -oder *Link. exe* -Eingabe anzukündigen. |
| <a name="force-inlinee"></a>FORCE_INLINEE | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [FUNCTION](#function) |
|  | Children | Keine |
|  | Eigenschaften | : Der Name der Force-Inline-Funktion.<br/>: Die Größe der Force-Inline-Funktion, die als zwischen Anweisungs Anzahl dargestellt wird. |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Forceingelinee](cpp-event-data-types/force-inlinee.md) |
|  | BESCHREIBUNG | Tritt auf, wenn eine Funktion in einer anderen Funktion durch die Verwendung des `__forceinline`-Schlüssel Worts erzwungen wird. |
| <a name="front-end-file"></a>FRONT_END_FILE | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Eigenschaften | -Absoluter Pfad zur Datei. |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Frontendfile](cpp-event-data-types/front-end-file.md) |
|  | BESCHREIBUNG | Tritt auf, wenn das Compiler-Front-End gestartet wird und die Verarbeitung einer Datei beendet. Dieses Ereignis ist rekursiv. Rekursion tritt auf, wenn das Front-End enthaltene Dateien verarbeitet. |
| <a name="front-end-pass"></a>FRONT_END_PASS | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [Versionen](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | Eigenschaften | -Absoluter Pfad zur Eingabe Quelldatei<br/>-Absoluter Pfad zur Ausgabe Objektdatei |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Compilerpass](cpp-event-data-types/compiler-pass.md)<br/>[Frontendpass](cpp-event-data-types/front-end-pass.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende des Compiler-Front-End-Pass-Ends auf. Dieser Durchlauf ist für die Verarbeitung von C/C++ Quellcode und die Umsetzung in eine zwischen Sprache zuständig. |
| <a name="function"></a>Funktion | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [CODE_GENERATION](#code-generation)<br/>[Aden](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | Eigenschaften | -Name der Funktion |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Function](cpp-event-data-types/function.md) |
|  | BESCHREIBUNG | Tritt beim Starten und Beenden des Codes für eine Funktion auf. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Amin](#linker) |
|  | Children | Keine |
|  | Eigenschaften | : Der absolute Pfad zu einer Import Bibliotheks Ausgabedatei. |
|  | Erfassungs Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[Impliboutput](cpp-event-data-types/imp-lib-output.md) |
|  | BESCHREIBUNG | Tritt auf, wenn einer der Ausgaben des Linker eine Import Bibliothek ist. |
| <a name="lib-output"></a>LIB_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Amin](#linker) |
|  | Children | Keine |
|  | Eigenschaften | : Der absolute Pfad zu einer statischen Bibliotheks Ausgabedatei. |
|  | Erfassungs Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[Liboutput](cpp-event-data-types/lib-output.md) |
|  | BESCHREIBUNG | Tritt auf, wenn eine der Ausgaben des Linker eine statische Bibliothek ist. |
| <a name="linker"></a>Amin | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | Keine |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | Eigenschaften | -Linker-Version<br/>-Arbeitsverzeichnis<br/>-Absoluter Pfad zur aufgerufenen *Verknüpfung. exe* |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Aufruf](cpp-event-data-types/invocation.md)<br/>[Linker](cpp-event-data-types/linker.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende eines " *Link. exe* "-Aufhörens auf. |
| <a name="ltcg"></a>LTCG | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende der Link-Zeit Codegenerierung auf. |
| <a name="obj-output"></a>OBJ_OUTPUT | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [Versionen](#compiler) |
|  | Children | Keine |
|  | Eigenschaften | : Der absolute Pfad zur *obj* -Ausgabedatei |
|  | Erfassungs Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[Objoutput](cpp-event-data-types/obj-output.md) |
|  | BESCHREIBUNG | Tritt einmal für jede *. obj* -Ausgabe auf, die von *cl. exe*erzeugt wird. |
| <a name="opt-icf"></a>OPT_ICF | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Opticf](cpp-event-data-types/opt-icf.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende der identischen COMDAT-Faltung (/opt: ICF) linker-Optimierung auf. |
| <a name="opt-lbr"></a>OPT_LBR | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Optlbr](cpp-event-data-types/opt-lbr.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende der linkeroptimierung Long Branch (/opt: LBR) auf. |
| <a name="opt-ref"></a>OPT_REF | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Optref](cpp-event-data-types/opt-ref.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende der linkeroptimierung der nicht referenzierten Funktionen und der Daten Löschung (/opt: Ref) auf. |
| <a name="pass1"></a>PASS1 | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [Amin](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende des Linker-Pass-1 auf. |
| <a name="pass2"></a>PASS2 | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [Amin](#linker) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende des Linker-bestanden 2 auf. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [PASS1](#pass1) |
|  | Children | Keine |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Preltcgoptref](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende der Linker-Optimierungs Übergabe auf, die nicht referenzierte Funktionen und Daten (/opt: Ref) ausschließt. Dies erfolgt vor der Link-Zeit Codegenerierung. |
| <a name="symbol-name"></a>SYMBOL_NAME | type | Einfaches Ereignis |
|  | Übergeordnete Elemente (Parents) | [C1_DLL](#c1-dll) |
|  | Children | Keine |
|  | Eigenschaften | -Einen Typschlüssel<br/> -Der Name des Typs. |
|  | Erfassungs Klassen | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Symbolname](cpp-event-data-types/symbol-name.md) |
|  | BESCHREIBUNG | Tritt am Ende der Front-End-Übergabe auf: einmal für jeden Typ, der an Vorlagen Instanziierungen beteiligt ist. Der Schlüssel ist ein numerischer Bezeichner für den Typ, während der Name seine Textdarstellung darstellt. Typschlüssel sind innerhalb der zu analysierende Ablauf Verfolgung eindeutig. Allerdings können verschiedene Schlüssel, die von unterschiedlichen Compiler-Front-End-Vorgängen stammen, auf denselben Typ verweisen. Der Vergleich von Typen zwischen verschiedenen compilerfront-End-Vorgängen erfordert die Verwendung ihrer Namen. SYMBOL_NAME Ereignisse werden am Ende eines Compiler-Front-End-Pass-Ends ausgegeben, nachdem alle Vorlagen Instanziierungen durchgeführt wurden. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Eigenschaften | : Der Schlüssel für den spezialisierten Typ<br/>: Der Schlüssel für den Typ der primären Vorlage<br/>-Die Art der Vorlage, die instanziiert wurde |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Templatin stantiations](cpp-event-data-types/template-instantiation.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende einer Vorlagen Instanziierung auf. Ein primärer Vorlagentyp (z. b. `vector`) wird instanziiert, was zu einem spezialisierten Typ (z. b. `std::vector<int>`) führt. Für beide Typen wird ein Schlüssel angegeben. Verwenden Sie das [SYMBOL_NAME](#symbol-name) -Ereignis, um einen Schlüssel in den Namen des Typs zu konvertieren. Typschlüssel sind innerhalb der zu analysierende Ablauf Verfolgung eindeutig. Allerdings können verschiedene Schlüssel, die von unterschiedlichen Compiler-Front-End-Vorgängen stammen, auf denselben Typ verweisen. Das Vergleichen von Typen zwischen verschiedenen compilerfront-End-Vorgängen erfordert die Verwendung von Symbolnamen Dieses Ereignis ist rekursiv. Die Rekursion findet in einigen Fällen statt, wenn das Front-End in der Instanziierung von vorgelagerten Vorlagen steht |
| <a name="thread"></a>Aden | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FUNCTION](#function) |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[Thread](cpp-event-data-types/thread.md) |
|  | BESCHREIBUNG | Tritt am Anfang und Ende der Ausführung eines Compiler-Back-End-Threads auf. Ein Thread, der angehalten wird, gilt als beendet. Ein Aufwach barer Thread wird als gestartet betrachtet. |
| <a name="top-down"></a>TOP_DOWN | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [FUNCTION](#function)<br/>[Aden](#thread) |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende der gesamten Programmanalyse ' Top-Down-Durchlauf ' auf. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | type | Aktivität |
|  | Übergeordnete Elemente (Parents) | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Eigenschaften | Keine |
|  | Erfassungs Klassen | [Aktivität](cpp-event-data-types/activity.md)<br/>["Wholeprogramanalysis"](cpp-event-data-types/whole-program-analysis.md) |
|  | BESCHREIBUNG | Tritt am Anfang und am Ende der Analysephase für das gesamte Programm der Link-Zeit Codegenerierung auf. |

::: moniker-end
