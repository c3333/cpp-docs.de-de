---
title: FRONT_END_FILE_DATA-Struktur
description: Der Verweis auf die FRONT_END_FILE_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FRONT_END_FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c2519bfd478776f54cee59ba08b83ea00b96beff
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041756"
---
# <a name="front_end_file_data-structure"></a>FRONT_END_FILE_DATA-Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FRONT_END_FILE_DATA`-Struktur beschreibt die Verarbeitung einer Datei durch das Compiler-Front-End.

## <a name="syntax"></a>Syntax

```cpp
typedef struct FRONT_END_FILE_DATA_TAG
{
    const char*         Path;

} FRONT_END_FILE_DATA;
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `Path` | Der absolute, in UTF-8 codierte Pfad der Datei. |

::: moniker-end
