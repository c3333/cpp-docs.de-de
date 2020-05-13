---
title: TEMPLATE_INSTANTIATION_DATA Struktur
description: Das C++ Build Insights SDK TEMPLATE_INSTANTIATION_DATA Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a38d19368e7c0a9912907f1da6e7a2e31ffe8d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325330"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TEMPLATE_INSTANTIATION_DATA` Struktur beschreibt eine Vorlageninstanziierung.

## <a name="syntax"></a>Syntax

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `SpecializationSymbolKey` | Der Schlüssel für den Typ der Vorlagenspezialisierung. Dieser Wert ist innerhalb der zu analysierenden Ablaufverfolgung eindeutig. |
| `PrimaryTemplateSymbolKey` | Der Schlüssel für den primären Vorlagentyp, der spezialisiert wurde. Dieser Wert ist innerhalb der zu analysierenden Ablaufverfolgung eindeutig. |
| `KindCode` | Der Typ der Vorlageninstanziierung. Weitere Informationen finden Sie [unter TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Bemerkungen

Die Schlüssel `TEMPLATE_INSTANTIATION_DATA` in der Struktur sind innerhalb der zu analysierenden Ablaufverfolgung eindeutig. Zwei verschiedene Schlüssel, die aus verschiedenen Compiler-Front-End-Pässen stammen, können jedoch auf zwei identische Typen verweisen. Wenn `TEMPLATE_INSTANTIATION_DATA` Sie Informationen aus mehreren Compiler-Front-End-Pässen verwenden, verwenden Sie die [SYMBOL_NAME](../event-table.md#symbol-name) Ereignisse, um zu bestimmen, ob zwei Typen identisch sind. `SymbolName`Ereignisse werden am Ende eines Compiler-Front-End-Passes angezeigt, nachdem alle Vorlageninstanziierungen stattgefunden haben.

::: moniker-end
