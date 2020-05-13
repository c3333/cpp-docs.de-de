---
title: InjectEvent
description: Die C++ Build Insights SDK InjectEvent-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c82aad5923eff60e5c72ceccaa39aa136f942665
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324039"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `InjectEvent` Funktion wird innerhalb eines Reloggers aufgerufen, der die [IRelogger-Schnittstelle](../other-types/irelogger-class.md) implementiert. Es wird verwendet, um ein ETW-Ereignis (Event Tracing for Windows) in die Ausgabeablaufverfolgungsdatei einer Relogging-Sitzung zu schreiben.

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
Ein Zeiger auf die Relogging-Sitzung. Eine Relogging-Sitzung wird für Relogger `IRelogger` bereitgestellt, die die Schnittstelle implementieren. Weitere Informationen finden Sie unter [IRelogger](../other-types/irelogger-class.md).

*ProviderId*\
Eine Ereignisablaufverfolgung für Windows (ETW)-Anbieter-GUID, unter der das ETW-Ereignis erneut protokolliert wird.

*Eventdescriptor*\
Der ETW-Ereignisdeskriptor für das ETW-Ereignis, das erneut protokolliert wurde.

*Processid*\
Der Prozessbezeichner (PID) für das ETW-Ereignis, das erneut protokolliert wurde.

*Threadid*\
Der Threadbezeichner (TID) für das ETW-Ereignis, das erneut protokolliert wird.

*prozessorIndex*\
Der Prozessorindex für das ETW-Ereignis, das erneut protokolliert wurde.

*Timestamp*\
Der Zeitstempel für das ETW-Ereignis, das erneut protokolliert wurde.

*Daten*\
Ein Zeiger auf die Daten, die in das erneut protokollierte ETW-Ereignis eingeschlossen werden sollen.

*Bytecount*\
Die Größe der Daten in Bytes, auf die durch *Daten*verwiesen wird.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu ETW-Konzepten, z. *B. Provider-GUID* und *Ereignisdeskriptor,* finden Sie in der [ETW-Dokumentation](/windows/win32/etw/about-event-tracing). Weitere Informationen zum Starten einer Relogging-Sitzung mit dem C++ Build Insights SDK finden Sie unter [Relog](relog.md).

::: moniker-end
