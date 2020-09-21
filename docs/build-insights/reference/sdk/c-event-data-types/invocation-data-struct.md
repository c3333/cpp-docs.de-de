---
title: INVOCATION_DATA-Struktur
description: Der Verweis auf die INVOCATION_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 48b4c28d3c01d61a31343894312a54ba2ab17a70
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041639"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA-Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `INVOCATION_DATA`-Struktur beschreibt einen Compiler- oder Linkeraufruf.

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

| name | BESCHREIBUNG |
|--|--|
| `MSVCToolCode` | Ein Code, der den Typ des Aufrufers identifiziert. Weitere Informationen finden Sie unter [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Ein Objekt, das die Version des aufgerufenen Tools als Gruppe von Integralwerten speichert. |
| `ToolVersionString` | Beschreibt die Version des aufgerufenen Tools in Textform. |
| `WorkingDirectory` | Das Verzeichnis, aus dem der Aufruf erfolgte. |
| `ToolPath` | Der absolute Pfad des aufgerufenen Tools. |

::: moniker-end
