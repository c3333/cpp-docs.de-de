---
title: OnBeginEndPassFunc-TypeDef
description: Der OnBeginEndPassFunc-TypeDef-Verweis im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnBeginEndPassFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2008dfb86d6f45a1c05a59e1f0f4f8c7868dcda2
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041977"
---
# <a name="onbeginendpassfunc-typedef"></a>OnBeginEndPassFunc-TypeDef

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `OnBeginEndPassFunc`-TypeDef ist eine der Funktionssignaturen, die in der [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)- und [RELOG_CALLBACKS](relog-callbacks-struct.md)-Struktur verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnBeginEndPassFunc)(
    void*                           callbackContext);
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `callbackContext` |  |

::: moniker-end
