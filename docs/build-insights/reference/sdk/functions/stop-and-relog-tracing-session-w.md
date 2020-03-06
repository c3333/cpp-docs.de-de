---
title: Stopandrelogtracingsessionw
description: Die C++ Funktionsreferenz für das Build Insights SDK stopandrelogtracingsessionw.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 021ea5986714fa3432ab6e2831c6069356f380d5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334205"
---
# <a name="stopandrelogtracingsessionw"></a>Stopandrelogtracingsessionw

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StopAndRelogTracingSessionW`-Funktion beendet eine laufende Ablauf Verfolgungs Sitzung und speichert die resultierende Ablauf Verfolgung in einer temporären Datei. Eine erneute Protokollierungs Sitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Die abschließende von der relogging-Sitzung erzeugte, erneut protokollierte Ablauf Verfolgung wird in einer Datei gespeichert, die vom Aufrufer angegeben wird. Ausführbare Dateien, die diese Funktion aufrufen, müssen über Administratorrechte verfügen.

## <a name="syntax"></a>Syntax

```cpp
enum RESULT_CODE StopAndRelogTracingSessionW(
    const wchar_t*              sessionName,
    const wchar_t*              outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>Parameter

*Sessionname* -\
Der Name der Ablauf Verfolgungs Sitzung, die angehalten werden soll. Verwenden Sie den gleichen Sitzungs Namen wie der, der an [starttracingsession](start-tracing-session.md), [starttracingsessiona](start-tracing-session-a.md)oder [starttracingsessionw](start-tracing-session-w.md)übergeben wird.

*outputlogfile* -\
Die Datei, in die die neu protokollierte Ablauf Verfolgung geschrieben werden soll, die von der erneuten Protokollierungs Sitzung erstellt wurde

*Statistik*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) Objekt. `StopAndRelogTracingSessionW` schreibt Statistiken der Ablauf Verfolgungs Sammlung in dieses Objekt, bevor Sie zurückgegeben wird

*analysisdescriptor* -\
Zeiger auf ein [RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) Objekt. Verwenden Sie dieses Objekt, um die relogging-Sitzung zu konfigurieren, die von `StopAndRelogTracingSessionW`gestartet wird.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

::: moniker-end
