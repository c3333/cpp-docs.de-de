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
ms.openlocfilehash: 2a97ae792392e5cc0dc83bab00a92d05609a4815
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922497"
---
# <a name="onbeginendpassfunc-typedef"></a>OnBeginEndPassFunc-TypeDef

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

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
