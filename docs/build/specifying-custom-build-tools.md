---
title: Angeben von benutzerdefinierten Buildtools
ms.date: 06/05/2018
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.openlocfilehash: dbce226b34503a9e8e70b6f19d9aa0c68ef487f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314753"
---
# <a name="specify-custom-build-tools"></a>Angeben von benutzerdefinierten Buildtools

Ein *benutzerdefiniertes Buildtool* stellt dem Buildsystem die Informationen bereit, die erforderlich sind, um bestimmte Eingabedateien zu erstellen. Ein benutzerdefiniertes Buildtool gibt einen auszuführenden Befehl, eine Liste von Eingabedateien, eine Liste von Ausgabedateien, die vom Befehl generiert wurden, und eine optionale Beschreibung des Tools an.

Allgemeine Informationen zu benutzerdefinierten Buildtools und Buildschritten finden Sie unter [Grundlagen benutzerdefinierter Buildschritte und Buildereignisse](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-custom-build-tool"></a>Angeben eines benutzerdefinierten Buildtools

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](working-with-project-properties.md).

1. Klicken Sie auf **Konfigurationseigenschaften**, um das Feld **Konfiguration** zu aktivieren. Wählen Sie im Feld **Konfiguration** die Konfiguration aus, für die Sie ein benutzerdefiniertes Buildtool angeben möchten.

1. Wählen Sie unter **Projektmappen-Explorer** die Eingabedatei für das benutzerdefinierte Buildtool aus.

   Wenn der Ordner **Benutzerdefiniertes Buildtool** nicht angezeigt wird, wird die Erweiterung der ausgewählten Datei einem Standardtool zugeordnet. Das Standardtool für C- und CPP-Dateien ist beispielsweise der Compiler. Wenn Sie die Einstellung für das Standardtool ändern möchten, klicken Sie im Knoten **Konfigurationseigenschaften** des Ordners **Allgemein** in der Eigenschaft **Elementtyp** auf **Benutzerdefiniertes Buildtool**. Klicken Sie auf **Übernehmen**, damit der Knoten **Benutzerdefiniertes Buildtool** angezeigt wird.

1. Geben Sie im Knoten **Benutzerdefiniertes Buildtool** im Ordner **Allgemein** die Eigenschaften an, die dem benutzerdefinierten Buildtool zugeordnet sind:

   - Geben Sie unter **Zusätzliche Abhängigkeiten** zusätzliche Dateien außer derjenigen an, für die das benutzerdefinierte Buildtool definiert ist (die dem benutzerdefinierten Buildtool zugeordnete Datei wird implizit als Eingabe für das Tool betrachtet). Zusätzliche Eingabedateien sind keine Voraussetzung für ein benutzerdefiniertes Buildtool. Wenn Sie mehr als eine zusätzliche Eingabe verwenden, trennen Sie diese durch Semikolons.

      Wenn das Datum einer Datei für **zusätzliche Abhängigkeiten** nach dem der Eingabedatei liegt, wird das benutzerdefinierte Buildtool ausgeführt. Wenn alle Dateien von **zusätzlichen Abhängigkeiten** älter als die Eingabedatei sind und die Eingabedatei älter als die Eigenschaftendatei für **Ausgaben** ist, wird das benutzerdefinierte Buildtool nicht ausgeführt.

      Nehmen Sie beispielsweise an, dass Sie ein benutzerdefiniertes Buildtool besitzen, das „MyInput.x“ als Eingabe verwendet und „MyInput.cpp“ generiert, und dass in „MyInput.x“ eine Headerdatei namens „MyHeader.h“ enthalten ist. Sie können „MyHeader.h“ als Eingabeabhängigkeit für „MyInput.x“ angeben. Das Buildsystem erstellt dann „MyInput.cpp“, wenn es im Vergleich zu „MyInput.x“ oder „MyHeader.h“ veraltet ist.

      Durch Eingabeabhängigkeiten kann ebenfalls sichergestellt werden, dass Ihre benutzerdefinierten Buildtools in der erforderlichen Reihenfolge ausgeführt werden. Nehmen Sie im vorherigen Beispiel an, dass „MyHeader.h“ die tatsächliche Ausgabe eines benutzerdefinierten Buildtools darstellt. Da „MyHeader.h“ eine Abhängigkeit von „MyInput.x“ ist, erstellt das Buildsystem zuerst „MyHeader.h“, bevor das benutzerdefinierte Buildtool für „MyInput.x“ ausgeführt wird.

   - Geben Sie in der **Befehlszeile** einen Befehl so ein, wie Sie ihn über die Eingabeaufforderung eingeben würden. Geben Sie einen gültigen Befehl oder eine Batchdatei sowie alle erforderlichen Ein- und Ausgabedateien an. Geben Sie den Batchbefehl **call** vor dem Namen einer Batchdatei an, um sicherzustellen, dass alle nachfolgenden Befehle ausgeführt werden.

      Mehrere Ein- und Ausgabedateien können symbolisch mit MSBuild-Makros angegeben werden. Weitere Informationen zum Angeben des Speicherorts von Dateien oder der Namen mehrerer Dateien finden Sie unter [Allgemeine Makros für MSBuild-Befehle und-Eigenschaften](reference/common-macros-for-build-commands-and-properties.md).

      Da das Zeichen „%“ von MSBuild reserviert ist, ersetzen Sie jedes **%** -Escapezeichen durch die Escapesequenz für Hexadezimalzahlen **%25**, wenn Sie eine Umgebungsvariable angeben. Ersetzen Sie beispielsweise **%WINDIR%** durch **%25WINDIR%25**. MSBuild ersetzt jede **%25**-Sequenz mit dem **%** -Zeichen, bevor auf die Umgebungsvariablen zugegriffen wird.

   - Geben Sie unter **Beschreibung** eine aussagekräftige Beschreibung des benutzerdefinierten Buildtools ein. Diese wird im **Ausgabefenster** ausgegeben, wenn das Buildsystem dieses Tool verarbeitet.

   - Geben Sie unter **Ausgaben** den Namen der Ausgabedatei an. Dieser Eintrag ist erforderlich. Das benutzerdefinierte Buildtool wird nicht ausgeführt, wenn kein Wert für diese Eigenschaft vorhanden ist. Wenn ein benutzerdefiniertes Buildtool mehr als eine Ausgabe besitzt, trennen Sie die Dateinamen mit einem Semikolon.

      Der Name der Ausgabedatei sollte dem Namen entsprechen, der in der **Befehlszeileneigenschaft** angegeben ist. Das Projektbuildsystem sucht nach der Datei und überprüft deren Datum. Wenn die Ausgabedatei älter als die Eingabedatei ist oder die Ausgabedatei nicht gefunden wird, wird das benutzerdefinierte Buildtool ausgeführt. Wenn alle Dateien von **zusätzlichen Abhängigkeiten** älter als die Eingabedatei sind und die Eingabedatei älter als die in der **Outputs**-Eigenschaft angegebene Datei ist, wird das benutzerdefinierte Buildtool nicht ausgeführt.

