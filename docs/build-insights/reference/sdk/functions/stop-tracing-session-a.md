---
title: StopTracingSessionA
description: Die C++ Build Insights SDK StopTracingSessionA-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 15560ecf4959ccda0d617c09d3645750210f331a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323504"
---
# <a name="stoptracingsessiona"></a>StopTracingSessionA

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StopTracingSessionA` Funktion beendet eine fortlaufende Ablaufverfolgungssitzung und erzeugt eine unformatierte Ablaufverfolgungsdatei. Raw-Ablaufverfolgungsdateien können an die Funktionen [Analyze](analyze.md), [AnalzeA](analyze-a.md)und [AnalyzeW](analyze-w.md) übergeben werden, um eine Analysesitzung zu starten. Raw-Ablaufverfolgungsdateien können auch an die [Funktionen Relog](relog.md), [RelogA](relog-a.md)und [RelogW](relog-w.md) übergeben werden, um die Relogging-Sitzung zu starten. Der Aufruf `StopTracingSessionA` von ausführbaren Dateien muss über Administratorrechte verfügen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StopTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der zu beendenden Ablaufverfolgungssitzung. Verwenden Sie denselben Sitzungsnamen wie an [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)oder [StartTracingSessionW](start-tracing-session-w.md)übergeben.

*outputLogFile*\
Pfad zur endgültigen Ausgabeprotokolldatei, in der die unformatierte Ablaufverfolgung gespeichert werden soll.

*Statistiken*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) Objekt. `StopTracingSessionA`schreibt Ablaufverfolgungssammlungsstatistiken in diesem Objekt, bevor es zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) Enumerum.

::: moniker-end
