---
title: CL_PASS_DATA Struktur
description: Das C++ Build Insights SDK CL_PASS_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3df5b5bc1cddbadc4a4d432ae021dd8b338c532e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335255"
---
# <a name="cl_pass_data-structure"></a>CL_PASS_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

In der `CL_PASS_DATA` Struktur wird ein Kompilierungs Durchlauf beschrieben.

## <a name="syntax"></a>Syntax

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `TranslationUnitPassCode` | Ein Code, der den ausgeführten Kompilierungs Durchlauf identifiziert. Weitere Informationen finden Sie unter [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | Die C- C++ oder Quelldatei, für die dieser Kompilierungs Durchlauf ausgeführt wird. |
| `OutputObjectPath` | Die vom Compiler erstellte Objektdatei. |

::: moniker-end
