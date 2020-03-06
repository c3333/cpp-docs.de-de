---
title: EVENT_COLLECTION_DATA Struktur
description: Das C++ Build Insights SDK EVENT_COLLECTION_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1a622a8459b6aa6d9dcbe0faaf90ae545b449466
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335243"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EVENT_COLLECTION_DATA`-Struktur beschreibt ein Array von [EVENT_DATA](event-data-struct.md) Elementen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Count` | Die Anzahl der `EVENT_DATA` Elemente im Array. |
| `Elements` | Zeiger auf das erste `EVENT_DATA` Element im Array. |

::: moniker-end
