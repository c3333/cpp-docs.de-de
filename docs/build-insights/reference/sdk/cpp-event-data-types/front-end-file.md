---
title: FrontEndFile-Klasse
description: Der C++ Build Insights SDK FrontEndFile-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c40137724279ea2fd615729db39f0ac5c907b79e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324760"
---
# <a name="frontendfile-class"></a>FrontEndFile-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FrontEndFile` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [FRONT_END_FILE](../event-table.md#front-end-file) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `FrontEndFile` der Aktivitätsbasisklasse enthält die Klasse die folgenden Member: [Activity](activity.md)

### <a name="constructors"></a>Konstruktoren

[FrontEndFile](#front-end-file)

### <a name="functions"></a>Functions

[Pfad](#path)

## <a name="frontendfile"></a><a name="front-end-file"></a>FrontEndFile

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FRONT_END_FILE](../event-table.md#front-end-file) FRONT_END_FILE-Ereignis.

## <a name="path"></a><a name="path"></a>Pfad

```cpp
const char* Path() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Datei, kodiert in UTF-8.

::: moniker-end
