---
title: RESULT_CODE-Aufzählung
description: Das C++ Build Insights SDK RESULT_CODE-Aufzählungs Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ee563d148b3456b288bc418255ec46f8cbade7ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333947"
---
# <a name="result_code-enum"></a>RESULT_CODE-Aufzählung

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RESULT_CODE`-Aufzählung beschreibt die Erfolgs-und Fehlerbedingungen.

## <a name="members"></a>Members

| Name | value | BESCHREIBUNG |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | Der Vorgang war erfolgreich. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | Eine ihrer Rückruf Funktionen in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md) hat den `CALLBACK_CODE_ANALYSIS_FAILURE` Wert zurückgegeben. Dieser Wert ist ein Member der [CALLBACK_CODE](callback-code-enum.md) Enumeration. |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | Eine ihrer Rückruf Funktionen in [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md) hat den `CALLBACK_CODE_ANALYSIS_CANCEL` Wert zurückgegeben. Dieser Wert ist ein Member der [CALLBACK_CODE](callback-code-enum.md) Enumeration. |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | Die angegebene Ablauf Verfolgung für die Ereignis Ablauf Verfolgung für Windows (ETW) ist ungültig. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | Die angegebene Ausgabe-etw-Ablauf Verfolgung ist ungültig. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005 bei der) | Die [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) Struktur wurde nicht ordnungsgemäß initialisiert. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | Die [RELOG_CALLBACKS](relog-callbacks-struct.md) Struktur wurde nicht ordnungsgemäß initialisiert. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | Fehler beim Öffnen der etw-Eingabe Ablauf Verfolgung. |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | Fehler beim Verarbeiten der etw-Eingabe Ablauf Verfolgung. |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | Fehler beim Starten der Sitzung zum erneuten protokollieren. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000a) | In der Eingabe-etw-Ablauf Verfolgung fehlen wichtige Ereignisse. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000b) | Sie verwenden C++ buildeinblicke für eine nicht unterstützte Windows-Version. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x0000000c) | Der angegebene Sitzungsname ist ungültig. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000d) | Für diesen Vorgang sind Administrator Berechtigungen erforderlich. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000e) | Fehler beim Erstellen einer GUID. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000f) | Fehler beim Versuch, den temporären Verzeichnispfad zu ermitteln. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | Fehler beim Erstellen eines temporären Verzeichnisses für die Ablauf Verfolgungs Sitzung, die gestartet wird. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | Fehler beim Starten der System Ablauf Verfolgung. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | Beim Versuch, die MSVC-Ablauf Verfolgung zu starten, ist ein Fehler aufgetreten. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | Fehler beim Versuch, die MSVC-Ablauf Verfolgung zu beenden. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | Fehler beim Starten der System Ablauf Verfolgung. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | Eine Ablauf Verfolgung wurde beendet, das temporäre Verzeichnis der Ablauf Verfolgungs Sitzung wurde jedoch nicht gefunden. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | Die Ablauf Verfolgungs Datei für die zu beendende MSVC-Ablauf Verfolgung wurde nicht gefunden. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Fehler beim Zusammenführen von Ablauf Verfolgungen mithilfe des Kernel-Trace-Steuer Elements. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | Es ist ein unbekannter Fehler aufgetreten. |

::: moniker-end
