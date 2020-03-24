---
title: C++Eigenschaften Seiten Debuggen
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 78115a6b-3799-4515-814e-8566b5bdc55d
f1_keywords:
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCLocalDebugPageObject.AmpDefaultAccelerator
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.Environment
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.AmpDefaultAccelerator
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
ms.openlocfilehash: c2190c4406e165cfec1915234b688c598f228777
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169707"
---
# <a name="c-debugging-property-pages"></a>C++Eigenschaften Seiten Debuggen

Diese Eigenschaften Seiten finden Sie unter **Project** > **Properties** > **Configuration Properties** > **Debugging**. Wählen Sie den Debuggertyp im Dropdown-Steuerelement aus. Weitere Informationen zum Debuggen C++ von Code finden Sie [unter Tutorial: Erlernen des Debuggens C++ von Code mit Visual Studio](/visualstudio/debugger/getting-started-with-the-debugger-cpp) und [Debuggen von nativem](/visualstudio/debugger/debugging-native-code)

## <a name="local-windows-debugger-property-page"></a>Lokale Windows-Debugger (Eigenschaften Seite)

### <a name="command"></a>Get-Help

Der auszuführende Debugbefehl.

### <a name="command-arguments"></a>Befehlsargumente

Die Befehlszeilenargumente, die an die Anwendung übergeben werden sollen.

### <a name="working-directory"></a>Arbeitsverzeichnis

Das Arbeitsverzeichnis der Anwendung. Standardmäßig das Verzeichnis, das die Projektdatei enthält.

### <a name="attach"></a>Attach

Gibt an, ob der Debugger beim Starten des Debuggens an einen vorhandenen Prozess angefügt werden soll.

### <a name="debugger-type"></a>Debuggertyp

Gibt den zu verwendenden Debuggertyp an. Wenn die Einstellung auf "Auto" festgelegt ist, wird der Debuggertyp basierend auf dem Inhalt der exe-Datei ausgewählt.

**choices**

- **Nur** System eigen (nur native)
- Nur **verwaltet** : nur verwaltet
- **Gemischt gemischt**
- **Automatisch** automatisch
- **Skript** -Skript
- **Nur GPU (C++ amp)** -nur GPU (C++ amp)

### <a name="environment"></a>Environment

Gibt die Umgebung für das zu debuggende Programm oder Variablen an, die mit der vorhandenen Umgebung zusammengeführt werden sollen.

### <a name="debugging-accelerator-type"></a>Debuggertyp

Der Debuggertyp, der zum Debuggen des GPU-Codes verwendet wird. (Verfügbar, wenn der GPU-Debugger aktiv ist.)

### <a name="gpu-default-breakpoint-behavior"></a>GPU-Standard Haltepunkt Verhalten

Legt fest, wie oft der GPU-Debugger unterbrochen wird.

**choices**

- Einmal pro Warp-Pause pro Warp **Abbrechen**
- **Bei jedem Thread (** z. b. CPU-Verhalten) einen Umbruch Abbrechen (z. b. CPU-Verhalten)

### <a name="merge-environment"></a>Merge-Umgebung

Führen Sie die angegebenen Umgebungsvariablen mit der vorhandenen Umgebung zusammen.

### <a name="sql-debugging"></a>SQL-Debugging

Fügen Sie den SQL-Debugger an.

### <a name="amp-default-accelerator"></a>Amp-Standard-Accelerator

Über C++ schreiben Sie die Standard Zugriffstaste von amp. Die Eigenschaft gilt nicht für das Debuggen von verwaltetem Code.

## <a name="remote-windows-debugger-property-page"></a>Remote-Windows-Debugger (Eigenschaften Seite)

Weitere Informationen zum Remote Debuggen finden Sie unter [Remote Debugging C++ a Visual Project in Visual Studio](/visualstudio/debugger/remote-debugging-cpp).

### <a name="remote-command"></a>Remotebefehl

Der auszuführende Debugbefehl.

### <a name="remote-command-arguments"></a>Remotebefehlsargumente

Die Befehlszeilenargumente, die an die Anwendung übergeben werden sollen.

### <a name="working-directory"></a>Arbeitsverzeichnis

Das Arbeitsverzeichnis der Anwendung. Standardmäßig das Verzeichnis, das die Projektdatei enthält.

### <a name="remote-server-name"></a>Remoteservername

Gibt einen Remote Servernamen an.

### <a name="connection"></a>Verbindung

Gibt den Verbindungstyp an.

**choices**

