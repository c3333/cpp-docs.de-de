---
title: Onrelogeventfunc-typedef
description: Die C++ onrelogeventfunc-typedef-Referenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 619f9a142ad19a7809b867eda93f2db634825a8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334025"
---
# <a name="onrelogeventfunc-typedef"></a>Onrelogeventfunc-typedef

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `OnRelogEventFunc` TypeDef ist eine der Funktions Signaturen, die in der [RELOG_CALLBACKS](relog-callbacks-struct.md) Struktur verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parameter

*Event Stack* -\
Der Ereignis Stapel für das aktuelle Ereignis. Weitere Informationen zu Ereignis Stapeln finden Sie unter [Ereignisse](../event-table.md).

\ " *relogsession* "
Der zum Aufrufen des [injetevent](../functions/inject-event.md)zu verwendende relogging-Sitzungs Zeiger.

*callbackcontext* -\
Der Kontextwert, der in [RELOG_DESCRIPTOR](analysis-descriptor-struct.md)für diesen Rückruf festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ein [CALLBACK_CODE](callback-code-enum.md) Wert, der steuert, was als Nächstes geschehen soll.

::: moniker-end
