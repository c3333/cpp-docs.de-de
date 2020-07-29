---
title: CReBar im Vergleich zu CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: d58efa3c0dfb888f0802a84b11ec597dd1267de6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228634"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar im Vergleich zu CReBarCtrl

MFC stellt zwei Klassen zum Erstellen von rebars bereit: " [Anbar](reference/crebar-class.md) " und " [krebarctrl](reference/crebarctrl-class.md) " (das die Common Control API von Windows umschließt). `CReBar`stellt die gesamte Funktionalität des allgemeinen Steuer Elements für die Grund Leiste bereit und verarbeitet viele der erforderlichen allgemeinen Steuerelement Einstellungen und-Strukturen für Sie.

`CReBarCtrl`ist eine Wrapper Klasse für das Win32-Grund leisten-Steuerelement und ist daher möglicherweise einfacher zu implementieren, wenn Sie nicht beabsichtigen, die Info Leiste in die MFC-Architektur zu integrieren. Wenn Sie beabsichtigen, den grundbalken zu verwenden `CReBarCtrl` und in die MFC-Architektur zu integrieren, müssen Sie die Bearbeitung von Grund leisten-Steuerelement Manipulationen an MFC berücksichtigen. Diese Kommunikation ist nicht schwierig. Es handelt sich jedoch um zusätzliche Aufgaben, die bei der Verwendung von nicht benötigt werden `CReBar` .

Visual C++ bietet zwei Möglichkeiten, das allgemeine Steuerelement der Grund Leiste zu nutzen.

- Erstellen Sie die Grund Leiste mithilfe `CReBar` von, und rufen Sie dann mit " [Anbar:: GetReBarCtrl](reference/crebar-class.md#getrebarctrl) " Zugriff auf die Element `CReBarCtrl` Funktionen auf.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl`ist eine Inline Member-Funktion, die den **`this`** Zeiger des Grund leisten-Objekts umwandelt. Dies bedeutet, dass der Funktionsaufruf zur Laufzeit keinen Overhead hat.

- Erstellen Sie die Info Leiste mit dem Konstruktor von " [krebarctrl](reference/crebarctrl-class.md)".

Beide Methoden erhalten Zugriff auf die Element Funktionen des Grund leisten-Steuer Elements. Wenn Sie `CReBar::GetReBarCtrl` den Befehl verwenden, wird ein Verweis auf ein-Objekt zurückgegeben, `CReBarCtrl` sodass Sie einen der beiden Member-Funktionen verwenden können. Weitere Informationen zum Erstellen und Erstellen einer Grund Leiste mithilfe von finden Sie unter " [krebar](reference/crebar-class.md) " `CReBar` .

## <a name="see-also"></a>Siehe auch

[Verwenden von CReBarCtrl](using-crebarctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
