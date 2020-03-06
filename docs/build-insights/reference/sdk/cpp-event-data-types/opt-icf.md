---
title: Opticf-Klasse
description: Die C++ Referenz für den Build Insights SDK-opticf-Klassen.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptICF
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b7594d573a0e4eaf2e19f306b8a109923ba235dc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334643"
---
# <a name="opticf-class"></a>Opticf-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `OptICF`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [OPT_ICF](../event-table.md#opt-icf) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class OptICF : public Activity
{
public:
    OptICF(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `OptICF`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Opticf](#opt-icf)

## <a name="opt-icf"></a>Opticf

```cpp
OptICF(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [OPT_ICF](../event-table.md#opt-icf) Ereignis.

::: moniker-end
