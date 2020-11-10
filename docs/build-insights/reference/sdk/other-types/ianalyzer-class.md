---
title: IAnalyzer-Klasse
description: Referenz zur C++ Build Insights SDK-Klasse „IAnalyzer“
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2514dd305a186d1153e9f9d1711bb774ea70cdf9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919812"
---
# <a name="ianalyzer-class"></a>IAnalyzer-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Klasse `IAnalyzer` bietet eine Schnittstelle zur Analyse einer Ereignisablaufverfolgung für Windows (ETW). Sie wird mit den Funktionen [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md) und [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) eingesetzt. Verwenden Sie `IAnalyzer` als Basisklasse zum Erstellen eines eigenen Analyzers, der Teil einer Analyzer- oder Reloggergruppe sein kann.

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

## <a name="remarks"></a>Hinweise

Aus `IAnalyzer` abgeleitete Klassen können sowohl als Analyzer als auch als Relogger verwendet werden. Bei einer Verwendung als Relogger führen die spezifischen Reloggerfunktionen zu einer Umleitung an das jeweilige Analyzeräquivalent. Umgekehrt gilt dies nicht: Eine Klasse, die aus `IRelogger` abgeleitet ist, kann nicht als Analyzer verwendet werden. Die Verwendung eines Analyzers in einer Reloggergruppe ist ein gängiges Muster. Wird ein Analyzer an einer frühen Position einer Reloggergruppe platziert, kann der Analyzer Informationen vorab berechnen und für nachfolgende Relogger zur Verfügung stellen.

Der Standardrückgabewert für alle nicht überschriebenen Klassen lautet `AnalysisControl::CONTINUE`. Weitere Informationen finden Sie unter [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Member

Zusätzlich zum Member [OnTraceInfo](irelogger-class.md#on-trace-info) der Schnittstelle `IRelogger` enthält die Klasse `IAnalyzer` die folgenden Member:

### <a name="destructor"></a>Destruktor

[~IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Functions

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnEndAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer"></a><a name="ianalyzer-destructor"></a> ~IAnalyzer

Zerstört die IAnalyzer-Klasse.

```cpp
virtual ~IAnalyzer();
```

## <a name="onbeginanalysis"></a><a name="on-begin-analysis"></a> OnBeginAnalysis

Für Analyzer, die Teil einer Analyzergruppe sind, wird diese Funktion vor dem ersten Analysedurchgang aufgerufen. Ist ein Analyzer Teil einer Reloggergruppe, wird diese Funktion vor dem Relogging aufgerufen. Für Analyzer, die im Rahmen einer Reloggingsitzung sowohl in der Analyzer- als auch in der Reloggergruppe verwendet werden, wird diese Funktion zweimal aufgerufen, bevor der erste Analysedurchgang beginnt.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onbeginanalysispass"></a><a name="on-begin-analysis-pass"></a> OnBeginAnalysisPass

Für Analyzer, die Teil einer Analyzergruppe sind, wird diese Funktion zu Beginn jedes Analysedurchgangs aufgerufen. Ist ein Analyzer Teil einer Reloggergruppe, wird diese Funktion zu Beginn des Reloggerdurchgangs aufgerufen. Für Analyzer, die im Rahmen einer Reloggingsitzung sowohl in der Analyzer- als auch in der Reloggergruppe verwendet werden, wird diese Funktion zu Beginn jedes Analysedurchgangs und zu Beginn des Reloggerdurchgangs aufgerufen.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a> OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

Diese Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Diese Funktion leitet den Aufruf an [OnBeginAnalysis](#on-begin-analysis) um.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [OnBeginAnalysis](#on-begin-analysis)-Aufrufs.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a> OnBeginReloggingPass

Diese Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Diese Funktion leitet den Aufruf an [OnBeginAnalysisPass](#on-begin-analysis-pass) um.

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [OnBeginAnalysisPass](#on-begin-analysis-pass)-Aufrufs.

## <a name="onendanalysis"></a><a name="on-end-analysis"></a> OnEndAnalysis

Für Analyzer, die Teil einer Analyzergruppe sind, wird diese Funktion nach Beendigung des letzten Analysedurchgangs aufgerufen. Ist der Analyzer Teil einer Reloggergruppe, wird diese Funktion nach Beendigung des Reloggingdurchgangs aufgerufen. Für Analyzer, die im Rahmen einer Reloggingsitzung sowohl in der Analyzer- als auch in der Reloggergruppe verwendet werden, wird diese Funktion zweimal aufgerufen:

1. nach der Beendigung aller Analysedurchgänge und vor dem Start des Reloggingdurchgangs sowie
1. nach dem Ende des Reloggings.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onendanalysispass"></a><a name="on-end-analysis-pass"></a> OnEndAnalysisPass

Für Analyzer, die Teil einer Analyzergruppe sind, wird diese Funktion am Ende jedes Analysedurchgangs aufgerufen. Ist ein Analyzer Teil einer Reloggergruppe, wird diese Funktion am Ende des Reloggerdurchgangs aufgerufen. Für Analyzer, die im Rahmen einer Reloggingsitzung sowohl in der Analyzer- als auch in der Reloggergruppe verwendet werden, wird diese Funktion am Ende jedes Analysedurchgangs und am Ende des Reloggerdurchgangs aufgerufen.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a> OnEndRelogging

Diese Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Diese Funktion leitet den Aufruf an [OnEndAnalysis](#on-end-analysis) um.

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [OnEndAnalysis](#on-end-analysis)-Aufrufs.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a> OnEndReloggingPass

Diese Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Diese Funktion leitet den Aufruf an [OnEndAnalysisPass](#on-end-analysis-pass) um.

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [OnEndAnalysisPass](#on-end-analysis-pass)-Aufrufs.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a> OnSimpleEvent

Diese Funktion wird aufgerufen, wenn ein einfaches Ergebnis verarbeitet wird. Die zweite Version dieser Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Alle Aufrufe von Version 2 werden an Version 1 umgeleitet.

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
Der Ereignisstapel für das betreffende einfache Ereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

*relogSession*\
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onstartactivity"></a><a name="on-start-activity"></a> OnStartActivity

Diese Funktion wird aufgerufen, wenn ein Aktivitätsstartereignis verarbeitet wird. Die zweite Version dieser Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Alle Aufrufe von Version 2 werden an Version 1 umgeleitet.

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
Der Ereignisstapel für das betreffende Aktivitätsstartereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

*relogSession*\
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a> OnStopActivity

Diese Funktion wird aufgerufen, wenn ein Aktivitätsstoppereignis verarbeitet wird. Die zweite Version dieser Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer Reloggergruppe ist. Alle Aufrufe von Version 2 werden an Version 1 umgeleitet.

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
Der Ereignisstapel für das betreffende Aktivitätsstoppereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

*relogSession*\
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

::: moniker-end
