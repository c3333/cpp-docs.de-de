---
title: Aktivitätsklasse
description: Die C++ buildinsights-SDK-Aktivitäts Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6de411c375b42e4acfb44bf0fac9d28ad57f1ca7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335027"
---
# <a name="activity-class"></a>Aktivitätsklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Activity`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein beliebiges Aktivitäts Ereignis abzugleichen In der [Ereignis Tabelle](../event-table.md) finden Sie alle Ereignisse, die mit der `Activity`-Klasse abgeglichen werden können.

## <a name="syntax"></a>Syntax

```cpp
class Activity : public Event
{
public:
    Activity(const RawEvent& event);

    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;
    const long long& ExclusiveDurationTicks() const;
    const long long& CPUTicks() const;
    const long long& ExclusiveCPUTicks() const;
    const long long& WallClockTimeResponsibilityTicks() const;
    const long long& ExclusiveWallClockTimeResponsibilityTicks() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Bemerkungen

Mehrere Element Funktionen in der `Activity`-Klasse geben eine Takt Anzahl zurück. C++Buildinsights verwendet den Windows-Leistungs Leistungswert als eine Quelle von Ticks. Eine Takt Anzahl muss mit einer Taktfrequenz verwendet werden, um Sie in eine Zeiteinheit, z. b. Sekunden, zu konvertieren. Die `TickFrequency` Member-Funktion, die in der [Ereignis](event.md) Basisklasse verfügbar ist, kann aufgerufen werden, um die Taktfrequenz zu erhalten. Auf der Seite [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) wird ein Beispiel für die Umstellung von Ticks in eine Zeiteinheit angezeigt.

Wenn Sie Ticks nicht selbst in Zeiteinheiten konvertieren möchten, stellt die `Activity`-Klasse Member-Funktionen bereit, die Zeit Werte in Nanosekunden zurückgeben. Verwenden Sie die C++ Standard-`chrono` Bibliothek, um Sie in andere Zeiteinheiten zu konvertieren.

## <a name="members"></a>Members

Zusammen mit den Membern, die von der [Ereignis](event.md) Basisklasse geerbt wurden, enthält die `Activity`-Klasse die folgenden Member:

### <a name="constructor"></a>Konstruktor

[Aktivität](#activity)

### <a name="functions"></a>Functions

[CPUTICKS](#cpu-ticks) -\
[Cputime](#cpu-time) -\
[Dauer](#duration)\
[Exclusivecputicks](#exclusive-cpu-ticks) -\
[Exclusivecputime](#exclusive-cpu-time) -\
[Exclusiveduration](#exclusive-duration) -\
[Exclusivedurationticks](#exclusive-duration-ticks) -\
[Exclusivewallclocktimeresponsibility](#exclusive-wall-clock-time-responsibility)\
[Exclusivewallclocktimeresponsibilityticks](#exclusive-wall-clock-time-responsibility-ticks)\
[Starttimestamp](#start-timestamp) -\
[Stoptimestamp](#stop-timestamp) -\
[Wallclocktimeresponsibility](#wall-clock-time-responsibility)\
[Wallclocktimeresponsibilityticks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a>Aktiv

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Beliebiges Aktivitäts Ereignis.

## <a name="cpu-ticks"></a>CPUTICKS

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der CPU-Ticks, die während dieser Aktivität aufgetreten sind. Ein CPU-Tick unterscheidet sich von einem regulären Tick. CPU-Ticks werden nur gezählt, wenn die CPU Code in einer Aktivität ausführt. CPU-Ticks werden nicht gezählt, wenn der der Aktivität zugeordnete Thread im Ruhezustand ist.

## <a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zeitspanne, in der die CPU Code in dieser Aktivität ausgeführt hat. Dieser Wert ist möglicherweise höher als die Dauer der Aktivität, wenn untergeordnete Aktivitäten in separaten Threads ausgeführt werden. Der Wert wird in Nanosekunden zurückgegeben.

## <a name="duration"></a>Auf

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden.

## <a name="exclusive-cpu-ticks"></a>Exclusivecputicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit [CPUTICKS](#cpu-ticks), aber nicht mit den CPU-Ticks, die in untergeordneten Aktivitäten aufgetreten sind.

## <a name="exclusive-cpu-time"></a>Exclusivecputime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit [cputime](#cpu-time), mit dem Unterschied, dass die CPU-Zeit von untergeordneten Aktivitäten nicht berücksichtigt wird.

## <a name="exclusive-duration"></a>Exclusiveduration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden, ohne die Zeitspanne, die für untergeordnete Aktivitäten aufgewendet wurde.

## <a name="exclusive-duration-ticks"></a>Exclusivedurationticks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Ticks, die in dieser Aktivität aufgetreten sind, ohne die Anzahl der Ticks, die in untergeordneten Aktivitäten aufgetreten sind.

## <a name="exclusive-wall-clock-time-responsibility"></a>Exclusivewallclocktimeresponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit der " [wallclocktimeresponsibility](#wall-clock-time-responsibility)", aber nicht mit der Zeit für untergeordnete Aktivitäten.

## <a name="exclusive-wall-clock-time-responsibility-ticks"></a>Exclusivewallclocktimeresponsibilityticks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit " [wallclocktimeresponsibilityticks](#wall-clock-time-responsibility-ticks)", aber nicht mit den Zeiteinheiten für die Zeit, die für untergeordnete Aktivitäten zuständig sind.

## <a name="start-timestamp"></a>Starttimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Teil Strich Wert, der zum Zeitpunkt der Aktivitäts Beginn aufgezeichnet wurde.

## <a name="stop-timestamp"></a>Stoptimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Wert, der zum Zeitpunkt der Beendigung der Aktivität aufgezeichnet wurde.

## <a name="wall-clock-time-responsibility"></a>Wallclocktimeresponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zeit in Nanosekunden, die für diese Aktivität verantwortlich ist. Weitere Informationen zur Bedeutung von "Wall-Clock Time Responsibility" finden Sie unter " [wallclocktimeresponsibilityticks](#wall-clock-time-responsibility-ticks)".

## <a name="wall-clock-time-responsibility-ticks"></a>Wallclocktimeresponsibilityticks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Zähler, der den Beitrag dieser Aktivität zur Gesamtzeit der Gesamtzeit darstellt. Der Takt der Aufgaben für die Wand Zeit unterscheidet sich von einem regulären Tick. Bei der Zeit, in der die Zeit für die Zeit in der Arbeit berücksichtigt wird Zwei parallele Aktivitäten können eine Dauer von 50 Ticks und dieselbe Start-und Endzeit aufweisen. In diesem Fall wird für beide die Aufgabe "Wall-Clock-Zeit" von 25 Ticks zugewiesen.

::: moniker-end
