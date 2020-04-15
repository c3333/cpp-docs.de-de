---
title: ObjOutput-Klasse
description: Der C++ Build Insights SDK ObjOutput-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ObjOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 194253e8995401114e2529b868b36c9823510a4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324495"
---
# <a name="objoutput-class"></a>ObjOutput-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `ObjOutput` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [OBJ_OUTPUT](../event-table.md#obj-output) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class ObjOutput : public FileOutput
{
public:
    ObjOutput(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `ObjOutput` der [FileOutput-Basisklasse](file-output.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[ObjOutput](#obj-output)

## <a name="objoutput"></a><a name="obj-output"></a>ObjOutput

```cpp
ObjOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [OBJ_OUTPUT](../event-table.md#obj-output) OBJ_OUTPUT-Ereignis.

::: moniker-end
