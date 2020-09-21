---
title: RELOG_CALLBACKS-Struktur
description: Der Verweis auf die RELOG_CALLBACKS-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 55f63b05691e3d729ee42ed21049669b94053559
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041431"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS-Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RELOG_CALLBACKS`-Struktur wird beim Initialisieren eines [RELOG_DESCRIPTOR](relog-descriptor-struct.md)-Objekts verwendet. Sie gibt an, welche Funktionen während der erneuten Protokollierung einer Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW) aufgerufen werden.

## <a name="syntax"></a>Syntax

```cpp
typedef struct RELOG_CALLBACKS_TAG
{
    OnRelogEventFunc        OnStartActivity;
    OnRelogEventFunc        OnStopActivity;
    OnRelogEventFunc        OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginRelogging;
    OnBeginEndPassFunc      OnEndRelogging;
    OnBeginEndPassFunc      OnBeginReloggingPass;
    OnBeginEndPassFunc      OnEndReloggingPass;
} RELOG_CALLBACKS;
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `OnStartActivity` | Wird aufgerufen, um ein Aktivitätsstartereignis zu verarbeiten. |
| `OnStopActivity` | Wird aufgerufen, um ein Aktivitätsstoppereignis zu verarbeiten. |
| `OnSimpleEvent` | Wird aufgerufen, um ein einfaches Ereignis zu verarbeiten. |
| `OnTraceInfo` | Wird einmal am Anfang des erneuten Protokollierungsdurchlaufs aufgerufen, nachdem `OnBeginReloggingPass` aufgerufen wurde. |
| `OnBeginRelogging` | Wird aufgerufen, wenn eine erneute Protokollierungssitzung gestartet wird, bevor der erneute Protokollierungsdurchlauf begonnen hat. |
| `OnEndRelogging` | Wird aufgerufen, wenn eine erneute Protokollierungssitzung beendet wird, bevor der erneute Protokollierungsdurchlauf geendet hat. |
| `OnBeginReloggingPass` | Wird aufgerufen, wenn der erneute Protokollierungsdurchlauf vor der Verarbeitung eines Ereignisses gestartet wird. |
| `OnEndReloggingPass` | Wird aufgerufen, wenn der erneute Protokollierungsdurchlauf nach der Verarbeitung aller Ereignisse beendet wird. |

## <a name="remarks"></a>Bemerkungen

Alle Member der `RELOG_CALLBACKS`-Struktur müssen auf eine gültige Funktion verweisen. Weitere Informationen zu den akzeptierten Funktionssignaturen finden Sie unter [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md) und [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
