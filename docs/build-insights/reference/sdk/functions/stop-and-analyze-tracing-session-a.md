---
title: StopAndAnalyzeTracingSessionA
description: Die Referenz zur StopAndAnalyzeTracingSessionA-Funktion im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fa5adfca2c5e4d3d4bd17abae4e78c2ac6464773
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922728"
---
# <a name="stopandanalyzetracingsessiona"></a>StopAndAnalyzeTracingSessionA

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `StopAndAnalyzeTracingSessionA`-Funktion beendet eine laufende Ablaufverfolgungssitzung und speichert die resultierende Ablaufverfolgung in einer temporären Datei. Eine Analysesitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Ausführbare Dateien, die diese Funktion aufrufen, benötigen Administratorberechtigungen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StopAndAnalyzeTracingSessionA(
    const char*                 sessionName,
    TRACING_SESSION_STATISTICS* statistics,
    const ANALYSIS_DESCRIPTOR*  analysisDescriptor);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der anzuhaltenden Ablaufverfolgungssitzung. Verwenden Sie den gleichen Sitzungsnamen wie den, der an [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md) oder [StartTracingSessionW](start-tracing-session-w.md) übergeben wurde.

*statistics*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)-Objekt. `StopAndAnalyzeTracingSessionA` schreibt Sammlungsstatistiken zur Ablaufverfolgung in dieses Objekt, bevor es zurückgegeben wird.

*analysisDescriptor*\
Zeiger auf ein [ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)-Objekt. Konfigurieren Sie mit diesem Objekt die Analysesitzung, die mit `StopAndAnalyzeTracingSessionA` gestartet wurde.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
