---
title: Objoutput-Klasse
description: Die C++ Referenz zum Build Insights SDK-objoutput-Klasse.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ObjOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 26cf110bcd086ab051174ebf0017a73370c0aa5e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334661"
---
# <a name="objoutput-class"></a>Objoutput-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `ObjOutput`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [OBJ_OUTPUT](../event-table.md#obj-output) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class ObjOutput : public FileOutput
{
public:
    ObjOutput(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [FileOutput](file-output.md) -Basisklasse enthält die `ObjOutput`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Objoutput](#obj-output)

## <a name="obj-output"></a>Objoutput

```cpp
ObjOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [OBJ_OUTPUT](../event-table.md#obj-output) Ereignis.

::: moniker-end
