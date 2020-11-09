---
title: Invocation-Klasse
description: Die Referenz zur Invocation-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dfd463c7b9ca72dc14ad74b3759fdd1e3730d5a9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923143"
---
# <a name="invocation-class"></a>Invocation-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `Invocation`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [COMPILER](../event-table.md#compiler)- oder [LINKER](../event-table.md#linker)-Ereignisses.

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

Zusammen mit den geerbten Membern aus der [Activity](activity.md)-Basisklasse enthält die `Invocation`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Aufruf](#invocation)

### <a name="functions"></a>Functions

[ToolPath](#tool-path)
[ToolVersion](#tool-version)
[ToolVersionString](#tool-version-string)
[Type](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a><a name="invocation"></a> Invocation

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [COMPILER](../event-table.md#compiler)- oder [LINKER](../event-table.md#linker)-Ereignis.

## <a name="toolpath"></a><a name="tool-path"></a> ToolPath

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zum aufgerufenen Tool.

## <a name="toolversion"></a><a name="tool-version"></a> ToolVersion

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Rückgabewert

Die Version des aufgerufenen Tools als [INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md)-Verweis.

## <a name="toolversionstring"></a><a name="tool-version-string"></a> ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Rückgabewert

Die Version des aufgerufenen Tools als ANSI-Zeichenfolge.

## <a name="type"></a><a name="type"></a>-Typ

```cpp
Type Type() const;
```

### <a name="return-value"></a>Rückgabewert

Code, der das aufgerufene Tool angibt.

## <a name="workingdirectory"></a><a name="working-directory"></a> WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zum Verzeichnis, in dem das Tool aufgerufen wurde.

::: moniker-end
