---
title: Bereitstellen, Ausführen und Debuggen Ihres C++-Projekts unter Linux in Visual Studio
description: Informationen zum Kompilieren, Ausführen und Debuggen von Code auf dem Remoteziel in einem C++-Projekt unter Linux in Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: e68feab3a71cd5bb3f6b88eee52f0872ef4bb213
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "80077836"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Bereitstellen, Ausführen und Debuggen eines Linux-Projekts

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

Nachdem Sie ein C++-Projekt in Visual Studio unter Linux erstellt haben und mit dem [Verbindungs-Manager von Linux](connect-to-your-remote-linux-computer.md) eine Verbindung mit dem Projekt hergestellt haben, können Sie das Projekt ausführen und debuggen. Die Kompilierung, die Ausführung und das Debuggen des Codes erfolgen auf dem Remoteziel.

::: moniker range="vs-2019"

**Visual Studio 2019 Version 16.1**: Sie können für verschiedene Linux-Systeme Debug- und Buildvorgänge durchführen. Beispielsweise können Sie unter x64 eine Crosskompilierung durchführen und eine Bereitstellung auf einem ARM-Gerät vornehmen, wenn Sie auf IoT-Szenarien abzielen. Weitere Informationen finden Sie unter [Angeben verschiedener Computer zum Erstellen von Builds und Debuggen](#separate_build_debug) weiter unten in diesem Artikel.

::: moniker-end

Es gibt mehrere Möglichkeiten für den Umgang mit dem Linux-Projekt sowie zum Debuggen des Projekts.

- Debuggen Sie mit herkömmlichen Features von Visual Studio wie Haltepunkten, Überwachungsfenstern und Positionieren des Mauszeigers über einer Variablen. Mit diesen Methoden können Sie wie bei anderen Projekttypen debuggen.

- Zeigen Sie die Ausgabe vom Zielcomputer im Linux-Konsolenfenster an. Sie können die Konsole auch verwenden, um Eingaben an den Zielcomputer zu senden.

## <a name="debug-your-linux-project"></a>Debuggen eines Linux-Projekts

1. Wählen Sie den Debugmodus auf der Eigenschaftenseite **Debuggen** aus.

   ::: moniker range="vs-2019"

   GDB wird zum Debuggen von Anwendungen verwendet, die unter Linux ausgeführt werden. Beim Debuggen auf einem Remotesystem (nicht WSL) stehen gdb für die Ausführung zwei verschiedene Modi zur Verfügung, die über die Option **Debugmodus** auf der Eigenschaftenseite **Debuggen** des Projekts ausgewählt werden können:

   ![GDB-Optionen](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB wird zum Debuggen von Anwendungen verwendet, die unter Linux ausgeführt werden. Für die Ausführung stehen GDB zwei verschiedene Modi zur Verfügung, die über die Option **Debugging Mode** (Debugmodus) auf der Eigenschaftenseite **Debugging** (Debuggen) des Projekts ausgewählt werden können:

   ![GDB-Optionen](media/vs2017-debugger-settings.png)

   ::: moniker-end

   - Im **gdbserver**-Modus wird GDB lokal ausgeführt und stellt eine Verbindung mit gdbserver auf dem Remotesystem aus.  Dies ist der einzige Modus, der vom Linux-Konsolenfenster unterstützt wird.

   - Im **gdb**-Modus steuert der Visual Studio-Debugger GDB auf dem Remotesystem. Diese Option eignet sich besser, wenn die lokale Version von GDB nicht mit der Version kompatibel ist, die auf dem Zielcomputer installiert ist. |

   > [!NOTE]
   > Wenn Sie im gdbserver-Debugmodus keine Haltepunkte treffen können, versuchen Sie es im gdb-Modus. GDB muss zunächst auf dem Remoteziel [installiert](download-install-and-setup-the-linux-development-workload.md) werden.

1. Wählen Sie das Remoteziel mit der Standardsymbolleiste **Debuggen** in Visual Studio aus.

   Wenn das Remoteziel verfügbar ist, wird es anhand des Namens oder der IP-Adresse aufgelistet.

   ![Remoteziel](media/remote_target.png)

   Wenn Sie noch keine Verbindung mit dem Remoteziel hergestellt haben, wird eine Anweisung angezeigt, mit dem [Verbindungs-Manager von Linux](connect-to-your-remote-linux-computer.md) eine Verbindung mit dem Remoteziel herzustellen.

   ![Remotearchitektur](media/architecture.png)

1. Legen Sie einen Haltepunkt fest, indem Sie auf der linken Seite einer Codezeile klicken, von der Sie wissen, dass sie ausgeführt wird.

   In der Codezeile, in der Sie den Haltepunkt festlegen, wird ein roter Punkt angezeigt.

1. Drücken Sie **F5** (oder **Debuggen > Debuggen starten**), um das Debuggen zu starten.

   Wenn Sie das Debuggen starten, wird die Anwendung auf dem Remoteziel kompiliert, bevor sie gestartet wird. Fehler bei der Kompilierung werden im Fenster **Fehlerliste** angezeigt.

   Wenn keine Fehler vorliegen, wird die App gestartet, und der Debugger unterbricht die Ausführung am Haltepunkt.

   ![Treffen eines Haltepunkts](media/hit_breakpoint.png)

   Jetzt können Sie mit der Anwendung in ihrem aktuellen Zustand interagieren, Variablen anzeigen und Code schrittweise durchlaufen, indem Sie Befehlstasten wie **F10** oder **F11** drücken.

1. Wenn Sie die Linux-Konsole für die Interaktion mit Ihrer App verwenden möchten, wählen Sie **Debuggen > Linux-Konsole** aus.

   ![Menü mit Linux-Konsole](media/consolemenu.png)

   In dieser Konsole werden alle Konsolenausgaben vom Zielcomputer angezeigt. Zudem werden über die Konsole Eingaben an den Zielcomputer gesendet.

   ![Linux-Konsolenfenster](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>Konfigurieren anderer Debugoptionen (MSBuild-basierte Projekte)

- Befehlszeilenargumente können mit dem Element **Programmargumente** auf der Eigenschaftenseite **Debugging** (Debuggen) des Projekts an die ausführbare Datei übergeben werden.

   ![Programmargumente](media/settings_programarguments.png)

- Bestimmte Debuggeroptionen können mit dem Eintrag **Weitere Debuggerbefehle** an GDB übergeben werden.  Beispiel: SIGILL-Signale (unzulässige Anweisung) sollen ignoriert werden.  Sie können den Befehl **handle** verwenden, um dies zu erreichen, indem Sie dem Eintrag **Additional Debugger Commands** wie oben gezeigt Folgendes hinzufügen:

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>Konfigurieren anderer Debugoptionen (CMake-Projekte)

Sie können zusätzliche Befehlszeilenargumente für ein CMake-Projekt in der Datei „launch.vs.json“ angeben. Weitere Informationen finden Sie unter [Debuggen des CMake-Projekts](cmake-linux-project.md#debug_cmake_project).

## <a name="debug-with-attach-to-process"></a>Debuggen mit „An den Prozess anhängen“

Die Eigenschaftenseite [Debuggen](prop-pages/debugging-linux.md) für Visual Studio-Projekte und die **launch.vs.json**-Einstellungen für CMake-Projekte enthalten Einstellungen, über die Sie Anfügungen an laufende Prozesse durchführen können. Wenn Sie zusätzliche Steuerungsoptionen benötigen, die nicht von diesen Einstellungen abgedeckt werden, können Sie eine Datei mit dem Namen `Microsoft.MIEngine.Options.xml` am Stamm Ihrer Projektmappe oder Ihres Arbeitsbereichs ablegen. Hier sehen Sie ein einfaches Beispiel:

```xml
<?xml version="1.0" encoding="utf-8"?>
<SupplementalLaunchOptions>
    <AttachOptions>
      <AttachOptionsForConnection AdditionalSOLibSearchPath="/home/user/solibs">
        <ServerOptions MIDebuggerPath="C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\Common7\IDE\VC\Linux\bin\gdb\7.9\x86_64-linux-gnu-gdb.exe"
ExePath="C:\temp\ConsoleApplication17\ConsoleApplication17\bin\x64\Debug\ConsoleApplication17.out"/>
        <SetupCommands>
          <Command IgnoreFailures="true">-enable-pretty-printing</Command>
        </SetupCommands>
      </AttachOptionsForConnection>
    </AttachOptions>
</SupplementalLaunchOptions>
```

Das Objekt **AttachOptionsForConnection** verfügt über die meisten Attribute, die Sie möglicherweise brauchen. Das oben stehende Beispiel veranschaulicht, wie Sie einen Speicherort für die Suche nach zusätzlichen SO-Bibliotheken angeben. Durch das untergeordnete Element **ServerOptions** können Sie stattdessen Anfügungen an den Remoteprozess mit gdbserver durchführen. Dazu müssen Sie einen lokalen gdb-Client (der mit Visual Studio 2017 ausgelieferte wird oben gezeigt) und eine lokale Kopie der Binärdatei mit Symbolen angeben. Durch das Element **SetupCommands** können Sie Befehle direkt an gdb übergeben. Alle verfügbaren Optionen finden Sie im [LaunchOptions.xsd-Schema](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) auf GitHub.

::: moniker range="vs-2019"

## <a name="specify-different-machines-for-building-and-debugging"></a><a name="separate_build_debug"></a> Angeben verschiedener Computer zum Erstellen von Builds und Debuggen

In Visual Studio 2019, Version 16.1, können Sie Ihren Remotebuildcomputer von Ihrem Remotedebugcomputer trennen, und zwar sowohl für MSBuild-basierte Linux-Projekte als auch für CMake-Projekte, die einen Linux-Remotecomputer als Ziel haben. Beispielsweise können Sie nun unter x64 eine Crosskompilierung durchführen und eine Bereitstellung auf einem ARM-Gerät vornehmen, wenn Sie auf IoT-Szenarien abzielen.

### <a name="msbuild-based-projects"></a>MSBuild-basierte Projekte

Standardmäßig ist der Remotedebugcomputer identisch mit dem Remotebuildcomputer (**Konfigurationseigenschaften** > **Allgemein** > **Remotebuildcomputer**). Um einen neuen Remotedebugcomputer anzugeben, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wechseln Sie zu **Konfigurationseigenschaften** > **Debuggen** > **Remotedebugcomputer**.  

![Linux-Remotedebugcomputer](media/linux-remote-debug-machine.png)

Das Dropdownmenü für **Remotedebugcomputer** wird mit allen eingerichteten Remoteverbindungen aufgefüllt. Um eine neue Remoteverbindung hinzuzufügen, navigieren Sie zu **Tools** > **Optionen** > **Plattformübergreifend** > **Verbindungs-Manager**, oder suchen Sie in **Schnellstart** nach „Verbindungs-Manager“. Sie können auch auf den Eigenschaftsseiten des Projekts (**Konfigurationseigenschaften** > **Allgemein** > **Remotebereitstellungsverzeichnis**) ein neues Remotebereitstellungsverzeichnis angeben.

Standardmäßig werden nur die Dateien, die für den zu debuggenden Prozess erforderlich sind, auf dem Remotedebugcomputer bereitgestellt. Sie können im **Projektmappen-Explorer** konfigurieren, welche Quelldateien dem Remotedebugcomputer bereitgestellt werden sollen. Wenn Sie auf eine Quelldatei klicken, sehen Sie direkt unter dem Projektmappen-Explorer eine Vorschau ihrer Dateieigenschaften.

![Unter Linux bereitstellbare Dateien](media/linux-deployable-content.png)

Die **Content**-Eigenschaft gibt an, ob die Datei auf dem Remotedebugcomputer bereitgestellt wird. Sie können die Bereitstellung vollständig deaktivieren, indem Sie zu **Eigenschaftsseiten** > **Konfigurations-Manager** navigieren und **Bereitstellen** für die gewünschte Konfiguration deaktivieren.

Möglicherweise benötigen Sie in einigen Fällen mehr Kontrolle über die Bereitstellung Ihres Projekts. Beispielsweise können sich einige Dateien, die Sie bereitstellen möchten, außerhalb Ihrer Projektmappe befinden, oder Sie möchten Ihr Remotebereitstellungsverzeichnis datei- oder verzeichnisweise anpassen. Fügen Sie in diesen Fällen die folgenden Codeblöcke an Ihre VCXPROJ-Datei an, und ersetzen Sie „example.cpp“ durch die tatsächlichen Dateinamen:

```xml

<ItemGroup>
   <RemoteDeploy Include="__example.cpp">
<!-- This is the source Linux machine, can be empty if DeploymentType is LocalRemote -->
      <SourceMachine>$(RemoteTarget)</SourceMachine>
      <TargetMachine>$(RemoteDebuggingTarget)</TargetMachine>
      <SourcePath>~/example.cpp</SourcePath>
      <TargetPath>~/example.cpp</TargetPath>
<!-- DeploymentType can be LocalRemote, in which case SourceMachine will be empty and SourcePath is a local file on Windows -->
      <DeploymentType>RemoteRemote</DeploymentType>
<!-- Indicates whether the deployment contains executables -->
      <Executable>true</Executable>
   </RemoteDeploy>
</ItemGroup>
```

### <a name="cmake-projects"></a>CMake-Projekte

Für CMake-Projekte, die einen Linux-Remotecomputer als Ziel haben, können Sie in „launch.vs.json“ einen neuen Remotedebugcomputer angeben. Standardmäßig wird der Wert von „remoteMachineName“ mit der Eigenschaft „remoteMachineName“ in „CMakeSettings.json“ synchronisiert, was Ihrem Remotebuildcomputer entspricht. Diese Eigenschaften müssen nicht mehr übereinstimmen, und der Wert von „remoteMachineName“ in „launch.vs.json“ bestimmt, welcher Remotecomputer für Bereitstellung und Debuggen verwendet wird.

![CMake-Remotedebugcomputer](media/cmake-remote-debug-machine.png)

IntelliSense schlägt eine Liste aller eingerichteten Remoteverbindungen vor. Sie können eine neue Remoteverbindung hinzufügen, indem Sie zu **Tools** > **Optionen** > **Plattformübergreifend** > **Verbindungs-Manager** navigieren oder in **Schnellstart** nach „Verbindungs-Manager“ suchen.

Wenn Sie die vollständige Kontrolle über Ihre Bereitstellung wünschen, können Sie die folgenden Codeblöcke an die Datei „launch.vs.json“ anfügen. Denken Sie daran, die Platzhalterwerte durch reale Werte zu ersetzen:

```json

"disableDeploy": false,
"deployDirectory": "~\foo",
"deploy" : [
   {
      "sourceMachine": "127.0.0.1 (username=example1, port=22, authentication=Password)",
      "targetMachine": "192.0.0.1 (username=example2, port=22, authentication=Password)",
      "sourcePath": "~/example.cpp",
      "targetPath": "~/example.cpp",
      "executable": "false"
   }
]

```

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

- Informationen zum Debuggen von ARM-Geräten unter Linux finden Sie im folgenden Blogbeitrag: [Debugging an embedded ARM device in Visual Studio (Debuggen eines eingebetteten ARM-Geräts in Visual Studio)](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Siehe auch

[C++-Debugeigenschaften (Linux C++)](prop-pages/debugging-linux.md)
