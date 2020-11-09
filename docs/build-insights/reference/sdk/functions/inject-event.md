---
title: InjectEvent
description: Die Referenz zur InjectEvent-Funktion im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b4d85f17a6d553d9dffa727824e6d4de94518645
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922837"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `InjectEvent`-Funktion wird innerhalb eines Reloggers aufgerufen, der die [IRelogger](../other-types/irelogger-class.md)-Schnittstelle implementiert. Sie dient zum Schreiben eines ETW-Ereignisses (Ereignisablaufverfolgung für Windows) in eine Ausgabe-Ablaufverfolgungsdatei einer Neuprotokollierungssitzung.

## <a name="syntax"></a>Syntax

```cpp
void InjectEvent(
    const void* relogSession,
    LPCGUID providerId,
    PCEVENT_DESCRIPTOR eventDescriptor,
    unsigned long processId,
    unsigned long threadId,
    unsigned short processorIndex,
    long long timestamp,
    unsigned char* data,
    unsigned long byteCount);
```

### <a name="parameters"></a>Parameter

*relogSession*\
Ein Zeiger auf die Neuprotokollierungssitzung. Eine Neuprotokollierungssitzung wird Reloggern bereitgestellt, die die `IRelogger`-Schnittstelle implementieren. Weitere Informationen finden Sie unter [IRelogger](../other-types/irelogger-class.md).

*providerId*\
Die GUID eines ETW-Anbieters (Event Tracing for Windows, Ereignisablaufverfolgung für Windows), unter der das ETW-Ereignis neu protokolliert wird.

*eventDescriptor*\
Der ETW-Ereignisdeskriptor für das neu protokollierte ETW-Ereignis.

*processId*\
Die Prozess-ID (PID) des ETW-Ereignisses, das neu protokolliert wird.

*threadId*\
Die Thread-ID (TID) des ETW-Ereignisses, das neu protokolliert wird.

*processorIndex*\
Der Prozessorindex des ETW-Ereignisses, das neu protokolliert wird.

*timestamp*\
Der Zeitstempel des ETW-Ereignisses, das neu protokolliert wird.

*data*\
Ein Zeiger auf die Daten, die in das neu protokollierte ETW-Ereignis eingeschlossen werden sollen.

*byteCount*\
Die Größe der Daten in Bytes, auf die durch *data* gezeigt wird.

## <a name="remarks"></a>Hinweise

Weitere Informationen zu ETW-Konzepten, z. B. *Anbieter-GUID* und *Ereignisdeskriptor* , finden Sie in der [ETW-Dokumentation](/windows/win32/etw/about-event-tracing). Ausführliche Informationen zum Starten einer Neuprotokollierungssitzung mit dem C++ Build Insights SDK finden Sie unter [Relog](relog.md).

::: moniker-end
