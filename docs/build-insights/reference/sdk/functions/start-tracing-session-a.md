---
title: Starttracingsessiona
description: Die C++ Funktionsreferenz für das Build Insights SDK starttracingsessiona.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6c5069a2b521472ee4fd06ee313a66de5d7aa814
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334271"
---
# <a name="starttracingsessiona"></a>Starttracingsessiona

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StartTracingSessionA`-Funktion startet eine Ablauf Verfolgungs Sitzung. Ausführbare Dateien, die diese Funktion aufrufen, müssen über Administratorrechte verfügen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StartTracingSessionA(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>Parameter

*Sessionname* -\
Der Name der Ablauf Verfolgungs Sitzung, die gestartet werden soll. Verwenden Sie den gleichen Namen, wenn Sie [stoptracingsessiona](stop-tracing-session.md) oder eine beliebige andere Stop-Ablauf Verfolgungs Funktion aufrufen.

*Optionen*\
Zeiger auf ein [TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md) Objekt. Verwenden Sie dieses Objekt, um auszuwählen, welche Ereignisse von der Ablauf Verfolgungs Sitzung gesammelt werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

::: moniker-end
