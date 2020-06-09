---
title: Methoden zum Erstellen einer Statusleiste
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: 9bdaa76dc68467dce1021d9b5f54eaafa248c529
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624271"
---
# <a name="methods-of-creating-a-status-bar"></a>Methoden zum Erstellen einer Statusleiste

MFC stellt zwei Klassen zum Erstellen von Status leisten bereit: [CStatusBar](reference/cstatusbar-class.md) und [CStatusBarCtrl](reference/cstatusbarctrl-class.md) (die die Common Control API von Windows umschließt). `CStatusBar`stellt die gesamte Funktionalität der allgemeinen Steuerung der Statusleiste bereit, interagiert automatisch mit Menüs und Symbolleisten und verarbeitet viele der erforderlichen allgemeinen Steuerelement Einstellungen und-Strukturen für Sie. die resultierende ausführbare Datei ist jedoch normalerweise größer als die, die mit erstellt wird `CStatusBarCtrl` .

`CStatusBarCtrl`in der Regel führt dies zu einer kleineren ausführbaren Datei, und Sie können verwenden, `CStatusBarCtrl` Wenn Sie nicht beabsichtigen, die Statusleiste in die MFC-Architektur zu integrieren. Wenn Sie beabsichtigen, `CStatusBarCtrl` die Statusleiste in der MFC-Architektur zu verwenden und zu integrieren, müssen Sie zusätzliche Sorgfalt walten lassen, wenn Sie die Manipulationen von Status leisten Steuerelementen an MFC übermitteln. Diese Kommunikation ist nicht schwierig. Es handelt sich jedoch um zusätzliche Aufgaben, die bei der Verwendung von nicht benötigt werden `CStatusBar` .

Visual C++ bietet zwei Möglichkeiten, um das allgemeine Steuerelement für die Statusleiste zu nutzen.

- Erstellen Sie die Statusleiste mithilfe `CStatusBar` von, und rufen Sie dann [CStatusBar:: GetStatusBarCtrl](reference/cstatusbar-class.md#getstatusbarctrl) auf, um Zugriff auf die Element Funktionen zu erhalten `CStatusBarCtrl` .

- Erstellen Sie die Statusleiste mithilfe des [CStatusBarCtrl](reference/cstatusbarctrl-class.md)-Konstruktors.

Beide Methoden erhalten Zugriff auf die Element Funktionen des StatusBar-Steuer Elements. Wenn Sie `CStatusBar::GetStatusBarCtrl` den Befehl verwenden, wird ein Verweis auf ein-Objekt zurückgegeben, `CStatusBarCtrl` sodass Sie einen der beiden Member-Funktionen verwenden können. Weitere Informationen zum Erstellen und Erstellen einer Statusleiste mithilfe von finden Sie unter [CStatusBar](reference/cstatusbar-class.md) `CStatusBar` .

## <a name="see-also"></a>Siehe auch

[Verwenden von CStatusBarCtrl](using-cstatusbarctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
