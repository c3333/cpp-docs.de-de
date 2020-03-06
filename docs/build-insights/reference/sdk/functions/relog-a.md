---
title: Reloga
description: Die C++ reloga-Funktionsreferenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c4427aa0ac85e34bfb9d569913a8ccf6ab264f52
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334319"
---
# <a name="reloga"></a>Reloga

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Mit der `RelogA`-Funktion werden MSVC-Ereignisse aus einer etw-Ablauf Verfolgung (Event Tracing for Windows, Ereignis Ablauf Verfolgung für Windows) gelesen und in eine neue, geänderte etw-Ablauf Verfolgung geschrieben.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Parameter

*inputlogfile* -\
Die Eingabe-etw-Ablauf Verfolgung, von der Ereignisse gelesen werden sollen.

*outputlogfile* -\
Die Datei, in die die neuen Ereignisse geschrieben werden sollen.

*relogdescriptor* -\
Zeiger auf ein [RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md) Objekt. Verwenden Sie dieses Objekt, um die relogging-Sitzung zu konfigurieren.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

::: moniker-end
