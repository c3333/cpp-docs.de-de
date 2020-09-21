---
title: INVOCATION_VERSION_DATA-Struktur
description: Der Verweis auf die INVOCATION_VERSION_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ec54c560dd408dc3beecbc20eaac69d389c7ec37
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041558"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA-Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `INVOCATION_VERSION_DATA`-Struktur beschreibt eine Versionsnummer als Gruppe von Integralwerten.

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

| name | BESCHREIBUNG |
|--|--|
| `VersionMajor` | Die Hauptnummer der Version. |
| `VersionMinor` | Die Nebennummer der Version. |
| `BuildNumberMajor` | Die Hauptnummer des Builds. |
| `BuildNumberMinor` | Die Nebennummer des Builds. |

::: moniker-end
