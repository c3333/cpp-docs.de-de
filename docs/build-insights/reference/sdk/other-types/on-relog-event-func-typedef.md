---
title: OnRelogEventFunc typdef
description: Der C++Build Insights SDK OnRelogEventFunc typdef-Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2df8646d530c089b1239978d716b2b619a5b4b61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329071"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc typdef

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `OnRelogEventFunc` typedef ist eine der Funktionssignaturen, die in der [RELOG_CALLBACKS-Struktur](relog-callbacks-struct.md) verwendet werden.

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
Der beim Aufrufen des [InjectEvent](../functions/inject-event.md)zu verwendende Sitzungszeiger für das erneute Protokollieren.

*callbackContext*\
Der Kontextwert, der für diesen Rückruf in [RELOG_DESCRIPTOR](analysis-descriptor-struct.md)festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ein [CALLBACK_CODE](callback-code-enum.md) Wert, der steuert, was als nächstes geschehen soll.

::: moniker-end
