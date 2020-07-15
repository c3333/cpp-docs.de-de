---
title: Eigenschaftenseite "VC++-Verzeichnisse"
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
ms.openlocfilehash: 7fc81cd5210167ee9df77605677349d6907f3e5d
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373904"
---
# <a name="vc-directories-property-page-windows"></a>Eigenschaftenseite „VC++-Verzeichnisse“ (Windows)

Verwenden Sie diese Eigenschaftenseite, um Visual Studio mitzuteilen, welche Verzeichnisse verwendet werden sollen, wenn das derzeit ausgewählte Projekt erstellt wird. Wenn Sie Verzeichnisse für mehrere Projekte in einer Projekt Mappe festlegen möchten, verwenden Sie ein benutzerdefiniertes Eigenschaften Blatt, wie unter [freigeben oder wieder verwenden von Visual Studio C++ Projekteinstellungen](../create-reusable-property-configurations.md)beschrieben.

Die Linux-Version dieser Seite finden Sie unter [VC++-Verzeichnisse (Linux C++)](../../linux/prop-pages/directories-linux.md).

So greifen Sie auf die Eigenschaftenseite **VC++-Verzeichnisse** zu:

1. Wenn das Fenster **Projektmappen-Explorer** nicht angezeigt wird, klicken Sie im Hauptmenü auf **Ansicht** > **Projektmappen-Explorer**.
1. Klicken Sie mit der rechten Maustaste auf einen Projektknoten (nicht auf die Projektmappe auf oberster Ebene), und wählen Sie **Eigenschaften** aus.
1. Klicken Sie im linken Bereich des Dialogfelds **Eigenschaftenseiten** auf **Konfigurationseigenschaften** > **VC++-Verzeichnisse**.

Die Eigenschaften für VC++-Verzeichnisse gelten für ein Projekt, nicht für den Projektmappenknoten auf oberster Ebene. Wenn **VC++-Verzeichnisse** nicht unter **Konfigurationseigenschaften** angezeigt wird, wählen Sie einen C++-Projektknoten im Fenster **Projektmappen-Explorer** aus:

![Wählen Sie den Projekt Knoten aus.](../media/vcppdir.png "Wählen Sie den Projekt Knoten aus, um die Eigenschaften für VC + +-Verzeichnisse anzuzeigen.")

Beachten Sie, dass die Eigenschaftenseite **VC++-Verzeichnisse** für plattformübergreifende Projekte anders aussieht. Weitere Informationen zu C++-Projekten unter Linux finden Sie unter [VC++-Verzeichnisse (Linux C++)](../../linux/prop-pages/directories-linux.md).

Wenn Sie mit den *Projekteigenschaften* in Visual Studio nicht vertraut sind, ist es möglicherweise hilfreich, zuerst [Set C++ Compiler und Buildeigenschaften in Visual Studio](../working-with-project-properties.md)zu lesen.

Die Standardeinstellungen für die Eigenschaften der **VC++-Verzeichnisse** hängen vom Projekttyp ab. Bei Desktopprojekten enthalten diese die Speicherorte der C++-Tools für ein bestimmtes Plattformtoolset sowie den Speicherort des Windows SDK. Sie können das **Plattformtoolset** und die Version des **Windows SDK** auf der Seite **Konfigurationseigenschaften** > **Allgemein** ändern.

So zeigen Sie die Werte für Verzeichnisse an:

1. Wählen Sie eine der Eigenschaften auf der Seite **VC++-Verzeichnisse** aus, z.B. **Bibliotheksverzeichnisse**.
1. Klicken Sie am Ende des Felds für Eigenschaftswerte auf die Schaltfläche mit dem Pfeil nach unten.
1. Wählen Sie im Dropdownmenü **Bearbeiten** aus.

![Bibliotheks Verzeichnisse bearbeiten](../media/vcppdir_libdir_edit.png "Dialog Feld zum Bearbeiten von Bibliotheks Pfaden")

Folgendes Dialogfeld wird angezeigt:

![Bibliotheks Verzeichnisse anzeigen](../media/vcppdir_libdir.png "Dialog Feld zum Hinzufügen oder Entfernen von Bibliotheks Pfaden")

Verwenden Sie dieses Dialogfeld, um die aktuellen Verzeichnisse anzuzeigen. Wenn Sie ein Verzeichnis jedoch ändern oder eines hinzufügen möchten, sollten Sie den **Eigenschaften-Manager** verwenden, um ein Eigenschaftenblatt zu erstellen oder das Eigenschaftenblatt für den Standardbenutzer ändern. Weitere Informationen finden Sie unter [freigeben oder wieder verwenden von Visual Studio C++ Projekteinstellungen](../create-reusable-property-configurations.md).

