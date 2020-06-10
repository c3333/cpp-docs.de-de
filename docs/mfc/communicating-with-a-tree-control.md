---
title: Kommunizieren mit dem Struktursteuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: f480cdad2fce53f830b8067083a8a4be4b4e4848
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619649"
---
# <a name="communicating-with-a-tree-control"></a>Kommunizieren mit dem Struktursteuerelement

Sie verwenden verschiedene Methoden zum Aufrufen von Element Funktionen in einem [CTreeCtrl](reference/ctreectrl-class.md) -Objekt, je nachdem, wie das Objekt erstellt wurde:

- Wenn sich das Struktur Steuerelement in einem Dialogfeld befindet, verwenden Sie eine Member-Variable des Typs, die `CTreeCtrl` Sie in der Dialogfeld Klasse erstellen.

- Wenn das Struktur Steuerelement ein untergeordnetes Fenster ist, verwenden Sie das- `CTreeCtrl` Objekt (oder den Zeiger), das Sie zum Erstellen des-Objekts verwendet haben.

- Wenn Sie ein- `CTreeView` Objekt verwenden, verwenden Sie die [Funktion CTreeView:: GetTreeCtrl](reference/ctreeview-class.md#gettreectrl) , um einen Verweis auf das Struktur Steuerelement zu erhalten. Sie können einen anderen Verweis mit diesem Wert initialisieren oder die Adresse des Verweises einem `CTreeCtrl` Zeiger zuweisen.

## <a name="see-also"></a>Siehe auch

[Verwenden von CTreeCtrl](using-ctreectrl.md)<br/>
[Steuerelemente](controls-mfc.md)
