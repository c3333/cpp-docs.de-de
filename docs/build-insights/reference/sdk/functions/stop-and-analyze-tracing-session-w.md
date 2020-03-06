---
title: Stopandanalyzetracingsessionw
description: Die C++ Funktionsreferenz für das Build Insights SDK stopandanalyzetracingsessionw.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ec36162efcd2bfcf17cb07a997a7ff170338d3d2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334265"
---
# <a name="stopandanalyzetracingsessionw"></a>Stopandanalyzetracingsessionw

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StopAndAnalyzeTracingSessionW`-Funktion beendet eine laufende Ablauf Verfolgungs Sitzung und speichert die resultierende Ablauf Verfolgung in einer temporären Datei. Eine Analyse Sitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Ausführbare Dateien, die diese Funktion aufrufen, müssen über Administratorrechte verfügen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StopAndAnalyzeTracingSessionW(
    const wchar_t*              sessionName,
    TRACING_SESSION_STATISTICS* statistics,
    const ANALYSIS_DESCRIPTOR*  analysisDescriptor);
```

### <a name="parameters"></a>Parameter

*Sessionname* -\
Der Name der Ablauf Verfolgungs Sitzung, die angehalten werden soll. Verwenden Sie den gleichen Sitzungs Namen wie der, der an [starttracingsession](start-tracing-session.md), [starttracingsessiona](start-tracing-session-a.md)oder [starttracingsessionw](start-tracing-session-w.md)übergeben wird.

*Statistik*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) Objekt. `StopAndAnalyzeTracingSessionW` schreibt Statistiken der Ablauf Verfolgungs Sammlung in dieses Objekt, bevor Sie zurückgegeben wird

*analysisdescriptor* -\
Zeiger auf ein [ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) Objekt. Verwenden Sie dieses Objekt, um die von `StopAndAnalyzeTracingSessionW`gestartete Analyse Sitzung zu konfigurieren.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

::: moniker-end
