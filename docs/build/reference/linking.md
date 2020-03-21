---
title: MSVC-Linkerreferenz
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: d46874b5eaff889834df284ba90e6c6f196d8d66
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079514"
---
# <a name="linking"></a>Verknüpfen

In einem C++ Projekt wird der *Verknüpfungs* Schritt ausgeführt, nachdem der Compiler den Quellcode in Objektdateien (*. obj) kompiliert hat. Der Linker (Link. exe) kombiniert die Objektdateien in einer einzelnen ausführbaren Datei.

Linkeroptionen können innerhalb von Visual Studio oder außerhalb von Visual Studio festgelegt werden. In Visual Studio greifen Sie auf die **Linkeroptionen** zu, indem Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf einen Projekt Knoten klicken und Eigenschaften auswählen, um die Eigenschaften Seiten anzuzeigen. Wählen Sie im linken Bereich **Linker** aus, um den Knoten zu erweitern und alle Optionen anzuzeigen.

## <a name="linker-command-line-syntax"></a>Linker-Befehlszeilen Syntax

Wenn Sie einen Link außerhalb von Visual Studio ausführen, können Sie die Eingabe auf eine oder mehrere Arten angeben:

- Über die Befehlszeile

- Verwenden von Befehls Dateien

- In Umgebungsvariablen

Verknüpfen Sie zuerst die in der Link-Umgebungsvariablen angegebenen Optionen, gefolgt von den Optionen in der Reihenfolge, in der Sie in der Befehlszeile und in den Befehls Dateien angegeben sind. Wenn eine Option mit unterschiedlichen Argumenten wiederholt wird, hat die letzte verarbeitete Priorität Vorrang.

Optionen gelten für den gesamten Build. Es können keine Optionen auf bestimmte Eingabedateien angewendet werden.

Zum Ausführen des Links. EXE verwenden Sie die folgende Befehlssyntax:

```
LINK arguments
```

Die `arguments` enthalten Optionen und Dateinamen und können in beliebiger Reihenfolge angegeben werden. Die Optionen werden zuerst verarbeitet, dann Dateien. Verwenden Sie ein oder mehrere Leerzeichen oder Registerkarten, um Argumente zu trennen.

> [!NOTE]
>  Sie können dieses Tool nur über die Visual Studio-Eingabeaufforderung starten. Sie können es nicht von einer Systemeingabeaufforderung oder vom Datei-Explorer aus starten.

## <a name="command-line"></a>Befehlszeile

In der Befehlszeile besteht eine Option aus einem optionsspezifizierer, entweder einem Bindestrich (-) oder einem Schrägstrich (/), gefolgt vom Namen der Option. Optionsnamen können nicht abgekürzt werden. Einige Optionen akzeptieren ein Argument, das nach einem Doppelpunkt (:) angegeben wird. In einer Options Spezifikation sind keine Leerzeichen oder Tabstopps zulässig, außer in einer Zeichenfolge in Anführungszeichen in der/Comment-Option. Geben Sie numerische Argumente in Dezimal-oder C-Sprachen-Notation an. Bei Optionsnamen und deren Schlüsselwort-oder Dateinamen Argumenten wird die Groß-/Kleinschreibung nicht beachtet

Wenn Sie eine Datei an den Linker übergeben möchten, geben Sie den Dateinamen in der Befehlszeile nach dem Link Befehl an. Sie können einen absoluten oder relativen Pfad mit dem Dateinamen angeben, und Sie können Platzhalter im Dateinamen verwenden. Wenn Sie die Punkt-(.) und Dateinamenerweiterung weglassen, wird von Link angenommen. obj für den Zweck der Suche nach der Datei. Der Link verwendet keine Dateinamen Erweiterungen oder nicht, um Annahmen über den Inhalt von Dateien zu treffen. der Typ der Datei wird durch die Untersuchung bestimmt und entsprechend verarbeitet.

