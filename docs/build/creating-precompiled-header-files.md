---
title: Vorkompilierte Headerdateien
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 158301ec3caacced1663892071b17ef2b8f8e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328672"
---
# <a name="precompiled-header-files"></a>Vorkompilierte Headerdateien

Wenn Sie ein neues Projekt in Visual Studio erstellen, wird dem Projekt eine *vorkompilierte Headerdatei* mit dem Namen *pch.h* hinzugefügt. (In Visual Studio 2017 und früher wurde die Datei *stdafx.h*aufgerufen.) Der Zweck der Datei besteht darin, den Buildprozess zu beschleunigen. Alle stabilen Headerdateien, z. B. Standardlibrary-Header wie `<vector>`, sollten hier enthalten sein. Der vorkompilierte Header wird nur kompiliert, wenn er oder alle darin enthaltenen Dateien geändert werden. Wenn Sie nur Änderungen am Projektquellcode vornehmen, überspringt der Build die Kompilierung für den vorkompilierten Header.

Die Compileroptionen für vorkompilierte Header sind [/Y](reference/y-precompiled-headers.md). Auf den Projekteigenschaftenseiten befinden sich die Optionen unter **Konfigurationseigenschaften > C/C++ > Vorkompilierte Header**. Sie können festlegen, dass keine vorkompilierten Header verwendet werden sollen, und Sie können den Namen der Headerdatei sowie den Namen und Pfad der Ausgabedatei angeben.

## <a name="custom-precompiled-code"></a>Benutzerdefinierter vorkompilierter Code

Bei großen Projekten, deren Erstellung erheblich ersucht wird, sollten Sie das Erstellen benutzerdefinierter vorkompilierter Dateien in Betracht ziehen. Die Microsoft C- und C++-Compiler stellen Optionen für das Vorkompilieren von beliebigem C- oder C++-Code bereit, einschließlich Inlinecode. Mithilfe dieser leistungsstarken Funktion können Sie einen stabilen Codeabschnitt kompilieren, den Code im kompilierten Zustand in einer Datei speichern und bei nachfolgenden Kompilierungen den vorkompilierten Code mit dem noch in Entwicklung befindlichen Code kombinieren. So können nachfolgende Kompilierungen beschleunigt werden, da der bereits stabile Code nicht neu kompiliert werden muss.

## <a name="when-to-precompile-source-code"></a>Wann sollte Quellcode vorkompiliert werden?

Vorkompilierter Code ist während des Entwicklungszyklus nützlich, um die Kompilierungszeit zu reduzieren, insbesondere wenn:

- Sie verwenden immer einen großen Codetext, der sich selten ändert.

- Ihr Programm besteht aus mehreren Modulen, die alle einen Standardsatz von Include-Dateien und die gleichen Kompilierungsoptionen verwenden. In diesem Fall können alle Include-Dateien in einem vorkompilierten Header vorkompiliert werden.

Die erste Kompilierung – diejenige, die die vorkompilierte Headerdatei (PCH) erstellt – dauert etwas länger als nachfolgende Kompilierungen. Nachfolgende Kompilierungen können schneller ausgeführt werden, indem der vorkompilierte Code eingebunden wird.

Sie können sowohl C- als auch C++-Programme vorkompilieren. In der C++-Programmierung ist es üblich, Klassenschnittstelleninformationen in Headerdateien zu trennen. Diese Headerdateien können später in Programmen enthalten sein, die die Klasse verwenden. Durch die Vorkompilierung dieser Header können Sie die Zeit reduzieren, die ein Programm zum Kompilieren benötigt.

> [!NOTE]
> Obwohl Sie nur eine vorkompilierte Headerdatei (.pch) pro Quelldatei verwenden können, können Sie mehrere PCH-Dateien in einem Projekt verwenden.

## <a name="two-choices-for-precompiling-code"></a>Zwei Methoden für das Vorkompilieren von Code

