---
title: Enumeration CALLBACK_CODE
description: Die Referenz zur Enumeration CALLBACK_CODE im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146d191d0b642ad538f5a314016b41fdbdf26113
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922599"
---
# <a name="callback_code-enum"></a>Enumeration CALLBACK_CODE

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Mit der Enumeration `CALLBACK_CODE` wird der Fluss einer Analyse- oder Neuprotokollierungssitzung gesteuert. Geben Sie einen Wert für CALLBACK_CODE aus den Funktionen in [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) oder [RELOG_CALLBACKS](relog-callbacks-struct.md) zurück, um zu steuern, was als Nächstes geschehen soll.

## <a name="members"></a>Member

| name | Wert | Beschreibung |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Normale Fortsetzung der aktuellen Analyse- oder Neuprotokollierungssitzung. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Abbrechen der aktuellen Analyse- oder Neuprotokollierungssitzung und Signalisieren eines Fehlers. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Abbrechen der aktuellen Analyse- oder Neuprotokollierungssitzung. |

::: moniker-end
