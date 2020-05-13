---
title: AnalysisControl-Enumerumklasse
description: Die C++ Build Insights SDK AnalysisControl-Enumerierungsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e9431f878390127f2cefbe8f0ee42ca509e147de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323639"
---
# <a name="analysiscontrol-enum-class"></a>AnalysisControl-Enumerumklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `AnalysisControl` Enumerierungsklasse wird verwendet, um den Fluss einer Analyse- oder Reloggingsitzung zu steuern. Geben `AnalysisControl` Sie einen Code von einer [IAnalyzer-](ianalyzer-class.md) oder [IRelogger-Memberfunktion](irelogger-class.md) zurück, um zu steuern, was als nächstes geschehen soll.

## <a name="members"></a>Member

|  |  |
|--|--|
| `BLOCK` | Verhindert, dass sich das aktuelle Ereignis in der Analyse- oder Reloggergruppe weiter ausbreitet. |
| `CANCEL` | Brechen Sie die aktuelle Analyse- oder Neuprotokollierungssitzung ab. |
| `CONTINUE` | Setzen Sie die aktuelle Analyse- oder Neuprotokollierungssitzung normal fort. Verteilen Sie das aktuelle Ereignis an das nächste Mitglied der Analyse oder der Neuprotokollierungsgruppe. |
| `FAILURE` | Brechen Sie die aktuelle Analyse- oder Reloggingsitzung ab, und signalisieren Sie einen Fehler. |

::: moniker-end
