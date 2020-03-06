---
title: Injetevent
description: Die C++ Funktionsreferenz für den Build Insights SDK-injetevent.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7b53eb71cf7a2ae40d04dbc3f8b5829f2737aba4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334415"
---
# <a name="injectevent"></a>Injetevent

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `InjectEvent`-Funktion wird in einer der reloggersitzung aufgerufen, die die [irelogger](../other-types/irelogger-class.md) -Schnittstelle implementiert. Es wird verwendet, um ein ETW-Ereignis (Event Tracing for Windows, Ereignis Ablauf Verfolgung für Windows) in der Ausgabedatei der Ablauf Verfolgung einer erneuten Protokollierungs Sitzung zu

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

\ " *relogsession* "
Ein Zeiger auf die relogging-Sitzung. Es wird eine Sitzung für erneute Protokollierung bereitgestellt, die die `IRelogger`-Schnittstelle implementiert. Weitere Informationen finden Sie unter [irelogger](../other-types/irelogger-class.md).

*ProviderID* -\
Eine Anbieter-GUID für die Ereignis Ablauf Verfolgung für Windows (ETW), unter der das ETW-Ereignis erneut protokolliert wird.

*EventDescriptor* -\
Der ETW-Ereignis Deskriptor für das erneut protokollierte ETW-Ereignis.

\ *ProcessID*
Die Prozess-ID (PID) für das ETW-Ereignis, das erneut protokolliert wird.

*ThreadId*\
Der Thread Bezeichner (TID) für das ETW-Ereignis, das erneut protokolliert wird.

*processorindex* -\
Der Prozessor Index für das ETW-Ereignis, das erneut protokolliert wird.

*Zeitstempel*\
Der Zeitstempel für das erneut protokollierte ETW-Ereignis.

*Daten*\
Ein Zeiger auf die Daten, die in das erneut protokollierte ETW-Ereignis eingeschlossen werden sollen.

*byteCount* -\
Die Größe der Daten in Bytes, auf die durch *Daten*verwiesen wird.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu etw-Konzepten, z. b. *Anbieter-GUID* und *Ereignis Deskriptor*, finden Sie in der [etw-Dokumentation](/windows/win32/etw/about-event-tracing). Ausführliche Informationen zum Starten einer relogging-Sitzung mit dem C++ Build Insights SDK finden Sie unter [relog](relog.md).

::: moniker-end
