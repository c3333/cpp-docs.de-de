---
title: Installieren der C++-Workload unter Linux in Visual Studio
description: Informationen zum Herunterladen, Installieren und Einrichten der Linux-Workload für C++ in Visual Studio
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 719fb9a04c3b0090a1ae5442f881ba6b7d2136c5
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077637"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Herunterladen, Installieren und Einrichten der Linux-Workload

::: moniker range="vs-2015"

Linux-Projekte werden von Visual Studio 2017 und höher unterstützt.

::: moniker-end

::: moniker range=">=vs-2017"

Sie können die IDE von Visual Studio unter Windows verwenden, um C++-Projekte zu erstellen, zu bearbeiten und zu debuggen, die auf einem Linux-Remotesystem, einem virtuellen Computer oder im [Windows-Subsystem für Linux](/windows/wsl/about) ausgeführt werden.

Sie können an Ihrer bestehenden Codebasis arbeiten, die CMake nutzt, ohne sie in ein Visual Studio-Projekt konvertieren zu müssen. Wenn Ihre Codebasis plattformübergreifend ist, können Sie sowohl Windows als auch Linux in Visual Studio als Ziel verwenden. Sie können beispielsweise Ihren Code unter Windows in Visual Studio bearbeiten, kompilieren und debuggen und dann das Projekt in kürzester Zeit auf Linux umstellen, um es in einer Linux-Umgebung zu kompilieren und zu debuggen. Linux-Headerdateien werden automatisch auf Ihren lokalen Computer kopiert, auf dem sie von Visual Studio genutzt werden, um vollständige IntelliSense-Unterstützung bereitzustellen (Anweisungsvervollständigung, „Gehe zu Definition“ usw.).

Für jedes dieser Szenarios ist die Workload **Linux-Entwicklung mit C++** erforderlich.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Setup von Visual Studio

1. Geben Sie „Visual Studio Installer“ in das Windows-Suchfeld ein:

   ![Windows-Suchfeld](media/visual-studio-installer-search.png)

2. Suchen Sie in den Ergebnissen unter **Apps** nach dem Installer, und doppelklicken Sie auf ihn. Wenn der Installer geöffnet wird, wählen Sie **Ändern**aus, und klicken Sie dann auf die Registerkarte **Workloads**. Scrollen Sie nach unten zu **Andere Toolsets**, und wählen Sie die Workload **Linux Entwicklung mit C++** aus.

   ![Workload „Visual C++ für Linux-Entwicklung“](media/linuxworkload.png)

1. Wenn Sie für IoT- oder Embedded-Plattformen entwickeln, wechseln Sie im rechten Bereich zu **Installationsdetails**. Erweitern Sie unter **Linux-Entwicklung mit C++** den Eintrag **Optionale Komponenten**, und wählen Sie die benötigten Komponenten. CMake-Unterstützung für Linux ist standardmäßig ausgewählt.

1. Klicken Sie auf **Ändern**, um mit der Installation fortzufahren.

## <a name="options-for-creating-a-linux-environment"></a>Optionen zum Erstellen einer Linux-Umgebung

Wenn Sie noch keinen Linux-Computer besitzen, können Sie einen virtuellen Linux-Computer in Azure erstellen. Weitere Informationen finden Sie unter [Schnellstart: Erstellen eines virtuellen Linux-Computers im Azure-Portal](/azure/virtual-machines/linux/quick-create-portal).

Unter Windows 10 können Sie Ihre bevorzugte Linux-Distribution im WSL (Windows-Subsystem für Linux) installieren und als Ziel verwenden. Weitere Informationen finden Sie unter [Windows-Subsystem für Linux – Installationsleitfaden für Windows 10](/windows/wsl/install-win10). Wenn Sie nicht auf den Microsoft Store zugreifen können, können Sie das [WSL-Distributionspaket manuell herunterladen](/windows/wsl/install-manual). WSL ist eine praktische Konsolenumgebung, die jedoch nicht für grafische Anwendungen empfohlen wird.

::: moniker-end

::: moniker range="vs-2019"

Linux-Projekte in Visual Studio erfordern die Installation der folgenden Abhängigkeiten in Ihrem Linux-Remotesystem oder WSL:

