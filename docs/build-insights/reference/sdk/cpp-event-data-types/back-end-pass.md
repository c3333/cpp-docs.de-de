---
title: Backendpass-Klasse
description: Die C++ backendpass-Klassenreferenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BackEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c159fa09b5d8a4156fc6bd886fc36da09a66db73
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335015"
---
# <a name="backendpass-class"></a>Backendpass-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `BackEndPass`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [BACK_END_PASS](../event-table.md#back-end-pass) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class BackEndPass : public CompilerPass
{
public:
    BackEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [compilerpass](compiler-pass.md) -Basisklasse enthält die `BackEndPass`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Backendpass](#back-end-pass)

## <a name="back-end-pass"></a>Backendpass

```cpp
BackEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [BACK_END_PASS](../event-table.md#back-end-pass) Ereignis.

::: moniker-end
