---
title: StopAndRelogTracingSessionA
description: Die Referenz zur StopAndRelogTracingSessionA-Funktion im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: de69ca379c6f0ef46e23d2b4a78c72518e997572
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919968"
---
# <a name="stopandrelogtracingsessiona"></a>StopAndRelogTracingSessionA

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `StopAndRelogTracingSessionA`-Funktion beendet eine laufende Ablaufverfolgungssitzung und speichert die resultierende Ablaufverfolgung in einer temporären Datei. Eine Neuprotokollierungssitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Die durch die Neuprotokollierung erzeugte endgültige Ablaufverfolgung wird in einer vom Aufrufer angegebenen Datei gespeichert. Ausführbare Dateien, die diese Funktion aufrufen, benötigen Administratorberechtigungen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der anzuhaltenden Ablaufverfolgungssitzung. Verwenden Sie den gleichen Sitzungsnamen wie den, der an [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md) oder [StartTracingSessionW](start-tracing-session-w.md) übergeben wurde.

*outputLogFile*\
Die Datei, in die die neu protokollierte Ablaufverfolgung geschrieben werden soll, die von der Neuprotokollierungssitzung generiert wurde.

*statistics*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)-Objekt. `StopAndRelogTracingSessionA` schreibt Sammlungsstatistiken zur Ablaufverfolgung in dieses Objekt, bevor es zurückgegeben wird.

*analysisDescriptor*\
Zeiger auf ein [RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)-Objekt. Konfigurieren Sie mit diesem Objekt die Neuprotokollierungssitzung, die mit `StopAndRelogTracingSessionA` gestartet wurde.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
