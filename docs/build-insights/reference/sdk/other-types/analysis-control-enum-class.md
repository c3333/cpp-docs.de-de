---
title: AnalysisControl-Enumerationsklasse
description: Der AnalysisControl-Enumerationsverweis des C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0f4887d626c5e80a0afaa393e255f8ffedbd6b1f
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922619"
---
# <a name="analysiscontrol-enum-class"></a>AnalysisControl-Enumerationsklasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Mit der `AnalysisControl`-Enumerationsklasse wird der Fluss einer Analysesitzung oder Neuprotokollierungssitzung gesteuert. Durch Rückgabe eines `AnalysisControl`-Codes von einer [IAnalyzer](ianalyzer-class.md)- oder [IRelogger](irelogger-class.md)-Memberfunktion wird gesteuert, was als Nächstes geschehen sollte.

## <a name="members"></a>Members

| name | BESCHREIBUNG |
|--|--|
| `BLOCK` | Verhindert, dass das aktuelle Ereignis in der Analyzer- oder Reloggergruppe weitergegeben wird. |
| `CANCEL` | Abbrechen der aktuellen Analyse- oder Neuprotokollierungssitzung. |
| `CONTINUE` | Normale Fortsetzung der aktuellen Analyse- oder Neuprotokollierungssitzung. Weitergeben des aktuellen Ereignisses an den nächsten Analyzer- oder Reloggergruppenmember. |
| `FAILURE` | Abbrechen der aktuellen Analyse- oder Neuprotokollierungssitzung und Signalisieren eines Fehlers. |

::: moniker-end
