---
title: Vorkompilierte Headerdateien
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: c68de0ee8e6376731254adf965fb9a81f10f2861
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838853"
---
# <a name="precompiled-header-files"></a>Vorkompilierte Headerdateien

Wenn Sie ein neues Projekt in Visual Studio erstellen, wird eine *vorkompilierte Headerdatei* namens *pch.h* zum Projekt hinzugefügt. (In Visual Studio 2017 und früher trug die Datei den Namen *stdafx.h*.) Der Zweck dieser Datei besteht darin, den Buildprozess zu beschleunigen. Alle stabilen Headerdateien, z. B. Standardbibliotheksheader wie `<vector>`, sollten hier eingefügt werden. Der vorkompilierte Header nur kompiliert, wenn er oder jegliche in ihm enthaltene Dateien geändert werden. Wenn Sie Änderungen am Quellcode Ihres Projekts vornehmen, überspringt der Buildprozess die Kompilierung des vorkompilierten Headers.

Die Compileroptionen für vorkompilierte Header finden Sie unter [/Y](reference/y-precompiled-headers.md). Auf den Projekteigenschaftenseiten finden Sie die Optionen unter **Konfigurationseigenschaften > C/C++ > Vorkompilierte Header**. Sie können sich dazu entscheiden, keine vorkompilierten Header zu verwenden, und den Headerdateinamen sowie den Namen und Pfad der Ausgabedatei festlegen.

## <a name="custom-precompiled-code"></a>Benutzerdefinierter vorkompilierter Code

Für große Projekte, deren Buildprozesse einige Zeit beanspruchen, sollten Sie das Erstellen benutzerdefinierter vorkompilierter Dateien in Erwägung ziehen. Die Microsoft C- und C++-Compiler stellen Optionen für das Vorkompilieren von beliebigem C- oder C++-Code bereit, einschließlich Inlinecode. Mithilfe dieser leistungsstarken Funktion können Sie einen stabilen Codeabschnitt kompilieren, den Code im kompilierten Zustand in einer Datei speichern und bei nachfolgenden Kompilierungen den vorkompilierten Code mit dem noch in Entwicklung befindlichen Code kombinieren. So können nachfolgende Kompilierungen beschleunigt werden, da der bereits stabile Code nicht neu kompiliert werden muss.

## <a name="when-to-precompile-source-code"></a>Wann sollte Quellcode vorkompiliert werden?

Vorkompilierter Code ist während des Entwicklungsprozesses nützlich, um die Kompilierungszeit zu reduzieren. Dies gilt insbesondere in folgenden Fällen:

- Sie verwenden immer umfangreiche Codeabschnitte, die häufig geändert werden.

- Ihr Programm besteht aus mehreren Modulen, die alle eine Standardgruppe von Includedateien und die gleichen Kompilierungsoptionen verwenden. In diesem Fall können alle Dateien in einen vorkompilierten Header vorab kompiliert werden.

Die erste Kompilierung, bei der die vorkompilierte Headerdatei (PCH) erstellt wird, dauert ein wenig länger als darauffolgende Kompilierungen. Nachfolgende Kompilierungen können schneller fortgesetzt werden, indem der vorkompilierte Code eingefügt wird.

Sie können sowohl C- als auch C++-Programme vorkompilieren. Bei der C++-Programmierung ist es üblich, Klassenschnittstelleninformationen in Headerdateien zu unterteilen. Diese Headerdateien können später in Programme eingefügt werden, die die Klasse verwenden. Indem Sie diese Header vorkompilieren, können Sie die Zeit reduzieren, die die Kompilierung eines Programms erfordert.

> [!NOTE]
> Sie können zwar nur eine vorkompilierte Headerdatei (PCH) pro Quelldatei verwenden, aber Sie können mehrere PCH-Dateien in einem Projekt verwenden.

## <a name="two-choices-for-precompiling-code"></a>Zwei Methoden für das Vorkompilieren von Code

Sie können beliebigen C- oder C++-Code vorkompilieren. Sie sind nicht auf die Vorkompilierung von Headerdateien eingeschränkt.

Die Vorkompilierung erfordert Planung, jedoch bietet sie schnellere Kompilierungen, wenn Sie nicht nur einfache Headerdateien, sondern auch Quellcode vorkompilieren.

Kompilieren Sie Code vorab, wenn Sie wissen, dass Ihre Quelldateien die gleichen Headerdateien verwenden, diese aber nicht in der gleichen Reihenfolge enthalten, oder wenn Sie Quellcode in Ihre Vorkompilierung einfügen möchten.

