---
title: Schwerwiegender Fehler C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: 57ae8f2d0b7f02732032151f86617498e5201c61
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509754"
---
# <a name="fatal-error-c1083"></a>Schwerwiegender Fehler C1083

> Die *filetype* -Datei kann nicht geöffnet werden: "*File*": *Message*

Der Compiler generiert einen C1083-Fehler, wenn er eine erforderliche Datei nicht finden kann. Es gibt zahlreiche mögliche Ursachen für diesen Fehler. Ein falscher includesuchpfad oder fehlende oder falsch benannte Header Dateien sind die häufigsten Ursachen, aber andere Dateitypen und Probleme können auch C1083 verursachen. Im folgenden sind einige der häufigsten Gründe aufgeführt, warum der Compiler diesen Fehler generiert.

## <a name="the-specified-file-name-is-wrong"></a>Der angegebene Dateiname ist falsch

Der Name einer Datei wurde möglicherweise falsch geschrieben werden. Beispiel:

`#include <algorithm.h>`

Die von Ihnen gewünschte Datei wird möglicherweise nicht gefunden. Die meisten Header Dateien der C++-Standard Bibliothek verfügen nicht über die Dateinamenerweiterung ". h". Der- \<algorithm> Header wurde von dieser `#include` Direktive nicht gefunden. Um dieses Problem zu beheben, überprüfen Sie, ob der richtige Dateiname eingegeben wurde, wie in diesem Beispiel:

`#include <algorithm>`

Bestimmte Header der C-Laufzeitbibliothek befinden sich in einem Unterverzeichnis des Standardincludeverzeichnisses. Wenn Sie z. b. einschließen möchten *`sys/types.h`* , müssen Sie den *`sys`* Namen des Unterverzeichnisses in die- `#include` Direktive einschließen:

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>Die Datei ist nicht im Include-Suchpfad enthalten.

Der Compiler kann die Datei anhand der Suchregeln, die in einer `#include`- oder `#import`-Anweisung angegeben wurden, nicht finden. Wenn z. b. ein Header Dateiname in Anführungszeichen eingeschlossen wird,

`#include "myincludefile.h"`

Dadurch wird der Compiler aufgefordert, nach der Datei in demselben Verzeichnis zu suchen, das zuerst die Quelldatei enthält, und dann an anderen Orten zu suchen, die in der Buildumgebung angegeben sind. Wenn die Anführungszeichen einen absoluten Pfad enthalten, sucht der Compiler nur nach der Datei an diesem Speicherort. Wenn die Anführungszeichen einen relativen Pfad enthalten, sucht der Compiler nach der Datei im Verzeichnis relativ zum Quellverzeichnis.

Wenn der Name in spitzen Klammern eingeschlossen ist,

`#include <stdio.h>`

