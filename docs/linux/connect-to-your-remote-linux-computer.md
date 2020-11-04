---
title: Herstellen einer Verbindung mit dem Linux-Zielsystem in Visual Studio
description: Informationen zum Herstellen einer Verbindung mit einem Linux-Remotecomputer oder einem Windows-Subsystem für Linux über ein Visual Studio C++-Projekt
ms.date: 01/17/2020
ms.openlocfilehash: da74d1c735a29304fdf46e920eac45580f386259
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921788"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Herstellen einer Verbindung mit dem Linux-Zielsystem in Visual Studio

::: moniker range="msvc-140"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range="msvc-150"

Sie können ein Linux-Projekt für einen Remotecomputer oder ein Windows-Subsystem für Linux (WSL) konfigurieren. Für Remotecomputer und WSL müssen Sie in Visual Studio 2017 eine Remoteverbindung einrichten.

::: moniker-end

::: moniker range="msvc-160"

Sie können ein Linux-Projekt für einen Remotecomputer oder ein Windows-Subsystem für Linux (WSL) konfigurieren. Für einen Remotecomputer müssen Sie in Visual Studio eine Remoteverbindung einrichten. Um eine Verbindung mit WSL herzustellen, fahren Sie mit dem Abschnitt [Herstellen einer Verbindung mit WSL](#connect-to-wsl) fort.

::: moniker-end

::: moniker range=">=msvc-150"

Wenn Sie eine Remoteverbindung verwenden, erstellt Visual Studio C++-Linux-Projekte auf dem Remotecomputer. Es spielt keine Rolle, ob es sich um einen physischen Computer, eine VM in der Cloud oder um WSL handelt.
Um das Projekt zu erstellen, kopiert Visual Studio den Quellcode auf Ihren Linux-Remotecomputer. Anschließend wird der Code entsprechend der in Visual Studio ausgewählten Einstellungen kompiliert.

::: moniker-end

::: moniker range="msvc-160"

> [!NOTE]
> Visual Studio 2019 Version 16.5 oder höher unterstützt auch sichere, mit FIPS 140-2 (Federal Information Processing Standard) kompatible kryptografische Verbindungen mit Linux-Systemen für Remoteentwicklung. Um eine mit FIPS kompatible Verbindung zu verwenden, führen Sie stattdessen die Schritte unter [Einrichten einer FIPS-konformen sicheren Linux-Remoteentwicklung](set-up-fips-compliant-secure-remote-linux-development.md) aus.

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>Einrichten des SSH-Servers auf dem Remotesystem

Wenn SSH nicht bereits auf Ihrem Linux-System eingerichtet ist und ausgeführt wird, führen Sie die folgenden Schritte aus, um SSH zu installieren. In den Beispielen in diesem Artikel wird Ubuntu 18.04 LTS mit OpenSSH Server Version 7.6 verwendet. Allerdings sollten die Anweisungen für jede Distribution identisch sein, die eine moderate aktuelle Version von OpenSSH verwendet.

1. Installieren und starten Sie auf dem Linux-System den OpenSSH-Server:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Wenn Sie möchten, dass der SSH-Server beim Start des Systems automatisch gestartet wird, aktivieren Sie ihn mithilfe von systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>Einrichten der Remoteverbindung

1. Klicken Sie in Visual Studio in der Menüleiste auf **Extras > Optionen** , um das Dialogfeld **Optionen** zu öffnen. Wählen Sie dann **Plattformübergreifend > Verbindungs-Manager** aus, um das Dialogfeld „Verbindungs-Manager“ zu öffnen.

   Wenn Sie zuvor noch keine Verbindung in Visual Studio eingerichtet haben, öffnet Visual Studio das Dialogfeld „Verbindungs-Manager“, wenn Sie das Projekt erstmals erstellen.

1. Wählen Sie im Dialogfeld „Verbindungs-Manager“ die Schaltfläche **Hinzufügen** aus, um eine neue Verbindung hinzuzufügen.

   ![Verbindungs-Manager](media/settings_connectionmanager.png)

   In beiden Fällen wird das Fenster **Connect to Remote System** (Mit Remotesystem verbinden) angezeigt.

   ![Connect to Remote System (Mit Remotesystem verbinden)](media/connect.png)

1. Geben Sie die folgenden Informationen ein:

   | Eingabe | Beschreibung
   | ----- | ---
   | **Hostname**           | Name oder IP-Adresse des Zielgeräts
   | **Port**                | Port, auf dem der SSH-Dienst ausgeführt wird, in der Regel Port 22
   | **Benutzername**           | Zu authentifizierender Benutzer
   | **Authentifizierungstyp** | Sowohl das Kennwort als auch der private Schlüssel wird unterstützt.
   | **Kennwort**            | Kennwort für den eingegebenen Benutzernamen
   | **Datei für den privaten Schlüssel**    | Für die SSH-Verbindung erstellte private Schlüsseldatei
   | **Passphrase**          | Passphrase mit dem zuvor ausgewählten privaten Schlüssel

   Sie können entweder ein Kennwort oder eine Schlüsseldatei und eine Passphrase zur Authentifizierung verwenden. In vielen Entwicklungsszenarien ist Kennwortauthentifizierung ausreichend, aber Schlüsseldateien sind sicherer. Wenn Sie bereits über ein Schlüsselpaar verfügen, ist es möglich, dieses wiederzuverwenden. Zurzeit werden von Visual Studio nur RSA- und DSA-Schlüssel für Remoteverbindungen unterstützt.

1. Klicken Sie auf die Schaltfläche **Verbinden** , um eine Verbindung mit dem Remotecomputer herzustellen.

   Wenn die Verbindung erfolgreich hergestellt wird, konfiguriert Visual Studio IntelliSense für die Verwendung der Remoteheader. Weitere Informationen finden Sie unter [IntelliSense für Header auf Remotesystemen](configure-a-linux-project.md#remote_intellisense).

   Wenn die Verbindung nicht erfolgreich hergestellt wird, werden die Eintragsfelder, die geändert werden müssen, rot umrandet.

   ![Fehler des Verbindungs-Manager](media/settings_connectionmanagererror.png)

   Wenn Sie Schlüsseldateien zur Authentifizierung verwenden, stellen Sie sicher, dass der SSH-Server des Zielcomputers ausgeführt wird und ordnungsgemäß konfiguriert ist.

   ::: moniker-end

   ::: moniker range="msvc-160"

## <a name="logging-for-remote-connections"></a>Protokollierung für Remoteverbindungen

   Sie können Protokollierung aktivieren, um Verbindungsprobleme zu beheben. Wählen Sie in der Menüleiste **Extras > Optionen** aus. Wählen Sie im Dialogfeld **Optionen** **Plattformübergreifend > Protokollierung** aus:

   ![Remoteprotokollierung](media/remote-logging-vs2019.png)

   Protokolle enthalten Verbindungen, alle an den Remotecomputer gesendeten Befehle (Text, Exitcode und Ausführungszeit) sowie die gesamte Ausgabe von Visual Studio an die Shell. Die Protokollierung funktioniert für alle plattformübergreifenden CMake-Projekte oder MSBuild-basierten Linux-Projekte in Visual Studio.

   Sie können konfigurieren, ob die Ausgabe in eine Datei oder in den Bereich **Plattformübergreifende Protokollierung** im Ausgabefenster erfolgen soll. Bei MSBuild-basierten Linux-Projekten werden MSBuild-Befehle, die an den Remotecomputer gesendet werden, nicht an das **Ausgabefenster** weitergeleitet, weil sie prozessextern gesendet werden. Stattdessen werden sie in eine Datei mit dem Präfix „msbuild_“ protokolliert.

## <a name="command-line-utility-for-the-connection-manager"></a>Befehlszeilenhilfsprogramm für den Verbindungs-Manager  

**Visual Studio 2019 Version 16.5 oder höher** : „ConnectionManager.exe“ ist ein Befehlszeilenhilfsprogramm zum Verwalten von Remoteentwicklungsverbindungen außerhalb von Visual Studio. Es ist gut für Aufgaben wie die Bereitstellung eines neuen Entwicklungscomputers geeignet. Sie können es auch zum Einrichten von Visual Studio für Continuous Integration verwenden. Beispiele für den und eine umfassende Referenz zum ConnectionManager-Befehl finden Sie unter [ConnectionManager-Referenz](connectionmanager-reference.md).  

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="tcp-port-forwarding"></a>TCP-Portweiterleitung

Die Linux-Unterstützung von Visual Studio verfügt über eine Abhängigkeit von der TCP-Portweiterleitung. Wenn die TCP-Portweiterleitung in Ihrem Remotesystem deaktiviert wird, wirkt sich dies auf **rsync** und **gdbserver** aus. Wenn Sie von dieser Abhängigkeit betroffen sind, können Sie in der Entwicklercommunity für dieses [Vorschlagsticket](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) abstimmen.

Sowohl MSBuild-basierte Linux-Projekte als auch CMake-Projekte verwenden „rsync“, um [Header aus Ihrem Remotesystem zur Verwendung für IntelliSense in Windows zu kopieren](configure-a-linux-project.md#remote_intellisense). Wenn Sie die TCP-Portweiterleitung nicht aktivieren können, deaktivieren Sie den automatischen Download von Remoteheadern. Navigieren Sie zum Deaktivieren zu **Extras > Optionen > Plattformübergreifend > Verbindungs-Manager > IntelliSense-Manager für Remoteheader**. Wenn im Remotesystem die TCP-Portweiterleitung nicht aktiviert ist, wird der folgende Fehler angezeigt, wenn der Download von Remoteheadern für IntelliSense startet:

![Fehler bei Headern](media/port-forwarding-headers-error.png)

Die CMake-Unterstützung von Visual Studio verwendet „rsync“ ebenfalls, um Quelldateien in das Remotesystem zu kopieren. Wenn Sie die TCP-Portweiterleitung nicht aktivieren können, können Sie SFTP als Methode zum Kopieren von Remotequellen verwenden. SFTP ist häufig langsamer als „rsync“, weist aber keine Abhängigkeit von der TCP-Portweiterleitung auf. Sie können Ihre Methode zum Kopieren von Remotequellen mit der **remoteCopySourcesMethod** -Eigenschaft im [CMake-Einstellungs-Editor](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects) verwalten. Wenn die TCP-Portweiterleitung in Ihrem Remotesystem deaktiviert ist, wird beim ersten Aufrufen von „rsync“ ein Fehler im CMake-Ausgabefenster angezeigt.

![rsync-Fehler](media/port-forwarding-copy-error.png)

„gdbserver“ kann zum Debuggen auf eingebetteten Geräten verwendet werden. Wenn Sie die TCP-Portweiterleitung nicht aktivieren können, müssen Sie „gdb“ für alle Remotedebuggingszenarios verwenden. Beim Debuggen von Projekten in einem Remotesystem wird standardmäßig „gdb“ verwendet.

## <a name="connect-to-wsl"></a>Herstellen einer Verbindung mit WSL

::: moniker-end

::: moniker range="msvc-150"

In Visual Studio 2017 verwenden Sie die gleichen Schritte, um eine Verbindung mit WSL herzustellen, wie Sie für einen Linux-Remotecomputer verwenden würden. Verwenden Sie **localhost** als **Hostnamen**.

::: moniker-end

::: moniker range="msvc-160"

In Version 16.1 von Visual Studio 2019 wurde native Unterstützung für die Verwendung von C++ mit dem [Windows-Subsystem für Linux (WSL)](/windows/wsl/about) hinzugefügt. Das bedeutet, dass Sie den Erstellungs- und den Debugvorgang direkt für Ihre lokale WSL-Installation durchführen können. Es ist nicht mehr erforderlich, eine Remoteverbindung hinzuzufügen oder SSH zu konfigurieren. Weitere Informationen zur [Installation von WSL](/windows/wsl/install-win10) finden Sie hier.

Sie müssen die Tools „gcc „oder „clang“, „gdb“, „make“, „ninja-build“ (nur für CMake-Projekte in Visual Studio 2019 Version 16.6 oder höher erforderlich), „rsync“ und „zip“ installieren, um die WSL-Installation so zu konfigurieren, dass sie mit Visual Studio verwendet werden kann. Sie können sie für Distributionen installieren, die apt verwenden, indem Sie diesen Befehl verwenden, der auch den g++-Compiler installiert:

```bash
sudo apt install g++ gdb make ninja-build rsync zip
```

Weitere Informationen finden Sie unter [Herunterladen, Installieren und Einrichten der Linux-Workload](download-install-and-setup-the-linux-development-workload.md).

Informationen zum Konfigurieren eines MSBuild-Projekts für WSL finden Sie unter [Konfigurieren eines Linux-Projekts](configure-a-linux-project.md). Informationen zum Konfigurieren eines CMake-Projekts für WSL finden Sie unter [Konfigurieren eines Linux CMake-Projekts](cmake-linux-project.md). Eine ausführliche Anleitung für das Erstellen einer einfachen Konsolenanwendung mit WSL finden Sie in diesem Blogbeitrag zur Einführung in [C++ mit Visual Studio 2019 und dem Windows-Subsystem für Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Konfigurieren eines Linux-Projekts](configure-a-linux-project.md)\
[Konfigurieren eines Linux CMake-Projekts](cmake-linux-project.md)\
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](deploy-run-and-debug-your-linux-project.md)\
[Konfigurieren von CMake-Debugsitzungen](../build/configure-cmake-debugging-sessions.md)
