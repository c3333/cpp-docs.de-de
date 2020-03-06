---
title: Analysiscontrol-Enumerationsklasse
description: Der C++ Build Insights SDK analysiscontrol-Aufzählungs Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cf162c11e0a7109b8d733dab79df80782398e14d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334121"
---
# <a name="analysiscontrol-enum-class"></a>Analysiscontrol-Enumerationsklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `AnalysisControl`-Enumerationsklasse wird verwendet, um den Fluss einer Analyse-oder neuprotokollierungs Sitzung zu steuern. Zurückgeben eines `AnalysisControl` Codes von einer [ianalyzer](ianalyzer-class.md) -oder [irelogger](irelogger-class.md) -Member-Funktion, um zu steuern, was als Nächstes geschehen soll.

## <a name="members"></a>Members

|  |  |
|--|--|
| `BLOCK` | Verhindert, dass das aktuelle Ereignis in der Analyzer-oder der reloggersitzung-Gruppe weitergegeben wird. |
| `CANCEL` | Abbrechen der aktuellen Analyse-oder neuprotokollierungs Sitzung. |
| `CONTINUE` | Setzt die aktuelle Analyse oder die erneute Protokollierungs Sitzung normal fort. Gibt das aktuelle Ereignis an das nächste Analyzer-oder der reloggersitzung-Gruppenmitglied weiter. |
| `FAILURE` | Abbrechen der aktuellen Analyse-oder neuprotokollierungs Sitzung und signalisieren eines Fehlers. |

::: moniker-end