Die Optionen für vorkompilierte Header sind [/Yc (vorkompilierte Headerdatei erstellen)](reference/yc-create-precompiled-header-file.md) und [/Yu (vorkompilierte Headerdatei verwenden)](reference/yu-use-precompiled-header-file.md). Verwenden Sie die Option **/Yc**, um einen vorkompilierten Header zu erstellen. Wenn die Option **/Yc** mit dem optionalen Pragma [hdrstop](../preprocessor/hdrstop.md) verwendet wird, können Sie sowohl Headerdateien als auch Quellcode vorkompilieren. Verwenden Sie **/Yu**, um einen vorhandenen vorkompilierten Header in der bestehenden Kompilierung zu verwenden. Sie können auch **/Fp** mit den Optionen **/Yc** und **/Yu** verwenden, um einen alternativen Namen für den vorkompilierten Header anzugeben.

In den Referenzartikeln zu den Compileroptionen **/Yu** und **/Yc** wird behandelt, wie in der Entwicklungsumgebung auf diese Funktionalität zugegriffen wird.

## <a name="precompiled-header-consistency-rules"></a>Konsistenzregeln für vorkompilierte Header

Da PCH-Dateien Informationen zur Computerumgebung und Speicheradresseninformationen zum Programm enthalten, sollten Sie eine PCH-Datei nur auf dem Computer verwenden, auf dem sie erstellt wurde.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Konsistenzregeln zur Verwendung einer vorkompilierten Headerdatei

Mit der Compileroption [/Yu](reference/yu-use-precompiled-header-file.md) können Sie festlegen, welche PCH-Datei verwendet werden soll.

Wenn Sie eine PCH-Datei verwenden, nimmt der Compiler dieselbe Kompilierungsumgebung an (mit konsistenten Compileroptionen, Pragmas usw.), die zu dem Zeitpunkt aktiv war, als Sie die PCH-Datei erstellt haben, es sei denn, Sie legen etwas anderes fest. Wenn der Compiler eine Inkonsistenz erkennt, wird eine Warnung ausgegeben und die Inkonsistenz wird identifiziert, wenn möglich. Solche Warnungen weisen nicht unbedingt auf ein Problem mit der PCH-Datei hin. Sie dienen lediglich dazu, Sie vor möglichen Konflikten zu warnen. In den folgenden Abschnitten werden die Konsistenzanforderungen für PCH-Dateien behandelt.

### <a name="compiler-option-consistency"></a>Konsistenz der Compileroptionen

Die folgenden Compileroptionen können bei Verwendung einer PCH-Datei eine Inkonsistenzwarnung auslösen:

- Makros, die mithilfe der Präprozessoroption (/D) erstellt wurden, müssen in der Kompilierung, in der die PCH-Datei erstellt wurde, und der aktuellen Kompilierung identisch sein. Der Zustand definierter Konstanten wird nicht überprüft, jedoch können unvorhersehbare Ergebnisse auftreten, wenn diese geändert werden.

- PCH-Dateien funktionieren nicht mit den Optionen /E und /EP.

- PCH-Dateien müssen entweder mit der Option zum Generieren von Browseinformationen (/FR) oder der Option zum Ausschließen von lokalen Variablen (/Fr) erstellt werden, bevor nachfolgende Kompilierungen, die diese PCH-Dateien verwenden, diese Optionen verwenden können.

### <a name="c-70-compatible-z7"></a>C 7.0-Kompatibilität (/Z7)

Wenn diese Option bei Erstellung der PCH-Datei aktiv ist, können nachfolgende Kompilierungen, die die PCH-Datei verwenden, die Debuginformationen verwenden.

Wenn die Option für die C 7.0-Kompatibilität (/Z7) nicht aktiv ist, wenn die PCH-Datei erstellt wird, lösen nachfolgende Kompilierungen, die die PCH-Datei und /Z7 verwenden, eine Warnung aus. Die Debuginformationen werden in der aktuellen OBJ-Datei platziert, und die in der PCH-Datei definierten lokalen Symbole sind nicht für den Debugger verfügbar.

### <a name="include-path-consistency"></a>Implementieren von Pfadkonsistenz

Eine PCH-Datei enthält keine Informationen über den Includepfad, der bei ihrer Erstellung aktiv war. Wenn Sie eine PCH-Datei verwenden, verwendet der Compiler immer den Includepfad, der in der aktuellen Kompilierung festgelegt ist.

