---
title: RELOG_DESCRIPTOR Struktur
description: Das C++ Build Insights SDK RELOG_DESCRIPTOR Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c3aee49fe9f609ca37082693ddcfd5e838cc96a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328938"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RELOG_DESCRIPTOR` Struktur wird mit den Funktionen [RelogA](../functions/relog-a.md) und [RelogW](../functions/relog-w.md) verwendet. Es wird beschrieben, wie eine Ereignisablaufverfolgung für Windows (ETW) neu protokolliert werden soll.

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

## <a name="members"></a>Member

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | Die Anzahl der Analysedurchläufe, die während der Analysephase der Relogging-Sitzung über die ETW-Ablaufverfolgung durchgeführt werden sollen. |
| `AnalysisCallbacks` | Ein [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) Objekt, das angibt, welche Funktionen während der Analysephase der Relogging-Sitzung aufzurufen sind. |
| `RelogCallbacks` | Ein [RELOG_CALLBACKS](relog-callbacks-struct.md) Objekt, das angibt, welche Funktionen während der Relogging-Phase der Relogging-Sitzung aufzurufen sind. |
| `SystemEventsRetentionFlags` | Eine [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) Bitmaske an, die angibt, welche System-ETW-Ereignisse in der erneut protokollierten Ablaufverfolgung beibehalten werden sollen. |
| `AnalysisContext` | Ein vom Benutzer bereitgestellter Kontext, der als Argument an alle in`AnalysisCallbacks` |
| `RelogContext` | Ein vom Benutzer bereitgestellter Kontext, der als Argument an alle in`RelogCallbacks` |

## <a name="remarks"></a>Bemerkungen

Das Erneute Protokollieren von ETW-Ereignissen während einer Relogging-Sitzung `RelogCallbacks`wird vom Benutzer über die in angegebenen Rückruffunktionen gesteuert. System-ETW-Ereignisse wie CPU-Beispiele werden jedoch nicht an diese Rückruffunktionen weitergeleitet. Verwenden `SystemEventsRetentionFlags` Sie das Feld, um die Neuprotokollierung von System-ETW-Ereignissen zu steuern.

Die `AnalysisCallbacks` `RelogCallbacks` und Strukturen akzeptieren nur Zeiger auf Nicht-Member-Funktionen. Sie können diese Einschränkung umgehen, indem Sie sie auf einen Objektzeiger festlegen. Dieser Objektzeiger wird als Argument an alle Nicht-Member-Rückruffunktionen übergeben. Verwenden Sie diesen Zeiger, um Memberfunktionen innerhalb Ihrer Rückruffunktionen ohne Mitglieder aufzurufen.

Die Analysephase einer Relogging-Sitzung wird immer vor der Relogging-Phase ausgeführt.

::: moniker-end