"Link. exe" gibt 0 (null) für Erfolg zurück (keine Fehler).  Andernfalls gibt der Linker die Fehlernummer zurück, die den Link beendet hat.  Wenn der Linker z. b. LNK1104 generiert, gibt der Linker 1104 zurück.  Entsprechend ist die niedrigste Fehlernummer, die bei einem Fehler vom Linker zurückgegeben wird, 1000.  Der Rückgabewert 128 stellt ein Konfigurationsproblem mit dem Betriebssystem oder einer config-Datei dar. das Lade Modul hat entweder "Link. exe" oder "C2. dll" nicht geladen.

## <a name="link-command-files"></a>LINK-Befehlsdateien

Sie können Befehlszeilenargumente übergeben, um Sie in Form einer Befehlsdatei zu verknüpfen. Verwenden Sie die folgende Syntax, um eine Befehlsdatei für den Linker anzugeben:

> **Verknüpfung \@** <em>Befehlsdatei</em>

Die *Befehlsdatei* ist der Name einer Textdatei. Zwischen dem @-Zeichen ( **\@** ) und dem Dateinamen ist weder ein Leerzeichen noch eine Registerkarte zulässig. Es ist keine Standard Erweiterung vorhanden. Sie müssen den vollständigen Dateinamen angeben, einschließlich einer beliebigen Erweiterung. Platzhalter können nicht verwendet werden. Sie können einen absoluten oder relativen Pfad mit dem Dateinamen angeben. Der Link verwendet keine Umgebungsvariable, um nach der Datei zu suchen.

In der Befehlsdatei können Argumente durch Leerzeichen oder Tabstopps (wie in der Befehlszeile) und durch Zeilen vorzeilenzeichen getrennt werden.

Sie können die Befehlszeile ganz oder teilweise in einer Befehlsdatei angeben. Sie können mehr als eine Befehlsdatei in einem Link Befehl verwenden. Link akzeptiert die Befehlsdatei Eingabe so, als ob Sie an dieser Stelle in der Befehlszeile angegeben wurde. Befehls Dateien können nicht eingefügt werden. Link gibt den Inhalt von Befehls Dateien an, es sei denn, die [/nologo](nologo-suppress-startup-banner-linker.md) -Option wurde angegeben.

## <a name="example"></a>Beispiel

Der folgende Befehl zum Erstellen einer DLL übergibt die Namen von Objektdateien und Bibliotheken in separaten Befehls Dateien und verwendet eine dritte Befehlsdatei zur Angabe der/Exports-Option:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>LINK-Umgebungsvariablen

Das LINK-Tool verwendet die folgenden Umgebungsvariablen:

- Link und \_Link\_, sofern definiert. Das Link Tool fügt die in der Link-Umgebungsvariablen definierten Optionen und Argumente voran und fügt die im \_Link\_ Umgebungsvariablen definierten Optionen und Argumente vor der Verarbeitung an die Befehlszeilenargumente an.

- LIB, falls definiert. Die Linktools verwenden den LIB-Pfad bei der Suche nach einem Objekt, einer Bibliothek oder einer anderen Datei, die in der Befehlszeile oder der [/Base](base-base-address.md) -Option angegeben ist. Der LIB-Pfad wird auch verwendet, um nach einer in einem Objekt genannten PDB-Datei zu suchen. Die LIB-Variable kann mehrere durch Semikolons getrennte Pfadangaben enthalten. Ein Pfad muss auf das Unterverzeichnis \lib der Visual C++-Installation zeigen.

- PATH, wenn das Tool CVTRES ausführen muss und die Datei nicht im selben Verzeichnis wie LINK findet. (Link erfordert CVTRES, um eine RES-Datei zu verknüpfen.) Der Pfad muss auf das Unterverzeichnis "\bin" der C++ visuellen Installation zeigen.

- TMP zum Angeben eines Verzeichnisses beim Verknüpfen von OMF oder RES-Dateien

## <a name="see-also"></a>Weitere Informationen

[C/C++ buildverweis](c-cpp-building-reference.md)
[MSVC-Linkeroptionen](linker-options.md)
[Modul Definitions Dateien (. def)](module-definition-dot-def-files.md)
[Linker-Unterstützung für verzögertes Laden von DLLs](linker-support-for-delay-loaded-dlls.md)