### <a name="source-file-consistency"></a>Konsistenz der Quelldatei

Wenn Sie die Option „/Yu“ (vorkompilierte Headerdatei verwenden) festlegen, ignoriert der Compiler alle Präprozessoranweisungen (einschließlich Pragmas), die im Quellcode vorliegen, der vorkompiliert werden soll. Die von solchen Präprozessoranweisungen festgelegte Kompilierung muss mit der Kompilierung übereinstimmen, die für die Option „/Yc“ (vorkompilierte Headerdatei erstellen) verwendet wurde.

### <a name="pragma-consistency"></a>Pragmakonsistenz

Pragmas, die während der Erstellung einer PCH-Datei verarbeitet werden, wirken sich in der Regel auf die Datei aus, mit der die PCH-Datei dann verwendet wird. Die Pragmas `comment` und `message` wirken sich nicht auf die restliche Kompilierung aus.

Die folgenden Pragmas beeinflussen nur den Code in der PCH-Datei. Sie wirken sich nicht auf den Code aus, der dann die PCH-Datei verwendet:

:::row:::
   :::column span="":::
      `comment`\
      `linesize`
   :::column-end:::
   :::column span="":::
      `message`\
      `page`
   :::column-end:::
   :::column span="":::
      `pagesize`\
      `skip`
   :::column-end:::
   :::column span="":::
      `subtitle`\
      `title`
   :::column-end:::
:::row-end:::

Die folgenden Pragmas werden als Teil eines vorkompilierten Headers beibehalten und wirken sich auf die restliche Kompilierung aus, die den vorkompilierten Header verwendet:

:::row:::
   :::column span="":::
      `alloc_text`\
      `auto_inline`\
      `check_stack`\
      `code_seg`\
      `data_seg`
   :::column-end:::
   :::column span="":::
      `function`\
      `include_alias`\
      `init_seg`\
      `inline_depth`
   :::column-end:::
   :::column span="":::
      `inline_recursion`\
      `intrinsic`\
      `optimize`\
      `pack`
   :::column-end:::
   :::column span="":::
      `pointers_to_members`\
      `setlocale`\
      `vtordisp`\
      `warning`
   :::column-end:::
:::row-end:::

## <a name="consistency-rules-for-yc-and-yu"></a>Konsistenzregeln für "/Yc" und "/Yu"

Wenn Sie einen vorkompilierten Header verwenden, der mit „/Yc“ oder „/Yu“ erstellt wurde, vergleicht der Compiler die aktuelle Kompilierungsumgebung mit der, die zum Zeitpunkt der Erstellung der PCH-Datei aktiv war. Stellen Sie sicher, dass Sie für die aktuelle Kompilierung eine Umgebung entsprechend der vorherigen festlegen (mithilfe konsistenter Compileroptionen, Pragmas usw.). Wenn der Compiler eine Inkonsistenz erkennt, wird eine Warnung ausgegeben und die Inkonsistenz wird identifiziert, wenn möglich. Solche Warnungen weisen nicht unbedingt auf ein Problem mit der PCH-Datei hin. Sie dienen lediglich dazu, Sie vor möglichen Konflikten zu warnen. In den folgenden Abschnitten werden die Konsistenzanforderungen für vorkompilierte Header erläutert.

### <a name="compiler-option-consistency"></a>Konsistenz der Compileroptionen

In dieser Tabelle werden die Compileroptionen aufgeführt, die eine Inkonsistenzwarnung auslösen könnten, wenn ein vorkompilierter Header verwendet wird:

