---
title: TEMPLATE_INSTANTIATION_DATA-Struktur
description: Der Verweis auf die TEMPLATE_INSTANTIATION_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c92fbd8ee7e1fff702757d003ab3bbe0bdabd886
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923438"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA-Struktur

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `TEMPLATE_INSTANTIATION_DATA`-Struktur beschreibt eine Vorlageninstanziierung.

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

| name | BESCHREIBUNG |
|--|--|
| `SpecializationSymbolKey` | Der Schlüssel für den Typ der Vorlagenspezialisierung. Dieser Wert ist eindeutig innerhalb der Ablaufverfolgung, die analysiert wird. |
| `PrimaryTemplateSymbolKey` | Der Schlüssel für den primären Vorlagentyp, der spezialisiert wurde. Dieser Wert ist eindeutig innerhalb der Ablaufverfolgung, die analysiert wird. |
| `KindCode` | Der Typ der Vorlageninstanziierung. Weitere Informationen finden Sie unter [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Bemerkungen

Die Schlüssel in der `TEMPLATE_INSTANTIATION_DATA`-Struktur sind eindeutig innerhalb der Ablaufverfolgung, die analysiert wird. Allerdings können zwei verschiedene Schlüssel, die aus unterschiedlichen Compiler-Front-End-Durchläufen stammen, auf zwei identische Typen verweisen. Wenn Sie `TEMPLATE_INSTANTIATION_DATA`-Informationen aus mehreren Compiler-Front-End-Durchläufen verarbeiten, bestimmen Sie anhand der [SYMBOL_NAME](../event-table.md#symbol-name)-Ereignisse, ob zwei Typen identisch sind. `SymbolName`-Ereignisse werden am Ende eines Compiler-Front-End-Durchlaufs ausgegeben, nachdem alle Vorlageninstanziierungen durchgeführt wurden.

::: moniker-end
