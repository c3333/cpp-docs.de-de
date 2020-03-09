---
title: Vorkompilierte Headerdateien
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 071839df431071a7d8921d1b445094f886ad38e2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884091"
---
# <a name="precompiled-header-files"></a>Vorkompilierte Headerdateien

Wenn Sie in Visual Studio ein neues Projekt erstellen, wird dem Projekt eine *Vorkompilierte Header Datei* mit dem Namen " *PCH. h* " hinzugefügt. (In Visual Studio 2017 und früher wurde die Datei " *stdafx. h*" genannt.) Der Zweck der Datei besteht darin, den Buildprozess zu beschleunigen. Alle stabilen Header Dateien, z. b. Standard Bibliotheks Header wie `<vector>`, sollten hier eingeschlossen werden. Der vorkompilierte Header wird nur kompiliert, wenn er oder alle darin enthaltenen Dateien geändert werden. Wenn Sie nur Änderungen im Projekt Quell Code vornehmen, überspringt der Build die Kompilierung für den vorkompilierten Header. 

Die Compileroptionen für vorkompilierte Header sind [/Y](reference/y-precompiled-headers.md). Auf den Eigenschaften Seiten des Projekts befinden sich die Optionen unter **Konfigurations Eigenschaften > vorkompilierte C/>-C++ Header**. Sie können auswählen, dass keine vorkompilierten Header verwendet werden sollen, und Sie können den Namen und den Pfad der Ausgabedatei angeben. 

## <a name="custom-precompiled-code"></a>Benutzerdefinierter vorkompilierter Code

Bei großen Projekten, die viel Zeit für die Erstellung benötigen, sollten Sie die Erstellung benutzerdefinierter vorkompilierter Dateien in Erwägung ziehen. Die Microsoft C- und C++-Compiler stellen Optionen für das Vorkompilieren von beliebigem C- oder C++-Code bereit, einschließlich Inlinecode. Mithilfe dieser leistungsstarken Funktion können Sie einen stabilen Codeabschnitt kompilieren, den Code im kompilierten Zustand in einer Datei speichern und bei nachfolgenden Kompilierungen den vorkompilierten Code mit dem noch in Entwicklung befindlichen Code kombinieren. So können nachfolgende Kompilierungen beschleunigt werden, da der bereits stabile Code nicht neu kompiliert werden muss.

## <a name="when-to-precompile-source-code"></a>Wann sollte Quellcode vorkompiliert werden?

Vorkompilierter Code ist während des Entwicklungsprozesses nützlich, um die Kompilierungszeit zu verkürzen, insbesondere in folgenden:

- Sie verwenden immer einen großen Code Körper, der sich nur selten ändert.

- Ihr Programm umfasst mehrere Module, die alle einen Standardsatz von Include-Dateien und die gleichen Kompilierungsoptionen verwenden. In diesem Fall können alle Include-Dateien in einen vorkompilierten Header vorkompiliert werden.

Die erste Kompilierung – die Datei, die die vorkompilierte Header Datei (PCH-Datei) erstellt – dauert etwas länger als nachfolgende Kompilierungen. Nachfolgende Kompilierungen können schneller fortgesetzt werden, indem der vorkompilierte Code eingeschlossen wird.

Sie können C-und- C++ Programme vorkompilieren. Bei C++ der Programmierung ist es üblich, Klassen Schnittstellen Informationen in Header Dateien zu trennen. Diese Header Dateien können später in Programme eingeschlossen werden, die die-Klasse verwenden. Durch die Vorkompilierung dieser Header können Sie die Zeit verkürzen, die ein Programm für die Kompilierung benötigt.

> [!NOTE]
> Obwohl Sie nur eine vorkompilierte Header Datei (. pch) pro Quelldatei verwenden können, können Sie mehrere PCH-Dateien in einem Projekt verwenden.

## <a name="two-choices-for-precompiling-code"></a>Zwei Methoden für das Vorkompilieren von Code

Sie können C-oder C++ Code vorkompilieren. Sie sind nicht auf die Vorkompilierung von Header Dateien beschränkt.

Vorkompilierung erfordert Planung, bietet jedoch deutlich schnellere Kompilierungen, wenn Sie einen anderen Quellcode als einfache Header Dateien vorkompilieren.

