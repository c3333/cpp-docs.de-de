---
title: Erstellen eines CMake-Projekts für Linux in Visual Studio
description: Informationen zum Erstellen ein CMake-Projekts für Linux in Visual Studio
ms.date: 08/06/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 1b622bcd2af49ee51f7546be4c7a6d804c3102d0
ms.sourcegitcommit: 2034f8e744a8b36cff8b15e9a5cfe684afebadfb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2020
ms.locfileid: "88043823"
---
# <a name="create-a-cmake-linux-project-in-visual-studio"></a>Erstellen eines CMake-Projekts für Linux in Visual Studio

::: moniker range="vs-2015"
Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie die Dropdownliste **Version** über dem Inhaltsverzeichnis auf **Visual Studio 2017** oder **Visual Studio 2019** fest.
::: moniker-end

::: moniker range=">=vs-2017"

Wir empfehlen, CMake für Projekte zu verwenden, die plattformübergreifend sind oder als Open Source veröffentlicht werden sollen. Sie können CMake-Projekte zum Erstellen und Debuggen desselben Quellcodes unter Windows, im Windows-Subsystem für Linux (WSL) und auf Remotesystemen verwenden.

## <a name="before-you-begin"></a>Voraussetzungen

Stellen Sie zunächst sicher, dass Sie die Visual Studio-Workload „ Linux“ einschließlich CMake-Komponente installiert haben. Sie ist Teil der Workload **Linux-Entwicklung mit C++** im Visual Studio-Installationsprogramm. Weitere Informationen finden Sie unter [Herunterladen, Installieren und Einrichten der Linux-Workload](download-install-and-setup-the-linux-development-workload.md), wenn Sie nicht sicher sind, dass sie installiert ist.

Stellen Sie sicher, dass Folgendes auf dem Remotecomputer installiert ist:

- gcc
- gdb
- rsync
- zip
- ninja-build (Visual Studio 2019 oder höher)
::: moniker-end

::: moniker range="vs-2017"
Die CMake-Unterstützung in Visual Studio erfordert Unterstützung des Servermodus, der in CMake 3.8 eingeführt wurde. Laden Sie für eine von Microsoft bereitgestellte CMake-Variante unter [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) die aktuellsten vordefinierten Binärdateien herunter.

Die Binärdateien werden unter `~/.vs/cmake` installiert. Nach dem Bereitstellen der Binärdateien wird Ihr Projekt automatisch neu generiert. Wenn die vom Feld `cmakeExecutable` in *CMakeSettings.json* angegebene CMake-Version ungültig ist (Version nicht vorhanden oder ungültig) und die vorab erstellten Binärdateien vorhanden sind, ignoriert Visual Studio `cmakeExecutable` und verwendet die vorab erstellten Binärdateien.

In Visual Studio 2017 kann ein CMake-Projekt nicht von Grund auf neu erstellt werden. Sie können jedoch, wie im nächsten Abschnitt beschrieben, einen Ordner öffnen, der ein vorhandenes CMake-Projekt enthält.
::: moniker-end

::: moniker range=">=vs-2019"
Sie können Visual Studio 2019 zum Erstellen und Debuggen auf einem Linux-Remotesystem oder im WSL verwenden, wobei CMake auf diesem System aufgerufen wird. Die CMake-Version 3.14 oder höher muss auf dem Zielcomputer installiert sein.

Stellen Sie sicher, dass der Zielcomputer über eine aktuelle Version von CMake verfügt. Die vom Standardpaket-Manager einer Distribution bereitgestellte Version ist häufig nicht aktuell genug, um alle für Visual Studio erforderlichen Features zu unterstützen. Visual Studio 2019 erkennt, ob eine aktuelle Version von CMake auf dem Linux-System installiert ist. Wenn keine gefunden werden kann, zeigt Visual Studio über dem Editorbereich eine Infoleiste an. Dort haben Sie die Möglichkeit, CMake von [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) herunterzuladen und zu installieren.

