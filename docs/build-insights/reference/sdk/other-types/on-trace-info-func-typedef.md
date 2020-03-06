---
title: Ontraceinfofunc-typedef
description: Die C++ Referenz zum Build Insights SDK ontraceinfofunc typedef.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b168d6783b31454f6a2837bcad1fc81199ce9054
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333989"
---
# <a name="ontraceinfofunc-typedef"></a>Ontraceinfofunc-typedef

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Der `OnTraceInfoFunc`-TypeDef ist eine der Funktions Signaturen, die in den [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) -und [RELOG_CALLBACKS](relog-callbacks-struct.md) -Strukturen verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parameter

*traceingefo* -\
Ein [TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md) -Objekt, das Informationen über die zurzeit analysierte oder erneut protokollierte Ablauf Verfolgung enthält.

*callbackcontext* -\
Der Kontextwert, der für diesen Rückruf in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md)festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ein [CALLBACK_CODE](callback-code-enum.md) Wert, der steuert, was als Nächstes geschehen soll.

::: moniker-end
