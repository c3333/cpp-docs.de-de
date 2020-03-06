---
title: Onanalysipedefunc-typedef
description: Die C++ Referenz zum Build Insights SDK onanalysipedefunc-typedef.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d260f6060e759f315589abda82e31c2c2b95a65e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334061"
---
# <a name="onanalysiseventfunc-typedef"></a>Onanalysipedefunc-typedef

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `OnAnalysisEventFunc` TypeDef ist eine der Funktions Signaturen, die in der [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) Struktur verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parameter

*Event Stack* -\
Der Ereignis Stapel für das aktuelle Ereignis. Weitere Informationen zu Ereignis Stapeln finden Sie unter [Ereignisse](../event-table.md).

*callbackcontext* -\
Der Kontextwert, der für diesen Rückruf in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md)festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ein [CALLBACK_CODE](callback-code-enum.md) Wert, der steuert, was als Nächstes geschehen soll.

::: moniker-end
