---
title: CompilerPass-Klasse
description: Die C++ Build Insights SDK-CompilerPass-Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bfbfdc28870a13a9cdb19d0ec050ea2e69fe1208
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920813"
---
# <a name="compilerpass-class"></a>CompilerPass-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `CompilerPass`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie sie, um ein [BACK_END_PASS](../event-table.md#back-end-pass)- oder [FRONT_END_PASS](../event-table.md#front-end-pass)-Ereignis abzugleichen.

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

Zusammen mit den geerbten Membern aus der [Activity](activity.md)-Basisklasse enthält die `CompilerPass`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[CompilerPass](#compiler-pass)

### <a name="enums"></a>Enumerationen

#### <a name="passcode"></a>PassCode

|Wert|BESCHREIBUNG|
|-|-|
|FRONT_END|Der Front-End-Durchlauf.|
|BACK_END|Der Back-End-Durchlauf.|

### <a name="functions"></a>Functions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[PassCode](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [BACK_END_PASS](../event-table.md#back-end-pass)- oder [FRONT_END_PASS](../event-table.md#front-end-pass)-Ereignis.

## <a name="inputsourcepath"></a><a name="input-source-path"></a> InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Eingabequelldatei, die in diesem Compilerdurchlauf verarbeitet wird.

## <a name="outputobjectpath"></a><a name="output-object-path"></a> OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Ausgabeobjektdatei, die in diesem Compilerdurchlauf produziert wird.

## <a name="passcode"></a><a name="pass-code"></a> PassCode

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der angibt, welcher Compilerdurchlauf durch dieses CompilerPass-Objekt dargestellt wird.

::: moniker-end
