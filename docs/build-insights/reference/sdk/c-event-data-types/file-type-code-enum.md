---
title: FILE_TYPE_CODE-Aufzählung
description: Das C++ Build Insights SDK FILE_TYPE_CODE-Aufzählungs Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e64f9315c62ce40c436032d6c96fdfa725847a7f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335165"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE-Aufzählung

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FILE_TYPE_CODE`-Aufzählung beschreibt den Typ einer Datei.

## <a name="members"></a>Members

| Name | value | BESCHREIBUNG |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Ein Dateityp, der in dieser Aufzählung nicht aufgeführt ist. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Eine Objektdatei (\*. obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Eine ausführbare Datei (\*. exe) oder eine DLL-Datei (\*. dll). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Eine statische Bibliotheksdatei (*. lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Eine Import Bibliothek (*. lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005 bei der) | Eine Exportdatei (*. exp). |

## <a name="remarks"></a>Bemerkungen

::: moniker-end
