---
title: Compilerklasse
description: Die C++ Build Insights SDK-compilerklassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a63a0bad1ab6063d5986fec77b5135f500ded1ce
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334943"
---
# <a name="compiler-class"></a>Compilerklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Compiler`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein- [compilerereignis](../event-table.md#compiler) abzugleichen

## <a name="syntax"></a>Syntax

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [Aufruf](invocation.md) enden Basisklasse enthält die `Compiler`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Versionen](#compiler)

## <a name="compiler"></a>Versionen

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [compilerereignis](../event-table.md#compiler) .

::: moniker-end
