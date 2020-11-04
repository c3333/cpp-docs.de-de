---
title: ANALYSIS_DESCRIPTOR-Struktur
description: Der Verweis auf die ANALYSIS_DESCRIPTOR-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ec2d0a76618d6ff2cf0e7fdff7e360a4fd2e0174
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919851"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR-Struktur

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `ANALYSIS_DESCRIPTOR`-Struktur wird mit der [AnalyzeA](../functions/analyze-a.md)- und [AnalyzeW](../functions/analyze-w.md)-Funktion verwendet. Es wird beschrieben, wie eine Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW) analysiert werden sollte.

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

| name | BESCHREIBUNG |
|--|--|
| `NumberOfPasses` | Die Anzahl der Analysedurchläufe, die über die ETW-Ablaufverfolgung durchgeführt werden sollten. |
| `Callbacks` | Ein [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)-Objekt, das angibt, welche Funktionen während der Analysesitzung aufgerufen werden sollen. |
| `Context` | Ein vom Benutzer bereitgestellter Kontext, der als Argument an alle in `Callbacks` angegebenen Rückruffunktionen übermittelt wird. |

## <a name="remarks"></a>Bemerkungen

Die `Callbacks`-Struktur akzeptiert nur Zeiger auf Funktionen, die nicht Member sind. Sie können diese Einschränkung umgehen, indem Sie `Context` auf einen Objektzeiger festlegen. Dieser Objektzeiger wird als Argument an alle Rückruffunktionen übermittelt, die nicht Member sind. Rufen Sie mit diesem Zeiger Memberfunktionen von den Rückruffunktionen aus auf, die nicht Member sind.

::: moniker-end
