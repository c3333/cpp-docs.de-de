---
title: Enumeration TRANSLATION_UNIT_PASS_CODE
description: Die Referenz zur Enumeration TRANSLATION_UNIT_PASS_CODE im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 31f3e16ce6d9aa8c3c9db6cf9c11069dc3ec22fe
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920917"
---
# <a name="translation_unit_pass_code-enum"></a>Enumeration TRANSLATION_UNIT_PASS_CODE

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Enumeration `TRANSLATION_UNIT_PASS_CODE`.

## <a name="members"></a>Member

| name | Wert | Beschreibung |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x00000000) | Der Front-End-Durchlauf, der für die Analyse des Quellcodes und die Konvertierung in Zwischensprache zuständig ist. |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | Der Back-End--Durchlauf, der für die Optimierung der Zwischensprache und die Konvertierung in Computercode zuständig ist. |

## <a name="remarks"></a>Hinweise

Wird von den C SDK-Funktionen verwendet.

::: moniker-end
