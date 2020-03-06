---
title: C2DLL-Klasse
description: Der C++ Build Insights SDK C2DLL-Klassen Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C2DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9a8ae7e8cd2d4d379865a9a7a388a6204eb9f173
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334973"
---
# <a name="c2dll-class"></a>C2DLL-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `C2DLL`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [C2_DLL](../event-table.md#c2-dll) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class C2DLL : public Activity
{
public:
    C2DLL(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `C2DLL`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[C2DLL](#c2-dll)

## <a name="c2-dll"></a>C2DLL

```cpp
C2DLL(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [C2_DLL](../event-table.md#c2-dll) Ereignis.

::: moniker-end
