---
title: Typedef „OnAnalysisEventFunc“
description: Referenz zur Typedef „OnAnalysisEventFunc“ im C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 069c89a01fa466e86986a821e5dd9d0b09f5c81a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919786"
---
# <a name="onanalysiseventfunc-typedef"></a>Typedef „OnAnalysisEventFunc“

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Typedef `OnAnalysisEventFunc` ist eine der Funktionssignaturen, die in der [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)-Struktur verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für das aktuelle Ereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

*callbackContext*\
Der Kontextwert, der für diesen Rückruf in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md) festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ein [CALLBACK_CODE](callback-code-enum.md)-Wert, der steuert, was als Nächstes geschehen soll.

::: moniker-end
