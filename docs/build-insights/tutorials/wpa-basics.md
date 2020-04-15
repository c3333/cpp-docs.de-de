---
title: 'Tutorial: Grundlagen des Windows-Leistungsanalyseprogramms'
description: Tutorial zum Abschließen grundlegender Vorgänge in Windows Performance Analyzer.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae1050b9389527a12f5bdbea6d695c0f20510127
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323404"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>Tutorial: Grundlagen des Windows-Leistungsanalyseprogramms

::: moniker range="<=vs-2017"

Die C++-Build-Insights-Tools sind in Visual Studio 2019 verfügbar. Um die Dokumentation für diese Version **Version** anzuzeigen, legen Sie das Visual Studio Version-Selektor-Steuerelement für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range="vs-2019"

Die Verwendung von C++ Build Insights erfordert effektiv einige Kenntnisse von Windows Performance Analyzer (WPA). Dieser Artikel hilft Ihnen, sich mit häufigen WPA-Vorgängen vertraut zu machen. Weitere Informationen zur Verwendung von WPA finden Sie in der [Windows Performance Analyzer-Dokumentation.](/windows-hardware/test/wpt/windows-performance-analyzer)

## <a name="change-the-view-mode"></a>Ändern des Ansichtsmodus

WPA bietet zwei grundlegende Ansichtsmodi, mit denen Sie Ihre Spuren erkunden können:

- Graph-Modus und
- Tabellenmodus.

Sie können zwischen ihnen wechseln, indem Sie die Ansichtsmodussymbole oben im Ansichtsbereich verwenden:

![Wechseln zwischen Diagrammmodus und Tabellenmodus.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Presets auswählen

Die meisten C++ Build Insights WPA-Ansichten verfügen über mehrere Voreinstellungen, aus denen Sie wählen können. Sie können die gewünschte Voreinstellung auswählen, indem Sie das Dropdown-Menü oben im Ansichtsbereich verwenden:

![Auswählen einer Voreinstellung.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Vergrößern und Verkleinern

Einige Build-Spuren sind so groß, dass es schwierig ist, die Details zu erkennen. Um einen Bereich zu vergrößern, der Sie interessiert, klicken Sie mit der rechten Maustaste auf das Diagramm, und wählen Sie **Zoom**aus. Sie können jederzeit zur vorherigen Einstellung zurückkehren, indem Sie **Zoom rückgängig machen**. Dieses Bild zeigt ein Beispiel für die Verwendung einer Auswahl und den Befehl **Zoom,** um einen Abschnitt des Diagramms zu vergrößern:

![Vergrößern eines Diagramms.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Gruppieren nach verschiedenen Spalten

Sie können die Anzeige der Ablaufverfolgung anpassen. Klicken Sie auf das Zahnradsymbol oben in einem Ansichtsbereich, und ordnen Sie die Spalten im Ansichts-Editor des Build-Explorers neu an. Die Spalten, die sich über der gelben Linie in diesem Dialogfeld befinden, sind die Spalten, nach denen Ihre Datenzeilen gruppiert sind. Die Spalte direkt über der gelben Linie ist etwas Besonderes: In der Diagrammansicht wird sie auf den farbigen Balken angezeigt.

Dieses Bild zeigt ein Beispielbalkendiagramm eines Linkaufrufs. Wir verwenden das Zahnradsymbol, um das Dialogfeld "Explorer-Ansichts-Editor erstellen" zu öffnen. Anschließend ziehen wir die Spalteneinträge "Komponente" und "Name" über die gelbe Linie. Die Konfiguration wird geändert, um die Detailgenauigkeit zu erhöhen und zu sehen, was tatsächlich innerhalb des Linkers passiert ist:

![Vergrößern eines Diagramms.](media/wpa-grouping.gif)

## <a name="see-also"></a>Siehe auch

[Tutorial: vcperf und Windows Performance Analyzer](vcperf-and-wpa.md)\
[Referenz: vcperf-Befehle](/cpp/build-insights/reference/vcperf-commands)\
[Referenz: Windows Performance Analyzer-Ansichten](/cpp/build-insights/reference/wpa-views)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
