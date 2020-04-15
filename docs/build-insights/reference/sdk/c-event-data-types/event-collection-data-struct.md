---
title: EVENT_COLLECTION_DATA Struktur
description: Das C++ Build Insights SDK EVENT_COLLECTION_DATA Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 88ba39ede8c86f47c2e6458332ae005eddc06fda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325692"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EVENT_COLLECTION_DATA` Struktur beschreibt ein Array von [EVENT_DATA](event-data-struct.md) Elementen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `Count` | Die Anzahl `EVENT_DATA` der Elemente im Array. |
| `Elements` | Zeiger auf das `EVENT_DATA` erste Element im Array. |

::: moniker-end