Vorkompilierung von Code, wenn Sie wissen, dass die Quelldateien allgemeine Sätze von Header Dateien verwenden, diese aber nicht in derselben Reihenfolge enthalten oder wenn Sie Quellcode in die Vorkompilierung einschließen möchten.

Die vorkompilierten Header Optionen sind [/Yc (Vorkompilierte Header Datei erstellen)](reference/yc-create-precompiled-header-file.md) und [/Yu (Vorkompilierte Header Datei verwenden)](reference/yu-use-precompiled-header-file.md). Verwenden Sie **/Yc** , um einen vorkompilierten Header zu erstellen. Wenn Sie mit dem optionalen [hdrstopp-](../preprocessor/hdrstop.md) Pragma verwendet wird, können Sie mit **/Yc** sowohl Header Dateien als auch Quellcode vorkompilieren. Wählen Sie **/Yu** aus, um einen vorhandenen vorkompilierten Header in der vorhandenen Kompilierung zu verwenden. Sie können auch **/FP** mit den Optionen **/Yc** und **/Yu** verwenden, um einen alternativen Namen für den vorkompilierten Header bereitzustellen.

In den Referenz Themen der Compileroption für **/Yu** und **/Yc** wird erläutert, wie Sie auf diese Funktionalität in der Entwicklungsumgebung zugreifen können.

## <a name="precompiled-header-consistency-rules"></a>Konsistenzregeln für vorkompilierte Header

Da PCH-Dateien Informationen über die Computerumgebung sowie Informationen zur Speicheradresse des Programms enthalten, sollten Sie nur eine PCH-Datei auf dem Computer verwenden, auf dem Sie erstellt wurde.

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>Konsistenzregeln zur Verwendung einer vorkompilierten Headerdatei

Mit der [/Yu](reference/yu-use-precompiled-header-file.md) -Compileroption können Sie angeben, welche PCH-Datei verwendet werden soll.

Wenn Sie eine PCH-Datei verwenden, nimmt der Compiler dieselbe Kompilierungs Umgebung an – eine, die konsistente Compileroptionen, Pragmas usw. verwendet –, die beim Erstellen der PCH-Datei wirksam war, sofern nicht anders angegeben. Wenn der Compiler eine Inkonsistenz erkennt, gibt er eine Warnung aus und identifiziert, wenn möglich, die Inkonsistenz. Diese Warnungen weisen nicht unbedingt auf ein Problem mit der PCH-Datei hin. Sie warnen lediglich von möglichen Konflikten. Die Konsistenz Anforderungen für PCH-Dateien werden in den folgenden Abschnitten beschrieben.

### <a name="compiler-option-consistency"></a>Konsistenz der Compileroptionen

Die folgenden Compileroptionen können bei Verwendung einer PCH-Datei eine Inkonsistenz Warnung auslöst:

- Makros, die mithilfe der Präprozessoroption (/D) erstellt wurden, müssen zwischen der Kompilierung, die die PCH-Datei und die aktuelle Kompilierung erstellt hat, identisch sein. Der Zustand der definierten Konstanten ist nicht aktiviert, aber unvorhersehbare Ergebnisse können auftreten, wenn sich diese ändern.

- PCH-Dateien funktionieren nicht mit den Optionen/E und/EP.

- PCH-Dateien müssen entweder mithilfe der Option zum Generieren von Suchinformationen (/FR) oder mit der Option Lokale Variablen ausschließen (/FR) erstellt werden, bevor nachfolgende Kompilierungen, die die PCH-Datei verwenden, diese Optionen verwenden können.

### <a name="c-70-compatible-z7"></a>C 7,0-kompatibel (/Z7)

Wenn diese Option aktiviert ist, wenn die PCH-Datei erstellt wird, können nachfolgende Kompilierungen, die die PCH-Datei verwenden, die Debuginformationen verwenden.

Wenn die Option C 7,0-kompatibel (/Z7) bei der Erstellung der PCH-Datei nicht wirksam ist, lösen nachfolgende Kompilierungen, die die PCH-Datei und/Z7 verwenden, eine Warnung aus. Die Debuginformationen werden in der aktuellen obj-Datei abgelegt, und lokale Symbole, die in der PCH-Datei definiert sind, sind für den Debugger nicht verfügbar.

