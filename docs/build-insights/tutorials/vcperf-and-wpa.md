---
title: 'Tutorial: vcperf und Windows Performance Analyzer'
description: Tutorial zur Verwendung von vcperf und WPA für die Analyse von Ablaufverfolgungen für C++-Builds.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b82c1f7105b3fd03d8c21dd79617dbc66f3e090c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507774"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Tutorial: vcperf und Windows Performance Analyzer

::: moniker range="<=vs-2017"

Die C++ Build Insights-Tools sind in Visual Studio 2019 verfügbar. Wenn die Dokumentation für diese Version angezeigt werden soll, legen Sie das Steuerelement zur Auswahl der **Version** für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range="vs-2019"

In diesem Tutorial erfahren Sie, wie Sie *vcperf.exe* zum Erfassen einer Ablaufverfolgung Ihres C++-Builds verwenden. Außerdem erfahren Sie, wie Sie diese Ablaufverfolgung in Windows Performance Analyzer anzeigen.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Schritt 1: Installieren und Konfigurieren von Windows Performance Analyzer

WPA ist ein Trace Viewer, der im Windows Assessment and Deployment Kit (ADK) verfügbar ist. Es handelt sich um ein separates Hilfsprogramm, das nicht Teil der Komponenten ist, die Sie mit dem Visual Studio-Installer installieren können.

