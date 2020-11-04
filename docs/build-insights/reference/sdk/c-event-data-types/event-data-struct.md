---
title: EVENT_DATA-Struktur
description: Die Referenz zur EVENT_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 617a82055f406c130d74a2823c2cf00aa1beef36
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923603"
---
# <a name="event_data-structure"></a>EVENT_DATA-Struktur

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `EVENT_DATA`-Struktur beschreibt ein Ereignis, das aus einer Analysesitzung oder einer Sitzung zur erneuten Protokollierung empfangen wurde. Diese Sitzungen werden durch Aufruf der Funktionen [Analyze](../functions/analyze.md), [AnalyzeA](../functions/analyze-a.md), [AnalyzeW](../functions/analyze-w.md), [Relog](../functions/relog.md), [RelogA](../functions/relog-a.md) oder [RelogW](../functions/relog-w.md) gestartet.

## <a name="syntax"></a>Syntax

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>Member

| name | Beschreibung |
|--|--|
| `EventId` | Eine Zahl, die das Ereignis identifiziert. Eine Liste der Ereignisbezeichner finden Sie unter [EVENT_ID](event-id-enum.md). |
| `EventInstanceId` | Eine Zahl, die das aktuelle Ereignis innerhalb einer Stapelüberwachung eindeutig identifiziert. Dieser Wert ändert sich nicht, wenn dieselbe Stapelüberwachung mehrmals analysiert oder erneut protokolliert wird. Verwenden Sie dieses Feld, um ein und dasselbe Ereignis in mehreren Durchläufen der Stapelüberwachung zur Analyse oder erneuten Protokollierung zu identifizieren. |
| `TickFrequency` | Die Anzahl von Ticks pro Sekunde, die beim Auswerten einer in Ticks gemessenen Dauer verwendet werden soll. |
| `StartTimestamp` | Wenn das Ereignis eine *Aktivität* ist, ist dieses Feld auf einen Tickwert festgelegt, der zum Startzeitpunkt der Aktivität erfasst wurde. Wenn das Ereignis ein *einfaches Ereignis* ist, ist dieses Feld auf einen Tickwert festgelegt, der zu dem Zeitpunkt erfasst wurde, als das Ereignis eingetreten ist. |
| `StopTimestamp` | Wenn das Ereignis eine *Aktivität* ist, ist dieses Feld auf einen Tickwert festgelegt, der zum Endzeitpunkt der Aktivität erfasst wurde. Wenn das Ereignis zum Beenden für diese Aktivität noch nicht empfangen wurde, ist dieses Feld auf Null (0) festgelegt. Wenn dieses Ereignis ein *einfaches Ereignis* ist, ist dieses Feld auf Null (0) festgelegt. |
| `ExclusiveDurationTicks` | Wenn dieses Ereignis eine *Aktivität* ist, ist dieses Feld auf die Anzahl von Ticks festgelegt, die direkt in dieser Aktivität aufgetreten sind. Die Anzahl von Ticks, die in einer untergeordneten Aktivität aufgetreten sind, werden ausgeschlossen. Dieses Feld ist für *einfache Ereignisse* auf Null (0) festgelegt. |
| `CPUTicks` | Wenn dieses Ereignis eine *Aktivität* ist, ist dieses Feld auf die Anzahl von CPU-Ticks festgelegt, die während dieser Aktivität aufgetreten sind. Ein CPU-Tick unterscheidet sich von einem normalen Tick. CPU-Ticks werden nur gezählt, wenn die CPU Code in einer Aktivität ausführt. CPU-Ticks werden nicht gezählt, wenn sich der mit der Aktivität verknüpfte Thread im Ruhezustand befindet. Dieses Feld ist für *einfache Ereignisse* auf Null (0) festgelegt. |
| `ExclusiveCPUTicks` | Dieses Feld hat die gleiche Bedeutung wie `CPUTicks`, außer dass es keine CPU-Ticks enthält, die in untergeordneten Aktivitäten aufgetreten sind. Dieses Feld ist für *einfache Ereignisse* auf Null (0) festgelegt. |
| `WallClockTimeResponsibilityTicks` | Wenn dieses Ereignis eine *Aktivität* ist, ist das Feld auf einen Tickzähler festgelegt, die den Beitrag dieser Aktivität zur tatsächlich verstrichenen Zeit insgesamt darstellt. Ein Tick der tatsächlich verstrichenen Zeit unterscheidet sich von einem normalen Tick. Ticks der tatsächlich verstrichenen Zeit berücksichtigen Parallelität zwischen Aktivitäten. Ein Beispiel: Zwei parallele Aktivitäten weisen eine Dauer von 50 Ticks und dieselbe Start- und Endzeit auf. In diesem Fall wird beiden Aktivitäten eine tatsächlich verstrichene Zeit von 25 Ticks zugewiesen. Dieses Feld ist für *einfache Ereignisse* auf Null (0) festgelegt. |
| `ExclusiveWallClockTimeResponsibilityTicks` | Dieses Feld hat die gleiche Bedeutung wie `WallClockTimeResponsibilityTicks`, außer dass es keine Ticks der tatsächlich verstrichenen Zeit in untergeordneten Aktivitäten enthält. Dieses Feld ist für *einfache Ereignisse* auf Null (0) festgelegt. |
| `Data` | Zeigt auf zusätzliche im Ereignis gespeicherte Daten. Der Typ der Daten, auf die gezeigt wird, unterscheidet sich je nach `EventId`-Feld. |
| `ProcessId` | Der Bezeichner für den Prozess, in dem das Ereignis aufgetreten ist. |
| `ThreadId` | Der Bezeichner für den Thread, in dem das Ereignis aufgetreten ist. |
| `ProcessorIndex` | Eine CPU-Zahl mit Nullindex, in der das Ereignis aufgetreten ist. |
| `EventName` | Eine ANSI-Zeichenfolge mit dem Namen der durch `EventId` identifizierten Entität. |
| `EventWideName` | Eine Zeichenfolge mit breiten Zeichen mit dem Namen der durch `EventId` identifizierten Entität. |

## <a name="remarks"></a>Hinweise

Viele Felder in `EVENT_DATA` enthalten Tickzähler. C++ Build Insights verwendet den Leistungsindikator von Windows als Tickquelle. Ein Tickzähler muss mit dem Feld `TickFrequency` verwendet werden, um ihn in eine geeignete Zeiteinheit wie z. B. Sekunden zu konvertieren. Ein Beispiel für diese Konvertierung finden Sie weiter unten. `EVENT_DATA` enthält kein Feld für den regulären Tickzähler einer Aktivität. Um diesen Wert zu erhalten, subtrahieren Sie `StartTimestamp` von `StopTimestamp`. `EVENT_DATA` ist eine Struktur, die von C-API-Benutzern verwendet werden soll. Für Benutzer der C++-API führen Klassen wie [Event](../cpp-event-data-types/event.md) Zeitkonvertierungen automatisch durch.

Der Wert des `EVENT_DATA`-Felds `Data` hängt vom Wert des zugehörigen `EventId`-Felds ab. Der Wert von `Data` wird in der folgenden Tabelle beschrieben. Möglicherweise sind in dieser Tabelle nicht alle Bezeichner aufgeführt. In diesem Fall ist das `Data`-Feld auf **`nullptr`** oder Null (0) festgelegt.

| `EventId`-Wert | Typ, auf den von `Data` gezeigt wird |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>Beispiel für Tickkonvertierung

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
