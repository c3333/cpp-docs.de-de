---
title: 'Tutorial: Windows Performance Analyzer-Grundlagen'
description: Tutorial zum Durchführen grundlegender Vorgänge in Windows Performance Analyzer.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 449fc2ddabc2bcf5b9b9f130a5e6816cdf4bc98d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685514"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>Tutorial: Windows Performance Analyzer-Grundlagen

::: moniker range="<=vs-2017"

Die C++ Build Insights-Tools sind in Visual Studio 2019 verfügbar. Wenn die Dokumentation für diese Version angezeigt werden soll, legen Sie das Steuerelement zur Auswahl der **Version** für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range="vs-2019"

Die Verwendung von C++ Build Insights setzt effektiv Kenntnisse in Windows Performance Analyzer (WPA) voraus. In diesem Artikel lernen Sie allgemeine WPA-Vorgänge kennen. Weitere Informationen zur Verwendung von WPA finden Sie in der Dokumentation zu [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer).

## <a name="change-the-view-mode"></a>Ändern des Ansichtsmodus

WPA bietet zwei grundlegende Ansichtsmodi, mit denen Sie Ihre Ablaufverfolgungen untersuchen können:

- den Diagrammmodus und
- den Tabellenmodus.

Sie können zwischen diesen Modi mithilfe der Ansichtmodussymbole oben im Ansichtsbereich wechseln:

![Wechseln zwischen Diagramm- und Tabellenmodus.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Auswählen von Voreinstellungen

Die meisten C++ Build Insights-WPA-Ansichten verfügen über mehrere Voreinstellungen, aus denen Sie auswählen können. Sie können die gewünschte Voreinstellung mithilfe des Dropdownmenüs am oberen Rand des Ansichtsbereichs auswählen:

![Auswählen einer Voreinstellung](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Vergrößern und Verkleinern

Einige Buildablaufverfolgungen sind so groß, dass Details schwer zu erkennen sind. Klicken Sie mit der rechten Maustaste auf das Diagramm, und wählen Sie **Zoom** aus, um einen relevanten Bereich zu vergrößern. Sie können jederzeit zur vorherigen Einstellung zurückkehren, indem Sie **Zoomvorgang rückgängig machen** auswählen. Diese Abbildung zeigt ein Beispiel für die Verwendung einer Auswahl und des **Zoom**-Befehls, um einen Abschnitt des Diagramms zu vergrößern:

![Kurzes Video, das das Vergrößern eines Diagramms zeigt.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Gruppieren nach verschiedenen Spalten

Sie können anpassen, wie die Ablaufverfolgung angezeigt wird. Klicken Sie oben im Ansichtsbereich auf das Zahnradsymbol, und ordnen Sie die Spalten im Build-Explorer-Ansicht-Editor neu an. Die Spalten über der gelben Zeile in diesem Dialogfeld sind die Spalten, nach denen Ihre Datenzeilen gruppiert sind. Die Spalte rechts über der gelben Linie ist ein Sonderfall: In der Diagrammansicht wird Sie auf den farbigen Balken angezeigt.

Diese Abbildung zeigt das Beispiel eines Balkendiagramms für einen Linkaufruf. Verwenden Sie das Zahnradsymbol, um das Build-Explorer-Dialogfeld „Ansicht-Editor“ zu öffnen. Anschließend ziehen Sie die Einträge für die Spalten „Komponente“ und Name“ über die gelbe Zeile. Die Konfiguration wird geändert, um den Detailgrad zu erhöhen und damit Sie sehen, was im Linker tatsächlich passiert ist:

![Kurzes Video zum Gruppieren nach verschiedenen Spalten.](media/wpa-grouping.gif)

## <a name="see-also"></a>Weitere Informationen

[Tutorial: vcperf und Windows Performance Analyzer](vcperf-and-wpa.md)\
[Referenz: vcperf-Befehle](/cpp/build-insights/reference/vcperf-commands)\
[Referenz: Windows Performance Analyzer-Ansichten](/cpp/build-insights/reference/wpa-views)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
