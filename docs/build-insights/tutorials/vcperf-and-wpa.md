---
title: 'Tutorial: vcperf und Windows Performance Analyzer'
description: Anleitung zur Verwendung von vcperf und WPA zum Analysieren von C++-Buildablaufläufen.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c22f3dfddfd346d4f0eee898cb5164fd8923336e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323414"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Tutorial: vcperf und Windows Performance Analyzer

::: moniker range="<=vs-2017"

Die C++-Build-Insights-Tools sind in Visual Studio 2019 verfügbar. Um die Dokumentation für diese Version **Version** anzuzeigen, legen Sie das Visual Studio Version-Selektor-Steuerelement für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range="vs-2019"

In diesem Tutorial erfahren Sie, wie Sie *mit vcperf.exe* eine Spur Ihres C++-Builds sammeln. Außerdem erfahren Sie, wie Sie diese Ablaufverfolgung in Windows Performance Analyzer anzeigen.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Schritt 1: Installieren und Konfigurieren von Windows Performance Analyzer

WPA ist ein Trace Viewer, der im Windows Assessment and Deployment Kit (ADK) verfügbar ist. Es handelt sich um ein separates Dienstprogramm, das nicht Teil der Komponenten ist, die Sie mit dem Visual Studio-Installationsprogramm installieren können.

