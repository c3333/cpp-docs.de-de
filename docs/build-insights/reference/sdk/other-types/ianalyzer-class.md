---
title: Ianalyzer-Klasse
description: Die C++ ianalyzer-Klassenreferenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 53f7b36695bb24d96ccfe88afbb56ff717c94dc9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334079"
---
# <a name="ianalyzer-class"></a>Ianalyzer-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `IAnalyzer`-Klasse stellt eine Schnittstelle zum Analysieren einer Ablauf Verfolgung für die Ereignis Ablauf Verfolgung für Windows (ETW) bereit. Es wird mit den Funktionen [makedynamicanalyzergroup](../functions/make-dynamic-analyzer-group.md), [makedynamikreloggergroup](../functions/make-dynamic-relogger-group.md), [makestaticanalyzergroup](../functions/make-dynamic-analyzer-group.md)und [makestatikreloggergroup](../functions/make-static-analyzer-group.md) verwendet. Verwenden Sie `IAnalyzer` als Basisklasse, um ein eigenes Analysetool zu erstellen, das Teil einer Analyse-oder der reloggersitzung-Gruppe sein kann.

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

Klassen, die von `IAnalyzer` abgeleitet werden, können sowohl als Analysen als auch als reloggers verwendet werden. Bei der Verwendung als reloggers leiten die relogger-spezifischen Funktionen zu ihrer Analyzer-Entsprechung um. Der umgekehrte Wert ist nicht "true": eine Klasse, die von `IRelogger` abgeleitet ist, kann nicht als Analyzer verwendet werden. Die Verwendung eines Analyzers in einer der reloggersitzung-Gruppe ist ein gängiges Muster. Bei der Platzierung in einer frühen Position einer der reloggersitzung-Gruppe kann ein Analyzer Informationen vorab berechnen und in späteren Positionen für die erneute Protokollierung verfügbar machen.

Der Standard Rückgabewert für alle Funktionen, die nicht überschrieben werden, ist `AnalysisControl::CONTINUE`. Weitere Informationen finden Sie unter [analysiscontrol](analysis-control-enum-class.md).

## <a name="members"></a>Members

