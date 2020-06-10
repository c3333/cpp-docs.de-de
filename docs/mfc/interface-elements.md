---
title: Schnittstellenelemente
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: 4d4d81287cb30a7d3608025085cdb3f9a208147a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619989"
---
# <a name="interface-elements"></a>Schnittstellenelemente

In diesem Dokument werden die Schnittstellen Elemente beschrieben, die in Visual Studio 2008 SP1 eingeführt wurden, und es werden auch Unterschiede in Bezug auf die frühere Version der Bibliothek beschrieben.

Die folgende Abbildung zeigt eine Anwendung, die mithilfe der neuen Schnittstellen Elemente erstellt wurde.

![Beispielanwendung für das MFC-Feature Pack](../mfc/media/mfc_featurepack.png "Beispielanwendung für das MFC-Feature Pack")

## <a name="window-docking"></a>Fenster Andocken

Die Fenster Docking-Funktionalität ähnelt dem Andock Fenster, das von der grafischen Visual Studio-Benutzeroberfläche verwendet wird.

## <a name="control-bars-are-now-panes"></a>Steuer leisten sind jetzt Bereiche.

Steuer leisten werden nun als Bereiche bezeichnet und werden von der [cbasepane-Klasse](reference/cbasepane-class.md)abgeleitet. In früheren Versionen von MFC lautete die Basisklasse von Steuer leisten `CControlBar` .

Das Hauptrahmen Fenster der Anwendung wird normalerweise durch die [CFrameWndEx-Klasse](reference/cframewndex-class.md) oder die [CMDIFrameWndEx-Klasse](reference/cmdiframewndex-class.md)dargestellt. Der Hauptframe wird als *Dock Site*bezeichnet. Bereiche können einen von drei Typen von übergeordneten Elementen aufweisen: eine Dock Site, eine Andock Leiste oder ein Mini Rahmen Fenster.

Es gibt zwei Arten von Bereichen: nicht Größenänderung und Größenänderung. In der Größe änderbare Bereiche (z. b. Status leisten und Symbolleisten) können mithilfe von Aufteilungen oder Schiebereglern geändert werden. In der Größe zu verwendende Bereiche können Container bilden (ein Bereich kann an einen anderen Bereich angedockt werden, um einen Splitter zwischen diesen zu erstellen). Die Größe der Größenänderung kann jedoch nicht an Andock leisten angefügt (angedockt) werden.

Wenn Ihre Anwendung nicht Größen fähige Bereiche verwendet, leiten Sie Sie von der [CPANE-Klasse](reference/cpane-class.md)ab.  Wenn Ihre Anwendung Größenänderung verwendet, leiten Sie Sie von der [CDockablePane-Klasse](reference/cdockablepane-class.md) ab.

## <a name="dock-site"></a>Dock Site

Die Dock Site (oder das Hauptrahmen Fenster) besitzt alle Bereiche und Mini Rahmen Fenster in einer Anwendung. Die Dock Site enthält einen [cdockingmanager](reference/cdockingmanager-class.md) -Member. Dieser Member verwaltet eine Liste aller Bereiche, die zur Dock Site gehören. Die Liste wird so angeordnet, dass die Bereiche, die an den äußeren Rändern der Dock Site erstellt werden, am Anfang der Liste positioniert werden. Wenn das Framework die Dock Site neu zeichnet, wird die Liste durchlaufen und das Layout der einzelnen Bereiche so angepasst, dass das aktuelle umschließende Rechteck der Dock Site enthalten ist. Sie können `AdjustDockingLayout` oder Abrufen `RecalcLayout` , wenn Sie das Andock Layout anpassen müssen, und das Framework leitet diesen Befehl an den Docking-Manager um.

## <a name="dock-bars"></a>Andock leisten

Jedes Hauptrahmen Fenster kann *Andock leisten* entlang seines Rahmens positionieren. Eine Andock Leiste ist ein Bereich, der zu einer [cdocksite-Klasse](reference/cdocksite-class.md)gehört. Andock leisten können von [CPANE](reference/cpane-class.md)abgeleitete Objekte akzeptieren, z. b. Symbolleisten. Zum Erstellen von Andock leisten, wenn das Hauptrahmen Fenster initialisiert wird, rufen Sie auf `EnableDocking` . Zum Aktivieren von "automatisch ausblenden"-leisten wird aufgerufen `EnableAutoHideBars` . `EnableAutoHideBars`erstellt [cautohidedocksite](reference/cautohidedocksite-class.md) -Objekte und positioniert diese neben den einzelnen Andock leisten.

Jede Andock Leiste ist in Andock Zeilen unterteilt. Andock Zeilen werden durch die [cdockingpanesrow-Klasse](reference/cdockingpanesrow-class.md)dargestellt. Jede Andock Zeile enthält eine Liste von Symbolleisten. Wenn ein Benutzer eine Symbolleiste andockt oder die Symbolleiste innerhalb derselben Andock Leiste von einer Zeile in eine andere verschiebt, erstellt das Framework entweder eine neue Zeile und passt die Größe der Andock Leiste entsprechend an, oder die Symbolleiste wird in einer vorhandenen Zeile positioniert.

## <a name="mini-frame-windows"></a>Mini Rahmen Fenster

