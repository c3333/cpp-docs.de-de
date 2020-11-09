---
title: RelogW
description: Die Referenz zur RelogW-Funktion des C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e01cf7ca769c60761999ca320a7f9a65b41a8ed6
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920059"
---
# <a name="relogw"></a>RelogW

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `RelogW`-Funktion dient zum Lesen von MSVC-Ereignissen aus einer ETW-Ablaufverfolgung (Event Trace for Windows, Ereignisablaufverfolgung für Windows), die in eine neue, geänderte ETW-Ablaufverfolgung geschrieben werden.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE RelogW(
    const wchar_t*          inputLogFile,
    const wchar_t*          outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Parameter

*inputLogFile*\
Die Eingabe-ETW-Ablaufverfolgung, aus der Ereignisse gelesen werden sollen.

*outputLogFile*\
Die Datei, in die die neuen Ereignisse geschrieben werden sollen.

*relogDescriptor*\
Zeiger auf ein [RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md)-Objekt. Konfigurieren Sie mit diesem Objekt die Neuprotokollierungssitzung.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
