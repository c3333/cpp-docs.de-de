---
title: 'Visual Studio-Projekte: C++'
ms.date: 10/25/2019
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: 3694478e22bfd2a3c58a72ba0c3ad2d15351bc9f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078691"
---
# <a name="visual-studio-projects---c"></a>Visual Studio-Projekte: C++

Ein *Visual Studio-Projekt* ist ein Projekt, das auf dem MSBuild-Buildsystem basiert. MSBuild ist das native Buildsystem für Visual Studio und stellt im Allgemeinen das beste Buildsystem für Windows-spezifische Programme dar. MSBuild ist eng in Visual Studio integriert. Sie können MSBuild jedoch auch über die Befehlszeile verwenden. Für plattformübergreifende Projekte oder Projekte, die Open-Source-Bibliotheken verwenden, wird die Verwendung von [CMake-Projekten in Visual Studio](cmake-projects-in-visual-studio.md) in Visual Studio 2017 und höher empfohlen. Weitere Informationen zum Upgrade von MSBuild-Projekten aus älteren Versionen von Visual Studio finden Sie im [Leitfaden C++ zum Portieren und Aktualisieren von Microsoft](../porting/visual-cpp-porting-and-upgrading-guide.md).

## <a name="create-a-project"></a>Erstellen eines Projekts

::: moniker range="vs-2019"

Sie können C++-Projekte erstellen, indem Sie **Datei** > **Neu** > **Projekt** auswählen und dann die **Sprache** auf C++ einstellen. In der Ergebnisliste sehen Sie eine Liste mit Projektvorlagen, die Sie filtern können, indem Sie die **Plattform** oder den **Projekttyp** festlegen oder Schlüsselwörter in das Suchfeld eingeben.

   ![Visual Studio 2019-Projektvorlagen](../build/media/vs2019-choose-console-app.png "Visual Studio 2019, Dialogfeld „Neues Projekt“")

::: moniker-end

::: moniker range="vs-2017"

Sie können C++-Projekte erstellen, indem Sie **Datei** > **Neu** > **Projekt** und dann Visual C++ im linken Bereich auswählen. Im mittleren Bereich sehen Sie eine Liste mit Projektvorlagen:

   ![Projektvorlagen](../overview/media/vs2017-new-project.png "Visual Studio 2017, Dialogfeld „Neues Projekt“")

::: moniker-end

Weitere Informationen zu allen in Visual Studio enthaltenen Standardprojektvorlagen finden Sie unter [C++-Projektvorlagen in Visual Studio](reference/visual-cpp-project-types.md). Sie können eigene Projektvorlagen erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Projektvorlagen](/visualstudio/ide/how-to-create-project-templates).

Nachdem Sie ein Projekt erstellt haben, wird es im Fenster des [Projektmappen-Explorers](/visualstudio/ide/solutions-and-projects-in-visual-studio) angezeigt:

   ![Projektmappen-Explorer](media/mathlibrary-solution-explorer-153.png)

Beim Erstellen eines neuen Projekts wird außerdem eine Projektmappendatei (SLN) erstellt. Sie können der Projektmappe weitere Projekte hinzufügen, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste darauf klicken. Die Projektmappendatei wird zum Koordinieren von Buildabhängigkeiten unter mehreren verwandten Projekten verwendet, leistet aber nicht viel mehr als das. Alle Compileroptionen werden auf Projektebene festgelegt.

## <a name="add-items"></a>Hinzufügen von Elementen

Fügen Sie Ihrem Projekt Quellcodedateien, Symbole oder beliebige andere Elemente hinzu, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Hinzufügen > Neu** oder **Hinzufügen > Vorhanden** auswählen.

## <a name="add-third-party-libraries"></a>Hinzufügen von Bibliotheken von Drittanbietern

Verwenden Sie zum Hinzufügen von Drittanbieterbibliotheken den [vcpkg](vcpkg.md)-Paket-Manager. Führen Sie den Visual Studio-Integrationsschritt aus, um die Pfade zu dieser Bibliothek einzurichten, damit sie für Verweise aus beliebigen Visual Studio-Projekten zur Verfügung steht.

## <a name="set-compiler-options-and-other-build-properties"></a>Festlegen von Compileroptionen und anderen Buildeigenschaften

Klicken Sie zum Konfigurieren der Buildeinstellungen für ein Projekt im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](working-with-project-properties.md).

## <a name="compile-and-run"></a>Kompilieren und Ausführen

Um das neue Projekt zu kompilieren und auszuführen, drücken Sie **F5**, oder klicken Sie auf die *Debug-Dropdownliste* mit dem grünen Pfeil in der Hauptsymbolleiste. In der *Dropdownliste „Konfiguration“* wählen Sie aus, ob ein *Debug-* oder ein *Release*-Build (oder eine andere, benutzerdefinierte Konfiguration) erstellt werden soll.

Ein neues Projekt wird ohne Fehler kompiliert. Wenn Sie eigenen Code hinzufügen, führen Sie damit möglicherweise gelegentlich einen Fehler ein oder lösen eine Warnung aus. Ein Fehler verhindert die Fertigstellung des Builds; eine Warnung tut das nicht. Beim Erstellen des Projekts werden alle Fehler und Warnungen sowohl im Ausgabefenster als auch in der Fehlerliste angezeigt.

   ![Ausgabefenster und Fehlerliste](../overview/media/vs2017-output-error-list.png)

In der Fehlerliste können Sie durch Drücken von **F1** auf einem hervorgehobenen Fehler zu dessen Dokumentationsthema gelangen.

## <a name="in-this-section"></a>In diesem Abschnitt

[Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio](working-with-project-properties.md)<br/>
Verwenden von Eigenschaftenseiten und Eigenschaftenblättern zum Festlegen von Projekteinstellungen.

[Verweisen auf Bibliotheken und Komponenten zur Buildzeit](adding-references-in-visual-cpp-projects.md)<br/>
Einschließen von Bibliotheken, DLLs, COM- und .NET-Komponenten in einem Projekt.

[Organisieren von Projektausgabedateien](how-to-organize-project-output-files-for-builds.md)<br/>
Anpassen des Speicherorts der im Buildprozess erstellten ausführbaren Dateien.

[Benutzerdefinierte Buildschritte und Buildereignisse](understanding-custom-build-steps-and-build-events.md)<br/>
Hinzufügen beliebiger Befehle zum Buildprozess an festgelegten Punkten.

[Erstellen eines Projekts aus vorhandenem Code](how-to-create-a-cpp-project-from-existing-code.md)<br/>
Erstellen eines neuen Visual Studio-Projekts aus einer losen Sammlung von Quelldateien.

## <a name="see-also"></a>Siehe auch

[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)<br>
[Microsoft C++-Handbuch: Portieren und Aktualisieren](../porting/visual-cpp-porting-and-upgrading-guide.md)
