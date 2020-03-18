---
title: Ausführen von LIB
description: Beschreibt die Befehlszeilenoptionen, die Sie mit "lib. exe" verwenden können.
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
ms.openlocfilehash: 871b92809f38b4dcbf84de802b1ac9940ea6f1e9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438938"
---
# <a name="running-lib"></a>Ausführen von LIB

Zum Steuern von lib können verschiedene Befehlszeilenoptionen verwendet werden.

## <a name="lib-command-line"></a>LIB-Befehlszeile

Um lib auszuführen, geben Sie den Befehl `lib`ein, gefolgt von den Optionen und Dateinamen für die Aufgabe, für die Sie lib verwenden. LIB akzeptiert auch Befehlszeilen Eingaben in Befehls Dateien, die im folgenden Abschnitt beschrieben werden. LIB verwendet keine Umgebungsvariable.

## <a name="lib-command-files"></a>LIB-Befehls Dateien

Sie können Befehlszeilenargumente an lib in einer Befehlsdatei übergeben, indem Sie die folgende Syntax verwenden:

> **Lib-\@** <em>Befehlsdatei</em>

Die Datei *Befehlsdatei* ist eine Textdatei. Zwischen dem @-Zeichen ( **\@** ) und dem Dateinamen sind keine Leerzeichen oder Tabstopps zulässig. Der Name der *Befehlsdatei* hat keine Standard Erweiterung. Geben Sie den vollständigen Dateinamen einschließlich einer beliebigen Erweiterung an. Platzhalter können nicht verwendet werden. Sie können einen absoluten oder relativen Pfad mit dem Dateinamen angeben.

In der Befehlsdatei können Argumente durch Leerzeichen oder Tabstopps getrennt werden, wie Sie in der Befehlszeile angezeigt werden können. Argumente können auch durch Zeilen vorzeichenzeichen getrennt werden. Verwenden Sie ein Semikolon ( **;** ), um einen Kommentar zu markieren. LIB ignoriert den gesamten Text vom Semikolon bis zum Ende der Zeile.

Sie können entweder die gesamte Befehlszeile oder einen Teil der Befehlszeile in einer Befehlsdatei angeben, und Sie können mehr als eine Befehlsdatei in einem LIB-Befehl verwenden. LIB akzeptiert die Befehlsdatei Eingabe so, als ob Sie an dieser Stelle in der Befehlszeile angegeben wird. Befehls Dateien können nicht eingefügt werden. LIB gibt den Inhalt von Befehls Dateien an, es sei denn, die Option **/nologo** wird verwendet.

## <a name="using-lib-options"></a>Verwenden von lib-Optionen

