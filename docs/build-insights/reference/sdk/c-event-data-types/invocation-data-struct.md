---
title: INVOCATION_DATA Struktur
description: Das C++ Build Insights SDK INVOCATION_DATA Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4e1f428facac413d7a4a5c059452dd8cdb07be4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325489"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `INVOCATION_DATA` Struktur beschreibt einen Compiler- oder Linkeraufruf.

## <a name="syntax"></a>Syntax

```cpp
typedef struct INVOCATION_DATA_TAG
{
    int                         MSVCToolCode;

    INVOCATION_VERSION_DATA     ToolVersion;

    const char*                 ToolVersionString;
    const wchar_t*              WorkingDirectory;
    const wchar_t*              ToolPath;

} INVOCATION_DATA;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `MSVCToolCode` | Ein Code, der den Aufruftyp identifiziert. Weitere Informationen finden Sie [unter MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Ein Objekt, das die Version des aufgerufenen Werkzeugs als Gruppe von integralen Werten speichert. |
| `ToolVersionString` | Beschreibt die Version des aufgerufenen Werkzeugs in Textform. |
| `WorkingDirectory` | Das Verzeichnis, aus dem der Aufruf erfolgt ist. |
| `ToolPath` | Der absolute Pfad des aufgerufenen Werkzeugs. |

::: moniker-end
