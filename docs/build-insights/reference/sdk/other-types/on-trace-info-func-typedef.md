---
title: OnTraceInfoFunc-TypeDef
description: Die Referenz zur OnTraceInfoFunc-TypeDef im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4aaa865fd0f907a67179e7ee967f23a9827b0026
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922470"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc-TypeDef

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `OnTraceInfoFunc`-TypeDef ist eine der Funktionssignaturen, die in der [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)- und [RELOG_CALLBACKS](relog-callbacks-struct.md)-Struktur verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parameter

*traceInfo*\
Ein [TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md)-Objekt, das Informationen über die momentan analysierte oder neu protokollierte Ablaufverfolgung enthält.

*callbackContext*\
Der Kontextwert, der für diesen Rückruf in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md) festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ein [CALLBACK_CODE](callback-code-enum.md)-Wert, der steuert, was als Nächstes geschehen soll.

::: moniker-end
