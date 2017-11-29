---
title: -MP (erstellen mit mehreren Prozessen) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCCLCompilerTool.MultiProcessorCompilation
dev_langs: C++
helpviewer_keywords:
- -MP compiler option (C++)
- /MP compiler option (C++)
- MP compiler option (C++)
- cl.exe compiler, multi-process build
ms.assetid: a932b14a-74fe-4b45-84e4-6bf53f0f5e07
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4cb43b7c3535fd5e09d08e1e488cf9ea3f39631a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="mp-build-with-multiple-processes"></a>/MP (Erstellen mit mehreren Prozessen)
Die Option **/MP** kann die Gesamtzeit für die Kompilierung der Quelldateien in der Befehlszeile reduzieren. Die Option **/MP** bewirkt, dass der Compiler eine oder mehrere Kopien von sich selbst erstellt, jeweils in einem separaten Prozess. Diese Kopien kompilieren dann gleichzeitig die Quelldateien. Daher kann die Gesamtzeit für die Erstellung der Quelldateien erheblich reduziert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
/MP[processMax]  
```  
  
## <a name="arguments"></a>Argumente  
 `processMax`  
 (Optional) Die maximale Anzahl von Prozessen, die der Compiler erstellen kann.  
  
 Das `processMax` -Argument muss zwischen 1 und 65536 liegen. Andernfalls gibt der Compiler die Warnmeldung `D9014`aus, ignoriert das `processMax` -Argument und nimmt an, dass die maximale Anzahl von Prozessen 1 ist.  
  
 Wenn Sie das `processMax` -Argument weglassen, fragt der Compiler die Anzahl der [effektiven Prozessoren](#effective_processors) auf dem Computer aus dem Betriebssystem ab und erstellt einen Prozess für jeden Prozessor.  
  
## <a name="remarks"></a>Hinweise  
 Die Compileroption **/MP** kann beim Kompilieren vieler Dateien die Buildzeit beträchtlich reduzieren. Zur Verbesserung der Buildzeit erstellt der Compiler bis zu `processMax` Kopien von sich selbst und verwendet dann diese Kopien, um die Quelldateien gleichzeitig zu kompilieren. Die Option **/MP** gilt für Kompilierungen, jedoch nicht für das Linken oder die Link-Zeitcodegenerierung. Standardmäßig ist die Option **/MP** Option deaktiviert.  
  
 Die Verbesserung der Buildzeit hängt von der Anzahl der Prozessoren auf einem Computer ab, der Anzahl der zu kompilierenden Dateien und der Verfügbarkeit von Systemressourcen, z.B. der E/A-Kapazität. Experimentieren Sie mit der Option **/MP** , um die beste Einstellung zum Erstellen eines bestimmten Projekts zu bestimmen. Ratschläge, die Sie bei dieser Entscheidung unterstützen, finden Sie unter [Richtlinien](#guidelines).  
  
## <a name="incompatible-options-and-language-features"></a>Inkompatible Optionen und Sprachfunktionen  
 Die Option **/MP** ist mit einigen Compileroptionen und Sprachfunktionen nicht kompatibel. Wenn Sie eine nicht kompatible Compileroption mit der Option **/MP** verwenden, gibt der Compiler die Warnung `D9030` aus und ignoriert die Option **/MP** . Wenn Sie eine nicht kompatible Sprachfunktion verwenden, meldet der Compiler Fehler `C2813` und beendet oder fährt fort, abhängig von der aktuellen Compilerwarnstufe.  
  
> [!NOTE]
>  Die meisten Optionen sind nicht kompatibel, denn wenn sie zulässig wären, würden die gleichzeitig ausgeführten Compiler ihre Ausgabe zur gleichen Zeit auf die Konsole oder in eine bestimmte Datei schreiben. Daher wäre die Ausgabe vermischt und verstümmelt. In einigen Fällen würde die Kombination von Optionen die Leistung verschlechtern.  
  
 Die folgende Tabelle enthält die Compileroptionen und Sprachfunktionen, die nicht mit der Option **/MP** kompatibel sind:  
  
|Option oder Sprachfunktion|Beschreibung|  
|--------------------------------|-----------------|  
|[#import](../../preprocessor/hash-import-directive-cpp.md) Präprozessordirektive|Konvertiert die Typen in einer Typbibliothek in C++-Klassen und schreibt diese Klassen dann in eine Headerdatei.|  
|[/E](../../build/reference/e-preprocess-to-stdout.md), [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiert die Präprozessorausgabe in die Standardausgabe (**stdout**).|  
|[/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|Ermöglicht eine inkrementelle erneute Erstellung.|  
|[/showIncludes](../../build/reference/showincludes-list-include-files.md)|Schreibt eine Liste von Includedateien in den Standardfehler (**stderr**).|  
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|Schreibt eine vorkompilierte Headerdatei.|  
  
## <a name="diagnostic-messages"></a>Diagnosemeldungen  
 Wenn Sie eine Option oder Sprachfunktion angeben, die nicht mit der Option **/MP** kompatibel ist, erhalten Sie eine Diagnosemeldung. Die folgende Tabelle enthält die Meldungen und das Verhalten des Compilers:  
  
|Diagnosemeldung|Beschreibung|Compilerverhalten|  
|------------------------|-----------------|-----------------------|  
|`C2813`|Die **#import** Direktive ist nicht kompatibel mit der Option **/MP** Option.|Die Kompilierung endet, sofern keine Option für [Compilerwarnstufen](../../build/reference/compiler-option-warning-level.md) etwas anderes angibt.|  
|`D9014`|Ein ungültiger Wert ist für das `processMax` -Argument angegeben.|Der Compiler ignoriert den ungültigen Wert und nimmt den Wert 1 an.|  
|`D9030`|Die angegebene Option ist nicht kompatibel mit **/MP**.|Der Compiler ignoriert die Option **/MP** .|  
  
##  <a name="guidelines"></a> Richtlinien  
  
### <a name="measure-performance"></a>Messen der Leistung  
 Verwenden Sie die gesamte Buildzeit zum Messen der Leistung. Sie können die Buildzeit mit einer physischen Uhr messen, oder Sie können Software verwenden, die den Unterschied zwischen Start und Ende des Build berechnet. Wenn Ihr Computer über mehrere Prozessoren verfügt, kann eine physische Uhr genauere Ergebnisse als eine Software-Zeitmessung ergeben.  
  
###  <a name="effective_processors"></a> Effective Processors  
 Ein Computer kann über einen oder mehrere virtuelle Prozessoren, die auch als effektive Prozessoren bekannt sind, für jeden seiner physischen Prozessoren verfügen. Jeder physischer Prozessor kann einen oder mehrere Kerne haben, und wenn das Betriebssystem für einen Kern Hyperthreading ermöglicht, erscheint jeder Kern als zwei virtuelle Prozessoren.  
  
 Beispiel: Ein Computer verfügt über einen effektiven Prozessor, wenn er einen physischen Prozessor mit einem Kern besitzt und Hyperthreading deaktiviert ist. Im Gegensatz dazu besitzt ein Computer acht effektive Prozessoren, wenn er zwei physische Prozessoren mit jeweils zwei Kernen hat und alle Kerne Hyperthreading aktiviert haben. D. h. (8 effektive Prozessoren) = (2 physische Prozessoren) x (2 Kerne pro physischem Prozessor) x (2 effektive Prozessoren pro Kern wegen Hyperthreading).  
  
 Wenn Sie das `processMax` -Argument in der Option **/MP** weglassen, ruft der Compiler die Anzahl der effektiven Prozessoren vom Betriebssystem ab und erstellt dann einen Prozess pro effektivem Prozessor. Jedoch kann der Compiler nicht garantieren, welcher Prozess auf einem bestimmten Prozessor ausgeführt wird; das Betriebssystem trifft diese Entscheidung.  
  
### <a name="number-of-processes"></a>Anzahl der Prozesse  
 Der Compiler berechnet die Anzahl der Prozesse, die dazu verwendet werden, die Quelldateien zu kompilieren. Dieser Wert ist kleiner als die Anzahl der Quelldateien, die Sie in der Befehlszeile angeben und die Anzahl der Prozesse, die Sie explizit oder implizit mit der Option **/MP** angeben. Sie können die maximale Anzahl von Prozessen explizit festlegen, wenn Sie das `processMax` -Argument der Option **/MP** angeben. Oder Sie können die Standardeinstellung verwenden, die gleich der Anzahl der effektiven Prozessoren in einem Computer ist, wenn Sie das `processMax` -Argument weglassen.  
  
 Beispielsweise können Sie die folgende Befehlszeile angeben:  
  
 `cl /MP7 a.cpp b.cpp c.cpp d.cpp e.cpp`  
  
 In diesem Fall verwendet der Compiler fünf Prozesse, da dies weniger als fünf Quelldateien und maximal sieben Prozesse sind. Beispiel: Ihr Computer hat zwei effektive Prozessoren und Sie geben die folgende Befehlszeile an:  
  
 `cl /MP a.cpp b.cpp c.cpp`  
  
 In diesem Fall meldet das Betriebssystem zwei Prozessoren. Daher verwendet der Compiler zwei Prozesse in seiner Berechnung. Daher wird der Compiler den Build mit zwei Prozessen ausführen, da dies der kleinere Wert von zwei Prozessen und drei Quelldateien ist.  
  
### <a name="source-files-and-build-order"></a>Quelldateien und Buildreihenfolge  
 Die Quelldateien werden möglicherweise nicht in der gleichen Reihenfolge kompiliert, in denen sie in der Befehlszeile angezeigt werden. Obwohl der Compiler eine Reihe von Prozessen erstellt, die Kopien des Compilers enthalten, plant das Betriebssystem, wann jeder Prozess ausgeführt wird. Daher können Sie nicht garantieren, dass die Quelldateien in einer bestimmten Reihenfolge kompiliert werden.  
  
 Eine Quelldatei wird kompiliert, wenn ein Prozess für ihre Kompilierung verfügbar ist. Wenn mehr Dateien als Prozesse vorhanden sind, wird der erste Satz von Dateien von den verfügbaren Prozessen kompiliert. Die restlichen Dateien werden verarbeitet, wenn ein Prozess die Behandlung einer vorherigen Datei beendet und für die Verarbeitung einer der verbleibenden Dateien bereitsteht.  
  
 Geben Sie die gleiche Quelldatei nicht mehrmals in einer Befehlszeile an. Dies kann zum Beispiel passieren, wenn ein Tool automatisch eine [Makefile](../../build/contents-of-a-makefile.md) erstellt, die auf Abhängigkeitsinformationen in einem Projekt basiert. Wenn Sie die Option **/MP** nicht angeben, verarbeitet der Compiler die Liste der Dateien sequenziell und kompiliert jedes Vorkommen der Datei neu. Wenn Sie jedoch die Option **/MP** angeben, wird die gleiche Datei möglicherweise von verschiedenen Compilern zur gleichen Zeit kompiliert. Aus diesem Grund versuchen die verschiedenen Compiler zur gleichen Zeit in die gleiche Ausgabedatei zu schreiben. Ein Compiler wird exklusiven Schreibzugriff auf die Ausgabedatei erhalten und die anderen Compiler werden einen Dateizugriffsfehler melden.  
  
### <a name="using-type-libraries-import"></a>Verwenden von Typbibliotheken (#import)  
 Der Compiler unterstützt nicht die Verwendung der [#import](../../preprocessor/hash-import-directive-cpp.md) -Direktive zusammen mit dem **/MP** -Schalter. Führen Sie wenn möglich die folgenden Schritte aus, um dieses Problem zu umgehen:  
  
-   Verschieben Sie alle `#import` -Direktiven in den verschiedenen Quelldateien in eine oder mehrere Dateien, und kompilieren Sie dann diese Dateien ohne die Option **/MP** . Das Ergebnis ist ein Satz generierter Headerdateien.  
  
