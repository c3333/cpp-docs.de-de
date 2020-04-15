---
title: Andockbare und unverankerte Symbolleisten
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: 30113565167b96b0df84a65768a1dfabe92ceffe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369774"
---
# <a name="docking-and-floating-toolbars"></a>Andockbare und unverankerte Symbolleisten

Die Microsoft Foundation-Klassenbibliothek unterstützt andockbare Symbolleisten. Eine andockbare Symbolleiste kann an jeder Seite des übergeordneten Fensters befestigt oder angedockt werden, oder sie kann in ihrem eigenen Minirahmenfenster getrennt oder geschwebt werden. In diesem Artikel wird erläutert, wie Sie andockbare Symbolleisten in Ihren Anwendungen verwenden.

Wenn Sie den Anwendungs-Assistenten zum Generieren des Skeletts Ihrer Anwendung verwenden, werden Sie aufgefordert, auszuwählen, ob sie andockbare Symbolleisten benötigen. Standardmäßig generiert der Anwendungs-Assistent den Code, der die drei Aktionen ausführt, die zum Platzieren einer andockbaren Symbolleiste in der Anwendung erforderlich sind:

- [Aktivieren Sie das Andocken in einem Rahmenfenster](#_core_enabling_docking_in_a_frame_window).

- [Aktivieren Sie das Andocken für eine Symbolleiste](#_core_enabling_docking_for_a_toolbar).

- [Docken Sie die Symbolleiste (an das Rahmenfenster)](#_core_docking_the_toolbar)an.

Wenn einer dieser Schritte fehlt, zeigt Ihre Anwendung eine Standardsymbolleiste an. Die letzten beiden Schritte müssen für jede andockbare Symbolleiste in Ihrer Anwendung ausgeführt werden.

Weitere Themen in diesem Artikel sind:

- [Schweben der Symbolleiste](#_core_floating_the_toolbar)

- [Dynamische Größenänderung der Symbolleiste](#_core_dynamically_resizing_the_toolbar)

- [Festlegen von Umbruchpositionen für eine Symbolleiste mit festem Stil](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Beispiele finden Sie im MFC General-Beispiel [DOCKTOOL.](../overview/visual-cpp-samples.md)

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>Aktivieren des Andockens in einem Rahmenfenster

Um Symbolleisten an ein Rahmenfenster anzudocken, muss das Rahmenfenster (oder Ziel) aktiviert sein, um das Andocken zu ermöglichen. Dies geschieht mit der [CFrameWnd::EnableDocking-Funktion,](../mfc/reference/cframewnd-class.md#enabledocking) die einen *DWORD-Parameter* verwendet, der eine Reihe von Stilbits ist, die angeben, welche Seite des Rahmenfensters das Andocken akzeptiert. Wenn eine Symbolleiste angedockt werden soll und mehrere Seiten vorhanden sind, an die sie `EnableDocking` angedockt werden könnte, werden die im Parameter übergebenen Seiten in der folgenden Reihenfolge verwendet: oben, unten, links, rechts. Wenn Sie Steuerleisten an einer beliebigen Stelle `EnableDocking`andocken möchten, übergeben Sie **CBRS_ALIGN_ANY** an .

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>Aktivieren des Andockens für eine Symbolleiste

Nachdem Sie das Ziel für das Andocken vorbereitet haben, müssen Sie die Symbolleiste (oder Quelle) auf ähnliche Weise vorbereiten. Rufen Sie [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) für jede Symbolleiste auf, die Sie andocken möchten, und geben Sie die Zielseiten an, an die die Symbolleiste andocken soll. Wenn keine der im Aufruf `CControlBar::EnableDocking` angegebenen Seiten, die den Seiten entsprechen soll, die für das Andocken im Rahmenfenster aktiviert sind, kann die Symbolleiste nicht andocken – sie wird schweben. Sobald es geglast wurde, bleibt es eine schwebende Symbolleiste, die nicht an das Rahmenfenster andocken kann.

Wenn der gewünschte Effekt eine permanent schwebende Symbolleiste ist, rufen Sie mit dem Parameter 0 auf. `EnableDocking` Rufen Sie dann [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)auf. Die Symbolleiste bleibt unverankert und kann dauerhaft nirgendwo andocken.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>Andocken der Symbolleiste

Das Framework ruft [CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) auf, wenn der Benutzer versucht, die Symbolleiste auf einer Seite des Rahmenfensters zu löschen, die das Andocken ermöglicht.

Darüber hinaus können Sie diese Funktion jederzeit aufrufen, um Steuerleisten an das Rahmenfenster anzudocken. Dies geschieht normalerweise während der Initialisierung. Mehr als eine Symbolleiste kann an eine bestimmte Seite des Rahmenfensters angedockt werden.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>Schweben der Symbolleiste

Das Trennen einer andockbaren Symbolleiste aus dem Rahmenfenster wird als floating die Symbolleiste bezeichnet. Rufen Sie [dazu CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) auf. Geben Sie die Symbolleiste, die geplatzt werden soll, den Punkt, an dem sie platziert werden soll, und einen Ausrichtungsstil an, der bestimmt, ob die unverankerte Symbolleiste horizontal oder vertikal ist.

Das Framework ruft diese Funktion auf, wenn ein Benutzer eine Symbolleiste von der angedockten Position zieht und sie an einem Speicherort ablegt, an dem das Andocken nicht aktiviert ist. Dies kann sich überall innerhalb oder außerhalb des Rahmenfensters befinden. Wie `DockControlBar`bei können Sie diese Funktion auch während der Initialisierung aufrufen.

Die MFC-Implementierung von andockbaren Symbolleisten bietet nicht einige der erweiterten Funktionen in einigen Anwendungen, die andockbare Symbolleisten unterstützen. Funktionen wie anpassbare Symbolleisten werden nicht bereitgestellt.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>Dynamische Seimierung der Symbolleiste

Ab Visual C++-Version 4.0 können Sie Benutzern Ihrer Anwendung die dynamische Größenänderung der unverankerten Symbolleisten ermöglichen. In der Regel hat eine Symbolleiste eine lange, lineare Form, die horizontal angezeigt wird. Sie können jedoch die Ausrichtung der Symbolleiste und ihre Form ändern. Wenn der Benutzer beispielsweise eine Symbolleiste an eine der vertikalen Seiten des Rahmenfensters andockt, ändert sich die Form in ein vertikales Layout. Es ist auch möglich, die Symbolleiste in ein Rechteck mit mehreren Zeilen von Schaltflächen umzuformen.

Ihre Möglichkeiten:

- Geben Sie die dynamische Größe als Symbolleistenmerkmal an.

- Geben Sie eine feste Größe als Symbolleistenmerkmal an.

Um diese Unterstützung bereitzustellen, gibt es zwei neue Symbolleistenstile für die Verwendung in Ihren Aufrufen der [CToolBar::Create-Memberfunktion.](../mfc/reference/ctoolbar-class.md#create) Sie lauten wie folgt:

- **CBRS_SIZE_DYNAMIC** Die Steuerleiste ist dynamisch.

- **CBRS_SIZE_FIXED** Die Steuerleiste ist fixiert.

Mit dem dynamischen Größenstil kann der Benutzer die Größe der Symbolleiste ändern, während sie unverankert ist, jedoch nicht, während sie angedockt ist. Die Symbolleiste "umschließt" bei Bedarf, um die Form zu ändern, während der Benutzer seine Kanten zieht.

Der feste Stil "Größe" behält die Umbruchzustände einer Symbolleiste bei und fixiert die Position der Schaltflächen in jeder Spalte. Der Benutzer Ihrer Anwendung kann die Form der Symbolleiste nicht ändern. Die Symbolleiste wird an bestimmten Stellen umbrochen, z. B. an den Positionen von Trennzeichen zwischen den Schaltflächen. Diese Form wird beibehalten, unabhängig davon, ob die Symbolleiste angedockt oder schwebend ist. Der Effekt ist eine feste Palette mit mehreren Spalten von Schaltflächen.

Sie können auch [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) verwenden, um einen Status und Stil für Schaltflächen auf den Symbolleisten zurückzugeben. Der Stil einer Schaltfläche bestimmt, wie die Schaltfläche angezeigt wird und wie sie auf Benutzereingaben reagiert. der Status gibt an, ob sich die Schaltfläche in einem umschlossenen Zustand befindet.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>Festlegen von Wrap-Positionen für eine Symbolleiste mit festem Stil

Legen Sie für eine Symbolleiste mit dem festen Stil der Größe Symbolleistenschaltflächenindizes fest, auf denen die Symbolleiste umbrochen wird. Der folgende Code zeigt, wie Sie dies `OnCreate` in der Außerkraftsetzung des Hauptframefensters tun:

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

Das MFC General-Beispiel [DOCKTOOL](../overview/visual-cpp-samples.md) zeigt, wie Memberfunktionen der Klassen [CControlBar](../mfc/reference/ccontrolbar-class.md) und [CToolBar](../mfc/reference/ctoolbar-class.md) verwendet werden, um das dynamische Layout einer Symbolleiste zu verwalten. Siehe die Datei EDITBAR. CPP in DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Toolbar-Grundlagen](../mfc/toolbar-fundamentals.md)

- [QuickInfos für die Symbolleiste](../mfc/toolbar-tool-tips.md)

- [Verwenden Ihrer alten Symbolleisten](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Siehe auch

[Implementieren der MFC-Symbolleiste](../mfc/mfc-toolbar-implementation.md)
