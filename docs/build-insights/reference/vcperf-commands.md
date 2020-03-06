---
title: 'Referenz: vcperf-Befehle'
description: Referenz für das Befehlszeilen-Hilfsprogramm "vcperf. exe".
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b85320ce4517eb41410c59a11bd79553405b8402
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333881"
---
# <a name="reference-vcperf-commands"></a>Referenz: vcperf-Befehle

::: moniker range="<=vs-2017"

Die C++ Build Insights-Tools sind in Visual Studio 2019 verfügbar. Um die Dokumentation für diese Version anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2019 fest.

::: moniker-end
::: moniker range="vs-2019"

In diesem Artikel werden die in " *vcperf. exe*" verfügbaren Befehle aufgelistet und beschrieben und erläutert, wie Sie verwendet werden.

## <a name="commands-to-start-and-stop-traces"></a>Befehle zum Starten und Abbrechen von Ablauf Verfolgungen

*Wichtig: die folgenden Befehle erfordern alle Administratorrechte.*

| Option           | Argumente und Beschreibung |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Weist *vcperf. exe* an, eine Ablauf Verfolgung unter dem angegebenen Namen der Sitzung zu starten. Auf einem bestimmten Computer kann jeweils nur eine aktive Sitzung vorhanden sein. <br/><br/> Wenn die `/nocpusampling`-Option angegeben ist, sammelt *vcperf. exe* keine CPU-Stichproben. Die Verwendung der Ansicht CPU-Auslastung (Sampling) in Windows Performance Analyzer wird verhindert, aber die gesammelten Ablauf Verfolgungen werden kleiner. <br/><br/> Nachdem die Ablauf Verfolgung gestartet wurde, wird " *vcperf. exe* " sofort zurückgegeben. Ereignisse werden für alle Prozesse, die auf dem Computer ausgeführt werden, systemweit gesammelt. Dies bedeutet, dass Sie das Projekt nicht von derselben Eingabeaufforderung aus erstellen müssen wie die, die Sie zum Ausführen von " *vcperf. exe*" verwendet haben. Beispielsweise können Sie Ihr Projekt aus Visual Studio erstellen. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Beendet die Ablauf Verfolgung, die durch den angegebenen Sitzungs Namen identifiziert wird. Führt einen nach Verarbeitungsschritt für die Ablauf Verfolgung aus, um eine Datei zu generieren, die in Windows Performance Analyzer (WPA) angezeigt werden kann. Um die beste Ansicht zu erhalten, verwenden Sie eine WPA-Version, C++ die das Add-in "Build Insights" enthält. Weitere Informationen finden Sie unter [Get Started with C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). Der `<outputFile.etl>`-Parameter gibt an, wo die Ausgabedatei gespeichert werden soll. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Beendet die durch den angegebenen Sitzungs Namen identifizierte Ablauf Verfolgung und schreibt die unverarbeiteten Rohdaten in die angegebene Ausgabedatei. Die resultierende Datei soll nicht in WPA angezeigt werden. <br/><br/> Der nach Verarbeitungsschritt, der am `/stop` Befehl beteiligt ist, kann manchmal sehr lange dauern. Sie können den `/stopnoanalyze`-Befehl verwenden, um diesen Schritt nach der Verarbeitung zu verzögern. Verwenden Sie den `/analyze` Befehl, wenn Sie bereit sind, eine Datei in Windows Performance Analyzer anzuzeigen. |

## <a name="miscellaneous-commands"></a>Verschiedene Befehle

| Option     | Argumente und Beschreibung |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Akzeptiert eine unformatierte Ablauf Verfolgungs Datei, die vom `/stopnoanalyze` Befehl erzeugt wird. Führt einen nach Verarbeitungsschritt für diese Ablauf Verfolgung aus, um eine Datei zu generieren, die in Windows Performance Analyzer angezeigt werden kann. Um die beste Ansicht zu erhalten, verwenden Sie eine WPA-Version, C++ die das Add-in "Build Insights" enthält. Weitere Informationen finden Sie unter [Get Started with C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Weitere Informationen

[Machen Sie sich C++ mit den Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights) -\
[Tutorial: Grundlagen zu Windows Performance Analyzer](/cpp/build-insights/tutorials/wpa-basics)\
[Referenz: Windows Performance Analyzer-Ansichten](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