|Option|name|Regel|
|------------|----------|----------|
|/D|Define constants and macros (Konstanten und Makros definieren)|Diese Option muss in der Kompilierung, in der der vorkompilierte Header erstellt wurde, und der aktuellen Kompilierung übereinstimmen. Der Zustand definierter Konstanten wird nicht überprüft, jedoch können unvorhersehbare Ergebnisse auftreten, wenn Ihre Dateien von den Werten der geänderten Konstanten abhängig sind.|
|/E oder /EP|Copy preprocessor output to standard output (Präprozessorausgabe in Standardausgabe kopieren)|Vorkompilierte Header können nicht mit der Option „/E“ oder „/EP“ verwendet werden.|
|/Fr oder /FR|Generate Microsoft Source Browser information (Microsoft-Quellbrowserinformationen generieren)|Damit die Optionen „/Fr“ und „/FR“ mit der Option „/Yu“ verwendet werden können, müssen sie auch bei der Erstellung des vorkompilierten Headers aktiv gewesen sein. Nachfolgende Kompilierungen mit dem vorkompilierten Header generieren ebenfalls Quellbrowserinformationen. Browserinformationen werden in einer einzelnen SBR-Datei platziert und auf gleiche Weise wie CodeView-Informationen von anderen Dateien referenziert. Sie können die Platzierung von Quellbrowserinformationen nicht überschreiben.|
|/GA, /GD, /GE, /Gw oder /GW|Windows protocol options (Windows-Protokolloptionen)|Diese Option muss in der Kompilierung, in der der vorkompilierte Header erstellt wurde, und der aktuellen Kompilierung übereinstimmen. Wenn sich diese Optionen unterscheiden, wird eine Warnmeldung ausgelöst.|
|/ZI|Generate complete debugging information (Vollständige Debuginformationen generieren)|Wenn diese Option bei Erstellung des vorkompilierten Headers aktiv ist, können nachfolgende Kompilierungen, die die Vorkompilierung verwenden, die Debuginformationen verwenden. Wenn die Option „/Zi“ bei Erstellung des vorkompilierten Headers aktiv ist, lösen nachfolgende Kompilierungen, die die Vorkompilierung und die Option „/Zi“ verwenden, eine Warnung aus. Die Debuginformationen werden in der aktuellen Objektdatei platziert, und die im vorkompilierten Header definierten lokalen Symbole sind nicht für den Debugger verfügbar.|

> [!NOTE]
> Vorkompilierte Header sind nur zur Verwendung in C- und C++-Quelldateien vorgesehen.

## <a name="using-precompiled-headers-in-a-project"></a>Verwenden von vorkompilierten Headern in einem Projekt

Die obigen Abschnitte veranschaulichen eine Übersicht über vorkompilierte Header: „/Yc“ und „/Yu“, die Option „/Fp“ und das Pragma [hdrstop](../preprocessor/hdrstop.md). In diesem Abschnitt wird eine Methode zur Verwendung der manuellen vorkompilierten Headeroptionen in einem Projekt beschrieben. Der Abschnitt endet mit einem Makefilebeispiel und dem Code, der durch dieses verwaltet wird.

Andere Ansätze zur Verwendung der Optionen für manuell vorkompilierte Header in einem Projekt finden Sie in den Makefiles im Verzeichnis „MFC\SRC“, das bei der Standardinstallation von Visual Studio erstellt wird. Diese Makefiles nutzen einen ähnlichen Ansatz wie in diesem Abschnitt, jedoch nutzen sie NMAKE-Makros (Microsoft Program Maintenance Utility) umfassender und bieten mehr Kontrolle über den Buildprozess.

## <a name="pch-files-in-the-build-process"></a>PCH-Dateien im Erstellungsvorgang

