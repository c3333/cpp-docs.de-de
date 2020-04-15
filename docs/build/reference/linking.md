---
title: MSVC-Linkerreferenz
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 2503e212e7325fc97f9057861cb85d5cf0571094
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336499"
---
# <a name="linking"></a>Verknüpfen

In einem C++-Projekt wird der *Verknüpfungsschritt* ausgeführt, nachdem der Compiler den Quellcode in Objektdateien (*.obj) kompiliert hat. Der Linker (link.exe) kombiniert die Objektdateien in einer einzigen ausführbaren Datei.

Linkeroptionen können innerhalb oder außerhalb von Visual Studio festgelegt werden. In Visual Studio greifen Sie auf Linkeroptionen zu, indem Sie mit der rechten Maustaste auf einen Projektknoten im **Projektmappen-Explorer** klicken und **Eigenschaften** auswählen, um die Eigenschaftenseiten anzuzeigen. Wählen Sie **Linker** im linken Bereich, um den Knoten zu erweitern und alle Optionen anzuzeigen.

## <a name="linker-command-line-syntax"></a>Linker-Befehlszeilensyntax

Wenn Sie LINK außerhalb von Visual Studio ausführen, können Sie Eingaben auf eine oder mehrere Arten angeben:

- Über die Befehlszeile

- Verwenden von Befehlsdateien

- In Umgebungsvariablen

LINK verarbeitet zunächst die in der LINK-Umgebungsvariablen angegebenen Optionen, gefolgt von Optionen in der Reihenfolge, in der sie in der Befehlszeile und in Befehlsdateien angegeben sind. Wenn eine Option mit unterschiedlichen Argumenten wiederholt wird, hat die zuletzt verarbeitete Option Vorrang.

Optionen gelten für den gesamten Build. Auf bestimmte Eingabedateien können keine Optionen angewendet werden.

So führen Sie LINK aus. EXE, verwenden Sie die folgende Befehlssyntax:

```
LINK arguments
```

Die `arguments` Include-Optionen und Dateinamen können in beliebiger Reihenfolge angegeben werden. Optionen werden zuerst verarbeitet, dann Dateien. Verwenden Sie einen oder mehrere Leerzeichen oder Registerkarten, um Argumente zu trennen.

> [!NOTE]
> Sie können dieses Tool nur über die Eingabeaufforderung für die Eingabeaufforderung Visual Studio starten. Sie können es nicht von einer Systemeingabeaufforderung oder vom Datei-Explorer aus starten.

## <a name="command-line"></a>Befehlszeile

In der Befehlszeile besteht eine Option aus einem Optionsbezeichner, entweder einem Bindestrich (-) oder einem Schrägstrich (/), gefolgt vom Namen der Option. Optionsnamen können nicht abgekürzt werden. Einige Optionen verwenden ein Argument, das nach einem Doppelpunkt (:) angegeben wird. Innerhalb einer Optionsspezifikation sind keine Leerzeichen oder Registerkarten zulässig, außer innerhalb einer Zeichenfolge in der Option /COMMENT. Geben Sie numerische Argumente in Dezimal- oder C-Sprache-Notation an. Optionsnamen und deren Schlüsselwort- oder Dateinamenargumente werden nicht von Groß-/Kleinschreibung beachtet, aber Bezeichner als Argumente werden von Groß-/Kleinschreibung beachtet.

Um eine Datei an den Linker zu übergeben, geben Sie den Dateinamen in der Befehlszeile nach dem Befehl LINK an. Sie können einen absoluten oder relativen Pfad mit dem Dateinamen angeben und Platzhalter im Dateinamen verwenden. Wenn Sie die Erweiterung dot (.) und filename weglassen, geht LINK von .obj aus, um die Datei zu finden. LINK verwendet keine Dateinamenerweiterungen oder deren Fehlen, um Annahmen über den Inhalt von Dateien zu treffen; Sie bestimmt den Dateityp, indem sie sie untersucht, und verarbeitet sie entsprechend.

