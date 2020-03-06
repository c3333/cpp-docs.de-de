---
title: Stopandrelogtracingsession
description: Die C++ Funktion "Build Insights SDK stopandrelogtracingsession".
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e99568f9b509b89ccd0f0711433dec9d96d904bc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334199"
---
# <a name="stopandrelogtracingsession"></a>Stopandrelogtracingsession

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StopAndRelogTracingSession`-Funktion beendet eine laufende Ablauf Verfolgungs Sitzung und speichert die resultierende Ablauf Verfolgung in einer temporären Datei. Eine erneute Protokollierungs Sitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Die abschließende von der relogging-Sitzung erzeugte, erneut protokollierte Ablauf Verfolgung wird in einer Datei gespeichert, die vom Aufrufer angegeben wird. Ausführbare Dateien, die diese Funktion aufrufen, müssen über Administratorrechte verfügen.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const char*                                   sessionName,
    const char*                                   outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const wchar_t*                                sessionName,
    const wchar_t*                                outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parameter

*Sessionname* -\
Der Name der Ablauf Verfolgungs Sitzung, die angehalten werden soll. Verwenden Sie den gleichen Sitzungs Namen wie der, der an [starttracingsession](start-tracing-session.md), [starttracingsessiona](start-tracing-session-a.md)oder [starttracingsessionw](start-tracing-session-w.md)übergeben wird.

*outputlogfile* -\
Die Datei, in die die neu protokollierte Ablauf Verfolgung geschrieben werden soll, die von der erneuten Protokollierungs Sitzung erstellt wurde

*Statistik*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) Objekt. `StopAndRelogTracingSession` schreibt Statistiken der Ablauf Verfolgungs Sammlung in dieses Objekt, bevor Sie zurückgegeben wird

" *numofanalysispasses* "\
Die Anzahl der für die Ablauf Verfolgung zu testenden Analyse Durchläufen. Die Ablauf Verfolgung wird einmal pro Analyse Durchlauf durch die angegebene Analysegruppe weitergeleitet.

*systemeventsretentionflags* -\
Eine [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md) Bitmaske, die angibt, welche System-ETW-Ereignisse in der protokollierten Ablauf Verfolgung aufbewahrt werden sollen.

*analyzergroup* -\
Die Analyzer-Gruppe, die für die Analysephase der erneuten Protokollierungs Sitzung verwendet wird. Rufen Sie [makestaticanalyzergroup](make-static-analyzer-group.md) auf, um eine Analysegruppe zu erstellen. Wenn Sie eine dynamische Analysegruppe verwenden möchten, die von [makedynamicanalyzergroup](make-dynamic-analyzer-group.md)abgerufen wurde, Kapseln Sie Sie zuerst in einer statischen Analysegruppe, indem Sie die Adresse an `MakeStaticAnalyzerGroup`übergeben.

*reloggergroup* -\
Die der reloggersitzung-Gruppe, die Ereignisse in der in *outputlogfile*angegebenen Ablauf Verfolgungs Datei erneut protokolliert. Rufen Sie [makestatikreloggergroup](make-static-relogger-group.md) auf, um eine der reloggersitzung-Gruppe zu erstellen. Wenn Sie eine dynamische der reloggersitzung-Gruppe verwenden möchten, die von [makedynamideloggergroup](make-dynamic-relogger-group.md)abgerufen wurde, Kapseln Sie Sie zuerst in eine statische der reloggersitzung-Gruppe, indem Sie die Adresse an `MakeStaticReloggerGroup`übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

### <a name="remarks"></a>Bemerkungen

Die Eingabe Ablauf Verfolgung wird durch die "Analyzer"-Gruppe " *anzahlungsanalysispasses* " geleitet. Es gibt keine ähnliche Option für die erneute Protokollierung. Die Ablauf Verfolgung wird nur einmal über die Gruppe der reloggersitzung übergeben, nachdem alle Analyse Durchläufen vollständig sind.

Die erneute Protokollierung von System Ereignissen wie CPU-Beispielen aus einer der reloggersitzung-Klasse wird nicht unterstützt. Verwenden Sie den Parameter " *systemeventsretentionflags* ", um zu entscheiden, welche Systemereignisse in der Ausgabe Ablauf Verfolgung aufbewahrt werden sollen.

::: moniker-end