### <a name="include-path-consistency"></a>Pfad Konsistenz einschließen

Eine PCH-Datei enthält keine Informationen über den Includepfad, der beim Erstellen wirksam war. Wenn Sie eine PCH-Datei verwenden, verwendet der Compiler immer den Includepfad, der in der aktuellen Kompilierung angegeben ist.

### <a name="source-file-consistency"></a>Konsistenz der Quelldatei

Wenn Sie die Option Vorkompilierte Header Datei verwenden (/Yu) angeben, ignoriert der Compiler alle Präprozessordirektiven (einschließlich Pragmas), die im Quellcode angezeigt werden, der vorkompiliert wird. Die von diesen Präprozessordirektiven angegebene Kompilierung muss mit der Kompilierung identisch sein, die für die Option Vorkompilierte Header Datei erstellen (/YC) verwendet wird.

### <a name="pragma-consistency"></a>Pragma-Konsistenz

Pragmas, die während der Erstellung einer PCH-Datei verarbeitet werden, wirken sich normalerweise auf die Datei aus, mit der die PCH-Datei anschließend verwendet wird Die `comment`-und `message`-Pragmas haben keine Auswirkung auf den Rest der Kompilierung.

Diese Pragmas wirken sich nur auf den Code in der PCH-Datei aus. Sie wirken sich nicht auf Code aus, der anschließend die PCH-Datei verwendet:

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

Diese Pragmas werden als Teil eines vorkompilierten Headers beibehalten und beeinflussen den Rest einer Kompilierung, die den vorkompilierten Header verwendet:

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>Konsistenzregeln für "/Yc" und "/Yu"

Wenn Sie einen vorkompilierten Header verwenden, der mit/Yc oder/Yu erstellt wurde, vergleicht der Compiler die aktuelle Kompilierungs Umgebung mit der, die beim Erstellen der PCH-Datei vorhanden war. Stellen Sie sicher, dass Sie eine Umgebung angeben, die mit der vorherigen übereinstimmt (mit konsistenten Compileroptionen, Pragmas usw.), um die aktuelle Kompilierung zu verwenden. Wenn der Compiler eine Inkonsistenz erkennt, gibt er eine Warnung aus und identifiziert, wenn möglich, die Inkonsistenz. Diese Warnungen weisen nicht unbedingt auf ein Problem mit der PCH-Datei hin. Sie warnen lediglich von möglichen Konflikten. In den folgenden Abschnitten werden die Konsistenz Anforderungen für vorkompilierte Header erläutert.

### <a name="compiler-option-consistency"></a>Konsistenz der Compileroptionen

In dieser Tabelle sind Compileroptionen aufgeführt, die bei Verwendung eines vorkompilierten Headers möglicherweise eine Inkonsistenz Warnung auslöst:

|Option|Name|Regel|
|------------|----------|----------|
|/D|Definieren von Konstanten und Makros|Muss zwischen der Kompilierung, die den vorkompilierten Header erstellt hat, und der aktuellen Kompilierung identisch sein. Der Zustand der definierten Konstanten ist nicht aktiviert, aber unvorhersehbare Ergebnisse können auftreten, wenn die Dateien von den Werten der geänderten Konstanten abhängig sind.|
|/E oder/EP|Präprozessorausgabe in Standardausgabe kopieren|Vorkompilierte Header können nicht mit der/E-Option oder der/EP-Option verwendet werden.|
|/FR oder/Fr|Informationen zum Microsoft-Quell Browser generieren|Damit die Optionen/fr und/fr mit der Option/Yu gültig sind, müssen Sie auch beim Erstellen des vorkompilierten Headers wirksam werden. Nachfolgende Kompilierungen, die den vorkompilierten Header verwenden, generieren ebenfalls Quell Browser Informationen. Browser Informationen werden in einer einzelnen SBR-Datei platziert, und auf die gleiche Weise wird von anderen Dateien auf dieselbe Weise wie CodeView-Informationen verwiesen. Die Platzierung der Quell Browser Informationen kann nicht überschrieben werden.|
|/GA,/GD,/ge,/GW oder/GW|Windows-Protokoll Optionen|Muss zwischen der Kompilierung, die den vorkompilierten Header erstellt hat, und der aktuellen Kompilierung identisch sein. Wenn sich diese Optionen unterscheiden, führt dies zu einer Warnmeldung.|
|/ZI|Umfassende Debuginformationen generieren|Wenn diese Option beim Erstellen des vorkompilierten Headers wirksam ist, können nachfolgende Kompilierungen, die die Vorkompilierung verwenden, diese Debuginformationen verwenden. Wenn/Zi beim Erstellen des vorkompilierten Headers nicht wirksam ist, wird bei nachfolgenden Kompilierungen, bei denen die Vorkompilierung und die/ZI-Option verwendet wird, eine Warnung ausgelöst. Die Debuginformationen werden in der aktuellen Objektdatei abgelegt, und lokale Symbole, die im vorkompilierten Header definiert sind, sind für den Debugger nicht verfügbar.|

