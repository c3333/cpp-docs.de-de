---
title: Enumeration FILE_TYPE_CODE
description: Die Referenz zur Enumeration FILE_TYPE_CODE im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ddd625829e94786c0daddf0e78b914e225b2ecfb
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921022"
---
# <a name="file_type_code-enum"></a>Enumeration FILE_TYPE_CODE

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Enumeration `FILE_TYPE_CODE` beschreibt den Typ einer Datei.

## <a name="members"></a>Member

| name | Wert | Beschreibung |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Dateityp, der in dieser Enumeration nicht aufgeführt ist. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Eine Objektdatei (\*.obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Eine ausführbare Datei (\*.exe) oder DLL-Datei (\*.dll). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Eine statische Bibliotheksdatei (*.lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Eine Importbibliothek (*.lib). |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | Eine Exportdateien (*.exp). |

## <a name="remarks"></a>Bemerkungen

::: moniker-end
