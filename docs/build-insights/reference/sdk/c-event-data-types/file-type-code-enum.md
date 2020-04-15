---
title: FILE_TYPE_CODE Enumerat
description: Das C++ Build Insights SDK FILE_TYPE_CODE Enumerierungsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dea603a072d7b2f472112a75b2e9ccded78399a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325564"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE Enumerat

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FILE_TYPE_CODE` Enumerat beschreibt den Typ einer Datei.

## <a name="members"></a>Member

| Name | Wert | BESCHREIBUNG |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Ein Dateityp, der in dieser Enumerat nicht aufgeführt ist. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Eine Objektdatei (\*.obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Eine ausführbare Datei (\*.exe) oder DLL (\*.dll). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Eine statische Bibliotheksdatei (*.lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Eine Importbibliothek (*.lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | Eine Exportdatei (*.exp). |

## <a name="remarks"></a>Bemerkungen

::: moniker-end