> [!NOTE]
>  Die vorkompilierte Header Funktion ist nur für die Verwendung in C C++ -und Quelldateien vorgesehen.

## <a name="using-precompiled-headers-in-a-project"></a>Verwenden von vorkompilierten Headern in einem Projekt

Die vorherigen Abschnitte enthalten eine Übersicht über vorkompilierte Header:/Yc und/Yu, die/FP-Option und das [hdrstopps](../preprocessor/hdrstop.md) -Pragma. In diesem Abschnitt wird eine Methode für die Verwendung der manuellen vorkompilierten Header Optionen in einem Projekt beschrieben. Sie endet mit einem Beispiel Makefile und dem Code, den Sie verwaltet.

Wenn Sie die manuellen Optionen für vorkompilierte Header in einem Projekt verwenden möchten, überprüfen Sie eine der Makefiles, die sich im Verzeichnis MFC\SRC befinden, das während der Standardinstallation von Visual Studio erstellt wird. Diese Makefiles haben einen ähnlichen Ansatz wie in diesem Abschnitt, machen aber eine größere Nutzung der Makros des Microsoft Program Maintenance Utility (NMAKE) und bieten eine bessere Kontrolle über den Buildprozess.

## <a name="pch-files-in-the-build-process"></a>PCH-Dateien im Erstellungsvorgang

