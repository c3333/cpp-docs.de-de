---
title: 'Vorgehensweise: Erstellen eines C++-Projekts aus vorhandenem Code'
ms.date: 05/06/2019
helpviewer_keywords:
- C++, creating projects from existing code
- Create New Project From Existing Code Files Wizard, project settings
f1_keywords:
- vc.appwiz.importwiz.location
- vc.appwiz.importwiz.appsettings
- vc.appwiz.importwiz.debugsettings
- vc.appwiz.importwiz.releasesettings
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: 5e59230186380b787c95dbe08914bcd9d3ca2407
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078549"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Vorgehensweise: Erstellen eines C++-Projekts aus vorhandenem Code

In Visual Studio können Sie vorhandene Codedateien mit dem Assistenten **Neues Projekt aus vorhandenen Codedateien erstellen** in ein C++-Projekt portieren. Dieser Assistent erstellt eine Projektmappe, die das MSBuild-System zum Verwalten der Quelldateien und Buildkonfigurationen verwendet. Diese Vorgehensweise hat sich vor allem für relativ einfache Projekte bewährt, die keine komplexen Ordnerhierarchien aufweisen. Der Assistent ist in älteren Express-Editionen von Visual Studio nicht verfügbar.

Durch das Portieren Ihrer vorhandenen Codedateien in ein C++-Projekt wird es Ihnen ermöglicht, alle nativen MSBuild-Projektverwaltungsfeatures zu verwenden, die in der IDE integriert sind. Wenn Sie es vorziehen, Ihr vorhandenes Buildsystem zu verwenden, z. B. NMake-Makefiles, CMake oder andere, können Sie stattdessen die Option „Ordner öffnen“ oder „CMake“ verwenden. Weitere Informationen finden Sie unter [„Ordner öffnen“-Projekte für C++](open-folder-projects-cpp.md) bzw. [CMake-Projekte in Visual Studio](cmake-projects-in-visual-studio.md). Mit beiden Optionen können Sie IDE-Features wie [IntelliSense](/visualstudio/ide/using-intellisense) und [Projekteigenschaften](working-with-project-properties.md) verwenden.

### <a name="to-create-a-c-project-from-existing-code"></a>So erstellen Sie ein C++-Projekt aus vorhandenem Code

1. Klicken Sie im Menü **Datei** auf **Neu** > **Project From Existing Code** (Projekt aus vorhandenem Code).

1. Geben Sie den Speicherort Ihres Projekts, das Verzeichnis Ihrer Quelldateien und die Dateitypen an, die der Assistent in das neue Projekt importieren soll. Klicken Sie auf **Weiter** , um fortzufahren.

    | Einstellung | Beschreibung |
    | --- | --- |
    | **Projektdateiverzeichnis** | Gibt den Verzeichnispfad des neuen Projekts an. Dieser Speicherort befindet sich dort, wo der Assistent alle Dateien (und Unterverzeichnisse) des neuen Projekts ablegt.<br/><br/>Klicken Sie auf **Durchsuchen**, um das Dialogfeld **Projektdateiverzeichnis** anzuzeigen. Navigieren Sie zum richtigen Ordner, und geben Sie das Verzeichnis an, das das neue Projekt enthält. |
    | **Projektname** | Gibt den Namen des neuen Projekts an. Projektdateien, die Erweiterungen wie z.B. VCXPROJ vorweisen, übernehmen diesen Namen, und vorhandene Codedateien behalten ihren ursprünglichen Namen. |
    | **Dem Projekt Dateien aus diesen Ordnern hinzufügen** | Wenn diese Option aktiviert ist, kopiert der Assistent vorhandene Codedateien aus ihren ursprünglichen Verzeichnissen (die im Listenfeld unter diesem Steuerelement angezeigt werden) in das neue Projekt.<br/><br/>Aktivieren Sie **Unterordner einbeziehen**, um festzulegen, dass Codedateien aus allen Unterverzeichnissen in das Projekt kopiert werden sollen. Die Verzeichnisse finden Sie in der Spalte **Ordner**.<br/>Klicken Sie auf **Hinzufügen**, um das Dialogfeld **Dateien von diesem Ordner zum Projekt hinzufügen** zu öffnen und dann die Verzeichnisse festzulegen, die der Assistent nach vorhandenen Codedateien durchsucht.<br/>Klicken Sie auf **Entfernen**, um den im Listenfeld ausgewählten Verzeichnispfad zu löschen.<br/><br/>Geben Sie im Feld **Dateitypen zum Projekt hinzufügen** die Dateitypen an, die der Assistent dem neuen Projekt basierend auf den jeweiligen Erweiterungen hinzufügen soll. Den Erweiterungen wird ein Sternchen als Platzhalterzeichen vorangestellt, und sie werden in der Liste von Dateierweiterungen durch Semikolons getrennt. |
    | **Alle Dateien im Projektmappen-Explorer anzeigen** | Gibt an, dass alle Dateien im neuen Projekt im Fenster **Projektmappen-Explorer** sichtbar sind und angezeigt werden. Diese Option ist standardmäßig aktiviert. |

    ![Projektspeicherort](media/location.png)

