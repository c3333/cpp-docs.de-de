---
title: Analyzew
description: Die C++ buildinsights-SDK-analyzew-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bd9b401f08941134d3c267df5c23c5d9e981cb86
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334487"
---
# <a name="analyzew"></a>Analyzew

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `AnalyzeW`-Funktion wird zum Analysieren von MSVC-Ereignissen verwendet, die aus einer Eingabe Ereignis Ablauf Verfolgung für Windows (ETW)-Ablauf Verfolgung gelesen werden.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE AnalyzeW(
    const wchar_t*             inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Parameter

*inputlogfile* -\
Die Eingabe-etw-Ablauf Verfolgung, von der Ereignisse gelesen werden sollen.

*analysisdescriptor* -\
Zeiger auf ein [ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) Objekt. Verwenden Sie dieses Objekt, um die Analyse zu konfigurieren.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

::: moniker-end