Die Codebasis eines Softwareprojekts ist in der Regel in mehreren C- C++ oder Quelldateien, Objektdateien, Bibliotheken und Header Dateien enthalten. In der Regel koordiniert ein Makefile die Kombination dieser Elemente in eine ausführbare Datei. In der folgenden Abbildung wird die Struktur eines Makefile gezeigt, das eine vorkompilierte Header Datei verwendet. Die NMAKE-Makronamen und die Dateinamen in diesem Diagramm sind mit denen im Beispielcode in [Beispiel Makefile für PCH](#sample-makefile-for-pch) und [Beispielcode für PCH](#example-code-for-pch)konsistent.

In der Abbildung werden drei Diagramm Geräte verwendet, um den Ablauf des Buildprozesses anzuzeigen. Benannte Rechtecke stellen jede Datei bzw. jedes Makro dar. die drei Makros stellen eine oder mehrere Dateien dar. Schattierte Bereiche stellen jede Kompilierungs-oder Verknüpfungs Aktion dar. Pfeile zeigen, welche Dateien und Makros während des Kompilierungs-oder Verknüpfungs Vorgangs kombiniert werden.

![Struktur eines Makefile, das eine vorkompilierte Header Datei verwendet](media/vc30ow1.gif "Struktur eines Makefile, das eine vorkompilierte Header Datei verwendet") <br/>
Struktur eines Makefiles, das eine vorkompilierte Headerdatei verwendet

Beginnend am oberen Rand des Diagramms sind "STABLEHDRS" und "BOUNDRY" NMAKE-Makros, in denen Sie Dateien auflisten, die wahrscheinlich nicht neu kompiliert werden müssen. Diese Dateien werden von der Befehls Zeichenfolge kompiliert.

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

nur, wenn die vorkompilierte Header Datei (stable. pch) nicht vorhanden ist oder wenn Sie Änderungen an den Dateien vornehmen, die in den beiden Makros aufgeführt sind. In beiden Fällen enthält die vorkompilierte Header Datei nur Code aus den Dateien, die im-Makro von STABLEHDRS aufgelistet sind. Listet die letzte Datei auf, die im BOUNDRY-Makro vorkompiliert werden soll.

Die Dateien, die Sie in diesen Makros auflisten, können entweder Header-oder C++ C-oder Quelldateien sein. (Eine einzelne PCH-Datei kann nicht sowohl mit C- C++ als auch mit Modulen verwendet werden.) Beachten Sie, dass Sie das **hdrstoppt** -Makro verwenden können, um die Vorkompilierung zu einem bestimmten Zeitpunkt in der BOUNDRY-Datei zu verhindern. Weitere Informationen finden Sie unter [hdrstopp.](../preprocessor/hdrstop.md)

Wenn Sie das Diagramm fortsetzen, stellt APPLIB. obj den in der endgültigen Anwendung verwendeten Unterstützungs Code dar. Sie wird aus "APPLIB. cpp", den im UNSTABLEHDRS-Makro aufgelisteten Dateien und dem vorkompilierten Code aus dem vorkompilierten Header erstellt.

MyApp. obj stellt die endgültige Anwendung dar. Es wird aus MyApp. cpp, den im UNSTABLEHDRS-Makro aufgelisteten Dateien und dem vorkompilierten Code aus dem vorkompilierten Header erstellt.

Zum Schluss die ausführbare Datei (MyApp. EXE) wird erstellt, indem die im OBJS-Makro ("APPLIB. obj" und "MyApp. obj") aufgeführten Dateien verknüpft werden.

## <a name="sample-makefile-for-pch"></a>Beispielmakefile für PCH

Das folgende Makefile verwendet Makros und eine! Wenn,! Andernfalls! Einflusssteuerungs-Befehlsstruktur, um die Anpassung Ihres Projekts zu vereinfachen.

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

Abgesehen von den Makros STABLEHDRS, BOUNDRY und UNSTABLEHDRS, die in der Abbildung "Struktur eines Makefile, das eine vorkompilierte Header Datei verwendet" in [PCH-Dateien im Buildprozess](#pch-files-in-the-build-process)verwendet, stellt dieses Makefile ein CLFLAGS-Makro und ein LINKFLAGS-Makro bereit. Sie müssen diese Makros verwenden, um Compiler-und Linkeroptionen aufzulisten, die unabhängig davon gelten, ob Sie eine Debugversion oder eine endgültige Version der ausführbaren Datei der Anwendung erstellen. Es gibt auch ein lisb-Makro, in dem Sie die Bibliotheken auflisten, die für das Projekt erforderlich sind.

Das Makefile verwendet auch! Wenn,! Andernfalls! EndIf, um zu erkennen, ob Sie ein Debugsymbol in der NMAKE-Befehlszeile definieren:

```NMAKE
NMAKE DEBUG=[1|0]
```

Diese Funktion ermöglicht es Ihnen, dasselbe Makefile während der Entwicklung und für die endgültigen Versionen des Programms zu verwenden – verwenden Sie für die endgültigen Versionen Debug = 0. Die folgenden Befehlszeilen sind äquivalent:

```NMAKE
NMAKE
NMAKE DEBUG=0
```

Weitere Informationen zu Makefiles finden Sie unter [NMAKE Reference](reference/nmake-reference.md). Weitere Informationen finden Sie auch unter [MSVC-Compileroptionen](reference/compiler-options.md) und [MSVC-Linkeroptionen](reference/linker-options.md).

## <a name="example-code-for-pch"></a>Beispielcode für PCH

Die folgenden Quelldateien werden im Makefile verwendet, das in [PCH-Dateien im Buildprozess](#pch-files-in-the-build-process) und im [Beispiel Makefile für PCH](#sample-makefile-for-pch)beschrieben wird. Beachten Sie, dass die Kommentare wichtige Informationen enthalten.

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

## <a name="see-also"></a>Weitere Informationen

[Referenz zur C/C++-Erstellung](reference/c-cpp-building-reference.md)<br/>
[MSVC-Compileroptionen](reference/compiler-options.md)
