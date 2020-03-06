---
title: Onbeginendpassfunc-typedef
description: Die C++ onbeginendpassfunc-typedef-Referenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnBeginEndPassFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6f5e602fdc460acf8e53307e88a1a3d7ad000893
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334055"
---
# <a name="onbeginendpassfunc-typedef"></a>Onbeginendpassfunc-typedef

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Der `OnBeginEndPassFunc`-TypeDef ist eine der Funktions Signaturen, die in den [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) -und [RELOG_CALLBACKS](relog-callbacks-struct.md) -Strukturen verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnBeginEndPassFunc)(
    void*                           callbackContext);
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `callbackContext` |  |

::: moniker-end
