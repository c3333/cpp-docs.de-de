---
title: IAnalyzer-Klasse
description: Der C++ Build Insights SDK IAnalyzer-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: be9d80bb94450458c73fd6ce8d908985ba6f293d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329171"
---
# <a name="ianalyzer-class"></a>IAnalyzer-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `IAnalyzer` Klasse stellt eine Schnittstelle zum Analysieren einer Ereignisablaufverfolgung für Windows (ETW)-Ablaufverfolgung bereit. Es wird mit den Funktionen [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)und [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) verwendet. Verwenden `IAnalyzer` Sie als Basisklasse, um einen eigenen Analysator zu erstellen, der Teil einer Analyse- oder Reloggergruppe sein kann.

## <a name="syntax"></a>Syntax

```cpp
class IAnalyzer : public IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
    virtual AnalysisControl OnStopActivity(const EventStack& eventStack)
    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
    virtual AnalysisControl OnBeginAnalysis();
    virtual AnalysisControl OnEndAnalysis();
    virtual AnalysisControl OnBeginAnalysisPass();
    virtual AnalysisControl OnEndAnalysisPass();

    AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnBeginRelogging() final;
    AnalysisControl OnEndRelogging() final;
    AnalysisControl OnBeginReloggingPass() final;
    AnalysisControl OnEndReloggingPass() final;

    virtual ~IAnalyzer();
};
```

## <a name="remarks"></a>Bemerkungen

Klassen, die `IAnalyzer` von stammen, können sowohl als Analysatoren als auch als Relogger verwendet werden. Bei Verwendung als Relogger, die Relogger-spezifische Funktionen auf ihre Analysator Äquivalent umleiten. Das Gegenteil ist nicht der Fall: Eine `IRelogger` Klasse, die von einem Analyser abstammt, kann nicht als Analyzer verwendet werden. Die Verwendung eines Analyzers in einer Reloggergruppe ist ein gängiges Muster. Wenn ein Analysator in einer frühen Position einer Reloggergruppe platziert wird, kann er Informationen vorberechnen und für Relogger in späteren Positionen zur Verfügung stellen.

Der Standardrückgabewert für alle Funktionen, die `AnalysisControl::CONTINUE`nicht überschrieben werden, ist . Weitere Informationen finden Sie unter [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Member

Zusätzlich zum [OnTraceInfo-Member](irelogger-class.md#on-trace-info) `IRelogger` aus der `IAnalyzer` Schnittstelle enthält die Klasse die folgenden Member:

### <a name="destructor"></a>Destruktor

[IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Functions

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnendAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer"></a><a name="ianalyzer-destructor"></a>IAnalyzer

Zerstört die IAnalyzer-Klasse.

```cpp
virtual ~IAnalyzer();
```

## <a name="onbeginanalysis"></a><a name="on-begin-analysis"></a>OnBeginAnalysis

Für Analysatoren, die Teil einer Analysegruppe sind, wird diese Funktion aufgerufen, bevor der erste Analysedurchlauf beginnt. Für Analysatoren, die Teil einer Reloggergruppe sind, wird diese Funktion aufgerufen, bevor der Relogging-Pass beginnt. Für Analysatoren, die Teil der Analyse- und Reloggergruppe derselben Relogging-Sitzung sind, wird diese Funktion zweimal aufgerufen, bevor der erste Analysedurchlauf beginnt.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onbeginanalysispass"></a><a name="on-begin-analysis-pass"></a>OnBeginAnalysisPass

Für Analysatoren, die Teil einer Analysatorgruppe sind, wird diese Funktion am Anfang jedes Analysedurchlaufs aufgerufen. Für Analysatoren, die Teil einer Reloggergruppe sind, wird diese Funktion am Anfang des Relogger-Passes aufgerufen. Für Analysatoren, die Teil der Analyse- und Reloggergruppe derselben Relogging-Sitzung sind, wird diese Funktion am Anfang jedes Analysedurchlaufs und am Anfang des Relogger-Durchlaufs aufgerufen.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

Diese Funktion kann nicht überschrieben werden. Es wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Diese Funktion leitet den Aufruf von [OnBeginAnalysis](#on-begin-analysis)um.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [OnBeginAnalysis-Aufrufs.](#on-begin-analysis)

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Diese Funktion kann nicht überschrieben werden. Es wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Diese Funktion leitet den Aufruf zu [OnBeginAnalysisPass](#on-begin-analysis-pass)um.

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [OnBeginAnalysisPass-Aufrufs.](#on-begin-analysis-pass)

## <a name="onendanalysis"></a><a name="on-end-analysis"></a>OnEndAnalysis

Bei Analysatoren, die Teil einer Analysegruppe sind, wird diese Funktion aufgerufen, nachdem der letzte Analysedurchlauf beendet wurde. Für Analysatoren, die Teil einer Reloggergruppe sind, wird diese Funktion aufgerufen, nachdem der Relogging-Pass beendet wurde. Für Analysatoren, die Teil der Analyse- und Reloggergruppe derselben Relogging-Sitzung sind, wird diese Funktion zweimal aufgerufen:

1. nachdem alle Analysedurchläufe beendet sind und bevor der Relogging-Pass beginnt, und
1. nachdem der Relogging-Pass beendet wurde.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onendanalysispass"></a><a name="on-end-analysis-pass"></a>OnendAnalysisPass

Für Analysatoren, die Teil einer Analysegruppe sind, wird diese Funktion am Ende jedes Analysedurchlaufs aufgerufen. Für Analysatoren, die Teil einer Reloggergruppe sind, wird diese Funktion am Ende des Relogger-Passes aufgerufen. Für Analysatoren, die Teil der Analyse- und Reloggergruppe derselben Relogging-Sitzung sind, wird diese Funktion am Ende jedes Analysedurchlaufs und am Ende des Relogger-Durchlaufs aufgerufen.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>OnEndRelogging

Diese Funktion kann nicht überschrieben werden. Es wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Diese Funktion leitet den Aufruf an [OnEndAnalysis](#on-end-analysis)um.

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [OnEndAnalysis-Aufrufs.](#on-end-analysis)

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass

Diese Funktion kann nicht überschrieben werden. Es wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Diese Funktion leitet den Aufruf zu [OnEndAnalysisPass](#on-end-analysis-pass)um.

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [OnEndAnalysisPass-Aufrufs.](#on-end-analysis-pass)

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>OnSimpleEvent

Diese Funktion wird aufgerufen, wenn ein einfaches Ereignis verarbeitet wird. Die zweite Version dieser Funktion kann nicht überschrieben werden. Es wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Alle Anrufe auf Version 2 werden auf Version 1 umgeleitet.

### <a name="version-1"></a>Version 1

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>Version 2

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für dieses einfache Ereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

*relogSession*\
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartActivity

Diese Funktion wird aufgerufen, wenn ein Aktivitätsstartereignis verarbeitet wird. Die zweite Version dieser Funktion kann nicht überschrieben werden. Es wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Alle Anrufe auf Version 2 werden auf Version 1 umgeleitet.

### <a name="version-1"></a>Version 1

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Version 2

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für dieses Aktivitätsstartereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

*relogSession*\
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivity

Diese Funktion wird aufgerufen, wenn ein Aktivitätstop-Ereignis verarbeitet wird. Die zweite Version dieser Funktion kann nicht überschrieben werden. Es wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Alle Anrufe auf Version 2 werden auf Version 1 umgeleitet.

### <a name="version-1"></a>Version 1

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Version 2

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für dieses Aktivitätsstoppereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

*relogSession*\
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

::: moniker-end
