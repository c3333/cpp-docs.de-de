---
title: FUNCTION_DATA Struktur
description: Das C++ Build Insights SDK FUNCTION_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 718e93bed798786a4596ccb3e724b2b54d4fe79d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335177"
---
# <a name="function_data-structure"></a>FUNCTION_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FUNCTION_DATA`-Struktur beschreibt eine-Funktion.

## <a name="syntax"></a>Syntax

```cpp
typedef struct FUNCTION_DATA_TAG
{
    const char*         Name;

} FUNCTION_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Name` | Der Name der Funktion, die in UTF-8 codiert ist. |

::: moniker-end
