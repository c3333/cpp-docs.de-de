---
title: Frontendfile-Klasse
description: Die C++ buildinsights SDK-frontendfile-Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 094b1326765e0e8edb00534ecb3d94c46702d4ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334793"
---
# <a name="frontendfile-class"></a>Frontendfile-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FrontEndFile`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [FRONT_END_FILE](../event-table.md#front-end-file) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `FrontEndFile`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Frontendfile](#front-end-file)

### <a name="functions"></a>Functions

[Path](#path)

## <a name="front-end-file"></a>Frontendfile

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FRONT_END_FILE](../event-table.md#front-end-file) Ereignis.

## <a name="path"></a> Path

```cpp
const char* Path() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Datei, der in UTF-8 codiert ist.

::: moniker-end
