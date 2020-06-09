---
title: Hinzufügen von Steuerelementen zu einem Eigenschaftenblatt
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: 527c0a5ef6e9dc4fcc9d7668c12e15ec956b0e70
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616061"
---
# <a name="adding-controls-to-a-property-sheet"></a>Hinzufügen von Steuerelementen zu einem Eigenschaftenblatt

Standardmäßig weist ein Eigenschaften Blatt den Fensterbereich für die Eigenschaften Seiten, den Registerkarten Index und die Schaltflächen "OK", "Abbrechen" und "anwenden" zu. (Ein nicht modalem Eigenschaften Blatt verfügt nicht über die Schaltflächen OK, Abbrechen und anwenden.) Sie können dem Eigenschaften Blatt weitere Steuerelemente hinzufügen. Beispielsweise können Sie rechts neben dem Eigenschaften Seitenbereich ein Vorschau Fenster hinzufügen, um dem Benutzer anzuzeigen, wie die aktuellen Einstellungen aussehen würden, wenn Sie auf ein externes Objekt angewendet werden.

Sie können dem Eigenschaften Blatt-Dialogfeld Steuerelemente im-Handler hinzufügen `OnCreate` . Wenn Sie zusätzliche Steuerelemente berücksichtigen, müssen Sie die Größe des Eigenschaften Blatt Dialogfelds erweitern. Nachdem Sie die Basisklasse **CPropertySheet:: OnCreate**aufgerufen haben, rufen Sie [GetWindowRect](reference/cwnd-class.md#getwindowrect) auf, um die Breite und Höhe des aktuell zugeordneten Eigenschaften Blatt Fensters zu erhalten, erweitern Sie die Abmessungen des Rechtecks, und rufen Sie " [muvewindow](reference/cwnd-class.md#movewindow) " auf, um die Größe des Eigenschaften Blatt Fensters zu ändern.

## <a name="see-also"></a>Siehe auch

[Eigenschaften Blätter](property-sheets-mfc.md)<br/>
[CPropertyPage-Klasse](reference/cpropertypage-class.md)<br/>
[CPropertySheet-Klasse](reference/cpropertysheet-class.md)
