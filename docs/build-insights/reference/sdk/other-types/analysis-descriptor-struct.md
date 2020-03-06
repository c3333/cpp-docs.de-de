---
title: ANALYSIS_DESCRIPTOR Struktur
description: Das C++ Build Insights SDK ANALYSIS_DESCRIPTOR Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fc11ce11e1faaae02edb36aac447c18ea8107e35
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334103"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `ANALYSIS_DESCRIPTOR`-Struktur wird mit den Funktionen [analyzea](../functions/analyze-a.md) und [analyzew](../functions/analyze-w.md) verwendet. Es wird beschrieben, wie eine Ablauf Verfolgung für die Ereignis Ablauf Verfolgung für Windows (ETW) analysiert wird.

## <a name="syntax"></a>Syntax

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `NumberOfPasses` | Die Anzahl von Analyse Durchläufen, die über die ETW-Ablauf Verfolgung durchgeführt werden sollen. |
| `Callbacks` | Ein [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) -Objekt, das angibt, welche Funktionen während der Analyse Sitzung aufgerufen werden. |
| `Context` | Ein vom Benutzer bereitgestellter Kontext, der als Argument an alle in angegebenen Rückruf Funktionen übermittelt wird `Callbacks` |

## <a name="remarks"></a>Bemerkungen

Die `Callbacks` Struktur akzeptiert nur Zeiger auf Funktionen, die nicht Mitglied sind. Sie können diese Einschränkung umgehen, indem Sie `Context` auf einen Objekt Zeiger festlegen. Dieser Objekt Zeiger wird als Argument an alle nicht-Member-Rückruf Funktionen übermittelt. Verwenden Sie diesen Zeiger, um Member-Funktionen innerhalb ihrer nicht-Member-Rückruf Funktionen aufzurufen.

::: moniker-end
