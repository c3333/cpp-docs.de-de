---
title: FileInput-Klasse
description: Die C++ FileInput-Klassenreferenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bea2cf72ca2a83a9cd630f8a9ccefb87dd4b7ff1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334847"
---
# <a name="fileinput-class"></a>FileInput-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FileInput`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [FILE_INPUT](../event-table.md#file-input) Ereignis abzugleichen.

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

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [SimpleEvent](simple-event.md) -Basisklasse enthält die `FileInput`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[FileInput](#file-input)

### <a name="functions"></a>Functions

[Pfad](#path)
[Typs](#type)

## <a name="file-input"></a>FileInput

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FILE_INPUT](../event-table.md#file-input) Ereignis.

## <a name="path"></a> Path

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Eingabedatei.

## <a name="type"></a>Sorte

```cpp
Type Type() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der den Typ der Eingabedatei beschreibt.

::: moniker-end
