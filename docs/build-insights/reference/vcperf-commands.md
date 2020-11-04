---
title: 'Referenz: vcperf-Befehle'
description: Referenz für das Befehlszeilen-Hilfsprogramm „vcperf.exe“.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 42ca422e11824bdbdad4e42e7b55950317095703
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922204"
---
# <a name="reference-vcperf-commands"></a>Referenz: vcperf-Befehle

::: moniker range="<=msvc-150"

Die C++ Build Insights-Tools sind in Visual Studio 2019 verfügbar. Wenn die Dokumentation für diese Version angezeigt werden soll, legen Sie das Steuerelement zur Auswahl der **Version** für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range="msvc-160"

In diesem Artikel werden die in *vcperf.exe* verfügbaren Befehle aufgelistet und beschrieben sowie deren Verwendung erläutert.

## <a name="commands-to-start-and-stop-traces"></a>Befehle zum Starten und Beenden von Ablaufverfolgungen

*WICHTIG: Alle folgenden Befehle erfordern Administratorrechte*.

| Option           | Argumente und Beschreibung |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Weist *vcperf.exe* an, eine Ablaufverfolgung unter dem angegebenen Sitzungsnamen zu starten. Es kann auf jedem Computer nur jeweils eine aktive Sitzung geben. <br/><br/> Wenn die Option `/nocpusampling` angegeben ist, erfasst *vcperf.exe* keine CPU-Stichproben. Der Befehl verhindert die Verwendung der Ansicht „CPU-Auslastung (Stichproben)“ in Windows Performance Analyzer, verkleinert aber die gesammelten Ablaufverfolgungen. <br/><br/> Sobald die Ablaufverfolgung gestartet wurde, gibt *vcperf.exe* sofort Ergebnisse zurück. Ereignisse werden systemweit für alle Prozesse gesammelt, die auf dem Computer ausgeführt werden. Das bedeutet, dass Sie Ihr Projekt nicht über dieselbe Eingabeaufforderung erstellen müssen, die Sie zum Ausführen von *vcperf.exe* verwendet haben. Sie können Ihr Projekt beispielsweise in Visual Studio erstellen. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Beendet die Ablaufverfolgung, die durch den angegebenen Sitzungsnamen identifiziert wird. Führt einen Nachverarbeitungsschritt in der Ablaufverfolgung aus, um eine Datei zu generieren, die in Windows Performance Analyzer (WPA) angezeigt werden kann. Zur optimalen Anzeige der Ergebnisse verwenden Sie eine WPA-Version, die das Add-In „C++ Build Insights“ enthält. Weitere Informationen finden Sie unter [Erste Schritte mit C++ Build Insights](../get-started-with-cpp-build-insights.md). Der Parameter `<outputFile.etl>` gibt an, wo die Ausgabedatei gespeichert wird. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Beendet die Ablaufverfolgung, die durch den angegebenen Sitzungsnamen identifiziert wird, und schreibt die nicht verarbeiteten Rohdaten in die angegebene Ausgabedatei. Die resultierende Datei ist für die Anzeige in WPA nicht geeignet. <br/><br/> Der im Befehl `/stop` integrierte Nachverarbeitungsschritt kann u. U. sehr lange dauern. Sie können den Befehl `/stopnoanalyze` verwenden, um diesen Schritt zu verschieben. Verwenden Sie den Befehl `/analyze`, wenn Sie bereit sind, eine Datei zu erzeugen, die in Windows Performance Analyzer angezeigt werden kann. |

## <a name="miscellaneous-commands"></a>Verschiedene Befehle

| Option     | Argumente und Beschreibung |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Akzeptiert eine unformatierte Ablaufverfolgungsdatei, die vom Befehl `/stopnoanalyze` erzeugt wird. Führt einen Nachverarbeitungsschritt in dieser Ablaufverfolgung aus, um eine Datei zu generieren, die in Windows Performance Analyzer angezeigt werden kann. Zur optimalen Anzeige der Ergebnisse verwenden Sie eine WPA-Version, die das Add-In „C++ Build Insights“ enthält. Weitere Informationen finden Sie unter [Erste Schritte mit C++ Build Insights](../get-started-with-cpp-build-insights.md). |

## <a name="see-also"></a>Siehe auch

[Erste Schritte mit C++ Build Insights](../get-started-with-cpp-build-insights.md)\
[Tutorial: Windows Performance Analyzer-Grundlagen](../tutorials/wpa-basics.md)\
[Referenz: Windows Performance Analyzer-Ansichten](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
