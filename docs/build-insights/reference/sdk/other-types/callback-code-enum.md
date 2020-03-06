---
title: CALLBACK_CODE-Aufzählung
description: Das C++ Build Insights SDK CALLBACK_CODE-Aufzählungs Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 68eaa9aa04d2f0a55ac12fb7dde14a080188a38d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334091"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE-Aufzählung

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `CALLBACK_CODE`-Aufzählung wird verwendet, um den Fluss einer Analyse-oder neuprotokollierungs Sitzung zu steuern. Geben Sie einen CALLBACK_CODE Wert aus den Funktionen in [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) oder [RELOG_CALLBACKS](relog-callbacks-struct.md) zurück, um zu steuern, was als Nächstes geschehen soll.

## <a name="members"></a>Members

| Name | value | BESCHREIBUNG |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Setzt die aktuelle Analyse oder die erneute Protokollierungs Sitzung normal fort. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Abbrechen der aktuellen Analyse-oder neuprotokollierungs Sitzung und signalisieren eines Fehlers. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Abbrechen der aktuellen Analyse-oder neuprotokollierungs Sitzung. |

::: moniker-end
