---
title: Aufruf Klasse
description: Die C++ Build Insights SDK-Aufruf Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c4698300a3eeaf77210ad74f84b0c0cd219b457
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334745"
---
# <a name="invocation-class"></a>Aufruf Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Invocation`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie ihn, um einen Vergleich mit einem [Compiler](../event-table.md#compiler) [-oder](../event-table.md#linker) linkerereignis

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

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `Invocation`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Aufruf](#invocation)

### <a name="functions"></a>Functions

[ToolPath](#tool-path)
[Toolversion](#tool-version)
[toolversionstring](#tool-version-string)
[Typ](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a>Aufruf

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [Compiler](../event-table.md#compiler) oder ein [Linker](../event-table.md#linker) -Ereignis.

## <a name="tool-path"></a>ToolPath

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zum Tool, das aufgerufen wurde.

## <a name="tool-version"></a>Tool Version

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Rückgabewert

Die Version des Tools, das aufgerufen wurde, als [INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md) Verweis.

## <a name="tool-version-string"></a>Toolversionstring

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Rückgabewert

Die Version des Tools, die als ANSI-Zeichenfolge aufgerufen wurde.

## <a name="type"></a>Sorte

```cpp
Type Type() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der das Tool angibt, das aufgerufen wurde.

## <a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zum Verzeichnis, in dem das Tool aufgerufen wurde.

::: moniker-end
