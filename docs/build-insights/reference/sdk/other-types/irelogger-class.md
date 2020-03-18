---
title: Irelogger-Klasse
description: Die C++ Referenz zum Build Insights SDK irelogger-Klasse.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0796cec3fe4ac6183279e8d8013a9550f18b61c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422895"
---
# <a name="irelogger-class"></a>Irelogger-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `IRelogger`-Klasse stellt eine Schnittstelle zum erneuten protokollieren einer Ereignis Ablauf Verfolgung für Windows (ETW)-Ablauf Verfolgung bereit. Es wird mit den Funktionen [makedynamikreloggergroup](../functions/make-dynamic-relogger-group.md) und [makestatikreloggergroup](../functions/make-static-analyzer-group.md) verwendet. Verwenden Sie `IRelogger` als Basisklasse, um eine eigene der reloggersitzung zu erstellen, die Teil einer der reloggersitzung-Gruppe sein kann.

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

Der Standard Rückgabewert für alle Funktionen, die nicht überschrieben werden, ist `AnalysisControl::CONTINUE`. Weitere Informationen finden Sie unter [analysiscontrol](analysis-control-enum-class.md).

## <a name="members"></a>Member

### <a name="destructor"></a>Destructor

[~ Irelogger](#irelogger-destructor)

### <a name="functions"></a>Funktionen

[Onbeginrelogging](#on-begin-relogging) -\
[Onbeginreloggingpass](#on-begin-relogging-pass) -\
[Onendrelogging](#on-end-relogging) -\
[Onendreloggingpass](#on-end-relogging-pass) -\
[Onsimpleevent](#on-simple-event) -\
[Onstartactivity](#on-start-activity) -\
[Onstopactivity](#on-stop-activity) -\
[Ontraceinfo](#on-trace-info)

## <a name="irelogger-destructor"></a>~ Irelogger

Zerstört die irelogger-Klasse.

```cpp
virtual ~IRelogger();
```

## <a name="on-begin-relogging"></a>Onbeginrelogging

Diese Funktion wird vor Beginn der erneuten Protokollierung aufgerufen.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-begin-relogging-pass"></a>Onbeginreloggingpass

Diese Funktion wird am Anfang der erneuten Protokollierungs Phase aufgerufen.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-end-relogging"></a>Onendrelogging

Diese Funktion wird aufgerufen, nachdem die erneute Protokollierung abgeschlossen wurde.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-end-relogging-pass"></a>Onendreloggingpass

Diese Funktion wird am Ende der erneuten Protokollierungs Phase aufgerufen.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-simple-event"></a>Onsimpleevent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Diese Funktion wird aufgerufen, wenn ein einfaches Ereignis verarbeitet wird.

### <a name="parameters"></a>Parameter

*Event Stack* -\
Der Ereignis Stapel für dieses einfache Ereignis. Weitere Informationen zu Ereignis Stapeln finden Sie unter [Ereignisse](../event-table.md).

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-start-activity"></a>Onstartactivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Diese Funktion wird aufgerufen, wenn ein Aktivitäts Start Ereignis verarbeitet wird.

### <a name="parameters"></a>Parameter

*Event Stack* -\
Der Ereignis Stapel für dieses Aktivitäts Start Ereignis. Weitere Informationen zu Ereignis Stapeln finden Sie unter [Ereignisse](../event-table.md).

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-stop-activity"></a>Onstopactivity

Diese Funktion wird aufgerufen, wenn ein Aktivitäts beenden-Ereignis verarbeitet wird.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Parameter

*Event Stack* -\
Der Ereignis Stapel für dieses Aktivitäts Ereignis zum Abbrechen. Weitere Informationen zu Ereignis Stapeln finden Sie unter [Ereignisse](../event-table.md).

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

## <a name="on-trace-info"></a>Ontraceinfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Diese Funktion wird einmal am Anfang jeder Analyse oder Neuprotokollierung aufgerufen.

### <a name="parameters"></a>Parameter

*traceingefo* -\
Ein [TraceInfo](../cpp-event-data-types/trace-info.md) -Objekt, das nützliche Eigenschaften über die verbrauchte Ablauf Verfolgung enthält.

### <a name="return-value"></a>Rückgabewert

Ein [analysiscontrol](analysis-control-enum-class.md) -Code, der beschreibt, was als Nächstes geschehen soll.

::: moniker-end
