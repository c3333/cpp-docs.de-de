---
title: Code Generierungs Klasse
description: Die C++ Build Insights SDK-codegenerations-Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CodeGeneration
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1bc56794a197b9ae7bf116757581fb5a49699462
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334961"
---
# <a name="codegeneration-class"></a>Code Generierungs Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `CodeGeneration`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [CODE_GENERATION](../event-table.md#code-generation) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class CodeGeneration : public Activity
{
public:
    CodeGeneration(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `CodeGeneration`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Code Generation](#code-generation)

## <a name="code-generation"></a>Code Generation

```cpp
CodeGeneration(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [CODE_GENERATION](../event-table.md#code-generation) Ereignis.

::: moniker-end