Zusätzlich zum [ontraceinfo](irelogger-class.md#on-trace-info) -Member der `IRelogger`-Schnittstelle enthält die `IAnalyzer`-Klasse die folgenden Member:

### <a name="destructor"></a>Destructor

[~ Ianalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Functions

[Onbeginanalysis](#on-begin-analysis) -\
[Onbeginanalysispass](#on-begin-analysis-pass) -\
[Onbeginrelogging](#on-begin-relogging) -\
[Onbeginreloggingpass](#on-begin-relogging-pass) -\
[Oneindanalysis](#on-end-analysis) -\
[Onenddanalysispass](#on-end-analysis-pass) -\
[Onendrelogging](#on-end-relogging) -\
[Onendreloggingpass](#on-end-relogging-pass) -\
[Onsimpleevent](#on-simple-event) -\
[Onstartactivity](#on-start-activity) -\
[Onstopactivity](#on-stop-activity)

## <a name="ianalyzer-destructor"></a>~ Ianalyzer

Zerstört die ianalyzer-Klasse.

```cpp
virtual ~IAnalyzer();
```

## <a name="on-begin-analysis"></a>Onbeginanalysis

Für Analyzer, die Teil einer Analysegruppe sind, wird diese Funktion aufgerufen, bevor der erste Analyse Durchlauf beginnt. Für Analysen, die Teil einer der reloggersitzung-Gruppe sind, wird diese Funktion aufgerufen, bevor die erneute Protokollierung beginnt. Für Analysen, die Teil der Gruppe "Analyzer" und "der reloggersitzung" derselben relogging-Sitzung sind, wird diese Funktion zweimal aufgerufen, bevor der erste Analyse Durchlauf beginnt.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-begin-analysis-pass"></a>Onbeginanalysispass

Für Analysen, die Teil einer Analysegruppe sind, wird diese Funktion zu Beginn jeder Analysephase aufgerufen. Für Analysemodule, die Teil einer der reloggersitzung-Gruppe sind, wird diese Funktion am Anfang der der reloggersitzung-Übergabe aufgerufen. Für Analyzer, die Teil der Gruppe "Analyzer" und "der reloggersitzung" derselben relogging-Sitzung sind, wird diese Funktion zu Beginn jeder Analysephase und am Anfang der der reloggersitzung-Weiterleitung aufgerufen.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-begin-relogging"></a>Onbeginrelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

Diese Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer der reloggersitzung-Gruppe ist. Diese Funktion leitet den Aufrufen von [onbeginanalysis](#on-begin-analysis)um.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [onbeginanalysis](#on-begin-analysis) -Aufrufes.

## <a name="on-begin-relogging-pass"></a>Onbeginreloggingpass

Diese Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer der reloggersitzung-Gruppe ist. Diese Funktion leitet den-Befehl an [onbeginanalysispass](#on-begin-analysis-pass)um.

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [onbeginanalysispass](#on-begin-analysis-pass) -Aufrufes.

## <a name="on-end-analysis"></a>Onenddanalysis

Für Analyzer, die Teil einer Analysegruppe sind, wird diese Funktion aufgerufen, nachdem der letzte Analyse Durchlauf beendet wurde. Für Analyzer, die Teil einer der reloggersitzung-Gruppe sind, wird diese Funktion aufgerufen, nachdem die erneute Protokollierung abgeschlossen wurde. Für Analyzer, die Teil der Gruppe "Analyzer" und "der reloggersitzung" derselben relogging-Sitzung sind, wird diese Funktion zweimal aufgerufen:

1. Nachdem alle Analyse Durchläufen beendet wurden und bevor der neuprotokollierungs Durchlauf beginnt, und
1. Nachdem die erneute Protokollierung abgeschlossen wurde.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-end-analysis-pass"></a>Onenddanalysispass

Für Analysen, die Teil einer Analysegruppe sind, wird diese Funktion am Ende jeder Analysephase aufgerufen. Für Analysen, die Teil einer der reloggersitzung-Gruppe sind, wird diese Funktion am Ende der der reloggersitzung-Übergabe aufgerufen. Für Analyzer, die Teil der Gruppe "Analyzer" und "der reloggersitzung" derselben relogging-Sitzung sind, wird diese Funktion am Ende jeder Analysephase und am Ende der der reloggersitzung-Weiterleitung aufgerufen.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-end-relogging"></a>Onendrelogging

Diese Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer der reloggersitzung-Gruppe ist. Diese Funktion leitet den-Rückruf an [onendanalysis](#on-end-analysis)um.

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [onsdanalysis](#on-end-analysis) -Aufrufes.

## <a name="on-end-relogging-pass"></a>Onendreloggingpass

Diese Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer der reloggersitzung-Gruppe ist. Diese Funktion leitet den-Rückruf an [onendanalysispass](#on-end-analysis-pass)um.

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des [onsdanalysispass](#on-end-analysis-pass) -Aufrufes.

## <a name="on-simple-event"></a>Onsimpleevent

Diese Funktion wird aufgerufen, wenn ein einfaches Ereignis verarbeitet wird. Die zweite Version dieser Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer der reloggersitzung-Gruppe ist. Alle Aufrufe von Version 2 werden an Version 1 umgeleitet.

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

*Event Stack* -\
Der Ereignis Stapel für dieses einfache Ereignis. Weitere Informationen zu Ereignis Stapeln finden Sie unter [Ereignisse](../event-table.md).

\ " *relogsession* "
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-start-activity"></a>Onstartactivity

Diese Funktion wird aufgerufen, wenn ein Aktivitäts Start Ereignis verarbeitet wird. Die zweite Version dieser Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer der reloggersitzung-Gruppe ist. Alle Aufrufe von Version 2 werden an Version 1 umgeleitet.

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

*Event Stack* -\
Der Ereignis Stapel für dieses Aktivitäts Start Ereignis. Weitere Informationen zu Ereignis Stapeln finden Sie unter [Ereignisse](../event-table.md).

\ " *relogsession* "
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-stop-activity"></a>Onstopactivity

Diese Funktion wird aufgerufen, wenn ein Aktivitäts beenden-Ereignis verarbeitet wird. Die zweite Version dieser Funktion kann nicht überschrieben werden. Sie wird vom C++ Build Insights SDK aufgerufen, wenn ein Analyzer Teil einer der reloggersitzung-Gruppe ist. Alle Aufrufe von Version 2 werden an Version 1 umgeleitet.

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

*Event Stack* -\
Der Ereignis Stapel für dieses Aktivitäts Ereignis zum Abbrechen. Weitere Informationen zu Ereignis Stapeln finden Sie unter [Ereignisse](../event-table.md).

\ " *relogsession* "
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

::: moniker-end
