---
title: RELOG_CALLBACKS Struktur
description: Das C++ Build Insights SDK RELOG_CALLBACKS Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5dbed196e6cafaa301b6e07cd0f5546a0f4d563
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333983"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RELOG_CALLBACKS`-Struktur wird verwendet, wenn ein [RELOG_DESCRIPTOR](relog-descriptor-struct.md) Objekt initialisiert wird. Gibt an, welche Funktionen während der erneuten Protokollierung einer Ereignis Ablauf Verfolgung für Windows (ETW)-Ablauf Verfolgung aufgerufen werden.

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `OnStartActivity` | Wird aufgerufen, um ein Aktivitäts Start Ereignis zu verarbeiten. |
| `OnStopActivity` | Wird aufgerufen, um ein Aktivitäts beenden-Ereignis zu verarbeiten. |
| `OnSimpleEvent` | Wird aufgerufen, um ein einfaches Ereignis zu verarbeiten. |
| `OnTraceInfo` | Wird einmal am Anfang der erneuten Protokollierung aufgerufen, nachdem `OnBeginReloggingPass` aufgerufen wurde. |
| `OnBeginRelogging` | Wird aufgerufen, wenn eine relogging-Sitzung gestartet wird, bevor der neuprotokollierungs Durchlauf begonnen hat. |
| `OnEndRelogging` | Wird aufgerufen, wenn eine relogging-Sitzung beendet wird, nachdem die erneute Protokollierung abgeschlossen wurde. |
| `OnBeginReloggingPass` | Wird aufgerufen, wenn der neuprotokollierungs Durchlauf vor der Verarbeitung eines Ereignisses gestartet wird. |
| `OnEndReloggingPass` | Wird aufgerufen, wenn die erneute Protokollierung beendet wird, nachdem alle Ereignisse verarbeitet wurden. |

## <a name="remarks"></a>Bemerkungen

Alle Elemente der `RELOG_CALLBACKS` Struktur müssen auf eine gültige Funktion verweisen. Weitere Informationen zu den akzeptierten Funktions Signaturen finden Sie unter [onrelogeventfunc](on-relog-event-func-typedef.md), [ontraceinfofunc](on-trace-info-func-typedef.md)und [onbeginendpassfunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
