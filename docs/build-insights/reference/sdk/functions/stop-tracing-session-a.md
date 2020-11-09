---
title: StopTracingSessionA
description: Die Referenz zur StopTracingSessionA-Funktion des C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 211538c1756d41b91dab6d43f33f4b4a41ceb70c
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922645"
---
# <a name="stoptracingsessiona"></a>StopTracingSessionA

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `StopTracingSessionA`-Funktion beendet eine laufende Ablaufverfolgungssitzung und generiert eine Ablaufverfolgungsdatei mit Rohdaten. Ablaufverfolgungsdateien mit Rohdaten können an die Funktionen [Analyze](analyze.md), [AnalzeA](analyze-a.md) und [AnalyzeW](analyze-w.md) übergeben werden, um eine Analysesitzung zu starten. Ablaufverfolgungsdateien mit Rohdaten können an die Funktionen [Relog](relog.md), [RelogA](relog-a.md) und [RelogW](relog-w.md) übergeben werden, um eine Neuprotokollierungssitzung zu starten. Ausführbare Dateien, die `StopTracingSessionA` aufrufen, benötigen Administratorberechtigungen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StopTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der anzuhaltenden Ablaufverfolgungssitzung. Verwenden Sie den gleichen Sitzungsnamen wie den, der an [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md) oder [StartTracingSessionW](start-tracing-session-w.md) übergeben wurde.

*outputLogFile*\
Pfad zur endgültigen Ausgabeprotokolldatei, in der die Rohdaten der Ablaufverfolgung gespeichert werden sollen.

*statistics*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)-Objekt. `StopTracingSessionA` schreibt Sammlungsstatistiken zur Ablaufverfolgung in dieses Objekt, bevor es zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
