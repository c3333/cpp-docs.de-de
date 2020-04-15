---
title: CompilerPass-Klasse
description: Der C++ Build Insights SDK Compilerpass-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 11af981b647d5183f88dad024d90c0ef4f8a28bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325042"
---
# <a name="compilerpass-class"></a>CompilerPass-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `CompilerPass` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [BACK_END_PASS](../event-table.md#back-end-pass) oder [FRONT_END_PASS](../event-table.md#front-end-pass) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class CompilerPass : public Activity
{
public:
    enum class PassCode
    {
        FRONT_END,
        BACK_END
    };

    CompilerPass(const RawEvent& event);

    PassCode       PassCode() const;
    const wchar_t* InputSourcePath() const;
    const wchar_t* OutputObjectPath() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `CompilerPass` der Aktivitätsbasisklasse enthält die Klasse die folgenden Member: [Activity](activity.md)

### <a name="constructors"></a>Konstruktoren

[CompilerPass](#compiler-pass)

### <a name="enums"></a>Enumerationen

#### <a name="passcode"></a>Passcode

|||
|-|-|
|FRONT_END|Der Front-End-Pass.|
|BACK_END|Der Back-End-Pass.|

### <a name="functions"></a>Functions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[Passcode](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [BACK_END_PASS](../event-table.md#back-end-pass) oder [FRONT_END_PASS](../event-table.md#front-end-pass) Ereignis.

## <a name="inputsourcepath"></a><a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Eingabequelldatei, die von diesem Compiler übergeben wird.

## <a name="outputobjectpath"></a><a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Ausgabeobjektdatei, die von diesem Compilerübergeben erstellt wurde.

## <a name="passcode"></a><a name="pass-code"></a>Passcode

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der angibt, welcher Compilerdurchlauf durch dieses CompilerPass-Objekt dargestellt wird.

::: moniker-end
