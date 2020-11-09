---
title: StartTracingSession
description: Die Referenz zur StartTracingSession-Funktion des C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 07272404aa8bb8cff1221a88497020fedeff315e
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919994"
---
# <a name="starttracingsession"></a>StartTracingSession

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `StartTracingSession`-Funktion startet eine Ablaufverfolgungssitzung. Ausführbare Dateien, die diese Funktion aufrufen, benötigen Administratorberechtigungen.

## <a name="syntax"></a>Syntax

```cpp
RESULT_CODE StartTracingSession(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS& options);

RESULT_CODE StartTracingSession(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS& options);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der zu startenden Ablaufverfolgungssitzung. Verwenden Sie den gleichen Namen, wenn Sie [StopTracingSession](stop-tracing-session.md) oder eine beliebige andere Funktion zum Anhalten der Ablaufverfolgung aufrufen.

*Optionen*\
Zeiger auf ein [TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md)-Objekt. Wählen Sie mit diesem Objekt aus, welche Ereignisse in der Ablaufverfolgungssitzung gesammelt werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
