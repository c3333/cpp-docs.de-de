---
title: 'CL: Starten des Linkers'
ms.date: 11/04/2016
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: 1f9bb466ae89b8e3491b027a98b28935e7c8b523
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440178"
---
# <a name="cl-invokes-the-linker"></a>CL: Starten des Linkers

CL Ruft den Linker nach dem Kompilieren automatisch auf, es sei denn, die Option/c wird verwendet. CL übergibt an den Linker die Namen von obj-Dateien, die während der Kompilierung erstellt werden, und die Namen aller anderen Dateien, die in der Befehlszeile angegeben sind. Der Linker verwendet die Optionen, die in der Link-Umgebungsvariablen aufgelistet sind. Mit der/Link-Option können Sie die Linkeroptionen in der CL-Befehlszeile angeben. Optionen, die auf die Option/Link folgen, überschreiben die in der Link-Umgebungsvariablen. Die Optionen in der folgenden Tabelle unterdrücken die Verknüpfung.

|Option|BESCHREIBUNG|
|------------|-----------------|
|/c|Kompilieren ohne Verknüpfen|
|/E, /EP, /P|Vorverarbeitung ohne Kompilierung oder Verknüpfung|
|/Zg|Funktionsprototypen generieren|
|/Zs|Überprüfen der Syntax|

Weitere Informationen zum Verknüpfen finden Sie unter [MSVC (Linkeroptionen](linker-options.md)).

## <a name="example"></a>Beispiel

Angenommen, Sie kompilieren drei C-Quelldateien: Main. c, MOD1. c und MOD2. c. Jede Datei enthält einen Aufrufe einer Funktion, die in einer anderen Datei definiert ist:

- Main. c Ruft die Funktions `func1` in MOD1. c und die Funktion `func2` in MOD2. c auf.

- MOD1. c Ruft die Standard Bibliotheksfunktionen `printf_s` und `scanf_s`auf.

- MOD2. c ruft Grafikfunktionen mit dem Namen "`myline`" und "`mycircle`" auf, die in einer Bibliothek namens "MYGRAPH. lib" definiert sind.

Kompilieren Sie das Programm mit der folgenden Befehlszeile, um dieses Programm zu erstellen:

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL kompiliert zuerst die C-Quelldateien und erstellt die Objektdateien "Main. obj", "MOD1. obj" und "MOD2. obj". Der Compiler platziert den Namen der Standardbibliothek in jeder OBJ-Datei. Weitere Informationen finden Sie unter [Verwenden der Lauf Zeit Bibliothek](md-mt-ld-use-run-time-library.md).

CL übergibt die Namen der OBJ-Dateien zusammen mit dem Namen MYGRAPH. lib an den Linker. Der Linker löst die externen Verweise wie folgt auf:

1. In "Main. obj" wird der Verweis auf `func1` mithilfe der Definition in "MOD1. obj;" aufgelöst. der Verweis auf `func2` wird mit der Definition in MOD2. obj aufgelöst.

1. In MOD1. obj werden die Verweise auf `printf_s` und `scanf_s` mithilfe der Definitionen in der Bibliothek aufgelöst, die der Linker innerhalb von MOD1. obj findet.

1. In MOD2. obj werden die Verweise auf `myline` und `mycircle` mithilfe der Definitionen in MYGRAPH. lib aufgelöst.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Festlegen von Compileroptionen](compiler-command-line-syntax.md)
