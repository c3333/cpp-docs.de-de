---
title: Frontendpass-Klasse
description: Die C++ Build Insights SDK-frontendpass-Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cc0bf38c46b51d4a49da46be88e23afa64c12cc8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334781"
---
# <a name="frontendpass-class"></a>Frontendpass-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FrontEndPass`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [FRONT_END_PASS](../event-table.md#front-end-pass) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class FrontEndPass : public CompilerPass
{
public:
    FrontEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [compilerpass](compiler-pass.md) -Basisklasse enthält die `FrontEndPass`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Frontendpass](#front-end-pass)

## <a name="front-end-pass"></a>Frontendpass

```cpp
FrontEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FRONT_END_PASS](../event-table.md#front-end-pass) Ereignis.

::: moniker-end
