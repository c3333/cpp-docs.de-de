---
title: TEMPLATE_INSTANTIATION_DATA Struktur
description: Das C++ Build Insights SDK TEMPLATE_INSTANTIATION_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa669d715dbe56ce7e889330f46f307f520710f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335081"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TEMPLATE_INSTANTIATION_DATA`-Struktur beschreibt eine Vorlagen Instanziierung.

## <a name="syntax"></a>Syntax

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `SpecializationSymbolKey` | Der Schlüssel für den Typ der Vorlagen Spezialisierung. Dieser Wert ist innerhalb der zu analysierende Ablauf Verfolgung eindeutig. |
| `PrimaryTemplateSymbolKey` | Der Schlüssel für den primären Vorlagentyp, der spezialisiert wurde. Dieser Wert ist innerhalb der zu analysierende Ablauf Verfolgung eindeutig. |
| `KindCode` | Der Typ der Vorlagen Instanziierung. Weitere Informationen finden Sie unter [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Bemerkungen

Die Schlüssel in der `TEMPLATE_INSTANTIATION_DATA` Struktur sind innerhalb der zu analysierende Ablauf Verfolgung eindeutig. Zwei verschiedene Schlüssel, die von unterschiedlichen Compiler-Front-End-Vorgängen stammen, können jedoch auf zwei identische Typen verweisen. Wenn Sie `TEMPLATE_INSTANTIATION_DATA` Informationen aus mehreren Compilerdurchläufen verarbeiten, verwenden Sie die [SYMBOL_NAME](../event-table.md#symbol-name) -Ereignisse, um zu bestimmen, ob zwei Typen identisch sind. `SymbolName` Ereignisse werden am Ende eines Compiler-Front-End-Pass-Ends ausgegeben, nachdem alle Vorlagen Instanziierungen durchgeführt wurden.

::: moniker-end