Sie können jeden C- oder C++-Code vorkompilieren. Sie sind nicht darauf beschränkt, nur Headerdateien vorzukompilieren.

Precompiling erfordert Planung, bietet jedoch deutlich schnellere Kompilierungen, wenn Sie anderen Quellcode als einfache Headerdateien vorkompilieren.

Vorkompilieren Sie Code, wenn Sie wissen, dass Ihre Quelldateien allgemeine Sätze von Headerdateien verwenden, diese jedoch nicht in derselben Reihenfolge enthalten, oder wenn Sie Quellcode in die Vorkompilierung aufnehmen möchten.

Die vorkompilierten Header-Optionen sind [/Yc (Create Precompiled Header File)](reference/yc-create-precompiled-header-file.md) und [/Yu (Use Precompiled Header File)](reference/yu-use-precompiled-header-file.md). Verwenden Sie **/Yc,** um einen vorkompilierten Header zu erstellen. Bei Verwendung mit dem optionalen [hdrstop-Pragma](../preprocessor/hdrstop.md) können Sie mit **/Yc** sowohl Headerdateien als auch Quellcode vorkompilieren. Wählen Sie **/Yu** aus, um einen vorhandenen vorkompilierten Header in der vorhandenen Kompilierung zu verwenden. Sie können **/Fp** auch mit den Optionen **/Yc** und **/Yu** verwenden, um einen alternativen Namen für den vorkompilierten Header bereitzustellen.

In den Compileroptionsreferenzthemen für **/Yu** und **/Yc** wird erläutert, wie sie in der Entwicklungsumgebung auf diese Funktionalität zugreifen können.

## <a name="precompiled-header-consistency-rules"></a>Konsistenzregeln für vorkompilierte Header

Da PCH-Dateien Informationen über die Computerumgebung sowie Speicheradressinformationen über das Programm enthalten, sollten Sie nur eine PCH-Datei auf dem Computer verwenden, auf dem sie erstellt wurde.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Konsistenzregeln zur Verwendung einer vorkompilierten Headerdatei

Mit der Compileroption [/Yu](reference/yu-use-precompiled-header-file.md) können Sie angeben, welche PCH-Datei verwendet werden soll.

Wenn Sie eine PCH-Datei verwenden, geht der Compiler von derselben Kompilierungsumgebung aus, die konsistente Compileroptionen, Pragmas usw. verwendet, die beim Erstellen der PCH-Datei wirksam war, es sei denn, Sie geben etwas anderes an. Wenn der Compiler eine Inkonsistenz erkennt, gibt er eine Warnung aus und identifiziert die Inkonsistenz, wo dies möglich ist. Solche Warnungen weisen nicht unbedingt auf ein Problem mit der PCH-Datei hin; sie warnen Sie einfach vor möglichen Konflikten. Konsistenzanforderungen für PCH-Dateien werden in den folgenden Abschnitten beschrieben.

### <a name="compiler-option-consistency"></a>Compileroptionskonsistenz

Die folgenden Compileroptionen können bei Verwendung einer PCH-Datei eine Inkonsistenzwarnung auslösen:

- Makros, die mit der Option Preprozessor (/D) erstellt wurden, müssen zwischen der Kompilierung, die die PCH-Datei erstellt hat, und der aktuellen Kompilierung identisch sein. Der Status der definierten Konstanten wird nicht überprüft, aber es können unvorhersehbare Ergebnisse auftreten, wenn sich diese ändern.

- PCH-Dateien funktionieren nicht mit den Optionen /E und /EP.

- PCH-Dateien müssen entweder mit der Option Browse Info (/FR) generieren oder mit der Option Lokale Variablen ausschließen (/Fr) erstellt werden, bevor nachfolgende Kompilierungen, die die PCH-Datei verwenden, diese Optionen verwenden können.

### <a name="c-70-compatible-z7"></a>C 7.0-Kompatibel (/Z7)

Wenn diese Option beim Erstellen der PCH-Datei aktiviert ist, können nachfolgende Kompilierungen, die die PCH-Datei verwenden, die Debuginformationen verwenden.