Eine Option besteht aus einem optionsspezifizierer, bei dem es sich entweder um einen Bindestrich ( **-** ) oder einen Schrägstrich ( **/** ) handelt, gefolgt vom Namen der Option. Optionsnamen können nicht abgekürzt werden. Einige Optionen akzeptieren ein Argument, das nach einem Doppelpunkt ( **:** ) angegeben wird. Innerhalb einer Optionsangabe sind keine Leerzeichen oder Tabstopps zulässig. Verwenden Sie eines oder mehrere Leerzeichen bzw. Tabstopps, um Optionsangaben in der Befehlszeile voneinander zu trennen. Bei Optionsnamen und Schlüsselwörtern oder Dateinamen Argumenten wird die Groß-/Kleinschreibung nicht beachtet LIB verarbeitet Optionen in der Reihenfolge, die in der Befehlszeile und in den Befehls Dateien angegeben ist. Wenn eine Option mit unterschiedlichen Argumenten wiederholt wird, hat die letzte zu verarbeitende Priorität Vorrang.

Die folgenden Optionen gelten für alle Modi von lib:

> **/Errorreport** \[**keine** &#124; **prompt** &#124; - **Warteschlange** &#124; **senden**]

Die/errorreport-Option ist veraltet. Ab Windows Vista wird die Fehlerberichterstattung durch [Windows-Fehlerberichterstattung (wer)](/windows/win32/wer/windows-error-reporting) -Einstellungen gesteuert.

> **/LINKREPRO:** _Verzeichnispfad_ \
> **/LINKREPROTARGET:** _Dateiname_

Sie können die [/LINKREPRO](linkrepro.md) -Option verwenden, um Microsoft bei der Diagnose von lib. exe-abstürzen und internen Fehlern zu unterstützen. Mit dieser Option wird eine *Link*Reproduktion generiert, eine Gruppe von buildartefakte, mit denen Microsoft ein Problem reproduzieren kann, das während der Bibliotheks Vorgänge auftritt. Die [/LINKREPROTARGET](linkreprotarget.md) -Option kann mit der **/LINKREPRO** -Option verwendet werden. Es werden nur Verknüpfungs Reproduktions Artefakte generiert, wenn "lib. exe" die angegebene Datei erzeugt. Weitere Informationen finden Sie unter [melden eines Problems mit dem Microsoft C++ -Toolset](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

> **/LTCG**

"LTCG" steht für die *Link-Zeit Codegenerierung*. Diese Funktion erfordert die Zusammenarbeit zwischen dem Compiler ([cl. exe](compiler-options.md)), lib und dem Linker ([Link](linker-options.md)). In kombinieren können Sie Code optimieren, der über die Möglichkeiten der einzelnen Komponenten hinausgeht.

Die **/LTCG** -Option für lib gibt an, dass die Eingaben aus cl. exe Objektdateien enthalten, die mithilfe der [/GL](gl-whole-program-optimization.md) -Compileroption generiert wurden. Wenn lib solche Eingaben findet und **/LTCG** nicht angegeben ist, wird nach dem Anzeigen einer Informations Meldung neu gestartet, wenn/LTCG aktiviert ist. Anders ausgedrückt: Es ist nicht erforderlich, diese Option explizit festzulegen, aber es beschleunigt die Buildleistung. Das liegt daran, dass lib nicht selbst neu gestartet werden muss.

Im Buildprozess wird die Ausgabe von lib an Link gesendet. Link hat eine eigene separate **/LTCG** -Option. Sie wird verwendet, um verschiedene Optimierungen auszuführen, einschließlich der Optimierung des gesamten Programms und der PGO-Instrumentation (Profil gesteuerte Optimierung). Weitere Informationen zur Link-Option finden Sie unter [/LTCG](ltcg-link-time-code-generation.md).

> **/MACHINE**

Gibt die Zielplattform für das Programm an. Normalerweise müssen Sie **/Machine**nicht angeben. LIB leitet den Computertyp aus den OBJ-Dateien ab. In einigen Fällen kann lib den Computertyp jedoch nicht ermitteln und eine Fehlermeldung ausgegeben. Wenn ein solcher Fehler auftritt, geben Sie **/Machine**an. Im **/extract** -Modus dient diese Option nur zur Überprüfung. Verwenden Sie `lib /?` in der Befehlszeile, um die verfügbaren Computertypen anzuzeigen.

> **/NOLOGO**

Unterdrückt die Anzeige der lib-Copyright Meldung und der Versionsnummer und verhindert das Wiederholen von Befehls Dateien.

> **/VERBOSE**

Zeigt Details zum Fortschritt der Sitzung an, einschließlich der Namen der OBJ-Dateien, die hinzugefügt werden. Die Informationen werden an die Standardausgabe gesendet und können in eine Datei umgeleitet werden.

> **/WX**[ **: No**]

Behandeln Sie Warnungen als Fehler. Weitere Informationen finden Sie unter [/WX (Linkerwarnungen als Fehler behandeln)](wx-treat-linker-warnings-as-errors.md).

Andere Optionen gelten nur für bestimmte Modi von lib. Diese Optionen werden in den Abschnitten erläutert, in denen die einzelnen Modi beschrieben werden.

## <a name="see-also"></a>Weitere Informationen

[LIB-Referenz](lib-reference.md)
