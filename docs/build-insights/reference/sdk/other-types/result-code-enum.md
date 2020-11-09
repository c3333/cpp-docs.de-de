---
title: Enumeration RESULT_CODE
description: Die Referenz zur Enumeration RESULT_CODE im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3d9d18d535d15d04a2e449bdbbf693364276a518
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922407"
---
# <a name="result_code-enum"></a>Enumeration RESULT_CODE

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Enumeration `RESULT_CODE` beschreibt Erfolgs- und Fehlerbedingungen.

## <a name="members"></a>Member

| name | Wert | Beschreibung |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | Der Vorgang wurde durchgeführt. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | Eine Ihrer Rückruffunktionen in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md) hat den Wert `CALLBACK_CODE_ANALYSIS_FAILURE` zurückgegeben. Dieser Wert ist ein Member der Enumeration [CALLBACK_CODE](callback-code-enum.md). |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | Eine Ihrer Rückruffunktionen in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md) hat den Wert `CALLBACK_CODE_ANALYSIS_CANCEL` zurückgegeben. Dieser Wert ist ein Member der Enumeration [CALLBACK_CODE](callback-code-enum.md). |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | Die angegebene Eingabe-ETW (Ereignisablaufverfolgung für Windows) ist ungültig. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | Die Ausgabe-ETW (Ereignisablaufverfolgung für Windows) ist ungültig. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005) | Die Struktur von [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) wurde nicht ordnungsgemäß initialisiert. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | Die Struktur von [RELOG_CALLBACKS](relog-callbacks-struct.md) wurde nicht ordnungsgemäß initialisiert. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | Fehler beim Öffnen der Eingabe-ETW (Ereignisablaufverfolgung für Windows). |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | Fehler beim Verarbeiten der Eingabe-ETW (Ereignisablaufverfolgung für Windows). |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | Fehler beim Starten der Neuprotokollierungssitzung. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | In der Eingabe-ETW (Ereignisablaufverfolgung für Windows) fehlen wichtige Ereignisse. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000B) | Sie verwenden C++ Build Insights für eine nicht unterstützte Windows-Version. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x0000000C) | Der angegebene Sitzungsname ist ungültig. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000D) | Dieser Vorgang erfordert Administratorrechte. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | Fehler beim Generieren einer GUID. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000F) | Fehler beim Versuch, den temporären Verzeichnispfad zu bestimmen. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | Fehler beim Versuch, ein temporäres Verzeichnis für die gestartete Ablaufverfolgungssitzung zu erstellen. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | Fehler beim Versuch, die Systemablaufverfolgung zu starten. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | Fehler beim Versuch, die MSVC-Ablaufverfolgung zu starten. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | Fehler beim Versuch, die MSVC-Ablaufverfolgung zu beenden. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | Fehler beim Versuch, die Systemablaufverfolgung zu starten. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | Eine Ablaufverfolgung wurde beendet, das temporäre Verzeichnis der Ablaufverfolgungssitzung jedoch nicht gefunden. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | Die Ablaufverfolgungsdatei für die zu beendende MSVC-Ablaufverfolgung wurde nicht gefunden. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Fehler beim Zusammenführen von Ablaufverfolgungen mithilfe des Steuerelements zur Kernelablaufverfolgung. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | Es ist ein unbekannter Fehler aufgetreten. |

::: moniker-end