Wie Sie oben sehen, werden viele der abgeleiteten Pfade als Makros angegeben.  Klicken Sie auf die Schaltfläche **Makros** in der unteren rechten Ecke des Dialogfelds, um den aktuellen Wert eines Makros zu überprüfen. Beachten Sie, dass viele Makros vom Konfigurationstyp abhängen. Ein Makro in einem Debugbuild kann einen anderen Pfad als das gleiche Makro in einem Releasebuild ergeben.

Sie können im Bearbeitungsfeld nach teilweisen oder vollständigen Übereinstimmungen suchen. Die folgende Abbildung zeigt alle Makros, die die Zeichenfolge „WindowsSDK“ enthalten, sowie den aktuellen Pfad, den das Makro ergibt:

![Anzeigen von Makro Werten](../media/vcppdir_libdir_macros.png "Dialog Feld zum Bearbeiten von Makros")

Hinweis: Diese Liste wird während Ihrer Eingabe aufgefüllt. Drücken Sie nicht auf die **EINGABETASTE**.

Weitere Informationen zu Makros und deren Verwendung anstelle von hart codierten Pfaden, wenn möglich, finden Sie unter [Set C++ Compiler and Build Properties in Visual Studio](../working-with-project-properties.md).

Eine Liste der häufig verwendeten Makros finden Sie unter [Allgemeine Makros für Buildbefehle und-Eigenschaften](common-macros-for-build-commands-and-properties.md).

Sie können eigene Makros auf zwei Arten definieren:

- Legen Sie Umgebungsvariablen in einer Developer-Eingabeaufforderung fest. Alle Umgebungsvariablen werden als MSBuild-Eigenschaften oder -Makros behandelt.

- Definieren Sie Benutzermakros in einer PROPS-Datei. Weitere Informationen finden Sie unter [Property page macros (Makros für Eigenschaftenseiten)](../working-with-project-properties.md).

Weitere Informationen finden Sie in den Blogbeiträgen zu den Themen [VC++ Directories (VC++-Verzeichnisse)](https://docs.microsoft.com/archive/blogs/vsproject/vc-directories), [Inherited Properties and Property Sheets (Geerbte Eigenschaften und Eigenschaftenblätter)](https://docs.microsoft.com/archive/blogs/vsproject/inherited-properties-and-property-sheets) sowie im [Visual Studio 2010 C++ Project Upgrade Guide (Visual Studio 2010-Handbuch für Upgrades von C++-Projekten)](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/).

## <a name="directory-types"></a>Verzeichnistypen

Sie können auch andere Verzeichnisse wie folgt angeben.

**Ausführbare Verzeichnisse**<br/>
Verzeichnisse, in denen nach ausführbaren Dateien gesucht wird. Entspricht der Umgebungsvariablen **PATH**.

**Includeverzeichnisse**<br/>
Verzeichnisse, in denen nach Includedateien gesucht wird, auf die im Quellcode verwiesen wird. Entspricht der Umgebungsvariablen **INCLUDE**.

**Verweisverzeichnisse**<br/>
Verzeichnisse, in denen nach Assembly- und Moduldateien (Metadaten) gesucht wird, auf die im Quellcode über die [#using](../../preprocessor/hash-using-directive-cpp.md)-Direktiven verwiesen wird. Entspricht der Umgebungsvariablen **LIBPATH**.

**Bibliotheksverzeichnisse**<br/>
Verzeichnisse, in denen nach Bibliotheksdateien (.LIB-Dateien) gesucht wird. Dies schließt auch die Laufzeitbibliotheken ein. Entspricht der Umgebungsvariablen **LIB**. Diese Einstellung gilt nicht für OBJ-Dateien; um einen Link zu einer. obj-Datei zu erhalten, wählen Sie auf der Eigenschaften Seite für die **Eigenschaften von Configuration Properties**  >  **Linker**die Option  >  **General** **zusätzliche Bibliotheksabhängigkeiten** aus, und geben Sie den relativen Pfad der Datei an. Weitere Informationen finden Sie unter [Linker-Eigenschaften Seiten](linker-property-pages.md).

**WinRT-Bibliotheksverzeichnisse**<br/>
Verzeichnisse für das Suchen nach WinRT-Bibliotheksdateien für die Verwendung in UWP-Apps (Universelle Windows-Plattform).

**Quellverzeichnisse**<br/>
Verzeichnisse, in denen nach Quelldateien gesucht wird, die für IntelliSense verwendet werden sollen.

**Verzeichnisse ausschließen**<br/>
Vor jeder Kompilierung fragt Visual Studio den Zeitstempel aller Dateien ab, um zu bestimmen, ob seit der letzten Kompilierung Änderungen an diesen vorgenommen wurden. Wenn Ihr Projekt eine große, stabile Bibliothek besitzt, können Sie die Buildzeiten eventuell beschleunigen, indem Sie diese Verzeichnisse aus der Überprüfung der Zeitstempel ausschließen.

## <a name="sharing-the-settings"></a>Freigeben der Einstellungen

Sie können Projekteigenschaften für andere Benutzer oder Computer freigeben. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).