- **Remote mit Windows-Authentifizierung** : Remote mit [Windows-Authentifizierung](/windows-server/security/windows-authentication/windows-authentication-overview).
- **Remote ohne Authentifizierung** -Remote ohne Authentifizierung.

### <a name="debugger-type"></a>Debuggertyp

Gibt den zu verwendenden Debuggertyp an. Wenn die Einstellung auf "Auto" festgelegt ist, wird der Debuggertyp basierend auf dem Inhalt der exe-Datei ausgewählt.

**choices**

- **Nur** System eigen (nur native)
- Nur **verwaltet** : nur verwaltet
- **Gemischt gemischt**
- **Automatisch** automatisch
- **Skript** -Skript
- **Nur GPU (C++ amp)** -nur GPU (C++ amp)

### <a name="environment"></a>Environment

Gibt die Umgebung für das zu debuggende Programm oder Variablen an, die mit der vorhandenen Umgebung zusammengeführt werden sollen.

### <a name="debugging-accelerator-type"></a>Debuggertyp

Der Debuggertyp, der zum Debuggen des GPU-Codes verwendet wird. (Verfügbar, wenn der GPU-Debugger aktiv ist.)

### <a name="gpu-default-breakpoint-behavior"></a>GPU-Standard Haltepunkt Verhalten

Legt fest, wie oft der GPU-Debugger unterbrochen wird.

**choices**

- Einmal pro Warp-Pause pro Warp **Abbrechen**
- **Bei jedem Thread (** z. b. CPU-Verhalten) einen Umbruch Abbrechen (z. b. CPU-Verhalten)

### <a name="attach"></a>Attach

Gibt an, ob der Debugger beim Starten des Debuggens an einen vorhandenen Prozess angefügt werden soll.

### <a name="sql-debugging"></a>SQL-Debugging

Fügen Sie den SQL-Debugger an.

### <a name="deployment-directory"></a>Bereitstellungsverzeichnis

Wenn Sie auf einem Remote Computer debuggen möchten, dass der Inhalt der Projekt Ausgabe (mit Ausnahme der PDB-Dateien) auf den Remote Computer kopiert werden soll, geben Sie hier den Pfad an.

### <a name="additional-files-to-deploy"></a>Zusätzliche bereitzustellende Dateien

Beim Debuggen auf einem Remote Computer werden die hier angegebenen Dateien und Verzeichnisse (neben der Projekt Ausgabe) in das Bereitstellungs Verzeichnis kopiert, sofern ein solcher angegeben wurde.

### <a name="deploy-visual-c-debug-runtime-libraries"></a>Bereitstellen von Visual C++-Debugging-Laufzeitbibliotheken

Gibt an, ob die Debug-Laufzeitbibliotheken für die aktive Plattform (Win32, x64 oder Arm) bereitgestellt werden sollen.

### <a name="amp-default-accelerator"></a>Amp-Standard-Accelerator

Über C++ schreiben Sie die Standard Zugriffstaste von amp. Die Eigenschaft gilt nicht für das Debuggen von verwaltetem Code.

## <a name="web-browser-debugger-property-page"></a>Eigenschaften Seite des Webbrowser Debuggers

### <a name="http-url"></a>HTTP-URL

Gibt die URL für das Projekt an.

### <a name="debugger-type"></a>Debuggertyp

Gibt den zu verwendenden Debuggertyp an. Wenn die Einstellung auf "Auto" festgelegt ist, wird der Debuggertyp basierend auf dem Inhalt der exe-Datei ausgewählt.

**choices**

- **Nur** System eigen (nur native)
- Nur **verwaltet** : nur verwaltet
- **Gemischt gemischt**
- **Automatisch** automatisch
- **Skript** -Skript

## <a name="web-service-debugger-property-page"></a>Eigenschaften Seite "Webdienst Debugger"

### <a name="http-url"></a>HTTP-URL

Gibt die URL für das Projekt an.

### <a name="debugger-type"></a>Debuggertyp

Gibt den zu verwendenden Debuggertyp an. Wenn die Einstellung auf "Auto" festgelegt ist, wird der Debuggertyp basierend auf dem Inhalt der exe-Datei ausgewählt.

**choices**

- **Nur** System eigen (nur native)
- Nur **verwaltet** : nur verwaltet
- **Gemischt gemischt**
- **Automatisch** automatisch
- **Skript** -Skript

### <a name="sql-debugging"></a>SQL-Debugging

Fügen Sie den SQL-Debugger an.
