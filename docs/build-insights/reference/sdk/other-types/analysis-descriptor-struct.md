---
title: ANALYSIS_DESCRIPTOR Struktur
description: Das C++ Build Insights SDK ANALYSIS_DESCRIPTOR Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1de7f2a5bc3f02a327daaecf8c2cebc44687ba43
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323615"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `ANALYSIS_DESCRIPTOR` Struktur wird mit den [AnalyzeA-](../functions/analyze-a.md) und [AnalyzeW-Funktionen](../functions/analyze-w.md) verwendet. Es wird beschrieben, wie eine Ereignisablaufverfolgung für Windows (ETW) verfolgt werden soll.

## <a name="syntax"></a>Syntax

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `NumberOfPasses` | Die Anzahl der Analysedurchläufe, die über die ETW-Ablaufverfolgung durchgeführt werden sollen. |
| `Callbacks` | Ein [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) Objekt, das angibt, welche Funktionen während der Analysesitzung aufzurufen sind. |
| `Context` | Ein vom Benutzer bereitgestellter Kontext, der als Argument an alle in`Callbacks` |

## <a name="remarks"></a>Bemerkungen

Die `Callbacks` Struktur akzeptiert nur Zeiger auf Nicht-Memberfunktionen. Sie können diese Einschränkung `Context` umgehen, indem Sie einen Objektzeiger festlegen. Dieser Objektzeiger wird als Argument an alle Nicht-Member-Rückruffunktionen übergeben. Verwenden Sie diesen Zeiger, um Memberfunktionen innerhalb Ihrer Rückruffunktionen ohne Mitglieder aufzurufen.

::: moniker-end
