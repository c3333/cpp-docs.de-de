---
title: Compilerpass-Klasse
description: Die C++ compilerpass-Klassenreferenz für Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c2fa1c2c4be8aaf5bec77b383f93a4b033ca8e3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334955"
---
# <a name="compilerpass-class"></a>Compilerpass-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `CompilerPass`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um eine Entsprechung für eine [BACK_END_PASS](../event-table.md#back-end-pass) oder [FRONT_END_PASS](../event-table.md#front-end-pass) Ereignis zu

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

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `CompilerPass`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Compilerpass](#compiler-pass)

### <a name="enums"></a>Enumerationen

#### <a name="passcode"></a>Kennung

|||
|-|-|
|FRONT_END|Der Front-End-Durchlauf.|
|BACK_END|Der Back-End-Durchlauf.|

### <a name="functions"></a>Funktionen

[Inputsourcepath](#input-source-path) -\
[Outputobjectpath](#output-object-path) -\
[Kennung](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a>Compilerpass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [BACK_END_PASS](../event-table.md#back-end-pass) -oder [FRONT_END_PASS](../event-table.md#front-end-pass) -Ereignis.

## <a name="inputsourcepath"></a><a name="input-source-path"></a>Input SourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Eingabe Quelldatei, die von diesem compilerdurchlauf verarbeitet wird.

## <a name="outputobjectpath"></a><a name="output-object-path"></a>Outputobjectpath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Rückgabewert

Der absolute Pfad zur Ausgabe Objektdatei, die von diesem compilerdurchlauf erzeugt wird.

## <a name="passcode"></a><a name="pass-code"></a>Kennung

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der angibt, welcher compilerdurchlauf durch dieses compilerpass-Objekt dargestellt wird.

::: moniker-end
