---
title: TRANSLATION_UNIT_PASS_CODE Enumerat
description: Das C++ Build Insights SDK TRANSLATION_UNIT_PASS_CODE Enumerierungsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0162d7e53bb7ee7035b94a6b640f6db87cd8b8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325291"
---
# <a name="translation_unit_pass_code-enum"></a>TRANSLATION_UNIT_PASS_CODE Enumerat

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TRANSLATION_UNIT_PASS_CODE` Enumerat.

## <a name="members"></a>Member

| Name | Wert | BESCHREIBUNG |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x00000000) | Der Front-End-Pass, der für das Analysieren des Quellcodes und dessen Konvertierung in eine Zwischensprache verantwortlich ist. |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | Der Backend-Pass, der für die Optimierung der Zwischensprache und deren Konvertierung in Maschinencode verantwortlich ist. |

## <a name="remarks"></a>Bemerkungen

Wird von den C SDK-Funktionen verwendet.

::: moniker-end
