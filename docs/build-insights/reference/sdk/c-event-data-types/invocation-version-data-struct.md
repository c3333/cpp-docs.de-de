---
title: INVOCATION_VERSION_DATA Struktur
description: Das C++ Build Insights SDK INVOCATION_VERSION_DATA Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1211b4eb999fd63767af71c6884d7d20d6920df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325470"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `INVOCATION_VERSION_DATA` Struktur beschreibt eine Versionsnummer als eine Gruppe von integralen Werten.

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

## <a name="members"></a>Member

|  |  |
|--|--|
| `VersionMajor` | Die Hauptnummer der Version. |
| `VersionMinor` | Die Nebennummer der Version. |
| `BuildNumberMajor` | Die Hauptnummer des Builds. |
| `BuildNumberMinor` | Die untergeordnete Zahl des Builds. |

::: moniker-end
