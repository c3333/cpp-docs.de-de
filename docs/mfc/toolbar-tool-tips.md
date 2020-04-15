---
title: QuickInfos für die Symbolleiste
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
ms.openlocfilehash: 1762931b75734801659fd6271377260bd0473614
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373456"
---
# <a name="toolbar-tool-tips"></a>QuickInfos für die Symbolleiste

Tool-Tipps sind die winzigen Popup-Fenster, die kurze Beschreibungen des Zwecks einer Symbolleistenschaltfläche darstellen, wenn Sie die Maus über einer Schaltfläche für einen bestimmten Zeitraum positionieren. Wenn Sie eine Anwendung mit dem Anwendungs-Assistenten erstellen, der über eine Symbolleiste verfügt, wird die Unterstützung für QuickInfos bereitgestellt. In diesem Artikel wird sowohl die vom Anwendungs-Assistenten erstellte Tooltippunterstützung als auch das Hinzufügen von Tooltippunterstützung für Ihre Anwendung erläutert.

In diesem Artikel wird Folgendes behandelt:

- [Aktivieren von Tool-Tipps](#_core_activating_tool_tips)

- [Flyby-Statusleisten-Updates](#_core_fly_by_status_bar_updates)

## <a name="activating-tool-tips"></a><a name="_core_activating_tool_tips"></a>Aktivieren von Tool-Tipps

Um Tooltipps in Ihrer Anwendung zu aktivieren, müssen Sie zwei Dinge tun:

- Fügen Sie den stil CBRS_TOOLTIPS zu den anderen Stilen (z. B. WS_CHILD, WS_VISIBLE und andere **CBRS_** Stile) hinzu, die als *dwStyle-Parameter* an die [Funktion CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) oder in [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle)übergeben werden.

- Wie in der folgenden Prozedur beschrieben, fügen Sie den Text der Symbolleistenspitze, getrennt durch ein Zeilenumzufolge, an die Zeichenfolgenressource an, die die Eingabeaufforderung für den Befehl "Symbolleiste" enthält. Die Zeichenfolgenressource teilt die ID der Symbolleistenschaltfläche.

#### <a name="to-add-the-tool-tip-text"></a>So fügen Sie den QuickInfo-Text hinzu

1. Während Sie die Symbolleiste im Symbolleisten-Editor bearbeiten, öffnen Sie das Fenster **Symbolleistenschaltflächeneigenschaften** für eine bestimmte Schaltfläche.

1. Geben Sie im Feld **Eingabeaufforderung** den Text an, der in der QuickInfo für diese Schaltfläche angezeigt werden soll.

> [!NOTE]
> Das Festlegen des Textes als Schaltflächeneigenschaft im Symbolleisten-Editor ersetzt die frühere Prozedur, in der Sie die Zeichenfolgenressource öffnen und bearbeiten mussten.

Wenn auf einer Steuerleiste mit aktivierten Werkzeugspitzen untergeordnete Steuerelemente angebracht sind, wird in der Steuerleiste für jedes untergeordnete Steuerelement auf der Steuerleiste eine QuickInfo angezeigt, sofern sie die folgenden Kriterien erfüllt:

- Die ID des Steuerelements ist nicht - 1.

- Der Zeichenfolgentabelleneintrag mit derselben ID wie das untergeordnete Steuerelement in der Ressourcendatei verfügt über eine QuickInfo-Zeichenfolge.

## <a name="flyby-status-bar-updates"></a><a name="_core_fly_by_status_bar_updates"></a>Flyby Status Bar Updates

Eine Funktion, die sich auf Tool-Tipps bezieht, ist die Aktualisierung der Statusleiste "Flyby". Standardmäßig wird in der Meldung in der Statusleiste nur eine bestimmte Symbolleistenschaltfläche beschrieben, wenn die Schaltfläche aktiviert ist. Durch das Einschließen CBRS_FLYBY in `CToolBar::Create`die Liste der an übergebenen Stile können Sie diese Meldungen aktualisieren lassen, wenn der Mauszeiger über die Symbolleiste geht, ohne die Schaltfläche tatsächlich zu aktivieren.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [MFC Toolbar-Implementierung (Übersichtsinformationen zu Symbolleisten)](../mfc/mfc-toolbar-implementation.md)

- [Docking und schwimmende Symbolleisten](../mfc/docking-and-floating-toolbars.md)

- Die Klassen [CToolBar](../mfc/reference/ctoolbar-class.md) und [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Arbeiten mit der Symbolleistensteuerung](../mfc/working-with-the-toolbar-control.md)

- [Verwenden Ihrer alten Symbolleisten](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Siehe auch

[Implementieren der MFC-Symbolleiste](../mfc/mfc-toolbar-implementation.md)