Eine Version von WPA, die C++ Build Insights unterstützt, ist derzeit nur in der Windows ADK Insider Preview verfügbar. Um auf diese Vorschau zuzugreifen, müssen Sie sich für das [Windows Insider-Programm](https://insider.windows.com)registrieren. Sie müssen das Betriebssystem Windows 10 Insider Preview nicht installieren, um die Windows ADK-Vorschau zu erhalten. Sie müssen nur Ihr Microsoft-Konto beim Windows-Insider-Programm registrieren.

### <a name="to-download-and-install-wpa"></a>So laden Sie WPA herunter und installieren

HINWEIS: Windows 8 oder höher ist für die Installation des Windows Performance Analyzer erforderlich.

1. Navigieren Sie zur Windows ADK Insider [Preview-Downloadseite](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK).

1. Laden Sie die Windows ADK Insider Preview herunter. Es ist ein Disk-Image.

1. Öffnen Sie das Datenträgerabbild, und führen Sie das Installationsprogramm *adksetup.exe* aus.

1. Wenn Sie zur Eingabe der Features aufgefordert werden, die Sie installieren möchten, wählen Sie das **Windows Performance Toolkit**aus. Sie können andere Funktionen auswählen, wenn Sie möchten, aber sie sind nicht erforderlich, um WPA zu installieren.

   ![Der Featureauswahlbildschirm des Windows Performance Analyzer-Installationsprogramms](media/wpa-installation.png)

### <a name="to-configure-build-insights"></a><a name="configuration-steps"></a>So konfigurieren Sie Build Insights

1. Starten Sie WPA.

1. Fenster **Auswahl Tabellen auswählen (Experimentell)**. **Window** >

1. Scrollen Sie nach unten zum Abschnitt **Diagnose.**

1. Wählen Sie alle MSVC Build Insights-Ansichten aus.

   ![Tabellenauswahlfeld von Windows Performance Analyzer](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Schritt 2: Verfolgen Sie Ihren Build mit vcperf.exe

Um C++ Build Insights-Daten anzuzeigen, sammeln Sie sie zunächst in einer Ablaufverfolgungsdatei, indem Sie die folgenden Schritte ausführen:

1. Öffnen Sie eine systemeigene Tools- oder Cross-Tools-Entwicklereingabeaufforderung für Visual Studio 2019 im Administratormodus. (Klicken Sie mit der rechten Maustaste auf das Menüelement Start und wählen Sie **Mehr** > **als Administrator ausführen**.)

1. Geben Sie im Eingabeaufforderungsfenster diesen Befehl ein:

   **vcperf.exe /Start _SessionName_**

   Wählen Sie einen Sitzungsnamen aus, an den Sie sich für *SessionName*erinnern.

1. Erstellen Sie Ihr Projekt wie gewohnt. Sie müssen nicht dasselbe Eingabeaufforderungsfenster zum Erstellen verwenden.

1. Geben Sie im Eingabeaufforderungsfenster diesen Befehl ein:

   **vcperf.exe /stop _SessionName_ _traceFile.etl_**

   Verwenden Sie denselben Sitzungsnamen, den Sie zuvor für *SessionName* ausgewählt haben. Wählen Sie einen geeigneten Namen für die *TraceFile.etl-Ablaufverfolgungsdatei* aus.

So sieht eine typische Befehlssequenz *von vcperf.exe* in einem Eingabeaufforderungsfenster für Entwickler aus:

![Ein einfaches vcperf.exe-Nutzungsszenario](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Wichtige Hinweise zu vcperf.exe

- Administratorrechte sind erforderlich, um eine *vcperf.exe-Ablaufverfolgung* zu starten oder zu beenden. Verwenden Sie ein Eingabeaufforderungsfenster für Entwickler, das Sie mit **Ausführen als Administrator**öffnen.

- Es kann jeweils nur eine Ablaufverfolgungssitzung auf einem Computer ausgeführt werden.

- Achten Sie darauf, den Sitzungsnamen zu speichern, den Sie zum Starten der Ablaufverfolgung verwendet haben. Es kann lästig sein, eine laufende Sitzung zu beenden, ohne ihren Namen zu kennen.

- Genau wie *cl.exe* und *link.exe*ist das Befehlszeilendienstprogramm *vcperf.exe* in einer MSVC-Installation enthalten. Zum Abrufen dieser Komponente sind keine zusätzlichen Schritte erforderlich.

- *vcperf.exe* sammelt Informationen über alle MSVC-Tools, die auf Ihrem System ausgeführt werden. Daher müssen Sie den Build nicht mit derselben Eingabeaufforderung starten, mit der Sie die Ablaufverfolgung gesammelt haben. Sie können Ihr Projekt entweder über eine andere Eingabeaufforderung oder sogar in Visual Studio erstellen.

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Schritt 3: Anzeigen Ihrer Ablaufverfolgung in Windows Performance Analyzer

Starten Sie WPA und öffnen Sie die Gerade gesammelte Spur. WPA sollte es als C++-Build-Insights-Ablaufverfolgung erkennen, und die folgenden Ansichten sollten im Diagramm-Explorer-Bedienfeld auf der linken Seite angezeigt werden:

- Build Explorer
- Dateien
- Funktion

Wenn diese Ansichten nicht angezeigt werden, überprüfen Sie, ob WPA ordnungsgemäß konfiguriert ist, wie in [Schritt 1](#configuration-steps)beschrieben. Sie können Ihre Builddaten anzeigen, indem Sie die Ansichten in das leere Analysefenster auf der rechten Seite ziehen, wie hier gezeigt:

![Anzeigen einer C++-Build-Insights-Ablaufverfolgung in Windows Performance Analyzer](media/wpa-viewing-trace.gif)

Weitere Ansichten sind im Diagramm-Explorer-Bedienfeld verfügbar. Ziehen Sie sie in das Analysefenster, wenn Sie an den darin enthaltenen Informationen interessiert sind. Eine nützliche ist die CPU-Ansicht (Sampled), die die CPU-Auslastung während des gesamten Builds anzeigt.

## <a name="more-information"></a>Weitere Informationen

[Tutorial: Grundlagen des Windows-Leistungsanalyseprogramms](wpa-basics.md)\
Erfahren Sie mehr über häufige WPA-Vorgänge, mit denen Sie Ihre Buildablaufverfolgungen analysieren können.

[Referenz: vcperf-Befehle](/cpp/build-insights/reference/vcperf-commands)\
Der *Befehlvcperf.exe* listet alle verfügbaren Befehlsoptionen auf.

[Referenz: Windows Performance Analyzer-Ansichten](/cpp/build-insights/reference/wpa-views)\
Weitere Informationen zu den C++-Build-Insights-Ansichten in WPA finden Sie in diesem Artikel.

[Windows-Leistungsanalyse](/windows-hardware/test/wpt/windows-performance-analyzer)\
Die offizielle WPA-Dokumentationsseite.

::: moniker-end