Wenn die Option C 7.0-Compatible (/Z7) beim Erstellen der PCH-Datei nicht wirksam ist, lösen nachfolgende Kompilierungen, die die PCH-Datei und /Z7 verwenden, eine Warnung aus. Die Debuginformationen werden in der aktuellen .obj-Datei platziert, und lokale Symbole, die in der PCH-Datei definiert sind, sind für den Debugger nicht verfügbar.

### <a name="include-path-consistency"></a>Pfadkonsistenz einschließen

Eine PCH-Datei enthält keine Informationen über den Includepfad, der beim Erstellen wirksam war. Wenn Sie eine PCH-Datei verwenden, verwendet der Compiler immer den in der aktuellen Kompilierung angegebenen Includepfad.

### <a name="source-file-consistency"></a>Quelldateikonsistenz

Wenn Sie die Option Vorkompilierte Headerdatei (/Yu) verwenden angeben, ignoriert der Compiler alle Präprozessordirektiven (einschließlich Pragmas), die im Quellcode angezeigt werden, der vorkompiliert wird. Die von solchen Präprozessordirektiven angegebene Kompilierung muss mit der Kompilierung identisch sein, die für die Option Vorkompilierte Headerdatei (/Yc) erstellen verwendet wird.

### <a name="pragma-consistency"></a>Pragma-Konsistenz

Pragmas, die während der Erstellung einer PCH-Datei verarbeitet werden, wirken sich in der Regel auf die Datei aus, mit der die PCH-Datei anschließend verwendet wird. Die `comment` `message` und Pragmas haben keinen Einfluss auf den Rest der Zusammenstellung.

Diese Pragmas wirken sich nur auf den Code in der PCH-Datei aus. Sie haben keinen Einfluss auf Code, der anschließend die PCH-Datei verwendet:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Diese Pragmas werden als Teil eines vorkompilierten Headers beibehalten und wirken sich auf den Rest einer Kompilierung aus, die den vorkompilierten Header verwendet:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Konsistenzregeln für "/Yc" und "/Yu"

Wenn Sie einen vorkompilierten Header verwenden, der mit /Yc oder /Yu erstellt wurde, vergleicht der Compiler die aktuelle Kompilierungsumgebung mit der, die beim Erstellen der PCH-Datei vorhanden war. Stellen Sie sicher, dass Sie eine Umgebung angeben, die mit der vorherigen Umgebung (mit konsistenten Compileroptionen, Pragmas usw.) für die aktuelle Kompilierung konsistent ist. Wenn der Compiler eine Inkonsistenz erkennt, gibt er eine Warnung aus und identifiziert die Inkonsistenz, wo dies möglich ist. Solche Warnungen weisen nicht unbedingt auf ein Problem mit der PCH-Datei hin. sie warnen Sie einfach vor möglichen Konflikten. In den folgenden Abschnitten werden die Konsistenzanforderungen für vorkompilierte Header erläutert.

### <a name="compiler-option-consistency"></a>Compileroptionskonsistenz

In dieser Tabelle werden Compileroptionen aufgeführt, die bei Verwendung eines vorkompilierten Headers eine Inkonsistenzwarnung auslösen können:

