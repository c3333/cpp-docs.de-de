---
title: StartTracingSessionW
description: Die C++ Build Insights SDK StartTracingSessionW-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: af67c3be50cb19ccbfb7fe286e5d61cd1d241bf8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323800"
---
# <a name="starttracingsessionw"></a>StartTracingSessionW

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StartTracingSessionW` Funktion startet eine Ablaufverfolgungssitzung. Ausführbare Dateien, die diese Funktion aufrufen, müssen über Administratorrechte verfügen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StartTracingSessionW(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der zu startenden Ablaufverfolgungssitzung. Verwenden Sie denselben Namen, wenn Sie [StopTracingSessionW](stop-tracing-session-w.md)oder eine andere Stop-Trace-Funktion aufrufen.

*Optionen*\
Zeiger auf ein [TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md) Objekt. Verwenden Sie dieses Objekt, um auszuwählen, welche Ereignisse von der Ablaufverfolgungssitzung erfasst werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) Enumerum.

::: moniker-end
