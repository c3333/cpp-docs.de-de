---
title: StartTracingSessionA
description: Die Referenz zur StartTracingSessionA-Funktion im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 388ccbe58ab5cc59d995601536a2034e847e2e1d
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920007"
---
# <a name="starttracingsessiona"></a>StartTracingSessionA

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `StartTracingSessionA`-Funktion startet eine Ablaufverfolgungssitzung. Ausführbare Dateien, die diese Funktion aufrufen, benötigen Administratorberechtigungen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StartTracingSessionA(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der Ablaufverfolgungssitzung, die gestartet werden soll. Verwenden Sie den gleichen Namen, wenn Sie [StopTracingSessionA](stop-tracing-session.md) oder eine beliebige andere Funktion zum Anhalten der Ablaufverfolgung aufrufen.

*Optionen*\
Zeiger auf ein [TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md)-Objekt. Wählen Sie mit diesem Objekt aus, welche Ereignisse in der Ablaufverfolgungssitzung gesammelt werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
