---
title: Pass1-Klasse
description: Der C++ Build Insights SDK Pass1-Klassen Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass1
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d81a933e21f6976624808be358230305459e4992
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334625"
---
# <a name="pass1-class"></a>Pass1-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Pass1`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [PASS1](../event-table.md#pass1) -Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class Pass1 : public LinkerPass
{
public:
    Pass1(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [linkerpass](linker-pass.md) -Basisklasse enthält die `Pass1`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Pass1](#pass1)

## <a name="pass1"></a>Pass1

```cpp
Pass1(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [PASS1](../event-table.md#pass1) -Ereignis.

::: moniker-end