|Option|Name|Regel|
|------------|----------|----------|
|/D|Definieren von Konstanten und Makros|Muss zwischen der Kompilierung, die den vorkompilierten Header erstellt hat, und der aktuellen Kompilierung identisch sein. Der Status der definierten Konstanten wird nicht überprüft, aber es können unvorhersehbare Ergebnisse auftreten, wenn Ihre Dateien von den Werten der geänderten Konstanten abhängen.|
|/E oder /EP|Präprozessorausgabe in Standardausgabe kopieren|Vorkompilierte Header funktionieren nicht mit der Option /E oder /EP.|
|/Fr oder /FR|Generieren von Microsoft-Quellbrowserinformationen|Damit die Optionen /Fr und /FR mit der Option /Yu gültig sind, müssen sie auch beim Erstellen des vorkompilierten Headers wirksam gewesen sein. Nachfolgende Kompilierungen, die den vorkompilierten Header verwenden, generieren auch Quellbrowserinformationen. Browserinformationen werden in einer einzigen .sbr-Datei abgelegt und von anderen Dateien auf die gleiche Weise wie CodeView-Informationen referenziert. Sie können die Platzierung von Quellbrowserinformationen nicht überschreiben.|
|/GA, /GD, /GE, /GW oder /GW|Windows-Protokolloptionen|Muss zwischen der Kompilierung, die den vorkompilierten Header erstellt hat, und der aktuellen Kompilierung identisch sein. Wenn sich diese Optionen unterscheiden, wird eine Warnmeldung angezeigt.|
|/Zi|Vollständige Debuginformationen generieren|Wenn diese Option beim Erstellen des vorkompilierten Headers wirksam ist, können nachfolgende Kompilierungen, die die Vorkompilierung verwenden, diese Debuginformationen verwenden. Wenn /Zi beim Erstellen des vorkompilierten Headers nicht wirksam ist, lösen nachfolgende Kompilierungen, die die Vorkompilierung und die Option /Zi verwenden, eine Warnung aus. Die Debuginformationen werden in der aktuellen Objektdatei platziert, und lokale Symbole, die im vorkompilierten Header definiert sind, sind für den Debugger nicht verfügbar.|

> [!NOTE]
> Die vorkompilierte Headerfunktion ist nur für die Verwendung in C- und C++-Quelldateien vorgesehen.

## <a name="using-precompiled-headers-in-a-project"></a>Verwenden von vorkompilierten Headern in einem Projekt

Die vorherigen Abschnitte bieten einen Überblick über vorkompilierte Header: /Yc und /Yu, die Option /Fp und das [hdrstop-Pragma.](../preprocessor/hdrstop.md) In diesem Abschnitt wird eine Methode zum Verwenden der manuellen vorkompilierten Headeroptionen in einem Projekt beschrieben. Sie endet mit einer Beispieldatei und dem von ihr verwalteten Code.

Untersuchen Sie eine der Makefiles im Verzeichnis MFC-SRC, die während der Standardeinrichtung von Visual Studio erstellt werden, wenn Sie die manuellen vorkompilierten Headeroptionen in einem Projekt verwenden. Diese Makefiles verfolgen einen ähnlichen Ansatz wie in diesem Abschnitt vorgestellt, nutzen jedoch die NMAKE-Makros (Microsoft Program Maintenance Utility) stärker und bieten eine bessere Kontrolle über den Buildprozess.

## <a name="pch-files-in-the-build-process"></a>PCH-Dateien im Erstellungsvorgang

