---
title: Event_id-Aufzählung
description: Das C++ Build Insights SDK event_id-Aufzählungs Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_ID
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6dba5d5dded4e08fc6a9fc2279827feefbf13393
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335219"
---
# <a name="event_id-enum"></a>Event_id-Aufzählung

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EVENT_ID`-Aufzählung.

## <a name="members"></a>Members

| Name | value | Ereignis Details-URL |
|--|--|--|
| `EVENT_ID_BACK_END_PASS` | 1 (0x00000001) | [BACK_END_PASS](../event-table.md#back-end-pass) |
| `EVENT_ID_BOTTOM_UP` | 2 (0x00000002) | [BOTTOM_UP](../event-table.md#bottom-up) |
| `EVENT_ID_C1_DLL` | 3 (0x00000003) | [C1_DLL](../event-table.md#c1-dll) |
| `EVENT_ID_C2_DLL` | 4 (0x00000004) | [C2_DLL](../event-table.md#c2-dll) |
| `EVENT_ID_CODE_GENERATION` | 5 (0x00000005 bei der) | [CODE_GENERATION](../event-table.md#code-generation) |
| `EVENT_ID_COMMAND_LINE` | 6 (0x00000006) | [COMMAND_LINE](../event-table.md#command-line) |
| `EVENT_ID_COMPILER` | 7 (0x00000007) | [Versionen](../event-table.md#compiler) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | 8 (0x00000008) | [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | 9 (0x00000009) | [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output) |
| `EVENT_ID_EXP_OUTPUT` | 10 (0x000000a) | [EXP_OUTPUT](../event-table.md#exp-output) |
| `EVENT_ID_FILE_INPUT` | 11 (0x000000b) | [FILE_INPUT](../event-table.md#file-input) |
| `EVENT_ID_FORCE_INLINEE` | 12 (0x000000c) | [FORCE_INLINEE](../event-table.md#force-inlinee) |
| `EVENT_ID_FRONT_END_FILE` | 13 (0x000000d) | [FRONT_END_FILE](../event-table.md#front-end-file) |
| `EVENT_ID_FRONT_END_PASS` | 14 (0x000000e) | [FRONT_END_PASS](../event-table.md#front-end-pass) |
| `EVENT_ID_FUNCTION` | 15 (0x000000f) | [FUNCTION](../event-table.md#function) |
| `EVENT_ID_IMP_LIB_OUTPUT` | 16 (0x00000010) | [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output) |
| `EVENT_ID_LIB_OUTPUT` | 17 (0x00000011) | [LIB_OUTPUT](../event-table.md#lib-output) |
| `EVENT_ID_LINKER` | 18 (0x00000012) | [Amin](../event-table.md#linker) |
| `EVENT_ID_LTCG` | 19 (0x00000013) | [LTCG](../event-table.md#ltcg) |
| `EVENT_ID_OBJ_OUTPUT` | 20 (0x00000014) | [OBJ_OUTPUT](../event-table.md#obj-output) |
| `EVENT_ID_OPT_ICF` | 21 (0x00000015) | [OPT_ICF](../event-table.md#opt-icf) |
| `EVENT_ID_OPT_LBR` | 22 (0x00000016) | [OPT_LBR](../event-table.md#opt-lbr) |
| `EVENT_ID_OPT_REF` | 23 (0x00000017) | [OPT_REF](../event-table.md#opt-ref) |
| `EVENT_ID_PASS1` | 24 (0x00000018) | [PASS1](../event-table.md#pass1) |
| `EVENT_ID_PASS2` | 25 (0x00000019) | [PASS2](../event-table.md#pass2) |
| `EVENT_ID_PRE_LTCG_OPT_REF` | 26 (0x0000001a) | [PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref) |
| `EVENT_ID_SYMBOL_NAME` | 27 (0x0000001b) | [SYMBOL_NAME](../event-table.md#symbol-name) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | 28 (0x0000001c) | [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) |
| `EVENT_ID_THREAD` | 29 (0x0000001d) | [Aden](../event-table.md#thread) |
| `EVENT_ID_TOP_DOWN` | 30 (0x0000001E) | [TOP_DOWN](../event-table.md#top-down) |
| `EVENT_ID_WHOLE_PROGRAM_ANALYSIS` | 31 (0x0000001f) | [WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis) |

## <a name="remarks"></a>Bemerkungen

Diese Werte werden mit den C SDK-Funktionen verwendet.

::: moniker-end
