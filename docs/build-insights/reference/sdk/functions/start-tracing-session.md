---
title: Starttracingsession
description: Die C++ buildinsights-SDK-starttracingsession-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: de9d46b4a684d66bf01f76e7ea753694cf40d2cd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334223"
---
# <a name="starttracingsession"></a>Starttracingsession

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StartTracingSession`-Funktion startet eine Ablauf Verfolgungs Sitzung. Ausführbare Dateien, die diese Funktion aufrufen, müssen über Administratorrechte verfügen.

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

*Sessionname* -\
Der Name der Ablauf Verfolgungs Sitzung, die gestartet werden soll. Verwenden Sie den gleichen Namen, wenn Sie [stoptracingsession](stop-tracing-session.md) oder eine beliebige andere Stop-Ablauf Verfolgungs Funktion aufrufen.

*Optionen*\
Zeiger auf ein [TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md) Objekt. Verwenden Sie dieses Objekt, um auszuwählen, welche Ereignisse von der Ablauf Verfolgungs Sitzung gesammelt werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

::: moniker-end
