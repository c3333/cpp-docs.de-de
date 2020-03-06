---
title: Optref-Klasse
description: Die C++ Build Insights SDK-optref-Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c2abad6489012250862bc0721663572d03261bd4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334637"
---
# <a name="optref-class"></a>Optref-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `OptRef`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [OPT_REF](../event-table.md#opt-ref) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class OptRef : public Activity
{
public:
    OptRef(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `OptRef`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Optref](#opt-ref)

## <a name="opt-ref"></a>Optref

```cpp
OptRef(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [OPT_REF](../event-table.md#opt-ref) Ereignis.

::: moniker-end
