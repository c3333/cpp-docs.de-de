---
title: SYMBOL_NAME_DATA Struktur
description: Das C++ Build Insights SDK SYMBOL_NAME_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 618e84f198c20aa089dc7e06e1e6c09b96b6d273
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335093"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `SYMBOL_NAME_DATA`-Struktur beschreibt ein Compiler-Front-End-Symbol.

## <a name="syntax"></a>Syntax

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Key` | Der Schlüssel des Symbols. Dieser Wert ist innerhalb der zu analysierende Ablauf Verfolgung eindeutig. |
| `Name` | Der Name des Symbols. |

## <a name="remarks"></a>Bemerkungen

Symbole, die aus zwei unterschiedlichen compilerfront-End-Vorgängen stammen, haben möglicherweise denselben Namen, aber einen anderen Schlüssel. Verwenden Sie in diesem Fall Symbolnamen, um zu bestimmen, ob zwei Typen identisch sind.

::: moniker-end
