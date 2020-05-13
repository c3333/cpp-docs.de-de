---
title: RELOG_CALLBACKS Struktur
description: Das C++ Build Insights SDK RELOG_CALLBACKS Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 60e7db81a48731090a23b82332704a79a51e97df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328973"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RELOG_CALLBACKS` Struktur wird beim Initialisieren eines [RELOG_DESCRIPTOR](relog-descriptor-struct.md) Objekts verwendet. Es gibt an, welche Funktionen während des Reloggings einer ETW-Ablaufverfolgung (Event Tracing for Windows) aufzurufen sind.

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

|  |  |
|--|--|
| `OnStartActivity` | Wird aufgerufen, um ein Aktivitätsstartereignis zu verarbeiten. |
| `OnStopActivity` | Wird aufgerufen, um ein Aktivitätsstoppereignis zu verarbeiten. |
| `OnSimpleEvent` | Wird aufgerufen, um ein einfaches Ereignis zu verarbeiten. |
| `OnTraceInfo` | Einmal zu Beginn des Relogging-Passes `OnBeginReloggingPass` aufgerufen, nachdem aufgerufen wurde. |
| `OnBeginRelogging` | Wird aufgerufen, wenn eine Relogging-Sitzung beginnt, bevor der Relogging-Pass begonnen hat. |
| `OnEndRelogging` | Wird aufgerufen, wenn eine Relogging-Sitzung beendet wird, nachdem der Relogging-Pass beendet wurde. |
| `OnBeginReloggingPass` | Wird aufgerufen, wenn der Relogging-Durchlauf beginnt, bevor ein Ereignis verarbeitet wird. |
| `OnEndReloggingPass` | Wird aufgerufen, wenn der Relogging-Durchlauf beendet wird, nachdem alle Ereignisse verarbeitet wurden. |

## <a name="remarks"></a>Bemerkungen

Alle Elemente `RELOG_CALLBACKS` der Struktur müssen auf eine gültige Funktion verweisen. Weitere Informationen zu den akzeptierten Funktionssignaturen finden Sie unter [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)und [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
