---
title: FILE_DATA Struktur
description: Das C++ Build Insights SDK FILE_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72cae8c8eb81bdb8d94897c46c5af90c89e92ab4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335195"
---
# <a name="file_data-structure"></a>FILE_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FILE_DATA`-Struktur beschreibt eine Dateieingabe oder-Ausgabe.

## <a name="syntax"></a>Syntax

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Path` | Der absolute Pfad der Datei. |
| `TypeCode` | Ein Code, der den Typ der Datei beschreibt. Weitere Informationen finden Sie unter [FILE_TYPE_CODE](file-type-code-enum.md). |

::: moniker-end
