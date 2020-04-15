---
title: CALLBACK_CODE Enumerat
description: Das C++ Build Insights SDK CALLBACK_CODE Enumerierungsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0d3dcc70040f562cd40755188e545f709a807b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329192"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE Enumerat

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `CALLBACK_CODE` Enumerierung wird verwendet, um den Fluss einer Analyse- oder Reloggingsitzung zu steuern. Geben Sie einen CALLBACK_CODE Wert aus den Funktionen in [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) oder [RELOG_CALLBACKS](relog-callbacks-struct.md) zurück, um zu steuern, was als nächstes geschehen soll.

## <a name="members"></a>Member

| Name | Wert | BESCHREIBUNG |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Setzen Sie die aktuelle Analyse- oder Neuprotokollierungssitzung normal fort. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Brechen Sie die aktuelle Analyse- oder Reloggingsitzung ab, und signalisieren Sie einen Fehler. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Brechen Sie die aktuelle Analyse- oder Neuprotokollierungssitzung ab. |

::: moniker-end
