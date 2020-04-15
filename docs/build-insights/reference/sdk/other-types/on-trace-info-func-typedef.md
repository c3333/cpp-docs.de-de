---
title: OnTraceInfoFunc typdef
description: Der C++ Build Insights SDK OnTraceInfoFunc typedef-Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b987d4db9852c2e52c148bb91015ad414c04d41b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329021"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc typdef

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `OnTraceInfoFunc` typedef ist eine der Funktionssignaturen, die in den [ANALYSIS_CALLBACKS-](analysis-callbacks-struct.md) und [RELOG_CALLBACKS-Strukturen](relog-callbacks-struct.md) verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parameter

*traceInfo*\
Ein [TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md) Objekt, das Informationen über die Ablaufverfolgung enthält, die derzeit analysiert oder erneut protokolliert wird.

*callbackContext*\
Der Kontextwert, der für diesen Rückruf in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md)festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ein [CALLBACK_CODE](callback-code-enum.md) Wert, der steuert, was als nächstes geschehen soll.

::: moniker-end
