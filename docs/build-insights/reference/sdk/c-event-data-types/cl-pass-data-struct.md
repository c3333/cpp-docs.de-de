---
title: CL_PASS_DATA Struktur
description: Das C++ Build Insights SDK CL_PASS_DATA Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0a41e59068ade285f1ffa1a9ce13734ef5f1f32
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325701"
---
# <a name="cl_pass_data-structure"></a>CL_PASS_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `CL_PASS_DATA` Struktur beschreibt einen Kompilierungsdurchlauf.

## <a name="syntax"></a>Syntax

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `TranslationUnitPassCode` | Ein Code, der den ausgeführten Kompilierungsdurchlauf identifiziert. Weitere Informationen finden Sie unter [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | Die C- oder C++-Quelldatei, für die dieser Kompilierungsdurchlauf ausgeführt wird. |
| `OutputObjectPath` | Die vom Compiler erstellte Objektdatei. |

::: moniker-end
