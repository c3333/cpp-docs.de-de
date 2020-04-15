---
title: StopAndRelogTracingSessionW
description: Die C++ Build Insights SDK StopAndRelogTracingSessionW-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c542ba8f313f30cf5adb069dd02cf3db29ffc532
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323690"
---
# <a name="stopandrelogtracingsessionw"></a>StopAndRelogTracingSessionW

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StopAndRelogTracingSessionW` Funktion beendet eine fortlaufende Ablaufverfolgungssitzung und speichert die resultierende Ablaufverfolgung in einer temporären Datei. Eine Relogging-Sitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Die letzte erneut protokollierte Ablaufverfolgung, die von der Relogging-Sitzung erzeugt wird, wird in einer vom Aufrufer angegebenen Datei gespeichert. Ausführbare Dateien, die diese Funktion aufrufen, müssen über Administratorrechte verfügen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StopAndRelogTracingSessionW(
    const wchar_t*              sessionName,
    const wchar_t*              outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der zu beendenden Ablaufverfolgungssitzung. Verwenden Sie denselben Sitzungsnamen wie an [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)oder [StartTracingSessionW](start-tracing-session-w.md)übergeben.

*outputLogFile*\
Die Datei, in die die erneut etologierte Ablaufverfolgung geschrieben werden soll, die von der Relogging-Sitzung erzeugt wurde.

*Statistiken*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) Objekt. `StopAndRelogTracingSessionW`schreibt Ablaufverfolgungssammlungsstatistiken in diesem Objekt, bevor es zurückgegeben wird.

*analyseDescriptor*\
Zeiger auf ein [RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) Objekt. Verwenden Sie dieses Objekt, um die Vonlogksitzung zu konfigurieren, die von `StopAndRelogTracingSessionW`gestartet wird.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) Enumerum.

::: moniker-end
