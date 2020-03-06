---
title: FileOutput-Klasse
description: Der C++ Build Insights SDK-FileOutput-Klassen Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1c4053d0378ddb9d5dd061bbc9889c454dc9b52c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334841"
---
# <a name="fileoutput-class"></a>FileOutput-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FileOutput`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie Sie, um eine [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)oder [OBJ_OUTPUT](../event-table.md#obj-output) Ereignis abzugleichen.

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

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [SimpleEvent](simple-event.md) -Basisklasse enthält die `FileOutput`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[FileOutput](#file-output)

### <a name="functions"></a>Functions

[Pfad](#path)
[Typs](#type)

## <a name="file-output"></a>FileOutput

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)-, [EXP_OUTPUT](../event-table.md#exp-output)-, [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)-, [LIB_OUTPUT](../event-table.md#lib-output)-oder [OBJ_OUTPUT](../event-table.md#obj-output) -Ereignis.

## <a name="path"></a> Path

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Ausgabedatei.

## <a name="type"></a>Sorte

```cpp
Type Type() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der den Typ der Ausgabedatei beschreibt.

::: moniker-end
