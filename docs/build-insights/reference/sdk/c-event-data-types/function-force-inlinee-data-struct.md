---
title: FUNCTION_FORCE_INLINEE_DATA-Struktur
description: Der Verweis auf die FUNCTION_FORCE_INLINEE_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d64a23c603d1f30726f30ffc91c1889c51138ef6
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041704"
---
# <a name="function_force_inlinee_data-structure"></a>FUNCTION_FORCE_INLINEE_DATA-Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FUNCTION_FORCE_INLINEE_DATA`-Struktur beschreibt eine erzwungene Inlinefunktion.

## <a name="syntax"></a>Syntax

```cpp
typedef struct FUNCTION_FORCE_INLINEE_DATA_TAG
{
    const char*         Name;
    unsigned short      Size;

} FUNCTION_FORCE_INLINEE_DATA;
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `Name` | Der in UTF-8 codierte Name der Funktion. |
| `Size` | Die Größe der Funktion als eine Reihe von Zwischenanweisungen. |

::: moniker-end