der Compiler folgt einem Suchpfad, der durch die Buildumgebung, die **`/I`** -Compileroption, die **`/X`** -Compileroption und die **include** -Umgebungsvariable definiert wird. Weitere Informationen, einschließlich spezifischer Details zur Such Reihenfolge, die zum Suchen einer Datei verwendet wird, finden Sie unter [#include-Direktive (C/C++)](../../preprocessor/hash-include-directive-c-cpp.md) und [#Import Direktive](../../preprocessor/hash-import-directive-cpp.md).

Wenn sich die Includedateien in einem anderen Verzeichnis relativ zum Quellverzeichnis befinden und Sie einen relativen Pfad in den Include-Direktiven verwenden, müssen Sie anstelle von spitzen Klammern doppelte Anführungszeichen verwenden. Wenn sich Ihre Header Datei z. b. *`myheader.h`* in einem Unterverzeichnis der Projekt Quellen mit dem Namen Headers befindet, kann in diesem Beispiel die Datei nicht gefunden werden, und es wird C1083 verursacht:

`#include <headers\myheader.h>`

Dieses Beispiel funktioniert jedoch:

`#include "headers\myheader.h"`

Relative Pfade können auch mit Verzeichnissen im Include-Suchpfad verwendet werden. Wenn Sie der **include** -Umgebungsvariablen oder dem Pfad der **Includeverzeichnisse** in Visual Studio ein Verzeichnis hinzufügen, fügen Sie auch keinen Teil des Pfads zu den Include-Direktiven hinzu. Wenn sich der Header beispielsweise unter befindet *`\path\example\headers\myheader.h`* und Sie den *`\path\example\headers\`* Pfad zum Einschließen von **Verzeichnissen** in Visual Studio hinzufügen, verweist Ihre `#include` Direktive auf die Datei als

`#include <headers\myheader.h>`

die Datei wurde nicht gefunden. Verwenden Sie den korrekten Pfad relativ zu dem Verzeichnis, das im Include-Suchpfad angegeben ist. In diesem Beispiel können Sie den Include-Suchpfad in ändern *`\path\example\`* oder das *`headers\`* Pfad Segment aus der- `#include` Direktive entfernen.

## <a name="third-party-library-issues-and-vcpkg"></a>Drittanbieter-Bibliotheks Probleme und vcpkg

Wenn diese Fehlermeldung angezeigt wird, wenn Sie versuchen, eine Bibliothek eines Drittanbieters als Teil Ihres Builds zu konfigurieren, sollten Sie [`vcpkg`](../../build/vcpkg.md) die Verwendung von, einem C++-Paket-Manager, zum Installieren und Erstellen der Bibliothek in Erwägung gezogen. vcpkg unterstützt eine große und wachsende [Liste von Bibliotheken von Drittanbietern](https://github.com/Microsoft/vcpkg/tree/master/ports)und legt alle Konfigurations Eigenschaften und Abhängigkeiten, die für erfolgreiche Builds erforderlich sind, als Teil des Projekts fest.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>Die Datei befindet sich in Ihrem Projekt, aber nicht im Include-Suchpfad.

Auch wenn Header Dateien in **Projektmappen-Explorer** als Teil eines Projekts aufgeführt sind, werden die Dateien nur vom Compiler gefunden, wenn Sie von einer- `#include` oder `#import` -Direktive in einer Quelldatei referenziert werden und sich in einem include-Suchpfad befinden. Für unterschiedliche Buildtypen können unterschiedliche Suchpfade verwendet werden. Die- **`/X`** Compileroption kann verwendet werden, um Verzeichnisse aus dem Include-Suchpfad auszuschließen. Dadurch können für verschiedene Builds unterschiedliche Includedateien verwendet werden, die denselben Namen besitzen, sich aber in unterschiedlichen Verzeichnissen befinden. Dies ist eine Alternative zur bedingten Kompilierung mithilfe von Präprozessorbefehlen. Weitere Informationen zur- **`/X`** Compileroption finden Sie unter [ `/X` (Standard mäßige Includepfade ignorieren)](../../build/reference/x-ignore-standard-include-paths.md).

Korrigieren Sie zur Behebung dieses Problems den Pfad, den der Compiler für die Suche nach der eingeschlossenen oder importierten Datei verwendet. Ein neues Projekt verwendet standardmäßige include-Suchpfade. Möglicherweise müssen Sie den Include-Suchpfad ändern, um ein Verzeichnis für das Projekt hinzuzufügen. Wenn Sie in der Befehlszeile kompilieren, fügen Sie den Pfad der **include** -Umgebungsvariablen oder der- **`/I`** Compileroption hinzu, um den Pfad zur Datei anzugeben.

Öffnen Sie das Dialogfeld **Eigenschaften Seiten** des Projekts, um den Verzeichnispfad einschließen in Visual Studio festzulegen. Wählen Sie im linken Bereich unter **Konfigurations Eigenschaften** die Option **VC + +-Verzeichnisse** aus, und bearbeiten Sie dann die Eigenschaft **Verzeichnisse einschließen** . Weitere Informationen zu den Verzeichnissen pro Benutzer und pro Projekt, die der Compiler in Visual Studio durchsucht, finden Sie unter [VC + +-Verzeichnisse (Eigenschaften Seite](../../build/reference/vcpp-directories-property-page.md)). Weitere Informationen zur- **`/I`** Compileroption finden Sie unter [ `/I` (Zusätzliche Includeverzeichnisse)](../../build/reference/i-additional-include-directories.md).

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>Die Befehlszeilen-oder lib-Umgebung ist nicht festgelegt.

Beim Aufrufen des Compilers über die Befehlszeile werden Suchpfade oft mithilfe von Umgebungsvariablen angegeben. Wenn der von der **include** -oder **lib** -Umgebungsvariablen beschriebene Suchpfad nicht ordnungsgemäß festgelegt ist, kann ein C1083-Fehler generiert werden. Wir empfehlen dringend die Verwendung einer Eingabe Aufforderungs Verknüpfung für Entwickler, um die grundlegende Umgebung für Befehlszeilenbuilds festzulegen. Weitere Informationen finden Sie unter [Build C/C++ in der Befehlszeile](../../build/building-on-the-command-line.md). Weitere Informationen zur Verwendung von Umgebungsvariablen finden Sie unter Gewusst [wie: Verwenden von Umgebungsvariablen in einem Build](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).

## <a name="the-file-may-be-locked-or-in-use"></a>Die Datei ist möglicherweise gesperrt oder wird verwendet.

Wenn Sie ein anderes Programm verwenden, um die Datei zu bearbeiten oder auf diese zuzugreifen, ist die Datei möglicherweise gesperrt. Versuchen Sie, die Datei im anderen Programm zu schließen. Manchmal kann das andere Programm auch Visual Studio selbst sein, wenn Sie Optionen für die parallele Kompilierung verwenden. Wenn der Fehler durch Deaktivieren der Option paralleler Build entfernt wird, ist dies das Problem. Auch andere parallele Buildsysteme können dieses Problem haben. Achten Sie darauf, Datei-und Projekt Abhängigkeiten festzulegen, damit die Buildreihenfolge korrekt ist In einigen Fällen sollten Sie die Erstellung eines zwischen Projekts in Erwägung nehmen, um die buildabhängigkeits-Reihenfolge für eine gemeinsame Datei zu erzwingen, die von mehreren Projekten Manchmal Sperren Antivirenprogramme zuletzt geänderte Dateien für die Überprüfung vorübergehend. Wenn möglich, sollten Sie die projektbuildverzeichnisse aus dem Antivirenscanner ausschließen.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>Die falsche Version eines Dateinamens wird verwendet

Ein Fehler C1083 kann auch darauf hinweisen, dass die falsche Version einer Datei verwendet wird. Ein Build kann z. B. die falsche Version einer Datei enthalten, die eine nicht für diesen Build vorgesehene `#include`-Anweisung für eine Headerdatei aufweist. Bestimmte Dateien können z. b. nur für x86-Builds oder zum Debuggen von Builds gelten. Wenn die Headerdatei nicht gefunden wird, generiert der Compiler einen Fehler C1083. Dieses Problem kann behoben werden, indem die richtige Datei verwendet wird. Durch Hinzufügen der Headerdatei oder des Verzeichnisses zum Build lässt sich das Problem nicht beheben.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Die vorkompilierten Header sind noch nicht vorkompiliert

Wenn ein Projekt für die Verwendung von vorkompilierten Headern konfiguriert ist, müssen die relevanten *`.pch`* Dateien erstellt werden, damit Dateien, die den Header Inhalt verwenden, kompiliert werden können. Beispielsweise wird die *`pch.cpp`* Datei ( *`stdafx.cpp`* in Visual Studio 2017 und früher) automatisch im Projektverzeichnis für neue Projekte erstellt. Kompilieren Sie diese Datei zuerst, um die vorkompilierten Headerdateien zu erstellen. Im typischen buildprozessentwurf erfolgt dies automatisch. Weitere Informationen finden Sie unter [Erstellen vorkompilierter Header Dateien](../../build/creating-precompiled-header-files.md).

## <a name="additional-causes"></a>Weitere Ursachen

- Sie haben ein SDK oder eine Bibliothek von Drittanbietern installiert, aber nach der Installation des SDKs oder der Bibliothek haben Sie noch kein neues Entwickler-Eingabe Aufforderungs Fenster geöffnet. Wenn das SDK **oder die Bibliothek** dem Includepfad Dateien hinzufügt, müssen Sie möglicherweise ein neues Entwickler-Eingabe Aufforderungs Fenster öffnen, um diese Umgebungsvariablen Änderungen zu übernehmen.

- Die Datei verwendet verwalteten Code, aber die-Compileroption **`/clr`** ist nicht angegeben. Weitere Informationen finden Sie unter [ `/clr` (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md).

- Die Datei wird mit einer anderen **`/analyze`** compileroptionseinstellung kompiliert, als für die Vorkompilierung der Header verwendet wird. Wenn die Header für ein Projekt vorkompiliert werden, sollten alle dieselben Einstellungen verwenden **`/analyze`** . Weitere Informationen finden Sie unter [ `/analyze` (Code Analyse)](../../build/reference/analyze-code-analysis.md).

- Die Datei oder das Verzeichnis wurde vom Windows-Subsystem für Linux erstellt, die Unterscheidung nach Groß-/Kleinschreibung ist aktiviert, und der angegebene Fall eines Pfads oder einer Datei stimmt nicht mit der Groß-/Kleinschreibung des Pfads oder der Datei auf dem Datenträger.

- Die Datei, das Verzeichnis oder der Datenträger ist schreibgeschützt.

- Visual Studio oder die Befehlszeilen Tools verfügen nicht über ausreichende Berechtigungen zum Lesen der Datei oder des Verzeichnisses. Dies kann beispielsweise der Fall sein, wenn die Projektdateien einen anderen Besitz aufweisen als der Prozess, in dem Visual Studio oder die Befehlszeilen Tools ausgeführt werden. Manchmal kann dieses Problem behoben werden, indem Visual Studio oder die Developer-Eingabeaufforderung als Administrator ausgeführt wird.

- Es sind nicht genügend Dateihandles vorhanden. Schließen Sie einige Anwendungen, und kompilieren Sie dann erneut. Diese Bedingung ist unter normalen Umständen ungewöhnlich. Sie kann jedoch auftreten, wenn große Projekte auf einem Computer erstellt werden, dessen physischer Speicher beschränkt ist.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein C1083-Fehler generiert, wenn die Header Datei `"test.h"` nicht im Quellverzeichnis oder im Include-Suchpfad vorhanden ist.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

Weitere Informationen zum Erstellen von C/C++-Projekten in der IDE oder über die Befehlszeile sowie Informationen zum Festlegen von Umgebungsvariablen finden Sie unter [Projekte und Buildsysteme](../../build/projects-and-build-systems-cpp.md).

## <a name="see-also"></a>Weitere Informationen

- [MSBuild-Eigenschaften](/visualstudio/msbuild/msbuild-properties)
