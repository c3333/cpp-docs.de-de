---
title: EVENT_DATA Struktur
description: Das C++ Build Insights SDK EVENT_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 572cbdaba346ddb77b665b5677b978c83a80aa3d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335213"
---
# <a name="event_data-structure"></a>EVENT_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EVENT_DATA` Struktur beschreibt ein Ereignis, das von einer Analyse oder einer erneuten Protokollierungs Sitzung empfangen wurde. Diese Sitzungen werden durch Aufrufen der Funktionen " [analysieren](../functions/analyze.md)", " [analyzea](../functions/analyze-a.md)", " [analyzew](../functions/analyze-w.md)", " [relog](../functions/relog.md)", " [reloga](../functions/relog-a.md)" oder " [relogw](../functions/relog-w.md) " gestartet

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `EventId` | Eine Zahl, die das Ereignis bezeichnet. Eine Liste der Ereignis Bezeichner finden Sie unter [event_id](event-id-enum.md). |
| `EventInstanceId` | Eine Zahl, die das aktuelle Ereignis innerhalb einer Ablauf Verfolgung eindeutig identifiziert. Dieser Wert ändert sich nicht, wenn dieselbe Ablauf Verfolgung mehrmals analysiert oder neu protokolliert wird. Verwenden Sie dieses Feld, um das gleiche Ereignis in mehreren Analysen zu identifizieren oder die erneute Protokollierung über dieselbe Ablauf Verfolgung durchzuführen. |
| `TickFrequency` | Die Anzahl der Ticks pro Sekunde, die verwendet werden sollen, wenn eine in Ticks gemessene Dauer ausgewertet wird. |
| `StartTimestamp` | Wenn das Ereignis eine *Aktivität*ist, wird dieses Feld auf einen Teil Strich Wert festgelegt, der zu dem Zeitpunkt aufgezeichnet wurde, als die Aktivität gestartet wurde. Wenn dieses Ereignis ein *einfaches Ereignis*ist, wird dieses Feld auf einen Teil Strich Wert festgelegt, der zu dem Zeitpunkt aufgezeichnet wurde, als das Ereignis aufgetreten ist. |
| `StopTimestamp` | Wenn das Ereignis eine *Aktivität*ist, wird dieses Feld auf einen Teil Strich Wert festgelegt, der zu dem Zeitpunkt aufgezeichnet wurde, zu dem die Aktivität beendet wurde. Wenn das Ereignis zum Abbrechen für diese Aktivität noch nicht empfangen wurde, wird dieses Feld auf 0 (null) festgelegt. Wenn dieses Ereignis ein *einfaches Ereignis*ist, wird dieses Feld auf 0 (null) festgelegt. |
| `ExclusiveDurationTicks` | Wenn dieses Ereignis eine *Aktivität*ist, wird dieses Feld auf die Anzahl der Ticks festgelegt, die direkt in dieser Aktivität aufgetreten sind. Die Anzahl der Ticks, die in einer untergeordneten Aktivität aufgetreten sind, wird ausgeschlossen. Dieses Feld ist für *einfache Ereignisse*auf 0 (null) festgelegt. |
| `CPUTicks` | Wenn dieses Ereignis eine *Aktivität*ist, wird dieses Feld auf die Anzahl der CPU-Ticks festgelegt, die während dieser Aktivität aufgetreten sind. Ein CPU-Tick unterscheidet sich von einem regulären Tick. CPU-Ticks werden nur gezählt, wenn die CPU Code in einer Aktivität ausführt. CPU-Ticks werden nicht gezählt, wenn der der Aktivität zugeordnete Thread im Ruhezustand ist. Dieses Feld ist für *einfache Ereignisse*auf 0 (null) festgelegt. |
| `ExclusiveCPUTicks` | Dieses Feld hat dieselbe Bedeutung wie `CPUTicks`, mit der Ausnahme, dass es keine CPU-Ticks enthält, die in untergeordneten Aktivitäten aufgetreten sind. Dieses Feld ist für *einfache Ereignisse*auf 0 (null) festgelegt. |
| `WallClockTimeResponsibilityTicks` | Wenn es sich bei diesem Ereignis um eine *Aktivität*handelt, wird dieses Feld auf eine Takt Anzahl festgelegt, die den Beitrag dieser Aktivität zur Gesamtzeit für die Uhrzeit darstellt. Der Takt der Aufgaben für die Wand Zeit unterscheidet sich von einem regulären Tick. Bei der Zeit, in der die Zeit für die Zeit in der Arbeit berücksichtigt wird Beispielsweise können zwei parallele Aktivitäten eine Dauer von 50 Ticks und dieselbe Start-und Endzeit aufweisen. In diesem Fall wird für beide eine Wand Zeit in der Verantwortung von 25 Ticks zugewiesen. Dieses Feld ist für *einfache Ereignisse*auf 0 (null) festgelegt. |
| `ExclusiveWallClockTimeResponsibilityTicks` | Dieses Feld hat dieselbe Bedeutung wie `WallClockTimeResponsibilityTicks`, mit dem Unterschied, dass es keine untergeordneten Aktivitäten von der Wand-/Uhrzeitangabe enthält. Dieses Feld ist für *einfache Ereignisse*auf 0 (null) festgelegt. |
| `Data` | Zeigt auf zusätzliche Daten, die im Ereignis gespeichert werden. Der Datentyp, auf den verwiesen wird, ist abhängig vom `EventId` Feld unterschiedlich. |
| `ProcessId` | Der Bezeichner für den Prozess, in dem das Ereignis aufgetreten ist. |
| `ThreadId` | Der Bezeichner für den Thread, in dem das Ereignis aufgetreten ist. |
| `ProcessorIndex` | Die NULL indizierte CPU-Zahl, auf der das Ereignis aufgetreten ist. |
| `EventName` | Eine ANSI-Zeichenfolge mit dem Namen der Entität, die durch `EventId`identifiziert wird. |
| `EventWideName` | Eine Breite Zeichenfolge, die den Namen der durch `EventId`identifizierten Entität enthält. |

## <a name="remarks"></a>Bemerkungen

Viele Felder in `EVENT_DATA` die Tick-Zähler enthalten. C++Buildeinblicke verwendet den Leistungs Leistungswert von Fenstern als Quelle von Ticks. Ein Tick-Zähler muss mit dem `TickFrequency`-Feld verwendet werden, um ihn in eine entsprechende Zeiteinheit, z. b. Sekunden, zu konvertieren. Sehen Sie sich das folgende Beispiel an, um diese Konvertierung durchzuführen. `EVENT_DATA` enthält kein Feld für die reguläre Takt Anzahl einer Aktivität. Zum Abrufen dieses Werts subtrahieren Sie `StartTimestamp` von `StopTimestamp`. `EVENT_DATA` ist eine Struktur, die von C-API-Benutzern verwendet werden soll. Für C++ API-Benutzer werden Klassen wie [Ereignis](../cpp-event-data-types/event.md) automatisch Zeit Konvertierungen durchführen.

Der Wert des Felds `EVENT_DATA` `Data` hängt vom Wert des `EventId` Felds ab. Der Wert `Data` wird in der folgenden Tabelle beschrieben. In der folgenden Tabelle fehlen möglicherweise einige Entitäts Bezeichner. In diesem Fall wird das Feld `Data` auf `nullptr` oder NULL festgelegt.

| Wert vom Typ `EventId` | Typ, auf den von verwiesen wird `Data` |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
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

## <a name="tick-conversion-example"></a>Beispiel für Tick-Konvertierung

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
