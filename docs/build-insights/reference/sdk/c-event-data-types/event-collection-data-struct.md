---
title: EVENT_COLLECTION_DATA-Struktur
description: Der Verweis auf die EVENT_COLLECTION_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 58be46d31af154bfe7ecef5c440092eaafdcbb0f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039598"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA-Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EVENT_COLLECTION_DATA`-Struktur beschreibt ein Array von [EVENT_DATA](event-data-struct.md)-Elementen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `Count` | Die Anzahl der `EVENT_DATA`-Elemente im Array. |
| `Elements` | Zeiger auf das erste `EVENT_DATA`-Element im Array. |

::: moniker-end