Wenn das Buildsystem eine Ausgabedatei verwenden soll, die vom benutzerdefinierten Buildtool generiert wurde, müssen Sie diese manuell zum Projekt hinzufügen. Das benutzerdefinierte Buildtool aktualisiert die Datei während des Builds.

## <a name="example"></a>Beispiel

Angenommen, Sie möchten eine Datei namens „parser.l“ in Ihr Projekt einfügen. Im Pfad der ausführbaren Datei ist ein lexikalisches Analysetool (**lexer.exe**) vorhanden. Dieses möchten Sie verwenden, um „parser.l“ zu verarbeiten, damit eine C-Datei erstellt wird, die den gleichen Basisnamen (parser.c) aufweist.

Fügen Sie zunächst „parser.l“ und anschließend „parser.c“ zum Projekt hinzu. Wenn die Dateien noch nicht vorhanden sind, fügen Sie einen Verweis auf diese hinzu. Erstellen Sie ein benutzerdefiniertes Buildtool für „parser.l“, und geben Sie Folgendes in die **Commands**-Eigenschaft ein:

> **lexer %(Vollständiger_Pfad) .\%(Dateiname).c**

Dieser Befehl führt das lexikalische Analysetool für „parser.l“ aus und gibt „parser.c“ in das Projektverzeichnis aus.

Geben Sie in der **Outputs**-Eigenschaft Folgendes ein:

> **.\%(Dateiname).c**

Wenn Sie das Projekt erstellen, vergleicht das Buildsystem die Zeitstempel von „parser.l“ und „parser.c“. Wenn „parser.l“ aktueller oder „parser.c“ nicht vorhanden ist, führt das Buildsystem den Wert der **Befehlszeileneigenschaft** aus, um „parser.c“ auf den neuesten Stand zu bringen. Da „parser.c“ ebenfalls zum Projekt hinzugefügt wurde, kompiliert das Buildsystem anschließend „parser.c“.

## <a name="see-also"></a>Siehe auch

[Gängige Makros für Buildbefehle und -eigenschaften](reference/common-macros-for-build-commands-and-properties.md)<br>
[Problembehandlung für Buildanpassungen](troubleshooting-build-customizations.md)