-   In den restlichen Quelldateien fügen Sie die [#include](../../preprocessor/hash-include-directive-c-cpp.md) -Direktiven ein, die die generierten Header angeben, und kompilieren Sie dann die restlichen Quelldateien mit der Option **/MP** .  
  
### <a name="visual-studio-project-settings"></a>Visual Studio Projekteinstellungen  
  
#### <a name="the-msbuildexe-tool"></a>Das Tool „MSBUILD.exe“  
 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] verwendet das [MSBuild.exe](/visualstudio/msbuild/msbuild-reference) Tool, um Projektmappen und Projekte zu erstellen. Die **/maxcpucount:**`number` (oder **/m:**`number`) Befehlszeilenoption des MSBuild.exe-Tools kann mehrere Projekte gleichzeitig erstellen. Die Compileroption **/MP** kann mehrere Kompilierungseinheiten gleichzeitig erstellen. Wenn es für die Anwendung geeignet ist, verbessern Sie die Buildzeit Ihrer Projektmappe, indem Sie **/MP** oder/und **/maxcpucount**verwenden.  
  
 Die Buildzeit der Projektmappe hängt teilweise von der Anzahl der Prozesse ab, die den Build ausführen. Das `number` Argument der MSBuild-Option [/maxcpucount](/visualstudio/msbuild/msbuild-command-line-reference) gibt die maximale Anzahl von Projekten an, die zur gleichen Zeit erstellt werden. Das `processMax` Argument der Compileroption **/MP** gibt die maximale Anzahl von Kompilierungseinheiten an, die zur gleichen Zeit erstellt werden. Wenn die Option **/maxcpucount** *P* Projekte angibt und die Option **/MP** *C* Prozesse angibt, werden bis zu *P*x*C* Prozesse gleichzeitig ausgeführt.  
  
 Die Richtlinie für die Entscheidung, ob `MSBuild` oder **/MP** -Technologie verwendet werden sollte, lautet wie folgt:  
  
