---
title: Implementieren von Arbeitsbereichen in Listensteuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 91577203163247bd230fecb083cf1c50e2875b98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377221"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementieren von Arbeitsbereichen in Listensteuerelementen

Standardmäßig ordnet ein Listensteuerelement alle Elemente in einer Standardraster-Mode an. Eine andere Methode wird jedoch unterstützt, Arbeitsbereiche, die die Listenelemente in rechteckige Gruppen anordnen. Ein Abbild eines Listensteuerelements, das Arbeitsbereiche implementiert, finden Sie unter Verwenden von Listenansichtssteuerelementen im Windows SDK.

> [!NOTE]
> Arbeitsbereiche sind nur sichtbar, wenn sich das Listensteuerelement im Symbol- oder kleinen Symbolmodus befindet. Alle aktuellen Arbeitsbereiche werden jedoch beibehalten, wenn die Ansicht in den Berichts- oder Listenmodus geschaltet wird.

Arbeitsbereiche können verwendet werden, um einen leeren Rahmen anzuzeigen (links, oben und/oder rechts von den Elementen) oder eine horizontale Bildlaufleiste anzuzeigen, wenn es normalerweise keinen gibt. Eine weitere häufige Verwendung besteht darin, mehrere Arbeitsbereiche zu erstellen, in die Elemente verschoben oder gelöscht werden können. Mit dieser Methode können Sie Bereiche in einer einzigen Ansicht erstellen, die unterschiedliche Bedeutungen haben. Der Benutzer kann die Elemente dann kategorisieren, indem er sie in einem anderen Bereich platziert. Ein Beispiel hierfür wäre eine Ansicht eines Dateisystems mit einem Bereich für Lese-/Schreibdateien und ein anderer Bereich für schreibgeschützte Dateien. Wenn ein Dateielement in den schreibgeschützten Bereich verschoben wird, wird es automatisch schreibgeschützt. Das Verschieben einer Datei aus dem schreibgeschützten Bereich in den Lese-/Schreibbereich würde die Datei zum Lesen/Schreiben bringen.

`CListCtrl`bietet mehrere Memberfunktionen zum Erstellen und Verwalten von Arbeitsbereichen in Ihrem Listensteuerelement. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) und [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) rufen ein `CRect` Array `RECT` von Objekten (oder Strukturen) ab und legen diese fest, die die aktuell implementierten Arbeitsbereiche für das Listensteuerelement speichern. Darüber hinaus ruft [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) die aktuelle Anzahl von Arbeitsbereichen für ihr Listensteuerelement ab (standardmäßig Null).

## <a name="items-and-working-areas"></a>Artikel und Arbeitsbereiche

Wenn ein Arbeitsbereich erstellt wird, werden Elemente, die innerhalb des Arbeitsbereichs liegen, Mitglieder. Wenn ein Element in einen Arbeitsbereich verschoben wird, wird es ebenfalls Mitglied des Arbeitsbereichs, in den es verschoben wurde. Wenn ein Element nicht innerhalb eines Arbeitsbereichs liegt, wird es automatisch Mitglied des ersten Arbeitsbereichs (Index 0). Wenn Sie ein Element erstellen und in einem bestimmten Arbeitsbereich einlegen möchten, müssen Sie das Element erstellen und dann mit einem Aufruf von [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition)in den gewünschten Arbeitsbereich verschieben. Das zweite Beispiel unten veranschaulicht diese Technik.

Im folgenden Beispiel werden vier`rcWorkAreas`Arbeitsbereiche ( ) gleicher Größe mit einem 10 Pixel breiten`m_WorkAreaListCtrl`Rahmen um jeden Arbeitsbereich in einem Listensteuerelement ( ) implementiert.

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

Der Aufruf von [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) wurde durchgeführt, um eine Schätzung der Gesamtfläche zu erhalten, die erforderlich ist, um alle Elemente in einer Region anzuzeigen. Diese Schätzung wird dann in vier Bereiche unterteilt und mit einem 5-Pixel-breiten Rahmen aufgepolstert.

Im nächsten Beispiel werden die vorhandenen Listenelemente jeder Gruppe (`rcWorkAreas``m_WorkAreaListCtrl`) zugewiesen und die Steuerelementansicht ( ) aktualisiert, um den Effekt abzuschließen.

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](../mfc/using-clistctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