Eine WPA-Version, die C++ Build Insights unterstützt, ist aktuell nur in der Windows ADK Insider Preview verfügbar. Um auf dieses Vorschauversion zuzugreifen, müssen Sie sich für das [Windows-Insider-Programm](https://insider.windows.com) registrieren. Eine Installation des Windows 10 Insider Preview-Betriebssystem ist für den Zugriff auf die Windows ADK-Vorschau nicht erforderlich. Sie müssen Ihr Microsoft-Konto lediglich für das Windows-Insider-Programm registrieren.

### <a name="to-download-and-install-wpa"></a>Herunterladen und Installieren von WPA

HINWEIS: Zum Installieren von Windows Performance Analyzer ist Windows 8 oder höher erforderlich.

1. Navigieren Sie zur [Downloadseite](/windows-hardware/get-started/adk-install) des Windows ADK.

1. Laden Sie die aktuelle Version des Windows ADK herunter, und installieren Sie sie.

1. Wenn Sie zur Angabe der Features aufgefordert werden, die installiert werden sollen, wählen Sie das **Windows Performance Toolkit** aus. Sie können auch weitere Features auswählen, diese sind für die Installation von WPA jedoch nicht erforderlich.

   ![Der Bildschirm zur Featureauswahl des Windows Performance Analyzer-Installers](media/wpa-installation.png)

### <a name="to-configure-wpa"></a><a name="configuration-steps"></a> Konfigurieren von WPA

Zum Anzeigen von C++ Build Insights-Ablaufverfolgungen in WPA ist ein spezielles Add-In erforderlich. Führen Sie folgende Schritte aus, um es zu installieren:

1. Rufen Sie das Add-In ab, indem Sie eine der unten aufgeführten Komponenten herunterladen. Sie benötigen nur eine der beiden Komponenten. Wählen Sie die für Sie am besten geeignete Komponente aus.
    1. [Visual Studio 2019 Version 16.6 und höher](https://visualstudio.microsoft.com/downloads/) oder das
    1. [C++ Build Insights NuGet-Paket](https://www.nuget.org/packages/Microsoft.Cpp.BuildInsights/).

1. Kopieren Sie die Datei `perf_msvcbuildinsights.dll` in Ihr WPA-Installationsverzeichnis.
    1. In Visual Studio 2019 Version 16.6 und höher befindet sich diese Datei hier: `C:\Program Files (x86)\Microsoft Visual Studio\2019\{Edition}\VC\Tools\MSVC\{Version}\bin\Host{Architecture}\{Architecture}`.
    1. Im C++ Build Insights NuGet-Paket befindet sich die Datei hier: `wpa\{Architecture}`.
    1. Ersetzen Sie in den Pfaden oben die Variablen in geschweiften Klammern wie folgt:
        1. `{Edition}` ist Ihre Visual Studio 2019-Edition (z. B. Community, Professional oder Enterprise).
        1. `{Version}` ist Ihre MSVC-Version. Wählen Sie die höchste verfügbare Version aus.
        1. `{Architecture}`: Wählen Sie `x64`, wenn Sie eine 64-Bit-Version von Windows ausführen. Anderenfalls wählen Sie `x86` aus.
    1. Das WPA-Installationsverzeichnis ist üblicherweise: `C:\Program Files (x86)\Windows Kits\10\Windows Performance Toolkit`.

1. Öffnen Sie in Ihrem WPA-Installationsverzeichnis die Datei `perfcore.ini`, und fügen Sie einen Eintrag für `perf_msvcbuildinsights.dll`hinzu.

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Schritt 2: Überwachen Ihres Builds mit vcperf.exe

Um C++ Build Insights-Daten anzuzeigen, müssen diese zunächst in einer Ablaufverfolgungsdatei erfasst werden. Führen Sie dazu folgende Schritte aus:

1. Öffnen Sie eine **x64** oder **x86 Native Tools-Eingabeaufforderung für VS 2019** im Administratormodus. (Klicken Sie mit der rechten Maustaste auf „Start“, und wählen Sie **Mehr** > **Als Administrator ausführen** aus.)
    1. Wählen Sie **x64**, wenn Sie eine 64-Bit-Version von Windows ausführen. Anderenfalls wählen Sie **x86** aus.

1. Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:

   **vcperf.exe /start _Sitzungsname_**

   Wählen Sie für *Sitzungsname* einen Namen aus, den Sie sich gut merken können.

1. Erstellen Sie das Projekt wie gewohnt. Sie müssen dazu nicht dasselbe Eingabeaufforderungsfenster verwenden.

1. Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:

   **vcperf.exe /stop _Sitzungsname_ _ablaufverfolgungsdatei.etl_**

   Verwenden Sie für *Sitzungsname* denselben Namen wie oben. Wählen Sie einen geeigneten Namen für die Ablaufverfolgungsdatei *ablaufverfolgungsdatei.etl*.

Nachfolgend ist eine typische *vcperf.exe*-Befehlssequenz in einem Developer-Eingabeaufforderungsfenster gezeigt:

![Ein einfaches Verwendungsszenario für vcperf.exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Wichtige Hinweise zu vcperf.exe

- Zum Starten oder Anhalten einer *vcperf.exe*-Ablaufverfolgung sind Administratorrechte erforderlich. Verwenden Sie **Als Administrator ausführen**, um ein Developer-Eingabeaufforderungsfenster zu öffnen.

- Auf einem Computer kann jeweils nur eine Ablaufverfolgungssitzung ausgeführt werden.

- Merken Sie sich den Sitzungsnamen, den Sie zum Starten Ihrer Ablaufverfolgung verwendet haben. Es kann schwierig sein, eine laufende Sitzung anzuhalten, wenn Sie den Namen nicht mehr wissen.

- Das Befehlszeilenprogramm *vcperf.exe* ist wie *cl.exe* und *link.exe* in einer MSVC-Installation enthalten. Es sind keine weiteren Schritte erforderlich, um diese Komponente abzurufen.

- *vcperf.exe* erfasst Informationen zu allen MSVC-Tools, die auf Ihrem System ausgeführt werden. Sie müssen Ihren Build daher nicht über dieselbe Eingabeaufforderung starten, die Sie zum Erfassen der Ablaufverfolgung verwendet haben. Sie können Ihr Projekt entweder über eine andere Eingabeaufforderung oder sogar in Visual Studio erstellen.

### <a name="vcperfexe-is-open-source"></a>vcperf.exe ist eine Open-Source-Komponente

Wenn Sie eine eigene Version von *vcperf.exe* erstellen und ausführen möchten, können Sie sie aus dem [vcperf-GitHub-Repository](https://github.com/microsoft/vcperf) klonen.

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Schritt 3: Anzeigen Ihrer Ablaufverfolgung in Windows Performance Analyzer

Starten Sie WPA, und öffnen Sie die Ablaufverfolgung, die Sie soeben erstellt haben. WPA sollte die Ablaufverfolgung als C++ Build Insights-Ablaufverfolgung erkennen, und im Fenster des Graph-Explorers auf der linken Seite sollten die folgenden Ansichten geöffnet werden:

- Build-Explorer
- Dateien
- Funktionen
- Vorlageninstanziierungen

Wenn diese Ansichten nicht angezeigt werden, überprüfen Sie, ob WPA ordnungsgemäß konfiguriert ist (siehe [Schritt 1](#configuration-steps)). Sie können Ihre Builddaten anzeigen, indem Sie die Ansichten in das leere Analysefenster auf der rechten Seite ziehen, wie hier gezeigt:

![Anzeigen einer C++ Build Insights-Ablaufverfolgung in Windows Performance Analyzer](media/wpa-viewing-trace.gif)

Im Graph-Explorer-Fenster sind weitere Ansichten verfügbar. Ziehen Sie diese in das Analysefenster, wenn Sie an den darin enthaltenen Informationen interessiert sind. Eine nützliche Ansicht ist die CPU-Ansicht (mit Stichprobendaten), die die CPU-Auslastung innerhalb Ihres Builds zeigt.

## <a name="more-information"></a>Weitere Informationen

[Tutorial: Windows Performance Analyzer-Grundlagen](wpa-basics.md)\
Erfahren Sie mehr über häufige WPA-Vorgänge, mit denen Sie Ablaufverfolgungen Ihrer Builds analysieren können.

[Referenz: vcperf-Befehle](../reference/vcperf-commands.md)\
In der *vcperf.exe-* -Befehlsreferenz sind alle verfügbaren Befehlsoptionen aufgeführt.

[Referenz: Windows Performance Analyzer-Ansichten](../reference/wpa-views.md)\
In diesem Artikel finden Sie ausführliche Informationen zu den C++ Build Insights-Ansichten in WPA.

[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)\
Die offizielle WPA-Dokumentationswebsite.

::: moniker-end
