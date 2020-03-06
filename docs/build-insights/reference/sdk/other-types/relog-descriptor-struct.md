---
title: RELOG_DESCRIPTOR Struktur
description: Das C++ Build Insights SDK RELOG_DESCRIPTOR Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6f20835ed6535dd05def629200c113772e8f077
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333971"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RELOG_DESCRIPTOR`-Struktur wird mit den Funktionen [reloga](../functions/relog-a.md) und [relogw](../functions/relog-w.md) verwendet. Es wird beschrieben, wie eine Ablauf Verfolgung für die Ereignis Ablauf Verfolgung für Windows (ETW) erneut protokolliert werden soll.

## <a name="syntax"></a>Syntax

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | Die Anzahl von Analyse Durchläufen, die während der Analysephase der erneuten Protokollierung über die ETW-Ablauf Verfolgung durchgeführt werden sollen. |
| `AnalysisCallbacks` | Ein [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) -Objekt, das angibt, welche Funktionen während der Analysephase der erneuten Protokollierung aufgerufen werden. |
| `RelogCallbacks` | Ein [RELOG_CALLBACKS](relog-callbacks-struct.md) -Objekt, das angibt, welche Funktionen während der neuprotokollierungs Phase der erneuten Protokollierung aufgerufen werden. |
| `SystemEventsRetentionFlags` | Eine [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) Bitmaske, die angibt, welche System-ETW-Ereignisse in der protokollierten Ablauf Verfolgung aufbewahrt werden sollen. |
| `AnalysisContext` | Ein vom Benutzer bereitgestellter Kontext, der als Argument an alle in angegebenen Rückruf Funktionen übermittelt wird `AnalysisCallbacks` |
| `RelogContext` | Ein vom Benutzer bereitgestellter Kontext, der als Argument an alle in angegebenen Rückruf Funktionen übermittelt wird `RelogCallbacks` |

## <a name="remarks"></a>Bemerkungen

Die erneute Protokollierung von ETW-Ereignissen während einer erneuten Protokollierungs Sitzung wird vom Benutzer über die in `RelogCallbacks`angegebenen Rückruf Funktionen gesteuert. System-ETW-Ereignisse wie z. b. CPU-Beispiele werden jedoch nicht an diese Rückruf Funktionen weitergeleitet. Verwenden Sie das `SystemEventsRetentionFlags` Feld, um die erneute Protokollierung von etw-System Ereignissen zu steuern.

Die `AnalysisCallbacks`-und `RelogCallbacks` Strukturen akzeptieren nur Zeiger auf Funktionen, die nicht Mitglied sind. Sie können diese Einschränkung umgehen, indem Sie Sie auf einen Objekt Zeiger festlegen. Dieser Objekt Zeiger wird als Argument an alle nicht-Member-Rückruf Funktionen übermittelt. Verwenden Sie diesen Zeiger, um Member-Funktionen innerhalb ihrer nicht-Member-Rückruf Funktionen aufzurufen.

Die Analysephase einer erneuten Protokollierungs Sitzung wird vor der erneuten Protokollierungs Phase immer ausgeführt.

::: moniker-end