- **Compiler**: Visual Studio 2019 bietet standardmäßig Unterstützung für GCC und [Clang](/cpp/build/clang-support-cmake?view=vs-2019).
- **gdb**: Visual Studio startet gdb automatisch auf dem Linux-System und nutzt das Front-End des Visual Studio-Debuggers, um unter Linux Funktionen für zuverlässiges Debuggen zu bieten.
- **rsync** und **zip**: Die Einbindung von rsync und zip ermöglicht Visual Studio das Extrahieren von Headerdateien aus Ihrem Linux-System in das Windows-Dateisystem zur Verwendung durch IntelliSense.
- **make**
- **openssh-server** (nur Linux-Remotesysteme): Visual Studio und Linux-Remotesysteme werden über eine sichere SSH-Verbindung miteinander verbunden.
- **CMake** (nur CMake-Projekte): Sie können [statisch verknüpfte CMake-Binärdateien für Linux](https://github.com/microsoft/CMake/releases) von Microsoft installieren.

Die folgenden Befehle gehen davon aus, dass Sie g++ anstelle von clang verwenden.

::: moniker-end

::: moniker range="vs-2017"

Linux-Projekte in Visual Studio erfordern die Installation der folgenden Abhängigkeiten in Ihrem Linux-Remotesystem oder WSL:

- **gcc**: Visual Studio 2017 bietet standardmäßig Unterstützung für GCC.
- **gdb**: Visual Studio startet gdb automatisch auf dem Linux-System und nutzt das Front-End des Visual Studio-Debuggers, um unter Linux Funktionen für zuverlässiges Debuggen zu bieten.
- **rsync** und **zip**: Die Einbindung von rsync und zip ermöglicht Visual Studio das Extrahieren von Headerdateien aus Ihrem Linux-System in das Windows-Dateisystem zur Verwendung durch IntelliSense.
- **make**
- **openssh-server**: Visual Studio und Linux-Remotesysteme werden über eine sichere SSH-Verbindung miteinander verbunden.
- **CMake** (nur CMake-Projekte): Sie können [statisch verknüpfte CMake-Binärdateien für Linux](https://github.com/microsoft/CMake/releases) von Microsoft installieren.

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Linux-Setup: Ubuntu im WSL

Wenn Sie für WSL entwickeln, ist es nicht erforderlich, eine Remoteverbindung hinzuzufügen oder SSH zu konfigurieren, um einen Build zu erstellen und zu debuggen. **zip** und **rsync** sind zur automatischen Synchronisierung von Linux-Headern mit Visual Studio für die IntelliSense-Unterstützung erforderlich. Wenn die erforderlichen Anwendungen noch nicht vorhanden sind, können Sie sie wie folgt installieren:

```bash
sudo apt-get install g++ gdb make rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu auf Linux-Remotesystemen

Auf dem Linux-Zielsystem müssen **openssh-server**, **g++** , **gdb** und **make** installiert sein. Zudem muss der SSH-Daemon ausgeführt werden. **zip** und **rsync** sind zur Unterstützung von IntelliSense für die automatische Synchronisierung von Remoteheadern mit Ihrem lokalen Computer erforderlich. Wenn diese Anwendungen noch nicht vorhanden sind, können Sie sie wie folgt installieren:

1. Führen Sie bei einer Shelleingabeaufforderung auf dem Linux-Computer Folgendes aus:

   ```bash
   sudo apt-get install openssh-server g++ gdb make rsync zip
   ```

   Aufgrund des Befehls „sudo“ werden Sie möglicherweise aufgefordert, Ihr Stammkennwort einzugeben.  Ist dies der Fall, geben Sie es ein und setzen den Vorgang fort. Nach Abschluss dieses Vorgangs sind die erforderlichen Dienste und Tools installiert.

1. Stellen Sie sicher, dass der SSH-Dienst auf dem Linux-Computer ausgeführt wird, indem Sie Folgendes ausführen:

   ```bash
   sudo service ssh start
   ```

   Damit wird der Dienst im Hintergrund gestartet und ausgeführt, sodass Verbindungen akzeptiert werden können.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora auf dem WSL

Fedora verwendet den **dnf**-Paket-Installer. Führen Sie den folgenden Befehl aus, um **g++** , **gdb**, **make**, **rsync** und **zip** herunterzuladen:

   ```bash
   sudo dnf install gcc-g++ gdb rsync make zip
   ```

**zip** und **rsync** sind zur automatischen Synchronisierung von Linux-Headern mit Visual Studio für die IntelliSense-Unterstützung erforderlich.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora auf Linux-Remotesystemen

Der Zielcomputer, auf dem Fedora ausgeführt wird, verwendet den **Dnf**-Paket-Installer. Um **openssh-server**, **g++** , **gdb**, **make**, **rsync** und **zip** herunterzuladen und den ssh-Daemon neu zu starten, befolgen Sie diese Anweisungen:

1. Führen Sie bei einer Shelleingabeaufforderung auf dem Linux-Computer Folgendes aus:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb make rsync zip
   ```

   Aufgrund des Befehls „sudo“ werden Sie möglicherweise aufgefordert, Ihr Stammkennwort einzugeben.  Ist dies der Fall, geben Sie es ein und setzen den Vorgang fort. Nach Abschluss dieses Vorgangs sind die erforderlichen Dienste und Tools installiert.

1. Stellen Sie sicher, dass der SSH-Dienst auf dem Linux-Computer ausgeführt wird, indem Sie Folgendes ausführen:

   ```bash
   sudo systemctl start sshd
   ```

   Damit wird der Dienst im Hintergrund gestartet und ausgeführt, sodass Verbindungen akzeptiert werden können.

::: moniker-end

::: moniker range="vs-2015"

Die Unterstützung für die C++-Entwicklung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Jetzt können Sie ein Linux-Projekt erstellen oder öffnen und es so konfigurieren, dass es auf dem Zielsystem ausgeführt wird. Weitere Informationen finden Sie unter:

- [Erstellen eines neuen Linux-Projekts](create-a-new-linux-project.md)
- [Konfigurieren eines Linux CMake-Projekts](cmake-linux-project.md)
