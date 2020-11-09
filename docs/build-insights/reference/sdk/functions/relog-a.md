---
title: RelogA
description: Die Referenz zur RelogA-Funktion im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4e4882bca2241c520d4cb6ba0a8eb9c32704eaef
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922801"
---
# <a name="reloga"></a>RelogA

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `RelogA`-Funktion dient zum Lesen von MSVC-Ereignissen aus einer Ereignisablaufverfolgung für Windows (Event Trace for Windows, ETW), die in eine neue, geänderte ETW-Ablaufverfolgung geschrieben werden.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Parameter

*inputLogFile*\
Die Eingabe-ETW, aus der Ereignisse gelesen werden sollen.

*outputLogFile*\
Die Datei, in die die neuen Ereignisse geschrieben werden sollen.

*relogDescriptor*\
Zeiger auf ein [RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md)-Objekt. Konfigurieren Sie mit diesem Objekt die Neuprotokollierungssitzung.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
