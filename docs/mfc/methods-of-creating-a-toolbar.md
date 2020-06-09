---
title: Methoden zum Erstellen einer Symbolleiste
ms.date: 11/04/2016
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
ms.openlocfilehash: b70e6f4dc15023b878bb58d6b7d0739eeb173d53
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624254"
---
# <a name="methods-of-creating-a-toolbar"></a>Methoden zum Erstellen einer Symbolleiste

MFC stellt zwei Klassen zum Erstellen von Symbolleisten bereit: [CToolBar](reference/ctoolbar-class.md) und [CToolBarCtrl](reference/ctoolbarctrl-class.md) (die die Common Control API von Windows umschließt). `CToolBar`stellt die gesamte Funktionalität des allgemeinen Steuer Elements der Symbolleiste bereit und verarbeitet viele der erforderlichen allgemeinen Steuerelement Einstellungen und-Strukturen für Sie. die resultierende ausführbare Datei ist jedoch normalerweise größer als die, die mit erstellt wird `CToolBarCtrl` .

`CToolBarCtrl`Normalerweise führt dies zu einer kleineren ausführbaren Datei, und Sie können verwenden, `CToolBarCtrl` Wenn Sie nicht beabsichtigen, die Symbolleiste in die MFC-Architektur zu integrieren. Wenn Sie `CToolBarCtrl` die Symbolleiste verwenden und in die MFC-Architektur integrieren möchten, müssen Sie die Manipulationen von Symbolleisten-Steuerelementen an MFC berücksichtigen. Diese Kommunikation ist nicht schwierig. Es handelt sich jedoch um zusätzliche Aufgaben, die bei der Verwendung von nicht benötigt werden `CToolBar` .

Visual C++ bietet zwei Möglichkeiten, um das allgemeine Steuerelement der Symbolleiste zu nutzen.

- Erstellen Sie die Symbolleiste mithilfe `CToolBar` von, und rufen Sie dann [CToolBar:: GetToolBarCtrl](reference/ctoolbar-class.md#gettoolbarctrl) auf, um Zugriff auf die Element Funktionen zu erhalten `CToolBarCtrl` .

- Erstellen Sie die Symbolleiste mithilfe des [CToolBarCtrl](reference/ctoolbarctrl-class.md)-Konstruktors.

Beide Methoden erhalten Zugriff auf die Element Funktionen des Toolbar-Steuer Elements. Wenn Sie `CToolBar::GetToolBarCtrl` den Befehl verwenden, wird ein Verweis auf ein-Objekt zurückgegeben, `CToolBarCtrl` sodass Sie einen der beiden Member-Funktionen verwenden können. Informationen zum Erstellen und Erstellen einer Symbolleiste mithilfe von finden Sie unter [CToolBar](reference/ctoolbar-class.md) `CToolBar` .

## <a name="see-also"></a>Siehe auch

[Verwenden von CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
