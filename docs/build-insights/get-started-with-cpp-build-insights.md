---
title: Erste Schritte mit C++ Build Insights
description: Eine Übersicht auf hoher Ebene über C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3a75dfe3bf1263cce53d70b764607cad4eec86d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325715"
---
# <a name="get-started-with-c-build-insights"></a>Erste Schritte mit C++ Build Insights

::: moniker range="<=vs-2017"

Die C++-Build-Insights-Tools sind in Visual Studio 2019 verfügbar. Um die Dokumentation für diese Version **Version** anzuzeigen, legen Sie das Visual Studio Version-Selektor-Steuerelement für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range="vs-2019"

C++ Build Insights ist eine Sammlung von Tools, die eine erhöhte Transparenz in die Microsoft Visual C++ (MSVC)-Toolkette bietet. Die Tools sammeln Daten zu Ihren C++-Builds und präsentieren sie in einem Format, das Ihnen bei der Beantwortung häufig gestellter Fragen helfen kann, z. B.:

- Sind meine Builds ausreichend parallelisiert?
- Was sollte ich in meinen vorkompilierten Header (PCH) aufnehmen?
- Gibt es einen speziellen Engpass, auf den ich mich konzentrieren sollte, um meine Buildgeschwindigkeiten zu erhöhen?

Die Hauptkomponenten dieser Technologie sind:

- *vcperf.exe*, ein Befehlszeilendienstprogramm, mit dem Sie Ablaufverfolgungen für Ihre Builds sammeln können,
- eine Windows Performance Analyzer (WPA)-Erweiterung, mit der Sie Buildablaufverfolgungen in WPA anzeigen können, und
- das C++ Build Insights SDK, ein Softwareentwicklungskit zum Erstellen eigener Tools, die C++ Build Insights-Daten verwenden.

Klicken Sie auf die untenstehenden Links, um schnell mit diesen Komponenten zu beginnen:

[Tutorial: vcperf und Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
Erfahren Sie, wie Sie Buildablaufverfolgungen für Ihre C++-Projekte sammeln und sie in WPA anzeigen.

[Tutorial: Grundlagen der Windows-Leistungsfähigkeit](tutorials/wpa-basics.md)\
Entdecken Sie nützliche WPA-Tipps für die Analyse Ihrer Build-Ablaufverfolgungen.

[C++ Build Insights SDK](reference/sdk/overview.md)\
Eine Übersicht über das C++ Build Insights SDK.

::: moniker-end
