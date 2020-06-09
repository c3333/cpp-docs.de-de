---
title: Implementieren von Arbeitsbereichen in Listensteuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: abbf9dd823e13fab252b7af8f32338b0d801079b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626372"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementieren von Arbeitsbereichen in Listensteuerelementen

Standardmäßig ordnet ein Listen Steuerelement alle Elemente in einem Standard Raster an. Eine andere Methode wird jedoch unterstützt, Arbeitsbereiche, die die Listenelemente in rechteckige Gruppen anordnen. Ein Bild eines Listen Steuer Elements, das Arbeitsbereiche implementiert, finden Sie unter Verwenden von Listenansicht-Steuerelementen in der Windows SDK.

> [!NOTE]
> Arbeitsbereiche sind nur sichtbar, wenn das Listen Steuerelement den Symbol Modus Symbol oder klein hat. Alle aktuellen Arbeitsbereiche bleiben jedoch erhalten, wenn die Sicht in den Berichts-oder Listenmodus gewechselt wird.

Arbeitsbereiche können verwendet werden, um einen leeren Rahmen anzuzeigen (auf der linken, oberen und/oder rechten Seite) oder eine horizontale Schiebe Leiste anzuzeigen, wenn normalerweise keiner vorhanden ist. Eine weitere häufige Verwendung besteht darin, mehrere Arbeitsbereiche zu erstellen, in die Elemente verschoben oder gelöscht werden können. Mit dieser Methode können Sie Bereiche in einer einzelnen Ansicht erstellen, die unterschiedliche Bedeutungen haben. Der Benutzer kann dann die Elemente kategorisieren, indem Sie Sie in einem anderen Bereich platzieren. Ein Beispiel hierfür wäre eine Ansicht eines Dateisystems mit einem Bereich für Dateien mit Lese-/Schreibzugriff und einem anderen Bereich für schreibgeschützte Dateien. Wenn ein Datei Element in den schreibgeschützten Bereich verschoben wurde, wird es automatisch schreibgeschützt. Wenn Sie eine Datei aus dem schreibgeschützten Bereich in den Lese-/Schreibbereich verschieben, wird die Datei mit Lese-/Schreibzugriff.

`CListCtrl`bietet mehrere Element Funktionen zum Erstellen und Verwalten von Arbeitsbereichen in Ihrem Listen Steuerelement. " [Getworkareas](reference/clistctrl-class.md#getworkareas) " und " [setworkareas](reference/clistctrl-class.md#setworkareas) " rufen ein Array von `CRect` Objekten (oder Strukturen) ab und legen es fest `RECT` , das die derzeit implementierten Arbeitsbereiche für das Listen Steuerelement speichert. Außerdem ruft [getnumofworkareas](reference/clistctrl-class.md#getnumberofworkareas) die aktuelle Anzahl von Arbeitsbereichen für das Listen Steuerelement ab (standardmäßig NULL).

## <a name="items-and-working-areas"></a>Elemente und Arbeitsbereiche

Wenn ein Arbeitsbereich erstellt wird, werden Elemente, die sich innerhalb des Arbeitsbereichs befinden, zu Mitgliedern des Arbeitsbereichs. Ebenso, wenn ein Element in einen Arbeitsbereich verschoben wird, wird es zu einem Member des Arbeitsbereichs, in den es verschoben wurde. Wenn ein Element nicht in einem Arbeitsbereich vorhanden ist, wird es automatisch zu einem Member des ersten Arbeitsbereichs (Index 0). Wenn Sie ein Element erstellen und es in einem bestimmten Arbeitsbereich platzieren möchten, müssen Sie das Element erstellen und es dann mit einem aufrufswert in den gewünschten Arbeitsbereich [verschieben.](reference/clistctrl-class.md#setitemposition) Das zweite Beispiel unten veranschaulicht dieses Verfahren.

Im folgenden Beispiel werden vier Arbeitsbereiche ( `rcWorkAreas` ) mit gleicher Größe und einem 10 Pixel weiten Rahmen um jeden Arbeitsbereich in einem Listen Steuerelement ( `m_WorkAreaListCtrl` ) implementiert.

[!code-cpp[NVC_MFCControlLadenDialog#20](codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

Der Ansichts Wert von [näherateviewrect](reference/clistctrl-class.md#approximateviewrect) wurde ausgelöst, um eine Schätzung des Gesamtbereichs zu erhalten, der zum Anzeigen aller Elemente in einer Region erforderlich ist. Diese Schätzung wird dann in vier Bereiche unterteilt und mit einem 5-Pixel-weiten Rahmen aufgefüllt.

Im nächsten Beispiel werden die vorhandenen Listenelemente jeder Gruppe ( `rcWorkAreas` ) zugewiesen und die Steuerelement Ansicht ( `m_WorkAreaListCtrl` ) aktualisiert, um den Effekt abzuschließen.

[!code-cpp[NVC_MFCControlLadenDialog#21](codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](using-clistctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
