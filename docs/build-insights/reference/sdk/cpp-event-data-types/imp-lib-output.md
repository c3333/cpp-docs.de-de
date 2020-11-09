---
title: ImpLibOutput-Klasse
description: Die Referenz zur ImpLibOutput-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ImpLibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 01adb0041a3d212acf1bb846ced9019600016cda
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923186"
---
# <a name="impliboutput-class"></a>ImpLibOutput-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `ImpLibOutput`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)-Ereignisses.

## <a name="syntax"></a>Syntax

```cpp
class ImpLibOutput : public FileOutput
{
public:
    ImpLibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der Basisklasse [FileOutput](file-output.md) enthält die `ImpLibOutput`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[ImpLibOutput](#imp-lib-output)

## <a name="impliboutput"></a><a name="imp-lib-output"></a> ImpLibOutput

```cpp
ImpLibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)-Ereignis.

::: moniker-end
