---
title: INVOCATION_DATA Struktur
description: Das C++ Build Insights SDK INVOCATION_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b2e8ddcf79201d8bcbbb8eb298b96b5c7680f90e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335141"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `INVOCATION_DATA`-Struktur beschreibt einen Compiler oder einen Linker-Aufruf.

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `MSVCToolCode` | Ein Code, der den Typ des aufruders identifiziert. Weitere Informationen finden Sie unter [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Ein-Objekt, das die Version des aufgerufenen Tools als Gruppe ganzzahliger Werte speichert. |
| `ToolVersionString` | Beschreibt die Version des aufgerufenen Tools in Textform. |
| `WorkingDirectory` | Das Verzeichnis, aus dem der Aufruf erfolgte. |
| `ToolPath` | Der absolute Pfad des aufgerufenen Tools. |

::: moniker-end
