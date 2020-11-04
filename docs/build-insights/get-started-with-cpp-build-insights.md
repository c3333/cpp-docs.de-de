---
title: Erste Schritte mit C++ Build Insights
description: Eine allgemeine Übersicht über C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c4ebbb280a5cccaa35b5efc7f90e9b570600c47b
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923638"
---
# <a name="get-started-with-c-build-insights"></a>Erste Schritte mit C++ Build Insights

::: moniker range="<=msvc-150"

Die C++ Build Insights-Tools sind in Visual Studio 2019 verfügbar. Wenn die Dokumentation für diese Version angezeigt werden soll, legen Sie das Steuerelement zur Auswahl der **Version** für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range="msvc-160"

C++ Build Insights ist eine Sammlung von Tools, mit denen Benutzer von verbesserten Einblicken in die Toolkette von Microsoft Visual C++ (MSVC) profitieren. Mit diesen Tools werden Daten zu Ihren C++-Builds erfasst und in einem Format angezeigt, mit dem sich häufige Fragen beantworten lassen. Dazu zählen z. B. folgende:

- Sind meine Builds ausreichend parallelisiert?
- Welche Elemente sollte mein vorkompilierter Header (Pre-Compiled Header, PCH) enthalten?
- Gibt es einen Engpass, den ich behandeln sollte, um die Geschwindigkeit meiner Builds zu erhöhen?

Nachfolgend sind die Hauptkomponenten dieser Technologie beschrieben:

- *vcperf.exe* , ein Befehlszeilenprogramm, mit dem Sie Ablaufverfolgungen für Ihre Builds erfassen können
- eine WPA-Erweiterung (Windows Performance Analyzer), mit der Sie Ablaufverfolgungen für Ihre Builds in WPA anzeigen können
- das C++ Build Insights SDK, ein Software Development Kit zum Erstellen eigener Tools, die C++ Build Insights-Daten nutzen

## <a name="documentation-sections"></a>Abschnitte der Dokumentation

[Tutorial: vcperf und Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
Erfahren Sie, wie Sie Ablaufverfolgungen für Ihre C++-Projekte erfassen und in WPA anzeigen.

[Tutorial: Windows Performance Analyzer-Grundlagen](tutorials/wpa-basics.md)\
Erhalten Sie nützliche WPA-Tipps für die Analyse der Ablaufverfolgungen Ihrer Builds.

[C++ Build Insights SDK](reference/sdk/overview.md)\
Eine Übersicht über das C++ Build Insights SDK.

## <a name="articles"></a>Artikel

In diesen Artikeln aus dem offiziellen C++-Teamblog finden Sie weitere Informationen zu C++ Build Insights:

[Introducing C++ Build Insights](https://devblogs.microsoft.com/cppblog/introducing-c-build-insights/) (Einführung in C++ Build Insights)

[Analyze your builds programmatically with the C++ Build Insights SDK](https://devblogs.microsoft.com/cppblog/analyze-your-builds-programmatically-with-the-c-build-insights-sdk/) (Programmgesteuerte Analyse Ihrer Builds mit dem C++ Build Insights SDK)

[Finding build bottlenecks with C++ Build Insights](https://devblogs.microsoft.com/cppblog/finding-build-bottlenecks-with-cpp-build-insights/) (Ermitteln von Engpässen bei Builds mit C++ Build Insights)

[Faster builds with PCH suggestions from C++ Build Insights](https://devblogs.microsoft.com/cppblog/faster-builds-with-pch-suggestions-from-c-build-insights/) (Schnellere Builds mit PCH-Vorschlägen aus C++ Build Insights)

::: moniker-end