Ein unverankerter Bereich befindet sich in einem Mini Rahmen Fenster. Mini Rahmen Fenster werden durch zwei Klassen dargestellt: [CMDITabInfo-Klasse](reference/cmditabinfo-class.md) (die nur einen Bereich enthalten kann) und [cmultipaneframewnd-Klasse](reference/cmultipaneframewnd-class.md) (die mehrere Bereiche enthalten kann). Um einen Bereich im Code zu verwenden, nennen Sie [cbasepane:: floatpane](reference/cbasepane-class.md#floatpane). Nachdem ein Bereich schwebt, erstellt das Framework automatisch ein Mini Rahmen Fenster, und dieses Mini Rahmen Fenster wird zum übergeordneten Element des gleitenden Bereichs. Wenn der Gleit kommatyp Andocken wird, setzt das Framework seinen übergeordneten Bereich zurück, und der Gleit Komma Bereich wird zu einer Andock Leiste (für Symbolleisten) oder zu einer Dock Site (für Bereiche mit Größenänderung).

## <a name="pane-dividers"></a>Bereichs Teiler

Bereichs Teiler (auch als Schieberegler oder Splitters bezeichnet) werden durch die [cpanedivider-Klasse](reference/cpanedivider-class.md)dargestellt. Wenn ein Benutzer einen Bereich andockt, erstellt das Framework Bereichs Teiler, unabhängig davon, ob der Bereich an der Dock Site oder in einem anderen Bereich angedockt ist. Wenn ein Bereich an die Dock Site angedockt wird, wird der Bereichs Teiler als *Standard Bereichs Teiler*bezeichnet. Der Standard Bereichs Teiler ist für das Layout aller Andock Bereiche an der Dock Site zuständig. Der Dock-Manager verwaltet eine Liste der Standard Bereichs Teiler und eine Liste von Bereichen. Dock-Manager sind für das Layout aller Andock Bereiche verantwortlich.

## <a name="containers"></a>Container

Alle Bereiche, die in der Größe geändert werden können, werden in Containern verwaltet. Container werden durch die [cpanecontainer-Klasse](reference/cpanecontainer-class.md)dargestellt. Jeder Container hat Zeiger auf den linken Bereich, den rechten Bereich, den linken unter Container, den rechten unter Container und den Splitter zwischen dem linken und dem rechten Teil. ("*Left* " und " *right* " verweisen nicht auf physische Seiten, sondern identifizieren die Verzweigungen einer Baumstruktur.) Auf diese Weise können wir eine Struktur von Bereichen und Aufteilungen erstellen und daher komplexe Layouts von Bereichen erzielen, deren Größe angepasst werden kann. Die- `CPaneContainer` Klasse verwaltet die Containerstruktur. Sie verwaltet außerdem zwei Listen mit Bereichen und Schieberegler, die sich in dieser Struktur befinden. Bereichs Container-Manager werden in der Regel in Standard Schieberegler und Mini Rahmen Fenster eingebettet, die mehrere Bereiche enthalten.

## <a name="auto-hide-control-bars"></a>Steuer leisten automatisch ausblenden

Standardmäßig `CDockablePane` unterstützt die Funktion automatisch ausblenden. Wenn ein Benutzer auf die Schaltfläche Pin in der Beschriftung von klickt `CDockablePane` , schaltet das Framework den Bereich in den Modus für automatisches ausblenden. Um den Klick zu verarbeiten, erstellt das Framework eine [cmfcautohidebar-Klasse](reference/cmfcautohidebar-class.md) und eine [cmfcautohidebutton-Klasse](reference/cmfcautohidebutton-class.md) , die dem Objekt zugeordnet ist `CMFCAutoHideBar` . Das Framework stellt das neue `CMFCAutoHideBar` auf der [cautohidedocksite](reference/cautohidedocksite-class.md)bereit. Das Framework fügt auch das `CMFCAutoHideButton` an die Symbolleiste an. Die [cdockingmanager-Klasse](reference/cdockingmanager-class.md) verwaltet `CDockablePane` .

## <a name="tabbed-control-bars-and-outlook-bars"></a>Registerkarten-Steuer leisten und Outlook-Balken

Die [cmfcbasetabctrl-Klasse](reference/cmfcbasetabctrl-class.md) implementiert die Basisfunktionen eines Fensters im Registerkarten Format mit trennbaren Registerkarten. Um ein- `CMFCBaseTabCtrl` Objekt zu verwenden, initialisieren Sie eine [cbasetabbedpane-Klasse](reference/cbasetabbedpane-class.md) in Ihrer Anwendung. `CBaseTabbedPane`wird von abgeleitet `CDockablePane` und verwaltet einen Zeiger auf ein- `CMFCBaseTabCtrl` Objekt. `CBaseTabbedPane`Ermöglicht Benutzern das Andocken und Ändern der Größe von Steuer leisten im Registerkarten Format. Verwenden Sie [CDockablePane:: attachdetabwnd](reference/cdockablepane-class.md#attachtotabwnd) zum dynamischen Erstellen von Steuer leisten, die angedockt und im Registerkarten Format angezeigt werden.

Das Outlook-leisten-Steuerelement basiert auch auf Balken im Registerkarten Format. Die [CMFCOutlookBar-Klasse](reference/cmfcoutlookbar-class.md) wird von abgeleitet `CBaseTabbedPane` . Weitere Informationen zur Verwendung der Outlook-Leiste finden Sie unter [CMFCOutlookBar-Klasse](reference/cmfcoutlookbar-class.md).

## <a name="see-also"></a>Siehe auch

[Konzepte](mfc-concepts.md)