1. Legen Sie die Projekteinstellungen wie etwa die Buildumgebung für das neue Projekt sowie die Buildeinstellungen so fest, dass sie der Art des Projekts entsprechen, das neu generiert werden soll. Klicken Sie auf **Weiter** , um fortzufahren.

    | Einstellung | Beschreibung |
    | --- | --- |
    | **Visual Studio verwenden** | Gibt an, dass Buildtools verwendet werden sollen, die zum Erstellen des neuen Projekts in Visual Studio enthalten sind. Diese Option ist standardmäßig ausgewählt.<br/><br/>Klicken Sie auf **Projekttyp**, um den Projekttyp anzugeben, den der Assistent generieren soll. Wählen Sie **Windows-Anwendungsprojekt**, **Konsolenanwendungsprojekt**, **DLL-Projekt (Dynamically Linked Library)** oder **LIB-Projekt (Static Library, Statische Bibliothek)** .<br/><br/>Aktivieren Sie **ATL-Unterstützung hinzufügen**, um ATL-Unterstützung zum neuen Projekt hinzuzufügen.<br/><br/>Aktivieren Sie **Unterstützung für MFC hinzufügen**, um MFC-Unterstützung zum neuen Projekt hinzuzufügen.<br/><br/>Aktivieren Sie **Unterstützung für die Common Language Runtime hinzufügen**, um Unterstützung für CRL-Programmierung zum Projekt hinzuzufügen. Wählen Sie die **Common Language Runtime-Unterstützung** als Konformitätstyp aus, z. B. **Common Language Runtime (old syntax)** (Common Language Runtime (alte Syntax)), um die Konformität mit der Managed Extensions for C++-Syntax zu gewährleisten. Dabei handelt es sich um Syntax für die CLR-Programmierung, die vor Visual Studio 2005 verwendet wurde. |
    | **Externes Buildsystem verwenden** | Gibt an, dass zum Erstellen des neuen Projekts Buildtools verwendet werden sollen, die nicht in Visual Studio enthalten sind. Wenn diese Option ausgewählt ist, können Sie Buildbefehlszeilen auf den Seiten **Einstellungen für Debugkonfiguration angeben** und **Einstellungen für Releasekonfiguration angeben** angeben. |

    ![Projekteinstellungen](media/settings.png)

    > [!NOTE]
    > Wenn die Option **Externes Buildsystem verwenden** aktiviert ist, erstellt die IDE das Projekt nicht. Die Optionen „/D“, „/I“, „/FI“, „/AI“, und „/FU“ sind für die Kompilierung also nicht erforderlich. Diese Optionen müssen allerdings ordnungsgemäß festgelegt werden, damit IntelliSense ordnungsgemäß funktioniert.

