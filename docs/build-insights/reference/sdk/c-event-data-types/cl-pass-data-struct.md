---
title: CL_PASS_DATA-Struktur
description: Der Verweis auf die CL_PASS_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 24e524b802a124f38043f3b69afed7f1aa9cd156
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923650"
---
# <a name="cl_pass_data-structure"></a>CL_PASS_DATA-Struktur

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `CL_PASS_DATA`-Struktur beschreibt einen Kompilierungsdurchlauf.

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

| name | BESCHREIBUNG |
|--|--|
| `TranslationUnitPassCode` | Ein Code, der den ausgeführten Kompilierungsdurchlauf identifiziert. Weitere Informationen finden Sie unter [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | Die C- oder C++-Quelldatei, mit der dieser Kompilierungsdurchlauf ausgeführt wird. |
| `OutputObjectPath` | Die vom Compiler erstellte Objektdatei. |

::: moniker-end
