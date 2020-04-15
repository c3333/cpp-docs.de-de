---
title: IRelogger-Klasse
description: Die C++ Build Insights SDK IRelogger-Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146377b2b44df43ed4b2f749efd9fb614a2a09c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329147"
---
# <a name="irelogger-class"></a>IRelogger-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `IRelogger` Klasse stellt eine Schnittstelle zum Erneutladen einer ETW-Ablaufverfolgung (Event Tracing for Windows) bereit. Es wird mit den Funktionen [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) und [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) verwendet. Verwenden `IRelogger` Sie als Basisklasse, um Einen eigenen Relogger zu erstellen, der Teil einer Reloggergruppe sein kann.

## <a name="syntax"></a>Syntax

```cpp
class IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
    virtual AnalysisControl OnBeginRelogging();
    virtual AnalysisControl OnEndRelogging();
    virtual AnalysisControl OnBeginReloggingPass();
    virtual AnalysisControl OnEndReloggingPass() ;

    virtual ~IRelogger();
};
```

## <a name="remarks"></a>Bemerkungen

Der Standardrückgabewert für alle Funktionen, die `AnalysisControl::CONTINUE`nicht überschrieben werden, ist . Weitere Informationen finden Sie unter [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Member

### <a name="destructor"></a>Destruktor

[€IRelogger](#irelogger-destructor)

### <a name="functions"></a>Functions

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger"></a><a name="irelogger-destructor"></a>€IRelogger

Zerstört die IRelogger-Klasse.

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging

Diese Funktion wird aufgerufen, bevor der Relogging-Pass beginnt.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Diese Funktion wird am Anfang des Relogging-Durchlaufs aufgerufen.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>OnEndRelogging

Diese Funktion wird aufgerufen, nachdem der Relogging-Pass beendet wurde.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass

Diese Funktion wird am Ende des Relogging-Durchlaufs aufgerufen.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Diese Funktion wird aufgerufen, wenn ein einfaches Ereignis verarbeitet wird.

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für dieses einfache Ereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Diese Funktion wird aufgerufen, wenn ein Aktivitätsstartereignis verarbeitet wird.

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für dieses Aktivitätsstartereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivity

Diese Funktion wird aufgerufen, wenn ein Aktivitätstop-Ereignis verarbeitet wird.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für dieses Aktivitätsstoppereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

## <a name="ontraceinfo"></a><a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Diese Funktion wird einmal am Anfang jedes Analyse- oder Relogging-Durchlaufs aufgerufen.

### <a name="parameters"></a>Parameter

*traceInfo*\
Ein [TraceInfo-Objekt,](../cpp-event-data-types/trace-info.md) das nützliche Eigenschaften zur verbrauchten Ablaufverfolgung enthält.

### <a name="return-value"></a>Rückgabewert

Ein [AnalysisControl-Code,](analysis-control-enum-class.md) der beschreibt, was als nächstes geschehen soll.

::: moniker-end