1. Legen Sie die zu verwendenden Debugkonfigurationseinstellungen fest. Klicken Sie auf **Weiter** , um fortzufahren.

    | Einstellung | Beschreibung |
    | --- | --- |
    | **Buildbefehlszeile** | Gibt die Befehlszeile an, mit der das Projekt erstellt wird. Geben Sie den Namen des Compilers (einschließlich aller Optionen und Argumente) oder des Buildskripts an, der bzw. das zum Erstellen des Projekts verwendet werden soll. |
    | **Neuerstellungsbefehlszeile** | Gibt die Befehlszeile an, mit der das neue Projekt neu erstellt wird. |
    | **Befehlszeile „Bereinigen“** | Gibt die Befehlszeile zum Löschen der von den Buildtools für das Projekt erstellten Unterstützungsdateien an. |
    | **Ausgabe (zum Debuggen)** | Gibt den Verzeichnispfad der Ausgabedateien für die Debugkonfiguration des Projekts an. |
    | **Präprozessordefinitionen (/D)** | Definiert Präprozessorsymbole für das Projekt. Weitere Informationen hierzu finden Sie unter [/D (Präprozessordefinitionen)](../build/reference/d-preprocessor-definitions.md). |
    | **Includesuchpfad (/I)** | Gibt Verzeichnispfade an, die der Compiler sucht, um Dateiverweise aufzulösen, die an Präprozessordirektiven im neuen Projekt übergeben werden. Weitere Informationen hierzu finden Sie unter [/I (Zusätzliche Includeverzeichnisse)](../build/reference/i-additional-include-directories.md). |
    | **Erzwungene Includedateien (/FI)** | Gibt Headerdateien an, die beim Erstellen des Projekts verarbeitet werden. Weitere Informationen hierzu finden Sie unter [/FI (Name Forced Include File) (Name der erzwungenen Includedatei)](../build/reference/fi-name-forced-include-file.md). |
    | **.NET-Assemblysuchpfad (/AI)** | Gibt die Verzeichnispfade an, die der Compiler durchsucht, um .NET-Assemblyverweise aufzulösen, die an Präprozessordirektiven im Projekt übergeben werden. Weitere Informationen hierzu finden Sie unter [/AI (Specify Metadata Directories) (/AI (Metadatenverzeichnisse festlegen))](../build/reference/ai-specify-metadata-directories.md). |
    | **Erzwungene Verwendung von .NET-Assemblys (/FU)** | Gibt .NET-Assemblys an, die beim Erstellen des Projekts verarbeitet werden. Weitere Informationen hierzu finden Sie unter [/FU (Name Forced #using File) (/FU (Name der erzwungenen #using-Datei))](../build/reference/fu-name-forced-hash-using-file.md). |

    ![Projektkonfiguration](media/config.png)

    > [!NOTE]
    > Die Einstellungen für die Befehlszeilen **Erstellen**, **Neu erstellen**, **Bereinigen** und **Output (for debugging)** (Ausgabe (Debuggen)) sind nur aktiviert, wenn die Option **Externes Buildsystem verwenden** auf der Seite **Projekteinstellungen angeben** ausgewählt ist.

1. Legen sie die Releasekonfigurationseinstellungen fest, die verwendet werden sollen. Diese Einstellungen sind dieselben wie die Einstellungen für die Debugkonfiguration. Klicken Sie auf **Fertig stellen**, um das neue Projekt zu generieren.

    > [!NOTE]
    > Hier können Sie **Wie Debugkonfiguration** aktivieren, um anzugeben, dass der Assistent die Projekteinstellungen für die Releasekonfiguration identisch mit den Projekteinstellungen für die Debugkonfiguration festlegt. Diese Option ist standardmäßig aktiviert. Alle anderen Optionen auf dieser Seite sind inaktiv, es sei denn, Sie deaktivieren dieses Kontrollkästchen.
