---
title: Wholeprogramanalysis-Klasse
description: Die C++ Klasse "Build Insights SDK-voll eprogramanalysis".
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- WholeProgramAnalysis
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b8e41242acb9e902b250bab960b1c2042dd981a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334493"
---
# <a name="wholeprogramanalysis-class"></a>Wholeprogramanalysis-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `WholeProgramAnalysis`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class WholeProgramAnalysis : public Activity
{
public:
    WholeProgramAnalysis(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `WholeProgramAnalysis`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

["Wholeprogramanalysis"](#whole-program-analysis)

## <a name="whole-program-analysis"></a>"Wholeprogramanalysis"

```cpp
WholeProgramAnalysis(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis) Ereignis.

::: moniker-end
