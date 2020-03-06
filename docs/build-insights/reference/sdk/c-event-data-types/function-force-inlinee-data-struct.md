---
title: FUNCTION_FORCE_INLINEE_DATA Struktur
description: Das C++ Build Insights SDK FUNCTION_FORCE_INLINEE_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3d6929f2f16e9b1bd79b7fb8b383b40e031268bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335147"
---
# <a name="function_force_inlinee_data-structure"></a>FUNCTION_FORCE_INLINEE_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FUNCTION_FORCE_INLINEE_DATA`-Struktur beschreibt eine Funktion, die Inline ist.

## <a name="syntax"></a>Syntax

```cpp
typedef struct FUNCTION_FORCE_INLINEE_DATA_TAG
{
    const char*         Name;
    unsigned short      Size;

} FUNCTION_FORCE_INLINEE_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Name` | Der Name der Funktion, die in UTF-8 codiert ist. |
| `Size` | Die Größe der Funktion als eine Reihe von zwischen Anweisungen. |

::: moniker-end