link.exe gibt Null für Erfolg zurück (keine Fehler).  Andernfalls gibt der Linker die Fehlernummer zurück, mit der die Verknüpfung beendet wurde.  Wenn der Linker beispielsweise LNK1104 generiert, gibt der Linker 1104 zurück.  Dementsprechend ist die niedrigste Fehlernummer, die bei einem Fehler vom Linker zurückgegeben wird, 1000.  Der Rückgabewert 128 stellt ein Konfigurationsproblem mit dem Betriebssystem oder einer .config-Datei dar. Der Lader hat weder link.exe noch c2.dll geladen.

## <a name="link-command-files"></a>LINK-Befehlsdateien

Sie können Befehlszeilenargumente in Form einer Befehlsdatei an LINK übergeben. Um eine Befehlsdatei für den Linker anzugeben, verwenden Sie die folgende Syntax:

> ** \@ ** <em>LINK-Befehlsdatei</em>

Die *Befehlsdatei* ist der Name einer Textdatei. Zwischen dem at-Zeichen (**\@**) und dem Dateinamen ist kein Leerzeichen oder eine Registerkarte zulässig. Es gibt keine Standarderweiterung. Sie müssen den vollständigen Dateinamen angeben, einschließlich einer beliebigen Erweiterung. Platzhalter können nicht verwendet werden. Sie können einen absoluten oder relativen Pfad mit dem Dateinamen angeben. LINK verwendet keine Umgebungsvariable, um nach der Datei zu suchen.

In der Befehlsdatei können Argumente durch Leerzeichen oder Tabstopps (wie in der Befehlszeile) und durch Zeilenzeilenzeichen getrennt werden.

Sie können die Befehlszeile ganz oder teilweise in einer Befehlsdatei angeben. Sie können mehr als eine Befehlsdatei in einem LINK-Befehl verwenden. LINK akzeptiert die Eingabe der Befehlsdatei so, als ob sie an dieser Stelle in der Befehlszeile angegeben wäre. Befehlsdateien können nicht geschachtelt werden. LINK gibt den Inhalt von Befehlsdateien wieder, es sei denn, die Option [/NOLOGO](nologo-suppress-startup-banner-linker.md) ist angegeben.

## <a name="example"></a>Beispiel

Der folgende Befehl zum Erstellen einer DLL übergibt die Namen von Objektdateien und Bibliotheken in separaten Befehlsdateien und verwendet eine dritte Befehlsdatei zur Spezifikation der Option /EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>LINK-Umgebungsvariablen

Das LINK-Tool verwendet die folgenden Umgebungsvariablen:

- LINK \_und\_LINK , falls definiert. Das LINK-Tool stellt die in der LINK-Umgebungsvariablen definierten Optionen und \_\_ Argumente voran und fügt die in der LINK-Umgebungsvariablen definierten Optionen und Argumente vor der Verarbeitung an die Befehlszeilenargumente an.

- LIB, falls definiert. Die LINK-Tools verwenden den LIB-Pfad bei der Suche nach einem Objekt, einer Bibliothek oder einer anderen Datei, die in der Befehlszeile oder durch die Option [/BASE](base-base-address.md) angegeben ist. Der LIB-Pfad wird auch verwendet, um nach einer in einem Objekt genannten PDB-Datei zu suchen. Die LIB-Variable kann mehrere durch Semikolons getrennte Pfadangaben enthalten. Ein Pfad muss auf das Unterverzeichnis \lib der Visual C++-Installation zeigen.

- PATH, wenn das Tool CVTRES ausführen muss und die Datei nicht im selben Verzeichnis wie LINK findet. (LINK erfordert CVTRES, um eine .res-Datei zu verknüpfen.) PATH muss auf das Unterverzeichnis von 'bin' ihrer Visual C++-Installation verweisen.

- TMP zum Angeben eines Verzeichnisses beim Verknüpfen von OMF oder RES-Dateien

## <a name="see-also"></a>Siehe auch

[C/C++ Gebäudereferenz](c-cpp-building-reference.md)
[MSVC Linker Optionen](linker-options.md)
[Modul-Definition (.def) Files](module-definition-dot-def-files.md)
[Linker-Unterstützung für verzögert geladene DLLs](linker-support-for-delay-loaded-dlls.md)
