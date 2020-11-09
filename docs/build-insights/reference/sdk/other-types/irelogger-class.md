---
title: IRelogger-Klasse
description: Die Referenz zur IRelogger-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e504ece95529f7279650062145f3ac0914449c98
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922523"
---
# <a name="irelogger-class"></a>IRelogger-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Klasse `IRelogger` bietet eine Schnittstelle zur Neuprotokollierung einer Ereignisablaufverfolgung für Windows (ETW). Sie wird mit den Funktionen [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) und [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) eingesetzt. Verwenden Sie `IRelogger` als Basisklasse zum Erstellen eines eigenen Reloggers, der Teil einer Reloggergruppe sein kann.

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

## <a name="remarks"></a>Hinweise

Der Standardrückgabewert für alle nicht überschriebenen Klassen lautet `AnalysisControl::CONTINUE`. Weitere Informationen finden Sie unter [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Member

### <a name="destructor"></a>Destruktor

[~IRelogger](#irelogger-destructor)

### <a name="functions"></a>Functions

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger"></a><a name="irelogger-destructor"></a> ~IRelogger

Zerstört die IRelogger-Klasse.

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a> OnBeginRelogging

Diese Funktion wird vor Beginn des Durchlaufs für die Neuprotokollierung aufgerufen.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a> OnBeginReloggingPass

Diese Funktion wird am Anfang des Durchlaufs für die Neuprotokollierung aufgerufen.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a> OnEndRelogging

Diese Funktion wird nach dem Durchlauf für die Neuprotokollierung aufgerufen.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a> OnEndReloggingPass

Diese Funktion am Ende des Durchlaufs für die Neuprotokollierung aufgerufen.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a> OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Diese Funktion wird aufgerufen, wenn ein einfaches Ergebnis verarbeitet wird.

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für das betreffende einfache Ereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onstartactivity"></a><a name="on-start-activity"></a> OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Diese Funktion wird aufgerufen, wenn ein Aktivitätsstartereignis verarbeitet wird.

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für das betreffende Aktivitätsstartereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a> OnStopActivity

Diese Funktion wird aufgerufen, wenn ein Aktivitätsstoppereignis verarbeitet wird.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Parameter

*eventStack*\
Der Ereignisstapel für das betreffende Aktivitätsstoppereignis. Weitere Informationen zu Ereignisstapeln finden Sie unter [Ereignisse](../event-table.md).

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

## <a name="ontraceinfo"></a><a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Diese Funktion wird einmal am Anfang jeder Analyse oder jedes Durchlaufs für die Neuprotokollierung aufgerufen.

### <a name="parameters"></a>Parameter

*traceInfo*\
Ein [TraceInfo](../cpp-event-data-types/trace-info.md)-Objekt, das nützliche Eigenschaften für die erfolgte Ablaufverfolgung enthält.

### <a name="return-value"></a>Rückgabewert

Dieser [AnalysisControl](analysis-control-enum-class.md)-Code beschreibt, welche Schritte als nächste auszuführen sind.

::: moniker-end
