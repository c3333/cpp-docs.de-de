---
title: INVOCATION_VERSION_DATA Struktur
description: Das C++ Build Insights SDK INVOCATION_VERSION_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 040b0f90b14133ec2b25f7a12d35b88d382c4f7a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335129"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

In der `INVOCATION_VERSION_DATA` Struktur wird eine Versionsnummer als Gruppe ganzzahliger Werte beschrieben.

## <a name="syntax"></a>Syntax

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `VersionMajor` | Die Hauptnummer der Version. |
| `VersionMinor` | Die neben Nummer der Version. |
| `BuildNumberMajor` | Die Hauptnummer des Builds. |
| `BuildNumberMinor` | Die neben Nummer des Builds. |

::: moniker-end