In Visual Studio 2019 können Sie ein CMake-Projekt von Grund auf neu erstellen oder ein vorhandenes CMake-Projekt öffnen. Um ein neues CMake-Projekt zu erstellen, befolgen Sie die nachstehenden Anweisungen. Oder fahren Sie mit [Öffnen eines CMake-Projektordners](#open-a-cmake-project-folder) fort, wenn Sie bereits ein CMake-Projekt haben.

## <a name="create-a-new-linux-cmake-project"></a>Erstellen eines neuen CMake-Projekts unter Linux

So erstellen Sie ein neues Linux CMake-Projekt in Visual Studio 2019

1. Wählen Sie in Visual Studio **Datei > Neues Projekt** aus, oder drücken Sie **STRG + UMSCHALT + N**.
1. Legen Sie **Sprache** auf **C++** fest, und suchen Sie nach „CMake“. Klicken Sie dann auf **Weiter**. Geben Sie einen **Namen** und einen **Speicherort** an, und klicken Sie auf **Erstellen**.

Alternativ können Sie Ihr eigenes CMake-Projekt in Visual Studio 2019 öffnen. Im folgenden Abschnitt wird dies erläutert.

Visual Studio erstellt eine minimale Datei namens *CMakeLists.txt* mit nur dem Namen der ausführbaren Datei und der mindestens erforderlichen CMake-Version. Sie können diese Datei jedoch manuell nach Belieben bearbeiten. Visual Studio wird Ihre Änderungen in keinem Fall überschreiben.

Um Ihnen zu helfen, Ihre CMake-Skripts in Visual Studio 2019 zu verstehen, zu bearbeiten und zu erstellen, verweisen wir auf die folgenden Ressourcen:

- [Dokumentation für CMake im Editor in Visual Studio](https://devblogs.microsoft.com/cppblog/in-editor-documentation-for-cmake-in-visual-studio/)
- [Codenavigation für CMake-Skripts](https://devblogs.microsoft.com/cppblog/code-navigation-for-cmake-scripts/)
- [Einfaches Hinzufügen, Entfernen und Umbenennen von Dateien und Zielen in CMake-Projekten](https://devblogs.microsoft.com/cppblog/easily-add-remove-and-rename-files-and-targets-in-cmake-projects/)
::: moniker-end

::: moniker range=">=vs-2017"
## <a name="open-a-cmake-project-folder"></a>Öffnen eines CMake-Projektordners

Wenn Sie einen Ordner öffnen, der ein bereits vorhandenes CMake-Projekt enthält, verwendet Visual Studio Variablen im CMake-Cache, um IntelliSense und Builds automatisch zu konfigurieren. Lokale Konfigurations- und Debugeinstellungen werden in JSON-Dateien gespeichert. Sie können diese Dateien optional für andere Personen freigeben, die Visual Studio verwenden.

Visual Studio ändert die *CMakeLists.txt*-Dateien nicht. Auf diese Weise können andere, die am gleichen Projekt arbeiten, ihre bereits vorhandenen Tools weiter verwenden. Visual Studio generiert den Cache neu, wenn Sie Änderungen an *CMakeLists.txt* oder in einigen Fällen an *CMakeSettings.json* speichern. Wenn Sie aber eine Konfiguration des Typs **Vorhandener Cache** nutzen, ändert Visual Studio den Cache nicht.

Allgemeine Informationen zur Unterstützung von CMake in Visual Studio finden Sie unter [CMake-Projekte in Visual Studio](../build/cmake-projects-in-visual-studio.md). Diesen Artikel sollten Sie lesen, bevor Sie hier fortfahren.

Klicken Sie zum Starten im Hauptmenü auf **Datei** > **Öffnen** > **Ordner**, oder geben Sie `devenv.exe <foldername>` in einem Fenster mit einer [Developer-Eingabeaufforderung](../build/building-on-the-command-line.md) ein. Der Ordner, den Sie öffnen, sollte eine Datei *CMakeLists.txt* sowie Ihren Quellcode enthalten.

Das folgende Beispiel zeigt eine einfache *CMakeLists.txt*-Datei und eine CPP-Datei:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

*CMakeLists.txt:*

```txt
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren eines Linux CMake-Projekts](cmake-linux-configure.md)

## <a name="see-also"></a>Siehe auch

[CMake Projects in Visual Studio (CMake-Projekte in Visual Studio)](../build/cmake-projects-in-visual-studio.md)<br/>
::: moniker-end
