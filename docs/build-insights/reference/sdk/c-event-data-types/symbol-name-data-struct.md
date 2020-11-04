---
title: SYMBOL_NAME_DATA-Struktur
description: Die Referenz zur SYMBOL_NAME_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 08c09f304f8cc90bd48a2cecc6771d90c997a7f4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920930"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA-Struktur

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `SYMBOL_NAME_DATA`-Struktur beschreibt ein Compiler-Front-End-Symbol.

## <a name="syntax"></a>Syntax

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `Key` | Der Schlüssel des Symbols. Dieser Wert ist eindeutig innerhalb der Ablaufverfolgung, die analysiert wird. |
| `Name` | Der Name des Symbols. |

## <a name="remarks"></a>Bemerkungen

Symbole, die von zwei unterschiedlichen Compiler-Front-End-Übergaben stammen, können denselben Namen, aber verschiedene Schlüssel aufweisen. Verwenden Sie in diesem Fall Symbolnamen, um zu bestimmen, ob zwei Typen identisch sind.

::: moniker-end
