---
title: Aufrufklasse
description: Der C++ Build Insights SDK Invocation-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fcb087d46ea445251b0108f811545a44c26f421e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324640"
---
# <a name="invocation-class"></a>Aufrufklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Invocation` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [COMPILER-](../event-table.md#compiler) oder [LINKER-Ereignis](../event-table.md#linker) abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class Invocation : public Activity
{
    const INVOCATION_DATA* data_;

public:
    enum class Type
    {
        CL      = MSVC_TOOL_CODE_CL,
        LINK    = MSVC_TOOL_CODE_LINK
    };

    Invocation(const RawEvent& event);

    Type             Type() const;
    const char*      ToolVersionString() const;
    const wchar_t*   WorkingDirectory() const;
    const wchar_t*   ToolPath() const;

    const INVOCATION_VERSION_DATA& ToolVersion() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `Invocation` der Aktivitätsbasisklasse enthält die Klasse die folgenden Member: [Activity](activity.md)

### <a name="constructors"></a>Konstruktoren

[Aufruf](#invocation)

### <a name="functions"></a>Functions

[ToolPath](#tool-path)
[ToolVersion](#tool-version)
[ToolVersionString](#tool-version-string)
[Typ](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a><a name="invocation"></a>Aufruf

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [COMPILER-](../event-table.md#compiler) oder [LINKER-Ereignis.](../event-table.md#linker)

## <a name="toolpath"></a><a name="tool-path"></a>Schneidweg

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zum aufgerufenen Werkzeug.

## <a name="toolversion"></a><a name="tool-version"></a>ToolVersion

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Rückgabewert

Die Version des Tools, das als [INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md) Referenz aufgerufen wurde.

## <a name="toolversionstring"></a><a name="tool-version-string"></a>ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Rückgabewert

Die Version des Tools, das als ANSI-Zeichenfolge aufgerufen wurde.

## <a name="type"></a><a name="type"></a>-Typ

```cpp
Type Type() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der das aufgerufene Tool angibt.

## <a name="workingdirectory"></a><a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zum Verzeichnis, in dem das Tool aufgerufen wurde.

::: moniker-end
