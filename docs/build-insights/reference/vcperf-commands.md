---
title: 'Referenz: vcperf-Befehle'
description: Referenz für das Befehlszeilendienstprogramm vcperf.exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9d3b0a9dbdfe922dc87f91006441e1f65d54c8a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323252"
---
# <a name="reference-vcperf-commands"></a>Referenz: vcperf-Befehle

::: moniker range="<=vs-2017"

Die C++-Build-Insights-Tools sind in Visual Studio 2019 verfügbar. Um die Dokumentation für diese Version **Version** anzuzeigen, legen Sie das Visual Studio Version-Selektor-Steuerelement für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range="vs-2019"

In diesem Artikel werden die in *vcperf.exe*verfügbaren Befehle und deren Verwendung aufgeführt und beschrieben.

## <a name="commands-to-start-and-stop-traces"></a>Befehle zum Starten und Stoppen von Ablaufverfolgungen

*WICHTIG: Die folgenden Befehle erfordern alle Administratorrechte.*

| Option           | Argumente und Beschreibung |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Weist *vcperf.exe* an, eine Ablaufverfolgung unter dem angegebenen Sitzungsnamen zu starten. Es kann jeweils nur eine aktive Sitzung auf einem bestimmten Computer geben. <br/><br/> Wenn `/nocpusampling` die Option angegeben ist, sammelt *vcperf.exe* keine CPU-Beispiele. Es verhindert die Verwendung der CPU-Auslastungsansicht (Sampled) in Windows Performance Analyzer, macht aber die gesammelten Ablaufverfolgungen kleiner. <br/><br/> Sobald die Ablaufverfolgung gestartet wird, kehrt *vcperf.exe* sofort zurück. Ereignisse werden systemweit für alle prozesse gesammelt, die auf der Maschine ausgeführt werden. Das bedeutet, dass Sie Ihr Projekt nicht mit derselben Eingabeaufforderung erstellen müssen, die Sie zum Ausführen von *vcperf.exe*verwendet haben. Sie können Ihr Projekt beispielsweise aus Visual Studio erstellen. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Beendet die Ablaufverfolgung, die durch den angegebenen Sitzungsnamen identifiziert wird. Führt einen Nachbearbeitungsschritt für die Ablaufverfolgung aus, um eine Datei zu generieren, die in Windows Performance Analyzer (WPA) angezeigt werden kann. Verwenden Sie eine Version von WPA, die das C++Build Insights-Add-In enthält, um ein optimales Anzeigeerlebnis zu erhalten. Weitere Informationen finden Sie unter [Erste Schritte mit C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). Der `<outputFile.etl>` Parameter gibt an, wo die Ausgabedatei gespeichert werden soll. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Beendet die durch den angegebenen Sitzungsnamen identifizierte Ablaufverfolgung und schreibt die unverarbeiteten rohen Daten in die angegebene Ausgabedatei. Die resultierende Datei ist nicht dazu gedacht, in WPA angezeigt zu werden. <br/><br/> Der `/stop` AmBefehl beteiligte Nachbearbeitungsschritt kann manchmal langwierig sein. Sie können `/stopnoanalyze` den Befehl verwenden, um diesen Nachbearbeitungsschritt zu verzögern. Verwenden `/analyze` Sie den Befehl, wenn Sie bereit sind, eine Datei zu erstellen, die in Windows Performance Analyzer angezeigt werden kann. |

## <a name="miscellaneous-commands"></a>Verschiedene Befehle

| Option     | Argumente und Beschreibung |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Akzeptiert eine unformatierte `/stopnoanalyze` Ablaufverfolgungsdatei, die vom Befehl erstellt wurde. Führt einen Nachbearbeitungsschritt für diese Ablaufverfolgung aus, um eine Datei zu generieren, die in Windows Performance Analyzer angezeigt werden kann. Verwenden Sie eine Version von WPA, die das C++Build Insights-Add-In enthält, um ein optimales Anzeigeerlebnis zu erhalten. Weitere Informationen finden Sie unter [Erste Schritte mit C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Siehe auch

[Erste Schritte mit C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Tutorial: Grundlagen des Windows-Leistungsanalyseprogramms](/cpp/build-insights/tutorials/wpa-basics)\
[Referenz: Windows Performance Analyzer-Ansichten](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