Die Codebasis eines Softwareprojekts ist üblicherweise in mehreren C- oder C++-Quelldateien, Objektdateien, Bibliotheken und Headerdateien enthalten. Ein Makefile koordiniert in der Regel die Kombination dieser Elemente in eine ausführbare Datei. Die folgende Abbildung veranschaulicht die Struktur eines Makefile, das eine vorkompilierte Headerdatei verwendet. Die Dateinamen und Namen der NMAKE-Markos in diesem Diagramm stimmen mit denen im Beispielcode der Abschnitte [Beispielmakefile für PCH](#sample-makefile-for-pch) und [Beispielcode für PCH](#example-code-for-pch) überein.

In der Abbildung werden drei Diagrammelemente zum Veranschaulichen des Ablaufs des Buildprozesses verwendet. Beschriftete Rechtecke stellen einzelne Dateien oder Makros dar. Die drei Makros stellen eine oder mehrere Dateien dar. Schattierte Bereiche stellen Kompilierungs- oder Verknüpfungsaktionen dar. Die Pfeile geben an, welche Dateien und Makros während des Kompilierungs- oder Verknüpfungsprozesses kombiniert werden.

![Struktur eines Makefiles, das eine vorkompilierte Headerdatei verwendet](media/vc30ow1.gif "Struktur eines Makefiles, das eine vorkompilierte Headerdatei verwendet") <br/>
Struktur eines Makefiles, das eine vorkompilierte Headerdatei verwendet

Am oberen Rand des Diagramms befinden sich die NMAKE-Makros STABLEHDRS und BOUNDRY, in denen Sie Dateien auflisten, die wahrscheinlich nicht erneut kompiliert werden müssen. Diese Dateien werden nur von der Befehlszeichenfolge

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

kompiliert, wenn die vorkompilierte Headerdatei (STABLE.pch) nicht vorhanden ist oder wenn Sie Änderungen an den Dateien vornehmen, die in den zwei Makros aufgeführt werden. In beiden Fällen enthält die vorkompilierte Headerdatei nur Code aus den Dateien, die im STABLEHDRS-Marko enthalten sind. Geben Sie die Datei, die zuletzt vorkompiliert werden soll, im Makro BOUNDRY an.

Bei den Dateien, die Sie in diesen Makros aufführen, kann es sich entweder um Headerdateien oder C- bzw. C++-Quelldateien handeln. (Eine einzelne PCH-Datei kann nicht sowohl mit C- als auch mit C++-Modulen verwendet werden.) Beachten Sie, dass Sie das Makro **hdrstop** verwenden können, um die Vorkompilierung zu einem bestimmten Zeitpunkt innerhalb der BOUNDRY-Datei zu beenden. Weitere Informationen hierzu finden Sie unter [hdrstop](../preprocessor/hdrstop.md).

Im weiteren Verlauf des Diagramm stellt die Objektdatei „APPLIB.obj“ den Unterstützungscode dar, der in Ihrer endgültigen Anwendung verwendet wird. Diese wird aus „APPLIB.cpp“, den im Makro UNSTABLEHDRS aufgeführten Dateien und dem vorkompilierten Code des vorkompilierten Headers erstellt.

Die Objektdatei „MYAPP.obj“ stellt Ihre endgültige Anwendung dar. Sie wird aus „MYAPP.cpp“, den im Makro UNSTABLEHDRS aufgeführten Dateien und dem vorkompilierten Code des vorkompilierten Headers erstellt.

Schließlich wird die ausführbare Datei („MYAPP.exe“) erstellt, indem die im OBJS-Makro aufgeführten Dateien verknüpft werden („APPLIB.obj“ und „MYAPP.obj“).

## <a name="sample-makefile-for-pch"></a>Beispielmakefile für PCH

Das folgende Makefile verwendet Makros und eine Befehlskontrollstruktur mit !IF-, !ELSE- und !ENDIF-Anweisungen, um die Implementierung in Ihr Projekt zu vereinfachen.

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

Neben den Makros STABLEHDRS, BOUNDRY und UNSTABLEHDRS, die auf der Abbildung „Struktur eines Makefiles, das eine vorkompilierte Headerdatei verwendet“ im Abschnitt [PCH-Dateien im Erstellungsvorgang](#pch-files-in-the-build-process) veranschaulicht wurden, stellt dieses Makefile ein CLFLAGS-Makro und ein LINKFLAGS-Makro bereit. Sie müssen diese Makros verwenden, um Compiler- und Linkeroptionen aufzulisten, die unabhängig davon angewendet werden, ob Sie eine Debugversion oder die endgültige Version der ausführbaren Datei erstellen. Es gibt auch ein LIBS-Makro, bei dem Sie die Bibliotheken aufführen, die Ihr Projekt erfordert.

Das Makefile verwendet ebenfalls die Anweisungen !IF, !ELSE und !ENDIF, um zu ermitteln, ob Sie ein DEBUG-Symbol in der NMAKE-Befehlszeile definieren:

```NMAKE
NMAKE DEBUG=[1|0]
```

Über dieses Feature können Sie dasselbe Makefile während der Entwicklung und für die endgültigen Versionen Ihres Programms verwenden. Verwenden Sie „DEBUG=0“ für die endgültigen Versionen. Die folgenden Befehlszeilen sind gleichwertig:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Weitere Informationen über Makefiles finden Sie unter [NMAKE-Referenz](reference/nmake-reference.md), [MSVC-Compileroptionen](reference/compiler-options.md) und [MSVC-Linkeroptionen](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Beispielcode für PCH

Die folgenden Quelldateien werden in den Makefiles verwendet, die in den Abschnitten [PCH-Dateien im Erstellungsvorgang](#pch-files-in-the-build-process) und [Beispielmakefile für PCH](#sample-makefile-for-pch) beschrieben wurde. Beachten Sie, dass die Kommentare wichtige Informationen enthalten.

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
