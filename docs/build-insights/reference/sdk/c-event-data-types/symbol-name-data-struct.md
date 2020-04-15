---
title: SYMBOL_NAME_DATA Struktur
description: Das C++ Build Insights SDK SYMBOL_NAME_DATA Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1217572f20a772fde629533d6ab170c14dc5b5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325339"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `SYMBOL_NAME_DATA` Struktur beschreibt ein Compiler-Front-End-Symbol.

## <a name="syntax"></a>Syntax

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `Key` | Der Schlüssel des Symbols. Dieser Wert ist innerhalb der zu analysierenden Ablaufverfolgung eindeutig. |
| `Name` | Der Name des Symbols. |

## <a name="remarks"></a>Bemerkungen

Symbole, die aus zwei verschiedenen Compiler-Front-End-Pässen stammen, haben möglicherweise denselben Namen, aber einen anderen Schlüssel. Verwenden Sie in diesem Fall Symbolnamen, um zu bestimmen, ob zwei Typen identisch sind.

::: moniker-end
