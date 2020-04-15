---
title: Bildlauf und Skalierung für Ansichten
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
ms.openlocfilehash: 366f0e2953e5190f80a2877804bff2fc7dbbd520
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372790"
---
# <a name="scrolling-and-scaling-views"></a>Bildlauf und Skalierung für Ansichten

MFC unterstützt Ansichten, die scrollen, und Ansichten, die automatisch auf die Größe des Rahmenfensters skaliert werden, in dem sie angezeigt werden. Die `CScrollView` Klasse unterstützt beide Arten von Ansichten.

Weitere Informationen zum Scrollen und Skalieren finden Sie unter Klasse [CScrollView](../mfc/reference/cscrollview-class.md) in der *MFC-Referenz*. Ein Bildlaufbeispiel finden Sie im [Scribble-Beispiel](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- Scrollen einer Ansicht

- Skalieren einer Ansicht

- [Koordinaten anzeigen](/windows/win32/gdi/window-coordinate-system)

## <a name="scrolling-a-view"></a><a name="_core_scrolling_a_view"></a>Scrollen einer Ansicht

Häufig ist die Größe eines Dokuments größer als die Größe, die seine Ansicht anzeigen kann. Dies kann auftreten, weil die Daten des Dokuments zunimmt oder der Benutzer das Fenster, das die Ansicht umrahmt, verkleinert. In solchen Fällen muss die Ansicht das Scrollen unterstützen.

Jede Ansicht kann Bildlaufleistenmeldungen `OnHScroll` `OnVScroll` in ihren und Memberfunktionen verarbeiten. Sie können entweder die Bildlaufleisten-Nachrichtenbehandlung in diesen Funktionen implementieren, `CScrollView` die gesamte Arbeit selbst erledigen, oder Sie können die Klasse verwenden, um das Scrollen für Sie zu behandeln.

Mit `CScrollView` wird Folgendes ausgeführt:

- Verwaltet Fenster- und Ansichtsfenstergrößen und Zuordnungsmodi

- Scrollen Sie automatisch als Reaktion auf Bildlaufleistenmeldungen

Sie können angeben, wie viel für eine "Seite" (wenn der Benutzer in eine Bildlaufleistenwelle klickt) und eine "Linie" (wenn der Benutzer in einen Bildlaufpfeil klickt) gescrollt werden soll. Planen Sie diese Werte entsprechend der Art Ihrer Ansicht. Sie können z. B. in 1-Pixel-Schritten für eine Grafikansicht, jedoch in Schritten basierend auf der Linienhöhe in Textdokumenten scrollen.

## <a name="scaling-a-view"></a><a name="_core_scaling_a_view"></a>Skalieren einer Ansicht

Wenn die Ansicht automatisch an die Größe des Rahmenfensters anpassen soll, können Sie sie für die Skalierung anstelle des Scrollens verwenden. `CScrollView` Die logische Ansicht wird gestreckt oder verkleinert, um genau in den Clientbereich des Fensters zu passen. Eine skalierte Ansicht hat keine Bildlaufleisten.

## <a name="see-also"></a>Siehe auch

[Verwenden von Ansichten](../mfc/using-views.md)
