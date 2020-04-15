---
title: RESULT_CODE Enumerat
description: Das C++ Build Insights SDK RESULT_CODE Enumerierungsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 62874e176c3f3e8f9df1ca64e7b593b7a0ef5c01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323621"
---
# <a name="result_code-enum"></a>RESULT_CODE Enumerat

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RESULT_CODE` Enumerat beschreibt Erfolgs- und Fehlerbedingungen.

## <a name="members"></a>Member

| Name | Wert | BESCHREIBUNG |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | Der Vorgang wurde durchgeführt. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | Eine Ihrer Rückruffunktionen in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder `CALLBACK_CODE_ANALYSIS_FAILURE` [RELOG_DESCRIPTOR](relog-descriptor-struct.md) den Wert zurückgegeben. Dieser Wert ist ein [CALLBACK_CODE](callback-code-enum.md) Member der CALLBACK_CODE-Enumerum. |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | Eine Ihrer Rückruffunktionen in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder `CALLBACK_CODE_ANALYSIS_CANCEL` [RELOG_DESCRIPTOR](relog-descriptor-struct.md) den Wert zurückgegeben. Dieser Wert ist ein [CALLBACK_CODE](callback-code-enum.md) Member der CALLBACK_CODE-Enumerum. |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | Die angegebene ETW-Ablaufverfolgung (Input Event Tracing for Windows) ist ungültig. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | Die angegebene ETW-Ausgabeablaufverfolgung ist ungültig. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005) | Die [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) Struktur wurde nicht korrekt initialisiert. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | Die [RELOG_CALLBACKS](relog-callbacks-struct.md) Struktur wurde nicht korrekt initialisiert. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | Fehler beim Öffnen der Eingabe-ETW-Ablaufverfolgung. |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | Bei der Verarbeitung der Eingabe-ETW-Ablaufverfolgung ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | Beim Versuch, die Relogging-Sitzung zu starten, ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | Der Eingabe-ETW-Ablaufverfolgung fehlen wichtige Ereignisse. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000B) | Sie verwenden C++ Build Insights für eine nicht unterstützte Windows-Version. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x0000000C) | Der angegebene Sitzungsname ist ungültig. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000D) | Für diesen Vorgang sind Administratorrechte erforderlich. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | Beim Generieren einer GUID ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000F) | Beim Versuch, den temporären Verzeichnispfad zu ermitteln, ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | Beim Versuch, ein temporäres Verzeichnis für die gestartete Ablaufverfolgungssitzung zu erstellen, ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | Beim Versuch, die Systemablaufverfolgung zu starten, ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | Beim Versuch, die MSVC-Ablaufverfolgung zu starten, ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | Beim Versuch, die MSVC-Ablaufverfolgung zu beenden, ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | Beim Versuch, die Systemablaufverfolgung zu starten, ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | Eine Ablaufverfolgung wurde angehalten, aber das temporäre Verzeichnis der Ablaufverfolgungssitzung konnte nicht gefunden werden. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | Die Ablaufverfolgungsdatei für die angehaltene MSVC-Ablaufverfolgung wurde nicht gefunden. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Beim Zusammenführen von Ablaufverfolgungen mithilfe der Kernel-Ablaufverfolgungssteuerung ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | Es ist ein unbekannter Fehler aufgetreten. |

::: moniker-end
