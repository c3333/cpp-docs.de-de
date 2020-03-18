---
title: CReBar im Vergleich zu CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: 94f889be453a17a55357a260bd2a0c07037f6ded
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445282"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar im Vergleich zu CReBarCtrl

MFC stellt zwei Klassen zum Erstellen von rebars bereit: " [Anbar](../mfc/reference/crebar-class.md) " und " [krebarctrl](../mfc/reference/crebarctrl-class.md) " (das die Common Control API von Windows umschließt). `CReBar` stellt die gesamte Funktionalität des allgemeinen Steuer Elements für die Grund Leiste bereit und verarbeitet viele der erforderlichen allgemeinen Steuerelement Einstellungen und-Strukturen für Sie.

`CReBarCtrl` ist eine Wrapper Klasse für das Win32-Grund leisten-Steuerelement und ist daher möglicherweise einfacher zu implementieren, wenn Sie nicht beabsichtigen, die Info Leiste in die MFC-Architektur zu integrieren. Wenn Sie `CReBarCtrl` verwenden und die Info Leiste in die MFC-Architektur integrieren möchten, müssen Sie die Bearbeitung von Grund leisten-Steuerelement Manipulationen an MFC berücksichtigen. Diese Kommunikation ist nicht schwierig. Es handelt sich jedoch um zusätzliche Aufgaben, die nicht benötigt werden, wenn Sie `CReBar`verwenden.

Visual C++ bietet zwei Möglichkeiten, das allgemeine Steuerelement der Grund Leiste zu nutzen.

- Erstellen Sie die Grund Leiste mithilfe von `CReBar`, und rufen Sie dann mit " [Anbar:: GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) " Zugriff auf die `CReBarCtrl` Member-Funktionen auf.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` ist eine Inline Member-Funktion, die den **this** -Zeiger des Grund leisten-Objekts umwandelt. Dies bedeutet, dass der Funktionsaufruf zur Laufzeit keinen Overhead hat.

- Erstellen Sie die Info Leiste mit dem Konstruktor von " [krebarctrl](../mfc/reference/crebarctrl-class.md)".

Beide Methoden erhalten Zugriff auf die Element Funktionen des Grund leisten-Steuer Elements. Wenn Sie `CReBar::GetReBarCtrl`aufgerufen wird, wird ein Verweis auf ein `CReBarCtrl` Objekt zurückgegeben, sodass Sie beide Member-Funktionen verwenden können. Weitere Informationen zum Erstellen und Erstellen einer Grund Leiste mithilfe `CReBar`finden Sie in der Info [Leiste](../mfc/reference/crebar-class.md) .

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Kontrollen](../mfc/controls-mfc.md)
