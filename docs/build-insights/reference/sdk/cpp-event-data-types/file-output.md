---
title: FileOutput-Klasse
description: Der C++ Build Insights SDK FileOutput-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 37823da8a4aaac0ce4094583b8aee8ac1eb04aaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324807"
---
# <a name="fileoutput-class"></a>FileOutput-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FileOutput` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)oder [OBJ_OUTPUT](../event-table.md#obj-output) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class FileOutput : public SimpleEvent
{
public:
    enum class Type
    {
        OTHER               = FILE_TYPE_CODE_OTHER,
        OBJ                 = FILE_TYPE_CODE_OBJ,
        EXECUTABLE_IMAGE    = FILE_TYPE_CODE_EXECUTABLE_IMAGE,
        LIB                 = FILE_TYPE_CODE_LIB,
        IMP_LIB             = FILE_TYPE_CODE_IMP_LIB,
        EXP                 = FILE_TYPE_CODE_EXP
    };

    FileOutput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `FileOutput` der [SimpleEvent-Basisklasse](simple-event.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[FileOutput](#file-output)

### <a name="functions"></a>Functions

[Pfadtyp](#path)
[Type](#type)

## <a name="fileoutput"></a><a name="file-output"></a>FileOutput

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output) [, LIB_OUTPUT](../event-table.md#lib-output)oder [OBJ_OUTPUT](../event-table.md#obj-output) Ereignis.

## <a name="path"></a><a name="path"></a>Pfad

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Ausgabedatei.

## <a name="type"></a><a name="type"></a>-Typ

```cpp
Type Type() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der den Typ der Ausgabedatei beschreibt.

::: moniker-end
