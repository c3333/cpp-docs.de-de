---
title: Typedef „OnRelogEventFunc“
description: Referenz zur Typedef „OnRelogEventFunc“ im C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ed639ab59b900f97d29dc69240e45b2f52f2f3b3
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919747"
---
# <a name="onrelogeventfunc-typedef"></a>Typedef „OnRelogEventFunc“

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Typedef `OnRelogEventFunc` ist eine der Funktionssignaturen, die in der [RELOG_CALLBACKS](relog-callbacks-struct.md)-Struktur verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für das aktuelle Ereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

*relogSession*\
Der Zeiger auf die Reloggingsitzung, der beim Aufruf von [InjectEvent](../functions/inject-event.md) verwendet werden soll.

*callbackContext*\
Der Kontextwert, der für diesen Rückruf in [RELOG_DESCRIPTOR](analysis-descriptor-struct.md) festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ein [CALLBACK_CODE](callback-code-enum.md)-Wert, der steuert, was als Nächstes geschehen soll.

::: moniker-end
