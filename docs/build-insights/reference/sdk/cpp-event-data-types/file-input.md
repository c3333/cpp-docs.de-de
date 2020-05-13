---
title: FileInput-Klasse
description: Der C++ Build Insights SDK FileInput-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 642236d3e67465ed38508cb24c8cd698ae880065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324792"
---
# <a name="fileinput-class"></a>FileInput-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FileInput` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [FILE_INPUT](../event-table.md#file-input) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class FileInput : public SimpleEvent
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

    FileInput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `FileInput` der [SimpleEvent-Basisklasse](simple-event.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[FileInput](#file-input)

### <a name="functions"></a>Functions

[Pfadtyp](#path)
[Type](#type)

## <a name="fileinput"></a><a name="file-input"></a>FileInput

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FILE_INPUT](../event-table.md#file-input) Ereignis.

## <a name="path"></a><a name="path"></a>Pfad

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Eingabedatei.

## <a name="type"></a><a name="type"></a>-Typ

```cpp
Type Type() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der den Typ der Eingabedatei beschreibt.

::: moniker-end