Die Codebasis eines Softwareprojekts ist in der Regel in mehreren C- oder C++-Quelldateien, Objektdateien, Bibliotheken und Headerdateien enthalten. In der Regel koordiniert ein Makefile die Kombination dieser Elemente in einer ausführbaren Datei. Die folgende Abbildung zeigt die Struktur eines Makefiles, das eine vorkompilierte Headerdatei verwendet. Die NMAKE-Makronamen und die Dateinamen in diesem Diagramm stimmen mit denen im Beispielcode in [Sample Makefile for PCH](#sample-makefile-for-pch) und [Example Code for PCH](#example-code-for-pch)überein.

Die Abbildung verwendet drei diagrammgesteuerte Geräte, um den Fluss des Buildprozesses anzuzeigen. Benannte Rechtecke stellen jede Datei oder jedes Makro dar. Die drei Makros stellen eine oder mehrere Dateien dar. Schattierte Bereiche stellen jede Kompilierungs- oder Linkaktion dar. Pfeile zeigen an, welche Dateien und Makros während des Kompilierungs- oder Verknüpfungsprozesses kombiniert werden.

![Struktur einer Makefile, die eine vorkompilierte Headerdatei verwendet](media/vc30ow1.gif "Struktur einer Makefile, die eine vorkompilierte Headerdatei verwendet") <br/>
Struktur eines Makefiles, das eine vorkompilierte Headerdatei verwendet

Beginnend am Anfang des Diagramms sind sowohl STABLEHDRS als auch BOUNDRY NMAKE-Makros, in denen Sie Dateien auflisten, die wahrscheinlich keine Neukompilierung benötigen. Diese Dateien werden über die Befehlszeichenfolge kompiliert

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

nur, wenn die vorkompilierte Headerdatei (STABLE.pch) nicht vorhanden ist oder wenn Sie Änderungen an den in den beiden Makros aufgeführten Dateien vornehmen. In beiden Fällen enthält die vorkompilierte Headerdatei nur Code aus den im STABLEHDRS-Makro aufgeführten Dateien. Listet die letzte Datei auf, die im BOUNDRY-Makro vorkompiliert werden soll.

Die Dateien, die Sie in diesen Makros auflisten, können entweder Headerdateien oder C- oder C++-Quelldateien sein. (Eine einzelne PCH-Datei kann nicht mit C- und C++-Modulen verwendet werden.) Beachten Sie, dass Sie das **hdrstop-Makro** verwenden können, um die Vorkompilierung zu einem bestimmten Zeitpunkt in der BOUNDRY-Datei zu beenden. Weitere Informationen finden Sie unter [hdrstop.](../preprocessor/hdrstop.md)

AppLIB.obj stellt den Supportcode dar, der in Ihrer endgültigen Anwendung verwendet wird. Es wird aus APPLIB.cpp, den im UNSTABLEHDRS-Makro aufgelisteten Dateien und vorkompiliertem Code aus dem vorkompilierten Header erstellt.

MYAPP.obj stellt Ihre endgültige Bewerbung dar. Es wird aus MYAPP.cpp, den im UNSTABLEHDRS-Makro aufgelisteten Dateien und vorkompiliertem Code aus dem vorkompilierten Header erstellt.

Schließlich die ausführbare Datei (MYAPP. EXE) wird durch Verknüpfen der im OBJS-Makro aufgeführten Dateien (APPLIB.obj und MYAPP.obj) erstellt.

## <a name="sample-makefile-for-pch"></a>Beispielmakefile für PCH

Die folgende makefile verwendet Makros und eine ! Wenn! oder! ENDIF Flow-of-Control-Befehlsstruktur, um die Anpassung an Ihr Projekt zu vereinfachen.

```NMAKE
# Makefile : Illustrates the effective use of precompiled
#            headers in a project
# Usage:     NMAKE option
# option:    DEBUG=[0|1]
#            (DEBUG not defined is equivalent to DEBUG=0)
#
OBJS = myapp.obj applib.obj
# List all stable header files in the STABLEHDRS macro.
STABLEHDRS = stable.h another.h
# List the final header file to be precompiled here:
BOUNDRY = stable.h
# List header files under development here:
UNSTABLEHDRS = unstable.h
# List all compiler options common to both debug and final
# versions of your code here:
CLFLAGS = /c /W3
# List all linker options common to both debug and final
# versions of your code here:
LINKFLAGS = /nologo
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi
LINKFLAGS = $(LINKFLAGS) /COD
LIBS      = slibce
!ELSE
CLFLAGS   = $(CLFLAGS) /Oselg /Gs
LINKFLAGS = $(LINKFLAGS)
LIBS      = slibce
!ENDIF
myapp.exe: $(OBJS)
    link $(LINKFLAGS) @<<
$(OBJS), myapp, NUL, $(LIBS), NUL;
<<
# Compile myapp
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp
# Compile applib
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp
# Compile headers
stable.pch : $(STABLEHDRS)
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp
```

Abgesehen von den Macros STABLEHDRS, BOUNDRY und UNSTABLEHDRS, die in der Abbildung "Struktur eines Makefiles, das eine vorkompilierte Headerdatei verwendet" in [PCH-Dateien im Buildprozess](#pch-files-in-the-build-process)gezeigt wird, stellt dieses Makefile ein CLFLAGS-Makro und ein LINKFLAGS-Makro bereit. Sie müssen diese Makros verwenden, um Compiler- und Linkeroptionen aufzulisten, die unabhängig davon gelten, ob Sie ein Debug- oder die endgültige Version der ausführbaren Datei der Anwendung erstellen. Es gibt auch ein LIBS-Makro, in dem Sie die Bibliotheken auflisten, die Ihr Projekt benötigt.

Das makefile verwendet auch ! Wenn! oder! ENDIF, um zu erkennen, ob Sie ein DEBUG-Symbol in der NMAKE-Befehlszeile definieren:

```NMAKE
NMAKE DEBUG=[1|0]
```

Diese Funktion ermöglicht es Ihnen, das gleiche Makefile während der Entwicklung und für die endgültigen Versionen Ihres Programms zu verwenden – verwenden Sie DEBUG=0 für die endgültigen Versionen. Die folgenden Befehlszeilen sind äquivalent:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Weitere Informationen zu Makefiles finden Sie unter [NMAKE Reference](reference/nmake-reference.md). Siehe auch [MSVC Compileroptionen](reference/compiler-options.md) und die [MSVC Linker-Optionen](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Beispielcode für PCH

Die folgenden Quelldateien werden in der Makefile verwendet, die in [PCH-Dateien im Buildprozess](#pch-files-in-the-build-process) und [Im Sample Makefile für PCH](#sample-makefile-for-pch)beschrieben wird. Beachten Sie, dass die Kommentare wichtige Informationen enthalten.

```cpp
// ANOTHER.H : Contains the interface to code that is not
//             likely to change.
//
#ifndef __ANOTHER_H
#define __ANOTHER_H
#include<iostream>
void savemoretime( void );
#endif // __ANOTHER_H
```

```cpp
// STABLE.H : Contains the interface to code that is not likely
//            to change. List code that is likely to change
//            in the makefile's STABLEHDRS macro.
//
#ifndef __STABLE_H
#define __STABLE_H
#include<iostream>
void savetime( void );
#endif // __STABLE_H
```

```cpp
// UNSTABLE.H : Contains the interface to code that is
//              likely to change. As the code in a header
//              file becomes stable, remove the header file
//              from the makefile's UNSTABLEHDR macro and list
//              it in the STABLEHDRS macro.
//
#ifndef __UNSTABLE_H
#define __UNSTABLE_H
#include<iostream>
void notstable( void );
#endif // __UNSTABLE_H
```

```cpp
// APPLIB.CPP : This file contains the code that implements
//              the interface code declared in the header
//              files STABLE.H, ANOTHER.H, and UNSTABLE.H.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
using namespace std;
// The following code represents code that is deemed stable and
// not likely to change. The associated interface code is
// precompiled. In this example, the header files STABLE.H and
// ANOTHER.H are precompiled.
void savetime( void )
    { cout << "Why recompile stable code?\n"; }
void savemoretime( void )
    { cout << "Why, indeed?\n\n"; }
// The following code represents code that is still under
// development. The associated header file is not precompiled.
void notstable( void )
    { cout << "Unstable code requires"
            << " frequent recompilation.\n";
    }
```

```cpp
// MYAPP.CPP : Sample application
//             All precompiled code other than the file listed
//             in the makefile's BOUNDRY macro (stable.h in
//             this example) must be included before the file
//             listed in the BOUNDRY macro. Unstable code must
//             be included after the precompiled code.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
int main( void )
{
    savetime();
    savemoretime();
    notstable();
}
```

## <a name="see-also"></a>Siehe auch

[Referenz zur C/C++-Erstellung](reference/c-cpp-building-reference.md)<br/>
[MSVC-Compileroptionen](reference/compiler-options.md)
