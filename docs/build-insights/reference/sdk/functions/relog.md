---
title: Erneut aufzuzeichnen
description: Die C++ Funktionsreferenz für den Build Insights SDK-Relog.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1ce09101deebd957de4b9305762dc37f38b53f4e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334283"
---
# <a name="relog"></a>Erneut aufzuzeichnen

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Mit der `Relog`-Funktion werden MSVC-Ereignisse aus einer etw-Ablauf Verfolgung (Event Tracing for Windows, Ereignis Ablauf Verfolgung für Windows) gelesen und in eine neue, geänderte etw-Ablauf Verfolgung geschrieben.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parameter

*Tanalyzergroupmembers* -\
Dieser Parameter wird immer abgeleitet.

*Treloggergroupmembers* -\
Dieser Parameter wird immer abgeleitet.

*inputlogfile* -\
Die Eingabe-etw-Ablauf Verfolgung, von der Ereignisse gelesen werden sollen.

*outputlogfile* -\
Die Datei, in die die neuen Ereignisse geschrieben werden sollen.

" *numofanalysispasses* "\
Die Anzahl der an der Eingabe Ablauf Verfolgung zu testenden Analysen. Die Ablauf Verfolgung wird einmal pro Analyse Durchlauf durch die angegebene Analysegruppe weitergeleitet.

*systemeventsretentionflags* -\
Eine Bitmaske, die angibt, welche System-ETW-Ereignisse in der protokollierten Ablauf Verfolgung aufbewahrt werden sollen. Weitere Informationen finden Sie unter [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

*analyzergroup* -\
Die Analyzer-Gruppe, die für die Analysephase der erneuten Protokollierungs Sitzung verwendet wird. Rufen Sie [makestaticanalyzergroup](make-static-analyzer-group.md) auf, um eine Analysegruppe zu erstellen. Wenn Sie eine dynamische Analysegruppe verwenden möchten, die von [makedynamicanalyzergroup](make-dynamic-analyzer-group.md)abgerufen wurde, Kapseln Sie Sie zuerst in einer statischen Analysegruppe, indem Sie die Adresse an `MakeStaticAnalyzerGroup`übergeben.

*reloggergroup* -\
Die der reloggersitzung-Gruppe, die Ereignisse in der in *outputlogfile*angegebenen Ablauf Verfolgungs Datei erneut protokolliert. Rufen Sie [makestatikreloggergroup](make-static-relogger-group.md) auf, um eine der reloggersitzung-Gruppe zu erstellen. Wenn Sie eine dynamische der reloggersitzung-Gruppe verwenden möchten, die von [makedynamideloggergroup](make-dynamic-relogger-group.md)abgerufen wurde, Kapseln Sie Sie zuerst in eine statische der reloggersitzung-Gruppe, indem Sie die Adresse an `MakeStaticReloggerGroup`übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

### <a name="remark"></a>Anmerkung

Die Eingabe Ablauf Verfolgung wird durch die "Analyzer"-Gruppe " *anzahlungsanalysispasses* " geleitet. Es gibt keine ähnliche Option für die erneute Protokollierung. Die Ablauf Verfolgung wird nur einmal über die Gruppe der reloggersitzung übergeben, nachdem alle Analyse Durchläufen vollständig sind.

Die erneute Protokollierung von System Ereignissen wie CPU-Beispielen aus einer der reloggersitzung-Klasse wird nicht unterstützt. Verwenden Sie den Parameter " *systemeventsretentionflags* ", um zu entscheiden, welche Systemereignisse in der Ausgabe Ablauf Verfolgung aufbewahrt werden sollen.

::: moniker-end