-   Wenn viele Projekte mit wenigen Dateien in jedem Projekt vorhanden sind, verwenden Sie das `MSBuild` -Tool.  
  
-   Wenn wenige Projekte mit vielen Dateien in jedem Projekt vorhanden sind, verwenden Sie die Option **/MP** .  
  
-   Wenn die Anzahl von Projekten und Dateien pro Projekt ausgeglichen ist, verwenden Sie beide, `MSBuild` und **/MP**. Legen Sie anfangs die Option **/maxcpucount** auf die Anzahl der zu erstellenden Projekte und die Option **/MP** auf die Anzahl der Prozessoren im Computer fest. Messen Sie die Leistung und passen Sie dann die Einstellungen so an, dass sie zu optimalen Ergebnissen führen. Wiederholen Sie diesen Zyklus, bis Sie mit der Gesamt-Buildzeit zufrieden sind.  
  
#### <a name="the-gm-compiler-option"></a>Die Compileroption /Gm  
 Standardmäßig aktiviert ein Projektbuild die Compileroption **/Gm** (inkrementelle Builds) für Debugbuilds und deaktiviert sie für Releasebuilds. Aus diesem Grund ist die Compileroption **/MP** bei Debugbuilds automatisch deaktiviert, da ein Konflikt mit der standardmäßigen Compileroption **/Gm** besteht.  
  
## <a name="see-also"></a>Siehe auch  
 [#import-Direktive](../../preprocessor/hash-import-directive-cpp.md)   
 [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) (MSBuild-Befehlszeilenreferenz)