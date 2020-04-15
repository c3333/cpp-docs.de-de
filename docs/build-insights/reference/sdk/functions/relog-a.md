---
title: RelogA
description: Die C++ Build Insights SDK RelogA-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5a772b1156fc69eeef39514afe401c549c3b7c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323850"
---
# <a name="reloga"></a>RelogA

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RelogA` Funktion wird verwendet, um MSVC-Ereignisse aus einer Ereignisablaufverfolgung für Windows (ETW) zu lesen und in eine neue, geänderte ETW-Ablaufverfolgung zu schreiben.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Parameter

*inputLogFile*\
Die Eingabe-ETW-Ablaufverfolgung, aus der Sie Ereignisse lesen möchten.

*outputLogFile*\
Die Datei, in die die neuen Ereignisse geschrieben werden sollen.

*relogDescriptor*\
Zeiger auf ein [RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md) Objekt. Verwenden Sie dieses Objekt, um die Relogging-Sitzung zu konfigurieren.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) Enumerum.

::: moniker-end
