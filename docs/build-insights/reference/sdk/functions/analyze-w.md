---
title: AnalyzeW
description: Die Referenz zur AnalyzeW-Funktion des C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a75668e0fc9d356315f5f0b3156a909187415521
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922861"
---
# <a name="analyzew"></a>AnalyzeW

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `AnalyzeW`-Funktion dient zum Analysieren von MSVC-Ereignissen, die aus ETW-Ablaufverfolgung (Event Trace for Windows, Ereignisablaufverfolgung für Windows) gelesen werden.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE AnalyzeW(
    const wchar_t*             inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Parameter

*inputLogFile*\
Die Eingabe-ETW-Ablaufverfolgung, aus der Ereignisse gelesen werden sollen.

*analysisDescriptor*\
Zeiger auf ein [ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)-Objekt. Konfigurieren Sie mit diesem Objekt die Analyse.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
