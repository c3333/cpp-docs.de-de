---
title: Erste Schritte mit C++ Build Insights
description: Eine allgemeine Übersicht über die Einblicke C++ in die Erstellung.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a5799fecc885b96f4278e0f5077662ce5fd7c8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332006"
---
# <a name="get-started-with-c-build-insights"></a>Erste Schritte mit C++ Build Insights

::: moniker range="<=vs-2017"

Die C++ Build Insights-Tools sind in Visual Studio 2019 verfügbar. Um die Dokumentation für diese Version anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2019 fest.

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights ist eine Sammlung von Tools, die eine bessere Sichtbarkeit der Microsoft C++ Visual (MSVC)-Toolkette bereitstellt. Die Tools erfassen Daten zu Ihren C++ Builds und stellen Sie in einem Format dar, das Ihnen helfen kann, häufig gestellte Fragen zu beantworten, wie z. b.:

- Werden meine Builds ausreichend parallelisiert?
- Was sollte ich in meinen vorkompilierten Header (PCH) einschließen?
- Gibt es einen bestimmten Engpass, auf den ich mich konzentrieren sollte, um meine buildgeschwindigkeiten zu steigern?

Die Hauptkomponenten dieser Technologie sind:

- *vcperf. exe*, ein Befehlszeilen-Hilfsprogramm, das Sie zum Erfassen von Ablauf Verfolgungen für Ihre Builds verwenden können.
- eine WPA-Erweiterung (Windows Performance Analyzer), mit der Sie buildüberwachungen in WPA anzeigen können.
- Das C++ Build Insights SDK, ein Software Development Kit zum Erstellen eigener Tools, die C++ buildinsights-Daten nutzen.

Klicken Sie auf die folgenden Links, um schnell mit den folgenden Komponenten zu beginnen:

[Tutorial: vcperf und Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
Erfahren Sie, wie Sie buildüberwachungen für Ihre C++ Projekte erfassen und in WPA anzeigen.

[Tutorial: Grundlagen zur Windows-Leistung](tutorials/wpa-basics.md)\
Entdecken Sie nützliche WPA-Tipps zum Analysieren ihrer buildüberwachungen.

Build Insights-SDK-\ [ C++ ](reference/sdk/overview.md)
Eine Übersicht über das C++ Build Insights SDK.

::: moniker-end
